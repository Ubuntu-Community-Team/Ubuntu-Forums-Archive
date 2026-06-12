---
title: "My experience with the comprehensive sound problem guide"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by benign on 2008-08-04
My sound was working find until a system lockup where I had to hard power off the computer. After reboot there is a red X in the speaker icon and aplay -l shows device_list:205: no soundcards found... 

lspci -v shows:

```

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 7
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]

```

I'm following the ["Comprehensive Sound Problem Solution Guide"]("http://ubuntuforums.org/showthread.php?t=205449") as I write this, and up to step 6:

```

sudo module-assistant a-i   alsa-source

```

It gives me:

```

Updated infos about 1 packages
Getting source for kernel version: 2.6.24-19-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  kdebase-workspace-data ksysguardd-kde4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
unpack 
Extracting the package tarball, /usr/src/alsa-driver.tar.bz2, please wait...
Target package file 
/usr/src/alsa-modules-2.6.24-19-generic_1.0.16-0ubuntu4+2.6.24-19.36_amd64.deb 
already exists, not rebuilding!
(however, you could use the -f switch to ignore it)
dpkg -Ei /usr/src/alsa-modules-2.6.24-19-generic_1.0.16-0ubuntu4+2.6.24-19.36_amd64.deb 
Version 1.0.16-0ubuntu4+2.6.24-19.36 of alsa-modules-2.6.24-19-generic already installed, skipping.

```

Should it do that even after I removed everything earlier? Anyway, I continued to the next step, extracted the tarball, and entered the alsa-driver directory to enter the command:

```

sudo ./configure --with-kernel=/usr/src/linux-headers-$2.6.24-19-generic --with-cards=intel8x0 --with-oss=yes 

```

```

The file /usr/src/linux-headers-.6.24-19-generic/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.24-19-generic/build).

```

I don't have the headers, so I try to install them:

```

sudo apt-get install build-essential kernel-headers-$2.6.24-19-generic

```

It doesn't work. I searched the Ubuntu packages area and added 

```
deb http://fr.archive.ubuntu.com/ubuntu hardy-updates main 

```
to my /etc/apt/sources.list

I tried it again, but it still didn't work. I'll cat it. Yep, it's on the last line.

Dang, I just checked again and it says "Replacing fr.archive.ubuntu.com/ubuntu with the mirror in question." Uh, ok. I'll change it to:

```

deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main

```

I'll try to get the headers again. ****. I'll just download it manually. Oh, wait, maybe if I use one of those mirrors down there it will work. I'll change the line in sources.list

```

deb mirrors.kernel.org/ubuntu hardy-updates main

```

What the hell? Bad line? Awwww. Let me check the directory in that command to see if it exists... yep it sure does. I'm doing something wrong. I'll just try to build it without the -with kernel option.

```
sudo ./configure --with-cards=intel8x0
```

Wow, it worked. Sudo Make, Sudo Make Install.

```

ALSA modules were successfully compiled.

```

Yay.

```

sudo modprobe snd-intel8x0

```

???? Nothing?

```

aplay -l

aplay: device_list:205: no soundcards found...

```

Doh.:confused:

---

