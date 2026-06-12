---
title: "To break the 4GB barrier"
date: 2008-09-13
forum: x86 64-bit Users
---

### Post by GepettoBR on 2008-09-13
I intend on buying a new computer soon (been pushing it off for over a year until I had enough money) and with the current tendency for mobility, it may be the last Desktop computer I buy.

I don't want to spend a lot of money on something that'll get old quick, so I want space for improvement. I want something that'll run on 64 bits, with spare PCI slots, et cetera.

I went down to a shop to take a look and see how much it would cost me to get together what I had in mind, only to be informed by the saleswoman that if I wanted a >4GB-RAM-compatible motherboard, it would cost me around twice as much as a "regular" one. This confuses me to no end, because in spite of my geekish tendencies I don't know that much about hardware.

I thought that all I needed in order to take advantage of the extra RAM would be a 64-bit processor and OS, but according to this lady regular motherboards can't address the extra memory. So, I ask of this community which has answered so many of my questions:

What does it take to break the 4GB barrier?

---

### Post by najames on 2008-09-13
Look at the motherboard specs, ignore what the woman is telling you unless she's the engineer who made the board.  For example on Newegg look at the specifications for this board.

GIGABYTE GA-MA78GM-S2H AM2+/AM2 AMD 780G HDMI Micro ATX AMD Motherboard
**Maximum Memory Supported  	16GB**

Add a 64bit chip on this board, install a 64bit OS, install up to 16GB of RAM.

Always double check the manufacture's website to make sure info is right.

---

### Post by soxs on 2008-09-13
A mainboard which supports 8GiB  of RAM. Nothing more, nothing less. I would suggest you to buy something like DFI LANPARTY UT 790FX (the pimpe one with dual SATA II and dual LAN or the shrunken one with only one each, I like them because of their "Award" bios, which isn
't as shrunk as many other are, though I didn't rn linux with any of those 2)

---

### Post by GepettoBR on 2008-09-13
Thanks for the responses, I'll look into those... Anything else I should be aware of?

---

### Post by jhenager on 2008-09-13
Just my thoughts - 4GB should be enough for anybody. (Shades of Gates!!! :))
I am only running 2GB (I remember having 2MB and being psyched.) and that's plenty for the forseeable future. My current system specs are in my sig. I'm a lifetime tech support pro, and this system should run any space hog Microsoft could ever throw at it, although it probably will never have to. Ubuntu is too good.

---

### Post by najames on 2008-09-13
Note: There are lots of motherboards on Newegg, search for them all (AMD or Intel), order by most reviews as you'll have an idea of which are most recommended.

A reason for >4GB RAM - VMWare or any virtual system and allocating RAM to each virtual machine + the host OS.  :)

---

### Post by Mau on 2008-09-13
The truth of the matter is that you can't buy technology and expect it to be forwards compatible. You can buy a motherboard with support up to 16 GB, but DDR3 will be become affordable before you actually ever have that much. Every type of interface is going to change (and already is changing).  In 2 years, PCI Express x16 might be the new AGP.

So, my two cents: look for future expansion possibilities, but don't spend more money up front to guarantee forwards compatibility.

---

### Post by Mister.Vash on 2008-09-14
> **jhenager said:**
> Just my thoughts - 4GB should be enough for anybody. (Shades of Gates!!! :))
I am only running 2GB (I remember having 2MB and being psyched.) and that's plenty for the forseeable future. My current system specs are in my sig. I'm a lifetime tech support pro, and this system should run any space hog Microsoft could ever throw at it, although it probably will never have to. Ubuntu is too good.

Depends on what you use the machine for, most people won't need it, but I regularly have multiple Virtual Machines running and I go over 4 GB.  My recommendation is just to know what you are going to be running, if it falls into an area where you know you will need it, then great, get it.  Most people don't need that right now and aren't going to be using it.  If you aren't going to be using it for the time being, save a little money and review it when it's time to get your next motherboard.

---

