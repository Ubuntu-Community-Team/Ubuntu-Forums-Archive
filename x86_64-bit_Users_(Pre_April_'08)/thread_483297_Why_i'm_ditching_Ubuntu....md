---
title: "Why i'm ditching Ubuntu..."
date: 2007-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by cmost on 2007-06-24
Unfortunately, after a year or so of relative happiness with Ubuntu, I find myself in the unfortunate position of distro shopping...again.  Why?  Because Feisty has a freezing problem and nobody has a solution.  I have searched these forums high and low as well as Google to no avail.  My workstation, which used to be rock solid and reliable for weeks on end under Ubuntu 6.06 and 6.10 now freezes unexpectedly under 7.04; for no apparent reason.  Sure, there's a reason, but nobody has been able to pin it down.  There are about a dozen or so posts on this subject on these forums alone and dozens more on various other Linux related forums all over the Net.  I thought if I compiled a new kernel, then it might solve the problem as some people running the latest Gutsy alpha have reported that the freezing stopped for them.  I will not run an alpha level OS on my production machine.  I tried to compile a custom kernel, but, my workstation keeps freezing during the compilation.  I cannot continue to put up with my workstation crashing and have decided to leave Ubuntu behind.

I've decided to switch to Debian Etch 4.0 for amd64 and I hope I will be able to get it to a state similar to my current Ubuntu Feisty amd64 box, albeit without the annoying freezes.  Out of curiosity, has anyone tested the latest Debian?  Pros?  Cons?  Thanks!  Perhaps I'll be back in October.

---

### Post by incubus on 2007-06-24
cmost, Debian is excellent.  If Ubuntu didn't exist, I would still be using it.  Although I have not tried the latest version, I think they are pretty up-to-date now.  That was one of the biggest complaints about Debian.

Out of curiosity, does it not work to run Feisty -1?  And perhaps just install the programs you need from Feisty?

incubus

---

### Post by jrusso2 on 2007-06-24
> **cmost said:**
> Unfortunately, after a year or so of relative happiness with Ubuntu, I find myself in the unfortunate position of distro shopping...again.  Why?  Because Feisty has a freezing problem and nobody has a solution.  I have searched these forums high and low as well as Google to no avail.  My workstation, which used to be rock solid and reliable for weeks on end under Ubuntu 6.06 and 6.10 now freezes unexpectedly under 7.04; for no apparent reason.  Sure, there's a reason, but nobody has been able to pin it down.  There are about a dozen or so posts on this subject on these forums alone and dozens more on various other Linux related forums all over the Net.  I thought if I compiled a new kernel, then it might solve the problem as some people running the latest Gutsy alpha have reported that the freezing stopped for them.  I will not run an alpha level OS on my production machine.  I tried to compile a custom kernel, but, my workstation keeps freezing during the compilation.  I cannot continue to put up with my workstation crashing and have decided to leave Ubuntu behind.

I've decided to switch to Debian Etch 4.0 for amd64 and I hope I will be able to get it to a state similar to my current Ubuntu Feisty amd64 box, albeit without the annoying freezes.  Out of curiosity, has anyone tested the latest Debian?  Pros?  Cons?  Thanks!  Perhaps I'll be back in October.

I am still using edgy, its still updated.  I tried Feisty on a test box and it had issues.

So I stay on edgy for now.

---

### Post by floke on 2007-06-24
> **jrusso2 said:**
> I am still using edgy, its still updated.  I tried Feisty on a test box and it had issues.

So I stay on edgy for now.

Sounds sensible to me; but there's no harm in a bit of distro-hopping.
I'd love to play with Etch, but unfortunately it doesn't support the 3945 wireless ootb.
I had a brief try at getting the drivers etc. installed, but really couldn't be bothered.
PCLOS is also a very good distro that you might consider; also - just been struck by a thought - why not try Linux Mint? Its basically ubuntu with a few added extras (codecs by default etc.). That way you'd get to keep ubuntu and might solve your freezing.

---

### Post by cmost on 2007-06-24
I've thought about downgrading back to 6.10 or even all the way back to 6.06, but I like the idea of Debian pure, because it's easier to steal more up-to-date packages from 'unstable' (a.k.a. Lenny.)  With Ubuntu, you're sort of stuck with current versions of software unless you want to compile software yourself or run pre-release versions of the upcoming Ubuntu release.

---

### Post by Mr_bleu on 2007-06-24
Good luck.

---

### Post by Kilz on 2007-06-24
> **cmost said:**
> I've thought about downgrading back to 6.10 or even all the way back to 6.06, but I like the idea of Debian pure, because it's easier to steal more up-to-date packages from 'unstable' (a.k.a. Lenny.)  With Ubuntu, you're sort of stuck with current versions of software unless you want to compile software yourself or run pre-release versions of the upcoming Ubuntu release.

Dapper is rock solid, it still has 2 years of support. If you tire of shopping, Dapper is always there. Just a question. The Feisty setup you had. Was it a fresh install or a Dapper that was upgraded to Edgy, then to Feisty? If so did you ever try a fresh Feisty install with new media?

---

### Post by cmost on 2007-06-24
Hi Kilz!  My setup was a Edgy upgraded to Feisty.  I thought of trying a fresh install, but my extensive research into the random freezing indicated that it would occur regardless.  To answer others comments, I cannot try Linux Mint or even PCLOS (which I adore and ran for a couple of years) because unfortunately, I have to run a 64 bit Linux due to a glitch in my motherboard (or, forego AGP & 3D graphics acceleration - don't ask!)  I may end up downgrading to Dapper as a last resort, but, I'll see how Debian Etch works out first.

---

### Post by kuja on 2007-06-24
I ran Debian Etch for a month or so, rock solid, and very nice, but it's lacking in some of the conveniences that Ubuntu has (though it does have little conveniences of its own!). All in all the difference is relatively minor, but if you want to use Etch you'll have a much better time if you're comfortable with a little bit of administration & such via the terminal ;)

As per your freezing, let me see if I can pin it down (never know, I might just be the wizard you were looking for, hehe). Post your /var/log/syslog so I can have a looksie at it. Kernel related problems usually show up in there. Oh, and if it is a kernel problem, you don't *have* to run that same kernel, for example, even though I switched back to Ubuntu, I'm still using Etch's kernel.

---

### Post by bluknight on 2007-06-24
> **cmost said:**
> Hi Kilz!  My setup was a Edgy upgraded to Feisty.  I thought of trying a fresh install, but my extensive research into the random freezing indicated that it would occur regardless.  <snip> I may end up downgrading to Dapper as a last resort, but, I'll see how Debian Etch works out first.

I am running Feisty on Edgy's 2.6.17-11 kernel and nothing freezes (just slower KDE??). Im still waiting for a workable Feisty 2.6.20 kernel on my system.

Here's how I make Feisty run on an old kernel:
[http://ubuntuforums.org/showthread.php?t=470002](http://ubuntuforums.org/showthread.php?t=470002)

---

### Post by nss0000 on 2007-06-24
CM:

Downgrade you say ?? Downgrade from Festering Faun -- that miasmic swamp of over-reaching byte_fantasy ?? 

Downgrade ... to rock-solid slick-as-a-horny-rattlesnake-in olive-oil DAPPERx64 ?

Surely you jest ...

nss
******

---

### Post by cmost on 2007-06-24
I do happen to have Edgy's old kernel  (2.6.17) and headers still installed in my /usr/src directory.  Hmmm.  I didn't stop to think I could use that in Feisty.  (Duh!)  Perhaps I'll try using that kernel and see if the freezing stops.  I'll post back results.  I'm also going to try to use the 'Server' version of 2.6.20 and see of that fares better than the 'Generic'.  Thanks for all the replies!

---

### Post by cmost on 2007-06-25
Switched back to Edgy's kernel (2.6.17-15.)  Feisty still freezes.  Obviously it's not the kernel.  Based on other threads, the problem is not related to:  video card or driver, WiFi card or driver, type of hard disk or driver, kernel type or processor class.  I give up.  Time to try Etch!  Cheers!

---

### Post by litemotiv on 2007-06-25
> **cmost said:**
> Switched back to Edgy's kernel (2.6.17-15.)  Feisty still freezes.  Obviously it's not the kernel.  Based on other threads, the problem is not related to:  video card or driver, WiFi card or driver, type of hard disk or driver, kernel type or processor class.  I give up.  Time to try Etch!  Cheers!

that syslog rundown kuja proposed would still be a viable thing to try. even if you do decide to switch to etch, it might provide valuable information about the problem in general and could help fix similar problems for other users. ;)

---

### Post by phidia on 2007-06-25
I'm using Etch 4.0-r0-amd64 on my recent 64bit build. (Gigabyte M55SLI-S4-rev.2; AMD64 X@ 4400; GeForce 7600GS; 2GB DDR2)
It runs well-quite fast by comapision to my old sempron-start up times are very good. I haven't quite got the flash plug-in installed yet. I installed the latest nvidia driver NVIDIA_Linux-x86_64-100.14.11 manually. I also have sabayon 3.4loop1for amd64 installed which sets lots of stuff up automatically. Sabayon is definately a slower boot but has nice features. I prefer gnome and debian more though.
I was going to install 64bit ubuntu but decided to try debian. I think it's an excellant release. totem worked right out of the box-but had some artifacts-so I installed mplayer and it works great. One problem is that I haven't been able to get lm-sensors working correctly although it worked on my sempron. I don't know if it's the motherboard or 64bit stuff. I've only been playing with this Debian 4.0 install a few days though so more to come.

---

### Post by interval1066 on 2007-06-25
Been using 7.04 on my Turion-based laptop with nVidia gfx since March, and its been like a rock. No freezing for me. Obviously this issue is with particular hardware.

---

### Post by vinnn on 2007-06-25
> **cmost said:**
> ...Feisty has a freezing problem and nobody has a solution...

I have suffered from this problem, seems that there's a bug in relation to the proprietory Nvidia driver, I have a 7600 GS PCIe 512MB card.
Once I disabled the Nvidia driver and used the open source nv graphics driver, all is rock solid. Only problem is that I have to switch back to play games or run Google Earth, neither of which I spent a great deal of time doing.

The 'lock up' doesn't lock the system though, just the keyboard, mouse & display. I'm still able to ssh into the system from my laptop and look at the syslogs which when the problem occurs goes something like this...
```
[ 3930.482518] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba3
[ 3938.466056] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba4
[ 3939.464008] NVRM: Xid (0001:00): 8, Channel 00000000
[ 3946.453560] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba5
[ 3947.451507] NVRM: Xid (0001:00): 8, Channel 0000001e
[ 3954.441077] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba6
[ 3955.439031] NVRM: Xid (0001:00): 8, Channel 00000020
[ 3962.424600] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba7
[ 3963.422547] NVRM: Xid (0001:00): 8, Channel 00000020
[ 3970.408134] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba8
[ 3971.406081] NVRM: Xid (0001:00): 8, Channel 0000001e
[ 3978.395657] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba9
[ 3979.393604] NVRM: Xid (0001:00): 8, Channel 00000020
[ 3986.379148] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071baa
[ 3987.377112] NVRM: Xid (0001:00): 8, Channel 00000020
[ 3994.362701] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071bab
```

I haven't got any further than that with the problem so far due to lack of time but this issue only cropped up since going from Edgy to Feisty.

---

### Post by cmost on 2007-06-25
Thanks for your input.  I've experienced the lock-up with and without the proprietary nvidia driver as well as with and without Beryl running.  Others report the same with ATI video cards.  Furthermore, when the system freezes, it locks up everything including the mouse.  Only a hard reset will restart the system.  I'm in agreement that the problem is likely hardware related.  I simply wish I could figure out what sequence or combination of hardware events triggers the freeze.  Personally, I believe the problem is related to HAL, but I can't prove it.

---

### Post by Enverex on 2007-06-25
People seem to be missing the point. Distros are basically the packaging of the cake, the kernel is the cake itself. If you're having freezing issues then there's an issue with your hardware, the kernel or a driver. You're not going to fix that by changing distros (unless they use a different kernel or driver which the other distro would be changing at some point anyway).

Diagnose your issues, don't run from them, they'll come back and bite you in the ***.

---

### Post by Kobalt on 2007-06-25
I had these freezes as well, from Edgy to Feisty, and even Gutsy. Since I've installed manually the latest nvidia drivers (100.14.11) I've had no freezes, even using the latest Compiz... Maybe you should try this, but these freezes are still very obscure though.

---

### Post by cmost on 2007-06-25
Enverex, I appreciate your comment.  I understand perfectly how Linux works (Linux is the kernel surrounded by a bevy of supporting applications which together create the "distribution.")  I'm not trying to run from my problems.  On the contrary, I've faced it daily ever since I upgraded to Feisty a couple of months ago.  I think I've gone above and beyond why is reasonable in an attempt to solve the issue.  While I'm no newbie, I'm also not a computer engineer.  I shouldn't have to spend untold hours pouring through system logs and debugging code in order to prevent my system from locking up.  All I know is that my system was stable and now it's not.  I just want it to be stable again.  Perhaps it is a piece of my hardware that has begun to malfunction.  If that's the case, then Debian Etch should lock up too.  It's a relatively simple test to check that out.  If it turns out I still get freezes, then I'll report back.

Kobalt.  Thanks for your suggestion.  I have the very latest and greatest nvidia driver (100.14.11).  Unfortunately, I'm still getting the freezes!  :-(

---

### Post by praxis22 on 2007-06-27
try:

```
 sudo apt-get remove powernowd
```

Seen a few people having problems with random freezes, quite often it appears to be a problem with either power management, or the graphics card.

---

### Post by jespdj on 2007-06-27
> **Kilz said:**
> Dapper is rock solid, it still has 2 years of support. If you tire of shopping, Dapper is always there. Just a question. The Feisty setup you had. Was it a fresh install or a Dapper that was upgraded to Edgy, then to Feisty? If so did you ever try a fresh Feisty install with new media?

Dapper may be rock solid, but that doesn't mean it runs on any hardware you try it on. It doesn't run properly on my Core 2 Duo PC (with Intel P965 chipset). Some problems are that the CD drive is not recognised (a kernel bug which prevents Linux from seeing the drive on the JMicron IDE controller), and the time running too fast (in 64-bit Dapper).

64-bit Feisty works a lot better on this PC.

---

### Post by Kilz on 2007-06-27
> **jespdj said:**
> Dapper may be rock solid, but that doesn't mean it runs on any hardware you try it on. It doesn't run properly on my Core 2 Duo PC (with Intel P965 chipset). Some problems are that the CD drive is not recognised (a kernel bug which prevents Linux from seeing the drive on the JMicron IDE controller), and the time running too fast (in 64-bit Dapper).

64-bit Feisty works a lot better on this PC.

IMHO no version of Linux runs perfectly on all hardware. IMHO there is no operating system period that runs perfectly on all hardware. But the original poster said they ran Dapper without a problem, that the problems started after upgrading a few times.
While its nice that updates solved your problems on new hardware, for some people upgrades break as much as they fix. Its a mixed bag. Thats why I always suggest sticking with a version unless you have a reason to upgrade. Simply because its "new" can lead to problems.

---

### Post by yetanothersteve on 2007-06-28
I tried the switch from 64bit Dapper to 64bit Feisty and switched back. For me it was a weekend trying everything I could read about and find to get NVidia 3D acceleration to work on my hardware.

Luckily, I keep /home on a separate partition just in case I need to switch to or back from another distro without too much pain shuffling files and configuration settings.

There are some things in Feisty I would like to try but I will content myself with using them from VMWare for now. Anything requiring hardware 3D acceleration is out using VMWare, but....

I tried Debian Etch from VMWare without coming away with a "I want to run this feeling."

Good luck.

---

### Post by aikishugyo on 2007-06-28
I had apparently random lockups of my system for a year and a half, I tried upgrading, switching X video drivers, changing kernel options, using LiveCDs, everything I could think of. I joined the UIM mailing list earlier this year, and in a bug report there were a couple of strange messages -- the maintainer told me this looks like a hardware problem and I should check my RAM properly: memtest86 did not turn up anything, but a thorough memtest86+ turned up a 1.25kiB error on my 1st RAM chip. Most applications could cope, but occasionally the system would have a complete crash. So I'd advise you to do a thorough memory test. Just my 2cents worth.

---

### Post by cmost on 2007-07-02
*** UPDATE ***

Well guys, I have been trying a few other distributions in my quest for stability.  Hands down, Ubuntu is the most polished Debian distribution around.  Here's what I've tried so far:

Debian Etch - Advantages:  pure Debian, constant updates from Testing, universal appeal.  Cons:  horribly ugly fonts, no plugins, etc. by default.  No Automatix support for the amd64 port.

SimplyMEPIS 64 - Advantages:  Debian based, build upon the rock solid foundation of Ubuntu 6.06 LTS, multimedia plugins and proprietary graphics drivers installed by default.  Cons:  software getting old; not all software available in the dapper repositories.

Sidux 2007-2 64 - Advantages:  pure Debian, constant updates from Testing, cutting edge kernel, cutting edge packages.  Easier setup and maintenance than Debian Etch, prettier fonts, cutting edge KDE desktop.  Lots of firmware patches in Sidux repos.  Cons:  No web plugins installed by default; no automatix support.  Chroot environment needs to be setup automatically.

Conclusions:  I'm sticking with Sidux for a little while and I'll see how it goes.  I can report that I haven't had any crashes since installing it.  Sidux is an up and coming fork of Kanotix.  I highly recommend you guys try it.

In the meantime, thanks for all the help and suggestions I received here.  I'm going to try that memory test ASAP!

---

### Post by Enverex on 2007-07-02
hahaha. Sorry but going from your "cons" there you're not going to be happy with anything other than Ubuntu or Windows where everyone's done absoloutely everything beforehand all-ready for you. The point is you install the base system then WHAT YOU WANT, not what people think you may want. There aren't supposed to be plugins by default, of course there wont be "automatix" (which even the Ubuntu devs advise against anyway). Also, Testing != Cutting Edge. That's Unstable/Sid and Experimental.

---

### Post by Kilz on 2007-07-02
> **cmost said:**
> 
SimplyMEPIS 64 - Advantages:  Debian based, build upon the rock solid foundation of Ubuntu 6.06 LTS, multimedia plugins and proprietary graphics drivers installed by default.  **Cons:  software getting old**; not all software available in the dapper repositories.


An operating system released 1 year ago is old? Please also tell us, what is not available?

---

### Post by bobz086 on 2007-07-02
> **cmost said:**
> I've thought about downgrading back to 6.10 or even all the way back to 6.06, but I like the idea of Debian pure, because it's easier to steal more up-to-date packages from 'unstable' (a.k.a. Lenny.)  With Ubuntu, you're sort of stuck with current versions of software unless you want to compile software yourself or run pre-release versions of the upcoming Ubuntu release.

If you are using AGP, try setting it back to 4x in your CMOS BIOS. Worked for me with a similar system as yours except for a Gforce 7600.

---

### Post by John.Michael.Kane on 2007-07-02
> **Kilz said:**
> An operating system released 1 year ago is old? Please also tell us, what is not available?

Looking at the things he "seems" to need. One is left to believe he is better off running arch,gentoo Or LFS.

---

### Post by Praill on 2007-07-02
> **jrusso2 said:**
> I am still using edgy, its still updated.  I tried Feisty on a test box and it had issues.

So I stay on edgy for now.

Same here. I heard nothing but rant and rave over how great feisty, the 2.6 kernel, and xorg7.2 were going be... the only problem is it was a lie. There are still several, several bugs with both and they should have never been included in a final release.

Your problem actually sounds simple, run edgy. Then try gutsy when it comes out and hope things get better.

---

### Post by cmost on 2007-07-02
> **Enverex said:**
> hahaha. Sorry but going from your "cons" there you're not going to be happy with anything other than Ubuntu or Windows where everyone's done absoloutely everything beforehand all-ready for you. The point is you install the base system then WHAT YOU WANT, not what people think you may want. There aren't supposed to be plugins by default, of course there wont be "automatix" (which even the Ubuntu devs advise against anyway). Also, Testing != Cutting Edge. That's Unstable/Sid and Experimental.

I misspoke.  Sidux is built from Debian Sid, not 'Testing'.  It's absolutely cutting edge.  My terminology is off a bit as it's been about two years since I've run pure Debian.  I forget that Etch is now stable.  I've been having one of those days....  :-)

As for plugins and Automatix...call me lazy.  I like being able to set all this up easily.  You must be one of the "purists".  I use my computer to get stuff done.  While it's true that I like tinkering with it and installing things myself, my grandma will not.  Web plugins, accelerated graphics drivers and codecs should ALL be available by default.  If you don't think people agree, simply look at the exploding popularity of Linux Mint and PCLinuxOS (these distros either install plugins by default or make them very easy to install.)

---

### Post by Kilz on 2007-07-02
> **cmost said:**
> I misspoke.  Sidux is built from Debian Sid, not 'Testing'.  It's absolutely cutting edge.  My terminology is off a bit as it's been about two years since I've run pure Debian.  I forget that Etch is now stable.  I've been having one of those days....  :-)

