---
title: "Intel dual core support?"
date: 2006-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by old_and_grey on 2006-09-02
I'm building two PCs for home use. Both have the same basic specs:

Intel E6400 conroe dual core cpu 1066 FSB 2MB buffer
Asus p5b LGA775 conroe mobo
2 gigs dual channel ddr2-533 RAM
2 320 gig Sata2 HDDs
Evga e-geforce 7600 580mhz dual dvi-i video card
2x21-inch 3ms LCD panels

They will be running on a 1GB internal network and talking to the outside world through a switch and router.

Does Ubuntu support the 64-bit Intel chips? Both will mainly be used for building CMS systems on LAMP.

Any feedback much appreciated.

---

### Post by ngdias on 2006-09-02
I don't know if this helps, but Ubuntu 64bits is running very well on my Pentium D 930. I'm also using an Asus board and a nvidia-based graphics card.

---

### Post by Cynical on 2006-09-02
No you wont be able to install ubuntu or any linux distribution for that matter unless you do it over the internet (gentoo is the exception), or use a sata connection for your cdrom drive. 
The motherboard you've chosen uses intel's p965 chipset which lacks an ide controller. The substitute jmicron controller isnt supported in the kernel yet, though it may be by the time edgy comes out. 

And yes if you download the amd64 version of ubuntu you can get a fully working 64-bit distro. I'm posting this from a Core 2 Duo E6300. (after installing over the internet using instlux) I'd suggest getting [this](http://www.newegg.com/Product/Product.asp?Item=N82E16813131032) board instead of the one you were planning to get. All the negatives aside, these Core 2's are fast! I love compiling and seeing everything scream past.

---

### Post by patrickfromspain on 2006-09-02
intel's core 2 duo cpus are 64 bit?? I though they were 32 bit. The core duo t2x00 are 32 bit aren't they?

---

### Post by John.Michael.Kane on 2006-09-02
Core 2 Duo Conroe has support for EM64T

Yonah-Core Solo/Duo are 32-bit
Used in: iMac, Mac mini, MacBook Pro, MacBook

hope this helps

---

### Post by samir85 on 2006-09-02
What Intel Core Duo is 32bit,
I thought it were 64 bit ?!

---

### Post by John.Michael.Kane on 2006-09-02
samir85 Yonah is 65nm dual core architecture processor. which doesn't support Intel's EM64T 64-bit extensions.

Core 2 Duo Conroe is the chip that was to include EM64T 64-bit extensions

---

### Post by fireboxtester on 2006-09-02
I made a wiki page to put all of the information about this issue in one place:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

As you can see it's a pretty major issue.  There are already 3 bugs and at least 9 forum threads regarding this.  Hopefully we can get this fixed for Edgy.  (I'm going to test Knot 2 later tonight)

---

### Post by John.Michael.Kane on 2006-09-02
fireboxtester jmicron support was to be added to edgy. 

If you do happen to test edgy,and it's all cleared please let those user's know who are trying to get dapper working that they may have to move to edgy [COLOR="Red"]provided their machines are are not for production use[/COLOR]. 

As edgy is not classed as stable right now.

---

### Post by fireboxtester on 2006-09-03
> **SD-Plissken said:**
> fireboxtester jmicron support was to be added to edgy. 

If you do happen to test edgy,and it's all cleared please let those user's know who are trying to get dapper working that they may have to move to edgy [COLOR="Red"]provided their machines are are not for production use[/COLOR]. 

As edgy is not classed as stable right now.

I tested Edgy (Kubuntu Knot 2) last night and I just hit a blank screen.  Details on Wiki page. I'm meaning to test the Alternative Install so I can get a more detailed error.  Is there any way to tell if it's supposed to be in Edgy yet?

---

### Post by bsodmike on 2006-09-08
> **Cynical said:**
> And yes if you download the amd64 version of ubuntu you can get a fully working 64-bit distro. I'm posting this from a Core 2 Duo E6300. (after installing over the internet using instlux)

