---
{"dg-publish":true,"permalink":"/0-inbox/internet/","created":"2023-12-05T18:27:05.394+07:00","updated":"2025-10-05T15:02:55.946+07:00"}
---

Internet began from the US-army funded research project.

APRANET is the first public packet-switched computer network.

WWW is not an Internet, WWW manage documents, how it being sent, etc. but that rely on the connected hardware which is internet.

Information's are broken down and sent as multiple packets, each will find it own way to the destinations.

**Router** can be used to connect multiple computer.
We use **telephone infrastructure, since** it is the things that has been connected at the first time. 
It require a special piece of equipment called **modem** to turns the information into what is manageable by the telephone infrastructure and vice versa.

Fiber optics are made from fiber optic cables and does not require **modem**
However, cable (coaxial cables) and DSL (telephone wires) require **modem** since they have to convert from analog signal to digital signal.

Ethernet cable is preferred for direct device connectivity, such as LAN in a simple network.
ISP's manage special routers that are all linked together and can access other ISP's routers
![Pasted image 20231205183441.png|90](/img/user/3%20Resources/Attachment/Pasted%20image%2020231205183441.png) ![Pasted image 20231205183856.png|237](/img/user/3%20Resources/Attachment/Pasted%20image%2020231205183856.png)

Every machine in the network has **IP address** (IP = Internet Protocol), and we alias an IP address with a human-readable name called [[2 Areas/Programming/Web/Domain Names, DNS\|Domain Names, DNS]]

What happened when you open the website?
1. Clients look at DNS or cached-DNS for the real ip-address
2. Server return 200 OK message + it content
3. Browser parse HTML first, then send back any CSS found in `<link>` and JS found in `<script>`
4. The browser generates an in-memory DOM tree from parsed HTML and generate in-memory CCSOM structure from the parsed CSS, and compiles and executes the javascript.


**Host** is divided into
- client
- servers

**forwarding**
- forwarding the received packet to the destination according to the table
- use forwarding table
**routing**
- most famous: BPG
- use algorithm, automatically determine best way to reach the destination

**network protocol:**
- like a grammar of the internet
- will include header and the data
- TCP, UDP, IP, HTTP


![Internet-1.png](/img/user/3%20Resources/Attachment/Internet-1.png)


**TCP/IP STACK (conceptual framework that standardize the protocols used to communicate in the internet)**
- application layer
	- request and response
	- HTTP, SMTP, FTP
- transport layer
	- data transfer between application
	- data segmentation, transfer, data assembly
	- TCP reliable order delivery
	- UDP faster but less reliable
- network layer (IP)
	- handle addressing and routing of data packet
	- IPv4, IPv6
	- differ in the way of how data is packetized, addressed, transmitted, routed, received
- link layer
	- manages physical between device in the same network segments
	- deal with hardware aspect
	- network interface cards, device driver, ethernet, wifi 
