---
title: "Loading second stage bootstrap..."
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by gconn77 on 2005-12-12
First Stage GNU/Linux Bootstrap

Press l for GNU/Linux,
       c for CDROM.

Stage 1 Boot:
Loading second stage bootstrap..._

[B]I press l and it just loops back to the begining.... I can press l again... and same thing... also I can just leave the computer running.... it will attempt to load GNU/Linux automatically..... then 40 seconds or so... it loops back to the begining again. Any tips on completing the install? G3 Applle B&W. Being working on this non stop for about 16 hours. If someone could help... I would so much appreciate it!

Thanks in advanced![/B]

[View This Thread]("http://www.ubuntuforums.org/showthread.php?t=102228") for a complete walk thru on my problem installing Ubuntu on my apple G3 B&W.




```

First Stage GNU/Linux Bootstrap

Press l for GNU/Linux,
       c for CDROM.

Stage 1 Boot:
Loading second stage bootstrap..._

```

---

### Post by ssam on 2005-12-12
it looks to me like the install did not complete. there is not enough there to boot past that part.

did you try checking the disk was good?

to check /target/var/log/bootstrap.log

press crt+alt+f2 to get a terminal (if this doesn't work try it with f3, f4 etc).

type
```
less /target/var/log/bootstrap.log
```
(up and down to navigate, 'q' to exit)

press crtl+alt+f1 to get back to the installer.

---

### Post by deathshadow on 2005-12-12
I recognize the behavior - it's what yaboot does when it cannot actually find a linux partition on the disk. I've seen similar issues on some G4's in regards to booting from the CD.

I'd suggest resetting the PRAM (command-option-p-r during boot) and reinstalling linux again after that. If that doesn't work, try seeing if the Live CD works. If it won't boot either in the same way, it's likely some form of hardware conflict. If the Live CD does boot, it's probably the drive.

---

### Post by gconn77 on 2005-12-18
[QUOTE=ssam]it looks to me like the install did not complete. there is not enough there to boot past that part.

did you try checking the disk was good?

to check /target/var/log/bootstrap.log

press crt+alt+f2 to get a terminal (if this doesn't work try it with f3, f4 etc).

type
```
less /target/var/log/bootstrap.log
```
(up and down to navigate, 'q' to exit)

press crtl+alt+f1 to get back to the installer.[/QUOTE]

[COLOR="DarkGreen"]ssam, thank you for the response back. The disk is from what I believe is good. The first copy I downloaded from the website. That one was definately bad...  the second disk was bit torrent copy and I believe it is good because the install made it past the first stage. The second stage is where it haults. But a few others have made some comments about this situation... and they are telling me that I did not partition the drive correctly. It is suggested that when I partition I erase the entire disk. I never did that before, and I am actually attempting a reinstall right now... I will post a message with the results. Thank you very much for your help.[/COLOR]

[QUOTE=deathshadow]I recognize the behavior - it's what yaboot does when it cannot actually find a linux partition on the disk. I've seen similar issues on some G4's in regards to booting from the CD.

I'd suggest resetting the PRAM (command-option-p-r during boot) and reinstalling linux again after that. If that doesn't work, try seeing if the Live CD works. If it won't boot either in the same way, it's likely some form of hardware conflict. If the Live CD does boot, it's probably the drive.[/QUOTE]

[COLOR="DarkGreen"]Deathshadow, please keep in mind that I am very new to the world of Linux... let alone attempting to install it on an Apple computer. Can you please explain what the PRAM is and what I need to reset it to? As mentioned above... I belive that I failed at not erasing the entire drive in the partition stage of the installation. I am trying this now and will post a reply with the results. Thank you very much for your response.[/COLOR]

---

### Post by pablogott on 2007-02-20
I am having the same problem. I let the installer automatically partition and erase the hard drive, but no luck. I have verified the drive is good by zeroing out all the data/repairing/and formatting from OSX disk utility. Although I don't remember for sure if I made the drive journaled or not, I strongly believe I didn't. 

I've installed 3 times on 2 verified drives and get the same result. Also, whenever I shut down after booting from the CD it tells me to eject the CD and press enter to continue. However, enter, return, and pounding on the keyboard won't let it finish the shutting down.

I tried manually partitioning the drive but could not get past the step of not having a New World boot strap or something like that, which I take to mean needing a HFS partition. However, creating one does nothing. It won't let me select HFS+.

Otherwise, everything seems to work as expected. I am online now after hard restarting and rebooting from the live CD. If anyone has any ideas, I'd greatly appreciate it.

I am running a G5 powermac (the single 1.6).

---

### Post by pablogott on 2007-02-20
The problem I am having while manually partitioning during the installation appears to be a separate issue, and I found a work around here:

[http://www.ubuntu.com/download/releasenotes/606](http://www.ubuntu.com/download/releasenotes/606)

*When installing from the Desktop CD on powerpc and using manual partitioning, you may experience problems setting up the HFS bootstrap partition required for the yaboot boot loader. You will need to deselect the bootstrap partition on the mount points page, and an error message beginning with "No NewWorld boot partition was found" will appear, at which you should select "Continue". If the bootstrap partition did not exist prior to starting installation, then you may need to create it using parted outside the installer: make sure the partition is of type hfs, at least 820kB in size, and has the boot flag set. Installations from the Desktop CD with automatic partitioning, or from the alternate install CD, do not have this problem.*

Since my install was with automatic partitioning, it would seem that that isn't an issue. I have been trying to install Edgy Eft, I am downloading Dapper right now and will try again tonight. I'll post the results here. 

If anyone has successfully installed on a G5, I am very curious to hear the details of your install process. I'm probably just missing a step.

---

### Post by pablogott on 2007-02-20
After a fine install, Dapper came up with the exact same problem. Here, at [http://ubuntuforums.org/archive/index.php/t-294293.html](http://ubuntuforums.org/archive/index.php/t-294293.html), a user writes:
[B]
Basically, yaboot on ubuntu didn't work.

Here's what I did.

I started it up with the gentoo ppc64 livecd.
Then I mounted the root on /mnt/gentoo.
I edited the ubuntu fstab to change the UID=### to /dev/sda ect...
Yaboot uses information in fstab to set up the bootloader.
I also edited the /etc/yaboot.conf file and included root=/dev/sda3, it didn't seem to be there in the ubuntu yaboot.conf but was on the gentoo ppc64 install page.
Then I used the gentoo yabootconfig and...
#yabootconfig -r /dev/sda3 (for example) -b /dev/sda2 -t /mnt/gentoo
Then yabootconfig does it's thing, you confirm that /dev/sda2 would be your boot... and then the computer restarts and ubuntu will load!

Fun experiment, but I'm probably gonna setup gentoo, the screen won't go larger then 1024x768, I'd like to use dm_crypted partitions, and since I'll be ploping this on the public internet... I'd like it to have some of the hardened gentoo aspects... and I think I can get dri, aiglx, and beryl running too.
[/B]

If that's the solution, it's a little over my head, as well as not very convenient as I don't have a gentoo disk. If anyone has some advice on completing this, please let us know.

---

