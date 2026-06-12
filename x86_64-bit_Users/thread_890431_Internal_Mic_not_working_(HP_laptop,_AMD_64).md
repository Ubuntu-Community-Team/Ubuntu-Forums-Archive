---
title: "Internal Mic not working (HP laptop, AMD 64)"
date: 2008-08-15
forum: x86 64-bit Users
---

### Post by opr8ive on 2008-08-15
hello, hello..

Trying to get either one of my internal mics working on this laptop, so far, no go..

The story so far: A mic plugged into the front panel mic-in works fine, all other audio seems to work fine, Heck even my Lexicon Lambda USB A/D works! just cant get the internal mics to work (There are 2 of them about  8" apart on my screens top border.. Dunno why two?)

Volume settings show a set of sliders for internal mic in the playback tab (Set to 100%, and unmuted) but the only set of sliders in the "Recording" tab day "Digital" (also unmuted, and set to 100%)

lspci |grep Audio returns:  00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

Any thoughts?
Thanks!

-Jason

---

### Post by opr8ive on 2008-08-19
-bump-

I hate doing this (bumping), but Id really like to get this working, and thought someone somewhere might have some ideas..

Mods:  If you feel this has a better chance elsewhere in the forums, Please feel free to move it..

Thanks!

-Jason

---

### Post by rchar66 on 2008-08-20
I've got the same problem with my mic's on my HP laptop to.

By the way, there are two of them because it's in stereo. one left and one right, that also match the two sliders.

I can't even get the an external mic to work on mine.

What settings do you have set for the audio?

By the way, My laptop is the HP DV9910us.

Richard

---

### Post by cespinal on 2008-08-20
This is a waaaaaay old problem. Myself and some other guys bumped similar threads for weeks without getting a solid solution for this. 

The only think I can suggest you to do is to go to Terminal, type "alsamixer" and try to boost up the volume for the mic. 

Somehow the alsamixer's configuration for some HP laptops just doesnt not allow you to use the mic. It seems that it does not recognizes it. 

*subscribes to thread* I hope there's a solution for this now..

---

### Post by rchar66 on 2008-08-20
Thanks, I'll give that a try and see if it helps the problem. When I try to test the mic, it does seem as if it is trying to record. Just that it's having trouble picking up audio.

Also, do you know what the third type of mic is in the Audio settings? There are sliders for three different mic's; internal, which I believe are the mic's next to the web cam, external, which I believe is the front mic jack. Then there is a third one called docking mic.

What is that?

Richard

---

### Post by niyonk on 2008-08-20
I also have a similar problem, so one day i decided not to stop until I found a solution, believe me you are asking nothing but big headaches and a big pain in the rear.

My advice to you is...just don't find a solution unless you are REALLY, really desperate.
I've heard some people got it working...you might be lucky, but I warn you that you will likely be disapointed :(

Search the forums and good luck! :)

---

### Post by opr8ive on 2008-08-20
What kind of response is that? :-k I have searched the forums at great length, as well as google, and come up with no solution. Thanks for that insightful, and shockingly appropriate answer. :-?

Anyway, I too have the docking mic slider, all I can think of is its a mic on the docking station so you still have a built-in mic even while the laptop is docked (and probably closed)

My laptop is the dv9920us, so I think we pretty much have the exact same hardware.
.
alsamixer shows internal mic, set to 100% and unmuted..

Sigh. Ill keep looking

-Jason

---

### Post by cespinal on 2008-08-20
> **rchar66 said:**
> Thanks, I'll give that a try and see if it helps the problem. When I try to test the mic, it does seem as if it is trying to record. Just that it's having trouble picking up audio.

Also, do you know what the third type of mic is in the Audio settings? There are sliders for three different mic's; internal, which I believe are the mic's next to the web cam, external, which I believe is the front mic jack. Then there is a third one called docking mic.

What is that?

Richard

That is exactly what my own experience leads to...just static :lolflag:

Moreover, I also have these 3 sliders that just wont work. 

My laptop is dv9000 as well so it seems we are still pretty much on the same boat...

---

### Post by cespinal on 2008-08-21
> **opr8ive said:**
> What kind of response is that? :-k I have searched the forums at great length, as well as google, and come up with no solution. Thanks for that insightful, and shockingly appropriate answer. :-?

Despite I share your pain and frustration, I don't share your sarcasm. Please try to be politer when we are not able to support you accordingly. 

Thanks.

---

### Post by rchar66 on 2008-08-21
Well.......at any rate.........I'm going to keep looking to find an answer/fix to this problem.

It's just in my nature to keep looking and hacking until it's fixed.

I'll post a fix if I figure it out.

Thanks to all for all you help and comments so far.

Richard

---

### Post by opr8ive on 2008-08-21
> **cespinal said:**
> Despite I share your pain and frustration, I don't share your sarcasm. Please try to be politer when we are not able to support you accordingly. 

Thanks.
Sorry.. Just the wrong post on the wrong day in the wrong mood.

But statements like ".just don't find a solution unless you are REALLY, really desperate"
and  "I warn you that you will likely be disapointed" Aren't exactly encouraging  let alone helpful.

So, Niyonk, Im sorry if I jumped on ya, but if you could post links / references to those you've heard about "getting it working" That would be most appriciated.

Thanks

-Jason

---

