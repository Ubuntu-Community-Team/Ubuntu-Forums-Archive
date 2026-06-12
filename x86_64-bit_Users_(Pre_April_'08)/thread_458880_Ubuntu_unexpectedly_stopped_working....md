---
title: "Ubuntu unexpectedly stopped working..."
date: 2007-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by rksk16it on 2007-05-30
The AMD64 Feisty was working good and then one fine evening it stopped bootin ! Before giving more detail I think I should state my PC configuration :

Intel 965G chipset,
Pentium Core 2 Duo
160 GB SATA HDD
MSI NVidia 7950 GT

I have AMD-64 bit version of Feisty installed along with Windows-XP (though i use it only to play games but at this moment it came handy ) . I have recently upgraded my Kernel from 2.6.20-15 to 2.6.20-16 and it worked all fine. But when i recently tried to boot my computer strange things happened...

Firstly GRUB failed to start (so I wasn't able to start any OS including WinXP) ...but then again it unexpectedly it started working. I tried to boot Ubuntu but it failed...using any option like 2 versions of Kernel and 2 versions of their 'safe' modes but all in vain. I tried to boot from my CD but it also failed ( in both cases of normal and safe modes). 

When I first started Windows after this incident it said it found new hardware, some video controller. I then suspected my graphics card is creating trouble but it was running good ( I tested i tested it by running Elder Scrolls-IV in full graphics !). But after on next booting of Windows-XP it stopped complaining...now back to Ubuntu...

I have recently also upgraded my NVidia driver ( restricted drivers section ), but after that i have booted Ubuntu 5 or 6 times !. I have previously seen in the system log of Ubuntu that there is some error saying something like....error : MSI interrupt... I don't remember the exact message.

If anyone have **any** idea, i will be **very** thankful if he/she mentions here. Also if anyone knows how to start Ubuntu in command-line mode ( i'm pretty comfortable with that ) or how can i obtain some-sort of 'rescue-disk', please tell me.

Thanks for reading this, i have posted this much detail because it is a bit difficult to find linux experts ( or even experienced users ) here in India ( or atleast where **I** live in India ).

Thanks a lot in advance for helping me :)

---

### Post by Ken_Lewis81 on 2007-05-30
Did you install from a Ubuntu LiveCD?  That's a good environment for recovery.  It may be that the kernel upgrade also changed the places your system looks for its disks and so you will need to do some fixing.

Recent kernels have changed over to record the disk locations by the partition information, not their /dev/hda1 or /dev/sda1 tree.  Your SATA drive will have begun to use a new driver that calls its disks '/dev/**s**da' rather than the previous standard '/dev/**h**da', so will need to be fixed.

If it's a simple case that the Filesystem Table (/etc/fstab) points to the old names and needs to be swapped to the new names, that's easy to resolve.  We will need to sort out some core files, so make backups of these.

Run LiveCD, and get a terminal prompt from the menu.
Run GPartEd from the System -> Configuration menu to find out the layout of data on your disks.  One should be on your SATA disk and labelled '/'.  Remember its name, e.g. */dev/sda1*.  There may be another, called /boot/.  Remember its name too.
Get a Terminal Window. (Ubuntu ->Accessories -> Terminal)
Mount your disk's root partition:
```
sudo mount /dev/sda1
```
Then, type the following in the terminal window:
```
ls -l /dev/disk/by-uuid/
```
Compare it to the content of the filesystem table in '/etc/fstab'.

You now need to match the entries in your '/dev/disk/by-uuid' listing to the ones in /etc/fstab: copy the long UUID strings into /etc/fstab (which you will need to edit as root, and breaking this may leave your computer unbootable, so make a backup)

If this doesn't yield the right information, don't panic.  It's possible that the LiveCD doesn't have the same driver for the hard disks as your new kernel.  If you want to fudge it, then swap every **hda** for an **sda**.

The last thing that needs to be fixed is /boot/grub/menu.lst.  There may be a faked one from the LiveCD, so we need the name of the /boot/ partition or /dev/sda1/boot/ for the "boot/grub/menu.lst".  This, again, is a core file that you will need to make a safe backup copy of. Each line for a Linux kernel contains the word "ROOT=" (don't be thrown by GRUB's "root (hd0,1)" lines) and then a description of the device that the root filesystem is.  Make sure that each of these -- I think you have four -- points to the right place, whether the UUID or the /dev/sda1 thing.

I hope this contains enough information to help you. Please ask some more questions.

Take care.
Ken.

---

### Post by rksk16it on 2007-05-30
Thanks for such a great deal of step-by-step info, but...

I need to access Terminal to follow your prescribed steps. I have installed Ubuntu by downloading an 'iso' CD image and then done offline installation ( i hope this is called a LiveCD ). But even with the help of that CD i am **unable** to boot linux.

That is why i asked, in my above post, that if there exists a way to boot Ubuntu in command-line mode ( using whatever means - CD/ HDD ...etc), or if any kind of 'rescue disk' ( i ask this because the Ubuntu CD mentions about a rescue mode which is not available on my CD ) available for download, i would like to know that first. To try your steps ( or anything which requires fiddling with Ubuntu filesystem ) requires me first to **get inside**, also because my WinXP doesn't 'know' about the 'other side' of the disk !.

Thanks again for such a description, i would really like to try them once .... i get a chance to boot Ubuntu again.

BTW, will this work ( if everything fails ) to redownload Ubuntu CD image (from WinXP) and then use that CD to sort out the situation ( reinstall Ubuntu )  ?

---

### Post by rksk16it on 2007-05-31
Will Ubuntu be able to boot again if it has crashed due to some fault in my chipset...

I ask this because two things happened :

1. The last time i was working on Ubuntu it has crashed....never to boot again.

2. WinXP says some device hardware is missing. I inserted my intel 965G chipset driver cd and then windows said that it has found the driver needed to make the device work properly and the device was indeed my intel chipset ! This means there **was** some fault in the chipset.

About the post made by **Ken ( 2nd in this thread)** , i would like to say that after upgrading Kernel, there was no **immediate** problem, everything (including booting) was perfectly normal. So now i am pretty sure that while on Ubuntu, the chipset has stopped working ( my chipset **did** create problems before !) so it crashed.

Can anyone help me how to 'restore' ( or fix) critical drivers of Ubuntu when i am truly **unable** to boot it.

Also I repeat my question whether reinstalling Ubuntu will work ( i have recently purchased this PC, so there is little data on Ubuntu which needs backup ). Also i would like to know, is there any way to backup any data on Ubuntu **without** booting it...like installing any OS on some other partition ( most probably Debian on another Hard-disk, which i am going to install ) and then using that OS to backup those files...like Ubuntu can 'read' windows files ?

Thanks for **any** ( however small or little ) advice :).

---

### Post by Kuoi on 2007-05-31
Try this :

Press ctrl alt f1 at the log in screen to put you into text mode

Or try this (from another threath ) >  Originally Posted by wjp.reg  View Post
You can get into rescue mode by pressing esc when the system reboots which displays the startup menu. Just select rescue mode.

Once booted, then run
Code:

dpkg-reconfigure xserver-xorg

and answer all the questions, most of which you are safe to accept the defaults (at least in my case

Ubuntu SHOULD auto detect your video and monitor and you should be good to go. If not, I can't help any further and suggest you search the forum some more.

good luck

Hope this helps  , because I think it's a Xorg issue.

Kuoi

---

### Post by rksk16it on 2007-05-31
Thanks for the tip, but....**i can't boot upto login screen !**

The farthest i can boot is upto approximately the third slot in the Ubuntu startup 'orange bar', even the 'safe' modes hangs up after showing lots of success messages and in the end a weirdo set of hexadecimal numbers and...nothing it just hangs up !

About the startup menu u said...is it refers to GRUB menu ? (the only menu i get chance to operate while trying to boot Ubuntu :()

I think u r right that this is a Xorg problem and that is why i want ubuntu not to load any graphics ( X-Window, gnome ...etc) and go right into 'classical' terminal mode...but i don't know any method so far...

So, i think the only viable solution is reinstalling Ubuntu....and i will also install Debian too..because ( i think, but not sure) that it can be made not to load any graphics by default !

Thanks again for the help :)

---

### Post by Jouke74 on 2007-05-31
Sound like hardware problems to me, either with memory (possible), motherboard (likely) and / or harddisk (very likely).  

How warm does everything get when you are playing games?

> There is a site for rescue CD which you can use to restore software and check your hardware : **[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)** this works for both windows and linux, though I would be careful with the windows part of your system.

> Check your memory using any boot CD with the memtest option.

> Check your SMART status of your harddisk(s). This can be done with a tool which you can download from your harddisk manufacturer (that means another boot CD / floppy) or a general program like windows HD tune (but requires you to enter windows). 

> Motherboard I don't know how to check. 

> If it's up and running also check your dmesg log for errors and the windows event viewer for errors.
That should give you a better clue.

---

### Post by Cappy on 2007-05-31
> **rksk16it said:**
> Thanks for the tip, but....**i can't boot upto login screen !**
About the startup menu u said...is it refers to GRUB menu ? (the only menu i get chance to operate while trying to boot Ubuntu :()
Thanks again for the help :)

Yes, exactly.
By selecting "Ubuntu, kernel 2.6.20-16-generic (recovery mode)" on the GRUB menu you will gain access to just a "single user terminal" where you will be logged in as root (no need for "sudo blahrunsomecommands", just do "blahrunsomecommands").

From there you can do what Kuoi said and use "dpkg-reconfigure xserver-xorg" (no sudo needed)

Your system can be rescued, it would be a waste to reinstall anything imo.

---

### Post by Kuoi on 2007-05-31
You didn't changed a setting in your BIOS ?

Just a thought .

Kuoi

---

### Post by rksk16it on 2007-05-31
Thanks everyone :)

As Jouke74 said (7th post) ,** it is a hardware problem** and the culprit is - Motherboard. It has created problems before, but not anything which has caused this much trouble ! I am going to try that rescue disk he mentioned !! :) This is precisely what i was looking for.

