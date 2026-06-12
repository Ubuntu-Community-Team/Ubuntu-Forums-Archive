---
title: "Java accelarating AMD 64 Athlon"
date: 2005-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by megashake on 2005-11-21
Had been trying to install azureus following the instructions in the starter guide..
[http://ubuntuguide.org/](http://ubuntuguide.org/)
...it hadn't worked, there was java missing, should've searched the fourms first, found the solution of course...
[http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus](http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus)
..now it's installed and working. 

Running breexy x86 on an Fujitsu-Siemens Amilo(notebook) AMD 64 with 1GB RAM and ATI mobility radeon 9700.. Anyway azureus is now working but it's crippling the machine, when I start the app the fans start and there's literally nothing else I can do with the machine. I ran "top" from terminal and I can see Java running the CPU at 99%, why is it doing this?? I previously used azureus on an old desktop I had running Fedora Core and it worked like a charm..

I was also getting a NAT error when azureus testing for ports 6881-6889, I think this is an ISP problem as I have a modem provided by my job which might be preconfigured to close these ports :)

Anyway any idea on the java acceleration of the CPU? Other than that ubuntu rocks, just installed amarok, cool :)

---

### Post by nalmeth on 2005-11-21
Very weird, thanks for passing on link...
I have azureus running on my AMD64, but I didn't do it anything like that. I'm simply using the 1.4 blackdown version of Java. I couldn't apt-get azureus, so I went to their website and downloaded the AMD64 tarball and run in right out of the box (folder) in my home folder, and everything works fine.
This might mean nothing to you, but if all you want from java is azureus, then you might want to try this way..
just an idea

---

### Post by RAOF on 2005-11-21
The thing that I would suspect is the problem is that you may not be using the Sun java runtime.  This sort of behaviour is what I got when I tried running azureus using the GNU java runtime :).
I'd check ```
sudo update-alternatives --config java
``` and make sure that the Sun java is the default.

---

### Post by megashake on 2005-11-22
Thanks! running..

sudo update-alternatives --config java

..sorted it. I'd noticed that the last part in the HowTo linked above..

sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java

..produced an error, Sun Java runtime is now selected and azureus runs as normal, now all I have to do is dort out a NATS and firewall error, oh well, its a start!

---

