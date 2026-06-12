---
title: "Thank you Ubuntu 7.10"
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by thaumielx72 on 2008-01-27
Short version:

I am running a 64 bit Sun Java application under Ubuntu 7.10.  It's running at 250% (!!!) of the speed it runs on the same machine using 32 bits.




Long version:

I lost my venerable (class of 2003 - HP Media Center m370n) PC a few months back.  I had been running a distributed computing project on it for about 10 or 11 months.  It would shut down regularly due to overheating the core.  I loaded RightMark and Speedfan on it and had it throttling back almost constantly just so it would keep running.  I had to leave my air conditioner on while I was at work during the summer months or it would be sure to be powered off when I came home.

Then one day I came home and found it had powered off again.  All attempts to power back up failed so I opened up the case and the heat sink fell out.

Well.

When I got my new loan I figured ''I'm not going through that again!."    I bought TWO computers this time: a desktop system and a laptop.  I figured the laptop would make the perfect little alternative unit to run my cherished DC project on.  It's an AMD64 with Cool 'n Quiet.  While it wont throttle back the CPU if it wants to run at 100% for days at a time it does switch from one cpu to the other so it manages to keep  the core under 60C even if it runs non-stop.

Excellent, thought I.  Then I began to read about 64 bit computers and noticed that they were often criticized for being no better than 32 bit machines unless you were running video creating programs, huge databases, or Certain Scientific Applications.

Since my Distributed Computing project was on of those  scientific applications; taking a small amount of input data and performing uber calculations on it; I decided to try AMD64 Linux to see if there was any noticeable improvement in speed.

Gentoo looked promising but absolutely refused to install on my laptop.  I read up on Google and figured they're going through some turmoil right now so I might wanna let them alone to solve their problems.

openSUSE was slick and a breeze for a Linux n00b to use - but it would regularly trash the Windows Vista partition.  (being a realist I figured I better keep M$ around - I'm unlikely to use all 120G of disk space for pretty much one application)

Debian, which had always served me well in the past when I needed to get away from Winduhs, also showed a new and alarming instability.

But I kept coming back to Ubuntu and it looks like I'm here to stay.  Not only does it install under Vista seamlessly it appears to have a serious 64 bit user community.

It was a bit of a chore to get Sun Java's AMD64 JRE  running on it at first but then I stumbled upon a Google post where an Ubuntu user said "just delete /usr/bin/java" and it has been smooth sailing ever since.

Sun doesn't even mention Ubuntu as one of the OS's that will support 64 bit Java applications but it is running right now as I type this.  A moderator from Sun's forum gave me some grief over claiming 64 bits was over twice, but not quite 3 times as fast - but I kid you not: it really is.

I suppose the essence of my thread is this:  If you remember the 80's and the heated debate over whether 'computer hobbyists' would ever have any use for 32 bit chips (the 386) - and the world dominance of that architecture right now -  then sit tight.  In 10 years everyone will be using 64 bits and wondering why it took so long to make such a huge improvement.

Long live Ubuntu.  I now feel that I have really arrived into the 21st Century.

:guitar:

---

### Post by prince_niceguy on 2008-01-27
yup... 64bit rocks... i use eclipse (a java application) and it works extremely fast compared to 32 bit OS... 

and of course ubuntu rocks... i have been using it from 2005 and i am keeping it for long time...

---

### Post by ghost_ryder35 on 2008-01-27
glad to hear your here to stay :)  Ubuntu is a great distro with an over whelming support forum of linux gurus.  If you ever have a problem, this is definetly the place to get it solved.

---

### Post by thaumielx72 on 2008-01-27
> **prince_niceguy said:**
> yup... 64bit rocks... i use eclipse (a java application) and it works extremely fast compared to 32 bit OS... 

and of course ubuntu rocks... i have been using it from 2005 and i am keeping it for long time...

Interesting...

I have been thinking about tackling their source code but so far they haven't made it public.  I guess I can't blame them.

If they do release it I suppose I'll take a look at Eclipse.  

Yeah, I can't see changing over to another distro since Ubuntu is doing the job right now.  I guess this means I'm gonna be reading a lot more about it as I get more up to speed.  Any suggestions as to where the Ubuntu fans hang out?  Other than here, of course.

---

