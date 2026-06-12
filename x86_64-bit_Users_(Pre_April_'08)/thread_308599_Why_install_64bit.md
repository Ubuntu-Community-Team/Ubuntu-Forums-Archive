---
title: "Why install 64bit?"
date: 2006-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by vikrant_me on 2006-11-28
I have a AMD athlon 3200+ 64 and i was wondering if there is an advantage (if any) of installing a 64bit version of 6.06 or 6.10 today as we speak.I hear the support for the 64bit aint as good nor do some of the programs work with the 64bit version

---

### Post by shartke on 2006-11-28
I would like to know the same thing :) I have been reading some forums and it seems like it might be worth it.:-D

---

### Post by crazedgremlin on 2006-11-28
I always thought there was a speed boost.  That's just me though :)

---

### Post by ByeByeBill on 2006-11-28
Unless youre using multimedia programs,like gimp,theres not much of an increase in speed.But thats not the reason to use it.64 bit OS's will be the future of computing,and it will come about sooner if we support whats out there now.True,some 32 bit programs wont work yet(like flash and java,there not nativly in 64 bit yet),but there are ways around this.I use Automatix2 to install 32 bit swiftfox and its plugins,and 32 bit java,and flash works this way.Its a pity we have to do this,but it will all be worth it down the road.Also,it shows Ubuntu that there is a market for 64 bit support now and in the future.Try it and see for yourself how well it works.

---

### Post by Cronjob on 2006-11-29
My opinion tends to be "why buy 64bit hardware if you're not going to run a 64bit system?". Granted, it's pretty much impossible to buy chips that aren't 64bit these days even though the operating systems for them are very lacking (especially in Windows), but considering how simple it is to get things working, I don't see why one would opt out of x64.

