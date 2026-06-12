---
title: "XMMS problems - loads but wont play"
date: 2005-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by musther on 2005-07-17
Has anyone had this problem with xmms, it loads fine and you can load playlists add files etc, but it hangs when you hit the play button, have to close it with xkill.

---

### Post by Strife on 2005-07-17
Yep. I have, and I'm not sure what the deal is.

---

### Post by Flac on 2005-07-18
wierd, ive not had any problems, running any plugins? maybe an older/newer version?

---

### Post by negatory on 2005-07-18
Change the output plugin...are you using alsa without instaling the kernel support for it?Try oss or esd.
Thanks
Pedro Carrico

---

### Post by Mauleye on 2005-07-18
Same problem here - even with MPlayer and Xine ... but no probs with Totem or Rhythmbox.

---

### Post by estel on 2005-07-18
[QUOTE=Mauleye]Same problem here - even with MPlayer and Xine ... but no probs with Totem or Rhythmbox.[/QUOTE]
 I replaced esd with poly, but now the esd plugin doesn't work at all, and I'm not sure how to get XMMS to use the poly plugin instead. Can anybody help? Or shall I just go back to esd?

---

### Post by Jet2k5 on 2005-07-18
Ok first do a quick search in synaptic on xmms.  Make sure that you have all the suitable plugins.

Second of all I need you guys to run xmms from a terminal window.  Just open up console are run xmms from the command line.  Watch the terminal as you hit the play button.   When you hit the play button it should spit out some kind of error.  I want you to just take that error and post it here so we can try to find out what it is.  Like I said it might be a bug of some sort.  Or you don't have the right plugins.  Are these .mp3's by the way that you are trying to play?

---

### Post by Jet2k5 on 2005-07-19
*BUMP*  

Just wanted to know if you guys have fixed your problem.  If so post your solution :).  If not run it from a terminal window and post the error.

---

### Post by lokett on 2005-07-20
Hi,

I've got problems as well with xmms (but also with totem :/)
I ran it in a terminal and I got no message at all (play, pause and stop buttons), and it just won't play...

Maybe I don't have the necessary plugins to play mp3s, but what are they?

Thanks :)

---

### Post by Jet2k5 on 2005-07-20
[QUOTE=lokett]Hi,

I've got problems as well with xmms (but also with totem :/)
I ran it in a terminal and I got no message at all (play, pause and stop buttons), and it just won't play...

Maybe I don't have the necessary plugins to play mp3s, but what are they?

Thanks :)[/QUOTE]


It's very weird .. maybe someone that has access to the full working amd64 repos can help you out.  I just followed the Ubuntu Guide ( 32-bit ) since that is what I'm on right now still have about 10 days for my processor to get here along with some other things.  When you ran xmms from command like how did you run it?  It's very odd that absolutely nothing came out.

---

### Post by medication on 2005-07-20
I had a similiar problem with XMMS.  It just stalled when I tried to play something.  I haven't tried it in a while but I will run it from a terminal when I get home tonight (I'm at work and my box at home is offline right now).

I'll post what I find.

---

### Post by Tamir on 2005-07-20
[QUOTE=medication]I had a similiar problem with XMMS.  It just stalled when I tried to play something.  I haven't tried it in a while but I will run it from a terminal when I get home tonight (I'm at work and my box at home is offline right now).

I'll post what I find.[/QUOTE]
 If it is a version problem (bugs etc..) the only thing I can do is to build new packages. what do you think?

---

### Post by medication on 2005-07-20
I'm confirming that the console doesn't report an error and the application just freezes after the 'play' button is clicked.

Tamir, do you think that you might have time t rebuild this package?  Before you do though - perhaps this issue should be raised to the community at large (as the 'package' is already out there).

---

### Post by cnspy on 2005-07-20
I just recompile the kernel 

1. remove the oss
2. compile the alsa into kernel (not as module)

then set the xmms output plug-in to alsa. 

it works well now.

---

