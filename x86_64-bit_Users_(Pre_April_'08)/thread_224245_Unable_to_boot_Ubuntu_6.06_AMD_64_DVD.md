---
title: "Unable to boot Ubuntu 6.06 AMD 64 DVD"
date: 2006-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ntgooroo on 2006-07-27
I cannot seem to install the Ubuntu 6.06 AMD 64 DVD on my AMD Sempron 64 3000+.

I have the following hardare:

AMD Sempron 64 3000+
ASRock AM2NF4G-SATA2 (nForce 410 chipset)
Onboard Nvidia 6100 video card (shared memory)
Seagate SATA1 ST3200822AS
1 GB DDR2 Dual Channel RAM
Sony DW-Q30A DL DVD Writer


The DVD boots.  It gives the main menu.  But it doesn't matter which option I choose: Start or Install Ubuntu, Start Ubuntu in Safe Graphics Mode, or Install in Text Mode, it will not Start or install.

Here is what happens when I choose one of the install options:

Starting, loading Linux Kernal
Decompressing kernal
Booting Kernal....

Then it hangs.

I know there are no defects on the DVD because it runs in VMware under Windows XP just fine.

---

### Post by ntgooroo on 2006-07-27
I updated my BIOS on my ASRock AM2NF4G-SATA2 motherboard to v1.20 and this helped.

I can now start the "Start Ubuntu or Install" menu option with 1280 x 1024 resolution.

However, it now hangs at "Configuring some drivers..."

I assume this means there is more about my hardware that it doesn't like.  From what I have read so far, it may be the SATA, USB, or the onboard NVIDIA 6100.

I will keep hacking away at it.

Man, you really get spoiled with Windows XP and all the 3rd party apps and drivers that generally work with out hassle.  You have to really want to run Linux to put up with all this trouble.  I guess I really want to.

---

### Post by ntgooroo on 2006-07-27
I disabled every thing I could in BIOS (USB, HD Audio, CPU features, etc.).  The only thing I cannot disable is onboard video as I have no other video card I can try.  Nothing seemed to help.  It still hangs at "Configuring some drivers...."

However, I ran setup in text mode and it told me it had an error reading some files and this means the DVD is probably damaged.  So, I ran an integrity check and it showed that some directories were invalid.

Things are starting to make sense now.  

Crete, Greece is a rather dusty place.  It doesn't rain here from April - September.  I have only had this PC for two weeks and the screen in the front of the case and the CPU fan are already gathering dust.  It is noticable enough that I can wipe off the dust from the front screen with my hand.

My Sony DVD drive is about 7 months old.  Thus, the problem may be that the head on my Sony DVD drive is simply dirty.  I had an MS Office 2003 CD just the other day that this same Sony DVD drive would not read in Windows XP due to errors, but my other PC with a brand new Lite-On DVD drive read the same CD with no problems.

I will switch the Sony DVD drive with the new Lite-On DVD drive from the other PC and see what happens.

I will update later after I have tested it.

---

### Post by Yasumoto on 2006-07-27
You could try downloading the .iso file online and burning it onto a new disc. Although this might not solve the problem, if there's an error with the DVD, this would be the way to fix it.

---

### Post by ntgooroo on 2006-07-29
I changed the Sondy DVD drive with the Lite-on and it still hangs at the same message, "Configuring some drivers....."

Now I will try burning a new DVD.  But it is strange that VMWare can run the DVD and get up to the desktop with not problem using the same PC with the same Sony DVD drive.

---

### Post by ntgooroo on 2006-07-30
I burned a new DVD with the same old AMD 64 image I had before but this time with the Lite-On DVD drive.  Same problem.  The install hangs at "Configuring some drivers..."

I downloaded a new AMD 64 CD-ROM image and burned it to a CD-R on the Lite-On DVD drive.  Same problem.  The install hangs at "Configuring some drivers..."

I disabled every feature I could think of in CMOS (USB, CPU features, etc.).  The install hung at "Adding video driver...".  After a reboot, I tried again and it went past Configuring some drivers.... but had several failed messages"

Kernel Event Manager FAILED
Enterprise Volume Manager FAILED
And two logs, can't remember which ones.
Then it starting scrolling some error message vertically down the screen.

I think it is now safe to say that there is something about my hardware configuration (see first post) that Ubuntu 6.06 AMD 64 does not like.
  
Any suggestions?

---

### Post by drn8 on 2006-08-01
I suggest SUSE. Ubuntu 64 does not seem to be quite ready yet. So far the standard answer I've seen here for install issues has been "check the md5 on your iso, verify the cd". I have a hunch that as soon as you try SUSE you will have a working 64-bit linux system you can learn from. If your internet connection is quick enough you can just download the net install image and install over the internet, that way you dont have to wait for a dvd download to find out if it will work.

---

### Post by Kilz on 2006-08-01
> **drn8 said:**
> I suggest SUSE. Ubuntu 64 does not seem to be quite ready yet. So far the standard answer I've seen here for install issues has been "check the md5 on your iso, verify the cd". I have a hunch that as soon as you try SUSE you will have a working 64-bit linux system you can learn from. If your internet connection is quick enough you can just download the net install image and install over the internet, that way you dont have to wait for a dvd download to find out if it will work.

SuSE 10.1 must have done a lot of work for someone to recommend it. I left Open Suse because 10.1 was a useless piece of !@#$%!@#$% with so many problems it was impossible to use

---

### Post by ntgooroo on 2006-08-01
And I dumped SUSE because it did not have an 3D accelerated driver for my ATI Rage Mobility P/M in Compaq Armada M700, which made Gnome and KDE move slowly.  And it was too freaking hard and poorly documented as to how to get any other MESA or DRI acceleration working.  I also dumped SUSE because it did not have a driver for my USR 8514 PCMCIA card.  Yet ArkLinux worked with it immediately after installing.

We are getting off topic here.

Does anyone know how to what is causing my problem with installing Ubuntu 6.06 for AMD 64 on my new PC (see top of thread) and how I can solve this problem?

---

### Post by kanenas on 2006-08-02
there seems to be a command that if is added on the f6 option
it helps and eventually the ubuntu x86 and amd64 boots
on socket am2 motherboars

press f6 and add the command "noapic" at the begining of the
line of all the commands
(amd 3800 x2, asus m2n sli)

---

### Post by drn8 on 2006-08-02
> **Kilz said:**
> SuSE 10.1 must have done a lot of work for someone to recommend it. I left Open Suse because 10.1 was a useless piece of !@#$%!@#$% with so many problems it was impossible to use

The last SuSe I used was 10.0, and it was smooth as shit. Considering the dumb issues all the *64 binary distros I have tried seem to have(with my desktop) I think I may just go the source/gentoo/LFS route for my next distro; it takes longer to install but in the end it's much quicker due to the lack of mis-compiled binaries, annoying support, and general troubleshooting involved with the current state of binary *64 distros. I'll take 6 hours at the beginning of an instalation to avoid 12 hours of troubleshooting later any day.

---

### Post by Yyrkoon on 2006-08-05
I had the same issues with this board, but with windows XP pro. However, I believe this to be a BIOS / SATA controller issue. 

What worked for me, was to pull the SATA cables from the drive, and install to a IDE drive instead, the OS then installed, and ran fine. Once I installed the SATA drivers from CD, I then reconnected the SATA drive, and it was emmediately recconized.

It was very frustrating, and even though I've been building PCs since the early 90's, I had to remember a post (from somewhere) about another user experiencing problems with installing to a SATA drive (same platform, different motherboard IIRC).

Hope this helps.

[EDIT]

Just incase I wasnt clear, what worked for me was NOT having a SATA drive connected at_all, go into the BIOS, set the IDE HDD as first boot option, optical drive second, and press F11 at boot, seleting the optical drive.

A couple of other things to note: 

1) if you're using DDR2 800 memory, you'll have to set it manually in the BIOS (board defaults to DDR2 533

2) if you're not using a Sempron CPU, BIOS defaults FSB / HTT to 800/1600, set manually to 1000 FSB, 2000 HTT.

