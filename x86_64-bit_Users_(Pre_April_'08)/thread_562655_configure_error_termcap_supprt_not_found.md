---
title: "configure error: termcap supprt not found"
date: 2007-09-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by freemanty on 2007-09-29
I am trying to install a package on my 64 bit  ubuntu 7.04, here is the error: 

----------------
checking for tgetent in -ltermcap... no
checking for tgetent in -ltinfo... no
checking for tgetent in -lcurses... no
checking for tgetent in -lncurses... no
configure: error: termcap support not found
make[2]: *** [editline] Error 1

where I can found that lib?

thanks!

---

### Post by Kilz on 2007-09-29
[Here are the results of a package search]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=termcap&searchmode=searchword&case=insensitive&version=feisty&arch=amd64") of the repositories. You can use synaptic or apt to install any of the listed packages.[ You might want to bookmark the package search page.]("http://packages.ubuntu.com/")

---

### Post by chiefofthejojos on 2008-03-09
```
sudo apt-get install libncurses-dev
```

---

