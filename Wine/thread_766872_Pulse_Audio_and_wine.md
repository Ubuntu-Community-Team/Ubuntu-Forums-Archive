---
title: "Pulse Audio and wine"
date: 2008-04-25
forum: Wine
---

### Post by Fred_E _krugar on 2008-04-25
Well I just recompiled 0.9.49 for Hardy. I still cannot get sound to work like it did for Gutsy.

I was able to listen to music while I played and talked through CSS, on Gutsy and 0.9.49 wine.

I want to be able to this again, the only difference between Gutsy and Hardy that I can tell is Pulse Audio. Could that be the problem?? Is there a way to remove Pulse Audio without degradation to all the gnome sound?? 

Plz help me figure this out.

---

### Post by cogadh on 2008-04-25
I had the same problem with PulseAudio on Gutsy, but I never really found a way around it. I ended up switching to Kubuntu just because they are staying with Alsa, which works fine with Wine (and everything else). In theory, you should be able to just install Alsa from the repos, then choose it as the default sound server for Gnome instead of PulseAudio. I wouldn't remove PulseAudio until you are sure Alsa will work.

---

### Post by Fred_E _krugar on 2008-04-25
ok after further investigating I have unchecked the Alsa drivers and check Esound Drivers which Pulse Audio is a drop in replacement for Esound.

I am now able to play Amarok and get the test sound from winecfg at the same time. I will be trying more things to see if this is really working.

---

### Post by Swarms on 2008-04-25
I installed Hardy when it was launched as beta, where Wine sound worked fine. Then after the launch, I did the distribution upgrade, and the sound from Wine disappeared. I solved it by installing the final version. The only issue left I got, is that the Wine Gecko engine is acting weird, which it also did before the install of Hardy Final.

---

### Post by mriedel on 2008-04-25
Under Hardy you can just set Wine's audio driver to OSS and start wine in a pulse audio wrapper ("padsp wine MyApp.exe").

---

### Post by Gigopepo on 2008-04-25
Is wine working fine in Hardy?
I'll probably change this week, maybe my no-sound-steam problems will vanish...

---

### Post by k99goran on 2008-04-25
Strangely, I had the complete opposite experience. I was never able to play music and Diablo II at the same time in Gutsy Gibbon. Now it worked without a problem.

---

### Post by Fred_E _krugar on 2008-04-26
It is now confirmed from my experiments that for me I have to uncheck the Alsa drives and check EsounD drivers (in winecfg) hope this helps other people.

---

### Post by Swarms on 2008-04-26
> **Fred_E _krugar said:**
> It is now confirmed from my experiments that for me I have to uncheck the Alsa drives and check EsounD drivers (in winecfg) hope this helps other people.

I got the issue again, so I want to try your solution, where do I find the EsounD driver? I can only pick between ALSA, OSS and Jack. I have 0.60.

---

### Post by mriedel on 2008-04-26
> **Swarms said:**
> I got the issue again, so I want to try your solution, where do I find the EsounD driver? I can only pick between ALSA, OSS and Jack. I have 0.60.

> **mriedel said:**
> Under Hardy you can just set Wine's audio driver to OSS and start wine in a pulse audio wrapper ("padsp wine MyApp.exe").

That should work for you.

---

### Post by Fred_E _krugar on 2008-04-26
> **Swarms said:**
> I got the issue again, so I want to try your solution, where do I find the EsounD driver? I can only pick between ALSA, OSS and Jack. I have 0.60.

are you using Hardy??

---

### Post by Fred_E _krugar on 2008-04-26
Ok here is an update. I can listen and talk on Ventrilo, Listen to music on Rythmbox and Amarok, get all sound in CSS no lag and can even talk through CS voice chat.

What I did was stop pulseaudio server in system menu, started winecfg rechecked Alsa, now things are working good. I am Finally happy. :)

---

### Post by Swarms on 2008-04-27
I am using Hardy.

---

### Post by andrebrait on 2008-04-27
strange...

pulseaudio is supposed to make things better...

anyway, where can I get the esound Driver for wine?

And isn't there a pulse driver too?

---

### Post by mriedel on 2008-04-27
padsp wine yourApp.exe (wine configured to use OSS) works, as I said.

With ALSA->PulseAudio->ALSA configuration enabled, it should theoretically work through ALSA without the padsp wrapper. I doesn't for me though. Don't ask me why they pushed Pulse as the default sound server in Hardy but didn't even set up basic features like the virtual PA device for ALSA.

---

### Post by Fred_E _krugar on 2008-04-27
Well on my system, when the PulseAudio server is running wine will show it in Audio tab (winecfg) (EsounD).


Now if I shut down wine, and shut down PulseAudio server (System monitor), then restart wine, In winecfg it will not show the EsounD option. There is no installing of drivers of any kind during this whole thread.

So if your winecfg does not show the EsounD option, you obviously do not have pulseAudio running.   If your PulseAudio is not running.........................................................THIS IS  A GOOD THING ...............................

You are having problems elsewhere.

---

### Post by andrebrait on 2008-04-27
hmm...

x86-64 Hardy here...

maybe it's the "problem" that makes wine not recognize ESD plugin.

---

### Post by mriedel on 2008-04-28
I'm on hardy64, my PA is definitely running and wine doesn't have esd support (nor did it ever), so probably yes.

---