How did you do this?  I'm willing to give this ago and get Ubuntu running on my E6600 :)

Thanks! 
Mike

---

### Post by incubus on 2006-09-08
Hey,

I've got a Core 2 Duo E6400 with a Gigabyte motherboard running Ubuntu Dapper AMD64 flawlessly. Out-of-the-box hardware detection was MUCH better than in Windows, which is not surprising.

The usual speedstep controls work too, though the lowest step is 1.6Ghz (actually, I don't even know if this is really the minimum step).

I also tested Edgy and had no problems whatsoever.

I'm running kernel amd64-generic, I haven't tested the xeon one, which is also available.

best,
incubus

---

### Post by bsodmike on 2006-09-09
How did you manage this?  If I try to boot off the CD it just halts due to the JMicron issue!

Did you alter anything in the BIOS or pass any arguments to the installer?

Thanks!

---

### Post by incubus on 2006-09-09
Hey Mike,

I was lucky and had absolutely no problem here. I'm not aware of this jmicron issue, what is it?

When I got my laptop, Breezy didn't behave very well. I then decided to take chances and test Dapper, which worked perfectly. I'd give you the same suggestion, try Edgy. Even if it's just to see what you'd have to fix to make Dapper run.

Take care,
incubus

---

### Post by bsodmike on 2006-09-10
Thanks Incubus,

I may end up waiting till Edgy Eft goes final in October as the JMicron controller in all the new Core 2 Duo mainboards is not supported other than in the 2.6+ kernels.  IDE is no longer native and whatever IDE is routed through this JMicron IC and therefore during install the installer dies as the optical drive *is* connected to IDE (for most people at least!)..

There seems to be a USB key install method but seems like too much trouble :P

---

### Post by lazerradial2003 on 2006-09-11
Anyone know if this has been resolved yet? Just about to buy something with the 965 chipset and really dont want to have to go back to windows but due to my budget i ahve to stick with IDE CD + harddrive

---

### Post by jespdj on 2006-09-11
I have an Intel Core 2 Duo E6600 too on an Asus P5B Deluxe motherboard, with CD-ROM drive connected to the JMicron IDE controller.

I can't boot from the Live CD because of the kernel bug, so I put the contents of the CD on a Compact Flash card and booted from that. It's not that difficult; see the instructions here: [Installation from USB stick](https://help.ubuntu.com/community/Installation/FromUSBStick).

Ofcourse you can also solve the problem by using a CD-ROM drive with SATA interface instead of IDE.

The AMD64 version of Ubuntu works on any Intel processor that supports EM64T, which includes the Core **2** Duo (Conroe for desktops or Merom for laptops, the Pentium D, and later versions of the Pentium 4 and Celeron D. Lookup the specs for your particular processor to see if it has EM64T. The Core Duo (Yonah) does NOT support EM64T.

[EM64T](http://en.wikipedia.org/wiki/EM64T) is Intel's implementation of AMD64.

---

### Post by jespdj on 2006-09-11
> **lazerradial2003 said:**
> Anyone know if this has been resolved yet? Just about to buy something with the 965 chipset and really dont want to have to go back to windows but due to my budget i ahve to stick with IDE CD + harddrive
Is your budget really that tight? You can buy a Samsung SATA CD-ROM drive in local shops here for just 39 Euros (about US$ 49).

---

### Post by incubus on 2006-09-11
lazerradial,

If you are conservative and in a hurry, I would suggest getting a card based on the intel 945 chipset, as it has been around for a while. As I told Mike, everything works out of the box here. I'm also using an IDE CD drive.

If you end up getting the 965 chipset, I bet very soon somebody's gonna come up with a solution. Of course, all this is directly related to the quantity and quality of the users getting these specs and working on the issues. But with all the (arguably reasonable) hype about core 2 duo, I'd say it will happen soon.

incubus

---

### Post by incubus on 2006-09-11
jespdj,

May I ask what is your samsung drive model? I'm interested in buying one that is SATA myself.

incubus

---

### Post by lazerradial2003 on 2006-09-12
My budgets quite tight right now, Im off to uni in a few days and my motherboard died on sunday night leading to a somewhat forced and very hurried upgrade, i'll be upgrading to SATA in a month or so but just want to get something going for now, have bought a SATA -> IDE  converter off ebay for £8 so hopefully that will do for now. I can't imagine that this issue won't be solved for edgy since pretty much all of the core 2 motherboards have this problem....

---

### Post by jespdj on 2006-09-12
> **incubus said:**
> jespdj,

May I ask what is your samsung drive model? I'm interested in buying one that is SATA myself.

incubus

It's the [Samsung SH-W163A](http://www.samsung.com/Products/OpticalDiscDrive/DVDWriter/OpticalDiscDrive_DVDWriter_SH_W163A.asp), a dual layer DVD writer with SATA interface.
In the Netherlands you can buy it for 39 Euros at [Alternate](http://www.alternate.nl/html/productDetails.html?baseId=1389&artno=cebu01) (a shop which happens to be close to where I live).

I did not buy this one myself, because I have a good Sony dual layer DVD writer that I'm happy with; instead, I installed Ubuntu by booting from a CompactFlash card.

---

### Post by lazerradial2003 on 2006-09-12
I'd be interested as well, have been having trouble finding anywhere that stocks SATA optical drives....

---

### Post by Menyus on 2006-09-12
My configuration is pretty much the same, ASUS P5B, Intel E6400, etc. I succesfully installed the ubuntu-6.06.1-desktop-amd64.iso using my external USB2 DVD burner.

---

### Post by DNVRDV on 2006-09-12
P5B e6400 here to.... Can't install any linux distro or Vista......  USB CD-rom.......... DUH!!!!!!!!!!!!!

---

### Post by John.Michael.Kane on 2006-09-12
Have you all given edgy a try?

also those who have tried other distro's have they all been 64bit only? 

have you tried installing the 32bit version of some distros?

Also as someone pointed out you could always try to use an addon card that may allow some form of linux support. till these issues with the chip can be sorted out.

---

### Post by lazerradial2003 on 2006-09-13
So far I've only tried Ubuntu 32 Bit edition, but i think a fair few people have tried quite a lot fo stuff including edgy, gentoo, fedora and so-on and from what i can gather it's a kernel issue.

My budget is very limited at the moment so i'd quite like to avoid an add-in card especially since i'd have to try and find one ubuntu likes....

---

### Post by jespdj on 2006-09-13
The problem with the JMicron controller is [bug #57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502) and is fixed in kernel 2.6.18.

AFAIK Edgy has kernel 2.6.17 (the docs [for Knot 2](http://www.ubuntu.com/testing/knot2) say: "Edgy will ship with the 2.6.17 kernel..."), so it will probably still not work with Edgy Knot 2.

Is the final version of Edgy also going to ship with kernel 2.6.17, or with a newer version? I think this fix is quite important, because there are a LOT of people who buy new computers now that have the JMicron chip (Intel's P965 chipset doesn't support PATA natively so different manufacturers are using the JMicron controller on their motherboards to add IDE support).

---

### Post by SFAOK on 2006-09-13
> **jespdj said:**
> The problem with the JMicron controller is [bug #57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502) and is fixed in kernel 2.6.18.

AFAIK Edgy has kernel 2.6.17 (the docs [for Knot 2](http://www.ubuntu.com/testing/knot2) say: "Edgy will ship with the 2.6.17 kernel..."), so it will probably still not work with Edgy Knot 2.

I'm pretty sure Knot 2 is confirmed as not working (see the wiki). The bug page says the fix has been backported which I think means the fix has been applied to an earlier kernel (but could be very wrong here ;)). I'm hoping this will make it into Knot 3 and we can see if there's been any progress.

The only problem after that is that we're "stuck" with Edgy or above... As excited as I am for Edgy, it would be nice to know that if I prefer Dapper's stability over Edgy's new features that I could go back to Dapper... Is or will there be a way to do this?

---

### Post by lazerradial2003 on 2006-09-13
Don't know much about this but is it likely to be possible to get a copy of the 2.6.18 kernel and use that in dapper/ edgy? Alternatively does anyone have information about the Jmicron fix being backported and what this entails? 

It would be nice to be able to choose between dapper and edgy but tbh i'd be happy with either since im about to have to install XP (groan) because I want some sort of an OS on my new box....

---

### Post by ph8 on 2006-09-15
I've just purchased a new server with this chipset, obviously I wouldn't want to soil my server with a bulky desktop install so I'm hoping Edgy Knot 3 (which *should* have the chipset patches backported in the kernel, if I'm interpreting info in this thread right) will solve all my problems. 

Has anyone else tried the boot from USB stick option? I tried it on a hard disk with 3 partitions (one of which i formatted to fat16 and marked bootable as specified) and I couldn't boot to it with my P5B i956... :s

ph8

---

### Post by ArizonaKid on 2006-09-16
Just to add for reference.

I just got a [Sony Vaio FE770G]("http://b2b.sony.com/Solutions/product/VGN-FE770G") and installed the AMD 64 version of Ubuntu off the live CD with zero problems.  My computer has a Intel Core 2 Duo Chip (Merom) 1.83Ghz chip.

---

### Post by ph8 on 2006-09-16
I believe it's the motherboard that poses the problem - for anyone still interested i'm told the fix for this will be in Monday (the 18th's) Daily Build of Edgy - I hope it works!

---

### Post by amorangi on 2006-09-16
I hope that's true - I've got a very expensive paperweight which I'd really rather worked. Where did you find that out from (about Edgy daily build on Monday)?

---

### Post by ph8 on 2006-09-18
I spoke to Ben Collins on IRC, a daily build hasn't appeared yet though so i'm starting to wonder wtf's going on :s

---

### Post by übertötung on 2006-09-18
Ubuntu 6.10 (Edgy Eft) Knot 3 is available here:
[http://cdimage.ubuntu.com/releases/edgy/knot-3/](http://cdimage.ubuntu.com/releases/edgy/knot-3/)

I don't know if it works though.  My motherboard was DOA when it arrived.  Hopefully this problem will be solved by the time I get the replacement.

---

### Post by ph8 on 2006-09-21
> **übertötung said:**
> Ubuntu 6.10 (Edgy Eft) Knot 3 is available here:
[http://cdimage.ubuntu.com/releases/edgy/knot-3/](http://cdimage.ubuntu.com/releases/edgy/knot-3/)

I don't know if it works though.  My motherboard was DOA when it arrived.  Hopefully this problem will be solved by the time I get the replacement.

It doesn't. I'm hoping that tomorrow's build of the daily edgy cd image (22nd) will contain all the fixes necessary to get this on the move, here's too hoping!

---

### Post by v8YKxgHe on 2006-10-26
Well I can't get Edgy to install on Core 2 Duo E6600 and Abit AB9 - and from this [https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support) it looks like the only way to install Edgy is by 

"Copy the contents of the Ubuntu CD to your flash drive" ...... Yes assuming you have a USB stick big enough ](*,) 

Well geeeee, I'm now stuck Ubuntu-less because of this. Great.

---

### Post by kthakore on 2006-11-14
if I got an intel dual core 930 would I have to install x64 ati drivers and everything x64 or only the kernel x64.

---

### Post by RAOF on 2006-11-14
> **kthakore said:**
> if I got an intel dual core 930 would I have to install x64 ati drivers and everything x64 or only the kernel x64.

You wouldn't even need to install the x86-64 kernel.  But if you do, then yes, you will need* 64bit binaries for everything.

* Ok, not actually **need** as such.  But everything you install properly (ie: through aptitude/apt-get/synaptic/etc) will be x86-64.

---

