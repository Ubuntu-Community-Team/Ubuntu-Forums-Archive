---
title: "Anyone using Ypops through Wine?"
date: 2008-09-18
forum: Wine
---

### Post by theedudenator on 2008-09-18
I have been trying to get something to check my yahoo email.

I can get Ypops to run, but I think I am having problems with the ports.

I have it set to 127.0.0.1 in Thunderbird

---

### Post by hikaricore on 2008-09-18
Never heard of it, but here's the appdb page:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2544](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2544)

---

### Post by theedudenator on 2008-09-20
That site mentions Dcom95 and Dcom98.  Any clue what that is?

---

### Post by user2037 on 2009-04-30
Ypops 0.9.7.3 just worked for me with Wine 1.1.19. I had to increase the port number from the default 110 to something above 1024 as those are reserved (you can probably use them if you run as a privileged user like Root). Thunderbird Webmail uses 1110 for POP access.

Some messages are duplicated several times. It is not clear if it is an issue with Ypops, Wine, or the combination.

Freepops from the Jaunty repo (0.2.7) didn't work for me after running Freepops update (to update the Yahoo plug-in). Thunderbird's Webmail also hasn't worked well for receiving mail from Yahoo.

---

