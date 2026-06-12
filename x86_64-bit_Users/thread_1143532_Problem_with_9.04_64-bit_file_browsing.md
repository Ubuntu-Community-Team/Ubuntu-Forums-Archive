---
title: "Problem with 9.04 64-bit file browsing"
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by numanahsan on 2009-04-30
Hi All,

I have just upgraded to 9.04 64-bit desktop from 8.10 64-bit desktop version. But now whenever i try to browse my hdrive in any application (be it firefox, openoffice or any other) by clicking on 'File->Open' or 'File->Save As' etc, the application goes grey and takes a very long time to come back to normal. nautilus is working fine.
Can anybody help me out here?

Regards,
Numan

---

### Post by bford16 on 2009-04-30
I can't guess why your applications are hanging in that way, but I can offer a suggestion.  Try the Open or Save As... operations with gedit (Text Editor). If you get the same behavior, then try the same experiment from within a terminal.  What this will do (hopefully) is reveal whatever error messages may appear when the hanging behavior happens.

---

### Post by tuga on 2009-05-01
I am having the same issue with firefox (it turns grey) when browsing some web pages (disney.com). Already reinstalled forefox ad flash plug in. My system is running 9.04 x4.

---

### Post by siylence on 2009-05-01
I'm having the same exact issue.

---

### Post by SukiSuki on 2009-05-02
> **bford16 said:**
> I can't guess why your applications are hanging in that way, but I can offer a suggestion.  Try the Open or Save As... operations with gedit (Text Editor). If you get the same behavior, then try the same experiment from within a terminal.  What this will do (hopefully) is reveal whatever error messages may appear when the hanging behavior happens.

I've got the same problem, also just upgraded from 8.10, and i'm not using the 64 bit version

No errors pop up when I hit file->open in a Gedit that I called from the terminal, it just takes 15+ seconds before the dialog box appears.

Python IDLE, Scilab, Freeciv all use non-standard GUIs and are not having any truble..

anyone have any other clues?

---

### Post by SukiSuki on 2009-05-02
Relavent bug reports:

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/24383](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/24383)
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/229539](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/229539)

the second one leads to:

[http://bugzilla.gnome.org/show_bug.cgi?id=569444](http://bugzilla.gnome.org/show_bug.cgi?id=569444)

It turns out tracker is the problem: I un-installed then reinstalled mine and things are working normally again.

---

### Post by solvip on 2009-05-16
moving ~/.local/share/tracker to ~/.local/share/tracker.old solved my problem.
Can you confirm?

---

