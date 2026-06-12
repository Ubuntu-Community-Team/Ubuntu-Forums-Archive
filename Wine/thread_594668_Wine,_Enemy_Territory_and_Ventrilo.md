---
title: "Wine, Enemy Territory and Ventrilo"
date: 2007-10-28
forum: Wine
---

### Post by Dipski on 2007-10-28
I have an unusual problem. I've just setup and got Wolfenstein - Enemy Territory running in Ubuntu, and Ventrilo running with Wine. Both work very well, until I try to run them together. When Ventrilo is running and I load up Enemy Territory I have no sound for ET. I tried something shown to me by a friend using 'aoss et.exe' to load up the game, which does make a difference - I get broken up distorted blocks of sound and the game stalls a bit, effectively worse than having no sound.

Has anyone come across this problem before (I suspect it wouldn't be limited to Enemy Territory), and does anyone have any ideas or suggestions?

Edit: Interestingly I've just discovered that ET will start with sound if I join a Vent server, so long as no data has been recieved (noone has spoken). As soon as I have heard someone speak on Vent, I cant load up ET with sound.

Update - I've since implemented the et-sdl workaround and I am now stuck on the following error :

SDL audio driver initializing...
SDL audio driver is "(UNKNOWN)"
./et_sdl_sound.sh: line 6:  5985 Segmentation fault      (core dumped) ./et.x86 $*

Which has me completely baffled and I can't seem to find anyone having the same problem. This happens with no other audio programs (ie. Ventrilo) running as well.

---

### Post by Dipski on 2007-10-29
All fixed and done, I thought I'd post for anyone else insane enough to try this.

This has been my first experience in Linux, one of the main reasons for the install was to run ET more smoothly than I was getting in Windows. For anyone else with the same idea - this is not a point click and install job. It is going to take some serious time.

Installing ET - not too hard. Needed to learn about permissions and some mucking around to update to the latest ET version, and similarly for Etpro. Was a bit surprised at the difficulty given that ET is native to Linux!

Punkbuster. Ridiculous. Tried updating punkbuster every conceivable way, automatically, manually, over and over. Guess what... there's a hidden directory where a duplicate punkbuster copy is stored in Linux, and it's the hidden version you have to update. Genius!

Sound in ET. I'm not going there as it had to change all over again to work with Ventrilo.

Ventrilo. Easy to install, install the latest version of Wine and away you go. Getting the sound to work, not so easy. You need to get windows .dll's for Ventrilo to work and change registry settings. Playing around with the input/output settings worked ok for me, and to get voice activation to work, there was painstaking tweaking of the input gain setting - which seemed to change all the time.

Push-to-Talk. Theres a nice little app made, Ventriloctrl that can allow you to use the push to talk feature while playing games (otherwise you are restricted to push-to-talk only while the Ventrilo window is the active window). There is a walk-through on these forums that takes you through the process.

Getting ET and Vent to work together. Enter the nightmare. The only way to do it is with SDL and a workaround, et-sdl-sound which re-routes sound from Enemy Territory. The walk-thru's are ok, but none are in detail, and when things can go wrong, they do. A file you have to make requires the line 

> export ETSDL_SDL_LIB="libSDL.so"

...however the "libSDL.so" is only if you have the oldest version installed, by default you will have the latest, and need to change this to libSDL-1.2.so.0" or something similar, you can look in packages installed and files installed to get the name of yours.

Then if you're like me you'd think great, nothing else could possibly go wrong - lets run the game with the audio workaround. Then you'd see the fatal errors. The short version is that the libSDL package you probably have installed isn't the full deal. You then need to do a search for libSDL in package manager and install the FULL package (libDSLdebian-all) so that ET even runs. Then if you still have no audio there are commands you can use

> echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
> echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

I now load up Ventrilo by using 

> aoss wine ventrilo

and the key grabber program to use push-to-talk. ET is loaded using the audio workaround. The sound in ET has some background interference but its working and that's all that matters for me.

So if you're going to have a crack at doing it, good luck - it can be done. 

Eventually.

---