### Post by thaumielx72 on 2008-01-27
> **ghost_ryder35 said:**
> glad to hear your here to stay :)  Ubuntu is a great distro with an over whelming support forum of linux gurus.  If you ever have a problem, this is definetly the place to get it solved.

lol  :lolflag:

I should have read your post before responding to prince_niceguy.  Anyway: do *you* have any recommendations where an Ubuntu n00b should go to study more about the ins and outs of this excellent OS?

---

### Post by jjthomas on 2008-01-27
I'm still in Distro Turmoil.  I would like to get something going with at least Java and Flash.  I can't seem to get it to work on either Ubuntu 64 bit or 32 bit (Ubuntu Studio).  I have a P-III that I cannot get GRUB to install correctly on.  I know why, but I can't seem to get it to install on the correct drive.  It installs on the wrong hard drive.  Old problem, the driver order switches when I boot, I just need to get into the grub file and get it to set correctly *sigh*

So far I've tried 
Mandrivia - has problems with NTFS-3g,
FreeBSD - multiple drive read errors, (Confirmed FreeBSD problem)
SuSE - Bricks the box
Fedora Core - won't survive the post install boot
Slackware, installs flawlessly, but doesn't do everything I need. *sigh*

Ubuntu I have gotten the furthest with, but the no Java and no Flash is really driving me up the wall.  So bad that I dug out my Windows disk.
[/whine]

-JJ

---

### Post by thaumielx72 on 2008-01-27
> **jjthomas said:**
> I'm still in Distro Turmoil.  I would like to get something going with at least Java and Flash.  I can't seem to get it to work on either Ubuntu 64 bit or 32 bit (Ubuntu Studio).  I have a P-III that I cannot get GRUB to install correctly on.  I know why, but I can't seem to get it to install on the correct drive.  It installs on the wrong hard drive.  Old problem, the driver order switches when I boot, I just need to get into the grub file and get it to set correctly *sigh*

So far I've tried 
Mandrivia - has problems with NTFS-3g,
FreeBS - multiple drive read errors, (Confirmed FreeBSD problem)
SuSE - Bricks the box
Fedora Core - won't survive the post install boot
Slackware, installs flawlessly, but doesn't do everything I need. *sigh*

Ubuntu I have gotten the furthest with, but the no Java and no Flash is really driving me up the wall.  So bad that I dug out my Windows disk.
[/whine]

-JJ

Believe me, I understand.   Getting Java to run the first time under Ubuntu took a couple of days.  Did you try deleting /usr/bin/java to get rid of the default Ubuntu GNU Java? With:

sudo rm /usr/bin/java

It really is the first step if you want to work with Sun's (or IBM's) Java.  After that, installing was a breeze.

Well, if you want my advice here it is:  try Debian stable one time.   It's probably the most reliable  Linux out there.  (after Knoppix)

I have seen in my travels through the Google landscape several posts on getting flash running.  Don't give up.  It's worth the extra effort.  Plus the knowledge you pickup along the way will certainly come in handy down the road.  That's the real problem with Winduhs, IMHO.  It makes it too easy even for little kids to get far in computers.  

Linux is definitely here to stay.:popcorn:

---

### Post by incubus on 2008-01-27
> **jjthomas said:**
> I'm still in Distro Turmoil.  I would like to get something going with at least Java and Flash.  I can't seem to get it to work on either Ubuntu 64 bit or 32 bit (Ubuntu Studio).  I have a P-III that I cannot get GRUB to install correctly on.  I know why, but I can't seem to get it to install on the correct drive.  It installs on the wrong hard drive.  Old problem, the driver order switches when I boot, I just need to get into the grub file and get it to set correctly *sigh*

So far I've tried 
Mandrivia - has problems with NTFS-3g,
FreeBS - multiple drive read errors, (Confirmed FreeBSD problem)
SuSE - Bricks the box
Fedora Core - won't survive the post install boot
Slackware, installs flawlessly, but doesn't do everything I need. *sigh*

Ubuntu I have gotten the furthest with, but the no Java and no Flash is really driving me up the wall.  So bad that I dug out my Windows disk.
[/whine]

-JJ

jj,
Did I read it right, you have a Pentium III and you're trying to run Ubuntu 64bit?  I assume it's a different machine.  Regarding the drive changing order when you boot, have you tried putting the drive's jumper to, say, master or slave, but not dependent on the setup?  (this is a random idea, I have no idea if it works)

