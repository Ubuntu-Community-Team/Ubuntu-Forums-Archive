---
title: "GFX Boot on x86_64"
date: 2007-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by jcfisher on 2007-08-15
Has anyone been able to get grub to use gfx (see: [Howto : GfxBoot ( Grub like suse )]("http://ubuntuforums.org/showthread.php?t=208855")) using 64 bit?  I tried following the instructions listed there, but the .deb is for 32 bit machines, and --force-architecture didn't help it.

---

### Post by jcfisher on 2007-09-02
For those who are interested, I figured out how to do it.  The answer can be found on [this]("http://allostalk.com/showthread.php?t=208855&page=40") page, but I will summarize it here:

```
#Download gfxboot
$ wget http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb

#Remove old grub
$ sudo apt-get remove grub

#Install the .deb
$ sudo dpkg -i --force-architecture grub-gfxboot_0.97-5_i386.deb

#Copy theme to boot directory - note that you must first download
#the theme from the beginning of the thread listed above
$ sudo cp message.suse /boot/grub/

#Back up your menu.lst
$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

#Add a line to menu.lst which says  gfxmenu /boot/grub/message.suse
$ gksudo gedit /boot/grub/menu.lst
```

Save your work, and return to the command line.  Now you need to install grub.  In the following code, replace x and y with the appropriate numbers for your hard drives.

```
$ sudo grub
grub> find /boot/grub/stage1
# This output will give you the numbers you use instead of x and y

grub> root (hdx,y)
grub> setup (hdx)
grub> quit

$ sudo grub-install hdx,y
```

Reboot, and enjoy your new boot screen.

---

### Post by deepnote on 2007-10-11
After removing grub and installing grub-gfxboot, i cant run grub. it says no grub at /sbin/. :confused:

---

### Post by Kilz on 2007-10-11
> **deepnote said:**
> After removing grub and installing grub-gfxboot, i cant run grub. it says no grub at /sbin/. :confused:

If you have your install disk, put it in, reboot, slect rescue a broken system. Eventualy after testing it will offer a list, select reinstall grub.

---

### Post by deepnote on 2007-10-12
So, the grub-gfxboot will work, if I install grub from rescue disk over it?

---

### Post by dabl on 2007-10-12
These screens look nice -- I didn't know about gfx boot.  I wonder if you can make your own splash screen, similar to what you can do with the bootsplash thing?

[http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)

:)

---

### Post by Kilz on 2007-10-12
> **deepnote said:**
> So, the grub-gfxboot will work, if I install grub from rescue disk over it?

No, but it will replace grub and solve the 
"After removing grub and installing grub-gfxboot, i cant run grub. it says no grub at /sbin/." problem.

---

### Post by iborg1013 on 2007-10-12
Download a 64 bits package from [http://kanotix.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-11_amd64.deb](http://kanotix.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-11_amd64.deb)      
 install it and then edit /sbin/update-grub change the first line:
#!/bin/sh
for
#!/bin/bash

it works perfect for me.

---

