---
title: "Xen and vnc console on gutsy domu"
date: 2008-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by accod on 2008-01-09
Hi all,

I've got a new install of gutsy and I'm trying to get a vnc console working on a domU.  As far as I know, xen is installed correctly and I'm able to create a xen domU with xen-create-image that I can get a text console to and ssh.

If I shut the domU down and add vnc=1 to its config, I don't get a listening vnc port next time it is started.  My domU config is:

kernel      = '/boot/vmlinuz-2.6.22-14-xen'
ramdisk     = '/boot/initrd.img-2.6.22-14-xen'
memory      = '1536'

root        = '/dev/sda1 ro'
disk        = [ 'file:/xenimages/domains/test/disk.img,sda1,w', 'file:/xenimages/domains/test/swap.img,sda2,w' ]

name        = 'test'

vif         = [ 'ip=192.168.76.40' ]

on_poweroff = 'destroy'
on_reboot   = 'restart'
on_crash    = 'restart'

extra = ' TERM=xterm xencons=tty console=tty1'
sdl=0
vnc=1
vncdisplay=3
vncconsole=1
vncpasswd='qwerty'
vnclisten="0.0.0.0"
#cdrom='/dev/cdrom'
#vncviewer=0

--
The above vncconsole, vncdisplay, etc have all been commented out and adjusted but still no joy.

Obviously from the config above, the domU is a paravirtualised guest and not hvm (cpu doesn't support vmx) but I don't think that should stop me from getting a vnc console - it doesn't with other dom0 distro's I've used.

In case it is related, xenman is also unable to display a console to my domU.

Any ideas?

Thanks in advance.

---

### Post by EnkiduinNZ on 2008-01-09
I've not tried to run vnc as a console, but why not try it as a normal app to start with?

On the 'guest' run

vncserver -depth 24 -geometry 1024x768

On the 'host' run 

vncviewer my-guest:1

This will at least tell you if the vnc works properly.

Do you have X installed? I presume that you have because vnc would prereq it.

Cheers,

Cliff

---

### Post by accod on 2008-01-10
Thanks for the reply EnkiduinNZ.

Yep, that's what I think I'm going to have to do.  Thought I'd ask though because having the xen vnc console is quite sweet.

---

