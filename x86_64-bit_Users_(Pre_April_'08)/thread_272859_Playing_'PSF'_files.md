---
title: "Playing 'PSF' files"
date: 2006-10-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by kopilo on 2006-10-07
Hi, I'm wondering if there is a way to play PSF (Playstation Sound format) files on Ubuntu 64.

There is [this]("http://www.brownjava.org/software/he-xmms/") plugin for xmms, however when I installed it, it doesn't show up in the plugins and xmms doesn't still regonise psf files.

---

### Post by pay on 2006-10-07
A 32bit plugin for XMMS requires the 32bit XMMS. To install it use the --force-arctecture option when installing the .deb file (you must download it, you can't use the repositories.

---

### Post by kopilo on 2006-10-07
thank you.
Err, there doesn't seem to be a deb file.. Hmm I think I just have to extract the folder from memory. :???:
Nope, need to compile the make file.. "no glib config-script found" >_<

---

### Post by pay on 2006-10-07
```
wget http://mirror.isp.net.au/ftp/pub/ubuntu/pool/main/x/xmms/xmms_1.2.10+cvs20050809-4ubuntu5_i386.deb
sudo dpkg -i --force-architecture xmms_1.2.10+cvs20050809-4ubuntu5_i386.deb
```
done

---

### Post by kopilo on 2006-10-07
oh my goodness, thank you so much!

EDIT:
"xmms: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

>_<

---

### Post by pay on 2006-10-08
Try sudo apt-get install libgtk-1.2
But you might need the 32bit version.

---

### Post by kopilo on 2006-10-10
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk-1.2


Maybe I should make another thread about installing the 32 bit version of xmms...

---

### Post by pay on 2006-10-10
Sorry it doesn't have the -. try ```
sudo aptitude install libgtk1.2
```If that doesn't work you can find the package here [http://packages.ubuntu.com/dapper/libs/libgtk1.2](http://packages.ubuntu.com/dapper/libs/libgtk1.2)
If you need the 32bit version do this. ```
wget http://mirror.isp.net.au/ftp/pub/ubuntu/pool/main/g/gtk+1.2/libgtk1.2_1.2.10-18_i386.deb
sudo dpkg -i --force-architecture libgtk1.2_1.2.10-18_i386.deb
```

---

### Post by kopilo on 2006-10-11
Well it installed.

However now I need the 32 bit version of libgmodule 1.2 or something...

xmms: error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by pay on 2006-10-11
```
wget http://mirror.isp.net.au/ftp/pub/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-10.1build1_i386.deb
sudo dpkg -i libglib1.2_1.2.10-10.1build1_i386.deb
```libgmodule-1.2 is part of libglib1.2. If it needs the 64bit version then sudo aptitude install libglib1.2

---

### Post by kopilo on 2006-10-12
YAY It's working!

By the way, with the last bit of code you typed, you forgot "--force-architecture" but it's still good.

Thank you for your help. Ok now if by any chance someone else is looking for how to do this, this is what I have done from start to finish.

Start, install the 32 bit version of xmms
```
wget http://mirror.isp.net.au/ftp/pub/ubuntu/pool/main/x/xmms/xmms_1.2.10+cvs20050809-4ubuntu5_i386.deb
sudo dpkg -i --force-architecture xmms_1.2.10+cvs20050809-4ubuntu5_i386.deb

```
then type 'xmms' into the terminal window.

To resolve the gtk+1.2 not being 32bit
```

wget http://mirror.isp.net.au/ftp/pub/ubuntu/pool/main/g/gtk+1.2/libgtk1.2_1.2.10-18_i386.deb
sudo dpkg -i --force-architecture libgtk1.2_1.2.10-18_i386.deb

```

To resolve ibgmodule-1.2/libglib1.2 not being 32 bit.
```

wget http://mirror.isp.net.au/ftp/pub/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-10.1build1_i386.deb
sudo dpkg -i --force-architecture libglib1.2_1.2.10-10.1build1_i386.deb

```

*note* With Synaptic and Update Manager, they will require you to reinstall the 64 bit version of GTK+1.2 everytime you use them, thus everytime you want to use xmms 32 you may need to reinstall these packages.

For the plugin go [here]("http://www.brownjava.org/software/he-xmms/") download it and extract it to "~/.xmms/Input".

---

