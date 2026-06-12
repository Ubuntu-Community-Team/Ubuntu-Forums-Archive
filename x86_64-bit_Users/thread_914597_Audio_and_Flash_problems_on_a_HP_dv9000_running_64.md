---
title: "Audio and Flash problems on a HP dv9000 running 64 bit"
date: 2008-09-09
forum: x86 64-bit Users
---

### Post by koolguynet on 2008-09-09
I have tried a few things and haven't been able to solve this problem.  I am hoping the community can help.  I have an HP dv9000 with an AMD Turion X2 64-bit processor and 2GB of RAM.  I am running an Nvidia card in it for video and audio.  I have Ubuntu 8.04.1(64-bit version) running on this machine.  Once I tweaked it, it runs very nice!  I do have one problem that is kinda big.  I have intermittent sound (more often then not, no sound).  I can't seem to play music and flash videos are acting up (which I feel is related).  Flash videos will only play for 2 seconds and will never have sound.  I have tried a few fixes and nothing has worked.  Any ideas?

---

### Post by gwenn on 2008-09-09
You must install the latest firefox(3.0),unninstall flash plugginns that you already have,in software sources you must check proprietary,restricted,and also the third party.Then you have two posibilities:apt-get install flash pluginn or manually search in Synaptic.

---

### Post by Yellow Pasque on 2008-09-10
If all else fails, try replacing ALSA with OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by koolguynet on 2008-09-12
I tried doing a complete removal of my flash plugin and then installed the non-free version.  No change... youtube still stops after two seconds and it will only play two seconds of music (still no sound) using amarok.  I can try switching to OSS, but does anyone know why this is happening?

---

### Post by koolguynet on 2008-09-12
Ok, the puzzle gets even more complex.  I am hoping this clue helps someone who is smarter on this figure out what is going on.  I can play music with 'Movie Player', but YouTube and Amarok don't work.

---

### Post by koolguynet on 2008-09-20
Still the same situation.  I am thinking it is a problem with Flash.  Does Amarok use any flash components?  Here are the programs that aren't working for sound:

Miro
Amarok
Flash videos

In most cases you can see the video move for 2 seconds and then the video freezes.  This is especially a problem seeing that I use Miro all the time.  Any advice?  Should I try upgrading to the beta of Flash.  I tried once before, but I believe I failed at it.

---

