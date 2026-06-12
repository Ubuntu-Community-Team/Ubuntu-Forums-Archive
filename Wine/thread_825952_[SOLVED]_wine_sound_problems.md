---
title: "[SOLVED] wine sound problems"
date: 2008-06-11
forum: Wine
---

### Post by chuugokujin on 2008-06-11
Nothing has sound when I wine. (0.9 version)

I tried winecfg to test my audio system. No matter what I choose between OSS and ALSA, the sound test is failed.

I updated wine to rc4 and tried again, the options became only OSS. I clicked the test sound and it failed again.

My system sound works fine tho, I can play music and watch movies.

I have a Creative Audigy 2 card, and a Embed sound card. By default it's Audigy 2 that produces sounds.

Could anyone pop up some solutions? Thanks in advance.

---

### Post by cogadh on 2008-06-11
What version of Ubuntu are you using? The current version of Ubuntu (8.04) uses PulseAudio for its sound system, which Wine does not support. You can supposedly get around this issue by installing the PulseAudio ESD compatability package and/or the libao-pulse package, then setting Wine's sound driver to ESound.

If you are using Kubuntu or an older version of Ubuntu, then it still uses ALSA as the sound system, in which case the problem is something completely different. If that is the case, the terminal output from Wine may give some indication as to what is going on.

---

### Post by chuugokujin on 2008-06-11
> **cogadh said:**
> What version of Ubuntu are you using? The current version of Ubuntu (8.04) uses PulseAudio for its sound system, which Wine does not support. You can supposedly get around this issue by installing the PulseAudio ESD compatability package and/or the libao-pulse package, then setting Wine's sound driver to ESound.

If you are using Kubuntu or an older version of Ubuntu, then it still uses ALSA as the sound system, in which case the problem is something completely different. If that is the case, the terminal output from Wine may give some indication as to what is going on.

My bad I did not state clearly that I am using Ubuntu 8.04. I will try to install the PulseAudio ESD compatablility package later. The question is will winecfg->audio show this option after the installation automatically? cuz I only have OSS right now, not even ALSA option. Thanks

---

### Post by cogadh on 2008-06-11
Did you compile your version of Wine yourself or are you using a precompiled package from the WineHQ repositories?

---

### Post by chuugokujin on 2008-06-11
> **cogadh said:**
> Did you compile your version of Wine yourself or are you using a precompiled package from the WineHQ repositories?

Yup, I downloaded the source from WineHQ and compliled it. The version 0.9 I used before was pre-compiled package from WineHQ repository. It had OSS, ALSA and something else which I don't know. lol

---

### Post by cogadh on 2008-06-11
That explains it. When you compiled it, you did not have all the necessary development libraries you need to build all of the sound support options. Given that, no matter what you do, your copy of Wine will never give you any sound option other than OSS. Next time you try to compile yourself, make sure you run this first:
```
sudo apt-get build-dep wine
```
That will get all of the necessary development libraries needed to compile a fully functional version of Wine. Alternatively, Dan Kegel (the guy responsible for the wonderful tool "winetricks") has a script that will make sure you have more than you could possibly need to compile a fully functional version of Wine. The Hardy version fo the script can be found [here](http://www.kegel.com/wine/hardy.sh).

BTW - Is there a particular reason you didn't use the precompiled 1.0-rc4 package from the WineHQ repositories?

---

### Post by chuugokujin on 2008-06-11
> **cogadh said:**
> That explains it. When you compiled it, you did not have all the necessary development libraries you need to build all of the sound support options. Given that, no matter what you do, your copy of Wine will never give you any sound option other than OSS. Next time you try to compile yourself, make sure you run this first:
```
sudo apt-get build-dep wine
```
That will get all of the necessary development libraries needed to compile a fully functional version of Wine. Alternatively, Dan Kegel (the guy responsible for the wonderful tool "winetricks") has a script that will make sure you have more than you could possibly need to compile a fully functional version of Wine. The Hardy version fo the script can be found [here](http://www.kegel.com/wine/hardy.sh).

BTW - Is there a particular reason you didn't use the precompiled 1.0-rc4 package from the WineHQ repositories?


Thanks a lot! I will try later.
LOL the reason I didn't install the precomplied was because I am a noob and I wanted to try compiling something by typing a few commands :)

---

### Post by cogadh on 2008-06-11
Hey, Wine is probably one of the best Linux apps to try out compiling with for the first time. If you screw it up, it won't screw up your system and you can always fall back to one of the precompiled packages (if necessary). Definitely worth messing with like this.

---

### Post by chuugokujin on 2008-06-12
> **cogadh said:**
> Hey, Wine is probably one of the best Linux apps to try out compiling with for the first time. If you screw it up, it won't screw up your system and you can always fall back to one of the precompiled packages (if necessary). Definitely worth messing with like this.

That was excellent my friend. I "make uninstall"'d my complied wine, and build-dep then installed the precomplied wine. Installed libao pakage, choose Esound for winecfg.

Now it works! I really appreciate it!

---

