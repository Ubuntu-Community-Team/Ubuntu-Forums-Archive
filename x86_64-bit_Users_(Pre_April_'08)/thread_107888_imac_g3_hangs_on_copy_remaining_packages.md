---
title: "imac g3 hangs on copy remaining packages"
date: 2005-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by imacQ on 2005-12-24
the live cd worked fine after i changed the screen monitor settings in xorg.conf file via the vi editor (which i found out about by reading this forum :D ). imac g3 is 333mhz, 6gb tray loader; got it on ebay and pumped up the ram yesterday from 32 to 288. since the live cd worked fine i decided to install on hard drive and get rid of os 8.6 which was password protected by At Ease and i couldn't do a damn thing with it:rolleyes: . okay, so goes through install (used guided partions and contiguous free space) when it gets to copy remaining packages, and is up to 85% complete screen goes red and says "...failed. you may have run out of disk space in the target /var filesystem, or your cd drive maybe having problems reading packages from the cd. clean drive or burn at lower rate. i'm using "real cd" from ubuntu and i don't think it's the drive. goes on to say "check /var/log/syslog or see virtual console 4 for the details. :confused: how do i get to /var/log/syslog or the virtual console from within the install? i don't see these in the installer main menu? do i select execute a shell? if that's the case i have no idea what to do when i get there. what to do to make this work? suggestions greatly apprecaited :)

---

### Post by Rxke on 2005-12-24
virtual console: CTRL-ALT-F4

```
sudo nano /var/log/syslog
``` opens the log in nano (you could use vi, too of course)

How big is the partition you installed on, or did you use the whole drive?

---

### Post by imacQ on 2005-12-24
:confused:  should i hit abort and try the other ubutu install cd; i have 2 install cds? i ran check the cd roms integrity from main install menu, and it found a possible corrupt image file.

---

### Post by imacQ on 2005-12-24
THANK YOU rxke, i'm in virtual cause i hit alt f4, now what?

---

### Post by Rxke on 2005-12-24
maybe this one is a better answer:

[http://ubuntuforums.org/showthread.php?t=82076](http://ubuntuforums.org/showthread.php?t=82076)

---

### Post by Rxke on 2005-12-24
[QUOTE=imacQ]:confused:  should i hit abort and try the other ubutu install cd; i have 2 install cds? i ran check the cd roms integrity from main install menu, and it found a possible corrupt image file.[/QUOTE]

yes, if you have a good one, definitely...

and your other question, there's nothing in the virtual console #4?

then type ```
sudo nano... 
``` as mentioned above, and look what it says at the end.

But better retry with the good disc rightaway...

---

### Post by imacQ on 2005-12-24
yes, there was "stuff"  in log/sys. i couldn't get out of there though. so i took out the cd, put 2nd install cd in, and stuck the mac tool in the little hole hit c. now i'm installing again. we'll see. thank u! can i skip the configure the network, since i don't have a network?

---

### Post by Rxke on 2005-12-24
yes, it will try, though, but then after awhile you can select to do it 'later'

---

### Post by imacQ on 2005-12-24
gotten to remaining packages again and up to 72%. go my finger crossed this time :smile:

---

### Post by imacQ on 2005-12-24
SUCCESS! installed and checking it out. tomorrow i'll try to figure out how to get online. the 2nd cd worked without a clitch? whew glad i had 2 of them!

---

### Post by Rxke on 2005-12-24
[QUOTE=imacQ] tomorrow i'll try to figure out how to get online. [/QUOTE]

Oops... you said you didn't need networking, so I thought you were going to use it as a standalone computer... (in hindsight, that is in fact a bit of a misleading term: 'setting up network connection' ... You see, originally, Linux (and Unix) were biiig computers, working with terminals etc... they were almost always hooked up to the 'net via a network... Nowadays with personal computers, I see that can be a confusing term... 

But now worries, now you have it up and running, you can still set up your connection, via menu system/administration(not sure that's the right term, I'm Dutch... it's the icon with the computer...) and then select network...

---

