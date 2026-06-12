---
title: "B&amp;W G3 Will not boot from CD."
date: 2006-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rikostan on 2006-04-21
I am at a loss here. I got a B&W G3 a couple of weeks ago. It runs Panther just fine, no issues at all, but I want to run ubuntu on it as well.
I burn the ppc cd on one of my ubuntu machines and pop it in the mac. I hold down the c key and it seems to be accessing the cdrom, but then it just boots in OSX.
I have checked the checksum for the iso file and it was fine. I downloaded different versions for the PPC and burned them at the lowest possible rate, but still the same thing.
I have also tried to boot the CD from the open firmware by typing cmd-opt-O-F and then using the boot cd @ 0:2,\\:tbxi deal too, but to no avail.
I just acquired the Panter CDs today, butthey won't be here for a few days, so I don't have any other discs to try to boot to.
 I also asked for 5 Mac cds to be shipped, so I'll try those when they come in too, but does anybody have ideas I can try now?


{EDIT} This is a second revision machine too.

---

### Post by davygravy on 2006-04-21
The B&W is easy to open, right? (I've got a "smurf" B&W, too.)

To see whether or not this is a hardware problem or not, you could just open up the side of your machine (while it is off-be careful w/ static discharge) and unplug the hard drive.  Then try again to boot up w/ a CD.  True, you wouldn't be able to install the OS on whatever CD you are booting from (as no HD would be available) , but at least you could see if it will boot from a CD in general.  Of course, don't forget to power down when you reattach the HD.


You could also check to see that your CD-ROM unit is set to master (there is usually a little chart/graphic on the outside of the CD-ROM unit that shows master, slave and cable-select settings).

Good Luck

davygravy

---

### Post by Rikostan on 2006-04-21
I actually already checked everything out hardware wise. I added another ide drive to the machine right after I got it and re-sat everything and cleaned it out(air can) then.

 I can browse all of the drives including the CDrom and manipulate files on the new HD as well as copy files off of the CDrom successfully too. I have installed a few apps and a couple of games from the CDrom as well, so I would imagine things are good that way.
Thanks for the reply though.

---

### Post by Rikostan on 2006-04-21
Hey that got me to thinking... Because of the second IDE drive wouldn't the syntax of this command boot cd @ 0:2,\\:tbxi be a slight bit different?

---

### Post by davygravy on 2006-04-21
I dunno there...but...

glad you got your smurf going on Ubuntu.

I use Tiger a lot, but there is so much that I like about Ubuntu/Dapper.

---

### Post by Rikostan on 2006-04-21
Actually I don't have it running Ubuntu yet because I can't boot the CDs! :)

I do have a few flavors of ubuntu running on a few laptops and two PCs at home and one here at work though.

---

### Post by davygravy on 2006-04-21
[QUOTE=Rikostan]...
 I can browse all of the drives including the CDrom and manipulate files on the new HD as well as copy files off of the CDrom successfully too. I have installed a few apps and a couple of games from the CDrom as well, so I would imagine things are good that way.
Thanks for the reply though.[/QUOTE]


When you say that you can browse, do you mean that you can browse the Ubuntu CD from the OS X Finder? 

You mentioned that you have installed a couple of games from the CDrom, which CDrom do you mean?  The Ubuntu?

I guess I'd have to say that if your hardware "checks out OK" but it won't boot off the CD, then either the CD may be bad (a bad burn?) or there may be some hardware issue that you may have missed.

IOW, if everything checks out OK, but it doesn't work still, then something is still probably wrong (though it may be difficult to find-not obvious).  If you haven't checked the jumper settings on the hard drives and the CD-ROM drive, that's the only thing I can think of.   **Come to think of it, that's exactly how an old Beige G3 of mine acted when I had it's drives incorrectly jumpered.

Which version of Ubuntu are you trying to install/boot into?  Dapper or Breezy?  Live or Install?

You are using the PPC (not x86) Ubuntu CD, right?  The x86 installers/live CD's won't boot a PPC. (perhaps this is obvious, but I see that you have a Toshiba & another x86 - but you say that you are sure you have the PPC CDs, so that shouldn't be the problem...).


Are you sure that the *board* is a rev2?  I've seen a Blue&White that indicate Rev2 (by serial number) on the outer case, but the mobo was actually an early rev1 (that had the flaky no-slave-support IDE chipset) that had been swapped in to replace a faulty rev2 mobo, after market.  Those old mobos can be finicky.

?? YMMV.  Good luck.

---

### Post by Rikostan on 2006-04-21
>  When you say that you can browse, do you mean that you can browse the Ubuntu CD from the OS X Finder?
Yes sir. I can browse any CD I pop into the drive so far while running OSX. I can manipulate the files on the CD as well.

> You mentioned that you have installed a couple of games from the CDrom, which CDrom do you mean? The Ubuntu?

No the Cdrom drive. I have installed different games and apps using the cdrom drive. I would even know how where to begin to install games on OSX from an Ubuntu CD, if that is even possible.


> I guess I'd have to say that if your hardware "checks out OK" but it won't boot off the CD, then either the CD may be bad (a bad burn?) or there may be some hardware issue that you may have missed.

I thought that at first as well, but I have made sure the download was a good one via the checksum and I downloaded the different files on three different machines.
When I say different files, I mean kubuntu, edubuntu, and Ubuntu.
 Two of the machines were Ubuntu on X86 and the other was XP.

It still could be bad burns, but the fact it was multiple downloads on three different machines with good checksums makes me think otherwise.

> Which version of Ubuntu are you trying to install/boot into? Dapper or Breezy? Live or Install?
Yes. :) I have tried all of them including the beta release yesterday of Dapper.

