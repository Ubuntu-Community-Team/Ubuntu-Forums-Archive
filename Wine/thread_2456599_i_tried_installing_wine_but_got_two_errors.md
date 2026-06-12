---
title: "i tried installing wine but got two errors"
date: 2021-01-15
forum: Wine
---

### Post by stonksdev on 2021-01-15
i am new to linux and have no idea what to do
these are the errors i got:

ibosmesa6 i386 20.2.6-0ubuntu0.20.10.1 [2,688 kB]
Get:317 [http://ubuntu-archive.mirrors.estointernet.in](http://ubuntu-archive.mirrors.estointernet.in) groovy-updates/main amd64 libosmesa6 amd64 20.2.6-0ubuntu0.20.10.1 [2,569 kB]
Fetched 304 MB in 5min 2s (1,007 kB/s)                                         
E: Failed to fetch [http://ubuntu-archive.mirrors.estointernet.in/pool/main/m/mpg123/libmpg123-0_1.26.3-1_i386.deb](http://ubuntu-archive.mirrors.estointernet.in/pool/main/m/mpg123/libmpg123-0_1.26.3-1_i386.deb)  Error reading from server - read (104: Connection reset by peer) [IP: 2403:8940:3:1::f 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by CelticWarrior on 2021-01-16
Welcome.

Please post the full error messages. It seems you've been adding PPAs that don't support your release (20.04). Better NOT do that if you don't know what you're doing. And how does it relate to Wine isn't at all clear. Exactly what instructions have you been following?

---

### Post by mastablasta on 2021-01-19
also - why do you need wine? what do you intend to use it for?

Have you tried Play on Linux that offers a GUI interface? It's not just for games.

Also if you intend it for games i would suggest to try Proton from Steam or if you need latest wine to run the game, then try Lutris.

For Epic games there is now also Heroic games launcher.

---

### Post by Kris_M on 2021-02-23
> **mastablasta said:**
> also - why do you need wine? what do you intend to use it for?

Have you tried Play on Linux that offers a GUI interface? It's not just for games.

Also if you intend it for games i would suggest to try Proton from Steam or if you need latest wine to run the game, then try Lutris.

For Epic games there is now also Heroic games launcher.

So wine is broken? I was just trying to install wine on Mint Mate and/or Cinnamon and winetricks throws:
 [COLOR=#000000][FONT=Liberation Serif][SIZE=3]sha256sum mismatch! Rename /home/kris/.cache/winetricks/directx9/directx_feb2010_redist.exe and try again[/SIZE][/FONT][/COLOR]

---

### Post by mastablasta on 2021-02-24
no it's not broke. that error says something doesn't match - for example downloaded file is of different size as it should be. as the error says rename or remove that specific file and try again.

> [COLOR=#000000][FONT=&quot]sha256sum mismatch! [/FONT][/COLOR]

means downloaded file was checked against the one on server and it is not the same.

---

### Post by Kris_M on 2021-02-24
> **mastablasta said:**
> no it's not broke. that error says something doesn't match - for example downloaded file is of different size as it should be. as the error says rename or remove that specific file and try again.



means downloaded file was checked against the one on server and it is not the same.

yes, which of course I did many times to no avail.

I did find an obscure note somewhere that seemed to say don't add directx to wine as it already has it included. This is apparently very new. There is no documentation about it that I found.  However, I was still unable to get this particular app to run, but that could well be for other reasons since wine never really tells you why something is getting an exception error, or the like - it's just try to guess which dll or whatever needs to be added. I will see if I can get it going with a VM......

---

### Post by mastablasta on 2021-02-24
an implementation of directx is there but sometime this is not enough and sometimes native libraries are still needed. it also depends on GPU and what kind of support is available for it (for new tech -  vulcan etc.)

how are you installing directx? you can also do it manually - download directx9 and install it. 

what application do you actually want to install? sometime wine version can be used and you just add one or two native libraries to system folder and it works.

---

