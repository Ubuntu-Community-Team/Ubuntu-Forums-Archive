---
title: "Perfect install in Ubuntu! (kubuntu added after)"
date: 2008-05-14
forum: x86 64-bit Users
---

### Post by cacycleworks on 2008-05-14
Wow, I can't believe it!

I put ubuntu Hardy desktop alt x86_64 cd in my Dell D630 ... and at the other end of the install, I had sound, wireless, 1400x900 video, *and flash* installed and worked, too. I used the FOSS mozilla-plugin, not the adobe non-free one. Didn't even try (or care) to use non-free. And apt-get install kubuntu-desktop now has me a working kubuntu installation!

what the he...... ?? I have never ever had an install work so smoothly on this viciously cantankerous notebook! Wow! In the last 2 weeks, I tried the following installations which were rejected for various reasons:

> Archlinux 64 bit to get archmod for kde4 but the Arch 32 bit developers broke'd dependencies for 64 bit archmod.
> OpenSUSE 64bit to get KDE install. Adding a new package took minutes... so I put in next cd & shutdown to install to another option...
> ubuntu server x86_64 alt cd, then aptitude to install KDE4 ... sorta worked, but KDE4 still isn't quite ready for consumption. Sound & wireless? Got me... was plugged in and couldn't get happy with the desktop.
> kubuntu KDE4 remix - no different than above.
> kubuntu Hardy desktop alt x86_64 (see below)

FWIW, kubuntu Hardy desktop alt x86_64 did NOT install correctly. Sound was missing (no fixes worked... no sound cards found) and the bootup was trying to get the intel 3945 microcode firmware from a bad directory, which I also couldn't figure out. So I tried ubuntu and it worked. 

To get kubuntu, I installed ubuntu and then [followed this guide]("http://www.debianadmin.com/install-kde-desktop-in-ubuntu.html") to the letter and out of this is a perfectly working kubuntu installation. This is the first time I've had sound on my desktop since buying this notebook!

Wowowowow!
:)

---

### Post by inphektion on 2008-05-15
Interesting that a kubuntu install didn't get everything working but the ubuntu install and then kubuntu-desktop install worked fine.  Both were with KDE4?

---

### Post by cacycleworks on 2008-05-15
No, KDE3 ... I was unable to get a satisfactory setup with KDE4, however, I would attribute that more to KDE4 and not the install itself. In other words, I would suspect the same chance of success with KDE4 if I went this route.

In KDE4, I couldn't figure out how to tweak the UI enough for me to stay with it. Too much different from KDE3. I'll invest time into the transition once 4 is released. I'd rather not put effort into learning something when some of that knowledge is about to change due to bugfixes. :) 4 looks exciting and I am eager for its release.

The major issue I had with 4 was how the screens are treated. Everything is ok if I just use the laptop's screen, but once I plug in an external monitor, KDE is a touch clumsy with how it treats them, and the desktop panel is stuck at the laptop's screen width... so looks silly on the 24" monitor at work and is cut off on the 19" monitor at home. 

Thanks,
Chris

---

### Post by Achetar on 2008-05-15
Happy to hear it. I know that the secondary (as in not the original Ubuntu) distros have a little bit of lag compared to Ubuntu. For instance Kubuntu didn't get Desktop Effects until 7.10, whereas Ubuntu got it at 7.04

---

