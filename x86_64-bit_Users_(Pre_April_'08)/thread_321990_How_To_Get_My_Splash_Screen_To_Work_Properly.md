---
title: "How To Get My Splash Screen To Work Properly?"
date: 2006-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ebozzz on 2006-12-19
Hi All,

I just completed an installation of Edgy on my 64 bit AMD Athlon 3500+ box. I have a problem where during the boot process the splash screen has no color, monochrome, and the progress indicator is not displayed. Is there a way to fix this or is a new install required? I have gone over the all of the resources that I have but have not found a solution to my problems as of yet. FYI, I am fairly new to Linux and Ubuntu. Thanks!

---

### Post by ebozzz on 2006-12-19
Alright, I have a found a way to disable the splash screen. 

> If you have problems with this splash screen, you can disable it. To do this, load the /boot/grub/menu.lst file into a text editor, and scroll to the bottom of the file. You should see a line such as this:

kernel       

[COLOR="Blue"]/boot/vmlinuz-2.6.15-10-386 root=/dev/hda1 ro quiet splash[/COLOR]

Just remove the splash word from the line and restart your computer. Now plain text boot messages are displayed when the system starts.

That's really not what I want to do. Call me vain but I like the appearance that it provides. :redface: So, is there any way of either repairing or changing the current splash? [GNOME-Look.org]("http://www.gnome-look.org/") has some nice screens available.

---

### Post by Azakus on 2006-12-19
This is an issue with all Ubuntu AMD64 versions (I have this problem myself). As of yet, there is no known fix.

---

### Post by ebozzz on 2006-12-19
> **Azakus said:**
> This is an issue with all Ubuntu AMD64 versions (I have this problem myself). As of yet, there is no known fix.

Thanks Azakus. Sounds like I would still have the problem even if I changed the screen. :(

---

### Post by Kikoolol on 2006-12-20
[http://www.ubuntuforums.org/showthread.php?t=304673&page=2](http://www.ubuntuforums.org/showthread.php?t=304673&page=2) :cool: 

Kkl

---

### Post by Pawel Stolowski on 2006-12-20
Use Janvitus repository - see [http://www.ubuntuforums.org/showthread.php?t=196093](http://www.ubuntuforums.org/showthread.php?t=196093).
They provide updated usplash-theme package which includes a workardound for this problem.

---

### Post by ebozzz on 2006-12-20
Thanks for the replies. I will have to read a little more on this issue before attempting to revision.

---

### Post by Azakus on 2006-12-20
> **Pawel Stolowski said:**
> Use Janvitus repository - see [http://www.ubuntuforums.org/showthread.php?t=196093](http://www.ubuntuforums.org/showthread.php?t=196093).
They provide updated usplash-theme package which includes a workardound for this problem.

I tried the theme from the janvitus repo and it didn't work for me. It actually took away any semblence of a splash screen I had.

---

### Post by igsimon on 2006-12-21
dont forget:

Set in the grub vga=791, and in /etc/usplash.conf 1024x768.

Grub:
kernel /boot/vmlinuz root=/dev/sda2 ro quiet splash vga=791

/etc/usplash.conf:
xres=1024
yres=768

Then:
sudo update-initramfs -u

---

### Post by Azakus on 2006-12-23
> **igsimon said:**
> dont forget:

Set in the grub vga=791, and in /etc/usplash.conf 1024x768.

Grub:
kernel /boot/vmlinuz root=/dev/sda2 ro quiet splash vga=791

/etc/usplash.conf:
xres=1024
yres=768

Then:
sudo update-initramfs -u

THANK YOU! Now my splash screen has full, radient color again!

---

### Post by xiaoxin on 2007-01-14
I have tried everything but still i dont have a correct splash screen, and if i follow the guide on the other thread or use the theme from that repository i have no boot splash at all.

Any other suggestions to fix this?

---

