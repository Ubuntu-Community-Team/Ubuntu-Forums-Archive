---
title: "AMD64 on Dapper - Printer Setup Help Needed"
date: 2006-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by trogbot on 2006-07-20
I've installed Dapper Twice & still have the same problem with getting a printer set up locally on my box.](*,)   Cups is working weird also.  The printer shows installed; test print shows going to printer.  Cups jobs shows it completes, but nothing prints out on printer.:confused:   Cups Admin keeps asking for userid/pw and apparently does nothing...goes to blank page.  The printer is a HP Officejet & driver is hpijs.  Anyone have any suggestions?  I'm a newbie, so I may need detailed info.  If I can get my printer installed & working with Windows Clients on my home network....No More M$ Windows For ME!!!:mrgreen:

---

### Post by hajk on 2006-07-20
Network printer? USB printer? We really need more info on this to help...

---

### Post by trogbot on 2006-07-20
It's a usb printer.

---

### Post by hajk on 2006-07-20
> **trogbot said:**
> It's a usb printer.

Start Gnome-Printing-Manager: first delete the printer that you have 
installed (and that doesn't work). Then click on New Printer, it will probably show two entries for your printer -- choose the one shown in 
CAPITAL letters, which provides the HPLIP backend to CUPS, and accept 
the default hpijs driver offered.

You might also install the python-qt3 package, needed by the HP Toolbox programme; the Toolbox can be activated in the Applications -> Accessories 
-> AlaCarte menu.

---

### Post by trogbot on 2006-07-21
That worked this time:D , but don't understand why.  I had tried that a number of time previously.  The only diff this time was that it showed my printer in CAPS as you said.  Before I had to go through and choose Manufacturer, etc..  Very confused about what's going on with my setup:confused: What do I need to do to get my home network windows clients able to use this printer?  Thanks in advance for all the help.  Greatly appreciated!

---

### Post by trogbot on 2006-07-21
Just a bit more info.  Trying to set printer as Default/Share Published Printers, etc. through CUPS Admin via browser results in "Not Authorized" in error log](*,) What's going on?  Help plz!

---

### Post by hajk on 2006-07-21
Yes, CUPS and HP have a strange interaction...
 
Administering CUPS via the browser ([http://localhost:631](http://localhost:631)) has been disabled in Ubuntu, but can be restored by adding yourself (user) to the group shadow.

I'm not really familiar with how to share a USB printer on a network with Windows computers... you have to run SAMBA, I believe -- just search the forums. Good luck!

---

