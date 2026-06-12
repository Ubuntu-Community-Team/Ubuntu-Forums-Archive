---
title: "Installing On AMD 64 x2 Dual Core 3800+"
date: 2007-04-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by yosef on 2007-04-01
I just got an HP pavillion a1520n which has an AMD 64 x2 Dual Core 3800+ with xp media center.  For nowI want to keep xp and dual boot. I have a live installation disk of Kubuntu  Dapper 64 bit version.  I want to install it but, as Isaid, Iwant to dual boot withxp which is already installed.  I do not have windows installation disks so xp has to stay there.  How do I go about installing Kubuntu on there too for the dual boot, and what else should I be aware of for this installation?  Please explain it too me as the noob that I am.  Including partitioning etc.  Thanks!

---

### Post by calraith on 2007-04-01
There are a couple of problems here.

1. You have no safety net -- no WinXP CD.  Whenever you undertake messing with your partitions, remember Murphy's Law.  If something can go wrong, it *will*.

2. You have Dapper.  Get Edgy, or even Feisty.  Dapper is a bit old.

I **strongly** encourage you to try out Feisty in a virtual machine before you start risking your partition table.  [Microsoft Virtual PC 2007]("http://www.microsoft.com/windows/virtualpc/default.mspx") is free, and if something goes wrong, your base XP Media Center Ed. won't get hosed.

I'm all for recommending that people try Ubuntu, but when I do, I want to make sure their first experience is positive.  In this case, far too many things can go wrong in my humble opinion.

Whatever you decide to do, good luck!

---

### Post by calraith on 2007-04-01
Oh, umm, yeah.  I just realized you have 79 posts and I have like 3.  That probably means you've used Ubuntu before.

OK.  If you're determined to do this, grab a [GParted LiveCD.]("http://gparted.sourceforge.net/livecd.php").  It should be able to resize your NTFS partition non-destructively.  After that, just allocate the drive's free space during Dapper (or Edgy or Feisty) installation.

Cheers!

---

### Post by Kilz on 2007-04-01
> **calraith said:**
> 

2. You have Dapper.  Get Edgy, or even Feisty.  Dapper is a bit old.



Bad idea. Dapper is still a current release, it will be untill 2009. Feisty is in BETA testing. I dont recommend anyone install BETA software on a machine they cant afford to mess up. Edgy wouldnt be bad, but Dapper is better than Edgy. Lastly Edgy will end of life in 2008, Dapper in 2009. That may be important if the person installing doest want to replace Ubuntu soon.

---

### Post by yosef on 2007-04-02
> **Kilz said:**
> Bad idea. Dapper is still a current release, it will be untill 2009. Feisty is in BETA testing. I dont recommend anyone install BETA software on a machine they cant afford to mess up. Edgy wouldnt be bad, but Dapper is better than Edgy. Lastly Edgy will end of life in 2008, Dapper in 2009. That may be important if the person installing doest want to replace Ubuntu soon.

...and this is why I am installing with Dapper.  At this point stability is where its at for me.  Truth is, the only reason I am keeping xp at all is because it is the media center edition and that makes certain things easier for my wife and kids... anyone know how mythtv compares to xp media center?  Or is there some other program which is comparable to  media center?  I have heard that mythtv is a real pain in the @$$ to get up and running.  How does it do on a 64 bit processor?

---

### Post by yosef on 2007-04-02
btw, how do I best take advantage of the dual core-ness of my processor?

---

### Post by Kilz on 2007-04-02
> **yosef said:**
> btw, how do I best take advantage of the dual core-ness of my processor?

With 64bit you dont have to do anything. All 64bit Dapper and above kernels are designed to use multicore processors because they have smp or [Symmetric Multiprocessing]("http://en.wikipedia.org/wiki/Symmetric_multiprocessing") enabled.

---

### Post by yosef on 2007-04-06
That is so cool!

:guitar:

---

### Post by nsteussy on 2007-04-06
Could you install a second hard drive and put Ubuntu on that?  It seems a safer option to me that moving partition boundaries around.

duke out

---

### Post by Kilz on 2007-04-06
> **nsteussy said:**
> Could you install a second hard drive and put Ubuntu on that?  It seems a safer option to me that moving partition boundaries around.

duke out

Its theoretically possible, but I have not done it. Grub would have to be installed on the master boot record of the drive that boots and you would have to edit the menu.lst to the location of the install. Resizing partitions isnt that hard compared to what you are suggesting.

---

### Post by stmiller on 2007-04-07
> **calraith said:**
> 

OK.  If you're determined to do this, grab a [GParted LiveCD.]("http://gparted.sourceforge.net/livecd.php").  It should be able to resize your NTFS partition non-destructively.  After that, just allocate the drive's free space during Dapper (or Edgy or Feisty) installation.



Yeah GParted can shrink your Windows partition and make room for Linux. And it doesn't mess up the Windows partition- everything stays intact. (Backup critical data to be safe, as always.)

Feisty is super sweet! And has latest Linux kernel. For me the Feisty beta is more stable/faster/uber-improved over any previous Ubuntu release. And this is just the beta.

---

### Post by russell.h on 2007-04-07
I had XP installed on a 80GB SATA drive, and had quite a bit of important data on that drive that I couldn't afford to lose. So when I went to install Ubuntu (32 bit Edgy at the time) I picked up a second 120GB IDE drive to use for it. Plugged it in, made it my secondary boot device in BIOS (CD drive being first), popped in the Ubuntu CD, and away I went.

Of course all that valuable data that I couldn't afford to lose has now been untouched for like 6 months... makes a person wonder just how valuable it really was :)

---

### Post by Kilz on 2007-04-07
> **stmiller said:**
> Yeah GParted can shrink your Windows partition and make room for Linux. And it doesn't mess up the Windows partition- everything stays intact. (Backup critical data to be safe, as always.)

Feisty is super sweet! And has latest Linux kernel. For me the Feisty beta is more stable/faster/uber-improved over any previous Ubuntu release. And this is just the beta.

Not that I doubt you think it is, but Feisty is still under development and still has issues that my super favorite version Dapper (still with support and updates until 2009)does not have. Vmware doesnt work, gdesklets wont start, I cant install the video driver from ATI, and firefox crashes all the time for me. Feisty looks good, but it cant compare to a very stable mature release where everything works.

---

### Post by yosef on 2007-04-08
So I did it.  First I burned a gparted livedisk and booted from it.  Gparted would not resize the partition, it gave me an error saying I should run chkdsk and then reboot twice (windows!:roll: )
so I did.  It then allowed me to resize the partition but after I did so windows woulld no longer boot!  The computer came with a little partion from which I can do a restore or a complete reinstallation to "factory settings" or whatever, so I did that and I was back at square one needing to resize again (not to mention having to fix all sorts of settings and reinstall firefox with all the addons etc!) but this time when I went to resize it, gparted worked right off the bat!  I then installed kubuntu 64 bit edition and that more or less where I stand now.  Thanks for all the advice guys!

---

