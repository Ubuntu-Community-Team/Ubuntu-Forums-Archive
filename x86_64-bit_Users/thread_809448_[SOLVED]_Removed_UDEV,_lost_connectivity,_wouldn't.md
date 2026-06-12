---
title: "[SOLVED] Removed UDEV, lost connectivity, wouldn't re-install, now won't boot"
date: 2008-05-27
forum: x86 64-bit Users
---

### Post by duhbunto on 2008-05-27
Hi,
Okay, before I start I now realise I'm a berk.
With that out of the way, here's my tale of woe::(
_Background_
I had a lovely 64bit 7.10 system doing all I wanted. I felt so good about it I put it on my mum's PC as didn't like her being fleeced for updated anti-virus etc every year and I was struggling to act as a remote I.T. helpdesk on an unfamiliar OS from 300 miles away (she was on XP).
Despite me telling her not touch anything she 'accidentally' upgraded to Hardy.

So that I could continue to compare like for like, I also upgraded 2 days ago. Looked at Hardy loved it, slightly worried when PC crashed (total death) when I inserted a picture CD but that problem is for another day.

_Problem 1_
I couldn't print. 
I have a Samsung 2010, hooked in through USB,worked like a dream in Dapper through CUPSYS. 
Looked through the threads, found a few that seemed to indicate a problem recognisingg the peripherals attached by USB. 
I tried lsusb and it showed all the relevant peripherals. 
I could see the printer but the job stopped almost as soon as it was sent (tried printing from Evolution and Open Office). 
Found a thread which I interpreted as suggesting to remove udev and re-install.......

_Problem 2_ 
Having removed udev in Synaptic, I then tried to re-install udev in Synaptic. It couldn't resolve the repository, a few frustrated attempts showed that in fact I was no longer networked. The 
network icon has gone from the banner at the top of the screen. I tried connecting via the LAN (rather than WiFi) but to no avail, it just didn't see any network connectivity. Using a very little knowledge I decided to re-boot, but........
On reboot I get "Error 15: File not Found  /  Press any key to continue".

I need help....

Here's what I'm planning:
Download a Live CD of Hardy
Mount 8.04 as a partition (not sure how anymore)
Re-install udev

Can anybody tell me if that will work ?
Is there a better way?

Assuming that I can get udev installed, it should work again right?

Am I better off forgetting about it and doing a clean install?

Looking for a bit of help and a sympathetic ear.

Thanks

Dave

---

### Post by Cappy on 2008-05-27
Using the Live CD is going to be the easiest way.

Chrooting is how you can log into the ubuntu partition from the live cd:
[http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html)

Another option is to just install udev by putting in the CD while ubuntu is running and it will give you the option of using its software packages rather than using the internet.

---

