---
title: "modules.dep - each entry is missing /lib/modules/&lt;version&gt;/..."
date: 2009-05-27
forum: x86 64-bit Users
---

### Post by LoPHat on 2009-05-27
I'm having trouble with drivers compiled for aircrack-ng (r8187). I was told by their support forum to look at modules.dep. I did and found that none of the entries contain the full path to the modules, i.e. the /lib/modules/2.6.28-11-generic/is missing from each entry.

Example

Instead of 
"/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rtl_ieee80211/ieee80211_crypt-rtl.ko:"

I see 
"kernel/drivers/net/wireless/rtl_ieee80211/ieee80211_crypt-rtl.ko:"

What's up with that?

I just looked at a previous version (2.6.24-22-generic) and the full path is there.

---

### Post by pixel :-) on 2009-05-28
I don't undrestand the isue, but aren't these relative paths? In ralation with where the files are actually.

If not, you can't just change the links to full path?

---

### Post by ptn107 on 2009-05-29
I believe its because during the kernel build process depmod[1] was used with the --basedir option.

[1] man depmod

---

### Post by LoPHat on 2009-06-15
But when i run depmod -ae manually, shouldn't it NOT use that option? 

Or does that create some sort of permanent default?

I'll look at the man.

Ok, Here's what i did. I put in the explicit paths and the files were indeed found and the errors went away. I have two installations of 9.04 x64 and the paths are all relative. The errors i noted are found on both systems. I also updated the kernel to 2.6.29 and the problem persists, if it is a problem. It seems that some programs I'm using (i.e.aircrack-ng) need the explicit path. I suppose it could be a problem with that app, but if that one has it then i would expect others to also? It does seem that the path change is only in the 28+ kernels?

---

