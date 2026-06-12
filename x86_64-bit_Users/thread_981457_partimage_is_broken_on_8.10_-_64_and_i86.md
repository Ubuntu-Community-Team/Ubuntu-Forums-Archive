---
title: "partimage is broken on 8.10 - 64 and i86"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by briandu on 2008-11-13
Hi all,
are other experiencing problems with restoring using partimage? 

I have some files that I made during 7.02 and I cannot restore these. I get a segmentation fault message and/or the prompt for filepath to restore becomes stupid.

Anyone else?

I have installed the Debian version as well and have exactly the same problems.

I really need to get at these files.

---

### Post by briandu on 2008-11-14
so far 34 reads and no responses from anyone.:(

Am I the only person using this?

---

### Post by Sef on 2008-11-14
> so far 34 reads and no responses from anyone.:sad:

Am I the only person using this? 	

You need patience.   Sometimes answers come quick, and sometimes they come slow.

---

### Post by Jouke74 on 2008-11-14
Did you try to run a 7.04 (Feisty) live CD already and install the version of partimage from the Feisty repository onto the live CD environment? 

Subsequently you can restore the whole old partition, not just one or two files. So take note to where you install that partition, because if you don't define a right empty one, you will loose your current partition data!!!

---

### Post by Yellow Pasque on 2008-11-14
I see a lot of reports of segfaults on the partimage user forums, especially when restoring NTFS partitions.
Personally, I would try uninstalling any old versions/.deb's and compiling the latest stable version (0.6.7) from source.  I'm not exactly sure what version you ran when you said you tried the "Debian version", but try compiling 0.6.7 (the changelog shows a patch for amd64).

You'll need these packages to compile from source -
```
sudo apt-get install build-essential libnewt-dev libslang2-dev libbz2-dev zlib1g-dev libssl-dev
```

Good luck.

---

### Post by rockorequin on 2008-12-21
Did you get it working? I know the 64 bit repositories have a really old version of partimage (0.6.4 versus 0.6.7) that is known to segfault on ntfs partitions. The 32 bit repositories have the 0.6.7 version. I put a bug for the 64 bit version ages ago (when Hardy came out).

So is the old version the problem? Compiling 0.6.7 isn't hard, except that in Intrepid it fails to compile saying 'iostream.h not found', since iostream.h has been deprecated. To fix this, I had to install gcc 4.2 and then copy iostream.h across:

sudo cp /usr/include/c++/4.2/backward/iostream.h /usr/include/c++/4.3.2/

to make iostream.h visible to gcc 4.3 (ie it then compiles with gcc 4.3).

---

### Post by drs305 on 2008-12-21
There seems to be a problem with compressed files larger than about 2GB if you use the the gz compression option and do not split the image into segments. I get an "invalid compression level" error when I try to restore the image. 

If it can't restore the image, you can simply change the extension from .000 to .gz and then uncompress the file yourself. You can then restore the uncompressed image with partimage.

---

