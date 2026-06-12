---
title: "Motherboard change."
date: 2007-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by eddieb on 2007-07-04
Hi, I have just this minute changed my Motherboard and upon booting Ubuntu refuses to boot into the Desktop. It goes into a text screen and I honestly don't know what to do.
The original M/B had a Nvidia card and now the new board has an onboard video.
Funny thing is that Puppy boots perfectly.
Any help would be greatly appreciated.
Cheers,
Eddie.

---

### Post by kuja on 2007-07-04
You probably need to reconfigure X. Try running the command "sudo dpkg-reconfigure xserver-xorg -phigh"

---

### Post by mattyrigby00 on 2007-07-04
you probably need to change the video drivers in x to the ones from the onboard video. you should be able to install the drivers for the onboard video from the "text screen" if it officially supports ubuntu

---

### Post by eddieb on 2007-07-04
Hi MTFYR. I tried that and got this: Xserver-xorg-phigh is not installed.

---

### Post by jespdj on 2007-07-04
Note the space between "xserver-xorg" and "-phigh".

---

### Post by eddieb on 2007-07-04
Jespdj your blood should be bottled. And MANY thanks to all who helped.

---

