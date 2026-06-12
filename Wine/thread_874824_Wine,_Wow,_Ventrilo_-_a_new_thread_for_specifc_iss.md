---
title: "Wine, Wow, Ventrilo - a new thread for specifc issues"
date: 2008-07-30
forum: Wine
---

### Post by nosto on 2008-07-30
> **endy said:**
> I'm sure I'm not alone when I say I've been trying to get ventrilo working for a while. Well today I got it working with no hastle and since a quick search here for 'ventrilo' turned up only one topic I thought I'd post what I found :D

Note: The version of wine I used was from the backports repository, I haven't tried any other version so step 1 may be unnecessary.

1. Add the extra repositores from the Unnoffical Ubuntu Guide:
```

[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

``` 

2. Install the following packages:
```

wine (version 0.0.20050419-1~5.04ubp1)
libwine (version 0.0.20050419-1~5.04ubp1)
libwine-alsa (version 0.0.20050419-1~5.04ubp1)
cabextract

``` 

3. Download Ventrilo: 
```

[http://www.ventrilo.com/download.php](http://www.ventrilo.com/download.php) 

``` 

4. Make a directory for ventrilo and extract it:
```

mkdir ~/ventrilo
cd ~/ventrilo
cabextract /path/to/ventrilo-2.2.0-Windows-i386.exe

``` 

5. Edit the file:
```

~/.wine/drive_c/windows/system.ini

``` 

And add the following line:
```

MSACM.msgsm610=msgsm32.acm

```

6. Next you need to get your hands on the windows file 'msgsm32.acm' from an existing windows partition (C:/WINDOWS/system32/msgsm32.acm) and copy it to  '~/.wine/drive_c/windows/system/'.

7. Run vent:
```

cd ~/ventrilo
wine ./Ventrilo.exe

```

I hope it works, and I also hope I'm didn't state the obvious  :razz:



