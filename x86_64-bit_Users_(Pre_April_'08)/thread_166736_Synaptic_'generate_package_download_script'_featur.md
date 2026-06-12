---
title: "Synaptic 'generate package download script' feature"
date: 2006-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by xwing on 2006-04-27
I've noticed that Synaptic has a 'Generate package download script' menu item. However, when I use it it doesn't seem to do anything at all (i.e i choose the destination dir. and even specify a script name, but the script is not generated and the file is not created).
 
Anyone else have the same issue:confused:

---

### Post by bettermentflux on 2006-10-20
Same here on a release candidate for 32-bit Edgy. Shame; it looks like a really useful feature.

I was hoping to use it so that I could recover quickly after a fresh install.

---

### Post by StratosL on 2006-10-30
Using official Edgy  release, still not working. It actually produces a script file, but it is empty except for the header. 

I actually asked about the very same feature back in April, on this forum:

[http://www.ubuntuforums.org/showthread.php?t=144817](http://www.ubuntuforums.org/showthread.php?t=144817)

The answer came from gborzi, try it out just in case. 

StratosL   	

Message from thread:

Re: how to get a snapshot of everything installed
Quote:
Originally Posted by StratosL
Hi there. Two quick questions:

1) I was wandering if there is a way to take a snapshot of everything installed on a system and store it in a file (ie every package and version)

2) Is there a way to use the above list with a new install, so that the exact packages are automagically installed on the new machine(s)?

Thanks,

Stratos
For 1) type dpkg -l . The answer will be something like this
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-=====================================-========================================-============================================
ii 3ddesktop 0.2.8-1ubuntu3 "Three-dimensional" desktop switcher
ii a2ps 4.13b-4.3 GNU a2ps - 'Anything to PostScript' converte
ii aatv 0.3-1ubuntu1 A program to watch TV in a text-based consol
ii abiword
....
As for 2) I would try this:
On the system where you have already installed all packages you wanted type

$ dpkg -l |grep '^ii '|sed -e 's/ii //' -e 's/ .*//' > list.txt

move the file list.txt to the other system and type

sudo for i in `cat list.txt`; do
yes| apt-get install $i
done

but I think there can be better alternatives. Little explanation:
the command dpkg -l |grep '^ii '|sed -e 's/ii //' -e 's/ .*//' gives you a list of installed packages without the initial ii, version and description.
__________________
Giuseppe Borzi' - Linux counter user #34028

---

### Post by mikedeatworld on 2006-11-21
i think that issue is fixed now.

---

### Post by StephaneLenclud on 2007-02-27
Not fixed for me it generates an empty script file :(
There must be a trick to get it working though...

StratosL I could not get your listing command to work, I've been using the following instead:
dpkg -l |grep '^ii '|sed -r 's/ii\s+(\S+)\s+.*/\1/i' > list.txt

---

### Post by peterquistgard on 2008-02-13
"Package download script" is used in order to download packages on a non networked system. If you select a few packages to be installed using Synaptic, then create a download script, the script will not be empty. 

In this case the script can be run on any suitable (Linux) system with a decent connection. It will download all the necessary files, which can then be transported back to the non networked system for installation. To install them, go to File->Add Downloaded Packages.

---

