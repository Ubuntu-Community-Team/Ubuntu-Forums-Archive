---
title: "Warty AMD64 fails to install?"
date: 2005-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by gratefulfrog on 2005-01-22
I have tried to install the warty amd64 version several times with several downloads all of which check out ok on the md5 of the image file, but then fail to install due to "missing" kernel-amd64-generic pacakge.

The media check in the boot helper tells me that the file 
./dists/wart/main/binary-amd64/Packages fails MD5 checksum.

But when I run the md5's on the accused file, it checks out ok, according to the master md5sums.txt file.

I have burned the cd at various speeds from various download mirrors, all give the same result, that is they are perfect, but will not install due to "missing" packages.

The last messages are:
> Err file: warty/main Packages
  Read error - read (5 Input/output error)
Failed to fetch file:///cdrom/dists/warty/main/binary-amd64/Packages.gz  Read error - read (5 Input/output error)
Reading Package Lists...
E: Some index files failed to download, they have been ignored, or old ones used instead.
Reading Package Lists...
Building Dependency Tree...
W: Couldn't stat source package list file: warty/main Packages (/var/lib/apt/lists/_cdrom_dists_warty_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
initrd-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading Package Lists...
Building Dependency Tree...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-amd64-generic: Depends: linux-image-amd64-generic but it is not installable
E: Broken packages



Has anyone gottent the amd64 version to install properly?

Is there another way of getting an amd64 version?

Any ideas would be welcome! :D 

Platform:
AMD64 3000+ 939 pin
Asus A8V Deluxe motherboard
ATI 9250 AGP 8x card (set to 4x in bios)
maxtor 160G stata drive

Ciao,
Gratefulfrog

---

### Post by Dylanby on 2005-01-22
I had a similar problem months ago.
I had disks which were good, but which just wouldn't install. Don't know if it was a dma issue or what.

I ended up doing a netinstall. You can try it if you're on broadband.
I used the mini.iso burned onto cdrw. See here:
[http://archive.ubuntu.com/ubuntu/dists/warty/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/warty/main/installer-amd64/current/images/netboot/)

&

[http://archive.ubuntu.com/ubuntu/dists/warty/main/installer-amd64/release/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/warty/main/installer-amd64/release/images/netboot/)

I would recommend the current image if you go that way. The md5sum's are in the parent directory.

---

### Post by gratefulfrog on 2005-01-23
Forgive my ignorance...

Do I just download the > mini.iso image, check its md5, and boot from that?

Anyway thanks for the help!

---

### Post by Dylanby on 2005-01-24
Yep.
'cause it's a network install it may take a while to fetch all of the packages for installation.
Good luck!

---

### Post by xpt on 2005-01-24
[QUOTE=gratefulfrog]
Has anyone gottent the amd64 version to install properly?
[/QUOTE]

Hi, I can't tell what your problem is, but one thing I can tell for sure: 

I download and install amd64 version just several days ago. Everything seems fine. I'm just fighting with the 32-bit chroot now. and it too seems to be installed perfectly.

---

### Post by gratefulfrog on 2005-01-25
thanks for all the feedback.

I've tried the netinstall using the mini.iso and ... failure once again. I have taken this to the ubuntu bugzilla (bug 5723 for those interested).

We can close this thread... unless there is someone out there who has managed to resolve this exact issue!  :!:

---

