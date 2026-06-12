---
title: "Advice request on 64-bit."
date: 2007-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by radio1 on 2007-02-20
Hey all.

Every now and then, I play around w/ Linux.

I have a Windows XP machine (AMD 64 3200, 2GB, NV6800Ultra and SBX-fi) and I'd liketo play around with Ubuntu 64bit. I was planning to attach an old 60GB Western digital (via USB 2.0) and use that for the distro.

My problem is that this is also the family computer?

Can I throw on Ubuntu 64 bit on this drive and have the equivalent of my 1GB key drive with Puppy Linux? Or is there a way to dual boot that 'defaults' to WinXP, and does mess up the MBR if I decide to remove Ubuntu from the drive and use it as storage?

Why you ask? Because I like to like to learn stuff! I learned some stuff about Linux when I tried installing MythTV on an old computer previously.

Thanks for your thoughts!

---

### Post by Kilz on 2007-02-20
> **radio1 said:**
> Hey all.

Every now and then, I play around w/ Linux.

I have a Windows XP machine (AMD 64 3200, 2GB, NV6800Ultra and SBX-fi) and I'd liketo play around with Ubuntu 64bit. I was planning to attach an old 60GB Western digital (via USB 2.0) and use that for the distro.

My problem is that this is also the family computer?

Can I throw on Ubuntu 64 bit on this drive and have the equivalent of my 1GB key drive with Puppy Linux? Or is there a way to dual boot that 'defaults' to WinXP, and does mess up the MBR if I decide to remove Ubuntu from the drive and use it as storage?

Why you ask? Because I like to like to learn stuff! I learned some stuff about Linux when I tried installing MythTV on an old computer previously.

Thanks for your thoughts!

I dont think Ubuntu will mess up your drive if you use it to dual boot. I have never seen or read of it happening.  You could edit the grub boot menu to load windows as default.

---

### Post by radio1 on 2007-02-21
When and how is that done?

Setup or in a terminal after install?

---

### Post by Kilz on 2007-02-21
> **radio1 said:**
> When and how is that done?

Setup or in a terminal after install?

After install type or copy/paste this in a terminal
```
gksudo gedit /boot/grub/menu.lst
```

It will open the text editor in administrator mode. Be careful about what you do. Towards the bottom you will see sections that are the menu options for grub. Like this

title		Ubuntu, kernel 2.6.15-27-amd64-k8
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-amd64-k8 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-amd64-k8
savedefault
boot

Cut the windows section and place it at the top of the list of sections and save. Then when grub times out/you hit enter, it will open Windows. You could change the timeout. But its only 10 seconds, and you want to be able to choose Ubuntu at times.

---

### Post by radio1 on 2007-02-21
Thank you very much!

---

### Post by j0eb0b on 2007-02-23
This is the XP section of my GRUB:

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

When I paste this into the top position above Ubuntu do i also need to add a line "boot"at the bottom?

---

### Post by Kilz on 2007-02-23
> **j0eb0b said:**
> This is the XP section of my GRUB:

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

When I paste this into the top position above Ubuntu do i also need to add a line "boot"at the bottom?

If it doesnt exist in the lower section it may not be needed. Even if it is needed you should be able to boot Ubuntu and add it. Wish I could tell you 100% for sure, But I no longer have a Windows partition. Its been gone a long time :grin:

---

### Post by j0eb0b on 2007-02-23
Thanks for the help.

i have decided to stay the course with Dapper 64 rather than wimping out and falling back to 32 bit.  I know you are passionate about this and you are right, Dapper 64 is more responsive than Windows.

---

### Post by radio1 on 2007-02-24
Awesome.
This is the big reason why I like Ubuntu- the community!

People are helpful here, none of this- 'you'll just have to struggle along for yourself, like I did...'

:)

---

