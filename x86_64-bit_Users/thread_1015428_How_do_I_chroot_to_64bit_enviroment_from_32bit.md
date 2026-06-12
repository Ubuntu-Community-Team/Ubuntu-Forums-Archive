---
title: "How do I chroot to 64bit enviroment from 32bit?"
date: 2008-12-18
forum: x86 64-bit Users
---

### Post by obsrv on 2008-12-18
How do I chroot to 64bit enviroment from 32bit? I get this:

obsrv@pirate:~$ sudo su
root@pirate:/home/obsrv# cd /
root@pirate:/# chroot /mnt/arch_games/ /bin/bash
chroot: cannot run command `/bin/bash': Exec format error
root@pirate:/# chroot /mnt/arch_games/ /mnt/arch_games/bin/bash
chroot: cannot run command `/mnt/arch_games/bin/bash': No such file or directory
root@pirate:/# chroot /mnt/arch_games/ /mnt/arch_games/bin/
arch           cut            fgrep          lsmod          pwd            tr
awk            dash           gawk           mbchk          readlink       traceroute
bash           date           gawk-3.1.6     mkdir          red            traceroute6
bashbug        dd             grep           mkfifo         rm             true
bunzip2        df             groups         mknod          rmdir          umount
bzcat          dir            gunzip         more           sed            uname
bzip2          dircolors      gzip           mount          sh             uncompress
bzip2recover   dmesg          hostname       mountpoint     shred          vdir
cat            dnsdomainname  install        mv             sleep          ypdomainname
chgrp          domainname     kill           netstat        stty           zcat
chmod          du             less           nisdomainname  su             
chown          echo           ln             pidof          sync           
compress       ed             loadkeys       ping           tar            
cp             egrep          login          ping6          touch          
cpio           false          ls             ps             tput           
root@pirate:/# chroot /mnt/arch_games/ /mnt/arch_games/bin/bash
chroot: cannot run command `/mnt/arch_games/bin/bash': No such file or directory
root@pirate:/# chroot /mnt/arch_games/
chroot: cannot run command `/bin/bash': Exec format error
root@pirate:/# 

It seems thats impossible :( any ideas?

I AM NOOB, SORRY.

---

### Post by Ehtetur on 2008-12-18
Hi obsrv.. what are you trying to chroot from/to?  :twisted:
Actually, what are you looking to do? There may be a different command that will do what it is you want..

chroot changes the root pointer like usually when you boot from a rescue CD and want to change / from the CD to the OS' / that's on the hard drive...

-- 
Ehtetur

---

### Post by obsrv on 2008-12-19
I have Baltix GNU/Linux in my machine as primary OS (Ubuntu), and just installed ArchLinux wich does not work and doesnt boot. I want to chroot from baltix to arch.

Baltix - 32
Arch - 64

THANKS FOR REPLY

---

### Post by gelimeri on 2008-12-19
Hi everyone here!
I've the same error when I try the following commands from a root terminal:
```
chroot /media/gentoo /bin/bash
```
I'm trying to install a gentoo 64 bit from Ubuntu hardy (8.04).
```
uname -a
Linux theMatrix 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

```
Thanks

Matteo

---

### Post by gelimeri on 2008-12-19
I think is impossible chrooting into a 64 bit environment from a 32 bit ones. It's quite logical but not obvious.
For example, I've found this: [http://readlist.com/lists/gentoo.org/gentoo-user/12/63008.html]("http://readlist.com/lists/gentoo.org/gentoo-user/12/63008.html")

bye bye

---

### Post by Ehtetur on 2008-12-19
> **obsrv said:**
> I want to chroot from baltix to arch.

You'll first have to mount Arch's / partition before you can chroot it.
To see which hard drive partition is / for Arch, you'll want to run the following. (The root partition is typically the largest):
> sudo /sbin/fdisk -l

Let's 'assume' that from fdisk -l, you discovered that /dev/sdb1 was Arch's /, you can mount it like this:

1. Create a mount point:
> sudo mkdir /media/arch64

2. Mount Arch's root:
> sudo mount /dev/sdb1 /media/arch64

If you're **just** looking to move over some important files from Arch to Baltix, then you don't need to chroot. Instead, change directory to Arch:
> cd /media/arch64
And start cp-ing over files.

But if you do want to chroot, then:
> cd
> chroot /media/arch64

Now, you've changed your / partition from Baltix's to Arch's...

After you're done you wanted to do, you'll need to sync everything and exit the chroot environment:
> sudo sync
> sudo exit

--
Ehtetur

---

### Post by obsrv on 2008-12-19
I know, this is not the first time I am chrooting. I used to Gentooer for 2 years. But I never tried to chroot from 32 to 64. In 32bit enviroment I think its imposible to execute 64bit bash :confused:

---

### Post by Ehtetur on 2008-12-20
ahhh, lots of Linux experience... sorry obsrv, i was looking at your darn bean count :redface:

anyways... I was thinking you wanted to chroot so you could do some rescue stuff in Arch: edit a config file in /etc; move over some data files; or dpkg missing/needed x64 programs. (via --force-architecture).. and I think you're right, 64bit apps won't run in a 32bit environ..

But if you do need to run 64bit apps in a chroot environ, you may need to boot up with an Arch rescue cd or the install cd if it has a rescue boot option.

---

### Post by obsrv on 2008-12-23
I resqued the system. I chrooted from 32bit live CD to ArchLinux and copied /boot/grub/menu.lst (some of it entrities) to the main /boot/grub/menu.lst where all the OS selections are, at first I wrote by hand root(... kernel /vmlinnuz.. **root=/dev/sdb9** and I needed to write root not the udev node but **UUID** :) that was the problem.

---

