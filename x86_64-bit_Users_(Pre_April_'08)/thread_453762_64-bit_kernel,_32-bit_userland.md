---
title: "64-bit kernel, 32-bit userland"
date: 2007-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by j0m on 2007-05-24
Hope to not be posting in the wrong forum, but I thought it was relevant here...

I have a dual-boot setup between 32-bit Ubuntu Feisty (U32 from now on, for conciseness' sake) and 64-bit Gentoo 2007.0 (G64 as abbreviation, same reason).

Now, I would like to avoid rebooting between the two OSes, and so far chroot'ing seems the right solution (I've already used it profitably from G64 to enter a 32-bit Gentoo chroot, on another PC of course, and I already succeed in chroot'ing from G64 to U32).

In that case I can chroot straight away, or type the "linux32" command in front of chroot to let uname think it's in a fully 32-bit environment; enough with these intricacies...

The issue here is that reversing the factors (chroot from U32 to G64) doesn't work, as I get "Exec format error" for trying to execute 64-bit binaries on a 32-bit kernel. In a Gentoo forum they confirmed that is (probably) the obvious cause, and pointed me to give the G64 kernel a try at booting my U32 setup (in general they say a 64-bit kernel should let the 32-bit system work).

But, as I expected, it stops responding very early in the boot process, and it's difficult to understand exactly why.

So I would like to take the most "natural" route: boot U32 with an U64 kernel, and see what happens with both my U32 userland, and the G64 chrooted one.

Therefore my questions are:

- Would this U64 kernel interact well with U32 userland ? Is there a risk to screw everything up (i would really _hate_ that) ? Has anyone tried anything similar ?

- How should I install it ? May I avoid using a custom-built kernel, and employ a standard U64 kernel image ?
If so, should I type something like

```
sudo dpkg --force-architecture -i linux-image-arch.deb
```

? Or is there a way to "apt-get install" it by simply adding a 64-bit repo to my sources.list, eventually with a few more bits to set to avoid other 64-bit packages overrides ?

- Are other 64-bit system/base packages needed along with the U64 kernel to ensure proper functioning ? Do I need to take special care of the initrd image ?

- Last, but not least, guessing any other issue should be out of my way (for instance, I suppose G64 userland shouldn't give me any headaches, and no special "linux32"-like utility should be needed), which is the Ubuntu way to start chrooted GNOME/KDE apps as if they were session-native ?

---

### Post by Kilz on 2007-05-24
> **j0m said:**
> Hope to not be posting in the wrong forum, but I thought it was relevant here...

I have a dual-boot setup between 32-bit Ubuntu Feisty (U32 from now on, for conciseness' sake) and 64-bit Gentoo 2007.0 (G64 as abbreviation, same reason).

Now, I would like to avoid rebooting between the two OSes, and so far chroot'ing seems the right solution (I've already used it profitably from G64 to enter a 32-bit Gentoo chroot, on another PC of course, and I already succeed in chroot'ing from G64 to U32).

In that case I can chroot straight away, or type the "linux32" command in front of chroot to let uname think it's in a fully 32-bit environment; enough with these intricacies...

The issue here is that reversing the factors (chroot from U32 to G64) doesn't work, as I get "Exec format error" for trying to execute 64-bit binaries on a 32-bit kernel. In a Gentoo forum they confirmed that is (probably) the obvious cause, and pointed me to give the G64 kernel a try at booting my U32 setup (in general they say a 64-bit kernel should let the 32-bit system work).

But, as I expected, it stops responding very early in the boot process, and it's difficult to understand exactly why.

So I would like to take the most "natural" route: boot U32 with an U64 kernel, and see what happens with both my U32 userland, and the G64 chrooted one.

Therefore my questions are:

- Would this U64 kernel interact well with U32 userland ? Is there a risk to screw everything up (i would really _hate_ that) ? Has anyone tried anything similar ?

- How should I install it ? May I avoid using a custom-built kernel, and employ a standard U64 kernel image ?
If so, should I type something like

```
sudo dpkg --force-architecture -i linux-image-arch.deb
```

? Or is there a way to "apt-get install" it by simply adding a 64-bit repo to my sources.list, eventually with a few more bits to set to avoid other 64-bit packages overrides ?

- Are other 64-bit system/base packages needed along with the U64 kernel to ensure proper functioning ? Do I need to take special care of the initrd image ?

- Last, but not least, guessing any other issue should be out of my way (for instance, I suppose G64 userland shouldn't give me any headaches, and no special "linux32"-like utility should be needed), which is the Ubuntu way to start chrooted GNOME/KDE apps as if they were session-native ?

To my knowlage you will be the first to try this. For some reason I dont think it will work. But let us know if you get it to work.
For the most part people dont use chroots that I know of. The number of needed 32bit applications is so small (and shrinking) that most people install them to the 64bit install. There are scripts for 32bit firefox for example(see my signature and the Dapper sticky, info is still good in Feisty for the most part). But if you find you need a lot of 32bit apps, for some reason, you may want to go with a chroot.
But its a jail.

---

### Post by RAOF on 2007-05-24
dpkg --force-architecture-ing an AMD64 kernel should work, I think.

There's no particular reason why a 64bit kernel would break a 32bit userspace.  And as long as you've still got a 32bit kernel in Grub, you won't **totally** break your system :).

---

### Post by j0m on 2007-06-01
I've found this [http://ubuntuforums.org/showthread.php?t=91010](http://ubuntuforums.org/showthread.php?t=91010)

And I've tried it, of course taking different versions and up-to-date naming (linux-generic) into account.

Problem is, it seems it doesn't end there, so no happy ending :( :

- the amd64 kernel wanna load a 64-bit fglrx.ko, so I forced also the xorg-driver-fglrx package
- then Xorg tries to start, but fails loading a *fglrx*.so (don't remember the name now), which belongs to libgl1-mesa-glx
- i force libgl1-mesa-glx, but then /usr/bin/Xorg needs to be 64-bit...

You may imagine the frustration, it looks like you have to follow the chain way down to libc6... :(

Does anyone know of a way to overcome these issues ? Maybe keeping around static versions of the above ? And then, what about the toolchain ? Will it compile 32-bit out-of-mainline (stuff like *-source packages) kernel modules only ? Should I install another, 64-pure, toolchain ? If so, would both toolchains coexist happily ? If not, could I go on with the normal 32-bit toolchain, plus a crosstoolchain, maybe in a chroot ?

Sorry for the question "storm", but I'm a bit confused, maybe I miss some details...

---

### Post by PremierSullivan on 2008-04-18
This works, in fact theres not much difference.  Unless you have a binary driver like fglrx or nvidia, it should work like a charm.  I'm doing it right now to debootstrap a 64 bit debian system.  

I bet if you just change some stuff in sources.list and then did sudo apt-get full-upgrade, it would just work;  obviously, dont try this if you cant afford to have you system borked.

---

### Post by Kilz on 2008-04-18
> **PremierSullivan said:**
> This works, in fact theres not much difference.  Unless you have a binary driver like fglrx or nvidia, it should work like a charm.  I'm doing it right now to debootstrap a 64 bit debian system.  

I bet if you just change some stuff in sources.list and then did sudo apt-get full-upgrade, it would just work;  **obviously, dont try this if you cant afford to have you system borked.**

While there are probably a few people with a 64bit system that dont have the proprietary video drivers installed. I think most of the people I know that have a 64bit ubuntu system do. Most of them are performance junkies like me and want everything they can get.
Still fewer are the people who can afford a fubar'd system.

---