> You are using the PPC (not x86) Ubuntu CD, right? The x86 installers/live CD's won't boot a PPC. (perhaps this is obvious, but I see that you have a Toshiba & another x86 - but you say that you are sure you have the PPC CDs, so that shouldn't be the problem...).

Yeah I am quite sure they are the PPC discs.


> Are you sure that the *board* is a rev2? I've seen a Blue&White that indicate Rev2 (by serial number) on the outer case, but the mobo was actually an early rev1 (that had the flaky no-slave-support IDE chipset) that had been swapped in to replace a faulty rev2 mobo, after market. Those old mobos can be finicky.

Actually no I am not sure. I just looked at the case itself and I can't even remember now how I came to the conclusion that it was indeed a rev 2. I'll check again tonight just to make sure.

---

### Post by Rikostan on 2006-04-21
Okay... this HAS to be the disc. I had a surprise waiting for me at home.. the Panther CDs are here. I popped the first one in and it booted to it right away by just holding C down.

The only thing I can think of that might be effecting this is the fact that I burned the Isos with DVD burners on all three machines I tried. I know that shouldn't have anything to do with it, but I am going to try a CD burner instead just to see what happens.

---

### Post by Rikostan on 2006-04-21
I am going to give up for now... It still did not work with a CD I burned, so I am going to wait until the official ubuntu PPC cd gets here.

---

### Post by Rxke on 2006-04-23
I just recently burned a 5.10 on my smurf, via an external SCSI (re-)writer and it went fine... Though the Kubuntu one didn't want to load... probably the drive getting old, having problems reading self-burned disks?

---

### Post by Rikostan on 2006-04-23
No all four drives I burned from are pretty new. And I have never had problems reading discs I burned, but this is the very first time I have burned something for a mac... I know an iso is an iso is an iso, but something odd is going on.

 Just to reiterate.. Three of the drives were DVD drives, two of which were installed on Ubuntu x86 machines, one of which was a Windows XP machine. The last drive was a CD burner installed on an ubuntu x86 machine. I do not have a burner in the mac, although I guess I could install one there and install toast to burn it instead. I think before I add any new hardware to that machine, I'll wait and see if the official CDs from Canonical work. They should be here in another 2 weeks or so.

---

### Post by Rxke on 2006-04-23
No need to install toast, you can burn isos using the disk utility with a few clicks. [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)
But anyhow, using other hardware (ie install an new CD drive) can sometimes lead to problems re: installing, but if you could lend (or is that loan... Sorry, I'm Dutch speaking) an external one somewhere (firewire or usb ) , you'd be set, to try... again ;)

The B&W's are getting a day older, and a bit temperamental, I guess. My machine has seen quite heavy use since I bought it in '99, and sometimes it acts up, not wanting to boot from CDs too... Still, it's my machine, that I use daily, it hasn't let me down in major ways otherwise (except that it's my second mouse and third keyboard, those things wear out pretty quick. )

---

### Post by farruinn on 2006-04-23
[quote=Rikostan]Yes sir. I can browse any CD I pop into the drive so far while running OSX. I can manipulate the files on the CD as well.[/quote]

What about the install disc? While running OS X you should be able to open the Ubuntu install disc and browse some files there. If the disc doesn't mount or you open it in the Finder and can't see any files then there's something wrong with the disc.

---

### Post by engla on 2006-04-23
Well I dunno about this, but the first computer I installed ubuntu on was my nice B&W G3/300.

I had a very weird configuration, I put an extra HD on the CD IDE chain, since I could not have more than one HD on the main IDE chain (controller bug that pretty much crippled this Rev. A machine).

Anyway, that extra HD was giving me issues, and I couldn't boot from CD as long as I had it in -- removing it, I could boot to the cd fine.

That was my small B&W drama. 

Note that this mac has an ati rage 128 card, and it seems to be pretty well supported by ubuntu. Even if it's a very weak card you should be able to get nice hardware acc. in dapper (or breezy with xorg cvs)

---

### Post by Rikostan on 2006-04-23
[QUOTE=farruinn]What about the install disc? While running OS X you should be able to open the Ubuntu install disc and browse some files there. If the disc doesn't mount or you open it in the Finder and can't see any files then there's something wrong with the disc.[/QUOTE]


I'll just copy and paste from earlier in the thread...
>  " When you say that you can browse, do you mean that you can browse the Ubuntu CD from the OS X Finder?"
> Yes sir. I can browse any CD I pop into the drive so far while running OSX. I can manipulate the files on the CD as well.

---

