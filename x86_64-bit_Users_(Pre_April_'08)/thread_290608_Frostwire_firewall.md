---
title: "Frostwire firewall"
date: 2006-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by greyghostx on 2006-11-01
Hey, I've removed both firestarter and iptables from my system and still everytime I run Frostwire it shows that a firewall is detected and won't connect to the network. I contacted my ISP and they said that their is no firewall (I have a EVDO satllite card ran through my cellphone company), so are their any other firewalls on linux or something?

---

### Post by taurus on 2006-11-01
Do you happen to have a router?

---

### Post by rozojc on 2006-11-01
I'm having the same problem... A reply with some help would be appreciated...

---

### Post by taurus on 2006-11-01
> **rozojc said:**
> I'm having the same problem... A reply with some help would be appreciated...
Do you happen to have a router?

---

### Post by rozojc on 2006-11-01
Nope... I have a cable modem connected directly to the ethernet port of my laptop. I used Dapper before and frostwire worked perfectly...

---

### Post by cime on 2006-11-05
Same problem here.

---

### Post by rozojc on 2006-11-05
Interesting, seems like the only people reading this thread are the people who have this problem, and nobody is willing to help out...

---

### Post by bennie on 2006-11-06
I have the same problems. I solved it by installing limewire (same program). Limewire gives no problems:
[http://www.limewire.com/english/content/beta.shtml](http://www.limewire.com/english/content/beta.shtml) or
[http://www.limewire.com/english/content/downloadfree2.shtml](http://www.limewire.com/english/content/downloadfree2.shtml)

You can install the rpm by transforming it with alien to a debfile or using the tar.gz file (other). The beta works fine.

---

### Post by rxgod on 2006-11-10
Welp, if you want to run Limewire, the answer is obvious.  If you want to run Frostwire, you want to take a look at the contents of gnutella.net in your /home/user/.frostwire/ .  Compare that to your Limewire file of the same name.  Notice a difference?

---

