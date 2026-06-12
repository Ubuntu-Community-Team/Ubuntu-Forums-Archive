---
title: "So, upgrading to Feisty x64?"
date: 2007-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by M$LOL on 2007-04-06
I'm wondering about upgrading to Feisty, and contrary to what I decided awhile ago, I've now made up my mind that I am going to if everything I need is supported.

Here's my list:

1> Madwifi (via restricted-modules is OK, I just need to know which one to get)
2> Kilz' script for installing FF 32 with the Flash plugin. That is vital.
3> Wine, again Kilz' script.
4> VMWare
5> All of the apps currently in the repos

Also, I need to be able to do everything I can currently do in Edgy, such as the installation of i386 debs using dpkg and the installation of RealPlayer etc etc.

So, will all of that work? :-k

---

### Post by Kilz on 2007-04-06
> **M$LOL said:**
> I'm wondering about upgrading to Feisty, and contrary to what I decided awhile ago, I've now made up my mind that I am going to if everything I need is supported.

Here's my list:

1> Madwifi (via restricted-modules is OK, I just need to know which one to get)
2> Kilz' script for installing FF 32 with the Flash plugin. That is vital.
3> Wine, again Kilz' script.
4> VMWare
5> All of the apps currently in the repos

Also, I need to be able to do everything I can currently do in Edgy, such as the installation of i386 debs using dpkg and the installation of RealPlayer etc etc.

So, will all of that work? :-k

#2 The mplayer part of the script doesnt work yet. I paln on a Feisty version because the older java used in the Edgy script doesnt work, but when upgraded it works fine.
#4 I have had no sucess getting vmware to work with Feisty.
#5 gdesklets still crashes while starting.

---

### Post by Ocxic on 2007-04-06
i try'ed the upgrade and it didn't work I ended up re-installing edgy.

I tried installing with the cd too, and it wouldn't pickup my software raid partitions, so i guess I'm gonna have to wait a bit longer, til i can upgrade.

---

### Post by M$LOL on 2007-04-07
Hmm, that's OK, apart from Vmware. That's fairly essential for me, so I won't upgrade if that doesn't work. That also worries me, because if Vmware doesn't work, will that mean that other apps that work fine in Edgy might not work in Feisty as well?

Any chance of that being fixed by the release of Feisty on the 19th?

---

### Post by StratosL on 2007-04-07
I just upgraded  to Feisty x64 from Edgy x64 and omg, it works. 

I had very strong doubts that this would work, because I am using LVM over RAID1, for which the installer always failed until now. However, this time, instead of installing from CD, I used the gui method (gksu "update-manager -c -d") from within Edgy.

I got several error messages line "mdadm: no devices listed in conf file were found", something about "unchecked /etc/mdadm/mdadm.conf", "no ...85-brltty.rules" file, but it actually worked after reboot. I hope it stays good. 

Other than that, firefox 32 from Kilz's script still works fine from Edgy64 to Feisty64, w/ all the plugins too (java, flash, mplayer). 

I activated the nvidia drivers and then Beryl, that works too (as a precaution, before the upgrade I changed xorg.conf from "nvidia" back to "nv" and commented out all references to composite; also, I chose "metacity" as a window manager from within the Beryl config menu).

I keep my fingers crossed, this would be my 5th attempt since herd5, all previous ones failed due to something screwed up with RAID during install.

---

### Post by StratosL on 2007-04-07
Crossover 6.0.1 works, Vmware server 1.0.2 does not seem able to successfully produce a kernel module.

---

### Post by xopher on 2007-04-08
I needed to get the beta version of VMware Workstation (6 something) for the modules to compile, now it works flawlessly though.

Wine works just as well as it did for edgy.

---

### Post by StratosL on 2007-04-08
Confirmed, VMware Workstation 6 beta installs and runs fine. Will it stop working when the final version is released? Oh well, maybe the Server version will be updated by then.

---

