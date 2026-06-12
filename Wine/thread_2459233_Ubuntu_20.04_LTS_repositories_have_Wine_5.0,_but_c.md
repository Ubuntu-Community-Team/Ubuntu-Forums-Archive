---
title: "Ubuntu 20.04 LTS repositories have Wine 5.0, but current version is 6.0"
date: 2021-03-14
forum: Wine
---

### Post by John Nagle on 2021-03-14
I'd like to stick with versions from Ubuntu repositories, because using wierdo third party repositories usually causes package manager problems. 
But Wine 5.0 won't run something, and I'd like to try Wine 6.0. Is it possible to run Wine without installing it as root?

---

### Post by CatKiller on 2021-03-14
> **John Nagle said:**
> I'd like to stick with versions from Ubuntu repositories, because using wierdo third party repositories usually causes package manager problems. 

It doesn't **usually** cause problems. It's possible to muck up your package manager, and it's also possible to not, just like everything. 
 
> But Wine 5.0 won't run something, and I'd like to try Wine 6.0. Is it possible to run Wine without installing it as root?

Lutris uses its own versions of Wine independently of the system version. You do need to install **a** version of Wine system-wide, so that you have all the required dependencies, but the actual version doesn't matter that much.

---

### Post by mastablasta on 2021-03-15
first make sure wine version is the issue.

---

### Post by david503 on 2021-03-21
I'm actually doing WINE stuff right now for the first time (I'm 18.04) and so I went to winehq to install it, and yea they're "[COLOR=#000000]wierdo third party repositories" but I mean we're talking about a decades established application set here.  

[/COLOR]Take a look at the winehq.org, installation page- it was thorough, it even covered some problems I'd had just trying it with apt-get.  

Oh also if you have that "winehq-stable : Depends: wine-stable" error, I had that too let me know.

Did you install virtualbox?  I had to uninstall virtualbox; a dependency conflict.  Although I'm guessing I can just reinstall a newer version, idk.  

There's another notification "N:" something that I think had to do with audio, I found how to fix that too, lemme know I'll go find the site again it was only like 2 days ago it's probably in my history. 

gl.

---

