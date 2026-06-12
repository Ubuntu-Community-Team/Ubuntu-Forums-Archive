---
title: "64-bit printer drivers?"
date: 2009-03-01
forum: x86 64-bit Users
---

### Post by Guns90 on 2009-03-01
I just purchased an HP laserjet P1006 printer and I'm having one heck of a time getting this thing to work.  At first it wouldn't work at all, then after changing some of the settings on it it worked fine until I powered off the computer and rebooted; then nothing.  I uninstalled it, reinstalled it, messed with the settings, got it working again, powered it off a couple of times and rebooted and it worked fine again.  Went to bed last night, woke up this morning and it won't work at all.  I have uninstalled it, reinstalled it, and messed with it till I'm blue in the face and I can't get it to work again.

I went to hp.com, looked up the printer and it lists several OS's to install it with.
 Microsoft Windows Vista
»  Microsoft Windows Vista (64-bit)
»  Microsoft Windows XP
»  Microsoft Windows Server 2003
»  Microsoft Windows Server 2003 64-Bit Edition
»  Microsoft Windows XP x64
»  Microsoft Windows 2000
»  Mac OS X
»  Linux 

The Liunx link doesn't help at all.  My question is:

Is my using the 64-bit version of Ubuntu the probable problem?  I sure would appreciate any suggestions.  Tanks

Ubuntu 8.10 64-bit
ASUS M2N32-SLI Premium (Vista Edition)
AMD Athlon 6400+ X 2
4 Gb Kingston DRAM
EVGA 8800 GT 
HP LaserJet P1006 printer

---

### Post by yyyc186 on 2009-03-01
It's not your printer.  I have all kinds of trouble with my Lexmark now which worked for years with Ubuntu.  I am also running the 64-bit 8.10.  If you have applied _any_ of the recent updates your printing will be sporadic at best.  Cheap, single sided, worthless printers seem to work OK, but high end postscript which support duplexing got trashed bad.  OpenOffice refuses to do anything more than send an empty file to my Lexmark Optra S 1855.  KWord does seem to print OK though, so it must be using a different path through CUPS.

If you only need a few pages once in a while to get by right now, I can tell you my el-cheapo Epson Stylus Color 880 is printing OK from this machine.  My HP T65 has occasional issues, but it was having its own issues a while back.  I haven't hooked up the Cannon MP210 I was forced to take out of the store along with a notebook I bought.  (It was $200 cheaper to buy the notebook and take the printer than to leave the printer behind...go figure.)

The updates over the past two months have been outright horrible.  We must be getting invaded by former Microsoft employees.

---

### Post by steveneddy on 2009-03-01
I use 8.04 64 bit with the HP printing suite HPLIP installed from the HP web site. I currently use an HP Officejet J6480 All-In-One and it works perfectly in hardy with HPLIP.

Sorry to read that 8.10 has poor printing capabilities.

Maybe a digression to Hardy 64 bit would be a likely solution.

---

### Post by marcelkoopman on 2009-03-01
This has nothing to do with Ubuntu, but with cups.

I suggest installing a different driver for your printer.
Try:

apt-get install linuxprinting.org-ppds-extra

You should try a different ppd.

---

### Post by TombKing on 2009-03-01
> **yyyc186 said:**
> It's not your printer.  I have all kinds of trouble with my Lexmark now which worked for years with Ubuntu. 

Lexmark is crap for *nix support. They basically just don't do it. You think it would support it with all the damn things they deployed at a large aircraft manufacturer in the pacific northwest that I do windows support for, and more than intimate with the print enviroment in particular. Then again it hasn't been the major PITA that Xerox was, that wouldn't even play well windows.

There are a few small areas that are keeping HP printers because the unix app will not work with Lexmark.

HP actually has good support for linux but x64 support be it windows or *nix is hit and miss for a lot of print stuff still. Which is annoying as x64 has been around a damn long time now.

As far as the hardware itself goes. HP hands down makes stuff that is amazing. We still have just a few HP4 printers and still a fair amount of HP5 model that have gone through the engineered life cycle several times over and still kick prints out like it isn't a problem.

---

### Post by Guns90 on 2009-03-01
I did the 'apt-get install linuxprinting.org-ppds-extra' and still no luck.

I'm not very good at this stuff, guys.  In honesty, I'm a GUI guy all the way.  I switched to Ubuntu because I just got tired of all the problems and $$ to fix them with M$. 

