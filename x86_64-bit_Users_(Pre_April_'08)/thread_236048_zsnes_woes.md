---
title: "zsnes woes"
date: 2006-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Grey on 2006-08-14
Hi...  I'm trying to get snes emulation working on my mythtv box, which runs amd64 dapper.  I've spent most of the night working on it and I am giving up for the night, but I was hoping that someone could give me some tips.  I'm just going over the steps I tried tonight, but I'll post some debs in the morning if anyone's interested.

I first tried snes9x, but it failed rather spectacularly.  It failed due to a lack of DGA support in new nvidia drivers.

So, I moved to ZSNES, which has no native 64-bit version.  I tried compiling the deb from source.  As expected, it failed compilation.

Undaunted, I tried the newest SVN version.  It compiled fine, but seg faulted.

I compiled it on my 32-bit laptop, and it compiled fine.  It runs FANTASTICALLY on my laptop, and I highly recommend that you give it a try, if you haven't already.

I installed the deb on my mythtv box, and it also ran fine... except that the sound was scratchy and out of synch.

No problem, I thought.  I've seen this behaviour a million times, and I installed the OSS version of SDL from the repositories.  After trying it again, and seeing no change, I remembered that it's the 64-bit version, and that won't help.

So, I copied the SDL shared libraries from my laptop to the mythtv box's /usr/lib32.  That had an effect, but unfortunately it had the effect of not producing any sound at all.

Figuring that the ia32 libs did something weird with the libraries to make them run on 64-bit, I decided to modify the ia32 package from the repository.  So, I downloaded the source, and modified it to use the oss version of the libraries instead.  It built the new package fine, but again, I was greeted with the lovely lack of sound.  (Hey, at least I recompiled it correctly (it's one messed up package))

I tried doing "cat /dev/urandom > /dev/dsp" at this point.  Again, silence.  ("aplay /dev/urandom" plays just fine).

So, I'm wondering now if anyone has any other suggestions, or would like to sample my debs?  Has anyone attempted anything like this before?  Does anyone have any clue why catting /dev/urandom to /dev/dsp would not play any audio?  Is there something wrong with my OSS?

For reference, this is an ASUS Pundit P1-AH1, which has a strange specially built motherboard.  ALSA says that the sound card is a Realtek ID 861. (ALSA exhibits some strange behaviour with the card as well.  There's no master volume control).

Thanks in advance for any help.

---

### Post by Kilz on 2006-08-14
You might try installing lib32asound2

---

### Post by Grey on 2006-08-14
It's already installed... it's a dependency of the ia32-sdl package, is it not?

---

### Post by Jason_25 on 2006-12-22
I fixed this finally.  I started by installing ia32-libs. Then I copied libSDL-1.2.so.0 and libSDL-1.2.so.0.7.3 from the libsdl-debian-oss i386 package to /usr/lib32.  Then I needed to copy everything from the i386 libdirectfb package to /usr/lib32.  Zsnes sound is perfect now.

---

### Post by janfsd on 2006-12-22
May I ask which version of zsnes where you using? Because I got a sound problem too, but I was not using the official stable build (1.42), it was a newer build actually. However when I tried the 1.42 build the sound was working great, all was ok.

---

### Post by Horbert on 2006-12-22
ZSNES 1.5 was released today and I think it may build better on 64 bit targets and has had many sound fixes. You might want to try that one out.

---

### Post by janfsd on 2006-12-22
Thanks for that, i just checked it, compiled it, but i get seg faults when i try to run it :(

EDIT: 
There are some binaries for amd64 at [http://board.zsnes.com/phpBB2/viewtopic.php?t=9179](http://board.zsnes.com/phpBB2/viewtopic.php?t=9179)
It's working for me, however the sound was choppy for me, I just followed Jason25 advice of installing the 32bit libsdl1.2debian-oss libraryand now everything is working great :)

---

### Post by Jason_25 on 2006-12-25
Thanks for the response.

Just an FYI, when installing firefox32 today, one of the depedancies copied libSDL-1.2.so.0.7.2 and symlinked it, so it made the sound crackly again.  After deleting libSDL-1.2.so.0.7.2 and copying libSDL-1.2.so.0.7.3's symlink things were well again.

I don't see a need for the new version when this one works very stable and plays chrono trigger great.

---

### Post by Slammer64 on 2006-12-27
janfsd, you can try compiling zsnes 1.50 with the following flags; export CFLAGS="-m32" export CXXFLAGS="-m32", that has worked for me under other 64 bit distros when compiling something with NASM calls in the source.

---

### Post by janfsd on 2006-12-28
I tried with that too, but it doesn't compile at all with that, I cannot remmeber what exactly it complains about (right now I am with another PC, not mine), but it was something like it cannot create executables for my system because it was incompatible, and looking at the log, I find that it looks for libc, and another libraries, maybe it looks for the 32bit ones? which I don't have them, do I need some special libraries to use that flags?

---

### Post by survient on 2007-03-03
I had this sucker working not a week ago. Then I had some issues where I broke libasound, it's fixed now, but I can't remember how I got zsnes running. I have tried compiling it with teh -m32 flags and such, but gah, I keep getting a segmentation fault. I think a 32 bit version of the libsdl package would help, but I can't find one. Where have I gone wrong??!!!

---

### Post by dfreer on 2007-08-12
You can try out my amd64 package of zsnes if you are still having problems ;)

---

