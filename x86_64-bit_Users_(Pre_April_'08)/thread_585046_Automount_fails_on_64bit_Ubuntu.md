---
title: "Automount fails on 64bit Ubuntu?"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by wolpert on 2007-10-21
I just changed over from 32-bit 7.4 to 64-bit 7.10 with few problems. But I did notice that the automounter is not working for usb flash drives that used to work on 7.04 32-bit, and still work on 32-bit 7.10. It seems to only fail with 64-bit 7.10. I can manually mount it just fine; its just the auto mounter that does not work...

Its a 'fat' file system on the usb drive. Same thing happens for my cowon mp3 player and psp... requires manual mounting on 7.10 64-bit where they automount on 7.10 32-bit

Thanks

fyi, /var/log/messages gives this:
Oct 21 08:19:22 desktop kernel: [209344.778686] usb 1-2.7: new high speed USB device using ehci_hcd and address 7
Oct 21 08:19:22 desktop kernel: [209344.854575] usb 1-2.7: configuration #1 chosen from 1 choice
Oct 21 08:19:22 desktop kernel: [209344.854763] scsi6 : SCSI emulation for USB Mass Storage devices
Oct 21 08:19:27 desktop kernel: [209348.942836] scsi 6:0:0:0: Direct-Access     Memorex  Mini TravelDrive 6.16 PQ: 0 ANSI: 0 CCS
Oct 21 08:19:27 desktop kernel: [209348.943546] scsi 6:0:0:1: CD-ROM            Memorex  Mini TravelDrive 6.16 PQ: 0 ANSI: 0
Oct 21 08:19:27 desktop kernel: [209348.946606] sd 6:0:0:0: [sdf] 1994751 512-byte hardware sectors (1021 MB)
Oct 21 08:19:27 desktop kernel: [209348.947569] sd 6:0:0:0: [sdf] Write Protect is off
Oct 21 08:19:27 desktop kernel: [209348.950692] sd 6:0:0:0: [sdf] 1994751 512-byte hardware sectors (1021 MB)
Oct 21 08:19:27 desktop kernel: [209348.952223] sd 6:0:0:0: [sdf] Write Protect is off
Oct 21 08:19:27 desktop kernel: [209348.952233]  sdf: sdf1
Oct 21 08:19:27 desktop kernel: [209348.954007] sd 6:0:0:0: [sdf] Attached SCSI removable disk
Oct 21 08:19:27 desktop kernel: [209348.954053] sd 6:0:0:0: Attached scsi generic sg5 type 0
Oct 21 08:19:27 desktop kernel: [209348.954126] scsi 6:0:0:1: Attached scsi generic sg6 type 5
Oct 21 08:19:27 desktop kernel: [209348.901667] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray

---

### Post by wolpert on 2007-10-21
Found the problem, it was because 'usbmount' is not installed by default on 64-bit ubuntu, which is really weird. The fix was do do this by command line:

sudo apt-get install usbmount

and answer 'yes' to the other packages it wants to install, and reboot when done. 

No idea why 64-bit does not include this by default, so I think its still a 'bug' with the amd64 bit version of ubuntu desktop install cd.

If someone has a better solution to this problem, please post.

Thanks
-Ned

---

### Post by Tanker Bob on 2007-10-26
Its not just 64-bit. I also fails in 32-bit gutsy. Automount is a legacy program that has other side effects like making dummy USB entries in /media for empty slots. I've found that Dolphin's Storage Media display will see the detected but unmounted devices. Selecting the newly plugged in device will cause it to be mounted and seen by the rest of Kubuntu. That's the only work-around I've found and I worked on it for about 6 hours yesterday. This is definitely a bug, but seems limited to vfat formattted mass storage devices.

---

### Post by wolpert on 2007-10-26
If automount is considered legacy, what replaces it in the new install? I can't imagine that this is intended considering how people mount flash cards from camera... most of that is vfat, right?

---

### Post by Tanker Bob on 2007-10-26
> **wolpert said:**
> If automount is considered legacy, what replaces it in the new install? I can't imagine that this is intended considering how people mount flash cards from camera... most of that is vfat, right?
The new approach uses HAL and pmount. These trigger the icons on the desktop, etc. Just to check, I ran automount last night and it did not solve my problem. Dolphin remains the most reliable workaround for me.

Flash cards and sticks are indeed vfat. After much testing, I've found that only vfat removable media refuses to mount automatically on my system. My USB Bluetooth works fine, as does my USB printer.

---

### Post by wolpert on 2007-10-26
That is very odd... as it did work for me once I added automount on my fresh 64bit 7.10 install, with a vfat usb drive.

I need to test this more.  BTW, my 32bit 7.10 install was an upgrade from 7.04, not fresh. The vfat 'stuff' works fine there.

More info as I find it...

---

### Post by wolpert on 2007-10-26
BTW, I see you said about running 'automount'.  Did you try to install usbmount?  (I don't know if those are the same things)

---

### Post by Tanker Bob on 2007-10-26
> **wolpert said:**
> BTW, I see you said about running 'automount'.  Did you try to install usbmount?  (I don't know if those are the same things)
I did install usbmount at one time to see if it helped. I tried so many things that I don't really remember what happened, but I do remember that it didn't solve the issue satisfactorily. I uninstalled it right away so that I wouldn't forget.

One caution. In playing with these, at one point I installed something (one of the auto mounting or usb utilities)  that caused kde-desktop including kde apps, network support, and the restricted kernel modules to all uninstall. I didn't catch on right away because of the way Adept is setup to provide little information by default. I was used to Kpackage which always shows you what will happen next. It took the better part of an hour to reconstruct my system and I hope that I've succeeded in restoring all functionality.

---

### Post by moron on 2008-01-03
Just a followup to note that the global uninstall bug hit me previously as well, I believe it is triggered by choosing "re-install" on a package.  I am now a tad afraid when using Adept as it took a lot of work to get my current install back (basically had to completely install KDE as things were pretty messed up by the time I realized what was happening).

I'm also currently fighting with the automount USB issue though in my case what happens is that the device never "settles" (dmesg talks about waiting for the device to settle) and the SCSI device entry never appears under /dev.

Cheers

---

