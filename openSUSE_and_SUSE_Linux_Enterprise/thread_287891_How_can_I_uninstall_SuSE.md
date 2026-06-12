---
title: "How can I uninstall SuSE?"
date: 2006-10-29
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Epperly on 2006-10-29
I have Suse installed on my laptop 2nd to Windows but I want to get rid of it due to the fact that I can't use it anyway (cannot get ndiswrapper/bcm43xx working with it or Ubuntu)

So I was wondering if there was a way I can remove it without hurting windows.
(Do I need a partitioning program for Windows to do it?)

---

### Post by wizap on 2006-10-29
It's on a seperate partition to windows, so it would not hurt.

---

### Post by Epperly on 2006-10-29
What would not hurt?
I am wondering how to uninstall it..
a partitioning program wouldn't hurt?

---

### Post by wizap on 2006-10-29
If you are using the windows boot loader then it is safe to reformat the Suse partition, else you will need to restore the windows Master Boot Record, prior to getting rid of Suse.

---

### Post by LakeWind on 2006-10-29
If you are using Grub (SUSE boot loader) then check out this link, I think it's what you are looking for:


[http://www.novell.com/de-de/documentation/suse91/suselinux-adminguide/html/ch07s05.html](http://www.novell.com/de-de/documentation/suse91/suselinux-adminguide/html/ch07s05.html)

or if that link wraps then use this one:

[http://tinyurl.com/yzufn9](http://tinyurl.com/yzufn9)

Once your Master Boot Record is restored properly and you can boot into Windows, then just delete the SUSE partition and repartition/format. If you need more help just ask.
 
Hope this helps you out.

:)

---

### Post by Epperly on 2006-10-29
well, is that just to get rid of the bootloader? I still need to delete the Suse partition and recover that disk space.

So I think that pretty much covers it, Thanks guys!

---

### Post by LakeWind on 2006-10-29
> **Epperly said:**
> well, is that just to get rid of the bootloader? I still need to delete the Suse partition and recover that disk space.

So I think that pretty much covers it, Thanks guys!

Yes the above link explains how to get rid of the boot loader. Once you do that and can boot into Windows you can repartition.

IIRC all you need to do is to open up the control panel in Windows, select Admin Tools, Computer Management, Disc Manager. Then select the partition that SUSE was installed on. Repartition it and then format it.

Take Care!:)

---

### Post by Epperly on 2006-10-29
oh sweet... thanks for that I was already looking for partitioning programs, phew

---

### Post by Epperly on 2006-10-29
uh oh.. in the disk managment I deleted locigal drives and then it all merged into 20 gigs of free space... so I didn't know what to do with it so I pressed delete logical drive again, and I thought it was format but it disappeared... and now I am left with 30 gigs and don't know what happened to the other 20....

[edit]wait, nevermind it's still there... how do I merge it into the 30 gigs though?
Thanks again
[/edit]

---

