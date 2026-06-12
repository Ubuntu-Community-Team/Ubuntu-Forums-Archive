---
title: "Cannot find /lib/modules/2.6.23.1custom1"
date: 2007-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-11-18
Since installing mdadm, my package manager has broke. I used dpkg -P to remove mdadm, and still, it is broke. I can not add or remove any other packages using apt. Here are some errors that I get.

```
chris@ubuntu:~/Desktop/pcsx2$ sudo apt-get install libglew1.4-dev
[sudo] password for chris:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
chris@ubuntu:~/Desktop/pcsx2$ 
chris@ubuntu:~/Desktop/mutt-1.4.2.3$ sudo apt-get --purge remove mutt 
[sudo] password for chris:
Sorry, try again.
[sudo] password for chris:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
chris@ubuntu:~/Desktop/mutt-1.4.2.3$
chris@ubuntu:~/Desktop/mutt-1.4.2.3$ sudo dpkg --configure -a
[sudo] password for chris:
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.23.1custom1
Cannot find /lib/modules/2.6.23.1custom1
update-initramfs: failed for /boot/initrd.img-2.6.23.1custom1
dpkg: subprocess post-installation script returned error exit status 1
You have new mail in /var/spool/mail/chris
chris@ubuntu:~/Desktop/mutt-1.4.2.3$ 
```

---

### Post by mkoyle on 2007-11-18
Did you compile your own kernel?  It seems like it is looking for a directory that does not exist and has no way to complete installation when it does not find it.  If you did compile your own, it appears your modules directory is missing.  If that doesn't make sense (i.e. you don't know what to do to fix that) I would go back to a default kernel from the repositories.  You need a really good reason to do otherwise, honestly.  I used to try making my own kernel for various reasons, but most of them have been fixed-- I can download .deb kernels through apt that fill my needs.

To go back to stock kernels, IF you did not uninstall all of your other kernels, do the following:

Restart and select a stock kernel when the grub menu comes up (something like 2.6.22-14-generic in stead of the default 2.6.23.1custom1).  Then open a terminal and do the following:

```
cd /boot
ls
```

That should display all of the kernel-related boot files.  My directory looks like this:

```
matthew@Abish:/boot$ ls -l
total 36000
-rw-r--r-- 1 root root  417807 2007-10-14 19:25 abi-2.6.22-14-generic
-rw-r--r-- 1 root root   67666 2007-10-14 19:25 config-2.6.22-14-generic
-rw-r--r-- 1 root root   74859 2007-10-14 19:37 config-2.6.22-14-rt
drwxr-xr-x 2 root root    4096 2007-11-18 14:51 grub
-rw-r--r-- 1 root root 7376619 2007-10-15 18:27 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root 7933375 2007-10-15 01:08 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root 7742260 2007-11-02 20:40 initrd.img-2.6.22-14-rt
-rw-r--r-- 1 root root 7382182 2007-11-02 20:38 initrd.img-2.6.22-14-rt.bak
-rw-r--r-- 1 root root  103204 2007-09-28 07:03 memtest86+.bin
-rw-r--r-- 1 root root 1052596 2007-10-14 19:25 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root 1073623 2007-10-14 19:37 System.map-2.6.22-14-rt
-rw-r--r-- 1 root root 1743368 2007-10-14 19:25 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root 1783464 2007-10-14 19:37 vmlinuz-2.6.22-14-rt
```

```
sudo rm *2.6.23.1custom1*
sudo update-grub
```

After that, try those commands again

```
sudo dpkg --configure -a
sudo apt-get install libglew1.4-dev
```

You'll probably be back in business.  Post again if you have questions.

---

### Post by go_beep_yourself on 2007-11-18
That's not a good option. I would like to learn how to get my own compiled kernel working with everything else. That's why I am here on the forum asking.

---

### Post by go_beep_yourself on 2007-11-19
Besides that, I want experiemental kernel features like networking support for distributed computing with Plan 9. Using the stock ubuntu kernel does not fix the problem. Running sudo dpkg --configure -a while using the stock kernel does not fix the problem.chris@ubuntu:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.23.1custom1
Cannot find /lib/modules/2.6.23.1custom1
update-initramfs: failed for /boot/initrd.img-2.6.23.1custom1
dpkg: subprocess post-installation script returned error exit status 1
chris@ubuntu:~$ uname -a
Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
chris@ubuntu:~$ 

