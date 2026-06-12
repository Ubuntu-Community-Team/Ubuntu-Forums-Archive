---
title: "Star Wars: Knights of the Old Republic - WINE - Ubuntu 12.04 LTS"
date: 2012-11-04
forum: Wine
---

### Post by Starminn on 2012-11-04
I am trying to get Star Wars: Knights of the Old Republic (the RPG, not the MMO) to work on my system, but I seem to be running into difficulties.

This is with plain WINE. I have tried PlayOnLinux and CrossOver as well to no avail, so I am back to plain WINE.

The game installs and launches fine, however when I get past the intro "credits" (which play flawlessly) to the Main Menu, practically all meshes/textures are gone. I have attached screenshots to illustrate this.

Any assistance would be appreciated.

System Specs:
OS: Ubuntu 12.04 LTS
CPU: Intel Pentium 4 3.0GHz with HyperThreading
RAM: 4.5GB
Video Card: ATI Radeon X600 (128MB)

WINE Version:
```
robert@robert-Dell-DE510:~$ wine --version
wine-1.5.16

```
-NOTE: It is the absolute most recent one from the WINE PPAs -- not the standard Ubuntu repositories still on (I think) wine-1.4, although I tried that as the default, which didn't work; ergo my upgrading.

Screenshots:
Main Menu: [http://imagebin.org/234587]("http://imagebin.org/234587")
Character Creation: [http://imagebin.org/234588]("http://imagebin.org/234588")


Terminal Output:
```
robert@robert-Dell-DE510:~/.wine/drive_c/Program Files/LucasArts/SWKotOR$ wine swkotor.exe 
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599
fixme:dsound:DSOUND_WaveFormat Limiting channels to 2 due to lack of multichannel support
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x30ae2dc,0x00000000), stub!
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x30ae2dc,0x00000000), stub!
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x30ae2dc,0x00000000), stub!
```

---

### Post by anarchticgrimm on 2012-11-06
Hey,

May I ask which registry keys do you have in your Wine Regedit?

---

### Post by Starminn on 2012-11-08
> **anarchticgrimm said:**
> Hey,

May I ask which registry keys do you have in your Wine Regedit?

That would make for a lot of keys to list off, 'eh?

Whatever the defaults are.

---

### Post by anarchticgrimm on 2012-11-08
> **Starminn said:**
> That would make for a lot of keys to list off, 'eh?

Whatever the defaults are.

[I]Not exactly =)

Under "HKEY_CURRENT_USER/Software/Software/Wine" have you ever made a Key named 'Direct3D'? If so, is there any registry key named "OffscreenRenderingMode" or any others?[/I]

**Edit!** I've just remembered that problem. Could you please install driconf from Software Center and go into Image section and switch the S3TC texture compression to Yes?

That should help you with your problem.

---

### Post by holastickboy on 2012-11-12
Your video card does not seem to make the minimum system requirements for the game.  The website says that you need a minimum of an X1800 for radeon, and you appear to be using an X600, which is not only a generation before the minimum, but also significantly slower than the minimum.

This is from their official website:
> Processor:
 
[LIST]
[*]AMD Athlon 64 X2 Dual-Core 4000+ or better
[*]Intel Core 2 Duo 2.0GHz or betterOperating System:
[*]Windows XP Service Pack 3 or later
[/LIST]
 RAM:
 
[LIST]
[*]Windows XP: 1.5GB RAM
[*]Windows Vista and Windows 7: 2GB RAM
[/LIST]
 Note: PCs using a built-in graphical chipset are recommended to have 2GB of RAM.
*Star Wars*: The Old Republic requires a video card that has a  minimum of 256MB of on-board RAM as well as support for Shader 3.0 or  better. Examples include:
 
[LIST]
[*]ATI X1800 or better
[*]nVidia 7800 or better
[*]Intel 4100 Integrated Graphics or better
[/LIST]


While most people might say "well it will probably run with reduced frame rate", the X600 does not support the shader model 3 architecture that the game needs to even run.  Perhaps this might be the reason why you are having rendering related errors?

---

### Post by Starminn on 2012-11-15
> **holastickboy said:**
> Your video card does not seem to make the minimum system requirements for the game.  The website says that you need a minimum of an X1800 for radeon, and you appear to be using an X600, which is not only a generation before the minimum, but also significantly slower than the minimum.

This is from their official website:


While most people might say "well it will probably run with reduced frame rate", the X600 does not support the shader model 3 architecture that the game needs to even run.  Perhaps this might be the reason why you are having rendering related errors?

I think you have the wrong idea -- if I'm not mistaken, you seem to have assumed that I am trying to play "Star Wars: The Old Republic" when I am not. What I AM trying to play is "Star Wars: Knights of the Old Republic". As much is stated in the original post:

> I am trying to get Star Wars: Knights of the Old Republic (**the RPG, not the MMO**) to work on my system...

I am sorry for any confusion that has occurred.

---

### Post by quentinl on 2012-11-15
does it need direct x?
cause if it does i don't think it'll work

---

### Post by Starminn on 2012-11-15
> **anarchticgrimm said:**
> [I]Not exactly =)

Under "HKEY_CURRENT_USER/Software/Software/Wine" have you ever made a Key named 'Direct3D'? If so, is there any registry key named "OffscreenRenderingMode" or any others?[/I]