### Post by swazzler on 2008-07-02
I'm writing to ask for some advice. First, I'm a complete gnubie. My knowledge of linux is limited. Second, I've also got a D630 which I bought at the end of 2007. I ordered it with XP as I'd heard too many horror stories about Vista. 
However, my plan was to shift over to Ubuntu 7.10. I had no problems with the install, creating a dual boot with XP - a 'just in case' measure. I then gave myself one month to get the system up and running before using it for work.
Needless to say, one month was not enough. I was forced to shift back to XP until I could figure out how to get my tbird settings into linux.
Then I tried to get the sound working, and had it functioning for about two weeks before it conked out (probably because I was trying out different programs and may have erased something important in the process).
Then, I started running into problems with the bcm43xx-fwcutter every time I went for updates and, to this day, have been unable to load in a new, working version.
With all these problems and so little know-how, even with the best of intentions, I found myself forced to revert back to XP.
Now that Hardy is out, and I have a bit more time on my hands, I'm ready to try getting back into Ubuntu... and perhaps ditch windows for good, if I'm lucky.
However, my Gutsy isn't giving me the option to upgrade with the update manager. Probably because it is having problems updating Gutsy.
So, I'm thinking that I'll have to do a clean install and overwrite Gutsy.
BUT, before I do anything, I'd like some advice and help.
You stated that you had a great upgrade experience with Hardy.
Was that with the final distro or a testing version?
Do you have any suggestions on the best way of going about upgrading? (I don't want to dump XP until I'm comfortable with Hardy. Is upgrading going to endanger my XP partition?)
Could you walk me through the process, step by step, or could you point me toward an on-line guide that would do this for me? (I haven't been able to locate one on the ubuntu site... at least not one that covers each step... just general directions)
Am I approaching this at the right time, or should I hold off for a couple of months.

Thanks in advance
2. Should I erase Gutsy before trying to install Hardy?

---

### Post by cariboo on 2008-07-03
Wait until tomorrow July 3 2008 version 8.04.1 is supposed to be released, with plenty of bug fixes.

Jim

---

### Post by cacycleworks on 2008-07-03
Hi swazzler,

Great questions.

My suggestion is not to perform an "upgrade" instead, as I mentioned above, do a fresh install. I also experienced troubles while upgrading within 7.04 and 7.10, so this I consider to be an unusual exception. If I had to guess, it is my thoughts the kernel changes coupled with some ubuntu changes created more instability than the ubuntu team would normally allow. 

I found 8.04 to be great (and the first time sound worked reliably) ... so 8.04.1 should be even better.

My next suggestion would be if you continue to have problems with the bcm43xx driver is to get and install an intel 3945 wireless card. There's one on [eBay for $14.95, shipped]("http://cgi.ebay.com/Intel-Pro-3945-Wireless-MINI-Card-802-11-a-b-g-802-11g_W0QQitemZ360067043803QQihZ023QQcategoryZ45000QQssPageNameZWDVWQQrdZ1QQcmdZViewItem"), item#  360067043803. Dell's support site has an online [service manual showing how to change it]("http://support.dell.com/support/edocs/systems/latd630/en/SM_EN/minicard.htm#wp1084976"). Even if you're not able to do it, print out the steps and take it all to a computer shop and they can do it. :)

Here are some other thoughts I have about your situation and your needs...
- look into mozbackup ... it can create a backup file with all of your info in it. Then you should be able to re-import this into the linux world.
- get something like norton ghost and backup your XP world. This makes fixing an "oops" much easier than a reinstall of XP.
- oh man, if t-bird is all that's holding you back, replicate your reality manually in linux land... ;)
- and always make /home its own partition, so when you do fresh installs of linux, it is a quick process to change from one version to the next.

:) Chris

---

### Post by swazzler on 2008-07-03
Chris,

Thanks for the suggestions :-)
Hope you can stand a few more questions.
1. Should I delete Gutsy before installing Hardy or can I leave that to the installer to clean the partition?
2. Will the install affect my XP partition (Yes, I'm backing everything up first, but I'd like to know anyway, to prepare myself for the downtime)
3. The Ubuntu Download page does not list Hardy as 8.04.1, simply as 8.04. If the download site directory lists 'last modified' as July 03, can I assume that it is version 8.04.1?
4. You suggest that I might consider picking up an Intel 3945 wireless card if I continue having problems with the bcm43xx driver. Please remember, I&#8217;m new to the Linux scene and still trying to figure things out. Having said that&#8230; I have a 3945 wireless card installed. I gather from your comment that if I have a 3945 I shouldn&#8217;t have bcm43xx&#8230; am I right?
5. The Thunderbird issue was tricky but solvable, and I had T-bird running with all my email info in Ubuntu. I switched back to XP because of the sound/video problems (this is an important issue for me), coupled with some other minor issues (getting the emule, skype, googletalk equivalents etc. functioning properly).
6. Can you point me to a good guide to partitioning? When I installed Gutsy, I didn&#8217;t create a home partition. Now, I think I&#8217;m ready to go ahead with this.
7. Which ISO would you suggest I use: the regular one or the alt (I&#8217;ve download them both)?

Thanks in advance :-),

Roger

---

### Post by cacycleworks on 2008-07-03
Hi Roger,

