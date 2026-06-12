---
title: "Flash Problems"
date: 2006-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by tobeon on 2006-09-18
Hi, I cant seem to get Flash to install, I downloaded the player from the macromedia website (install_flash_player_7_linux) but I get this error

ERROR: Your architecture, \'x86_64\', is not supported by the Macromedia Flash Player installer.

can anyone help? (taking into account my lack of experience with linux!)
Thanks v much

Tom

---

### Post by amo-ej1 on 2006-09-18
flash player is a 32 bit applications which won't work on a 64 bit platform.

---

### Post by tobeon on 2006-09-18
so there is no way to get flash working? :'(

---

### Post by mrw on 2006-09-18
Download nspluginwrapper_0.9.90,1-2_amd64.deb and try it. It will install the 32-bit flash onto your 64-bit firefox

---

### Post by kez on 2006-09-18
There is an option involving nspluginwrapper, 64bit Firefox and Flash (see the sticky about getting specific apps to work at the top of this forum), but I have read there are apparently some stability problems with it.

You could try installing 32bit Firefox - it worked for me - using Kilz' script. As a bonus you can get Java and Mplayer plugins with it.

Follow the link below, save and extract the appropriate script to your desktop, and follow the instructions in the How-To and Read Me. The whole thread of that How-To is very useful, actually.

[Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64]("http://www.ubuntuforums.org/showthread.php?t=202537")

Hope this is of help to you. One of the things I like about Linux is the choice available.

---

### Post by tobeon on 2006-09-19
brilliant it all works great now, thanks very much!

---

### Post by acefreely on 2006-09-22
Where can one find nspluginwrapper_0.9.90,1-2_amd64.deb?

---