As for plugins and Automatix...call me lazy.  I like being able to set all this up easily.  You must be one of the "purists".  I use my computer to get stuff done.  While it's true that I like tinkering with it and installing things myself, my grandma will not.  Web plugins, accelerated graphics drivers and codecs should ALL be available by default.  If you don't think people agree, simply look at the exploding popularity of Linux Mint and PCLinuxOS (these distros either install plugins by default or make them very easy to install.)

I never quite understood why someone would go to all the trouble of getting an open source and Free as in freedom operating system, then fill it full of non-free proprietary things(by choice). Even more questionable is why someone would require those Free as in freedom operating systems to pervert their ideals and install those non-free things.
Granted some drivers have no open source equivlents. But by useing the non free ones we send a message that thats ok with us. So dont expect free ones for those.
For those that dont feel this way, you pointed out there are alternatives. If you need a compromized operatiting system , pay for and install Linspire.

---

### Post by Kilz on 2007-07-02
> **Praill said:**
> Same here. I heard nothing but rant and rave over how great feisty, the 2.6 kernel, and xorg7.2 were going be... the only problem is it was a lie. There are still several, several bugs with both and they should have never been included in a final release.

Your problem actually sounds simple, run edgy. Then try gutsy when it comes out and hope things get better.

"Newitis" or the idea that you must have the newest release in linux leads to opinions like yours. Think of the latest release as Beta quality in all Linux os's and applications. The development model uses the community to check for bugs. Unfortunately some people just don't understand this in the mad rush to get the latest and (not so) greatest. 
Some are hooked in a never ending search for the perfect software, so they deal with all the bugs, as soon as thats done a new version comes out, they replace the working install with a buggy new release.
Gutsy will be no better. I personally wont use a release for 4 months after its release. Im still using Dapper, which at this time is rock solid. If you want to help look for bugs or test, use vmware. That way you have the stable system to actualy do something with.

