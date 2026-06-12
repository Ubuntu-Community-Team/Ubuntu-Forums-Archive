---
title: "Font size in wine 5.0 on 20.04 LTS"
date: 2021-06-03
forum: Wine
---

### Post by cearlp2 on 2021-06-03
Installed wine 5.0 on Ubuntu 20.04 and tried running a Windows 32 bit program but the display of the Windows application is so small it is almost unreadable.
Is there a way to change the font size in wine or could it be done some way in the windows application?
I tried to change the Ubuntu Display parameters but that changed nothing.
This same Windows program worked fine on Ubuntu 18.04.

---

### Post by mewingatthemoon on 2021-06-04
Try adjusting the DPI in the "Graphics" section of winecfg. This may not work properly for all apps, but it's a start. I use 192 DPI for my Surface Pro 3.

---

### Post by cearlp2 on 2021-06-06
Where do I find the Graphics section of winecfg? /usr/bin/winecfg and winecfg-stable have nothing about Graphics.
Can you provide me more info about getting to the Graphics configuration?
Thanks.

---

### Post by Butthead on 2021-06-06
type sudo winecfg in console.

---

### Post by cearlp on 2021-06-06
Changed the desktop size from 800x600 to 1024x768 and now cannot get a window large enough to see an Apply changes button,,,My BAD!
Can I restore a base winecfg to get back to a valid desktop size?

---

### Post by mark bower on 2021-07-03
Is there a way to restore winecfg to its defaults without reinstalling wine?  

System:  4k monitor (TV), 20.04 MATE desktop, WINE 5.0.2

I have the same problem as cearlp.  I changed a number of settings in winecfg GUI to try and get the menu line and drop downs in ACAD 2000 to produce a larger font.  In the process, the winecfg display became corrupted and now shows only about 1/4 of the winecfg GUI which prevents restoring the winecfg GUI.  The programs I run under WINE, ACAD 2000 and IrfanView both run o.k. [However, I have never discovered how to make the ACAD menu fonts larger, and the ACAD 2000 setting for fonts tops out at 14pt.

Might I be able to modify the config file for winecfg?  If so, where is the config file for winecfg located and what is its name?  I drilled down mark/.wine/dosdevices/C:/windows/system32, but do not see a winecfg file there.  I do see winecfg.exe, but guessing that is of no value for the problem at hand.

---

