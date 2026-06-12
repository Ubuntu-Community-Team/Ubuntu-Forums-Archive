---
title: "NVIDIA Driver nightmare x-64"
date: 2007-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sm0ke42o on 2007-08-08
Hello new to the forums and to ubuntu. I have researched this topic and exhausted all options otherwise I would not post. I have reinstalled countless times and rebooted hundreds. Hopefully someone can help.

I am running an AMD-64, 1 gig of RAM, a 6600 GT, and an Audigy 2ZS Platinum. 3 HDD's with Windows on one, one for storage, and Ubuntu 64bit on the other. Samsung SyncMaster 730b LCD

My problem is this; I switched from PCLinuxOS to take advantage of the 3D fun Ubuntu had to offer. However the first time I went to mess with the desktop and was prompted to enable the NV restricted drivers I ran into the issue. When I rebooted I reached the Ubuntu Splash but after the loading bar completed I was taken to a blank screen. this is where my problem differs from others, instead of the blank screen where one can hear the sound queue, I was simply taken to a blank screen, no sound ever. I tried entering my login info to see if I could proceed into the desktop but as far as I could tell it didn't work. So I used the command to reset my x config to defaults and returned to the desktop and tried NVIDIA's latest forceware (100.14.11) and got the same result. After trying the forceware and reseting my x config I began getting the "failed to initialize HAL" error on startup which I was unable to remedy. So I reinstalled and tried with Envy; same result, same HAL error, another futile attempt to fix it, another reinstall. Needless to say i gave up due to the HAL error, as I got tired of reinstalling to fix it and also having to revert back to the basic driver after the config reset. I would appreciate any help offered. Thanks.

---

### Post by kuja on 2007-08-09
Which version of Ubuntu did you try with? Maybe if you use a different version (like Edgy or perhaps Dapper) it will work. (My thoughts are that it could be a bug in hal)

---

