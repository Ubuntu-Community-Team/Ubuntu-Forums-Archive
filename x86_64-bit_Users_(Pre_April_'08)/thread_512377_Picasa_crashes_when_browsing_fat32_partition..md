---
title: "Picasa crashes when browsing fat32 partition."
date: 2007-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by jimdaworm on 2007-07-29
I am using Kubuntu 7.04 amd64  (2.6.20-16-generic kernel)  I installed Picasa 2 using Automatix 2.  It loads fine and can browse my photos in my home folder.

As soon as I try to browse my fat32 partition that has all my photos it crashes.  I have had a look in the dmesg and I get this:
> [  406.090585] ioctl32(wdi.exe.so:6089): Unknown cmd fd(9) cmd(82187201){02} arg(7fabed10) on /home/adam/picasa/wine/drive_c/windows/system32
[  406.091091] ioctl32(wdi.exe.so:6089): Unknown cmd fd(9) cmd(82187201){02} arg(7fabed10) on /home/adam/picasa/wine/drive_c/windows/system
[  406.091561] ioctl32(wdi.exe.so:6089): Unknown cmd fd(9) cmd(82187201){02} arg(7fabed10) on /home/adam/.picasa/drive_c/windows
[  406.092078] ioctl32(wdi.exe.so:6089): Unknown cmd fd(9) cmd(82187201){02} arg(7fabed10) on /home/adam/picasa/wine/drive_c/windows/system32
[  406.092597] ioctl32(wdi.exe.so:6089): Unknown cmd fd(9) cmd(82187201){02} arg(7fabed10) on /home/adam/.picasa/drive_c/windows
[  406.093078] ioctl32(wdi.exe.so:6089): Unknown cmd fd(9) cmd(82187201){02} arg(7fabed10) on /home/adam/.picasa/drive_c/Program Files
[  406.093350] ioctl32(wdi.exe.so:6089): Unknown cmd fd(9) cmd(82187201){02} arg(7fabed10) on /home/adam/.picasa/drive_c/Program Files/Picasa2
[  406.137236] ioctl32(wdi.exe.so:6089): Unknown cmd fd(9) cmd(82187201){02} arg(7fabe3c0) on /home/adam/picasa/wine/lib/wine


Any ideas?

---

### Post by jimdaworm on 2007-07-30
Nothing? :(:popcorn:

---

### Post by Mr. Swiveller on 2007-07-31
I had the same problem until I copied the Picasa folder to the Program Files folder in my regular Wine install, and ran the application from there. Could you try that?

Cheers,

Swiveller

---

### Post by jimdaworm on 2007-10-19
Thanks a lot for your reply sorry I didnt recieve an email telling me you had!  I think I am going to wait a bit and hope that Google comes out with a linux version of Picasa that works.:guitar:

---

