---
title: "Advice - AMD64 eMachine M6805 Laptop"
date: 2005-09-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by d1337 on 2005-09-26
I am aquiring a new laptop with an AMD Athlon 64 3000+ processor and am trying to decide what to do for my install.  It has WinXP on it, which I'll probably leave on it for a few work apps (quickbooks, namely).  I will be using this machine for work mostly, so I'll likely stick with a 32bit install for work stuff.  But, I hate having 64bit potential and not using it.  I'd also like to start learning (and help where I can) the 64bit arch.  I have looked around in the forums, but haven't quite come up with an explanation to install both a 32bit and 64bit base.  I'm assuming that this would be similar to a tri-boot install.  Is there, by chance, a nifty little howto that I am not seeing that may help?  The HDD has been upgraded to a 100G, so I can afford to have partitions for each.  May I share /home between the two for some settings and preferences?

Thanks,
d1337

---

### Post by mlomker on 2005-09-26
> May I share /home between the two for some settings and preferences?


No problem.  You could even see the /home partition from Windows if you decided to format it as VFAT.

The key thing for you is going to be to install windows first, then install the Ubuntu versions one at a time.  If you really want 32-bit Ubuntu...it's really not necessary.  It's a little more complicated to use a chroot to run your 32-bit apps in but it does work.

In any case, you'll always need to select manual partitioning for Ubuntu during the install.  Make a swap partition of 1.5x memory, and then a partition for each version of linux (which will be / for that version).  My / is about 3 Gig so if you went 10 Gb for each then that'd be plenty.  The rest of your space you can make /home and share that between versions if you like....and store everything you care about in it.

If you are going to run different versions of KDE/gnome then you should have a different user account name in each version of unix (so that there are separate /home/username directories to store preferences).

---

### Post by n0ah420 on 2005-09-26
I have this exact same laptop running WinXP_64 (7GB) / Breezy_64 (10GB) / Scratch-Fat32 (40GB) / Home (2GB) / Swap (1GB).  Wireless, 3D, Sound, pretty much everything working without a hitch.  Make sure you get the upgraded bios so your acpi will not freek out and you should be all set.  If you run into an issue just let me know and I'd be happy to give some advice.

---

