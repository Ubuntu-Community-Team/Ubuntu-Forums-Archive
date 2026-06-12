---
title: "Losing my marbles getting WoW 1.12.1 to work in Ubuntu 12.04 SMOOTHLY"
date: 2013-01-14
forum: Wine
---

### Post by chrisdku on 2013-01-14
Ok. Here it goes. I just recently installed Ubuntu 12.04 (32 bit) onto my macbook pro 8.3. I know that in itself sounds like a pain in the ***, and to an extent it was. I downloaded the 12.10 catalyst drivers from AMD after trying the ones in additional drivers and getting the same result. Bit of back story. I first installed wine then wow 1.12.1 and it looked great as far as smoothness and FPS but there were NO characters or objects so I finally figured that out and entered the command given from the website on wowwiki about it into my config.wtf file. Then I tried to play and noticed it just wasn't that smooth. I ended up tinkering a ton and getting barely anywhere. As it stands I have 12.10 drivers, about 40-75 FPS BUT it does not look smooth at all. It feels choppy and just not right. I have every single setting at the lowest aside from resolution and I am using 24 bit color with 1 sampling. I took a look around youtube and ran into this.

[http://www.youtube.com/watch?v=XyeQpUZ8sZo](http://www.youtube.com/watch?v=XyeQpUZ8sZo)

This guy is running it years back on wine and it runs like butter! It infuriates me to know I have the specs I do and can't even run it smooth on the lowest settings =\. I'm unsure of what to do here. I am playing the original game on a private server and it ran perfect on windows with max settings but I don't want to run windows. I have tried the set it to opengl command in my config.wtf and quite a few other things but I am out of ideas.

Here are my specs and some info you probably need:

Macbook Pro 8.3 17"
Intel i7 2720QM @ 2.20ghz x8
16 GB of memory
128GB SSD
Radeon HD 6750M 1024 MB memory (although I noticed when running steam on full screen it yelled at me for only having 268MB.)

Wine 1.5.21

Terminal Output:

chrisurban@Matilda:~$ wine /home/chrisurban/.wine/drive_c/Program\ Files/World\ Of\ Warcraft\ Classic/Wow.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee30,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f18c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f640,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f640,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f0b0,0x00000000), stub!
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit [http://ubuntuforums.org/showthread.php?t=1960599](http://ubuntuforums.org/showthread.php?t=1960599)
fixme:imm:ImmReleaseContext (0x20024, 0x150c58): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32e440,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e490,0x00000000), stub!

I have installed PlayonLinux and tried to install wow 1.12.1 through it but it never ran it. I also tried this horribly extensive guide on installing direct x to run wow on as I read in the old WineHQ database that it "ran in d3d much better." I failed horribly at installing directx. Anyone out here into the vanilla version of wow and able to help me? Thanks so much and sorry if I forgot something or didn't follow protocol. Let me know if I need to include anything else.

P.S. I noticed there was a sound error in that terminal. I am less concerned about sound but fixing it would be nice.

---

