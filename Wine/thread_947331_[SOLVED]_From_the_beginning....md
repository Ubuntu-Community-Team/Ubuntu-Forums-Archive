---
title: "[SOLVED] From the beginning..."
date: 2008-10-14
forum: Wine
---

### Post by RJWEcology on 2008-10-14
Ok, I really want to get Wine working along with my Steam games. I have PlayOnLinux 3.1.2 installed along with Wine 1.1.5 (installed through PlayOnLinux). I have some of my Steam games installed (HL2, CS:S) and Steam seems to run fine. The only issue I'm having is a strange graphical one. I've uploaded a pic taken when HL2 loads. 

Screen pic: [http://i472.photobucket.com/albums/rr83/RJWEcology/DSC01411.jpg](http://i472.photobucket.com/albums/rr83/RJWEcology/DSC01411.jpg)  

My fglrxinfo says: 

```
root@Obsidian:/home/rich# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7659 Release
```

This is my ATI Catalyst info: [http://i472.photobucket.com/albums/rr83/RJWEcology/catalyst.png](http://i472.photobucket.com/albums/rr83/RJWEcology/catalyst.png)

I'm trying to be as detailed as possible so I can explain my situation. I also have another question. I chose to download the ATI drivers using EnvyNG (8.6 drivers) but why does my ATI Catalyst info say 8.50.3 ? 

Am I missing something important? Is my ATI card just crap? (it ran perfect under windows). Can anyone recommend what I should do?

Any help would be greatly appreciated.

Thanks, 

Rich

---

### Post by RJWEcology on 2008-10-15
Bump :(

---

### Post by asdfoo on 2008-10-15
> **RJWEcology said:**
> Ok, I really want to get Wine working along with my Steam games. I have PlayOnLinux 3.1.2 installed along with Wine 1.1.5 (installed through PlayOnLinux). I have some of my Steam games installed (HL2, CS:S) and Steam seems to run fine. The only issue I'm having is a strange graphical one. I've uploaded a pic taken when HL2 loads. 

Screen pic: [http://i472.photobucket.com/albums/rr83/RJWEcology/DSC01411.jpg](http://i472.photobucket.com/albums/rr83/RJWEcology/DSC01411.jpg)  

My fglrxinfo says: 

```
root@Obsidian:/home/rich# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7659 Release
```

This is my ATI Catalyst info: [http://i472.photobucket.com/albums/rr83/RJWEcology/catalyst.png](http://i472.photobucket.com/albums/rr83/RJWEcology/catalyst.png)

I'm trying to be as detailed as possible so I can explain my situation. I also have another question. I chose to download the ATI drivers using EnvyNG (8.6 drivers) but why does my ATI Catalyst info say 8.50.3 ? 

Am I missing something important? Is my ATI card just crap? (it ran perfect under windows). Can anyone recommend what I should do?

Any help would be greatly appreciated.

Thanks, 

Rich

It makes me very concerned that you are a root, but that is another issue...

It's not your card that is really crap (ok, it might be a few years old) but it's more the drivers that ATI release, they're just not very good compared to the windows drivers or nVidia's drivers on GNU/Linux.


If you can figure out your driver version problem (ie, that you are running the latest) then you should check the AppDB entry for the game and run with any recommended commandline switches etc.

---

### Post by RJWEcology on 2008-10-15
I've done that already. I've set the switches they recommended on the site but I've still had the same problems. 

I actually have another question. How do I change / edit my monitor type? I think it may be the problem. I just tried to load Doom 3 and it loaded the same blocky resolution and I got the OSD saying 'Out of Range'. I might need to change my monitor type / default resolution. That may fix the problem. Any suggestions?

---

### Post by RJWEcology on 2008-10-16
I solved it! It WAS the monitor setup that was messing with everything. HL2 had always worked!!! I had to configure my monitor in 'Screens & Graphics' and then install EnvyNG again. At least it's all working nice now.

---

