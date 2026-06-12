---
title: "problem with yaboot..."
date: 2006-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jawbreaker4Fs on 2006-03-25
:evil: Hey,

I'm trying to install Ubuntu on a blue and white g3... and install seems to be working fine up until the "Install yaboot on a disk" step. When I get here it says

"The yaboot package failed to install into /target/. Installing Yaboot as a bootloader is a required step. The install problem however might be unrelated to Yaboot, so continuing the installation might be possible.

Yaboot installation failed. Continue anyway?"

When I attempt to continue the install, it still fails. I can't seem to get past this step. Does anyone have any suggestions/ideas?

Thanks!

---

### Post by linear on 2006-03-25
That's an OldWorld Mac, and as such won't boot directly. You will need to use BootX, as described here: [https://wiki.ubuntu.com/Installation/OldWorldMacs]("https://wiki.ubuntu.com/Installation/OldWorldMacs")

EDIT: Ignore that - for some reason I got B&W mixed up with Beige. :oops:

---

### Post by 3rdalbum on 2006-03-26
No, it's a NewWorld Mac, so Yaboot should work.

It's possible the problem could be caused by a faulty CDR?

Don't remember much about the install process, but does the installer give you the option to look for other operating systems and add them to the Yaboot menu? If so, try answering NO to that step and seeing if it installs.

---

### Post by jdp on 2006-03-26
Are you installing to the internal main HDD, or an external FW drive?

---

### Post by grazie on 2006-03-26
I have a B&W G3 (it's NewWorld) with Ubuntu successfully installed. With a none standard IDE config it can be an awkard beast to install many Linux distros on, but the Ubuntu installer copes well.

I too would suspect a duff InstallCD.  Incidently, this machine cannot boot from a FW drive.

---

### Post by Jawbreaker4Fs on 2006-03-26
I'm installing onto an internal hdd, and the problem is not related to the media... I've downloaded the CD 3 separate times from different mirrors and burned each twice. All times I've tried to install have had the same result.

---

### Post by jdp on 2006-03-26
Are you trying to setup a dual boot on that internal drive, or do a Ubuntu-only install?  I'm guessing dual boot.  Did you setup the partitions by hand, or did you let  installer take care of it?  If you forgot to setup a /boot partition, or forgot the HFS YaBoot partition if you did it manually, then it might cause YaBoot trouble.

---

### Post by Jawbreaker4Fs on 2006-03-27
nope.. I'm trying to do a single boot for just Ubuntu (why would you need another OS? :mrgreen:) I've just been using the partitioner that comes with the installer. Anyone have any other ideas?

---

### Post by grazie on 2006-03-27
You haven't stated whether you're manually setting up the partitions or allowing Ubuntu to do it automatically - it's important.

Also, is installing yaboot the last step in the whole installation process ? If it is, yaboot could be set up outside the installation. Look at my instructions in [http://ubuntuforums.org/showthread.php?t=150425]("http://ubuntuforums.org/showthread.php?t=150425"). Post the details here. You can gain access to the installation environment by opening a shell. Alternatively, reboot using a LiveCD or with an InstallCD in rescue mode, but the LiveCD is the better option.

---

### Post by Jawbreaker4Fs on 2006-03-27
Uhh... so I just tried doing a reinstall over the old one and for some reason everything went smoothly with yaboot this time. I'm not really sure what the problem was, but it seems to have resolved itself. Strange...

Anyway... now the new problem I'm running into is that I get stuck with installing packages. When I reboot after the initial install sequence I seem to get stuck on the gstreamer0.8-tools package (44%). I did a check to make sure I had enough hdd space to install (it's 6gb, that should be enough right?)... not really sure if this is the right command to check that...

sudo more /proc/ide/hdc/capacity

I figure that's only checking the disk capacity and not the remaining space on the volume though. It's just plain stopped at this exact point in the installation process 3 times now, so I'm not really sure exactly what the culprit could be (again, I've redownloaded and reburned from several different mirrors... so the media is not to blame). Anyone have any ideas?

---

### Post by jdp on 2006-03-27
To check the space on mounted volumes, try **df -h** which will print out a list of mount points with capacities and amounts filled, in human understandable numbers.  If you just use **df** or **df -k** you'll get listings in blocks or kilobits.

---

### Post by Jawbreaker4Fs on 2006-03-27
ok.. so it's telling me I have 4gb left on the drive. Any ideas what could be causing this?

---

### Post by grazie on 2006-03-27
From your description of faults it still seems most likely that you've got media reading problems. It could be the InstallCD or it could be the CD-ROM, which is known to be temperamental. You seem certain that your InstallCD is good, but you haven't said why? Does the MD5 hash verify? Does the burn application you're using to create the InstallCD verify the burnt image? Have you tried the InstallCD on another machine? Can you boot with an OSX CD and install the OS? Have you tried any other bootable CDs?

---

### Post by Jawbreaker4Fs on 2006-03-27
Sorry that I didn't clarify...

I know that the install CD is working ok, because I've got a pile of them sitting here (all of which are from different mirrors and have had md5sum checked) and they all have the same problem. Additionally, I've used the drive to install OS X beforehand, so I'm relatively certain that isn't the problem. I also worked briefly at the plant where the CD drive was manufactured, and they had few problems with the particular model... all of these are reasons that I'm fairly certain the fault lies not with the drive or the media.

---

### Post by grazie on 2006-03-28
I'd try doing a server install (enter **server** at the **boot:** prompt) and then complete the desktop install over the net. Don't know how much RAM your machine has, but installing XFCE, Fluxbox or a similar window manager is probably a better option for speed than Gnome anyway.

---

### Post by Jawbreaker4Fs on 2006-03-28
Finally got it up! Seems the problem WAS the install media. I reburned as slow as possible and it went through.. thanks for all the help guys! Now I can run Ubuntu on all my computers :-D

---

