---
title: "Can't connect to internet"
date: 2008-12-06
forum: x86 64-bit Users
---

### Post by Hellaxe on 2008-12-06
Hello people i'm getting furious with this.
Somehow this stupid installation with 2 days can't connect to the internet.
Yesterday was fine but today nothing happens. Emails, IM's nothing.
It's just if a firewall blocked everything but I don't have any rules in Iptables.
In the private network it works fine, only the internet fails and all it's services.
Another stupid thing: the network configuration applet is in the "Preferences" tab and not in "Administration" so I cannot change it from GUI. So no password is required and of course no changes are applied.
I had to dig in the interfaces file.
What are this guys from Cannonical doing. I think this is inadmissible. 
Help me please.

PS: I use Ubuntu for 3 years now and things like this never happened to me. The OS was always very stable.

---

### Post by Sef on 2008-12-07
What version of Ubuntu are you using?

---

### Post by Hellaxe on 2008-12-07
> **Sef said:**
> What version of Ubuntu are you using?

I had and still have Intrepid.
I re-installed today in the mourning because i needed the box working.
But I still need answers because that's not normal and I am curious.
Thanks for reply

---

### Post by marcelkoopman on 2008-12-07
You say you cant connect to the internet.

- are you able to ping?
- do you have a network adress? see ifconfig

---

### Post by Hellaxe on 2008-12-07
The private network worked very well without problems: samba, printing, etc.
Only the comunication to the internet and all it't services was broken.
Ping to outside my network was impossible however within the network was fine.
I made something on Friday: i've changed my hostname. But on that day the net worked without problems even after a reboot.
Was that incident caused by the changed os the hostname?
I was completly blind on that.
Thanks.

---

