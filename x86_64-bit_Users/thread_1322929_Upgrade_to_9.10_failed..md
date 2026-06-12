---
title: "Upgrade to 9.10 failed."
date: 2009-11-11
forum: x86 64-bit Users
---

### Post by alias_neo on 2009-11-11
Hi guys, I tried the upgrade via internet to 9.10 karmic but it finished by saying it completed except the kernel did not install.

It rebooted and now I can not boot, the changes made seem to prevent my old kernel from booting, it simply hangs.

I can enter recovery mode for a command line so i found what I believe to be the problem, grub-gfxboot so i downloaded the .deb for grub from another computer and replaced it. now the partially configured packages don't appear anymore so I can't finish installing the kernel.

I can't boot into the desktop environment and I can't get wireless to connect from command line in order to install the new kernel. (Nework required a log in on the home page to connect to internet but i can't even get the access point to associate.)

Any solutions please?

---

### Post by Kilz on 2009-11-12
> **alias_neo said:**
> Hi guys, I tried the upgrade via internet to 9.10 karmic but it finished by saying it completed except the kernel did not install.

It rebooted and now I can not boot, the changes made seem to prevent my old kernel from booting, it simply hangs.

I can enter recovery mode for a command line so i found what I believe to be the problem, grub-gfxboot so i downloaded the .deb for grub from another computer and replaced it. now the partially configured packages don't appear anymore so I can't finish installing the kernel.

I can't boot into the desktop environment and I can't get wireless to connect from command line in order to install the new kernel. (Nework required a log in on the home page to connect to internet but i can't even get the access point to associate.)

Any solutions please?

Only one I can suggest is to do a clean install. Use a live cd to boot into the system so you can back up anything you may have forgotten to backup before the upgrade.

---

### Post by alias_neo on 2009-11-12
> **Kilz said:**
> Only one I can suggest is to do a clean install. Use a live cd to boot into the system so you can back up anything you may have forgotten to backup before the upgrade.

Yeh, this is exactly what I did and finally got it working, BUT, for the sake of completeness I will mention this...

I managed to get a wired connection and use Aptitude to install the kernel, rebooted and it stayed at black screen with medium amounts of hard drive access constantly for half an hour before I got bored and turned it off.

I did a fresh install but had some problems, The old partition manager was much better, and allowed me to install grub on the boot sector of the linux partition instead of the MBR, when I went to advanced and changed it here and finished install then rebooted, Linux was now not bootable, my loader from the Windows 7 bootloader just did nothing and the PC had to be forcefully switched off.

I solved this by switching to the grub bootloader (doing another fresh install) and loading 7 from within that.

The reason I used the Windows 7 bootloader originally is because when using Ubuntu 9.04 and was chainloading Win7 from Grub, it was causing power management problems that would prevent hte system from hibernating, which was hard to solve might I add when the last thing ever I would have thought of was  the bootloader.

Anyway, system is finally set up now and I'm happily replying to you from my new Karmic 9.10, and I must say, the good Karma is welcomed (finally)!

---

