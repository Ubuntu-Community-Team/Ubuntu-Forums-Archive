---
title: "sound card problems"
date: 2007-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by yorkiet on 2007-05-31
hi all 

I've recently started trying to get  to grips with ubuntu edgy however i have hit a bit of a stumbling block,

I'm currently using a Creative XFi Xtreme gamer 7.1 sound card  and regardless of what i do I cnat seem to get it working, I've had a look round on the net but cant seem to find anything of use,

can anyone help me get my sound card installed please :)

many thanks 

Yorkie -T

---

### Post by renzokuken on 2007-05-31
have you tried using the latest alsa-driver? i believe its at 0.1.0.14rc4 right now. its newer than the edgy default and has better support for newer cards

go to [www.alsa-project.org](www.alsa-project.org) and download the latest "alsa-driver" package to your home folder.

now make sure you have the tools for compiling from source
```
sudo apt-get install build-essential
```

then to compile do the following

```

tar xjf alsa*
cd alsa*
./configure
make
sudo make install

```

reboot and see how that goes

---

### Post by yorkiet on 2007-05-31
thanks for that will give it a try when i get home tonight and let you know how it goes :)

and thanks for giving me intructions on what to do i've tried a couple of other related forums in the past for other things and people tend to treat you like you should know what to do, but as im still quite new obviously I dont, so thanks for that :)

---

### Post by renzokuken on 2007-05-31
not a prob at all.

it wasnt long ago i was a complete n00b too, but if people explain stuff properly (like so many great members did for me when i started) then you soon learn things for yourself

---

### Post by yorkiet on 2007-05-31
I've jsut tried what you said but it keeps coming up with "error 1" any ideas why??

heres what t says when i try to do as you said:
```

make[1]: Entering directory `/home/yorkiet/alsa-driver-1.0.9/acore'
mkdir -p /lib/modules/0.0.0/misc
cp snd-hpet.o snd-page-alloc.o snd-pcm.o snd-timer.o snd.o /lib/modules/0.0.0/misc
cp: cannot stat `snd-hpet.o': No such file or directory
cp: cannot stat `snd-page-alloc.o': No such file or directory
cp: cannot stat `snd-pcm.o': No such file or directory
cp: cannot stat `snd-timer.o': No such file or directory
cp: cannot stat `snd.o': No such file or directory
make[1]: *** [_modinst__] Error 1
make[1]: Leaving directory `/home/yorkiet/alsa-driver-1.0.9/acore'
make: *** [install-modules] Error 1


```

---

### Post by yorkiet on 2007-06-01
I even tried using the instructions on the alsa site but it came up with the same error :(

---

### Post by renzokuken on 2007-06-01
you got the kernel headers installed??

i think you may need those first, cant honestly remember.

---

### Post by yorkiet on 2007-06-01
kernel headers? how would i go about installing these? 

lol oh how i hate being a n00b.

---

### Post by yorkiet on 2007-06-02
does anyone know a way round this problem? I'm sorry if i seem impatient.

---

### Post by Kuraudo on 2007-06-02
You probably miss a bunch of libraries.

Try this and see if it solves you problem.
```
sudo apt-get install alsa
```

Don't you get any sound at all?

---

### Post by Cappy on 2007-06-02
The only X-Fi sound card that works at all on Linux is the "Sound Blaster X-Fi Extreme Audio (and not very good, supposedly).

Creative was supposed to release drivers for X-Fi by now but they pushed them back .. to the end of this year (I think).

I would buy an Audigy 2, Audigy 2 ZS, or SoundBlaster Live! card. You should be able to find one for $10-$25 on ebay if you can't find one locally.

---

### Post by yorkiet on 2007-06-04
sorry but that hasnt helped :( 

no im not getting any sound at all :(

---

### Post by yorkiet on 2007-06-04
ah i didnt realise that this thread had gone onto another page. I'll look into what you said cappy and see if i can find a cheap audigy card which is just a bit annoying as i only upgraded from an audigy carda couple of months before  started using linux :( ah well

---

### Post by Zhillsguy on 2007-06-06
I am a noob to Ubuntu and linux.... and have a Xtreme Audio card for recording in my band room. Unfortunately, Creative is not supporting their stuff (supposedly because of time spent for Vista user suppport) for the freeware distros. 
I installed the latest Alsa drivers with no errors and it is not detected. Luckily, I left my pc in dual boot mode for Win XP. I also tried it with Fedora, but Redhat even has more problems with Alsa. I also cannot get my wireless usb working, ndiswrapper sees it but does not load the driver properly. As this  pc is mainly sound oriented I won't pursue trying to get the sound working for a while, it's not worth the effort to me. I have Ubuntu on an old p3 laptop and it detected the wireless pcmcia card (both wireless cards are D-Link) and onboard sound when installed.

Oh well, chalk up another "money wins".

---

### Post by yorkiet on 2007-07-18
lol well i will keep pursuing a way of getting my soudn working :)

---

