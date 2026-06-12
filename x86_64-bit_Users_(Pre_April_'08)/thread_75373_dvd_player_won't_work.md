---
title: "dvd player won't work"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by gsaathoff on 2005-10-13
Hey all,

I can't get my DVD/RW drive to play or record to DVD's.  The drive is also a CD/RW and CD-ROM/RW functions work fine.  Ubuntu seems to recognize that the drive is DVD capable.

I have tried mounting DVD's as iso9660 and cannot read them.  When I do, dmesg gives me this output:

[61539.417120] end_request: I/O error, dev hdd, sector 64
[61539.417214] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
[61539.422136] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[61539.422143] hdd: packet command error: error=0x40 { LastFailedSense=0x04 }
[61539.422148] ide: failed opcode was: unknown
[61539.422840] ATAPI device hdd:
[61539.422843]   Error: Hardware error -- (Sense key=0x04)
[61539.422847]   Focus servo failure -- (asc=0x09, ascq=0x02)
[61539.422852]   The failed "Read Cd/Dvd Capacity" packet command was: 
[61539.422855]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "

when trying to play a dvd in mplayer I get this output:

MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2


CommandLine: '-v' 'dvd://'
get_path('font/font.desc') -> '/home/graham/.mplayer/font/font.desc'
font: can't open file: /home/graham/.mplayer/font/font.desc
font: can't open file: /usr/local/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/graham/.mplayer/input.conf'
Can't open input config file /home/graham/.mplayer/input.conf: No such file or directory
Can't open input config file /usr/local/etc/mplayer/input.conf: No such file or directory
Falling back on default (hardcoded) input config
get_path('.conf') -> '/home/graham/.mplayer/.conf'
Playing dvd://.
get_path('DVDKeys') -> '/home/graham/.mplayer/DVDKeys'
Reading disc structure, please wait...

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)

~~

IDE-SCSI and DMA are enbled, and I am using the latest version of "breezy".  Synaptic shows that all packages are up to date.  

Maybe it will help to note that I had weird problems burning CD's at first, and in order to get it to work I have to specify --dev=/dev/hdd at the command line.  cdrecord --scanbus does not see my drive unless I specify this.

Anyone have ideas about this?

Thanks,
Graham

---

### Post by diska on 2005-10-13
Drop the IDE-SCSI or specify your drive as a a scsi device, /dev/sda probably

---

### Post by gsaathoff on 2005-10-13
hey.  thanks for the tip.  how do i specify my drive as a scsi device?

thanks,
-g

---