---

### Post by Praill on 2007-07-02
> If you want to help look for bugs or test, use vmware. That way you have the stable system to actualy do something with.
This is a good idea. However, it wont help you identify hardware issues since vmware will emulate your working hardware configuration.

---

### Post by aikishugyo on 2007-07-02
There's a fine trade-off between getting what you want from a system because it has it already, and getting it because you're capable of doing it yourself (TM). I'm very aware that the success of distributions hangs on the excellent teamwork of specialists in different areas of the OS and applications who somehow manage to keep the whole thing working while developing it at the same time, a task that would be really hard for any single person to do (my humble opinion). The bottom line though is that you really can't get by not doing anything yourself, and you also can't get a system that has absolutely everything set up the way you want it. If you don't manage to cover your bases between the two outlined above, the third option is taking part in the community to get what you want (bug reports, Usenet and other forums, patches, some development), a fourth is paying money for customization, and a fifth is simply waiting.

---

### Post by cmost on 2007-07-02
> **Kilz said:**
> I never quite understood why someone would go to all the trouble of getting an open source and Free as in freedom operating system, then fill it full of non-free proprietary things(by choice). Even more questionable is why someone would require those Free as in freedom operating systems to pervert their ideals and install those non-free things.
Granted some drivers have no open source equivlents. But by useing the non free ones we send a message that thats ok with us. So dont expect free ones for those.
For those that dont feel this way, you pointed out there are alternatives. If you need a compromized operatiting system , pay for and install Linspire.

I've never understood why so called purists are so hell bent against non-free or non-open sourced binary blobs in Linux!  It would be one thing if there were plenty of free or open alternatives that actually worked...unfortunately there's not.  Furthermore, we live in a world where Windows dominates.  Therefore, we have to deal with proprietary, Windows only formats in order to interoperate with the majority of our friends and colleagues.  It's really doing a disservice to say Linux is "compromised" or "perverted" just because one has installed plugins, codecs, and closed binary drivers.  That's only your opinion.  I for one couldn't care less.  I use Linux because of its power and its open development.  While I buy into some of the philosophy, I don't make it my religion.  I want my computer to be able to do certain things (easily) and if that means using something like Automatix (or hours of tediousmanual labor) to install a bunch of closed software I'll do so and not feel the least bit guilty about it.  In fact, I'm happy to send a message loud and clear to hardware and software vendors far and wide:  "We're Linux users; we're many and growing; we want your software titles, your hardware drivers, and your general overall support equal to that given to Windows or Macintosh!"

---

### Post by Kilz on 2007-07-02
> **cmost said:**
> I've never understood why so called purists are so hell bent against non-free or non-open sourced binary blobs in Linux!  It would be one thing if there were plenty of free or open alternatives that actually worked...unfortunately there's not.  Furthermore, we live in a world where Windows dominates.  Therefore, we have to deal with proprietary, Windows only formats in order to interoperate with the majority of our friends and colleagues.  It's really doing a disservice to say Linux is "compromised" or "perverted" just because one has installed plugins, codecs, and closed binary drivers.  That's only your opinion.  I for one couldn't care less.  I use Linux because of its power and its open development.  While I buy into some of the philosophy, I don't make it my religion.  I want my computer to be able to do certain things (easily) and if that means using something like Automatix (or hours of tediousmanual labor) to install a bunch of closed software I'll do so and not feel the least bit guilty about it.  In fact, I'm happy to send a message loud and clear to hardware and software vendors far and wide:  "We're Linux users; we're many and growing; we want your software titles, your hardware drivers, and your general overall support equal to that given to Windows or Macintosh!"

To me it sounds like you want a free as in cost version of Windows. One where you get whatever you want, and who cares about anyone else.

Further Reply
After reading your post again I feel I cant let something slide. You said
"It's really doing a disservice to say Linux is "compromised" or "perverted" just because one has installed plugins, codecs, and closed binary drivers.  That's only your opinion.  I for one couldn't care less.  I use Linux because of its power and its open development."
Which is a twisting of what I wrote, since you quoted me, I think its safe to say you were replying to my "perverted" comment. What I wrote has nothing to do with you installing anything afterwards. Feel free to compromise your personal system to your hearts content. What I am against is people who are to lazy to install the non-free garbage wanting the operating system to include said garbage. This inclusion would be a bad thing. It would be against the law in some places to include some codecs. It would make it hard for people who want their system to be as free as can be to have a clean system. 
Since you are already on your way out the door by the title of your post. Feel free to go to all the Linsipres and Xandros's of the world who include proprietary things by default. Feel free to install all the garbage they install along with it. But leave the free as in freedom ones be. Im sure that Ubuntu developers would , [by their philosophy]("http://www.ubuntu.com/community/ubuntustory/philosophy"), not want to include the garbage by default anyway.

---

### Post by kspn on 2007-07-02
> **Kilz said:**
> To me it sounds like you want a free as in cost version of Windows. One where you get whatever you want, and who cares about anyone else.

