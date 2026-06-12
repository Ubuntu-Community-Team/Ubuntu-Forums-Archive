---
title: "Beige G3 All-in-one"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Wyvernspirit on 2006-05-07
I am trying to install ubuntu 5.10 breezy on a g3 AIO w/ 160 MB or RAM and a 6.5 GB hard drive.  750 MB are used for the OS 9.2.2 installation, the remainder used for the ubuntu install.  I have boot X installed, and easily get through the installation process, until it gets to the boot loader issue.  I follow the instructions on the wiki:

[B]cd /target
mkdir hfs
mount /dev/sda5 hfs -t hfsplus
[/B]
but I get an error message with that last line and can't continue, and can't seem to find any answers.  The error message is:

**mount: Mounting /dev/sda6 on /target/hfs failed: No such file or directory**

My ubuntu installation is on 7 so 6 should be the Mac OS.  I am not sure how to continue and am hoping someone out there knows what can be done next.  This is the third time I have tried to install this, following different "installation guides" in regards to this issue.  That doesn't include a failed attempt at installing Gentoo Linux on this machine.  Gentoo said it supported this comp, and an older one I was using, and Ubuntu didn't give me a good idea as to wether or not it supported them or not.  After some investigation found the guides, but am stuck at this point.  It is as far as I have gotten this round of testing.

I appreciate any help anyone can give me.

Thanks,
w

---

### Post by nkbj on 2006-05-08
> 

**mount: Mounting /dev/sda6 on /target/hfs failed: No such file or directory**



Are you sure it is a SCSI disk? The beige G3 often came with an IDE disk which would be named /dev/hda, so I would try /dev/hda6.

Regards,
Niels Kristian

---

### Post by Wyvernspirit on 2006-05-08
[QUOTE=nkbj]Are you sure it is a SCSI disk? The beige G3 often came with an IDE disk which would be named /dev/hda, so I would try /dev/hda6.

Regards,
Niels Kristian[/QUOTE]

Thanks for the reply, but I have tried that as well.  It was part of my first attept, the sda was part of the wiki, should have mentioned trying hda as well.

Any other clues?

---

### Post by davygravy on 2006-05-08
w,

When you install, you will see a section that shows the partitions.  Make a note of them all {*_write them down on paper, double check them_*}(some should be specified as Apple partitions or HFS partitions).  nkbj is right, it must be hda or hdb (which is ide/ata), etc., instead of sda (scsci). 

If you know the possible partitions, then you can just try them all.  Depending on how your partitions/slave/master/bus are all set up, it could be hda, hdb, hdc, etc.  Also, it might not be partition #6, like you mentioned.  I usually could spot the right partition by looking at the size of it (when I used the Drive Setup Utility in OS 9, I always wrote down the size of it).

hth,

davygravy

---

### Post by Wyvernspirit on 2006-05-08
[QUOTE=davygravy]w,

When you install, you will see a section that shows the partitions.  Make a note of them all {*_write them down on paper, double check them_*}(some should be specified as Apple partitions or HFS partitions).  nkbj is right, it must be hda or hdb (which is ide/ata), etc., instead of sda (scsci). 

If you know the possible partitions, then you can just try them all.  Depending on how your partitions/slave/master/bus are all set up, it could be hda, hdb, hdc, etc.  Also, it might not be partition #6, like you mentioned.  I usually could spot the right partition by looking at the size of it (when I used the Drive Setup Utility in OS 9, I always wrote down the size of it).

hth,

davygravy[/QUOTE]

Thanks for the reply, I know the mac partition is on 6 and the Ubuntu is o n 7 with a swap on 8.  I took note of this, plus I set the ubuntu to partition the unallocated space, so it was easy to spot the mac partition (the largest space used, and the last on the list).  it is the only HD on the system and it is set to master (its ata/ide). the machine does have a CD and a Zip as well.  I believe the show up as hda, and I tried that one out, instead of sda, but also tried sda, just in case.  I don't have andy sczi drives to try this out with, so that is not an option.

Any other possibilities?  I am at a lost, and I thought I was following the directions as indicated.  Like I said, the whole process is easy till that boot loader problem.

Again thanks,

W

Let me know if there is any additional info you might need to diagnose this problem.

---

### Post by davygravy on 2006-05-08
did you try hdb?

