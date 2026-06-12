---
title: "removing wine from ubuntu 16.04 LTS"
date: 2017-03-18
forum: Wine
---

### Post by kerupukmoe on 2017-03-18
I am new to Ubuntu so I'm still noob at this, I tried installing Adobe Photoshop in Ubuntu using Wine but I think I did something wrong with the command line in the terminal.
Instead of installing it directly from the Ubuntu Software, I googled Wine for Ubuntu and followed a set of instructions (command line in the terminal) and when the process has done I can't seem to find any traces of wine on my system (using search doesn't return any results).

using dpkg --list : [http://imgur.com/a/vvZen](http://imgur.com/a/vvZen)

it says
wine
wine-staging-a
wine-staging-i

how do I remove them so I can just directly install it from the Ubuntu Software?
Thanks.

---

### Post by howefield on 2017-03-18
Thread moved to the "Wine" forum for a better fit.

You have wine installed but also installing the Playonlinux package might help make the installation of Windows software a little easier.

---

### Post by deadflowr on 2017-03-18
> how do I remove them so I can just directly install it from the Ubuntu Software?
```
dpkg -l | grep wine | awk '{print $2}' | xargs sudo apt-get purge -s
```
this will do a dry run that you can double check and make sure the correct packages are removed.
If it looks good and the packages you wanted to remove are the only ones listed, switch out the -s for -y and re run it.

You can also run a command like
```
sudo apt-get purge -s wine wine-staging wine-staging-i386 wine-staging-amd64
```
(the i and a in those staging packages are cut short, so it's most likely that the full names are the arch types i386 (32-bit) and amd64 (64-bit))
again switch out the -s flag to run the command for realsy.

And +1 for PlayonLinux.
It provides a nice user interface and also makes it easy to install multiple versions of wine all of which are isolated from one another.
(this makes it easy to run one app that works well in one version of wine and another app that works well in another version of wine, if that make sense)

---

