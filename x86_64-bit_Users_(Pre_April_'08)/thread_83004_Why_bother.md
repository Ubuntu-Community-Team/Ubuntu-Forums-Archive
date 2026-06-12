---
title: "Why bother"
date: 2005-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by kingmob on 2005-10-27
I've just got my new amd64 system today and happily installed both win64 as ubuntu64. Now, many hours later and many dissapointments later i'm wondering, is it all worth the trouble?
Honestly, the number of ordinary things that stop working is awfull and the workarounds are so hard or weird, that it's just too much hassle.
I'm really amazed that a new game (quake4) does not run on amd64. The single thing you suspect would work is state of the art games...
Thing is, it feels like a step back to go to 32bit again, but who is really getting something out of 64bit from you guys atm?

I'm not quite beaten yet, but i'm very close :(

---

### Post by mlomker on 2005-10-27
This is a recurring thread here and the only answer is to be different, imo.  There are probably a handful of processor or memory intense applications that will benefit but that's about it (64-bit supports more than 4 Gig of RAM).  I run amd64 Hoary but went 32-bit for Breezy because it's easier to work with and feels just as fast to me.

---

### Post by superhew on 2005-10-27
i know what you mean, I have almost become addicted to painkillers for all the headaches I've had with 64bit arch systems. Many times i have been tempted to simply switch back to 32 bit, but I realize that if it weren't for the people sticking with 64 and refusing to use 32, very little would ever get done. For example, the Macromedia Flash plugin is not supported for 64 bit systems, but I believe I read in a news statement that they weren't planning to release until the 64 bit community grew to a point where it was worth their time/money.

On a side note, how do you like XPx64? i've heard its really buggy and unstable. i decided i would skip it and wait until the stable x64 version of Vista is released.

---

### Post by gpw797 on 2005-10-27
I went back to 32... 64 not quite ready for primetime yet, will be soon tho I hope.

---

### Post by neufena on 2005-10-28
I've found amd64 really good, although I've never ran 32-bit on this processor so I can't compare speeds.

For me the only problem is Flash, other than that I can do everything I need to do fine.  All the headache's I've come across are no different to the headaches I had on Hoary (32-bit, old PC) and generally tend to stem from me trying to be 'clever' with my system and over tweak it!

Neufena

---

### Post by kingmob on 2005-10-28
Yes i figured i wasn't the first with this kind of thread, which makes it all the weirder. From what i can tell the number of people who have the same problem as me, that is, not being a superuser, but enough of a user to be able to run into all kinds of problems, is pretty big. I'm not accusing the developers of being lazy or anything, i wouldn't dare to do that tbh, but it's just a weird observation to see that after more than a year of 64bit cpu's, it's still so underdeveloped.

Windows seems to have the exact same problem, with the big distinction that most things are not open source there, which makes it even worse. Companies that simply don't care :|.

I agree with the post that says you'll have to stick with 64bit for it to develop, but i think i'm going to go 32bit anyway for a while and look back 2 months from now or so. It's just gone to the point where it's not fun for me to fiddle with my computer anymore. Since i bought the thing to have fun with primarily, that is probably going to outweigh for me when i revert to 32bit tonight when i get back from work ;).

> 
On a side note, how do you like XPx64? i've heard its really buggy and unstable. i decided i would skip it and wait until the stable x64 version of Vista is released.

I haven't really done much with it yet (only had my system for 1 day now), but it doesn't seem buggy to me. It does have weird things i'll have to solve though. For instance, windows is being itself again in telling me i've already set up a LAN connection (which is infact my firewire) and that i may not make another (wtf?). So for the moment i haven't even got internet on XP x64 :|

---

### Post by GuyveR800 on 2005-10-28
What surprises me is that operating systems (both Win64 and Linux) are so poorly supporting 32-bit drivers and applications!

Technically AMD64 CPUs are capable of executing 32-bit and 64-bit mixed, just like the 32-bit x86 CPUs are capable of executing 16-bit and 32-bit program code mixed.

Windows 3.1 had a 32-bit subsystem (Win32s) available to run 32-bit apps and even MS-DOS was capable of running 32-bit programs via so-called DOS-extenders. Then came Windows 95 which was 32-bit in essence, but ran 16-bit and 32-bit programs and even *drivers* quite happily together.

So it sounds to me this is just an OS issue... There shouldn't be any problem (from a user's and hardware perspective) to run 32-bit and 64-bit apps and drivers side by side, and it shouldn't be necessary to have to wait for 64-bit software in order to have Flash or video codecs or what have you.

---

### Post by Wyld on 2005-10-28
I was very tempted to go AMD32 with my new install, but I decided against it.  My aim is to see if I can do what I want in 64 rather than use what I normally use, to be task focused rather than application focused.

