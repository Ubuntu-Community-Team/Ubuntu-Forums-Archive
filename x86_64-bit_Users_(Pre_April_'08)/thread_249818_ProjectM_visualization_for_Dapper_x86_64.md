---
title: "ProjectM visualization for Dapper x86_64"
date: 2006-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by nephre on 2006-09-03
Hi

For all these guys having problem with compiling projectM and libvisual-projectM on 64-bit Dapper, I've created pre-compiled packages.

Use ftgl-dev_2.1.2-2ubuntu3_amd64.deb if you want to compile projectM yourself (tested on projectM version 0.99). This one fixes problem with relocation error with ftgl (or something, don't remember ;))

libprojectM and libvisual-projectM are precompiled and working on my computer. I don't give any warranty if it fails elsewhere. Install both to use in amaroK.

Possibly, you'll also have to install libvisual-0.4.

---

### Post by WattoDaToydarian on 2006-09-17
What about debs for Dapper i386:confused:

---

### Post by nephre on 2006-11-24
> **WattoDaToydarian said:**
> What about debs for Dapper i386:confused:

I've created debs for amd64 version of projectM, because there is a problem with compiling it on standard installation on dapper (something with ftgl, don't remember), and I've not found these packages anywhere. Unofficial debs for projectM i386 exist, so you just have to look for them, or compile projectM yourself. It's as easy as ./configure && make && make install

---

### Post by bluevincent on 2006-11-29
Awesome, thanks mate this was really making me pull my hair out :)

---

### Post by svapunk on 2007-07-09
Merci pour les .deb en amd64 c'est cool je n'arrivai pas à compiler!

j'obtenai : /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libprojectM.la] Erreur 1
make[2]: quittant le répertoire « /home/svapunk/libprojectM/src »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/svapunk/libprojectM »
make: *** [all] Erreur 2

Thank you for the deb in amd64 they is cool I did not manage to compile!

I have :/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libprojectM.la] Erreur 1
make[2]: quittant le répertoire « /home/svapunk/libprojectM/src »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/svapunk/libprojectM »
make: *** [all] Erreur 2

[presets.zip]("http://www.milkdrop.co.uk/Downloads/Milkdrop_1.04_Source.zip")

svapunk

---

