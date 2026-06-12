---
title: "CrossOver for Linux"
date: 2007-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by groeswenphil on 2007-08-21
Hi Group,

Has anybody managed to get CrossOver or Wine to work using an AMD64?
If I could get one of these to work, THEN get my Ubuntu computer to use Microsoft Publisher 97, my life would be more or less complete.

Any advice?
Phil

---

### Post by zsouthboy on 2007-08-21
Both CrossOver and Wine work just fine on AMD64.

What problems do you have exactly?

---

### Post by groeswenphil on 2007-08-21
Well, actually at the moment I haven't got a problem.
I tried installing WINE some time ago and it didn't like my AMD64.
How should it be installed?
All the best,
Phil

---

### Post by tgm4883 on 2007-08-21
> **groeswenphil said:**
> Well, actually at the moment I haven't got a problem.
I tried installing WINE some time ago and it didn't like my AMD64.
How should it be installed?
All the best,
Phil

Probably the best way to install it in AMD64 is from the repo.  Look at the winehq site for details.

---

### Post by groeswenphil on 2007-08-22
OK I managed to get Crossover to install.
I can get it to work from Terminal, but it isn't showing in my application list.
Ho do I get it to show there?
Phil

---

### Post by groeswenphil on 2007-08-22
Crossover now FULLY FUNCTIONAL :O)

Tried Wine and got this

~/Desktop$ sudo dpkg --force-architecture -i wine_0.9.43~winehq0~ubuntu~6.06-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package wine.
(Reading database ... 134418 files and directories currently installed.)
Unpacking wine (from wine_0.9.43~winehq0~ubuntu~6.06-1_i386.deb) ...
Setting up wine (0.9.43~winehq0~ubuntu~6.06-1) ...

So...........does that mean I've succeeded?
Phil

---

### Post by sawjew on 2007-08-22
You don't have to force-architecture for wine anymore, there are 64bit packages available in the wine repository.  Just go here [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb") and follow the directions then ```
sudo apt-get install wine
```

If you want it to be a little easier to set up you can go here [http://www.wine-doors.org/wordpress/]("http://www.wine-doors.org/wordpress/") and download the deb package for wine-doors which will set up and configure wine for you and can install a lot of packages very easily.  Unfortunately Publisher is not supported yet but MS Office is coming.

I have Publisher XP (2002) installed via Crossover Office but I haven't tried it on wine yet.

---

