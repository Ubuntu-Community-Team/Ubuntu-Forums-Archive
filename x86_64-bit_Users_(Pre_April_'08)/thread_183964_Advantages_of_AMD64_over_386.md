---
title: "Advantages of AMD64 over 386"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by bforbes on 2006-05-29
I have an AMD64 processor so I installed the AMD64 version of Ubuntu. Did I have to do that? Could I have installed the i386 version, and if so, what advantages does the AMD64 version actually have?

---

### Post by Falados on 2006-05-29
Honestly,  the i386 is probably the best option at this point.  64 bit processors arn't widely supported yet, so most of the applications/libraries you are using are running in 32bit emulation mode anyway.  There is no Flashplayer for 64 bit, and there are a host of other things that still need developement...

On the bright side, you are no longer capped at 4GB of RAM?

---

### Post by bforbes on 2006-05-29
Sounds like I might switch to i386 if anything gives me too much trouble. I want to use flash and 32-bit codecs again, and I'm also planning on installing Wine, and the whole chroot business sounds a complicated. Thanks for the advice.

---

### Post by henriquemaia on 2006-05-29
[quote=bforbes]Sounds like I might switch to i386 if anything gives me too much trouble. I want to use flash and 32-bit codecs again, and I'm also planning on installing Wine, and the whole chroot business sounds a complicated. Thanks for the advice.[/quote]

While I do not have knowledge of technical issues like how many libs my 64bit Ubuntu is using in a 32bit emulation, I'm pretty much happy with my 64bit installation. I have flash, realplay, skype, and all those things I want to have running on my computer. I'm happy with the performance and stability. I don't think I would have a faster or stabler Ubuntu running a i386 version. But I'm using Dapper, the next-to-be release.

---

### Post by bforbes on 2006-05-29
[QUOTE=henriquemaia]While I do not have knowledge of technical issues like how many libs my 64bit Ubuntu is using in a 32bit emulation, I'm pretty much happy with my 64bit installation. I have flash, realplay, skype, and all those things I want to have running on my computer. I'm happy with the performance and stability. I don't think I would have a faster or stabler Ubuntu running a i386 version. But I'm using Dapper, the next-to-be release.[/QUOTE]

What kind of 32bit emulation is that?

---

### Post by sugonaut on 2006-05-29
[QUOTE=henriquemaia]I have flash, realplay, skype, and all those things I want to have running on my computer.[/QUOTE]

Can you post instructions on how you got Flash installed and working?  When I attempted to install I got a message stating that Flash is unsupported on 64 bit processors.

Is your Flash working with Firefox?  If so, which version of Firefox are you using?  Did you have to install the mozflash lib?

I am using 5.10, so perhaps it's something the next release of Ubuntu addresses.

Tx, sugo

---

### Post by bforbes on 2006-05-29
[QUOTE=sugonaut]Can you post instructions on how you got Flash installed and working?  When I attempted to install I got a message stating that Flash is unsupported on 64 bit processors.

Is your Flash working with Firefox?  If so, which version of Firefox are you using?  Did you have to install the mozflash lib?

I am using 5.10, so perhaps it's something the next release of Ubuntu addresses.

Tx, sugo[/QUOTE]

I believe this is what you're looking for:
[https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

Always do a wiki search, there's a lot of good stuff there already.

---

### Post by sugonaut on 2006-05-29
[QUOTE=bforbes]I believe this is what you're looking for:
[https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

Always do a wiki search, there's a lot of good stuff there already.[/QUOTE]

Yep, found that via another thread, shortly after posting a reply to this one.  Thanks for the quick response!

---

### Post by henriquemaia on 2006-05-29
[quote=sugonaut]Yep, found that via another thread, shortly after posting a reply to this one.  Thanks for the quick response![/quote]

Yes, I followed that HowTo.

Good luck.

---

### Post by kaalimato on 2006-05-30
[QUOTE=henriquemaia]While I do not have knowledge of technical issues like how many libs my 64bit Ubuntu is using in a 32bit emulation, I'm pretty much happy with my 64bit installation. I have flash, realplay, skype, and all those things I want to have running on my computer. I'm happy with the performance and stability. I don't think I would have a faster or stabler Ubuntu running a i386 version. But I'm using Dapper, the next-to-be release.[/QUOTE]

This is maybe little off topic, but how did you get that skype working? I have been fighting with it for 2 days, and I can't get it working. I am using ubuntu 5.10 amd64, with server install and xubuntu-desktop. I have tried to install it with apt-get, but it won't download the repositories where skype should be. I also tried to download it from skype.com and use dpkg, but it said that it can't be installed on 64. Do I have to install Dapper to get it work?

---

### Post by Kilz on 2006-05-30
[QUOTE=kaalimato]This is maybe little off topic, but how did you get that skype working? I have been fighting with it for 2 days, and I can't get it working. I am using ubuntu 5.10 amd64, with server install and xubuntu-desktop. I have tried to install it with apt-get, but it won't download the repositories where skype should be. I also tried to download it from skype.com and use dpkg, but it said that it can't be installed on 64. Do I have to install Dapper to get it work?[/QUOTE]

I have had some luck forcing 32 bit packages into dapper and manualy adding the lib's they need. I set up Breezy in vmware because I was courious and could not do the same thing. You will have to upgrade to even try it. You will have to look up any lib's it says it cant find and copy them into lib32.

---

### Post by Labyrinth on 2006-09-10
I've installed Edgy knot 2 amd64, but after some testing I'd rather want to switch to K7 again. (or generic 32bit. Whatever.)

Can I just uninstall all the 64bit packages and install a 32bit kernel and all new 32bit packages?

I don't really want to burn another CD when I'm already having a running system that I can get all the files with.

Thanks,
Lab

---

### Post by tseliot on 2006-09-10
> **Labyrinth said:**
> I've installed Edgy knot 2 amd64, but after some testing I'd rather want to switch to K7 again. (or generic 32bit. Whatever.)

Can I just uninstall all the 64bit packages and install a 32bit kernel and all new 32bit packages?

I don't really want to burn another CD when I'm already having a running system that I can get all the files with.

Thanks,
Lab

You have to install it from scratch

---

### Post by Labyrinth on 2006-09-11
Okay, thank you!

Is it possible to mount a CD image from one of the harddrives' partitions instead of burning an installation CD?

Like, with this floppy bootmanager in the /install directory of the CDs? (sbm)

Thank you,
-- Lab.

PS: Nice nickname! :)

---

