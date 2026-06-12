---
title: "Uninstall a .exe with wine"
date: 2011-12-07
forum: Wine
---

### Post by Lalaith on 2011-12-07
Hi, 

I tried to uninstall MS Office 2007 from wine 1.2 but apparently it "can't find the C:/ (...) system32/uninstall.exe" file. I would like to remove MSOffice and wine 1.2, since apparently wine 1.3 + MS Office 2010 work better. 

How can I do it easily? (I don't mind using the terminal)

Thanks :)

---

### Post by oldos2er on 2011-12-07
Thread moved to Wine.

---

### Post by Tweak42 on 2011-12-07
I never completely trusted windows uninstallers even in native windows much less under wine.  They always left some clutter behind.  Best is to just nuke the wine prefix and start from scratch.  

A wine prefix is basically the directory where wine puts the emulated windows "c: drive".  Best practices is to put each program into separate prefixes, so individual programs don't step on each other, and can simple be uninstalled by deleting the directory.

The default wine prefix is in .wine directory in your home directory.  The . makes it hidden, so you need to show hidden files (ctrl-H) in the file manager to see it.

Google wine prefixes if you want to know more on using them.

Addendum: There will probably be some harmless menu entries left behind you need to manually remove.

---

### Post by Soulcage on 2011-12-08
Check out the faq [http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa]("http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa")

---

### Post by Lalaith on 2011-12-08
All your info was very useful.

Thanks a lot to all of you. =)

---