I built this computer for my kids.  They hated my trying to enforce the use of linux, and cried that they needed M$ for school, so I built this with what I thought was all the latest M$ technolgy (hence the Vista Edition motherboard).  They have now procured laptops, so I took over this computer because it has much better speed and graphics than my old one.  I have it dual-booted with Vista, but default it to Ubuntu upon boot-up.  I simply wanted to have an economical way of printing b&w, so I bought this cheap little printer.  It works fine with Vista.  I just don't WANT to use use VISTA.  If I find a fix, I'll let you guys know.  

Thanks for the responses.

---

### Post by yyyc186 on 2009-03-01
> **TombKing said:**
> Lexmark is crap for *nix support. They basically just don't do it. You think it would support it with all the damn things they deployed at a large aircraft manufacturer in the pacific northwest that I do windows support for, and more than intimate with the print enviroment in particular. Then again it hasn't been the major PITA that Xerox was, that wouldn't even play well windows.

There are a few small areas that are keeping HP printers because the unix app will not work with Lexmark.

HP actually has good support for linux but x64 support be it windows or *nix is hit and miss for a lot of print stuff still. Which is annoying as x64 has been around a damn long time now.

As far as the hardware itself goes. HP hands down makes stuff that is amazing. We still have just a few HP4 printers and still a fair amount of HP5 model that have gone through the engineered life cycle several times over and still kick prints out like it isn't a problem.

I must strongly disagree with your position.  I have never had a Lexmark printer fail to work with any Linux, DOS, OS/2, Windows, or OpenVMS installation I connected it with.  Their level of support in the industry is without equal.  I purchase only Optra series or higher and get an average of 7 years out of them both at client sites and with my book writing.  I only purchase printers rated above 30,000 pages per month duty cycle on the low end, but generally look for 100,000 page per month duty cycles.

HP is a completely different story.  They build printers out of the cheapest sh*t they can find looking to turn a profit on the replacement ink.  Their laser printers are a laughing stock in the industry, unless someone points at a Brother printer which has the entire world laughing at it.  My work on OpenVMS dates back to when it was simply VMS and owned by a company called DEC.  The operating system is now owned by HP.  You don't want to know how many HP printers I've hooked up to OpenVMS to have them not work at all.  Replace them with a Lexmark Optra and life is good.  HP printers have the same problem with TRUE/64 and UX, both Unix variants HP owns.  

While you are at it, try getting an HP printer to survive even a year in a shop which prints 90,000 pages per month.  I have never had even one make it that long, no matter how high its rating.

---

### Post by yyyc186 on 2009-03-01
> **Guns90 said:**
> I did the 'apt-get install linuxprinting.org-ppds-extra' and still no luck.

I'm not very good at this stuff, guys.  In honesty, I'm a GUI guy all the way.  I switched to Ubuntu because I just got tired of all the problems and $$ to fix them with M$. 

I built this computer for my kids.  They hated my trying to enforce the use of linux, and cried that they needed M$ for school, so I built this with what I thought was all the latest M$ technolgy (hence the Vista Edition motherboard).  They have now procured laptops, so I took over this computer because it has much better speed and graphics than my old one.  I have it dual-booted with Vista, but default it to Ubuntu upon boot-up.  I simply wanted to have an economical way of printing b&w, so I bought this cheap little printer.  It works fine with Vista.  I just don't WANT to use use VISTA.  If I find a fix, I'll let you guys know.  

Thanks for the responses.


You have two solutions, because waiting for a fix isn't an option.

1)  visit On-Disk and purchase a fully updated Hardy DVD or CD.
2)  visit On-Disk and purchase OpenSuse 11.x  (You might want to get both a LIVE CD and an installation DVD so you can test printing prior to installing)

This printing problem has dragging on and my guess is the Ubuntu developers are about to have a crisis of faith.  Something Ubuntu developers have done in their wide fork from Debian has caused this problem.  It doesn't exist on SuSE.  I am ___very___ tempted to re-install SuSE this afternoon as I need to be able to print for proofing by Thursday a book which is going to weigh in at 1100+ pages.  I'm sure not printing that out single sided on an el-cheapo ink jet.

---

### Post by TombKing on 2009-03-01
> **yyyc186 said:**
> I must strongly disagree with your position.  
Then we can disagree. But there are some unix apps that are not printing correctly to the lexmark printers without major work and if there are printer firmware updates then they can break all over again. They will not supply us drivers for any of our unix servers. For the small office network mfd devices they will not supply us with print only driver as it was a windows server print queue that did not have any scanning software installed, office, etc. HP gave us a print only version in 2 weeks.