This ubuntu kernel version is old. I don't want it, and using it isn't solving the problem.

---

### Post by mkoyle on 2007-11-20
If you need a custom kernel, that's fine.  Before I make you more annoyed by asking more questions, remember you are asking for free assistance and I am not the absolute kernel-building wiz.

How did you build the kernel?  Do you happen to know what how-to you used or have a list of the instructions you used?  If you did not build and install your modules, the following might help:

```
make modules
su
make modules_install
```

Basically, initramfs (the program that builds the boot-up file system) cannot find your module information.  Without the modules for your kernel you would probably not be able to boot (and certainly not be able to use any hardware that has the drivers as a module).

Just to give you an idea why I can't answer your question with confidence, there are zillions of ways to configure a kernel and just as many different patches that you could apply.  When I have done it I have occasionally been left with errors or problems that I had to figure out on my own.  Most of the Ubuntu community just doesn't go building their own kernels.

Anyway, with an idea of how you created your kernel I might be able to come up with a solution.

If the make modules_install command above didn't fix it, I will need some more information to keep looking for a solution.  Post the output from ls in the kernel build/source directory and

```
ls /boot
ls /lib/modules
```

--Matthew

---

### Post by mkoyle on 2007-11-20
By the way, which release of Ubuntu are you using?  I'm just chuckling to myself that you say the Ubuntu kernel is old because mine

matthew@Abish:~$ uname -a
Linux Abish 2.6.22-14-rt #1 SMP PREEMPT RT Sun Oct 14 22:53:32 GMT 2007 x86_64 GNU/Linux

is a 2.6.22 kernel.  If you go looking, you will see that 2.6.22 was released in July this year (and they built it on October 14).  That is anything but old in the realm of kernels.  Of course, 2.6.23 has been out for about three weeks so it is newer. You mentioned Plan 9 and distributed computing.  Do you have a particular use in mind or a particular web page that is giving you ideas?

--Matthew

---

### Post by armalite on 2007-12-10
I had the same problem with an initrd of a custom kernel i built, installed and already removed some time ago. 
I don't know why, but "dpkg --configure -a" complained about a not-existent kernel:


```
root@hyperion:/usr/src# dpkg --configure -a
Configuro initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22.9-hyperion
Cannot find /lib/modules/2.6.22.9-hyperion
update-initramfs: failed for /boot/initrd.img-2.6.22.9-hyperion
dpkg: il sottoprocesso post-installation script ha restituito un codice di errore 1
```

I deleted the file /boot/initrd.img-2.6.22.9-hyperion and retried with "dpkg --configure -a" with no success. Note that there are no kernel-, vmlinuz- or similar of this specific kernel version, and /lib/modules has only the 22.14-generic standard ubuntu modules, no custom built modules.
Synaptic won't start, just complained to run the above dpkg command. Aptitude same thing. I was just stuck, until i tried:

```
root@hyperion:/boot# update-initramfs -k 2.6.22.9-hyperion -d
update-initramfs: Deleting /boot/initrd.img-2.6.22.9-hyperion
```

Finally, i could successfully run "dpkg --configure -a", now synaptic works again and mdadm is installed.

---

### Post by go_beep_yourself on 2007-12-10
> **mkoyle said:**
> If you need a custom kernel, that's fine.  Before I make you more annoyed by asking more questions, remember you are asking for free assistance and I am not the absolute kernel-building wiz.

How did you build the kernel?  Do you happen to know what how-to you used or have a list of the instructions you used?  If you did not build and install your modules, the following might help:

```
make modules
su
make modules_install
```

Basically, initramfs (the program that builds the boot-up file system) cannot find your module information.  Without the modules for your kernel you would probably not be able to boot (and certainly not be able to use any hardware that has the drivers as a module).