other than running the installer again and double-checking the location, that's really my only suggestion.

anychance the partition is hfsplus instead of hfs?  do they both mount w/ the same command?

You could theoreticcally  boot off teh live cd, copy the insstalled kernel onto a floppy (or to some network location - on another computer), then boot into OS 9 and copy it into the BootX folder on the Mac partition...?

???

davygravy

---

### Post by Wyvernspirit on 2006-05-08
[QUOTE=davygravy]did you try hdb?

other than running the installer again and double-checking the location, that's really my only suggestion.

anychance the partition is hfsplus instead of hfs?  do they both mount w/ the same command?

You could theoreticcally  boot off teh live cd, copy the insstalled kernel onto a floppy (or to some network location - on another computer), then boot into OS 9 and copy it into the BootX folder on the Mac partition...?

???

davygravy[/QUOTE]

I can't recall if I used hsb, will try.  The partition is hfs+ and I used hfsplus as part of the command, the one listed in the post is copied from the wiki.  I suppose I could try partitioning it hfs and see if that helps, but that means installing os 9 for the 5th time this weekend.

Maybe I can try the other solution, not sure if I am tech savvy enough to do so, but willing to try.

This seems very weird and I wish the solution was something stupid that I just overlooked.

Thank you for your post.  If any one else has any ideas, please let me know.  I will post with my results when I get the chance, good or bad.

---

### Post by Theo-Ubu on 2006-05-08
I'm trying a 5.10 install on a beige tray-loader G3 also.  I've made it all the way through the whole install process, had the install program eject the CD for me, but then when it comes back for a boot of the HD, I get the blinking folder/? symbol.

It seems like the iMac is probably looking for the wrong directory to boot from, doesn't find it, so just gives up.  Is there some settings in PRAM or something that I could knock out with a PRAM-zap?

Also... is there some way to boot into a command prompt and do a very low-level hard-drive blow-out or erasure like you can through DOS (format /mbr)?  It seems like I can't be dead sure the 5.10 CD is writing up the partitions in the proper way to be bootable?

---

### Post by Wyvernspirit on 2006-05-08
[QUOTE=Theo-Ubu]I'm trying a 5.10 install on a beige tray-loader G3 also.  I've made it all the way through the whole install process, had the install program eject the CD for me, but then when it comes back for a boot of the HD, I get the blinking folder/? symbol.

It seems like the iMac is probably looking for the wrong directory to boot from, doesn't find it, so just gives up.  Is there some settings in PRAM or something that I could knock out with a PRAM-zap?

Also... is there some way to boot into a command prompt and do a very low-level hard-drive blow-out or erasure like you can through DOS (format /mbr)?  It seems like I can't be dead sure the 5.10 CD is writing up the partitions in the proper way to be bootable?[/QUOTE]

Unfortunately this is not an iMac.  An iMac would be a new World computer, you need to follow those install directions, while this computer is an old world computer.  It is an ugly, ungainly system, not like the pretty imacs.  I wish it was an imac, would be smaller, and mostly newer tech.

Wish could help you myself, sure someone here can, I only have experience installing Ubuntu on this machine, and am failing so far.

---

### Post by nkbj on 2006-05-09
[QUOTE=Wyvernspirit]Thanks for the reply, I know the mac partition is on 6 and the Ubuntu is o n 7 with a swap on 8.  I took note of this, plus I set the ubuntu to partition the unallocated space, so it was easy to spot the mac partition (the largest space used, and the last on the list).  it is the only HD on the system and it is set to master (its ata/ide). the machine does have a CD and a Zip as well.  I believe the show up as hda, and I tried that one out, instead of sda, but also tried sda, just in case.  I don't have andy sczi drives to try this out with, so that is not an option.[/QUOTE]

When I got my second hand beige G3 (300MHz MT rev. 1) the cables on the two IDE controller channels were switched so the cdrom drive was hda and hard drive was hdc. The zip drive in these computers are SCSI i.e. sda.

Have you tried /dev/hdc?

Another thing to try:
When you execute the shell to mount you hfs+ partition try to run df. If your /target partition shows something like this **/dev/ide/host0/bus0/target0/lun0/part7** you should try using the same string with part6 as the last part. It has worked for me once when /dev/hda6 didn't.

Regards,
Niels Kristian

---

