---
title: "direct rendering for ATI 128 rage pro on iMac"
date: 2006-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by jasonli on 2006-02-14
Hi,

I have just compiled a mplayer CVS on my own, hiahia!

But the rmvb files played really really bad, the video is way too slow. So i checked glxinfo and it said direct rendering: no.

I guess there is something wrong with my ati driver, how can i turn the direct rendering on?

I am using: iMac G3 500, 128ram, 8m ATI 128 rage pro, ubuntu 5.10

Thanks a lot for teaching a beginner!

---

### Post by scottlpatterson on 2006-02-14
Here is the workaround for Dapper Flight 3 (perhaps this will help):

[https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz]("https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz")
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/29543]("https://launchpad.net/distros/ubuntu/+source/xorg/+bug/29543")

---

### Post by jasonli on 2006-02-15
[QUOTE=scottlpatterson]Here is the workaround for Dapper Flight 3 (perhaps this will help):

[https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz]("https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz")
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/29543]("https://launchpad.net/distros/ubuntu/+source/xorg/+bug/29543")[/QUOTE]
So, in dapper, still we have to refrain from using the full depth of color to use the 3d acceleration? I am a little disappointed, though.

---

### Post by scottlpatterson on 2006-02-15
I'm not sure. I read another thread where dropping the bit depth from 24 to 16 enabled direct rendering. So, I did that and it worked. Whether or not it's a limitation of the card and memory I don't know.

---

### Post by jasonli on 2006-02-16
[QUOTE=scottlpatterson]I'm not sure. I read another thread where dropping the bit depth from 24 to 16 enabled direct rendering. So, I did that and it worked. Whether or not it's a limitation of the card and memory I don't know.[/QUOTE]
You did that on an iMac or iBook? I tried to lower the depth of my iMac but it didn't work.

---

### Post by Lanrond on 2006-02-16
[QUOTE=jasonli]You did that on an iMac or iBook? I tried to lower the depth of my iMac but it didn't work.[/QUOTE]

Same here. :(

---

### Post by scottlpatterson on 2006-02-17
iBook. Sorry guys, I didn't read close enough:(

---

