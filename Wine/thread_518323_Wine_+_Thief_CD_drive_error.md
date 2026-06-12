---
title: "Wine + Thief CD drive error"
date: 2007-08-05
forum: Wine
---

### Post by Hobo Joe on 2007-08-05
Ok, so I really like Thief, and it doesn't work on Windows XP(unless there is some tweak I don't know of), so I thought I'd give it a try out on WINE, emulating Windows 98. So I popped the CD in, and everything worked perfect, not a single hitch through the whole install.

Then, after the install finished, the window popped up with options like 'play' and 'uninstall' etc. So I click play, and it says "Please enter CD into drive". Normally I wouldn't consider this a really weird error with WINE, in fact, I would say it's to be expected, but because I was able to install perfectly from the CD, it doesn't really make sense.
Has anyone had this problem or knows how to fix it?

---

### Post by cogadh on 2007-08-05
It's probably the CDs copy protection. Wine doesn'thave complete support for all copy protection schemes, which sometimes presents itself as a "insert CD" error, so you might try to use a cracked exe.

---

### Post by Hobo Joe on 2007-08-05
I might have agreed with that normally, but the fact that is was able to install pretty much tells me that that isn't it, but then again, I could be wrong.

Is there any way I could make a 'no-CD' patch for it? Or is that illegal?

---

### Post by cogadh on 2007-08-05
Quite often, the copy protection doesn't actually come into play until after the game is installed. For example, Starforce copy protection only really works after it has installed a hidden driver on the system, which occurs during game installation (only on Windows, of course). A security check doesn't occur until you try to launch the game for the first time.

As for a no CD crack, its not illegal as long as you legally own the game, but why would you try to make your own when you can just download one from any number of sites?

---

### Post by Hobo Joe on 2007-08-05
Ok, I tried installing Warcraft 3, and had the exact same results. Installed fine, but can't see the CD when I try to run.

Would it have anything to do with the fact that I'm running 64-bit Ubuntu? Or is it a bugged wine version?

---

### Post by cogadh on 2007-08-05
What does it say for your CD drive on the Drives tab in winecfg? Is your CD drive properly configured there? You might also check to see if there is a symbolic device link to your CD drive in the .wine/dosdevices directory. If you need help with that, click on the "Stuff I've learned about Wine" link in my sig, I included some info on the drive configuration in Wine there.

Almost forgot, what version of Wine are you using?

EDIT - I did find that if you are using Warcraft 3 on a 64-bit system, you may need to run it with this command:
```
setarch i386 -X wine "Warcraft III.exe"
```
[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

---

### Post by Hobo Joe on 2007-08-06
```

setarch i386 -X wine "Warcraft III.exe"
bash: setarch: command not found

```

Hmmmm.

I'm using Wine version 0.9.42

My CD drive config is:  "A: /media/cdrom0/"

Should it be a differen't letter or something?

---

### Post by cogadh on 2007-08-06
A: is usually reserved for the floppy drive only in Windows, so I can see how it might cause a problem. It seems pretty unlikely, but try changing it to D: or something higher.

---

### Post by Hobo Joe on 2007-08-15
I know I'm bumping and old thread, but i fixed the drive problem, and now I have another.

When I boot into WC3 it tries to stretch across both my monitors,(which is normal, all fullscreen apps try to do this), but when I click on options, to change it windowed mode, it crashes. So I was wondering if anyone knows about a config file or something that would change it without me having to open the game.

---

### Post by cogadh on 2007-08-15
Try using Wine's "Emulate virtual desktop option", that makes any app run through Wine open in a window instead of full screen.

---

