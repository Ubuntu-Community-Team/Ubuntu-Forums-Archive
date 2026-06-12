---
title: "Cant install halo"
date: 2008-07-03
forum: Wine
---

### Post by filip102 on 2008-07-03
I tryed install HALO but when I run setup it just show me installation box and then shut down. Is that because CD is not original and it have safedisc copy-protection? I just because I just going install DX?

DX installed, still nothing.

---

### Post by cogadh on 2008-07-03
If you are trying to run a pirated copy of a game, you will not find any help here as that is against the forum TOS.

---

### Post by filip102 on 2008-07-03
I sayd NO ORIGINAL and no PIRATE. This is copy of my CD, I found it now and original is anywhere but nobody know where.

---

### Post by |{urse on 2008-07-03
[http://ubuntuforums.org/showthread.php?t=486986&highlight=halo+combat+evolved](http://ubuntuforums.org/showthread.php?t=486986&highlight=halo+combat+evolved)

i also had my own howto up but it was removed because it had piratey things in it. But that howto did work for me also. you'll also need a decent video card and the correct drivers (3d working)

---

### Post by filip102 on 2008-07-03
== Step 2: Install Halo ==
Cant run :lolflag:

---

### Post by |{urse on 2008-07-03
reread those instructions. they tell you how to install it. You will need crossover installed as well.

---

### Post by cogadh on 2008-07-03
You don't need to pay for Crossover (though go right ahead if you want, it will support Wine), the game works fine in Wine. There are Wine specific instructions here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720)
Also, I just noticed your edit about installing DX. You should not install DX in Wine as Wine already has its own implementation of DX. By installing Microsoft's DX, you have broken Wine's DX and nothing will work. The easiest way to fix it is to delete your .wine directory and create a new one.

BTW - I said _IF_ you are trying to run a pirated copy, don't ask for help. Just saying your disk was "not original" leaves things open to interpretation and I was not about to offer advice without some clarification.

---

### Post by filip102 on 2008-07-03
How many times I must sayd I have this dll but setup.exe dont want run..

---

### Post by |{urse on 2008-07-03
you need to be using wine version > 9.6, there were a couple people on thread with your very same problem. and installing version 9.6 fixed the problem. Sorry your posts are hard to understand, bit of a language breakdown.

---

### Post by filip102 on 2008-07-03
Can u post link for deb plz? And sorry for my english, but I writing what I need and dont care about if it is right or no :lolflag::lolflag: (so it take 30 seconds and no 5 minutes to write this. :guitar:

---

### Post by |{urse on 2008-07-03
well first off what release of ubuntu and wine version are you running. You could just install the latest wine from the repos.

sudo apt-get remove wine --purge && sudo apt-get install wine

---

### Post by filip102 on 2008-07-03
OK, going try. And I have it from repos... and have problem too. Downloading from wineHQ deb pack.

---

### Post by filip102 on 2008-07-03
THX, working gr8 :popcorn:

---

### Post by filip102 on 2008-07-04
Installed but have any error :confused: and same problem if I dont enable virtual desktop.

---

