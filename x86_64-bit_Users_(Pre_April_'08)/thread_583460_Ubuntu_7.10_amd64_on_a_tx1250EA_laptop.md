---
title: "Ubuntu 7.10 amd64 on a tx1250EA laptop"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by tuscani20001 on 2007-10-20
Hello there, I'm a new member of the ubuntu forums as I'm a new user of the ubuntu os. My problem actually is that I cannot even get into the os. :(
I installed ubuntu 7.10 amd64 using unetbootin (I'm not gonna get more specific in to that as most of you already know what it is used for).
Now my problem is when I select to boot ubuntu my laptop stalls at "loading hardware drivers". I tried the ctrl+c method but then it stalls at setting the time or something like that. When I boot from recovery mode it shows that it actually stalls at eth0 no link during initialization.

---

### Post by ddrichardson on 2007-10-20
Which 7.10 are you using - 386 or 64? I have the 386 version running on a TX1250EA now.

You also need to append the following to the kernel (F6) at boot:```
noapic irqnodebug
```

---

### Post by tuscani20001 on 2007-10-20
I'm using 64 version. I will try that, I hope I will get it right....

Update:
How do I access kernel on boot? I pressed the F6 button several times but nothing happened.

Update2:
I think I managed to edit the kernel but the laptop still stalls at eth0 no link during initialization

---

### Post by tuscani20001 on 2007-10-21
anyone facing the same problem??

---

### Post by ddrichardson on 2007-10-21
There's a big post on the TX1000 series laptops [here]("http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000&page=2"). The 32 bit version works fine and there are still a few apps that are problematic under 64.

---

### Post by jit.sd on 2007-10-21
I have a similar problem . I just installed gutsy from a live cd onto my AMD turion 64 laptop and the live CD worked beautifully , but when i rebooted to start the OS from my HDD nothing happened . literally nothing happened . 

Grub loads , i ask it to start ubuntu , its shows hardware initializing and then poof blank screen !! nothing more nothing less , just a plain black blank screen . 

Am quite new at this , can someone please help . thanks !!

---

