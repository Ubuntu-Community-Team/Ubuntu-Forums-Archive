---
title: "Help with Wine Installation"
date: 2008-06-08
forum: Wine
---

### Post by agrace on 2008-06-08
--------------------------------------------------------------------------------

I am trying to install Wine on my computer running ubuntu 6.06 LTS. I have the Wine downloaded but everytime I click the package, the package installer pops up for like two seconds and then goes away. I don't see anything that would point to wine being already installed. Does anyone have any advice on how to fix the problem? TIA

---

### Post by doorknob60 on 2008-06-08
Try installing wine with the terminal
```
cd ~/Desktop               (assuming it's on your desktop)
sudo dpkg -i wine*
```

Or you could use this, but it might be a really outdate version (although I'm not sure how old your current version that you're trying to install is either...)
```
sudo aptitude install wine
```

---

