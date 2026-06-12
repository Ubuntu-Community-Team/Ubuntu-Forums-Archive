---
title: "problems kernel 2.6.28-14-generic"
date: 2009-07-29
forum: x86 64-bit Users
---

### Post by didi32 on 2009-07-29
Hello,

I believe my kernel was updated this morning with the automatic updates. Since then, I cannot use VirtualBox anymore and get the following message when trying to  launch the guest:

```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

Last time the kernel was updated I got the same issue, but I was able to solve it with DKMS.

This time it is not possible.

Here is what I get when I execute sudo /etc/init.d/vboxdrv setup:

```

 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

```

and if i look at vbox-install.log:
```

Attempting to install using DKMS
  removing old DKMS module vboxdrv version  2.2.4

------------------------------
Deleting module version: 2.2.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.2.4/source ->
                 /usr/src/vboxdrv-2.2.4

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.28-14-generic cannot be found at
/lib/modules/2.6.28-14-generic/build or /lib/modules/2.6.28-14-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:148: Warning: using /usr/src/linux as the source directory of your Linux kernel. If this is not correct, specify KERN_DIR=<directory> and run Make again.
Makefile:156: *** Error: /usr/src/linux (version 2.6.28-11-generic) does not match the current kernel (version 2.6.28-14-generic).  Stop.

```


Now, I thought the issue could get fixed after removing/reinstalling DKMS, which I did. It didn't work anyway, and I got the following return from the installation:
```

Unpacking dkms (from .../dkms_2.0.21.1-0ubuntu3_all.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.0.21.1-0ubuntu3) ...
 * Running DKMS auto installation service for kernel 2.6.28-14-generic           *  vboxdrv (2.2.4)...                                                   [fail] 
 *  vboxnetflt (2.2.4)...                                                [fail] 

```

What is happening here, and how do I get virtualbox to work.

Thanks for your help!

---

### Post by nmaster on 2009-07-29
bump.  I have the same problem.  Would reinstalling fix the problem?

---

### Post by didi32 on 2009-07-29
Hello,

Well I've tried to reinstall VirtualBox, if that's what you mean, and I got no luck with that either.

---

### Post by didi32 on 2009-07-29
FYI, here is what I get when I try to reinstall-- Thanks! :
```

VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-<version> whereby <version> can be determined by 'uname -r') and execute

  /etc/init.d/vboxdrv setup

as root.


```

---

### Post by didi32 on 2009-07-29
Uninstalled the deb package. Then downloaded the new virtualbox 3 deb package, and installed it. The installation failed as well because the new kernel cannot be found.

[...] I'm sure everybody using VirtualBox Puel is having the same issue, so let's hope someone gets to find a fix.

Thanks!

---

### Post by didi32 on 2009-07-29
Uninstalled the deb package. Then downloaded the new virtualbox 3 deb package, and installed it. The installation failed as well because the new kernel cannot be found.

[...] I'm sure everybody using VirtualBox Puel is having the same issue, so let's hope someone gets to find a fix.

Thanks!

---

### Post by For The People on 2009-07-29
I had the same problem this morning... After a look around I tried a couple things that worked for me....

1. Reinstall DKMS... I used synaptic..
2. Run 
               sudo /etc/init.d/vboxdrv setup

to recompile the kernal module. 

After that I got VB up and running....

---

### Post by didi32 on 2009-07-29
Hello,

For some reason, reinstalling dmks didn't work for me. I did so, once more, but this time with synaptic. Then, I tried the vbox setup command line, but it fails as usual.

And in the details of synaptic for the reinstallation, I can see:

```

vboxdrv (3.0.2)...
... Fail!

```

I guess my next step will be to try to remove the new kernel, then try to reinstall it again and see if it is any better.

If you have any other idea, I'd be more than happy to read it!

Thanks!

---

### Post by didi32 on 2009-07-29
Hey guys!

I finally found what was preventing me from using DKMS and the setup command for vbox. The kernel was actually properly installed, but linux-headers-2.6.28-14 package wasn't.

After installing this package, the problem was fixed!

---

### Post by For The People on 2009-07-30
Nice one! I'm sure there are tons of people who need this fix..

---

### Post by bjtuna on 2009-07-30
Running /etc/init.d/vboxdrv setup worked for me. Thanks!

---

### Post by nmaster on 2009-07-30
sweet! when i get out of work i'll try this stuff.  thanks all!

---

### Post by coogur on 2009-07-30
I think you may have to download and install, extract the kernel header from the kernel source package.  From my understanding, virtualbox is trying to re-compile it's modules base on your installed kernel and can't locate the file, header-libraries required.

---

