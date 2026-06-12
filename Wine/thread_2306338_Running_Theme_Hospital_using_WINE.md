---
title: "Running Theme Hospital using WINE"
date: 2015-12-14
forum: Wine
---

### Post by ian104 on 2015-12-14
Hello

An odd request... I think I've succesfully installed Theme Hospital using wine, however we I attempt to run the game using the command wine "Hospital.exe" -opengl all I get is blank screen?

I'm sure I'm missing a trick somewhere, but not sure where! Any help would be amazing

ian

---

### Post by ian104 on 2015-12-14
I get this output from the terminal, if it helps

```
 fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x14adfa8,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x8 @0! (XRandR 1.2)
```

---

### Post by kostkon on 2015-12-14
The best way to run Theme Hospital is by using [CorsixTH]("https://github.com/CorsixTH/CorsixTH/"). Since they don't provide packages (they used to) you'll have to hunt one down yourself. There is [one on playdeb.net]("http://www.playdeb.net/app/corsix-th").

I'll save you some trouble and give you [the direct url to the deb packages]("http://archive.getdeb.net/ubuntu/rpool/games/c/corsix-th/") (corsixth and corsixth-data) so that you won't have to add their repo just for this one application.

By the way, why are you trying to pass the -opengl parameter to wine?

Hope that helps.

---

### Post by ian104 on 2015-12-14
Hi. Thanks for your help. I'll give that a go. I had read that was the best way to run games with wine, have I misunderstood?

---

### Post by kostkon on 2015-12-14
> **ian104 said:**
> Hi. Thanks for your help. I'll give that a go. I had read that was the best way to run games with wine, have I misunderstood?
Generally, the best way to run Windows games is to either use Wine or PlayOnLinux (which is also based on Wine), DOS games (Theme Hospital is a DOS game, by the way) run better in DOSBox, etc. etc. for other systems...

In this case though, CorsixTH appears to be a better choice.

---

### Post by ian104 on 2015-12-14
I've tried opening the exe file with wine, but I still get a blank scree. Are there settings in wine I need to adjust? I've some other old games id like to try. It sound like I'm not using wine correctly?

---

### Post by kostkon on 2015-12-15
> **ian104 said:**
> I've tried opening the exe file with wine, but I still get a blank scree. Are there settings in wine I need to adjust? I've some other old games id like to try. It sound like I'm not using wine correctly?
You should give [PlayOnLinux]("https://www.playonlinux.com/") a try, which is a much friendlier front-end for Wine.

---

### Post by ian104 on 2015-12-17
Hello, thanks for your help. I tried that but got another error whilst installing. I think it's clear I've got a bit to learn about Linux,  will read up over Christmas. In the meantime I've got my netbook to dual boot to xp until I get the hang of ubuntu! Thanks for helping out

---

