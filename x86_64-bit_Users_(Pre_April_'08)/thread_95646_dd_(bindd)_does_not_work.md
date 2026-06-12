---
title: "dd (/bin/dd) does not work"
date: 2005-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ricardo06 on 2005-11-27
I think there is a real bug in the amd64 build. 

I cannot create a file with /bin/dd. ex:

richard@ubuntu:/opt$ sudo dd if=/dev/zero of=rootfs.img bs=320k count=1
sudo: dd if=/dev/zero of=rootfs.img bs=320k count=1: command not found

The above command would never pass.

I went to my i386 buils on the same machine on the same disk and directory. And it worked fine !

any opinion ? Should i fill a bug somewhere ?

Richard

---

### Post by amohanty on 2005-11-27
what does 
type dd
return?

AM

---

### Post by ricardo06 on 2005-11-27
[QUOTE=amohanty]what does 
type dd
return?

AM[/QUOTE]
This is what it does.

[COLOR="Blue"]richard@ubuntu:~$ type dd
dd is /bin/dd[/COLOR]


I did many things among which typing the filenames + complete path. changing the sizes and count. But it does not change anything. 

Richard

---

### Post by amohanty on 2005-11-27
You dont need to sudo, if you are working in a directory where you have write access..  

aseem@kandinsky:~$ dd if=/dev/zero of=rootfs.img bs=320k count=1
1+0 records in
1+0 records out
327680 bytes transferred in 0.002892 seconds (113308357 bytes/sec)

HTH
AM

---

### Post by ricardo06 on 2005-11-27
I do have right permissions in the directory.
The error message is in french; It says "no file or directory of that type"

[COLOR="Blue"]richard@ubuntu:/opt$ dd if=/dev/zero of=rootfs.img bs=320k count=1
bash: dd if=/dev/zero of=rootfs.img bs=320k count=1: Aucun fichier ou r&#233;pertoire de ce type[/COLOR]

I re-installed the coreutils package. And it still fails.

By the way I created the file allright with i386 build but then again, the mk2fs behaves the same way.

Now the file exists I attemp to format it as ext2:

[COLOR="Blue"]richard@ubuntu:/opt$ mke2fs -i 1024 -F rootfs.img
bash: mke2fs -i: command not found
[/COLOR]

This is strange.  The above command looks like the command is "mke2fs -i" instead of mke2fs !!

Richard

---

### Post by amohanty on 2005-11-27
> 
richard@ubuntu:/opt$ dd if=/dev/zero of=rootfs.img bs=320k count=1
bash: dd if=/dev/zero of=rootfs.img bs=320k count=1: Aucun fichier ou répertoire de ce type


Ok this might be a stupid question since /dev/zero should normally exist, but does it exist on your system and do have read access to it?

> richard@ubuntu:/opt$ mke2fs -i 1024 -F rootfs.img
bash: mke2fs -i: command not found

the -i 1024 simply tells mke2fs to use 1kb per inode.

also try this before using mke2fs
sudo apt-get install e2fsprogs

my attempt at what you are doing as myself:

> 
aseem@kandinsky:~$ dd if=/dev/zero of=rootfs.img bs=320k count=1
1+0 records in
1+0 records out
327680 bytes transferred in 0.012004 seconds (27297414 bytes/sec)
aseem@kandinsky:~$ mke2fs -F rootfs.img
mke2fs 1.38 (30-Jun-2005)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
40 inodes, 320 blocks
16 blocks (5.00%) reserved for the super user
First data block=1
1 block group
8192 blocks per group, 8192 fragments per group
40 inodes per group

Writing inode tables: done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 35 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
aseem@kandinsky:~$



HTH
AM

---

### Post by ricardo06 on 2005-11-28
I think i have the answer.

Now it works !

what i think happenned is that I cut and pasted the command line from a pdf document. SO my guess is hat there are hidden characters in the spaces so that the command is not recognized. 
Actually If I do it again (cu and paste from pdf), it fails again.

I feel stupid..

thanks for your help Amohanty , it did help me to keep on.

Richard

---

