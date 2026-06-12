---
title: "Any difficulties in AMD x64 for newbie?"
date: 2006-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Brian Boyko on 2006-12-12
I'm considering shifting from Windows to Ubuntu.  The only things keeping me on Windows is Photoshop and games (mostly Photoshop.)  The GIMP is not yet a suitable replacement for the type of work I do. 

However, I'm wondering if I can't get a little more oomph out of my AMD Athlon64 3200+ chip if I go with a 64 bit OS; and for various reasons I'm not going to go with Windows XP 64 bit or Vista.  

I've run Ubuntu 32 bit with little to no problems (I was on Dapper at the time, and had some problems with USB drives; this should be fixed in Edgy from the documentation.)  Will 64 bit Ubuntu become problematic?

---

### Post by mand0 on 2006-12-12
I just installed Ubuntu 64 bit last night and I haven't really had any major problems.  Everything went quite smoothly.  The internet worked right away, USB flash drive worked, cd rom drive worked, installed nvidia graphics driver.  I suppose that the majority of the problems I will encounter will be when I try customizing further, but for the basics, they just worked.

---

### Post by radiobuzzer on 2006-12-12
It is very possible that you will have problems with the Flash player and Java plugin for Firefox, as well as some programs that cannot run with 64bit Linux, such as Matlab and Google Earth. Please look at the support forum to see which programs are difficult to be installed.

---

### Post by Kilz on 2006-12-12
> **Brian Boyko said:**
> I'm considering shifting from Windows to Ubuntu.  The only things keeping me on Windows is Photoshop and games (mostly Photoshop.)  The GIMP is not yet a suitable replacement for the type of work I do. 

However, I'm wondering if I can't get a little more oomph out of my AMD Athlon64 3200+ chip if I go with a 64 bit OS; and for various reasons I'm not going to go with Windows XP 64 bit or Vista.  

I've run Ubuntu 32 bit with little to no problems (I was on Dapper at the time, and had some problems with USB drives; this should be fixed in Edgy from the documentation.)  Will 64 bit Ubuntu become problematic?

Since you have installed the 32bit version and found problems. You know there is no such thing as a linux distro that doesn't have some setup you have to accomplish. Be it applications that need some setup or hardware. The 64bit version may have some setup you need to do. Its impossible to tell what you will need to do because every computer is different and so are the needs of the user. But there is nothing that is impossible in the 64bit version.

---

### Post by John.Michael.Kane on 2006-12-12
I second Kilz statment,and will add that most if not all apps one would use under 32bit ubuntu should installable under 64bit ubuntu provided you are up to reading a couple of howto's, and using the commandline.

---

### Post by iLoVe.cF- on 2006-12-16
Well.. im not 100% noob.. but.. my 64 bit install is the most the best install ive ever had.. i got some apps i cant install.. but.. 
googleearth is the only app i couldnt find any other app for.. :p

But else than that.. no problems at all =)

---

### Post by Azakus on 2006-12-17
For the ultimate easy time in Ubuntu, install Automatix2 and then install Swiftfox and all the plugins that go with it. That will give you flash, java, and other necessary codecs for an optimized build of Firefox.

---

### Post by Kilz on 2006-12-17
> **Azakus said:**
> For the ultimate easy time in Ubuntu, install Automatix2 and then install Swiftfox and all the plugins that go with it. That will give you flash, java, and other necessary codecs for an optimized build of Firefox.

That is a way to take a free and open source operating system and make it non free. If you want to do that, might as well keep running Windows.

---

### Post by Azakus on 2006-12-18
> **Kilz said:**
> That is a way to take a free and open source operating system and make it non free. If you want to do that, might as well keep running Windows.

Uh not really. The things Automatix installs exactly the same things you actually have a howto for in your sig (such as Flash and Java), and mplayer is released under GPL v2. I'm not quite sure what you would be objecting to. Unless you are saying that any addition of proprietary software that is still distributed freely is against some moral standing you have with the GNU/Linux philosophy, Automatix is the quickest way to set someone up with a fully functioning web browser to interact will nearly all available content. While I agree that using only FOSS software is indeed the most adherent to the GPL license that governs Linux and makes using it truly free, I have yet to see a perfect open source replacement for Flash, which is almost necessary for today's web browsing. Perhaps the new user who asked for help in this topic can eventually come to using only FOSS software, but until such time using proprietary software seems the only usable route.