I agree with that sentiment. Interesting Rant there :roll:

If I find a program that does what I need and it is Non-Free then I pay for it (as long as it is worth what they are asking for it, I don't believe Windows is). The Author deserves the money :D

If they offer it for free then it is their choice.

---

### Post by Kilz on 2007-07-02
> **kspn said:**
> I agree with that sentiment. Interesting Rant there :roll:

If I find a program that does what I need and it is Non-Free then I pay for it (as long as it is worth what they are asking for it, I don't believe Windows is). The Author deserves the money :D

If they offer it for free then it is their choice.

If you want to spend money. By all means do so. I dont disagree with people adding what they want to Linux. What I am against is wanting free operating systems to include those non free things.  Sadly some people want to change free into non-free as long as it makes it easier for them.

---

### Post by caryb on 2007-07-03
I guess it's a case of functionality! I prefer open source software any day but I guess there are only enough times you can open a web site to be told you cant view as you have a missing plugin. What we require is a software matrix to show what is equivilant to what software. for example I install Adobe flash by default, but it wasn't till I got a 64 bit laptop when I couldn't install the 32 bit version that I looked further afield & found gnash. What I thing we need is some sort of wiki or similar where we can see what is available (cross reference) & what level & versions are compatible. 

Cary


BTW I'm not ditching *buntu;-)

---

### Post by lisati on 2007-07-03
> **caryb said:**
> I guess it's a case of functionality! I prefer open source software any day but I guess there are only enough times you can open a web site to be told you cant view as you have a missing plugin. What we require is a software matrix to show what is equivilant to what software. for example I install Adobe flash by default, but it wasn't till I got a 64 bit laptop when I couldn't install the 32 bit version that I looked further afield & found gnash. What I thing we need is some sort of wiki or similar where we can see what is available (cross reference) & what level & versions are compatible. 

Cary


BTW I'm not ditching *buntu;-)

Missing plugins isn't unique to Ubuntu - I've had it happen on Windoze 98SE & XP Home too.....

---

### Post by Praill on 2007-07-03
> **kspn said:**
> I agree with that sentiment. Interesting Rant there :roll:

If I find a program that does what I need and it is Non-Free then I pay for it (as long as it is worth what they are asking for it, I don't believe Windows is). The Author deserves the money :D

If they offer it for free then it is their choice.
It doesn't get any simpler than this and you are completely right. A completely FOSS ideal is noble in nature but not realistic... especially in a capitalist free-market society (yes I've read several papers that miss the point entirely trying to explain the contrary). If you think a system is "unpure" or "comprimised" for using proprietary software then you are nothing short of paranoid and unrealistic. People shouldnt be lynched for choosing a superior product simply because it's author wants to get paid for their hard work.

However, I should probably just shut up and stop feeding the fire.. less this thread turns into thread number 4,000,000 that debates the universal FOSS ideal :).

---

### Post by Kilz on 2007-07-03
> **Praill said:**
> It doesn't get any simpler than this and you are completely right. A completely FOSS ideal is noble in nature but not realistic... especially in a capitalist free-market society (yes I've read several papers that miss the point entirely trying to explain the contrary). If you think a system is "unpure" or "comprimised" for using proprietary software then you are nothing short of paranoid and unrealistic. People shouldnt be lynched for choosing a superior product simply because it's author wants to get paid for their hard work.

However, I should probably just shut up and stop feeding the fire.. less this thread turns into thread number 4,000,000 that debates the universal FOSS ideal :).

No one (but the person who took my comments out of context) said YOU cant install anything YOU want on YOU OWN system. Please point out where anyone but the person who took my words out of context and twisted them to their own point of view in order to make this into a debate on some other topic said anything about purity or compromised.
What I originally said was I was against people wanting Ubuntu to install the proprietary garbage as default and thus pervert the [philosophy]("http://www.ubuntu.com/community/ubuntustory/philosophy") of Ubuntu. To use only free software where there is an option and there are alternatives. [Please reread my comments ]("http://ubuntuforums.org/showpost.php?p=2952311&postcount=34").
Those that are against Ubuntu staying as close to its [philosphy]("http://www.ubuntu.com/community/ubuntustory/philosophy") are free (as cmost the person who is twisting things, and plans to leave anyway) to go to a distro that caters to thier need to be lazy so they dont have to install garbage not everyone wants , needs , and the legality of such is in question in some countries.
For those that take issue with "compromised" Realize that you chose a Free as in Freedom Operating system. You chose it because of its quality. That quality is the result of people working had and not going the easy rout. If they had you would have no free operating system. So if (by your choice) you want to install proprietary blobs (your free to do so) you are in fact compromising the ideals that made the operating system something you wanted.  But don't think, or require those Free as in Freedom operating systems to compromise themselves for the sake of someone who is lazy and just doesn't want to install that which the operating systems don't want or need.

---

### Post by cmost on 2007-07-03
> **Kilz said:**
> To me it sounds like you want a free as in cost version of Windows. One where you get whatever you want, and who cares about anyone else.

Further Reply
After reading your post again I feel I cant let something slide. You said
"It's really doing a disservice to say Linux is "compromised" or "perverted" just because one has installed plugins, codecs, and closed binary drivers.  That's only your opinion.  I for one couldn't care less.  I use Linux because of its power and its open development."
Which is a twisting of what I wrote, since you quoted me, I think its safe to say you were replying to my "perverted" comment. What I wrote has nothing to do with you installing anything afterwards. Feel free to compromise your personal system to your hearts content. What I am against is people who are to lazy to install the non-free garbage wanting the operating system to include said garbage. This inclusion would be a bad thing. It would be against the law in some places to include some codecs. It would make it hard for people who want their system to be as free as can be to have a clean system. 
Since you are already on your way out the door by the title of your post. Feel free to go to all the Linsipres and Xandros's of the world who include proprietary things by default. Feel free to install all the garbage they install along with it. But leave the free as in freedom ones be. Im sure that Ubuntu developers would , [by their philosophy]("http://www.ubuntu.com/community/ubuntustory/philosophy"), not want to include the garbage by default anyway.

No, I never said I need or want the proprietary binary blobs to be included by default.  I simply would like them to be easy to obtain and install if I choose.  Again, you're stating that I'd be compromising my system.  Again, I state that's your opinion.  I sense a lot of anger and hostility in your posts on this; obviously it's a touchy subject.  Please don't take me the wrong way.  We can agree to disagree on this point.  My point of view is that I don't see a good reason to have a computer that's feature-crippled while I'm waiting around for developers to reverse-engineer a particular function or feature when there's a perfectly good, binary blob that supplies that function or feature.  When the free, open blobs become available, then the proprietary closed blobs will fade away into obscurity.  Finally, please don't insult my intelligence by insisting I switch to Linspire or Xandros.  I've been using Linux for many years and I won't touch those distributions.  I've been a heavy contributer to MEPIS's, PCLinuxOS's, Mandriva's, and Ubuntu's community forums.  I'm not a whiny newb or an ungrateful Windows convert.  I've made a (hopefully temporary) switch to Debian Sid.  Perhaps I'll reexamine Ubuntu Gutsy upon its release.

---

### Post by Kilz on 2007-07-03
> **cmost said:**
> No, I never said I need or want the proprietary binary blobs to be included by default.  I simply would like them to be easy to obtain and install if I choose. 
Really? I could have sworn you said
> **cmost said:**
> Web plugins, accelerated graphics drivers and codecs should ALL be available by default.  
Looks like you are calling for them to be default to me. 
> **cmost said:**
> 
 Again, you're stating that I'd be compromising my system.  Again, I state that's your opinion. 
Compromising the [philosophy]("http://www.ubuntu.com/community/ubuntustory/philosophy") of the distro you install. Are you not doing that by installing non free, non open source blobs? Granted only you will know, and its only you thats affected. But as I proved above, you did call for the blobs to be installed by default.
> **cmost said:**
> 
 I sense a lot of anger and hostility in your posts on this; obviously it's a touchy subject.  Please don't take me the wrong way.  We can agree to disagree on this point.  
No, no anger here. Its very difficult to gauge the emotions of someone typing.
> **cmost said:**
> 
My point of view is that I don't see a good reason to have a computer that's feature-crippled while I'm waiting around for developers to reverse-engineer a particular function or feature when there's a perfectly good, binary blob that supplies that function or feature.  When the free, open blobs become available, then the proprietary closed blobs will fade away into obscurity.  

But you want the blobs by default, what makes you think work would still go on on those things if they were made to be defaults? No ones ever said you cant install them afterwards.
> **cmost said:**
> 
Finally, please don't insult my intelligence by insisting I switch to Linspire or Xandros.  I've been using Linux for many years and I won't touch those distributions.
Why not . those have exactly what you asked for.
> **cmost said:**
> Web plugins, accelerated graphics drivers and codecs should ALL be available by default.  
Is it that they install so many blobs by default?
> **cmost said:**
> 
 I've been a heavy contributer to MEPIS's, PCLinuxOS's, Mandriva's, and Ubuntu's community forums.  I'm not a whiny newb or an ungrateful Windows convert.  I've made a (hopefully temporary) switch to Debian Sid.  Perhaps I'll reexamine Ubuntu Gutsy upon its release.
Come back any time, let us know if distro hopping solved your quest for the perfect distro.

---

### Post by diesel1 on 2007-07-03
Hey Kilz,  easy now!