### Post by GepettoBR on 2008-09-14
> **jhenager said:**
> Just my thoughts - 4GB should be enough for anybody. (Shades of Gates!!! :))
I am only running 2GB (I remember having 2MB and being psyched.) and that's plenty for the forseeable future. My current system specs are in my sig. I'm a lifetime tech support pro, and this system should run any space hog Microsoft could ever throw at it, although it probably will never have to. Ubuntu is too good.

> **najames said:**
> Note: There are lots of motherboards on Newegg, search for them all (AMD or Intel), order by most reviews as you'll have an idea of which are most recommended.

A reason for >4GB RAM - VMWare or any virtual system and allocating RAM to each virtual machine + the host OS.  :)

That's almost exactly my problem. You see, I can't bear Windows. It's awful in every respect. However, I depend on it for running heavy-duty video editing software (namely, Adobe's AfterEffects and Premiere and Sony's Vegas) that misbehave terribly in WINE and have no satisfactory Linux-friendly alternative. These are processes that consume too much RAM and I intend to run them in a Virtual Machine so Ubuntu can take care of everything else (like my torrents) in the background, hence the need for gratuitous amounts of RAM.

> **Mau said:**
> The truth of the matter is that you can't buy technology and expect it to be forwards compatible. You can buy a motherboard with support up to 16 GB, but DDR3 will be become affordable before you actually ever have that much. Every type of interface is going to change (and already is changing).  In 2 years, PCI Express x16 might be the new AGP.

So, my two cents: look for future expansion possibilities, but don't spend more money up front to guarantee forwards compatibility.

I'm vaguely aware of that. I obviously don't expect to still be using this same machine in ten years, but I do expect to have it for at least five. I know I can't hope for it to accept all the cutting-edge technologies by then, but a little room for expansion is necessary, if nothing else to keep up-to-date with the bare minimum. I don't want something I'll have to throw away because not even one of my current parts is compatible with whatever new hardware I'll need for a specific function. As for DDR3, I'd rather have lots of DDR2 memory than a smaller pool of DDR3, because what I really need is a bunch of good old megabytes lying around. I'm willing to sacrifice speed for this purpose, especially since when it comes to editing raw video the HDD puts a cap on speed long before the RAM has a chance.

Thank you everyone for the input. Living in Brazil, it isn't really feasible to order anything from Newegg (if they even deliver offshore) but it certainly looks like a good source of information.

---

### Post by soxs on 2008-09-14
for excesive rendering/CAD/moddeling I would say get 4GiB or more, otherwise, 2 or 3 GiB are enough

---

### Post by sjbaugh on 2008-09-14
To add my 2 pence (I am English!), I have found that when I want to upgrade my setup, a new motherboard and processor seem to be the best way to go as so much will have changed in the mean time (different graphics card slot, different processor socket etc).

I am currently running Hardy Heron 64 bit quite successfully with a 3GHz core duo and 2 MB of RAM on a Gigabyte motherboard.

Steve

---

### Post by Sky Pixie on 2008-09-14
Some motherboards operate below the stated memory standard when the maximum memory capacity is inserted.

IE Newegg claims:
Memory Standard:  DDR2 800
Maximum Memory Supported:  8 GB

Fact:
Memory runs at DDR2 667 when more than 4 GB of memory is inserted.

Read all comments.

Purchase the best performance per real.  Today's high end hardware will be mainstream within one year.  Don't pay a premium for "upgradable" hardware that will never be upgraded.  I doubt you will purchase a LGA 775 or AM2+ socket compliant CPU in five years.

---

### Post by GepettoBR on 2008-09-14
> **Sky Pixie said:**
> Some motherboards operate below the stated memory standard when the maximum memory capacity is inserted.

IE Newegg claims:
Memory Standard:  DDR2 800
Maximum Memory Supported:  8 GB

Fact:
Memory runs at DDR2 667 when more than 4 GB of memory is inserted.

Read all comments.

Purchase the best performance per real.  Today's high end hardware will be mainstream within one year.  Don't pay a premium for "upgradable" hardware that will never be upgraded.  I doubt you will purchase a LGA 775 or AM2+ socket compliant CPU in five years.

Then what would you do in my place? Keep in mind that I do need a lot of RAM.

---

### Post by Jouke74 on 2008-09-15
> **sjbaugh said:**
> 
I am currently running Hardy Heron 64 bit quite successfully with a 3GHz core duo and **2 MB** of RAM on a Gigabyte motherboard.

