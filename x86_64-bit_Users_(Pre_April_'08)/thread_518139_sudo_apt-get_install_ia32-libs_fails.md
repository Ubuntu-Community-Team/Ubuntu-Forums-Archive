---
title: "sudo apt-get install ia32-libs fails"
date: 2007-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidkahn on 2007-08-05
Output from terminal: 

    Reading package lists... Done 
    Building dependency tree 
    Reading state information... Done 
    The following NEW packages will be installed: 
    ia32-libs 
    0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.  
    Need to get 17.9MB of archives. 
    After unpacking 48.8MB of additional disk space will be used. 
    Get:1  [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty/main ia32-libs 1.5ubuntu9 [17.9MB] 
    Fetched 17.9MB in 1m41s (176kB/s) 
    (Reading database ... 130164 files and directories currently installed.) 
    Unpacking ia32-libs (from .../ia32-libs_1.5ubuntu9_amd64.deb) ... 
    dpkg: error processing /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb 
    (--unpack): 
    unable to create `./usr/lib32/libGL.so.1.2': No such file or directory 
    dpkg-deb: subprocess paste killed by signal (Broken pipe) 
    Errors were encountered while processing: 
    /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb 
    E: Sub-process /usr/bin/dpkg returned an error code (1)  

Looking inside the /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb package shows "usr/lib32/libGL.so.1.2" as being in it. Is there simply something wrong with the package on the Ubuntu server? 

While it's probably not the source of the problem, there is a 32-bit chroot on this PC.

---

### Post by jnorthr on 2007-08-05
Is your machine really an AMD64 chip ? Are you sure you've installing the correct package for your hardware config. ?

---

### Post by davidkahn on 2007-08-05
Thanks for the response.  It is definitely an  AMD 64-bit chip

    uname -a
    Linux CERTIBY-DEV1 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

In any case I seem to have solved my problem.  Which I am posting to potentially help others that run into it.

I did:  dpkg -S libGL.so.1.2
and found out that the same file was part of nvidia-glx

So I used "sudo apt-get remove nvidia-glx" to uninstall the nvidia, which seemed to have a conflict.  Nevertheless sudo apt-get install ia32-libs continued to fail.

I then reinstalled nvidia-glx (sudo apt-get install nvidia-glx), and then 
sudo apt-get install ia32-libs succeeded!

Better yet VMware now works.

---

