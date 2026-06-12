---
title: "install problems: b&amp;w splash, panel crashing"
date: 2007-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Senor Hubris on 2007-02-11
Hello,

I recently built an AMD64 (socket AM2) machine.  I initially attempted to install the AMD64 Edgy desktop using the live install CD.  I encountered a few strange things and one problem I don't know how to get around:

1) the splash screen was in black & white and the image was partially corrupted.   

2) when the OS was loaded and X started up the color was fine, but gnome-panel crashed continually.  I was swamped with bug-buddy and crash report dialogs.  Due to the crashing the icon for installing the system never appears.  

So, for now, I am running i386 Ubuntu on this hardware.

I searched this forum for install issues and issues with gnome-panel, but I didn't see anything relevant.  Are most people not seeing this problem?  Are they installing Ubuntu differently?  The only thing I can think of is to install the server version of Ubuntu for AMD64 and apt-get my way to the desktop.

Thanks for any pointers.

---

### Post by cmost on 2007-02-11
Hi!  Welcome aboard.  The black & white boot splash is a well known bug, and, is fixable (I don't take credit for the following fix:)

wget [http://archive.ubuntu.com/ubuntu/poo...ntu_0.6.tar.gz](http://archive.ubuntu.com/ubuntu/poo...ntu_0.6.tar.gz)
tar xzfv usplash-theme-ubuntu_0.6.tar.gz
cd usplash-theme-ubuntu-0.6
mv usplash-theme-ubuntu.c usplash-theme-ubuntu.c.orig
wget [http://librarian.launchpad.net/52477...theme-ubuntu.c](http://librarian.launchpad.net/52477...theme-ubuntu.c)
make
sudo make install
sudo update-initramfs -u

change defoptions line in /boot/grub/menu.lst to:
# defoptions=quiet splash vga=791

sudo update-grub

As to your gnome-panel crashing, I can't say I experienced the same thing at all.  Ubuntu 6.10 is rock stable on my system.  Is it possible you just happened to get a crappy ISO burn?  Try burning your install disk again, but at the slowest possible speed.  You might also try the 6.06 LTS dapper release of Ubuntu as it contains more stable versions of the core software (just to rule out something in Edgy not playing nice nice with your system.)  Otherwise, you might try going the other way and give the amd64 version of Feisty Herd 3 a spin to see if it likes your hardware better.  Good luck!

---

### Post by Senor Hubris on 2007-02-11
> **cmost said:**
> Hi!  Welcome aboard.  The black & white boot splash is a well known bug, and, is fixable (I don't take credit for the following fix:)

....


Thanks for the bugfix.  Somehow I missed finding any info on the black & white problem.  I'll try a few different AMD64 install discs and see how they work.

---

### Post by Ravanous on 2007-02-11
I too had similar problems with both the ubuntu and kubuntu live cd installations.

I ended up using the Extras CD to install the system (kubuntu) and then went about installing the drivers for my ATI card.

The only remaining problem from the initial set that I had is the splash screen showing up corrupted. Ubuntu showed up in b/w & kubuntu shows up in color but like parts of it are missing.

---

### Post by shanepardue on 2007-02-12
> **cmost said:**
> Hi!  Welcome aboard.  The black & white boot splash is a well known bug, and, is fixable (I don't take credit for the following fix:)

wget [http://archive.ubuntu.com/ubuntu/poo...ntu_0.6.tar.gz](http://archive.ubuntu.com/ubuntu/poo...ntu_0.6.tar.gz)
tar xzfv usplash-theme-ubuntu_0.6.tar.gz
cd usplash-theme-ubuntu-0.6
mv usplash-theme-ubuntu.c usplash-theme-ubuntu.c.orig
wget [http://librarian.launchpad.net/52477...theme-ubuntu.c](http://librarian.launchpad.net/52477...theme-ubuntu.c)
make
sudo make install
sudo update-initramfs -u

change defoptions line in /boot/grub/menu.lst to:
# defoptions=quiet splash vga=791

sudo update-grub

As to your gnome-panel crashing, I can't say I experienced the same thing at all.  Ubuntu 6.10 is rock stable on my system.  Is it possible you just happened to get a crappy ISO burn?  Try burning your install disk again, but at the slowest possible speed.  You might also try the 6.06 LTS dapper release of Ubuntu as it contains more stable versions of the core software (just to rule out something in Edgy not playing nice nice with your system.)  Otherwise, you might try going the other way and give the amd64 version of Feisty Herd 3 a spin to see if it likes your hardware better.  Good luck!
Those links are broken..Maybe I can find another howto on fixing that bug if you don't have working links anymore

---

