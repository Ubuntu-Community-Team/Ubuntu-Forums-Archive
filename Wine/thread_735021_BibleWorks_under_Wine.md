---
title: "BibleWorks under Wine"
date: 2008-03-25
forum: Wine
---

### Post by Althippie on 2008-03-25
Dear Community,

I tried very intensiv to make BibleWorks run on Ubuntu. But is did not work.
Thats what console gives back
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: could not load L"c:\\windows\\system32\\bw500.exe": Modul nicht gefunden
> 
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4070407, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4070407, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: stub!


I also tried to install the fonts on [http://www.bibledoctrine.net/fonts/]("http://www.bibledoctrine.net/fonts/")
directly in wine/drive_c/windows/fonts but it didn't help

Do you have an idea?

Thanks in advance,

Althippie

---

### Post by Althippie on 2008-03-28
Would be perfect if somebody could help

---

### Post by 71CH on 2008-04-07
Hey
I have BW7 installed on Ubuntu 7.10 but I did not use Wine.  I installed Crossover office pro version 6.2.  Once that is installed you have to install DCOM98.  Then in the same bottle you can install BW7.  It's a bit buggy but all the essentials seem to work.  Crossover office costs money so use the trial version first to make sure it works for you.

---

### Post by cogadh on 2008-04-07
Since Crossover actually is Wine, you could probably do the same thing with Wine and get it to work.

---

### Post by amiga_os on 2008-04-14
Hi Althippie,

If you've tried intensively, then I presume you checked out the BibleWorks app page on the wine website.  Here it is anyway:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=538](http://appdb.winehq.org/objectManager.php?sClass=application&iId=538)

Some questions that would help:
What version of Ubuntu?
What version of Wine?
What version of Bible Works?

Have you tried, using a fresh install of Wine, installing Internet Explorer first, and then installing Bible Works?  That has helped clean it up for some people.

CrossOver does actually work better than Wine, as it's bottle system solves these random dependency problems.  Try installing the demo of CrossOver (for free), which will confirm whether or not BW will then work for you.

[http://www.codeweavers.com/products/cxlinux/download_trial/](http://www.codeweavers.com/products/cxlinux/download_trial/)

But if you're using vanilla Ubuntu and vanilla Wine you *should* be able to get Bible Works running properly.  So try what I've suggested, and answer the questions above if you have a problem.

Anybody who has a version of Bible Works other than 6, please consider becoming an app maintainer on the Win AppDB.  I'm the only one!  And since I only have 1 version, I don't want to be a super maintainer.  Thanks
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=538](http://appdb.winehq.org/objectManager.php?sClass=application&iId=538)

---

### Post by Althippie on 2008-08-13
Thank you very very much.
It did work.
After a long time of having no time to solve the problem I tried out your advice and it perfectly worked out.

:guitar:

---

### Post by wtstommy on 2008-08-20
I have a how to for setting up Bibleworks (with Wine) on my blog. Maybe it will help. [http://nerdlets.thekeenehouse.com/2008/08/18/run-bibleworks-7-with-wine-in-ubuntu-804/](http://nerdlets.thekeenehouse.com/2008/08/18/run-bibleworks-7-with-wine-in-ubuntu-804/)

---

