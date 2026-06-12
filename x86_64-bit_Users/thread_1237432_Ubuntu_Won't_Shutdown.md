---
title: "Ubuntu Won't Shutdown"
date: 2009-08-11
forum: x86 64-bit Users
---

### Post by zjagannatha on 2009-08-11
Hi,

I recently bought a Toshiba Satellite with an Intel Centrino 2 64-bit Processor from a friend of mine. Originally, my first thought was to install Ubuntu x686 version to it, which worked perfectly. After further thought I install Ubuntu amd64. Until recently, it worked fine. Unfortunately, now it won't let me shutdown the computer. If I use the normal shutdown applet in the gnome-panel, it shows the Ubuntu closing screen, continues to shutdown until it shows a blank screen. The keyboard works fine, and anything I type will show up on the screen, but in order to have it continue shutting down I must press control-alt-delete and it gives me a message about restarting modules and then restarts. I encounter the same issue with restart, and I've tried (from the terminal)
```
sudo reboot
```
```
sudo init 6
```
```
sudo init 0
```
None of them work.
Thanks in advance for any help!

Information about my laptop:
Toshiba Satellite M300
```
uname -a
```
Linux zjagannatha-laptop 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:53:35 UTC 2009 x86_64 GNU/Linux

---

### Post by Sef on 2009-08-11
Check the power management setting in the BIOS.

---

### Post by zjagannatha on 2009-08-11
> **Sef said:**
> Check the power management setting in the BIOS.

I checked both BIOS and the Power Management settings in Ubuntu, there didn't seem to be an issue with either.

---

### Post by samurai_r on 2009-08-11
I observed the same issue in 9.04. Laptop ASUS U81A

Computer goes to sleep without problem but cannot be reboot or halted

I tried several ways

reboot
shutdown

Init 1

But did not achive positive result


Could anybody help me to resolve this problem

---

### Post by theZoid on 2009-09-07
I had problems shutting down or restarting with Jaunty x64, but soon found out it was Wicd causing the problem.  Went back to Networkmanager and the problem ceased.  Just another data point.

---

### Post by agh1 on 2009-09-10
I'm also having the same problem.  Another Toshiba, but with an AMD Turion X2 64-bit processor.  I'm going to play around with BIOS sometime soon, so I'll let you know if I figure anything out.

---

