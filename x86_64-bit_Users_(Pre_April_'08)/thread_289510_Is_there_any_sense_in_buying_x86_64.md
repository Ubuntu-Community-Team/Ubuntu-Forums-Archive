---
title: "Is there any sense in buying x86_64?"
date: 2006-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by chaosgeisterchen on 2006-10-31
Good morning.

As I have a machine with an 64bit CPU (as many people have) I am still bound to using i386. I really want to use x86_64 but there is no advantage in it as it seems. More disadvantages concerning i386 apps.

So - what is the software world thinking about? 64bit was proclaimed to be the future but no one seems to be really using it profitably. Is it lost input to spend money on buying 64bit-CPUs? Or will there be ever perfect 64bit-support with Ubuntu, making it perfectly optimized towards 64bit. What are you thinking about this issue?

I would be very happy to know how to make the best out of my hardware ;)

---

### Post by mips on 2006-10-31
Get a 64bit system, it will future proof you.

The problem is more of a Ubuntu/Debian one as it does not currently support Multi-Arch which makes things pretty tricky.

There are other Distros and OSs out there that DOES support multi-arch.

[http://ubuntuforums.org/showthread.php?t=254552](http://ubuntuforums.org/showthread.php?t=254552)

---

### Post by chaosgeisterchen on 2006-10-31
As far as I remember Gentoo is among them, ain't I right?

Well, another question:

Are Intels processors 64bit? I currently have a Centrino Duo so I do not know.

---

### Post by Reshin on 2006-10-31
> **chaosgeisterchen said:**
> As far as I remember Gentoo is among them, ain't I right?

Well, another question:

Are Intels processors 64bit? I currently have a Centrino Duo so I do not know.

Centrinos are 32bit

IMHO gentoo is the only properly 64bit-capable linux

---

### Post by chaosgeisterchen on 2006-10-31
Okay, I can live with their i686-architecture.

I have an sempron 64 at home which I will surely once test with Gentoo. See what advantages can be got out of it.

---

### Post by mips on 2006-10-31
> **chaosgeisterchen said:**
> Okay, I can live with their i686-architecture.

I have an sempron 64 at home which I will surely once test with Gentoo. See what advantages can be got out of it.

Instead of gentoo you might want to look at Sabayon Linux which is based on gentoo and very nice. I really liked it for the brief moment I used it and yes i used the 64bit version. i think this is a distro to watch and keep your eye on.  [http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)

As far as i know the core due 7 core 2 due cpus are 64bit but then again i dont know that much about Intel

---

### Post by daou on 2006-10-31
There aren't many advantages to 64-bit with today's programs/hardware. Once you start breaking the 4GB limit on RAM and memory usage in applications, you will have no other choice than to use 64-bit arch, but I wouldn't say this is something that you need to worry about in the near future. Or even in the near distant future ;).

---

### Post by kuja on 2006-10-31
Yeah, 64-bit support could use some work, both with the actual problem (software that is 32-bit only) and the potential workaround (dpkg/apt multiarch support).

Aside from the increased RAM limit, in its current state it does offer a few advantages, at least to some. Rendering, encoding, and complex math can see a decent boost. For example blender gets a good boost of 20-30% from 64-bit.

---

### Post by scott stanley on 2006-10-31
Mandriva

---

### Post by usernamed on 2006-10-31
I've found it frustrating that certain packages don't seem to have 64 bit counterparts, but surely if you're buying a processor now, they're all 64 bit?  

Give the software chaps a bit of time to catch up.  Eventually 64-bit will become the standard, just like after the switch from 16  bit to 32 bit computing.

---

### Post by Kilz on 2006-10-31
> **Reshin said:**
> Centrinos are 32bit

IMHO gentoo is the only properly 64bit-capable linux

SuSE is also among the best multiarch distro's. 10.1 had some problems with package management because of the new package manager. But ti was still as easy as clicking on what version and bit you wanted to run for any application. 10.2 due in Dec should really be good. With Ubuntu continuing to ignore 64bit users I will be giving it a try.

---

### Post by chaosgeisterchen on 2006-10-31
SuSE? Ain't it dead slow?

---

### Post by Kilz on 2006-10-31
> **chaosgeisterchen said:**
> SuSE? Ain't it dead slow?

I dont remember the slowness, but I did stop using it when 10.1 came out. So it has been awhile. But it is one of the best multiarch setups. It is also a lot easier to install than Gentoo.

---

### Post by BIGtrouble77 on 2006-10-31
I've been using dapper64 since it came out.  I'm not sure what advantages I've had, if any over the i686 arch. I only have 2gb of memory in my laptop.  

I haven't had much trouble getting 32bit software working.  I have google earth, vmware, cedega, swiftfox 32bit mplayer and several other 32bit apps working perfectly fine.  My machine is also highly customized becuase I use it for development for several different platforms.  I've run into very few headaches so far.  Nothing I couldn't solve.  So I would definately say that 64bit Dapper is very well supported.

I haven't tried 64bit Edgy yet.  I do also use gentoo on my servers and it's a no brainer to go 64bit there.  I would definately suggest using a 64bit distro with the turion to get every ounce of performance out of it.

---

### Post by chaosgeisterchen on 2006-11-01
I will definately try several of them out in the future. SuSE 10.2 looks interesting if the KDE support is great as always.

---

### Post by annihilation on 2006-11-04
Hi, I'm using the 64 bit distro of ubuntu dapper. Could you please tell me how to get google earth working. I cannot seem to get it to work.

---

### Post by sloggerkhan on 2006-11-04
First of all, I  would not use SUSE, they are now an M$ bitch ruining FOSS. I have windows x64 cause it was free for me. Nothing special. Some apps don't work with it in the way of AV/Firewalls, but most stuff does. Drivers don't always exist either, or function differently than the 32 bit drivers.

I've used gentoo 64 bit, and I don't remember it being too notable, but than I don't think I compiled in all of the features I should have. Still, gentoo is a great distro. Sabion sounds cool, but haven't tried it.

I had 64 bit ubuntu, but I don't remember much about it other than it being easier to use than gentoo... ;).

---

### Post by Kilz on 2006-11-04
> **sloggerkhan said:**
> First of all, I  would not use SUSE, they are now an M$ bitch ruining FOSS. I have windows x64 cause it was free for me. Nothing special. Some apps don't work with it in the way of AV/Firewalls, but most stuff does. Drivers don't always exist either, or function differently than the 32 bit drivers.

I've used gentoo 64 bit, and I don't remember it being too notable, but than I don't think I compiled in all of the features I should have. Still, gentoo is a great distro. Sabion sounds cool, but haven't tried it.

I had 64 bit ubuntu, but I don't remember much about it other than it being easier to use than gentoo... ;).

Yes my comments recommending SuSE came before the Novell-Microsoft deal that has been in the news lately. My first linux distro was SuSE. I had planned on trying 10.2 when it was released in December. I wont even download it now. SuSE is a good distro, its got fantastic multiarch support. Maybe someone will fork it now.

---

### Post by sloggerkhan on 2006-11-05
Off topic, but I like the watchmen avatar. And with vista so close, it seems like buying a MS OS now is especially pointless.

---

### Post by Kilz on 2006-11-05
> **sloggerkhan said:**
> Off topic, but I like the watchmen avatar. And with vista so close, it seems like buying a MS OS now is especially pointless.

Thanks, Im a big comics fan. The Watchmen was one of my favorite series. :D 
IMHO buying a MS OS anytime is a waste of money. I never have bought one by iteself. Like most people I have gotten the ones I have preinstalled on the computers I buy(yes I know the cost may be hidden). I think thats going to be a problem for Vista. XP is very good(for a MS OS), and people may just wait untill they get their next computer instead of buying it as an upgrade.
Even so if I were to get a new computer with Vista, I dont think I would use it. I removed XP media center long ago, and linux is all thats left. :D

---

### Post by sloggerkhan on 2006-11-05
LoL. I am an enineering student at the moment, (though probably changing major to CS), and I get free M$ software. Otherwise my laptop came with windows, and I have enough space for probably 5 OS on it, though I only have 3 setup. So I keep windows64 as one of them. It's nice occasionaly as I can't stop playing with linux installs, which means they usually don't last more than a couple of weeks, since I don't really know what I'm doing.

Yeah, I like comics a fair bit, too. I like Watchmen, V for Vendetta, Sandman, Preacher, Calvin and Hobbes, Get Fuzzy, and Fox Trot. Wolverine is pretty cool, but most of his stories are lousy.

But I doubt I will ever own a computer running vista...

---

### Post by Kilz on 2006-11-05
> **sloggerkhan said:**
> LoL. I am an enineering student at the moment, (though probably changing major to CS), and I get free M$ software. Otherwise my laptop came with windows, and I have enough space for probably 5 OS on it, though I only have 3 setup. So I keep windows64 as one of them. It's nice occasionaly as I can't stop playing with linux installs, which means they usually don't last more than a couple of weeks, since I don't really know what I'm doing.

Yeah, I like comics a fair bit, too. I like Watchmen, V for Vendetta, Sandman, Preacher, Calvin and Hobbes, Get Fuzzy, and Fox Trot. Wolverine is pretty cool, but most of his stories are lousy.

But I doubt I will ever own a computer running vista...

Yes I alos have enough room for 5 OS's (200gig). But Ubuntu is the only one on it now. Even if I got the software for free(as in beer) I dont think i would use it. There is so much free software and it is ususaly high quality.

Right now Im reading the civil war stuff from Marvel and Im enjoying the new creeper and martian manhunter series from DC. I agree on the lousy writing of Wolverine, but IMHO thats because Marvel has figured out that anything with his name on it sells no matter how bad it is.

---

### Post by pony-tail on 2006-11-05
I do not see any real advantage at present Running a 64bit OS .
I paid my Micro$oft Tax (the "free"-NOT comes with the machine version) and got XP64 (not well supported at all by M$ or the hardware vendors ) pretty much a waste of harddrive space not to mention the ugly OEM M$ sticker on the top of my nice new Sonata case .
Ubuntu "Dapper 64" has given me no grief at all - but does not seem any faster than "Dapper 32"
Ubuntu "Edgy" does not play nice with my Hardware (nVidia sata controller and Radeon X850XT-PE video card )
Gentoo 64 works well on this machine but is too easy to break and too time consuming to fix after I break it - Gentoo feels to be much faster !
SuSE 10.2 beta would not even install on my machine - it consistently detects my onboard nVidia controller as a Silicon Image raid (says sil 3112) The guys on their forum were a little abrupt for my liking as well - very much unlike the Gentoo forum or the Ubuntu forum .
But so far I have found that SLAMD64 and Ubuntu "Dapper" have been the least problematic.
As for Vista beta 64 The machine locked up every time I tried to run anything 3D (possibly ATI drivers ) but no way will I be buying Vista it is an overly bloated slightly sluggish (My machine is an A64 X2 4600 with 2 gig ram on an nForce 4 mobo )I would not call it lame - I know that I am talking about a beta here but please !
So I at present have a drive installed with "Dapper" and a couple of Seagate 40 gig Satas that I plug in and install what ever come out that intewrests me - Still looking for that perfect soloution . Meanwhile all my important stuff is done on my old 32bit Athlon XP 3000+ powered Shuttle ("Dapper" and Win2k dual boot)

---

