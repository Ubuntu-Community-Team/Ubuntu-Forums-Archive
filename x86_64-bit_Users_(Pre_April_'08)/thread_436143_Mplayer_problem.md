---
title: "Mplayer problem"
date: 2007-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ev1L on 2007-05-07
I report this problem here too.
I installed MPlayer from automatix, but the suggestions they gave me on their support forum didn't solve the problem.

i get this error when i try to open any movie:
error opening/initializing the selected video_out (-vo) device

I've been suggested to:
Please open up /etc/mplayer/mplayer.conf as root
CODE
sudo gedit /etc/mplayer/mplayer.conf

and change the following line
QUOTE
#vo=xv

to
QUOTE
vo=xv

save and close the file
and check if the error still remains.
If it does, change the same line to:
QUOTE
vo=x11

and save the file and test again.


I did but nothing again...

any other idea?

thanks

---

### Post by bailewen on 2007-05-07
ttt

I'm getting the same thing.

---

### Post by Cappy on 2007-05-07
Right click on the video and click "preferences". Click the "Video" tab. Try "gl". Click ok. If that doesn't work try other drivers until it works.

---

### Post by Ev1L on 2007-05-08
the right one was xv.

thank you very much!

---

### Post by mwales on 2007-05-10
Seems like the first time I install MPlayer and go to use it I got that error too.
I think the following will fix it too:

mplayer -vo xv <some_random.avi>

It then remembers what the video output driver is.

---

