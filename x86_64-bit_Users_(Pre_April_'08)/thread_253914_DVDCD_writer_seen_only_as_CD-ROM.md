---
title: "DVD/CD writer seen only as CD-ROM"
date: 2006-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by KimJarvis on 2006-09-09
Although I can read CDs,DVDs I cannot write them.

cdrecord -scanbus does not show my CD drive, however dmesg shows it to be on /hda.  Other posts (about red hat) indicated that I sould check to see if the ide-scsi kernel module is loaded.  It is not.  I am unsure how to proceed.:( 

kim@shuttle:/mnt$ sudo cdrecord -scanbus
cdrecord: Warning: Running on Linux-2.6.15-26-amd64-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Linux sg driver version: 3.5.33
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copy right 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'ATA     ' 'SAMSUNG SP2504C ' 'VT10' Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *

kim@shuttle:/mnt$ dmesg | grep hd
[   27.180412] testing NMI watchdog ... OK.
[   28.916721]     ide0: BM-DMA at 0x8880-0x8887, BIOS settings: hda:pio, hdb:pio
[   28.916739]     ide1: BM-DMA at 0x8888-0x888f, BIOS settings: hdc:pio, hdd:pio
[   29.657987] hda: HL-DT-ST DVDRAM GSA-H10A, ATAPI CD/DVD-ROM drive
[   30.581853] hda: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   31.475645] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   31.475710] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[  354.809124] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!

kim@shuttle:/mnt$ /bin/lsmod|grep ide-scsi
kim@shuttle:/mnt$

---

