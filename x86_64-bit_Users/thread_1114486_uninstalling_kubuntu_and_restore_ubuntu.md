---
title: "uninstalling kubuntu and restore ubuntu"
date: 2009-04-02
forum: x86 64-bit Users
---

### Post by ynyus75 on 2009-04-02
I have installed both kubuntu and ubuntu on my system. Now I want to keep only ubuntu. Can I unstall kubuntu and just keep ubuntu?

---

### Post by steeleyuk on 2009-04-03
sudo apt-get remove kubuntu-desktop kubuntu-artwork-usplash

Should do it but not 100%.

Also do the following, not sure if it would have been removed or not:

sudo apt-get install gdm

---

### Post by Kareeser on 2009-04-03
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by oldos2er on 2009-04-03
> **ynyus75 said:**
> I have installed both kubuntu and ubuntu on my system. Now I want to keep only ubuntu. Can I unstall kubuntu and just keep ubuntu?

 Depends on how Kubuntu was installed; i.e. as a separate OS on its own partition, or just the DE (desktop environment).

---

### Post by 3Miro on 2009-04-03
> **oldos2er said:**
> Depends on how Kubuntu was installed; i.e. as a separate OS on its own partition, or just the DE (desktop environment).

Correct. If you have two separate OS versions, then you can just reformat/repartition its part of the HD (after backing up all the important files of course). You may have to remove the boot entry from GRUB (I advise that you install a grub editor application, otherwise you can use:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_mybackup
sudo pico /boot/grub/menu.lst

```
and remove the unwanted entries.

If you simply have both KDE and GNOME desktops installed on one operating system, remove the corresponding packages using the instructions from the posts above (I have never done that so I cannot advice).

---