Steve

Can you please me how to do that with 2 MB instead of GB??? That would be extremely useful, since it means I can run about 500 Ubuntu Hardy VMs in my 2 GB of memory :lolflag:

Seriously, just put together a "basic computer spec sketch" from pieces of hardware that are available & affordable to you. When you have a basic list, the crucial component will be the motherboard. From many Mobo vendors you can download a manual and in there should be the qualified vendor list en compatibility list. You'll see straight which and how much of memory will work and what not. 

Then, before buying, check compatibility for paired combinations of the hardware in Google. If you find multiple consistent instances of people (that know what they are doing) reporting issues select a different component.

---

### Post by GepettoBR on 2008-09-15
> **Jouke74 said:**
> Seriously, just put together a "basic computer spec sketch" from pieces of hardware that are available & affordable to you. When you have a basic list, the crucial component will be the motherboard. From many Mobo vendors you can download a manual and in there should be the qualified vendor list en compatibility list. You'll see straight which and how much of memory will work and what not. 

Then, before buying, check compatibility for paired combinations of the hardware in Google. If you find multiple consistent instances of people (that know what they are doing) reporting issues select a different component.

Sounds like a solid plan. Thanks a lot! Are there any general combinations to look out for? For example, I know that if I want 2X RAM and have a dual-core processor, it's best to have two RAM sticks worth X each than one worth 2X. Are there any other ideal matches like that involving processors, motherboards, et cetera?

---

### Post by tuxxy on 2008-09-15
If you are into virtualisation software you will see also benefits of using 64-Bit Hardy, what hardware you choose is up to you, I prefer AMD as you can probably tell heh

Also heres the link to the [64-Bit user group]("https://wiki.ubuntu.com/64BitTeam") if you need any more information

---

### Post by Jouke74 on 2008-09-15
1	Antec LifeStyle Sonata III Zwart	
1	Asus EAH3650/HTDI/512M
1	Asus P5K-E/WiFi-AP	
1	Intel Core 2 Quad Q9450	
1	Lite-On LH-20A1S	
1	Logitech G5 Laser Mouse	
1	Logitech Z-3e (2.1, 2x 8.5W, 23W, Zilver)
1	Microsoft Natural Ergo Keyboard 4000 (USB)	
1	NEC 3,5" Diskette Drive 1,44MB (Zwart)	
1	OCZ OCZ2P10004GK 4GB (2x 2GB) DDR2	
2	Samsung Spinpoint F1 HD753LJ, 750GB	
1	Scythe Infinity SCINF-1000	

Wel something like this was in the best buy guide of the Dutch tweakers site just before the holidays. It encompasses a comfortable workstation, that in addition to being capable of doing some serious stuff, is also relatively quiet.

The screen that was added is most expensive: 1	Eizo ColorEdge CG241W-BK
But that is basically loose from the computer and any LCD will suffice.

You can start from this and adjust to your wishes.

Best, Jouke.

---

### Post by Sky Pixie on 2008-09-16
> **GepettoBR said:**
> Then what would you do in my place? Keep in mind that I do need a lot of RAM.

I have not paid close attention to the motherboard chipset market for almost one year therefore I will not suggest a specific motherboard for fear of suggesting an outdated model.

