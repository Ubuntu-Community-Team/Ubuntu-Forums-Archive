---
title: "getting 20 or lower FPS in Diablo 3"
date: 2013-04-24
forum: Wine
---

### Post by hydrizl on 2013-04-24
[COLOR=#000000][FONT=MavenPro]I'm a new linux user and I'm using ubuntu 12.04. I installed diablo 3 through playonlinux. My issue is whenever I'm in game I get sub 20s FPS consistently. It doesn't matter if I lower my graphics setting or resolution I still get the same frames. This same rig runs this game great on windows.[/FONT][/COLOR][COLOR=#000000][FONT=MavenPro]
[/FONT][/COLOR]
[COLOR=#000000][FONT=MavenPro]I tried reverting back to gnome desktop and it doesn't seem to help. I'm using a radeon HD 9790 with latest Catalyst 13.3 beta drivers. My processor is  amd phenom X6 (6 core). I tried setting the core affinity to use a different number of cores using the WINE task manager and it did not seem to help. Any insight into my issue would be very helpful.

Edit: I just noticed theres a playonlinux subsection to this forum. Sorry about the misplaced post just noticed it now [/FONT][/COLOR]:(

---

### Post by myromance123 on 2013-04-24
> radeon HD 9790 Do you mean a 7970?

Since this game is running in Wine, have you tried different versions of Wine inside PlayOnLinux? It's very easy to do. At the top of POL, there is a Tools -> Manage Wine versions. By clicking this, you can install any Wine whether new or old, patched or default. I'd suggest trying out a newer version of Wine, such as 1.5.28 or better yet try the different patched Wines with Diablo3 suffixed to them.

Now that you have another version of Wine installed or more, highlight your Diablo3 in POL. Then click the Configure button. Under the General tab, you can see Wine version drop down box. Here is where you can select the version of Wine Diablo3 will run in. Just choose one, and run Diablo3 again. POL will automatically update your installation to make it use that selected Wine version.

An alternative would also be to try CrossOver 12.1. I use it myself, and it's pretty solid in terms of performance. However, it's not free like PlayOnLinux, though you can try a trial version for free. Just take note, AMD's Linux drivers are really horrible. I had to ditch my 6850 after Catalyst 12.11 was just continuing to regress. Even if all the software you're using is good, if AMD's driver is the failing part we can't do anything about it.

---

### Post by Perfect Storm on 2013-04-24
Moved to wine section.

---

### Post by hydrizl on 2013-04-24
> **myromance123 said:**
> Do you mean a 7970?

Since this game is running in Wine, have you tried different versions of Wine inside PlayOnLinux? It's very easy to do. At the top of POL, there is a Tools -> Manage Wine versions. By clicking this, you can install any Wine whether new or old, patched or default. I'd suggest trying out a newer version of Wine, such as 1.5.28 or better yet try the different patched Wines with Diablo3 suffixed to them.

Now that you have another version of Wine installed or more, highlight your Diablo3 in POL. Then click the Configure button. Under the General tab, you can see Wine version drop down box. Here is where you can select the version of Wine Diablo3 will run in. Just choose one, and run Diablo3 again. POL will automatically update your installation to make it use that selected Wine version.

An alternative would also be to try CrossOver 12.1. I use it myself, and it's pretty solid in terms of performance. However, it's not free like PlayOnLinux, though you can try a trial version for free. Just take note, AMD's Linux drivers are really horrible. I had to ditch my 6850 after Catalyst 12.11 was just continuing to regress. Even if all the software you're using is good, if AMD's driver is the failing part we can't do anything about it.Yeah I did mean 7970, haha. I'm going to keep trying different wine versions and report back here. I hope its not a driver issue but I have a feeling it might be.

---

### Post by hydrizl on 2013-04-26
Well I figured out my issue. I thought I'd post my solution in case someone else has a similar problem. I downloaded the cpufreq package and checked my core speeds while in D3.  It turns out only 2 of my cores were at max capacity while playing (which explains why the core affinity did not help past two cores). So I changed the governor to performance for the other cores I was using and now my FPS shot up. I'm glad I'm able to play the game on linux now, one less reason to boot into windows :p

---

### Post by ryan.oflaherty on 2013-08-11
Thank you sir I have been pulling out my hair trying to figure what to do about the low FPS. Im newer to linux and just formatted my Windows HD with Ubuntu 12.04. Thanks alot sir!

---

### Post by petsoukos on 2013-08-15
> **hydrizl said:**
> Well I figured out my issue. I thought I'd post my solution in case someone else has a similar problem. I downloaded the cpufreq package and checked my core speeds while in D3.  It turns out only 2 of my cores were at max capacity while playing (which explains why the core affinity did not help past two cores). So I changed the governor to performance for the other cores I was using and now my FPS shot up. I'm glad I'm able to play the game on linux now, one less reason to boot into windows :p

Can you post a step-by-step guide of sorts on how to do that?

---

### Post by ryan.oflaherty on 2013-08-21
```
sudo apt-get install indicator-cpufreq
```

You may have to logout then log back in to see the indicator. The cpu indicator should appear at the top right hand corner and it sort of looks like an SD card. There you can set your CPU for performance. Before installing the cpufreq I could lower all the D3 settings and still be getting 20 FPS  and now I get 50-60 FPS which was better than my windows machine.

---

### Post by texaswriter on 2013-08-23
I've been a fan of AMD graphic cards for a long time, but I have had nothing but problems with them and gaming since I moved to Linux. I use NVidia now + proprietary driver to run Linux native games and win32 games on Linux. Have much better luck.

---

