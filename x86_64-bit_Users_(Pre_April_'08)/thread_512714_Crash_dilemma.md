---
title: "Crash dilemma"
date: 2007-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by axelsvag on 2007-07-29
I need some advice for a dilemma I have been caught in.
 I got a amd64 x2 put in a htpc context with a 690G motherboard. I use feisty 64 bit with mythtv. The problem is that my x window crash at two occasions.
 First if I don´t use any ATI prop. driver the window fill the tvset perfectly but when I try to change the theme in mythtv settings, mythtv crash and go back to Ubuntu/Feisty login window. The same thing happens when I try to stop xine-ui. It also happens when I try to look at the news in mythtv. 
When I try to install the ATI prop. driver. Everything works perfectly but now the image don´t fill the tv set and leave big black bars in the top and bottom. Now when I change the themes the system don´t crash and I can watch the news freely. 
But.... now I can´t look at the movies if I have downloaded a cover with the imdb number. The system does a small crash and return to ubuntu/feisty. Now I ask if someone have any idea what I should do. I want to fill the complete screen as it do with the generic driver. And I want to look at news and change theme without crash.

---

### Post by qneill on 2007-07-30
Is mythtv crashing or is the XServer crashing?

Check the mythtv logs (usually /var/log/mythtv/mythfrontend.log  or /var/log/mythtv/mythbackend.log) if it is the former.

Check the X server logs otherwise (usually /var/log/Xorg.0.log)
-- 
Q

---

### Post by axelsvag on 2007-07-31
Thank for your answer

Ok I will look in the files  when I come home tonight

---

### Post by axelsvag on 2007-07-31
Check the mythtv logs (usually /var/log/mythtv/mythfrontend.log or /var/log/mythtv/mythbackend.log) if it is the former.


2007-07-31 16:51:48.719 MainServer::HandleAnnounce Monitor
2007-07-31 16:51:48.727 adding: aco-desktop as a client (events: 0)
2007-07-31 16:51:48.731 MainServer::HandleAnnounce Monitor
2007-07-31 16:51:48.731 adding: aco-desktop as a client (events: 1)
2007-07-31 16:52:32.812 MainServer::HandleAnnounce Monitor
2007-07-31 16:52:32.820 adding: aco-desktop as a client (events: 0)
2007-07-31 16:52:32.824 MainServer::HandleAnnounce Monitor
2007-07-31 16:52:32.824 adding: aco-desktop as a client (events: 1)

Check the X server logs otherwise (usually /var/log/Xorg.0.log)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

---

### Post by ahchong on 2007-07-31
eeiii.. what with all that prob? in what i know n belive is that Ubuntu and ATi have a bit conflict.
not conflict actually, only that what ive seen that when i installed the restricted ATi divers in my laptop in become more frequent to crash and return to login windows. Driver that ubuntu support for ATi is came from the community!!! and soem from other supporter in Ubuntu Comp.

---

### Post by axelsvag on 2007-07-31
Yes I understand that AtI and ubuntu don´t work together very good. Does the log give anyone a clue what is wrong. The best with this error is that it allways the same. Whenever I enter the the menu for video I get thrown out of mythtv. And as I sad when a use generic driver the error is different, but always repeatable.

---

### Post by axelsvag on 2007-07-31
Now I discovered one more clue to the riddle. If I use the catalyst control center and change from the default 800x600 to for example 720x576. And then go back to mythtv and enter the EPG mythtv crash and go back to ubuntu. It seem like the 800x600 is the only possible "resolution". Maybe it has something to do with mispalced "load preview video" window. Is this recognized??

---