**Edit!** I've just remembered that problem. Could you please install driconf from Software Center and go into Image section and switch the S3TC texture compression to Yes?

That should help you with your problem.

I have installed DRIconf, but under the "Image Quality" section there is nothing mentioning anything about "compression." Perhaps I am overlooking it?

Additionally, I do not have any such keys under regedit.

Screenshot: [http://imagebin.org/235960]("http://imagebin.org/235960")

---

### Post by anarchticgrimm on 2012-11-15
> **Starminn said:**
> I have installed DRIconf, but under the "Image Quality" section there is nothing mentioning anything about "compression." Perhaps I am overlooking it?

Additionally, I do not have any such keys under regedit.

Screenshot: [http://imagebin.org/235960]("http://imagebin.org/235960")

Hey,

Now I'm completely sure this is a texture compression problem since you don't have additional keys in your regedit.

Under Image Quality section, there should be an option for S3TC.

Just like this; (this might be an old version but there must be such option)
[IMG]http://www.codemadness.nl/downloads/screenshots/driconf.png[/IMG]

---

### Post by Starminn on 2012-11-15
> **anarchticgrimm said:**
> Hey,

Now I'm completely sure this is a texture compression problem since you don't have additional keys in your regedit.

Under Image Quality section, there should be an option for S3TC.

Just like this; (this might be an old version but there must be such option)
[IMG]http://www.codemadness.nl/downloads/screenshots/driconf.png[/IMG]

Here are some screenshots of what I'm looking at:

[http://imagebin.org/236087]("http://imagebin.org/236087")
[http://imagebin.org/236088]("http://imagebin.org/236088")

Might it be possible that my graphics card simply doesn't support this option, therefore it is not being shown? Or perhaps since mine may be a newer version it has been phased out? (Under "Expert Mode" there are not any additional settings)

---

### Post by anarchticgrimm on 2012-11-15
Now that is odd. Or maybe it's because of ATI.

When I searched for the exact same problem few years ago, this was the solution. Yet, I have KoTOR and KoTOR-II on this system and without this solution I'm having this problem too.

Since I don't have an ATI card, I can't be %100 sure but that first option in Image Section may be your solution as well. Because this common problem is absolutely about texture compression. Please take a look if you can solve your problem via changing "At least 1 texture must fit under worst-case assumptions" option.

---

### Post by Starminn on 2012-11-15
> **anarchticgrimm said:**
> Now that is odd. Or maybe it's because of ATI.

When I searched for the exact same problem few years ago, this was the solution. Yet, I have KoTOR and KoTOR-II on this system and without this solution I'm having this problem too.

Since I don't have an ATI card, I can't be %100 sure but that first option in Image Section may be your solution as well. Because this common problem is absolutely about texture compression. Please take a look if you can solve your problem via changing "At least 1 texture must fit under worst-case assumptions" option.

I set it to the other options, "No," and, "Announce hardware limitations," and tried it again to no avail.

---

### Post by anarchticgrimm on 2012-11-16
> **Starminn said:**
> I set it to the other options, "No," and, "Announce hardware limitations," and tried it again to no avail.

Then, Wine Application Database may have the answers. - According to [these]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4124&iTestingId=69386") testing results;

> force_s3tc_enable=true wine /path/to/kotor/swkotor.exe

may help with texture compression problems.

---

### Post by Starminn on 2012-11-16
> **anarchticgrimm said:**
> Then, Wine Application Database may have the answers. - According to [these]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4124&iTestingId=69386") testing results;



may help with texture compression problems.

Aha! That did it, man! I was actually trying this method earlier, but I forgot that I need "wine" in there since it was a .exe file.

My many thanks to you!!! :)

Marking as [SOLVED], but first a quick summary of the finished product for others searching....

---

Scenario:
Trying to run "Star Wars: Knights of the Old Republic" (NOT the online MMO -- rather, the single-player RPG).

Problem:
Upon running the .exe, the "splash screen credits" (LucasArts, BioWare, etc.) ran fine, but the menu had a white background and all 3D models were lacking textures of any kind. Additionally, many text objects appeared as blobs or blocks instead of letters.

Conclusion:
After the help of this forum, it was discovered that S3TC texture compression was disabled by default for me. DRIConf ("3D Acceleration") did not present this option to me. Somehow I must enable S3TC texture compression.

The Solution:
When running the .exe, use the command line tool "force_s3tc_enable=true" BEFORE the rest of the NORMAL command to run the file. In my case, the following is run:
```
force_s3tc_enable=true wine /home/robert/.wine/drive_c/Program\ Files/LucasArts/SWKotOR/swkotor.exe

```

Setup Notes:
-Using the latest game version (1.0.3)
-No custom registry keys have been added.
-WINE is configured to run in Windowed mode, so none the of "disable certain mouse settings" apply.
-As far as game configuration goes, the default game settings appear to work just fine.
-The game disc is Disc 1 and is mounted manually from an .iso for the sake of a speed increase. This should be no different than from a physical CD/DVD, though.

---

### Post by anarchticgrimm on 2012-11-16
I'm glad it solved. Still, there should be such option to enable s3tc texture compression as default.

Anyway, have fun =)

---

