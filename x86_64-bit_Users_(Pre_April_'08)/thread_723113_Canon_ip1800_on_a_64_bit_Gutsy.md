---
title: "Canon ip1800 on a 64 bit Gutsy"
date: 2008-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by tooCanad on 2008-03-13
Any suggestions on getting the 32 bit print  drivers to work on a 64 bit system?

Thanks

---

### Post by tooCanad on 2008-03-16
Bump

---

### Post by him610 on 2008-03-17
I am not sure how a Canon ip1800 interfaces to your system, but I was able to get my own Dell 1700n working with available printer drivers using CUPS from three different systems all using different flavors of _buntu, plus four XP systems. The only problem I experienced was with a 64-bit XP Professional system. 

It isn't difficult to do with Ubuntu, in fact, the printer setup using 64-bit Ubuntu 7.10 was the smoothest printer setup I have completed.

What have you tried so far?

---

### Post by tooCanad on 2008-03-17
I've looked at all of the printers using the same or similar ink cartridge: IP 2600; MP2600; MP140; MP210; MP 470; MX 300; IP2500; IP3200; MP160; MP510; and MP600 for delivered cups drivers that work on the canon.

No luck so far.

I've successfully got my 32 bit laptop printing just fine using drivers I found on the the web.  [http://hex1a4.net/xubuntu/howto.php?htid=04]("http://http://hex1a4.net/xubuntu/howto.php?htid=04")


The 32 bit drivers don't want to install on the 64 bit machine.

I've seen a post where someone has got the thing going on a 64 bit machine by calling / configuring cups in 32 bit mode. Unfortunately the poster prvided no details.

Any insights are appreciated.


TC

---

### Post by him610 on 2008-03-17
I don't know if this will help to solve your problem, but follow this thread to see where it leads.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Good luck.

---

### Post by tooCanad on 2008-03-17
Looks promising. I will let you know how it works out. I'll give it a try tonight.

Thanks

TC

---

### Post by tooCanad on 2008-03-19
No go on the force package.

Canon IP1800 appears to be a no go on the 64 bit machine. Not recomended for 64 bit Ubuntu.

---

### Post by tooCanad on 2008-03-20
Installed the 32 Bit version of Gutsy. 

Then loaded the Canon Ip1800 drivers from here [http://caletalinux.blogspot.com/2007/07/canon-ip1800-drivers-en-ubuntu-feisty.html]("http://caletalinux.blogspot.com/2007/07/canon-ip1800-drivers-en-ubuntu-feisty.html")

Everything seems to be good now.

---

### Post by leoh on 2008-04-03
Same problem over here. Any news about this, or still not working?
Is there any chance to use a universal driver? Any alternatives?

---

### Post by tooCanad on 2008-04-17
No go here, I've kept looking but the only out for me was to move to 32 bit Ubuntu.

There has been a modest performance degration, but still well within tolerable limits and I can print.

---

### Post by Jive Turkey on 2008-06-07
I love this guy:
> [http://hex1a4.net/xubuntu/howto.php?htid=04](http://hex1a4.net/xubuntu/howto.php?htid=04)

I will soon be trying to solve this problem on 8.04 & XP 64-bit, the 32-bit CUPS tweak sounds the most promising.  

Does anyone know if its possible to serve a printer that will print jobs from hosts that do not have a driver for the printer in question, say by passing postscript files or something?

I might just break down and get a supported printer when my ink runs out next time.

---

### Post by dedyisn on 2008-06-10
I Still have problem in Installing This Printer.

I'm Using Acer 4520, AMD 64*2.
is there any trick/way so i can get my printer work?

Thanks for the info.

---

