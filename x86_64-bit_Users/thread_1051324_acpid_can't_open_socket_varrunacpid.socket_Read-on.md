---
title: "acpid: can't open socket /var/run/acpid.socket: Read-only file system"
date: 2009-01-26
forum: x86 64-bit Users
---

### Post by Caesonia on 2009-01-26
I can really use some help on this. Its a Dell package, 64 bit.

The system had been running for 6 months, and then this sweet little error popped up.

It WILL still boot in the 32 bit mode, if I use that installation, but not the 64 bit. It runs as a server, so I would hate to have to rebuild it all...but...

But, I rebooted and got this little error:

acpid: can't open socket /var/run/acpid.socket: Read-only file system

It comes after a series of read right errors. 

I have used a live install to try and find the obvious, and no luck. 

I really need to get this back up and running and its been a few weeks. Its time.

TIA.

---

### Post by bettlebrox on 2009-01-26
There might be a problem with the filesystem or maybe the disk is starting to fail. I'd suggest you take the system into single-user (safe) mode and fsck the filesystem.

---

### Post by Caesonia on 2009-01-26
> **bettlebrox said:**
> There might be a problem with the filesystem or maybe the disk is starting to fail. I'd suggest you take the system into single-user (safe) mode and fsck the filesystem.

I ran fsck using the live install disk, as the file was unmounted, and it came back with no errors. The drive is about 6 months old, so if its bad, dell will hear about it. 

Are you saying that I can fsck the file system itself?

---

### Post by bettlebrox on 2009-01-26
In single user mode you can if it's separate file system. Otherwise you should be able to do with the Live Disk. You'll need to know which device it is.

---

### Post by Caesonia on 2009-01-27
> **bettlebrox said:**
> In single user mode you can if it's separate file system. Otherwise you should be able to do with the Live Disk. You'll need to know which device it is.


If when you are talking about the file system, you are referring to the particualr installation of linux, yes, I know which parition it is on-/dev/sda6- and I ran it from the 32 bit installation on /dev/sda3 as well as from the live disk.

I got no errors running the basic command. 

Are there some specific commands I should be using to determine particular things?

Whatever the error is appears to have impacted both my 64 bit installations, but not the 32 bit one. I am suspicious of an update.

---

### Post by bettlebrox on 2009-01-27
Are the 32bit & 64bit installs all using the /etc/fstab file?

---

