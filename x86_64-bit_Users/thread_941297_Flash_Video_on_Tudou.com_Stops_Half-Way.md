---
title: "Flash Video on Tudou.com Stops Half-Way"
date: 2008-10-07
forum: x86 64-bit Users
---

### Post by nordrasor on 2008-10-07
I watch a lot of streaming video on Tudou.com (Most shows stay up fairly indefinitely without being removed for Copyright issues, probably because it is based in China) but am forced to use Vista to do so. When I try to watch videos on Tudou (usually 21sh min) they usually skip to the next video on the playlist at the exact same point, roughly 25% through the video. 

I've experienced this issue on both flash 9.0 and 10 rc. I'm running 64 bit Ubuntu on an AMD64 based system. 4 GB RAM. I've tried fiddling with the right click menu and increasing the cache size to unlimited for the tudou movie player but have had fairly limited success. Any ideas? I've switched back and forth between flash 9 and 10 several times to try and resolve the issue. Flash 9.0 performs pretty badly due to choppy full screen playback so I've been using rc 10 as of late.

---

### Post by patrickballeux on 2008-10-08
Hi,

Have you tried different browsers (Opera, Epiphany)?  I don't know what Firefox does, but somethings is wrong with Flash and Firefox 3.x...

Here is what I do:

I installed in Firefox "Download Helper" (FF plugins) who is able to detect the video file downloaded by Flash.  So I start the movie, wait a little and download the FLV with Download Helper.  And to be really fast, I copy/paste the URL of the file, open a terminal and execute "wget THE_URL_OF_THE_FILE".  It will download like 4 or 5 times faster.

When the first part is downloade, I start watching it in Totem or Mplayer.  No lag, no surprise.

I almost dropped Firefox for Epiphany which is lighter and cleaner.  I keep Firefox for those sites that requires IE or Firefox.

Good luck!

---

### Post by nordrasor on 2008-10-08
The addon seems to help, thanks.

---

