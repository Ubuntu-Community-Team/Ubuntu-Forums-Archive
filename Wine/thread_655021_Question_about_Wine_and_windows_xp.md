---
title: "Question about Wine and windows xp"
date: 2007-12-31
forum: Wine
---

### Post by besby11 on 2007-12-31
I had an idea last night and just thought id confirm it before I put any type of plan into action. Say I was to install Windows XP on a small portion of the hard drive, a full install I mean. and tell wine on my Ubuntu partition to instead of using the fake C:\ drive for  installing and loading DLL's to use the actual C:\ drive that I installed Windows XP so that I could install more apps on account of me having a full install of XP and having all the DLL's needed is this possible? Thnx




                                                                              xXHunterXx

---

### Post by slavik on 2008-01-01
because that partition will be formatted using ntfs, many things might not work ...

---

### Post by rm_mn on 2008-01-01
Some programs work well that way, others not at all, but they may not work in Wine anyway.  Try it! \\:D/

---

### Post by YokoZar on 2008-01-01
> **besby11 said:**
> I had an idea last night and just thought id confirm it before I put any type of plan into action. Say I was to install Windows XP on a small portion of the hard drive, a full install I mean. and tell wine on my Ubuntu partition to instead of using the fake C:\ drive for  installing and loading DLL's to use the actual C:\ drive that I installed Windows XP so that I could install more apps on account of me having a full install of XP and having all the DLL's needed is this possible? Thnx
Do not try this.  It will both not work as well as a normal Wine installation, and will also break your Windows install.

The reason is the registry (Wine overwrites a lot of it), and some Windows DLLs cannot act as replacements for Wine ones.

---

### Post by jken146 on 2008-01-01
You'd be better off with a VM install of windows.

---

### Post by rm_mn on 2008-01-01
I've run many programs right from their installed locations in my Windows partition with not noticing any ill effects.  That may be due to having Winefix installed.  It's described with accompaning download links here.

[http://wine-review.blogspot.com/2007/10/winefix-improved-desktop-integration.html](http://wine-review.blogspot.com/2007/10/winefix-improved-desktop-integration.html)

---

### Post by YokoZar on 2008-01-01
> **rm_mn said:**
> I've run many programs right from their installed locations in my Windows partition with not noticing any ill effects.  That may be due to having Winefix installed.  It's described with accompaning download links here.

[http://wine-review.blogspot.com/2007/10/winefix-improved-desktop-integration.html](http://wine-review.blogspot.com/2007/10/winefix-improved-desktop-integration.html)

This will work with portable applications (ones that don't really use the registry), however attempting to have Wine's registry be the same one that XP uses will break a lot of things.

Quick rule of thumb: if it works on Windows by shoving it onto a USB stick, it should work in Wine when being run directly rather than reinstalled.

---