I also want to stop going back and forth between windows and linux, and if I include the additional complication of windows and linux32 and linux64 .. I'd just go back to windows .. which is something I'm really trying to avoid.

Yes, it's not a fully featured as 32bit, but it's up to us to provide guidance and support to the developers and the community to do just that.  It **is** just a matter of time and patience until the chipset is fully supported, just as it was when we shifted from 16bit to 32bit - if people remember that far back.

My pet whinge .. people who post up FAQs on arch-non-specific information but bundle it in a i386 wrapper.

---

### Post by queenorych on 2005-10-28
Not sure what the complaints about amd64 are.  Built an nforce4 system with nvidia.  Running breezy, everything works great.  Even has openoffice (actually 32bits).  rt2500 wireless nic works.  totem,mplayer,ffmpeg,evolutoin, firefox, java.  No flash yet, but I don't care about that.

I havn't got bitpim to run in 64bit, but I just use a chroot.  See amd64 howto.  I use the chroot to run wine and bitpim.  It's also handy if I want to comile 32 bit programs

---

### Post by GuyveR800 on 2005-10-28
Sure, chroot is a solution. It would just be nice if a user didn't have to think about it and it would Just Work.

---

### Post by zekolas on 2005-10-28
well it depends what you want to do with your machine as a lot of stuff in 64 bit is not supported yet. However for me I use 64 bit, I can live without a java plug in, I can live without an official flash(I use gplflas). 

I see the benifit in two places, java sun's x64 bit java seems faster and more stable, I run apps like limewire azurus and a few other. Audio and video encoding is a lot faster as well.

---

### Post by BoyOfDestiny on 2005-10-30
Yeah, I've been dual booting on my opteron for a while. Backward compatibility of debian/ubuntu is less than stellar.

Tempted to try this (since there is multilib)

[http://distrowatch.com/table.php?distribution=rr4](http://distrowatch.com/table.php?distribution=rr4)

Live DVD with gentoo gui installer...

---

### Post by bonzodog on 2005-10-30
[QUOTE=zekolas]well it depends what you want to do with your machine as a lot of stuff in 64 bit is not supported yet. However for me I use 64 bit, I can live without a java plug in, I can live without an official flash(I use gplflas). 

I see the benifit in two places, java sun's x64 bit java seems faster and more stable, I run apps like limewire azurus and a few other. Audio and video encoding is a lot faster as well.[/QUOTE]

Hrm...am using 5.10 x86_64 here, and flash is more of a problem than java. I'm using the Blackdown Java plugins for firefox, and find they work just as well as sun's java system. I am also using gplflash, and a lot of sites just complain that it's out of date. Still, I don't see that 'missing plugins' thing quite so much anymore.....

---

### Post by pjs_flyer on 2005-11-02
The 64 bit flavour has been pretty good for me, with just the usual issue with flash etc - however, it is worth highlighting the excellent work that's being done at [http://tamir.nooms.de/wiki/doku.php](http://tamir.nooms.de/wiki/doku.php).

Stick with it - it'll only get better if enough of us persist!

---

### Post by jvictor on 2005-11-03
Im a 64 bit user, I find it prety stable. The beauty is that if one app doesnt work anither will work :-) Gnomebaker dint work for me , but Graveman works fine ... 

Yes flash is the problem , but again it depends on the sites u  visit.. I use my computer mainly for j2ee development and the sites i visit are pretty narrow , so i dont find flash as a problem

---

### Post by queenorych on 2005-11-03
if flash is so important just run a chroot.  See the amd64 debian howto.

---

### Post by Biased turkey on 2005-11-03
"Why bother"
I think the title describes perfectly the 64 bits situation right now.
I use Ubuntu 5.10 32 bits for my day to day activities, gaming, multimedia etc..
I installed Gentoo 64 bits on my 2nd drive just to see if I could do it. I  use Gentoo 64 bits almost exclusively for the default packages included with KDE + 2D graphics programming ( kdevelop ) and for sure gcc 64 bits rocks.
I don't feel like going the chroot way.
It's already difficult for us to convince regular windows user to switch to Linux, imagine if we had to convince them to deal with chroot.

---

### Post by Optimal Aurora on 2005-11-03
You would want a 64bit system if what you do is programming or very intensive graphics are just want to be prepared for the future. I personally like my 64bit system and enjoy running it with Fedora Core 4 x86_64 and Ubuntu Live 5.10 in 64 bit mode and Windows XP Home 32bit with some enhancements that I made. But if you are just the average run of the mill user that doesn't do graphics intensive gaming then you should have brought a 64 bit system unless you wanted to prepare for the future.

Personally, I wanted to prepare for the future at first. Then at my school we started using the 64bit windows and 64 bit linux system we made in one of my computer classes, and have enjoyed it since.

---

