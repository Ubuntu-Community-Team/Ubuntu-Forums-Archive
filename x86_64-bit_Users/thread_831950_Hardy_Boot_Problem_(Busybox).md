---
title: "Hardy Boot Problem (Busybox)"
date: 2008-06-17
forum: x86 64-bit Users
---

### Post by GOB1029 on 2008-06-17
Hey everyone,

I've got a bit of a problem here, and I would REALLY appreciate any help.

I've been running Hardy 64bit since its final release, and have had NO issues whatsoever until last night.  I was testing to see if I could suspend my computer, it went into suspend mode, but when I pressed the power button to bring it back up, it went to a blank screen.  After no progression, I shut it down using the power button.  Upon restarting and loading Ubuntu, it takes me to the Busybox prompt.

I'd like to know how to fix this, as right now I'm having to use my windoze partition.

I'm running a Toshiba Satellite P205-D laptop, with a 160GB HD, 130GB partitioned for Ubuntu.  If you need any other information, just let me know.

Again, any and all help is GREATLY appreciated.

Thanks!

EDIT::Boot problem fixed, but now I cannot login (see below)

---

### Post by ravindran.k on 2008-06-17
Greetings.. Are you able to boot into Ubuntu you previous kernels?

You press Esc to get into Grub.. The press E to edit the lines. Mine looks like below

title           Ubuntu 8.04.1, kernel 2.6.24-19-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-server root=UUID=b9f4c570-8b44-413d-bcc8-300f0a0890f9 ro combined_mode=libata clocksource=acpi_pm elevator=deadline rootflags=data=writeback splash vga=795
initrd          /boot/initrd.img-2.6.24-19-server
quiet

Can you tell us wht you see before you boot?

---

### Post by GOB1029 on 2008-06-17
When I boot up, it loads the Toshiba screen, then goes to Grub.  I select Ubuntu (Ubuntu 8.04, kernel 2.6.24-18), and hit enter.  It goes to a black screen saying the Kernel is loaded and active, and then switches to the Ubuntu loading screen.  The section of orange bounces back and forth once on the bar, and then goes to the busybox screen:

BusyBox V 1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash) enter 'help' for a list of built-in commands
(initramfs)

I tried booting w/ the 2.6.24-17 kernel, it did the same thing.

---

### Post by GOB1029 on 2008-06-18
Bit of an update:

I booted from the LiveCD, and ran fsck through the terminal there, and it fixed (at least I hope) a TON of errors with my harddisk.  After this when I loaded up Ubuntu, it took me to my regular login screen.  However, when I try to login, it gives me the incorrect user/pass error.  I tried logging in through the console (ctrl+alt+f2), it did not work as well.  I also went through the recovery console, however, when it asked for a sudo pass, that pass also did not work.

I returned to the LiveCD boot, and checked the permissions of the .dmrc file in my /home/user/ directory, the permissions are -rw, however where it would normally display my username, it says 1000 instead. I.E. it should be (i think):
-rw------- 1 gabe gabe 28 2008-06-16 16:10 /media/disk/home/gabe/.dmrc
But instead its:
-rw------- 1 1000 1000 28 2008-06-16 16:10 /media/disk/home/gabe/.dmrc

Any ideas on how to recover my group/user/root/etc.?

---

### Post by bpl07 on 2008-06-18
> **GOB1029 said:**
> Bit of an update:

I booted from the LiveCD, and ran fsck through the terminal there, and it fixed (at least I hope) a TON of errors with my harddisk.  After this when I loaded up Ubuntu, it took me to my regular login screen.  However, when I try to login, it gives me the incorrect user/pass error.  I tried logging in through the console (ctrl+alt+f2), it did not work as well.  I also went through the recovery console, however, when it asked for a sudo pass, that pass also did not work.

I returned to the LiveCD boot, and checked the permissions of the .dmrc file in my /home/user/ directory, the permissions are -rw, however where it would normally display my username, it says 1000 instead. I.E. it should be (i think):
-rw------- 1 gabe gabe 28 2008-06-16 16:10 /media/disk/home/gabe/.dmrc
But instead its:
-rw------- 1 1000 1000 28 2008-06-16 16:10 /media/disk/home/gabe/.dmrc

Any ideas on how to recover my group/user/root/etc.?

1000 means gabe, as long as you are the primary user on the computer.

---

### Post by GOB1029 on 2008-06-18
So if that's not the problem, any idea on what would be preventing me from logging in?

EDIT::Also, if this thread could perhaps be moved to general discussion by a moderator? (since I don't believe this is really a problem with just the 64bit release of Ubuntu)

---

### Post by philinux on 2008-06-18
From the live cd I think if you delete or rename as backup the .dmrc file and any .gnome directories, there's two I think, it will recreate them correctly when you log in.

---

### Post by GOB1029 on 2008-06-18
I backed up the files, but it didn't change anything.  I'm not able to log-in at all, as my own user, or as root.  I am the only user on the machine.  I'm really stumped here as to what could be causing the problem.  Also note that I haven't lost any data, all my files are still in my home folder, and i'm perfectly capable of accessing my ubuntu partition, both from my windows partition and by booting from my LiveCD.

---

### Post by GOB1029 on 2008-06-20
I finally just bit the bullet and reinstalled.  Don't have the problem anymore, let's hope I don't get it again.

Thanks again for the help, guys :)

---

