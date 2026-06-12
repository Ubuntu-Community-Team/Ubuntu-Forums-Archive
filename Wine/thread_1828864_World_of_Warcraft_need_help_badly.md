---
title: "World of Warcraft need help badly"
date: 2011-08-19
forum: Wine
---

### Post by curt122895 on 2011-08-19
Ok, so let me begin. this is clean install of ubuntu 10.10, I haven't even installed flash player, i installed WoW via wine with the launcher. But the problem is, it wont start. I don't even get a screen to begin, I can't begin the launcher, nor direct begin from Wow.exe. Please help me!

---

### Post by Perfect Storm on 2011-08-19
Moved to Wine Section.

Try start the game via the terminal.
```
wine <path>/wow.exe
```

---

### Post by curt122895 on 2011-08-19
> **Artificial Intelligence said:**
> Moved to Wine Section.

Try start the game via the terminal.
```
wine <path>/wow.exe
```


This is what comes up immediately after 

wine: cannot find L"C:\\windows\\system32\\plugplay.exe"
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
archive Data/Cache/SoundCache-1.MPQ opened for writing
archive Data/Cache/SoundCache-2.MPQ opened for writing
archive Data/Cache/SoundCache-3.MPQ opened for writing
archive Data/Cache/SoundCache-0.MPQ opened
archive Data/Cache/enUS/SoundCache-enUS.MPQ opened
archive Data/wow-update-13164.MPQ opened
archive Data/Cache/patch-base-13164.MPQ opened
archive Data/Cache/enUS/patch-enUS-13164.MPQ opened
archive Data/Cache/SoundCache-patch-13164.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13164.MPQ opened
archive Data/wow-update-13205.MPQ opened
archive Data/Cache/patch-base-13205.MPQ opened
archive Data/Cache/enUS/patch-enUS-13205.MPQ opened
archive Data/Cache/SoundCache-patch-13205.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13205.MPQ opened
archive Data/wow-update-13287.MPQ opened
archive Data/Cache/patch-base-13287.MPQ opened
archive Data/Cache/enUS/patch-enUS-13287.MPQ opened
archive Data/Cache/SoundCache-patch-13287.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13287.MPQ opened
archive Data/wow-update-13329.MPQ opened
archive Data/Cache/patch-base-13329.MPQ opened
archive Data/Cache/enUS/patch-enUS-13329.MPQ opened
archive Data/Cache/SoundCache-patch-13329.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13329.MPQ opened
archive Data/wow-update-13596.MPQ opened
archive Data/Cache/patch-base-13596.MPQ opened
archive Data/Cache/enUS/patch-enUS-13596.MPQ opened
archive Data/Cache/SoundCache-patch-13596.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13596.MPQ opened
archive Data/wow-update-13623.MPQ opened
archive Data/Cache/patch-base-13623.MPQ opened
archive Data/Cache/enUS/patch-enUS-13623.MPQ opened
archive Data/Cache/SoundCache-patch-13623.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13623.MPQ opened
archive Data/wow-update-base-13914.MPQ opened
archive Data/enUS/wow-update-enUS-13914.MPQ opened
archive Data/Cache/patch-base-13914.MPQ opened
archive Data/Cache/enUS/patch-enUS-13914.MPQ opened
archive Data/Cache/SoundCache-patch-13914.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13914.MPQ opened
archive Data/wow-update-base-14007.MPQ opened
archive Data/enUS/wow-update-enUS-14007.MPQ opened
archive Data/Cache/patch-base-14007.MPQ opened
archive Data/Cache/enUS/patch-enUS-14007.MPQ opened
archive Data/Cache/SoundCache-patch-14007.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-14007.MPQ opened
archive Data/wow-update-base-14333.MPQ opened
archive Data/enUS/wow-update-enUS-14333.MPQ opened
archive Data/Cache/patch-base-14333.MPQ opened
archive Data/Cache/enUS/patch-enUS-14333.MPQ opened
archive Data/Cache/SoundCache-patch-14333.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-14333.MPQ opened
archive Data/wow-update-base-14480.MPQ opened
archive Data/enUS/wow-update-enUS-14480.MPQ opened
archive Data/Cache/patch-base-14480.MPQ opened
archive Data/Cache/enUS/patch-enUS-14480.MPQ opened
archive Data/Cache/SoundCache-patch-14480.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-14480.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\sound.MPQ opened
archive Data\world.MPQ opened
archive Data\art.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x32eccc,0x00000000), stub!


and then nothing happens:(

---

### Post by cwwilson721 on 2011-08-19
Actually, first things first.

[LIST]
[*]What hardware are you running?
[*]Do you have the propriatary hardware drivers for your videocard/chip installed?
[*]What version of wine?
[*]Post the output of the terminal when you run wine from it (easiest way is to 'edit' the launcher icon, and copy/paste the command into the terminal)
[/LIST]

READ THE FORUM STICKIES!

And follow my own post 
[http://ubuntuforums.org/showthread.php?t=1773985](http://ubuntuforums.org/showthread.php?t=1773985)

---

### Post by curt122895 on 2011-08-19
> **cwwilson721 said:**
> Actually, first things first.

[LIST]
[*]What hardware are you running?
[*]Do you have the propriatary hardware drivers for your videocard/chip installed?
[*]What version of wine?
[*]Post the output of the terminal when you run wine from it (easiest way is to 'edit' the launcher icon, and copy/paste the command into the terminal)
[/LIST]

READ THE FORUM SICKIES!

And follow my own post 
[http://ubuntuforums.org/showthread.php?t=1773985](http://ubuntuforums.org/showthread.php?t=1773985)
Gcard- Radeon HD 4200
CPU AMD phenom 2 x4 or something like that @ 2.6 ghz
8g of ram
1 tb of Hard drive

I will make sure that i install the drivers after i finish updating to 11.04
But I think I do. wine 1.3 beta downloaded today
And I don't know how to do that last part. I am reading your post now. Looks like it could work, will post back later

---

