---
title: "Wireless internet problem (almost fixed)"
date: 2006-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fredd191 on 2006-07-16
Hello everyone,

I'm a fairly new Linux user, and I already tried a number of distro's but very few supported my D-Link DWL-G520+ card, until now I found Ubuntu. 
Before you stop reading thinking "not another whiner with a D-Link card", I almost got this problem solved, just one more issue and it should be working fine.

I set up my network card with the graphical interface in System -> Administration -> Networking, these are the properties:

Network name: Topcom
Key Type: Hexadecimal
WEP key: *my WEP key*

Configuration: Static IP address
IP address: 192.168.1.3
Subnet mask: 255.255.255.0
Gateway address: 192.168.1.1

I set up the DNS servers my ISP uses, configured my router (Topcom Wireless Webr@cer 1154G+) from another computer to recognize the static IP I set and it seems to work locally: I can ping other computers on the same router (my fathers laptop).
But when I click the "Getting Started" bookmark, FF's status bar shows me "Looking up www.mozilla.com..." for a minute or so, and after that FF tells me this: "Server not found // Firefox can't find the server at www.mozilla.com." 
When I type in an IP address (e.g. Google's IP 66.102.9.104), I get this error: "Unable to connect // Firefox can't establish a connection to the server 66.102.9.104."

Does anyone know what I'm doing wrong and maybe how my problem can be fixed? I can't wait to start using Linux as a good second OS but I strand every time when I try to connect to the internet.

Thanks in advance

Frederik Druyts, Belgium

(sorry if my English is bad)

---

### Post by Fredd191 on 2006-07-17
Nobody who can help me?

---

### Post by igb on 2006-07-17
> **Fredd191 said:**
> Hello everyone,


Network name: Topcom
Key Type: Hexadecimal
WEP key: *my WEP key*

Configuration: Static IP address
IP address: 192.168.1.3
Subnet mask: 255.255.255.0
Gateway address: 192.168.1.1



Have you tried with no encryption, just to eliminate that as a source of the problem? Is your gateway address correct? If you can see computers on the local network, but not the Internet it suggests a routing problem.

Ian.

---

