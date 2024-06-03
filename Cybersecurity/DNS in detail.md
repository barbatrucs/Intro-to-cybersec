DNS (Domain Name System) provides a simple way for us to communicate with devices on the internet without remembering IP adresses

## Domain hierarchy

![[dns domain name hierarchy.png]]
**TLD (Top-Level-Domain)**
 TLD is the most righthand part of a domain name.
 There are two types of TLD, gTLD (Generic Top Level) and ccTLD (Country Code Top Level Domain).
 
**Second-Level Domain**
When registering a domain name, the second-level domain is limited to 63 characters + the TLD and can only use a-z 0-9 and hyphens

**Subdomain**  
A subdomain sits on the left-hand side of the Second-Level Domain using a period to separate it.
limited to 63 characters and can only use a-z 0-9 and hyphens. 
You can use multiple subdomains split with periods to create longer names, but the total length must be kept to 253 characters or less.  There is no limit to the number of subdomains you can create for your domain name.


## DNS Record Types

**A Record**
These records resolve to IPv4 addresses, for example 104.26.10.229

**AAAA Record**
These records resolve to IPv6 addresses, for example 2606:4700:20::681a:be5  

**CNAME Record**
These records resolve to another domain name, for example, TryHackMe's online shop has the subdomain name store.tryhackme.com which returns a CNAME record shops.shopify.com. Another DNS request would then be made to shops.shopify.com to work out the IP address.  

**MX Record**
These records resolve to the address of the servers that handle the email for the domain you are querying, for example an MX record response for tryhackme.com would look something like alt1.aspmx.l.google.com. These records also come with a priority flag. This tells the client in which order to try the servers, this is perfect for if the main server goes down and email needs to be sent to a backup server.

**TXT Record**
TXT records are free text fields where any text-based data can be stored. TXT records have multiple uses, but some common ones can be to list servers that have the authority to send an email on behalf of the domain (this can help in the battle against spam and spoofed email). They can also be used to verify ownership of the domain name when signing up for third party services.

## Making a DNS Request

0. The first thing that your computer does is check its local "**_[Hosts](https://www.ionos.co.uk/digitalguide/server/configuration/hosts-file/) File_**" to see if an explicit IP->Domain mapping has been created. This is an older system than DNS and much less commonly used in modern environments; however, it still takes precedence in the search order of most operating systems

1. When you request a domain name, your computer first checks its **local cache** to see if you've previously looked up the address recently; if not, a request to your Recursive DNS Server will be made. 

2. A **Recursive DNS Server** is usually provided by your ISP, but you can also choose your own and companies such as Google and OpenDNS also control recursive servers.  
   Details for a recursive DNS server are stored in your router or computer.
   
   This server also **has a local cache of recently looked up domain names**. If a result is found locally, this is sent back to your computer, and your request ends here (this is common for popular and heavily requested services such as Google, Facebook, Twitter). 
   If the request cannot be found locally, a journey begins to find the correct answer, starting with the internet's root DNS servers.

3. The **root servers** act as the DNS backbone of the internet; their job is to redirect you to the correct Top Level Domain Server, depending on your request. If, for example, you request [www.tryhackme.com](http://www.tryhackme.com/), the root server will recognise the Top Level Domain of .com and refer you to the correct TLD server that deals with .com addresses.
   Before 2004 there were precisely 13 root name DNS servers in the world. These days there are many more; however, they are still accessible using the same 13 IP addresses assigned to the original servers (balanced so that you get the closest server when you make a request).

4. The **TLD server** (Top Level Domain) holds records for where to find the authoritative server to answer the DNS request. 
   Top-Level Domain (TLD) servers are split up into extensions. So, for example, if you were searching for tryhackme**.com** your request would be redirected to a TLD server that handled `.com` domains.
   
    As with root name servers, TLD servers keep track of the next level down: _Authoritative name servers_. When a TLD server receives your request for information, the server passes it down to an appropriate Authoritative name server.

5. An **authoritative DNS serve**r is the server that is responsible for storing the DNS records for a particular domain name and where any updates to your domain name DNS records would be made. Depending on the record type, the DNS record is then sent back to the Recursive DNS Server, where **a local copy will be cached** for future requests and then relayed back to the original client that made the request. DNS records all come with a **TTL (Time To Live)** value. This value is a number represented in seconds that the response should be saved for locally until you have to look it up again. Caching saves on having to make a DNS request every time you communicate with a server.
   
   The authoritative server is often also known as **the nameserver** for the domain. For example, the name server for [tryhackme.com](http://tryhackme.com/) is [kip.ns.cloudflare.com](http://kip.ns.cloudflare.com/) and [uma.ns.cloudflare.com](http://uma.ns.cloudflare.com/). You'll often find multiple nameservers for a domain name to act as a backup in case one goes down.

![[dns request response.png]]

## Practical example

`nslookup --type=CNAME subdomain.second_domain_name.tdl
Server: 127.0.0.53  
Address: 127.0.0.53#53  
Non-authoritative answer:  
shop.website.thm canonical name = shops.myshopify.com


## Dig
When you visit a website in your web browser this all happens automatically, but we can also do it manually with a tool called `dig` . Like ping and traceroute, dig should be installed automatically on Linux systems.

Dig allows us to manually query recursive DNS servers of our choice for information about domains:  
`dig <domain> @<dns-server-ip>`

Another interesting piece of information that dig gives us is the TTL (**T**ime **T**o **L**ive) of the queried DNS record. As mentioned previously, when your computer queries a domain name, it stores the results in its local cache. The TTL of the record tells your computer when to stop considering the record as being valid -- i.e. when it should request the data again, rather than relying on the cached copy.

It's important to remember that TTL (in the context of DNS caching) is measured in _seconds_.
