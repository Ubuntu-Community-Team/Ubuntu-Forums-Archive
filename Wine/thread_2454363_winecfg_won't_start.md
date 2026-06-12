---
title: "winecfg won't start"
date: 2020-11-27
forum: Wine
---

### Post by Dukenukemx on 2020-11-27
I upgrade 19.04 to 20.04 and reinstalled Wine Staging, but now winecfg doesn't work.  Regedit doesn't work either.  Winetricks does work.  I installed wine from [here](https://wiki.winehq.org/Ubuntu) but I've also tried wine-installer.  I've deleted .wine and purged wine multiple times.  No errors are given.  It just stops.  I need some help please.

---

### Post by Raffles727 on 2020-11-30
Hi, try installing it with Synaptic Package Manager.

---

### Post by CelticWarrior on 2020-11-30
> **Raffles727 said:**
> Hi, try installing it with Synaptic Package Manager.

What makes it different with Synaptic, in your opinion?

---

### Post by Raffles727 on 2020-11-30
> **CelticWarrior said:**
> What makes it different with Synaptic, in your opinion? It will install all the dependencies. I've solved several problems with various applications by using Synaptic. Of course, it won't solve all problems, but it's worth a try. You could also simply ask it to update your package, and it will determine whether there are missing dependencies.

---

### Post by CelticWarrior on 2020-11-30
> **Raffles727 said:**
> It will install all the dependencies. I've solved several problems with various applications by using Synaptic. Of course, it won't solve all problems, but it's worth a try. You could also simply ask it to update your package, and it will determine whether there are missing dependencies.

So, as expected, you can't see past (or deeper) than the surface of a GUI tool.
Synaptic is just a GUI with a search feature that runs commands in the background. The exact same commands you can run on your own. Synaptic isn't "smarter" than those commands it runs.

What matters isn't any tool, GUI or CLI, helping to install software, it's the software itself, how is it package, which version and where does it comes from that matters.

If you have read the OP properly you would know the question is about 1) Wine (available in the Ubuntu repository, tested but not the latest version) and 2) a particular version of Wine - wine-staging (AKA "alpha", even more unstable then "beta" - not available at the Ubuntu official repositories but instead provided by a third-party PPA (WineHQ). Knowing that the OP followed the linked instructions, i.e., added the PPA, it no longer matters which way the software will be installed. The Ubuntu Store, Synaptic  or any of the dozen similar tools merely use APT to retrieve and install the software with results in terms of dependencies resolution indistinguishable from simply running 'sudo apt install <package>' (in this case package = wine-staging). And this is NOT a dependencies problem. Suggesting Synaptic in the context of this thread is regrettably dumb and unhelpful.

---

### Post by Raffles727 on 2020-12-01
> **CelticWarrior said:**
> So, as expected, you can't see past (or deeper) than the surface of a GUI tool.
Synaptic is just a GUI with a search feature that runs commands in the background. The exact same commands you can run on your own. Synaptic isn't "smarter" than those commands it runs.

What matters isn't any tool, GUI or CLI, helping to install software, it's the software itself, how is it package, which version and where does it comes from that matters.

If you have read the OP properly you would know the question is about 1) Wine (available in the Ubuntu repository, tested but not the latest version) and 2) a particular version of Wine - wine-staging (AKA "alpha", even more unstable then "beta" - not available at the Ubuntu official repositories but instead provided by a third-party PPA (WineHQ). Knowing that the OP followed the linked instructions, i.e., added the PPA, it no longer matters which way the software will be installed. The Ubuntu Store, Synaptic  or any of the dozen similar tools merely use APT to retrieve and install the software with results in terms of dependencies resolution indistinguishable from simply running 'sudo apt install <package>' (in this case package = wine-staging). And this is NOT a dependencies problem. Suggesting Synaptic in the context of this thread is regrettably dumb and unhelpful.

I'm sorry I tried to be helpful. Maybe this suggestion will help you though. [https://en.wikipedia.org/wiki/How_to_Win_Friends_and_Influence_People](https://en.wikipedia.org/wiki/How_to_Win_Friends_and_Influence_People)  Cheers, I'm out of here.

---

### Post by Dukenukemx on 2020-12-17
Yea, none of this solved my problem.  Something is definitely missing that allows Wine to run because even Lutris doesn't work.  It just stops when install a game and does nothing. I have another working Ubuntu 20.04 machine and will try and see what files are missing on this one compared to the other one.

**EDIT**
Actually that's harder than I thought.  Anyone got any idea what packages are needed for Wine to work?

---

### Post by Dukenukemx on 2020-12-19
Went to the Wine forum and got it working.  For some reason this command worked.  So now whenever I use winecfg it just works, along with any application I run. 

```

WINEPREFIX=~/wine-test /opt/wine-staging/bin/wine winecfg
```

---

### Post by Dukenukemx on 2020-12-21
Ok, this time I'm certain I know what the problem is and have it fixed. The issue is that when I update or install wine-staging from the wine repository, for some reason it also installs wine from the Ubuntu repository. So I had Wine 6.0 and 5.0 installed at the same time, in two different locations. I had to remove Wine 5.0 and reboot the PC and now everything works fine.

---

