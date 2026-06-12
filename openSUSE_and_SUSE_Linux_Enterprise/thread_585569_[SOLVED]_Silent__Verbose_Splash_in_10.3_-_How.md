---
title: "[SOLVED] Silent / Verbose Splash in 10.3 - How?"
date: 2007-10-21
forum: openSUSE and SUSE Linux Enterprise
---

### Post by coldstatue on 2007-10-21
I tried editing grub/menu.lst as per [http://en.opensuse.org/SDB:Changing_the_Splash_Screen's_Default_Settings](http://en.opensuse.org/SDB:Changing_the_Splash_Screen's_Default_Settings)

as well as grub.conf when that didn't work.

I installed SuSE after Ubuntu, and left grub up to Ubuntu. I didn't let SuSE do anything automatically with grub, I added it manually. 

here is my menu.lst

```

#boot=/dev/sda
default=0
timeout=11
#splashimage=(hd1,1)/boot/grub/splash.xpm.gz
#hiddenmenu

gfxmenu /boot/grub/message.blusplash

title		Ubuntu Feisty Fawn
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=356b68b5-97a1-45aa-b8e2-22c278102467 ro splash text_color=e73f12 vga=792
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
       
title openSUSE 10.3
	root (hd1,2)
kernel  /boot/vmlinuz-2.6.22.9-0.4-default root=UUID=55c7fd49-d879-4833-a8b8-5675d6554474  splash=silent
initrd		/boot/initrd-2.6.22.9-0.4-default


	
title Windows XP
	rootnoverify (hd0,0)
	chainloader +1
```

What do i need to add here?

I am still getting the native black screen with grey writing. 

The page above gives this advice:

[B]"Problems with the Splash Screen

If after setting the parameter splash=verbose, the black console is loaded instead of the splash screen, use the command mkinitrd to create a new initial ramdisk and make sure the "splash picture" is included in it. If you use LILO as your boot loader, execute the command lilo later to rewrite the boot loader. "[/B]

When I run mkinitrd in SuSE, I get this:

```
 # mkinitrd

Kernel image:   /boot/vmlinuz-2.6.22.9-0.4-default
Initrd image:   /boot/initrd-2.6.22.9-0.4-default
Root device:    /dev/disk/by-id/scsi-SATA_WDC_WD1500AHFD-_WD-WMAP41204306-part3 (/dev/sdb3) (mounted on / as ext3)
Kernel Modules: processor thermal scsi_mod libata sata_sil pata_atiixp fan jbd mbcache ext3 edd sd_mod usbcore ohci-hcd uhci-hcd ehci-hcd ff-memless hid usbhid
Features:       block usb resume.userspace resume.kernel
17213 blocks
2007-10-21 14:24:36 ERROR: Bootloader::Library::SetLoaderType: Initializing for unknown bootloader none
2007-10-21 14:24:36 ERROR: Bootloader::Core::ListFiles: Running generic function, it should never be called
2007-10-21 14:24:36 ERROR: Bootloader::Core::ParseLines: Running generic function, it should never be called

```

Would I need to run that in Ubuntu, since that is the OS controlling GRUB? I am a bit spooked to do it, as my GRUB is working perfectly. I also do not know how to check that the splash image is included, or where to get one if it isn't.

Thanks

---

### Post by dca on 2007-10-22
On older Dell laptop(s) the SuSE splash was not able to be displayed because it didn't have the ability to display larger than 8bit color when the splash was in 16 bit or something thereabouts... It was a framebuffer issue on the older computers.
 
You can change the boot display settings if you're computer can support it by adding the vga = 0x317 or 0x314 parameter to the kernel line before the splash=... 
 
Towards the bottom of the page in this link shows hex-code settings.  Now, I may be wrong w/ what you're going through it could be completely different than the problems I had w/ 10.2 a year back.
 
[http://gentoo-wiki.com/HOWTO_Framebuffer:Bootsplash:Grubsplash](http://gentoo-wiki.com/HOWTO_Framebuffer:Bootsplash:Grubsplash)
 
 
I would probably leave it alone if it runs alright, though.  The 'mkinitrd' requires a size spec I believe, ie:  mkinitrd-s 1024 x 768 you'll have to research that one...

---

### Post by coldstatue on 2007-10-23
Cool, thanks. i will give it a shot, but it might have to wait till this weekend. I will post back with results and mark solved if necessary.

---

### Post by coldstatue on 2007-10-23
Well, it didn't work. Maybe because I didn't have SuSE install a bootloader. Maybe there's no image there. I'm not about to mkinitrd in Ubuntu. I might try to install splashy to SuSE, as sugested at the susecommunity site.

Thanks,.

---

### Post by coldstatue on 2007-10-24
I ran makeinitrd on the suse part., and then installed splashy (with the dependencies of dependencies of interdependencies.)

It worked!

---

