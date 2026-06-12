---
title: "wine 10MB vs wine 30MB"
date: 2008-03-11
forum: Wine
---

### Post by giuspen on 2008-03-11
Do anybody can tell me why the wine package from the ubuntu repository is 30MB and the package for ubuntu from winehq repository is only 10MB? Due to this mismatching I always waited 6months to have new version of wine because the wine on ubuntu repository is never updated :(
Bye & thanks.

---

### Post by wblancqu on 2008-03-11
To always have the latest wine, follow instructions on 
[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```

Grtz

---

### Post by Sukarn on 2008-03-11
The question was not how to get a new version of wine, but rather what are the differences between ubuntu's wine and the official one from winehq. How can there be so much difference between the two that they have a 20 MB difference in the size of the installer, and a 50+ MB size difference of the installed application?

This question has always perplexed me, but it seems that in wine 0.9.57 in hardy, this difference of size is almost gone (although the one from winehq is for gutsy). They are both about 11 MB in size (although this was not the case with 0.9.56)

---

### Post by Sammi on 2008-03-11
Maybe the official Ubuntu deb comes with the source code?

Anyway the debs from winehq.org are just good as the debs in the official repository. Been using them for years :D

---

### Post by Sukarn on 2008-03-12
Yeah, I've been using winehq's debs too.

---

### Post by YokoZar on 2008-03-12
It's because the Ubuntu packages weren't stripping the debugging symbols until recently.  The winehq debs were also compressed with bzip2 while the ubuntu ones defaulted to gzip.

Nothing really important, unless you were using the debugger.

---

### Post by giuspen on 2008-03-12
Thanks a lot, so I will start to use packages from winehq repository.
Bye,
Beppe.

---

