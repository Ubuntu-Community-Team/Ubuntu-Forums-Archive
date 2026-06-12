---
title: "New to Kubuntu"
date: 2006-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by RustyShackleford on 2006-04-27
Hey y'all,

I haven't played with Kubuntu yet, but I plan to shortly.  The final parts for my computer rebuild should be here today, and I plan to run Kubuntu on it, as well as dual booting XP, as much of my stuff still resides there, and I'm wanting to get my feet wet a bit before I jump in.

So I've got a few questions before I get going, and any opinions, experiences, et cetera that y'all have would be greatly appreciated.

First off, the hardware specs for the new box:

AMD Athlon 64 X2 4800+
ASUS A8N32-SLI (nForce4)
4GB Corsair VMS DDR400 RAM
nVidia GeForce 7800 GSOC
Creative Soundblaster X-Fi Music
2 300GB Maxtor IDE hard drives
SIID floppy drive and media card reader
2 Sony DVD-R/RW drives

As I said, hopefully the last parts (case and processor) will show up today, so I may be installing tonight.  This box is made primarily to run on Windows, as most of my programs are there right now.  Migrating from MS Office to OpenOffice or KOffice should be pretty easy, but a lot of my other stuff I want to research and experiment a bit before I move over.  I run Visual Studio 6.0 and Visual Studio .NET, as well as MSSQL Server 2000 there, though I am beginning to play a bit with migrating my VS projects into working with MySQL instead of MSSQL.  But for now, that stuff will be staying on the Windows side.

I've played with Linux a bit before, but this will be my first really serious build.  I've used SuSE before, I've run SLAX off a USB key (because my motherboard fried, and I couldn't get to my HDs, but I could still run fine off a USB key), and recently, I've run Mandriva on another computer.  I like them, but I've gotten a little confused with how to work get around, like when a program (Yahoo messenger, for instance) asks whether it's a Debian build, BSD build, et cetera.  And I haven't gotten quite used to KDE yet, but I haven't tried very hard, I'll admit.  So I'm going to really try jumping into it here, but my Linux experience is so far pretty minor.

I'm leaning towards Kubuntu because I am more familiar with KDE than GNOME, and I'm posting it on the Kubuntu side, so I expect to get more people leaning that way, too, but anyone have any pros or cons to share on using KDE vs. GNOME?

I'm also posting to the AMD 64 forum, and I'm, at the moment, planning to run the AMD 64 version of Kubuntu, but is there any reason I should look at running the 32 bit version instead?  At the moment, I'm not looking at doing anything too heavy with it, just getting used to it and seeing how well I like it, so I don't think I'll have any 64-bit requirements, but should I stick with the 64-bit anyway?

Dual booting - I've installed dual boots both ways, Linux first then Windows, and Windows first then Linux.  I've heard that Linux should go on first, but I've never had any problems either way.  Should I do Linux first, or does it matter?

I think I read somewhere that Ubuntu is a Debian base, if I've got the terminology right.  If a program has multiple Linux versions, like the Yahoo messenger, do I pick the Debian version, then?

I also read that you can run either GNOME or KDE from either installation.  Is this something that's enabled from the start, or would I have to install GNOME somehow to be able to use either?

I've seen messages before about setting up a separate partition for the home directory.  Seems like a good idea to me, so you can change your OS or reinstall it without disrupting your files.  I've always done this with my Windows machines.  Any other benefits to this or reasons behind it?  How big should I make this partition?  How big should my root partition be?  One of the 300 GB drives will be used for data storage for my databases and projects and such, but the other I can work with as need be.

Anything else I should know before getting into this?  Thanks in advance, and I look forward to getting to Kubuntu.

Rusty

---

### Post by mishranurag on 2006-04-27
I will answer the few questions of which I know about. You can install KUBUNTU or UBUNTU, whatever you like. Later you can add other option by going to terminal window and typing sudo apt-get install ubuntu-desktop (if you installed Kubuntu before).

Most programs, you can get from synaptic package manager or adept (in case of Kubuntu).  If you want to install yahoo messenger (for now, you can't because of some library compatibility issues), you can download the deb file, right click on it and there should be an option to install (in Dapper). If not you can easily dpkg in terminal (I don't remember the exact command). 

On a side note, yahoo messenger for linux appears like a beggar in front of yahoo messenger in windows, so I use GAIM.

I hope these helps.

Anurag
---------------------------
[My two cents on installing dapper and about different flavors]("http://mishranurag.blogspot.com/2006/04/following-on-with-ubuntu-606.html")

---

### Post by tymek666 on 2006-04-29
About dualbooting, always install win first, then linux. I'm runnig Kubuntu 64 bit without any serious problems.

---

### Post by mesp on 2006-05-15
yep winxp/windoze first is the easy way
just leave some room, debian a big install says 2-3 gb, kubuntu much less. sure someone will correct me

---

### Post by jamb on 2006-05-28
Hi,
I have spent some time trying out various distros on a dual disk computer. I have one HDD set up with pure Windows, and the other disk as Linux. In that configuration you can continue to play, re-install, configuring Linux without worrying about the Windows disk. 
Consider this dual disk scheme, it have saved my day many times.

---

### Post by Christopher on 2006-05-30
[QUOTE=mishranurag]I will answer the few questions of which I know about. You can install KUBUNTU or UBUNTU, whatever you like. Later you can add other option by going to terminal window and typing sudo apt-get install ubuntu-desktop (if you installed Kubuntu before).

Most programs, you can get from synaptic package manager or adept (in case of Kubuntu).  If you want to install yahoo messenger (for now, you can't because of some library compatibility issues), you can download the deb file, right click on it and there should be an option to install (in Dapper). If not you can easily dpkg in terminal (I don't remember the exact command). 

On a side note, yahoo messenger for linux appears like a beggar in front of yahoo messenger in windows, so I use GAIM.

I hope these helps.

Anurag
---------------------------
[My two cents on installing dapper and about different flavors]("http://mishranurag.blogspot.com/2006/04/following-on-with-ubuntu-606.html")[/QUOTE]


Does the newest Kubuntu come installed with gaim or is there an option at install? Thank you for your time.

---

