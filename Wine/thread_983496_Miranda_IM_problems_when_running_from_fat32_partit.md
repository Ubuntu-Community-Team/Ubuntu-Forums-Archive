---
title: "Miranda IM: problems when running from fat32 partition"
date: 2008-11-15
forum: Wine
---

### Post by art_s on 2008-11-15
Hi all,

I'm trying to get Miranda IM working under wine. 

The problem I'm having is that if it's installed in Program Files it's all good, it works OK etc, but if I install it on mounted vfat partition and run, it cannot find database driver:


***'Unable to find any database drivers, this means you cannot create new profile, you need to get dbx_3x.dll'***


If I copy app's folder to wine's 'C' drive, which is somewhere under ~, it all works brilliantly.

Any suggestions how to fix?

Cheers!

---

### Post by cogadh on 2008-11-15
You need to add the FAT32 drive as a drive in Wine's configuration (winecfg > Drives tab).

---

### Post by art_s on 2008-11-15
> **cogadh said:**
> You need to add the FAT32 drive as a drive in Wine's configuration (winecfg > Drives tab).

It was already mapped to a drive.

---

### Post by cogadh on 2008-11-16
How are you launching the app (from the terminal, using a menu shortcut, etc.)?

---

### Post by art_s on 2008-11-16
> **cogadh said:**
> How are you launching the app (from the terminal, using a menu shortcut, etc.)?

I tried both, result is the same. When in terminal mode, there's no additional messages being displayed during the execution.

---

