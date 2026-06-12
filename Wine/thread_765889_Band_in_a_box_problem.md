---
title: "Band in a box problem"
date: 2008-04-24
forum: Wine
---

### Post by tonymoloney on 2008-04-24
Is this the best place to discuss problems with Band in a Box on Wine, or does someone know of a more suitable forum?
I've searched for Band in a Box but got no hits, but I am aware from the Band in a Box forum that some BIAB users have installed BIAB on Wine.

---

### Post by tubunu on 2008-04-25
I can confirm that BIAB runs fine with wine. Ubuntu 7.04, will be doing an upgrade to Hardy in a moment though. What problems do you have?

---

### Post by tonymoloney on 2008-04-26
Sorry it took so long to reply - living on the other side of the world and all that.
I installed BIAB 2006 on my system and it works OK except for a couple of strange things.
All the text beneath the toolbar buttons looks like it's written in an alien language. However, when I hold the mouse over the button, the hint box is written in normal English text.
Also, all of the styles and style types are written in the same weird text, whilst the style description is written normally.
I can enter chords, go into notation and enter notes and print the whole lot out as usual, but the weird text just slows things down.
I haven't been able to get any sound out yet, but I'm working on it - MIDI is not the easiest thing to get going in Ubuntu. I did get MIDI working once but seem to have lost it again!

---

### Post by guayabound on 2008-12-29
Ever get BiaB 2006 to work? I just installed it too and it loads okay...but I also get no sound.

Thanks,
Joe

---

### Post by guitarrastan on 2009-04-20
hi..i've also this problem..any suggestions??
to tonymoloney: have you fixed the problem??
please help me!!

---

### Post by guayabound on 2009-04-20
No, unfortunately not :(

Please post here if you find one. Supposedly it works, so there must be some little trick that I am missing.

---

### Post by Kareeser on 2009-04-20
Is BIAB a midi-playback program? If so, you'll need to install TiMidity

```
sudo apt-get install timidity
sudo /etc/init.d/timidity restart
```

The second line of code stops Timidity from stealing sound focus from PulseAudio.

---

### Post by guitarrastan on 2009-04-20
timidity works..i still have the problem with the language..
and not only with band in a box..
noone knows how to fix it??

---

### Post by NightMKoder on 2009-04-20
Is this what you're talking about? [http://ubuntuforums.org/showthread.php?t=974111](http://ubuntuforums.org/showthread.php?t=974111) 

If not, post a screenshot (alien doesn't exactly satisfy a problem description)

---

### Post by The Caller on 2009-05-02
> **Kareeser said:**
> Is BIAB a midi-playback program? If so, you'll need to install TiMidity

```
sudo apt-get install timidity
sudo /etc/init.d/timidity restart
```

The second line of code stops Timidity from stealing sound focus from PulseAudio.

Thanks for this timely advice.

---

### Post by Kareeser on 2009-05-02
As for font problems, you may have to install the package "msttcorefonts".

---

