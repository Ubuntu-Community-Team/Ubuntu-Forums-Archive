---
title: "AMD64 using Non 64 bit Ubuntu"
date: 2006-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by tman_ubuntu on 2006-02-24
Is this possible?  Wasn't quite sure if I needed to install the x86_64 version of Ubuntu.  I have 64 bit architecture that I wanted to use as a small business server.  It seems as though all the 64bit versions of distributions are somewhat unstable so I would like to just use a non 64bit version of Ubuntu on a AMD64 architecture.  Is this possible or am I just off my rocker?

---

### Post by tekwarren on 2006-02-24
YES


None of the new Intel or AMD processors boasting x64 architecture "require" a 64bit operating system. Regular Ubuntu...or even one of the regular windows OS's will still work fine.

---

### Post by BoyOfDestiny on 2006-02-25
Yeah go for it... As for being unstable... I've yet to have dapper crash.

 uptime
 00:28:31 up 16 days, 20:33,  3 users,  load average: 1.30, 0.88, 0.36

I've rebooted a few times (due to kernel updates, etc), but if that's your only reason for avoiding 64-bit... I say give it a try...

If it's having more certainty about an app working or easy install of wine, flash, etc... then maybe 32-bit is for you. :)

EDIT: I just noticed this is the breezy section, well breezy64 was stable for me too. I had a problem with the open source 3d driver for my radeon 9250... issue is gone in dapper 64.

---

### Post by tman_ubuntu on 2006-02-25
Thanks for your replies.  I'll give dapper 64 a try.:D

---

### Post by Joe on 2006-03-01
What's the best kernel to use if you're using an athlon 64 cpu but running 32 bit?

Edit: Nevermind I guess I should be running the K7.

---

### Post by amosbatto on 2006-03-01
Personally, I don't think 64 bit Ubuntu is worth the trouble unless you have some special need for fast graphics processing or intense math.  Dealing with a 32 bit chroot environment is a real pain.  There are some unresolved bugs in the 64 bit Ubuntu. For instance, you can't copy plain text from one applicationa and paste it into OpenOffice.  The only way to do it, is to first paste it into a 3rd application which will give it formatting, then copy and paste the formatted text into OpenOffice.  Removing the strange formatting from AbiWord is another pain.  

My advice is to just use 32bit Ubuntu on your 64bit machine, unless you like fooling around with your machine.

---