### Post by niyonk on 2008-08-22
Hi, I did search for keywords like 'hp microphone' 'hp mic' 'pavilion internal mic/microphone' and so on...

I say it was really hard to find a solutions because most of the time you will have to compile this and that (mainly drivers) and none worked...

will post links as i get them back...

UPDATE: you asked for it...:biggrin: (i went back through my internet history)

[http://ubuntuforums.org/showthread.php?t=255071](http://ubuntuforums.org/showthread.php?t=255071)
[http://ubuntuforums.org/showthread.php?t=385739](http://ubuntuforums.org/showthread.php?t=385739)
[http://ubuntuforums.org/showthread.php?t=701647](http://ubuntuforums.org/showthread.php?t=701647)
[http://ubuntuforums.org/showthread.php?t=622383](http://ubuntuforums.org/showthread.php?t=622383)
[http://ubuntuforums.org/showthread.php?t=284336](http://ubuntuforums.org/showthread.php?t=284336)
[http://ubuntuforums.org/showthread.php?t=788531](http://ubuntuforums.org/showthread.php?t=788531)
[http://ubuntuforums.org/showthread.php?t=765971](http://ubuntuforums.org/showthread.php?t=765971)
[http://ubuntuforums.org/showthread.php?t=791760](http://ubuntuforums.org/showthread.php?t=791760)
[http://www.tomshardware.com/forum/28945-35-pavillion-microphone-problem](http://www.tomshardware.com/forum/28945-35-pavillion-microphone-problem)
[http://forums.opensuse.org/archives/sf-archives/hardware/laptop-support/343495-hp-laptop-microphone.html](http://forums.opensuse.org/archives/sf-archives/hardware/laptop-support/343495-hp-laptop-microphone.html)
[http://www.tomshardware.com/forum/28945-35-pavillion-microphone-problem](http://www.tomshardware.com/forum/28945-35-pavillion-microphone-problem)
[http://forum.notebookreview.com/showthread.php?p=3579923](http://forum.notebookreview.com/showthread.php?p=3579923)
[http://clet.blogspot.com/2008/02/microphone-on-ubuntu-gutsy-and-hp-6710s.html](http://clet.blogspot.com/2008/02/microphone-on-ubuntu-gutsy-and-hp-6710s.html)
[http://bbs.archlinux.org/viewtopic.php?id=51324](http://bbs.archlinux.org/viewtopic.php?id=51324)
[http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/)

believe me i have way more but i will end up double posting :lolflag:
In the End, my advice to you was...just deal with the fact that ALSA sucks :(
If you have any of the cards that are mentioned, then you are lucky.
As for me i have conexant CX20561 (Hermosa) which you will see mentioned in the links.

---

### Post by aodhan on 2008-09-23
Hello All,

This article may be the answer to the Mic issue raised on HP laptops.

[http://nxadm.wordpress.com/2008/04/28/microphone-on-ubuntu-804/](http://nxadm.wordpress.com/2008/04/28/microphone-on-ubuntu-804/)

Simply follow these steps...it worked for me, but I am a novice with Ubuntu...10 years with Solaris

To fix it, just right click on the speaker icon in the top menu, choose “Open Volume Control”, go to Edit-Preferences and click on “Capture”. A new tab “Recording” will appear on your settings. If the microphone icon is disabled, click it to enable it. That’s it.

Hope this helps, please update if it does .. or not.

---

### Post by Sickafant on 2008-10-22
The last post didn't work for me. But I was able to fiddle with alsamixer settings and get my mic to record.

What I had to do was to press space over the capture mixers to make them have "L   R CAPTUR" in red written underneath. Then I pumped up their volumes. 

I then set the first Digital mixer to about 75 percent. Too high and there would be a lot of distortion and feedback. The next "Digital" option, "Digital Input Source" should be set to "Digital". Then the last Digital mixer should be set to 0, otherwise causing distortion and feedback again. 

The "Input source" should be set to Mic. The second one had no effect, but I assumed it had to do with the alternate mic port on the front, so I set it to Front mic. I have no mic to test it though.

[IMG]http://i34.tinypic.com/2rw7ux5.png[/IMG]

I realize these settings are specific to my machine, which is an HP DV5-1008, but hopefully this will help someone.

---

### Post by ellannjohnson on 2008-12-22
> **aodhan said:**
> Hello All,

This article may be the answer to the Mic issue raised on HP laptops.

[http://nxadm.wordpress.com/2008/04/28/microphone-on-ubuntu-804/](http://nxadm.wordpress.com/2008/04/28/microphone-on-ubuntu-804/)

Simply follow these steps...it worked for me, but I am a novice with Ubuntu...10 years with Solaris

To fix it, just right click on the speaker icon in the top menu, choose “Open Volume Control”, go to Edit-Preferences and click on “Capture”. A new tab “Recording” will appear on your settings. If the microphone icon is disabled, click it to enable it. That’s it.

Hope this helps, please update if it does .. or not.

Thanx for the help. Fixed my  mic issues.:P

---

### Post by niceguy123 on 2009-02-08
> **cespinal said:**
> This is a waaaaaay old problem. Myself and some other guys bumped similar threads for weeks without getting a solid solution for this. 

The only think I can suggest you to do is to go to Terminal, type "alsamixer" and try to boost up the volume for the mic. 


Wow, this really helped me with my plug-in mic that was recording real low. But, I am still not getting voice though on Skype.

---

