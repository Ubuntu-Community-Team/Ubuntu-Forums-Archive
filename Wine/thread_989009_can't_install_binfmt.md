---
title: "can't install binfmt"
date: 2008-11-21
forum: Wine
---

### Post by Amateur Phantom on 2008-11-21
Hi, I recently upgraded my pc, everything is new an all, I happilly procceded to install Ubuntu 8.04, all was well, but when I tried installing binfmt so I could put Wine onto my pc, Gdebi crashed, I tried multiple times to no avail, could anyone help me out?:confused:

---

### Post by jrib on 2008-11-21
Why are you using gdebi instead of just installing wine directly from the repositories with a program like System -> Administration -> Synaptic or apt-get?

---

### Post by Amateur Phantom on 2008-11-21
I'm still a bit of a rookie, do you think you could walk me through how to do that?
thanks

---

### Post by jrib on 2008-11-21
[LIST=1]
[*]Open System -> Administration -> Synaptic
[*]Search for wine
[*]Right Click -> Install
[*]Apply
[/LIST]

---

### Post by Amateur Phantom on 2008-11-22
thanks, still not working, I decided to put files onto a disk and use the synaptec add disk(or something like that) feature, as I say it is not working,It gave me an error report saying something about the disk not being .deb, so i think somehow the files for binfmt and wine have been corrupted, I will try downloading it again some other time, thanks again

---

### Post by jrib on 2008-11-22
Copy and paste actual error messages, otherwise it's really hardy to understand what is happening.

You want to install wine, so open a terminal and run ```
sudo apt-get install wine
```.  Then paste the full output here.

---

### Post by cogadh on 2008-11-22
Something everyone has failed to mention so far is that you do not need to install binfmt separately from Wine. If you just use Synaptic or apt-get, it will determine that Wine depends on binfmt and automatically install it when you install Wine.

---

