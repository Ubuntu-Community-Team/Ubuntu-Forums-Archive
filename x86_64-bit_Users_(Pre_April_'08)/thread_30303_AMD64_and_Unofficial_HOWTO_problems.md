---
title: "AMD64 and Unofficial HOWTO problems"
date: 2005-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by makis on 2005-04-28
Hi all,

There is a perfect [unofficial HOWTO]("http://www.ubuntuguide.org/") out there but with in some cases with little support for amd64 processor. I do not complain, there is a lot of work done in this HOWTO, and much more that has to be done.

However, I have to notice the howtos do not work yet:
acrobat reader
flash player (macromedia does not support amd64 plugins yet)
w32codecs
RAR archiver

THE PROBLEM WITH _MPLAYER_ IS SOLVED. Follow the instructions given in the [HOWTO]("http://www.ubuntuguide.org/#mplayer") and Instead of:

**sudo apt-get -t hoary install mplayer-386**

type in the console the following:

[b]sudo apt-get -t hoary install mplayer-amd64

[/b]after that, follow the rest 2 steps as they are given in the [HOWTO]("http://www.ubuntuguide.org/#mplayer")

It is interesting that this is the only way to install mplayer-amd64. If you try via synaptics you will face problems with some libraries dependancies:

**libc6, libfontconfig1, libvorbis0a** etc

If someone knows how to solve other problems for amd64 in this HOWTO, especially with acrobat reader (7.0 or previous) let me know.

Thank you

---

### Post by jiyuu0 on 2005-04-28
sad to say that i have only got the resources to test on x86 and not others...

currently workin on the ubuntu add-on cd... 

once complete will start porting ubuntuguide to the official doc format... then maybe other ppl can gave input on other architectures...

---

### Post by heimo on 2005-04-28
jiyuu0, let me use this opportunity to bow deep and thank you for the enermous effort and great contribution to Ubuntu community. That guide is awesome and seems like that's not only thing you're working on. Thank you*.
 
=D>
 
 
 
*) These thanks apply to everyone involved.

---

### Post by hack_benjamin on 2005-04-28
the libdvdcss2 howto didnt work for me.. how did you get yours?

---

### Post by makis on 2005-04-28
[QUOTE=hack_benjamin]the libdvdcss2 howto didnt work for me.. how did you get yours?[/QUOTE]

I didn't! Because of that problems with the new editions of these libraries, I gave an advice for MPlayer. If you try to intall or upgrade MPlayer via synaptics you will see that you cannot do it. But manually, you can, and all the important libraries are installed automatically.

---

### Post by arbearce on 2005-04-28
Do you mean that you couldn't find it or that it didn't install?

To find it I had to add
```

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

``` 

to /etc/apt/sources.list 
then get the gpg for them.
If I remeber right it's the unstable repo that has the amd64 packages.

After that I had dvd playing in kaffeine. Sometimes you have to turn on dma for hdc with
```

sudo hdparm -d1 /dev/hdc

``` 
where hdc equals your dvd/cdrom drive.

---

### Post by makis on 2005-04-28
[QUOTE=hack_benjamin]the libdvdcss2 howto didnt work for me.. how did you get yours?[/QUOTE]

if you try in the terminal the code:

**sudo upt-get install  libdvdcss2** 

may you copy/paste terminals feedback??

---

### Post by makis on 2005-04-28
[QUOTE=jiyuu0]sad to say that i have only got the resources to test on x86 and not others...

currently workin on the ubuntu add-on cd... 

once complete will start porting ubuntuguide to the official doc format... then maybe other ppl can gave input on other architectures...[/QUOTE]

I want also to thank you my friend. I think you have done a perfect job, and I have underlined that in my comments. I deeply appreciate your work!!;-)

---

### Post by Drain on 2005-05-16
I was wondering if anyone has come up with a better solution to the problem mentioned in this thread yet: [http://ubuntuforums.org/archive/index.php/t-28241.html](http://ubuntuforums.org/archive/index.php/t-28241.html)

Otherwise, the unofficial howto has been working great on my server... Good job with the libdvdcss2 solution!

---

