---
title: "MOL SIGNAL4 illegal instruction"
date: 2006-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by paulsomm on 2006-03-17
I've gotten MOL to compile and, thanks to help from this forum, got the modules to compile.  I've configured the /etc/mol/molrc.osx file to point to my external OSX installation.  When I try to run MOL, I get a small white box, the following output, and then MOL quits:


Mac-on-Linux 0.9.70 [Jul 23 2005 19:20]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Removing stale lockfile /var/lock/mol-1
Running in PowerPC 7400 mode, 256 MB RAM
Timebase: 18.43 MHz, Bus: 73.72 MHz, Clock: 765 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not open '/var/lib/mol/x11.kbd'
Fullscreen video on VT 8.
Could not open '/var/lib/mol/console.kbd'
Video driver(s): [xvideo] [console_video]

     640* 480, depth 8,15,32   { 59.9 } Hz
     800* 600, depth 8,32   { 0.0 } Hz
    1024* 768, depth 8,32   { 0.0 } Hz
    1152* 768, depth 8,15,32   { 54.7 } Hz
    1280* 854, depth 8,15,32   { 0.0, 60.0 } Hz
    1152* 864, depth 8,32   { 0.0 } Hz
    1280*1024, depth 8,32   { 0.0 } Hz
    1600*1200, depth 8,32   { 0.0 } Hz

DHCP nameserver exported: 69.9.35.46
Initializing IP Masquerading...done.
Restarting DNS forwarder and DHCP server: dnsmasq.
Ethernet Interface 'tun-<tun0>' @ 00:00:0D:EA:DB:EE
ALSA sound driver (device 'default')
MOL SCSI controller registered


    <No SCSI Devices>

    CD   /dev/cdrom       CD-ROM         <read-only>   ------
    Unembedded HFS+ /dev/sda3                       <rw> 194352 MB

***** SIGNAL 4 [Illegal instruction] in thread main-thread *****
   si_signo = 4, si_errno 0, si_code 00000005, si_addr 0x10014140
   Last RVEC: 0x0 (0), last OSI: 0, mac_nip 01C01044
   NIP switch_magic + 0x0
***** Backtrace *****
   7fd79e30: backtrace + 0x40
   7fd79e50: signal_handler + 0x220
   7fd79e80: 0x7fd7a1d8
   7fd7a4d0: 0x00000000
   7fd7a670: mainloop_start + 0x20
   7fd7a690: main + 0x230
   7fd7a6c0: 0x0fb9c80c
   7fd7a8d0: 0x0fb9c954
   7fd7a8e0: 0x00000000
cleaning up...
Initializing IP Masquerading...done.
Restarting DNS forwarder and DHCP server: dnsmasq.
Terminating threads...
DONE

I get the same output running startmol --test too


I'm using the MOL packages from Synaptic, with the only home-built portion being the modules.


This error is rather ominous, but I'm hoping someone has a suggestion :-D

---

### Post by paulsomm on 2006-03-18
Never mind this question. I bit the bullet and upgraded to Dapper Flight 5 and Mol boots fine here.

---

