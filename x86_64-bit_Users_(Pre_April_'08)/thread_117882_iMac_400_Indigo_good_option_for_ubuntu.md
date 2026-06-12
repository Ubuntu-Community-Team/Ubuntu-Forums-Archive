---
title: "iMac 400 Indigo good option for ubuntu?"
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by schmuckychucky on 2006-01-15
Hey everyone,

I have found a site that sells the iMac 400 Indigo (2001 model I think) for really cheap, and I am wanting an extra computer in my house that is just dedicated to use the internet, and satisfy my geeky needs for tinkering.  Would this computer be able to handle Ubuntu pretty well?  Thanks in advance for the input.

---

### Post by hndrcks on 2006-01-15
Hi, this page [http://www.lowendmac.com/imacs/2001-400.html](http://www.lowendmac.com/imacs/2001-400.html) and this page [http://www.lowendmac.com/imac/ideals.html](http://www.lowendmac.com/imac/ideals.html) should give you sufficient info about the iMac in question to make an informed decision.

That being said, OSX is a pretty cool OS; and there are problematic areas in PPC Linux (java being a good example). I went down the road you are currently on (B&W and Beige G3s, iMacs, and a Sawtooth AGP G4) and ended up with Jaguar or Tiger on every one. (The opportunities to tinker still exist with OSX, by the way.)

If you are looking for a groovy form factor to use with Ubuntu, you might want to take a look at XPC-style Intel hardware. My primary do-work-PC is an old Shuttle SK41G with an Athlon 2100. It's a competent platform in a very small package.

On the other hand... the introduction of Intel to the Mac platform is going to (IMHO) push prices on older Motorola Macs down significantly. There may be real deals to pick up  soon.

---

### Post by ssam on 2006-01-16
thats a resonable machine for browsing the internet and tinkering. they look good, are fanless (very quiet), quite good built in speakers if you want to put music on it.

you may need to stick some extra ram in it, but ram is pretty cheap.

there are a few things to note if you are running linux on powerpc. no flash, no realplayer, no skype, no wine, and i think java is a bit more work to get running (although i have not tryed to install java in ubuntu (i dont like it much)). i dont really miss any of these, but i think some people find them essential.

---

### Post by Avicus on 2006-01-16
Thats exactly what I'm using right now... it works, sorta... what I mean by that is X crashes on first install... or is broken anyway. No idea why, I have to put the screen color to 15 bit or 16/24 just lock it up. Debian PPC work fine at 24 so I don't see why Ubuntu has this problem. And noone can fix it! I've asked! Anyway, the machine is very snappy, but I do have 512 MB ram in it, which is a must. Go for it!

---

### Post by g12345567 on 2006-01-19
[QUOTE=Avicus]Thats exactly what I'm using right now... it works, sorta... what I mean by that is X crashes on first install... or is broken anyway. No idea why, I have to put the screen color to 15 bit or 16/24 just lock it up. Debian PPC work fine at 24 so I don't see why Ubuntu has this problem. And noone can fix it! I've asked! Anyway, the machine is very snappy, but I do have 512 MB ram in it, which is a must. Go for it![/QUOTE]

Same thing appens to me. I just installed a fresh copy

On my Mac G3 crt / indigo / 500mhz / 384mb ram / 20gb hdd / ati 16mb video

and nothing works properly. everything freezes for ages and clicking on items takes ages to respond. The software runs so slow. Even login takes ages to start up.

The fix as stated above is to goto the shell prompt / log in / edit the config file and change the defult colordepth from 24bit to 15. Everything should now work at a decent speed. But this is a known problem with this linux release and ati onboard video cards

[http://ubuntuforums.org/showthread.php?t=119573](http://ubuntuforums.org/showthread.php?t=119573)

As for performance. It runs slower than the native OS X.4.4 running on the same machine.

---

### Post by linear on 2006-01-19
[QUOTE=g12345567]The fix as stated above is to goto the shell prompt / log in / edit the config file and change the defult colordepth from 24bit to 15. Everything should now work at a decent speed. But this is a known problem with this linux release and ati onboard video cards

[http://ubuntuforums.org/showthread.php?t=119573](http://ubuntuforums.org/showthread.php?t=119573)[/QUOTE]

If you want 24 bit color back, you can disable dri instead:

[http://ubuntuforums.org/showpost.php?p=646240&postcount=3](http://ubuntuforums.org/showpost.php?p=646240&postcount=3)

---

### Post by ardibug on 2006-02-07
I just bought an iMac 400. Nice little machine. 

The problem I have is that when I installed OSX 10.3 everything works but there's some wierd thing where the mouse cursor leaves a pixelated trail on certain parts of the screen occasionally.

So I installed Ubuntu. No problem, or so I thought, until I decided to listen to the BBC. Unfortunately their site uses RealPlayer. I downloaded RealPlayer 10 Gold but I can't get it to install. 

I've followed the instructions and this is what happens:

[I][B]ian@ubuntu:~/Desktop$ chmod a+x RealPlayer10GOLD.bin
ian@ubuntu:~/Desktop$ ./RealPlayer10GOLD.bin
bash: ./RealPlayer10GOLD.bin: cannot execute binary file[/B][/I]

As you can probably tell I'm a complete novice at this, so please excuse me if I'm being particularly dumb. But any help or advice on how to install RealPlayer would be very much appreciated.

Ian

---

### Post by jdp on 2006-02-08
Did you do the FirmWare update before you installed OS X?  There are some known issues with the video if the FW isn't upto date.  It's so bad that even just booting the OS X CD, and not installing it, will cause trouble.  You'll need at least OS 9.1 installed somewhere to do the update.  The most currect for a slotloader should be 4.1.9f, IIRC.

---

### Post by linear on 2006-02-08
Is this a PPC binary that you've downloaded? If not, you are out of luck...
 
There are also instructions here, but they don't say whether Real makes a PPC binary available:
 
[https://wiki.ubuntu.com/RealplayerInstallationMethods](https://wiki.ubuntu.com/RealplayerInstallationMethods)

---

### Post by ssam on 2006-02-08
[QUOTE=linear]Is this a PPC binary that you've downloaded? If not, you are out of luck...
 
There are also instructions here, but they don't say whether Real makes a PPC binary available:
 
[https://wiki.ubuntu.com/RealplayerInstallationMethods](https://wiki.ubuntu.com/RealplayerInstallationMethods)[/QUOTE]

you can try the ones at [https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/) but i am not sure if they work well

---

### Post by ardibug on 2006-02-09
Thanks for the very helpful replies. It looks like there's quite a lot of stuff that won't run on a ppc with Ubuntu - and that's a shame :( 

So the iMac is now set up with OSX 10.3 - the simple fix was to reduce the colors to 256 - it looks terrible, but it works, and when I need higher res I can always switch.

As for Ubuntu - I really like it, so I've got the live version to run on my macs when I want to play, and I just installed the full version on my PC. The PC has always misbehaved ever since I bought it - it just didn't seem to like XP - but it ***loves*** Ubuntu - YAY! \\:D/

---

### Post by jdp on 2006-02-11
Did you need to do the FW update?  It's an extrememly common problem for iMacs if an OS X CD is booted before it is done.

---

