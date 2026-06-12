---
title: "uTorrent : tray icon not appearing"
date: 2008-06-24
forum: Wine
---

### Post by XAVeRY on 2008-06-24
Hello there.
I've upgraded my Ubuntu 8.04 this morning, rebooted it, and found out that the tray icon of uTorrent doesn't show up anymore.

Any suggestions? Thank you in advance.
D.K.

---

### Post by Cup of Squirrels on 2008-06-24
Try going to winecfg and setting utorrent as an XP program.

Type 'winecfg' into your terminal, and go to the applications tab (will probably be there by default)

Click "add application" and look for the .exe you use to start utorrent. Back on the main applications list, highlight "utorrent.exe" (or whatever is used to start it), and at the bottom change the dropdown list to "Windows XP"


Otherwise, try this:

[http://ubuntuforums.org/showthread.php?t=295134](http://ubuntuforums.org/showthread.php?t=295134)

---

### Post by TenPlus1 on 2008-06-24
Different solution, but, have you went to [www.getdeb.net](www.getdeb.net) and tried a program called Deluge instead...  Looks and feels like uTorrent and is very fast indeed...

---

### Post by XAVeRY on 2008-06-24
I have already tried Deluge, actually, it was the first BitTorrent client that I've tried on my Ubuntu installation. I've used it for some time, but I was disappointed by how irresponsive and unstable this program was. Also, I felt that the performance was much lower than uTorrent's. I missed the *Labels* option, too, so I just came back to uTorrent, since I don't mind running Windows applications on Linux, especially those, which are excellently supported - and that's the case of uTorrent.

About the tray icon, I did what **Cup of Squirrels** advised and it appears to have been fixed. Thank you very much! :)

---

### Post by TenPlus1 on 2008-07-06
Just a quick note...   Dleuge has come a LONG way since lately and has a lot of new features and bug fixes, plus 0.60 is almost out which has a better gui and some ncie extras...

---

