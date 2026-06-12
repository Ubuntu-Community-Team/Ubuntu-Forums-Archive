---
title: "Phenom 9850, 8gb ram, radeon HD, 64bit ubuntu. Problems making games work."
date: 2008-07-11
forum: x86 64-bit Users
---

### Post by mortexic on 2008-07-11
What Ive got:
Phenom 9850
8gb DDR2 800 ram
PCIE 16x Radeon HD (dont remember exact model #, its a newer 512mb one)
64-bit ubuntu Hardy Heron
proprietary ati driver installed via the gui

Ive read other forum posts about people successfully making wine/wow, doom3, ut2k4, etc all go on 64bit ubuntu but ive been continually unable to do so.

The doom3 installer fails, claiming the self-decompressing archive is missing setup.sh (tried 3 versions of the doom3 installer, all fail)

Trying to run wow-via-wine fails and gives me the wow-crash-reporter tool.

UT2K4 wont install, similar issues to the doom3 installer.

fglrx-gears works, and beryl gives nice drippy/gooey effects if I turn it on, so im rather sure 3d rendering is actually WORKING not just reporting "yes" to glxinfo ;-)


I'm non-noob and come from gentoo land, so im not scared of the CLI or anything. I havent been able to find much in the way of troubleshooting for games on 64bit ubuntu...


Also quick Q, im having trouble making dual-monitors work (one widescreen one 4:3), how do I know if I have installed the gui for the new ati catylist linux version?


Thoughts?
I'm a gamer, and this box is a powerhouse under xp pro 64 but I really dont want to have to reboot into windows anytime I want to get a game going.... :-\

---

### Post by dagrump on 2008-07-11
Well, I run doom3 & quake4 on Ubuntu w/o wine, loki has installers. I just used google for links. I play prey w/ wine, I don't have WOW but i was under the impression it ran great.
My machine is pretty close to your rig other than quadcore & nvidia, opposed to amd & ati. 
I hate to say it but I have never any luck with ATI cards & linux, I just got rid of one, to a windows using coworker as it left artifacts & tore moving windows or watching a movie.
I look for the native installers for ID games & see if you have better luck there, & as far as wine goes, it is what it is. 
there is more info on tweaking it than you could dig thru in a month. I'd borrow a nvidia card and try that, but the install issues shouldn't be related. Might reinstall wine & install wine-tools or wine-doors. Then there are always Nexis, OpenArena, AlienArena, etc...

---

### Post by Kilz on 2008-07-11
The 64bit part is not your problem if you have wine installed. Google and the [Wine application database ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329")are your friends.

As a side note, I wouldnt install the 8.6 ati drivers, they have issues with wine. I went back to the 8.5.

---

