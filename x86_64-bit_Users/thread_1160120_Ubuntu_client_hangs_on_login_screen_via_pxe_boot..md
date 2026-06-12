---
title: "Ubuntu client hangs on login screen via pxe boot."
date: 2009-05-15
forum: x86 64-bit Users
---

### Post by Davion on 2009-05-15
Hi there,
Im a 64bit ubuntu desktop user and i'm trying to set up a cluster using pxe boot,nfs and tftp.I have make a search all over the web and at this forum but i can't find a solution yet.
This project is for educational purposes and is really important to me to understand how all that stuff works. So..my problem is that as i set up properly pxe linux,nfs-kernel-server,dhcp3-server and tftp daemon on my server machine(ubuntu desktop 64bit as i said),nfs client hangs at startup when i'm trying to write the pass at login screen.I tried everything but all configuration files (fstab,exports,dhcpd.conf) seems to be ok.I can post my config files if you need them in order to see what i have done so far. I really really need your help guys!!:-k

Thanks in advance!

---

### Post by drave on 2009-05-15
are the clients 64 bit ??

you might have to install that lot into a 32bit jail or the clients will hang

---

### Post by drave on 2009-05-15
actually i meant the code that the clients will run, not the servers

---

### Post by Davion on 2009-05-15
Hi drave,
thanks for the reply.

I didn't mension that both server and client are running ubuntu 9.04 64bit. At server i have 2 partitions one for "/" and one for "/home". I made o folder /nodes/nfs/node1 at server's root partition and in there i mounted client's root folder. Also i made the folder "/tftpboot" and putted there pxelinux,pxelinux.cfg, initrd image(from client's ramdisk) and vmlinuz.
Dhcp works properly and gives the client an ip,tftp reads the content of /tftpboot and the OS loads perfectly on client machine. The only problem is tha login screen hangs when i try to type something..

---

### Post by drave on 2009-05-15
hmm i used the ltsp, which mostly just worked and the client is 32bit. 
what did you put in /nodes/nfs/node1? can you ctrl-alt-f1 to a terminal prompt on the client before you try and login?

---

### Post by Davion on 2009-05-15
Well..i have these partitions..

sda1 for server's "/"
sda2 for server's "/home"
sda3 for "swap"
sda5 for client's "/" (node1)

here is server's fstab file
----------------------------
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6c85924b-da1a-49f0-8262-572cabfbe460 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=9f48c78a-21fc-4cfb-9610-7c0786b3ab9a /home           ext3    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=bc858fd9-7f29-439c-8ab6-21d071589c8c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda5    /nodes/nfs/node1    ext3    noatime    0    0
```As you can see i mount client's root which is at /dev/sda5 at server's /nodes/nfs/node1 folder.

EDIT:ctrl+alt+f1 puts me into terminal mode but does nothing when i type for login..

---

### Post by drave on 2009-05-15
but what did you put in there? 
can you ctrl-alt-f2 on the client before you try to login (f1 is a login prompt, f2 is straight in)

---

### Post by Davion on 2009-05-15
In sda5 i installed the ubuntu 9.04 for the client without to install grub.I use grub from server's installation in sda1.In order to have access at client's filesystem via pxeboot i mounted it at server's root partition and specially at /nodes/nfs/node1. So,node1 folder contains all the files and folders from the client's filesystem which are exported via nfs. 
Ctrl+alt+f2 does nothing also..:sad:

Here is client's fstab file
-----------------------------

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
/dev/sda5    /               ext3    relatime    0    0
# swap was on /dev/sda3 during installation
/dev/sda3    none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
192.168.2.1:/home    /home    nfs    defaults    0    0
192.168.2.1:/nodes    /nodes    nfs    defaults    0    0

```

---

### Post by drave on 2009-05-15
err. on the client /dev/sda5 , sda3 etc will be meaningless wont they, root and swap will be nfs as well.

ps. its 8 o'clock in the evening here in London, so i'll be signing off. 
good luck
pps. might be worth trying ltsp to see what it does, then move to 64 bit later

cheers

---

### Post by Davion on 2009-05-15
Ok i made this change at client's fstab.Although i don't know if it is correct..

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
#/dev/sda5    /               ext3    relatime    0    0
192.168.2.1:/nodes/nfs/node1    /    nfs    defaults    0    0
# swap was on /dev/sda3 during installation
/dev/sda3    none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
192.168.2.1:/home    /home    nfs    defaults    0    0
#192.168.2.1:/nodes    /nodes    nfs    defaults    0    0
#192.168.2.1:/nodes/nfs    /nodes/nfs    nfs    defaults    0    0
#192.168.2.1:/nodes/nfs/node1  /nodes/nfs/node1      nfs     defaults        0       0

Same results even if with this change..

But is it possible to have a swap partition over nfs? How can i mount it :confused:

Thanks for your help drave ;)

---

