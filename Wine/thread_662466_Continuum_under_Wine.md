---
title: "Continuum under Wine?"
date: 2008-01-09
forum: Wine
---

### Post by Fireblend on 2008-01-09
Anyone able to play Continuum under Wine? If so, I'd like to get some support on its installation process. It seems that the project whose page is available at wine.getcontinuum.com is still stuck on Continuum v0.39, thus making it impossible to play the game, as when I try, I'll get prompted to download the new version, and make the game crash.

I tried using the [patched Wine method]("http://ubuntuforums.org/showthread.php?t=339455") to work with Continuum 0.40, but everytime I try logging in into any server, it will reject me as if the username was already in use or if I had input the password incorrectly (I'm pretty sure of this, tried random usernames without avail).

I'd love to know if the Linux project is still active or if I just should lose all hope on getting this to work under Ubuntu. I found several guides, but all applied to the old version, as the newest thing I could find was from January last year.

Any help would be greatly appreciated, as I'd really like to get into this game again. Thanks in advance.

---

### Post by biohypnotix on 2008-01-09
I downloaded and installed the latest dev version of Continuum-wine from:

[http://wine.getcontinuum.com/development.php](http://wine.getcontinuum.com/development.php)

I received an error when I tried to run it and had to edit the "wine" shell script located in:

/home/username/Continuum-wine/

I deleted the following lines in that file to get Continuum to run:

# else
# echo "$0: could not locate Wine source tree"
# exit 1

It's still the old version though and I couldn't enter a zone without that upgrade message. I then downloaded the latest Windows version from:

[http://subspacedownloads.com/download.php?fid=1335](http://subspacedownloads.com/download.php?fid=1335)

And installed it through WINE to the same folder where I installed the Continuum-wine dev version.

e.g. /home/username/Continuum-wine/Continuum

After all that I was able to fire Continuum up and enter a zone fine except for my frame rate being at 13 which is unplayable for me. ESC + F in game shows your frame rate. I hope you have higher FPS than I do.

---

### Post by romancexplosion on 2008-12-15
do you play on chaos zone? if so, what your name?

---

