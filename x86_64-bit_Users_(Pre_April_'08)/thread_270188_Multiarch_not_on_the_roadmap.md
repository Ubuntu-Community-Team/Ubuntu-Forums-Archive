---
title: "Multiarch not on the roadmap"
date: 2006-10-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kilz on 2006-10-02
I have had an interesting discussion on the Developers mailing list. The discussion is winding down. But I would just like to let every 64bit user know that there are no plans to implement multiarch. In case you want to make sure you can read the words of the lead developer.

[http://archives.free.net.ph/message/20061002.225433.c68da4dd.en.html](http://archives.free.net.ph/message/20061002.225433.c68da4dd.en.html)

There is also an interesting side note that I am at present getting a answer regarding them stopping 64bit users from modifying our installs with 32bit applications. You can read my response to the above email here.

[http://archives.free.net.ph/message/20061003.004742.e125068c.en.html](http://archives.free.net.ph/message/20061003.004742.e125068c.en.html)

I will let the rest of the 64bit system owners know what the response was to this email as it may well impact on your decisions to use Ubuntu in the future or projects that may rely on the functionality.

---

### Post by basementgeek on 2006-10-02
Well that suxors!  It would seem that 64 bit is indeed the future, (which is why I built this box!) and not even planning on multiarch might hamper the widespread usage of that version, which would in turn slow development of 64 bit apps......and thus begins the vicious cycle.

I guess that you could still get 32 bit functionality if they remove it, but that might sour a lot of potential users from using it at all.

---

### Post by John Jason Jordan on 2006-10-02
> **Kilz said:**
> I have had an interesting discussion on the Developers mailing list. The discussion is winding down. But I would just like to let every 64bit user know that there are no plans to implement multiarch.
Does "multiarch" mean running 32-bit apps on 64-bit Ubuntu?

---

### Post by John.Michael.Kane on 2006-10-02
multiarch would in theroy allow users to install on the fly any 32bit package reguardless of it's build. there would be no real need for one to compile a package that was made for 32bit for 64bit.

Example: if you have a dev who only machine is 32bit based,and the only packages he/she can put out will be 32bit. you the enduser are running 64bit only,and want to run that program, your normal options would be to compile said program from source for your architecture. with multiarch support you would not have to do that.

Hope that clears it up a bit.

---

### Post by RAOF on 2006-10-02
> **John Jason Jordan said:**
> Does "multiarch" mean running 32-bit apps on 64-bit Ubuntu?

Yes.

@Basementgeek: **Almost** every open-source project builds under x86-64.  The notable exception, of course, is WINE, which can't be built as a 64bit binary for obvious reasons.  You don't have to "develop 64bit apps": well coded apps will build **whatever** (reasonable) architecture you use.  32bit compatibility is really **only** necessary for non-free (as in "freedom") stuff.

@Kilz - You know, we could provide 32bit AMD64 packages to Universe (using the REVU server).  It'd only be for Edgy/Edgy+1, but they'd get in there.  You **could** make a Firefox32 package, an AMD64 (32bit) Wine package would be quite easy (we'd just need to package the lone 32bit library not packaged elsewhere, and add it as a dependency), etc.  One of the properties of being a "community distro" is that it's actually quite easy for members of the forum/launchpad to get packages into Universe, as long as you're willing to do the work.

---

### Post by Kilz on 2006-10-02
> **RAOF said:**
> Yes.

@Basementgeek: **Almost** every open-source project builds under x86-64.  The notable exception, of course, is WINE, which can't be built as a 64bit binary for obvious reasons.  You don't have to "develop 64bit apps": well coded apps will build **whatever** (reasonable) architecture you use.  32bit compatibility is really **only** necessary for non-free (as in "freedom") stuff.

@Kilz - You know, we could provide 32bit AMD64 packages to Universe (using the REVU server).  It'd only be for Edgy/Edgy+1, but they'd get in there.  You **could** make a Firefox32 package, an AMD64 (32bit) Wine package would be quite easy (we'd just need to package the lone 32bit library not packaged elsewhere, and add it as a dependency), etc.  One of the properties of being a "community distro" is that it's actually quite easy for members of the forum/launchpad to get packages into Universe, as long as you're willing to do the work.
Yes and I am thinking along those lines.  [I have already created a wine package.]("http://home.comcast.net/~ubuntu64user/wine_0.9.22_6.06-1_amd64.deb") That is , as long as they dont take the ability to run 32bit applications away.

---

### Post by RAOF on 2006-10-02
> **Kilz said:**
> Yes and I am thinking along those lines.  [I have already created a wine package.]("http://home.comcast.net/~ubuntu64user/wine_0.9.22_6.06-1_amd64.deb") That is , as long as they dont take the ability to run 32bit applications away.

They said the ia32-libs-* would end up in Universe at worst.

---

### Post by Kilz on 2006-10-02
> **RAOF said:**
> They said the ia32-libs-* would end up in Universe at worst.

Yes but if you read what in that reply I linked to. I quoted from a email he sent me, that wasnt on the list. It says they may take away the ability to force in 32 bit applications. If they make it like Breezy where 32bit applications didnt run. I think it will be really bad.
I really cant understand the developers at all. To me they seem to want to make the amd64bit version so bad no one will use it.

---

### Post by John Jason Jordan on 2006-10-03
> **Kilz said:**
> Yes but if you read what in that reply I linked to. I quoted from a email he sent me, that wasnt on the list. It says they may take away the ability to force in 32 bit applications. If they make it like Breezy where 32bit applications didnt run. I think it will be really bad.
I really cant understand the developers at all. To me they seem to want to make the amd64bit version so bad no one will use it.
It's a marketing issue. Clearly, everyone wants to move to 64-bit. Some think that making it difficult or impossible to run 32-bit apps will force developers to create 64-bit versions of their apps. But if the result is fewer people adopting 64-bit, there will be less incentive for developers to create 64-bit versions of their apps. Chicken and egg problem. 

Personally, I run Dapper AMD-64 and there is nothing I need that moving to 32-bit would help with. Sure, there are things I need that I can't run, but they wouldn't run in 32-bit either -- e.g., CorelDRAW 9.0 under CrossOver Office or WINE.

If Edgy will not run some of the 32-bit apps I use now (I don't even know which of my apps are 32-bit), then I'll just stick with Dapper. All this will become clearer after Edgy is released.

---

### Post by RAOF on 2006-10-03
> **John Jason Jordan said:**
> ...
If Edgy will not run some of the 32-bit apps I use now (I don't even know which of my apps are 32-bit), then I'll just stick with Dapper. All this will become clearer after Edgy is released.

Unless you've manually installed an application by --force-architecture ing an i386 deb, all the programs you're running are 64bit.  With the exception of Open Office, **everything you can install from the repositories is 64bit**.  Perhaps by the time Edgy is released the problems they have with the 64bit build will be worked out, and **everything** in the repos will be 64bit.

---

### Post by kleeman on 2006-10-03
I have been reading the developers list on this issue and also the kernel issue as well as following interviews of sabdfl and several things occur to me:

1) The developers appear to be attempting to simplify their lives. Edgy will no longer support specialty kernels (eg xeon etc etc). They are also attempting to "simplify" the 64 bit support as noted by kilz above. 

2) sabdfl is complaining about developers being overwhelmed by the number of bugs coming in from the HUGE and rapidly expanding user base. I suspect that this is one of the reasons developers are looking to simplify their lives as in points in 1) above.

3) I noticed on the developers list that a number of the (main) developers were running 64 bit as their main platforms. This is always a good sign for the future imho. I have been told after lodging several bugreports that my problem got fixed because a developer had it as well.

4) The developers were not very sympathetic to kilz's concerns because the issues were "minor" in their eyes (flash, win32 codecs, mplayer, googleearth etc etc) and probably they could fix them themselves and they probably think that users who want to "experiment" with 64 bit are better than the average windows newbie in sorting things out. I don't neccessarily agree with this I am just discerning their attitude at present.

5) The future is definitely 64 bit as the next Windows and OSX releases will have much better support. Whether they admit it or not on a developers list ;-) (devs tend to be acerbic and macho in my experience) this will place significant pressure on developers of Ubuntu to follow suit probably in the next year or two I would guess.

