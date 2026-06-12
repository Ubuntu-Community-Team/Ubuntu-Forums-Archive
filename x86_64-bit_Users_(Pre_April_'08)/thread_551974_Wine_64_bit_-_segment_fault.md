---
title: "Wine 64 bit - segment fault"
date: 2007-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikeym on 2007-09-15
Hi,

I'm trying to get wine running and I'm getting errors no matter what I seem to do. I've followed the [community wiki guide for Wine 64]("https://help.ubuntu.com/community/WineForAMD64") and when I run any of the commands I get a segmentation fault:

```

$ winecfg 
Segmentation fault (core dumped)

```

I then followed the [guide on wine HQ]("http://wiki.winehq.org/WineOn64bit#head-08d4087d863019523214064680fcf26721c9a1af") for compiling wine from source and I got the error:

```

$ /usr/local/bin/winecfg 
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

Could someone direct me toward a way of getting this to work. 

[Also I have suspicions about my nvidia drivers - I have a nvidia 8600GTS so the drivers have to be nviia's own - these are the latest 100.14.11]

---

### Post by Kilz on 2007-09-15
Are you running Feisty?

---

### Post by mikeym on 2007-09-16
Ubuntu 7.04 (Feisty Fawn) - 64 bit variety

---

### Post by mikeym on 2007-09-16
Seems it was an issue with my graphics drivers. I installed the latest nvidia drivers using [this guide]("http://www.robdian.co.uk/content/view/56/") and wine started working from the repositories.

---

### Post by Kilz on 2007-09-16
Is there a reason you are compiling wine rather than use the .deb file in the winehq's repository? The reason I ask is that some people dont know that there is a 64bit .deb file for Feisty.
[If you go here]("http://www.winehq.org/site/download-deb") and add the repository for Feisty you can use apt/synaptic/adept to install wine.

---

### Post by mikeym on 2007-09-16
Thanks,

It was the deb's in the repository that I used when I finally got it working. Compiling was only out of desperation because everything else I have tried had not worked. As I said above though it was just a problem with my NVIDIA drivers.

---

### Post by Baby Boy on 2007-09-16
> **Kilz said:**
> The reason I ask is that some people dont know that there is a 64bit .deb file for Feisty.
[If you go here]("http://www.winehq.org/site/download-deb") and add the repository for Feisty you can use apt/synaptic/adept to install wine.
I am also trying to install Wine 64bit. I did what you said, added the repository and reloaded synaptic but I don't see any 64bit versions when I do a search, only normal WIne. How do I find the 64bit version?

---

### Post by mikeym on 2007-09-16
The 64 bit version of wine's package is still called 'wine'. Check in synaptec and you should see the version says something like 0.9.43~winehq0~ubuntu-7.04-1

---

### Post by Yellow Pasque on 2007-09-16
Rather than putting the repository in my database and slowing down the update process, I just check this link occasionally: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Baby Boy on 2007-09-17
> **mikeym said:**
> The 64 bit version of wine's package is still called 'wine'. Check in synaptec and you should see the version says something like 0.9.43~winehq0~ubuntu-7.04-1
OK, thanks, found it.

---

