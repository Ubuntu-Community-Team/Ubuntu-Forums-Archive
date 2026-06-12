---
title: "ATI Radeon 3870 driver trouble"
date: 2009-10-11
forum: x86 64-bit Users
---

### Post by Rainfallen on 2009-10-11
I recently (yesterday) switched to Linux 9.04 Jaunty. I tried installing ATI drivers from their website, and after much trouble, managed to install them, but upon reboot I got a black screen (I could type in my username and password, and it would make the 'start up' sound, but always completely black. 
So I went into recovery and somehow managed to repair the graphic drivers, and tried again, but this time with 64bit drivers (I'm unsure at this point whether or not the first were 64). The installation went much smoother, but I got the same result; black screen. Sighing, I quickly restarted and went to recovery, but there were now two Ubuntu selections to choose from, and two recoveries, one ending in .11-generic and the other in .15-generic, and I don't remember there being two before. They both seemed to do the same thing: I tried what I did before with the recoveries, but this time ubuntu didn't start back up. I get a message "kinit: no resume image, doing normal boot" and after that message, it gives me a terminal, and I always have to do a 'sudo shutdown now -r' to get out.

I'm royally stumped. Any takers? At this point just getting Ubuntu back up and running would be a godsend.
Thanks all.

---

### Post by Rainfallen on 2009-10-12
Thought'd I'd put an update up. I started up ubuntu with a LiveCD and went to Hardware Settings to install the proprietary drive there, hoping that would solve my problem, but ubuntu still still doesn't give me and GUI what-so-ever.

---

### Post by Yellow Pasque on 2009-10-12
This will get you back up and running: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

> I started up ubuntu with a LiveCD and went to Hardware Settings to install the proprietary drive there
This wouldn't do anything to your hard disk installation.

---

### Post by Rainfallen on 2009-10-13
I seem to have another problem. I tried the link and it still didnt work afterwards, but I doubt I did it right :p
So I just reinstalled ubuntu, installed correctly, and restarted all good. I tried doing the updates ubuntu suggested, but there was some 'jockey backend' problem, and it didn't go for some reason. So I tried restarting again, but this time I got the same exact error I had before: 'kinit: No resume image, doing normal boot...' 

I don't understand it. What keeps happening?

---

### Post by Pauly BC on 2009-10-14
I've been having similar troubles to Rainfallen, except sometimes the video driver also takes out my sound driver as well. This frustrates me because the ATI 3850/3870 was marketed very well and there are lots of them around. Installing the driver is neither simple nor straight forward, it seems to result in as many problems and benefits, plus for noobs the advice in the wiki is something you just follow blindly and hope for the best.

I can only hope and wish Catalyst is more smoothly integrated into Karmic, otherwise my Linux experiment will end with a Vista DVD. It sucks but it works.

---

### Post by Rainfallen on 2009-10-14
Pauly BC, does Linux start up for you? I used to get the 'login' screen, with the Ubuntu logo in the bottom right side of the screen, but now I only get a terminal (and that kinit message). 
I agree that there the documentation on codes for noobs is a shaky trail, as I am totally unfamiliar with Ubuntu and DO just follow blindly, hoping I'm getting it right. I can't even learn the coding if it will never even start up for me :confused:

---

