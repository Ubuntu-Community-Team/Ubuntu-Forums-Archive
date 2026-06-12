---
title: "No sound. what? I said no sound."
date: 2005-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by jhbumby on 2005-10-21
Finally got my DVD to work.  Plays great, except I have no sound???  Anyone, a little help here.  Ubuntu reads the card correctly, it just isn't putting any sound out.  I am a newbie, so it could be something simple.  Thx---
John

---

### Post by zekolas on 2005-10-22
What program are you using to play the dvds with? Also is there sound when you play mp3, wave files or audio cd, or do you just have no sound when you play dvds?

---

### Post by jhbumby on 2005-10-22
It seems to be for everything.  I am using totem for my dvds, but none of the things you suggested work either (atleast the ones I can use, another category another time.)  So I don't know what to do.  I assume that since the computer reads the card and knows the type, that it isn't the card.  I assume that it isn't the speakers because I tried them on another computer, and they worked there.  Anything else is fair game.  Thanks again-
John Newbie

---

### Post by LittleReinhart on 2005-10-30
Hey John,

I'm a newbie myself, using linux for half a year now.

I had major problems to get my sound working with Ubuntu 5.04. Since I switched over to Ubuntu 5.10, it all worked perfectly (exept for multi-channel sound, I had to do that manualy).

Let me try to tell you in human words how I got my sound working on the ubuntu 5.04, it might give you some idea where to start looking.

1) The problem was that Hoary recognised a sound-card, but not the right one.
So check the driver. (if you type "alsamixer" in a terminal, the first line gives you your installed driver)
I use the card "ca0106" and I found the installation prosedure over here: [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+24bit.&chip=SB0410%2C+P17&module=ca0106#Inst](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+24bit.&chip=SB0410%2C+P17&module=ca0106#Inst)

For other sound-cards : [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

2) Second problem I had: Sometimes sound was working, sometimes not.
[To all you linux-experts, please correct me if I'm wrong]
In Linux every device is controlled by something. Unlike in windows, every device can onely be controlled by one thing. So, for example, if xmms is using the sound-device, any other program (like Totem or mplayer) who would like to play some sound will give an error. So, even if you don't hear any sound at all, the sound-device can still be in use by some program.
A way to solve this is setting up a "demon sound device" that controles the sound device and tell all programs that want to play a sound that they have to contact the demon instead of sending everything to the sound device directly. (The sound demon then mixes all the sound and sends it to the soundcard (the soundcard then thinks there's onely one sound playing))
I am nog exactly shure anymore how I set this multi-channel sound up (I accidentally deleted the wrong directory some time ago, wish contained my personal "how to" files).
What I do remember: On my current Ubuntu (5.10), I first set up esd (enlightenment sound demon)
FYI: I use Ubuntu with the enlightenment (E16) window manager and I have installed gnome and kde, so I can use all these apps.
Mulitchannel sound worked but the soundquality with esd was realy crappy, so I disabled it again.
And since then, my sound works just fine (good quality and multichannel). So I'm not realy shure how this comes.

But here are some config files:
/home/"user"/.xsession  #this is my startup-script
[INDENT]# Enlightenment inserted Execution string here
#esd &                      <- esd has to be started befor something else takes controle over the sound-card, but because of bad soundquality I disabled it
xmms -fp &
xterm &
gnome-panel &
gaim &
mozilla-thunderbird &
kate /home/reinhart/Todo &
exec /usr/bin/enlightenment[/INDENT]

/etc/esound/esd.conf
[INDENT][esd]
# auto_spawn=0        <- orriginal setting
auto_spawn=1
# spawn_options=-terminate -nobeeps -as 5        <- orriginal setting
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=[/INDENT]

Damn, I have changed an other config file as well... but I can't remember wish one... it had something to do with alsa i think...

I hope this got you closer to a sollution.

Greetings,
Reinhart

P.S. You might want to boot from the latest knoppix, and look arround how your sound works there (drivers, config files, ...)

---