### Post by chrisccoulson on 2008-05-27
Yes, you will definately need to repair from the live CD. Bare in mind that removing udev will have removed a lot of other stuff (most of the desktop I think). To do this, boot the live CD and then do the following in a terminal:
```
sudo mkdir /mnt/target
sudo mount -t ext3 /dev/xxxx /mnt/target
sudo mount --bind /dev /mnt/target/dev
sudo mount -t proc proc /mnt/target/proc
sudo mount -t sysfs sysfs /mnt/target/sys
sudo chroot /mnt/target
apt-get update
apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop
exit

```
...substitute /dev/xxxx for your root filesystem (you're the only one who knows this)

---

### Post by duhbunto on 2008-05-27
Thanks guys,

I guess I'm only proving my first point here but....

I'm absolutely certain that my main boot disc is dev/hda1

I can create the target directory in mnt (& hardy in media, tried them both in desperation) no problem.

Then the second line is giving me problems: 

I type: sudo mount -t ext3 /dev/hda1 /mnt/target

and I get:  special device /dev/hda1 does not exist

I've tried /dev/hda 1 ..... and then I get the spiel about how to use Mount options (a bit beyond me if the truth is known, but I have looked at it)

I also treid not specifying the type

Have interpreted the instructions wrongly?

Thanks

Dave

---

### Post by chrisccoulson on 2008-05-27
It seems /dev/hda1 doesn't exist. What is the output of:
```
sudo fdisk -l
```

---

### Post by duhbunto on 2008-05-27
Chris, 

Its:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe31be31b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12289693+  83  Linux
/dev/sda2            4524        4865     2747115    5  Extended
/dev/sda3   *        1531        4523    24041272+  83  Linux
/dev/sda5            4678        4865     1510078+  82  Linux swap / Solaris
/dev/sda6            4659        4677      152554+  82  Linux swap / Solaris
/dev/sda7            4524        4658     1084324+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10bf082f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3386    27198013+  83  Linux
/dev/sdb2            3387        6519    25165822+  83  Linux
/dev/sdb3            6520        9729    25784325   83  Linux


Think I can see where this is heading so trying sda3 in place of hda1. Looking good so far will come back to you when I've got past apt-get update

Thanks again

PS - When I get the black screen at boot where you can select the kernel version and /or  recovery mode I have 6 unnamed options with 8.04, a memtest option and then 6 older options listed as dev/hda1 .. that's why I was convinced I wanted hda1

---

### Post by duhbunto on 2008-05-27
Back again. 

It all seemed to be going well. 

replaced hda1 with sda3. 

Went through all remaining command line entries without issue or comment until the last one. This suggested that I run apt-get install -f, which I did without a problem, this seemed to be okay and said it was installing udev.

It looked so good that I exited, rebooted and got the same Error 15: File not found problem. Back to the Live CD, will re-mount sda3, look in etc for udev, but after that I'm flummoxed again. Any ideas where I may have gone wrong or where best to look to show you what's missing?

Many thanks again.

Dave

---

### Post by chrisccoulson on 2008-05-27
Have you installed ubuntu-desktop, ubuntu-standard and ubuntu-minimal?

---

### Post by duhbunto on 2008-05-27
I certainly thought that I had first time around as it was then that it was prompting me for the apt-get install -f. 

However, having gone back to the live CD it wanted a lot more packages the second time around so I doubt that I typed it in right first time.

This second time round I've gone through the command line instructions from scrath and I've C&P'd the last command, and the first bit of the output, skipped all the download bits and pasted the 'errors' (?) below. Is there anything else I should do before I try a reboot?

root@ubuntu:/# apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-standard is already the newest version.
The following packages were automatically installed and are no longer required:
  nvidia-kernel-common linux-headers-2.6.24-16 linux-headers-2.6.24-16-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  brltty brltty-x11 console-setup gnome-mount gnome-power-manager
  gnome-session gnome-volume-manager hal hal-cups-utils network-manager
  network-manager-gnome pcmciautils pulseaudio-module-hal sound-juicer
  update-notifier usplash usplash-theme-ubuntu
Suggested packages:
  brltty-flite festival libbrlapi-dev desktop-base gnome-device-manager
Recommended packages:
  libsmbios-bin
The following NEW packages will be installed:
  brltty brltty-x11 console-setup gnome-mount gnome-power-manager
  gnome-session gnome-volume-manager hal hal-cups-utils network-manager
  network-manager-gnome pcmciautils pulseaudio-module-hal sound-juicer
  ubuntu-desktop ubuntu-minimal update-notifier usplash usplash-theme-ubuntu
0 upgraded, 19 newly installed, 0 to remove and 3 not upgraded.
Need to get 5480kB/6870kB of archives.
After this operation, 40.9MB of additional disk space will be used.
Do you want to continue [Y/n]? [I]y

downloads - loads[/I]

ends....


Setting up brltty-x11 (3.9-6ubuntu1) ...
Processing triggers for initramfs-tools ...
Errors were encountered while processing:
 hal
 gnome-mount
 gnome-power-manager
 gnome-session
 gnome-volume-manager
 hal-cups-utils
 network-manager
 network-manager-gnome
 pulseaudio-module-hal
 sound-juicer
 update-notifier
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

What do you think, reboot?

D

---

### Post by chrisccoulson on 2008-05-27
Try exiting the chroot, unmounting /dev, /proc and /sys from it, going back in and then trying to fix it:
```
exit
sudo umount /mnt/target/dev
sudo umount /mnt/target/proc
sudo umount /mnt/target/sys
sudo chroot /mnt/target
apt-get install -f
```

---

### Post by duhbunto on 2008-05-27
Chris,

Just tried that, errors look similar to me but I'll post them in full this time. It looks to me like if I could configure hal (don't know what that is or how to do it!) then it may all fall into place(?):

