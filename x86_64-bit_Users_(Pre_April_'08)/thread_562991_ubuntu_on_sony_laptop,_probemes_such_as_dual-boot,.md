---
title: "ubuntu on sony laptop, probemes such as dual-boot, video resolution and others"
date: 2007-09-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by user_2492007 on 2007-09-29
Problems during installation of Ubuntu on Sony laptop

I have tried installation of Ubuntu 7.04 through x86-64bit live CD on Sony laptop two times, but the installation is not successful yet. The model no. for laptop is Sony VGN-FZ145E. The laptop has Intel core-2-dual processor, 3100 Video Graphics from Intel (965G chip set), 160 GB hard disk, and DVD-RW drive.

During first installation, booting from Ubuntu live CD, I got following message error and system hangs, I have searched the internet to find the solution for this type of error. 

Error when installing :
/bin/sh: can't access tty; job control turned off

Then I typed command as below and it worked successfully. 

modprobe piix 
Exit

Then I got a screen with Install icon, I started installation of Ubuntu with largest free space from the partition option, I have initially tried with manual option, but it failed to proceed ahead. 

Then I able to install Ubuntu on a system using largest free space available. I boot the system using Ubuntu option during the grub menu.


1.Dual boot system;

	As I have successfully install Ubuntu on laptop, I have chose 	Ubuntu system from the grub menu. I log in to Ubuntu using the 	boot menu, and played some time with the Ubuntu OS. 

Ubuntu, Kernel 2.6.20-15-generic
Ubuntu, Kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)

When I choose windows vista/longhorn option after restarting laptop to see windows OS, then system hangs and shows the following errors.

Grub loading stage 1.5

Grub loading , please wait
Error 22


After getting this menu I boot the system using Ubuntu live CD and install Ubuntu second time successfully. I played the Ubuntu system some time and updated the kernel through internet.
Now during re-start of the laptop I can see the grub menu with following options.

Ubuntu, Kernel 2.6.20-16-generic
Ubuntu, Kernel 2.6.20-16-generic (recovery mode)
Ubuntu, Kernel 2.6.20-15-generic
Ubuntu, Kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)
Windows Vista/Longhorn (loader)


I am using the Ubuntu option to log in Ubuntu system. 
I have not tried still vista option to boot in windows operating system. Kindly provide the help for dual OS boot so that I can use both operating system..

2.Video resolution
During the installation of Ubuntu my resolution is 800 x 600. After installation I get only two options such as 800 x 600 and 640 x 600. I could not get 1024 x 800 video resolution, which was default for vista. So kindly help to fix the resolution problem for Sony laptop with Intel 965 chip set. It has 3100 graphics resolution. 

3.DVD-RW not accessible
I could not able to read CD or DVD after installation. It shows the following error message when I try to read CD or DVD.

So kindly help me to solve all these problems.

Waiting for help.

user_2492007

---

### Post by David A Knight on 2007-09-30
Try adding

all_generic_ide

to the command line in grub (press e to edit the command line on the line you are wanting to boot)

---

