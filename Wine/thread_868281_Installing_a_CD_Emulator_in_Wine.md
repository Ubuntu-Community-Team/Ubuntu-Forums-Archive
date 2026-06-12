---
title: "Installing a CD Emulator in Wine"
date: 2008-07-23
forum: Wine
---

### Post by jaezcurra on 2008-07-23
Some Windows programs need a CD to be present when running.  A CD Emulator software lets you have multiple virtual CD devices in your pc.  Is there any Windows CD Emulator program suitable to work under Wine?

---

### Post by uberlube on 2008-07-23
As far as I know if you install a windows program with Wine that requires a CD to run, it works automatically. Whenever Im playing Starcraft or Warcraft it automatically reads from the CD.

---

### Post by jaezcurra on 2008-07-23
Yes, but as I only have one CD drive, what if I need to use another CD in the meantime?

---

### Post by Lurieh on 2008-07-23
There's AcetoneISO that can mount most image files types.
[http://www.acetoneiso.netsons.org/]("http://www.acetoneiso.netsons.org/")

---

### Post by jaezcurra on 2008-07-24
My feelings are that I need a Windows CD Emulator to be installed by the means of Wine so I will be able to manage several virtual CD drives in Windows in case I am forced by a Windows program to have a CD present in my PC while, let us say, I am listening to a music CD with an Ubuntu CD music player, for instance.
I have tried Daemon Tools and Alcohol and none of them can be installed by Wine.

---

### Post by jastonas on 2011-04-05
Reviving this thread.. to ask a question.
My sister is doing italian classes and the book came with a cd. The cd is not working on her laptop.

I made an iso, and installed the .exe file that came with wine. Now when I try to open the installed program I get "insert CD". Any workaround?

---

### Post by Tweak42 on 2011-04-06
> **jastonas said:**
> Reviving this thread.. to ask a question.
My sister is doing italian classes and the book came with a cd. The cd is not working on her laptop.

I made an iso, and installed the .exe file that came with wine. Now when I try to open the installed program I get "insert CD". Any workaround?

I sounds like you need to mount the iso and assign that path to a drive letter in wine.  You can do this on the "Drives" tab in winecfg.

---

