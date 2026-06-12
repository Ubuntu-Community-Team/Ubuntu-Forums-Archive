---
title: "Trying to install Linux on a G3 B&amp;W"
date: 2006-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by andre-w on 2006-01-08
Fellow Linux users,

My brother gave me his old G3, on which I decided to experiment installing and running a PPC Linux distribution. My troubles began when I tried to boot the installation disc... the moment it starts to read the CD, the display goes blank and nothing happens... and yes, I am holding C.

I am not, by any means, an expert on the PPC Linux subject, but I have been using PCs (Windows and Linux) and Macs (Classic and OS X) for a quite while, and successfully troubleshooting problems with some research on internet. Unfortunately I did not find any information on my specific circumstances. I hope this forum will bring some light on my situation.

Here is my Mac:

A 400MHz G3 Blue & White (Yosemite), 640MB RAM, 10GB Maxtor disk, DVD-ROM (from a G4 Graphite), 100MB ZIP drive, CPU type is PowerPC 750 (82.1), and boot ROM version is f4, according to System Profiler. Also a Sonata SD Macintosh PCI card, and a 15" Compaq TFT5000 LCD.

Here is what I already did:

I borrowed the Mac OS X 10.3 Panther installation discs to make sure my G3 was OK. It is! Panther is installed and running well. But coming back to Linux, the weird behavior remains.

I tried a original Ubuntu 5.10 'The Breezy Badger' for Mac. Note: on the Ubuntu CD sleeve, it is written "This Mac Edition will run on modern G3, G4 and G5 computers, including iBooks and Powerbooks".

In addition, I tried a working 19" Sony SDM-HS95 TFT LCD monitor, however it too did not respond. It says "No input signal Go to power safe". By the way, the Compaq would say "Going to sleep".

Next week, I will try to borrow a CRT - either a PC VGA or an Apple DB-15 - in order to do more tests and narrow the possibilities. Meanwhile I will also wait for someone to post some suggestions. Any help will be appreciated!

I am still not sure about the source of my difficulties, neither what is occurring when the screen turns off.

Thanks in advance,

Andre W.

---

### Post by andre-w on 2006-01-08
Hello again!

I came to believe that my video card - a Sonata SD - is not supported by any Linux distribution. I assume this is what is causing my problems, and I will try to replace it for a "Mac-Linux" compatible.

Andre W.

---

### Post by gconn77 on 2006-01-09
Hey there... last month I was pretty much in the same situation. I bought a G3 B&W from my uncle to give to my daughter for Christmas.

Please [follow this link]("http://ubuntuforums.org/search.php?searchid=3301738") to the search results page of topics that I have created. View them because they pertain to the situation you are in, or atleast similiar. I think the posts that I created last month should help you quite a bit. Just be sure to read them, take your time and actually read the questions I asked, and the responses I got back from the Community. Most important advise I can give you is to be relaxed and patient when you run into any snags with installing linux. The process can take a few days... at times. Especially when you are in a situation that you don't know how to correct.

At anyrate, view my [previous posts]("http://ubuntuforums.org/search.php?searchid=3301738")... and reply with any questions in this thread. I will subscribe to it, so that I can receive the reply notification via email.

---

### Post by andre-w on 2006-01-11
Hello gconn77,

Thanks for your interest and information. Sorry for not answering sooner.

I did read some of your threads, "Trouble Installing Ubuntu 5.10 on a Mac G3", "Loading Second Stage Bootstrap" and "Partition Apple G3 B&W Hard Drive For Ubuntu Only", and I did learn new details about installation while looking the postings. Indeed we both have problems trying to install Ubuntu on ours G3 B&W, and will not give up easily. By the way, I also have Ubuntu installed on my PC, and it is running quite well.