### Post by uniko on 2005-07-21
I gave up trying some time ago and ended up with beep media player, which I believe is a fork of XMMS with GTK2. It can be in universe if anyone's interested.

---

### Post by Sam on 2005-07-21
I know people who had the same problem. They changed the output plugin and it works well now.

---

### Post by Jet2k5 on 2005-07-21
Can anyone else confirm on changing the output plugin fixing it?

---

### Post by alegomes on 2005-07-21
[QUOTE=Sam]I know people who had the same problem. They changed the output plugin and it works well now.[/QUOTE]

Yeah, it worked also for me. For those who don't know how to change the xmms output plugin, open xmms and hit ctrl+p for preferences and then go to the I/O audio plugins tab. 

I had libOSS.so and changed it to libesdout.so.

[]s

---

### Post by Jet2k5 on 2005-07-21
Ok good good.  All you other guys with problems try this and tell us if it fixes it, so what we can determain the thread as solved ....

---

### Post by medication on 2005-07-21
[QUOTE=Jet2k5]Ok good good.  All you other guys with problems try this and tell us if it fixes it, so what we can determain the thread as solved ....[/QUOTE]
 I'll try to make this change tonight and determine wether or not that resolves the problem. (no promises though, we'll have to see what the wife says)

---

### Post by medication on 2005-07-22
[QUOTE=medication]I'll try to make this change tonight and determine wether or not that resolves the problem. (no promises though, we'll have to see what the wife says)[/QUOTE]
 Unfortunately I wasn't able to try the fix last night... I'll have to try this over the weekend.  Sorry to anyone who was waiting on me.

---

### Post by mike998 on 2005-07-22
I was using the ALSA output plugin and when I switched to ESD it kinda went away.
I'll edit if it doesn't work!

---

### Post by Psquared on 2005-07-24
[QUOTE=alegomes]Yeah, it worked also for me. For those who don't know how to change the xmms output plugin, open xmms and hit ctrl+p for preferences and then go to the I/O audio plugins tab. 

I had libOSS.so and changed it to libesdout.so.

[]s[/QUOTE]

I was having the same problem. I tried it with ALSA but that didn't work. I changed to libesdout.so and all is well now.

Strange since it was working and I didn't change the output plugin??

---

### Post by agds on 2005-08-01
I had the same problem.  I only made two changes to my system.  The first was installing the gstreamer0.8-plugins package.  The second was changing the XMMS output plugin, as another poster described.  Initially XMMS would play with the output set to ESD and nothing else.  Now that I've applied Gandalf's ALSA fix, it works better with the output set to ALSA.

