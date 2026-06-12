---
title: "iMac G3 can't find hard-drive to boot from after full installation"
date: 2006-05-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Theo-Ubu on 2006-05-18
So I've been battling this problem for more than a week now.  I added more memory and a 10Gig hard-drive and the installation of 5.10 runs through with flying colors.  Then when the machine reboots, it never finds the hard-drive or whatever it's looking for in order to boot.

I have tried holding down the proper keys to go to the "open firmware" command line.  Then I try:

> boot hd:#,yaboot

with any of the numbers one through 10 as the partition number to replace the "#" in that line, but I always get:

cant OPEN: hd:#,yaboot

The first time I type the boot line mentioned above, it takes a while for the error message to appear, then after that, while trying different numbers the error message comes back very quickly.

I'm at my wits end and very frustrated.   Are there any open-firmware commands I can try to check if the hard-drive is even being found by the hardware system?  It seems like I can't even hear the HD spin up at boot.  The HD was definately making noise when it went through the install process and was writing from CD to HD.  Is there something funky about setting the jumpers on the HD when putting it in.  I thought "MA" (master) would be pretty standard and fine.

PLEASE HELP, HELP, HELP!!!!!

---

### Post by Das Hammer on 2006-05-19
I am an expert by no means, but I thought the hard drives in those were usually set to "Cable Select".  I've got a G3/400 DV SE, but I've never opened it up far enough to see what the drive is set at.

Also, did you try 0 (Zero) for a number?

---

### Post by ssam on 2006-05-19
could try zapping the PRAM, or holding alt (option) during boot.

---

### Post by Peter76 on 2006-05-19
Had the same problem, turned out that the bootable flag was not set on the yaboot partition when partitioning and formatting the drive in the installer. Run the installer again till you get to the partitioning part and see if the bootable flag is set. Can't remember if I had to reinstall or if you could reset it. Post back please if it was unset, then there should be a bug filed about this. Good luck

---

### Post by Theo-Ubu on 2006-05-19
In regards to the jumper settings comment above about cable-select.... :

What is odd to me is that the install CD goes all the way through the whole process, acting totally as if it is writing all the required files to the hard drive, so it would seem that the hardware is indeed finding the hard-drive.  Then, when it reboots for the last step, I don't seem to HEAR the HD spin up at all, and open-firmware doesn't seem to see the HD, nor the boot system PROM when it powers up in the normal sequence.

I'll run through the install process again and get to the partitioning pages.  How will I recognize which one is supposed to be the yaboot directory?

Thanks!

---

### Post by Peter76 on 2006-05-20
Select the partition manually option. Then you can see all the partitions and the yaboot one as well, select it and check if the bootable flag is set

---

### Post by Theo-Ubu on 2006-05-20
I went through the install CD progression once again until I got the the manual partitioning window.    As with the ten other times and configurations I've tried installing it in, I see the same partition layout.   Partition #1 says it is 32.1Kb and is APPLE formatted.  Partition #2 is set to 1.0Mb, and says it is the boot partition and does have the boot flag with the little lightening bolt arrow symbol next to it.

I also tried taking out the hard-drive once again and setting the jumper on it to "CS".  I looked at the original hard-drive that was in there with the original System 8.1 on it, and it is a Quantum fireball 4.0Gig drive.  What's weird about it is that it has "PK", "CS", and "DS" in that order up above the jumpers in the usual spot.  I don't recognize "PK" or "DS".  Also the jumper is in it's stock place and it does not seem to correspond to any of those letter designations.  There are four jumper sets (above/below pins), and the letters don't seem to lign up directly with the jumpers below.  This is the best I can describe it all.

So... nobody seems to be able to answer why I don't hear the HD spin up on boot at all.  It seems like I did hear it when the CD contents was being copied to the HD during install.

This is so dissapointing.  So close, yet NADA.

---

### Post by EuroCity on 2006-05-21
If I'm not mistaken, the original Bondi, tray-loading iMac (G3) must have the system (OS X or Linux) installed within the first 8 GB of the hard drive: so, if your hard disk is larger (you said 10 GB), that could explain the failure to boot. And the HD must be set as master, probably.

