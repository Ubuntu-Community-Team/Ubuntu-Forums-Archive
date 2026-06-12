---
title: "Can't login at all now - Fatal X error"
date: 2008-05-07
forum: x86 64-bit Users
---

### Post by X-Fi6 on 2008-05-07
**LONG STORY:**

:( If I could I would make this shorter but I simply can't.

Alright, I am pretty new to Linux. Keep trying to figure out how to make good use of it. A couple days ago I decided to make the computer downstairs that nobody uses as a small web server simply for when I needed it.

So two days ago I installed Xubuntu 8.04 for AMD64, and after installation, I logged in and all was well, until my act of stupidity where I was like "hmm what does ctrl+alt+esc do again" and accidentally clicked on the desktop. So my icons disappeared. I was like WTF and I restarted the computer. The desktop still didn't load, but the taskbars at the top and bottom still worked fine. Trying to get the desktop back again, I accidentally ctrl+alt+esc'd the taskbars as well.

When I restarted again, the background didn't load (but the blue color did). I tried a LOT to fix it but nothing worked. So in the end I decided to install normal Ubuntu 8.04 LTS for AMD64, and guess what, even the LiveCD part of it didn't work--and what's worse is that **not only does the desktop not load, but after about 4 seconds it logs me out**.

But I noticed Failsafe GNOME works, which meant I could view the system log. I waited a couple minutes and then logged out, logged back in with GNOME, got logged out, logged back in with Failsafe GNOME, and in the system log it contained this:```
Warning: gdm_slave_zioerror_handler: Fatal X error: Restarting :0
```So is there any way to fix this?? It SUCKS because Ubuntu is such a great distro but I can't get it to work.

---

### Post by ASULutzy on 2008-05-07
This may not be the most helpful post, but if your install is only two days old why not just reinstall?

I mean I'm sure the problem is fixable, but if you're not too invested at this point why not just reload Ubuntu fresh?

edit: and I thought ctrl+alt+esc was a KDE thing, not a Gnome thing? I'm probably wrong about this one.

---

### Post by Cappy on 2008-05-08
Try creating a new user. If a new user works then all you have to do is clear your (hidden) settings on your original account that are stored in the home folder.

I would check to see if using "startx" while in single user recovery mode would work too.

Make sure compiz is disabled.

If all else fails post your video card and if/how you installed the restricted drivers (The 3D acceleration that is required to play games).

---

### Post by X-Fi6 on 2008-05-09
Hmm well today when I was messing around with it it managed to actually login correctly in normal GNOME mode.

But...whole new problem...when I tried to install the AC'97 audio drivers it make the audio settings window not work and MUCH worse, when I restarted, it wouldn't even let me log in with failsafe GNOME (this time it said the computer was not logged in for 10 seconds before logging off, and when I viewed the error it said that this audio file is missing).

Augh I don't want to have to reinstall AGAIN. Failsafe terminal still works...

---

