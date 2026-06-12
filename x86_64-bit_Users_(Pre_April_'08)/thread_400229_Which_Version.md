---
title: "Which Version"
date: 2007-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by sammyd253 on 2007-04-03
I am planning to do some upgrading work on my PC in the near future.  More of my applications and drivers are becoming compatible with Vista.  I plan to back up my PC and "upgrade".  Now, I also want to create a separate partition for Ubuntu.  I realize that dual-booting can be tedious and in some cases, not the best solution, but my mood towards operating systems changes frequently.  Unfortunately, I've also reverted back to Windows as a safety net when things became tough in Linux.  This has prevented me from keeping a full time Linux install and I regret that.

I believe with computers, you can never have too much knowledge.  There's so much to learn, even just using Linux.  The amount of power behind the OS is amazing.

So now that I've given you a cheesy little intro into this post, my question is:

Which version of Ubuntu should I install?

I have it narrowed down between 6.06 LTS and 7.04 Beta.  I understand that if I want stability I should go with version 6.06 LTS.  Regardless of which version I get, I will be installing the 64 bit version.  Here, I also understand that I may run into some slight incompatibilities, but believe that I have the patience to work around these issues.  From what I'm hearing, the final release of 7.04 is sometime in April, but I want to use Linux now.  Do you think I'd be more beneficial from installing 6.06 LTS, or 7.04 at this point in time?

Keep in mind, I am NOT looking for a Windows replacement.  I am simply looking for a chance to get better acquainted with Linux.  It will most likely take me awhile (months), but I believe if I leave the OS on my system, I will have an enjoyable experience with it.  I even expect to break the OS a few times, no problem though, I don't plan to keep critial data on that partition.


Sorry for the long post, and thanks in advance.  I'm curious to hear people's opinions!

---

### Post by nss0000 on 2007-04-03
BigS:

So I read, Dapperx64 ( U_6.06LTS ) will be "wrapped into" future releases of LTS UBUNTU versions. I take that to mean TRIVIAL UPGRADE TASK. To me that means a lot as I expect lots of feature packporting during LTS lifetime from the more "frisky" releases.

So with U_6.06 you get-da-gravy without working overtime . 

nss
*******

---

### Post by madcow72 on 2007-04-03
Hey sammyd253.  For stability and long support, nss0000 is correct that 6.06 would be a good choice.  However, my opinion is to install Feisty.  Don't be scared by it's name!

I began using 6.06 as a Linux first time user doing dual-boot last September with XP.  After a month or so, I deleted Windows, installed Edgy and made Windows my Virtual machine.  I only used Dapper for a little while, but still found Edgy significantly smoother than Dapper as a user.  About 2 months ago, I upgraded to Feisty and am *really* impressed at how streamlined this distribution is becoming.  Feisty has excellent support for peripherals, samba, etc. and seems to require even less of my time on the command line.  Even though it's in its beta stage, Feisty is quite stable on both of my computers and may end up giving you a lot less headache in the long run.  If you keep up with the updates, then your system will be no different from the final version released this month.

I don't know what your system looks like, but if you plan on dual-booting, I would suggest getting separate harddrives for Ubuntu and for Windows.  Then, after installing Windows first, install Ubuntu (whichever version you decide) on the 2nd harddrive, and while installing, use the partition manager to give your /home directory it's own partition.  This way, you can install, re-install, or choose different versions of Ubuntu without ever losing your documents or settings.  If you decide to install another version of Ubuntu, just install it to the first partition of your Ubuntu harddrive and point the installer to your /home directory partition - Ubuntu will take care of the rest.

Hope that makes sense!

---

### Post by sammyd253 on 2007-04-03
Very helpful.  I think I am going to install Fiesty onto my system.  Here's what I'm thinking.

I would like to install Windows and Linux on 2 separate hard drives, however, I currently only have 1 drive.  I have the funds to purchase a new drive but I find this extremely unnecessary.  Since my main drive is 250GB I can partition this for both operating systems.  I plan to give Vista a 40GB partition, and I'd also like to give Ubuntu a 40GB partition.  The nice thing is that I currently have an 80GB NTFS partition containing all of my music/movies, and by default I hear Fiesty should be able to read from that partition just fine.  

I plan on making my swap partition 4GB (I have 2GB of RAM).  How big should I make the /home partition?

Basically this is how things seem to be shaping up:

Vista - 40GB
Ubuntu - 40GB
/home - 10GB?
/swap - 4GB
Media - 80GB

This still leaves me quite a bit of room, perhaps I'll make a gaming partition.

What I am concerned about though is this.  If I install Fiesty now and setup everything the way I like it, once it goes final, won't I have to update the kernel and re configure everything anyways?  Or is this what you mean by the separate home folder partition?  I'm a little confused about how to get that working right...

---

### Post by madcow72 on 2007-04-03
I would swap your numbers between the /home and the Ubuntu root partitions.  Ubuntu only requires 3GB I think for install, but you obviously want to give that some room.  I usually give my root partition about 15GB, actually, and then designate all remaining room to /home.

I only have to warn you, however, that if your partitioning fails at any time, it's likely that you'll lose everything on that drive.  Windows, ubuntu, Media, etc...  You're right that there's no reason you have to go out and buy a 2nd harddrive to do the install, but I would really really suggest getting yourself an external drive to backup your media and important documents to.  It's not fun to lose your files because either you or the OS install (or both) did something stupid.  (Speaking from experience.)

Good luck!

---

### Post by madcow72 on 2007-04-03
> **sammyd253 said:**
> What I am concerned about though is this.  If I install Fiesty now and setup everything the way I like it, once it goes final, won't I have to update the kernel and re configure everything anyways?  Or is this what you mean by the separate home folder partition?  I'm a little confused about how to get that working right...

Well, if you have any restricted drivers, such as the nvidia video driver, you'll likely have to reinstall that when the kernel changes.  However, this has nothing to do with Feisty hitting its final version - you would have to do that regardless.  On the other hand, if you use open source drivers, you shouldn't have to worry about anything.  

Either way, when your /home directory has its own partition, all of your files and settings (icons, desktop wallpaper, firefox history, plugins, bookmarks, etc) are preserved on that partition.  That means that, say you screw up your system, or want to install a different version, then you don't lose any of that.  What you do is this:

Assume your hard drive is partitioned like this:

hda1 - Windows
hda2 - /root (Ubuntu)
hda3 - /home
hda4 - swap

and you want to reinstall Ubuntu.  You throw in the live CD, start the install, tell the partition manager that you will be formatting and installing the /root partition to hda2, the /home partition is hda3 which should **NOT** be formatted, and swap is hda4.  Then continue with the installation.  [NOTE:  If you don't use the same user name for the re-install as the original, then you will create a new user which won't have the same settings.  For simplicity's sake, always use the same user name upon re-install.]  After the install, when you reboot your computer into Ubuntu, you should boot into an account that looks identical to the way you left it, only being accessed by your fresh Ubuntu installation.

Hope that makes sense!

---

### Post by sammyd253 on 2007-04-04
Very helpful information.  Since I am pretty familiar with the partitioning process, this shouldn't be too difficult for me to setup.  I completely understand and agree with your viewpoint on having the external HD, and fortunately I do, 120GB of backup storage.  Before I do any formatting, I will be backing up my music, pictures, and documents.  I plan to run the Windows Vista install and during that time, wipe ALL partitions from my hard drive.  Then I'll create a 40GB parition for Vista and leave the rest of the space unallocated.  Then when I run the Ubuntu setup, I will create the Linux partitions in the unallocated space.  What filesystem do you recommend for the /root and /home partitions?  ext3?  Is there anywhere I can go to research file systems a bit?

---

### Post by Kilz on 2007-04-04
> **sammyd253 said:**
>   Is there anywhere I can go to research file systems a bit?

Google has a wealth of information on linux file systems.

---

### Post by sammyd253 on 2007-04-04
Awesome.  I'll check it out.  Thanks.

---

