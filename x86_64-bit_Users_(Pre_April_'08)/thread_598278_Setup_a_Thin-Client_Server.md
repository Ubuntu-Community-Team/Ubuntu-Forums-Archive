---
title: "Setup a Thin-Client Server"
date: 2007-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by yvijayakumar on 2007-10-31
I am new to Linux.
I need to setup a Thin-Client Server with ubuntu feity-fawn 7.04 (Free Installation Kit obtained). I installed the ltsp kit ([http://www.ltsp.org](http://www.ltsp.org)) on the ubuntu installation and removed the dhcp server object to obtain ip/static ip from windows server. 
The other local network machines are windows xp (I call these machines as clients) and I need to provide internet to all the local machines through Remote Desktop. For this purpose I setup the ubuntu machine.
My ubuntu machine has 2 network cards, one connected to internet and the other to local network using static ip. I can browse the internet from ubuntu machine but I cannot even ping to the windows clients.
How to solve the problems and enable the terminal services on ubuntu?

---

### Post by netbandit on 2007-10-31
You really got a lot going on here, and it might be a couple different issues.  I'm going to start on the basics:

Check your network configs.  You have 2 nic's and you probably need an address on each one.  Use ifconfig to see what you have.  Once the nic's are up, you should be able to ping the ubuntu box from the windows boxes.

-nb

---

### Post by timcredible on 2007-10-31
i haven't used ltsp, but I've used PXES before, and it's real easy.  You might want to try it.  I have a how-to/info article about PXES at [http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=22&Itemid=29](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=22&Itemid=29)

---

