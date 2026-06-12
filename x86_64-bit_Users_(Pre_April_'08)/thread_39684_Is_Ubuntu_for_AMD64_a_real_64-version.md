---
title: "Is Ubuntu for AMD64 a real 64-version?"
date: 2005-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by bret on 2005-06-06
Hi,

ist the 64-bit version of Ubuntu a kind of "fake"-64bit distrubution like Readhat and SuSE that use a special /lib directory for the 64bit binaries or ist is a wannabe real 64bit one that Debian ist going be in some month, i.e. in /lib are all the 64bit libraries.

Bret

---

### Post by FluffyElmo on 2005-06-06
I believe it is a pure 64bit OS, but others may know more. /lib is linked to /lib64, there is also a /lib32 but in my case there is very little in there.

```
root root   8192 2005-04-10 16:22 lib
root root   4096 2005-04-10 16:20 lib32
root root      3 2005-04-10 16:18 lib64 -> lib

```

---

### Post by ::DoGG:: on 2005-06-06
It is a pure 64 environment, just like debian amd64 releases. All th elibraries are 64, soem are 32, but only for compatibility purpose.

---

### Post by Optimal Aurora on 2005-06-07
Yep... Just like other OS's like Fedora, Ubuntu is pure 64 bit as long as you have the amd64 version or the x86_64 version of say Fedora...

---

### Post by fistfullofroses on 2005-06-25
So much talk of Fedora... am I the only human on Earth who hates Fedora?

---

### Post by Jet2k5 on 2005-06-26
hehe well I hear from a lot of people that have Fedora Core that it is one of the best  64-bit distros next to gentoo.  From several people they said that Ubuntu lags behind in the 64-bit edition.  Not only in programs, but in general use.  They complain that the desktop is very slow.  I don't know what is up with this because you have those that can't get it working right and those of you who say that 64-bit is awesome and running flawlessly.  I just hope that this goes for me as well when the time comes.

I'm building a 64-bit computer by the end of this summer.  Going AMD64 and maybe nforce4.  With an Nvidia GeForce 6800 256 mb.  I just hope that ubuntu will work on it as well as it's working on my lappy right now  :-P 

Congrats for those of you who have it working good.  Right now I look at my official 64-bit edition cd's that I just recieved in the mail and it wants me want to pop it in .. but of course /me has no computer!  ](*,)

---

### Post by dmn_clown on 2005-06-26
You should be patient on building that dream system.  nVidia has a new chipset coming out that will make the 6800 GT's look like an FX5700. :smile:

---

### Post by Jet2k5 on 2005-06-26
Is it the 7800? I don't know I might go for something cheaper maybe the 6600 GT or so, why do you say that though?  it is a good card.  What I'm worries about now is SATA , nforce4, and 64-bit working with Ubuntu/ linux in general.  Right now I've asked in a couple of forums and people say that Fedora has one of the best 64-bit distros out there.  Ubuntu seems to lag behind.  Which I can't say because I've never tried.  But I've seen a lot of issues here that seem to be because ubuntu can't do things 64-bit properly.

My price is going to be smaller than I thought ... I was aiming about 1000 now it's down to like 800.  I have to hold back on the LCD and the maybe the nvidia gforce 6800 I might go with 6600 or so.  That time has to come yet.  Also 64-bit or x82

---

### Post by jerutley on 2005-06-26
Right now, I'm using an Athlon 64 3000+ cpu, with a NForce4-based Asus motherboard (A8N-SLI Deluxe), with Ubuntu's AMD64 system on it.  Everything works beautifully in where I use it (both nics and SATA chipsets are supported beautifully by Ubuntu).  Nvidia's SLI isn't working in Linux yet, but that's a minor thing to me anyway.  

The big problem with Ubuntu AMD64 is the fact that the 3rd-party repos, such as the hoary-backports and hoary-extras repos, have zero AMD 64 support in them, which means I can't view my divx/xvid videos, and can't watch DVD's in Ubuntu.

---

### Post by FluffyElmo on 2005-06-27
Really? I can play DVDs and DIVX/Xvid. I can also encode to DIVX without difficulty...it's only some closed source codecs I have trouble with such as WMV9/10 and some RealPlayer. 

Probably going a bit off topic but I think I got libdvdcss2 from the marillat repositories...though it has been a while so I can't be sure. Add the following to */etc/apt/sources.list* (edit as root):
```

deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main
deb ftp://ftp.nerim.net/debian-marillat/ stable main

```
In any case, you can try the ubuntuguide.org instructions with marillat installed and see if you get video working. If you still have trouble, I can try and help further when I get home to my 64bit box.

---

### Post by negatory on 2005-06-27
I'm running 64bits since Hoary preview and it runs perfectly!The only thing I only miss is Macromedia Flash...apart from that everything runs fast and stable on my system.And I have no complaints at all about ubuntu it's solid,fast,stable and Debian  :smile: !

Pedro Carrico

---

### Post by Jet2k5 on 2005-06-27
Sounds good, but from other forums I hear nothing but bad things about ubuntu 64  :? 

It's not multilib or something like that I don't know.  I have the official 64-bit Ubuntu CD so that is THE first cd that is going on there.  I'm going to test it out with the Live CD first, since I think ubuntu has one of the best Live CD's out there.

Then if I don't like ubuntu 64-bit I will download fedora.  Since that seems to be the best one right now besides gentoo, and it has that multilib allowing 32-bit apps like Firefox etc. etc....

---

### Post by jerutley on 2005-06-28
[QUOTE=FluffyElmo]Really? I can play DVDs and DIVX/Xvid. I can also encode to DIVX without difficulty...it's only some closed source codecs I have trouble with such as WMV9/10 and some RealPlayer. 

Probably going a bit off topic but I think I got libdvdcss2 from the marillat repositories...though it has been a while so I can't be sure. Add the following to */etc/apt/sources.list* (edit as root):
```

deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main
deb ftp://ftp.nerim.net/debian-marillat/ stable main

```
In any case, you can try the ubuntuguide.org instructions with marillat installed and see if you get video working. If you still have trouble, I can try and help further when I get home to my 64bit box.[/QUOTE]

From what I've read on the forum here, the marillat repos are not recommended because of how much ubuntu has diverged from the debian tree.  I'm personally about to go to the x86 ubuntu on my amd64 box and see how that works.

---

### Post by FluffyElmo on 2005-06-28
> From what I've read on the forum here, the marillat repos are not recommended because of how much ubuntu has diverged from the debian tree. I'm personally about to go to the x86 ubuntu on my amd64 box and see how that works.

To get DVDs playing with the x86 version you're still going to have to use the marillat repositories though. They have diverged, but it's more apparent with complex packages such as ffmpeg and transcode. Simple packages like libdvdcss2 (needed to decode commercial DVDs) havn't changed in ages, and you can get the various decoders from the standard (universe/multiverse) repositories.

You should be able to get DVDs/DIVX playing without too much trouble, since you have 64bit installed already it may be worth a try before reformatting?

---

### Post by dewey on 2005-06-29
Using marillat on a select number of packages like libdvdcss2 should work fine.  Just be sure to comment it out when you're not wanting a specific package that only marillat has.

---

### Post by Big Venus on 2005-06-29
yes if it wasn't the you could go and download macromedia flash player and it work...

Yes, that seems to be the only place to find the libdvdcss2 is in the marillats, why haven't they been move to the backports or extras yet?

---

### Post by jon_gunnar on 2005-07-11
[QUOTE=jerutley]Right now, I'm using an Athlon 64 3000+ cpu, with a NForce4-based Asus motherboard (A8N-SLI Deluxe), with Ubuntu's AMD64 system on it.  Everything works beautifully in where I use it (both nics and SATA chipsets are supported beautifully by Ubuntu).  Nvidia's SLI isn't working in Linux yet, but that's a minor thing to me anyway.[/QUOTE]
This was wery interesting for me. I got the same motherboard, AMD63 3500+, two sata disks and a dvd writer on he first primary pata. Grub uses over 4.5 minutes to start the system, and I have no clue were the problem might be.
Did you have any issues at all with the installation?

---