### Post by brahm on 2005-11-08
[QUOTE=gpw797]I went back to 32... 64 not quite ready for primetime yet, will be soon tho I hope.[/QUOTE]

Correction, **Ubuntu** is not quite ready for the x86_64 architecture. Reverted to Gentoo on my Athlon64 which solved ALL my problems, and with a little more effort I sorted out all cosmetic issues with all my 32-bit apps (such as Firefox, Adobe Reader, Opera, Skype, OpenOffice.org-2.0, etc).

Running a 32-bit OS (other than WinXP, which I **hardly** ever use) was just not an acceptable option -  could have saved a bundle by using a socket 754 Sempron 3100 instead! Just in terms of compiling software on AMD64 makes the 64-bit environment absolutely worthwhile! ;) 

Gentoo provides ebuilds for 32-bit binaries for those still seeking compatibility with 32-bit libraries and codecs (such as Firefox, MPlayer, et al). Win32 codecs for MPlayer are also packaged (obviously only compatible with MPlayer-bin).

Ubuntu developers should focus on sorting out all 32-bit emulation/compatibility libraries, which was the no. 1 reason why I reverted to Gentoo. Why should I run 32-bit Firefox in a chrooted environment, for goodness sake?!! (If someone has solved this issue in Breezy, please fill me in).

I find it rather disappointing to learn that most of the issues that pestered me in Hoary on amd64 still remain in Breezy. I would much rather like to see the issues been addressed by the package maintainers, rather than encouraging anyone to use another distro if they wish to stay with 64-bit. 

PS: I still can't understand why anyone would release a distro with the kernel and base system compiled with two different major releases of gcc...

---

### Post by 23meg on 2005-11-08
[QUOTE=brahm]
PS: I still can't understand why anyone would release a distro with the kernel and base system compiled with two different major releases of gcc...[/QUOTE]

Probably because by the time Breezy was out it was too early to compile something as crucial as a distro shipped kernel with gcc 4.

---

### Post by Mayfairy on 2005-11-09
I'm not too familiar with this 64-bit system so one question still remains unanswered: IF I install 32-bit system and I got 64-bit AMD processor will it be like throwing money away? What I mean is that will I gain anything by using 32-bit system and 64-bit processor, or should I have just bought 32-bit processor?

---

### Post by Yagisan on 2005-11-09
[QUOTE=brahm]Correction, **Ubuntu** is not quite ready for the x86_64 architecture.[/quote] I disagree. Ubuntu is quite ready for amd64, their decision was that the **whole** system was to be 64bit, otherwise there would be no point in having an amd64 specific version.

[QUOTE=brahm]Reverted to Gentoo on my Athlon64 which solved ALL my problems, and with a little more effort I sorted out all cosmetic issues with all my 32-bit apps (such as Firefox, Adobe Reader, Opera, Skype, OpenOffice.org-2.0, etc).[/quote]If your proprietry applications don't work, well bitch to the vendor (hint, it's not ubuntu). The vendor doesn't care ? Tough, find an alternative. (If it was opensource, you or someone else could fix it)

[QUOTE=brahm]Gentoo provides ebuilds for 32-bit binaries for those still seeking compatibility with 32-bit libraries and codecs (such as Firefox, MPlayer, et al). Win32 codecs for MPlayer are also packaged (obviously only compatible with MPlayer-bin).[/quote] Ubuntu provides an i386 distribution for those needing compatablity with all those issues caused by proprietry software.

[QUOTE=brahm]Ubuntu developers should focus on sorting out all 32-bit emulation/compatibility libraries, which was the no. 1 reason why I reverted to Gentoo. Why should I run 32-bit Firefox in a chrooted environment, for goodness sake?!! (If someone has solved this issue in Breezy, please fill me in).

I find it rather disappointing to learn that most of the issues that pestered me in Hoary on amd64 still remain in Breezy. I would much rather like to see the issues been addressed by the package maintainers, rather than encouraging anyone to use another distro if they wish to stay with 64-bit. [/quote] It really sounds like you would have been better off on i386.

[QUOTE=brahm]PS: I still can't understand why anyone would release a distro with the kernel and base system compiled with two different major releases of gcc...[/QUOTE] Because, IIRC not ALL of the kernel was compatable with GCC4 at the time.

---

### Post by Yagisan on 2005-11-09
[QUOTE=Mayfairy]I'm not too familiar with this 64-bit system so one question still remains unanswered: IF I install 32-bit system and I got 64-bit AMD processor will it be like throwing money away? What I mean is that will I gain anything by using 32-bit system and 64-bit processor, or should I have just bought 32-bit processor?[/QUOTE]It's more like buying a racecar, but being only able to drive it at the legal speed limit. It's good, but it has a lot more potential. If you intend to keep the system for a while, I'd buy the amd64 chip and it can run the 64bit OS if you choose to put one on in future. If you are going to junk the system soon anyway, and you can save a significant amount of money by not buying an amd64 system, then get the 32bit system.

