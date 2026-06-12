---
title: "Is my WoW issue unresolvable?"
date: 2012-11-11
forum: Wine
---

### Post by manopapalex on 2012-11-11
I'm a completely new user to Ubuntu 12.10, so i apologise if i don't provide the necessary information or use appropriate terminology. If i don't; chances are i don't know how! But i will try to update this as often as possible if anyone could be generous enough to provide me with steps to resolve my issue.

Thanks in advance!

----

Basically, i have World of warcraft installed on an external hard drive and i am able to play it through wine ('browse c: drive'), however it only plays on the lowest settings (with a low framerate) citing 'Unsupported for graphics related reasons' on many of the game's system options.

```
lspci -k
```returns the following output:

NVIDIA Corporation G92 [GeForce 9800 GT] (rev a2)
 Subsystem: CardExpert Technology Device 0401
 Kernel driver in use: nvidia
 Kernel modules: nvidia_current, nouveau, nvidiafb

I truly won't be bothered if the issue turns out to be unresolvable, so long as i know it's not something that can be fixed by altering my drivers or configuration settings in Wine. 

Again, i am a total beginner with this OS, and i realise it might be a pain to help me due to this, but any help would be greatly appreciated as Ubuntu is currently my sole OS.

Thanks again!

---

### Post by Dlambert on 2012-11-11
Are you using the latest Nvidia drivers?

---

### Post by Bsohm on 2012-11-11
It is because of Opengl.....direct x doesnt work well

---

### Post by Dlambert on 2012-11-11
> **Bsohm said:**
> It is because of Opengl.....direct x doesnt work well

Yes, you could be correct. Did you set the game to run with the -opengl setting?

In the config.wtf file add the following:

SET gxApi "opengl"


Other possible fixes: 


> - Open Wine's version of the registry editor by running "regedit"  - Navigate to HKEY_CURRENT_USER\Software\Wine\   - Select the "Wine" folder, right-click onto the folder symbol and select  New-> Key and rename it to "OpenGL"  - Select the OpenGL-Key, then right-click into the right-hand pane, chose New-> String Value and hit enter  - Rename "New Value #1" to "DisabledExtensions"  - Double-Click on the renamed Key and enter "GL_ARB_vertex_buffer_object" into the "value" field

---

### Post by manopapalex on 2012-11-11
> **Dlambert said:**
> Yes, you could be correct. Did you set the game to run with the -opengl setting?

In the config.wtf file add the following:

SET gxApi "opengl"


Other possible fixes:

Yes i have set the game to run in opengl through its config.wtf file, i have also added the regedit value you suggested with no change.

i'm not sure how to check that i have the latest nvidia drivers installed, i think there is an experimental 304 driver but i'm using the most current stable  version.

hmmm...

Edit: After poking around i think it's most likely the problem might be with the installed drivers. Though i wouldn't know how to remove the current and install the most recent.

---

### Post by holastickboy on 2012-11-12
You could always use the Synaptic package manager and uncheck the nvidia drivers and reboot your machine.  Afterwards, open the same program and install the nvidia-experimental, which is the 310.14 driver (I use it with WoW and get great frame rates, even through Direct x mode).

---

### Post by manopapalex on 2012-11-12
> **holastickboy said:**
> You could always use the Synaptic package manager and uncheck the nvidia drivers and reboot your machine.  Afterwards, open the same program and install the nvidia-experimental, which is the 310.14 driver (I use it with WoW and get great frame rates, even through Direct x mode).

here's a screen shot of all the nvidia driver's synaptic shows me:

[http://i.imgur.com/VlnkG.png](http://i.imgur.com/VlnkG.png)

Would you be so kind as to tell me exactly which to 'uncheck' which to leave alone and which to 'check', and when i should be rebooting in between this process?

Thanks you so much.

---

### Post by manopapalex on 2012-11-12
It was taking a while to get a response so i just went ahead and used the experimental drivers. Still the same problem of having to play WoW on low settings with low framerate. I really don't want to have to reinstall windows if this can be solved.

---

### Post by Tweak42 on 2012-11-16
> **manopapalex said:**
> It was taking a while to get a response so i just went ahead and used the experimental drivers. Still the same problem of having to play WoW on low settings with low framerate. I really don't want to have to reinstall windows if this can be solved.

If the propritary Nvidia drivers are installed correctly, you should be able to launch the nvidia settings tool gui and should tell if there is a problem, list your driver version, settings, hardware temp, monitor output etc. (hit winkey and type for nvidia to find the program)

For Wow detail settings, if you are using the opengl mode most of the settings will only run in the low or lowest,(aka 'Unsupported for graphics related reasons') this is because the opengl client does not support those graphicss features.  There also a few bugs with the Wow opengl client that [Blizzard has refused]("http://us.battle.net/wow/en/forum/topic/6712862205") to fix; one such that the player cursor does not appear on world map.

If you are using directx mode, performance will take a hit but should render correctly and the some of the detail settings will be available (most noticably the water).

In compared to windows performance linux is slower mainly caused by wine is only able to run wow on a single processor core.  This can be alleviated somewhat by brute force by just using a faster cpu and video card.

On a positive note the latest beta 310.xx series of nvidia drivers have some multi-threaded optimizations that might help framerate or they could run worse, ymmv.  I have been using them on my desktop system (i5 3.0Ghz cpu, Nvidia GTX480). see this thread:
[http://ubuntuforums.org/showthread.php?t=2071968](http://ubuntuforums.org/showthread.php?t=2071968)

---

### Post by Thee on 2012-11-16
What version of Wine are you using? I use 1.5.16 and my FPS is at playable numbers on low settings (~25fps in OG, and 30-60fps in MoP while doing quests), with no additional tweaks, except the OpenGL flag ofc. I have an ATI card, so you should be able to get better fps on Nvidia. So if you have older version of Wine, maybe try the version of Wine that I'm using.

> There also a few bugs with the Wow opengl client that Blizzard has refused to fix; one such that the player cursor does not appear on world map.

To fix this, I used the solution described here, post #18
[http://us.battle.net/wow/en/forum/topic/6712862205](http://us.battle.net/wow/en/forum/topic/6712862205)

---

