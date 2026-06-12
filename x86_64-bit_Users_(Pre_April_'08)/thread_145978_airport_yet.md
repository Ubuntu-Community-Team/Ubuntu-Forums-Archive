---
title: "airport yet?"
date: 2006-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidmaxwaterman on 2006-03-17
Hi,

I'm hankering to get free of OS X and install Ubuntu on my Apple. I have a Titanium Powerbook G4/800 DVI.

I've been led to believe that the only thing not working is the airport wifi card, so I'm wondering if there's been any progress with making it work.

I found this :

[http://www.fisica.unipa.it/~lavaget/ubuntuae/](http://www.fisica.unipa.it/~lavaget/ubuntuae/)

but it's about the airport express, which might have a different chipset in it.

Anyone care to give me an update?

Max.

---

### Post by codejunkie on 2006-03-17
[QUOTE=davidmaxwaterman]Hi,

I'm hankering to get free of OS X and install Ubuntu on my Apple. I have a Titanium Powerbook G4/800 DVI.

I've been led to believe that the only thing not working is the airport wifi card, so I'm wondering if there's been any progress with making it work.

I found this :

[http://www.fisica.unipa.it/~lavaget/ubuntuae/](http://www.fisica.unipa.it/~lavaget/ubuntuae/)

but it's about the airport express, which might have a different chipset in it.

Anyone care to give me an update?

Max.[/QUOTE]

i don't know for 100% sure, but i've seen several posts on this, and from what i've read the regular airport card should work. but just in case download the ubuntu live cd, and make sure everything works before you install. if it works with the livecd you shouldn't have any problems when you install it.

---

### Post by stuporglue on 2006-03-17
>> i don't know for 100% sure, but i've seen several posts on this, and from what i've read the regular airport card should work. but just in case download the ubuntu live cd, and make sure everything works before you install. if it works with the livecd you shouldn't have any problems when you install it.

It's only in Dapper, IIRC. Dapper is the devel version, but works fine for many people.

---

### Post by jdp on 2006-03-17
Even AP Express doesn't work on the LiveCD right off.  You need to get some extra software and write some scripts to get it working.  Regular, original AirPort works just great already, even back in Breezy and Warty.

---

### Post by davidmaxwaterman on 2006-03-17
re. original airport card working

I assume I have the 'original' - it's 802.11b only.

I've already tried the most recent (breezy?) live cd - that's why I think the airport doesn't work. If it should work, perhaps I'll try it again...do I need to do anything to get it working?

Max.

---

### Post by stuporglue on 2006-03-17
> re. original airport card working

I assume I have the 'original' - it's 802.11b only.


802.11b == the original. 

> I've already tried the most recent (breezy?) live cd - that's why I think the airport doesn't work. If it should work, perhaps I'll try it again...do I need to do anything to get it working?

I think it should detect it. I never ran Ubuntu on my Mac that had the original card (Ubuntu wasn't arround then), but if you have to do anything, you might have to open a terminal and run "sudo modprobe airport". That'll load the module for the card if it wasn't automatically detected. With it loaded, the card might show up in (menu) System-->Administration-->Networking.

---

### Post by Ikzann on 2006-03-17
Airport (original) worked perfectly on my old iMac under Hoary and Breezy.

---

### Post by Rxke on 2006-03-18
The original Airport works without a hitch (Hoary and Breezy) on my (old) Clamshell iBook, I don't see why it shouldn't work in newer machines...

---

### Post by stuporglue on 2006-03-18
> The original Airport works without a hitch (Hoary and Breezy) on my (old) Clamshell iBook, I don't see why it shouldn't work in newer machines...

The orriginal airport will work on any machine it can go into. At one point though, Apple stopped making machines that can fit the 802.11b airport card. The new card (aka. Airport Extreme) has a Broadcom chip, and there wasn't Linux support for it untill recetly. 

I don't remember the time frame of when the switch occured, but it might have been two years or more, hence the "old machines" references.

---

### Post by ssam on 2006-03-20
it should work. can you run
```
iwconfig
```
in a terminal and post the output here.

---

### Post by engla on 2006-03-20
For Airport Express, the new card you need firmware (extracted from OSX) in addition to the driver (included in Dapper, can be built on Breezy). Because of this, it can never work out of the box..
I've seen many howtos on this, so just search around the net..

---