Cmost definitely says 'available by default' not installed by default, you even quote him saying that.

I too prefer not to have proprietary 'blobs' etc. installed by default, but it is 'nice' for them to be available, not on the distribution media though.


Diesel1.

---

### Post by Mr_bleu on 2007-07-03
I chose Ubuntu not because it's Free, as in beer, but because I was sick of windows.  I work on windows pc's as a past time.  I was tired of having to reformat every 3-6 months.  I always wanted to try linux and saw Suse In a store!!! I won't mention the store's name, but their geeks don't know much about linux.  Folks don't always switch to linux because it's free, as in beer.  Some just get so freaking sick of $BS, er, MS that they're willing to try the unknown.  I came to Ubuntu because of the Help folks get in the forums; I'd tried linuxforums and wasn't very happy with the "help".

---

### Post by greymongrey on 2007-09-03
> **Kilz said:**
> I never quite understood why someone would go to all the trouble of getting an open source and Free as in freedom operating system, then fill it full of non-free proprietary things(by choice).
Where in the Linux manifesto does it say everything in Linux has to be free?

---

### Post by stmiller on 2007-09-03
Interesting thread. I'll put in my quick $0.02

Linux is about freedom and choice, in my opinion. The more options, be that commercial or free, the better.

This is the great thing about Ubuntu: choice. Installs a default free desktop, and makes options for non-free stuff as desired.

---

### Post by Kilz on 2007-09-03
> **greymongrey said:**
> Where in the Linux manifesto does it say everything in Linux has to be free?

[Right here, at least for Ubuntu.]("http://www.ubuntu.com/community/ubuntustory/philosophy")

---

### Post by por100pre1 on 2007-09-03
> **stmiller said:**
> Interesting thread. I'll put in my quick $0.02

Linux is about freedom and choice, in my opinion. The more options, be that commercial or free, the better.

This is the great thing about Ubuntu: choice. Installs a default free desktop, and makes options for non-free stuff as desired.

It makes a lot of sense to me.  Free as default, gratis added if desired. :)

---

### Post by tszanon on 2007-09-03
> **stmiller said:**
> Interesting thread. I'll put in my quick $0.02

Linux is about freedom and choice, in my opinion. The more options, be that commercial or free, the better.

This is the great thing about Ubuntu: choice. Installs a default free desktop, and makes options for non-free stuff as desired.
I agree completely. The default installation should not include anything non-FOSS, but some things, like video driver, should be available for those who want to install them.

---

### Post by kuja on 2007-09-03
If only people would stop feeding these sorts of threads :\
They're sooooOOOO redundant.

---

### Post by Em-Buntu on 2007-09-03
> **cmost said:**
> No, I never said I need or want the proprietary binary blobs to be included by default.  I simply would like them to be easy to obtain and install if I choose.  Again, you're stating that I'd be compromising my system.  Again, I state that's your opinion.  I sense a lot of anger and hostility in your posts on this; obviously it's a touchy subject.  Please don't take me the wrong way.  We can agree to disagree on this point.  My point of view is that I don't see a good reason to have a computer that's feature-crippled while I'm waiting around for developers to reverse-engineer a particular function or feature when there's a perfectly good, binary blob that supplies that function or feature.  When the free, open blobs become available, then the proprietary closed blobs will fade away into obscurity.  Finally, please don't insult my intelligence by insisting I switch to Linspire or Xandros.  I've been using Linux for many years and I won't touch those distributions.  I've been a heavy contributer to MEPIS's, PCLinuxOS's, Mandriva's, and Ubuntu's community forums.  I'm not a whiny newb or an ungrateful Windows convert.  I've made a (hopefully temporary) switch to Debian Sid.  Perhaps I'll reexamine Ubuntu Gutsy upon its release.

cmost, sorry to hear you having these troubles. I know how frustrating hardware issues can be.
If you haven't already done so, I suggest you run a complete memory test.  It wouldn't be a bad idea to reseat your memory either. 

I noticed when I moved from Dapper to Feisty, that 7.04 seems to have slightly tighter memory requirements then 6.10. My system uses ECC memory. For some reason systems running Dapper don't generate ECC errors on my systems, but running Feisty memory test does.

I also had a slight problem with my RAID. The boot drive is a small single drive. An additional drive contains Windows, and then there's a 1TB RAID. It seems that the IRQ assignments lumped the RAID controller with the ATI AIW. The system doesn't like this and will reset if you attempt to access the RAID.  
I disable the RAID in ubuntu and the system hasn't crashed again in over 1 year. That's with running dual and quad Opterons and dual booting Windows XP 64.
Dapper was nice, but Feisty is much better. So far, Gutsy won't load on my system, so I'll have to wait to see how it will run.

---

### Post by DjBones on 2007-09-03
although i know you were rockin a machine for work,
if you weren't aware already Sidux is a really nice distro that's built off of Sid, a touch unstable but its worked without a hitch on one of my machines for a month now lol

---

### Post by cprofitt on 2007-09-03
Interesting debate.

I am curious why Open Source zealots want software to be free...

Software developers produce a product... why should it be free?

Should TV Manufacturers produce free TVs?

Should computer manufacturers produce free computers?

Certainly it can be said that software manufacturers do not have "materials" as a cost, but labor and overhead they do.

The computers the program on are not free.

The electricity they consume is not free.

The programmers want to eat.

How is it those things would be paid for?

Just curious because I just don't understand. I think it is great that some people provide us with great products for free, but I do not expect or demand it.

---

### Post by praxis22 on 2007-09-04
hmm, low post count and using the word zealot, do I feed the troll?

I think I do. :)

As a rule, and this is common across most digital content created by end users in their spare time, the creators of such content require that the content is made available for free. You can see this in another very prolific community too. Namely that of "the Sims" and "The Sims2" content creation. 

Above and beyond that, especially where the chief reward for such content creation is the kudos and respect of the community that spawned it, many people go the extra yard and then start to think of making use free tools and other community content rather than the proprietary equivalent, as a show of faith in the quality of the free software. 

It's a personal value judgement, but many people who are actively involved in their respective communities actually think the "free" stuff is better, if only because it more readily updated and improved, and they can in most cases talk directly to the people responsible if they so desire. 

If you subscribe to the kernel mailing list and actively get involved, you too can make your opinions known to Torvalds, Cox, et al. 

It's more a matter of community standards than anything else I guess.

---

### Post by cogitordi on 2007-09-04
To the original poster:

A full lock-up such as you describe is probably your RAM. In the long run, you would be best to take the advice that you've been given and run a verification or swap in some known-good RAM. Bad RAM will cause reboots and will eventually damage other hardware at the rate at which your computer has been locking up.

As for the tangential discussion... gentlemen, please! There are distributions of Linux to suit every political stripe. But we owe the existence of Linux itself to students, zealots, and militants. Recognize that and get on with your computing.

---

### Post by jso2897 on 2007-09-04
> **indigo196 said:**
> Interesting debate.

I am curious why Open Source zealots want software to be free...

Software developers produce a product... why should it be free?

Should TV Manufacturers produce free TVs?

Should computer manufacturers produce free computers?

Certainly it can be said that software manufacturers do not have "materials" as a cost, but labor and overhead they do.

The computers the program on are not free.

The electricity they consume is not free.

The programmers want to eat.

How is it those things would be paid for?

Just curious because I just don't understand. I think it is great that some people provide us with great products for free, but I do not expect or demand it.

This does not strike me a s a troll. It's a legitimate question, and I think I have a partial answer. Actually, you are right. Nothing in this world is "free". Linux is only "free" if one writes off all the millions of hours and gallons of blood, sweat, and tears that have gone into it.
A good analogy would be this: Let us say that the folks in your neighborhood are sick of their municipal park - they are charging an outrageous fee, there are lots of stupid and restrictive rules, the equipment is run-down, and the authorities are doing nothing to protect your kids from the perverts and criminals they allow to hang around the park.
 So you and your neighbors all get together and use the materials and skills you have (some of you are carpenters, welders, etc.) to build a better, safer park for your kids that they don't have to pay to get into. 
Would that be a good thing? You bet. 
Would it really be "free", in the sense that it had no cost? Not at all.

---

### Post by Kilz on 2007-09-04
I will also attempt to answer some of this.

> **indigo196 said:**
> Interesting debate.
I am curious why Open Source zealots want software to be free...
Software developers produce a product... why should it be free?
I may not have to go any further than this. Because you seem to think that the so called "zelots" are not the developers. Its called FOSS Free and Open Source Software because the developers chose a FOSS license for their code.  The developer has that choice, they produced it, and made it available as such. 
It may not be a "product", because use of that term means that someone planned on selling the end result. Clearly the developer did not choose to sell it because they chose a FOSS license.

> **indigo196 said:**
> Should TV Manufacturers produce free TVs?
Should computer manufacturers produce free computers?
Certainly it can be said that software manufacturers do not have "materials" as a cost, but labor and overhead they do.
You answered your own question. There is no cost other than someones free time to produce FOSS code. 

> **indigo196 said:**
> 
The computers the program on are not free.
The electricity they consume is not free.
The programmers want to eat.
How is it those things would be paid for?
Yes all those things are not free, and yet someone who created the code chose to put it under a FOSS license as is their right to do. Perhaps they make their living doing other things and write code as something they enjoy to do. Since it costs them nothing they release it as FOSS code.


