---
title: "32bit or 64bit for Wine?"
date: 2008-11-10
forum: Wine
---

### Post by chazdraves on 2008-11-10
Greetings, all!

I'm just wondering if there is any general performance improvement for using 64-bit or 32-bit Ubuntu? I've noticed problems with DoW: Dark Crusade, for example, in 64-bit that a 32-bit user has never experienced. Coincidence? Hardware issue? Obviously these games were mostly intended for 32-bit Windows, but does that have any affect on Ubuntu?

One of my primary PC uses is gaming, and I want to be sure that I have comparable performance in Ubuntu to XP and right now it's not even close (DoW: DC is silky under XP, but bogs down quickly in 8.10 64-bit, Wine 1.0.1). Obviously, it doesn't make sense to upgrade competent hardware just because the OS is lacking.

Thanks in advance!
- Chaz

---

### Post by asdfoo on 2008-11-10
> **chazdraves said:**
> Greetings, all!

I'm just wondering if there is any general performance improvement for using 64-bit or 32-bit Ubuntu? I've noticed problems with DoW: Dark Crusade, for example, in 64-bit that a 32-bit user has never experienced. Coincidence? Hardware issue? Obviously these games were mostly intended for 32-bit Windows, but does that have any affect on Ubuntu?

One of my primary PC uses is gaming, and I want to be sure that I have comparable performance in Ubuntu to XP and right now it's not even close (DoW: DC is silky under XP, but bogs down quickly in 8.10 64-bit, Wine 1.0.1). Obviously, it doesn't make sense to upgrade competent hardware just because the OS is lacking.

Thanks in advance!
- Chaz

64bit vs 32bit is a non-issue.  Wine is 32bit only and runs as such on 64bit distros.

The reason for your game not being smooth could be due to a bug in Wine.

Do you have the latest video drivers? nvidia or ati?  ati is known to have more issues the nvidia.  have you tried using the latest Wine beta? [http://winehq.org/download](http://winehq.org/download)

---

### Post by chazdraves on 2008-11-10
Yeah, the beta actually was far worse (1.1.8). I reverted back to 1.0.1. The problems seem to be mostly with audio glitching and visual slowdown in even medium-sized battles. All of which runs flawlessly under XP, so I know it's not the hardware...

I have actually just re-installed Ubuntu with the 32-bit version and am so far finding it faster and also finding that DoW runs leaps and bounds better than it did in 64-bit. I'm not saying one is faster than the other in general, I'm merely saying it seems to be working a lot better in my case. Even with the largest army I could muster, I didn't have any real problems. It would certainly drop from a solid 60fps, but it wasn't near as bad as it had been under 64-bit with an army half that size.

I don't know what the explanation is, and I'm not pointing fingers, but that is the data I've collected. Maybe someone can come up with a proper explanation?

Rig:

Core2 E4400 @ 3.1GHz
9600GT (stock)
2GB DDR2 800
Raptor 10,000RPM HDD
Ubuntu 8.10 32-bit

Thanks!
- Chaz

---

### Post by YokoZar on 2008-11-10
The most likely explanation is differences in software other than Wine.  Perhaps the 64 bit drivers for something on your system are slow and buggy compared with the 32 bit ones.

---

### Post by tvtech on 2008-11-10
I've run 32 bit and 64 bit on my asus laptop with wine and various games and a cadd program called visualcadd 64 bit uses my hardware much more effectively, but that's just me.

---

### Post by chazdraves on 2008-11-10
Either way, it's curious.

Well, I appreciate the insights. I can't say anything against any other programs in 64-bit, but DoW ran like trash. It's too bad that gaming in Linux has never really taken off. Don't get me wrong, there's a lot of excellent open-source games out there (Wesnoth comes to mind), but there's nothing as polished as what's available for Windows. I think it's unfortunate, but it must be what the masses demand, or there'd be better support.

That said, I just can't figure it. It seems like there's so much activity with Wine and the like that one would figure Linux to have a very active gamer base, but that must not be the case. For as polished and professional as programs like Thunderbird, Firefox, and OpenOffice are (heck even Ubuntu for that matter), I just don't see why similar attention isn't paid to games. I realize 3D engines are a bear to create, but what about a 2D RTS ala Starcraft?

I'm rambling, and I'll catch myself now, but I'd be curious for input from you all.

Thanks again!
- Chaz

---

### Post by asdfoo on 2008-11-11
> **chazdraves said:**
> Either way, it's curious.

Well, I appreciate the insights. I can't say anything against any other programs in 64-bit, but DoW ran like trash. It's too bad that gaming in Linux has never really taken off. Don't get me wrong, there's a lot of excellent open-source games out there (Wesnoth comes to mind), but there's nothing as polished as what's available for Windows. I think it's unfortunate, but it must be what the masses demand, or there'd be better support.

That said, I just can't figure it. It seems like there's so much activity with Wine and the like that one would figure Linux to have a very active gamer base, but that must not be the case. For as polished and professional as programs like Thunderbird, Firefox, and OpenOffice are (heck even Ubuntu for that matter), I just don't see why similar attention isn't paid to games. I realize 3D engines are a bear to create, but what about a 2D RTS ala Starcraft?

I'm rambling, and I'll catch myself now, but I'd be curious for input from you all.

Thanks again!
- Chaz

Generally speaking,

big businesses within the game development industry goes where the most money is, which often happens to use technologies that aren't readily available on Linux.  DirectX 9, 10, soon 11, PhysX? I think the windows nvidia drivers come with physx capabilities but the linux ones don't.

It's usually the smaller studios and independent game developers that consider writing their games with OpenGL instead of DirectX and using Mono instead of .NET to produce games that will work with little effort on Mac, Linux and Windows.

Also, generally speaking -- recently there was supposed to be a huge revision to OpenGL which had been long delayed to bring OpenGL closer to something more desirable and approaching DirectX, but that flopped which was something of a another nail in the coffin for targeting new games on Linux and Mac.

---

