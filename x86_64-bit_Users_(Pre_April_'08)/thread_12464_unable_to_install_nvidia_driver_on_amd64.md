---
title: "unable to install nvidia driver on amd64"
date: 2005-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by flanker on 2005-01-24
Hi guys,

The nvidia installer is failing while checking the opengl links, reporting that libGL.so.1.0.6629 was expected in /emul/ia32-linux/usr/lib/ but found in /usr/lib32/

After editing the xf86config and loading the nvidia module I can start X but I get bad screen corruption and the mouse cursor is an inch square of dots. Moving the mouse  over the blank sections of screen redraws whats missing.

glxgears is reporting 7500fps with the cpu (amd64 3200) at 100%.  The graphics card is a geforce 6600gt pci-e.

any ideas?

thanks.

-----------------------
# ls -l /emul/ia32-linux/usr/lib/
total 7528
lrwxrwxrwx    1 root     root           21 2005-01-24 22:27 libGLcore.so.1 -> libGLcore.so.1.0.6629
-rwxr-xr-x    1 root     root      7230360 2005-01-24 22:27 libGLcore.so.1.0.6629
-rw-r--r--    1 root     root          653 2005-01-24 22:27 libGL.la
lrwxrwxrwx    1 root     root           10 2005-01-24 22:27 libGL.so -> libGL.so.1
lrwxrwxrwx    1 root     root           17 2005-01-24 22:27 libGL.so.1 -> libGL.so.1.0.6629
-rwxr-xr-x    1 root     root       442592 2005-01-24 22:27 libGL.so.1.0.6629
lrwxrwxrwx    1 root     root           25 2005-01-24 22:27 libnvidia-tls.so.1 -> libnvidia-tls.so.1.0.6629
-rwxr-xr-x    1 root     root         2352 2005-01-24 22:27 libnvidia-tls.so.1.0.6629
drwxr-xr-x    2 root     root         4096 2005-01-24 22:27 tls


# ls -l /usr/lib32/libGL*
lrwxrwxrwx    1 root     root           21 2005-01-24 19:25 /usr/lib32/libGLcore.so.1 -> libGLcore.so.1.0.6629
-rwxr-xr-x    1 root     root      7230360 2005-01-24 21:21 /usr/lib32/libGLcore.so.1.0.6629
-rwxr-xr-x    1 root     root          652 2005-01-24 21:21 /usr/lib32/libGL.la
lrwxrwxrwx    1 root     root           12 2005-01-23 21:04 /usr/lib32/libGL.so.1 -> libGL.so.1.2
-rwxr-xr-x    1 root     root       442592 2005-01-24 21:21 /usr/lib32/libGL.so.1.0.6629
lrwxrwxrwx    1 root     root           27 2005-01-23 21:04 /usr/lib32/libGL.so.1.2 -> ../X11R6/lib32/libGL.so.1.2
lrwxrwxrwx    1 root     root           13 2005-01-23 21:04 /usr/lib32/libGLU.so.1 -> libGLU.so.1.3
lrwxrwxrwx    1 root     root           28 2005-01-23 21:04 /usr/lib32/libGLU.so.1.3 -> ../X11R6/lib32/libGLU.so.1.3

# ls -l /usr/lib/libGL*
lrwxrwxrwx    1 root     root           21 2005-01-24 22:27 /usr/lib/libGLcore.so.1 -> libGLcore.so.1.0.6629
-rwxr-xr-x    1 root     root      6675104 2005-01-24 22:27 /usr/lib/libGLcore.so.1.0.6629
-rw-r--r--    1 root     root          655 2005-01-24 22:27 /usr/lib/libGL.la
lrwxrwxrwx    1 root     root           10 2005-01-24 22:27 /usr/lib/libGL.so -> libGL.so.1
lrwxrwxrwx    1 root     root           17 2005-01-24 22:27 /usr/lib/libGL.so.1 -> libGL.so.1.0.6629
-rwxr-xr-x    1 root     root       600408 2005-01-24 22:27 /usr/lib/libGL.so.1.0.6629
lrwxrwxrwx    1 root     root           13 2005-01-24 22:09 /usr/lib/libGLU.so.1 -> libGLU.so.1.3
lrwxrwxrwx    1 root     root           26 2005-01-24 22:09 /usr/lib/libGLU.so.1.3 -> ../X11R6/lib/libGLU.so.1.3

---

### Post by hams on 2005-01-25
i think you may find more about this on the gentoo forums. forums.gentoo.org and i also think you can find some infromation about this on the nvnews.net site in their forums.

  i think this is a summation of the info:
  there's an issue in the 6629 driver and to get around it you can disable hardware acceleration and enable the SWCursor. Then i believe there is a bug reported for the xorg X11 code where there is corruption on the PCI-E bus.

  so i don't think there is any total solution to the issue.

---

### Post by flanker on 2005-01-25
Thanks Hams,

Reading the nv forum ( [http://www.nvnews.net/vbulletin/showthread.php?t=42597&page=1&pp=15](http://www.nvnews.net/vbulletin/showthread.php?t=42597&page=1&pp=15) ) it seems to be a problem with X rather than the nvidia driver and a patch has been submitted ( [https://bugs.freedesktop.org/show_bug.cgi?id=2322](https://bugs.freedesktop.org/show_bug.cgi?id=2322) ) which solves all the reported problems;

no cursor
no nvidia splash screen
truetype font corruption


Havent had chance to try it yet but will tomorrow.

---

### Post by hams on 2005-01-26
i just got ubuntu - warty working with my nForce4 / 6600 GT (pci-e)

you need the 6629 driver and in the XF86Config-4 file in the Device section
you need:

        Option          "NoRenderExtension"     "true"
        Option          "SWCursor"      "true"

  that works with gnome at least.

kevin

---

### Post by flanker on 2005-01-26
Todays build of xorg has the patch applied. This should allow hardware acceleration on AMD64 machines with PCI-E cards.

[http://xorg.freedesktop.org/X11R6.8.2/xorg-x11-6.8.1.903.tar.gz](http://xorg.freedesktop.org/X11R6.8.2/xorg-x11-6.8.1.903.tar.gz).


I wonder when Hoary will have this?

---

### Post by smdeep on 2005-01-26
[QUOTE=hams]i just got ubuntu - warty working with my nForce4 / 6600 GT (pci-e)

you need the 6629 driver and in the XF86Config-4 file in the Device section
you need:

        Option          "NoRenderExtension"     "true"
        Option          "SWCursor"      "true"

  that works with gnome at least.

kevin[/QUOTE]

Hi 

Where to get the 6629 driver from?
This is what I have installed and am unable to get X working.

Thanks in advance

---

### Post by daniels on 2005-01-26
I've already prepared packages of 6.8.1.903, despite the fact it's a public holiday.  They'll be called 6.8.1-1ubuntu12, for largely historical reasons, but should hit the archive tomorrow.

---

### Post by flanker on 2005-01-26
It dont get much faster then that. Cheers daniels

---

### Post by Tichondrius on 2005-01-30
Yes, I just installed hoary-amd64 and the pre-packaged nvidia driver worked well. Just install nvidia-glx (nvidia X windows driver), and run "nvidia-glx-config enable". This somehow causes the installation of "restriced modules" package which has the nvidia kernel module, which is also required. Alternatively, if you want to compile the kernel, you can install nvidia-kernel-source and use the kernel-package to create the nvidia-kernel package for your kernel ("make-kpkg modules_image").

When I upgraded from Nvidia driver v6111 to v6629 on woody-i386, I got a relatively big and noticeable improvement in frame rates in doom3 and ut2004 (at least 10-15%). But going from woody-i386 to hoary-amd64 (both on v6629 driver, same hardware), only gave a slight improvement (1% in doom3, a little more in ut2004). Of course, these games are still running a 32 bit binary, but if they were compiled for 64 bit, we could see more improvement.

BTW, the nvidia-settings tool crashes now in hoary-amd64. It works fine with woody-i386 (both with v6629 driver). Not sure if it's a 64 bit issue, or a hoary issue. I also like to know if anyone knows if you can use it to overclock the GPU/mem on the video card, just like in the Windows version of this tool.

Update: ut2004 actually comes with 64 bit binaries, in addition to the 32 bit version. It runs well in full 64 bit mode ! Although I can't really tell the difference in speed. Will try some benchmarks soon.

Update 2: I recorded a couple of my own demos in ut2004 (I couldn't find any good ones on the web) and played them back with the 32 bit and 64 bit game binaries. The demos are about 1 minute long each, and playing them gives quite consistent results, so the bottom line is there is hardly any difference at all, but looking closely at results, there is a very small but consistent advantage of 0.1-0.5% to the 32 bit version. Also the loading time of the game is a little shorter with the 32 bit binaries. So I'm dissapointed by not seeing any improvement with the 64 bit version, but at least it's not like what some people claimed to get huge slowdowns on 64 bit. For me it's practically the same. btw, another interesting observation is about running the game in a window rather then full screen - it doesn't slow down the game too much at all (only about 1%), so if you want to play this way, you don't have to worry about performance.

---

### Post by valadil on 2005-01-30
FWIW the nvidia-glx-enable script simply adds glx to your xorf.conf or XF86Config.

---

### Post by Tichondrius on 2005-01-30
[QUOTE=valadil]FWIW the nvidia-glx-enable script simply adds glx to your xorf.conf or XF86Config.[/QUOTE]

The nvidia-glx package installs the Nvidia binary driver for X-Windows (nvidia_drv.o) as well as X windows libraries which use the driver.  The script you refer to, nvidia-glx-config, is a convenience script, which mainly changes xorg/XF86 config file to use the binary nvidia driver, as well as making sure that the nvidia kernel module is present and loaded (the nvidia kernel module is installed by another package, nvidia-kernel or linux-restricted-modules).

This actually brings a question - is the Nvidia X driver, a 64 bit or 32 bit driver ? or does the package contain both? Can anyone please clarify that ?

---

### Post by flanker on 2005-01-31
I havent seen [Xorg 6.8.2 release candidate 3](http://xorg.freedesktop.org/X11R6.8.2/)  make its way to Hoary yet. Anyone have a timescale on this so that I can make use of my 6600gt pci-e card.

This patch should fix screen corruption problems for people using pci-e cards on amd64 platforms.



Xorg 6.8.2 release candidate 3
---------------------------------------

Bugzilla #2322: Fix corruption of PCI config BAR1 of native PCI-Express boards on 64-bit platforms. [Michael Yaroslavtsev]

---

### Post by daniels on 2005-01-31
6.8.1-1ubuntu12, which I uploaded about 10 hours ago, is almost entirely equivalent to 6.8.2rc3.  The only difference is that xorgversion.def says 6.8.1 + 6.8-branch CVS, or something, instead of 6.8.1.903.

---

### Post by flanker on 2005-01-31
The 6.8.1-1ubuntu12 update hasnt fixed the problem. 

It was only available for xorg-common, is this correct? I was expecting to see the update for xserver-xorg also.

Maybe I should move back to 32bit Hoary for now as it is not affected.

---

### Post by daniels on 2005-01-31
Failed to build on amd64/powerpc/ia64 -- will make a corrective upload later tonight.

---

### Post by flanker on 2005-02-14
Still the same.

---

### Post by Tichondrius on 2005-02-14
Yeah, it would be nice to have the fix for [this bug](http://www.ubuntuforums.org/showthread.php?t=15311)  (see link for a workaround).

---

### Post by daniels on 2005-02-15
Not until late this week, maybe early next week.

---

### Post by martijntje on 2005-02-15
[QUOTE=Tichondrius]The nvidia-glx package installs the Nvidia binary driver for X-Windows (nvidia_drv.o) as well as X windows libraries which use the driver.  The script you refer to, nvidia-glx-config, is a convenience script, which mainly changes xorg/XF86 config file to use the binary nvidia driver, as well as making sure that the nvidia kernel module is present and loaded (the nvidia kernel module is installed by another package, nvidia-kernel or linux-restricted-modules).

This actually brings a question - is the Nvidia X driver, a 64 bit or 32 bit driver ? or does the package contain both? Can anyone please clarify that ?[/QUOTE]
 The kernel module is 64 bit, of course. A 32 bit module wouldn't work with a 64 bit kernel AFAIK.

---

### Post by robbert on 2005-02-18
[QUOTE=daniels]Not until late this week, maybe early next week.[/QUOTE]
 did you allready fix the bug, that would be very nice ;) I just bought a Asus a8n sli deluze + XFX 6600gt and I really want to run Ubuntu on my new machine.

---

### Post by Tichondrius on 2005-02-18
[QUOTE=robbert]did you allready fix the bug, that would be very nice ;) I just bought a Asus a8n sli deluze + XFX 6600gt and I really want to run Ubuntu on my new machine.[/QUOTE]
 You can run 32-bit (i386) hoary on your machine relatively easily (you'll still need to install the nvidia-glx package from text mode, cause the default drivers will not work).  If you install the 64-bit version (amd64), you'll have to use the workaround I mentioned by adding options in the Xorg.conf file, or wait for this bug fix.

I suggest you forget about installing warty as Ubuntu's warty repositories don't have the new nvidia drivers which support the 6600/gt cards (although you could still download them directly from nvidia).

---

### Post by pwe on 2005-02-18
hello!
how can I do this "Reboot using "recovery mode" option in the grub menu, which doesn't start X-windows" - i didnt instal Ubuntus GRUB - I have my own GRUB - what i need to write in menu.lst??? please help me! 

or command line:
grub> root (hd0,12)
grub> kernel /boot/vmlinuz root=/dev/sda13
grub> initrd /boot/initrd 

what args???

thanks

ps sorry for my english!! :)

---

### Post by Tichondrius on 2005-02-18
[QUOTE=pwe]hello!
how can I do this "Reboot using "recovery mode" option in the grub menu, which doesn't start X-windows" - i didnt instal Ubuntus GRUB - I have my own GRUB - what i need to write in menu.lst??? please help me! 

or command line:
grub> root (hd0,12)
grub> kernel /boot/vmlinuz root=/dev/sda13
grub> initrd /boot/initrd 

what args???

thanks

ps sorry for my english!! :)[/QUOTE]
 You can append "single ro" to the kernel line to boot into "single user" mode , which doesn't start X.  So you can either create a new entry in your menu.lst, or just hit escape during the boot to see the grub menu, then highlight the entry above, and press "e" to edit it, and then add "single  ro" manually on the kernel line. Then hit "b" to boot. This will only take effect for that one boot.

---

### Post by pwe on 2005-02-18
thanksss!! its working!:) standard i work on ARCHlinux but i wont to use 64bits so i think ubuntu is the best choice:) \\:D/ 

bye

---

### Post by robbert on 2005-02-20
[QUOTE=Tichondrius]You can run 32-bit (i386) hoary on your machine relatively easily (you'll still need to install the nvidia-glx package from text mode, cause the default drivers will not work).  If you install the 64-bit version (amd64), you'll have to use the workaround I mentioned by adding options in the Xorg.conf file, or wait for this bug fix.

I suggest you forget about installing warty as Ubuntu's warty repositories don't have the new nvidia drivers which support the 6600/gt cards (although you could still download them directly from nvidia).[/QUOTE]
I know that I don't get the problem when running i386, but I want to run amd64. I know that I have to wait for the fix, but how long does it take before the fix get released?

---

### Post by Tichondrius on 2005-02-20
Even without the fix, you could still have your hoary-amd64 running perfectly (well, almost) with the latest nvidia drivers. If you add the "SWCursor" & "NoRenderExtension" options to your xorg.conf file, it works fine, and you still get top performance in 3D apps. This is working perfectly for me as well as many other people. you can follow the instructions the the second post in [this thread](http://www.ubuntuforums.org/showthread.php?t=15311)  on how to install the nvidia drivers and modify xrg.conf to avoid the bug in hoary-amd64.

---

### Post by Tichondrius on 2005-03-01
[QUOTE=daniels]Not until late this week, maybe early next week.[/QUOTE]

Thanks !!!!!!!! it's working now after I did apt-get update

---

### Post by paTt3rN R3CoGnItIon on 2005-05-18
I'm the proud owner of an ASUS A8N SLI Deluxe mobo.  I see that several people in this thread have reported that everything works in 5.04 except for maybe nvidia or soundblaster 24 bit.
<p>
But when I booted the live distro of 5.04 for AMD64 I couldn't connect to the Internet via my router/switch. So my question is whether anyone can offer tips/guidance on getting Ubuntu to recognise the proprietary ethernet NIC in this mobo?
<p>
If not I may have to just pop in a standard, generic PCI NIC card (this is what I have previously had to resort to with other LINUX distros on other mobos with integrated ethernet/NICs.) But if possible I'd like to avoid wasting the onboard ethernet/NIC and unnecessarily taking up a PCI slot.

Thanks for any help anyone can provide!

P.S. I do plan to install the HDD based version but I wanted to sort this issue out with the Live version first in case it's easier to set things up correctly during the initial install.

---

