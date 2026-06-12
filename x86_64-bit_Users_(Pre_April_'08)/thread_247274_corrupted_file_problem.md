---
title: "corrupted file problem"
date: 2006-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrw on 2006-08-30
This one has me baffled. I tried to change permissions to allow user access to my Epson scanner. Somehow some files got corrupted and I'm at a loss of how to correct the problem. The files are located in /proc/bus/usb/. It turns out the same files (not corrupted) are also located in: /dev/bus/usb/. The files are "x-Special/device-char" fiies. I've been trying to copy the uncorrupted files into the /proc/bus/usb directory but nothing works. I've logged in as root in the terminal console as well as work directly from the prompt (desktop off). The /proc/bus/usb/ directly seem protected in some way that I can't overwrite, rename or delete. I've also tried to access the files from and overwrite from my Windows partition (dual boot system) but from there no files show at all in the directory. The consequence of the corrupted files is that I can't access my scanner from user or sudo but only if I login as root.
Does anyone have any advice of how to regenerate these files.

---

### Post by mrw on 2006-08-30
Problem fixed.

---

