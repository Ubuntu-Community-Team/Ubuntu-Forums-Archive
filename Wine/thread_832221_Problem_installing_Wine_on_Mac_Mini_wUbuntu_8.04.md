---
title: "Problem installing Wine on Mac Mini w/Ubuntu 8.04"
date: 2008-06-17
forum: Wine
---

### Post by SouthernPott on 2008-06-17
I am trying to install WINE and I have been following the directions on the sticky showing how to get the latest version.  

I can see where the problem is but I don't know what it means.

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/Release](http://wine.budgetdedicated.com/apt/dists/hardy/Release)  Unable to find expected entry  main/binary-powerpc/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
malcolm@apple-mini:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
malcolm@apple-mini:~$ sudo apt-get install wine 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

---

### Post by cogadh on 2008-06-17
Wine doesn't work on non-Intel (PowerPC) Macs. There is a separate project called Darwine that is trying to create a Wine derivative that will work on that architecture:
[http://darwine.sourceforge.net/](http://darwine.sourceforge.net/)

---

### Post by SouthernPott on 2008-06-17
No wonder I am having so much trouble.

I actually need three things.  

1. Adobe Flash or something equivalent.

2. Java Run Time environment or something equivalent.  Tried to get it off the IBM website but after I download it I don't know what to do.

3. Something to run PokerStars.

I am still very inexperienced using the command line so any help is appreciated.  Mostly I depend on the Add/Remove or Synaptic Package Manager. Everything else is above my head.

---