This was taken from [http://ubuntuforums.org/showthread.php?t=579378&highlight=wine+wow+ventrilo](http://ubuntuforums.org/showthread.php?t=579378&highlight=wine+wow+ventrilo)

I have followed this guide - however I am still having severe sound issues in regards to this.  Someone who has this working spotless could you please go through your configuration of wine (in the audio tab) any scripts you are running and if you are using aoss to run these applications.

My issue is that if I have both alsa and oss checked i can hear people but they can't hear me.  As soon as I uncheck alsa - I can't hear anyone but I come through crystal clear.

Another issue I had is that after i use my push to talk key once it picks it up the first time but any time after that even with ventrilo selected it will not "push to talk"

Any help would be much appreciated.  I am running 8.04 but I can't tell you my wine version because I am currently at work.

---

### Post by jasontu on 2008-07-30
I have wrestled with sound, wine, and WoW for a while... Ultimately I just had to drop about $20 and get a Turtle Beach sound card, which worked beautifully out of the box.

Your problem sounds different though.  Can you only not hear voice chat when you turn off ALSA or can you not hear the game either?

If you give us all the tedious details we may be able to help out.  Since you're coordinating your system, wine, WoW, and Vent... all the same time, you are dealing with several control panels.  It sounds like Vent may be having conflicts with your mic when you have both ALSA and OSS turned on, but the speakers are definitely managed by ALSA rather than OSS.  You may need to figure out how to disable OSS as a manager for your mic... or something.

See if you can find all the control panels involved and see if you cannot get them synchronized - with each driver controlling the same stuff on every one.

---

### Post by jasontu on 2008-07-30
Keep in mind that I'm just pushing forward what I fiddled with for hours with varying results.  (It ultimately turned out that my mic channel on my onboard sound was just too weak to be heard.)

I'll say it first before the few others who will mention it:  Ventrilo is not terribly Linux friendly.  I know there are plenty of guilds that are pretty attached to the program, and I also know that it *is* possible to do.  Don't give up hope.  Personally I always just use the in-game voice-chat option... simply because it's just there.  If you start to get really frustrated maybe other voice-chat options are worth looking into.

---

### Post by nosto on 2008-07-30
> **jasontu said:**
> 
Your problem sounds different though.  Can you only not hear voice chat when you turn off ALSA or can you not hear the game either?

See if you can find all the control panels involved and see if you cannot get them synchronized - with each driver controlling the same stuff on every one.


I can hear the game sound and I can talk to the people in vent but I can not hear their reply.  So in game audio works in ventrilo my input works but i receive no output.

No other option from ventrilo either so. 

As a side note I also have had this working previously but I had to format my drive so I could have both xp and ubuntu on at the same time.

---

### Post by jasontu on 2008-07-30
Hmmm... sounds like something is conflicting with something... what I found to be helpful is just to find out any possible place these drivers could be set.  Make sure mic is turned all the way up for both, etc.  I hope someone with more technological knowledge can help you.  My advice is basically: just fiddle with it until it works!

---

### Post by nosto on 2008-08-01
I am running wine-1.0.  ubuntu 8.04. ventrilo 3.0.1.

I have followed the guides out there which are mostly the same and still having low results.

This is also a bump.

---

### Post by drpunkerz on 2008-08-06
> **nosto said:**
> This was taken from [http://ubuntuforums.org/showthread.php?t=579378&highlight=wine+wow+ventrilo](http://ubuntuforums.org/showthread.php?t=579378&highlight=wine+wow+ventrilo)

I have followed this guide - however I am still having severe sound issues in regards to this.  Someone who has this working spotless could you please go through your configuration of wine (in the audio tab) any scripts you are running and if you are using aoss to run these applications.

My issue is that if I have both alsa and oss checked i can hear people but they can't hear me.  As soon as I uncheck alsa - I can't hear anyone but I come through crystal clear.

Another issue I had is that after i use my push to talk key once it picks it up the first time but any time after that even with ventrilo selected it will not "push to talk"

Any help would be much appreciated.  I am running 8.04 but I can't tell you my wine version because I am currently at work.

I am also experiencing this issue. Anyone else?

---

### Post by Roulette1 on 2008-08-17
On the Ventrilo website it says they are working on a Linux version - maybe we can threaten/pay them into working on it more so it will come out quicker? :)

---

### Post by Dekafox on 2008-09-02
Bumping this up with a alternate possible solution I found.

I was already running WoW with padsp, with alsa-oss installed and OSS selected in the WINE config.  If I launch Ventrilo also with padsp, as in "padsp wine ./ventrilo" it seems to coexist peacefully.  Not sure offhand which part did the trick, other than padsp making it work.

My openalrc consists of:
```
(define devices '(alsa))
(define alsa-in-device "plughw:0,0")
(define alsa-out-device "pulse")
```

If it matters.

---

### Post by sdtootle on 2008-09-08
I just installed Ubuntu 8.04.1 x64 on my desktop using onboard sound and an evga nvidia 8800GT 512 video card.  I'm using the latest version of wine via their download/install instructions on the website and did a WoW folder copy from a fresh install on my windows laptop.

I have WoW working flawlessly for the most part (graphics look good, sound doesn't stutter, etc) and I can get on ventrilo and hear people and speak.  My question is still that I cannot use ventrilo while in WoW as far as talking is concerned since the window isn't in focus.  My old install of Feisty and that version of wine (I don't recall) I had no issues with PTT while in WoW.  I've also tried VentriloCTRL 0.5 which doesn't work either (when I set PTT key, it sets it to numlock instead of Key A or whatever the readme says it is suppose to be when I press the '~' key).

Also, I can only use WoW audio or Rhythmbox audio atm.  Whichever I want to listen to more, I have to open first or else all I get is the other's audio.  I've tried using aoss on either/or, and both without any luck.  I've tried different configurations for audio under winecfg, but in order for vent to work while focused, I need both OSS and ALSA checked.

I've been searching for the passed few days with no solution found.  All help is appreciated.

---

### Post by sdtootle on 2008-09-08
> **drpunkerz said:**
> I am also experiencing this issue. Anyone else?

I had this issue when I had "Use Direct Sound" checked in setup for the input device.  My current setup is "Use Direct Sound" for output checked and unchecked for input

---

### Post by Darth Buh on 2008-10-20
I've done the same thing with unchecking the DirectInput option, however, people hear all of my WoW sounds when I hold down my PTT key... the game sounds are as loud if not louder than my own voice.

---

### Post by soiled skivvies on 2008-12-28
I can get my mic to work, and the only way to hear people talk is if i go into the setup tab, wheere I cannot talk, but can hear everyone else.  I had to enable every audio option just to get the mic to work.  Sometimes, it errors out and says it failed to open the default something with either an rc=10 or rc=1.

Itt's registering them as speaking when they do, but I can't hear them.  it registers me as speaking, and they say they can hear me so easily and clearly, it's impossible to miss what I say.

---

### Post by SoAnIs on 2009-01-07
Soiled, just had a very similar problem.

Got it working with the following:
WINE config: only ALSA enabled. Full hardware accel, driver emulation checked.
Vent setup, voice tab:
Output device: dmix:0
Input device: Default Wave Mapper (NOT dsnoop:0)
Mixer: (none)

With the python push-to-talk script it works fine.

---

### Post by sin1984 on 2009-01-09
here is my problem. sound from both WoW and Vent i can hear them talking. i can hear wow playing smoothly. BUT they cant hear me. my mic works fine in skype, i can hear them they can hear me. 

its driving me nuts why cant vent hear me?

---

### Post by gmerrick on 2009-01-14
Before you start wow and vent, open a terminal window and type

killall pulseaudio

I found this tidbit in the world of warcraft forums and it seems to work for me.

---

### Post by GeoPirate on 2009-01-16
what is the turtle beach sound card that works for wow + vent + mic out of the box?  I would happliy buy it, just need to know the model and stuff.

---

### Post by Falheim on 2009-01-17
I have another problem that probably is a total noobish one.
My Ventrilo doesn't find any codec what so ever.. i tried to install a codecpack into my .wine/dirve_c but vent is still unable to find a codec 
all other sound in any game works perfectly.

Im using SB Audigy 2

---

### Post by yoma819 on 2009-01-25
speaking of problems
has anyone had the problem that when they start wow using crossover office then the bottom of the screen is cut off!
the only work around i have found is to run it in window mode.
this is most annoying as it is very small!
any one fixed this issue?
many thanks
yoma

---