As Kuoi (and Cappy) suggested about logging through recovery mode.....**that mode also is not working** !!! This is what  that made me particularly worried :(

As Kuoi asked about BIOS..no, i haven't changed it.

I think the solution is clear for this problem after all this discussion....i'm going to backup all necessary data using the rescue disk Jouke mentioned and then....wipe everything clean....and reinstall Ubuntu !

Thanks again everyone for such a nice support :)
I'm the only one in between my friends who use Ubuntu ( or for that matter - linux), they are all 'lesser-mortals' stuck with crappy winXP....and this much support on the forums has reinforced my belief in linux and its community :)

---

### Post by tgalati4 on 2007-05-31
Go into your BIOS and declock your machine.  Run it at half speed if possible.  Game-playing can put a load of stress on a machine.  The VIIV chipset tends to get toasty.  It's possible that you have warped your motherboard.

If you have another machine, pull the drive and plug it into a working machine and run a disk check on it to confirm that the drive is OK.  (It probably is OK.)

Make sure that your heatsink and fan is working and seated properly.  You could be experiencing thermal halts during boot up.  Set your fans to "MAX" in the BIOS until you get a successful boot.

It's interesting how Windows users point to the OS as the problem when it's really a hardware fault.  Usuually Ubuntu software failures leave lots of error files to decipher.

