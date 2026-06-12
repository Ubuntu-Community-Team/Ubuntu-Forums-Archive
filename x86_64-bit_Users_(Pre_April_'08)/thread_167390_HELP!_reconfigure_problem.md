---
title: "HELP! reconfigure problem"
date: 2006-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by MrFrodo on 2006-04-28
I was am in the process of doing this:

sudo dpkg-reconfigure xserver-xorg

when I got, at the bottom of the screen, a warning message about overwriting and a backup path was displayed followed by a prompt:

username@password:~$ 

What does it want me to do?! :confused: 

Unfortunately while making attempts, It asked me if I wanted to "Display all 1646 possibilities? (y/n)" and I now can't see the original warning message.

HELP!

---

### Post by MrFrodo on 2006-04-28
OK, I am back to the message. Here it is:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.200604280953

then a prompt of username@password:~$


WHAT DO I DO??!!!??!?!?!:confused:

---

### Post by jazzmuzik on 2006-04-28
It sounds like you successfully reconfigured the file that controls the graphical user interface, /etc/X11/xorg.conf, and the process created a backup file for you: xorg.conf.200604280953. 

When the reconfigure script is finished it sends you back the user prompt. I'm not sure what the password prompt is for. But you do need to run the script in sudo mode.

At this point you can look at the newly created file:

more /etc/X11/xorg.conf

If you want to start up the GUI, depending on the mode you are in, you can reboot, or at the text prompt -- assuming you are logged in -- you can type 'startx' to see if GUI mode works.

---

### Post by MrFrodo on 2006-04-28
Well, I'm back up... i guess... but my mouse wheel isn't working. Any help with this?

---

### Post by ajgreeny on 2006-04-28
Sounds as though you gave your computer the name on installation of ubuntu.  Confusing but not a disaster.  See what happens when you reboot. If you did all things right you should boot into your chosen desktop.

---

### Post by MrFrodo on 2006-04-28
I rebooted. Still no mouse wheel. Do I need to re-do xorg.config again? If so, can I stop after the mouse config without going through all the rest again?

TIA

---

### Post by jazzmuzik on 2006-04-28
I did run the xorg.conf reconfigure program but only about twice. As I recall I could just accept the default values and everything worked for me. I don't know what to tell you.

---

### Post by mistypotato on 2007-01-10
Thank GOD I do regular MondoArchive backups :-D 

Otherwise I'd be starting from scratch.

Been reading and trying for hours...time to just re-load from Mondo.

MONDO TO THE RESCUE !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

