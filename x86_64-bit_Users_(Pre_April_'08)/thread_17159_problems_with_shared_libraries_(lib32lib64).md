---
title: "problems with shared libraries (lib32/lib64)"
date: 2005-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by marco_craveiro on 2005-02-26
hello all,

apologies if this has been posted before - my googling did not find the solution to my exact problem. apologies for the long post as well. my main problem is i cannot get skype to work. before you start screaming rtfm :-) these are the things i've already read:

[Q: How to install Messenger (Skype)?](http://ubuntuguide.org/#skype) 
[32 bit on AMD64 (skype)](http://ubuntuforums.org/showthread.php?p=76532#post76532) 
[Debian AMD64](http://www.imilesi.it/lore/linux/notsoweirdprograms.html) 
[cedega 4.2.1 debian packages for amd64](http://ubuntuforums.org/showthread.php?t=16143) 

ok, whilst all of these were very useful, i'm still stuck. so basically, the situation is as follows: 

1. i've installed skype using the deb provided by [skype](http://www.skype.com/go/getskype-linux-deb). to get it to install i had to do a --force-architecture. (is this bad?)
[FONT=Courier New]
$ dpkg --force-architecture -i skype_1.0.0.7-1_i386.deb
[/FONT]
2. when i try to run skype it fails with:
[FONT=Courier New]
$ skype 
skype: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
[/FONT]
3. if i ldd skype, i get:
[FONT=Courier New]
$ ldd /usr/bin/skype | grep not
        libqt-mt.so.3 => not found
[/FONT]
4. however, i know libqt-mt.so.3 is installed properly, as kdevelop works fine:
[FONT=Courier New]
$ ldd /usr/bin/kdevelop3 | grep libqt-mt.so.3
        libqt-mt.so.3 => /usr/lib/libqt-mt.so.3 (0x0000002a98451000)
[/FONT]
(actually, i find this quite peculiar because /etc/ld.so.conf has no mention of /usr/lib or /usr/lib64 but hey-ho, ldd seems to find /usr/lib for kdevelop. i did try to include /usr/lib in ld.so.conf and run ldconfig but alas, kdevelop still worked and skype still failed to find the library)

5. ok, so according to the Debian AMD64 page (see link above) i can satisfy all dependencies by obtaining the required i386 packages in the debian repository and installing them. i dowloaded libqt3c102_3.3.3-8_i386.deb and i was ready to follow the instructions when i noticed that it will install in /usr/lib:

[FONT=Courier New]# dpkg -c libqt3c102_3.3.3-8_i386.deb
drwxr-xr-x root/root         0 2005-01-14 16:02:29 ./
drwxr-xr-x root/root         0 2005-01-14 16:02:23 ./usr/
drwxr-xr-x root/root         0 2005-01-14 16:02:24 ./usr/lib/
-rw-r--r-- root/root   7150480 2005-01-14 16:02:24 ./usr/lib/libqt.so.3.3.3
[/FONT]
6. so now, i'm a bit stuck. can someon explain me *in a simple way please* :-) how to proceed? should i --force-architecture with libqt3c102_3.3.3-8_i386.deb? it just seems like a bad idea to me because i've already got the 64-bit libqt living there...

many thanks for your time,

marco

---

### Post by kubla on 2005-02-26
Though it's probably not the most correct way, I just downloaded the static binaries from Skype and am running those without any problems whatsoever.

Ian

---

### Post by cmsj on 2005-03-01
Install a 32bit chroot, use the 64bit skype binaries, or wait for hoary to include more 32bit compatibility (which might include qt)

---

### Post by subterrific on 2005-03-02
You didn't say what problem you had with my scripts. Tell me why they didn't work and I'll fix them.

[http://ubuntuforums.org/showthread.php?t=16143](http://ubuntuforums.org/showthread.php?t=16143)

---

### Post by ZeroVerteX on 2005-04-20
To fix Skype, install libqt3c102-mt from Synaptic. It is described as:

Qt GUI Library (Threaded runtime version), Version 3
This is the Trolltech Qt library, version 3. It's necessary for
applications that link against the libqt-mt.so.3, e.g. all KDE3
applications.

Good Luck,

---

