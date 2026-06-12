---
title: "lightscribe?"
date: 2007-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by nonewmsgs on 2007-05-06
i know there was a lightscribe program in automatix for i*86, but i dont remember the name.  i would prefer a 64bit one but ill take what i can get.

---

### Post by tgm4883 on 2007-05-06
lightscribe 4 linux

---

### Post by John Jason Jordan on 2007-05-06
> **tgm4883 said:**
> lightscribe 4 linux
Where is that? I can't find it in Automatix for Feisty amd64, nor do I find anything when I search in Synaptic for "lightscribe." I have all the repositories enabled, I think. Or do I have to download a .deb and install from the command line?

---

### Post by Enverex on 2007-05-06
> **John Jason Jordan said:**
> Where is that? I can't find it in Automatix for Feisty amd64, nor do I find anything when I search in Synaptic for "lightscribe." I have all the repositories enabled, I think. Or do I have to download a .deb and install from the command line?

You probably need to download the source for it from their website, compile it then install it to use it. Google got a few hits for me, none of them named "LightScribe 4 Linux" though...

---

### Post by tgm4883 on 2007-05-06
arg, the program is called 4L and it is put out by Lacie

---

### Post by Enverex on 2007-05-06
Heh, so it was the first hit then. [http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)
Have fun installing JJJ.

---

### Post by Mau on 2007-05-06
Do you need special disks to use LightScribe or can you use any old CD-R?

---

### Post by Shay Stephens on 2007-05-06
You have to use lightscribe disks if you want to burn a label.

---

### Post by John Jason Jordan on 2007-05-06
> **Enverex said:**
> Heh, so it was the first hit then. [http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)
Have fun installing JJJ.
OK, I went there, but I had a couple problems. First, nowhere did it say if it would work on amd64 Linux. Second, when you click to download the labeler it pops up a black window which calls a video player. I refuse to have a video player in my browser, so that was the end of that. What on earth possessed them to think I wanted to view a movie in order to download their driver.

And the host software link is broken -- no download window pops up or anything else. 

Now that I know it is "4L" maybe I can find it somewhere else.

---

### Post by Enverex on 2007-05-06
Erm, in that case you have a weird setup. Clicking either of the links for me went to a download page where you could download either of the programs (they are in RPM format). God knows why it was opening a media player for you...

---

### Post by John Jason Jordan on 2007-05-06
> **Enverex said:**
> Erm, in that case you have a weird setup. Clicking either of the links for me went to a download page where you could download either of the programs (they are in RPM format). God knows why it was opening a media player for you...
Problem solved. Turns out my laptop thought "RPM" was a video format. :)

But I wanted it on my desktop anyway, so I downloaded with Firefox there and then it popped up a download window. It still identified it as a video file, though. :)

Do I have to use alien on these things if I have Feisty amd64?

Edit: Alien doesn't work. It pukes up a bunch of errors that appear to boil down to the fact that amd64 is not in the RPM's list (i386). I could install an i386 deb of it with --force-architecture, but I can't seem to create the deb file.

---

### Post by Detonate on 2007-05-06
If, for some reason, you are trying to download a "rpm" and your browser tries to open it with a media player, you can just click on File>Save Page As and it will download the file.  BTDT.   It would occasionally happen to me when I was using Fedora, which is a rpm based distro.

But I don't know what to suggest about your problems with Alien, I've never used it.

---

### Post by John Jason Jordan on 2007-05-06
> **Detonate said:**
> ... I don't know what to suggest about your problems with Alien, I've never used it.
I just need someone with 32-bit Ubuntu to use alien to convert them to debs. I don't understand why LaCie didn't bother to offer them as debs as well as rpms. Like it would have taken them five minutes.

---

### Post by Mongoose on 2007-05-07
Use a i386 chroot -- you'll likely need one for the lightscribe too.  The last person I knew to use it on amd64 ran it from a chroot, and if you were skilled enough to setup the app for lib32 you wouldn't have to ask for help with alien.  ;)

I made some debs for that several months ago, but they're likely out of date.

---

### Post by pitmansm on 2007-08-19
i have the same issue i really want lightscribe to work  but im not bright enough to figure it out ive really look in alotta places. anyone? gotit to work if so remmebr how you did it? i did that wheel thing and all that. i dont know what that did etc..

