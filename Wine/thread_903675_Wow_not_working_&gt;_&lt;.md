---
title: "Wow not working &gt;_&lt;"
date: 2008-08-28
forum: Wine
---

### Post by limitaten on 2008-08-28
I'm very new to linux, just installed it two days ago. Installed Wine from the add/remove thing. And downloaded WoW and installed it. 

When I run WoW from the Icon or through the terminal with opengl my laptop screen goes black(have a desktop monitor plugged into the vga port)and my other screens resolution goes down. I figured it would be my graphics drivers. but I don't know what chipset I have, hanks to the fact that ubuntu doesn't seem to have a device manager in its latest version. I do know its an intergrated intel, but not sure what kind. 

> Use the restricted drivers for your video card - many graphics issues in Wine are due to missing features in the free drivers for various video cards. Try enabling the proprietary drivers for your video card, if available, using the restricted drivers manager.

I have no idea were any of that is. And if I find out what kind of drivers I need, I know I won't be able to install them.

I have no idea how to find out my wine version. 

Termal output is

> fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8dd, disabling mixer
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec74,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f278,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f124,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x135030) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x133f58) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x32efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f124,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
wine: Unhandled page fault on write access to 0x00000004 at address 0x7bc43714 (thread 0009), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc43714


When i try to set a resolution for wow in the wine config, wow starts up in a 800x600 res but shuts off shortly after. heres the terminal output

> fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8dd, disabling mixer
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec74,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f278,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f124,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x135140) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x134068) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x32efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f124,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22


OS Version for wow - XP
All other settings are default



Hope someone can help me, i wanna play wow and raid :(

---

### Post by unca.paka on 2008-08-28
First of all, click on System --> Administration --> Hardware Drivers, and see if your video card is detected in there. If so, check the Enabled box. That should get your vid. drivers up and running. You should have the newest version of Wine if you installed from the repos(1.0). You can check by opening a terminal, and using,
```
wine --version
```

Second, check out this how-to, lots of useful info for getting WoW up and running.
[https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")

---

### Post by limitaten on 2008-08-28
Well, i check the Hardware Drivers. There is nothing in there at all. So I'm guessing I don't have any drivers for my graphics. 

And I am running wine 1.0 

Last, I have been to that site and followed al lthe instructions except for the config.wtf file part, because it doesnt exist till i get the game up and running. but i load with opengl. think it does the same thing. Also did the registry config thing. didnt change anything. (pretty sure thats just for framerates)

---

### Post by kdorf on 2008-08-28
I'm going to assume you're starting with a default install of Ubuntu 8.04 since you don't seem to have the knowhow to change things around.

First things first, if you haven't read [this]("http://ubuntuforums.org/showthread.php?t=885111") yet, you should.

> When I run WoW from the Icon or through the terminal with opengl my laptop screen goes black(have a desktop monitor plugged into the vga port)and my other screens resolution goes down. I figured it would be my graphics drivers. but I don't know what chipset I have, hanks to the fact that ubuntu doesn't seem to have a device manager in its latest version. I do know its an intergrated intel, but not sure what kind.

You'll note in that sticky that one of the things it says before asking for help is "search for an existing howto." That applies to more than just Wine. In fact, a Google search for "linux list hardware" will tell you exactly what you want to know. [http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=EVm&q=linux+list+hardware&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=EVm&q=linux+list+hardware&btnG=Search) -> [http://www.cyberciti.biz/faq/linux-display-information-about-installed-hardware/](http://www.cyberciti.biz/faq/linux-display-information-about-installed-hardware/)

Notice that is the first result. It took me less than five minutes to find that information.

You also claim that you don't know how to enable hardware drivers. You clearly haven't spent time looking for it. On a default Ubuntu 8.04 install, it's in System > Administration > Hardware Drivers. I never would've guessed to look there. There (I think) are drivers for your Intel card there.

And back to the sticky: did you read an existing howto? A Google search of "ubuntu world of warcraft" -> [http://www.google.com/search?q=ubuntu+world+of+warcraft&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=ubuntu+world+of+warcraft&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a) and once again, the first result is something that will probably help. [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

You would do well to read the link in my sig. Thanks.

---

### Post by unca.paka on 2008-08-28
As kdorf suggedted, lets do some research. Did your laptop come with documentation? If so, check it out and see if it lists the your video card. If it doesnt, google your laptop model to find out which one your using.

After thats done, use google and these forums to find out if theres any issues with it, if its supported natively, or if you need to manually install drivers for the device.

---

### Post by limitaten on 2008-08-28
kdort, you assume to much. If you read my post then you know i read the before asking thread. I did a google search but couldn't find anything. I searched for things like "Device manager" and found out ubuntu doesn't have this feature. But thank you for the site(even though the commands don't work). I would of not thought of searching for that phrase.

> You also claim that you don't know how to enable hardware drivers. You clearly haven't spent time looking for it. On a default Ubuntu 8.04 install, it's in System > Administration > Hardware Drivers. I never would've guessed to look there. There (I think) are drivers for your Intel card there.

If you had taken the time to read other posts in my thread. you would already know what I'm going to say. But I'll say it again. There are no drives in the hardware drivers. It is completely empty.

> And back to the sticky: did you read an existing howto? A Google search of "ubuntu world of warcraft" -> [http://www.google.com/search?q=ubunt...ient=firefox-a](http://www.google.com/search?q=ubunt...ient=firefox-a) and once again, the first result is something that will probably help. [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)  
Once again you failed to read. Someone had alrdy suggested it to me(in a less rude way). Even though I had alrdy been through all of it before they had even asked me. The reason I'm asking for help is because I'm at the end of my rope. Thanks

---

### Post by limitaten on 2008-08-28
> As kdorf suggedted, lets do some research. Did your laptop come with documentation? If so, check it out and see if it lists the your video card. If it doesnt, google your laptop model to find out which one your using.

After thats done, use google and these forums to find out if theres any issues with it, if its supported natively, or if you need to manually install drivers for the device.

Well, as of now, I know it is an intel intergrated chipset. Been looking on google for about 40 minutes to findout what chipset I have but no luck. Not really sure what to search for. I know when i had vista I used a graphics accelrator. But thats about it. I'll keep looking though

Update : Found it
> Graphics: Intel Graphics Media Accelerator 950, Up To 224 MB Shared

so I'm guessing i just search this up on the forums.

also used the command 
> $ lspci | grep Graphic


got back 
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

so, i dunno, if its updated or not. going to keep looking

---

### Post by unca.paka on 2008-08-28
Just throw your laptop model into google(inspiron 6000 specs for example)
You could also try copying config.wtf from your windows partition to the WoW directory on your linux parition, edit it to use opengl, and see what results you get there.

---

### Post by limitaten on 2008-08-28
Yea, thats what I did, I updated my last post with the type of chipset and all I have. Also checked if i Had direct rendering on, and I do. I do not have a vista partition. Vista  died, and i threw in my ubuntu cd because I lost my vista cd :-P Or I'd be running both.

---

### Post by unca.paka on 2008-08-28
Try running WoW with just the laptop screen(unplug your lcd), and let us know what happens.

---

### Post by limitaten on 2008-08-28
> **unca.paka said:**
> Try running WoW with just the laptop screen(unplug your lcd), and let us know what happens.

same results. reason i dont use my labtop screen is because theres a huge crack in the middle, covers the center

---

