---
title: "another dvd problem..."
date: 2006-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by keenwerkz on 2006-04-13
hi i hope you wont get tired of this dvd issue... since every case presents differently on everyone... ok here's my story...

i started using kubuntu 5.04 i386 due to ease of installation/setup of multimedia thingies... i still get a bit of jerky dvd playback.. :( plus i dont have open office, gimp etc... :( so i decided to upgrade to ubuntu breezy (5.10 in i386).. installed all the necessary thingies... i was now having playback but still jerky video even w/ dma on... :( so i tried 5.10 in amd64 since i know there would be some noticeable improvements as some said... but this thing happened:

1. when i insert a dvd, it says something like it cant play device... :( this thing never happened to both my 5.10 and 5.04 installs but it happened with the dapper flight 5 install that i tried... but... i can play the dvd if i would go into the  video directory and queue the vob's manually... but i get far more jerky video than before plus scanlines... :(

here's my setup btw:

athlon 64 3000+
2 x 512 mb ram
120 gb SATA
nvidia 6600 pcie (latest driver installed)
LG GSA-4082B DVD Writer

i wanna stay w/ the amd64 setup since i have noticed a faster boot-up than the 32bit ubuntu counterpart... help.. :( 

thanx!

---

### Post by Efrain Valles on 2006-04-13
does it mention somhing about some libraires missing? post the error message...
Ihad similar Issues... I installed a library and that was it.

---

### Post by oscar on 2006-04-13
At the moment in dapper Totem cannot play dvds because the gstreamer packages aren't finished (or something?). Try using a different media player, I use gxine for dvds. In gxine File > DVD will play the dvd. [edit]I just checked and totem can play dvds now, not sure when that changed[/edit]

As for the jerky playback enabling dma should fix it. The important thing is to make sure that you do it for the right device. See  [https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA) for the howto. My dvd drive is recognised as /dev/hda for some reason. I'm not sure exactly how to find the device but /dev/dvd should work. 
For me:

```
oscar@oscarslaptop:~$ ls -l /dev | grep dvd
lrwxrwxrwx 1 root root           3 2006-04-13 19:21 dvd -> hda
lrwxrwxrwx 1 root root           3 2006-04-13 19:21 dvdrw -> hda
```

/dev/dvd is a link to /dev/hda

---

### Post by keenwerkz on 2006-04-13
no missing libraries error...

its just that:

cant open
dvd://


message. :(

---

