---
title: "Hoary64 state"
date: 2005-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by kagou on 2005-03-27
I'v tested hoary64 but i'v switch to 32 due to lack of features.
Can we make a point without using CHROOT :

Can I install jre of sun ?
Java under firefox ?
Flash under firefox ?
Encrypted DVD playing ?
DVD writing ?
ATI 3D drivers ?
graveman under hoary 64 ?
BLender/Yafray ?

Thx

---

### Post by fjleal on 2005-03-27
[QUOTE=kagou]
Can I install jre of sun ?
Java under firefox ?
Flash under firefox ?
Encrypted DVD playing ?
DVD writing ?
ATI 3D drivers ?
graveman under hoary 64 ?
BLender/Yafray ?
[/QUOTE]

There's a Sun JRE 1.5 version available for amd64 processors. It runs fine, but it has no plugin available for Firefox.  :(
There's no Flash client available for amd64 machines yet. (Will it ever be?...)
You can compile Blender from source,  no problem.

Don't know about the other ones... ;)

---

### Post by negatory on 2005-03-27
You can use the blackdown java version for the amd64 plugin download the jre or jsdk [here](http://www.blackdown.org/java-linux/java-linux-d2.html).Encrypted dvd playing you can download it at marillats at [his ftp](ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-amd64/) but I haven't had much success at it with media player.DVD writing works just fine with me using k3b.

Hope I could help.
Pedro Carrico

---

### Post by kagou on 2005-03-27
[QUOTE=negatory]You can use the blackdown java version for the amd64 plugin download the jre or jsdk [here](http://www.blackdown.org/java-linux/java-linux-d2.html).Encrypted dvd playing you can download it at marillats at [his ftp](ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-amd64/) but I haven't had much success at it with media player.DVD writing works just fine with me using k3b.

Hope I could help.
Pedro Carrico[/QUOTE]
Are you sure that dvd writing is ok ? or just cd writing ?

Thx for all responses

---

### Post by fdoving on 2005-03-27
[QUOTE=kagou]Are you sure that dvd writing is ok ? or just cd writing ?

Thx for all responses[/QUOTE]
 I'm sure dvd writing is ok. I use it all the time.

---

### Post by negatory on 2005-03-27
DVD and CD writing work "out of the box"!No issues there!

Pedro Carrico

---

### Post by wmcbrine on 2005-03-27
For encrypted DVDs, I built libdvdcss from source, no problems. (Except that it defaulted to /usr/local/lib, which wasn't in /etc/ld.so/conf -- fixed.)

I'm about to test dvd writing with the 32-bit closed-source binary of cdrecord-prodvd, which I'll be copying over from my other distro. I'll let you know how it goes.

So far, I'm just blowing off Flash and Java. Not much use anyway, and if I ever do need them, I can boot to my 32-bit distro. I can't speak to the other apps, and I don't have an ATI card.

---

### Post by wmcbrine on 2005-03-27
Yep, cdrecord-prodvd works fine. Oh, the reason I'm using it is that the other tools didn't work for me, back when I first got my DVD burner. But that's been a couple years (and nothing to do with 64-bit), so I'll try them again.

---

### Post by MarsDude on 2005-04-01
[QUOTE=kagou]I'v tested hoary64 but i'v switch to 32 due to lack of features.
Can we make a point without using CHROOT :

Can I install jre of sun ?
Java under firefox ?
Flash under firefox ?
Encrypted DVD playing ?
DVD writing ?
ATI 3D drivers ?
graveman under hoary 64 ?
BLender/Yafray ?

Thx[/QUOTE]
- jre , use the one from blackdown, they have a 64bit deb, and a plugin with the 1.4 version,  you might have to install java-common first.

- java plugin , yes the 1.4 blackdown has it.. ln -s it to the /usr/lib/mozilla-firefox/plugins dir (remove the link that is allready there, if it points to something in /etc )

- flash... there is no 64 bit macromedia plugin ... go complain to macromedia ;-) there is gplflash, which isn't really a complete solution yet (only older flash support and crashes your firefox a lot)

- encrypted dvd playing , install (if you haven't yet) libdvdread3 .. go to /usr/share/doc/libdvdread3/examples/ and ./install-css.sh which downloads css , compiles it and makes a deb and installs it.

- dvd writing ... this should be no problem either (you mentioned graveman)

- graveman... yes it's there... in universe

---

### Post by Pse on 2005-04-07
ATI's 3D drivers for AMD64/Linux are not THAT good, but usable. I can play Enemy Territory and UT2004 at playable framerates without lowering quality with a low-end card. Though, you may want to install a chroot to run most 32-bit games, as it's a bit hard to make them run under a 64-bit system (due to libs and stuff).

---

### Post by c_dog on 2005-04-09
[QUOTE=Pse]ATI's 3D drivers for AMD64/Linux are not THAT good, but usable. I can play Enemy Territory and UT2004 at playable framerates without lowering quality with a low-end card. Though, you may want to install a chroot to run most 32-bit games, as it's a bit hard to make them run under a 64-bit system (due to libs and stuff).[/QUOTE]

That's kind of interesting becuase I've had better luck getting the 64-bit Nvidia drivers to install far more easily then their 32-bit drivers on Hoary.

---

### Post by WMCoolmon on 2005-04-09
Has anyone figured out a way to get Cedega working? I've tried using linux32 with the WineCVS script available from linux-gamers, but have just gotten errors.  No one has replied anywhere else on the forums where I've asked about it; and yeah, I have googled/searched (How I found the linux32 command).

I can post the errors here, if that would help.

---