---

### Post by rksk16it on 2007-05-31
> Go into your BIOS and declock your machine.  Run it at half speed if possible.  Game-playing can put a load of stress on a machine.  The VIIV chipset tends to get toasty.  It's possible that you have warped your motherboard.

If you have another machine, pull the drive and plug it into a working machine and run a disk check on it to confirm that the drive is OK.  (It probably is OK.)

Make sure that your heatsink and fan is working and seated properly.  You could be experiencing thermal halts during boot up.  Set your fans to "MAX" in the BIOS until you get a successful boot.

It's interesting how Windows users point to the OS as the problem when it's really a hardware fault.  Usuually Ubuntu software failures leave lots of error files to decipher.

You may be right but i am sure my chipset is not toasted because :

1. The only 'heavy' game i played last time on this is Elder-Scrolls-IV and that too about 3-4 weeks ago and then Ubuntu was not installed on my PC. After i got Ubuntu i did not play much games ( usually half an hour day ) , and those games were not 'heavy' as they belong to 1998-99 ( Starcraft & Unreal-Tournament ), you can run these games with full graphics even without a graphics card !

2. Though i don't find WinXP very reliable but it still says that my chipset is working properly.

3. I usually keep my CPU with one side open and a sizeable pedestrial-fan constantly running at maximum speed pointing towards the guts of CPU , so it is unlikely that the motherboard is 'toasted'

