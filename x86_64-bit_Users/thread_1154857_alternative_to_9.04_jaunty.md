---
title: "alternative to 9.04 jaunty"
date: 2009-05-10
forum: x86 64-bit Users
---

### Post by milanlin on 2009-05-10
Hardware: gigabyte mobo 939, athlon 4200+, 4 GB DDR 400 Corsair Memory (3.6 physical), ATI HD4850 1024 MB DDR3, Creative SB Audigy 4

Prologue: Being linux probably means that you will spent with it more time than anything else. Learning, tweaking, configuring and again and again, because the development is going very fast. Even with ubuntu - linux for human beings. I see that average ms-user will give it up very fast and many of them are scared to try linux. But this forum is good place to get advise, so I am here again to learn and have a little bit fun. 
 
My experience with 9.04 64-bit after cca 1 month: 
The system is not cooked well, it is freezing, it is slow. I did not have so many dead screens on 8.10 32-bit (felicia) within half a year like with 64bit 9.04 within only 1 month. Has the logout function CTR-AlT-Backspace been removed? why?
Well, I know that gnome is relatively "heavy" but the question is:
Is my hardware configuration realy so poor that it can not run smoothly the most favourite distro? 
And here we are: ATI - very bad choice - video playback is real catastrophy  and it seem to me that ati driver is the main problem for overall sluggish performance. 
Audigy - absolutely and totally bad choice for linux. I did not find distro to play sound out of the box. Only fedora 11.1 was playing some very low quality sound barely listenable. I tested latest mandriva, suse, fedora, pclinuxos. Felicia played audio but not video on audigy device.

I would like to stay with gnome but 9.04 64bit is going out of my machine. So what do you recommend now? 

1. Test lxde on 9.04 64bit.
2. Test lubuntu.
3. Go back to 32bit - probably Gloria. 
4. Go to the father and PLAY & SPENT MORE TIME WITH DEBIAN.
5. Other but other than xfce = too much conservative outlook
6. Your hardware configuration did not match requirements for gnome

THANK YOU ALL for your answers, time and interest

---

### Post by agnes on 2009-05-10
I'd try Intrepid x86_64 first.
I have an ATI card too (Radeon HD 3650) but it works (with Intrepid).

---

### Post by Arup on 2009-05-10
My dual GPU ATI 4850 works well with Jaunty x64.

---

### Post by Yellow Pasque on 2009-05-10
That hardware should run GNOME with ease. IMO, the 2D performance and stability of the Catalyst/fglrx driver leaves a lot to be desired, and is probably responsible for a lot of your issues.

---

### Post by jespdj on 2009-05-11
There are lots of people who seem to experience [freezes with Jaunty](http://ubuntuforums.org/showthread.php?t=1135055), it looks like it's not a problem specific to the 64-bit version so going back to 32-bit is probably not going to help.

It's not clear what the cause of those freezes is... :(

---

### Post by starcannon on 2009-05-11
If your new, or if the concern is something easier for someone new to Ubuntu from the Windows world, I would recommend 8.04 Hardy Heron 32 bit, at least to get their feet wet. 

It's an LTS (Long Term Support Release), 32 bit is very easy to install, post install, and use; and the performance difference between 32 and 64 bit is negligible; granted you can't use more than 3gb of ram, but were getting our feet wet right? Once someone has learned the necessary knowledge and if one requires that last little drop of performance, then move on to 64 bit. The only downside to 64bit as far as my own experiences have been, is the plugins and codecs I use regularly are either 32bit or in alpha/beta stages of developement for 64bit. Other than that, "it just works" is pretty much there.

GL how ever you decide to go.

---

### Post by Jimmyfj on 2009-05-11
I've been running Jaunty since the Alpha 2 release on both my 64 bit maschines: 1 Intel core-Duo with 2 Gigs RAM and 1 AMD Athlon XP64 with 1,5 Gigs RAM. Both systems are, to day at least, configured with a nVidia graphics card each. My AMD maschine used to have a Radeon 9500 Pro card but I dumped it for a new nVidia card due to too many flaws in the ATI driver. Since the switch to the nVidia card in my AMD nothing has gone wrong there either. My Intel based maschine just runs what ever I throw at it.

I've seen a lot of users having issues with Jaunty but nothing that can't be overcome. Being new to GNU/Linux I'd strongly advise you against trying to go Debian. Debian is NOT for beginners at all. Sure - Many people do start with Debian, no doubt, but with your maschines setup I'd stay very far away from Debian being a newbie in Linux - If 8.10 worked for you then go back to 8.10 either 32 or 64 bit. Unless you really need those extra features in 64 bit edition you should install the 32 bit edition.

---

### Post by milanlin on 2009-05-11
> **Jimmyfj said:**
> I've been running Jaunty since the Alpha 2 release on both my 64 bit maschines: 1 Intel core-Duo with 2 Gigs RAM and 1 AMD Athlon XP64 with 1,5 Gigs RAM. Both systems are, to day at least, configured with a nVidia graphics card each. My AMD maschine used to have a Radeon 9500 Pro card but I dumped it for a new nVidia card due to too many flaws in the ATI driver. Since the switch to the nVidia card in my AMD nothing has gone wrong there either. My Intel based maschine just runs what ever I throw at it.

I've seen a lot of users having issues with Jaunty but nothing that can't be overcome. Being new to GNU/Linux I'd strongly advise you against trying to go Debian. Debian is NOT for beginners at all. Sure - Many people do start with Debian, no doubt, but with your maschines setup I'd stay very far away from Debian being a newbie in Linux - If 8.10 worked for you then go back to 8.10 either 32 or 64 bit. Unless you really need those extra features in 64 bit edition you should install the 32 bit edition.

Well, lenny is my next challenge. 
Right now I am back from sabbayon gnome 4.1 and a live session is quite fast with compiz off, codecs and drivers are in, videoplayback good but it has got gnome 2.4.2 and it is not my choice. 
Ubuntu 9.04 is for people with nvidia and friendly hardware nice system. But still lots of debian users see debian's supremacy.
 
I have actually onboard nvidia 6100, and I can tell that I was really disappointed when I had put money into fast ati and then I have seen the difference between ATI drivers and nvidia. 
There was a video flickering in 8.10, but I have used tweaked VLC so I could be with it. Now the new ati driver has got some improvements but it it is far from beeing usable with compiz on, at least for me now. Flickering is gone but the system is slow. And what for is fast graphics??? Only for games in MS???
I agree that I could run 32bit, because there is not so many appps which I will use to utilize advantage of 64bit. But again 64bit is here so we should keep going forward. 
The sound from audigy I will need to configure manually in every gnome distro, because there is lots of sound devices, so why not in debian?
HDA NVidia ALC880 Digital(ALSA)
Audigy 4 [SB0610](rev.0,serial:0x10211102) Multichannel Playback (ALSA)
HDA ATI HDMI ATI HDMI (ALSA)
+ some usb ...
I can learn with forums people as well. 
What everybody want is fast gui system with lots of developers and community involved in it. And you know the feeling when you fix something or configure to work or find out how :))

