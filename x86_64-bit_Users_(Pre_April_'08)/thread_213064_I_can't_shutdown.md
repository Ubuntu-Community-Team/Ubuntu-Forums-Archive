---
title: "I can't shutdown"
date: 2006-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by absurdist on 2006-07-10
I can't logout, shutdown or restart. The computer just goes to a black screen with 2 white squares(garbage), or displays the kubuntu logo with an empty status bar.  Nothing happens, so I have to force shutdown or restart. Shutdown from the command-line doesn't work either.
 
My setup:
kubuntu (dapper drake) for x86_64
ASUS P5P800-VM
Pentium D - 830
integrated graphics - intel 865G, i810 driver

Can anyone help me with this?  Thanks in advance.

---

### Post by mmarkvillanueva on 2006-07-11
i do have the same problem: [http://tinyurl.com/h6hyg](http://tinyurl.com/h6hyg)

any ideas

---

### Post by mmarkvillanueva on 2006-07-11
did you try shutting down using
sudo shutdown -h now
sudo halt ?

---

### Post by absurdist on 2006-07-11
> **mmarkvillanueva said:**
> did you try shutting down using
sudo shutdown -h now
sudo halt ?
Same problem.  I either get black screen with 2 white sqares, or black screen with kubuntu logo and empty status bar.  Computer will not shutdown.

---

### Post by mmarkvillanueva on 2006-07-12
i just tried SUSE 10.1 Live DVD. There is no shut down problem :(.
Is there a work around for this problem in ubuntu?

---

### Post by mmarkvillanueva on 2006-07-16
i added acpi=off as a boot parameter before booting the live cd.
There was no shutdown problem when i tried to log-off from GNOME. Except that it didn't shutdown automatically. I have to manually press the power button on the CPU. Any ideas?

---

### Post by absurdist on 2006-07-24
I really like my kubuntu, but I've still got this problem.  I'm pretty sure it has something to do with the i810 driver for xorg.  Anybody got a solution?

---

### Post by mmarkvillanueva on 2006-07-24
yep, I've tried running Ubuntu using the vesa driver and there's no shutdown problem. Have you tried using 855resolution?

Anyway I searched tons of threads, and most of their issues is that they cannot get accelerated graphics or they cannot obtained higher resolution. But I didn't see anyone experiencing our problem. :(

Any ideas?

---

### Post by absurdist on 2006-07-30
I posted a bug report on this problem:

[https://launchpad.net/bugs/54495](https://launchpad.net/bugs/54495)

If you're having the same problem, add your comments to the report.

---

### Post by mmarkvillanueva on 2006-08-08
check this out: 
[http://www.suseforums.net/index.php?showtopic=21690&st=0&#entry123197](http://www.suseforums.net/index.php?showtopic=21690&st=0&#entry123197)

thanks to pvh513. he found a solution to our problem!

---

### Post by absurdist on 2006-08-10
> **mmarkvillanueva said:**
> check this out: 
[http://www.suseforums.net/index.php?showtopic=21690&st=0&#entry123197](http://www.suseforums.net/index.php?showtopic=21690&st=0&#entry123197)

thanks to pvh513. he found a solution to our problem!

Hey that's fantastic! Now everything works.  Thanks for finding that, I'll add that soulution to my bug report.

---

