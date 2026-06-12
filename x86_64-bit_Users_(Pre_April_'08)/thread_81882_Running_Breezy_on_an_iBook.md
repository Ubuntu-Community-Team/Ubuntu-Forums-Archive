---
title: "Running Breezy on an iBook?"
date: 2005-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by felix_stegerman on 2005-10-25
Hi all,

My laptop (a Toshiba satellite A 50 522) recently broke. I'm hoping it can
be fixed for a decent price, but that doesn't seem likely.
So now, I'm looking around for a (possible) suitable replacement.

I've been running Debian on my Mac Mini for over three months now,
and I'm very happy. Especially because of the peace & quiet.
So I'm considering buying an iBook on which to run Breezy.

I used Hoary on my Toshiba, and everything just worked. That's why I
used Ubuntu instead of Debian.

Now I wonder whether the same would hold for the iBook.
I don't mind setting some things up by myself, but I would like to know
what I'm getting myself into.

I already know how to use Debian on PPC,
so I'm familiar with problems with Java and the unavailability of Flash.

I've also heard that Airport Extreme doesn't work so I figure I'd have to
buy a USB wireless adapter if I really want that.
(I never used WiFi on my Toshiba, so it's not a high priority)

Is there anything else (you think) I should be aware of ?

Thanks.


Felix

---

### Post by stuporglue on 2005-10-25
> Now I wonder whether the same would hold for the iBook.
I don't mind setting some things up by myself, but I would like to know
what I'm getting myself into.

I already know how to use Debian on PPC,
so I'm familiar with problems with Java and the unavailability of Flash.

When I installed Ubuntu on my iBook, it auto detected everything that was going to work. Sound, sleep, etc. Java 1.4.2 is installable and worked mostly fine. CD burning and DVD playing worked too. 

> I've also heard that Airport Extreme doesn't work so I figure I'd have to
buy a USB wireless adapter if I really want that.
(I never used WiFi on my Toshiba, so it's not a high priority)

There is a project to reverse engineeer the drivers. It's made quite a bit of progress, but it's probalby still a year off. (wild unsustantiated guess). I tried a number of USB wireless adapters under Gentoo on my iBook, but never got them to work. Some people have gotten them to work though, so you might get lucky. 

> Is there anything else (you think) I should be aware of ?
ATI cards have more in kernel support in Linux than Nvidia does. Since neither provide binary drivers for ppc, this means getting an ATI card will get you the most ppclinux support. This affects sleep as well as video acceleration. 

oh yeah, my iBook was a 12 inch 1.2 GHz model from arround October 2004.

---

### Post by Rxke on 2005-10-25
Skype doesn't work on Linux ppc arch, either.

---

### Post by felix_stegerman on 2005-10-28
Thanks.

I'm happy w/ IBM Java 1.5 beta on my Mac Mini,
I don't use Skype, and I think I can live w/out Airport Extreme.

So, unless anybody has something negative to add,
I'll probably buy an iBook 14" (w/ ATI video card) in about two weeks.


Felix

---

### Post by Janfi on 2005-10-28
For the Airport Extreme, it's under heavy developement. Make a search on the forum. The airport can work with MOL and Gentoo. The broadcom chipset is reverse engineered and work is in progress.
Take a look here :
[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

I have no idea about WHEN, but I'm sure that now it is a question of time.

---

### Post by Rxke on 2005-10-28
Oh another niggle (if you're a gamer it's a big issue) hardware acceleration doesn't work. No problem for most things, but (arcade)games become impossibly slow or just plain un... errr... workable. Again the drivers being unavaiable, sigh.


(Edit) All of which didn't prevent me to make my Clamshell oldie iBook an Ubuntu-only machine, which I use on a daily basis. No regrets. The plethora of good software didn't make it a hard decision.

---

### Post by felix_stegerman on 2005-10-28
Hi,

It's nice to see there's work being done on getting Airport Extreme to work.
I prefer using cables, but I think my university has wireless access covering
the entire building now. So it would be nice to have it in the future.

And the lack of hardware acceleration doesn't bother me. I'm not a gamer
(I only play my self-created Java mastermind occasionally), so I think I'll
be just as happy (or happier ;-) since it looks better and should be more
robust) with an iBook as with my old Toshiba.


Felix

---

### Post by jonatin on 2005-11-04
I've just recently clean-installed breezy on my iBook 500, and I'm wondering if I should have just left well enough alone. I started the iBook with Warty, and had taken it as far as breezy-backports, with no exceptional problems. (Just the ususal "oh, it's x86 only" stuff)

But now I've gone and fresh-installed it on a roomy hard drive all to itself and gotten rid of the last bit of OSX in my house. . . and my audio is (basically) inoperative. I had to kludge /etc/modules with the old install/remove of dmasound-pmac hack in order to get *any* sound at all.

All that got me was the interface noises. I still can't play any MP3s in Rhythmbox or muine. Both complain that they can't access plugins or backend decoders. I'm lost. Never had audio problems before.

I've used the Multimedia System Selector to test OSS and ALSA, both are completely mute, but the ESD test noise worked.

Top it all off, I've got a nasty headcold and can't manage to think my way out of this tangle for all the cold medication. Any thoughts from the PPC crowd? (I think I'm off to bed, this is giving me a headache.)

Cheers...

<edit>
Felix, I'm 'stealing' your sig and posting it on the whiteboard at work... fantastic!
</edit>

---

### Post by savage on 2006-01-14
This is an older post I understand that, but in case someone is looking this over trying to make the same decision, here is my 2 cents. I purchesed a Powerbook and indeed the hardware is super sexy. Mac OSX does nothing for me, and I used it a dozen times. After which I repartitioned OSX down to 10GB so that Ubuntu could have some breathing room. Every once in awhile I pop back in to keep myself edumacated about Apple. However for me the biggest issue was that there are very few Live CD's available, and much less distros. If you want to do cool stuff with [audio]("http://demudi.agnula.org"), [security]("http://www.remote-exploit.org/index.php/Auditor_main"), [science]("https://www.scientificlinux.org"), or simply try out a new distro you will not have the broad range of options that you would get with a x86. There are some excellent live cd's out there, and they are so much more useful with a laptop. If I was going to do it again I'd go x86.

---

### Post by Ptero-4 on 2006-01-14
The iBook 600 Mhz and later models have conexant softmodems.

---