---

### Post by John Jason Jordan on 2006-10-03
> **RAOF said:**
> Unless you've manually installed an application by --force-architecture ing an i386 deb, all the programs you're running are 64bit.  With the exception of Open Office, **everything you can install from the repositories is 64bit**.  Perhaps by the time Edgy is released the problems they have with the 64bit build will be worked out, and **everything** in the repos will be 64bit.
Did I not read in this forum that 64-bit OO.o is in beta? Hopefully that will be available concurrently with Edgy. As for the rest, the only things I installed with --force-architecture are RealPlayer 10, Opera, and Adobe Reader 7.08. So I guess all I have to watch for is to make sure that I can still run those on Edgy before upgrading. In fact, I love my Dapper amd-64 so much that I am not sure I care about upgrading.

---

### Post by kleeman on 2006-10-03
I installed realplayer 10.0.7 and acroread 7.0.8 from the vendors directly and they worked perfectly on amd64 (acroread needed a bit of rejigging, see the sticky above).

---

### Post by fabertawe on 2006-10-03
> **John Jason Jordan said:**
> So I guess all I have to watch for is to make sure that I can still run those on Edgy before upgrading. In fact, I love my Dapper amd-64 so much that I am not sure I care about upgrading.

What is actually involved in upgrading to Edgy? I came straight in on Dapper and have no experience of a major upgrade.

