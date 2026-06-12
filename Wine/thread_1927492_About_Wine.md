---
title: "About Wine"
date: 2012-02-18
forum: Wine
---

### Post by SkyLinePH on 2012-02-18
I removed wine but it remain its folder in applications, how can i totally removed it.

PS.

Does virus from wine can affect Ubuntu OS?

---

### Post by howefield on 2012-02-18
Thread moved to the "*Wine*" forum.

---

### Post by ajgreeny on 2012-02-18
Simply delete the hidden .wine folder in your /home and it's all gone.

Uninstalling any application or package never ever removes the configuration in any user's /home, only the configs in /etc and other system folders.

---

### Post by SkyLinePH on 2012-02-18
I already deleted it Sir, but the wine folder still appears in the application tab. :(

---

### Post by SkyLinePH on 2012-02-18
Any feedback?

---

### Post by Toz on 2012-02-18
Look in ~/.local/share/applications.

If you've totally removed wine, you'll probably want to delete the wine folder (if one exists) and any wine* related desktop files.

---

### Post by ajgreeny on 2012-02-18
Sorry, are you talking about the menu system in your *ubuntu OS.  If so have a look in the menu-editor, alacarte.  I have no idea if it is available or whether it works in 11.10 unity, but I imagine there must be a way to remove applications from the menu system and/or dash.

---

