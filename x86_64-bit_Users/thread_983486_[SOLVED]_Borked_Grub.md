---
title: "[SOLVED] Borked Grub?"
date: 2008-11-15
forum: x86 64-bit Users
---

### Post by John Jason Jordan on 2008-11-15
For the past couple of days I have been trying to fix my broken Hardy > Intrepid (x86_64) upgrade. I can boot and get X, but then the mouse and keyboard are dead (except I can Ctrl-Alt-F1 to a shell). Or I can just boot in Recovery mode and then to a Root command prompt. Either way the keyboard works in the shell; it just won't work in the GUI. And therefore I can't log in at the login screen. Also ethernet is not functioning.

But now I think I have found the source of all my troubles, except I don't know how to fix it.

I ran lsmod and found a module that I suspected might not be running properly. So I did a modprobe, only to be told that there was no modules file in the folder for 2.6.24-19. Sure enough, the file was not there. But there sure was a dandy modules file in the folder for 2.6.27-7. A quick "uname -a" revealed that I had booted to 2.6.24-19. Looking in /boot/grub/menu.lst reveals no such boot option. The menu.lst file correctly shows the new kernel for Intrepid (2.6.27-7). So then I rebooted and hit esc to get the menu. The menu on the screen lists only 2.6.24-19. The menu.lst file says only 2.6.27-7. WTF?

All my woes - ethernet not working, keyboard not working, mouse not working - are probably due to the fact that I am running the wrong kernel for the drivers installed by Intrepid.

I did "locate vmlinuz" and it found /vmlinuz and /boot/vmlinuz-2.6.27-7-generic. There are no other vmlinuz* files on the machine. 

I ran sudo update-grub, but it made no difference. The menu.lst file is the same (2.6.27-7) and the menu on screen still shows 2.6.24-19.

Intrepid x86_64 (updated from Hardy) is the only OS installed on the computer. 

I have a passing familiarity with grub, but this has me flummoxed. The
ghost of 2.6.24-19 refuses to leave. I'm about to call in a priest. Any
suggestions?

---

### Post by tenmoi on 2008-11-15
> **John Jason Jordan said:**
> For the past couple of days I have been trying to fix my broken Hardy > Intrepid (x86_64) upgrade. I can boot and get X, but then the mouse and keyboard are dead (except I can Ctrl-Alt-F1 to a shell). Or I can just boot in Recovery mode and then to a Root command prompt. Either way the keyboard works in the shell; it just won't work in the GUI. And therefore I can't log in at the login screen. Also ethernet is not functioning.

But now I think I have found the source of all my troubles, except I don't know how to fix it.

I ran lsmod and found a module that I suspected might not be running properly. So I did a modprobe, only to be told that there was no modules file in the folder for 2.6.24-19. Sure enough, the file was not there. But there sure was a dandy modules file in the folder for 2.6.27-7. A quick "uname -a" revealed that I had booted to 2.6.24-19. Looking in /boot/grub/menu.lst reveals no such boot option. The menu.lst file correctly shows the new kernel for Intrepid (2.6.27-7). So then I rebooted and hit esc to get the menu. The menu on the screen lists only 2.6.24-19. The menu.lst file says only 2.6.27-7. WTF?

All my woes - ethernet not working, keyboard not working, mouse not working - are probably due to the fact that I am running the wrong kernel for the drivers installed by Intrepid.

I did "locate vmlinuz" and it found /vmlinuz and /boot/vmlinuz-2.6.27-7-generic. There are no other vmlinuz* files on the machine. 

I ran sudo update-grub, but it made no difference. The menu.lst file is the same (2.6.27-7) and the menu on screen still shows 2.6.24-19.

Intrepid x86_64 (updated from Hardy) is the only OS installed on the computer. 

I have a passing familiarity with grub, but this has me flummoxed. The
ghost of 2.6.24-19 refuses to leave. I'm about to call in a priest. Any
suggestions?

I think you should remove the 2.6.24.x. apt-get remove --purge linux-image-2.6.24.x, linux-headers-2.6.24.x, i.e everything x.24.-related.

---

### Post by John Jason Jordan on 2008-11-16
> **tenmoi said:**
> I think you should remove the 2.6.24.x. apt-get remove --purge linux-image-2.6.24.x, linux-headers-2.6.24.x, i.e everything x.24.-related.

Thanks for the suggestion. However, when I do "locate 2.6.24-19" the only things that come up are .deb files for its installation. 

The confusing part is that it still boots to that kernel, and that kernel is the only kernel in the boot screen. Yet the /boot/grub/menu.lst file shows the correct 2.6.27-7 kernel, and the only vmlinuz file is 2.6.27-7.

Somewhere there must be a vmlinuz file for 2.6.24-19, but I'll be darned if I can find it.

I know the problem is in the MBR. But the problem is complicated by the fact that the /boot folder is on a RAID array. The array is composed of /dev/sda and /dev/sdb (two identical 320 GB SATA-2 drives). These are the only drives in the computer. Therefore the MBR must be on one of them.

