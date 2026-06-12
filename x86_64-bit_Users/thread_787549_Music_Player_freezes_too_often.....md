---
title: "Music Player freezes too often...."
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by indikid on 2008-05-09
Hi, I'm using the Gutsy Gibbon version of Ubuntu and it seemed to be working fine so far. But of recently I ran into problems, whenever I try to play a music file on any of the media players the player freezes. This has turned out to be very annoying and frustrating! Music is my stress buster and I find it hard to survive without it... Can someone help me resolve this issue please...

---

### Post by NightwishFan on 2008-05-09
That is a very odd issue. Try to run a player with the terminal so I can see what the error is.

```
rhythmbox
```

---

### Post by indikid on 2008-05-09
> **NightwishFan said:**
> That is a very odd issue. Try to run a player with the terminal so I can see what the error is.

```
rhythmbox
```
Jus tried that.... rhythmbox opens but when I try to play a music file it freezes.... Its the same with VLC and movie player too...

---

### Post by NightwishFan on 2008-05-09
:)

Whats the error in the terminal?

---

### Post by indikid on 2008-05-09
There was no error. I typed the code in and pressed enter. Rhythmbox player opende. Then I clicked on file > import file > - selected the track i wanted to play (mp3) and clicked ok. The file was queued in. now the problem starts here. Once i hit the play button the player freezes. They are those odd times when the player plays the track but when the track comes to an end the player freezes and does not move to the next song queued in... I've tried to click on the play button again but the entire window is frozen by then. any idea whats wrong here??? I'm so lost now... :(

---

### Post by NightwishFan on 2008-05-09
It won't say why it is freezing? Odd.

---

### Post by indikid on 2008-05-09
I'm not sure if I'm doing this the right way. I'm kinda new to linux and ubuntu... Could you give me a step by step guide - If its not much of a bother- for this please???

---

### Post by NightwishFan on 2008-05-09
Press Alt+f2
type:
```
xterm
```
Then type in the window:
```
rhythmbox
```
Do not close the terminal. When you press play and it crashes it should report the problem in the terminal, paste the output here.

---

### Post by indikid on 2008-05-09
Jus tried doing what you suggested. rhythmbox jus froze when I pressed play. Nothing appeared in the terminal. The light on my cpu was still flickering so guess the system was working but real slow though. I left it that way for 20mins. Nothing happen. Jus reinstalled rhythmbox now, updating it.... Hope this works out. Problem is, movie player is also behaving the same... :( Hey, thanks for all the help... Btw, do u think this is a problem with the Brasero disk burning apps? Had installed that before this glitch... Uninstalled it but still have the problem...

---

### Post by RuarriS on 2008-05-09
Codec problem maybe?

---

### Post by funrider on 2008-05-09
have you tried clearing your current playlist? that worked for me last time when i ran into a similar problem.

---

### Post by indikid on 2008-05-12
I'v cleared my current playlist and reinstalled all gstreamer codecs but Movie layer and VLC freeze as soon as I add a track to them... I've unistalled rhythmbox...

---

### Post by indikid on 2008-05-14
Hey guys,i desperately need help on this. I still haven't got my multimedia working on my Ubuntu 7.10. Rhythmbox and Movie player stop responding as soon as i load a track in them. I've already reinstalled the codecs and both players but things are still the same.... :confused: any ideas on this....? Thanks in advance...

---

