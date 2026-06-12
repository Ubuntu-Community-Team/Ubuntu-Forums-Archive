---
title: "Which version of ubuntu for pent D"
date: 2006-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Brokenrgv on 2006-08-24
hiya, just put together a new Pent D system, kinda confused about what version of Ubuntu to get is it the alternative version of amd64 or the power pc or desktop, sorry for the dumb question, thanks for the help

---

### Post by eternalsword on 2006-08-24
I would suggest the PC (Intel x86) desktop CD  that's what I'm using on my Pentium D.  I wouldn't use the 64bit version yet because of some software incompatabilities ie 32bit plugins and codecs.  Don't use the smp kernels (for dual-core) either as they have constant freeze-ups.  I guarantee that using one processer, Ubuntu is faster then Windows XP using both.

---

### Post by Brokenrgv on 2006-08-24
np thanks for the heads up :)

---

### Post by Kilz on 2006-08-24
> **eternalsword said:**
> I would suggest the PC (Intel x86) desktop CD  that's what I'm using on my Pentium D.  I wouldn't use the 64bit version yet because of some software incompatabilities ie 32bit plugins and codecs.  Don't use the smp kernels (for dual-core) either as they have constant freeze-ups.  I guarantee that using one processer, Ubuntu is faster then Windows XP using both.

The 32 bit plugins and codecs can easly be added to the 64bit version. The Firefox link in my signature contains an automated setup script. The codecs are all available in the repotitories , except the wmv-wma. They can be installed in under 10 minutes following the mplayer howto in 64bit areas sticky.

---

### Post by RAOF on 2006-08-25
> **eternalsword said:**
> I would suggest the PC (Intel x86) desktop CD  that's what I'm using on my Pentium D.  I wouldn't use the 64bit version yet because of some software incompatabilities ie 32bit plugins and codecs.  Don't use the smp kernels (for dual-core) either as they have constant freeze-ups.  I guarantee that using one processer, Ubuntu is faster then Windows XP using both.

If you've got a Pentium D, I would strongly suggest a SMP kernel.  Otherwise you're using exaclty one half of your processor.  Presumably you bought such a powerful CPU for a reason, so... :)

---

### Post by eternalsword on 2006-08-25
> **RAOF said:**
> If you've got a Pentium D, I would strongly suggest a SMP kernel.  Otherwise you're using exaclty one half of your processor.  Presumably you bought such a powerful CPU for a reason, so... :)

As I stated, the smp kernels cause constant freeze-ups.  I have to hard reboot after about four minutes.  And that was on a fresh install.  I don't know what would happen on my now modified system.

> 
The 32 bit plugins and codecs can easly be added to the 64bit version. The Firefox link in my signature contains an automated setup script. The codecs are all available in the repotitories , except the wmv-wma. They can be installed in under 10 minutes following the mplayer howto in 64bit areas sticky.


I guess I just didn't want the hastle and as far as I know ndiswrapper doesn't work on 64-bit with 32-bit drivers.  And alot of people need ndiswrapper if they go wireless like I do.

---

### Post by Kilz on 2006-08-25
> **eternalsword said:**
> I guess I just didn't want the hastle and as far as I know ndiswrapper doesn't work on 64-bit with 32-bit drivers.  And alot of people need ndiswrapper if they go wireless like I do.

Hastle? No version of Ubuntu is 100% hastle free. Some setup is required regardless of the version. 64bit Dapper is pretty much hastle free depending on what you want to use it for. If you want to do some things like development you are going to do some additional setup, regardless of the version. If you are just using it for common tasks, there is very little setup.
As for ndiswrapper, it is avaiable. [There is even a howto]("https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64") to set it up. Again this is no different than the 32bit version, you have to do [setup on it to.]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

It seems you are not alone in these ideas that its "harder" or something is missing". It seems we in the 64bit section have to deal with this fud all the time.](*,)  Its sad that it continues to happen. I find it even more prevalent in the beginners section where people who failed installing the 64bit version spread fud constantly.

---

