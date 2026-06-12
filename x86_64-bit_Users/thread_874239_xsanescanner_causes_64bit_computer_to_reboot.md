---
title: "xsane/scanner causes 64bit computer to reboot"
date: 2008-07-29
forum: x86 64-bit Users
---

### Post by Craig P on 2008-07-29
I am an utter newbie to Linux. I'm using the Hardy Heron 8.04.01 distro for a new AMD 64bit machine, and I love most of the software. But I'm having trouble running my old scanner, a hp Scanjet 5300C. The xsane software recognizes the peripheral correctly, but when I try to get it to actually scan it either shuts xsane down, or even reboots my machine. I've read other threads, and tried what they suggested, namely re-installing xsane (no change) and installing xsane-extras (no longer recognized scanner, so I uninstalled) so I'm back to square one.

Any suggestions are appreciated!
Craig:confused:

---

### Post by cariboo on 2008-07-30
The first thing you have to remember is Linux is not Windows. If something doesn't work the way you expect it to, reinstalling it won't help. The first thing to check is to make sure you are a member of the scanner group, to do this go to System-->Administration-->Users and Groups. Click the unlock button and enter your password, Click Manage Groups and scroll down until you see scanner and highlight it, Next click properties and make sure there is a check mark beside your user name, then click OK, Click Close, then Click Close. Now log out and then log back in again. Xsane should now work.

Jim

---

### Post by Craig P on 2008-07-30
Dear Jim,
Thanks for your quick and helpful advice. I added myself as a member of the scanner group, then logged off and back on. Apparently this isn't the only problem, as I've tried scanning four times since, and three times the SANE has shut down, and once my computer re-booted. 

I've followed some of the help files. Using the terminal, I added  sane-utils, but when I run  $ scanimage -L  it doesn't find any scanners. And once when loading SANE, it didn't find any scanners.

Another oddity--my scanner light has been on since last night, even when my computer was off. Is there a way to see if the hardware is functioning properly? My scanner did have a rough few days with a move and a new workspace and new computer.

FYI, I'm using SANE version 1.0.19, with loaded backend avision:libusb:002 

Thanks again,
Craig

Edit: This gets stranger. Xsane no longer finds my scanner, but  scanimage -L does. I restart my computer, and  scanimage -L finds nothing, and Xsane originally finds nothing, but does (and finally gives me a window) after a minute or two.

---

### Post by c2b on 2008-08-20
I have the same problem with my Scanjet 5370C, which is supported. I followed the advice without success. My computer still restarts when I press the scan button in Xsane or want to insert a scanned picture in OpenOffice. I would appreciate some help.

---

