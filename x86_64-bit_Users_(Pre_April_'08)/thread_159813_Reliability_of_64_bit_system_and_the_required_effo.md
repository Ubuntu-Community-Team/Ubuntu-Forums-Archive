---
title: "Reliability of 64 bit system and the required effort"
date: 2006-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by artik on 2006-04-13
Hello All,
Few days ago I'd done little benchmark tests with 32/64 bit LiveCD of Dapper Flight 6... I was quite impressed:
[http://www.geocities.com/artyomtnk/bench-amd-64-32.pdf](http://www.geocities.com/artyomtnk/bench-amd-64-32.pdf)

At this point I'm running 32bit breezy and think to move to 64bit but...
I have several questions about problems and solutions (and mostly how complete they are)

1. Flash player - I've understood that I need to run 32bit version of FF (it does not seems too nice - connection to environment but still works)
2. Multimedia - I can play allmost everything with mplayer and xine but: not WMV8 (buggy) / WMV9(not plays at all). Can I view them without debootstrap?
3. I've seens that lost of things can be run (like skype, acroread, realplayer etc) with linux32 however I still ask myself - is it works well.
4. wine and IE - I need them form web development - any chances or debootstrap only?

And final - If I install programs in debootstrap do they run as well as in pure 32bit environment - I talk moslty about games etc.. 

**The actuall question is:**

1. Will I be able to run **all I need** wether using debootstrap or just lib32
2. Does 32bit programs work well in 32bit environment?
3. How much effort should I put in order to make the system run anything I need.

Thanks,
Artik
P.S.: Most of my work on PC is quite multimedia oriented - so I do need good support of codecs and I do need speed of 64bits

---

### Post by Goatee on 2006-04-13
I have a 64bit machine (i'm typing from it) 32 bit programs work fine and I'm a newbie still so I don't know what debootstrap is so... sorry if i'm not much help.

---

### Post by maury on 2006-04-14
I have Dapper AMD_64 on a drive and it runs very good and faster than anything I've run on this box so far. (2 years) I have a removeable drive bay and check out a lot of distros. Most of the 32 bit distros that I have tried run well on this box and simply mepis has been my primary system for close to 2 and 1/2 years. Comming from windows I leaned toward KDE but as I've gotten more comfortable with Linux and Ubuntu I have no real problem with Gnome. With Mepis using Ubuntu and an effort being made to bring KDE and Gnome closer together good things should happen.

---

### Post by artik on 2006-04-14
Is there any chances that Ubuntu will add some "important" applications in 32bit mode to the repositories:
Something like firefox32, xine-u[COLOR=black]i32, mpl[/COLOR]ayer32, wine - like they did for OpenOffice?
In order to prevent headache of installation of different 32bit programs?

---

### Post by WhiteHorse on 2006-05-04
I'm on x64 ubuntu and it seems ok. I really notice the difference with my encrypted drives and compile times. I can completely compile Thunderbird+enigmail in about 10-15 min. It usually takes an hour or so on a 32 bit processor. XMMS works like a dream with my recompiled ALSA driver. Still can't get mplayer to work without disabling the system sounds though... Once that's working I bet it will scream with media files. The only drawback so far is I've had to compile alot of programs to get them to play nice. I have to use 32 bit firefox to get flash to work and that has the ole audio out of sync with the video problem. Hey, is there ANY file that totem can open? I haven't found any yet...

---

