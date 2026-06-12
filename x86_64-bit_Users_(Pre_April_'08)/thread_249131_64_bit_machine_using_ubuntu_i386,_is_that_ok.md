---
title: "64 bit machine using ubuntu i386, is that ok?"
date: 2006-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by jalanbuntu on 2006-09-02
I've new AMD64 machine and I try to install ubuntu using i386 version. After installing, I found that my ps/2 optical mouse doesn't work properly.Otherwise if I use USB optical mouse, it's OK.

My question is....,
Is it ok to use i386 in 64 machine? Or Must I use the 64 version? Whats need to be consider before I'm going to install 64?

I'm going to install ubuntu in 12 client for my internet cafe. That's why I need to be convinced about what version should I install :biggrin:

Help me plizzz.... :) thanx

---

### Post by kaffelars on 2006-09-02
You may very well run the i386 version. You should, however, install the AMD optimized kernel (search for **linux-image** and pick the K7 version.

Some 32-bit software does not run well (or run at all) on the 64-bit version.
My experience was problems with Flash, Picasa, Skype, and OpenGL, and I decided to use the i386-version instead.

On the positive side though, the 64-bit version was very fast, and all the software that came with Ubuntu worked flawlessly.

---

### Post by ShadowRage on 2006-09-02
> **kaffelars said:**
> You may very well run the i386 version. You should, however, install the AMD optimized kernel (search for **linux-image** and pick the K7 version.

Some 32-bit software does not run well (or run at all) on the 64-bit version.
My experience was problems with Flash, Picasa, Skype, and OpenGL, and I decided to use the i386-version instead.

On the positive side though, the 64-bit version was very fast, and all the software that came with Ubuntu worked flawlessly.

flash, got working with nspluginwrapper. (download the rpm's and convert with alien, look for nspluginwrapper in these forums for more info)
picasa: havent tried it, but I'm sure installing it and getting it working wont be too hard.
Skype: install the 64 bit qt libs, then download the debs for the i386 version of qt3-mt in the ubuntu package search (one of the firefox engines) and ```
dpkg -x file.deb . 
```
and then
```
sudo cp ./usr/lib/* /usr/lib32/
```

skype works, it starts up a bit slow, if you have troubles starting it, install the linux32 wrapper. or add /usr/lib32 to /etc/ld.so.conf

there's always a way to get things done.



-------

Also, for the i386 question

Not a problem at all, for new/intermediate users, I'd recommend it until you get used to the feel of things then try to take on 64 bit as 64 bit lacks some things most users would cringe at.
backwards compatibility is nice, aint it though? you can still run a 32 bit OS, in fact the x86 arch has support back to 16 bit IIRC.

---

### Post by kaffelars on 2006-09-02
Both Picasa and Skype used to work, but stopped.
I would need a desktop OS that works without to much hazzle, so I don't think I'll bother to go back to 64-bit in the nearest future. 
It was fun trying though, and I guess I'll give 64-bit Edgy a try :)

---

### Post by Kilz on 2006-09-02
> **kaffelars said:**
> Both Picasa and Skype used to work, but stopped.
I would need a desktop OS that works without to much hazzle, so I don't think I'll bother to go back to 64-bit in the nearest future. 
It was fun trying though, and I guess I'll give 64-bit Edgy a try :)

So if one person fails to get something working, or does something that makes what they installed to stop working. Everyone else should install 32bit software?

---

### Post by Kilz on 2006-09-02
> **jalanbuntu said:**
> I've new AMD64 machine and I try to install ubuntu using i386 version. After installing, I found that my ps/2 optical mouse doesn't work properly.Otherwise if I use USB optical mouse, it's OK.

My question is....,
Is it ok to use i386 in 64 machine? Or Must I use the 64 version? Whats need to be consider before I'm going to install 64?

I'm going to install ubuntu in 12 client for my internet cafe. That's why I need to be convinced about what version should I install :biggrin:

Help me plizzz.... :) thanx

Depending on what you are going to use the systems for 64bit is an option. If you plan on doing heavy 32bit development work or running Windows applications. It may require a little more work but its possible. 
If you are going to surf, listen to music, write email, edit office documents, and play some linux games. 64bit is more than capable. The only thing you will want to do is install 32bit firefox. Look in my signature below for a script that can install the setup with 2 commands.

---

### Post by kaffelars on 2006-09-03
> **Kilz said:**
> So if one person fails to get something working, or does something that makes what they installed to stop working. Everyone else should install 32bit software?

Of course not! I just provide my experience. And from reading around on the forums, it's not a secret that some things are harder to get working on 64-bit.

As with all other Linux-matters, it's a matter of personal taste :)

---

### Post by tymek666 on 2006-09-03
> **jalanbuntu said:**
> I've new AMD64 machine and I try to install ubuntu using i386 version. After installing, I found that my ps/2 optical mouse doesn't work properly.Otherwise if I use USB optical mouse, it's OK.

Help me plizzz.... :) thanx

I've installed xubuntu i386 on old system with and rs232 mouse also didn't work, so i isn't rather AMD64 related problem (USB mouse works fine).

---

### Post by kopilo on 2006-09-03
> **jalanbuntu said:**
> My question is....,
Is it ok to use i386 in 64 machine? Or Must I use the 64 version? Whats need to be consider before I'm going to install 64?
Depends on your processor and if it is backwards compatiable, generally they are but I'd still recommend checking it out.

To my knowledge the AMD Athlon 64 processor series works fine under 32 operating systems. I also proberly should state that my $9 optical ps/2 mouse works fine under Ubuntu Drapper AMD64.

---

### Post by cneil on 2006-09-03
You should use 64-bit on my AMD64 if you have an application in mind that requres that type of performance.  I used 64-bit for about six months, but I got frustrated because lots of software requires extra tinkering to use on that distrobution.  It is true that 64-bit can be better than 32-bit, but it just takes more time to install and configure software.  
About a month ago I switched to 32-bit.  There is much better support and almost everything works out of the box.  I don't have any problems viewing web content and, except for the newest version of flash, everything just works.

---

### Post by pharcyde on 2006-09-03
I would go with the 64bit install.  I installed it on my AMD64 X2 and haven't looked back.  The one app that took a bit more to configure was wine.  But if you follow the how-to given by Kliz then its not an issue.  All 32bit apps should work without a problem so long as you have the 32-bit libraries to support them.

---

### Post by jalanbuntu on 2006-09-03
I've decided to use 32bit version first, since my friend who will help me to maintain the computers is new to ubuntu. So, I think may be it is the best way for me now to use 32bit version with less effort to maintain.
Maybe after we got some experiences, we will move to 64bit.But thank you guys for your comments. It really help me to decide :D

---

### Post by Kilz on 2006-09-03
> **jalanbuntu said:**
> I've decided to use 32bit version first, since my friend who will help me to maintain the computers is new to ubuntu. So, I think may be it is the best way for me now to use 32bit version with less effort to maintain.
Maybe after we got some experiences, we will move to 64bit.But thank you guys for your comments. It really help me to decide :D

No problem, I just hope you dont have a lot of crashes, slow opperation, missing drives, or inability to install that sometimes happen installing a 32bit os on a 64bit system.

---

### Post by ColinG on 2006-09-04
I've been usung Kubuntu 64 fir a few weeks now and it seems rock solid. What I hate (and this is Ubuntu generic) is the effort reuirwd to find codecs - libdvdcss etc). Why these cannot be included openly in a repository I do not know. Yes, I know "thank the Ubuntu God for Automatrix", but why cannot more distros go the way of PCLOS?

As a matter of interest, what are the real adfvantages of 64 bit though? I use it 'cause I have 64 bit kit and wnat to use it :). I don't see it being any faster than the likes of PCLOS or Mandriva 32 in general so where is the ereal benefit - it may be heavy editing like video - ideas?

So, 64 bit works great but if it were not for Automatix I would probably not have bothered.

---

### Post by Kuprin on 2006-09-04
Perhaps an X2 or similar processor has enough horsepower to handle 64-bit Ubuntu, but my Athlon 64 3000 does not.

Firefox-Win32 in Wine works, but is ridiculously slow. I can't get a proper framerate on VisualBoyAdvance. OpenGL is about the same as it is in 32-bit Ubuntu, though, which is interesting - probably due to the ATI drivers, that it doesn't work properly in either 64 or 32.

My current recommendation? 32-bit unless you have power to spare. If you don't have speed issues, go 64-bit, it'll give you a LOT more speed on the things that do support it. :)

