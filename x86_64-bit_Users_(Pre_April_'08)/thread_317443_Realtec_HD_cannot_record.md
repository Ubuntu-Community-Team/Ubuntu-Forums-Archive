---
title: "Realtec HD cannot record"
date: 2006-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by radiobuzzer on 2006-12-12
Hello, I am using Ubuntu Edgy, on a three-months old laptop of ACER, AMD64 x2. My sound card is detected by Windows as Realtec HD. I have the following problems in Linux

[LIST]
[*]Right balanced sound! When Ubuntu starts, only the right speaker works. If I go to the mixer and play with the balance, after two or three times I move the bars, the sound gets balanced to both speakers. I tried to solved this, but using a rexima command in one of the scripts, but it was the one that works only when I get into the terminal. I will have to find the init script that works when I get to gnome 
[*]The worst problem is this one: I can't get sound in! Microphone and line in gives no input to programs such as Audacity, Ekiga etc, so I have to log in to Windows in order to make recordings and talk to VoIp phone. 
If this helps, Windows appears to recognise the sound card as TWO devices. When I try to record, I have to select as a device the Realtec HD Sound IN and when I play the Realtec HD Sound out.
[/LIST]

Has anybody experienced similar problems? I work for radio, so sound is really important for me

---

### Post by fabertawe on 2006-12-13
As regards the balanced sound, try
```
sudo alsactl store 0
```
once you've got it balanced to store mixer settings. It should stick hopefully, no guarantees though!

Paul

---

