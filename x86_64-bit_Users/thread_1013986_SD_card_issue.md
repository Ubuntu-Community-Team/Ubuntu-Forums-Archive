---
title: "SD card issue"
date: 2008-12-17
forum: x86 64-bit Users
---

### Post by putnam120 on 2008-12-17
I am running Ubuntu Hardy (8.04) on my Hp Pavilion DV6000 and everything is running well except for my SD card reader. it works fine under Vista but whenever I try to use it in Ubuntu my computer just freezes up and I have to remove the card and then restart my system. Does anyone know how I can fix this problem?

---

### Post by cariboo on 2008-12-17
Could you insert your sd card in the reader, then paste the output of the following:

```
dmesg | tail -n 10
```

in your next post. The above command must be run in a Applications-->Accessories-->Terminal. What the above  command prints out the last ten lines of /var/log/dmesg.

Jim

---

### Post by Billxyzzy on 2008-12-17
I am jumping in the middle of this as I have a similar problem
with IBEX 64Bit.  While my system does not hang 
nothing shows up in Places> Computer
I am using a card reader/writer which is USB 1.1 I believe.
Notice the last line below.

  Here is the dmesg output:
bill@ubuntu:~$ dmesg | tail -n 20
[   28.226134] Bluetooth: SCO (Voice Link) ver 0.6
[   28.226139] Bluetooth: SCO socket layer initialized
[   28.557404] Bluetooth: RFCOMM socket layer initialized
[   28.557918] Bluetooth: RFCOMM TTY layer initialized
[   28.557922] Bluetooth: RFCOMM ver 1.10
[   31.820660] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   31.820671] [fglrx] Reserved FB block: Unshared offset:ffb7000, size:44000 
[   31.820674] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   32.668434] r8169: eth0: link up
[   32.858466] NET: Registered protocol family 17
[   77.901879] NET: Registered protocol family 10
[   77.902808] lo: Disabled Privacy Extensions
[   88.224416] eth0: no IPv6 routers present
[  127.073263] ppdev0: registered pardevice
[  127.121171] ppdev0: unregistered pardevice
[  127.193089] ppdev0: registered pardevice
[  127.240948] ppdev0: unregistered pardevice
[  129.338093] ppdev0: registered pardevice
[  129.388143] ppdev0: unregistered pardevice
[  872.692495] usb 4-2: new full speed USB device using ohci_hcd and address 2
bill@ubuntu:~$

---

### Post by caljohnsmith on 2008-12-17
Billxyzzy, if you do:
```
sudo fdisk -l
```
Does that show your USB card?

---

### Post by Billxyzzy on 2008-12-17
I just booted up without any usb device plugged in.
Keep in mind I am running dual boot Wubi for Ibex 64 under
Win xp

I will have to restart my computer to plug in any devices and
expect them to show up in dmesg.  I will do this after you respond
and ask more questions.

Here is some output;

bill@ubuntu:~$ sudo fdisk -l
[sudo] password for bill: 

Disk /dev/sda: 13.6 GB, 13601193984 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0b5d0b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1652    13269658+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaae8f327

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15935   127997856    7  HPFS/NTFS
/dev/sdb2           15936       60800   360378112+   f  W95 Ext'd (LBA)
/dev/sdb5           15936       31870   127997856    7  HPFS/NTFS
/dev/sdb6           31871       60800   232380193+   7  HPFS/NTFS
bill@ubuntu:~$ lsusb
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
bill@ubuntu:~$ 

I cut a part of dmesg and have it below
[    1.640306] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.640310] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pmp pio 
[    1.652136] usbcore: registered new device driver usb
[    1.663112] scsi0 : ahci
[    1.671420] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.680093] scsi1 : ahci
[    1.692799] scsi2 : ahci
[    1.708071] scsi3 : ahci

---

### Post by rjpilla on 2008-12-17
I am having the same problem on all 4 computers in my house including the laptop, toshiba satellite, another post by rjpilla. Hope somebody comes up with the answer.

---

### Post by Billxyzzy on 2008-12-17
Ok everyone some additional info:
(I have some egg on my face)
I have more than one USB card reader laying around
See what is comming?
I have been playing around with 3 card readers,  all USB 1.1.
Well,  I just found under the pile in the other room my 
USB 2 card reader.  Plugged it in and vola it was immediately
recogonized on the desktop and file browser opened up and showed
the contents of the attached SD card.
The problem is USB 1.1,  I think that the kernel is not recogonizing
version 1.1 devices correctly.

Yesterday I got a mount failure message when I plugged one of the 1.1
card readers in.  I could not duplicate that even as I tried several times
with new reboots of the system.  
Ok more to add to the confusion.

---

