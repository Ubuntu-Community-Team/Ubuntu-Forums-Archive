---
title: "Crackling Sound in Wine!"
date: 2008-11-02
forum: Wine
---

### Post by KillaW0lf04 on 2008-11-02
Hey, i recently did a fresh install of Intrepid on my machine after using Hardy and installed wine as usual. 

When i was using hardy, i never had any sound problems, but when using Intrepid i get crackling sound, and noticeably slower performance as a result. Is anyone else experiencing this issue? The only difference i can think of is that this time im using PulseAudio (but i got the same cracking noise when i tried using ALSA).

Thanks in advance for any help

---

### Post by Faith912 on 2008-11-02
you must go to process manager and kill pulseaudio process, trust me :popcorn:

---

### Post by KillaW0lf04 on 2008-11-02
holy crap it worked lol What kind of weird bug is this? Thanks!

So this basically mean i should stop using pulseaudio and start using ALSA again? Damn, my USB mic seems to work better in pulseaudio :/ If anyone has a better solution please tell me! :)

---

### Post by Trap3d on 2008-11-02
hope this helps... and next time atleast check the first page if ur not using search... ;/
> This works if you are using 1.1.7. if any other it still might work if you have ever installed 1.1.7.
First you'll have to get rid of your current wine so do that.
**System > Administration > Synaptic packet manager**, there find wine and check complete removal, then go to home folder (**Places > Home folder**) and delete your .wine folder ([COLOR="Red"]**you might want to backup your games from that folder as when you delete it [SIZE="5"]they will be lost unless backuped[/SIZE]**[/COLOR])
Then remove every single thing related to your wine in the Software sources(**System > Administration > Software sources**)
Now all you have to do is install wine from your Add/Remove apps in Applications tab and voila you should have normal sound once again tought do not upgrade it to 1.1.7 let it stay 1.0.1.

---

### Post by Trap3d on 2008-11-02
hope this helps... and next time atleast check the first page if ur not using search... ;/
> This works if you are using 1.1.7. if any other it still might work if you have ever installed 1.1.7.
First you'll have to get rid of your current wine so do that.
**System > Administration > Synaptic packet manager**, there find wine and check complete removal, then go to home folder (**Places > Home folder**) and delete your .wine folder ([COLOR="Red"]**you might want to backup your games & apst and other stuff from that folder as when you delete it [SIZE="5"]they will be lost unless backuped[/SIZE]**[/COLOR])
Then remove every single thing related to your wine in the Software sources(**System > Administration > Software sources**)
Now all you have to do is install wine from your Add/Remove apps in Applications tab and voila you should have normal sound once again tought do not upgrade it to 1.1.7 let it stay 1.0.1.

---

### Post by KillaW0lf04 on 2008-11-02
oh so its a wine AND pulseaudio problem? Ill try this out. Thanks

---

### Post by Trap3d on 2008-11-02
oops double post sorry sum1 delete 1 of them....

---

### Post by Bios Element on 2008-11-02
Pulseaudio is what lets you system handle multiple audio streams from multiple programs at once. Without it, only one program can use a sound device at any given time. You want Pulseaudio.

Now what program is giving you the problem? I the program is using Alsa (Most are) Launch it using
```
padsp wine PROGRAM.exe
```
and if it's using OSS use
```
aoss wine PROGRAM.exe
```
to use pulseaudio. Now more then likely it's your Wine sound settings. So open up the wine config using
```
winecfg
```
and go to the audio tab.

Now you'll have to tinker with alsa or oss by selecting one and unselecting the other to see which one works better. But the directsound will make the most difference usually.

Generally, (Not always, this changes per program) You want Hardware acceleration to standard and Driver Emulation unchecked.

So if that doesn't help gimme an idea of the programs your having problems with and your current audio settings.

---

### Post by Trap3d on 2008-11-03
Bios trust me if hes uzing interprid that is almost 100% he has 1.1.7 wich is a 100% the easyest way is to reinstall wine 1.0.1 i had same problem

