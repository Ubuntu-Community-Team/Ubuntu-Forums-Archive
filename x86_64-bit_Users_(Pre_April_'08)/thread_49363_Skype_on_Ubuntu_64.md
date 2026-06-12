---
title: "Skype on Ubuntu 64"
date: 2005-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by musther on 2005-07-16
I've been doing a lot of searching and reading about getting skype to run on Ubuntu 64, some people seem to have installed it directly from the i386.deb and some seem to have converted the deb.  I've tried the conversion:

[http://ubuntuforums.org/showthread.php?t=16143](http://ubuntuforums.org/showthread.php?t=16143)

but with no luck, anyone know how the people here seemed to do it?

[http://forum.skype.com/viewtopic.php?t=28932&highlight=ubuntu](http://forum.skype.com/viewtopic.php?t=28932&highlight=ubuntu)

I'm really stuck and just want somebody to tell me how to do it...  If anyone knows.

---

### Post by Jet2k5 on 2005-07-16
I'm sorry I can't be of much help, but I don't have a 64-bit system yet so I don't know what is up.  As for the package ask Tamir if he can make a package for ubuntu 64.  Refrain to the the topic on this forum about making packages.  I'm sure he will be delighted to make a package for you, and not only will you benefit from it, but many others :)

Good Luck :)

---

### Post by AllenGG on 2005-07-16
Ditto that.   Miss Skype, can install on older machine, but not on my 64 bit monster.
Allen

---

### Post by Jet2k5 on 2005-07-16
Like I said make a request for it.  Tamir is willing to I'm sure.  I would make it right now for you, but for one I don't know how to make .debs and on top of that I don't even have a 64-bit processor ... yet :P  But just ask ... seriously.  It's not that hard.  In fact I think I'll ask right now.

---

### Post by musther on 2005-07-17
Thanks, that saved me a good ten seconds  :)   Now, I wonder how long we'll have to wait.....  I really really really miss skype.

---

### Post by musther on 2005-07-18
Ok, so there's no way to build a deb for skype, could somebody talk me through setting up a 32bit chroot (and explain what exactly that is) and how to set up skype using it.

---

### Post by Jet2k5 on 2005-07-18
I can't walk you on how to do it, since I've never done it :).  However I can give you [this](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap_on_AMD64)  it's a good guy it appears.  If I have to set up a chroot mode when I get my 64-bit processor I'll be sure to follow this one.  Post back if some of the commands given aren't working, which I think it shouldn't.

---

### Post by musther on 2005-07-18
Thanks, I just came accross that myself, I'm in the middle of it now, I'll let you know how it goes, and if I need any help.  By the way, when are you getting this new PC we keep hearing about, you're getting very involved in the Ubuntu 64 side of things, and don't even have a 64bit CPU yet.  Get your new PC, get on the 64bit side of the fence, come on, it's great and we could do with you over here!

---

### Post by Flac on 2005-07-18
he may not have his new compy, but jet is one of the 64-bit side of the fences best members :p

 Keep up the good work jet, hope you can join us on the fast-processing-edge soon :)

---

### Post by musther on 2005-07-18
I know, but I can't wait for him to be able to build me packages!!!   :)

---

### Post by musther on 2005-07-18
Ok, I've got skype running in 32bit chroot.  It loads and connects, downloads my contacts etc.  When I try to make a call, it says connecting and then just hangs, it doesn't let me terminate the call.  The rest of skype continues to work, but the call panel hangs and can't be stopped.  Problem with audio? I don't know.

---

### Post by musther on 2005-07-18
According to the multimedia systems selector, my output is via the ESD and my input the OSS, the device is just my onboard sound card, can't quite remember what chip, I can look it up tomorrow but my mobo is Gigabyte GAK8NS Ultra 939.

I think it's ALC 850 AC97

I wonder if this could be why I'm havng trouble with XMMS too, the EDS isn't as well supported as OSS is it?  Is there any way to use OSS instead?  I've tried changing it in the multimedia systems selecor, but when I click test I get a 'could not open pipeline' error.

---

### Post by X3N on 2005-07-18
I don't see what is causing the difficulties, use the skype static QT release works fine, no messing arround with chroot either. [http://www.skype.com/go/getskype-linux-static](http://www.skype.com/go/getskype-linux-static)

extract and type ./skype 
bingo

---

### Post by Tamir on 2005-07-19
[QUOTE=X3N]I don't see what is causing the difficulties, use the skype static QT release works fine, no messing arround with chroot either. [http://www.skype.com/go/getskype-linux-static](http://www.skype.com/go/getskype-linux-static)

extract and type ./skype 
bingo[/QUOTE]

You gave me an idea. Maybe I can make a deb that copy this binary to /usr/bin/ ?
It doesn't have to be compiled.

Edit: But I don't think I have the permission to do that.

---

### Post by musther on 2005-07-19
[QUOTE=Tamir]You gave me an idea. Maybe I can make a deb that copy this binary to /usr/bin/ ?
It doesn't have to be compiled.

Edit: But I don't think I have the permission to do that.[/QUOTE]

Yep, that would work, the binary runs just fine, then you only have to mess around with the sound system to try and get it working.  The input from mic seems to be really bad in ubuntu, I can make it work, but it's a bit rough and it's quiet.  The other thing that seems to work is doing a forced architecture install of the 386 deb, if you have the required libs it works, but you're still stuck with the dodgy sound system.  

Two things to do with using skype and ESD which I learnt are:
If you kill esd (assuming you're using it) and then load skype it works fine.
If you remove esd and install the polypaudio packages, skype will work along with other apps, so long as two don't try to access the demon at the same time.

---

### Post by nwillis on 2005-07-19
[QUOTE=Tamir]You gave me an idea. Maybe I can make a deb that copy this binary to /usr/bin/ ?
It doesn't have to be compiled.[/QUOTE]

That should *definitely* be put in /usr/local or in /opt , not /usr....

Actually, I think it should be put in /opt and a symlink to /usr/local/bin

[QUOTE=Tamir]Edit: But I don't think I have the permission to do that.[/QUOTE]

Well, how is the MS Corefonts package built?  Back in the 'day when I was running Fedora, you had to download the .zip as-is, then extract and repackage an RPM with the corefonts.  But once I switched to Ubuntu, one of the first surprises was that the corefonts deb did all of that for me automatically -- seemingly.

Anyway, I don't know exactly how that works, but it ought to be possible to make a "dummy" package that downloads it, slaps it into /opt and makes a symlink.  

And doing a weird brute-force install like that is best insulated from the main filesystem anyway (hence /opt).

Any thoughts on how that might be done?

FHS Stickler,
N

---

