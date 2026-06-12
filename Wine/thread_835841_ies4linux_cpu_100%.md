---
title: "ies4linux cpu 100%"
date: 2008-06-20
forum: Wine
---

### Post by casey.mynott on 2008-06-20
Hey everyone,

I know that this has been touched on before but I am in dire need of an answer. I have searched and cannot find a definitive solution to the CPU problems with the wineserver when running IE under wine. Does anyone have or know of a fix / hack to make IE quit completely when you close down a browser session. Thanks a ton! 

Casey

---

### Post by casey.mynott on 2008-06-22
:confused:

---

### Post by invenit on 2008-06-22
This seems to be a known problem. Check out the discussion at [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895) , esp. the most recent postings.

---

### Post by samandiriel on 2008-11-19
Had the same problem using the latest ies4linux on Ubuntu 8.10 (Intrepid). For me, the start up script fix did the trick.

I also found several rogue explorer.exe processes as well as IEXPLORE and winserver. After killing all these, modifying the script as above, and running the modified script I had absolutely no problems.

It looks like the script's piping to the debug is fouling things up; perhaps this was left in accidentally by the author during development.

script fix (credit Marc Davignon) from [http://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895](http://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895)
---------------------------------------------------------------
1) cd $HOME/.ies4linux/bin
2) cp -av ie6 ie6.orig
3) Replaced the content of the ie6 file with:
#!/usr/bin/env bash
# IEs 4 Linux script to run ie6 - [http://tatanka.com.br/ies4linux](http://tatanka.com.br/ies4linux)

cd
export WINEPREFIX="$HOME/.ies4linux/ie6"

wine "$HOME/.ies4linux/ie6/drive_c/Program Files/Internet Explorer/IEXPLORE.EXE" "$@" >/dev/null 2>&1 &

---

### Post by casey.mynott on 2008-12-02
Hey all,

I found some info here:

[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895)

The package found here:

[http://www.tolaris.com/apt/pool/main/w/wine/wine_1.0.0-2eitri1_i386.deb](http://www.tolaris.com/apt/pool/main/w/wine/wine_1.0.0-2eitri1_i386.deb)

did the trick.

No more wineserver issues! ;D

Casey

---

### Post by Orographic on 2008-12-06
I'm fairly new to Ubuntu, so what do I need to do here? Do I just install this link you provided?

I know how to install Wine and cabextract although i have re-imaged to a previous state where they are no longer installed.

---

