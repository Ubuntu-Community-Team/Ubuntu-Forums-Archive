---
title: "Kismet Installation Troubles"
date: 2009-08-20
forum: x86 64-bit Users
---

### Post by DivineX on 2009-08-20
Hey everyone.  I am a total noobie when it comes to linux, this is literally my first day on my 9.04 64bit Ubuntu installation.  All help is appreciated greatly.

I began to install the unarchived kismet files by using ./configure in the command line.  I had already installed libpcap 0.8.1 by ./configure, make, and make install.  However, I get an error saying I need the libpcre and libpcap libraries when I try to install Kismet.
This is my terminal output.

```
checking for pcre_compile in -lpcre... no
configure: WARNING: Failed to find libpcre
checking for pcap_open_live in -lpcap... no
configure: WARNING: Compiling without libpcap support.
configure: error: Could not find working libpcap.  Libpcap is vital for the majority of capture sources Kismet supports.  It must be explicitly disabled.
george@george-laptop:~/kismet-2009-06-R1$ 

```I have googled around for libpcre, however I cannot find much about it.  And for libpcap, I am confused as I have already installed it. Am I doing something incorrectly, or is something just missing  I can provide the full terminal ouput if needed.

Thanks!

Just an update:

I reinstalled pcre and am no longer getting that error.  However, the libpcap remains.

---

### Post by Yellow Pasque on 2009-08-21
```
sudo apt-get install libpcap0.8-dev
```
:)

EDIT: You'll probably need other packages too like:
```
$ sudo apt-get build-dep kismet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmagick9-dev is a virtual package provided by:
  libmagickwand-dev 7:6.4.5.4.dfsg1-1ubuntu3.1
You should explicitly select one to install.
Note, selecting graphicsmagick-libmagick-dev-compat instead of libmagick-dev
The following NEW packages will be installed:
  automake1.9 bison cdbs fdupes flex graphicsmagick-libmagick-dev-compat
  intltool libbz2-dev libexif-dev libglib1.2-dev libgmp3-dev libgmpxx4ldbl
  libgraphics-magick-perl libgraphicsmagick++1 libgraphicsmagick++1-dev
  libgraphicsmagick1 libgraphicsmagick1-dev libjasper-dev liblcms1-dev
  libncurses5-dev libpcap0.8-dev libsnacc-dev libsnacc0c2 libtiff4-dev
  libtiffxx0c2 libwmf-dev omniidl4 snacc snacc-doc wireshark-dev
```

---

### Post by DivineX on 2009-08-21
Thankyou Very Much!

---