> **indigo196 said:**
> 
Just curious because I just don't understand. I think it is great that some people provide us with great products for free, but I do not expect or demand it.
Because it exists, I can chose to use only FOSS code if I choose. Is if FREE? Well in one sense it is free, free as in freedom. I can take the code and run it, I can take the code and change it, I can take the code and pass it on to someone else.
But I have to give something back to the person who wrote it. The license may only require that I give back the credit for writing it, or the changes I have made, under the same license the original code was under. If I have to give back code the original writer gets that code for free. They gain in that way.
If I help in other ways it is just as important to the community. Developers write code, but may not have the time to help new users to use , install , or make the code run right on their computers. So if you help out in other ways it pays the person who wrote the code back a little.
But I cant demand the code. If no one writes it and does not release it under a FOSS license. I cant receive it. I can choose to run only what exists. so in fact all credit for the code and the ability to run it goes to the person who wrote it and gave it to us under a FOSS license.

[You may also want to read this page,]("http://linux.oneandoneis2.org/LNW.htm") it only answers a little of your question. But it may give you some insight into FOSS.

---

### Post by greymongrey on 2007-09-05
> **Kilz said:**
> [Right here, at least for Ubuntu.]("http://www.ubuntu.com/community/ubuntustory/philosophy")

Ok, that's their philosophy. Why should it be mine? They have the freedom to put in and take out what they chose. I should have the same freedom.

I'm not arguing against FOSS because I believe in it. But FOSS is about fredom of choice, first and foremost, I believe. My choice hopefully won't be the same as yours.

---

### Post by Kilz on 2007-09-05
> **greymongrey said:**
> Ok, that's their philosophy. Why should it be mine? They have the freedom to put in and take out what they chose. I should have the same freedom.

I'm not arguing against FOSS because I believe in it. But FOSS is about fredom of choice, first and foremost, I believe. My choice hopefully won't be the same as yours.

I just have to keep reading my own signature. Another verse that seems to fit you.

Let them alone: they be blind leaders of the blind. And if the blind lead the blind, both shall fall into the ditch. Matthew 15:14

Lets go back to what I said that you seemed to jump on.

**I never quite understood why someone would go to all the trouble of getting an open source and Free as in freedom operating system, then fill it full of non-free proprietary things(by choice).**

What was said, by me . was my own opinion. I dont understand why someone would go to all the trouble of getting , installing , and using a free as in freedom operating system and then load in things that are not free as in freedom. Especially when there are 20,000
free pieces of software in the repositories. More if you bother to use Google. It to me, defeats the purpose. To me its stupid, to me its something only someone who didnt think about the common sense aspect of it  would do. 
I think its something I may have learned. That FOSS code is the best there is, and that the Ubuntu chooses to use it, so do I. Its a choice, and my opinion. But dont let something like learning stand in your way of doing what you want. Why on earth do you think most people choose Linux? Because they got fed up with proprietary software (M$). So now you want to forget the past and start down the same road?
But by all means , if you want to go down that road, more power to you. After all you see no wisdom in using only free software, you are blind to the wisdom of it, and being blind, following other blind people doing the same thing, dont be surprised when you fall in the ditch. The ditch happens when that piece of proprietary software messes over your system because of hidden bugs.

---

### Post by greymongrey on 2007-09-05
> **Kilz said:**
> I just have to keep reading my own signature. Another verse that seems to fit you.

Ok, calling people names is not cool.  Please don't sink to that level. Let's discuss this like adults. 
> 
Lets go back to what I said that you seemed to jump on.

**I never quite understood why someone would go to all the trouble of getting an open source and Free as in freedom operating system, then fill it full of non-free proprietary things(by choice).**

What was said, by me . was my own opinion. I dont understand why someone would go to all the trouble of getting , installing , and using a free as in freedom operating system and then load in things that are not free as in freedom. Especially when there are 20,000
free pieces of software in the repositories. More if you bother to use Google. It to me, defeats the purpose. To me its stupid, to me its something only someone who didnt think about the common sense aspect of it  would do. 

OK, it's your opinion and you are entitled to it and I respect that. I really do. Now, you need to respect anyone who might have a different opinion. Everyone feels differently about these things. Why should we respect your opinion  if you don't respect ours? 

To answer you question as to why.....I didn't download it beacuse it was free. I downloaded it because it is Linux, which happens to be free. I would gladly pay for it, the same as I have for Windows all these years. I would also pay for any codecs or drivers I needed as well. I'm not looking for a handout. I just wanted the freedom to run my computer the way I wanted to run it and not the way some corporation wanted me to run it. That it is free to boot is an added bonus. 

However, as I am the computer guy for a small company, I am evaluating Linux for our business. I purchased Crossover Office and I have Photoshop and Dreamweaver and Quickbooks and MS Office loaded, and I am also trying some other apps to see how well they run as well. I am hoping to move to open source apps eventually, if we do move to Linux,  but these things take time.  We have some complex Excel and Access files, for example, and you can't just chunk the whole thing out the window over night and start over with something new. Time is money and all that, you know. :)

I run Linux at home just for fun. I no longer run Windows at all. And since it's my computer I put what I want on it. It's my choice. 
 
> 
But by all means , if you want to go down that road, more power to you. After all you see no wisdom in using only free software, you are blind to the wisdom of it, and being blind, following other blind people doing the same thing, dont be surprised when you fall in the ditch. The ditch happens when that piece of proprietary software messes over your system because of hidden bugs.

It's just software. It is a tool, nothing more and nothing less. It's not a religious cause or a political statement.  I choose the tool that works for me and I expect others to choose the tools that work for them.The same ones won't work for everyone. Thank goodness for choice.

---

### Post by Kilz on 2007-09-05
> **greymongrey said:**
> To answer you question as to why.....I didn't download it beacuse it was free. I downloaded it because it is Linux, which happens to be free.

Exactly how did you know you wanted linux?
What made you want it?

---

### Post by EXCiD3 on 2007-09-05
> **greymongrey said:**
> Where in the Linux manifesto does it say everything in Linux has to be free?

It doesnt, Ubuntu just chooses to use free software. If you want you can go purchase a commercial version of linux and go about your business that way. I personally enjoy Ubuntu the most because of the great community surrounding it.

---

### Post by greymongrey on 2007-09-05
> **Kilz said:**
> Exactly how did you know you wanted linux?
What made you want it?

I didn't know until I tried it. I was basically tired of having to reinstall XP every six months or so and I really disagree with that activation thing and I didn't want Vista after everything I've heard about it. I had always wanted to try Linux, so I did some reading and downloaded a few LiveCDs and played away. I actualy started with Mepis and loved it but the apps were kinda old and all I kept hearing was Ubuntu this and Ubuntu that, so I tried it next. I hated Gnome at first so I went with Kubuntu but Gnome sort of grows on you and I prefer it now. 

I'm basically an apps guy. I really don't care what OS I use as long as it stays in the background and lets me run my apps my way. Windows not longer did that. When Linux gets to the point where it doesn't do that I'll probably be switching again.  I don't see that happening, however. Freedom is a wonderful thing. I'm even starting to grok the Gimp. :D

Somehow I feel all this is terribly off topic and I apologize.

---

### Post by Kilz on 2007-09-05
> **greymongrey said:**
> I didn't know until I tried it. I was basically tired of having to reinstall XP every six months or so and I really disagree with that activation thing and I didn't want Vista after everything I've heard about it. I had always wanted to try Linux, so I did some reading and downloaded a few LiveCDs and played away. I actualy started with Mepis and loved it but the apps were kinda old and all I kept hearing was Ubuntu this and Ubuntu that, so I tried it next. I hated Gnome at first so I went with Kubuntu but Gnome sort of grows on you and I prefer it now. 

I'm basically an apps guy. I really don't care what OS I use as long as it stays in the background and lets me run my apps my way. Windows not longer did that. When Linux gets to the point where it doesn't do that I'll probably be switching again.  I don't see that happening, however. Freedom is a wonderful thing. I'm even starting to grok the Gimp. :D

Somehow I feel all this is terribly off topic and I apologize.

Thank you for proving to me that you didnt run to linux, you ran away from Windows and all the problems that the proprietary model. But as I see it, you still want to bring those problems with you. It sounds to me like you want linux windows.
[But linux is not windows. ]("http://linux.oneandoneis2.org/LNW.htm")The differences are what are important.From what I have read Im guessing you have less than a year running linux. You still use windows applications because you havent yet found the applications you want to replace them. Its something we all go through if we came from the Windows world. Not wanting to let go of what we are comfortable with. Hence wanting to run proprietary stuff on a free operating system. 
Foss is great, not because its Free not in cost but the freedom it gives you. Allowing you to break away from the proprietary world.

---

### Post by greymongrey on 2007-09-05
> **Kile said:**
> Thank you for proving to me that you didnt run to linux, you ran away from Windows and all the problems that the proprietary model. But as I see it, you still want to bring those problems with you. It sounds to me like you want linux windows.
[But linux is not windows. ]("http://linux.oneandoneis2.org/LNW.htm")The differences are what are important.

I'll admit I came to Linux to escape Windows. Probably a large number of the people here did. I am also glad that I have been useful today. :)