Well, I am afraid I was not very clear about my case. I was able to install and run Mac OS X on my G3 B&W, but not Ubuntu... I am really willing to install Ubuntu on my G3, and like you I do not intend to install more than one OS on my disk. For instance, when I tried a not formatted disk, the screen displays a folder with a MacOS face and a question mark alternating, but when I put the Ubuntu Installation CD, at the very moment it starts to read, the monitor looses signal. The same happens when I try the Ubuntu Live CD, or the disk that has the Mac OS installed.

First I thought my misfortune was caused by either a G3 B&W / Linux incompatibility, or a limited monitor. I was thinking it might have something to do with the text-mode linux installation. Now I suppose my Sonata SD video card is not supported by Linux distributions. I did find some information (not much useful for my case though) on the Sonnet website: [http://www.sonnettech.com/product/sonata_sd.html](http://www.sonnettech.com/product/sonata_sd.html)

I do have Mac OS 10.3 running perfectly on my G3, and opening the System Profile, the 'PCI/AGP Cards' option shows me "Card: VTXP jjbabacd; Type: Display; Bus: PCI; Slot: J12." I guess it is my video card... it is the only card I have installed! Opening the G3 and looking inside, I see my Sonata SD for Macintosh video card installed on the monitor card slot (slot 1). It does have a sticker where I can read "3460 99P-22 16MB 0437".

Assuming replacing the video card is the solution for my problem, I will try to borrow a "Mac-Linux" compatible video card for testings, and proceed with my plans. I was suggested to try a Radeon Mac Edition video card.

I also notice one of the postings in your threads considers reseting (or "zapping") the PRAM, but I still do not know for sure what it is about. Doing some research, I did study forums concerning the Apple open-firmware, and I think it either has something to do with the PRAM, or is the same. I am aware that the firmware in some Macs has to be updated in order to install newer versions of Mac OS, so I am not certain that the firmware version may influence too on a Linux installation...

Anyway, it may take some work, but I will keep the trial-and-error until I go a step forward on my installation. I will write more after I have some success.

Best regards,

Andre W.

---

### Post by andre-w on 2006-01-15
Well... The good news is... my video card was replaced and my monitor now works all the time! The bad news is... my monitor shows an error as the Ubuntu Installation CD is booting!

I was unable to try a Radeon Mac Edition video card, as I was suggested, but I tried two slightly different 16MB ATi rage 128 GL (AMC ver. 2.0 PN 109-57400-00) PCI video cards from other B&W G3's. One has an Apple expansion on it.

So I tested both video adaptors running the Mac OS X already installed on my G3, and it works all right. But when it comes to Linux, I tried my original Ubuntu Installation CD, but an "error" message is shown.

While my G3 is booting, first the screen briefly shows an icon with a Mac OS smile and a question mark alternating, and just after this, when the CD begins to spin, some texts (that I don't have enough time to read) appear on a light gray background with a repeating line (except for the SRR0 address) where it reads:

DEFAULT CATCH!, code=300 at  %SRR0: ff______  %SRR1: 0000b030

I have absolutely no idea on what is up now, and any help will be very much appreciated.

Andre W.

---

### Post by ssam on 2006-01-16
you should not see the Mac OS smile and a question mark alternating if it is booting the ubuntu cd. i suspect that that is failing and it is falling back to booting from the hard drive.

could you try holding down [alt] at boot. it should give you a choice of all the bootable disks it can see.

its also possibible that the cd is damage or faulty. would it be possible do download and burn another copy, or try the cd in another mac.

perhaps restting the PRAM might help.

---

### Post by andre-w on 2006-01-16
Hello ssam,

Thanks for the reply! It makes sense... before that, I did not know about this little detail. Now, taking this into account, I think I failed to mention a small workaround I have done in order to try to boot my original Ubuntu for Mac Installation or Live CDs, that may or may not have something to do with my case.

First, while running the Mac OS 10.3 on my B&W G3, when I insert the Installation or Live CD, I notice the CD is not displayed as an option in the Startup Disk (System Preferences) utility application, although it is shown on my Desktop and I can browse it. However the Mac OS installation CD is displayed in the Startup Disk, thus I can select and restart my G3 on it.

If I wish to boot the Ubuntu CD, I have to either put a Mac OS installation CD, select it as a startup disk and quickly replace it for the Ubuntu Installation/Live CD when restarting, or use an unformatted hard disk (the Mac OS installation CDs would work on an unformatted disk) instead of my hard disk with Mac OS already installed. If I use the Ubuntu CDs, it does not matter if do or do not hold [C] or [alt] key while booting, either way I will see the MacOS face and the question mark alternating, so... according to what we now know, I presume my G3 may not be booting from the CD.

Just in case, I will test my Ubuntu for Mac Installation and Live CDs in another Mac, as soon as I have a chance, even though I do not believe my CDs are damaged.

Lastly, I have a question about the PRAM... What is and how do I reset the PRAM, and what does it imply? And are the PRAM and the Apple OpenFirmware the same?

Best regards,

Andre W.

---

### Post by Rxke on 2006-01-17
Hi Andre_w,

I'm the guy everybody hates because running/installing Ubuntu on my B&W works flawlessly ;)

Your workaround might be the cause of your problems... You really should try booting up holding the 'c' key... I initially had to try several times with a less than optimally burned disk in the past...
Or it might be the videocard... I still have the original RAGE128, I guess there probably are not too many drivers for other cards for the PPC than the 'standard' ones...
and... Ack, that darned "DEFAULT CATCH!"... it can mean anything, sigh. 

Resetting PRAM: [http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

---

### Post by andre-w on 2006-01-18
Hello again,

After lots of study, tests, and some progress, let me summarize my current situation:

I zapped the PRAM, so instead of a kernel panic (DEFAULT CATCH!), Mac OS 10.3 (already installed) starts up properly when I boot my G3. :)

My Ubuntu CDs are OK... I checked them, and even tried my Ubuntu Live CD on my Mac mini. :)

My G3 no longer has the original CD-ROM, it does have however an original Apple DVD-ROM from a G4 Graphite, and it is working fine since I can play CDs or DVDs with it. :)

