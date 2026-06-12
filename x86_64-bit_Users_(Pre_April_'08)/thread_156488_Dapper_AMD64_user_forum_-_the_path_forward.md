---
title: "Dapper AMD64 user forum - the path forward"
date: 2006-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by skylark on 2006-04-07
Hi all,

After using both Hoary and Breezy AMD64 editions as my main desktop for the past year I've come across many issues that 32-bit users don't face. Hopefully with Dapper the situation will improve a bit. I think we can also help out in a small way by building a better AMD64 user forum for Dapper.

One idea I've had is simply to include some "stickies" in the forum. These would act to guide users to frequent problems, commonly used HOWTOs and FAQs particular to the AMD64 distribution.

Stickies might include:
* Problem applications
  - here we could list programs which either don't work or have issues, sudivided by whether they are available in the main Ubuntu repository or in Universe or are 3rd party etc. For example in Breezy we have discovered GnomeBaker fails to burn DVDs, copy and paste into OpenOffice is flaky, Celestia doesn't seem to load properly etc etc I'm sure we will run into similar issues in Dapper.
* Setting up Firefox with MacroMedia Flash & Sun Java HowTo
  - or at least a link to a wiki page on this
* Setting up a 32-bit chroot for wine (and potentially Flash in Firefox etc)
* Playing media files
  - since we don't have a "win64codecs" it is more difficult for AMD64 users to play all their media files (eg latest quicktime, windows media) [I've resorted to playing some of my files with 32-bit Totem-xine in a chroot, maybe there are better ways?].
* Video driver HowTo for ATI and NVidia (might only be needed if there are any specific AMD64 issues with these...).

I'm sure you all have better ideas than me, I just thought I'd post this as a starter for discussion :-D

---

### Post by henriquemaia on 2006-04-07
[QUOTE=skylark]Hi all,

After using both Hoary and Breezy AMD64 editions as my main desktop for the past year I've come across many issues that 32-bit users don't face. Hopefully with Dapper the situation will improve a bit. I think we can also help out in a small way by building a better AMD64 user forum for Dapper.

One idea I've had is simply to include some "stickies" in the forum. These would act to guide users to frequent problems, commonly used HOWTOs and FAQs particular to the AMD64 distribution.

Stickies might include:
* Problem applications
  - here we could list programs which either don't work or have issues, sudivided by whether they are available in the main Ubuntu repository or in Universe or are 3rd party etc. For example in Breezy we have discovered GnomeBaker fails to burn DVDs, copy and paste into OpenOffice is flaky, Celestia doesn't seem to load properly etc etc I'm sure we will run into similar issues in Dapper.
* Setting up Firefox with MacroMedia Flash & Sun Java HowTo
  - or at least a link to a wiki page on this
* Setting up a 32-bit chroot for wine (and potentially Flash in Firefox etc)
* Playing media files
  - since we don't have a "win64codecs" it is more difficult for AMD64 users to play all their media files (eg latest quicktime, windows media) [I've resorted to playing some of my files with 32-bit Totem-xine in a chroot, maybe there are better ways?].
* Video driver HowTo for ATI and NVidia (might only be needed if there are any specific AMD64 issues with these...).

I'm sure you all have better ideas than me, I just thought I'd post this as a starter for discussion :-D[/QUOTE]

When this new forum opens, count me in. This is something I'm really looking forward.

---

### Post by maury on 2006-04-07
Count me in also. I'm running the latest beta on a spare drive and it runs well. The only real issues are not having Flash and a ubuntu_64 ver. of gnofin which  I use to keep track of my finances. I'm hopeing more packages will be ported to amd-64 soon.

---

### Post by rkerstetter on 2006-04-08
I look forward to participating in Dapper amd64 discussions.  I am very impressed so far, and will do my best to shed some light if and where I can.

---

### Post by BjornHaland on 2006-04-08
Whatever you do, have an organized sticky with strict rules:

* ONLY well tested methods that work for top x problems
* NO chat, direct to a child thread
* Jump/Anchor list to each possible approach
* Standards for post layout, eg. #1: Jump tags on top, #2: etc #3: etc
* External links well tested and found to be non-confusing and explanatory

= Happy customers :)

(these are of course only examples, just wanted to advocate the need for a good layout)

---

### Post by Robocoastie on 2006-04-08
I'd like to know why simply compileing apps from source doesn't make them work in 64 bit. Isn't that the supposed strength that Gentoo touts? Perhaps there's something about the process that I don't understand.

---

### Post by WelterPelter on 2006-04-11
Can't wait.

---

### Post by Adler on 2006-04-18
Count me in also.

---

### Post by jdusablon on 2006-04-18
Robocoastie:
> I'd like to know why simply compileing apps from source doesn't make them work in 64 bit. Isn't that the supposed strength that Gentoo touts? Perhaps there's something about the process that I don't understand.
Just converting the code into 64bit isn't enough. There exists the problem of system resources and drivers which are not only 64-bit, but also in most cases set up differently. Also, 64bit OSes map memory differently.

Basically, the whole thing is different, not just the application code.

---

### Post by sparker on 2006-04-21
The Gentoo 64bit team provide firefox-bin and mplayer-bin, statically compiled at 32bit. With this packages we can use the flash-plugin and the win32codecs.

---

### Post by mschievano on 2006-04-21
count on me.
no java, w32codecs and ati X1600 driver for my dapper amda 64 4200+ X2 now ](*,)

---

### Post by Jazzyjazz on 2006-04-21
Same here, missing some nice stuff out there. Looking forward to find a solution to it :-k

---

### Post by s_spiff on 2006-04-26
ok i'm in too.. but before that, I've still to resolve my present issue [ posted as 'from 32 to 64..how? ]... also.. can i install a 32 bit OS on my new 64 bit without hassles?

---

### Post by mschievano on 2006-05-01
ati driver now ok:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.24.8_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.24.8_drivers_in_Ubuntu_Dapper_Manually)

---

