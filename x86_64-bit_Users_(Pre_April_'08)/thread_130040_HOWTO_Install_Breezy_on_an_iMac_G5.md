---
title: "HOWTO: Install Breezy on an iMac G5"
date: 2006-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by gwon on 2006-02-15
I tried to install ubuntu a while back on my iMac G5 but ran into the same problem as everyone else, it would install fine and then freeze (no keyboard or mouse input accepted) at GDM.

I am proudly typing this from my iMac G5 after finally getting it to work.

**What you need**

Ubuntu install disk
Gentoo PPC64 install disk (other distros or live CD's *may work, but I used a gentoo disk)

**Let's Go**

Install ubuntu in the normal way, follow other Howto's for this.

Once the installation has finished the **first stage** your machine will reboot. At this point, **eject your ubuntu disk**. To do this, if you have a 2 (or more) button mouse, hold down the right button as your machine powers on and the disk will eject*.

Insert your Gentoo disk, and choose to boot from CD.

Gentoo will boot you through to a command prompt.

Type:

mkdir -p /mnt/ubuntu
mount /dev/sda4 /mnt/ubuntu (replace /dev/sda4 with your ubuntu install partition).
cd /mnt/ubuntu/usr/bin
mv esd esdback
echo "false" | sudo tee /mnt/ubuntu/etc/X11/default-display-manager (this disables GDM).
cd /
umount /mnt/ubuntu
reboot

When you get to yaboot, choose linux, and the ubuntu installation will complete and you will be presented with a command prompt.

Login and then start gnome with **startx**.

Gnome will start and work normally.

The only thing you will be missing is sound.

Enjoy, and hope this helps others.



*If you don't have a two button mouse, boot to OS X and eject your ubuntu disk, and restart your machine, and get back to your yaboot screen.

---

### Post by ssam on 2006-02-15
thanks for the post, i can't confirm that it works, but it looks like it would. it might be worth putting it on the wiki somewhere.

couple of notes:
on a single button mouse holding that button down at start up should eject the disk.

if you need to find out which partition you installed ubuntu on you can run
```
fdisk -l /dev/hda
```
and look for the partition labled Linux native

---

### Post by Arden Shik on 2006-02-19
I've been able to rename esd (using the Ubuntu install CD and the recover boot option), but my iMac G5 is still freezing when I try to start Gnome.  I've managed to get to the command prompt login, and it works fine, but when I try to start Gnome using gdm (startx didn't work), it froze again.  Any other suggestions?

---

### Post by gwon on 2006-02-22
Have you disabled gdm as described?

---

### Post by jesperkr on 2006-02-23
Hey

Thanks gwon for this great HOWTO... I finally managed to get Ubuntu installed, thanks to you...

But... :???: 

The cpu fan accelerates to max. speed after 5 - 10 min. And after another 5-10 min. freezes the system...

My configuration:

IMac 1.8 MHz rev b
1.5 Gb Ram
OS: Ubuntu 5.10

Any ideas, anyone?

I'm a newbie to Ubuntu, so please be gentle ;) 

Regards
Jesper Kristensen

---

### Post by glennric on 2006-03-08
Can't anyone figure out how to properly install Ubuntu on a G5?  Who wants an operating system installed that doesn't have any sound?  It seems clear that the problem is something to do with the sound server configuration.  Someone out there surely has some better ideas than to just disable the sound.

---

### Post by Astounded on 2006-03-10
[QUOTE=jesperkr]Hey

Thanks gwon for this great HOWTO... I finally managed to get Ubuntu installed, thanks to you...

But... :???: 

The cpu fan accelerates to max. speed after 5 - 10 min. And after another 5-10 min. freezes the system...

My configuration:

IMac 1.8 MHz rev b
1.5 Gb Ram
OS: Ubuntu 5.10

Any ideas, anyone?

I'm a newbie to Ubuntu, so please be gentle ;) 

Regards
Jesper Kristensen[/QUOTE]

I do have the exact same problem, fan is accelerating. What to do? Use PC instead? :/

---

### Post by ubuser_ on 2006-03-11
I'm not a Ubuntu user at all, but i wanted to reply to this topic anyway. The complete freezes people are experiencing has something todo with the alsa pmac sound driver. For some reason this driver locks the system completely up. Thermal support is only working via a bashscript. Thermal support not working and no working sound makes this release totally useless. For some reason many developers don't realize this. I'm talking about the alsa developers, Ubuntu developers, and BenH who maintains the PPC branch.

---

