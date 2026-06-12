---
title: "Help with 32bit environment in Ubuntu 64 (Hoary)"
date: 2005-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by capriciousmind on 2005-04-11
Hi, I am trying to install a 32bit environment in my ubuntu 64 system.  Mainly for the use of wine.  I followed the directions from this site [http://www.nerdarium.com/archives/2005/03/13/new-64-bit-pc-ubuntu-32-bit-chroot-fun/](http://www.nerdarium.com/archives/2005/03/13/new-64-bit-pc-ubuntu-32-bit-chroot-fun/).   When I do the "dchroot -d" command I get this:

```
dchroot: chdir: No such file or directory
dchroot: Child exited non-zero.
dchroot: Operation failed.
```

I am not sure how to configure locales in this step:

```
chroot /var/32
dpkg-reconfigure locales
```

But I did add the local en-us UTF-8 because when i tried to apt-get in chroot it said that it need it (I not sure I was supposed to be messing around with chroot at this point).  If you can't tell I am a real newbie, so in chroot just for kicks I tried "apt-get install wine" and got this:

```
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.8.1-3-386: Depends: linux-image-2.6.8.1-3-386 but it is not going to be installed
  wine: Depends: libwine (= 0.0.20040615-1ubuntu1) but it is not going to be installed
        Depends: xbase-clients (>= 4.0) but it is not going to be installed or
                 xcontrib
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So, of course i tried "apt-get -f install" and got this:

```
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.8.1-3-386
Suggested packages:
  lilo grub linux-doc-2.6.8.1 linux-source-2.6.8.1
The following NEW packages will be installed:
  linux-image-2.6.8.1-3-386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
Need to get 0B/15.5MB of archives.
After unpacking 45.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 11792 files and directories currently installed.)
Unpacking linux-image-2.6.8.1-3-386 (from .../linux-image-2.6.8.1-3-386_2.6.8.1-16.1_i386.deb) ...

You are attempting to install an initrd kernel image (version 2.6.8.1-3-386)
This will not work unless you have configured your boot loader to use
initrd. (An initrd image is a kernel image that expects to use an INITial
Ram Disk to mount a minimal root file system into RAM and use that for
booting).

   As a reminder, in order to configure LILO, you need
   to add an 'initrd=/initrd.img' to the image=/vmlinuz
   stanza of your /etc/lilo.conf

I repeat, You need to configure your boot loader -- please read your
bootloader documentation for details on how to add initrd images.

If you have already done so, and you wish to get rid of this message,
please put
  `do_initrd = Yes'
in /etc/kernel-img.conf. Note that this is optional, but if you do not,
you'll continue to see this message whenever you install a kernel
image using initrd.
Do you want to stop now? [Y/n]
```

I wanted to be defiant so I answered "n" and this happened:
```
You are attempting to install a kernel image (version 2.6.8.1-3-386)
However, the directory /lib/modules/2.6.8.1-3-386 still exists.  If this
directory belongs to a previous linux-image-2.6.8.1-3-386 package, and if
you have deselected some modules, or installed standalone modules
packages, this could be bad. However, if this directory exists because
you are also installing some stand alone modules right now, and they
got unpacked before I did, then this is pretty benign.  Unfortunately,
I can't tell the difference.

If /lib/modules/2.6.8.1-3-386 belongs to a old install of
linux-image-2.6.8.1-3-386, then this is your last chance to abort the
installation of this kernel image (nothing has been changed yet).

If this directory is because of stand alone modules being installed
right now, or if it does belong to an older linux-image-2.6.8.1-3-386
package but you know what you are doing, and if you feel that this
image should be installed despite this anomaly, Please answer n to the
question.

Otherwise, I suggest you move /lib/modules/2.6.8.1-3-386 out of the way,
perhaps to /lib/modules/2.6.8.1-3-386.old or something, and then try
re-installing this image.
Do you want to stop now? [Y/n]
```

I was not as brave this time as I had no earthly idea what I was doing  :wink:. Could you please help?

---

### Post by HungSquirrel on 2005-04-11
Sure, we can help, but it's better if you start help topics in the appropriate forum.  ;)

[http://ubuntuforums.org/showthread.php?t=22348](http://ubuntuforums.org/showthread.php?t=22348)

---

### Post by capriciousmind on 2005-04-11
Sorry, Ill try another forum :-)

---

