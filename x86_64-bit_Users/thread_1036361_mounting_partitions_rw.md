---
title: "mounting partitions r/w"
date: 2009-01-10
forum: x86 64-bit Users
---

### Post by anafshalom on 2009-01-10
I just installed Ubuntu I have a couple of problems:

I've been using Fedora core6, and I'm trying out Ubuntu.

I had my Home on its own partition.  I tried to use this same partition as the home for Ubuntu, but could not figure that out, so I have the Home for Ubuntu in another partition.  I want to have the Fedora home partition mounted RW so I can keep the files I use syncronized without having to be a super user.

For some reason some of the partitions are not mounting at boot up, and when I do a mount -a they mount, but they are read-only.

The other problem I have, is that I do not remember the root password I used when I installed Ubuntu

Here is the fstab as it reads now:
# /etc/fstab: static file system information.
#
# 		<file system> <mount point>   	<type>  <options>    		    <dump>   <pass>
proc            /proc           proc   			 defaults      			0      0

# /dev/sda4
UUID=d5053608-2763-42f0-ab9b-90e98199789c /    	ext3    relatime,errors=remount-ro 	0	1

/dev/sda2 		/home/FedoraRoot	ext3	defaults			0	0

/dev/sda5 			       /home/E	  vfat	rw,user,auto			0	0

# /dev/sda6
UUID=fdddc7c6-d7c2-4ccd-8854-f1f038a714a3 none     swap    sw              		0	0

/dev/sda7 			/home/FedoraHome ext2	 auto,user,rw			0	2

/dev/sda8				/home/D	vfat	auto,user,rw			0	0

# /dev/sda9
UUID=9f1c3764-6aa1-4745-ab7f-70f92d8c5301 /home  ext3    relatime        		0	2

# /dev/sda10
UUID=a068755a-bbec-4d94-b4ec-46b098de81d0 /home/g  ext3    relatime        		0	2


/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 			0	0

/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 			0	0

---

### Post by Arup on 2009-01-10
Install pysdm from repos, best way to set mount points etc.

---

### Post by garnser on 2009-01-11
> **anafshalom said:**
> 
The other problem I have, is that I do not remember the root password I used when I installed Ubuntu

You don't set a root-password when you install ubuntu, your user should have full sudo access using its own password.

Try the following:

jpetersson2@jpetersson-desk1:~$ sudo su -
[sudo] password for jpetersson2: 
root@jpetersson-desk1:~#

---

