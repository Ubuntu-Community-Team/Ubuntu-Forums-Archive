---
title: "Hoary Hedgehog Kernel Problem"
date: 2005-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by MistaED on 2005-05-25
Hello all,

Ubuntu has been running great ever since I installed it. I've been running the Hoary Hedgehog 5.04 AMD64 release with the 2.6.10-5-amd64-generic kernel.

I tried getting the 2.6.10-5-amd64-k8 kernel but that one gave me an error:

/bin/sh: error while loading shared libraries: libc.so.6 cannot open shared object file: No such file or directory
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

Ubuntu's root is installed on hda3/(hd 0,2), and grub is all configured correctly to boot from there. So I have no idea what it is doing.

This has become urgent now because I tried reinstalling the k8 kernel and now my generic kernel is dead like this too :( I have no idea what is happening!

Please, could someone help me? I have the 64-bit live cd so I can chroot and use apt. My PC is dead at the moment as XP is acting up, I really need help ASAP and I don't want to format and start again! This is ubuntu/linux after all.

Update: This problem (for the amd64-generic) could've been caused by the security update. 
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11135](https://bugzilla.ubuntu.com/show_bug.cgi?id=11135)

Thanks
-MistaED

---

### Post by Burgundavia on 2005-05-25
Can I see your sources.list? There is some thought that "enhanced" sources.list, with debian sources might be causing the issue.

Corey

---

### Post by Michal Fapso on 2005-05-26
Please, look at this post:

[http://www.ubuntuforums.org/showthread.php?t=36573&page=2](http://www.ubuntuforums.org/showthread.php?t=36573&page=2)

---