I do not want to make Linux into Windows. I like it just as it is. However, business people (the people who pay me the money that I need to eat) neither know or care about open source philosphy. If Linux is ever going to expand into the business world it is going to have to compromise a bit. The business world is centered on proprietary stuff and it's not going away. If a client sends you a .PSD file with layer effects, you are going to need Photoshop, like it or not. To do Flash, you'll need that app. Sometimes I bring my work home and I'm not going to risk the company's complex Excel file when I know OOO won't do that yet. Sometimes a customer sends us an Access database file. I can just see the boss's face if I told him we had just switched to OOO and Base wouldn't do that needed function we had been doing for years in Access. 

In the business work, software is just a tool and you pick the right tool for the job. If you don't, you're out. Proprietary stuff has it's place, as does open source stuff. My personal preference is posted below. I think the proper way to influence the business world is to give them what they are use to running and then slowly switch them to open source. It's going to be a slow process. 

It's funny, becuase the most requested app for Linux is Photoshop. One day the Linux market share will be large enough that Adobe will release PS and the rest of the Creative Suite and people will surge to Linux and nearly every one of them will be running proprietary stuff. Some of you guys won't use it as a matter of principle but most won't care. If Microsoft was really smart they would release Office for Linux. 
 
> From what I have read Im guessing you have less than a year running Linux. You still use windows applications because you haven't yet found the applications you want to replace them. Its something we all go through if we came from the Windows world. Not wanting to let go of what we are comfortable with. Hence wanting to run proprietary stuff on a free operating system. Free not in cost but the freedom it gives you. Allowing you to break away from the proprietary world.

You're right, I've been using Linux only since last November but you're wrong in the fact that I still use Windows apps. My main OS is PCLinuxOS and I don't have any Windows apps or wine installed. I much prefer the Linux apps. My wife is a photographer and I edit the pictures for her with the Gimp, for example. I keep up with my bills with a little spreadsheet with Open Office for another. I simply adore Amarok and K3B. Don't mistake what I do for work as being what my personally tastes are. 

However, if I did want to run proprietary stuff, I would. I get the impression you think it's evil and tainted. I don't. I see it as another tool. All tools have their place.

---

### Post by stmiller on 2007-09-05
> **greymongrey said:**
> 

However, if I did want to run proprietary stuff, I would. I get the impression you think it's evil and tainted. I don't. I see it as another tool. All tools have their place.

Reminds me of this quote:
[URL="http://www.brainyquote.com/quotes/quotes/l/linustorva129184.html"]
Microsoft isn't evil, they just make really crappy operating systems.[/URL]

I agree with greymongrey. 

There are many tools, and I think Linux gives great choice. I welcome commercial applications on Linux, if you want them. Adobe Flash 9 is nice, don't you think?

Choice is always better than "Linux is ONLY this way..." In my opinion, that sounds more like MS or Apple.

---

### Post by Kilz on 2007-09-05
> **greymongrey said:**
> 
You're right, I've been using Linux only since last November but you're wrong in the fact that I still use Windows apps. My main OS is PCLinuxOS and I don't have any Windows apps or wine installed. I much prefer the Linux apps. My wife is a photographer and I edit the pictures for her with the Gimp, for example. I keep up with my bills with a little spreadsheet with Open Office for another. I simply adore Amarok and K3B. Don't mistake what I do for work as being what my personally tastes are. 

However, if I did want to run proprietary stuff, I would. I get the impression you think it's evil and tainted. I don't. I see it as another tool. All tools have their place.

Thats better than what Im thinking right at this very second. That the entire time I have wasted on this thread are minutes I will never get back. Because someone wanted to argue the right to do something they are not doing themselves.

That makes even less sense to me that proprietary applications on a FOSS os.

I have a rusty old sledge hammer in the garage with a cracked handle. I wouldn't use it for fear of the head flying off. I have this strange feeling you would argue that its perfectly good for attaching a loose piece of trim in my hallway that needs a few finishing nails.

---

### Post by Kilz on 2007-09-05
> **stmiller said:**
> Reminds me of this quote:
[URL="http://www.brainyquote.com/quotes/quotes/l/linustorva129184.html"]
Microsoft isn't evil, they just make really crappy operating systems.[/URL]

I agree with greymongrey. 

There are many tools, and I think Linux gives great choice. I welcome commercial applications on Linux, if you want them. Adobe Flash 9 is nice, don't you think?

Choice is always better than "Linux is ONLY this way..." In my opinion, that sounds more like MS or Apple.

I would like it better if there was a free flash plugin that was as good as adobe's. Adobe's Flash has issues with crashing Firefox. Since Ubuntu or FOSS developers cant see the code we are stuck with it. As adobe with a few eyes on it, slowly works on it.

---

### Post by greymongrey on 2007-09-05
> **Kilz said:**
> Thats better than what Im thinking right at this very second. That the entire time I have wasted on this thread are minutes I will never get back. Because someone wanted to argue the right to do something they are not doing themselves.

That makes even less sense to me that proprietary applications on a FOSS os.



If you feel this time defending your beliefs is wasted minutes I really feel sorry for you. No matter, you twist everything I say into something I didn't, so maybe it is wasted. You sure you aren't my mother-in-law? Anyway, have a good life, my friend.

---

### Post by John.Michael.Kane on 2007-09-05
You both have your beliefs, and your reasons for them. Which have been clearly stated, however.There is no need to make things personal or turn to flaming.

IMHO the best thing to do is agreeing to disagree.

---

### Post by Emerald Wolf on 2007-09-06
Caught this thread, and thought that I'd add my .02 worth.

A little background.  I turned to Linux for several reasons.  First, I'd been running pirated versions of Win 3.11 for quite some time on my trusty old 486/33.  They worked, played the few games I had, all was okay.  After a while the software was blowing by my poor little machine, and I started to slowly upgrade.  Windows was kinda pokey, but it more software (games) available than OS/2. (Despite OS/2 being "compatible", it was FAR worse than WINE to get things going)  Anyway, it was seeing MS raise the price of Windows higher and higher, and their DRM preaching that made me start to worry about having a pirated copy. So when I happned into a copy of Red Hat 6.0 at Office Max, I thought I'd give it a try....(Just to clarify, at this point I did have a PII, and I had heard of Linux....had a friend that was really into it since around 1995)

Now, fast forward a few years (probably about 5).  I've successfully cut my teeth on Red Hat, Slack, Solaris, and now Ubuntu....Still have (a now legal) copy of Win2k just to handle a few pieces of evil hardware I still have.  I've been thoroghly impressed with Ubuntu.  But I learned a few lessons about free (as in freedom) and free (as in beer) software.

Free as in freedom software is nice, because it supports EVERYTHING.  If you dont have the driver disk for Windows, you're mostly screwed. (Well, it was more so in the old days before widespread internet access).  Linux has supported (with a couple of Win-hardware exceptions) all of my hardware.  Sure, it meant some head pounding, but the ...as in freedom crowd comes through. (I did find a solution for that Flash crashing Firefox thing, and had I the link handy, I'd post it)

But...

