---
title: "Ctrl + Click; Cmd + Click"
date: 2006-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Churusaa on 2006-05-09
This is the solution, so sayeth the prophecy.

To get the mouse to function as you're accustomed to it working in Mac OS_, do this:

Install mouseemu (this may involve un-restricting apt-get by opening /etc/apt/sources.list and removing the "#"s from the universe entries)

Run these commands as root:
[COLOR=Red]apt-get update
apt-get install mouseemu
vi [COLOR=Blue](or your editor of choice) [COLOR=Red]/etc/default/mouseemu
[/COLOR][/COLOR][/COLOR]
Edit /etc/default/mouseemu so that it looks like this:
[COLOR=DarkOrchid]```
# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default. 
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


MID_CLICK="-middle 125 272"         # Cmd key + Click
RIGHT_CLICK="-right 29 272"        # Ctrl key + Click
#SCROLL="-scroll 56"              # Alt key (default)
TYPING_BLOCK="-typing-block 100" # block mouse for 100ms after a keypress
``` 
[/COLOR]Save, exit, and reboot.  Voila!
---Churusaa

---

