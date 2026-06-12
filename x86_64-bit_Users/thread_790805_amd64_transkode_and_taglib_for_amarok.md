---
title: "amd64 transkode and taglib for amarok"
date: 2008-05-11
forum: x86 64-bit Users
---

### Post by firecat53 on 2008-05-11
In case anyone is interested, I've uploaded .deb versions of taglib and the transkode extension for amarok (you need both) for amd64, as the version in Amarok is only for x86. People have had trouble compiling these, and I've used these on both gutsy and hardy without any issues. I'm really not an expert on compiling and creating packages, so I hope these work for other people's machines too! If there are any problems, let me know and I'll see if I can help.

Transkode is a nice extension that lets you both transcode automatically when loading up a music player or right click (from Amarok) and transcode files on your computer. 

To install:
   sudo dpkg -i taglib*deb
   sudo dpkg -i trankode*deb

   Run amarok, select Tools -> Script Manager
   You should see Trankode in the list of scripts. Highlight transkode, then select run, and then configure. Make sure the naming scheme is set under the profiles section -- that's the location your files will end up. It's a little confusing at first to get it all configured right. You may also have to install oggdec, oggenc, faac, faad, lame, ffmpeg, mplayer, flac, or other programs to transcode certain formats. After you install the appropriate programs, just shutdown and restart amarok so it will recognize the programs for transkode.

Good luck!
Scott

---

### Post by Ashex on 2008-06-14
Thanks for posting these!

---

### Post by doorknob60 on 2008-09-19
Nice, I couldn't get it to compile on Intrepid because it includes KDE4, and there wasn't a package for the KDE 3 dev files, and this seems to be working fine :)

---

### Post by earlycj5 on 2008-09-24
Thank you very much for posting these!

---

### Post by xen-uno on 2008-11-23
=D> =D> =D> =D> =D>

I was beating my head against the wall trying to get the source to compile ... muchos gracias as it installed and works perfectly. I thought setting the Simultaneous Jobs option of transkode to 2 might spread the encodes to each proc of a dual core ... according to Sys Monitor it doesn't. Time to hit rarewares for optimized encoders/decoders.

---