If I insert a Mac OS X Installation CD, restart my G3 and hold the [C] key, it will boot from the CD as expected. :)

If I insert the Ubuntu Installation or Live CD, restart and hold [C] (or [alt]) key, it will ignore the CD and boot from the Mac OS installed on the hard disk. :(

I am using an Apple ADB keyboard on my G3, however I also tried an Apple USB keyboard from my Mac mini, but [C] and [alt] keys still have no effect on booting. :(

Now, it looks like my Ubuntu CDs are good but not "bootable" on my G3 only. :(

Any ideas on why I can't boot my Ubuntu CDs with my B&W G3? I will greatly appreciate any suggestions.

Andre W.

---

### Post by linear on 2006-01-19
You may be able to force the CD to boot with this incantation (from an Apple support article):

([http://docs.info.apple.com/article.html?artnum=25793](http://docs.info.apple.com/article.html?artnum=25793))

> Restart the computer and hold these keys: Command-Option-O-F . This asks the computer to start in Open Firmware.
Tip: If you don't start in Open Firmware, try again. Make sure you're using a USB keyboard, and that the keyboard is connected directly to one of the computer's USB ports.
type: **boot cd:,\\:tbxi**
Press Return.

---

### Post by Rxke on 2006-01-23
Great to hear you were successful!

[QUOTE=andre-w]I intend to visit this forum more often, not only because of future questions that I might have, but also for I believe I may contribute on other people's troubleshooting.
[/QUOTE]

 :D Spoken in the true Ubuntu spirit!

No matter how much or how little you think you know, when you browse the boards, you'll see there's  almost always someone with a problem you know the solution to. 

(Offtopic: Heh, I use the old ADB keyboard too, that's the nice thing about these 'new' G3's: the ADB port.... Those minikeyboards it came with, after awhile they feel really cramped, don't they?)


(EDIT: huh??? How come my post, despite being an answer to andre_w, shows up *before* his post????)

---

### Post by andre-w on 2006-01-23
My B&W G3 is running Ubuntu ! ! !

Thanks for all your suggestions... I really appreciated! I studied almost all the information I was given and I learned a lot about my G3 and Linux installation features.

What I did to successfully install Ubuntu on my G3 was a bit... odd. Instead of my B&W G3, I used another one of the exactly same model! So, my brother, who gave me the original B&W, had an additional B&W with everything original except for upgraded memory and hard drive. Knowing about my case, and since his other G3 was being used for experiments only, we agreed to exchange the G3s and give it a try. Well, we guessed right. Now I have a B&W (the new one) running Ubuntu 5.10 and my brother has one (the old one) running Mac OS 10.3.

About my "new" B&W: So far, for testing purposes I did a provisory installation of Ubuntu 5.10. Just for the record. I also tried my Sonata SD video card but unfortunately it didn't work under Ubuntu, so I put the original ATi rage video card back.

About my "old" B&W: I tried all the tips I was recommended... none worked.  I tried holding [C] or [alt] keys, I tried 'boot cd:,\\:tbxi' and 'boot cd:\\yaboot' too but nothing I expected happened... I did many other tricks, but to make a long story short, I could boot from my Mac OS X Installation CDs, but not from my Ubuntu Installation and Live CDs. I wonder what was wrong... maybe my DVD-ROM... perhaps my plain picky ol' G3.

I was initially hesitant of zapping (resetting) the PRAM, but now I know it is an ordinary-almost-required procedure.

Thanks once more for all support and interest on helping me. I intend to visit this forum more often, not only because of future questions that I might have, but also for I believe I may contribute on other people's troubleshooting.

Best regards,

Andre W.

---

### Post by ristosu on 2006-01-23
One explanation might be that B&W's OF doesn't support the DVD-ROM drive for booting. It always boots from the hard drive, and Mac OS X identifies its own installation CD (and transfers the control to it), but not Ubuntu's. To overcome this, my suggestion is to put back the original CD-ROM drive.

OF, Open Firmware, is like BIOS in PCs, only more flexible. It's based on language Forth. To get an idea of its possibilities, take a look at [http://www.firmworks.com/QuickRef.html](http://www.firmworks.com/QuickRef.html)

---

### Post by ZeCaQ on 2006-01-27
I think the problem is related with the hard disk change.

I have a similar problem: I install successfully ubuntu in a original iMac 233MHz (G3 - PPC) in a disk of 4GB (with a dual boot - with partitions).

But, when I change the hard drive to a Seagate Barracuda with 40GB, the problem is there - the installation are successfully but, when I boot/restart the machine, the iMac freezes immediately after the first sound of boot with a blank screen.

Take a look at this site: [http://www.terrasoftsolutions.com/support/hardware/breakdown/index.php?hw_cat_id=5](http://www.terrasoftsolutions.com/support/hardware/breakdown/index.php?hw_cat_id=5) - there are the following text for iMac 233/266MHz: "If you have replaced the original drive with something larger, you will need to select the Manual Drive Partition option and create a 100MB /boot partition BEFORE the / partition or the machine will not boot" - it looks like the same thing...

If I hold down the 'D' key it starts normally the Mac OS 8.6.

It seems to be the firmware and yaboot are not prepared to work in large hard disks.

I'm a newbie in Linux/Ubunto. I have no solution for this problem. I'm still looking for...

Excuse my English.

Best regards,

José Carlos Quental

---

### Post by andre-w on 2006-02-11
Hello ZeCaQ,

I think you may be right. Maybe my troubles were cause at least in part by non original devices. My first G3 had a upgraded the HD and the CD-ROM replaced by a DVD-ROM. Also, it makes pretty much sense that the firmware has a lot to do with what happened. I only installed Ubuntu after I replaced my original G3 for another one. Both where B&W (Yosemite), however the second one is a "Revision 2", with improved video and IDE controler.

Thanks for your contribution. Hope see you again.

By the way, your English is just fine!

Regards,

Andre W.

---