---

### Post by milanlin on 2009-05-12
Performance problems resolved.
1. New proprietary ATI driver is responsible for a terrible computing. Ubuntu is pushing on a market and has got deadlines for their new releases. Then the new updates are welcomed for promotion as well. But to put label on a new ATI driver as tested by ubuntu team is a big joke to ubuntu users. FGLRX is still big crap!!! It is understandable why Arch people dropped proprietary ATI driver!
2. I have installed and configured Debian Lenny 5.0.1. stable. This is my first Debian. I have to tell that going from Jaunty to Lenny is like going from MS Milenium to MS 98. You have the feeling of stability with Lenny  out of the box but on the other hand you are loosing the shine of updated software. But still you can visit 3rd party repositories and upgrade software you like to be up to date, if independancies are possible to resolve.  Later I will go for sid. 
3. So what I have is 64bit Lenny with an older fglrx and an older version of sound preferences in gnome 2.22.3. It is the same behavior like in Felicia. Audigy is playing audio but video sound is going through onboard sound card and video is flickering, so I use vlc only. But there is significant system performance difference.
4. So if you want gnome and you have ATI problems go for Debian. And do not listen to people creating myths about how easy is Ubuntu and that debian is not for "newbies". 
5. Thanks all voters in my minipool, where the result is: DEBIAN RECOMMENDED

---

### Post by Artemis3 on 2009-05-12
> **milanlin said:**
> Hardware: gigabyte mobo 939, athlon 4200+, 4 GB DDR 400 Corsair Memory (3.6 physical), ATI HD4850 1024 MB DDR3, Creative SB Audigy 4

The system is not cooked well, it is freezing, it is slow. I did not have so many dead screens on 8.10 32-bit (felicia) within half a year like with 64bit 9.04 within only 1 month. Has the logout function CTR-AlT-Backspace been removed? why?

Here is my recommendation, please try to understand hardware manufacturers are heavy at fault here:

Don't use the Audigy, i'm sure your motherboard has onboard audio, use that and hope for the day the Audigy is supported in Alsa.

Don't use the ATI. Yes, if you get a super cheap under 100$ Nvidia 9800GT you will see wonders.

Gnome itself doesn't demand much, just like 512mb of ram to be steady.
I see you mentioned Felicia, maybe you will want to wait for linuxmint to release Gloria 64bits?

As for using Debian, well you could also achieve a similar result using Ubuntu 8.04 LTS, but if you are happy with Lenny then congrats :)

---

### Post by Arup on 2009-05-13
In your case, Hardy Heron is the closest and most likely superior equivalent to Debian.

---

