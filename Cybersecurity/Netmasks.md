
## WHAT IS A NETMASK?

At its core, a netmask is a fundamental component of IP addressing. It acts as a filtering mechanism, separating an IP address into two distinct parts: the network address and the host address. By defining the netmask, we can determine which portion of the IP address represents the network and which portion identifies the devices within the network.

A netmask consists of 32 bits, typically represented in the dotted decimal notation, and is closely related to IP addresses. You can see a few examples in the image below.

The subnet mask is a more common term used to describe netmasks in the context of dividing networks into subnets. Both terms are often used interchangeably.

![netmask-in-article-3.jpg](https://teltonika-networks.com/cdn/extras/18115/netmask-in-article-3-840xAuto.webp)

## HOW DOES A NETMASK WORK?

To understand how a netmask works, it's crucial to understand the [binary](https://en.wikipedia.org/wiki/Binary_number) representation of IP addresses. In binary, an IP address consists of 32 bits, divided into four octets (groups of eight bits each). The netmask, also represented in binary, features a series of consecutive ones (1s) followed by consecutive zeros (0s).

By performing a bitwise AND operation between the IP address and the netmask, we effectively "mask" the host portion, leaving only the network address. This allows devices on the network to determine whether a target IP address is within their own network or should be routed to another network.