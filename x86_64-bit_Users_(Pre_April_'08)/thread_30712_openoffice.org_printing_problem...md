---
title: "openoffice.org printing problem.."
date: 2005-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by rsw on 2005-04-29
I have a printer set up in "System->Administration->Printing". In ubuntu 5.04 for 386 openoffice.org would have that printer listed in its "print..." dialog menu. However, in this x86_64 version of ubuntu & openoffice.org, there is only a "Generic Printer" in the print dialog box, and needless to say, it doesn't work.

The printer works when printing via Evolution, gedit, etc. (all of which list it specifically in their print dialog menus).

Any idea's on a fix? Thanks.

# dpkg -l | grep openoffice
ii  openoffice.org 1.1.3-8ubuntu2 high-quality office productivity suite
ii  openoffice.org 1.1.3-8ubuntu2 OpenOffice.org office suite binary files
ii  openoffice.org 1.1.3-3+1ubunt Debian specific parts of OpenOffice.org
ii  openoffice.org 1.1.3-8ubuntu2 Gtk UI Plugin and GNOME File Picker for Open
ii  openoffice.org 1.1+20040420-2 OpenOffice.org office suite help (English)
ii  openoffice.org 20030813-3ubun English (GB) hyphenation pattern for OpenOff
ii  openoffice.org 20030813-3ubun English (US) hyphenation pattern for OpenOff
ii  openoffice.org 1.1.3-8ubuntu2 English (US) language package for OpenOffice
ii  openoffice.org 1.1.3-8ubuntu2 English (US) Thesaurus for OpenOffice.org

---

### Post by yoyo on 2005-05-01
Had the same problem. 

Try going to System .. Admin .. User and Groups
Select Groups and your login
add cupsys to your group members

the generic printer should work

---

### Post by negatory on 2005-05-02
This hasn't worked for me...
Isn't it the other way around?Making me part of the cupsys group?But I haven't got the cupsys group just the user.
Any other sugestions?
Thanks

Pedro Carrico

---

### Post by Bob D. on 2005-05-02
Would using the OOo spadmin program help? It's the printer administration utility for OOo.

I've had to use it before to manually add installed printers into OOo. Should find a spadmin link in the File Browser you can double click to launch in /<your home>/.openoffice/1.1.3/ (at least in the 386 version of Ubuntu).

Bob

---

### Post by FluffyElmo on 2005-05-02
Sounds like the same problem we had with Warty64 here:
[http://ubuntuforums.org/showthread.php?t=16266](http://ubuntuforums.org/showthread.php?t=16266)

"As a workaround I've been printing to a file and sending it to the printer from the command line ( *lpr -P printername filename* )."

I haven't used Open Office lately, and hoped it had been fixed by now but I guess not?  :neutral:

---

