---
title: "ivtv-tune on tune one channel"
date: 2007-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by manjo on 2007-03-09
I am trying to use ivtv-tune to tune to different broadcast channels, I have 4 broadcast channels (US) but I am able to get signal only on one channel, if I use my TV set I can tune all 4, but IVTV sees signal on only one channel. 

manjo@sleepy:~$ ivtv-tune -c 36 /dev/video0
/dev/video0: 295.250 MHz
manjo@sleepy:~$ ivtv-tune -c 7 /dev/video0
/dev/video0: 175.250 MHz  (Signal Detected)
manjo@sleepy:~$ 

I know that 36 is a valid channel 


[http://en.wikipedia.org/wiki/List_of_television_stations_in_Texas#Austin](http://en.wikipedia.org/wiki/List_of_television_stations_in_Texas#Austin)

Any suggestions ?

---

### Post by manjo on 2007-03-10
any suggestion  ?

---

### Post by kdub432 on 2007-04-28
I am having a similiar problem.... 
I can tune VHF frequencies (channels 1-13 or whatever) 
but not UHF frequencies (14+)              

(i may have gotten UHF and VHF mixed up there, correct me if  i'm wrong...)

I'm gonna look into exactly what the right frequency table should be.....

---

### Post by kdub432 on 2007-04-28
Alright. 
Sorry for one post right after the other....

use

ivtv-tune -tus-bcast -c62

(that tunes to channel 62.....)

---

