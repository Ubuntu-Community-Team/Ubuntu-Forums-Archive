---
title: "Unable to add trash icon to panel following update"
date: 2009-09-22
forum: x86 64-bit Users
---

### Post by timgood on 2009-09-22
Following an update today my trash icon disappeared from the bottom panel and I am unable to add it back. I can add the icon to the desktop, but it does not seem to link to the deleted items folder. Any ideas? I've checked .local/share/Trash/files and can manually delete but no trash can.

---

### Post by timgood on 2009-09-22
This is really strange. I've added the Deleted Items icon to the Desktop and it appears OK. But clicking on it to open the folder results in Image Burning Setup appearing with an 'operation not supported' message. If I go to 'properties' I find 'type' as 'type unknown application octet/stream'. How have I broken my system?

---

### Post by timgood on 2009-09-22
Reinstallation of gvfs and nautilus resolved the problem (after a reboot)!

---

