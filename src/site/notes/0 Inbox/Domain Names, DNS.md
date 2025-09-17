---
{"dg-publish":true,"permalink":"/0-inbox/domain-names-dns/","created":"2023-12-05T18:48:49.716+07:00","updated":"2025-09-17T11:37:18.419+07:00"}
---

![Pasted image 20231205184905.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020231205184905.png)
we read from right to left

you cannot buy a domain name, but you buy the right to use it.
registrars use domain name registries to keep track of technical and administrative information connecting you to your domain name

**DNS Refreshing,** whenever your registrar creates or updates any information for a given domain, the information must be refreshed in every DNS database. Each DNS server that knows about a given domain stores the information for some time before it is automatically invalidated and then refreshed. Thus, it takes some time for DNS servers that know about this domain name to get the up-to-date information.

![Pasted image 20231205185414.png|425](/img/user/3%20Resources/Attachment/Pasted%20image%2020231205185414.png)

![DNS Process.png|500](/img/user/3%20Resources/Attachment/DNS%20Process.png)

You can learn more about DNS in https://howdns.works/

## Summarizing howdns.works

- Browser check for the IP address in the cache, it then ask the OS.
- Found nothing? It then ask resolver for the address (**Resolver** is actually DNS Resolver Server ISP)
- Resolver don't know the answer but knew where the **Root** is 
	- Root server sits at the top of hierarchy, **it know all the top-level domain server of each domain (.com, .org, .net)**
	- After resolver acquired the location of TLD domain server, it saves the location so it doesn't need to ask root again
	- ICANN are the one who coordinate all top-level domains (TLDs)
- Resolver then go ask the TLD domain server
	- TLD Domain server, with a help of **Domain Registrar** allow the TLD domain server to point to the **authoritative name server** (โดยแนบ ip-address ของ nameserver เข้ามาด้วย เรียกว่า **glue record**)
	- There are multiple authoritative name server to distribute the workload.
	- Authoritative name server knew everyone about the domain, website, e-mail etc.
	- use **WHOIS** to find the name server
- Resolver acquired the ip-address, it then save it to the cache

![DNS Pattern.png](/img/user/3%20Resources/Attachment/DNS%20Pattern.png)
The problem is, we can't get a subdomain without getting the domain first.
The solution is **glue record**. Simply, when the resolver ask TLD Server about the address, **the respond was attached with extra IP address** from TLD server for each authoritative name server. So the circular dependency has been broken.
![Pasted image 20241030112040.png|625](/img/user/3%20Resources/Attachment/Pasted%20image%2020241030112040.png)




## Summary
- OS จะเสิชในตัวเองก่อน ว่ามีมั้ย ถ้าไม่มีจึงถาม Resolver
	- Resolver = ISP
- Root = มีแค่ 13 เซิฟบนโลก ISP ทุกเจ้าต้องรู้จัก root
	- ROOT จะบอก TLD และ ISP ก็จะเซฟไว้จะได้ไม่ลืมว่า TLD นี้คืออะไร
- TLD จะบอก Authoritative DNS Server หรือ Name Server โดย ICANN เป็นผู้จัดการดูแล
	- TLD จะไม่รู้ไอพี แต่จะรู้ Name Server + Glue IP ติดมาด้วย
- Name Server
	- มีสองประเภท
		- A [**Primary name server**](https://www.cloudns.net/blog/primary-dns-server/) (also known as a **Master server**) stores the authoritative copies of all zone records. The DNS administrator is responsible for making changes to Master server zone records. All Slave Servers receive updates via the DNS protocol’s special automatic updating mechanism and maintain an identical copy of the Master records.
		- A [**Secondary name server**](https://www.cloudns.net/blog/what-is-secondary-dns/) (also known as a **Slave server**) is an exact replica of a Master server. We use it to distribute the load on the DNS server and to increase the availability of a DNS zone in the event of a failure ([DNS outage](https://www.cloudns.net/blog/what-is-a-dns-outage-dns-downtime-and-how-to-avoid-it/), DNS attacks, etc) of the Primary server. Furthermore, it is advisable for a domain to have at least two Slave servers and one Master server.
	- Name server จะรู้ว่าไอพีอะไร (อันนี้ อาจจะมีของ registrars, third-party หรือโฮสเองก็ได้)
	- **name server** does not host website data. Instead, it only handles the **DNS (Domain Name System) records** for a domain, mapping domain names to the IP addresses where the actual website or service is hosted.
- สุดท้ายจะได้ไอพีของเว็บไซต์จริง ๆ (web server)


Registra
![domain registra.png|525](/img/user/3%20Resources/Attachment/domain%20registra.png)
- Everyone who reserves a top-level domain name must fill out WHOIS information for that domain.
- Many registrars provide the option of a private registration. In this arrangement, the registrar’s information is provided in the WHOIS listing for that domain, and the registrar acts as a proxy for the registrant.
- registrar is a business that handles the reservation of domain names as well as the assignment of [IP addresses](https://www.cloudflare.com/learning/dns/glossary/what-is-my-ip-address/) for those [domain names](https://www.cloudflare.com/learning/dns/glossary/what-is-a-domain-name/).
- Registries are organizations that manage [top-level domains (TLDs)](https://www.cloudflare.com/learning/dns/top-level-domain/) ‘.com’ and ‘.net’ — specifically by maintaining the records of which individual domains belong to which people and organizations. Registries delegate the commercial sales of domain name registrations to **registrars**



![Pasted image 20241030112133.png|725](/img/user/3%20Resources/Attachment/Pasted%20image%2020241030112133.png)
ปล. ในภาพจริง ๆ recursive DNS server กับ authoritative dns server ต่างกันน้า

