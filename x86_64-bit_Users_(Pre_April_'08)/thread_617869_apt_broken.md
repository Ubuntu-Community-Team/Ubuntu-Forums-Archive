---
title: "apt broken"
date: 2007-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-11-19
It has been working for about a year. Recently I install mdadm, and apt gave me lots of errors. I attempted to remove the package with apt, and it would not remove but instead gave me the same error messages again. Then I used dpkg -P mdadm and the package did get removed. However, I can't use apt to remove or add anything any more. I get an error about a kernel module directory for the kernel I configured and compiled. I tried using the Ubuntu kernel that comes with Ubuntu instead and then run sudo dpkg --configure -a. That did not solve the problem. Here is the error message I get.

chris@ubuntu:~/Desktop/pcsx2$ sudo apt-get install libglew1.4-dev
[sudo] password for chris:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
chris@ubuntu:~/Desktop/pcsx2$
chris@ubuntu:~/Desktop/mutt-1.4.2.3$ sudo apt-get --purge remove mutt
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

Also 2.6.23.1custom1 is not a kernel I was using when this all occurred. It was a kernel I compiled vanilla kernel I compiled and removed a while ago because I could not compile vmware kernel modules while using it. When the errors began, I was using a kernel I compiled from the linux-source Ubuntu package that included patches. How can I fix apt?

---

### Post by go_beep_yourself on 2007-11-20
It has been working for about a year. Recently I install mdadm, and apt gave me lots of errors. I attempted to remove the package with apt, and it would not remove but instead gave me the same error messages again. Then I used dpkg -P mdadm and the package did get removed. However, I can't use apt to remove or add anything any more. I get an error about a kernel module directory for the kernel I configured and compiled. I tried using the Ubuntu kernel that comes with Ubuntu instead and then run sudo dpkg --configure -a. That did not solve the problem. Here is the error message I get.

chris@ubuntu:~/Desktop/pcsx2$ sudo apt-get install libglew1.4-dev
[sudo] password for chris:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
chris@ubuntu:~/Desktop/pcsx2$
chris@ubuntu:~/Desktop/mutt-1.4.2.3$ sudo apt-get --purge remove mutt
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

Also 2.6.23.1custom1 is not a kernel I was using when this all occurred. It was a kernel I compiled vanilla kernel I compiled and removed a while ago because I could not compile vmware kernel modules while using it. When the errors began, I was using a kernel I compiled from the linux-source Ubuntu package that included patches. How can I fix apt?

---

### Post by rmemm on 2007-11-20
Can you fix this by going into synaptic and using the Fix Broken Packages menu option?  By the way -- there is also a custom filter that will find all broken packages also.

Just a thought.

Rob

---

