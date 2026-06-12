---
title: "MOL on Dapper Drake not running"
date: 2006-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rob Friefeld on 2006-04-05
I installed MOL per directions in the wiki. The first "startmol -X" ran fine. Then I installed the drivers. Now MOL quits with an error message. Note: I gave MOL 512MB to run (from 1GB physical RAM) and changing that didn't make a difference. Any suggestions?

Here is the console output:

> Mac-on-Linux 0.9.70 [Nov 20 2005 11:45]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Running in PowerPC 7400 mode, 512 MB RAM
Timebase: 33.21 MHz, Bus: 132.86 MHz, Clock: 933 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not open '/var/lib/mol/x11.kbd'
Fullscreen video on VT 8.
Could not open '/var/lib/mol/console.kbd'
Video driver(s): [xvideo] [console_video]

     640* 480, depth 8,32   { 0.0 } Hz
     800* 600, depth 8,32   { 0.0 } Hz
    1024* 768, depth 8,32   { 0.0 } Hz
    1152* 864, depth 8,32   { 0.0 } Hz
    1280*1024, depth 8,32   { 0.0 } Hz
    1280*1024, depth 8   { 60.0, 60.0 } Hz
    1600*1200, depth 8,32   { 0.0 } Hz

ALSA sound driver (device 'default')
MOL SCSI controller registered


    <No SCSI Devices>

    CD   /dev/cdrom       CD-ROM         <read-only>   ------
    HFS+ /dev/hda5        Fornax         <rw> 29999 MB
No volumes found in '/dev/hdb'
No volumes found in '/dev/sda'
No volumes found in '/dev/sdb'


>> ==================================================
>> MacOS X Boot Loader 0.9.70
>> Candidate boot volume: /mol-blk@0/disk@0:0
>> /mol-blk@0/disk@0:0,\mach_kernel (4330320 bytes)
>> Old mkext timestamp (or safe-boot)
>> Loading from /mol-blk@0/disk@0:0,\System\Library\
>> --> Boot loader failure: Out of memory
cleaning up...
Terminating threads...
DONE


---

### Post by thomasxie on 2006-04-06
My mol can't start either after I installed the driver. It works fine without install the mol driver. But I don't know how to uninstall the driver.

---

### Post by hentaidan on 2006-04-06
Rob Friefeld, try the modified version of the bootloader @ [http://www-user.rhrk.uni-kl.de/~nissler/mol/](http://www-user.rhrk.uni-kl.de/~nissler/mol/)

---

### Post by Rob Friefeld on 2006-04-07
Sheer genius, Mattias! It works. Many thanks. How did you do it?

---

### Post by trash on 2006-07-04
[QUOTE=hentaidan]Rob Friefeld, try the modified version of the bootloader @ [http://www-user.rhrk.uni-kl.de/~nissler/mol/](http://www-user.rhrk.uni-kl.de/~nissler/mol/)[/QUOTE]


I have gzip installed but it keeps telling me that the file format is not recognized... not even sure it will help but nothing else has worked so far, osx stalls everytime between the grey boot screen and the very end of the blue startup screen.

---

### Post by trash on 2006-07-04
DOH!!!! still haven't solved the gzip issue, but I just found a cd in my drive which was perventing osx from booting.. removing it was the cure!

---

