---
title: "Ubuntu Server 5.10 on UMAX Pulsar (604e)"
date: 2005-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by tjm on 2005-12-03
I could install the system smoothly first. Then I copied the kernel and the ramdisk-image to the Mac OS partition and booted using it as described in the OldWorldMac Wiki.

But then, hmmppfff. I got this (it was the reboot after the CD was ejected by the installer that should finish installation):

[IMG]http://koelleontherocks.de/media/pics/ubuntu-server-604e.jpg[/IMG]

Now my file-server is down. It ran Yellowdoglinux 3.0.1 before but I wanted it to run Ubuntu. - Because it did not work I tried Debian Sarge 3.1 NetInstall PPC but the installer failed. It did not enable the network and couldn't setup the timezone. The Ubuntu-installer could.

I am not very happy with this situation. Maybe I should give YDL a second chance. There is a special OldWorld SCSI-Mac kernel at shiner.info that can be used and that works. But I do not like Fedora anymore...

Any helpful ideas how to get Debian or Ubuntu run on this machine?

(UMAX Pulsar, 192 MB RAM, ATI Mach64 PCI VGA, 2 x 4,5 GB IBM, 1 x 18,9 GB IBM UW-SCSI HDs, CD-ROM and SCSI CD-R, Farallon 10/100 PCI network)

---

### Post by tjm on 2005-12-04
Did it!

The trick was to boot using the ramdisk-image and give BootX the root-device path additionally.

This was uncommon to me as YDL, that I was used in, did not need the ramdisk-image after installing the OS.

So copying the kernel and ramdisk from /target/boot to the Mac OS partition and using this boot-prompt made it: 

"root=/dev/sb8 video=atyfb:vmode:13" (ATI Mach 64 PCI)

But it is really important to boot from the ramdisk! Check the appropiate option is enabled and the correct image is selected.

Now I have the server up and running with openssh, netatalk 2.0.3, apache2 and vsftpd.

The only thing that does not want to run is mysql-server... 

```
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

I will look around for a solution...

So here's a system overview:

UMAX Pulsar S900
Formac ProRAID II UW-SCSI PCI card (Slot A)
ATI Mach 64 PCI VGA (Slot B)
224 MB RAM interleaved
4,5 GB IBM UW-SCSI (Mac OS 9.1)
4,5 GB IBM UW-SCSI (Ubuntulinux 5.10 Server)
18 GB IBM UW-SCSI (ext3 data partition, shared via netatalk and nfs)
Farallon FastEther TX 10/1000 PCI (Slot E)
Archive Python SCSI DAT-Tape drive

Now it really makes fun!

---

### Post by tjm on 2005-12-04
```
sudo apt-get install apache2 mysql-server-4.1 phpmyadmin
```

did it! mySQL is up and running! Yippieheyjay!

At least I installed "nfs-kernel-server" and made my server's 18 GB UW-SCSI data partition available to my Mac-Mini Ubuntu-client and let it automount it on the desktop. It's so smooth!

My LAMP-Server is up! Ubuntu-Server PPC rocks! Even on an OldWorld 233 MhZ 604e PowerMac-clone.

If you want to check, the URL ist tjm.mine.nu with ftp, ssh and afpovertcp running. Pings and portscans won't work (protected by a NAT router with SPI and 'do not allow pings' enabled). The server is offline sometimes!

:D

---

### Post by Rxke on 2005-12-05
Good job!
In hindsight, the ramdisk bit was probably too "obvious" for anyone reading this... Ubuntu, during install (and livecd, IIRC) loads the ramdisk image to boot from there...  Of course, you coming from YDL, didn't know that, so didn't think of it. Neither did I, and probably a gazillion other people, heehee, because assuming too much... Out of (Debian-raised) habit.

---