### Post by eternalsword on 2006-08-25
> **Kilz said:**
> Hastle? No version of Ubuntu is 100% hastle free. Some setup is required regardless of the version. 64bit Dapper is pretty much hastle free depending on what you want to use it for. If you want to do some things like development you are going to do some additional setup, regardless of the version. If you are just using it for common tasks, there is very little setup.
As for ndiswrapper, it is avaiable. [There is even a howto]("https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64") to set it up. Again this is no different than the 32bit version, you have to do [setup on it to.]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

It seems you are not alone in these ideas that its "harder" or something is missing". It seems we in the 64bit section have to deal with this fud all the time.](*,)  Its sad that it continues to happen. I find it even more prevalent in the beginners section where people who failed installing the 64bit version spread fud constantly.

I'm not some ignorant noob.  Please read [http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#Can_I_use_32-bit_Windows_driver_in_64-bit_mode.3F](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#Can_I_use_32-bit_Windows_driver_in_64-bit_mode.3F)
And I didn't say it was harder I just didn't want to deal with the amount of hastle for the amount of gain.

---

### Post by Kilz on 2006-08-25
> **eternalsword said:**
> I'm not some ignorant noob.  Please read [http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#Can_I_use_32-bit_Windows_driver_in_64-bit_mode.3F](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#Can_I_use_32-bit_Windows_driver_in_64-bit_mode.3F)
And I didn't say it was harder I just didn't want to deal with the amount of hastle for the amount of gain.
No matter what some faq's says. Obviously it can be done since there is a howto telling us how to do it.
By calling it a hassle you are saying its annoying, troublesome, difficult. Harder may not have been a good choice on my part , but hassle isn't a good choice on yours. 
The amount of gain is subjective, YMMV. This is because the applications you may use may not give a benefit. But in that situation, why on earth would someone get a 64bit processor to run low level applications? You might as will save your money and buy a celeron. Secondly are you saying that those low level applications are so troublesome? In that case what low level applications are they? When did you try to install them?
In any case are you honestly saying you believe others are going to run those same low level applications on a 64bit processor?

---

### Post by eternalsword on 2006-08-25
> **Kilz said:**
> No matter what some faq's says. Obviously it can be done since there is a howto telling us how to do it.
By calling it a hassle you are saying its annoying, troublesome, difficult. Harder may not have been a good choice on my part , but hassle isn't a good choice on yours. 
The amount of gain is subjective, YMMV. This is because the applications you may use may not give a benefit. But in that situation, why on earth would someone get a 64bit processor to run low level applications? You might as will save your money and buy a celeron. Secondly are you saying that those low level applications are so troublesome? In that case what low level applications are they? When did you try to install them?
In any case are you honestly saying you believe others are going to run those same low level applications on a 64bit processor?

I don't really want to turn this thread into an argument.  The howto you pointed to was instructions for 64bit ndiswrapper with WinXP64bit drivers.  The link I gave was directly from the ndiswrapper developers and they say it can't be done with 32bit drivers on 64bit ndiswrapper.  So between no wireless with 64bit with my 32bit only device and wireless with 32bit, I will choose 32bit 100% of the time.  That is the amount of gain for amount of hassle (and I do mean annoyance) I was referring to, sorry if that wasn't clear.  The reason I have 64bit processor is because I await the time when the gain is greater than the hassle and because I will be installing Vista when it's primed to go.  I won't be able to use wireless with Vista for the same reason I can't use wireless on 64bit ubuntu, but ubuntu is my primary OS so I need internet on it.  And just so you know, I bought mine on sale, so it was cheaper than the 32bit ones out there.  Just because I don't utilize it now is no reason not to plan ahead.  The same reasoning applies for me not using the smp kernels.  The amount of hassle (constant freeze-ups) does not surpass the amount of gain (dual-core), but I await the day when that is not the case.

---

### Post by livedevil on 2006-08-26
I'd reccomend using the 64 bit with the amd64-xeon kernel/module/images.

My cpu is a plain jane Pentium D 820 w/2gb of ram- running the 386 kernel is painfully slow-- actually it is slower than winxp by a good margin.  I tried the smp versions (incl the 686) as well when I had the 32-bit Ubuntu installed and experienced a decent increase in performance.  When I re-installed ubuntu using the 64-bit dvd I noticed drastic improvements.  

The difference in performance between the 32-bit and 64-bit versions of Ubuntu is well worth the extra effort to configure the above mentioned items (which are not really that difficult, IMO).



