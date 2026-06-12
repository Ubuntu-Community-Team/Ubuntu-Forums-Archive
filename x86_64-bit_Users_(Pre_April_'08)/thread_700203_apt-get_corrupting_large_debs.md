---
title: "apt-get corrupting large debs"
date: 2008-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by firstmagic on 2008-02-18
2.6.22-14-server #1 SMP Sun Oct 14 22:09:15 GMT 2007 x86_64 GNU/Linux

Brand new ubuntu 7.10 system.  I am *constantly* getting corrupted .deb files from apt-get.  This of course causes installs to fall on their face.

I've been trying to install vim-runtime for hours now, to no avail.  I constantly see messages like:

```

root@hammerstorm:~# aptitude install vim
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  vim-runtime
The following packages have been kept back:
  bind9-host dnsutils e2fslibs e2fsprogs findutils libbind9-30 libblkid1 libc6 libcomerr2 libdb4.4 libdns32
  libisc32 libisccc30 libisccfg30 liblwres30 libss2 libssl0.9.8 libuuid1 linux-image-2.6.22-14-server perl
  perl-base perl-modules tzdata
The following NEW packages will be installed:
  vim-runtime
The following partially installed packages will be configured:
  vim
0 packages upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
Need to get 5471kB of archives. After unpacking 23.1MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com gutsy/main vim-runtime 1:7.1-056+2ubuntu2 [5471kB]
Fetched 5471kB in 1m7s (81.6kB/s)
(Reading database ... 14871 files and directories currently installed.)
[color=red]Unpacking vim-runtime (from .../vim-runtime_1%3a7.1-056+2ubuntu2_all.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/vim-runtime_1%3a7.1-056+2ubuntu2_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/vim/vim71/doc/pattern.txt')
[/color]
Errors were encountered while processing:
 /var/cache/apt/archives/vim-runtime_1%3a7.1-056+2ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of vim:
 vim depends on vim-runtime (= 1:7.1-056+2ubuntu2); however:
  Package vim-runtime is not installed.
dpkg: error processing vim (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 vim
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

```

The specific complaint of the short read on buffer_copy varies with each attempt at this (ie. it's usually different files within the package).  Also, I check the md5sum of the .deb each time, and it's different. :(

I can scp much larger files than this to my system, and they come across without corruption.  Any hints on what might be causing this, and how I can fix it, would be much appreciated.  I'm going nuts!

---

### Post by dcstar on 2008-02-18
> **firstmagic said:**
> 2.6.22-14-server #1 SMP Sun Oct 14 22:09:15 GMT 2007 x86_64 GNU/Linux

Brand new ubuntu 7.10 system.  I am *constantly* getting corrupted .deb files from apt-get.  This of course causes installs to fall on their face.
.........

Delete the cached file before downloading again, and choose another mirror in Synaptic.

---

