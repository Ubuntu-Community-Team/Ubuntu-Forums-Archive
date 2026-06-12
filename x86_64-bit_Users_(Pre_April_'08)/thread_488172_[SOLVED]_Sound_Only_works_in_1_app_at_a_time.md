---
title: "[SOLVED] Sound Only works in 1 app at a time"
date: 2007-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mr_bleu on 2007-06-29
I've checked the multimedia forums and did not find a solution to my problem.
I thought I'd try here as this is where I usually post.  I can't get sound to work in 2 apps at one time.  If I have a game playing and try watching a video or listening to music while a game is playing, Sound will only work on the first application opened.
Please advise.  I have built in sound on my notebook.  snd_hda_intel.

---

### Post by stmiller on 2007-06-29
This was a problem in OSS in recent history. But should not be an issue with ALSA, which is standard in Feisty. What applications are you using, specifically? The game may be using an oss-compatibility layer which could be the culprit.

---

### Post by Mr_bleu on 2007-06-30
Snes 9express + any other app that uses sound.

---

### Post by dabl on 2007-06-30
> **Mr_bleu said:**
>  I can't get sound to work in 2 apps at one time. 

Hmmmmm.  I'm trying to imagine the sound of two middle C's at the same time .....

Are you sure you can actually listen to two sound streams simultaneously, and appreciate either one of them?

:confused:

---

### Post by Mr_bleu on 2007-07-01
Yes, I have adhd.  I occupy my time doing various things.  Could this be causing it?:
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
I play spades online, for which I like to have sound.  While I'm waiting, I surf the 'net.  Sometimes I like to listen to music while I play spades, (I play in Hardwood spades, there are fooms and sounds to go with them).

---

### Post by dabl on 2007-07-01
OK, that's a reasonable story!  ;)

I did the following experiment on my system:

1. Start Amarok and start my favorite Madeleine Grey song from "Songs of the Auvergne"

2. In Firefox, start the mindless copter game at : [http://www.hurtwood.demon.co.uk/Fun/copter.swf](http://www.hurtwood.demon.co.uk/Fun/copter.swf)

Sure enough, even with Madeleine Grey singing, I can hear the crashes when my copter hits the deck. So, I guess the answer is "yes", in some situations you can have 2 sound sources working.  However, I am also aware that when I start Firefox, Audacity will refuse to play a sound file -- it claims to have no "output device". Shut down Firefox, and re-start Audacity, and it is OK.  So, I guess the answer is "it's complicated ...."

I'm set up as an ALSA sound system, on the Intel HDA system that is integrated on my motherboard.  I hope this helps a bit.  :)

---

### Post by tetrafuran on 2007-07-02
Interetingly enoug. I have pretty much the same situation. I started audacity and went on editing for a while. Then all of a sudden I got a message in gmail chat and after that the channel was owned by swiftweasel (browser) and I was unable to continue editing in audacity. gmail insisted on playing that stupid bling sound and that killed the sounds for audacity. VLC player was able play however. Strange. I've noticed the same thing in firefox and it was fixed just as you said. Stealing a channel never happened to me before. I some programs

How can I direct my programs to use different output "channels" so that I can edit sounds and still hear the occasional bling of swiftweasel or another communication software?

---

### Post by dabl on 2007-07-02
You're over my head with that last question.

Since I note that you have issues when using Audacity, and I have issues when using Audacity, I'm going out on a limb to suggest that there is some component of this problem that can attributed to limitations of Audacity, rather than limitations of the hardware or the OS.  Just a guess, but an informed one ...

:p

---

### Post by tszanon on 2007-07-03
I think it's a hardware related problem, because I had Dapper working in another computer and didn't have any problems playing simultaneous sounds. But, after I bought this new computer 6 months ago, I can never play more than 1 sound at a time. If xmms is playing and I run gnome-baker, xmms will refuse to play the next song, saying that the audio device is busy, or something like that.
Since then, I think it's because my hardware can't handle it.

---

### Post by tetrafuran on 2007-07-03
Actually it seems that audacity is to blame since for some pseudo-random reason it just looses the output device. In preferences the device is dev/dsp, however when the situation described above occurs, this area gets blank! It sounds like it's related to this specific software.

---

### Post by Mr_bleu on 2007-07-08
It was wine's settings.  I went to audio and changed it from oss to the alsa driver and hit apply.  I can now listen to music and play spades. :guitar::lolflag::popcorn::)

---