I know **it is a hardware fault, not OS's**, i only want to recover from that.

BTW, my BIOS have the option ( in chipset category) - "PCI Latency Timer  <32>", is this the option to reduce the clock speed....i rarely go to BIOS, so i need to ask this. There is also the option - "Memory Frequency - <667 MHz>"...i am not sure which one points to 'clock-speed'.

Thanks for the advice anyway :)

---

### Post by tgalati4 on 2007-05-31
Clock speed can be changed a number of ways.  Sometimes there is a BIOS menu labeled "Frequency".  Sometimes running your bus at half speed (333 MHz) will cut the CPU speed in half.  Other BIOS picks include multiplier (10X, 8X, 4X, auto).  Pick something other than auto and reboot and write down the speed that you see posted on boot-up.  Then you will get a relationship between multiplier and and final CPU clock speed.

What I meant by "toast" is that many manufacturers use a ball-grid-array solder technique to save cost and slight warpage of the motherboard will cause the video, CPU, or PCI bridge chip to lift off of the motherboard.  This can cause intermittent failures.  Perhaps this is similiar to what you have been experiencing.

Good luck.

---

### Post by rksk16it on 2007-06-01
> **tgalati4 said:**
> 
What I meant by "toast" is that many manufacturers use a ball-grid-array solder technique to save cost and slight warpage of the motherboard will cause the video, CPU, or PCI bridge chip to lift off of the motherboard.  This can cause intermittent failures.  Perhaps this is similiar to what you have been experiencing.


You seem to be PERFECTLY right !!!!!
My motherboard DOES cause intermittent failures !!! 
On one occassion (much before this trouble), Ubuntu failed to boot displaying the message that it is stuck on some .... BUS !!! Actually i had just restarted it after playing for a lot of time on Windows.
After that i switched it off and then about half an hour later....everything was normal !!!

I want to ask one last thing...do i need to change motherboard or just keep the temperature low enough ?

Thanks a lot for that informative post !! :)

---

### Post by Jouke74 on 2007-06-01
If you really have a hardware problem I would try to resolve these issues first (buy a new mobo?) until everything runs stable and the way it should. Ie. Learn about the hardware settings and make them correct. Nothing more frustrating than needing to reinstall your system a day before a dealine, crashing while you just finished your <insert other important document here> or when your game black screens....

my 2 cents.  

PS. the CD is just for emergency recovery of stuff, and does not guarantee that you get everything back.

---

