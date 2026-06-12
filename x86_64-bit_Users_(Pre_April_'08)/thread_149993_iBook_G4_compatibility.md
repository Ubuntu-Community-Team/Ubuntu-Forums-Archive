---
title: "iBook G4 compatibility?"
date: 2006-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by omeg on 2006-03-25
Hi everyone. I'm currently posting this on an old 400 MHz Toshiba laptop of which the screen has a response time of probably around 60 ms. I have two laptops, one of which is a much newer 3.0 GHz P4 that dual-boots Windows and Ubuntu, but I sometimes prefer using this old one because of how noisy the new one is.

I have been wanting to switch to Mac for a long time now, and now that I've got a decent job, I can start to look at new computers without just dreaming of ever buying them. Since I like the setup that I have now (one computer for all my heavy duty graphics work and another for occasional browsing/chatting) I want to sell my 3.0 GHz P4 and use the money to buy an older (probably second-hand) iBook G4, on which I'd dual boot Mac OS and Ubuntu, in addition to what will probably be an Intel iMac.

I'm cerrtain that I'll be able to boot Ubuntu on an Intel iMac in the future, so my question to you is: how is the compatibility rating of Ubuntu with an Apple iBook G4? I've thought that since Apple uses limited hardware vendors, it would be easy to get Ubuntu working on it 100%, but lately I've heard that this isn't the case.

Another thing I've been wondering about: since Apple is switching to Intel chips, will the old G4 and G5 chipsets still be supported with future releases?

Thanks a lot, hope you answer soon. :D

---

### Post by staticdisaster on 2006-03-25
Everything on my iBook works. Sleep, external fw & usb devices connected. Even the Airport Extreme card after some cryptic command line trickery.  I've never used the modem though. I'm using Dapper, btw.

---

### Post by spaceballl on 2006-03-27
With my iBook G4, just about everything works out of the box. The only thing you need to mess w/ is Airport Extreme. Well, there's always lots of tweaking to be done, but that's the major thing that is missing when you first boot it up. I wrote a quick how-to right here. For some, they have problems with it... but it works for most...
[http://www.ubuntuforums.org/showthread.php?t=142727](http://www.ubuntuforums.org/showthread.php?t=142727)

---

### Post by string on 2006-03-27
[QUOTE=spaceballl]With my iBook G4, just about everything works out of the box. The only thing you need to mess w/ is Airport Extreme. Well, there's always lots of tweaking to be done, but that's the major thing that is missing when you first boot it up. I wrote a quick how-to right here. For some, they have problems with it... but it works for most...
[http://www.ubuntuforums.org/showthread.php?t=142727](http://www.ubuntuforums.org/showthread.php?t=142727)[/QUOTE]

What about the energy management ? what autonomy can you get ? and does the cooling work fine or does the fan starts more that it should and makes the noise of twelve hardrock guitarists ??

---

### Post by engla on 2006-03-27
[QUOTE=string]What about the energy management ? what autonomy can you get ? and does the cooling work fine or does the fan starts more that it should and makes the noise of twelve hardrock guitarists ??[/QUOTE]
I think that energy/battery management works fine*, I run powernowd that down-cycles the cpu when it's idle and that seems to work fine. Compared to OSX, the fan runs quite much though, often starting instantly if I start an itensive task rather than wait 15 mins until it gets really hot (like OS X basically does). So there is a bit more noise, but I haven't looked into it or tweaked it a bit.. you can probably raise the threshold if you find the right configuration tool. 

The thermal kernel module works fine, so real temperature should be provided so you can make sure nothing goes wrong.. I don't know where the safe limit for temperatures is though.

*fine in terms of battery life. Mostly 3-3.5 hrs normal usage on a year old iBook, not bad but far from excellent, of course.

---

### Post by ssam on 2006-03-27
the internal 56k modem will not work, as it is a soft modem.

i think ubuntu will keep supporting powerpc for a long time. i expect linux on macs to become more popular as they stop being supported by apple, adobe, ms etc.

---