root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/target/dev
ubuntu@ubuntu:~$ sudo umount /mnt/target/proc
ubuntu@ubuntu:~$ sudo umount /mnt/target/sys
ubuntu@ubuntu:~$ sudo chroot /mnt/target
root@ubuntu:/# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nvidia-kernel-common linux-headers-2.6.24-16 linux-headers-2.6.24-16-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
12 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up hal (0.5.11~rc2-1ubuntu8.1) ...
invoke-rc.d: initscript dbus, action "force-reload" failed.
polkit-auth: This operation requires the system message bus and ConsoleKit to be running
polkit-auth: AuthorizationAlreadyExists: An authorization for uid 107 for the action org.freedesktop.policykit.read with constraint '' already exists
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on hal (>= 0.5.10); however:
  Package hal is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on gnome-mount; however:
  Package gnome-mount is not configured yet.
 gnome-volume-manager depends on hal (>= 0.5.5.1); however:
  Package hal is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-cups-utils:
 hal-cups-utils depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hal-cups-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on hal (>= 0.5.7.1); however:
  Package hal is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-hal:
 pulseaudio-module-hal depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing pulseaudio-module-hal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sound-juicer:
 sound-juicer depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing sound-juicer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on gnome-volume-manager; however:
  Package gnome-volume-manager is not configured yet.
 ubuntu-desktop depends on hal; however:
  Package hal is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 gnome-mount
 gnome-power-manager
 gnome-session
 gnome-volume-manager
 hal-cups-utils
 network-manager
 network-manager-gnome
 pulseaudio-module-hal
 sound-juicer
 update-notifier
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 

Cheers

dave

---

### Post by chrisccoulson on 2008-05-27
The problem is is that ConsoleKit and DBUS aren't running in the chroot environment, causing the install scripts to fall over. Also, /mnt/target/dev needs to be mounted again. The hal script expects /dev/pts to exist in the chroot environment.

Not sure what else to suggest.

You should be able to boot at least to a command line system now though and finish off the install by doing 'sudo apt-get install -f'. If you can't, then there is something else wrong

---

### Post by duhbunto on 2008-05-28
Thanks for your help there. 

I'm not sure that I follow all of the first paragraph. I think what I'm going to do is use many of the instructions you gave me to go in and back up  my data and then do a clean install of Hardy. 

Whilst it'll be a pain to install everything I want again, I think there's a better than fair chance that the printer should work on a fresh install.

Will have a go tonight and report back tomorrow. 

Dave

---

### Post by duhbunto on 2008-05-30
Ended up doing a clean install. I guess that's giving up in some ways but I'm happy and going to mark this solved in the hope that nobody else see's the mess I made of what should have been a simple fix. 
Even a fresh install wasn't totally straightforward. 
I couldn't back up all my data due to various permissions and locks on files that I didn't have the patience to work around. I don't think I lost anything too important.
Formatted disk using fdisk (terminal) whilst in Live CD
Then fresh install, then it's the exciting bit of looking at all the new programs to choose. Surprised at how things have come along in the last year or so.
AND - THE PRINTER WORKS.

---

