---
title: "acpi, syslog and modprobe"
date: 2007-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by moltke on 2007-11-08
I've recently installed Ubuntu 7.10 Server x86_64 and Ubuntu 7.10 i386 and I'm little bit disappointed.
Both were running fine until reboot.
First of all I had to turn off acpi in x86_64. This is strange because previously installed OpenSUSE x86_64 worked with acpi on.
Secondly, syslog couldn't start in BOTH (!) Ubuntu versions. I had to change syslog init.d script to run as root.
Thirdly, cups ddn't start in x86_64 because it hanged at [FONT="Courier New"]modprobe ppdev[/FONT].
I commented out this line and then it started.
However, now, I would like to install my multifunction printer (Samsung SCX-4200) and the driver requires ppdev. Also when I type (everything as root) [FONT="Courier New"]scanimage -l[/FONT] it hangs. I've figured out than problem is in modprobe. If I type [FONT="Courier New"]modprobe ppdev[/FONT] the terminal hangs. If i open onother terminal and execute [FONT="Courier New"]killall modprobe[/FONT], the module (ppdev) is loaded end everything works fine. Accordingly, killing modprobe few times after invoking scanimage, makes it unhang and work. The same is with printing. Loading other modules like lp also hangs, but strangely lp is properly loaded during cups startup. I haven't this problem on i386 version. The problem is also not in the kernel (because I've tried generic kernel too).
So what is going on? Is it a bug or I'm doing something wrong?

---

### Post by moltke on 2007-11-09
I've manageded to solve the problem with modprobe. The real problem was bad configured options of parport_pc module (they were configured by ubuntu installer, not by me).
I've commented out (with a #) the options line of the parport_pc module in /etc/modprobe.conf.
Then, other modules like lp and ppdev started to work.
Now, the printing and scanning works perfectly.
I think I'll have to live without acpi and with syslog running as root.

---

### Post by dren on 2008-04-22
Thanks for this post, it helped me out after my machine got screwed up by the Samsung Unified Driver.

After installing the Samsung Unified Driver, my machine hung on "Loading manual drivers..." during startup.  To get back up I had to load from the live CD and comment out rtc and lp from /etc/modules.  I still couldn't fully boot.  My machine hung while trying to load cups.  I had to ctrl+alt+f1 over to a text terminal and remove cups from my machine (it hung while the startup script tried to modprobe lp) before I could boot.

With your fix I was able to successfully get cups reinstalled.  Thanks a bunch.

---

