---
title: "DLL's in Wine"
date: 2007-12-17
forum: Wine
---

### Post by mikesmith00 on 2007-12-17
I'm not sure if this has been answered or not, I looked through the stickys and searched and couldn't find anything, so I'll ask, has anyone done any comparison between the wine DLL's and the windows DLL's?  I have copies of windows that I could pull the DLL's from if necessary to get wine working as well as possible, or do the Wine DLL's work better now?  I'm not even necessarily looking at speed, but just to get the highest compatibility.  If anyone has tested this, and can reply, thanks, I tried to find my way through the wine wiki, but it's laid out poorly.  Thanks in advance, before I go trying to tear things up.

---

### Post by mc4man on 2007-12-18
Adding, replacing, or setting dll overrides is mainly specific to what program you are trying to run. Your best bet is to try installing/running your program(s) and if they don't or your not happy with the way they work then look at the dll's or other config options. The AppDb at winehq is a good place to start. Also installing/running apps from the terminal can be informative

---

### Post by caratuco on 2007-12-18
It's rather sloppy as you end up with alot of useless dlls but I copied my entire system 32 folders and all from an xp install onto a thumb drive (and cd for future use) and pasted it into wine's system 32 letting it overwrite everything. Works well.

---

### Post by CarpKing on 2007-12-18
> **caratuco said:**
> It's rather sloppy as you end up with alot of useless dlls but I copied my entire system 32 folders and all from an xp install onto a thumb drive (and cd for future use) and pasted it into wine's system 32 letting it overwrite everything. Works well.

Does anything in particular work better than it did before?

---

### Post by cogadh on 2007-12-18
> **caratuco said:**
> It's rather sloppy as you end up with alot of useless dlls but I copied my entire system 32 folders and all from an xp install onto a thumb drive (and cd for future use) and pasted it into wine's system 32 letting it overwrite everything. Works well.
You really shouldn't do this. There are several Wine DLLs that should never be overridden: kernel32.dll, gdi32.dll, user32.dll, and ntdll.dll. If you override those files, Wine won't work correctly at all. However, just copying the DLLs actually does nothing until you apply an override in winecfg for it. Unless you have also done that with all the files you copied, they aren't actually doing anything more than Wine's default placeholders that already exist in Wine's system32 folder, so you shouldn't really see any difference, except for maybe fewer missing support DLL errors.

---

### Post by caratuco on 2007-12-18
Everything I've installed works perfectly. This includes office 2003. Also, I found copying "Fonts"over to the wine windows helps as well.

---

### Post by cogadh on 2007-12-19
Like I said, if you just copied all the DLLs and never applied an override in winecfg, then Wine is still using its built in DLLs. The DLLs you copied are just acting as placeholders, just like the original fake DLLs that came with Wine. Chances are, that is why Wine is still working for you, despite the fact that you copied over the kernel32.dll, gdi32.dll, user32.dll, and ntdll.dll.

Copying the font folder is a different story, that can help a lot, but you can get basically the same results by just installing the msttcorefonts package.

---

### Post by caratuco on 2007-12-19
Excellent.

---

### Post by sarthorks on 2010-07-01
how do i find out if i have the wrong ntdll.dll in my system32 folder? I think i may have replaced the original one with some other downloaded from the net.
Im on Ubuntu 10.04 using wine-1.2-rc4.

---