I suggest you search a few sites:
[http://www.hardforum.com](http://www.hardforum.com)
[http://forums.extremeoverclocking.com](http://forums.extremeoverclocking.com)
[http://www.ocforums.com/](http://www.ocforums.com/)

There are dozens of "what is the best motherboard for..." threads.

Read [**this**](http://ubuntuforums.org/showthread.php?t=890604) thread before purchasing a P45-based motherboard.

---

### Post by soxs on 2008-09-16
As an amd friend: 
Mobo: Mobo with AMD 790FX : 80 - 200&#8364;  (using M3A32-MVP Deluxe, though it is limited to PCI slot but 4 PCIe which I'll never use ~ 140&#8364;)
CPU: Phenom 9xxx : 120&#8364; - 160&#8364;
GPU: ATI RadeonHD 4870 : 190&#8364; - 240&#8364;
Mouse: Razor Krait : ~20&#8364;
Keyboard: Cherry ... 2.99&#8364; *g*
Harddevices should be choosen to you needs, maybe blue ray if you're going to have a devil-box and high budget.

---

### Post by dagrump on 2008-09-17
Well now! an old fool, (what! I resemble that remark) and his money are soon parted. I upgraded my main toy & went stupid.
Beware of motherboard spec's supports XX gb's ram, well, yeah, you should be aware you may need to do multiple tweak sessions w/ your bios. 
I have 8 gb of ram (overkill for me), but it did require digging around on different forums, the machine is great now. I have a 150 gb raptor free for intrepid. I put the machine together to run different stuff in virtualbox & figured out, I didn't play with virtualbox enough to justify the extra RAM, I really thought I'd use it, YMMV, you can always add more if you need it.

---

### Post by SarahKH on 2008-09-19
> **soxs said:**
> for excesive rendering/CAD/moddeling I would say get 4GiB or more, otherwise, 2 or 3 GiB are enough

Dunno.  Would bumping the memory give more of a performance boost than throwing another machine at the problem?  Considering I can get a C2D base box only for like £240.  

Of course you might need 4GB+ on the designing machine to actually load the work before feeding it out.

---

### Post by GepettoBR on 2008-09-20
Some of these replies have put me in a bit of doubt... Let me ask another question, then. If I do not go over 4GB of RAM, is there really an advantage for installing the x64 version of my OSes?

---

### Post by Kilz on 2008-09-20
> **GepettoBR said:**
> Some of these replies have put me in a bit of doubt... Let me ask another question, then. If I do not go over 4GB of RAM, is there really an advantage for installing the x64 version of my OSes?

Yes!
But first let me ask you a question, are there any disadvantages of installing a 64bit os? After all we know that even 32bit users are not guaranteed a seamless install with no setup? If you think that 32bit means you wont have issues I suggest you look [here]("http://ubuntuforums.org/forumdisplay.php?f=326"), and [here]("http://ubuntuforums.org/forumdisplay.php?f=331"), and [here]("http://ubuntuforums.org/forumdisplay.php?f=329").
Im not asking if you think that a 5 minute extra setup is a good reason. Because thats just being lazy. Are there any real reasons not to run 64bit any more other than listening to old outdated FUD?

Now on to your question, the ability to go over 4gb of ram isnt the only reason to run the 64bit os. Other reasons include
1. To use the hardware you paid good money for to its potential.
2. To get up to a 30% increase in performance for some applications like ripping cd's, editing graphics, encoding movies, 3d modeling, CAD, and other resource intensive applications.
3. To support the future, the more people we have running the 64bit os the more improvement in performance we will see because support will shift from the 32bit os.

---

### Post by GepettoBR on 2008-09-20
> **Kilz said:**
> Yes!
But first let me ask you a question, are there any disadvantages of installing a 64bit os? After all we know that even 32bit users are not guaranteed a seamless install with no setup? If you think that 32bit means you wont have issues I suggest you look [here]("http://ubuntuforums.org/forumdisplay.php?f=326"), and [here]("http://ubuntuforums.org/forumdisplay.php?f=331"), and [here]("http://ubuntuforums.org/forumdisplay.php?f=329").
Im not asking if you think that a 5 minute extra setup is a good reason. Because thats just being lazy. Are there any real reasons not to run 64bit any more other than listening to old outdated FUD?

Now on to your question, the ability to go over 4gb of ram isnt the only reason to run the 64bit os. Other reasons include
1. To use the hardware you paid good money for to its potential.
2. To get up to a 30% increase in performance for some applications like ripping cd's, editing graphics, encoding movies, 3d modeling, CAD, and other resource intensive applications.
3. To support the future, the more people we have running the 64bit os the more improvement in performance we will see because support will shift from the 32bit os.

No, I know there are lots of issues with 32-bit versions of everything... don't worry, I come to you free of prejudice.

I asked about other possible advantages because I wasn't aware of any others, and also because of the only bit of experience I have with 64-bit OSes: my girlfriend bought a computer with a 64-bit capable processor, and wanted me to install Windows XP for her brother and Ubuntu for her. I noticed that the 64-bit XP had higher system requirements, and in the Ubuntu setup, it took a long while to get gDesklets running (she wanted the dockbar) because of that whole python 2.4 mess. So, if I had no advantage to trade for the higher resource consumption, it wouldn't be really worth it.

This was almost a year ago, and gDesklets is an old, abandoned project, but I thought it was worth asking anyways. Never too much information, right?

Looking around the forums, I noticed a lot of people complaining that flash and java don't work on 64-bit Ubuntu, others reply saying "yes it does, I didn't tweak anything and it works". I don't mind tweaking anything (in fact, I think it's loads of fun), but are there any big current shortcomings of x64 that aren't present in regular x86 systems? I ask just to avoid being shocked when I see them, since I'll go 64-bits anyways.

P.S.: you hit me where it hurts. Video encoding is exactly what I want the machine for, and it's right there on your list. Hooray!

---

### Post by Shadowmeph on 2008-09-20
I cannot seem to get 64bit Ubuntu to Boot with 4 gbs ram while running the fglrx (ati video drivers). but if I boot in safe mode (sorry can't remember the proper name for it) or if I turn off the fglrx video driver I can boot to desktop. this is strange because I also have 64bi opensuse11 installed  bit and it runs with out any problems at all.
has anyone else had this problem?

---

### Post by malrost on 2008-09-21
Your lady misinformed you. Over a year ago I bought a Gigabyte M57SLI-S4, (which supports up to 16GB) for under $100 US. I was also, at the time, able to find a sale and buy 8 GB of DDR2 for around $300 US.

Regardless of whether you use a 32 or 64 bit OS, you can run it on a motherboard that supports more RAM.

As you point out, this may be the last desktop you build or buy. It is wise to consider future upgrading when building a system, and the motherboard is key. An obsolete motherboard with minimal RAM space will probably seem unbearably useless far sooner; you'll have to replace it with another system entirely and in the long run won't save any money at all.

Regarding the separate question of 32 or 64 bit OS: in my experience the 64-bit system does require some additional tweaking, initially. My only real issue was getting flash to work, and that process is now well-documented. It's not as if the 64-bit system requires more time on an ongoing basis.

I believe the advantages of the 64-bit OS far outweigh the minor inconveniences, and if you will be using applications that benefit from 64-bits like video encoding or virtual machines it is the obvious choice.

---

### Post by GepettoBR on 2008-09-22
I went to another store and this time I asked the salesman to write down the motherboard model for me. It was a Gigabyte motherboard, and he wrote down "G31M". On the Gigabyte website, there are five motherboards named "GA-G31Mx-xx" and I have no idea which one this is - the salesman also said that the motherboard supports up to 16GB RAM and is compatible with DDR3, but Gigabyte's website states that all five support up to 4GB and DDR2. Other things did not match (he said there were 6 USB ports, the website says 8****).Is this motherboard missing from the listing, or is the sales guy stupid/uninformed/trying to swindle me?

UPDATE: I looked aaround some online stores and they all seem to confirm what Gigabyte's website says. They could all have copied and pasted the info from the website, of course. The reason I'm not 100% certain that the salesman is lying is that he actually made a budget for a computer with 8GB of RAM. I can see the lawsuits coming in if he were giving away wrong information like that and letting people buy the wrong product - but then again, people don't usually buy that much RAM...

---

### Post by RadarG on 2009-01-04
> **najames said:**
> Look at the motherboard specs, ignore what the woman is telling you unless she's the engineer who made the board.  For example on Newegg look at the specifications for this board.

GIGABYTE GA-MA78GM-S2H AM2+/AM2 AMD 780G HDMI Micro ATX AMD Motherboard
**Maximum Memory Supported  	16GB**

Add a 64bit chip on this board, install a 64bit OS, install up to 16GB of RAM.

Always double check the manufacture's website to make sure info is right.

I looked up GIGABYTE GA-MA78GM-S2H, as I am also hunting for a good board. I like the fact that you can put 8G of DDR2 in it. I also would like to look at ones that take DDR3. Anybody know of any?

---

