---
title: "Streamlining"
date: 2007-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by daltocli on 2007-10-01
Heya,

I've recently just reinstalled Ubuntu Feisty with the intention of either stripping it down so games like ut2004 will perform better (and with higher settings) or somehow altering things so Ubuntu runs more efficiently (and games performing better)...

My current system spec:
[list]
[*]Intel Core 2 Duo (Centrino) @ 1.66GHz
[*]2GiB RAM
[*]160GiB SATA HDD
[*]Intel 945GM 128Mb (shared memory)
[*]8x DVD+/-RW drive
[*]15.4" WXGA 'UltraBright' TFT (1280x800 max resolution)
[/list]

Any ideas how I can make ubuntu perform better? I've done things like editing /etc/init.d/rc and changing CONCURRENCY to shell, removing swap (and changing vm.swappiness to 0 in /etc/sysctl.conf), etc etc

I'd be greatful for any help - REALLY want to get a perfect setup!

Cheers!

---

### Post by maharbA on 2007-10-01
I'm afraid I don't know how to help you, but you may want to list your video card, since this could affect game performance.

---

### Post by John.Michael.Kane on 2007-10-01
First I'm taking it that your using ubuntu 64?

Second That setup should not be bog down or bottlenecking. 

Third in most cases where gaming performance is having problems/suffering the first place one should look is at their gpu. Next would be the amount of memory in the machine. 

Fourth Regarding striping down Ubuntu, it's always best to do a minimal install Vs trying to strip down a full Ubuntu install. 

Most users who run minimal installs start with the following.
1) Install ubuntu commandline system
2) sudo aptitude install xorg gnome-core firefox synaptic
3) build from there.

On the extreme end.
1) install ubuntu commandline system
2) sudo aptitude install xorg fluxbox firefox synaptic

---

### Post by daltocli on 2007-10-01
Heya,

GPU wise I only have an Intel 945GM graphics card with 128Mb shared memory... However physical memory is 2GiB, which I'm upgrading to 4GiB soon.

Daft question, but how do I go about installing just the commandline system? Use the server distro? I've installed this current instance with the LiveCD which doesn't seem to have any option but a full install.

Cheers!

---

### Post by John.Michael.Kane on 2007-10-01
> **daltocli said:**
> Heya,

GPU wise I only have an Intel 945GM graphics card with 128Mb shared memory... However physical memory is 2GiB, which I'm upgrading to 4GiB soon.
While that gpu seems capable at least for normal use, I'm not sure how well it does at gaming. For that info I would suggest you have look over in Gaming & Leisure to see if there are any other gamers using this card with the games you wan to use.

> **daltocli said:**
> Daft question, but how do I go about installing just the commandline system? Use the server distro? I've installed this current instance with the LiveCD which doesn't seem to have any option but a full install.

Cheers!

Regarding installing command line systems. You can do so using the alternate iso 

or 

The [MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by daltocli on 2007-10-01
Cheers,

Downloading the Alternate ISO now... The Minimal one (amd64) gave me an error about the Release file just after setting up networking... Weird :\

---

### Post by Jouke74 on 2007-10-02
If you really want to see an imprivement in games buy a Nvidia G79## card and install the right drivers. Gaming does not compare to windows but I think it will run better on Ubuntu than "an internal memory using integrated graphics chip".

---

### Post by daltocli on 2007-10-02
**[Jouke74]** While that's an ideal solution and will be done for my workstation, it is unfortunately not a solution for this instance, since the machine in question is a laptop.

I've considered upgrading to a new laptop - some of the new Dell's have dedicated gpus which look good, but seem to be limited to 2GiB RAM maximum... Whereas this laptop is capable of upto 4GiB! So I'm kinda stuck in the middle.

---

### Post by saru411 on 2007-10-02
2 gb of ram should be fine for any gaming system. your problem is your video card. if you want your gaming to preform better you will need a new one. intel graphics are ok for a budget pc but it will not give you the desired frame rates for gaming. The new dell vostros are extremely cheap and have the option of an nvidia 256mb 8400. im not sure how good it will work for games. i have a vostro 1500 with the 128mb version of the nvidia 8400 and it preforms well with the 3d effects of compiz fusion. im unsure about gaming since the only game i play is go, which does not require high fps.

---