You can follow simple guides in these very forums to get most codecs working (though wmv doesn't seem to be working right now, but it had stopped working in dapper for me, too), including flash and java. Yeah, getting fancy desktop themes can be difficult to impossible sometimes, but other than window dressing, it's just fine. And you don't need to use any third party stuff to get it to work. You can use EasyUbuntu or Automatix... or you can just use apt-get and follow simple instructions. It's well worth it.

I'm still a little baffled as to the rather lacking x64 support in most distributions (of linux and others), considering that's all you can buy these days and has been for the last year and a half.

---

### Post by predaeus on 2006-11-29
When I bought my AMD Athlon 3200+ 64 I thought the turn would come quickly. But it didn't, so I switched back and forth between 64bit and 32bit Ubuntus because 64bit is not hassle free, even today it isn't.

I can practically do everything I need with my 64bit Ubuntu today. But if you depend on 32bit binaries, it becomes more difficult. For Flash I have to run a 32bit installation of Firefox. For some applications you have to provide shared 32bit libs, by downloading packages, unpacking them and copying to the appropriate locations, since Ubuntu does not allow the automatic installation of 32bit packages on a 64bit Ubuntu install yet.

I think for Java I've got a 64bit version of the Beta of the newest release. Community provided packages, like Beryl, took some time to be released for 64bit. So it isn't without problems yet, but like I said there is 64bit Nvidia drivers, Java and others are coming.

For me it also feels smoother. Maybe that's just my imagination, since theoretically it should not bring a great performance boost. If you are unsure, scan the 64bit forums about problems and try both live cds, to see if you see a difference.

---

### Post by H3g3m0n on 2006-11-29
I just ditched my x86_64 install for a normal x86 install.

It is possible to get a lot of the stuff working but it involves a lot of screwing around, also some parts seem to be buggier.

I haven't noticed any speed changes between the 2 (actually x86 seems faster to me, but probably just my imagination).

You will need to screw around to get flash working, a few codecs, wine. Also some of the 3rd party repos don't have x86_64 packages available.
The final thing that made me change was Wine, I need to build it myself to enable the Guild Wars cursor and the 64 bit version was looking like a lot more work.

I recommend sticking to a 32bit install, unless you are planning to transcode a lot of media or such.

---

### Post by Cronjob on 2006-11-29
Unless you're running some insanely obscure hardware, it's really not a big deal to get everything working. In 6.10 Kubuntu, I installed firefox32, had flash, sound, mp3 and my videocard (I run on a 30" ACD in 2560x1600) as well as my favorites, like basket, krusader, thunderbird64 and everything else working within an hour of installing Kubuntu (and that itself took less than an hour -- most of which was spent trying to figure out why using the GUI to manually chop up my hard drive so I could place /home and /var on a separate partition would cause it to want to erase my 300gb storage drive instead of the install drive).

And while I'm very experienced with linux (since 1998), I've never really used it on the desktop (I'm a Solaris guy), so this was only the second time I've ever installed Kubuntu and any linux window manager. So I'm not some uber genius.

Really, just take a read through the UbuntuGuide wiki for "getting started" and go through the tutorials people have written in the forums here for getting firefox32, flash, audio and codecs working and you'll be just fine with very little effort. I would actually say that doing it manually was even easier than using Automatix (which I had done once before).

Yeah, there's not a huge performance boost, but there is one and since it requires minimal effort, why not go for it? You paid for the hardware after all. And if you find that it's just too incredibly baffling or difficult in your environment, then just pop in an i386 install disk and have yourself up and running in 32bit by the end of your favorite sitcom.

---

### Post by Kilz on 2006-11-29
> **Cronjob said:**
> Unless you're running some insanely obscure hardware, it's really not a big deal to get everything working. In 6.10 Kubuntu, I installed firefox32, had flash, sound, mp3 and my videocard (I run on a 30" ACD in 2560x1600) as well as my favorites, like basket, krusader, thunderbird64 and everything else working within an hour of installing Kubuntu (and that itself took less than an hour -- most of which was spent trying to figure out why using the GUI to manually chop up my hard drive so I could place /home and /var on a separate partition would cause it to want to erase my 300gb storage drive instead of the install drive).

And while I'm very experienced with linux (since 1998), I've never really used it on the desktop (I'm a Solaris guy), so this was only the second time I've ever installed Kubuntu and any linux window manager. So I'm not some uber genius.

Really, just take a read through the UbuntuGuide wiki for "getting started" and go through the tutorials people have written in the forums here for getting firefox32, flash, audio and codecs working and you'll be just fine with very little effort. I would actually say that doing it manually was even easier than using Automatix (which I had done once before).

Yeah, there's not a huge performance boost, but there is one and since it requires minimal effort, why not go for it? You paid for the hardware after all. And if you find that it's just too incredibly baffling or difficult in your environment, then just pop in an i386 install disk and have yourself up and running in 32bit by the end of your favorite sitcom.

The reason is some people are lazy. They dont want to do anything. They just want to click a few things, never go near the command line, never read anything, and have everything work without any effort or learning on their part.
The few applications that are needed that are 32bit are not hard to install. Almost all of them have howto's or install scripts. So lack of knowledge isnt a reason. 
Just pure plain lazy ex windows users imho. Why else do you think the forum is full of the same topic over and over? Users to lazy to search the forums. Users to lazy to search google. They want it handed to them without any work on their part.

---

### Post by xopher on 2006-11-29
> Why install 64bit?

Because it's cool ;)

---

### Post by COL on 2006-11-29
Hello,

I went through the same process of debating the pro's and con's of installing the 64 bit version.  To make a long story short, I tried the 32 and then installed the 64 and have been very satisfied.  Automatix2 is very helpful, and frankly there is more in the repositories than I thought.

..and as indicated above, it should just get better and better.

---

### Post by TheVrolok on 2007-01-13
I use the 64 edition just because I enjoy more of a challenge and ... style points.  :mrgreen:

---

### Post by skinny on 2007-01-15
Why not?

A little more effort in some areas (really only flash + 32bit browser) and even then, look hard enough and you'll find excellent [scripts]("http://www.xnowherex.net/simple64/") or howtos already written and tested.

$

---

### Post by Doug11 on 2007-01-16
I just upgraded to a 64 and then installed the 64 for edgy. After much frustartion, I went back to Dapper,,then tried the 64 bit dapper,,then said the hell with it,,,and put the 64 edgy back on. After much hair-pulling,,i finally got my wireless working the the fwcutter, wine is now functional and a few other proggies I used in the 32bit distro. No looking back now. Have patience, do lots of reading and enjoy.

---

