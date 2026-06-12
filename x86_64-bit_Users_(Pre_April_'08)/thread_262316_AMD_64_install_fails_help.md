---
title: "AMD 64 install fails help"
date: 2006-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by riotnerd on 2006-09-21
Abit KN9-sli  amd X2

I have been unable to get the ubuntu or kubuntu 64 live cd to load on my system.  Once X starts the system hangs.

I have tried the safe mode gui also, check the Mem and the CD for errors. 

I have install a copy of XP for games but linux is my primary OS.
I know  [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=530&num=5") has had good luck with fedora 5 64bit.

I have used ubuntu for the last year and am very happy but I am down loading fedora 5 now.

Please help
Thanks

---

### Post by tymek666 on 2006-09-21
Have You also tried alternate CD?

---

### Post by riotnerd on 2006-09-21
No I have not tried the Alt install CD, but I am down loading it now.  I did read that suggestion. Thank you.

I have not used the Alt install CD before what should I down anything special during the Alt install?

Thank you

---

### Post by Kilz on 2006-09-21
> **riotnerd said:**
> Abit KN9-sli  amd X2

I have been unable to get the ubuntu or kubuntu 64 live cd to load on my system.  Once X starts the system hangs.

I have tried the safe mode gui also, check the Mem and the CD for errors. 

I have install a copy of XP for games but linux is my primary OS.
I know  [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=530&num=5") has had good luck with fedora 5 64bit.

I have used ubuntu for the last year and am very happy but I am down loading fedora 5 now.

Please help
Thanks

The alternate cd is the best for the 64bit version. But if you find Fedora works better for you , best wishes. Linux is one community, or at least it should be. :D

---

### Post by riotnerd on 2006-09-22
I have used the Alt Kubuntu 64 bit install.  I did install all the way though,

Now KDM starts but the system now Kernel panics 

not syncing: Aiee, killing interrupt handler!

any thoughts :confused: 

? I am unable to login at the KDM screen of in a tty session.

---

### Post by riotnerd on 2006-09-22
I Have tested Fadora Core 5 64 install it hangs when loading the firewall.

Anyone able to solve the kernal panic after install if Alt CD Kubuntu 64

---

### Post by riotnerd on 2006-09-25
I was able to install and run using the ubuntu 64 Alt cd.
The fix was setting the memory speed on my kn9-sli
to 533mhz NOT the auto setting of 667 for my 

No my system runs for about 10-15min in both windows and linux then reboots or freezes.

Any thoughts

---

### Post by John.Michael.Kane on 2006-09-25
Random system rebooting can be from kernel issues to hardware issues.

Is this machine overclocked?

Did it run completely stable under windows even during heavy gaming?

What are you complete system spec's? (what is listed in your sig is vague)

---

### Post by kuja on 2006-09-25
SD, looks to me like he was overclocking his RAM(autosetting or not), then s/he backed it off. 

Here's my recommendation though, if Linux is still very unstable, in Windows, run a nice little app named prime95. If your system fails within the first few hours with prime95's torture test, then this is most definitely a hardware problem.

---