If you need to get ALSA configured correctly, you can look up his HowTo or check out my blog, which essentially contains a duplicate of his instructions ([http://livegnudegirls.blogspot.com/2005/08/alsa-sprach-zarathustra.html)](http://livegnudegirls.blogspot.com/2005/08/alsa-sprach-zarathustra.html)).

---

### Post by lavarock09 on 2005-08-09
Hey Guys

I have read throught this topic and I have the same problem, I load up an MP3 and when I press play It freezes,

Does anyone know how to fix this, I only got ubuntu yesterday and have never used linux before

Thanks

Lavarock09

---

### Post by Jessehk on 2005-08-09
[QUOTE=lavarock09]Hey Guys

I have read throught this topic and I have the same problem, I load up an MP3 and when I press play It freezes,

Does anyone know how to fix this, I only got ubuntu yesterday and have never used linux before

Thanks

Lavarock09[/QUOTE]


Same problem. I am able to play music on other players though. 

Xmms is the only one causing problems.

---

### Post by lavarock09 on 2005-08-09
I decided to not bother with xmms and have installed gstreamer0.8-mad

and now Rhythmbox 0.8.8 (Music Player) now Plays MP3's

---

### Post by Tamir on 2005-08-09
And doesn't rhythmbox freeze? :/ on my system it is.

---

### Post by agds on 2005-08-09
Did gstreamer0.8-plugins not help?  My next suggestion would be to run XMMS and/or Rhythmbox from a terminal window and see if any errors appear.  Unfortunately those applications often don't output anything to the terminal, so it may be a dead end.

---

### Post by Steve1961 on 2005-08-15
I also had a problem with xmms not playing.  This how to fixed it (not sure how to put it in a box):


Preferably for AC97 Sound

1. Install alsa-oss
2. Install alsa-headers
3. Make sure you have libesd0 and gstreamer0.8-esd installed. (if not, install)
4. Make sure esound and esound-common are installed. (if not, install)
5. Install alsa-base
6. Install alsa-utils
7. Install gstreamer0.8-alsa
8. Install libpt-plugins-alsa

Ok, next.
1. Right click on the little volume control in your top panel and the
choose Open volume control.
2a. *IF* it opens, you should see two tabs, one for OSS and the other
for Alsa. Make sure nothing is muted.
2b. If it does not open and instead gives you an error, let me know.

We're going to switch you to a sound daemon that allows multiple sounds.
1. In gstreamer-properties, change the Default Sink to output: ESD -
Enlightenment Sound Daemon (Why not alsa you ask? Because alsa makes
crackling noises with the ac97)
2. Change your Output plugin in XMMS to eSound output plugin. (You
also might want to think about using beep-media-player ; it's
essentially identical to xmms, uses same plugins and skins, only it's
made for gtk2 and it's much nicer.)
3. Enable your sound server startup.

That should do it

---

### Post by mizako on 2005-09-01
Hi, 
I am using a laptop and i am suffering the same problems with xmms loading but freezing. I tried to follow your steps but i did not manage to fix it. 

[QUOTE=Steve1961]
1. Install alsa-oss
2. Install alsa-headers
3. Make sure you have libesd0 and gstreamer0.8-esd installed. (if not, install)
4. Make sure esound and esound-common are installed. (if not, install)
5. Install alsa-base
6. Install alsa-utils
7. Install gstreamer0.8-alsa
8. Install libpt-plugins-alsa
[/QUOTE]
Everything installed!
[QUOTE=Steve1961]
Ok, next.
1. Right click on the little volume control in your top panel and the
choose Open volume control.
2a. *IF* it opens, you should see two tabs, one for OSS and the other
for Alsa. Make sure nothing is muted.
2b. If it does not open and instead gives you an error, let me know.
[/QUOTE]
On Volume Control I can chosse in file->change Device between: 
- Intel ICH (Alsa Mixer) 
- Realtek ALC250 rev2(OSS Mixer).
Nothing is muted. 

[QUOTE=Steve1961]
We're going to switch you to a sound daemon that allows multiple sounds.
1. In gstreamer-properties, change the Default Sink to output: ESD -
Enlightenment Sound Daemon (Why not alsa you ask? Because alsa makes
crackling noises with the ac97)
[/QUOTE]
I run on command line gstreamer-properties and a window pop up I chan choose between Alsa, ESD, OSS and Custom. I choose ESD as you said. 

[QUOTE=Steve1961]
2. Change your Output plugin in XMMS to eSound output plugin. (You
also might want to think about using beep-media-player ; it's
essentially identical to xmms, uses same plugins and skins, only it's
made for gtk2 and it's much nicer.)
[/QUOTE]
Here is where the problem appears. I can only choose between:
- OSS Driver 1.2.10 [libOSS.so]
- Disk writer plugin 1.2.10 [libdisk_writer.so]
So i can not choose eSound :-(

What should i do?. Thanks in advanced for your help it sucks not being able to play mp3.

---

### Post by Tux_army on 2005-09-01
Hello i'm also here to confirm that i have XMMS working fine. Like the other users when i pressed play it hangs and when run from the terminal it didn't give any output.

This is what i did 

1. Remove and reinstall xmms

2. Install gstreamer0.8-plugins.

3. Under alsa this is what i have - i don't remember which one i exactly installed some were added as part of dependecies.

> alsa-bae
alsamixergui
alsa-oss
alsaplayer-common
alsa-gtk
alsa-oss
alsa-jack
alsa-nas
alsa-utils
gstreamer0.8-alsa
libpt-plugins-alsa
python2.4-alsaaudio
vlc-plugins-alsa

4.  Press CTRL+P . My outplugin is oss driver 1.2.10 [libOSS.so)and click on configure.

5. I have multiple sound cards on my computer- yours might differ from mine. Under Audio device i changed it to EMU10K1 (DUPLEX) from default (NVIDIA CK804 (DUPLEX)).

6. Under Mixer device i changed SigmalTel STAC9721/23 to my realtek soundcard.

There you go, that how i got it working.

---

### Post by mizako on 2005-09-01
Thanks for the help but i still do not manage to use xmms. 
I still do not manage to get it work.
[QUOTE=Tux_army]
This is what i did 

2. Install gstreamer0.8-plugins.
[/QUOTE]
I installed it

[QUOTE=Tux_army]
3. Under alsa this is what i have - i don't remember which one i exactly installed some were added as part of dependecies.
[/QUOTE]
I have pretty much the same. At least the mentioned by the other guys who have xmms kicking. 
[QUOTE=Tux_army]
4.  Press CTRL+P . My outplugin is oss driver 1.2.10 [libOSS.so)and click on configure.
[/QUOTE]
Same as me
[QUOTE=Tux_army]
5. I have multiple sound cards on my computer- yours might differ from mine. Under Audio device i changed it to EMU10K1 (DUPLEX) from default (NVIDIA CK804 (DUPLEX)).

6. Under Mixer device i changed SigmalTel STAC9721/23 to my realtek soundcard.
[/QUOTE]
I am not able to change anything since only gives me one option. 

I still can not believe how can it be so difficult to use xmms in ubuntu with a normal conf.iguration. Every linux i used came with a default xmms installation which worked perfectly. This things drives me crazy. I hope anyone of you can help me guys!, thanks in advanced.

---

### Post by DancingSun on 2005-09-01
[QUOTE=mizako](...)
I am not able to change anything since only gives me one option. 

I still can not believe how can it be so difficult to use xmms in ubuntu with a normal conf.iguration. Every linux i used came with a default xmms installation which worked perfectly. This things drives me crazy. I hope anyone of you can help me guys!, thanks in advanced.[/QUOTE]
I know, I heard the last release was much better in the sound department.  I'm actually really disappointed to find out sound was so hard on Ubuntu/Linux (Hoary was my first taste of Linux).  The impression is:  there's still a loooong way to go before Linux can catch up to Windows in *some* aspects.

Anyway, the one option that you get in the sound devices, was it OSS or ALSA?

I'll need you to try something to see if I can determine a cause of your problems.  Does other players play sound?  If so, try opening 2 sound files and play them at the same time, preferably with two different applications.  Can you hear audio from both sound files?

If so, try this in a terminal:
```
killall esd
```
Then try playing audio via XMMS.

Also, in the XMMS, have you tried using all the different output plugins?

---

### Post by mizako on 2005-09-01
[QUOTE=DancingSun]
I'll need you to try something to see if I can determine a cause of your problems.  Does other players play sound?  
If so, try opening 2 sound files and play them at the same time, preferably with two different applications.  Can you hear audio from both sound files?
If so, try this in a terminal:
```
killall esd
```
Then try playing audio via XMMS
[/QUOTE]
Yes, you are the man!!!. the 'killall esd' solved the problem. 
So killing the Enlightened Sound Daemon solved it. But can you explain me what was the problem more understandable. I do not know almost anything about sound daemons in linux and it will be good to learn why this problem was happening. Again thanks a lot!!!

[QUOTE=DancingSun]I know, I heard the last release was much better in the sound department.  I'm actually really disappointed to find out sound was so hard on Ubuntu/Linux (Hoary was my first taste of Linux).  The impression is:  there's still a loooong way to go before Linux can catch up to Windows in *some* aspects.
[/QUOTE]
I tried Knopix, Guadalinux, Suse before and i have never a problem with sound. Really disappointed with Ubuntu in that aspect.

---

### Post by DancingSun on 2005-09-01
[QUOTE=mizako]Yes, you are the man!!!. the 'killall esd' solved the problem. 
So killing the Enlightened Sound Daemon solved it. But can you explain me what was the problem more understandable. I do not know almost anything about sound daemons in linux and it will be good to learn why this problem was happening. Again thanks a lot!!![/QUOTE]
The problem is that esd is hogging the soundcard or something to that effect.  Ubuntu utilizes gstreamer as for system sounds.  The sound sink used by gstreamer can be configured by entering 
```
gstreamer-properties
```
in the terminal.  Or you could just go to the menu, System --> Preferences --> Multimedia Systems Selector.  I think the default is either OSS or esound (that's esd).  The sound sink is basically a mixer that mixes mutiple sounds streams together as one stream and sends it to the soundcard, this allows the soundcard to output sounds from multiple applications.  The problem is, all the applications that want to output sound has to output to the selected soundsink, or else it would not be captured if the soundcard is already in use.

In your case, you had XMMS using OSS output plugin (I'm not sure if OSS has a mixer or not though), and if your system sound uses esound, esound would be grabbing the soundcard for its use right when the desktop is loaded (so you can here the startup sounds and those "click-clicks").  This is why typing "killall esd" will allow XMMS to playback audio.  Essentially you're just telling esd to die and bugoff, and let XMMS's output grab the soundcard for use.  Yes, you'll lose all system sounds after doing so.

There are several methods to solve your problem.  The quick way is to let XMMS output use the system's sound sink.  But if you had an application that uses OSS output and you can't change it, you'll have to use "killall" again.

The better way is to follow [this guide](http://www.ubuntuguide.org/#configuresoundproperly).  Notice that you won't find this sound guide in the AMD64 version of the Unofficial Ubuntu Starter Guide, that's because the guide requires a package (libesd-alsa0) that is not available on AMD64. Fret not, luckily, we have our very own [AMD64 repository](http://tamir.nooms.de/wiki/doku.php).  Add our repository to your sources.list file, and you should be good to go.

> I tried Knopix, Guadalinux, Suse before and i have never a problem with sound. Really disappointed with Ubuntu in that aspect.
Ah...well hopefully the next version of Ubuntu brings the sound back on par with other distros...I was really bummed out to find out it was so hard to get sound working.  Even with the above sound guide, some applications still require some workaround to get sound working.  I think the goal is not only to get sound working but to work correctly.   For example, I know that right now, if you want to use the microphone AND listen to audio at the same time, it's not possible without more hacks.

---

### Post by Steve1961 on 2005-09-03
Since first posting I've since installed Ubuntu on two further PCs.  In both cases changing to the ESD sound daemon and following the how to originally given in:
 [http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon](http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon) 

solved the XMMS freezes.  However, At first I couldn't get any sound out of either machine - one had an onboard sis ac97 chip and the other a via ac97 chip.  I installed a cheap soundblaster card in one but still no sound untill I followed the instructions in this thread: 

[http://ubuntuforums.org/showthread.php?t=19307&highlight=soundblaster+24](http://ubuntuforums.org/showthread.php?t=19307&highlight=soundblaster+24).  

I then adapted this method for the other PC by first identifying the driver I needed on the alsa web site and then following along.  Worked first time!  Anybody else having problems with ac97 chips might find this useful.  Once I'd set esd i found I could also change to alsa if I wanted by following this how to:

[http://ubuntuforums.org/showthread.php?t=32063&highlight=gandalf](http://ubuntuforums.org/showthread.php?t=32063&highlight=gandalf)

and XMMS still worked.  However, the sound quality was very scratchy and full of feedback, so I switched back to ESD.

---

### Post by Scottcollins89 on 2005-09-03
i changed my output plug in to esound and it worked fine after that? with xmms!

---

