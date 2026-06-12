---
title: "Trouble getting newest Wine"
date: 2008-06-09
forum: Wine
---

### Post by pixelkitty on 2008-06-09
I'm having trouble getting the newest Wine, and was wondering if anyone else was having trouble connecting to the winehq repository. 

Every time I use the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

It just hangs there in limbo after I give it the root password. After about five minutes of nothing, I ctrl^c out of it, and have nothing to show for it. 

Am I doing something wrong? Is there a setting I should check? Or is it maybe a server issue that others are having as well? 

Oh, and as for answers, I'm coming back to linux after about ten years off, so while I'm not clueless, you might want to use simple explanations. ;)

Thanks for any help.

---

### Post by Sammi on 2008-06-09
You can actually skip that line that adds the repo authentication key: ```
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
```And just go straight to this line, which adds the Wine repository ```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```If you do this, then apt-get will keep complaining about the wine repo not being authenticated, but it'll use it anyway.

---

### Post by pixelkitty on 2008-06-09
Ah, excellent. 

Thanks for your help. 

.
.
.

And I have wine 1.0-rc4. Thanks again. :)

Pixel

---

### Post by Sammi on 2008-06-09
You could also try this:

```
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
sudo apt-key add [387EE263.gpg]("http://wine.budgetdedicated.com/apt/387EE263.gpg")
```
I'll be honest though, I don't know much about adding authentication keys from .gpg files, and I'm on a mac right now so I can't test it for you. But you can always just try :)
[]("http://wine.budgetdedicated.com/apt/387EE263.gpg")

---

### Post by pixelkitty on 2008-06-09
Yeah, that worked. Thanks again. 

That's not the first time things went wrong when I tried getting fancy with sudo. Even just putting '&' at the end will cause trouble with sudo for some reason. 

In any case, thanks again for your help. 

Pixel, who needs to get around to making a sig. ;)

---

