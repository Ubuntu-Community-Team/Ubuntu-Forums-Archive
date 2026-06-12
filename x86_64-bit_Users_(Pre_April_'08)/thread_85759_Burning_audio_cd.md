---
title: "Burning audio cd?"
date: 2005-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jason-X on 2005-11-03
Hi all

I have been using Gnomebaker to create audio cd's from mp3's in Hoary. I am now using Breezy which is great apart from not being able to burn audio cd's.

[[IMG]http://img476.imageshack.us/img476/9075/audiocd2vu.th.png[/IMG]](http://img476.imageshack.us/my.php?image=audiocd2vu.png)

Basically the problem is when I drag the selected mp3's into the audio cd panel in gnomebaker, the tracks display as about 20% the time of what the track should be (see screenshot). Also when I try to burn the cd of the offchance that it may work I get this error from the terminal:

> ** (gnomebaker:5629): CRITICAL **: gst_audioscale_link: assertion `caps' failed

I have also tried Serpentine. The track times appear correct this time, but it still fails to burn and I get this error:

> Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/serpentine/converting.py", line 71, in start
    self.__oper = self.__pool.fetch_music (self.__music)
  File "/usr/lib/python2.4/site-packages/serpentine/converting.py", line 194, in fetch_music
    oper = audio.sourceToWav (source, sink)
  File "/usr/lib/python2.4/site-packages/serpentine/audio.py", line 339, in sourceToWav
    bin = gst.parse_launch (
GError: could not link audioscale0 to wavenc0

Does anybody have any idea what could be going wrong here?

Many thanks
Jason:confused:

---

### Post by farruinn on 2005-11-03
Have you tried this with a multitude of files? Perhaps rip some new files and try to burn then?

---

### Post by Jason-X on 2005-11-03
I have tried with loads if different files. Some downloaded and some encoded by myself. Still no joy.

---

### Post by Jason-X on 2005-11-04
hmmmm...... I tried K3B and it worked! Also it seems about 5 times faster than gnomebaker to encode and burn. 

I guess i will be sticking with K3B from now on:)

---

### Post by farruinn on 2005-11-06
Sadly, since gnomebaker etc. on gnome are fairly new, they don't quite compare with k3b.  Have you filed a bug against this?

---

### Post by Jason-X on 2005-11-07
I must admit I have never filed a bug before so I'm not sure how to go about this.

I'll have a go later when I get home from work.

---

### Post by farruinn on 2005-11-07
Sorry, I should have provided some links.  Since gnomebaker is in Universe file you can file the bug at [https://launchpad.net/products/gnomebaker/+bugs](https://launchpad.net/products/gnomebaker/+bugs).

---

