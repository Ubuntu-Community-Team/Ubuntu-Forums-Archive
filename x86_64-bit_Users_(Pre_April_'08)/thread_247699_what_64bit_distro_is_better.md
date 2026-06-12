---
title: "what 64bit distro is better"
date: 2006-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by sunrex on 2006-08-31
what 64bit distro is better? im not talking about KDE or GNOME, i can easily download those.

what im asking is what distro works the best with 64bit? ubuntu or kubuntu? Whats faster? (yet again, im not talking about KDE or GNOME, from what i understand ubuntu and kubuntu are not the same distro, kubuntu is baised on ubuntu but has other core files.. from what i know)

Thanks

---

### Post by Carl H on 2006-08-31
I think that Ubuntu and Kubuntu are exactly the same apart from the desktop?

I had all kinds of problems with FC4 64-bit, so wouldn't recommend it. I have a new, almost built, 64-bit PC at home that's going to have Ubuntu Dapper 64-bit installed sometime soon, so I'll see how I get on with that. First impressions from reading various Ubuntu sites (including this one) are that Dapper 64-bit is a lot easier to sort than FC4 was. Watch this space....

---

### Post by Kilz on 2006-08-31
> **Carl H said:**
> I think that Ubuntu and Kubuntu are exactly the same apart from the desktop?

I had all kinds of problems with FC4 64-bit, so wouldn't recommend it. I have a new, almost built, 64-bit PC at home that's going to have Ubuntu Dapper 64-bit installed sometime soon, so I'll see how I get on with that. First impressions from reading various Ubuntu sites (including this one) are that Dapper 64-bit is a lot easier to sort than FC4 was. Watch this space....

Ubuntu and kubuntu are the same except for the desktop and some of the applications. The command sudo aptitude install kubuntu-desktop will install not just kde, but the things that go along with kde like Kate. Either or in this one for being fast. I think Xubuntu is the fastest of the 3. You could also install either fluxbox or icewm and they would be faster still. But a lot harder to setup.
Now for what I dont recommend. SuSE 10.1, what a mess. I left it and installed Ubuntu and never looked back. The last straw was RTFM when I had problems.

---

### Post by cocteau on 2006-09-01
My 2 cents.

I used Fc4 and had some problems using that. I was alright, especially with the audio support from Planet CCRMA, but in the end I felt it was too bloated, and the upgrade from fc3 to fc4 severely slowed down real-time audio. Gentoo 64 worked quite well, however I managed to ruin two installs trying to experiment with different settings (I'm quite new to linux) and it just takes too long to setup a working system.

Ubuntu seems to be the best of the bunch so far, although I keeping an eye out for what the people at 64studio are doing, as that looks interesting.

I installed the various desktops a while ago to experiment and as for my experiences. KDE looks good and feels nice and fluffy, so 10 points for eye candy. However it feels too big (i.e. slow) and I don't like arts. 
   Xfce was good. I looks alright, although a bit too OS-X inspired as default, but nice features and a good feel when you're working in it. Loads fast too, so that's a bonus.
   Fluxbox is my favorite. It's not that hard to configure if you're prepared to do a bit of reading and it's blisteringly fast. 
   But in the end I always fall back on Gnome for its good-looking simplicity. I works well, it looks good, it loads reasonably fast and has a nice layout and structure.

   But at the end of the day it's really what's working best for you, so I suggest installing the meta packages for Kubuntu, Xubuntu and apt-get fluxbox or whatever else you might be interested in trying a get a feel for what works best. Just do this on a seperate install as it will install way to much stuff that might be difficult to get rid of afterwards.

   Hope that helps a little.

---

### Post by hizaguchi on 2006-09-01
As far as 64-bit support, I've had the most luck with Suse 10.1.  Nothing about it being a 64-bit OS got in the way of anything I wanted to do.  However, I had enough other problems out of it to not stick around very long.  Small upgrades are dangerous, you have to track down extra repositories to get some common drivers (fglrx, madwifi, some stuff that I thought was standard in alsa now), and unless you weed out the 32-bit libraries during installation you end up with a system that is actually slower than a plain 32-bit OS because certain programs (Firefox) load a whole extra set of libraries.

The next best thing I've found is Arch 64.  It doesn't have everything I need for my laptop (powersaved, networkmanager), and you'll have to compile alot of stuff yourself (very easy with the AUR, ABS, and makepkg), but the basic system itself seems very stable and functional.  Plus the compiling isn't much of a downside compared to the situation in Ubuntu, where most stuff is pre-packaged but you're up the creek if you need something that isn't or have a problem with something that is (synaptics, for me).

---

### Post by hizaguchi on 2006-09-03
Ok, I take it back.  Edgy 64 supports everything in my laptop (even suspend) and seems to be working flawlessly.  Despite being a beta, I'd say it's the best distro I've ever used, 64-bit or not.

---