1) The installer will nuke Gutsy for you.
2) The install will affect your XP partition. I have seen lots and lots of Q&A about this topic on the forum, but have no personal knowledge. When I wanted to "dual boot", I took the hard drive out of my sony sz220 and put it in a USB enclosure. If attached upon power-on, XP would boot. This was how I did my own transition. Otherwise, I'm sure there are some good tutorials about how to make a dual boot happen.
3. I don't know enough about it to answer this. imho, this is not a worry ... install 8.4 (.0?) and then is ok to upgrade (but again, never do a dist-upgrade).
4. Yes, you do not want the bcm43xx thing. The Intel 3945 is the best card that can be bought with the D630 for linux.
5. Given the awesome basic install that I got, I am sure you will be pleased. I understand your hesitation as my gutsy experience was also one to be forgotten.
6. [This post is pretty good]("http://ubuntuforums.org/showthread.php?t=282018")... they have an example for windows + linux, that you can use. Note that home is all by itself. ;)

Here is how my D630 is set up now:
```
/dev/sda1 on /boot  200M
/dev/sda2 on /		15G
/dev/sda3 on /usr 	10G
( /dev/sda4 is the extended partition )
/dev/sda5 on /home	the rest... ~80G?
/dev/sda6 on /var 	15G
/dev/sda7 on /tmp 	5G
```

You don't need so many partitions. Heck, *I* probably don't, but I got in the habit with the servers. Sometimes /var/log goes crazy and fills up. I could get away with a very tiny /tmp as I have a ton of memory, however, to suspend you must have more /tmp than RAM. I don't know why I do the /boot 200M partition, but this is something everyone in my circle does and I think I read somewhere there is an advantage. Got me.

Minimally, I use /, /home, and /tmp, which I believe is the current setup on my sz220 at home.

7. I believe only the ALT CD will boot in the D630. imho, the only difference is that the live cd lets you use a mouse to install and takes forever to boot, while the alt cd FLIES and you use the command line and then boot to ubuntu gnome desktop on restart. 

Whenever I install the OS, I normally have the ethernet cable plugged in. It just seems to make life a touch smoother. But I've done it both ways.

BTW, that great partitioning post came from googling ubuntu partitioning

:) Chris

---

### Post by swazzler on 2008-07-04
Chris,

Well, I went for it. First, I did a thorough (and I mean thorough) backup... just in case. 
Then I rebooted with the altCD. I checked the CD before going through with the install.
Everything was fine until I got to the repartitioning. At this point, I decided to go with the guided partitioning. I still don't feel fully prepared and comfortable with mucking around with the partitioning, especially as I don't have a written, clear guide to the process, only virtual copies that can't be accessed during a system installation (for that, I'd need two computers).
Anyway, the option it gave was to put 8.04.1 in the same partition where I had 7.10. As I allowed it to use the whole partition, it completely overwrote Gutsy, which was fine with me.
The rest of the set-up required virtually no input from me, so I let it run.
Then, came the bit about names, passwords etc. I used the same ones I'd used for Gutsy. 
Grub installation recognized the XP so I let it install.
Finally, the message came up to remove the cd and reboot the computer.
This I did, re-entering with Hardy.
However, it gave me an error message on the sign-in (name and password).
I don't know exactly what the error was as nothing appeared in the error box. But, the end result is that I can't get into Ubuntu.
As it's already 10pm, I think I'll leave it for another day.
Would I be right in thinking that I'm going to have to go through the whole installation process again?

