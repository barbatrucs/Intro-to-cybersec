oThe TCP/IP model is, in many ways, very similar to the OSI model. It's a few years older, and serves as the basis for real-world networking. The TCP/IP model consists of four layers: Application, Transport, Internet and Network Interface. Between them, these cover the same range of functions as the seven layers of the OSI Model.

![The layesrs of the TCP/IP model: Application, Transport,Internet, Network Interface](https://muirlandoracle.co.uk/wp-content/uploads/2020/02/image-4.png)

_**Note:** Some recent sources split the TCP/IP model into five layers -- breaking the Network Interface layer into Data Link and Physical layers (as with the OSI model). This is accepted and well-known; however, it is not officially defined (unlike the original four layers which are defined in RFC1122). It's up to you which version you use -- both are generally considered valid._  

You would be justified in asking why we bother with the OSI model if it's not actually used for anything in the real-world. The answer to that question is quite simply that the OSI model (due to being less condensed and more rigid than the TCP/IP model) tends to be easier for learning the initial theory of networking.  

The two models match up something like this:
![Comparison between the TCP/IP and OSI models.](https://muirlandoracle.co.uk/wp-content/uploads/2020/02/image-3.png)
![Comparison between the TCP/IP and OSI models.](https://muirlandoracle.co.uk/wp-content/uploads/2020/02/image-3.png)

![[iso-tcp models comparison.png]]
The processes of encapsulation and de-encapsulation work in exactly the same way with the TCP/IP model as they do with the OSI model. At each layer of the TCP/IP model a header is added during encapsulation, and removed during de-encapsulation.

A layered model is great as a visual aid -- it shows us the general process of how data can be encapsulated and sent across a network, but how does it actually happen?

When we talk about TCP/IP, it's all well and good to think about a table with four layers in it, but we're actually talking about a suite of protocols -- sets of rules that define how an action is to be carried out. TCP/IP takes its name from the two most important of these: the **T**ransmission **C**ontrol **P**rotocol (which we touched upon earlier in the OSI model) that controls the flow of data between two endpoints, and the **I**nternet **P**rotocol, which controls how packets are addressed and sent. There are many more protocols that make up the TCP/IP suite; we will cover some of these in later tasks. For now though, let's talk about TCP.

As mentioned earlier, TCP is a _connection-based_ protocol. In other words, before you send any data via TCP, you must first form a stable connection between the two computers. The process of forming this connection is called the _three-way handshake_.

When you attempt to make a connection, your computer first sends a special request to the remote server indicating that it wants to initialise a connection. This request contains something called a _SYN_ (short for _synchronise_) bit, which essentially makes first contact in starting the connection process. The server will then respond with a packet containing the SYN bit, as well as another "acknowledgement" bit, called _ACK_. Finally, your computer will send a packet that contains the ACK bit by itself, confirming that the connection has been setup successfully. With the three-way handshake successfully completed, data can be reliably transmitted between the two computers. Any data that is lost or corrupted on transmission is re-sent, thus leading to a connection which appears to be lossless.

[[Packets & Frames]]


## Control Bits


[Resource](https://www.baeldung.com/cs/tcp-protocol-syn-ack#control-bits)

As a rule, every TCP request and response packet starts with a header segment that contains critical information like Source Port, Destination Port, Packet Sequence Number, Packet Acknowledgement Number, Data Offset, Window Size, Checksum, and Flags. Our TCP client needs to make a connection, and with this purpose in mind, **we’ll utilize the flags available to us in the packet header:**

![tcp header segment](https://www.baeldung.com/wp-content/uploads/sites/4/2021/02/tcp-header-segment.svg)

Specifically, we’ll need the SYN flag and ACK flag. These flags are bits that are in the header, set to on with the value of 1 or off with the value 0. **Ultimately, flags are how TCP clients and servers determine what to do with a packet they have received and how to respond.** So let’s see how we use the SYN flag to make our connection.
