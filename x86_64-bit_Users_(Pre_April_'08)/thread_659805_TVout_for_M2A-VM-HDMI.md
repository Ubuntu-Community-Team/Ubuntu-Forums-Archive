---
title: "TVout for M2A-VM-HDMI"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by JayKav on 2008-01-06
I've been trying to get TV-out working for some considerable time and wondered if anyone has actually been able to do this.

System: Asus M2A-VM-HDMI with AMD X2 64 bit, X1250 integrated ATI graphics. Latest bios and HDMI is enabled in the bios.

What I have done:

(For each attempt I do a fresh install of Ubuntu 7.10 64 bit, update everything, enable all repositories)

1. Download and install ati-driver-installer-8.443.1-x86.x86_64.run

Result: Screen goes to a lower resolution (800x600). Catalyst control centre appears on menu but does nothing (won't start)

2. Install using the restricted drivers manager.

Result: Again a lower resolution display. 

3. [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

Low resolution display again. I got a message saying I was using a restricted driver.
fglrxinfo gives:

Xlib: extension "GLX" missing on display ":0.0"
...

(I had to manually modify the xorg.conf file as the aticonfig command caused a seg fault.)

4. Use Envy

At least this installs and I get the full resolution back. 

After installing the deb package, 'sudo apt-get install -f' didn't give any errors but Envy complained about missing dependencies and installed some more libraries. Don't know if this means something is going wrong.

Anyway, aticonfig appears not to work. All I get is 'bad file descriptor' for xorg.conf.



Any ideas? If what I'm trying to do is really impossible, it would be good to know as I can just go back to XP for the time being. I guess what I'm looking for is a step by step guide from a fresh install to having TVout working.

---