---

### Post by Kilz on 2006-12-18
> **Azakus said:**
> Uh not really. The things Automatix installs exactly the same things you actually have a howto for in your sig (such as Flash and Java), and mplayer is released under GPL v2. I'm not quite sure what you would be objecting to. Unless you are saying that any addition of proprietary software that is still distributed freely is against some moral standing you have with the GNU/Linux philosophy, Automatix is the quickest way to set someone up with a fully functioning web browser to interact will nearly all available content. While I agree that using only FOSS software is indeed the most adherent to the GPL license that governs Linux and makes using it truly free, I have yet to see a perfect open source replacement for Flash, which is almost necessary for today's web browsing. Perhaps the new user who asked for help in this topic can eventually come to using only FOSS software, but until such time using proprietary software seems the only usable route.

Java is free, its been free for about a month. It is currently licensed under the gpl. Flash isnt free, but there is no non-free application that works as well as it does so it gets a pass from me. Swiftfox on the other hand isnt free as in freedom. Its builder takes the free Firefox code, doesnt add a thing to it. Then relicenses the binary under the proprietary Swiftfox license. This license restricts redistribution of Swiftfox, something that Firefox allows.
But Automatix doesnt just install this, it installs the proprietary rar, skype, Acrobat, non-free audio codec's and possibly illegal dvd codecs. 
Im not against some proprietary applications "if" the functionality isnt available in free software.  But most of these applications have free counterparts. Users of Linux should support free (as in freedom, not just cost) applications if they exist. Because if we send the message that its ok to sell out we lose out in the end.
And no, my howto isnt the same thing if you look at it. It installs one thing, offering the user the information so they can do it themselves. Automatix installs multiple applications. Sometimes to fast for a newbie to see. If there are errors, it leaves a newbie up the creek without a paddle. They will have no knowledge on what was done, so no idea on how to fix it.
Instead of promoting things like this to new people, imho we should be pointing them to sites [like this one]("http://www.monkeyblog.org/ubuntu/installing/") that give them the knowledge to do more for themselves.

---

### Post by Azakus on 2006-12-18
Automatix does not install those things by default. You can use Automatix and just install Swiftfox with the plugins for Swiftfox. You don't have to install anything else with Automatix. It just provides, at least for me, an easy way to install Swiftfox. Honestly, the swiftfox installer script is all that is really necessary, but the codecs are a nice plus anyway.

---

### Post by slicker on 2006-12-19
> **Azakus said:**
> Automatix does not install those things by default. You can use Automatix and just install Swiftfox with the plugins for Swiftfox. You don't have to install anything else with Automatix. It just provides, at least for me, an easy way to install Swiftfox. Honestly, the swiftfox installer script is all that is really necessary, but the codecs are a nice plus anyway.

If you install Swiftfox, you are installing non-free software. Firefox or better yet Iceweasel are better alternatives. Swiftfox limits freedoms that Firefox gives you. Since Swiftfox is based on Firefox one has to wonder why Swiftfox does this. It cant legally be included in repositories like Ubuntu's. You therefore miss out on security updates.
While you say its optional, there is no information in the installer that what you are in fact doing is installing non-free software. New users are likely to just install everything without that information.

---

### Post by fabertawe on 2006-12-19
> **slicker said:**
> If you install Swiftfox, you are installing non-free software. Firefox or better yet Iceweasel are better alternatives. Swiftfox limits freedoms that Firefox gives you. Since Swiftfox is based on Firefox one has to wonder why Swiftfox does this. It cant legally be included in repositories like Ubuntu's. You therefore miss out on security updates.
While you say its optional, there is no information in the installer that what you are in fact doing is installing non-free software. New users are likely to just install everything without that information.

[Swiftfox]("http://www.getswiftfox.com/") now has a [repo]("http://www.getswiftfox.com/debian.htm"), so therefore you won't miss out on security updates slicker. [Check it out]("http://www.getswiftfox.com/debian.htm").

Oh, and Swiftfox has been great for me and not limited **my** freedom one bit. Isn't it great to have a choice :D 

Paul

---

### Post by slicker on 2006-12-19
> **fabertawe said:**
> [Swiftfox]("http://www.getswiftfox.com/") now has a [repo]("http://www.getswiftfox.com/debian.htm"), so therefore you won't miss out on security updates slicker. [Check it out]("http://www.getswiftfox.com/debian.htm").

