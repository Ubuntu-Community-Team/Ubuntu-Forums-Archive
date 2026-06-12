---
title: "Flash in Gutsy?"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Stochastic on 2007-10-25
Hi I'm new to 64bit as of the Gutsy release of UbuntuStudio.  I'm just trying to get my flash configured in firefox (maybe I should be using swiftfox?).  What's the best method for Gutsy?  The installer from Macromedia certainly doesn't like to be run on a 64bit system.

---

### Post by NilsE on 2007-10-25
Try installing the flashplugin-nonfree in the repository.  It is 32 bit but I believe it works.

---

### Post by FredB on 2007-10-25
> **NilsE said:**
> Try installing the flashplugin-nonfree in the repository.  It is 32 bit but I believe it works.

This meta-package is for both 32 and 64 bits.

Flash is only 32 bits. Hope Gnash will soon kick flash *** !

---

### Post by sicone on 2007-10-25
I've tried installing Flash from Synaptic and from Macromedia and in both cases flash player will freeze up after about 8 - 15 secs of playing.
I've even tried installing 32bit FF and reinstalling flash but the same thing happens.
Anyone know how to solve this?

---

### Post by jasonsweet on 2007-10-25
I had similar problems.  I installed 64 bit flash with Automatix, that fixed the problem for me.

[http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

### Post by sicone on 2007-10-25
Tried Automatix and still no good :(

---

### Post by Stochastic on 2007-10-25
Hmm, I apt-got flashpluin-nonfree but upon a firefox reboot no flash was to be found (went to youtube).  Is more needed to configure it?  Should I just let Automatix do the work?  (I've heard nasty things uttered about automatix so I'd rather not)

---

### Post by rumblered on 2007-10-25
Install flashplugin-nonfree and nspluginwrapper. The latest version of nspluginwrapper now works better than using a 32-bit Firefox, in my experience, and since it runs the plugin in a separate 32-bit process, it even isolates Firefox from Flash-induced crashes!

---

### Post by rplantz on 2007-10-25
> **Stochastic said:**
> Hmm, I apt-got flashpluin-nonfree but upon a firefox reboot no flash was to be found (went to youtube).  Is more needed to configure it?  Should I just let Automatix do the work?  (I've heard nasty things uttered about automatix so I'd rather not)

I had the same problem. I did the following (I use synaptic for my package management because I like to have a history.):

1. Completely removed nspluginwrapper and flashplugin-nonfree.

2. Deleted the .mozilla directory in my home directory. NOTE: This deletes all your bookmarks, history, etc. I recommend making a backup of this directory. Perhaps just renaming it will work. (I did not think of this, so lost everything. Luckily, I had a somewhat recent backup.)

3. Installed flashplugin-nonfree, which also brings in nspluginwrapper.

Flash now works for me.

---