About flash and java, I'm sure if you ask around people here will try to help.  I'm on Ubuntu 64 bit, and java and flash (32bit) are working flawlessly, so it can be done.  Just tell us where exactly it goes wrong.

incubus

---

### Post by jjthomas on 2008-01-27
> **incubus said:**
> jj,
Did I read it right, you have a Pentium III and you're trying to run Ubuntu 64bit? 

No!  LOL  Two machines.  I'm trying to get 7.10 server installed on the P-III.  The difficulty with it is that I have a 
SCSI drive (/dev/sda) and controller, a 
Promise Ultra 100 controller (/dev/hde /dev/hdg) and the obligatory onboard 
ATA controller (/dev/hda).  
When gurb runs it has the drives as though /dev/hde is the first boot drive and installs itself on that drive.  BIOS boots the SCSI as the first drive and since there is no grub on it, it just errors out.  The struggle I have is getting into grub during the installation so I get it installed on the SCSI drive.  With Slackware (my best friend heading for retirement) I have the option to build the lilo.conf file during the installation and I can get it pointed to the correct drive.  Ubuntu does not give me that option, so I have to install and then boot the rescue disk to get grub pointed to the correct drives.  Part of my difficulty is that I really don't know grub that well (yes I see some education coming my way) so I have to RTFM and get it figured out.  Which I just did, I installed grub on every <censored> ](*,) drive!!!  But I need to clean that up.

The AMD 64 machine is getting 64bit Ubuntu Studio and is where I am having troubles getting Java and Flash to run.  Still reading up on getting that to work.

thaumielx72:  I've tried it from fresh install.  I read some suggestions at  work that I will try when I get some time at home.  I'm going to put my Vista installation disk next to my Ubuntu Studio installation disk and see if that will scare Ubuntu into cooperation.

-JJ

---

### Post by homerhomer on 2008-01-28
This is what I have for Flash and Java


for flash
apt-get install flashplugin-nonfree
it should install some 32bit libs but it works until adobe can pull there head from there ***

and for java add this repo
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
and then 
apt-get install icedtea-java7-plugin
This should work until Sun can catch up with the time and release a 64 bit browser plugin

---

### Post by jjthomas on 2008-01-28
Do you have sound with your Flash?  I'll try this when I get home.

Thanks.-JJ

---

### Post by Jouke74 on 2008-01-28
> **jjthomas said:**
> No!  LOL  Two machines.  I'm trying to get 7.10 server installed on the P-III.  The difficulty with it is that I have a 
SCSI drive (/dev/sda) and controller, a 
Promise Ultra 100 controller (/dev/hde /dev/hdg) and the obligatory onboard 
ATA controller (/dev/hda).  
When gurb runs it has the drives as though /dev/hde is the first boot drive and installs itself on that drive.  BIOS boots the SCSI as the first drive and since there is no grub on it, it just errors out.  The struggle I have is getting into grub during the installation so I get it installed on the SCSI drive.  With Slackware (my best friend heading for retirement) I have the option to build the lilo.conf file during the installation and I can get it pointed to the correct drive.  Ubuntu does not give me that option, so I have to install and then boot the rescue disk to get grub pointed to the correct drives.  Part of my difficulty is that I really don't know grub that well (yes I see some education coming my way) so I have to RTFM and get it figured out.  Which I just did, I installed grub on every <censored> ](*,) drive!!!  But I need to clean that up.
-JJ

Yup you need to clean up your Master Boot Records of all disks, as there is probably still old installs around. Second, thry to change the boot order from your harddrives in your BIOS if you haven't done so already. This could save lot's of problems as you can simply make the BIOS match the OS order. Otherwise, and maybe also, make a plan beforehand from which drive (and de/sd*/) you are going to start. Then use the Ubuntu Alternate CD to install. During partitioning make note on which drive is which. Then when installing grub say "no" to install Grub to MBR of HDD0. Afterwards an option will appear where to install grub instead, select /dev/<whatever you want> here.

---

### Post by jjthomas on 2008-01-31
I used dd to wipe out all the disks.  The P3 is going to be a Mandrivia computer, I ran into to many brick walls tying to get ubuntu installed on it.

My AMD machine has UbuntuStudio coexisting with XP64 and it will remain that way. :)

I did get icedtea installed, But it does not work work when I access a particular module at my employers website.

I have not tried to install flash, as of yet.

-JJ

---