---

### Post by Eviljim on 2008-11-03
> **Trap3d said:**
> Bios trust me if hes uzing interprid that is almost 100% he has 1.1.7 wich is a 100% the easyest way is to reinstall wine 1.0.1 i had same problem

Spot on my friend, upgraded to 8.10 from 8.04 and WoW runs fine apart from the crackling sound.

Followed your instructions and it restored the sound. 
 :)

Why o why do the Wine people play around with stuff, causing more problems with each upgrade? meh who knows........

---

### Post by emlyn on 2008-11-15
I upgraded to wine 1.1.8 in order to install the WotLK expansion to World of Warcraft; using the standard repos version (1.0.?) causes a bug where the Accept button will never enable on the license screen during install, and the newer wine fixes that).

I then got the crackling sound that people are complaining about here (terrible). It appears to be a regression in ALSA and Wine, not sure exactly.

I don't want to go back to the old version of Wine. Instead, I found that using the OSS driver under Wine fixes this issue for me (use winecfg as Bios Element describes above). I have both ALSA and OSS ticked in the Audio tab, and now the sound works fine, just like magic.

HTH

---

### Post by Rich43 on 2008-11-16
Thanks! Killing pulseaudio process works!

Is there a fix for this that doesnt involve killing pulse?

---

### Post by Brynster on 2008-11-17
Yup the only way i got it sorted was to go back to wine 1.17 as 1.18 caused my head to hurt with the crackling sounds.

---

### Post by CoercibleGerm on 2008-11-19
> **Bios Element said:**
> Now you'll have to tinker with alsa or oss by selecting one and unselecting the other to see which one works better. But the directsound will make the most difference usually.

Generally, (Not always, this changes per program) You want Hardware acceleration to standard and Driver Emulation unchecked.

So if that doesn't help gimme an idea of the programs your having problems with and your current audio settings.

Switching to OSS completely uncrackles the audio for me. Sounds perfect now. \\:D/

---

### Post by iheartubuntu on 2008-11-24
> **CoercibleGerm said:**
> Switching to OSS completely uncrackles the audio for me. Sounds perfect now. \\:D/

Me too! woohoo

---

### Post by Brynster on 2008-11-25
If i switch to OSS i can have game sound and nothing else. Being a clan player in Counterstrike I cannot use OSS as I can have game sound and no skype or skype and no game sound. 

So simply dropping back to 1.17 works better for me :-)

---

### Post by Krank on 2008-11-25
I've been using the OSS workaround for a week or so (discovered it independently), but today, it suddenly stopped working after I installed a bunch of updates. None of the updates was wine, but there were like 129 of them and I can't seem to find a way to see "recently upgraded" packages anywhere...

I do seem to remember there was some kind of update for PulseAudio.

In hindsight, I should've known better. Never upgrade unless you need to.



So now I got crackling sound again. Killing the pulseaudio service just kills audio, period. Alsa works, ESD works, only OSS (the only crackle-free option) does not.

---

### Post by aasami on 2012-08-29
Searching for solution for this issue I came accross [_this thread_]("http://forum.winehq.org/viewtopic.php?t=12917") on wine forums that solved my problems with crackling sound.

> edit /etc/pulse/daemon.conf

find and set these two from
default-fragments = 8
default-fragment-size-msec = 10

to
default-fragments = 24
default-fragment-size-msec = 100 

or quickly
```
sudo sed -i -e '/^default-fragments = /s/8/24/'\
 -e '/^default-fragment-size-msec = /s/10/100/' /etc/pulse/daemon.conf
```

This saved my day. I hope it helps someone.
Cheers Aas.

---

### Post by LillyDragon on 2012-08-29
Old topic is old. =P

Anyway, this fix did nothing for me after a logout. My sound in WINE still pops and crackles, possibly even more consistently than before. ;_; I think WINE is still overwhelming PulseAudio.

---

