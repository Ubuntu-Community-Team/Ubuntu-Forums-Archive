---
title: "[SOLVED] Unable to compile C file...."
date: 2007-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by amirseg on 2007-08-21
Hi,
I have just installed Ubuntu 7.04, added all the updates, but when I am trying to compile a C file, I always get:
*'Draw.c:1:19: error: stdio.h: No such file or directory'*

I looked in the forums, and saw all kind of suggestions. I am having a problem with *'http://il.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb which I get an'* MD5Sum mismatch on it. I tryed downloading the file from the link, and then in the* 'package controller'* when installing it I get [I]'dpkg: error processing /home/amirseg/Desktop/libc6-dev_2.5-Oubuntu14_amd64.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)'[/I].

I could not find solutions for those problem... Can anyone help me?

Thanks
Amir.

---

### Post by xeo_pt on 2007-08-21
I think you have the C compiler not full installed.

---

### Post by ddrichardson on 2007-08-21
You haven't got headers installed.

---

### Post by John.Michael.Kane on 2007-08-21
Looks like the package is corrupt. Also if this is a source tar-ball you may need to install build-essential before it will compile.

---

### Post by amirseg on 2007-08-21
Hi,
Thaks for the fast answers. I forgot to write about the update after installing, I had a problem when updating I got:
[I]'E: ttf-opensymbol: subprocess post-installation script returned error exit status 2
E: openoffice.org-core: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured
E: openoffice.org-calc: dependency problems - leaving unconfigured
E: python-uno: dependency problems - leaving unconfigured
E: openoffice.org-writer: dependency problems - leaving unconfigured
E: openoffice.org-draw: dependency problems - leaving unconfigured
E: openoffice.org-impress: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-filter-mobiledev: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org-gtk: dependency problems - leaving unconfigured
E: openoffice.org-gnome: dependency problems - leaving unconfigured
E: openoffice.org-math: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured'[/I]


Is there anything I can do?

---

### Post by stmiller on 2007-08-22
Try these:

```

sudo apt-get autoclean

sudo apt-get autoremove

```

---

### Post by amirseg on 2007-08-22
> **stmiller said:**
> Try these:

```

sudo apt-get autoclean

sudo apt-get autoremove

```

Hi,
I did what you said, everything went OK.
What to do now? I still can't compile...

Sorry for all the begginers questions.... I'm really new to all of this....

---

### Post by amirseg on 2007-08-22
Anyone got an Idea what I can do? I really need it working quickly.....


*sorry for bothering.
Amir

---

### Post by John.Michael.Kane on 2007-08-22
> **amirseg said:**
> Anyone got an Idea what I can do? I really need it working quickly.....


*sorry for bothering.
Amir

First try to configure all packages that are unconfigured :
```
sudo dpkg --configure -a
```

Try to remove all problematic packages automatically :
```
sudo aptitude -f remove
```

Try again to configure all packages that are unconfigured :
```
sudo dpkg --configure -a
```

Run:
```
sudo aptitude update && sudo aptitude upgrade
```

Now try installing build-essential, and other programs your where trying to.

```
gksudo aptitude install build-essential
```

---

### Post by amirseg on 2007-08-22
Thanks.
All what you wrote me to do went fine, except the last one - *gksudo aptitude install build-essential*.

I get this:
[I]gksudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 2459kB/7062kB of archives. After unpacking 29.0MB will be used.
Do you want to continue? [Y/n/?] Y
[/I]

And it just stay like this

what to do?

---

### Post by amirseg on 2007-08-22
I tryed downloading it from [http://il.archive.ubuntu.com/ubuntu/...tu14_amd64.deb](http://il.archive.ubuntu.com/ubuntu/...tu14_amd64.deb)
and saved it on my computer, opened it with archive manager, and I saw 3 files:
control.tar.gz
data.tar.gz
debian-binary

I could open control.tar.gz and saw some files inside, but when trying to open data.tar.gz I got an error saying:
tar: Skipping to next header

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
tar: Child returned status 1
tar: Error exit delayed from previous errors

What can I do?


*I tryed to think what could be diffrent in my computer from other computers out there and I think that the only thing is that I have a Hebrew package installed. Does that matter?

Amir

---

### Post by John.Michael.Kane on 2007-08-22
> **amirseg said:**
> I tryed downloading it from [http://il.archive.ubuntu.com/ubuntu/...tu14_amd64.deb](http://il.archive.ubuntu.com/ubuntu/...tu14_amd64.deb)
and saved it on my computer, opened it with archive manager, and I saw 3 files:
control.tar.gz
data.tar.gz
debian-binary

I could open control.tar.gz and saw some files inside, but when trying to open data.tar.gz I got an error saying:
tar: Skipping to next header

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
tar: Child returned status 1
tar: Error exit delayed from previous errors

What can I do?


*I tryed to think what could be diffrent in my computer from other computers out there and I think that the only thing is that I have a Hebrew package installed. Does that matter?

Amir

That your linking to is a .deb file. You should be able to double click it, and have gdebi install it.

---

### Post by amirseg on 2007-08-23
Hi,
I di clicked it and did tryed to install it, but got an error, I got Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (2007041]/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb MD5Sum mismatch.

anything I can do?

---

### Post by amirseg on 2007-08-23
Hi,
I solved my problem by [http://ubuntuforums.org/showthread.php?p=2585522#post2585522](http://ubuntuforums.org/showthread.php?p=2585522#post2585522)

Thanks a lot to whoever helped me :)

bye

---