---

### Post by LinuxConvertJune2006 on 2006-08-05
> **ntgooroo said:**
> I updated my BIOS on my ASRock AM2NF4G-SATA2 motherboard to v1.20 and this helped.

I can now start the "Start Ubuntu or Install" menu option with 1280 x 1024 resolution.

However, it now hangs at "Configuring some drivers..."

I assume this means there is more about my hardware that it doesn't like.  From what I have read so far, it may be the SATA, USB, or the onboard NVIDIA 6100.

I will keep hacking away at it.

Man, you really get spoiled with Windows XP and all the 3rd party apps and drivers that generally work with out hassle.  You have to really want to run Linux to put up with all this trouble.  I guess I really want to.


Just an FYI, the reason I started using Ubuntu is because Windows XP wouldn't recognize my SATA drive without a floppy (floppy?!?) and my video card wouldn't work properly until I downloaded newest drivers, and I had to download a 200mb files from HP to get my printer to print! No thanks, Ubuntu did all three out of the box.

Windows isn't great at all, you're just used to dealing with that non-sense, I really blew up when I found out it wanted me to install a floppy drive to get a hard disk controller installed, ridiculous!

---

### Post by Kilz on 2006-08-05
> **drn8 said:**
> The last SuSe I used was 10.0, and it was smooth as shit. Considering the dumb issues all the *64 binary distros I have tried seem to have(with my desktop) I think I may just go the source/gentoo/LFS route for my next distro; it takes longer to install but in the end it's much quicker due to the lack of mis-compiled binaries, annoying support, and general troubleshooting involved with the current state of binary *64 distros. I'll take 6 hours at the beginning of an instalation to avoid 12 hours of troubleshooting later any day.

