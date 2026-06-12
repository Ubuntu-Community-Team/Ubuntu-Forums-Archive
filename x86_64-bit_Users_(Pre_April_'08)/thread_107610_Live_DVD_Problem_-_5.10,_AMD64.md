---
title: "Live DVD Problem - 5.10, AMD64"
date: 2005-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by eflynn00 on 2005-12-23
Hi, ran into a problem when using the LiveDVD (iso for 64bits) for the first time. I inserted the dvd, answered a few questions about language, keyboard, video and such. The live dvd boot was going well and then when it came time to start X I got an ATI video error. I am using an eMachine AMD64 T6212 it has an ATI Radeon Express 200 onboard video chip. 

I viewed the X logs and then tried to reboot my system. I removed the DVD in hopes of returning to my windows install but now the screen is blank. I reinserted the live dvd in hopes that it would try to boot from the dvd but still the blank screen. I do not hear any beeps or sounds when I start the computer now.

Any suggestions? The dystem does not seem to respond to any keyboard input and I am not sure if the system is booting at all, just a blank screen.
Thanks,
Earle

---

### Post by eflynn00 on 2005-12-23
I think I found a link that is similar to my problem. 
[http://ubuntuforums.org/showthread.php?t=103577](http://ubuntuforums.org/showthread.php?t=103577)

The only issue I have now though is that I can not boot my computer properly. When it starts now I do not see any bios screen or anything so I am not able to change boot options. Any suggestions?

---

### Post by eflynn00 on 2005-12-23
whew, ok, fixed it. 

My machine does not have a reset button on the front, or at least I have not found one if it does. Anyways, to cycle power I hold the power button for 4 secs. When I would do that the machine would turn on and off and appear to reboot but the reboot would not really happen. 

So, to fix my issue, I pulled the power cable from the back of the machine, waited a few seconds, and then plugged it back in. This time when I pushed the power button the bios screen came right back and I could choose to boot from the hard drive. Sweet.

Ok, now to figure out how to install the proper ATI drivers.
Earle

---

### Post by bonzodog on 2005-12-23
yeah, ATI based systems can be dodgy. 

Put up with getting kicked to a console, then alt+F2, to get a login: prompt. login with the 'ubuntu' user name and repeat it for the password.then, sudo nano /etc/X11/xorg.conf, and change the line with:

Driver "ATI" to say "vesa" instead.  save the file.

Issue the command:

sudo /etc/init.d/gdm restart

That should get you a working X.

---