:-( Roger

---

### Post by cacycleworks on 2008-07-08
Hey Swazzler,

Aw man you're so close! I believe a reinstall is not required, though you'll need to search around how you can reset your login and password by using the liveCD or alt cd with "repair" option.

Ubuntu forums should have it somewhere... its search or google should be able to help.

But it could be worse! I actually managed to do the same thing with the bios password on a laptop once. :( I set it to the most basic of my memorized passwords and somehow typed it wrong the same way twice in a row. It took me faxing my receipt in and then 3 days to get through to sony tech support who could help me. That was fun...

I'm sorry about the partitioning ... maybe print out the virtual copies? It isn't difficult but has lots of repetitive steps making for lots of keystrokes.

:)
Chris

---

### Post by swazzler on 2008-07-11
Chris,
Sorry for taking so long in getting back, work, you know. It really seems to get in the way of the important stuff, like getting Ubuntu running.
Anyway. As I mentioned, I haven't been able to login to hardy.
The message I get is the "Your session only lasted 10 seconds..." one, which gives a lack of diskspace as a possible reason. I seriously doubted that this could be the problem, as I gave Hardy around 60G to use.
So, today, with a bit of time on my hands, I went looking for an explanation for the '10 seconds' message.
Googling it led me to one Ubuntu page that suggested entering via the terminal (which I've been able to do) and typing: 
df -h
to see how much space is available, then typing
sudo apt-get clean
to clear up some more space
I did this, and for some reason it said the partition had only 2.1G, of which 2.1G was being used. After the 'clean' it dropped to 2G being used
Does this make any sense? Did the Installation go badly wrong and not use all the space I asked it to? Is this easily fixable or should I try re-installing Hardy? As I've not even used Hardy and have no files to lose, I'm not really bothered by the idea of reinstallation... it's just a question of setting aside about an hour or so to go through the process again. 
What's your take on my predicament?

thanks, 
Roger

---

### Post by cacycleworks on 2008-07-11
Hi Roger,

Thanks for writing back. Yeah, I'm hip deep in that work thing, too! :)

It is possible that the partitioner used all "available" disc space, meaning there was only 2.1 G unused at the time. 

Ultimately, you need to put some effort into learning more about partitions. I think there could be something fundamental we are not realizing together, which might be solved if you got better understanding of partitioning.

I looked around a little bit, and Norton's "partition magic" program's [User Guide]("ftp://ftp.symantec.com/public/english_us_canada/products/norton_partitionmagic/npmagic_8/manuals/norton_partitionmagic_8.pdf") has some great information. Specifically, on page 14 is a diagram showing the visual layout of the disks. After paging down quickly, there is a lot of great generic information in it. Just ignore where they talk about how to use the program.

Always remember that any partitioner gives you a very obvious chance to cancel the commit of a partitioning. 

Another thing to try is see if something like Knoppix will run on your D630. When I first got in a batch of Dell C521's, I wanted to keep one of them dual boot with Vista... I ran knoppix, which has gparted. I forget if it was gparted or another program, but I resized the Vista partition and then installed ubuntu in the free space. I was in a learning frenzy then and this computer would boot to 4 OSs... Vista or Ubuntu via HD, Knoppix if I forgot to remove its CD from the tray, or SLAX via a USB stick.

I really like gparted because it does a visual map of the drives and partitions (like the user manual above). 

Here is aptitude's description for its command line cousin, parted:
> 
The GNU Parted disk partition resizing program
GNU Parted is a program that allows you to create, destroy, resize, move and copy hard disk partitions. This is useful for creating space for new operating systems, reorganising disk usage, and copying data to new hard disks. This package contains the Parted binary and manual page.
 
Parted currently supports DOS, Mac, Sun, BSD, GPT, MIPS and PC98 disklabels/partition tables, as well as a 'loop' (raw disk) type which allows use on RAID/LVM. Filesystems which are currently fully supported are ext2, ext3, fat (FAT16 and FAT32), ReiserFS (with libreiserfs) and linux-swap. Parted can also detect and remove HFS (Mac OS), JFS, NTFS, UFS (Sun and HP), XFS and ASFS/AFFS/APFS (Amiga) filesystems, but cannot create, resize or check these filesystems yet.
 
Note that ReiserFS support is only enabled if you install the libreiserfs0.3-0 package. Since libreiserfs0.3-0 has been removed from sarge, ReiserFS support is not compiled in the default package.
 
The nature of this software means that any bugs could cause massive data loss. While there are no known bugs at the moment,  they could exist, so please back up all important files before running it, and do so at your own risk.


aptitude is a command-line "apt" package managing tool. It is very powerful and does better dependency checking and maintenance of your packages than other managers I've seen. It's kinda clunky to work with, so I use synaptic to find what I want and then use / search in aptitude to actually get it. :)

gparted is the gnome front end for parted. I have attached a screenshot of my D630's current configuration.


Thanks,
Chris

---

### Post by swazzler on 2008-07-12
Chris,
Thanks for the fast response :-)
Last night, I was re-reading the 'hermanzone' page on installing Ubuntu ([http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)), as I found his instructions quite helpful last year when I installed Gutsy.
About a third of the way down the page, he gets to the part about partitioning and shows a screen display option list with the third option being 'erase data on this partition'.
Is it possible that this is what I should have done the first time around on my ext partition?
I've just downloaded gparted and am working my way through the manual, haven't read it all yet, and I've got a doubt. 
If the Hardy install only used available space on the partition, then the Gutsy files should still be occupying the rest of the space, right?. 
So, will gparted show which is which, or will it just show the overall partitioning. And, if it does show that there are two different OS occupying the partition, will it be clear which is which (so I'll know which one to erase and which one to keep)?

Again, thanks so much for your advice; it truly is inestimable. This is one of the great advantages that Ubuntu has over Windows: ubuntu folks are friendly and helpful, whereas the windows help crew, if they deign to respond, often appear 'put upon' when asked for advice.

Roger

---

### Post by swazzler on 2008-07-26
Hello again,

After a hectic two weeks of massive workload, I've now got a moment to breathe and see if I can resolve this installation problem.
GParted gave me the following info:

/dev/sda1 fat16       62.72MiB   7.69MiB 55.04MiB
/dev/sda2 ntfs        59.15GiB  31.70GiB 27.45GiB boot
/dev/sda3 ext3        48.15GiB 569.23MiB 47.60GiB
/dev/sda4 extended     4.43GiB   ---       ---
/dev/sda6 ext3         2.08GiB   2.01GiB 70.71MiB
/dev/sda7 linux-swap 164.70MiB   ---       ---
/dev/sda5 linux-swap   2.19GiB   ---       ---

It appears that Hardy only took the absolute minimum space required for install from the Gutsy partition, though the Gutsy files seem to have been wiped (I can't believe that Gutsy is only 570MiB).

So, I'm guessing that the next step would be to shift partitioning from the first ext3 partition (Gutsy) to the second ext3 (Hardy) partition, right?
Would I also be correct in guessing that I'll have to chase this space down (add it to the 'extended' partition, then remove it from the 'extended', then add it to the second 'ext3' partition) or is there a way to simply shift it directly to the second partition?

Do you have any idea what the 'extended' partition is?
Do you have any idea why the sda numbering is confused (sda4, sda6, sda7, sda5)?
I'm guessing that one of the linux-swap partitions is for Gutsy and the other is for Hardy. Is there any way to tell which is which? Could it be that the lower number, sda5, is Gutsy and the higher number, sda7, is Hardy?

Right now, I'm thinking that the safest option would be to just transfer the partition space from the first ext3 to the second ext3 and leave the other partitions alone. Does this sound reasonable?

Looking forward to hearing from you,

Roger

---

### Post by cacycleworks on 2008-07-26
Hi Roger!

Oooo, sorry about not seeing that 2 week old post. I'm hip deep in a miasma of MySQL, javascript, jQuery and php. :)

> **swazzler said:**
> Hello again,
After a hectic two weeks of massive workload, I've now got a moment to breathe and see if I can resolve this installation problem.
GParted gave me the following info:

/dev/sda1 fat16       62.72MiB   7.69MiB 55.04MiB
/dev/sda2 ntfs        59.15GiB  31.70GiB 27.45GiB boot
/dev/sda3 ext3        48.15GiB 569.23MiB 47.60GiB
/dev/sda4 extended     4.43GiB   ---       ---
/dev/sda6 ext3         2.08GiB   2.01GiB 70.71MiB
/dev/sda7 linux-swap 164.70MiB   ---       ---
/dev/sda5 linux-swap   2.19GiB   ---       ---

It appears that Hardy only took the absolute minimum space required for install from the Gutsy partition, though the Gutsy files seem to have been wiped (I can't believe that Gutsy is only 570MiB).

My thought is that the 2nd automated installer did the best it could with what was leftover from the 1st automated installer's work.

> **swazzler said:**
> Hello again,
Do you have any idea what the 'extended' partition is?
Do you have any idea why the sda numbering is confused (sda4, sda6, sda7, sda5)?
I'm guessing that one of the linux-swap partitions is for Gutsy and the other is for Hardy. Is there any way to tell which is which? Could it be that the lower number, sda5, is Gutsy and the higher number, sda7, is Hardy?
(note, I changed the order of your post here)

Yes, the extended partition is a result of the original limitations of how computers "see" hard drives. I dug up a few more how-tos that do a great job explaining it all...
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[http://www.linuxplanet.com/linuxplanet/tutorials/3174/1/](http://www.linuxplanet.com/linuxplanet/tutorials/3174/1/)

And this one has screen shots from the ubuntu installer:
[http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html)

You only get 4 "primary" partitions. If you need more than 4 "drives" or partitions on a disk, you need to make one of the "primary" partitions "extended", or a like a holder for extended partitions. Those articles above talk about this a few different ways. Linux always makes sda4 the extended partition and it is a "ghost" partition, while sda5 (and greater) are what the computer and the operating systems use to get to the files.

> **swazzler said:**
> Hello again,
So, I'm guessing that the next step would be to shift partitioning from the first ext3 partition (Gutsy) to the second ext3 (Hardy) partition, right?
Would I also be correct in guessing that I'll have to chase this space down (add it to the 'extended' partition, then remove it from the 'extended', then add it to the second 'ext3' partition) or is there a way to simply shift it directly to the second partition?

Wellll, assuming that you're not wanting to attempt to reuse data on either of the unix installations, I suggest doing exactly as the guy does in that last tutorial:
[http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html)

BUT... you will need to delete partitions before telling the installer to go automatic! So you'd have to enter manual mode, delete the partitions, then "go back" or "cancel" or whatever it takes to get back to that same manual/automatic page and then choose automatic paritioning.

Use the menus to navigate through:
delete sda7, then 6, then 5, then 4, and finally 3. You will be left with sda1 and sda2, which are for your windows world. And you should have roughly 55GB available for ubuntu.

I re-reviewed that above great pictorial howto ( [http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html) ) and he has pictures of most of the process, but not exactly the deleting part.

> **swazzler said:**
> Hello again,
Right now, I'm thinking that the safest option would be to just transfer the partition space from the first ext3 to the second ext3 and leave the other partitions alone. Does this sound reasonable?

Oh, I kinda handled that above. :) BUT -- please read the links I posted and understand the process before you actually do what I suggested. Nothing I said will hurt your windows install... but here are some tools I believe you (me, and everyone) should have before setting out to play with partitions:

- have backed up important data on the disk to DVD, CD, etc
- have a working "live cd", preferably more than one flavor. I particularly like knoppix in addition to ubuntu. The knoppix live cd is more tailored to act as a rescue cd than the ubuntu live cd and has gparted ready to go.
- if you care about windows, you should have dos and/or winXP boot disks.

:) Chris

---

### Post by swazzler on 2008-07-27
Chris,

Thanks for the tips :-)
I feel like a bit of an idiot (well, actually, a great big idiot) because I'd already read the second link (ubuntuforum) that you list and should have realized immediately what was going on with sda4 extended and the subsequent sda5-7.
If I understand correctly, when I told the installer to use the Gutsy partition for the Hardy install, it broke off only 4.43 GiB, sda4, from which it subdivided 5-7, as logical partitions, to install Hardy, right?

Am I correct in understanding that you suggest I should reinstall Hardy (after deleting the non-windows partitions), rather than trying to shift the diskspace to the existing Hardy partition (sda6)?

Also, when I delete the partitions, which option would be better: leaving the 55-odd GiB as free space or allocating them to the windows partition? When I first installed Gutsy it was all part of the windows partition, but I think I remember seeing an option in the Hardy install for using free space instead of dividing the existing partition, though I can't remember for sure.

I'm thinking about deleting the unix partitions with my GParted cd, then loading the Hardy cd to do the re-install. Will deleting Hardy do a number on my grub, considering that various versions of Hardy are listed  before windows, or will everything be fine?

as ever, thanks so much for your assistance!

Roger

---

### Post by cacycleworks on 2008-07-27
> **swazzler said:**
> Chris,
Thanks for the tips :-)
I feel like a bit of an idiot (well, actually, a great big idiot) because I'd already read the second link (ubuntuforum) that you list and should have realized immediately what was going on with sda4 extended and the subsequent sda5-7.