### Post by Wyvernspirit on 2006-05-09
[QUOTE=nkbj]**/dev/ide/host0/bus0/target0/lun0/part7** [/QUOTE]

I believe this is exactly what it shows, I will try your suggestion, thank you.

---

### Post by 3rdalbum on 2006-05-09
Theo: I've never experienced a problem like yours, but here goes. When you installed Ubuntu, did you tell it NOT to install a bootloader? The bootloader Ubuntu can install on PPC is for "Newworld" Macs, and won't work on your beige Mac. This could be causing your trouble.

I don't know how many Ubuntu installs you've done in the past on x86, but there's also the possibility that you've accidentally erased your Mac drive. A surprisingly large number of people (Windows users who have recieved old Macs from friends, mostly) have done this.

---

### Post by Wyvernspirit on 2006-05-09
[QUOTE=3rdalbum]Theo: I've never experienced a problem like yours, but here goes. When you installed Ubuntu, did you tell it NOT to install a bootloader? The bootloader Ubuntu can install on PPC is for "Newworld" Macs, and won't work on your beige Mac. This could be causing your trouble.

I don't know how many Ubuntu installs you've done in the past on x86, but there's also the possibility that you've accidentally erased your Mac drive. A surprisingly large number of people (Windows users who have recieved old Macs from friends, mostly) have done this.[/QUOTE]

If its an iMac (as he said in his second paragraph) then its not a beige G3 and is a New World Mac not an Old world.  I guess Theo needs to explain exactly which model he has to see what his needs are.

---

### Post by Theo-Ubu on 2006-05-09
I'm pretty sure that it is new-world, as it has the factory USB ports on the side as on the keyboard.  I get confused with all the terminology though.   I'm not sure what "bondi-blue" means either, but I think that's what this one is (version A also, because of the tray-loader CD).  It looks greenish-blue to me though, and the front is kind of a white-ish beige.  What's the story with "bondi blue"?

Anyway, I wanted to make sure I could always go back to the original OS on this one, so I removed the old drive with 8.1 on it and set it aside and put in a used WD 10Gig to do the install.  At install I chose "erase the drive" and let it run with the guided partitioning on the first tries.   I still haven't been able to get it to boot yet from HD.  It goes through the whole install process just fine until reboot comes without the CD in the tray-loader, but always goes to the question mark folder on reboot.

I heard rumors that these can only "see" up to 8Gigs of HD, so on one of the install tries I made this morning, I brought the partition size of the main hda #3 down to 7Gig.  The boot partion it sets up on #2 only gets aloted 1mb however (where yaboot is set), and the menu system will not allow me to make it any bigger.   It gives me about 282Mb of swap space also, and will not allow me to change that size either.  Oh, and for #1, it says 32Kb, as "APPLE" formatted.

I found some instructions somewhere else on how to boot to the "open firmware" prompt (command-alt-o-f) and I tried the command:

boot hd:2,\\yaboot

but it wouldn't read or boot from that either.  I tried different numbers to replace the "2" in that string also to not avail.  I'm pretty bummed so far.  The install process is one of the smoothest and nicest I've seen yet for linux, yet I can't boot at all still from the HD.  Very frustrating to be so close, but nobody seems to have an answer.

Thanks for your interest,
Theo

---

### Post by Wyvernspirit on 2006-05-09
[QUOTE=Theo-Ubu]I'm pretty sure that it is new-world, as it has the factory USB ports on the side as on the keyboard.  I get confused with all the terminology though.   I'm not sure what "bondi-blue" means either, but I think that's what this one is (version A also, because of the tray-loader CD).  It looks greenish-blue to me though, and the front is kind of a white-ish beige.  What's the story with "bondi blue"?

Anyway, I wanted to make sure I could always go back to the original OS on this one, so I removed the old drive with 8.1 on it and set it aside and put in a used WD 10Gig to do the install.  At install I chose "erase the drive" and let it run with the guided partitioning on the first tries.   I still haven't been able to get it to boot yet from HD.  It goes through the whole install process just fine until reboot comes without the CD in the tray-loader, but always goes to the question mark folder on reboot.

I heard rumors that these can only "see" up to 8Gigs of HD, so on one of the install tries I made this morning, I brought the partition size of the main hda #3 down to 7Gig.  The boot partion it sets up on #2 only gets aloted 1mb however (where yaboot is set), and the menu system will not allow me to make it any bigger.   It gives me about 282Mb of swap space also, and will not allow me to change that size either.  Oh, and for #1, it says 32Kb, as "APPLE" formatted.

