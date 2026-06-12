---
title: "x64 vs. i386"
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by vollkommenegal on 2008-06-12
Hello.

I am working on a web based system. There is a communication part between me (web server / PHP) and a machine through Sockets. (Sending telegrams in XML)

Using Ubuntu 8.04 i386: Everythings works fine.

Using Ubuntu 8.04 x64: No telegram receiving from the machine. Tried iptables and everything. Nothing helped.

Any suggestions what to do?

THX for help

P.S.: Sorry for my bad english.

---

### Post by Cappy on 2008-06-12
I don't understand what program is running on the 64-bit Ubuntu that isn't working properly. If it is a 32-bit program you would need to use
[CODE]sudo apt-get install ia32-libs lib32nss-mdns[/QUOTE]

---