---

### Post by marcelkoopman on 2009-03-01
If you go to [http://localhost:631/printers](http://localhost:631/printers) in your internet browser, what printers are configured?

---

### Post by Guns90 on 2009-03-01
Search in Printers: Clear

Showing 1 of 1 printer.
  	Sort Descending 	 
HP-LaserJet-P1006 (Default Printer)
	Description: Hewlett-Packard HP LaserJet P1006
Location: gary-desktop
Printer Driver: HP LaserJet P1006 Foomatic/foo2xqx (recommended)
Printer State: idle, accepting jobs, published.
Device URI: hp:/usb/HP_LaserJet_P1006?serial=AB0NF26

Print Test Page 	Stop Printer Reject Jobs Move All Jobs Cancel All Jobs 	Unpublish Printer Modify Printer Set Printer Options Delete Printer Set As Default Set Allowed Users
  	Sort Descending

---

### Post by steveneddy on 2009-03-01
May I again recommend HPLIP for your issue?

Please uninstall any printer drivers in Printers under administration.

May I recommend then installing from the Ubuntu repos

hplip and hplip-gui

```
sudo apt-get install hplip hplip-gui
```

After installation you will find it under Applications --> Accessories

Open it and let it configure your printer for you. It will DL the correct driver and give you better control of your printer.

Please go here for more info:

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1006.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1006.html)

---

### Post by Guns90 on 2009-03-02
Steveneddy,

Sorry that I did not reply to your earlier post; however, I did install HPLIP.  I again just ran your suggested terminal command and I got

 Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version.
hplip-gui is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gary@gary-desktop:~$ 

Applications > Accessories only provides a 'Manage Print Jobs' option dealing with printers.  Clicking on that gives me a 'Document Print Status (My Jobs)' window with no data in it and no options.  


I have been busy researching everything I could about using this printer with linux and had no luck.  Last night I downloaded live CD's of Fedora 10, PCLinuxOS 2008, openSUSE 11.1, and Ubuntu 8.04.2.  I tried using all of them in the live mode and none of them, regardless of which driver I tried or firmware I downloaded, would make this printer work.  As I mentioned before, I have this computer dual-booted with Vista,and this printer works fine with with Vista.  I have another computer with XP and both of my kids MAC's will operate this printer.  NONE of the linux programs work, so I think it's pretty obvious that this HP printer is the problem.  It simply has no software to run linux.  As much of a hassle as it is, I guess that I'll just have save whatever I want to print on a flashdrive and print it on the Vista boot. Sucks to be me, huh?

---

### Post by raygj on 2009-03-02
> **Guns90 said:**
> Steveneddy,

Sorry that I did not reply to your earlier post; however, I did install HPLIP.  I again just ran your suggested terminal command and I got

 Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version.
hplip-gui is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gary@gary-desktop:~$ 

Applications > Accessories only provides a 'Manage Print Jobs' option dealing with printers.  Clicking on that gives me a 'Document Print Status (My Jobs)' window with no data in it and no options.  



I have been busy researching everything I could about using this printer with linux and had no luck.  Last night I downloaded live CD's of Fedora 10, PCLinuxOS 2008, openSUSE 11.1, and Ubuntu 8.04.2.  I tried using all of them in the live mode and none of them, regardless of which driver I tried or firmware I downloaded, would make this printer work.  As I mentioned before, I have this computer dual-booted with Vista,and this printer works fine with with Vista.  I have another computer with XP and both of my kids MAC's will operate this printer.  NONE of the linux programs work, so I think it's pretty obvious that this HP printer is the problem.  It simply has no software to run linux.  As much of a hassle as it is, I guess that I'll just have save whatever I want to print on a flashdrive and print it on the Vista boot. Sucks to be me, huh?

TRY THIS
Instead of "Applications > Accessories" try "System > Preferences > HPLIP Toolbox"

---

### Post by Guns90 on 2009-03-02
Well, my wife says that I just get obsessed too easily, but I like to think that I'm tenacious.   I have continued to look for an answer, and I believe I have found one.  I found this site; [http://foo2xqx.rkkda.com/](http://foo2xqx.rkkda.com/).   I followed its direction, and it appears that the printer is working as it should.  

I would like to thank everyone for their responses. I hope that maybe someone else may benefit from the aforementioned website.  

You guys are great.  Thanks a lot!

---