If it is that model of iMac, you should manually partition the HD, in this way (after the Apple Partition Map, the first one, which shouldn't be touched):

- a 1 MB Apple Bootstrap partition (or "New World" boot partition, for the yaboot bootloader);

- an approximately 100 MB /boot partition (which is required, due to the above firmware limitation, to hold the kernels; if you format the drive before with Apple's OS X Disk Utility (as HFS+ Journaled), you could make the /boot partition 127 MB, thus completely using up the 128 MB free space which is put at the beginning of the drive);

- a /, swap and optionally /home partition in the remaining space.

The separate /boot partition ensures that the iMac will always be able to boot, being safely within the 8 GB open firmware limit.

Maybe the problem isn't that one, but it might be good to repeat this fact, which is often overlooked: which is also understandable, as the original iMac is getting rather old as a model, so it's easy to forget such things.

See also this link:

[http://www.terrasoftsolutions.com/support/hardware/breakdown/index.php?hw_cat_id=5](http://www.terrasoftsolutions.com/support/hardware/breakdown/index.php?hw_cat_id=5)

---

### Post by Theo-Ubu on 2006-05-21
Those are some interested ideas, however I used a completely different 10Gb hard-drive for the installation.  I did not use the original HD of 4Gig which had the OS 8.1 installed on it.   I wanted to be able to go back to the original iMac if I couldn't get Ubu to work.

So... I don't quite understand all the stuff you said about the partitions, or why there is even an "APPLE" 32Kb partition created on the disk when all that I am doing is a Ubuntu install straight from CD.

Sigh....

---

### Post by EuroCity on 2006-05-21
The very first partition is the Apple Partition Map, which is needed also for Ubuntu (or any other PPC Linux): so this isn't a problem at all. For example, with automatic partitioning from the Ubuntu installer, it is normal that this small partition gets created (hda1). So, if you start over, you should then additionally create a 1 MB Apple Bootstrap partition (hda2), an approximately 100 MB /boot partition (hda3) needed for the first generation iMacs, and then the root and swap partitions (hda4 and hda5), optionally with a separate /home partition (hda6); of course, the root partition (/) should be big enough to hold the system and the software you plan to install (several gigabytes); and /boot, / and /home should all be formatted with ext3. 

Sadly, I think you need to do this manually from the Ubuntu CD installer, as it doesn't seem to recognise the need for a separate /boot partition on these old iMacs.

You could try and see if this solves the booting problem...

---

### Post by EuroCity on 2006-05-22
... And, if I'm not mistaken, the internal hard drive must be set as "master" on these old iMacs.

An alternative partition strategy could also be to not necessarily make a separate /boot partition, provided that the root (/) partition is entirely contained within the first 8 GB of the hard drive: for example, if you decide to include a separate /home partition, thus limiting root to less than 8 GB. This could be, just as an example:

- hda1: the small Apple partition map, to leave untouched;

- hda2: a 1 MB new world Apple_Bootstrap partition (which has nothing to do with /boot, BTW);

- hda3: a 6 GB root partition (or even less: depends on how much software you plan to install);

- hda4: a swap partition which is approximately 1.5x your RAM in MB;

- hda5: and the remaining space for /home.

---

### Post by Theo-Ubu on 2006-05-22
Thanks for your interestd EuroCity,

I'm confused about the hda2 partition.  What should it be named, what should it's formatting be, and should it be set to bootable?

You refer to such things as the "root (/)" martition and the "home (/home)" partions, but the installer does not creat these kinds of directories when left to do its thing.

During the manual partitioning step as well, I noticed that the system did not let me change the swap partion size at all.  Kind of strange.

Again, thanks for the continued interest.  I will try bringing the root partion down to less than 6Gig and let you know what happens.  I'll also try to write down and then reproduce here exactly what my partions are looking like through the interface.

---

### Post by nyranger66 on 2006-05-23
Funny, on a whim I decided to install Ubuntu on a Rev. A iMac I had laying around, and am having similar problems to the original poster. Has this been at least confirmed to work? 

When I wake up tommorow, I'll try the partitioning idea, and changing the HD from Cable Select to Master.

I'll keep everyone posted.

---

### Post by ceenvee703 on 2006-05-24
Add me to the list. I attempted to install Dapper Drake onto my iBook G3 500 MHz from a DVD ISO. Install appeared to go fine but at restart, yaboot gave a long error that I can copy down if necessary.

Searching the forum turned up this thread. I'm trying to do the manual formatting now but (at least) using the graphical formatter that is part of the install process, I don't see any way of either resizing the HFS /boot partition that was created the first time through the install, or of specifying that a newly-created HFS partition should be /boot (maybe that comes later in the partitioning process?).

I'll play with this some more. Thanks for the ideas.

EDIT: played with it some more. I could not get the Live DVD's partition program to make an "apple-bootstrap" partition when run in manual mode. I read in a different thread that the Live disc's installer was messed up. Unfortunately, when I try an install CD ISO, it either results in a screwed-up screen, or X server errors if I use the "live video=ofonly" yaboot option.

---

### Post by EuroCity on 2006-05-26
[QUOTE=Theo-Ubu]I'm confused about the hda2 partition.  What should it be named, what should it's formatting be, and should it be set to bootable?

You refer to such things as the "root (/)" martition and the "home (/home)" partions, but the installer does not creat these kinds of directories when left to do its thing.[/QUOTE]

The hda2 partition is the so-called bootstrap partition: AFAIK, sofar, you can only create it with the traditional text-based Ubuntu installer (but still not manually from the Dapper Live/Desktop CD, which is based on GParted for partitioning); this bootstrap partition is also called of type Apple_Bootstrap or a New World boot partition (I think the latter is Ubuntu's naming). So, it should be 1 MB in size, have the bootable flag set and no mount point (the file system will then eventually be HFS, if I'm not mistaken, but this partition will be invisible to OS X). It is also automatically created if you select to automatically partition your hard drive: so if you have problems, maybe you could just try the automatic partitioning option and then resize the root (/) partition (immediately after the bootstrap one) to something under 8 GB after having finished the install.

A separate /home partition is an optional feature, useful for example if you have to reinstall the system (i.e., erase the root partition), thus leaving your data intact on /home, where your user folders are stored.

It's rather difficult, anyway, to explain all this only theoretically: the best thing one can do is probably an experimental, "trial-and-error" approach, which also learns you a lot of things, besides... :) :cool:

---

### Post by EuroCity on 2006-05-26
[QUOTE=ceenvee703]EDIT: played with it some more. I could not get the Live DVD's partition program to make an "apple-bootstrap" partition when run in manual mode. I read in a different thread that the Live disc's installer was messed up. Unfortunately, when I try an install CD ISO, it either results in a screwed-up screen, or X server errors if I use the "live video=ofonly" yaboot option.[/QUOTE]

Yes, as I said previously, currently it doesn't seem to be possible to manually create the bootstrap partition from the GParted-based Live CD installer.

You could, anyway, try the automatic partitioning (which always creates the bootstrap partition) and then resize (always from GParted on the CD) the installed root partition to a value under 8 GB; the remaining space could be used in various ways, for example for a /home partition.

In this way, you wouldn't need a separate /boot partition immediately after the bootstrap partition: anyway, if you would rather go for this approach (if you want a root partition larger than 8 GB, for example), /boot should be formatted as ext3 and have the mount point at /boot, and be about 100 MB in size (it will hold the kernels).

At least, currently there don't seem to be other viable options, if the text-based install CD doesn't work...

---

### Post by kellogs on 2006-05-26
Just installed ubuntu yesterday. After a long time messing with the partitioner ubuntu has, I noted that I needed an HFS partition, so I put the tiger cd(macosx) and booted from it, created a HFS+ partition of about 4mb(this is the minimum that it allowed me) and another with all the space left. then I booted from the install ubuntu cd and made 2 more partitions, one ext3 of more than 200 gb, and one of about 512mb( I've got 2,5 gb ram).so i deleted the big hfs partition left, and made those two on this space. 
So in my system it is organized like this:

-first 32k, that little apple partition that you dont touch and its always there.

-a little 4 mb HFS+ partition marked as bootable and Newworldmac(in my case i did the marks with the ubuntu installer, the hfs with tiger install cd or macosx).

-swap partition of 512 mb(im not sure about this but ive got lots of ram , in linux long time ago 128 mb was ok but now Ive got plenty of ram and it seems to work ok).

-a root (/) ext3 partition of almost all the space in the disc.

After this, I booted my powermac and the install went very good, booted again and the system was fully working.

Hope you find it useful. For info: ive got a Dual powermac G5 2.3 ghz, 2.5gb ram. 20inch apple display, and two discs of 200gb. one of them still unrecognized thought cos ive got it yet hfs. lol. but everything else is working fine.

ok, I discovered that right-click is simulated with shift+F10 by default in my G5, not as ctrl+f12 as other macs. 

will post any advance... cheers.

Edit: edited for fixes.

Edit: the fans work WAY better here than in macosx tiger, now they go silent until you put a lot of work on your mac , lol.

---

### Post by EuroCity on 2006-05-26
Interesting: but the Power Macs (G4 and G5) don't have the original G3 iMac's 8 GB open firmware limitation, so you could as well have made an automatical partitioning of the free space (the whole disk or the part not used by OS X) directly from the Ubuntu installer. If you begin from the free space, it's easy also to manually create the partitions form the Ubuntu installer, anyway. If I'm not mistaken, also, the bootstrap partition will subsequently be formatted as HFS (not HFS+) by the installer and will remain "invisible" as a disk from OS X: the only time this small partition will be modified is when yaboot.conf is updated (for example, automatically after a kernel upgrade) with the command sudo ybin -v (ybin is the "yaboot installer", which is probably run in the background when the kernel is updated through apt-get).

---

### Post by ceenvee703 on 2006-05-26
EuroCity: thanks for the reply. I have fallen back to installing Breezy Badger as that goes just fine from the install CD.

Is there any way to start up from my Breezy Badger hard drive in my iBook, then insert the Dapper Drake CD (or DVD) and do the install that way? If there's a thread or FAQ you can point me to, I can take it from there. Otherwise I'll probably just wait for the official Dapper Drake release. Thanks again.

---

### Post by EuroCity on 2006-05-27
Here is an interesting link:

[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

Of course, if possible, it would probably be better to eventually make a clean, official Dapper install; but in the meantime, you could always try the upgrade and see how well it works...

---

### Post by Celeritas on 2006-06-03
Hi guys, i joined this forum because i have a similar problem. I tried following your advise and i came to the following problem during the boot.

I have installed a new 40 gig hd on my recently aquired Imac G3. Installation was succesfull each and every time but every time when i boot after installation i come to a blank screen with in the middle a small icon of a folder with a question mark. It changes every second to a face inside that icon.

I have:

32k apple partition
100 mb boot partition
1mb boot partition (set for install for Yaboot)
6gig swap (mistyped should have been smaller ;))
7gig / partition
and the rest is for /home.

Does the order of these partitions have any effect?

---

### Post by Celeritas on 2006-06-07
Nobody can answer my question?

---