Hi Roger, no worries -- after you have done this a few times, it gets easier.

> **swazzler said:**
> If I understand correctly, when I told the installer to use the Gutsy partition for the Hardy install, it broke off only 4.43 GiB, sda4, from which it subdivided 5-7, as logical partitions, to install Hardy, right?

Probably.  ?? I do not know enough about the installer to say for certain how "automagical" it is.

> **swazzler said:**
> Am I correct in understanding that you suggest I should reinstall Hardy (after deleting the non-windows partitions), rather than trying to shift the diskspace to the existing Hardy partition (sda6)?

That's my feeling, yes. It is my thought that goring or shrinking partitions is ok for one area, but this would be moving across 2 partitions? 

> **swazzler said:**
> Also, when I delete the partitions, which option would be better: leaving the 55-odd GiB as free space or allocating them to the windows partition? When I first installed Gutsy it was all part of the windows partition, but I think I remember seeing an option in the Hardy install for using free space instead of dividing the existing partition, though I can't remember for sure.

Yes, leave the 55GiB as free space.

> **swazzler said:**
> I'm thinking about deleting the unix partitions with my GParted cd, then loading the Hardy cd to do the re-install. Will deleting Hardy do a number on my grub, considering that various versions of Hardy are listed  before windows, or will everything be fine?

That sounds like a great plan. And when the installer reconfigures grub, it should show windows and hardy. Further once done, you can manipulate grub to change the order or show more or less entries.

> **swazzler said:**
> as ever, thanks so much for your assistance!
Roger

You're very welcome!  :-)

---