Free as in beer software has it's issues.  Much like free beer, it causes headaches.  Especially if you're weaning off of Windows, used to MS-DOS, and suddenly you're thrust into a world of /usr/blah/blah/blah that is actually sorted and there is hidden meaning to the madness.  God help you if you managed to have some hardware bit that isn't supported (Whaddya mean I can't run my 1 mb Bournelli Box on the 386?)  But like I said, a headache is the price of free beer.

As far as polluting Linux with proprietary code.  Well, you have several choices.  Support those that develop open source formats and codecs that compete with the likes of Flash.  Develop your own codecs.  Use the proprietary ones.  Live without the propreitary media.  It really all comes out in the wash eventually anyway.  Remember 8 tracks and Betamax?  Yeah, didn't think you did... :)  

Overall, I do what works.  I have my fair share of rants built it, but ultimately it comes down to whether is works or not (especially seeing as how my rants are occaisionally conflicting...ask my wife :lolflag:  Do I run proprietary stuff? Yes.  Do I feel bad about it? No.  To me the freedom of choice of OS had less to do with principal and more to do with it running on my old POS computers....(I'm giddy to try Linux on a 486 :)

To wrap up with the blasting cap that started this thread, I somewhat agree that it would be nice if it were a little easier to install the "proprietary blobs" that are plugins.  But in contrast, I'd use an open source version if it worked as well and installed easily.  I want it to work, with a minimum of head scratching (hear that LIRC developers :)

Catchya on the Flip Side.....

Emerald Wolf -- that said, I'd prolly still be a Windows only user had it not been for the friendly/helpful Linux community...=D>

---

### Post by greymongrey on 2007-09-06
> **Emerald Wolf said:**
> 
.... But I learned a few lessons about free (as in freedom) and free (as in beer) software.


Nice rant. Don't you thnk many people confuse the two free? I do.The free crowd always seems to want the free as in beer stuff, the free ride as it were. I think they forget there is also the free as in speech (or freedom) stuff and that might or might not have a cost.

---

### Post by Emerald Wolf on 2007-09-07
Well gonna keep it short since I've been somewhat plagued with the random reboot bug.  I think it's hardware related though (It's a dual PIII w/397mb of PC100, Matrox G400,)  I've had Fiesty running on a Pavilion for some time with few problems. (until the hard drive crapped).  So far I've not been able to nail down the issue.  Memory checked out fine, and it's done with more than a few sticks of ram and a couple of harddrives... :confused:

But as to the free software thing...There is a commonality between freedom and free beer philosophies....That being that seekers of both are willing to spend a lot of time and energy in there pursuit.  Funny thing is that the freedom lover does it for personal piece of mind.  The free beer chaser will expend enormous amounts of energy to "save" a dollar.....I guess it's a question of priorities....

Catchya on the Flip Side.....

Emerald Wolf -- although there are a few free beer ppl that are in it for the challenge (a good many crackers)

---

### Post by cprofitt on 2007-09-08
To the person that thinks a low post count = troll; sorry to disappoint, but I am just starting at the same place everyone who gets involved does.

To those that took my pondering seriously; thanks.

I guess the use of the word zealot needs a bit more explantion or rather a definition.

I refer to Linux users who refuse to use non-free software and demand open source software as zealots. Certainly some of those people are developers, but some are likely just leaches.

I get the concept of a company producing open source code so they can have it tested and proven before they deploy it. I get the concept that people contribute because of what they have already gotten and what they will receive... but in the end all of us need to eat... and I am not sure how the "zealots" plan on doing that.

As I said before - I appreciate open source. I have contributed on the Windows side to open source -- for the reasons some of you have listed, but at the same time I have produced code that I have charged for and not made open source.

I will continue my journey in trying to understand the FOSS community better, but at this point some things still puzzle me.

Again, thanks to those that chose not to label me a troll.

:)

---

### Post by spoatamaster on 2007-10-30
This is for most that are using Beryl, Compiz, Nvidia. the message or lockup you see as follows;
NVRM: Xid (0001:00): 8, Channel 00000000 . I am using a 9639 driver. I have an old 1.7GHz P4 Dell Inspiron 8200 GeForce4 440 Go and can run all the pretty graphics that everyone likes. well mine use to lock up and I found this;
as sudo or su (root) you need to do a lsmod |grep agp
you will see something like this;
intel_agp and a nvidia agp
well you need to blacklist the intel_agp by going to /etc/modprobe.d/  in Suse vi the blacklist and add 
blacklist intel_agp 
this removes it from the modules on startup, before you reboot, you should also go to your xorg.conf  in /etc/X11 and vi the xorg.conf with the following line under the driver section of the card;
Option "NVAGP" "1"
you should restart, then you shouldn't have the lock up problems anymore, if you have an old Dell like mine you also need to set the;
Option "UseDisplayDevice" "DFP-0" 
or it will be blank as it is not a CRT device. So even on old laptop runs this very well and I have all the candy abiet one thing, I can not have those rain drops for some reason, but who needs it to rain all the time anyway.
Best Of Luck,
Spoata because you are spoata do it

---

### Post by nss0000 on 2007-10-30
CMOST:

Yep you're right -- I wouldn't touch festering_faun with a flaming pitchfork.  But YoY did you ever leave DAPPER LTS ?? It's a flawless "production box" OS  that works every day and updates without error.

I'll swap to the new LTS next April and I bet it's flawless too -- after all the poor dweebs have troubleshot low_beta versions of it like  FF.

---

### Post by spoatamaster on 2007-10-30
I am not ditching free. I have 20 free OS's on my old rinky dink laptop, even WindowsXP which I find quite boring anymore, I only have it because I have one program from my company I have to do my hours on, so I do this via good ole VBOX and VPN through this with Windows to turn in my time. Let me explain, I like to make things work, I like to investigate, I have only had a few problems, I am not a MCSE or any Cert type person, I spent 15 years in the U.S.M.C. making things work, blowing things up and yes you kow what else, cool, now I travel even more at a job that doesn't pay me what I am worth, I am always working I go to boring places, so I started using Linux a few years ago, and would actually like to get a job in this field, but I really do not know how, I use it sometimes at work, I am a quick learner but not a programmer, So this is my entertainment. Like I said I have all the BSD's, Qnx, DOS, and 20+ linux's on my box now, I used to have to reboot, but found VBox to work for this good enough, I know people hate linux, and hate Bill, I admire Bill Gates, I wish him all the money, I just wish he would give me some too, if it were not for Bill, the Evil Empire, you wouldn't have a laptop unless you are some rich person, I remember a few years ago, yes a few, a nice SGI box would cost only 10,000.00USD with no RAM, I have 4 at home I know, A Sun Sparc20 30,000.00USD, a MAC only 10,000.00 and then came Bill took Steve's idea and made it cheap, so he could make money and sell you a Computer, think about it? I don't knock any of it, I appreciate what these guys out there are doing, yes some people make it rich, but when you get up in age you will always find out this; Rich people were always Rich people or someone in there family was. look around you and you know this to be true, unless they won the lottery, come on, even Bill comes from a Rich family, he got a ticket in a Porsche at 15, I don't know any kid with a Porsche at 15, and to go to Harvard, has nothing to do with Grades, this is a Rich person School, ask the kid that got a perfect score on the SAT test and was not accepted to Harvard or any Ivy leauge school, so think about what you are b"tching bout,:confused:

---

### Post by kollapse on 2007-10-31
Not to sound like a jerk but I have been running the 64-bit version of feisty since it was released and it has never once locked up.
In fact, the only real issue I had with it was getting xgl to work right.

Last night I installed gutsy without a hitch. Same issue though was getting xgl to work, but it took me 5 minutes this time instead of 20 minutes with feisty.

To give some background, I have been running linux for a little over a year now, upgrading from Windows XP. 
I spent 3 days trying to manually install Debian. Once I got it right, I started tweaking it until it failed.
Then I discovered Ubuntu. It's been smooth sailing ever since.

---

### Post by Yellow Pasque on 2007-10-31
> **nss0000 said:**
> CMOST:

Yep you're right -- I wouldn't touch festering_faun with a flaming pitchfork.  But YoY did you ever leave DAPPER LTS ?? It's a flawless "production box" OS  that works every day and updates without error.

I'll swap to the new LTS next April and I bet it's flawless too -- after all the poor dweebs have troubleshot low_beta versions of it like  FF.

So what you're saying is that they're not going to add any new features to Hardy Heron, just troubleshoot the issues with FF and GG? LMAO, It's hilarious how blissfully unaware you are of how the development cycle works.

---

### Post by nss0000 on 2007-10-31
BigT:

Mebbe a few "toys" get thrown in --- but they will be toys scrubbed squeeky clean. What's certain is HH_LTS  -- a workingmans OS where toys play 2nd fiddle -- will arrive without even one showstopper. But thanks again, keep struggling_away at the betas, cleaning up bugs and validating drivers ... we appreciate it  %^/ .

---

### Post by tech9 on 2007-10-31
> **cmost said:**
> Unfortunately, after a year or so of relative happiness with Ubuntu, I find myself in the unfortunate position of distro shopping...again.  Why?  Because Feisty has a freezing problem and nobody has a solution.  I have searched these forums high and low as well as Google to no avail.  My workstation, which used to be rock solid and reliable for weeks on end under Ubuntu 6.06 and 6.10 now freezes unexpectedly under 7.04; for no apparent reason.  Sure, there's a reason, but nobody has been able to pin it down.  There are about a dozen or so posts on this subject on these forums alone and dozens more on various other Linux related forums all over the Net.  I thought if I compiled a new kernel, then it might solve the problem as some people running the latest Gutsy alpha have reported that the freezing stopped for them.  I will not run an alpha level OS on my production machine.  I tried to compile a custom kernel, but, my workstation keeps freezing during the compilation.  I cannot continue to put up with my workstation crashing and have decided to leave Ubuntu behind.

I've decided to switch to Debian Etch 4.0 for amd64 and I hope I will be able to get it to a state similar to my current Ubuntu Feisty amd64 box, albeit without the annoying freezes.  Out of curiosity, has anyone tested the latest Debian?  Pros?  Cons?  Thanks!  Perhaps I'll be back in October.

Have you tried upgrading to 7.10?

---

### Post by Yellow Pasque on 2007-10-31
> **nss0000 said:**
> BigT:

Mebbe a few "toys" get thrown in --- but they will be toys scrubbed squeaky clean. What's certain is HH_LTS  -- a workingman's OS where toys play 2nd fiddle -- will arrive without even one show stopper. But thanks again, keep struggling_away at the betas, cleaning up bugs and validating drivers ... we appreciate it  %^/ .

Oddly enough, I haven't had any problems with the release versions that weren't related to the ATI driver or Adobe Flash9 plugin. But yes, I do like to test the real alpha/beta releases and play with the new toys. Your welcome. (BTW, I still feel your opinion is uninformed. and based on generalization.)

---

### Post by nss0000 on 2007-11-01
BigT:

From the UBUNTU developers Summit ... sez the squawing seabirds own mouth:

".....
The primary goal for the Hardy development cycle is to make existing features more usable and robust rather than adding a lot of new functionality. This differs significantly from the Gutsy Gibbon development cycle which focused on delivering highly experimental features—like compositing by default—that improved the user experience at the expense of robustness in certain documented areas. ....."

Notice the oh-so-polite "... at the expense of robustness ..." lingo. Ha! We work-a-day low_risk_types are loving it and look forward to yet another 3-yrs of OS leasure. Finding useful tasks for the new right_priced 8x64 HW kit will keep us off-da-streets.

---

### Post by Yellow Pasque on 2007-11-01
> **nss0000 said:**
> ".....
The primary goal for the Hardy development cycle is to make existing features more usable and robust rather than adding a lot of new functionality. This differs significantly from the Gutsy Gibbon development cycle which focused on delivering highly experimental features—like compositing by default—that improved the user experience at the expense of robustness in certain documented areas. ....."

Very well then. I stand corrected.

---