(on a side note--and only b/c it was referred to in an above post)
I have used both the 32 and 64-bit Vista betas (newest release), and the 64 bit was much quicker than the 32-bit version (which is a complete mess) when I tried them out.  Likewise, windows xp pro 64 shows noticable improvements over the windows xp pro 32-bit edition and I would purchase it if the driver support was better (you can get a free 6 month trial from MS, or at least you COULD back in May).

my .02

---

### Post by eternalsword on 2006-08-26
> **livedevil said:**
> I'd reccomend using the 64 bit with the amd64-xeon kernel/module/images.

My cpu is a plain jane Pentium D 820 w/2gb of ram- running the 386 kernel is painfully slow-- actually it is slower than winxp by a good margin.  I tried the smp versions (incl the 686) as well when I had the 32-bit Ubuntu installed and experienced a decent increase in performance.  When I re-installed ubuntu using the 64-bit dvd I noticed drastic improvements.  

The difference in performance between the 32-bit and 64-bit versions of Ubuntu is well worth the extra effort to configure the above mentioned items (which are not really that difficult, IMO).



(on a side note--and only b/c it was referred to in an above post)
I have used both the 32 and 64-bit Vista betas (newest release), and the 64 bit was much quicker than the 32-bit version (which is a complete mess) when I tried them out.  Likewise, windows xp pro 64 shows noticable improvements over the windows xp pro 32-bit edition and I would purchase it if the driver support was better (you can get a free 6 month trial from MS, or at least you COULD back in May).

my .02

I guess the way to go about it then is to try the 64bit and see if everything works that you need.  If it doesn't, go with the smp kernel to see if it's stable on your system.  If all else fails like it did with mine, use the 386 kernel.

---

### Post by Kilz on 2006-08-26
> **eternalsword said:**
> I guess the way to go about it then is to try the 64bit and see if everything works that you need.  If it doesn't, go with the smp kernel to see if it's stable on your system.  If all else fails like it did with mine, use the 386 kernel.

All 64bit kernels are smp. :D

---

### Post by eternalsword on 2006-08-26
guess I should have said 32bit smp

---

### Post by wilsonrm on 2006-09-07
i've got an intel 805 proc overclocked to 4.01 GHz with the standard 32bit 686-smp kernel. it's fast (of course) and stable but would it be worth fiddling with 64-bit right now since it seems a bit experimental to some degree over the standard packages in the repositories? this is the production machine in my network, but if there is quite a bit of effort compared to the standard dist, then i'm wondering if i should save experimenting with my amd64 that's kinda busted right now. will it be a few dist releases until 64-bit is as straightforward as the 32-bit? what are your opinions?

---

### Post by Kilz on 2006-09-07
> **wilsonrm said:**
> i've got an intel 805 proc overclocked to 4.01 GHz with the standard 32bit 686-smp kernel. it's fast (of course) and stable but would it be worth fiddling with 64-bit right now since it seems a bit experimental to some degree over the standard packages in the repositories? this is the production machine in my network, but if there is quite a bit of effort compared to the standard dist, then i'm wondering if i should save experimenting with my amd64 that's kinda busted right now. will it be a few dist releases until 64-bit is as straightforward as the 32-bit? what are your opinions?

First off 64bit is no experimental. Its pretty stable. The problems you may have relate to proprietary applications like flash and multimedia codecs that the owners of said applications have not made 64bit versions. That isn't to say that these are not available, but you might have to follow a howto or install a automated install script.
The other area of extra work is development packages. The work around for them is a chroot. But you should be running development in a chroot anyway imho.
Granted in a few releases we may see multiarch that would solve the multimedia work arounds. But we are talking Edgy +1 or +2 as Ubuntu developers are waiting on the slow as snails Debian development process.
Being that its a work computer, unless it has extra room to make another partition to test 64bit I would leave it alone. If it does have room install it, you can see if it works for you, and if it doesn't you can go back to using the the 32bit install.

---

### Post by eternalsword on 2006-10-06
I tried the current 32-bit smp kernel and it is no longer freezing up on me :)  I doubt it was the kernel itself that was causing the freezes, but something arbitrary on my system, but I'm glad it's working because it is much faster, now it beats XP by a landslide.

---

