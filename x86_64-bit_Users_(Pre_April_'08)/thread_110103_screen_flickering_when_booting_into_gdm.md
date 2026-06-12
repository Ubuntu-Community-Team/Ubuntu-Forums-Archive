---
title: "screen flickering when booting into gdm"
date: 2005-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by linoox on 2005-12-30
Need some help here. Had installed successfully Ubuntu 5.10 on this G4. Was working fine until i thought of installing some java and Bluedragon server. Managed to install IBM's jdk 1.4.2 (as outlined on the wiki). Had some issues installing bluedragon server (but that's another issue for now in another thread until i get this fix). Not sure what i did but the next thing i knew, i wasn't able to get into the login screen (it seemed that gdm is rebooting itself again and again). I can't see the gdm login screen and the CRT monitor simply flickered away intermittently. 

Question, can i boot into a basic console and edit files or perhaps try running dpkg-reconfigure xserver-xorg without this annoying flickering problem? Thx

---

### Post by khc on 2005-12-30
Ctrl+alt+f1 will drop you to console

---

### Post by linoox on 2005-12-30
thx khc. tried that many times .. ctrl-alt-F1 only momentarily brings me back to console but it starts to flicker again. Luckily, just a minute again, i managed to stop the gdm service and somehow manage to fix it. 

sudo /etc/init.d/gdm stop

alright .. to the next problem. How to fix THE flickering problem once and for all?

---

### Post by linoox on 2005-12-30
running dpkg-reconfigure xserver-xorg doesn't fix the problem :(

---

### Post by linoox on 2005-12-30
also noticed the following while i click on ctrl-alt-f1 - sort of screen captures what i think reasons why the video flickers.

insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/bitblit.ko': No such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/font.ko': No such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/tileblit.ko': No such file or directory

and the list goes on (about 10 of them at least).

What should i do? pLease help ...

---

### Post by linear on 2005-12-30
I hate to say it, but could it be that either the java or Bluedragon install has hosed Ubuntu? Re-install may be the safest bet...

---

### Post by jmdennis on 2005-12-30
I get these same messages during the install and when my system turns on it flickers for a second and then it does to a non-graphical login and brings me to the $ sign prompt so if you have fixed this I would be intrested in knowing what you did.

[QUOTE=linoox]also noticed the following while i click on ctrl-alt-f1 - sort of screen captures what i think reasons why the video flickers.

insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/bitblit.ko': No such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/font.ko': No such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/tileblit.ko': No such file or directory

and the list goes on (about 10 of them at least).

What should i do? pLease help ...[/QUOTE]

---

### Post by khc on 2005-12-30
[QUOTE=linoox]thx khc. tried that many times .. ctrl-alt-F1 only momentarily brings me back to console but it starts to flicker again. Luckily, just a minute again, i managed to stop the gdm service and somehow manage to fix it. 

sudo /etc/init.d/gdm stop

alright .. to the next problem. How to fix THE flickering problem once and for all?[/QUOTE]

Sounds like X is failing to start and gdm keeps trying to restart it. I think after a while gdm will give up trying.

Can you post your /var/log/Xorg.0.log? Is your G4 a desktop, or a powerbook?

---

### Post by linoox on 2006-01-02
I'm going to try to get the log files tomorrow - probably via ftp to get it posted here. It's a G4 Desktop. I've read a couple of posts about reconfiguring for ATI Rage Pro 128 video card on this G4. Had tried some of those and it hasn't fixed the flickering problem yet.

Stopping gdm service remains the only thing that I know how to apply to prevent x-windows or gnome from restarting itself. I didn't know that Java could play a part in this problem. I kinda switched the default Java environment to the newly installed IBM Java version. Could that be a problem too?

---

