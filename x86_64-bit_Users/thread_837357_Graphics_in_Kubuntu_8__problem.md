---
title: "Graphics in Kubuntu 8  problem"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by joni b on 2008-06-22
Hi everyone, hope you all had a good weekend :)


I am a new Kubuntu8 user and I'll be grateful if anyone could  help me with these problems encountered in this great  operating system:



After installing Kubuntu 8.04 remix 64bit ( kde 4)  choosing safe graphics because normal leads  to video distortion, I've not been able to change the colour ( i.e. from 16-32 bits) and as a result the display is blotchy( not smooth as in say, XP.

Im not sure how to , and  if installing the official Linux graphics driver would help any.

The  graphics is  "VIA Chrome9 HC IGP " ( integrated with the Asus P5VD2-VM SE motherboard.





Note: The Kubuntu 8.04 i386 version , though allows for adjusting the the resolution and even selecting the graphics card make , crashes and refuses to boot or log in when changed.

---

### Post by pixel :-) on 2008-06-22
After installing ( kde 4) 
kde4 is still in development install kde3.in aterminal

 sudo apt-get install kubuntu-desktop

The graphics is "VIA Chrome9 HC IGP " ( integrated with the Asus P5VD2-VM SE motherboard.
If the kde3 gui tool,is crashy.You'll need to edit /etc/X11/xorg.conf
for this ask at [http://ubuntuforums.org/forumdisplay.php?f=332]("http://ubuntuforums.org/forumdisplay.php?f=332").This is not 64 bit specific,you'll have faster responces there.

crashes and refuses to boot or log in when changed.
When this happens chose the "recovery mode" from the boot menu,it will give you some usefull options.

---

### Post by joni b on 2008-06-23
Thanks Pixel.

  I tried that to no avail.
Oddly enough, I installed Mandriva (which is very  stable with pre-installed graphics drivers), and it works like  a dream- the GUI is lovely too.I cant beleive how good this os  is ...its brilliant :)

---