---

### Post by John.Michael.Kane on 2006-09-04
Kuprin thats not true for my hardware,and with the same cpu

Athlon 64 3000+ socket 939
biostar tforce-6100
1GB mem 64 of it is used for onboard graphics processor
80GB sata
NEC dvd-rw

The setup above not only runs only 64bit ubuntu.it has compiled a kernel,and runs xgl/compiz.does the normal web surfing email ect.

[COLOR="Red"]**Note: It does not take an x2 or any other dual core cpu to run ubuntu64-bit**[/COLOR]

---

### Post by Kilz on 2006-09-04
I totaly agree you dont need an x2 for Ubuntu 64bit 
I have a Atalon 64 3500 
Radon express 200 graphics
1 gig ram 128 shared w/graphics
dvdrw
80gig hd

I also run only the 64bit version. I just run the generic kernel.
If you are running the ATI binary driver I have found the 8.26.18 version to be the best. Except for screen savers for some strange reason. But I normaly turn off my monitor. I have tried up to 8.28.8 .

---

### Post by pharcyde on 2006-09-04
I agree with the others.  Any AMD 64 X2 or not cpu will only see a speed increase from 64bit ubuntu.

---

### Post by patrickfromspain on 2006-09-05
I have migrated from the 32 bit ubuntu to 64bit. My machine:

Amd Athlon64 3200+
Asus mobo (A8V-E deluxe)
1 gig of ram
Nvidia 6600 256mb

All runs fantastic, I'd a bit snappier than on 32bits, but maybe it's only what I think, more than what I really feel ;)

---

