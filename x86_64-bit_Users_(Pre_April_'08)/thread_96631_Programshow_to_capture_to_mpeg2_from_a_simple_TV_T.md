---
title: "Programs/how to capture to mpeg2 from a simple TV Tuner Card???"
date: 2005-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by CyberAngel on 2005-11-29
Hi, I have a Pinnalce PCTV Stereo TV Tuner card and I want to be able to capture from TV programs (or S-Video) directly to mpeg2 format so I can burn them later to DVD`s.
In windows there are many programs that doing this job but in linux the only one I found is xdtv. The problem now is that I haven`t managed to get xdtv work correctly in (k)ubuntu. I had work with it and I was able to capture in mpeg2 directly in Slamd64. In the record options there were a lot of codecs that it was able to capture in (mpeg2, mpeg4, xvid and many others), but this was on slamd64. Now that I have tried to install it on kubuntu, in the recording options my only choice is to capture video Uncompressed......
Where the choice for all the other codecs gone!!! :confused: :confused: 
I`ve installed it using the following repositories:

> #xdtv
deb [http://xawdecode.sourceforge.net/debian-amd64/](http://xawdecode.sourceforge.net/debian-amd64/) binary/
deb-src [http://xawdecode.sourceforge.net/debian-amd64/](http://xawdecode.sourceforge.net/debian-amd64/) source/


Can anyone please help me???
Or can anyone suggest me another program or anyway tell me how can I do the above mentioned with any other other way in linux and especially ubuntu?

---

### Post by Joeb on 2005-11-29
You might check out Myth TV ([www.mythtv.org)](www.mythtv.org)).  I haven't used it personally, but I have heard that others speak very highly of it.


Joeb

---

### Post by dsauter on 2005-11-29
I use MythTV, and nothing else compares.  The following link will take you to the guide I used to get it installed on Breezy:

[http://www.abarbaccia.com/component/option,com_frontpage/Itemid,1/](http://www.abarbaccia.com/component/option,com_frontpage/Itemid,1/)

Andrew (of abarbaccia.com) did a great job of making the install process straightforward, although I don't know what problems you might have to figure out on your own since you aren't using the Hauppauge cards.  The following link has lots of great information, which might help you with non-Hauppauge cards (although it's geared toward Fedora):

[http://wilsonet.com/mythtv/fcmyth.php](http://wilsonet.com/mythtv/fcmyth.php)

I hope you give Mythtv a shot.  It's the single reason that I switched to Linux, and because of it, I now see all the other reasons to stay.

---

### Post by CyberAngel on 2005-11-29
Thanks for your replys gyus. I`ll try mythtv and I`ll post my progress here.
Do you know if it is able to capture direct in mpeg2 as I asked above?

---

### Post by dsauter on 2005-11-29
If the capture card encodes it, it will.  If not, MythTV will record it and then use transcode in the background to change it to something else (it isn't a quick process, but it runs at a very low priority so it doesn't slow other things down at all).  There are several choices that transcode can change it to and I'm sure mpeg2 is one of them.

For example, the PVR250 capture card I use has on-board encoding to mpeg2.  When MythTV recordes from it, it records an mpeg2 file (although it names it with a .nuv extension).  From there it is pretty easy to get it to a CD or DVD.  I can even rename it with a .mpg extension and get it play on windows.

---

### Post by CyberAngel on 2005-12-07
Back with very good news :)

I am so happy :KS :) 
I found some repositories that has many many packages (amd64 packages) that does not exist in official repositories.
I found avidemux (that i couldn`t compile it), ffmpeg with full support for everything (again I had problems with recompilation) and a perfect xdtv compilation that supports every codec for capture!!

I love you all :p :p 

Here are the links:
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
[http://debian.video.free.fr/](http://debian.video.free.fr/)
[http://spello.sscnet.ucla.edu/marillat/dists/sid/main/binary-amd64/](http://spello.sscnet.ucla.edu/marillat/dists/sid/main/binary-amd64/)
[http://spello.sscnet.ucla.edu/marillat/dists/sarge/main/binary-amd64/](http://spello.sscnet.ucla.edu/marillat/dists/sarge/main/binary-amd64/)


and here are the repositories I have added to my sources.list:
deb [http://spello.sscnet.ucla.edu/marillat/](http://spello.sscnet.ucla.edu/marillat/) sid main
deb [http://spello.sscnet.ucla.edu/marillat/](http://spello.sscnet.ucla.edu/marillat/) sarge main


As for Mythtv I haven`t try to install it yet cause the packages in official repositories are broken and I didn`t had the time to try it on my own. I will try it some time. :) 
I had compiled it in slamd64 and it was so beautiful but with many problems.... (possibly beacause of my own compilation)

Thanks gyus :D

---