I will agree, 10.0 was a good version. Most of my issues were with 10.1. When I coundnt get help with issues I couldnt fix myself I left it and found Ubuntu.

---

### Post by Yyrkoon on 2006-08-05
> **LinuxConvertJune2006 said:**
> Just an FYI, the reason I started using Ubuntu is because Windows XP wouldn't recognize my SATA drive without a floppy (floppy?!?) and my video card wouldn't work properly until I downloaded newest drivers, and I had to download a 200mb files from HP to get my printer to print! No thanks, Ubuntu did all three out of the box.

Windows isn't great at all, you're just used to dealing with that non-sense, I really blew up when I found out it wanted me to install a floppy drive to get a hard disk controller installed, ridiculous!

Or you could have learned how to slipstream, and either slipstream the drivers into the ISO, or used a SP 2 disk . . .

Any OS is only as good as that thing that sits between the chair, and keyboard . . .

---

### Post by LinuxConvertJune2006 on 2006-08-06
> **Yyrkoon said:**
> Or you could have learned how to slipstream, and either slipstream the drivers into the ISO, or used a SP 2 disk . . .

Any OS is only as good as that thing that sits between the chair, and keyboard . . .

A few things, the hard drive was dead (Windows wouldn't boot any longer) so I couldn't slipstream my XP SP1 ISO image. I bought a SATA drive to replace my dead PATA drive. And I bought XP Pro before SP2 was out so you are correct, I would need to slipstream it. Except one issue, how do I boot to do this unless I install linux first or some other OS ? I couldn't of course, so I tried 32bit Ubuntu, then decided to test it. I was hooked.

I called MS also, before trying Ubuntu, and they wanted me to purchase another disc XP Pro SP2 disc. No thanks. Also, isn't Windows "so easy" that this wouldn't be neccesary ? That was the original argument I was referring to in the first thread , if you care to read it.

In addition, neither resolves the automatic detetion and usage of my HP printer nor my video card. Two things that people complain about a lot regarding linux, but also occur on Windows.

Next ? ;)

---

### Post by Yyrkoon on 2006-08-06
> **LinuxConvertJune2006 said:**
> A few things, the hard drive was dead (Windows wouldn't boot any longer) so I couldn't slipstream my XP SP1 ISO image. I bought a SATA drive to replace my dead PATA drive. And I bought XP Pro before SP2 was out so you are correct, I would need to slipstream it. Except one issue, how do I boot to do this unless I install linux first or some other OS ? I couldn't of course, so I tried 32bit Ubuntu, then decided to test it. I was hooked.

I called MS also, before trying Ubuntu, and they wanted me to purchase another disc XP Pro SP2 disc. No thanks. Also, isn't Windows "so easy" that this wouldn't be neccesary ? That was the original argument I was referring to in the first thread , if you care to read it.

In addition, neither resolves the automatic detetion and usage of my HP printer nor my video card. Two things that people complain about a lot regarding linux, but also occur on Windows.

Next ? ;)