---

### Post by John Jason Jordan on 2007-08-19
> **pitmansm said:**
> i have the same issue i really want lightscribe to work  but im not bright enough to figure it out ive really look in alotta places. anyone? gotit to work if so remmebr how you did it? i did that wheel thing and all that. i dont know what that did etc..
I finally got it working in Feisty amd64. The details are in another thread. I didn't save the bookmark, though. Just search on recent posts by me.

And after all that it turns out it does black and white only. Therefore, I am no longer intereested.

---

### Post by rsambuca on 2007-08-20
> **John Jason Jordan said:**
> I finally got it working in Feisty amd64. The details are in another thread. I didn't save the bookmark, though. Just search on recent posts by me.

And after all that it turns out it does black and white only. Therefore, I am no longer intereested.

Didn't you know that lightscribe is grayscale only by design?

---

### Post by hikaricore on 2007-08-21
> **rsambuca said:**
> Didn't you know that lightscribe is grayscale only by design?

:lolflag:

*goes off to write udev rules so he doesn't have to run 4L-gui as root*

I'll share em here if I actually get around to it.  :p

---

### Post by groeswenphil on 2007-08-21
Have you ever tried making a Lightscribe label in Windows?
Personally, I'm totally underwhelmed with the system.
Even for the most simple design it takes at least half an hour to print the label onto the CD or DVD.
Even after that time, results are disappointing, looking rather like what you would see from a very old photocopier......unless I'm doing something wrong.

I've had it for six months now....I think I've used it four times.
In my opinion, the pen is mightier than a Lightscribe DVD drive.
Good luck,
Phil

---

### Post by Shay Stephens on 2007-08-21
> **groeswenphil said:**
> Have you ever tried making a Lightscribe label in Windows?
Personally, I'm totally underwhelmed with the system.
Even for the most simple design it takes at least half an hour to print the label onto the CD or DVD.
Even after that time, results are disappointing, looking rather like what you would see from a very old photocopier......unless I'm doing something wrong.

I've had it for six months now....I think I've used it four times.
In my opinion, the pen is mightier than a Lightscribe DVD drive.
Good luck,
Phil

It takes about 14 minutes for me to burn a label, but I have a new drive.  I make the label with a template I made in Photoshop so it is pretty fast to make a label and save it and then open it in the lightscribe program.  I made sure to design the template to take advantage of the lower contrast output of the drive, so the results looks complementary and I am happy with it.  If you try to make a high contrast design look good you might not be satisfied.

---

### Post by tgm4883 on 2007-08-21
> **Shay Stephens said:**
> It takes about 14 minutes for me to burn a label, but I have a new drive.  I make the label with a template I made in Photoshop so it is pretty fast to make a label and save it and then open it in the lightscribe program.  I made sure to design the template to take advantage of the lower contrast output of the drive, so the results looks complementary and I am happy with it.  If you try to make a high contrast design look good you might not be satisfied.

I've used mine alot, I found that to make it darker, you can "burn" the lightscribe side more than once.  I have done that it makes the image much darker (well, twice as dark or 3 times as dark if you do it a third time) and that makes it look much much better.  You can take the disk out in between burns if you want to see how it looks, it starts in the right place no matter if I take it out or leave it in between multiple burns.  This is in an HP 840i

---

### Post by Shay Stephens on 2007-08-22
That is good to know, thank you!

---

### Post by rsambuca on 2007-08-22
That is very intersting.  I have never tried it before.  I am curious as to how the burner aligns the disc so that it writes in the same orientation.  Very cool!

---

### Post by swisscow on 2007-08-25
Just read on wikipedia that there is some code on the disc which tells the writer the alignment of the disc in the drive......clever stuff

---

### Post by stinger30au on 2007-08-25
gee whiz, thats a lot of stuffing round to get a neat label on the disc.
either get a colour inkjet printer you can feed your discs thru or a "stomper" type package that you feed sticky labels thru the printer and stick to the disc. can be done way faster then 15 minutes like the lightscribe does to burn a label, plus full colour rather then grayscale

---

### Post by jamesford on 2007-08-25
no amd64 deb for this stuff yet?
ive got a lightscribe burner, never tried it tho.

---

