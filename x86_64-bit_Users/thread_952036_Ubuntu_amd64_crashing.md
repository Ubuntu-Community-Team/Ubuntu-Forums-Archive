---
title: "Ubuntu amd64 crashing"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by JohnLM_the_Ghost on 2008-10-18
I am increasingly concerned about my Ubuntu's stability.
Though I would usually consider Ubuntu very stable (as I had from 6.06) my current Hardy is crashing constantly.

I have really no idea what is wrong, cause I cannot determine any pattern. Nothing is dumped to logs, gives no errors, it just simply  freezes (nothing works, even SysRq-B magic combination doesn't work).

So I am using Ubuntu 8.04 Hardy Heron x86-64 (amd64) on a AMD Phenom 9950 (Quad-Core)

I am slightly suspecting latest updates might not been very healthy as I am updating from all sources (including hardy-proposed)

Any feedback appreciated!

---

### Post by Sef on 2008-10-18
>  I am slightly suspecting latest updates might not been very healthy as I am updating from all sources (including hardy-proposed)Likely could be the problem.

Are you doing or using any program when this happens?

Update: Moved to 64-bit forum.

---

### Post by JohnLM_the_Ghost on 2008-10-19
I got various programs running, but there seems to be no real pattern.
Only thing comes in mind that it is usually multimedia program what runs in foreground (VLC or Aqualung), but I often have lots of other ones opened like Azureus, Anjuta, Firefox, gnome-terminal, samba, noip2, jackd, screenlets. I'm more concerned about system processes what have been updated. Cause I haven't updated any user-apps for a while (at least I can't recall of any).

It didn't freeze (often) when I installed it, and some while afterwards. But lately it freezes often after an hour or so. And It is clearly not a hardware issue, cause XP partition runs like charm!

EDIT: Hmm I also suspect Azureus now... I'm running Ubuntu now for few hours without a glitch (and without Azureus running). Not really sure yet, needs a bit more testing, but might be possible. (might be a good reson to migrate to rtorrent)

---

### Post by Tommy100 on 2008-10-19
Hi. May i tag along? My 8.04 ubuntu is also crashing since yesterday, and i don`t know if it is the wine installation i did or trying to get the printer going, when i boot it in diagnostic mode i get lots of messages of various update sites that are not loading. And one of them is wine.

How can i save all the updates ubuntu made after i did my first installation? Where are they kept? Because i feel like starting from scratch again, but don`t feel like downloading all the updates that popped up after the installation. :(

---

### Post by JohnLM_the_Ghost on 2008-10-19
For me Azureus is probably not the problem. I didn't run Azureus and everything went fine until it hanged up in middle of my OpenTTD game. Rather irritating!
Same symptoms - absolute freezing (no input works, not even SysRq+B)
Any bright ideas?
I might also do a stress test for XP overnight, to see how it handles. If it does OK, must be a software problem.
I could also try revert all system packages to *hardy* or *hardy-updates* ones if somebody tells a good and quick way how to do that.

> **Tommy100 said:**
> Hi. May i tag along? My 8.04 ubuntu is also crashing since yesterday, and i don`t know if it is the wine installation i did or trying to get the printer going, when i boot it in diagnostic mode i get lots of messages of various update sites that are not loading. And one of them is wine.

How can i save all the updates ubuntu made after i did my first installation? Where are they kept? Because i feel like starting from scratch again, but don`t feel like downloading all the updates that popped up after the installation. :(

Hey Tommy! So what are your symptoms? (i.e. How it crashes?)
About the Update sites... As I can recall networking is not working in Recovery mode, so trying to update returns heaps of errors. You should try that in normal mode!

If you think to reinstall over again, I can tell you that APT package cache is located in **/var/cache/apt** if I recall right. But in any case the cache is partial, and you would have to download the most of the packages anyway. 
You may also save package list from Synaptic, but that might include package that is failing (in case there is any).
User settings mostly reside in **~/.*** (point folders in home directory).

btw What kind of printer do you have?

---

### Post by Tommy100 on 2008-10-20
My printer is a Canon Pixma iP1000 :(. i have changed my bios settings, advanced chipset, Switched off AGP fast write and ASPSS ADDR. And set the HT freq down to 1x. LOL! Now the ubuntu works fine.

The crashes were during boot up after the user name and password, or during shut down, or when opening to many web sites at the same time! :D

---

### Post by JohnLM_the_Ghost on 2008-10-20
> **Tommy100 said:**
> My printer is a Canon Pixma iP1000 :(. i have changed my bios settings, advanced chipset, Switched off AGP fast write and ASPSS ADDR. And set the HT freq down to 1x. LOL! Now the ubuntu works fine.

The crashes were during boot up after the user name and password, or during shut down, or when opening to many web sites at the same time! :D

Pixma, ouch! I think you might have hard time setting that thing up! Of course it is not impossible. Refer to a some printer thread for more info :)

All right. Startup crashes are often associated with Video Driver (video driver is invoked right after login), even more if switching AGP settings improves things. What Video Card and driver do you use? 
Of course it wouldn't explain crashing on many web sites :\
Using Flash Player in Linux might also be painful, try not to open many sites with flash objects (flash ads also counts).

And how does your system crash? (i.e. Kernel Panic, Freeze, Sudden Restart)
If it hangs up try **Ctrl+Alt+Backspace** or **SysRq+B** (invoked Alt+PrintScreen+B)

lol, I'm just throwing any idea comes in mind! :D

---

### Post by Tommy100 on 2008-10-22
Thanks John. AGP card is Nivida GE Force 6600GT 128Meg RAM.
If i run with the disabled functions then ubuntu does not crash, except when i put my Sansa player in the USB! LOL! Then the crash is a screen feeze, and i have to reset the PC.

---

### Post by MasterNetra on 2008-10-22
It seems to be the new kernel. Same thing happens with me and it all started shortly after the new kernel upgrade. Ubuntu seem to behave more after some updates so i had thought it to be fixed...of course this morning the kernel paniced while the OS was in the early stages of loading so idk. It was suggested that i use the previous kernel however the new drivers that my wireless card is using doesn't work with the prior kernel so i'm a bit stuck with this kernel :/ (And i'm stuck using only a wireless connection :( )

---

### Post by Tommy100 on 2008-10-22
Just loaded Kubuntu 8.04 :D LOL! Really had turn down the AGP card, but i am so impressed with the interface! :) NICE! Well done to the developers!

---

### Post by JohnLM_the_Ghost on 2008-10-29
I would say that video problem and USB bug is seperate, but who knows.
To give a thought what **MasterNetra** suggest, new kernel might be a cause too.
Have to test it some more!

---

### Post by Doug77 on 2008-10-31
I've also had problems with stability recently.  Running a Dell Inspirion 1525 laptop with Ubuntu 64-bit Hardy, fully updated, dual booted with Vista.  When I open some applications, it will completely freeze up and ctrl-alt-backspace won't even work - those applications are: neverball, neverputt.  Some applications don't close and I have to kill them (dosbox).  Amarok also seems to be causing some problems - sometimes it will freeze up and I can't even kill it, sometimes it will cause the system to go all wonky, like alt-tab won't work and I can't switch applications, can't shutdown.  This usually happens when I'm running a lot of other things (OpenOffice, Azureus, Firefox, Opera, Emesene).  Amarok was crashing badly for a while, very often - my music library is huge though, so maybe that's why.  On top of that, Pidgin and other messengers can't connect to MSN about 90% of the time (except Emesene in HTTP mode) - although I think that's an MSN problem.  Also, I installed Wine and then tried to get Warcraft 3 running, but I couldn't, and the system  started screwing up when I tried to run it - the screen contrast seemed to go to maximum and I couldn't get it back down and had to reset.  

I'm hoping an update to Intrepid will make things more stable - I hate being hesitant to stress out the system too much.  

I read a lot about Ubuntu's stability, and not having to reset very often, but I'm not seeing it just yet - I do like to tweak, but I don't think I did that much to mess things up!

---

### Post by lH)4~mK0e on 2008-10-31
I have had lots of problems with audio and SDL based apps (quake2 nwn and I imagine this could be the case with other apps like never<games>).  I had to change all settings in System --> Preferences --> Sound to ALSA, I also ran this command:

```

asoundconf unset-pulseaudio

```

And remove all ~/.asound* /etc/asound*...

and run:

```

export SDL_AUDIODRIVER=alsa

```

Strangely enough, I have this setting still configured:

```

echo "default_driver=pulse" > ~/.libao

```

But any apps that used SDL (and even some that didn't) would not work correctly and would even in some cases lock up my video to the point that Ctrl + Alt + Backspace was my only solution.  This setup works nicely with my nforce3 audio card (rtl based) but I don't expect it to work with HDA based cards.

---

### Post by JohnLM_the_Ghost on 2008-10-31
Thanks **Doug77**!
You helped to have little insight into this problem.
So obviously it hangs up only on considerable workload, it doesn't seem to be any application in particular. So I could suspect the kernel... maybe buggish multi-processing (multi-threading)? Or something about 64bits... never had problem with x84, but then again I never had multi-core processor with Ubuntu x84.

Anyone else have any bright ideas?

---

### Post by JohnLM_the_Ghost on 2008-11-15
So I've installed Interpid! I haven't tested thoroughly, but it does seem to be stable. It hasn't crashed since I installed it three days ago.

Not a bright solution but works OK!
Problem solved for me! I'm going to mark this solved, unless you guys want to continue the thread with your problems.

---

### Post by purifiedmadness on 2008-11-15
hello i am also having problems with amd64 crashing sometimes it will run fine for days and sometimes only hours but it will lockup and all i can do is use the reset button i cant use ctrl+alt+backspace or sysrq.

running 8.04.01 i think an update broke it was working till about 3 weeks ago the only apss running are firefox and/or vlc

---

### Post by JohnLM_the_Ghost on 2008-11-15
> **purifiedmadness said:**
> hello i am also having problems with amd64 crashing sometimes it will run fine for days and sometimes only hours but it will lockup and all i can do is use the reset button i cant use ctrl+alt+backspace or sysrq.

running 8.04.01 i think an update broke it was working till about 3 weeks ago the only apss running are firefox and/or vlc

Sounds pretty much what I had. I tried different tests and tricks, but failed to locate the bug. I think it had something to do with the kernel, but I had no luck when installing older kernel. Also VLC surfaced few times, so it maybe something to do with that.
Anyway I can't give you any good solution to repair the current system, but I think you should consider installing Interpid (8.10).
And if you do decide to install, do fresh install if possible.

---

### Post by purifiedmadness on 2008-11-15
was planing on a fresh install of 8.10 since im putting in a new hd anyway but i really wanted bluetooth and it sounds like people are having a lot of problems with that. oh well i will prolly give it a shot anyway.

---

### Post by JohnLM_the_Ghost on 2008-11-16
Sadly, I have no experience with bluetooth on Ubuntu. So I know nothing about it.
And as you're having new hdd, you could also install it alongside hardy and see which one does better! But I guess you probably had this idea already. :)

---

### Post by AllenGG on 2008-11-16
Somehow I was able to stop the crashes on my AMD64, 5 years old, after I bought a new system.
Yup, did all the updates, installed a new power supply and 2 fans, heat was a huge problem.
Was it the updates ? Better cooling ? So now  I'm selling a perfectly good system. (have 3)

---