I found some instructions somewhere else on how to boot to the "open firmware" prompt (command-alt-o-f) and I tried the command:

boot hd:2,\\yaboot

but it wouldn't read or boot from that either.  I tried different numbers to replace the "2" in that string also to not avail.  I'm pretty bummed so far.  The install process is one of the smoothest and nicest I've seen yet for linux, yet I can't boot at all still from the HD.  Very frustrating to be so close, but nobody seems to have an answer.

Thanks for your interest,
Theo[/QUOTE]

I wish I could help you with your issue.  The front color should be a translucent white, and I have never heard it refered to as beige. Bondi-Blue is the color, that greenish blue color, the apple coined.

check this wiki:

[http://en.wikipedia.org/wiki/Bondi_blue](http://en.wikipedia.org/wiki/Bondi_blue)

The iMac is a new world mac, and so your problem should be different then mine, though I suppose they may be closer then I think.  Have you tried using the Live CD?  I don't know the specifics for installing on the iMac, but try following all the instructions for a New World Machine.  Hopefully someone here will know what to do.

I didn't think the imac had that 8 GB limit, which is a limit for installing OS X on a Beige G3.  I also don't know if Linux suffers from this limitation either.

Good Luck.

---

### Post by Theo-Ubu on 2006-05-09
OK, thanks for the name explanation on that color.  I'll butt out of your thread here and go a-searchin' for my problem fix elsewhere.  You might be right about that 8Gig limit not applying to me.  I've been confused about the naming of these machines, so I may have mixed up that limit with mine.

---

### Post by jdp on 2006-05-09
[LowEndMac.com](http://lowendmac.com/imacs/imac.shtml) has some good listing of Mac specs and quirks.  It says early imacs did have the 8GB issue, at least usder OS X.  FWIW, that might not apply to Ubuntu but I don't have an iMac of that vintage so I can't say for sure.

---

### Post by jdp on 2006-05-10
[QUOTE=Wyvernspirit]I am trying to install ubuntu 5.10 breezy {...}
[B]cd /target
mkdir hfs
mount /dev/sda5 hfs -t hfsplus
[/B]
but I get an error message with that last line and can't continue, and can't seem to find any answers.  The error message is:
{...}
[/QUOTE]

On 5.10 you absolutely do not put the **-t hfsplus** as part of the mount command.  When I went through it on a fresh G3MT last night, I tried leaving the filesystem flag in the command and it failed.  I ran it again with just **mount /dev/sda5 /target/mnt/hfs** it mounted without issue.  Note that this G3 has a PCI SCSI card, so sda is correct in this instance.  The MacOS HFS+ is on partition 5, / is EXT3 on 6, and swap is on 7.

Also, on 5.10, you do have to specify both the kernel and initrd in BootX, and also put a setting in the boot options box for root.  ie **root=/dev/sda6** or it will fail to mount root.

I covered this in the update for 5.10 in my [thread on Applefritter.com](http://www.applefritter.com/node/8936#comment-27914).

---

### Post by Wyvernspirit on 2006-05-10
[QUOTE=jdp]On 5.10 you absolutely do not put the **-t hfsplus** as part of the mount command.  When I went through it on a fresh G3MT last night, I tried leaving the filesystem flag in the command and it failed.  I ran it again with just **mount /dev/sda5 /target/mnt/hfs** it mounted without issue.  Note that this G3 has a PCI SCSI card, so sda is correct in this instance.  The MacOS HFS+ is on partition 5, / is EXT3 on 6, and swap is on 7.

Also, on 5.10, you do have to specify both the kernel and initrd in BootX, and also put a setting in the boot options box for root.  ie **root=/dev/sda6** or it will fail to mount root.

I covered this in the update for 5.10 in my [thread on Applefritter.com](http://www.applefritter.com/node/8936#comment-27914).[/QUOTE]
 

Thank you for the post, I will try your suggestion.

---

### Post by 3rdalbum on 2006-05-12
Sorry for the wrong information, I got a bit confused.

Theo: In Open Firmware, try typing the command without the backslashes, e.g.:

boot hd:2,yaboot

---

### Post by Wyvernspirit on 2006-05-13
[QUOTE=jdp]On 5.10 you absolutely do not put the **-t hfsplus** as part of the mount command.  When I went through it on a fresh G3MT last night, I tried leaving the filesystem flag in the command and it failed.  I ran it again with just **mount /dev/sda5 /target/mnt/hfs** it mounted without issue.  Note that this G3 has a PCI SCSI card, so sda is correct in this instance.  The MacOS HFS+ is on partition 5, / is EXT3 on 6, and swap is on 7.

Also, on 5.10, you do have to specify both the kernel and initrd in BootX, and also put a setting in the boot options box for root.  ie **root=/dev/sda6** or it will fail to mount root.

I covered this in the update for 5.10 in my [thread on Applefritter.com](http://www.applefritter.com/node/8936#comment-27914).[/QUOTE]

I am going to try your suggestion about leaving the filesystem flag off, but I did want to make one point.  Although the G3 has a SCZI Bus, the standard HD, and the one I have, is IDE.  The one I have is an upgrade from Stock, but is on the IDE bus.

---

### Post by Wyvernspirit on 2006-05-13
Ok, I have gotten past this problem (by the way **mount /dev/hdc6 hfs**, no filesystem tags, worked, thanks for the help) but I have a new issue.  In-Fact, its the next part of the install, the command is supposed to go in as:

**cp /target/boot/vmlinux /target/hfs/System\ Folder/Linux\ Kernels/ubuntu.5.1.0.vmlinux**
(ubuntu.5.1.0.vmlinux is what I named the vmlinux file)

I get an "no such file or directory" error message on this.  Any ideas what  I have done wrong?  The help so far has been great, hopefully someone will be able to figure this one out.

---

### Post by jdp on 2006-05-14
Did you use the auto name completion, or did you type each file/directory by hand?  I use the name completion so that I always get the correct full path.  You do it by typing the start of the directory or file name, and then hit tab.  If you have enough characters for a unique name, it'll fill in the rest of that one name, then start a few letters of the rest of the name and press tab again.  It's much easier done than explained.  If you don't use it yet, it'll be a feature you come to love when working in the terminal, esp. when dealing with the naming structure of files with spaces and other odd characters in the filename.

---

### Post by Wyvernspirit on 2006-05-14
[QUOTE=jdp]Did you use the auto name completion, or did you type each file/directory by hand?  I use the name completion so that I always get the correct full path.  You do it by typing the start of the directory or file name, and then hit tab.  If you have enough characters for a unique name, it'll fill in the rest of that one name, then start a few letters of the rest of the name and press tab again.  It's much easier done than explained.  If you don't use it yet, it'll be a feature you come to love when working in the terminal, esp. when dealing with the naming structure of files with spaces and other odd characters in the filename.[/QUOTE]

Thank you for the response, and no I did not use tab to auto-complete.  I will give that a shot.  One thing, and this is just some more info just in case it matters, when I view the hfs directory, it has four files, a Finder, a System, one that I don't recall and a Where_did_my_files_go?.  In System (not System Folder) it is empty.  Don't know if this will affect the cp command or the auto-complete.

Thanks for the help thus far, and for any that may come later in advance.

---

### Post by Wyvernspirit on 2006-05-14
Ok, problem, when using the auto-complete feature and I get to Sy (for System Folder) I get System followed by a space, no /, no Folder no \, just System followed by a space.  It doesn't try to auto-complete anything else.  if I hit enter I get"

cp: unable to open `/target/boot/vmlinux /target/hfs/System' Read-only file system

So now what?  Thanks for all the help.

---

### Post by jdp on 2006-05-15
It looks like your partitionis mounting as HFS and not HFS+.  Thus, the Where_did_my_files_go? file.  What Mac OS is on the G3? I haven't seen that pop up unless it was with an older install of OS 8.  ISTR not having that issue when using OS 9.  I haven't installed to a G3 with OS 8 yet, so i'm almost outta help here.  I did half start a couple installs on a 7600 and an 8500, but I'm pretty sure the 7600 was with OS 7.6 and the 8500 had 9.1...  OS 8 was the mid point for HFS/HFS+ transition so it may be an issue with that.  Maybe there is some flag to force mounting with HFS+ that would work, since it seems that using the **-t hfsplus** is causing troubles?

---

