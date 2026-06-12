---
title: "VirtualBox Error..."
date: 2009-04-23
forum: x86 64-bit Users
---

### Post by CyberPrime on 2009-04-23
When I run VirtualBox I get this error,
```

Virtual machine 'Name Here' has terminated unexpectedly during startup.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {ea6fb7ea-1993-4642-b113-f29eb39e0df0}

```

then I get this one,
```
VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

Why is this? I have had this during the beta of 9.04 as well, and I am surprised it hasn't been fixed. I have reinstalled VirtualBox from many places, including the Sun site, and I have ran "/etc/init.d/vboxdrv setup" only to get this output:
```
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         /etc/init.d/vboxdrv: 342: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong

```

any ideas? Here's the content of /var/log/vbox-install.log
```
Attempting to install using DKMS
  removing old DKMS module vboxdrv version 

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.1.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.1.4/source ->
                 /usr/src/vboxdrv-2.1.4

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.27-11-generic cannot be found at
/lib/modules/2.6.27-11-generic/build or /lib/modules/2.6.27-11-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:143: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

Thanks for your time.

---

### Post by bela42 on 2009-04-24
Well...

> Error: unable to find the sources of your current Linux kernel.

But you are sure, you did install all packages neccessary to compile a kernel module?

I'm running Sun's amd64 binary packages (for Intrepid) since 9.04 beta, no problems so far.

---

### Post by cariboo on 2009-04-24
I just installed VirtualBox 2.1.4 this morning, and haven't had any problems. I downloaded the package [here]("http:///www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by lee.eden on 2009-04-24
I'm having exactly this problem too (precisely as decribed by CyberPrime)

Upgraded today from 8.10 on an AMD 64 bit machine.  Lots of trouble, this is just the latest one in the list.  Didn't have virtual box installed previously, so can't say for certain whether this is a 9.04 problem or not.

---

### Post by cariboo on 2009-04-24
I would suggest you check and make sure you are fully upgraded, as Janunty is running kernel 2.6.28-11.

Open a terminal and type:

```
sudo apt-get -f install
```

to make sure there aren't any missing dependencies then type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by evermooingcow on 2009-04-24
The error looks like youre missing the kernel headers.  Do you have linux-headers-(kernel version) installed?

---

### Post by CyberPrime on 2009-04-24
Interestingly enough virtualbox won't even start anymore after another reinstall. Also, I am fully up to date (don't you think i would have tried that?) and saying that you don't have the problem, interestingly enough, doesn't help our situation.

---

### Post by jkarcz on 2009-04-24
Anything interesting from dmesg or /var/log/syslog?

---

### Post by CyberPrime on 2009-04-27
Well, I installed as much as I could that looked related to virtualization, and reinstalled virtualbox about 10 times and lookey here, it works! Hmm... I'm missing all my machines, but it works.

---

### Post by cariboo on 2009-04-27
IF you still have your vm's stored on your hard drive, you can go to File-->Virtual Media Manager and just add the machines, then you can just setup the new vm's without having to reinstall them.

I just finished setting up Virtual box on Karmic Koala. It takes less than a couple of minutes to set up each vm.

---

### Post by CyberPrime on 2009-04-28
Yea, I restarted VirtualBox and bam, there they are. Curious.

---

### Post by lee.eden on 2009-04-28
Just to let you know that it's all working for me too now.  After multiple problems with just about everything I gave up on my upgraded (from 8.10) version of 9.04 and wiped the whole thing and did a fresh install.  Everything is now fine.

I really can't see the point of upgrading from within an existing ubuntu installation if anyway all the applications get removed (and then fail to work on reinstallation).  I anyway keep my data seperate from the linux file-system so from now on I will only ever do fresh installs.  The whole thing cost me a day, and all I got out of it was a slightly faster boot time.  You live and learn.

---

### Post by chikaku on 2009-05-18
chika@earth:/mnt$ sudo apt-get install linux-headers-2.6.18-6-all

then do...

chika@earth:/mnt$ sudo /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel module: done.
Recompiling VirtualBox kernel module: done.
Starting VirtualBox kernel module: done.

:popcorn:

chika.tambun

debian-etch

---

