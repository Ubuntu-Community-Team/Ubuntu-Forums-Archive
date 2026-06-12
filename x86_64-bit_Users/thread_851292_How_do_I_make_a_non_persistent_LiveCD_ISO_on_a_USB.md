---
title: "How do I make a non persistent LiveCD ISO on a USB thumbdrive persistent?"
date: 2008-07-06
forum: x86 64-bit Users
---

### Post by DanJC on 2008-07-06
Hey all.

This is my first post on the Ubuntu forums.  I'm quite new to Linux, and to Ubuntu for that matter.  I like what I've seen from Ubuntu, and I'd like to have persistent memory so I can Ubuntu with me, and still have my settings and files.

I tried the tutorial on Pendrivelinux.com, but all that really did was screw up my flash drive so I had to call tech support to fix it. :(

I also tried a full blown HDD install on the drive, but all that happened was that I kept getting Error 17s.

So, if possible, please explain to me, in the simplest way possible, how to make this flash drive have persistent memory.

I have a SanDisk Cruzer Micro 4GB.  I also have Hardy Haron burned to a disk, if that's necessary.

Thanks much!

EDIT: I should probably mention what I have tried on Pendrivelinux.

Ubuntu 8.04 Non persistent install  END RESULT: A functioning version of Ubuntu, but no persistence.

Ubuntu 8.04 Persistent install via Windows  END RESULT: All went well until I had to switch to Windows.  After executing fixu.bat, folder USB-Ubuntu was not created, therefore stalemate.

Ubuntu 8.04 Persistent install via Live CD.  END RESULT: Ubuntu would not boot, asking me for a floppy disk (I don't have a floppy drive).  Attempting the repair via Lilo download began well, but ended with an Permission Denied message.

Ubuntu 8.04 HDD install to USB  END RESULT: Error 17 message upon boot, could not continue.

---

### Post by cariboo on 2008-07-06
The way to do this is disconnect your internal hard drive. Boot from the LiveCD and install on your USB key, Install grub on the device, and you should be able to boot from you USB device.

Jim

---

### Post by DanJC on 2008-07-06
Hang on.  I really don't want to mess with the computer hardware, mostly because I have no idea what I'm doing.  Why do I need to disconnect the hard drive?

---

### Post by soxs on 2008-07-06
It's the easiest way to make sure you won't kill your MBR aswell your private data plus current system ;-)

Note: If you want to boot successfully, you must make sure the boot order is set correctly (after you plugged your hds back in and you're going to test your protable ubuntu) (usb -> .. -> hd)

---