I've compiled GYachI as 32bit and installed loads of 32bit libs to get it to work so I may have to stick with Dapper also.

Cheers ... Paul

---

### Post by gurgle on 2006-10-03
wow, looks like i might have to move away from ubuntu/debian to get a mature multiarch environment, that is a shame.

---

### Post by Kilz on 2006-10-03
> **gurgle said:**
> wow, looks like i might have to move away from ubuntu/debian to get a mature multiarch environment, that is a shame.

Unfortunately you may be correct. While distros like SuSe are now fully multiarch Debian/Ubuntu is dragging its feet. I did get a sort of non answer.
[http://archives.free.net.ph/message/20061003.085253.36f76aba.en.html](http://archives.free.net.ph/message/20061003.085253.36f76aba.en.html)
That while there are no plans of adding it, they could change their minds in the future because its kind of like on indefinite postponement.
I think I will stick around as long as the ability to run 32bit is avilable. I really like the forums and people. The development is another story.....

---

### Post by fatsheep on 2006-10-03
What I don't get is how Debian (particularly the package system) is of such good quality when their development cycle is so slow...

---

### Post by Kilz on 2006-10-03
> **fatsheep said:**
> What I don't get is how Debian (particularly the package system) is of such good quality when their development cycle is so slow...

You answerd the question. Their development cycle is slow. This gives the package maintainers a long time to get packages ready.

---

### Post by gurgle on 2006-10-03
kinda OT: what multiarch, 64-bit linux distro is the best right now?

---

### Post by Kilz on 2006-10-03
> **gurgle said:**
> kinda OT: what multiarch, 64-bit linux distro is the best right now?

For ease of use in installing applications of different architecture I would say SuSE. To install a different architecture of any application you simply click a radio button in yast. 
But version 10.1, the current version had package management issues because they did extensive work in a little amount of time. They may have been fixed, its been 4 months since I used SuSE. I can bet 10.2, scheduled for release in dec will fix any of those issues that remain. Suse is also a little slower in the 10.1 version. But XGL is very easy compared to Ubuntu to setup.
I also understand Gentoo is good, but it is a royal pain to install. Fedora is also multiarch, but I have limited experience with it.

---

