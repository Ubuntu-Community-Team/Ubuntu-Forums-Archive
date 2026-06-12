---
title: "Need Help New Computer Install Problems"
date: 2008-11-24
forum: x86 64-bit Users
---

### Post by DzTrajan on 2008-11-24
I've biuld a new computer and tryed to install ubuntu 8.10 but after i get to the ubuntu splash screen and the progres bar fills the computer gos into some kind of sleep mode and wont wake up. I have tryed useing an older version of ubuntu both 32bit and 64 bit I even tryed just running it off the live cd the samething keep happening. so I tryed other linux os most of them would do the samething i got some of the smaller unknow os to boot the liver cd. i would realy like to get ubuntu working any help would be great.

Thanks 

DzTrajan

---

### Post by jyaan on 2008-11-24
Which video card do you have? When I had ATI Radeon 9200 this kind of thing happened to me and I had to use the alternate install CD. You might also want to try disabling acpi on the boot options (on the live CD menu), but I haven't had problems with that before so I'm not sure (I think that's mainly with computers from before 2002).

---

### Post by DzTrajan on 2008-11-24
I have a Diamond Viper ATI Radeon HD 3870 PCIE 1024MB GDDR3 Video Card 3870PE31G.
i have tryed using the alternate install CD and it installs but when it boots up samething happens gos into sleep mode and wont wake up. Ill try turing off the acip and see what happens.

---

### Post by DzTrajan on 2008-11-24
Ok i tryed turning off acpi did nothing pc still went into sleep mode.

---

### Post by jyaan on 2008-11-24
We found the solution:

Since the recovery shell doesn't provide networking you'll need to boot into a live CD and then chroot into Ubuntu to fetch packages/install:
```

# If your drive with Ubuntu is /dev/sda1 and using the Gentoo Minmal CD
# Otherwise you may need to create a mount point; do so with
# mkdir /mnt/ubuntu
# and change /mnt/gentoo to that
mount /dev/sda1 /mnt/gentoo 
mount -t proc none /mnt/gentoo/proc
mount -o bind /dev /mnt/gentoo/dev
chroot /mnt/gentoo /bin/bash 

# Now install envyng
sudo apt-get install envyng-core

# This will fail, but it will fetch the driver file & must be done
sudo envyng -t

# Now exit chroot and reboot into Ubuntu
exit
# either this command
halt -r NOW
# or this one depending on your live CD
reboot

```

When booting Ubuntu, press ESC to enter the GRUB menu and select "Recovery Mode".

Ubuntu will start booting into text mode, when the menu pops up select "Drop to root shell"

Install ATI drivers:
```

# install the driver with envyng in text mode
envyng -t

```



Select 3 from the menu, and then select the ATI driver with 0. The driver will install itself, and afterwards you'll be prompted to restart. Select to restart and boot into Ubuntu normally.

---

