---
title: "Wrath of the lich king, d3d problems"
date: 2008-08-06
forum: Wine
---

### Post by Morph-------------- on 2008-08-06
Yey! I'm lucky and i can participate in the Wrath of the lich king beta!
Well now i got this problem, when I do the Death Knight quest with the eye, my screen blackens out in OpenGL. Well this is a bug everyone who use linux has but they say I should run it with the -d3d parameter. I've done that but now the only thin i see is glitchy, badly textured mountains so no character, no plateau or anything so this doesn't help me anything.

I'm using wine 1.1.2

Terminal Output:

```

fixme:mixer:ALSA_MixerInit No master control found on Camera, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\enGB\patch-enGB.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\lichking-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
archive Data\enGB\lichking-speech-enGB.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edc0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ecb0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f438,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub!
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexImage2D @ surface.c / 347
fixme:win:EnumDisplayDevicesW ((null),0,0x39d688,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39d6e4,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

```

Then it starts spamming this (This is at the menu, the background is black here
```

fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3418
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 411
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3418
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 411
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 411
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 411
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3418
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 411
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 411
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3418
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 411

```

Then i get this at the loading screen:

```

fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x39d284,0x00000000), stub!

```

And in game it starts spamming this:
```

fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3418
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 411

```

At this point I can't see my portrait, my character, all i see around me are blueish mountains and nametags floating around. My UI shows properly except for the portrait

---

### Post by ooobuntooo on 2008-08-07
Awsome, u got selected for the beta testing!
Why not try using windows for now if it is really important.
I run WoW in D3D mode and it runs perfectly, better than OpenGL!

---

### Post by Mistrblank on 2008-08-07
> **ooobuntooo said:**
> Awsome, u got selected for the beta testing!
Why not try using windows for now if it is really important.
I run WoW in D3D mode and it runs perfectly, better than OpenGL!

What is in your system?  I'm running a Q6600@2.4Ghz, nvidia8800gt, 4GB RAM and I can't even get the login screen to render in d3d mode on wine.

What versions of wine and video drivers are you using?

---

### Post by ooobuntooo on 2008-08-07
> **Mistrblank said:**
> What is in your system?  I'm running a Q6600@2.4Ghz, nvidia8800gt, 4GB RAM and I can't even get the login screen to render in d3d mode on wine.

What versions of wine and video drivers are you using?

HP Pavilion 453
2.4 GHz
ATI Radeon 9000
1 GB RAM
Default Ubuntu drivers (Not Envy)
WINE 1.1.2

---

### Post by Morph-------------- on 2008-08-07
> **Mistrblank said:**
> What is in your system?  I'm running a Q6600@2.4Ghz, nvidia8800gt, 4GB RAM and I can't even get the login screen to render in d3d mode on wine.

What versions of wine and video drivers are you using?

No got that problem either, not rendering the login screen, I think it's a problem with nvidea maybe, I've a GeForce 6800. The point is that I got my windows all messed up and not fixed since i never use it anymore =P I'll try to recover it and in the meanwhile I hope someone stands up to write an OpenGL fix or some other workaround! :) or find one myself i'll do my best ;)

---

### Post by flytripper on 2008-08-08
you lucky git

---

### Post by Toxicity999 on 2008-08-22
I'm in the beta too! Installing now. I'm going to try the Death Knight starting quests first thing. I'll report back in a few hours, maybe tomorrow, after I finish patching and trying it out. I have a similar system, and past bad experience with d3d on it. so we'll see. People claim it to be a Fullscreen shader issue, have you just tried disabling them in OpenGL?

---

### Post by nickgaydos on 2008-08-22
Man your lucky, I log in this morning to find my main is gone :(

---

### Post by hotballz87 on 2008-08-23
i had to update wine to the newest version to get it fully installed today, but i cant get into the login screen either, the screen changes resolution mode and then errors out. i have a nvidia 8800 gt,

i have an idea, but i need someone that is in the beta to compare their WTF folders, and see how much is different, i was thinking of copying the cnfig.wtf to the beta wtf folder, and see if that works in it

---

### Post by hotballz87 on 2008-08-23
yes. copying the WTF works, just did it and it started no problem. just copy your config.wtf file into the beta wtf folder

---

### Post by Toxicity999 on 2008-08-23
People are saying that 0.9.46 works with the new shaders, but I didn't take the time to compile it and check.

---

