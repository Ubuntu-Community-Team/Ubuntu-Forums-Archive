---
title: "EQ 2 now working on WINE"
date: 2007-12-07
forum: Wine
---

### Post by Faud on 2007-12-07
Gratz to all of you Everquest Fans. EQ 2 is now working with the newest version of WINE.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=358](http://appdb.winehq.org/objectManager.php?sClass=version&iId=358)

---

### Post by Faud on 2007-12-14
Requirements: Please make sure your system meets these specs. 

MUST have wine > 0.9.49. Everquest 2 will not work with earlier wine versions. 

Runs slowly, if at all with 512MB RAM. 1GB+ recommended. 
Graphics cards that support pixel shaders 3.0 are known to work: refs: [http://en.wikipedia.org/wiki/Pixel_shader](http://en.wikipedia.org/wiki/Pixel_shader) 

GeForce series 6+ 
Intel GMA 950+ 
Radeon R520+ (X1300+) 
Todo: test SiS Mirage 4 
glxinfo | grep direct # should say yes. If not, check your distro's docs for setting up accelerated video drivers. 

Rename .wine folder (if you have just upgraded wine) mv .wine wineold 
run winecfg. Set up your audio tab. Alsa emulation works in most cases. 
GLSL and pixel shaders are enabled by default now. I needed no special registry tweaks. 

Install, or copy working game folder from windows partition. 
Wine_gecko crashes the patcher screen (no BITS support in wine yet. See bug 6253) so if you want to run patcher, rename the HKCU/wine/MSHTML/x.x.x/GeckoPath registry key temporarily or just don't install wine_gecko in the first place. 

Patch the game: wine explorer /desktop=eq2,1024x768 eq2.exe 

Add r_font_ft 0 to eq2_default.ini 
Change cl_fullscreen 1 to cl_fullscreen 0 . The game crashes when run fullscreen with a "what to do" error. 

Save and back up your eq2_default.ini . cp eq2_default.ini eq2_default.ini.ok  . It will be erased next time you patch the game so you will have to copy it back. 

Skip the patcher by running everquest2.exe directly from the command line: wine explorer /desktop=eq2,1024x768 everquest2.exe 


If you have any questions getting it working, please post them here and I'll do the best I can to get you up and running =)

---

### Post by brento73 on 2008-04-18
Is there no way to just get that font loaded so you don't have to mess with the ini every time?

---

### Post by javafiend on 2008-04-29
> **brento73 said:**
> Is there no way to just get that font loaded so you don't have to mess with the ini every time?

Yes.

I added 'r_font_ft 0' and 'cl_fullscreen 0' to my EQ2.ini file.  I'm not sure, but EQ2.ini seems to have some sort of precedence over EQ2_default.ini.

---

### Post by jbysmith on 2008-04-29
Hmm good to know, thanks for the heads up on EQ2.

I've been bored to tears lately with World of Warcraft, and Guild Wars I only play every so often when the mood hits me.  May have to reactivate my old EQ2 account and give it another go for a change of pace.

Before I spend some cash on my account, have you tried it? How's the performance?  I recall EQ2 being a heavy hitter on the video card when running natively on XP.  I'm of course not expecting perfection, but if it runs at an acceptable speed I'm gonna have to try it again. I miss my old wood elf shadowknight.

---

### Post by javafiend on 2008-04-29
I've been running it for 2 months or more (I think) and haven't really had any show stopping issues.  There is lots of info at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=358](http://appdb.winehq.org/objectManager.php?sClass=version&iId=358).  

One thing that is easy to miss is that I had to use the Linux kernel version 2.6.24-15 (ref this post [http://ubuntuforums.org/showpost.php?p=4701618&postcount=36](http://ubuntuforums.org/showpost.php?p=4701618&postcount=36) on tabula rasa).  It may be the same case for you or may not.

---

### Post by zir0n on 2008-04-29
Hi all,

I've been trying to get EQ2 to run. I don't get the font issue anymore when adding the changes to the eq2_default.ini but after i run wine explorer /desktop=eq2,1024x768 EverQuest2.exe my system becomes unrecoverable. mouse freezes and can't do anything but reisub the thing. I do hear the music in the background and my terminal out put ends on a list of:

```
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
...
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #3: "Fragment shader(s) linked, vertex shader(s) linked. \n "

```
i'm running:
Hardy 8.04 kernel 2.6.24-16-generic
wine-0.9.60
IBM thinkpad with an ati radeon mobility x1400

---

### Post by Ittindi on 2008-12-03
The only two files that I had in my folder were eq2_default.ini and eq2_recent.ini.  If I changed the default file then the patcher would change it back every time.  So I created my own eq2.ini file.  The only line I have is r_font_ft 0 and now everything is running smoothly (fast load times, great frame rates, graphics almost maxed out.)  Look me up.

Ittindi
Froglok Dirge on Antonia Bayle

---

