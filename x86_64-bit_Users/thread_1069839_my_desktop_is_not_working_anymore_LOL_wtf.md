---
title: "my desktop is not working anymore LOL wtf?"
date: 2009-02-14
forum: x86 64-bit Users
---

### Post by Zaytoven on 2009-02-14
I had a computer freeze earlier this morning. I had to hard re-start and when i logged in my desktop stopped working. My wallpaper won't show up I can see any of the icons o have on my desktop. When i go to the desktop folder i can see them and use them but they are not on my desktop anymore. I have Ubuntu 8.10 by the way. This is a weird problem to have. I did all of my updates and restarted again. Still no functional desktop.

---

### Post by cariboo on 2009-02-14
I would suggest reinstalling the desktop to see if that helps open a terminal and type:

```
sudo apt-get reinstall ubuntu-desktop
```

BTW if your desktop freezes you can restart X by pressing Ctrl-Alt-Backspace

Jim

---

### Post by Stunts on 2009-02-15
That sounds like some problem starting nautilus.
Try running from the console: ```
 nautilus -n
```
This will attempt to make nautilus manage the desktop again.
Just post any errors you may encounter.
If it fails,[COLOR=Black] cariboo907'[/COLOR]s suggestion sounds good.

---

