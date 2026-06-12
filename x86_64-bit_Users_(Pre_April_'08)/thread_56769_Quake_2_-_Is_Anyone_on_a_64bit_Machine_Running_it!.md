---
title: "Quake 2 - Is Anyone on a 64bit Machine Running it!?"
date: 2005-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by hammett111 on 2005-08-14
Hi, this is a rant and question time post.

I have tried the loki installer for Quake 2. It comes with the demo bundled in it, which you can install, and the option to install the full version at a later date. My rant is this. After the install I type ./quake2 and this horror comes up:

Console initialized.

------- sound initialization -------
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so") failed: ./ref_softx.so: cannot open shared object file: No such file or directory
Refresh failed
recursive shutdown
Error: Couldn't fall back to software refresh!
-> Red  1.300, Green  1.300, Blue  1.300
<- Red  1.000, Green  1.000, Blue  1.000
quentin@andromeda:~$

I have trawled all the Quake sites and many possibilities have been trialled. Here they are. :? 

**FIRST** I had installed quake2 into my home directory, NO NO NO!! you shouldnt do this install it to /usr/local/games/. I did this and still the same error. ](*,) 

**SECOND** Curiously the loki installer does not come with a bunch of required files which can be found in the following package "quake2-snd.tar.gz". These files included my dearly beloved missing "ref_softx.so." So installed to the correct location /usr/lib/games/quake2, ref_softx.so and all his buddies......and....you guessed it NO LOVE!! ](*,) 

**THIRD** Googling till my eyes bled I came across this same problem listed on a linux gamers site. Their solution was that a file named quake2.conf was meant to be in /etc. I checked, and hello!! not there. I followed their suggestions and made my own. NOW!! in it your supposed to put the path for your quake2 directory. AHA!! so I put in the following: ](*,) 

/usr/local/games/quake2

Thast all you are not allowed to put anything else. Tried it again and same old error.

**FOUR** Reinstalled the bugger and still no love. ](*,) 

**FIVE** Now for the bugger. I am now compiling a native 64bit version of quake2. This is a horrid solution so please, anyone gimme a clue cause I have tried all the tricks in my book.......

---

### Post by hammett111 on 2005-08-14
[QUOTE=hammett111]Hi, this is a rant and question time post.

I have tried the loki installer for Quake 2. It comes with the demo bundled in it, which you can install, and the option to install the full version at a later date. My rant is this. After the install I type ./quake2 and this horror comes up:

Console initialized.

------- sound initialization -------
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so") failed: ./ref_softx.so: cannot open shared object file: No such file or directory
Refresh failed
recursive shutdown
Error: Couldn't fall back to software refresh!
-> Red  1.300, Green  1.300, Blue  1.300
<- Red  1.000, Green  1.000, Blue  1.000
quentin@andromeda:~$

I have trawled all the Quake sites and many possibilities have been trialled. Here they are. :? 

**FIRST** I had installed quake2 into my home directory, NO NO NO!! you shouldnt do this install it to /usr/local/games/. I did this and still the same error. ](*,) 

**SECOND** Curiously the loki installer does not come with a bunch of required files which can be found in the following package "quake2-snd.tar.gz". These files included my dearly beloved missing "ref_softx.so." So installed to the correct location /usr/lib/games/quake2, ref_softx.so and all his buddies......and....you guessed it NO LOVE!! ](*,) 

**THIRD** Googling till my eyes bled I came across this same problem listed on a linux gamers site. Their solution was that a file named quake2.conf was meant to be in /etc. I checked, and hello!! not there. I followed their suggestions and made my own. NOW!! in it your supposed to put the path for your quake2 directory. AHA!! so I put in the following: ](*,) 

/usr/local/games/quake2

Thast all you are not allowed to put anything else. Tried it again and same old error.

**FOUR** Reinstalled the bugger and still no love. ](*,) 

**FIVE** Now for the bugger. I am now compiling a native 64bit version of quake2. This is a horrid solution so please, anyone gimme a clue cause I have tried all the tricks in my book.......[/QUOTE]

As of 7.38pm tonight I am now running Quake2 IN native 64bit!!!! It took alot of compiling of source and a few binary edits here and there but now I have got it. Once I learn how to create a .deb file I will try and post it somewhere for everyone to DOWNLOAD!!! HAIL 64bit its F$@&* awesome when you get the biatch goin!!

---

