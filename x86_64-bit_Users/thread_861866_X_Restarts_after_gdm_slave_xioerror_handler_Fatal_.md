---
title: "X Restarts after gdm_slave_xioerror_handler: Fatal X error"
date: 2008-07-17
forum: x86 64-bit Users
---

### Post by xyexz on 2008-07-17
Hello all,
  I've been trying to resolve this issue myself and so far I've been able to find a lot of threads where people are having the same issues as myself but no fixes.
  I actually did find one "fix", it required downloading a patched libnvidia-wfb.so.173.08 and creating a sym link to that as root.
  This didn't solve my issues, which seem to be easily re-created by highlighting some text that has a line break in it, and hitting ctrl+f in Firefox and then hitting ctrl+v.  Something freak's out because, my guess, is that it doesn't have anyway to handle the break newline character in the string (meta-data), and gdm has a hayday with my x-session.
  I'm using a laptop (which doesn't seem to matter as desktop noobs are having the issue as well) model hp tx2110us (tx2000 series), Hardy 8.04.
  - uname -a returns 2.6.24-19-generic
  - using glx
  - using 173.14.05 nvidia drivers
  - firefox v3
  The System Log Viewer, under messages returns this lovely:
Jul 17 00:12:16 Brian-PC kernel: [   91.910748] npviewer.bin[6749]: segfault at f5b32030 rip f7926540 rsp fff4428c error 4

  It used to be this:
Jul 16 23:37:43 Brian-PC kernel: [   96.167402] compiz.real[6466] trap stack segment rip:40fee0 rsp:7fff79ef46a0 error:0

  But that changed after I did the above mentioned "fix".
  I'm running emerald, compiz, awn, all of which i've disabled all at the same time and in different patterns and never does it change the results of the error test.

  Anyone got any ideas, I don't think it's a firefox issue solely, but I can't seem to find another application that has a search box that can't display carriage newline meta-data.

Thanks,
Brian

---

### Post by xyexz on 2008-07-17
New details, Ubuntu updates just ran, had some "linux" updates, the one's that break all your custom drivers :)

After the updates ran and installed, I reboot my laptop, and voila no issues, so i'm recompiled the linuxwacom drivers for my tablet pc, restarted the box and boom, the problem is back!

So the plot thickens, seems to only happen when I've got my tablet drivers installed.

BTW this is what i'm using to install the drivers, it's from a forum post in the finnish ubuntu forums:

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev cpp-3.4 f2c fort77 g77 tcl tcl-dev tclx8.4 tclx8.4-dev tk tk-dev input-utils xserver-xorg-input-wacom xserver-xorg-input-evdev gawk mawk

wget [http://internap.dl.sourceforge.net/sourceforge/linuxwacom/linuxwacom-0.7.9-11.tar.bz2](http://internap.dl.sourceforge.net/sourceforge/linuxwacom/linuxwacom-0.7.9-11.tar.bz2)

wget -O usbtx2000z.patch [http://linuxwacom.pastebin.com/pastebin.php?dl=f3d5b9e73](http://linuxwacom.pastebin.com/pastebin.php?dl=f3d5b9e73)

tar xjvf linuxwacom-0.7.9-11.tar.bz2
cd ~/linuxwacom-0.7.9-11
patch -p1 < ../usbtx2000z.patch

./configure --enable-wacom

make
sudo make install
sudo rmmod wacom
sudo cp src/2.6.24/wacom.ko /lib/modules/2.6.24-19-generic/kernel/drivers/input/tablet/wacom.ko
sudo depmod -e
sudo modprobe wacom
sudo rm /usr/local/bin/xsetwacom

I'm going to try to stop the wacom module and without restarting seeing if the issue still occurs with the module stopped.

---

### Post by xyexz on 2008-07-17
Bump Bump, 16 views and nothing? :(

---

### Post by xyexz on 2008-07-23
This problem is still killing me, anybody?

---

