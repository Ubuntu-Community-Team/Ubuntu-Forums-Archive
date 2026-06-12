---
title: "KDE 3.5 desktop not in my session list"
date: 2006-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bhawns on 2006-12-19
I did the aptitude update and the aptitude install Kubuntu but KDE is not in my session list after I log out and back in. Debian is in my application list with a lot of stuff which is great but I want to work with the KDE desktop. I need some advice on how to make this so.

Thanks

---

### Post by xopher on 2006-12-21
I dont know, since I've never used Kubuntu, but you could try this:

CTRL+ALT+F1, then ```
sudo invoke-rc.d gdm stop; sudo invoke-rc.d kdm start
```

This should start KDM instead of GDM, and with common sense, that should allow you to run KDE too :D

If I recall correctly, you can even change GDM to KDM from GDM settings, or login manager settings in gnome, as long as you have KDM installed that is..

Hope this'll get you somewhere.. :)

---

