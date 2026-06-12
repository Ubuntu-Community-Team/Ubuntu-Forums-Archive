---
title: "Wine requires Nvidia openCL driver to be removed"
date: 2014-04-22
forum: Wine
---

### Post by Dave.YNA on 2014-04-22
Hello all, 
   I am looking to install wine on 14.04 but when attempting the install I am told that an Nvida opencl driver and icd loader must be removed first.

[ATTACH=CONFIG]252367[/ATTACH]

I am also running the Nvidia display drivers. 

How will removing this driver affect my system?

---

### Post by jbaerboc on 2014-04-22
Hi Dave, I honestly have no clue...but that being said I had the same prompt and said ok...and my computer still works fine. I have the Nvidia 9600 GT video card with Nvidia proprietary drivers installed.

My guess is that what it wants to remove would be something related to the free open driver Ubuntu uses by default on your computer when you first install it. Maybe Wine realizes you'd need the proprietary driver to do much in it? Just some guesses but hope someone can give you a more knowledgeable answer.

---

### Post by Dave.YNA on 2014-04-22
Thanks for the info. 

Well it is good to know that someone else has seen it and is also using the proprietory drivers. I was a little bit hesitent to hit install and hope after spending quite a while setting up this comp to how I like it.

---

### Post by kryptt2 on 2014-05-26
This is probably a mistake on the package maintainer's part.

I would go to their launchpad page and ask there!

---

### Post by lah-ca on 2014-05-26
See here: [http://ubuntuforums.org/showthread.php?t=2225279](http://ubuntuforums.org/showthread.php?t=2225279)

---