### Post by d1337 on 2005-10-05
Update, if anyone cares.
Got the machine last Friday and played on the windows side for awhile...mostly to get anything off from the prior owner whom is a friend of family.  Started with a new install of WinXP just to clear out all the leftovers.  XP gave no option for partition size...no surprise.  I was a little anxious to get Ubuntu on the machine, but it wouldn't take Breezy 64...wouldn't recognize the keyboard during install.  I didn't realize (I'm a newbie) that this had to do with acpi.  So I dropped in Breezy instead and it took without issue.  Didn't have any issues with sound at all.  The box worked great, with exception to 3D and wireless, from the start.  I was surprised as I've had issues with sound on 5 desktops that I have put Hoary on.  I was pleaseantly surprised to see that the installer allows for simple shrinking of an existing partition...worked like a charm.  I shrunk XP down to 12G. 
Last night, I dug around and finally found the Bios update.  This must be done from the windows side, best I can tell.  Had problems finding it as the emachines support site reported that it was too busy.  Here's the address where I got it from...finally
[http://www.emachines.com/support/product_support.html?cat=notebook&subcat=M-Series&model=M6805](http://www.emachines.com/support/product_support.html?cat=notebook&subcat=M-Series&model=M6805)
Again, this appears to only be possible through windows...but someone else may know differently.  It uses an .exe file to backup and flash the bios.  It shuts the machine down, you should leave it down for 30 seconds, as recommended by the instructions.  When you bring it back up, it updates the bios and shuts back down...another 30 seconds is probably a good idea.
After this was done, I dropped Breezy 64 in and ran through the install without a hitch.  I have a pretty fast connection, so I was running in Breezy 64 fully updated (prior to repo changes) in less than an hour.  Sound...out of the box no probs.
Today, I decided to fix wireless.  Used two guides and filled in the blanks.
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=m6805+emachines+ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=m6805+emachines+ndiswrapper)
[http://greg.primate.net/m6805/](http://greg.primate.net/m6805/)
insuring that you use the 64 bit drivers as recommended by Greg, but note that he is using a Debian AMD64 install.  Especially if you're a newbie as myself, I stongly suggest reading the entirety of both posts before proceeding.  Use the appropriate drivers.  I just downloaded to my desktop and extracted there.  The drivers are BCMWL564.SYS and netbc564.inf.  Follow the instructions from the Ubuntu Forums How To by jonny.  My wireless is working without issue, except I haven't set up a WAP in my office yet and my neighbors is locked (good for them).  But it receives signal strength, so I'd assume it's fine.
The only thing I have left to tackle is 3D.  I'll do some digging and report results back.  Fortunately, the last link above to greg has a copy of his Xconfig which I guess I can use for reference.
d1337

---

### Post by manno on 2005-10-13
I do care. I have an m6805, and I was wondering if I should bother putting ubuntu on it, or if getting the wireless drivers in particular would be a pain. After I read this post I'm sold. Thanks for taking the time to update. By the way does WPA work on the card or is it still WEP only?
Oh and you can install the 3D drivers with this program

[http://ubuntuforums.org/showthread.php?t=64629](http://ubuntuforums.org/showthread.php?t=64629)

All the info to use it should be in there.

Thanks again,
-manno

---

### Post by mlomker on 2005-10-13
> By the way does WPA work on the card or is it still WEP only?


My previous laptop was an M5310.  Emachines uses Broadcom cards, so you'll have to use ndiswrapper.  Ndiswrapper is supported by wpa_supplicant so you should be fine.

---

### Post by d1337 on 2005-10-13
Thanks for the link, manno.  I've stumbled upon Easy Ubuntu several times, but have been hesitant in even giving it a try as I don't think it's set up to run Breezy 64.  Haven't spent much time yet on 3D, but maybe this weekend.

d1337

---

### Post by LateNighter on 2005-10-25
I am running an AMD Sempron 64bit 3300+.
 It touts the Capability of being able to run 32bit as well as 64bit at the sametime.
 Which I thought was Nice, because to the best of my knowledge, my Old Athlon 64 3000+ couldn't do that, At least i never heard about it.
 I have no doubt the New Athlon 64's can do the same as well as the X2 Dual Core.

 I figured it would be kinda a mess to run 32 as well as 64 at the same time, But it does it without Problems. Run a 64bit Maintence Program while playing a 32bit Game, Something i never couldv'e Dreamed of before.

 And the Multi Tasking is Awesome Compared to any 32bit System, and is quite a bit better then my Old Athlon.

 I just wanted to tout a little on my New Toy, I Hope you didn't mind.:rolleyes: 

 Back on Track.

 I am Dual Booting Win XP only for a couple of Programs that Linux really doesn't have any that Will Replace them, at least Not Yet.
 But I hope they will soon. One being a program to Maintain my Printer Cartridges after I refill them, And to run DVD Decrypter as well as Xdvd Shrink.
 And to run My Scanner as I have yet to find a Linux Program that gives me Good Scanning Results with my Scanner.

 Other then That WINDOWS is Garbage, I haven't booted to Windows for about 2 weeks Now.
 
 I use Ubuntu Hoary 5.04 for all other things I need to do on my computer.

 But you must make One thing that I found is absolute.
 Windows must be Put on the Primary Partation First then which ever other one(s) that you want. Otherwise the Dualboot will not Work "PERIOD".

 I'm Dualbooting with XP on 10 Gig Partation, and Ubuntu Hoary 5.04 on a 70 Gig Partation.

 I have a Seagate 80 Gig Ultra ATA 133 Harddrive, and it Works Flawless.

 The Ubuntu as well as anyother Linux OS that I know of next to Linspire, Must be installed Manually doing the Partation during Installation, Otherwise Windows will "$%^&#" it all up. 

 I've found a Good little way to FORMAT and PARTATION your Hardrive without any type of Problems.

 I use a Disk Wizard CD that came with my Seagate, and it worked also on a Maxtor I use to have as well as a Western Digital I still have but have Moth Balled for the moment.

 Even though they say it won't Work on anything Other then a Seagate, but It does.

 Using the advanced Installing Mode to ready your harddrive, Just boot to the CD and go into Advanced Install Mode, Select the size of your Partation for Windows my case 10 gig, Format to Fat 32, or NTFS, then Format the Remaining Space in my Case 70 Gig to Fat 32, then install Windows First and in advanced options it'll give you the choice to format the Partation for Windows to either Fat 32 or NTFS.

 Then install your Ubuntu and during the Manual Install choose the Reiser Format, I do this to keep Windows from trying to Cross over unto My Ubuntu Partation.

 Many will tell you this can't Happen, But beleave me my friend it can because, I've had it happen, Nothing Major happened I just don't like it.
 When I'm running linux i want to See Linux Files not Windows.

 Reboot and there You Have it: A NICE Clean Dual Boot System with Windows, and Ubuntu.

 One other Peice of Advice though, DISABLE your Windows Installation from being able to Connect to the Internet.
 This will Greatly lessen the Chance of Windows fouling Up and getting a Virus, GEE Imagine that.:p ;) 
 And Causing you to Have to Redo the Whole Thing Windows, Ubuntu and All.

 Now if you MUST use Windows on the Internet which I don't, any Upgrades I need for Windows I get while in Ubuntu, Burn them Down then go into Windows and install them from there.

 Then all I can Say is GOOD LUCK.
 Just while under Windows WATCH what Sites you go to, And you should be fine.

 Beleave it or Not while running Windows I got MORE Virus, Spyware, Adware. and MalWare from MicroSoft and their so called Trusted Sites then almost all other sites I visited Combined.

 "Just My THREE CENTS Worth and theres MORE where that Came From"

---

