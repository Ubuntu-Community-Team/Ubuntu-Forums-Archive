---
title: "Jack won't start after installing wineASIO"
date: 2012-10-30
forum: Wine
---

### Post by IonutCampean on 2012-10-30
Hey there!
I'm new to this forum and new to ubuntu. My version is 12.10, and i'm running the gnome-shell desktop. My problem is the following:
    I installed jack and ardour3 to use for my personal recording setup, but jack wouldn't start so i had to remove pulseaudio. After that, jack and ardour worked fine, but ardour kept getting disconnected from the jack server, with some king of x-error (can't really remember what it was called) because ardour wasn't fast enough. 
    Seeing that didn't work quite so well, i installed wine, wineasio (compiled fine) and reaper, however i used some kxstudio repositories. Reaper worked beautifully but only with a hell of a lot of latency. 
    I tried to run ardour again, but jack wouldn't start, giving me this error message in the terminal:

The program 'jackd' can be found in the following packages:
 * jackd1
 * jackd2
Try: sudo apt-get install <selected package>

BTW: i always launched jack from the terminal, i couldn't get qjackctl to work.

I tried removing jack, no problems. Now, whenever i try installing it again i get an error saying i have unmet dependencies:

The following packages have unmet dependencies:
 jackd : Depends: jackd2 but it is not going to be installed or
                  jackd1 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

I think this might be because i used the kxstudio repos.
I tried using ppa-purge to remove those repos and downgrade my software to what it was before, but i still can't install jack. 
Reaper still starts up fine, however i can't get any audio input into it, i can just get it to play back files and use vst plugins.
Any thoughts?

---