### Post by rksk16it on 2007-06-01
Thanks jouke, but learning about correct hardware settings is a bit difficult...the biggest problem is that it is not a piece of Open Source Application with huge wikis and forums (like this!) :(

Though i'm still pretty new to linux but very soon going to learn how to manually configure linux ( the hardware related stuff ) so that i'm better able to solve ( or should i say survive ) such devastating but rare problems.

Did u say that i should purchase a new one ? i have two reasons why i don't wish to purchase a new mobo :-

1. These problems are...rare...but i did not know it could be this much devastating.

2. It's barely 2 months ago i purchased this 965G !!! (i know there r some more threads out there complaining about this model )

But first i'm going to try out the recovery disk first and then reinstallation...and Debian too ( this is a part of learning linux hard way....Ubuntu is not 'hard', since it is a linux for human beings ! :) )

And yes of course if problems persists i would be left with no other option but to purchase a new mobo :(.

Yet another thanks for the support :)

---

### Post by Jouke74 on 2007-06-01
Did you build it yourself, or did you have your computer build? If the mobo is two months old you can claim guarantee if it is not working correctly (that is under the right settings). 

Rant on: 

- Read your motherboard manual (yes I know these are usually crap). 
   If you don't know a term in there google it on internet. 

- Understand the different memory types and how their speed settings work. DDR / DDR2 RAS, CAS etc..

- Leave your BIOS configuration to auto / default in case you have not got a clue what to use for the settings. If you don't know what it does, see point 1.

- Don't overclock, but read about overclocking as it usually explains the working of things much better.

- Make sure you know the temperatures of your rig in full working condition. Yes, playing Elderscrolls is such a condition and things you did in the past do influence your computer now... Damage in electronics remain.
Use e.g. windows speedfan, play Elderscrolls for an hour and read out all the temps. Nothing should be over 45 degrees celsius.

- The operating system of a computer is the software that makes the hardware work together. Also here you can influence the way the hardware runs, however you cannot correct problems with hardware itself. 

As a comparison, if my car (hardware) has only three wheels I (windows) could go drive and notice that the steering is very difficult. If a formula 1 driver (ubuntu) would take it for a spin, he will come to the same conclusion or won't even go without installing the fourth wheel. Driving without the fourth wheel we might damage the chassis, brakes etc. End conclusion is that we need that fourth wheel installed correctly.  

Rant off... sorry for that...

Best, JJ.

---

### Post by rksk16it on 2007-06-01
Hello again guys, i have tried the rescue disk Jouke mentioned, it did not boot up successfuly but terminated with following message...

.......[B]
  <6>Time: tsc clocksource has been installed.
Kernel Panic - not syncing : Attempted to kill init ![/B]


...Then nothing happened.

GNU make has once complained about clock skew, but then i did internet synchronization of the clock. I also discovered clock skew in winXP (its so sad i'm typing this from here) too and did synchronization there too.

Does the above message means i have to replace my BIOS battery (which runs the clock) in order to make the Kernel (any one...Ubuntu, Debian, Rescue disk....) boot !

...or it maybe something else looming over the horizon...

Thanks for any advice

---

### Post by tgalati4 on 2007-06-01
I think clock skew refers to the bus clock, not the real-time clock.  It appears that you have a timing error that is tripping up data-access within the motherboard.

It could be as simple as moving memory chips around.  Try swapping memory slots.  Clean the memory tabs with an eraser if the memory is old or recycled from another machine.

Try running memtest (on the Live CD--in the options pick) overnight to see if your memory is up to snuff.

Unfortunately, Linux expects perfect hardware.  When the hardware acts up, you get strange errors that will send you on a chase to find the problem.  The same hardware error can cause several different software error reports--this will drive you crazy.

Of course a kernel panic is rare in Linux--if it happens on bootup then it's a good chance that there is a hardware problem.  It's possible that a corrupt disk will cause this, for new installs, this is rare.

Windows users are so accustomed to rebooting, that they sometimes miss the hardware errors that cause a lockup and blame the software.

In Linux, your machine should be stable and run for months on end without a problem.  If not, then there is a problem.  It's intereting how Linux can really shake out wonky hardware.

---

### Post by rksk16it on 2007-06-01
i am writing this while memtest is going on....from a different PC in my home (old one - the new one is having a tour of hell itself !)

i would like to know what memtest actually checks...RAM/ Hard-disk/ motherboard..or all of them.

also i would like your opinion which components of my PC are definitely good...i state some facts :

1. i recently downloaded intel-desktop utilities (for winXP), and they reported that **everything is ok !**

2. now, my windows has also refused to boot....that is why i mentioned 'hell' above :(

3. the graphic card is (was - winXP is dead too) also working good.

4. my PC is entirely new - only 2 months passed, all components are new.

5. there is some dust always present in the air so after some time a lot of dust gathers in the cabinet. But i have seen all the computers ( my 2 old PCs, all of my friends' PCs) run for more than 3-4 years without such consequences.

i'm most worried about :- processr, chipset, RAM, hard-disk,..(and anything that is a very important component)

I must thank you guys for continuously helping me in this trouble and keeps my hopes up :) (in hardware not linux - i have **full** faith in linux). i worked at linux for about 2 weeks and it exceeded all my expectations regarding everything i heard about linux, i was almost at the point of removing winXP entirely but just not done so to play games ! 

There is a severe lack of linux professionals here. All do those 'computer-mechanics' promise that i should just handle my PC in their hands and they will clean everything, install the worst OS of the planet and then handle that back to me...

---

### Post by Jouke74 on 2007-06-01
Memtest is checking your memory... RAM + processor cache,  nothing else.

:popcorn:

---

### Post by tgalati4 on 2007-06-01
Depending on the machine, memtest will get the processor toasty.  That's been my experience running PC's P1's through PIII's overnight and instrumented with thermocouples on the heatsinks.  If you can pass 30 cycles (considered a large population of cycles) then you can be 99% confident that your memory is OK and good to go for Linux.

Linux hates wonky memory.  And it will let you know.

As far as graphics, running

glxgears -printfps

will give a workout to the video chipset.  

Install smartmontools to outfit Ubuntu with some monitoring tools.   You will need these to see what is getting toasty.

Finding hardware faults can be a pain.  I spent 6 hours repairing an iBook clamshell that was shorting out the video cable inside the hinge.  This was causing a 6-amp draw that fried a motherboard transistor that powers the video chip.  A little patchwork and the craplet is running again.  

The original symptons were spontaneous, hard shutdowns.  Talk about frustrating.  No logs, nothing.  I managed to get the machine running in Frankenstein mode (dismembered) and poked around and when I touched the video cable--BAM, shutdown.  Craplets are a pain to reassemble.  Well, any notebook is for that matter.

Take it a step at a time and be methodical about verifying all of your hardware.  

Good luck.  We could use another Ubuntu user.

---

### Post by rksk16it on 2007-06-04
Ubuntu is working again !!! :guitar:

What i did was this....

1. 
Ran memtest, which gave no errors on **std** test but gave some errors on **full** test, though i never completed either one of them (my patience was broken into bits at pass 25).

2.
I just covered up my PC (remember i said, i usually run PC with a side of CPU box open) and then waited for an engineer (or so those computer-people are called here...they are rarely actually engineers!! ) i called to show up.

3.
Then one day morning i restarted my computer and....viola...Ubuntu ran but with loads of disk errors along with failure of X-Window System. I inserted Ubuntu CD and then took backup of some data on my USB and then reinstalled it (wiping out WinXP and giving Ubuntu full disk space !) !!

4.
Today the engineer came and found no problems...even if there is a problem, i know he (and me too) cannot find that untill something happens next time...and i hope that happen after 4 yrs when i'll be buying a new PC :lolflag:

So here i am on my PC..Ubuntu...but without winXP :guitar: :guitar: :guitar:

But i'll be soon installing winXP because wine on my Ubuntu is unable to run any games...and i'll most probably install that crap on **another disk**.

So...i ask u guys about any guide about installing winXP **after**, Ubuntu...ie after winXP destroys my GRUB booting and modify the MBR, how can i restore that ?

Thanks !!! :)

---

### Post by Kuoi on 2007-06-04
I restored the grub using the first message of this threath [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Works like a charm here ,  Kuoi

---

