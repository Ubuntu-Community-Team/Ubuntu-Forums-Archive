---
title: "Any help with Citrix F5 networking for my companies VPN"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by Flexxall on 2008-05-05
Hey all,
I run my vpm currently through win ie7 on my xp box. Id love to run from my linux box but for Ubuntu Hardy fresh install I cant seem to get it runnin. Firefox gives me an error after logging into the firepass page and trying to load citrix NFuse I have tried installing the ICA client for citrix but im lost. I've googled and tried a few things but nothing is gettin me up and running. I'm running 8.04 64 bit if I need to switch to the 32 bit version i can but would like to get it running smooth in this install.

---

### Post by stankopp on 2008-05-12
The lack of a 64-bit AMD Citrix client is a deal-buster for me.  I am going back to Vista Business 64.  When there is more support for 64-bit Linux in general, maybe I'll be back (there is no 64-bit Opera either).

Done.

---

### Post by stankopp on 2008-05-15
I HAVE successfully installed the Citrix Presentation Server Client by following advice found in various threads in th Ubuntu fora.  My problem was that I had not installed the 32-bit libraries.

"sudo apt-get install 1a32-libs" got them for me.

Now on to Opera.

---