You slipstream the drivers into the disk . . .no need for SP2 IF you have the drivers slipstreamed . . . atleast where the SATA drive is concerned. As for the 'easy' statement, SATA wasnt around when XP was first released, and its kind of hard for them to include it with your CD, if you've had it previous to the hardware being availible. You have to do the same thing with Linux, except, instead of having to buy it, you download a ISO.

Seriously, whats the difference, you download a program called nLite, you download your SATA drivers, unzip them or whatever you use, you run the program, locate your WinXP CD, Locate your SATA drivers, have nLite work its majic, and burn the CD. Not difficult at all, and less time consuming. Of course, you NEED to learn how to do all this before you can do it well . . .

---

### Post by Yyrkoon on 2006-08-06
Anyhow, for this given situation, its a moot point, his issue is the same as the problem I had, which seems to be a BIOS / controller issue, and I see no mention of it on Asrocks BIOS update page.

---

### Post by LinuxConvertJune2006 on 2006-08-06
> **Yyrkoon said:**
> You slipstream the drivers into the disk . . .no need for SP2 IF you have the drivers slipstreamed . . . atleast where the SATA drive is concerned. As for the 'easy' statement, SATA wasnt around when XP was first released, and its kind of hard for them to include it with your CD, if you've had it previous to the hardware being availible. You have to do the same thing with Linux, except, instead of having to buy it, you download a ISO.

Seriously, whats the difference, you download a program called nLite, you download your SATA drivers, unzip them or whatever you use, you run the program, locate your WinXP CD, Locate your SATA drivers, have nLite work its majic, and burn the CD. Not difficult at all, and less time consuming. Of course, you NEED to learn how to do all this before you can do it well . . .

If you can't boot, you can't slipstream. Read my post it explains all. Now if I had it done earlier....yeah then maybe, good thing I ddn't.

---

### Post by Yyrkoon on 2006-08-17
Well, to the OP, if you havent fixed the problem yet, this motherboard NEEDS SATA Operation mode set to [RAID], vs [non-RAID]. If set to [non-RAID], the SATA drive connected will actually be operating in IDE mode, as per AsrockAmerica technical support.

You can read more bout the issue at this link [http://forum.abit-usa.com/showthread.php?p=746803#post746803]("http://forum.abit-usa.com/showthread.php?p=746803#post746803")

Or this link [http://forumz.tomshardware.com/hardware/modules.php?name=Forums&file=viewtopic&p=1208295#1208295]("http://forumz.tomshardware.com/hardware/modules.php?name=Forums&file=viewtopic&p=1208295#1208295")

---

### Post by ntgooroo on 2006-08-18
I finally got Ubuntu 6.06.1 to boot and install!!!

Here is how:

1.) It is possible that a bios update was all I ever really needed.  However, I had tried that before and it wasn't enough.  So, I updated my BIOS again to ensure it was the latest one.  Maybe it reverted at some point back to the previous version and I didn't notice.

2.) I obtained the latest version of Ubuntu, v6.06.1 for AMD64.  I already had it and installation was failing with it, but after I updated my bios and did step 3 below, every thing worked.

3.) added the following agrguments to the front of the F6 line:
noapic ide=nodma.  I had done this before and it failed.  It wasn't until I updated my bios that it worked this time.

Yeah!!!!!

---

### Post by checkup on 2006-08-21
i took the way over an debian amd64 installation and a tricky way up "upgrading" to edgy eft. It is possible!! It's even cleanly possible! But you have to work with versions and distributions in dpkg. In about 1-2 hours i had a clean ubuntu edgy eft with amd64 smp. 

Mainboard asrock-am2 with athlon 64 x2

---

### Post by ntgooroo on 2006-09-03
Here is the actual fix to my prolem.

After struggling for a long time to get Ubuntu 6.0.6.1 for AMD64 installed, I still had strange problems in my Windows XP partition.  It would tell me that it had to restore a copy of the registry from backup, Firefox would randomly become corrupt and I would have to re-install it, multiply RAR files would some times un-rar just fine, other times WinRAR would say that one of the files had a bad password, which was incorrect.

So, I finally booted from the Ubuntu 6.0.6.1 AMD64 CD and ran the memory test.  Voila!  I had bad RAM.

So, bad memory was my problem all along.  Now that the memory has been replaced, every thing is working fine in Windows XP and in Ubuntu 6.0.6.1 AMD64.

---

