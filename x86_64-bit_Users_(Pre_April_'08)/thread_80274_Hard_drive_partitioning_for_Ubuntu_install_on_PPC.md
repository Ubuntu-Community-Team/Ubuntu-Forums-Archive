---
title: "Hard drive partitioning for Ubuntu install on PPC"
date: 2005-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by jproenca on 2005-10-21
Hey. I'm running OS X on a G5 iMac, and need to partition my hard drive in order to install Ubuntu if I'm correct. Now, how can I create a separate partition since, as I am led to believe, one cannot work the boot partition, which is all I've got. Any help would be great, as well as any tips. I am about 1 year into my first experience with Macs, coming from Windows, and have no experience whatsoever with Linux, but curious and determined. Cheers!

---

### Post by pauljwells on 2005-10-21
The easiest way is to get an external firewire drive (I have a LaCie) and a copy of CarbonCopyCloner for mac. Run CCC to make a bootable copy of your hard disk on the external. Then reboot, holding the option key, and select the external drive copy of OSX. Then you can run disk utility to repartion the internal hard drive (say two equal size partitions for starters). Make one of them HFS and leave the other as 'free space'. Use CCC to copy the OSX from the external drive to your HFS partition. Reboot and check that everything works okay. (It's a good idea to use CCC to make a backup of your OS regardless of using linux)

Now you can insert your install cd, reboot holding the 'c' key and it will find the free space onto which to install itself. Once you've got through the install (quite a while) you  will end up with a simple 'grub' menu of options at bootup for osx linux or cd. Remember never to use the system preferences startup disk setting from now on as this overwrites the grub menu.

As a final tip, keep your mac plugged into an ethernet cable during install.

hope all this helps.

If you don't have/want an external drive, then you need to backup your data, and reinstall osx from the cd, but first selecting disk utility from the top menu before the install starts in order to create the partitions.

Good Luck.

---

### Post by jproenca on 2005-10-21
That was a lot of help. Do I have to copy all of my system? I ask because I have about 30 Gb on my iPod I could use for something, if this was at all possible... as external devices go, I have that and a win laptop, which I doubt I could use, or could I? thanks.

---

### Post by pauljwells on 2005-10-22
If you want to keep your existing system setup then I don't know another way. There isn't a 'fdisk' or 'parted' type command that will let you resize an hfs partition :( Also, the iPod _can_ be used as a firewire drive, but to use it to make a bootable system copy, which is what you need, you have to erase it completely first. The iPod has several hidden partitions, which it needs to be able to work as a player rather than just a drive. This is not so drastic as it sounds because you can always reset the iPod afterwards and all these partitions will be restored. I've never done it myself though and, frankly, I'd be a bit worried about bricking it. You lose all your music too, so you need to make sure you have all that saved somewhere else too!

I think in your position I'd copy all my data (I mean everything you have in your home directory) to iPod/PC/CD. I'd use BackUp and the .Mac syncing to save all my preferences and bookmarks, then I'd bite the bullet, pop the install CD in and set up the partitions like I described before, then reinstall OSX and all your apps and then ubuntu. Have you ever fixed permissions on your system? If not then you probably don't have your system set as well as it could be. Google up on this, it's important for OSX

Do a search on these forums to read about exactly how to partition, I think you need to leave the first partition as free space for ubuntu and install osx on the second. I actually always set a third partition as small as possible for the 'classic' system folders too, if you use any OS9 stuff, otherwise don't worry about this.

I really would recommend a backup firewire drive though, once you've done a few copies of your system you get much less worried about hosing it! I think I reinstalled three times before I ended up with my current setup.

---

### Post by nicholaspaul on 2005-10-22
Having just gone through a hard drive crash, I would highly recommend buy/borrowing an external firewire drive and making an image of your entire drive. Disk Utility will do this, as will SuperDuper! 
(actually I would recommend buying a firewire drive anyhow: some people say 'if it isn't backed up twice, it doesn't exist'. )
When you've repartitioned, restore the image and then install ubuntu on the second partition. Easy as pie. Honest!

---

### Post by Joe_lurker on 2005-10-22
I used gnu-parted on my Mac to resize the main partition.  It worked just fine.  You can resize hfs partitions but you cannot move them.  Of course make sure to back up any important data and programs before trying to repartition a drive.

Joe

---

### Post by kioshi on 2005-10-23
Can anyone show me the partition map? Does the bootstrap really have to be number 2 after Apple partiotion map?

And how do I install yaboot manually in the bootstrap? The ubuntu installer never installs it for me, it always fails.

---