### Post by janfsd on 2008-04-28
Maybe this can help:
[http://blog.paulbetts.org/index.php/2007/05/27/make-wine-and-pulseaudio-get-along/](http://blog.paulbetts.org/index.php/2007/05/27/make-wine-and-pulseaudio-get-along/)

---

### Post by mriedel on 2008-04-28
That method has already been discussed in this thread

---

### Post by Swarms on 2008-04-28
> **mriedel said:**
> That method has already been discussed in this thread

Still more interested in the other solution.

---

### Post by prepstyles on 2008-04-30
Hey thought I'd chime in.

I used the "padsp" command method described on this thread (a few times) and I can now have sound in Banshee and World of Warcraft at the same time.  I didn't think it worked initially however, it seems Banshee overpowered the sound in Wine and I couldn't pick it out ... I'm not sure why that is as the volume in WOW was maxed and Banshee's was not.  Anyway if anyone thought using "padsp" didn't work try again and turn your non wine apps down.

Cheers!

Also I noticed wine (0.9.60) on my machine has an option for "JACK Driver" under sound drivers, anyone know anything about it?

---

### Post by dmn_clown on 2008-05-01
> **prepstyles said:**
> Also I noticed wine (0.9.60) on my machine has an option for "JACK Driver" under sound drivers, anyone know anything about it?

[http://jackaudio.org/](http://jackaudio.org/)

It's a good enough sound system that it can be made to blow your speakers.

---

### Post by peacewithall on 2008-05-03
> **mriedel said:**
> Under Hardy you can just set Wine's audio driver to OSS and start wine in a pulse audio wrapper ("padsp wine MyApp.exe").


This worked in games with wine for me, thanks :)

---

### Post by Bastaard on 2008-05-03
Seems to me pulseaudio should've never been set default for Hardy as it creates all kinds of trouble.

---

### Post by Patriot1776 on 2008-05-03
Delete Post Please, somebody.  Problem solved.

---

### Post by empty89 on 2008-05-04
Actually the easier way to ensure sound is working is to go to System>Preference>sound option. Select alsa for all playback. Do not put it as autodetect.

enable oss in winecfg too.

---

### Post by Fred_E _krugar on 2008-05-04
> **empty89 said:**
> Actually the easier way to ensure sound is working is to go to System>Preference>sound option. Select alsa for all playback. Do not put it as autodetect.

enable oss in winecfg too.


Even if you do this the PulseAudio server still runs.  You need to shut it down.

---

### Post by empty89 on 2008-05-04
My laptop work fine with the setting even if pulse audio server is on.. just eating up the system resource..

---

### Post by Patriot1776 on 2008-05-04
> **Fred_E _krugar said:**
> Even if you do this the PulseAudio server still runs.  You need to shut it down.

Sorry if it sounds noobish, but how?

"stop" and then what, or possibly kill?

I don't think pulseaudio though could be causing my choppy video problems I'm now having while playing Steam games.

---

### Post by Swarms on 2008-05-04
> **Patriot1776 said:**
> Sorry if it sounds noobish, but how?

"stop" and then what, or possibly kill?

I don't think pulseaudio though could be causing my choppy video problems I'm now having while playing Steam games.

Head into > Preferences > Sessions, and delete the item named "PulseAudio Session Management". Then it wont start when you boot. But be sure to save the command somewhere else, if you want to restore it.

---

### Post by Patriot1776 on 2008-05-04
Unchecking it doesn't work you have to completely remove it?

---

### Post by dalen__ on 2009-12-05
For those of you that is running Ubuntu Karmic 9.10 there is now a possibility to install a version of wine with pulseaudio support. This solved the sound issues with wine for me. 

I've created a guide on how to install winepulse in Ubuntu 9.10, hope it can help you. 

[http://dalenscomputerblog.blogspot.com/2009/11/how-to-install-winepulse-for-ubuntu.html]("http://dalenscomputerblog.blogspot.com/2009/11/how-to-install-winepulse-for-ubuntu.html")

---

### Post by radu.c on 2010-03-03
I ran Wine 1.2 from PPA with PulseAudio. Sound was great, but the window manager didn't seem play ball with Spotify, so I downgraded back to stock Wine from Karmic (9.10) and did this:

In winecfg, I deselected ALSA and selected ESounD instead. I did this after I read that PulseAudio can actually emulate ESounD.

And it works perfectly! Unless the ESounD compatibility is dropped from PulseAudio [-X, this is my solution to the problem.

---

### Post by MerlinW on 2010-08-21
I made a script for build **wine-git** with **pulseaudio** and **directx 9**. I'm using it, so it's working well. Enjoy:)

The latest version has:
* wine 1.3.17 (2011.04.10)
* winepulse 0.3.11 (2011.01.21)
* winetricks (2011.04.02)
* git (1.7.3.5)

* PPA installer - not always up-to-date, but faster. The PPA version doesn't include DirectX.

More details:
[Wine+Pulse+DX9 Installer v1.3.17-311.31]("http://merlinw.org/index.php?cid=312")

Script download:
[winepulse_installer.sh]("http://merlinw.org/downloads/download.php?id=2") (1.3.17)

Uninstaller download:
[winepulse_uninstaller.sh]("http://merlinw.org/downloads/download.php?id=3")

PPA installer download:
[winepulse_installer_ppa.sh]("http://merlinw.org/downloads/download.php?id=8") (1.3.17)

---

### Post by Milos_SD on 2011-01-12
This web site where I used to download wine-pulse patches is not working: [http://art.ified.ca/?page_id=40](http://art.ified.ca/?page_id=40)

@MerlinW: Will your web site have updated versions of patches?

---

### Post by MerlinW on 2011-01-26
> **Milos_SD said:**
> This web site where I used to download wine-pulse patches is not working: [http://art.ified.ca/?page_id=40](http://art.ified.ca/?page_id=40)

@MerlinW: Will your web site have updated versions of patches?

Yes, I updated now. 

Edit: Tested, working well. See my actual script above.

---

