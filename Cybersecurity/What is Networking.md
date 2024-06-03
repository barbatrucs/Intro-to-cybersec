
In computing, a network can be formed by anywhere from 2 devices to billions. These devices include everything from your laptop and phone to security cameras, traffic lights and even farming!

## What is the internet ?

The first iteration of the Internet was within the ARPANET project in the late 1960s. This project was funded by the United States Defence Department and was the first documented network in action. However, it wasn't until 1989 when the Internet as we know it was invented by Tim Berners-Lee by the creation of the **W**orld **W**ide **W**eb (**WWW**). It wasn't until this point that the Internet started to be used as a repository for storing and sharing information, just like it is today.


![[the internet.png]]
As previously stated, the Internet is made up of many small networks all joined together.  These small networks are called private networks, where networks connecting these small networks are called public networks -- or the Internet! So, to recap, a network can be one of two types:  

- A private network  
- A public network

Devices will use a set of labels to identify themselves on a network, which we will come onto in the task below.

## Identifying devices on a network

Devices on a network are very similar to humans in the fact that they have two ways of being identified:
- An IP Address (our name)
- A Media Access Control (MAC) Address -- think of this as being similar to a serial number. (Our fingerprints)

**IP Addresses**
Briefly, an IP address (or **I**nternet **P**rotocol) address can be used as a way of identifying a host on a network for a period of time, where that IP address can then be associated with another device without the IP address changing. First, let's split up precisely what an IP address is in the diagram below:
![[ip address.png]]
An **IP** address is a set of numbers that are divided into four octets. The value of each octet will summarise to be the IP address of the device on the network. This number is calculated through a technique known as IP addressing & subnetting, but that is for another day. What's important to understand here is that IP addresses can change from device to device but cannot be active simultaneously more than once within the same network.

IP Addresses follow a set of standards known as protocols. These protocols are the backbone of networking and force many devices to communicate in the same language, which is something that we'll come onto another time. However, we should recall that devices can be on both a private and public network. Depending on where they are will determine what type of IP address they have: a public or private IP address.

A public address is used to identify the device on the Internet, whereas a private address is used to identify a device amongst other devices.
Public IP addresses are given by your **I**nternet **S**ervice **P**rovider (or **ISP**)

**IPv6** is a new iteration of the Internet Protocol addressing scheme to help tackle this issue. Although it is seemingly more daunting, it boasts a few benefits:

- Supports up to 2^128 of IP addresses (340 trillion-plus), resolving the issues faced with IPv4
- More efficient due to new methodologies

**MAC Address**es

Devices on a network will all have a physical network interface, which is a microchip board found on the device's motherboard. This network interface is assigned a unique address at the factory it was built at, called a **MAC** (**M**edia **A**ccess **C**ontrol ) address. The MAC address is a **twelve-character** hexadecimal number (_a base sixteen numbering system used in computing to represent numbers_) split into two's and separated by a colon. These colons are considered separators. For example, _a4:c3:f0:85:ac:2d_. The first six characters represent the company that made the network interface, and the last six is a unique number.

![[MAC address.png]]

However, an interesting thing with MAC addresses is that they can be faked or "spoofed" in a process known as spoofing. This spoofing occurs when a networked device pretends to identify as another using its MAC address. When this occurs, it can often break poorly implemented security designs that assume that devices talking on a network are trustworthy. Take the following scenario: A firewall is configured to allow any communication going to and from the MAC address of the administrator. If a device were to pretend or "spoof" this MAC address, the firewall would now think that it is receiving communication from the administrator when it isn't.

Places such as cafes, coffee shops, and hotels alike often use MAC address control when using their "Guest "or "Public" Wi-Fi. This configuration could offer better services, i.e. a faster connection for a price if you are willing to pay the fee per device.  The **interactive lab attached to this task** has been made to replicate this scenario!


## Basic Tools

### Ping (ICMP)
Ping is one of the most fundamental network tools available to us. Ping uses **ICMP** (**I**nternet **C**ontrol **M**essage **P**rotocol) packets to determine the performance of a connection between devices, for example, if the connection exists or is reliable.
`ping IP address or website URL`

The ICMP protocol works on the Network layer of the OSI Model, and thus the Internet layer of the TCP/IP model. The basic syntax for ping is `ping <target>`. 

Notice that the ping command actually returned the IP address for the target server that it connected to, rather than the URL that was requested. This is a handy secondary application for ping, as it can be used to determine the IP address of the server hosting a website. 
One of the big advantages of ping is that it's pretty much ubiquitous to any network enabled device. All operating systems support it out of the box, and even most embedded devices can use ping!

### Traceroute
Traceroute can be used to map the path your request takes as it heads to the target machine.
The basic syntax for traceroute on Linux is this: `traceroute <destination>`

By default, the Windows traceroute utility (`tracert`) operates using the same ICMP protocol that ping utilises, and the Unix equivalent operates over UDP. This can be altered with switches in both instances.


### Whois

Whois essentially allows you to query who a domain name is registered to. In Europe personal details are redacted; however, elsewhere you can potentially get a great deal of information from a whois search.

Just use `whois <domain>` to get a list of available information about the domain registration.

