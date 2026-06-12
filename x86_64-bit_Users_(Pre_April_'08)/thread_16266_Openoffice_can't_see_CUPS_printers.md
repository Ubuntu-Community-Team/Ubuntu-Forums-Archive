---
title: "Openoffice can't see CUPS printers"
date: 2005-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by tonym on 2005-02-20
My machine dual boots warty i386 and hoary amd64.  I print to a printer on a Windows 98 machine set up in both boot environments via Administration -> Printing -> New Printer.

The warty system works fine,  as does hoary amd64 in most applications eg kword.  However,  the printer does not show up in openoffice.  I've found a number of problems relating to openoffice and CUPS printing but most are old and don't seem immediately relevant.  Is anyone else having the same problem?

Regards

Tony Middleton

---

### Post by FluffyElmo on 2005-02-20
Yes, I have the same problem with a locally attached printer in Hoary amd64. AbiWord, KWord and other programs work fine. 

As a workaround I've been printing to a file and sending it to the printer from the command line ( lpr -P *printername* *filename* ). Hoping it will be fixed in an update eventually.

---

### Post by WW on 2005-02-20
You may be experiencing this bug:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1925](https://bugzilla.ubuntu.com/show_bug.cgi?id=1925)

---

### Post by tonym on 2005-02-22
[QUOTE=WW]You may be experiencing this bug:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1925](https://bugzilla.ubuntu.com/show_bug.cgi?id=1925)[/QUOTE]
 I had looked at that one and wasn't at all sure it was relevant.  I tried the entry in openoffice.conf it refers to but that didn't help.  After trawling through the trail of links it looked as if that sugestion was to turn off CUPS access anyway to avoid other problems.

I think I am going to wait for the next release before I try again.

---

### Post by GeBo on 2005-02-22
I also have that annoying problem.

Normally users can add a printer to OpenOffice.org by using spadmin, but that is also broken in Ubuntu... 

That workaround that FluffyElmo mentioned, is also the one I use. (Btw, if you use the default printer, you only have to type lpr *filename* on the command line.)

---

### Post by petunia_volubilis on 2005-03-02
any idea how workaround the spadmin thing ?

---

### Post by hva on 2005-06-13
I had already experienced this problem on debian sid i386 some time ago, but then it got fixed.
Since i've switched to Ubuntu for my new amd64 system i've met same old problem.
Until it get fixed you can work it out uninstalling openoffice.org-gtk-gnome package: it  made my cups printers show up in the printing dialog, even if openoffice will look a bit uglier.

---

### Post by uiteoi on 2007-03-07
After reading [_[COLOR="Navy"]bug #8662 (OpenOffice: can't print)[/COLOR]_]("https://launchpad.net/ubuntu/+source/openoffice.org/+bug/8662"), I successfully fixed the problem by adding the line:
[INDENT]**[COLOR="DarkRed"]export SAL_DISABLE_CUPS=1[/COLOR]**[/INDENT]
to the file:
**[COLOR="DarkRed"]/etc/openoffice/openoffice.conf[/COLOR]**

Because this file did not exist on my system (Ubuntu 6.06), I created the file with this single line to openoffice.conf. This could be done via the command:
```
[INDENT]**# [COLOR="DarkRed"]sudo echo 'export SAL_DISABLE_CUPS=1' >> /etc/openoffice/openoffice.conf[/COLOR]**
[/INDENT]
```

_**[COLOR="DarkBlue"]Note[/COLOR]**_: OpenOffice needs to be stopped before this takes effect. To stop OpenOffice one needs to close all OpenOffice windows - Databases, Spreadsheets, Presentations and Word Processors.

---