Just to give you an idea why I can't answer your question with confidence, there are zillions of ways to configure a kernel and just as many different patches that you could apply.  When I have done it I have occasionally been left with errors or problems that I had to figure out on my own.  Most of the Ubuntu community just doesn't go building their own kernels.

Anyway, with an idea of how you created your kernel I might be able to come up with a solution.

If the make modules_install command above didn't fix it, I will need some more information to keep looking for a solution.  Post the output from ls in the kernel build/source directory and

```
ls /boot
ls /lib/modules
```

--Matthew

[http://www.quietearth.us/articles/2006/09/15/Ubuntu-Compiling-a-custom-kernel](http://www.quietearth.us/articles/2006/09/15/Ubuntu-Compiling-a-custom-kernel)

These are the instructions I followed. Are they incorrect?

---

### Post by go_beep_yourself on 2007-12-10
> **mkoyle said:**
> By the way, which release of Ubuntu are you using?  I'm just chuckling to myself that you say the Ubuntu kernel is old because mine

matthew@Abish:~$ uname -a
Linux Abish 2.6.22-14-rt #1 SMP PREEMPT RT Sun Oct 14 22:53:32 GMT 2007 x86_64 GNU/Linux

is a 2.6.22 kernel.  If you go looking, you will see that 2.6.22 was released in July this year (and they built it on October 14).  That is anything but old in the realm of kernels.  Of course, 2.6.23 has been out for about three weeks so it is newer. You mentioned Plan 9 and distributed computing.  Do you have a particular use in mind or a particular web page that is giving you ideas?

--Matthew

I have Plan 9 running under Qemu. When I was configuring the kernel, I noticed that there was an experimental new feature that can be added to the kernel for networking with Plan 9.

chris@ubuntu:~/Desktop$ uname -a
Linux ubuntu 2.6.22.9chris1 #1 SMP Fri Oct 26 21:36:14 CDT 2007 x86_64 GNU/Linux
chris@ubuntu:~/Desktop$ 

The newest kernel version as of today is 2.6.23.9.

Your kernel is newer than mine and the linux-source package provides an older kernel than what is the stock ubuntu kernel. I'd rather not use the linux-source package and compile a vanilla kernel, but last time I did that, VMware Server would not run even after running sudo vmware-config.pl.

---

### Post by mkoyle on 2008-01-08
Sorry this is so late in coming.  I'm in law school and just went through finals and then went on a limited-internet vacation.

The howto you used should work but is rather limited... [http://symbolik.wordpress.com/2007/11/10/vanilla-kernel-26231-on-gutsy-gibbon/](http://symbolik.wordpress.com/2007/11/10/vanilla-kernel-26231-on-gutsy-gibbon/) seems to be directed at exactly what you want (but is still rather minimalist).  It seems you might be in a former version of Ubuntu.  I am still not certain if this is a testing/learning box or if it is a live environment.  If it is testing/learning, you probably want to upgrade to the latest version of ubuntu and then follow symbolik's howto.

If this is a live box, try symbolik's howto and see if it doesn't get you through.  

I am guessing that armalite's solution probably will get you out of the apt-get problem

> $ sudo update-initramfs -k 2.6.23.1custom1 -d


And the same for any other kernels that are giving you trouble.  I am guessing you have already solved the problem... post what you did if that is the case.

--Matthew

---

### Post by teslarage on 2008-02-28
I had the same problem and armalite solution worked for me. Thank you!

```
teslarage@PONSB-COE-DEV:/etc/initramfs-tools$ sudo dpkg --configure initramfs-tools
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-custom
Cannot find /lib/modules/2.6.24-custom
update-initramfs: failed for /boot/initrd.img-2.6.24-custom
dpkg: subprocess post-installation script returned error exit status 1
teslarage@PONSB-COE-DEV:/etc/initramfs-tools$ sudo update-initramfs -k 2.6.24-custom -d
update-initramfs: Deleting /boot/initrd.img-2.6.24-custom
teslarage@PONSB-COE-DEV:/etc/initramfs-tools$ sudo dpkg --configure initramfs-tools
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
teslarage@PONSB-COE-DEV:/etc/initramfs-tools$

```

---