Oh, and Swiftfox has been great for me and not limited **my** freedom one bit. Isn't it great to have a choice :D 

Paul

While Swiftfox may have a repo. It isn't distributable from any distro. It cant be included in a distributions repository because of its license. The license isn't the MPL but the proprietary Swiftfox license. [According to its own license page]("http://getswiftfox.com/source.htm") it is non-free. It only has one pair of eye's looking at the code. That in itself is a security risk. Firefox in Ubuntu is taken care of by the security team. It is more secure.
Swiftfox restricts your freedom to redistribute the application to a friend. Redistribution is one of the four freedoms listed in the Free Software Foundations [definition of Free software.]("http://www.gnu.org/philosophy/free-sw.html"). So it in fact does restrict your freedom as well as every one else's. This is also important because the source code it is based on is free as in freedom. You can redistribute Firefox. 
Choice is all well and good, but if the application restricts your freedom, it is best to choose not to use it IMHO. Especially if the only benefit is that it renders pages [a fraction of a second]("http://www.apcstart.com/node/3097") faster than the application it is based on. If there was a great improvement, or it had features that Firefox did not, maybe it would be tolerable. But it just isn't worth it. Linux is all about freedom.

---

### Post by Kalibur on 2006-12-19
Well it depends on which version you install and the hardware makeup of you PC.  Here is what am running on at the moment and my problems.

Edgy Eft or ubuntu 6.10 64
AMD Athlon(tm) 64 Processor 3500+...........works very swiftly
NVIDIA GeForce FX 5500..................................Hell to setup if using a widescreen (1280x768_)
RAM single channel 512mb............................always occupied less than 10mb free
motherboard nForce3 am2 vista.....................no problems all plug n play
LG DVD wr...........................................................writes fine just can't play dvd movies
1x on board NIC................................................no problems except I can link to my Winxp pc
1x pci NIC...........................................................no problems except I can link to my Winxp pc
Creative vista Live webcam...........................not picked up at all, I dont even know where to start troubleshooting

Other issues
*no flash player web content cant install flash as there is no 64bit version for linux
*can't write to my ntfs partitions
*can't run Google Earth after install
*I was never able to play real media web content on any version of ubuntu even after installing realplayer and that helix player
*Nvidia drivers am using nvidia-setting now but that xserver-xorg is hell to deal am not sure about other graphics card brands

My advice to you -- if you are using a production machine stick to dapper drake 32bit, 
but if you got no hobbies go ahead and join the 64bit generation just make sure you have a working system to access the Internet for support and spicy up your terminal commands learn apt-get, aptitude and 'dpkg-reconfigure xserver-xorg' in case of driver failures.  I love gui and it was hell for me.

---

### Post by fabertawe on 2006-12-19
> **slicker said:**
> Choice is all well and good, but if the application restricts your freedom, it is best to choose not to use it **IMHO**.

Then don't use it. I will. Everybody's happy ;) 

Paul

---

### Post by Azakus on 2006-12-19
Huh. I never noticed the license was all restrictive like that. I guess I'm in the wrong then. However, it is still open **source**, just not open distributed binaries, so that might have been what threw me off. I might just try out IceWeasel then. Thanks for bringing this to my attention!

---

### Post by xopher on 2006-12-19
As long as I can use it for free Im happy.

---

### Post by aikishugyo on 2006-12-22
> **radiobuzzer said:**
> It is very possible that you will have problems with the Flash player and Java plugin for Firefox, as well as some programs that cannot run with 64bit Linux, such as Matlab and Google Earth. Please look at the support forum to see which programs are difficult to be installed.

I don't know about GoogleEarth, but Matlab works perfectly well on AMD64 architecture.
I have run all versions from 7.0 to 7.3.0 on my dual Opteron with no troubles.

---

### Post by Azakus on 2006-12-22
Google Earth works if you use the PLF repos.
```
## PLF
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
```

---

### Post by fabertawe on 2006-12-23
> **Azakus said:**
> Google Earth works if you use the PLF repos.

It's always worked for me. I just updated to version 4.0.2693 with Google's own download and it's still working here. I seem to be lucky with regard to a lot of the niggles others are having 8-[

Paul

---