I did "sudo grub-install /dev/sda" and it said it found the boot files for 2.6.27-7 and installed the MBR on /dev/sda. But when I rebooted the menu still offered only 2.6.24-19.

Here is the relevant part of the menu.lst file:

title	Ubuntu 8.10, kernel 2.6.27-7-generic
root	(hd0,0)
kernel	/boot/vmlinuz-2.6.27-7-generic root=/dev/md1 ro quiet splash
initrd	/boot/initrd.img-2.6.27-7-generic

I also tried installing to hd0 ("sudo grub-install /dev/hd0") and that also appeared to work, yet it did not change what's on the MBR.

I hope someone can tell me what I am doing wrong here.

---

### Post by tenmoi on 2008-11-16
I cannot offer any help. out of any idea. but as a last resort I think you can possibly reinstall the .27.x stuff and see if it gets rid of the 24.x . Oh and browse into the boot folder and delete any traces of the 24.x there and see if it works.

---

### Post by larryweeks on 2008-11-16
Ive got a similar problem, I crash on startup, what I found was that the cd was not being read as I loaded, it could not find it. The cd is a new sata drive. It is evidently not there to ubuntu.

This was after all my system crashed on a load to 8.10 from a working 8.04, which took a long time to set up as I have nvidia drivers, when I loaded it wouldnt accept them, then it failed to reload.

I have gone back to 7.04 which worked really great, in fact it loaded perfectly from the drive...explain that, Im not upgrading till they get these bugs out..

It should be easy to load and no hardware problems. 

Supportsage

---

### Post by John Jason Jordan on 2008-11-27
> **John Jason Jordan said:**
> Thanks for the suggestion. However, when I do "locate 2.6.24-19" the only things that come up are .deb files for its installation. 

The confusing part is that it still boots to that kernel, and that kernel is the only kernel in the boot screen. Yet the /boot/grub/menu.lst file shows the correct 2.6.27-7 kernel, and the only vmlinuz file is 2.6.27-7.

Somewhere there must be a vmlinuz file for 2.6.24-19, but I'll be darned if I can find it.

I know the problem is in the MBR. But the problem is complicated by the fact that the /boot folder is on a RAID array. The array is composed of /dev/sda and /dev/sdb (two identical 320 GB SATA-2 drives). These are the only drives in the computer. Therefore the MBR must be on one of them.

I did "sudo grub-install /dev/sda" and it said it found the boot files for 2.6.27-7 and installed the MBR on /dev/sda. But when I rebooted the menu still offered only 2.6.24-19.

Here is the relevant part of the menu.lst file:

title	Ubuntu 8.10, kernel 2.6.27-7-generic
root	(hd0,0)
kernel	/boot/vmlinuz-2.6.27-7-generic root=/dev/md1 ro quiet splash
initrd	/boot/initrd.img-2.6.27-7-generic

I also tried installing to hd0 ("sudo grub-install /dev/hd0") and that also appeared to work, yet it did not change what's on the MBR.

I hope someone can tell me what I am doing wrong here.

OK, I finally fixed it, with the help of a local Linux guru. He said to run:

```
sudo grub-install --root-directory=/dev/md1 /dev/sda
```

But that command gave me an error that /dev/md1 was not a directory. I changed to just / and the command worked. That is, then I got the proper kernel in the boot menu, but when I tried to boot I got Error 15: File not found. I tried editing the line on the fly (in the boot menu) by changing root=/, root=/boot and root=/dev/md1, but still no joy.

Even though it wouldn't boot at all, I felt this was progress. At least I managed to change the instructions in the MBR.

Eventually it took five different rescue CDs and several hours of my time, but I finally did it. The video was still not correct, but I fixed that later. The important thing was that Intrepid was finally booting to the GUI and the mouse, keyboard and network were all working perfectly.

Now, for those who are curious about what happened, it seems that the Hardy > Intrepid upgrade updated the /boot files, but only on sda1, not on sdb1. I had those two in a RAID1 array as MD1. Even after I used the code above and got the 2.6.27-7 kernel into the MBR, it could not find the files it needed to boot.

I finally discovered that the correct files were on sdb1 but not on sda1 when I tried a Knoppix 5.01 live CD. This version of Knoppix automatically mounts all devices, except it does not understand RAID, so it mounted them as individual file systems. Looking at them both side by side I quickly realized where the 2.6.24-19 kernel was coming from - sda1. All the boot files on sda1 were the old Hardy files.

Knoppix mounts the partitions read-only and, even as root, I couldn't seem to change that, so I shuffled through various other rescue CDs until I found one that would mount both devices and let me read/write to them. I used the scary command line to delete all the files in sda1's /boot folder, then copied them over from sdb1's boot folder. On rebooting (with fingers tightly crossed) Ubuntu Intrepid came up and all was well again.

---