---

### Post by BLTicklemonster on 2005-11-10
I was on my way out the door to buy a 64 bit, and my daughter called and asked me to buy her a laptop... well, I had built her a real nice pc, but she was going away to college, and my 6 year old would be without a pc if the older one took it, so I said sure. Bought her a really nice acer, figured I'd get a 64 bit later, then the reports began flooding in about how many people regretted getting 64 bit. 

I smile every time I think about that.


Yeah, later, but not right now.

---

### Post by RAOF on 2005-11-10
[QUOTE=Mayfairy]I'm not too familiar with this 64-bit system so one question still remains unanswered: IF I install 32-bit system and I got 64-bit AMD processor will it be like throwing money away? What I mean is that will I gain anything by using 32-bit system and 64-bit processor, or should I have just bought 32-bit processor?[/QUOTE]
No.  The AMD 64bit processors (athlon64, athlonfx, opteron, etc) also happen to better at running 32bit code than Intel chips (Pretty much.  They tend to be better price/performance than the Intel chips, and the fastest AMD chip is faster than the fastest Intel chip.  Or, at least, it was last time I looked).

(Some of the) New Intel processors also support the x86-64 instruction set, so if your trying to buy a fast computer, you're pretty much going to get a 64bit chip regardless.  It will be **faster** (I have seen numbers in the order of 10-20% for many tasks) running 64bit stuff (because of some improvements in the 64bit instruction set, over ia32) than 32bit stuff, but it'll still be faster running 32bit stuff than anything else you could have bought ;).

---

### Post by XXFCTEXX on 2005-11-10
I started out with Ubuntu 64 and found out quickly that all the apps would not work with it. I went to 32 and you really don't notice any difference. 

If it wasn't for the 64 edition I might not have tried Ubuntu and fell in love with it. I'd still be using XP :( 

Everything happens for a reason :D

As far as the reports of AMD 64 problems with 32bit software I've never had any. I love my AMD 64.

---

### Post by XXFCTEXX on 2005-11-10
[QUOTE=Mayfairy]I'm not too familiar with this 64-bit system so one question still remains unanswered: IF I install 32-bit system and I got 64-bit AMD processor will it be like throwing money away? What I mean is that will I gain anything by using 32-bit system and 64-bit processor, or should I have just bought 32-bit processor?[/QUOTE]

AMD 64 will run processes faster than a 32 and multi-task better. There is no better processor on the market (IMHO) and anything and everything can run on it better than a 32.

---

### Post by BoyOfDestiny on 2005-11-10
[QUOTE=Mayfairy]I'm not too familiar with this 64-bit system so one question still remains unanswered: IF I install 32-bit system and I got 64-bit AMD processor will it be like throwing money away? What I mean is that will I gain anything by using 32-bit system and 64-bit processor, or should I have just bought 32-bit processor?[/QUOTE]

Well, I was a running a 32-bit os for 2 years on my opteron, and just took the plunge to 64-bit ubuntu.

I'd say (my opinion) dollar for dollar, if you pick up an amd64 (or opteron) you will get better performance (this applies to 32-bit as well) than a comparably priced intel chip.

So with a 64-bit processor you have quite a few options. Run a 32-bit os or 64-bit os, or both.

With 32-bit you are stuck with 32-bit (unless you emulate 64bit... which would be very very slow ;) )

Anyway, I guess browse the repos, see if all the software you want runs natively in 64-bit, for those that don't...well I'm learning as I go

(I really miss my zsnes ;) )

---

### Post by Yagisan on 2005-11-10
[QUOTE=BoyOfDestiny]I'd say (my opinion) dollar for dollar, if you pick up an amd64 (or opteron) you will get better performance (this applies to 32-bit as well) than a comparably priced intel chip.[/quote]That tended to be true when I used to retail them a while ago, should still be true now.
[QUOTE=BoyOfDestiny](I really miss my zsnes ;) )[/QUOTE]And for that very special application I run an i386 chroot :)

---

### Post by estel on 2005-11-12
Agree with what someone said above, I use AMD64 because I'm both a stubborn person, and I recognise that some people (Mad people) will *have* to stick with it from the start, through thick and thin in order to usher in the next generation of computing.
Not only that, but the challenge of getting some stuff to work is also one of the things that I enjoy about Linux in general (only, again, because I make it difficult for myself).

I also run XP x64 as an OS just as much as Ubuntu, and I have to completely disagree with parent - it is not an Operating System that is in the *slightest* unstable or buggy. Having been built off of Windows Server, its more stable, fluid and faster than XP Pro x86. Only problems that I have with it are getting my webcam to work, and my TV card. These are exactly the same two problems that I have with Ubuntu (well, the webcam works, but no IM for it :P).

---

