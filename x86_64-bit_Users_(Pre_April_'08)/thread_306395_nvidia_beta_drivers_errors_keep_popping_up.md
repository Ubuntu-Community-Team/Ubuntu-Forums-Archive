---
title: "nvidia beta drivers errors keep popping up"
date: 2006-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by alek66 on 2006-11-24
I was trying to install beryl  so I started by installing the beta drivers for Nvidia. But after a sudo apt-get install build-escential and tried to install the driver this came up on the installation log:
[HTML]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Nov 25 00:25:45 2006

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.17-10-generic/build'
-> Kernel output path: '/lib/modules/2.6.17-10-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
ERROR: Unable to determine the NVIDIA kernel module filename.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
[/HTML]

Can Anyone help me here?

---

### Post by wdaniels on 2006-11-25
I'm having exactly the same problem, can anybody help?  I'm currently using the 9625 version of these beta drivers which installed fine :confused:

---

### Post by fabertawe on 2006-11-25
Did either of you try [this guide]("https://help.ubuntu.com/community/BerylOnEdgy")? People seem to go to extraordinary lengths to install Beryl when this guide took me 10 minutes and worked perfectly first time. Of course I may have just been lucky!

Paul

---

### Post by alek66 on 2006-11-25
its a cool link. nice guide... but outdated.... most apt-keys changed... and dont work... do you have an update one?
I download the key, but when I do a apt-get update I get a w: GPG error: hhtp://ubuntu.lupine.me.uk edgy release: the following signatures couldnt be verified becasuse the public key is no avalible: NO_PUBKEY 3FF0DB166A7476EA

so... lrm packaged for nvidia... as the guide explains, cant get installed.

Alex

---

### Post by kleeman on 2006-11-25
Two things:
1) Nvidia has now released this driver as a non-beta (9629).
2) Did you install the kernel headers package for your kernel? It's called linux-headers-**** where **** is your kernel version.

Also I assume you are using edgy?

---

### Post by alek66 on 2006-11-25
Nvidia drivers installed, yes edgy edition
still getting this error
```
Fetched 4523B in 2s (1618B/s)
Failed to fetch http://compiz-mirror.lupine.me.uk/dists/edgy/Release  Unable to find expected entry  main-edgy/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: GPG error: http://ubuntu.lupine.me.uk edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
alek@Darkstar:~$ wget http://compiz-mirror.lupine.me.uk/quinn.key.asc -O - | sudo apt-key add - 
--21:34:17--  http://compiz-mirror.lupine.me.uk/quinn.key.asc
           => `-'
Resolving compiz-mirror.lupine.me.uk... 80.77.247.17
Connecting to compiz-mirror.lupine.me.uk|80.77.247.17|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:34:20 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.

```

Without that I cant install beryl... any help?

---

### Post by xopher on 2006-11-25
You should check out [http://ubuntu.beryl-project.org]("http://ubuntu.beryl-project.org")

The repos have changed; and the only line you should add to sources.list is now:

```
deb ubuntu.beryl-project.org edgy all
```

and get the key by issuing this:
```
wget http://beryl-mirror.lupine.me.uk/1609B551.gpg -O- | sudo apt-key add -
```

Have fun.

---

### Post by alek66 on 2006-11-25
after adding that line... I can follow the guide? o should I follow another guide.
the guide install gls or aiglx?
after adding the line I still get a
```
Reading package lists... Done
W: GPG error: http://ubuntu.lupine.me.uk edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
```

alex

---

### Post by alek66 on 2006-11-25
this is the latest problem I had with beryl... i installed everthing.
Dispite the missing key thing, it all comes to this:
I got beryl working but all the window toolbars had disappeared.
[IMG]http://img146.imageshack.us/img146/9845/screenshotuj5.png[/IMG]

---

### Post by kleeman on 2006-11-25
I had that problem too when I rebooted into the usual metacity desktop. If you launch the beryl-manager a diamond appears in the panel and when you right click on it you will see a window manager option. This has beryl, metacity and kwin (at least). I went to beryl and then went back to metacity and then the window frames came back.

---

### Post by alek66 on 2006-11-25
yes that was all the fuzz!!! thanks a lot I have beryl running now!!

---

### Post by fabertawe on 2006-11-26
> **alek66 said:**
> its a cool link. nice guide... but outdated.... most apt-keys changed... and dont work... do you have an update one?
I download the key, but when I do a apt-get update I get a w: GPG error: hhtp://ubuntu.lupine.me.uk edgy release: the following signatures couldnt be verified becasuse the public key is no avalible: NO_PUBKEY 3FF0DB166A7476EA

so... lrm packaged for nvidia... as the guide explains, cant get installed.

Alex

My apologies for the delay in replying. I'm glad you got it working :)

You can upgrade to version 0.1.2 (if you don't already have it) [here]("http://ubuntu2.lupine.me.uk/dists/edgy/all/"). The key given for the repo works but I had to break it into separate parts as the one liner just hangs in the terminal and the key never gets installed (an Edgy problem or just mine?).

If you like eye-candy you can get a deb of kiba-dock [here]("http://www.ubuntuforums.org/showthread.php?t=295197").

Paul

---

### Post by alek66 on 2006-11-26
though everything is working. The lrn nvidia packages seem to make a lot of use of the nvidia graphic device... temperature are at the sky... is there a way to down the temps?

---

