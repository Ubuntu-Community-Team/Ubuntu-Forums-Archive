---
title: "Problems with KOTOR2 and wine"
date: 2007-10-05
forum: Wine
---

### Post by daltocli on 2007-10-05
Hello,

Currently I have wine 0.9.26 installed, running in a Virtual Desktop (800x600) and I'm trying to run KOTOR2.

After using it's Scan Hardware facility I find out that the only problems are:

[list]
[*]Graphics: Defined as [] 128MiB, Would prefer an nVIDIA or ATi card... Ignorable
[*]OpenGL: Failed. "Tungsten Graphics, Inc - 1.3 Mesa 6.5.2 installed, it wants "Non-Windows Generic OpenGL 1.4.0 drivers"
[/list]

Without a doubt it's the OpenGL stopping the game running... I'm running Feisty amd64/x86_64 with 32-bit wine... How do I solve this OpenGL problem?

Just encase anyone finds it useful, a screenshot of the "diagnostics" is here: [http://daltocli.co.uk/KOTOR2-ScanHardware.png](http://daltocli.co.uk/KOTOR2-ScanHardware.png)

Any help would be much appreciated!

---

### Post by cogadh on 2007-10-05
For one thing, you are using a very out of date version of Wine, it would probably be best to upgrade at least to 0.9.33 (the version in the Ubuntu repositories), but the latest version (0.9.46) does have better performance.

As for your OpenGL problem, it would be helpful to know which Intel chipset you have. Some of the older Intel IGP's pretty much have no hope of running the game, but some of the newer chipsets might be able to.

---

### Post by daltocli on 2007-10-05
Heya,

The chip is an Intel 945GM (Got this laptop around January this year), 128MiB shared RAM.

---

### Post by cogadh on 2007-10-05
Then I'm afraid you are probably SOL on this one. The default Intel drivers that come with Ubuntu are the latest available for the 945 and earlier chipsets. Since OpenGL support is a function of the drivers, you won't be able to update to the OpenGL 1.4 support the game requires.

---

### Post by albertotapia80 on 2008-08-09
I have the same problem, and I also tryed to play it with wine, and I even try to play it in güindous vista and it didn't worked, is it because of the intel chipset???

I wan't to make this clear güindous was a desperate intent

---

