---
title: "ubuntu auto update -- screwed up something -- yay!!"
date: 2006-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jonathan987 on 2006-09-15
linux noob here....stick with me

I went to auto update my system which I would think should be an easy task, but then reminded my self that it's linux I'm using :)

my setup: 2x80gigs on raid1 array , this is where ubuntu is installed. I then have 4x500gig on raid5 array.  No other OS's....

The update:
E: linux-image-2.6.15-26-amd64-generic: subprocess post-installation script killed by signal (Interrupt)
E: linux-restricted-modules-2.6.15-26-amd64-generic: dependency problems - leaving unconfigured

the error(when auto updating):
Install a boot block using the existing /etc/lilo.conf? [Yes] y
Testing lilo.conf ...
An error occurred while running lilo in test mode, a log is
available in /var/log/lilo_log.10080. Please edit /etc/lilo.conf
manually and re-run lilo, or make other arrangements to boot
your machine.

the log file:
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/evms/.nodes/hda1'
Fatal: Only RAID1 devices are supported as boot devices


Advice anyone?

thanks in advance!

Jonathan

---

### Post by kuja on 2006-09-15
Well, errors aren't good, but unless you have been playing with things lilo probably isn't even installed. Ubuntu uses grub by default for the bootloader.

---

### Post by Jonathan987 on 2006-09-16
well, seeing as this error didn't do anything bad.... I now rebooted the machine and I cannot connect to it anymore.....riiiiiight

the catch is, I'm in Germany and the machine is in Canada. thanks for you help.....=D> 

does anyone else know what lilo does, what this error means and how I can get my friend (who has the server) to fix it?

Thanks,

Jonathan

oh, and while I'm asking, how does he does he edit the lilo config file (since it won't boot) so everything boots normally?

---

### Post by kuja on 2006-09-16
Lilo is another bootloader. Your system probably uses grub for a bootloader unless you've changed your setup to use lilo instead, which I wouldn't really recommend.

---

### Post by fatsheep on 2006-09-16
You'll most likely need to boot up on a LiveCD and then mount your linux partition in a folder so you can make repairs.

---

