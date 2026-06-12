---
title: "How To: Steam Counter-Strike Source Edgy WINE"
date: 2006-11-21
forum: Wine
---

### Post by snype on 2006-11-21
I followed a howto guide over at linux-gamers.net (I think) but I found that it was rather incomplete and at times gave me wrong commands but I ended up able to get Steam installed and run Counter-Strike Source through WINE on my Ubuntu Edgy box. My specs are: 1.7ghz 512 MB ram and a Radeon 9600 64mb graphics card(using fglrx)-- all wrapped into a sexy little IBM T42. Below is the quick run through of how I did it, the full version is on my blog: [http://t42buntu.blogspot.com]("http://t42buntu.blogspot.com")

1. Download WINE

    sudo apt-get install wine


2. Run WINE setup--

    wine setup


3. Download Tahoma font and put it in your wine fonts folder:

    cp Tahoma.ttf /home/USERNAME/.wine/drive_c/windows/fonts


4. Download Steam the go to the directory and install it

    wine SteamInstaller.exe


(Note I just took a break to test out my CSS on Linux, and after a few trial and errors i figured it out and got onto a server and played it! So, IT WORKS!) 5.During the steam install just use all the same options/answers you would use in a windows environment-- at some point it will prompt you that it needs to install a Mozilla Gecko plugin? just say yes and it will do it's own thing.
6. When the installer finishes open up a terminal and do the following to launch steam:

    cd /home/USER/.wine/drive_c/Program Files/Steam
    WINEDEBUG="fixme-all" wine steam.exe


This will launch steam while hiding any outputs from wine, thus running your game faster.
7. When steam launched I couldnt type my name in the login/password boxes without first right clicking in the login field then left clicking. After this I could login as normal.
8. Now that you're ready to launch your game you will want to make sure that all other windows besides the steam "My Games" window are minimized or closed.
9. Double click "Counter Strike Source" and as soon as it says "preparing" click the x button on the steam window with "My Games List" or it will interfere with the game.
10. The game should be running fairly close to normal now, you ay be warned that you're video is wierd and that it's using software mode, but even on my 1.7 Ghz 512mb ram 64mb Radeon 9600 the game was more than playable.



I will be fidiling around with all the settings later so check the blog for   updates on it. 

I hope this helps someone.
-Snype

---

### Post by dogwi11hunt on 2006-11-24
Im new to Linux and i dont know too much i just needed an operating system and my friend recomended Ubuntu. Anywho ive installed Wine but I can't run the wine setup.when i put it in the terminal "wine setup" it does nothing. Please help because i miss playing CS.

---

### Post by claydoh on 2006-11-24
If you simply run "wine steaminstaller.exe" it will set up a wine environment automatically and run the installer. The command "winecfg" beforehand  will open a configuration gui if you want to edit some things. Setting up drive paths for cdroms is one important task (though not needed for steam) you may want to do.

---

### Post by dogwi11hunt on 2006-11-25
I think I have the whole Wine thing down. I think. I need to install tahoma, I've downloaded it but when i try and put it in the file shown "home/John/.wine/..." in my "john" file theres no ".wine" file to send the tahoma font to. and when I search the comp for the file in general to see if its located elsewhere it cant find it. It's like certain files have yet to be created.

---

### Post by Ferrat on 2006-11-25
> **dogwi11hunt said:**
> Im new to Linux and i dont know too much i just needed an operating system and my friend recomended Ubuntu. Anywho ive installed Wine but I can't run the wine setup.when i put it in the terminal "wine setup" it does nothing. Please help because i miss playing CS.

have you done a 

```

$ winecfg 

``` 

?? 

If so just browser to your steam folder and dubbel klick on the steaminstaller.exe and it should start by it self :)

---

### Post by Ferrat on 2006-11-25
> **dogwi11hunt said:**
> I think I have the whole Wine thing down. I think. I need to install tahoma, I've downloaded it but when i try and put it in the file shown "home/John/.wine/..." in my "john" file theres no ".wine" file to send the tahoma font to. and when I search the comp for the file in general to see if its located elsewhere it cant find it. :-?

That means you haven't done a winecfg at the terminal window just do that and you get a .wine dir :) =)

---

### Post by dogwi11hunt on 2006-11-25
Well i have ran the wine configuration in the terminal. and the window popped up and i clicked on the audio tab and this came up in the terminal after the window auto matically closed "Creating link /home/john/.kde/socket-john-desktop.
can't create mcop directory" id imagine thats not good? it didn't say anything about .wine and its not that i cant run steam because ive gotten it to start but you cant see anything, which id imagine is from not having tahoma font which i thought i had. So then i tried to put on the font again and it didn't detect the "/.wine/..." directory and i remember reading you need to run wine for it to make that directory. So if im correct i need to find out how to run wine, to create that directory, just so i can put on tahoma.

---

### Post by dogwi11hunt on 2006-11-25
after messing with the wine configuration a bit in the "drives" tab i saw the .wine file and i guess its a hidden file on the computer so ive read and since its "hidden" the terminal cant find it to put in the tahoma font i think i dont know

---

### Post by maax on 2006-12-06
so steam does update...  it just take a bit... 

main feature which is missing now, is how to make shure CSS run in open-gl mode

in glxgears, i am getting 
3700 fps(windowed), 530 fps (maximized)
In the game:
40 fps average in cs:source speed test

does anyone know how to do that?

---

### Post by Brynster on 2006-12-07
CounterStrike source to the best of my knowledge doesn't and cannot run in open-gl. Its purely directX based. So some of the advanced textures like thwater effects will always look a little dodgy.


But hey if anybody knows different feel free to better inform me and the OP

---

### Post by Lystrodom on 2006-12-07
I'm having a problem with Steam, maybe you can help.

I followed the instructions for getting the Tahoma font, and it's sitting in my fonts directory and everything, but Steam still runs without any words.

I even tried it with a different Tahoma.ttf, but that didn't do anything. Any advice?

---

### Post by Fitzy_oz on 2006-12-07
There is a switch for CSS to force GL, I'm not sure how much of a difference it makes.
Can be run with the following command line switch -gl, I have however not tried it yet.

You can also bump up performance by knocking down the H/W DX Level.  Default is 9.0, I run it at 8.1 which seems to be a bit quicker.  The switch for it is -dxlevel 8.1.  
This helped me a bit.

---

### Post by Fitzy_oz on 2006-12-09
The following switches may also help for improving performance.
-gl "Force Open GL"
-dxlevel xx "70 = DirectX 7.0, 80 = 8.0, 81= 8.1 etc.

Direct x 8.1 provides the best balance between Performance and prettiness.

The switches can be added under properties inst my games menu of steam.

---

### Post by AndyW on 2006-12-09
I'm getting this
```
wine: could not load L"c:\\windows\\system32\\SteamInstaller.exe": Module not found

```
when I run
```
wine SteamInstaller.exe
```

any suggestions?

---

### Post by mitchbones on 2006-12-09
> **AndyW said:**
> I'm getting this
```
wine: could not load L"c:\\windows\\system32\\SteamInstaller.exe": Module not found

```
when I run
```
wine SteamInstall**er**.exe
```

any suggestions?

You made a typo on the filename :P

Try this instead!
```
wine SteamInstall.exe
```
Good luck

---

### Post by AndyW on 2006-12-09
I'm pretty sure I typed in right in the consol. I tried it a couple times, but now I have it installing of my cdrom.
One thing though, last time I tried to minimize the steam window it froze my computer. Im hesitant to do it again, but is this a known problem and is there a fix?

---

### Post by ErikTheRed on 2006-12-10
From what I can tell the -gl option doesn't offer much of a performance boost but it does seem to eliminate a lot of the graphical glitches I was getting without it.

---

### Post by mitchbones on 2006-12-10
> **AndyW said:**
> I'm pretty sure I typed in right in the consol. I tried it a couple times, but now I have it installing of my cdrom.
One thing though, last time I tried to minimize the steam window it froze my computer. Im hesitant to do it again, but is this a known problem and is there a fix?
Yeah you can't hit minimize at all, you always have to hit exit.

---

### Post by jc87 on 2006-12-10
*My specs are: 1.7ghz 512 MB ram and a Radeon 9600 64mb graphics card*

**[off topic]** Just by curiosity, do you have any performance benchmark in running native in Windows versus running it with wine on Ubuntu?

And when you say 1,7 ghz CPU, which is the exact model;) 
[B]
[/off topic][/B]

---

### Post by mitchbones on 2006-12-10
> **jc87 said:**
> *My specs are: 1.7ghz 512 MB ram and a Radeon 9600 64mb graphics card*

**[off topic]** Just by curiosity, do you have any performance benchmark in running native in Windows versus running it with wine on Ubuntu?

And when you say 1,7 ghz CPU, which is the exact model;) 
[B]
[/off topic][/B] Me personally, I don't rember what my processer is :P its like AMD Sempron :P Its clockspeed is only 1.7 so since its an AMD that means its like 2.

Edit: Wow....I recorded Shift-F1, Shift-F2,Shift-F3,Shift-F4 to the workspaces, and it switches really fast in-game.

---

### Post by AndyW on 2006-12-10
One more thing. Mine plays windowed, but without the window meaning I cant move it or make it bigger or smaller. I know this is possible because I saw it in some screenshots on the wine site.
I just dont know how to do it. Anyone?

---

### Post by claydoh on 2006-12-10
running winecfg, you can play with the window behaviour in the graphics section, or try editing the in-game video settings

---

### Post by AndyW on 2006-12-10
now it runs full screen (what I really wanted)and I didnt change a thing.
Oh well

---

### Post by snype on 2006-12-10
sorry-- to the pwerson asking my cpu model it's a Pentium M 1.7 i forget i think its the like 735? oh and I upgraded to 1 GGB ram- its a thinkpad. I also started using cedega as I find it plays source better, for me anyways.



t42buntu.blogspot.com

---

### Post by Gravity on 2006-12-11
If any of you have CSS working, could you please post some benchmarking results, I might consider switching to ubuntu if it runs well :P

---

### Post by Fitzy_oz on 2006-12-11
I had it running relatively well under SUSE, but I prefer using Ubuntu.  My graphics config is an ATI Radeon 9600 on a 1.5 gig athlon 1.5 gig of ram Shouldn't really a be huge issue.  Are there any major issues with the ATI Driver (frgl) as I have installed the newest one from their site.

---

### Post by AndyW on 2006-12-11
Computer Specs:
Amd 64 3200+
1 gig ram
6800 xt

My fps hang about 30-40 but range from 20-60 fps. It runs really well IMO, but it lacks anti aliasing.

BTW Im playing with direct x 8.1. 9 would play but the players would skip.

---

### Post by Fitzy_oz on 2006-12-12
I'm gonna try it with Edgy instead of Dapper, and try a few different settings with the drivers.  Appeared to be getting a lot of trouble from the winehq.org version of wine, sound errors on startup seem to be slowing it down.  Will post the FPS and whatever command switches i use.  My graphics config is a bit messed up as well.  :twisted:

---

### Post by SpinesN on 2006-12-13
I got a strange problem. Once steam loads up and asks me to log in I cannot type in the steam window. I am forced to type in the command line window I opened wine from.

Fixed: Emulated a desktop and it got my input :D

---

### Post by Fitzy_oz on 2006-12-13
> **SpinesN said:**
> I got a strange problem. Once steam loads up and asks me to log in I cannot type in the steam window. I am forced to type in the command line window I opened wine from.

Fixed: Emulated a desktop and it got my input :D

You can also sort it by right clicking in the username field and clicking paste.  This should also fix it without having to emulate the desktop.

On another note, anyone had any trouble with sound being really choppy.  I am almost convinced that this is what is killing my gameplay.  The chipset is an N-Force 2 Ultra.  I have tried the OSS, ALSA, ESOUND.  Everything I can think of.  Still getting errors with wine regaring the sound setup - error loading libjack.so.

The console report from wine also says - Your soundcard does not support direct access  Using Slower Directsound HEL instead.  

Any thoughts?
[COLOR="Blue"]
Fixed - Removed Radeon 9600 and replaced with 64mb Nvidia Mx440 - ATI's drivers really leave a lot to be desired.[/COLOR]  
If anyone knows how to successfuly get a 9600se working please let me know, I've tried just about every solution i can find on the internet....

---

### Post by yawnster on 2006-12-20
Anyone know of the fix for the unplayable framerate bug?

I got it working correctly, except that I only getting a framerate of ~ 1fps...

Im using Edgy, with a NVidiaGeForce FX 5200, old I know but it does the job..

Anyone got any ideas?

Thanks, Alex.

---

### Post by maxM on 2006-12-28
I get a message I dont understand under the installation of Steam.
```
wine /home/jd/Desktop/SteamInstall.exe
```
The instaler starts up, I choose everything I would do in windows. Then in the midle of Steam Updating this comes up:
[img]http://img149.imageshack.us/img149/7650/screenshotpc6.png[/img]

If I try to run Steam.exe directly thrue Wine the same message comes up.

Anyone knows why this happends?

---

### Post by Fitzy_oz on 2007-01-01
> **yawnster said:**
> Anyone know of the fix for the unplayable framerate bug?

I got it working correctly, except that I only getting a framerate of ~ 1fps...

Im using Edgy, with a NVidiaGeForce FX 5200, old I know but it does the job..

Anyone got any ideas?

Thanks, Alex.

I recently installed the same card - Are you running Nvidia's GLX drivers of the standard Xorg-server?

try running steam with the following command:

WINEDEBUG="-all" wine "c:\Program Files\Valve\Steam\Steam.exe"

Goto to the game properties and set the following launch options [COLOR="Red"]-dxlevel 70 -gl[/COLOR]
[COLOR="Blue"](This is required as the H/W direct x level supported by the 5200 is 7.0, mine will not work above 2 fps without that switch..."[/COLOR]
Mine runs very nicely at around 30-40 fps which is more than playable for me anyway.

---

### Post by yawnster on 2007-01-01
> **Fitzy_oz said:**
> I recently installed the same card - Are you running Nvidia's GLX drivers of the standard Xorg-server?

try running steam with the following command:

WINEDEBUG="-all" wine "c:\Program Files\Valve\Steam\Steam.exe"

Goto to the game properties and set the following launch options [COLOR="Red"]-dxlevel 70 -gl[/COLOR]

Mine runs very nicely at around 30-40 fps which is more than playable for me anyway.

Hmm, when I run the first command I get the error..

[IMG]http://www.yawnster.com/images/error.png[/IMG]

I would usually combat that by running the command under sudo, but that doesnt work either, bringing the error message...

```
sudo: WINEDEBUG=fixme-all: command not found
```

If anyone has got any ideas about how to fix this it would be greatly appreciated..

Thanks again, Alex.

---

### Post by Fitzy_oz on 2007-01-01
I don't mean to ask dumb questions but which version of Wine are you running - 0.28 or the version that ships with ubuntu?
Were there any errors installing steam?  Are you using steam or a *"cough"* different version?

---

### Post by yawnster on 2007-01-01
> **Fitzy_oz said:**
> I don't mean to ask dumb questions but which version of Wine are you running - 0.28 or the version that ships with ubuntu?
Were there any errors installing steam?  Are you using steam or a *"cough"* different version?

I'm presuming you are talking to me..

alex@alex-ubuntu:~$ wine --version
Wine 0.9.22

That's what I am using, installed it through agt-get..

I installed Steam using my HL2 cd.. I guessed that was the correct way?

I have got the drivers that I was told to install on this [wiki article]("https://help.ubuntu.com/community/BerylOnEdgy"), and before you ask.. I don't run CSS with Beryl on, I switch back to Metacity :p 

Thanks.. Alex

---

### Post by Fitzy_oz on 2007-01-02
> **yawnster said:**
> I'm presuming you are talking to me..

alex@alex-ubuntu:~$ wine --version
Wine 0.9.22

That's what I am using, installed it through agt-get..

I installed Steam using my HL2 cd.. I guessed that was the correct way?

I have got the drivers that I was told to install on this [wiki article]("https://help.ubuntu.com/community/BerylOnEdgy"), and before you ask.. I don't run CSS with Beryl on, I switch back to Metacity :p 

Thanks.. Alex


Yes mate, I am talking to you. :)

You'll need to add custom repositories for wine to get the most updated version of it.
[this is the link ]("http://winehq.org/site/download-deb")to that page, after which synaptic should show an update for it being available.
Try it with the updated version.  This is my current setup and it seems to work well:

Athlon XP 1800+
1.5 gig of ram
Nvidia FX5200 128mb
Im using the proprietry Nvidia Driver  (xorg-nvidia-glx) driver from the restricted modules - But given the fact that your running berryl, I'm guessing your running them too if your using berryl.

Probably wouldn't hurt to install CS:S and HL2 again either.

Good luck,
Hayden.

---

### Post by Jammy_Stuff on 2007-01-07
I'm having a strange problem with mine. I can start CS:S and even run a video test. However, I can't join a server or start a server. When I try and join a server, it freezes at "Sending client data" and when I try and start one, it freezes at "Initializing game data". Anyone got any ideas?

---

### Post by Fitzy_oz on 2007-01-07
I had that problem also, what H/W setup are you using?  More importantly what graphics card?  I had to install the propr. drivers before mine would work (ATI or Nvidia).

Try running steam or CSS from the command line with this line WINEDEBUG="-all"  wine "c:\<steamdir>\steam.exe" - This should stop it from displaying all of the errors in the console and may give it a speed boost.

---

### Post by Jammy_Stuff on 2007-01-08
I'm running it on a nvidia (along with the latest drivers). Running it with that command doesn't help, still freezes.

---

### Post by Jarn on 2007-01-08
Has anyone been able to use the backup function in Steam? I created a backup of game files inside Windows and moved it over to Linux and put it in the same folder it was in in Windows. However, when I run it (steambackup.exe) with Wine, Wine tells me that it cannot launch the external program "c:/program files\steam/steam.exe" and a look at the cli shows that Wine produced the error "err:exec:SHELL_ExecuteW cannot set directory L"C:\\PROG~FBU\\Steam\\Backups\\Disk_1\\c:/program files/steam""

EDIT: Well, I got around the problem by creating a folder c:, then "program files", then "steam" and copying steam.exe there. It had to update steam again and I'll just copy the game files up to the original directory once it installs the game files.

---

### Post by mailbox on 2007-01-10
hmm.
running the following, like you said:
[quote=the OP]6. When the installer finishes open up a terminal and do the following to launch steam:

cd /home/USER/.wine/drive_c/Program Files/Steam
WINEDEBUG="fixme-all" wine steam.exe[/quote]
returns: "wine: could not load L"c:\\windows\\system32\\steam.exe": Module not found"

[edit]note: i also tried *WINEDEBUG="-all" wine steam.exe"*, to no avail.

---

### Post by claydoh on 2007-01-10
Try it this way with quotes around the file path. You won't have to cd to any directories, either:
```
WINEDEBUG="fixme-all" wine "c:/program files/steam/steam.exe" 
```

---

### Post by mailbox on 2007-01-11
sweet, that worked, at least to load steam.

now, when i play, i have the following problem: the valve intro video (which is unskippable, for some reason) plays at about half speed with no audio, and when it finishes, the game crashes.

---

### Post by Fitzy_oz on 2007-01-12
> **Jammy_Stuff said:**
> I'm running it on a nvidia (along with the latest drivers). Running it with that command doesn't help, still freezes.

I had this problem with the ubuntu pre-packaged version that came with edgy, it came good when I updated to the version from the WineHq repo.  try adding this source: deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main to your third party reposositories and updateing wine to .28 or .29 I think it is now.  That should do it, I use the OSS sound plugin it seems to run a bit faster.

---

### Post by Fitzy_oz on 2007-01-12
> **mailbox said:**
> sweet, that worked, at least to load steam.

now, when i play, i have the following problem: the valve intro video (which is unskippable, for some reason) plays at about half speed with no audio, and when it finishes, the game crashes.

In steam go to the game properties and add the switch -novid or -novideo.  This should take care of the valve intro :)

---

### Post by Kittens on 2007-01-13
I can't get around this error.

[http://img59.imageshack.us/img59/235/steamerrorsn7.png](http://img59.imageshack.us/img59/235/steamerrorsn7.png)

I've tried the WINEDEBUG to get around it, but it doesn't work. Can anyone please assist me?

---

### Post by mailbox on 2007-01-13
> **Fitzy_oz said:**
> In steam go to the game properties and add the switch -novid or -novideo.  This should take care of the valve intro :)

well, that got part of it. now there's no video, but all i see is the blurry loading screen, then it crashes to desktop a few seconds later.
i'm pretty sure it's crashing as soon as it tries to render some 3d.

---

### Post by Fitzy_oz on 2007-01-14
> **Fitzy_oz said:**
> In steam go to the game properties and add the switch -novid or -novideo.  This should take care of the valve intro :)

Mailbox,
Just couple of quick questions,
Can you run the command in a terminal glxinfo |more and paste the first couple of lines for me.
Second command in the terminal: wine --verison and let me know the version number.

If it's a rendering problem it will almost certainly be the drivers for the card.  If using nvidia I find using the proprietary drivers the most effective.  For ATI, it might be a little more interesting depending on the card type.  Let me know and we'll go from there.

> **Kittens said:**
> I can't get around this error.

[http://img59.imageshack.us/img59/235/steamerrorsn7.png](http://img59.imageshack.us/img59/235/steamerrorsn7.png)

I've tried the WINEDEBUG to get around it, but it doesn't work. Can anyone please assist me?

Same as above - Which version of wine are you using - it may seem trivial but it does make a difference.  If it's the one out of the multiverse ubuntu repo's, add the repos from winehq.org the instructions are in one of my posts in this thread. :)

---

### Post by mailbox on 2007-01-14
**glxinfo|more**```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7900 GTX/PCI/SSE2/3DNOW!
OpenGL version string: 2.0.2 NVIDIA 87.76
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_HP_occlusion_test, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_gpu_program_parameters, GL_NV_half_float, GL_NV_light_max_exponent, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess
```

**wine --version**```
wine-0.9.29
```

if it matters, WoW runs, although i don't think it's running in OpenGL.

---

### Post by mailbox on 2007-01-14
another queastion: has anyone gotten Valve's Hammer editor to run in wine? it's just plain not working for me.

---

### Post by Fitzy_oz on 2007-01-14
WOW is running, yeah it's a good sign, you do have direct rendering, thats for sure.  Here is a screenshot of the options I have set for CS:S, including the directx settings I use.  With my Nvidia card I have to force it to render in OpenGL mode otherwise it just freaks out.  I also have to use Dxlevel 8 or it is just way too slow.  Just try these options and see it that fixes it - If it doesn't hit me back and we'll try something else.

You could also try the video card drivers off Nvidia's site - Here's part of my GLXINFO, the difference is highlighted...

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE/3DNOW!
OpenGL version string: [COLOR="Red"]2.1.0 NVIDIA 97.46[/COLOR]

My video card's old and crappy and runs it nicely, it's just a matter of tweaking it.

> **mailbox said:**
> another queastion: has anyone gotten Valve's Hammer editor to run in wine? it's just plain not working for me.

Yeah, I got it to work...  I didn't try and do anything with it though

---

### Post by abzolutxero on 2007-01-14
for those of you who have gotten steam running, i have a few questions....

steam runs, downloads the game files, chat works, friends list... etc.... as soon as i try to load a game, it resizes the screen to 640x480, and then the game hangs.  steam still works, but obviously wont exit because it is trying to load a game... i have the most current nvidia drivers installed, so i assume it isnt gfx... is there a wine configuration i am missing?  thanks

---

### Post by Kittens on 2007-01-14
I added it to the repositories, reloaded, but it didn't work. I still get the error message! :(

---

### Post by mailbox on 2007-01-14
> **Fitzy_oz said:**
> Yeah, I got it to work...  I didn't try and do anything with it thoughtry and create a new map, and tell me what you see.

---

### Post by Fitzy_oz on 2007-01-14
> **mailbox said:**
> try and create a new map, and tell me what you see.

No worries, I'll give it a try when I get home tonight, will let you know what happens.

> **Kittens said:**
> I added it to the repositories, reloaded, but it didn't work. I still get the error message! :(

Hmmm, which version of windows is it emulating? XP or 98.

---

### Post by Fitzy_oz on 2007-01-14
> **abzolutxero said:**
> for those of you who have gotten steam running, i have a few questions....

steam runs, downloads the game files, chat works, friends list... etc.... as soon as i try to load a game, it resizes the screen to 640x480, and then the game hangs.  steam still works, but obviously wont exit because it is trying to load a game... i have the most current nvidia drivers installed, so i assume it isnt gfx... is there a wine configuration i am missing?  thanks

Create a text file called steam.sh and paste the following into it... (provided you user the defaults for the install it should work otherwise change the path"

sh WINEDEBUG="-all" wine "c:\Program Files\Valve\Steam\steam.exe"

the reasoning behind this is that it will supress all of the error messages that wine generates when it can't implement something properly - and for direct3d, it's a lot of messages, which in turn slows wine down to a crawl.  Try that in a script or run it at the terminal.

For the 640*480 Check under you winecfg that you don't have emulate desktop option set, this force all of your wine apps into a small area in the middle of the desktop instead of using them as part of the linux desktop.  see my screenshot for the startup switches I use to run CS:S or Half Life 2.  Any dramas, let me know.  I'm happy to help if I can.

---

### Post by abzolutxero on 2007-01-15
> **Fitzy_oz said:**
> Create a text file call steam.sh and paste the following into it... (provided you user the defaults for the install it should work otherwise change the path"

sh WINEDEBUG-"-all" wine "c:\Program Files\Valve\Steam\steam.exe"

the reasoning behind this is that it will supress all of the error messages that wine generates when it can't implement something properly - and for direct3d, it's a lot of messages, which in turn slows wine down to a crawl.  Try that in a script or run it at the terminal.

For the 640*480 Check under you winecfg that you don't have emulate desktop option set, this force all of your wine apps into a small area in the middle of the desktop instead of using them as part of the linux desktop.  see my screenshot for the startup switches I use to run CS:S or Half Life 2.  Any dramas, let me know.  I'm happy to help if I can.


thanks Fitzy,  I changed all of the switiches, and made my configuration identical to yours.  and here is the response i have.

abzolutxero@FreeSpirit:~/Desktop$ sh steam.sh
sh: Can't open WINEDEBUG--all
abzolutxero@FreeSpirit:~/Desktop$ 

(see attachments)

also, is it wrong that i have to run it as root so that way it will load?  if i dont, it says something like "can't load blob file"

Thanks Again...

---

### Post by Fitzy_oz on 2007-01-15
> **abzolutxero said:**
> thanks Fitzy,  I changed all of the switiches, and made my configuration identical to yours.  and here is the response i have.

abzolutxero@FreeSpirit:~/Desktop$ sh steam.sh
sh: Can't open WINEDEBUG--all
abzolutxero@FreeSpirit:~/Desktop$ 

(see attachments)

also, is it wrong that i have to run it as root so that way it will load?  if i dont, it says something like "can't load blob file"

Thanks Again...

Sorry Mate, typo in there.

WINEDEBUG="-all" wine "c:\Program Files\Valve\Steam\steam.exe"

You won't be able to run it as root as the .wine directory that you have everything installed to is user specific, so you'll need to remove sudo from the script.  In your winecfg sound TAB, I'd recommend using either OSS or Alsa, not both.  use which ever one works best for you, I use OSS which seems to do the trick for me.  Fingers crossed you should be good to go ;)
Let me know how you go.  :)

---

### Post by abzolutxero on 2007-01-16
Fitzy, you are amazing.  thanks for all your help.  it runs really well.  I'd love to be able to get it to work through the alsa drivers, but for some reason wine says it cant use it... i have an altec lansing usb sound card that i use so i can swap between speakers and a headset quickly, but i can fix that later.

to fix the whole root problem, i had to uninstall and reinstall wine.... seems when i installed it i installed it as root, so it wrote my entire .wine directory as root, meaning i could only run programs that changed files when i had root privledges... bonehead move really.. lol.  

anyhow, it works, video on it works, sound works through OSS... thanks for the help.

---

### Post by Jarn on 2007-01-16
When I run it with ALSA sound, it freezes while joining a game. When I run it with OSS, it doesn't freeze but I have no sound.

---

### Post by abzolutxero on 2007-01-16
that is interesting... i didnt even corelate the game freezes with the sound, but now that i think about it, it started to work when i chose OSS sound instead of ALSA.  

Jarn, what is your system setup? mobo/sound etc...  just curious.

---

### Post by Jarn on 2007-01-16
nForce4 mobo, onboard sound card

---

### Post by Fitzy_oz on 2007-01-16
> **Jarn said:**
> nForce4 mobo, onboard sound card

Screen dump your winecfg Audio page - Make a note of the sound emulation settings - Full, standard, basic etc..... 16bit/8bit - Sample Rate, 44100 22020 etc.  OSS should work straight up though.  Post it and I'll have a look

> **abzolutxero said:**
> Fitzy, you are amazing.  thanks for all your help.  it runs really well.  I'd love to be able to get it to work through the alsa drivers, but for some reason wine says it cant use it... i have an altec lansing usb sound card that i use so i can swap between speakers and a headset quickly, but i can fix that later.

to fix the whole root problem, i had to uninstall and reinstall wine.... seems when i installed it i installed it as root, so it wrote my entire .wine directory as root, meaning i could only run programs that changed files when i had root privledges... bonehead move really.. lol.  

anyhow, it works, video on it works, sound works through OSS... thanks for the help.

Your welcome mate,
and don't beat yourself up, I think I've done it myself more than once so don't worry about it. ;)

---

### Post by AusIV4 on 2007-01-17
I've recently installed Steam under wine to play Half-Life and TFC. It starts up fine, but it usually crashes after about 5 minutes. I can SSH into the box from another machine, and top says hl.exe is upwards of 150% CPU. Ctrl-Alt-Backspace doesn't do anything, and I ultimately wind up rebooting the machine. Any advice?

---

### Post by Fitzy_oz on 2007-01-17
> **AusIV4 said:**
> I've recently installed Steam under wine to play Half-Life and TFC. It starts up fine, but it usually crashes after about 5 minutes. I can SSH into the box from another machine, and top says hl.exe is upwards of 150% CPU. Ctrl-Alt-Backspace doesn't do anything, and I ultimately wind up rebooting the machine. Any advice?

Which Wine are you using, the one from the Ubuntu Repos or the Winehq.org site?

If it's the ubuntu ones, add the wine repos from winehq.org and upgrade it.
If not what video setup are you running?  What sound emulation and what command are you using to start steam?

additional note - you can't minimize steam, it will freeze.  Instead always use the close button to minimize it to the tray.

---

### Post by ppglabrat on 2007-01-18
ok  heres the the deal after hours of trying i can get cs-s sort of working .

it starts up , but menu screen is blank i get flashing cursor so I blindly select options or whatever then eventually I can see menu 

I tried starting server but it crashed

---

### Post by AusIV4 on 2007-01-18
> **Fitzy_oz said:**
> Which Wine are you using, the one from the Ubuntu Repos or the Winehq.org site?

If it's the ubuntu ones, add the wine repos from winehq.org and upgrade it.
If not what video setup are you running?  What sound emulation and what command are you using to start steam?

additional note - you can't minimize steam, it will freeze.  Instead always use the close button to minimize it to the tray.

I get wine from the winehq repository (deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main).

My video card is a Mobility Radeon X600, using the open source radeon driver. I use Compiz most of the time, but I've found I have to turn it off in order to play full screen games. I'm running HL in OpenGL mode. Sound emulation uses the OSS driver. Since I pretty much just play TFC, I use the command ```
wine "c:\Program Files\Steam\Steam.exe" -applaunch 20
``` which launches TFC without choosing it from the Steam application. I've also tried running steam with ```
wine "C:\Program Files\Steam\steam.exe"
``` then closing the steam window to play. Either way, the game runs fine for a while, then everything just freezes up.

Thanks for any help.

---

### Post by Jarn on 2007-01-18
Here it is. I use the same settings for ALSA, only with ALSA checked instead of OSS.

---

### Post by Fitzy_oz on 2007-01-18
[COLOR="Blue"]Just a quick note guys - I'm happy to do whatever I can to help anyone out with getting source games to run, but it would save a lot of typing and a lot of time if any new posts for help could have the following information: 
Graphics card & driver being used, Version of wine (you can get this by typing wine --version in the console), have you tried running it with  WINEDEBUG="-all" in front of wine?, what sound emulation are you using (ALSA, OSS, ESOUND), have you added the -gl -dxlevel 70?  

A lot of the information for this is already in the thread and is worth trying before posting another reply.  I can understand if your're new to linux and don't know how to find these options I can certainly help you with that but providing me with above information will make it easier for me to see what's wrong and quicker for you to start playing the game :) [/COLOR]

> **Jarn said:**
> Here it is. I use the same settings for ALSA, only with ALSA checked instead of OSS.

Up the Bitrate to 16 bit, sounds funny but it actually made mine less jerky...

> **AusIV4 said:**
> I get wine from the winehq repository (deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main).

My video card is a Mobility Radeon X600, using the open source radeon driver. I use Compiz most of the time, but I've found I have to turn it off in order to play full screen games. I'm running HL in OpenGL mode. Sound emulation uses the OSS driver. Since I pretty much just play TFC, I use the command ```
wine "c:\Program Files\Steam\Steam.exe" -applaunch 20
``` which launches TFC without choosing it from the Steam application. I've also tried running steam with ```
wine "C:\Program Files\Steam\steam.exe"
``` then closing the steam window to play. Either way, the game runs fine for a while, then everything just freezes up.

Thanks for any help.

Ok, I can't comment on the sort of frame rates your going to get with the open source driver, if you can make fglrx driver work use it, I didn't have any luck with open source driver when trying to get my 9600 working.  Can you run glxinfo in a terminal and paste it's output here for me.

Also, when running the steam apps, run it with a script or from the terminal like so WINEDEBUG="-all" wine wine "c:\Program Files\Steam\Steam.exe".  Forget about the applaunch part, mine goes a bit haywire if I do it that way and reports funny errors.  Goto the in game properties and add the following switches: -gl -dxlevel 70.  This will pull the directx hw implentation down to 7.0 which won't matter to TFC or HL but will make a big difference to the performance of wine itself.  Another worthy thing to note is that the ' WINEDEBUG="-all" ' function supresses all of the (many) directx error outputs for deubugging purposes which will speed your game up.

> **ppglabrat said:**
> ok  heres the the deal after hours of trying i can get cs-s sort of working .

it starts up , but menu screen is blank i get flashing cursor so I blindly select options or whatever then eventually I can see menu 

I tried starting server but it crashed

You need the tahoma and lucida console fonts from windows which are located under the c:\windows\fonts folder on a windows computer, otherwise you will have to download them and place them in your /home/<user>/.wine/drive_c/windows/fonts folder.  That should fix the menu.

---

### Post by Jarn on 2007-01-18
> **Fitzy_oz said:**
> Up the Bitrate to 16 bit, sounds funny but it actually made mine less jerky...Do you mind if I declare my undying love for you?



That meant it worked. Thanks much!

---

### Post by Fitzy_oz on 2007-01-18
Awesome :) On with the killing :mrgreen:

---

### Post by Xenix on 2007-01-19
EDIT - Delete post. Sorry.

---

### Post by kilroy4231 on 2007-01-20
I'm sure i'm just having a brainfart......but i can't seem to get to the directory where i've installed steam through the terminal, i can navigate there through file browser 

```
cd /home/dan/.wine/drive_c/Program Files/Steam
``` 

it returns that Program Files is not a directory when i can plainly see it in the file browser....

thx for any help

---

### Post by Jarn on 2007-01-20
You need to put quotes around it since it has a space in it. Or put a \ in it so it reads either:

cd "/home/dan/.wine/drive_c/Program Files/Steam"
cd /home/dan/.wine/drive_c/Program\ Files/Steam

---

### Post by Fitzy_oz on 2007-01-21
> **Jarn said:**
> You need to put quotes around it since it has a space in it. Or put a \ in it so it reads either:

cd "/home/dan/.wine/drive_c/Program Files/Steam"
cd /home/dan/.wine/drive_c/Program\ Files/Steam

If you doing it from Linux terminal it's apsotrophes - 

cd '/home/dan/.wine/drive_c/Program Files/Steam' ;)

"=Windows
'=Linux

:)

---

### Post by Enverex on 2007-01-21
> **Fitzy_oz said:**
> If you doing it from Linux terminal it's apsotrophes - 

cd '/home/dan/.wine/drive_c/Program Files/Steam' ;)

"=Windows
'=Linux

:)

Not true, you can use either. They just have slightly different meanings, but they'd both work in this case.

---

### Post by Fitzy_oz on 2007-01-21
> **Enverex said:**
> Not true, you can use either. They just have slightly different meanings, but they'd both work in this case.

Fair enough... The " " don't work in the console for me in this case unless I'm using a windows  virtual path ie. wine "c:\Program Files\Valve\Steam\Steam.exe", where as if it were the physical path I would use /home/<user>/.wine/drive_c/'Program Files/Valve/Steam/Steam.exe'.  Thats the only way I could make it work....

---

### Post by caltabellotta on 2007-01-24
i am trying to configure wine so i can play counter-strike (yeah im addicted ). When I set up, wine does not create a /home/USERNAME/.wine/ folder (or at least not that I can see). I thus cannot install my tahoma fonts. this is what happens with $wine cfg:
Code:

~$ wine cfg wine: could not load L"c:\\windows\\system32\\cfg.exe": Module not found

I think I did a sudo apt-get install wine correctly, but I am not sure since wine setup or wine cfg does not work.

Please help!


this happens with cs:
```
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: could not load L"c:\\windows\\system32\\SteamInstall.exe": Module not found

```

---

### Post by Jarn on 2007-01-24
winecfg is one command, not two. When you do 'wine cfg' it is trying to run the program cfg with wine. Do it as one word, 'winecfg'.

---

### Post by caltabellotta on 2007-01-24
ok, with winecfg i get the config box but this comes up:
```
~$ winecfg
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.

```

what do I do in winecfg to allow me to have an emulated c folder? Or how do I get rid of all these errors and install tahoma font and steam....

---

### Post by Fitzy_oz on 2007-01-26
> **caltabellotta said:**
> ok, with winecfg i get the config box but this comes up:
```
~$ winecfg
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.

```

what do I do in winecfg to allow me to have an emulated c folder? Or how do I get rid of all these errors and install tahoma font and steam....  


when you initially ran winecfg, did you run it with sudo?  Try sudo apt-get remove wine, then  re-install it... As soon as it's installed drop to a terminal and type winecfg - It will automatically create the virtual mappings for you. It's good idea to add the winehq repos as the latest version of wine runs CSS a lot better than the now out of date version that ships with Ubuntu - Instructions for this are 1 page previous.  

Installing steam should just be a matter of right clicking on the setup.exe file and clicking run with wine or windows emulator.  Simply install it as normal - again the latest version of wine will help here as the setup routine does'nt malfunction in the later version as it does in .22 that ships with ubuntu.  Once this is done it will very kindly create the icons for you and it is at this point that I would refer to the scripts and config settings earlier in the thread to get the most out of it.
Obtaining the Tahoma font is as easy as ripping of a windows installation if you have one available - it's under windows\fonts - copy to the /home/<username>/.wine/drive_c/windows/fonts.  That should do it ;)  Other wise just download it off the Internet.... and place it in the above listed directory.

 
  Good luck :)

---

### Post by ramasdf123 on 2007-01-28
i have a problem with wine and CS... everytime i am playing CS it hardlocks aka freezes and I cant do anything it wont even force quit and i cannot access the desktop

and i have no sound

how can i fix these 2 problems mainly the freezing

---

### Post by Enverex on 2007-01-29
> **ramasdf123 said:**
> i have a problem with wine and CS... everytime i am playing CS it hardlocks aka freezes and I cant do anything it wont even force quit and i cannot access the desktop

and i have no sound

how can i fix these 2 problems mainly the freezing

That sounds like the ALSA hardlock. Set Wine to use OSS in winecfg.

> **Fitzy_oz said:**
> when you initially ran winecfg, did you run it with sudo?  Try sudo apt-get remove wine, then  re-install it... As soon as it's installed drop to a terminal and type winecfg - It will automatically create the virtual mappings for you. It's good idea to add the winehq repos as the latest version of wine runs CSS a lot better than the now out of date version that ships with Ubuntu - Instructions for this are 1 page previous.  

Installing steam should just be a matter of right clicking on the setup.exe file and clicking run with wine or windows emulator.  Simply install it as normal - again the latest version of wine will help here as the setup routine does'nt malfunction in the later version as it does in .22 that ships with ubuntu.  Once this is done it will very kindly create the icons for you and it is at this point that I would refer to the scripts and config settings earlier in the thread to get the most out of it.
Obtaining the Tahoma font is as easy as ripping of a windows installation if you have one available - it's under windows\fonts - copy to the /home/<username>/.wine/drive_c/windows/fonts.  That should do it ;)  Other wise just download it off the Internet.... and place it in the above listed directory.

 
  Good luck :)

Uninstalling wont fix the breakages if wine has been run as root. You need to "sudo rm -rf ~/.wine" and then rerun winecfg as the .wine folder is independent from installations of Wine.

---

### Post by Fitzy_oz on 2007-01-29
> **Enverex said:**
> That sounds like the ALSA hardlock. Set Wine to use OSS in winecfg.



Uninstalling wont fix the breakages if wine has been run as root. You need to "sudo rm -rf ~/.wine" and then rerun winecfg as the .wine folder is independent from installations of Wine.

True ...  But then there isn't really annything needs to fix as it was installed for another user. By just running winecfg without the sudo should create a prefix for the correct user anyway but removing the directory created under the root user is a good idea given that it will rarely if ever be used. (For anyone who doesn't know - Using wine apps under sudo opens your system to an unnecessary security risk)

---

### Post by AusIV4 on 2007-01-29
A little over a week ago I made a comment about having trouble with TFC through steam. The problem is that after I play for a little while, my system completely freezes up. top on another computer connected by SSH shows hl.exe taking upwards of 150% CPU. I'm using OSS sound emulation, the open source radeon drivers, and OpenGL for rendering. 

Last time I posted, all I got were suggestions on how to make my game run faster. It runs quite satisfactorily for about 5 minutes, then it freezes up and I have to hold the power button to get a reboot. At this point I'm not interested in performance tweaks unless it's also going to keep my game from freezing.

Any help is appreciated.

---

### Post by Enverex on 2007-01-30
> **Fitzy_oz said:**
> True ...  But then there isn't really annything needs to fix as it was installed for another user. By just running winecfg without the sudo should create a prefix for the correct user anyway but removing the directory created under the root user is a good idea given that it will rarely if ever be used. (For anyone who doesn't know - Using wine apps under sudo opens your system to an unnecessary security risk)

No, running Wine with sudo will create a .wine folder in the current users home folder but with root ownership, thus rendering Wine unusable for that user. Running Wine as root WILL most likely have dire consequences (deleting of system files, wiping of MBR, etc).

---

### Post by Enverex on 2007-01-30
> **AusIV4 said:**
> A little over a week ago I made a comment about having trouble with TFC through steam. The problem is that after I play for a little while, my system completely freezes up. top on another computer connected by SSH shows hl.exe taking upwards of 150% CPU. I'm using OSS sound emulation, the open source radeon drivers, and OpenGL for rendering. 

Last time I posted, all I got were suggestions on how to make my game run faster. It runs quite satisfactorily for about 5 minutes, then it freezes up and I have to hold the power button to get a reboot. At this point I'm not interested in performance tweaks unless it's also going to keep my game from freezing.

Any help is appreciated.

What graphics card? But to be honest, if you're using the Open source Radeon drivers then I'm not all that supprised, they aren't the best in the world. What version of Wine are you using?

---

### Post by PrairieShaman on 2007-01-30
thanks for this thread everyone, after reading through it I got CS:S to work on ubuntu! 

awesome!!

---

### Post by Fitzy_oz on 2007-01-31
> **Enverex said:**
> What graphics card? But to be honest, if you're using the Open source Radeon drivers then I'm not all that supprised, they aren't the best in the world. What version of Wine are you using?

They're kind of hit and miss with the new cards I think, probably due to the fact that the DRI project has had to reverse engineer the drivers after ATI stopped providing them with the specs for their cards.  Have you used the prop. drivers for ATI for this game (or any other wine 3d FPS game)?  I get really ordinary performance out of them on my 9600se which traditionally wipes the floor with my Nvidia FX5200 under windows, yet the opposite applies under linux?  Any thoughts?

---

### Post by Enverex on 2007-01-31
> **Fitzy_oz said:**
> They're kind of hit and miss with the new cards I think, probably due to the fact that the DRI project has had to reverse engineer the drivers after ATI stopped providing them with the specs for their cards.  Have you used the prop. drivers for ATI for this game (or any other wine 3d FPS game)?  I get really ordinary performance out of them on my 9600se which traditionally wipes the floor with my Nvidia FX5200 under windows, yet the opposite applies under linux?  Any thoughts?

That's because the official ATi drivers also suck (but not quite as badly as the open source ones). My old GeForce 4 MX comes close to the performance of my Radon 9700 Pro with official drivers, so that should give you a rough idea of what I mean. Basically if you want to play games then don't use ATi.

---

### Post by Fitzy_oz on 2007-01-31
> **Enverex said:**
> That's because the official ATi drivers also suck (but not quite as badly as the open source ones). My old GeForce 4 MX comes close to the performance of my Radon 9700 Pro with official drivers, so that should give you a rough idea of what I mean. Basically if you want to play games then don't use ATi.

I'm not holding my breathe... As I said, i've got the FX5200 in the main computer which seems to do the job just fine...

---

### Post by AusIV4 on 2007-01-31
> **Enverex said:**
> What graphics card? But to be honest, if you're using the Open source Radeon drivers then I'm not all that supprised, they aren't the best in the world. What version of Wine are you using?
Graphics card is a Mobility Radeon X600. Wine version 0.9.30.

I was under the impression that the while the open source Radeon wouldn't provide the best performance, they were more stable than the binary drivers. If this isn't the case, I may consider installing the binary drivers.

---

### Post by Fitzy_oz on 2007-02-01
> **AusIV4 said:**
> Graphics card is a Mobility Radeon X600. Wine version 0.9.30.

I was under the impression that the while the open source Radeon wouldn't provide the best performance, they were more stable than the binary drivers. If this isn't the case, I may consider installing the binary drivers.

I really don't have any trouble in relation to the stability of the proprietary drivers and they are definitely faster than the open source.  When installing them just make sure you follow the guide as I had a lot of  trouble getting direct rendering to work (which is essential if you want to play games).  [Check out this page]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

---

### Post by ghandi69_ on 2007-02-10
Hi Guys!

I seem to have installed steam fine.  I go to run it, and I click on CounterStrike:Source to start the installation.  It brings up the "Preparing CounterStrikeSource files for install... and the progress bar will get to 100% and it will just sit there.. forever and ever.. it doesn't freeze... cuz the
three "..." go from "." to ".." to  "..." continusouly to show its running.  Any ideas who to move to the next step

AMD 3200 +
Nvidia 7600 GT nvidia-glx drivers
Edgy

---

### Post by cherva on 2007-02-10
i run my CSS with the command 
 nice -20 wine hl2.exe  -game cstrike  -gl -console
the "-gl" makes the game in Open GL

---

### Post by Fitzy_oz on 2007-02-11
> **ghandi69_ said:**
> Hi Guys!

I seem to have installed steam fine.  I go to run it, and I click on CounterStrike:Source to start the installation.  It brings up the "Preparing CounterStrikeSource files for install... and the progress bar will get to 100% and it will just sit there.. forever and ever.. it doesn't freeze... cuz the
three "..." go from "." to ".." to  "..." continusouly to show its running.  Any ideas who to move to the next step

AMD 3200 +
Nvidia 7600 GT nvidia-glx drivers
Edgy

try running steam from the command line to see if it's encountering any stubs in the code that will prevent it from downloading the files.

I reinstalled steam just 2 hours ago and had no problems with it - Mines downloading the ship at the moment and I didn't encounter that anything like that.  Do you have any other Steam games installed yet?  And which version of wine are you using (if it's not 0.9.30 install that version).

---

### Post by ghandi69_ on 2007-02-12
Thanks Fitzy... 

It turns out problems I was having with my system related to the virtualbox package was my problem..

Now steam runs fine and the game runs fine.. a little lower performance however...

qustions::

1.I heard there was a way to hide all the fixme's that show up in the console while playing?  And doing this is supposed to increase performance.  I tried the command found on the HOWTO from linuxgamers.net.. 

WINEDEBUG="fixme-all" wine Steam

and running it that way.. but it says ...command "WINEDEBUG blah blah" not found.

2. The only other problem the game has is that whenever there is a grenade that explodes on my screen.. ( It could only be flash grenade or smoke.. but I never get a chance to see!) but whenever a grenade explodes my screen freezes for about 8 seconds.  I'm guessing these grenades use some kind of rendering not supported by the wine method.. any fixes for this?  Thanks guys!

Ghandi

---

### Post by to4i on 2007-02-13
> **Fitzy_oz said:**
> 
You need the tahoma and lucida console fonts from windows which are located under the c:\windows\fonts folder on a windows computer, otherwise you will have to download them and place them in your /home/<user>/.wine/drive_c/windows/fonts folder.  That should fix the menu.
I put the fonts in the folder but still have the same problem:
"the game starts up , but menu screen is blank i get flashing cursor so I blindly select options or whatever then eventually I can see menu"
Any other ideas.

**EDIT: FIXED** using this switch: -dxlevel70

---

### Post by Fitzy_oz on 2007-02-14
> **ghandi69_ said:**
> Thanks Fitzy... 

It turns out problems I was having with my system related to the virtualbox package was my problem..

Now steam runs fine and the game runs fine.. a little lower performance however...

qustions::

1.I heard there was a way to hide all the fixme's that show up in the console while playing?  And doing this is supposed to increase performance.  I tried the command found on the HOWTO from linuxgamers.net.. 

WINEDEBUG="fixme-all" wine Steam

and running it that way.. but it says ...command "WINEDEBUG blah blah" not found.

2. The only other problem the game has is that whenever there is a grenade that explodes on my screen.. ( It could only be flash grenade or smoke.. but I never get a chance to see!) but whenever a grenade explodes my screen freezes for about 8 seconds.  I'm guessing these grenades use some kind of rendering not supported by the wine method.. any fixes for this?  Thanks guys!

Ghandi

Mine has only recently started freezing on the flashes and I assumed it was just something isolated to my computer - Apparently not.  I'm working on it, will let you know how i go.

*Edit: I'm Reverting back to 0.29 and failing that i'll go back to 0.28 to see if there's any connection between the version changes - I will post my results as this wasn't a problem for me a month ago - I think it has something to do with the new D3d implementation code they're working on.  *

running steam with WINEDEBUG="-all" wine "c:\Program Files\Valve\Steam.exe" should be done from the terminal or create a script by pasting this command into a text file and saving it with an extension of sh example steam.sh and use this to launch the game.

---

### Post by ghandi69_ on 2007-02-14
I'll be checking on the flash problem as well...

(although lately I've been playing a lot of doom 3, not sure when I 'll get back to cs....)

thanks for the help on the fix me command...

---

### Post by Fitzy_oz on 2007-02-14
> **ghandi69_ said:**
> I'll be checking on the flash problem as well...

(although lately I've been playing a lot of doom 3, not sure when I 'll get back to cs....)

thanks for the help on the fix me command...

Reverting to wine 0.9.29 corrected this error for me.

---

### Post by jseiser on 2007-02-16
whew, tried everything in this thread and all it took was re-installing wine a few times and it eventually worked.  The only thing is, when i installed steam, i moved my maps/cfg's over to /home/justin/.wine/drive_c/Program Files/Steam but when i enter to a game i still have to dl maps and my cfg's are absent.  I also installed the veranda font from the thread, could someone please post or show me where i can get the other font steam is missing?  I googled lucinda console but couldnt find one allowing me to download.  Another question is there really a c:/program files folder on my computer?  I know this is the structure that steam is in on windows, but why does wine put everything in /home/justin/.wine/drive_c/Program Files/Steam when i can only launch steam from c/program files/etc steam.exe.  If there really is a c/program files do i jus tput my cfg's and maps in there?

---

### Post by Jarn on 2007-02-16
I just updated to 0.9.31 and now Counter-Strike doesn't work. When I select it from the Steam menu, it starts up, has the Counter-Strike background, says "Loading..." in the bottom right... then the screen goes gray and my mouse flashes. I never tried steam in 0.9.30, so I'm not sure when this started. I know it worked in 0.9.29.

---

### Post by Protoss on 2007-02-16
I was having the flashband problem on 0.9.30 and found that turning the resolution to 1024x768 fixes it. No need to downgrade to .29 or anything.

---

### Post by bastiegast on 2007-02-17
> **Jarn said:**
> I just updated to 0.9.31 and now Counter-Strike doesn't work. When I select it from the Steam menu, it starts up, has the Counter-Strike background, says "Loading..." in the bottom right... then the screen goes gray and my mouse flashes. I never tried steam in 0.9.30, so I'm not sure when this started. I know it worked in 0.9.29.

Having exactly the same problem since 0.9.31 upgrade. The game loads, as soon as the menu should appear the screen goes gray. However the game is still running underneath and I can hear when I move my mouse over the buttons.

---

### Post by GFree on 2007-02-17
Also have the same menu issues as noted when I upgraded to 0.9.31.

---

### Post by Protoss on 2007-02-17
Yeah I just upgraded to 0.9.31 and all Source-based games seem to be broken...dang, and I was hoping .31 would allow me to run CS at my native res =/
Seems it isn't an issue with Wine, as according to [this comment]("http://appdb.winehq.org/appview.php?iVersionId=3731&mode=nested#Comment-18222"), the 'flashbang freeze' was fixed with 0.9.31.

Seems that the menu is broken in .31 but if you add "+map de_dust" into the Steam Launch Options, it should load de_dust and then you'll be able to press Escape and the menu will be fully functional. Hopefully someone finds a workaround for this, as loading dust every time is somewhat lengthy.

---

### Post by GFree on 2007-02-17
Well, there seems to be a workaround (tested, works for me):

---------------

Sorry I should have mentioned - the menu is indeed broken in 0.9.31.

However if you open the console (with `) once you're in the broken menu, you can type:

map de_dust (or whatever map you like)

To start a game!

From there, if you press Esc, the menu works ok (unless you disconnect from the server).

If you have the console disabled, you can do it by changing the launch options in Steam so that you have:

+map de_dust (or whatever map you like).

Hope that helps!

-------------- (from the above link)


EDIT: From testing other Source games I've determined the problem. If the game is NOT running a map (eg. upon startup of CSS), you'll have issues with the menu. Thing is, HL2 works fine because it has an animated map upon startup, underneath the menu; CSS just has a static image. If you turn off the 3D background in HL2 you'll suffer the same problem. Also, if you're in CSS and you disconnect, this will also screw with the menu because you'll return to the static image.

---

### Post by Fitzy_oz on 2007-02-17
> **jseiser said:**
> whew, tried everything in this thread and all it took was re-installing wine a few times and it eventually worked.  The only thing is, when i installed steam, i moved my maps/cfg's over to /home/justin/.wine/drive_c/Program Files/Steam but when i enter to a game i still have to dl maps and my cfg's are absent.  I also installed the veranda font from the thread, could someone please post or show me where i can get the other font steam is missing?  I googled lucinda console but couldnt find one allowing me to download.  Another question is there really a c:/program files folder on my computer?  I know this is the structure that steam is in on windows, but why does wine put everything in /home/justin/.wine/drive_c/Program Files/Steam when i can only launch steam from c/program files/etc steam.exe.  If there really is a c/program files do i jus tput my cfg's and maps in there?

Okay, I don't use the Lucida console font personally so I don't know whether it works or with what results - If you still have a windows installation on a computer nearby, goto to the "c:\windows\fonts" folder and copy the tahoma.ttf file otherwise download it from the net by searching for tahoma.ttf.  (I copy all of the windows fonts from my windows box anyway just to be sure).  The font file goes under the following path /home/justin/.wine/drive_c/windows/fonts
As for the cfg's and files like that you have created or "migrated" from another copy of CSS, I'm pretty sure they need to go under your specific Steam user name folder which has the decompressed game folders, I've attached a screenshot to show you what I mean but the path would be something like this /home/justin/.wine/drive_c/Program Files/Valve/Steam/SteamApps/<steam username>/counter-strike source/cstrike/cfg and /home/justin/.wine/drive_c/Program Files/Valve/Steam/SteamApps/<steam username>/counter-strike source/cstrike/maps respectively.  
Hope that helps
> **Protoss said:**
> I was having the flashband problem on 0.9.30 and found that turning the resolution to 1024x768 fixes it. No need to downgrade to .29 or anything.

Yeah, i'd love to run it in 1024*768 but sadly my poor old FX5200 doesn't like doing anything over 800*600 under linux, It's a bit much for the old card.  0.29 works perfectly for me without the need to start with a map on the console.  I think i'll just wait until .32 before I upgrade again and see if the menu and other issue s are fixed first.  That being said are there any major performance differences with the workaround in place from .29 to .31, speed differences?

---

### Post by GFree on 2007-02-17
I have another question. This has happened with both .30 and .31 of WINE, but I can't seem to get CSS to run for any great length of time before it crashes. If I run my own game (i.e. new server, not connecting to a net server), it seems to be fine. If I connect to a server on the net though, it will hang for a few seconds and crash/disappear during either the join, where the black message box is displayed, or soon after. I've noticed HL2 will occasionally crash in the same manner, though not as frequently. Kinda makes it difficult to play much CSS.

That and the fact transparent textures seem to have some issues with not being shown, but that's another story.

---

### Post by Fitzy_oz on 2007-02-17
> **GFree said:**
> I have another question. This has happened with both .30 and .31 of WINE, but I can't seem to get CSS to run for any great length of time before it crashes. If I run my own game (i.e. new server, not connecting to a net server), it seems to be fine. If I connect to a server on the net though, it will hang for a few seconds and crash/disappear during either the join, where the black message box is displayed, or soon after. I've noticed HL2 will occasionally crash in the same manner, though not as frequently. Kinda makes it difficult to play much CSS.

That and the fact transparent textures seem to have some issues with not being shown, but that's another story.

Mine crashes but only when I try and muck around with too many settings at once and as yet I have not tried 0.9.31 due to the posts here.  Did u have these issues in 0.9.29?  Might be worth pasting a bug report in the appdb on winehq.org

---

### Post by GFree on 2007-02-17
> **Fitzy_oz said:**
> Mine crashes but only when I try and muck around with too many settings at once and as yet I have not tried 0.9.31 due to the posts here.  Did u have these issues in 0.9.29?  Might be worth pasting a bug report in the appdb on winehq.org
I've tried many things including forcing dxlevel 7, but it doesn't seem to do much to fix the crashing. It's difficult to pin-point the cause, so I'll keep looking. I never tried 0.9.29; the moment I installed Ubuntu I made sure I had the latest version. Ah well.

---

### Post by Pugwash on 2007-02-18
I'm downloading css now, hope it works :grin: !

---

### Post by ghandi69_ on 2007-02-18
Hey all... I'm running wine version .31  (well I did a sudo apt-get upgrade wine.. which I'm pretty sure got me 3.1) .. and its still running the same as before which gives me two problems...

1.)Game still freezes whenever I see flash grenade.

2.) Game runs pretty good performance wise.. however when I try to use the WINEDEBUG thinger... I get an error saying... "command not found"

and ideas?

---

### Post by Fitzy_oz on 2007-02-18
> **GFree said:**
> I've tried many things including forcing dxlevel 7, but it doesn't seem to do much to fix the crashing. It's difficult to pin-point the cause, so I'll keep looking. I never tried 0.9.29; the moment I installed Ubuntu I made sure I had the latest version. Ah well.

Might be worth running it from the console with out the WINEDEBUG="-all" and force CSS to run in a window so you can see the output in the console, might give you a hint to what is triggering the crash....

---

### Post by Fitzy_oz on 2007-02-18
> **ghandi69_ said:**
> Hey all... I'm running wine version .31  (well I did a sudo apt-get upgrade wine.. which I'm pretty sure got me 3.1) .. and its still running the same as before which gives me two problems...

1.)Game still freezes whenever I see flash grenade.
[COLOR="Red"]Disable the wine repositories, then get the 0.9.29 deb from [here]("http://wine.budgetdedicated.com/archive/index.html") and install it, this resolved my issue 
[/COLOR]
2.) Game runs pretty good performance wise.. however when I try to use the WINEDEBUG thinger... I get an error saying... "command not found"

and ideas?

[COLOR="Red"]drop to the console and paste this in WINEDEBUG="-all" wine "C:\Program Files\Valve\Steam\steam.exe" -applaunch 240[COLOR="Red"][/COLOR][/COLOR]

---

### Post by Protoss on 2007-02-18
Hey guys, there is a patch for Wine to fix HL2 and CSS menus!
[http://www.winehq.org/pipermail/wine-patches/2007-February/035990.html](http://www.winehq.org/pipermail/wine-patches/2007-February/035990.html)
I'm going to try it now, and see if it actually fixes it.

---

### Post by bastiegast on 2007-02-18
How do you apply a patch?

---

### Post by Protoss on 2007-02-18
I think the patch was made to be applied to Wine-GIT, so I am going to just apply it manually (No clue if I did it correctly), see if it actually fixes it, and then I'll just upload the package.

---

### Post by Jarn on 2007-02-18
It does fix it. I applied it a few days ago. I should have posted it here, but I didn't think of it. However, the patch didn't work with the patch command - it errored out. I had to change the listed stuff manually.

However, I have another problem. Steam runs fine, but when I try to launch CS:S it tells me the registry is in use by another process. And every time I do shut down correctly (File -> Exit).

EDIT: Oh, this seemed to fix it: [http://ubuntuforums.org/showpost.php?p=1960714&postcount=3](http://ubuntuforums.org/showpost.php?p=1960714&postcount=3) - However, I have no sound :(. Hardware Acceleration is emulation, Default sample rate is 44100, Default bits per sample is 16, Driver emulation is checked, and OSS is set in winecfg.

---

### Post by Protoss on 2007-02-18
=/ Well I applied the patch to fix the menu problem, but now nothing else works. HL2's menu works fine, I can access the Options menu, but CSS freezes whenever I try to start or join a game, or even access the Options menu.

---

### Post by pepolez on 2007-03-03
The method posted here did not work as excepted for me.

(Using wine_0.9.30-0ubuntu2~edgy1_i386)
I found that instead of running
```

$ wine setup

```
I had to run
```

$ winecfg

```
Secondly, I had to put the command to start Steam into a bash script:
```

#!/bin/sh
## Start steam with WINE
WINEDEBUG="fixme-all" wine "C:\Program Files\Steam\steam.exe"

```


This was simply to get Steam to start in the first place. After starting Steam, I encountered the window focus glitch, requiring me to right and then left click in the username and password fields. Also Steam has decided that all of my purchased games were only preloaded. Now that I had Steam running, I exited Steam and copied the 'steamapps' directory from my windows Steam installation.

After doing this, I started Steam again, and logged in. Steam was still convinced I didn't own any games, and that they were simply preloaded. I tried logging out and logging in with my brother's account, and all of the games except for GarrysMod 10 showed up correctly.

Next, I tried to start Counterstrike source, which garbled my screen ([http://beta.toxicantidote.net/files/indexok/ubuntu-css/startup.png](http://beta.toxicantidote.net/files/indexok/ubuntu-css/startup.png)) but did start correctly, without any evident problems. Next I tried joining an empty server. After waiting normal (same as windows) load times, the game loaded successfully and I was able to select a team, player model and weapons. I could run around the level  (de_aztec) and do everything normally, except for a few texture glitches:
[http://beta.toxicantidote.net/files/indexok/ubuntu-css/de_aztec0002.jpg](http://beta.toxicantidote.net/files/indexok/ubuntu-css/de_aztec0002.jpg)
[http://beta.toxicantidote.net/files/indexok/ubuntu-css/de_aztec0003.jpg](http://beta.toxicantidote.net/files/indexok/ubuntu-css/de_aztec0003.jpg)
[http://beta.toxicantidote.net/files/indexok/ubuntu-css/de_aztec0004.jpg](http://beta.toxicantidote.net/files/indexok/ubuntu-css/de_aztec0004.jpg)
[http://beta.toxicantidote.net/files/indexok/ubuntu-css/de_aztec0005.jpg](http://beta.toxicantidote.net/files/indexok/ubuntu-css/de_aztec0005.jpg)

Seeing that this worked, I decided to try starting a local server (with map cs_office). Which I was able to do successfully. Again I could move around and play the game normally, aside from a few texture problems including missing fog:
[http://beta.toxicantidote.net/files/indexok/ubuntu-css/cs_office0008.jpg](http://beta.toxicantidote.net/files/indexok/ubuntu-css/cs_office0008.jpg)
[http://beta.toxicantidote.net/files/indexok/ubuntu-css/cs_office0012.jpg](http://beta.toxicantidote.net/files/indexok/ubuntu-css/cs_office0012.jpg)
and weird ice like stuff on some walls:
[http://beta.toxicantidote.net/files/indexok/ubuntu-css/cs_office0009.jpg](http://beta.toxicantidote.net/files/indexok/ubuntu-css/cs_office0009.jpg)
[http://beta.toxicantidote.net/files/indexok/ubuntu-css/cs_office0010.jpg](http://beta.toxicantidote.net/files/indexok/ubuntu-css/cs_office0010.jpg)
[http://beta.toxicantidote.net/files/indexok/ubuntu-css/cs_office0011.jpg](http://beta.toxicantidote.net/files/indexok/ubuntu-css/cs_office0011.jpg)

Next I decided to try joining a server with about 8 players playing cs_office. As soon as the game had loaded, it lagged to an unplayable level, with characters warping everywhere and >400ms latency (my latency to the server is normally around 20ms). Although the FPS meter reported 13fps, this appeared as if it was rendering a frame approximately every 7 seconds.

After this, I read through this thread a bit further, and decided to upgrade WINE (to version wine_0.9.31~winehq0~ubuntu~6.10-1_i386). Steam started again fine, and I was able to login to my brother's account (mine still said everything was only preloaded) but this time when I tried to start Counterstrike source, I was presented with the garbled screen while it was loading and then with a blank grey screen. I tried moving the mouse around a bit, and found the menu had loaded, but simply was not shown. I was able to move my mouse to where the quit button would have been and press it. The screen then turned white, but I was able to click where the 'quit game' option in the dialog box would be.

I then decided to try starting Halflife 2. This started ok, again with the garbled screen, but then changing to the Halflife 2 loading screen (blurred background, black box saying 
'Loading'). After this the game simply gave me a greenish grey (teal?) screen. I was not able to exit the game by clicking where the quit button would have been, and was forced to restart the X server (ctrl+alt+backspace).

After the upgrade, even with any combination of the '-gl' and '-dxlevel 81' game command line options I had the same result.

I have no idea what to do here, other then include some information (collected after upgrading WINE):

**System specs:**
AMD Semperon 2400+ (1.6GHz)
XFX nVidia 6600GT AGP graphics card
1GB unknown brand DDR RAM
MSI KM4AM-L motherboard

**Terminal output when starting Steam:**
```

7err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 

4b0b9012 while expecting b2d876d1)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 64f71bbd while expecting c34120d0)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 37737ec1 while expecting 5f878f92)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 240df4c3 while expecting 96bfbe8d)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 786b232d while expecting 6438b370)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 61383a03 while expecting a3c17729)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got de7b20bf while expecting 08ebb121)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got fbce8c37 while expecting dfe04873)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got eac9c054 while expecting a8f718cf)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 97ad029c while expecting 430b342a)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got b331dc2e while expecting 574dc8d2)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 8b691573 while expecting 5ccd22a3)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 860f4619 while expecting 702c3ab4)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got b7c819c9 while expecting f679ad14)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got ebf85602 while expecting 7783ce51)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 18e1ba4c while expecting 03449ac6)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 18760f3e while expecting 5cbae5d7)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 41e1f9a6 while expecting dbb3553b)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 6c2ab690 while expecting 82dcf21e)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got d1619f5e while expecting a4873846)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 1b3b353b while expecting dc4315be)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 9f44ede3 while expecting b0164827)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 158b670b while expecting c0d3aae9)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 730b689d while expecting bb3d4695)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 409c20c8 while expecting 5a2362e6)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 3117bb85 while expecting 3f1033ce)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got ddc3c9f6 while expecting da51481b)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 6b854447 while expecting 9afeeab8)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 980c03f3 while expecting 5768dd08)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 9d20bc6c while expecting ce5ab09f)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got b425c94f while expecting fb5386b8)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got c00f8568 while expecting 944aaa52)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got cfaf839f while expecting 28b76abe)

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 0118ed6f while expecting dc880658)

err:systray:delete_icon invalid tray icon ID specified: 1d

```

**Terminal output when starting Counterstrike Source or Halflife 2:**
```

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered

err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1

err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)

```

**glxinfo**
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/AGP/SSE/3DNOW!
OpenGL version string: 2.0.2 NVIDIA 87.76
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_HP_occlusion_test, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_gpu_program_parameters, GL_NV_half_float, GL_NV_light_max_exponent, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x134 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

**/proc/cpuinfo**
```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 8
model name      : AMD Sempron(tm)   2400+
stepping        : 1
cpu MHz         : 1665.978
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts
bogomips        : 3335.32

```

**uname -a**
```

Linux nibbler 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux

```

**lshw**
```

nibbler                   
    description: Desktop Computer
    product: KM400-8237
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MS-6734
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (07/28/2004)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm)   2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 1666MHz
          capacity: 2100MHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 1GB
          capacity: 2GB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MB
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: c0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:c0000000-cfffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV43 [GeForce 6600/GeForce 6600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a2
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master vga_palette cap_list
                configuration: driver=nvidia
                resources: iomemory:e0000000-e0ffffff iomemory:d0000000-dfffffff iomemory:e1000000-e1ffffff irq:201
        *-network:0
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 7
             bus info: pci@00:07.0
             logical name: eth0
             version: 10
             serial: 00:30:bd:19:15:76
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.2.3 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:d000-d0ff iomemory:e4000000-e40000ff irq:193
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@00:0f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:d400-d40f irq:169
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: WDC WD800JB-00FMA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 13.03G13
                   serial: WD-WMAJ91083579
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 10236MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 101MB
                      capabilities: primary
                 *-volume:2
                      description: Linux swap / Solaris partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 509MB
                      capabilities: primary nofs
                 *-volume:3
                      description: Extended partition
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      capacity: 63GB
                      capabilities: extended partitioned partitioned:extended
              *-disk:1
                   description: ATA Disk
                   product: ST3120022A
                   vendor: Seagate
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 8.54
                   serial: 5JS3GA1M
                   size: 111GB
                   capacity: 111GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume
                      description: W95 Ext'd (LBA) partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 111GB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: DVD reader
                   product: PIONEER DVD-117RD 0105
                   vendor: Pioneer
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.05
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio dvd
                   configuration: mode=udma4
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
              *-cdrom:1
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GSA-4163B
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: A103
                   serial: K2653HC0948
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: ET-0405A-UV2.0-3
                   vendor: WACOM
                   physical id: 1
                   bus info: usb@1:1
                   version: 2.03
                   capabilities: usb-1.10
                   configuration: driver=wacom maxpower=40mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:dc00-dc1f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: USB hub
                   product: G11 Keyboard
                   vendor: Logitech, Inc.
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.71
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
                 *-usb:0
                      description: Keyboard
                      product: Gaming Keyboard
                      vendor: Logitech, Inc.
                      physical id: 1
                      bus info: usb@2:1.1
                      version: 1.90
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
                 *-usb:1
                      description: Human interface device
                      product: G11 Keyboard
                      vendor: Logitech, Inc.
                      physical id: 4
                      bus info: usb@2:1.4
                      version: 1.71
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=12.0MB/s
              *-usb:1
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@2:2
                   version: 27.10
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:e000-e01f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:e400-e41f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e4001000-e40010ff irq:177
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-11-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb:0
                   description: Mass storage device
                   product: USB Mass Storage Device
                   vendor: Myson Century, Inc.
                   physical id: 5
                   bus info: usb@5:5
                   logical name: scsi0
                   version: b0.07
                   serial: 100
                   capabilities: usb-2.00 emulated scsi-host
                   configuration: driver=usb-storage maxpower=10mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: MHV2040AH
                      vendor: FUJITSU
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 0000
                      size: 37GB
                      capabilities: partitioned partitioned:dos
                    *-volume
                         description: W95 FAT32 partition
                         physical id: 1
                         bus info: scsi@0:0.0.0,1
                         logical name: /dev/sda1
                         capacity: 37GB
                         capabilities: primary
              *-usb:1
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 7
                   bus info: usb@5:7
                   version: 6.0b
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:e800-e8ff irq:209
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth1
             version: 78
             serial: 00:11:09:2c:59:e6
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full ip=172.20.0.205 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:ec00-ecff iomemory:e4002000-e40020ff irq:185

```

Anybody have any ideas? If not I might have to keep dualbooting so I can play my games :<

---

### Post by ijjz on 2007-03-03
> **pepolez said:**
> After this, I read through this thread a bit further, and decided to upgrade WINE (to version wine_0.9.31~winehq0~ubuntu~6.10-1_i386). Steam started again fine, and I was able to login to my brother's account (mine still said everything was only preloaded) but this time when I tried to start Counterstrike source, I was presented with the garbled screen while it was loading and then with a blank grey screen. I tried moving the mouse around a bit, and found the menu had loaded, but simply was not shown. I was able to move my mouse to where the quit button would have been and press it. The screen then turned white, but I was able to click where the 'quit game' option in the dialog box would be.

I then decided to try starting Halflife 2. This started ok, again with the garbled screen, but then changing to the Halflife 2 loading screen (blurred background, black box saying 
'Loading'). After this the game simply gave me a greenish grey (teal?) screen. I was not able to exit the game by clicking where the quit button would have been, and was forced to restart the X server (ctrl+alt+backspace).

After the upgrade, even with any combination of the '-gl' and '-dxlevel 81' game command line options I had the same result.

I have no idea what to do here, other then include some information (collected after upgrading WINE):

The gray screen issue is a problem with wine 0.9.31.  

Wine 0.9.32 was just released last night which should fix this problem.

To get around this, add ```
+map de_dust
``` to your startup command, once loaded you should be able to get access to the menu.

---

### Post by Pugwash on 2007-03-04
No, its not working for me, I get a black screen after the loading screen. I've entered "+map de_dust" in the launcher options but it doesn't seem to do anything. Anybody know whats wrong?

---

### Post by Fitzy_oz on 2007-03-04
> **Pugwash said:**
> No, its not working for me, I get a black screen after the loading screen. I've entered "+map de_dust" in the launcher options but it doesn't seem to do anything. Anybody know whats wrong?

Try running winecfg and enabling the pixel shader checkbox under the video section - This worked for me for 0..9.31.    Alternatively - I just run CSS as normal and when the gray blank screen appears i hit the console key and type map de_dust and hit enter.  this starts a local server for that map after whcih the menu will be visible and you will be able to seledct the options normally provided there is a map loaded in the background.

---

### Post by finite9 on 2007-03-12
> **ErikTheRed said:**
> From what I can tell the -gl option doesn't offer much of a performance boost but it does seem to eliminate a lot of the graphical glitches I was getting without it.

how do you pass the -gl option?  I have a steam link on the desktop that starts:

env WINEPREFIX="/home/andrew/.wine" wine "C:\Program Files\Steam\steam.exe"

and if I add -gl to that before the last double quote then steam doesn't start.  If I type:

env WINEPREFIX="/home/andrew/.wine" wine "C:\Program Files\Steam\steamapps\adhenry\half-life 2\hl2.exe -gl"

then wine says that the program could not be found.  How do you do this?

---

### Post by frodon on 2007-03-12
Thanks mate, i tested it and it works like a charm, what is hard to believe is that i get better results with wine than cedega !

I think i will give up cedega soon.

Again thank you.

---

### Post by jacksaff on 2007-03-12
> **finite9 said:**
> how do you pass the -gl option?  I have a steam link on the desktop that starts:

env WINEPREFIX="/home/andrew/.wine" wine "C:\Program Files\Steam\steam.exe"

and if I add -gl to that before the last double quote then steam doesn't start.  If I type:

env WINEPREFIX="/home/andrew/.wine" wine "C:\Program Files\Steam\steamapps\adhenry\half-life 2\hl2.exe -gl"

then wine says that the program could not be found.  How do you do this?

The -gl is inside the quotes so wine thinks it is part of the file name. Try the command using \ to escape the '\'s and the spaces instead of using the ".

---

### Post by Fitzy_oz on 2007-03-14
> **finite9 said:**
> how do you pass the -gl option?  I have a steam link on the desktop that starts:

env WINEPREFIX="/home/andrew/.wine" wine "C:\Program Files\Steam\steam.exe"

and if I add -gl to that before the last double quote then steam doesn't start.  If I type:

env WINEPREFIX="/home/andrew/.wine" wine "C:\Program Files\Steam\steamapps\adhenry\half-life 2\hl2.exe -gl"

then wine says that the program could not be found.  How do you do this?

Hey,
The -gl option must be passed from within steam  under the games properties.
Right click on Counter-Strike Source and select properties, then goto advanced or startup options (I can;t remeber off the top of my head) and add the switch -gl in there.

---

### Post by finite9 on 2007-03-14
> **Fitzy_oz said:**
> Hey,
The -gl option must be passed from within steam  under the games properties.
Right click on Counter-Strike Source and select properties, then goto advanced or startup options (I can;t remeber off the top of my head) and add the switch -gl in there.

Thanks, that solved it; In Steam, when you choose the Games tab, right-click the game in question then choose Properties|Advanced and startup options.  Here I could add -gl or -dxlevel 90.

-gl solved the issue for me!  But performance suffered slightly and gfx do *not* look as nice as dx 9 :(  -dxlevel 90 changed the hardware setting in-game so that both hw and sw read dx 90 but it  was running completely in software mode!!  Even though I forced it, it would not use my cards hardware acceleration for dx 9.  So basically it ran like a pig.  Shame as dx 9 does unfortunately look nicer in hl2.

Thanks for the tip!!

---

### Post by frodon on 2007-03-20
I have a question.

I have good performances with counter strike source and steam but i wonder if i can increase the performances forcing counter strike source to use opengl and not directx and does forcing the game to use opengl will make the game using hardware acceleration instead of emulation ?
I am not using any options to launch steam and my main problem is that i don't have access to my biggest resolution which is 1280*1024.

---

### Post by finite9 on 2007-03-21
When I force opengl, it runs slightly slower than dx.  I compare the first opening scene in HL2, as there are no dx9 specific effects until you come out of the train station in HL2.  I am running a Core2Duo 7200 with 2GB RAM and nVidia Go 7600 512MB on a HP Pavilion so maybe if you have lower specs, the performance difference between gl and dx will be greater.

I have to force gl despite slightly lower performance as dx9 runs like its on a dx50 with 4MB ram when I come across and dx9 specific effects.

---

### Post by mayfer on 2007-03-24
> **abzolutxero said:**
> for those of you who have gotten steam running, i have a few questions....

steam runs, downloads the game files, chat works, friends list... etc.... as soon as i try to load a game, it resizes the screen to 640x480, and then the game hangs.  steam still works, but obviously wont exit because it is trying to load a game... i have the most current nvidia drivers installed, so i assume it isnt gfx... is there a wine configuration i am missing?  thanks

with me, changing the sound driver from both ALSA and OSS to only OSS in winecfg solved this exact same problem.

cheers,
- Murat

---

### Post by frodon on 2007-03-30
Unfortunatly the OP is not often here to keep this guide up date, i wonder if one of you would be interested to post an updated guide based on the first post and keep it up to date.
It would be good to include for example the detail of the possible option like -gl, -dxlevel, -console and so on.
Also it would be good to list all the wine version which have problems to run steam, from what i know 0.30 and 0.31.
Anyone tested CSS with wine 0.33 ?

If anyone is interested go for it then send me the link to the new thread and i will close this one and leave a link to the updated thread.

---

### Post by Enverex on 2007-03-30
> **frodon said:**
> Unfortunatly the OP is not often here to keep this guide up date, i wonder if one of you would be interested to post an updated guide based on the first post and keep it up to date.
It would be good to include for example the detail of the possible option like -gl, -dxlevel, -console and so on.
Also it would be good to list all the wine version which have problems to run steam, from what i know 0.30 and 0.31.
Anyone tested CSS with wine 0.33 ?

If anyone is interested go for it then send me the link to the new thread and i will close this one and leave a link to the updated thread.

Actually a better idea would be to add the guide as a "HowTo" on the appDB page so everyone can make use of it rather than putting it in an obscure thread in a forum.

---

### Post by frodon on 2007-03-30
Which appDB are you refering to ?
We need a thread for support and maintain the guide up to date in all the case IMO, the purpose is just to have someone to maintain the guide.

---

### Post by Enverex on 2007-03-30
> **frodon said:**
> Which appDB are you refering to ?
We need a thread for support and maintain the guide up to date in all the case IMO, the purpose is just to have someone to maintain the guide.

The Official Wine Application Compatibility Database, the one everyone is expected to check before asking for help with the program they are trying to run. [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by frodon on 2007-03-30
Good call, we should add this link somewhere in a sticky.

Thanks for pointing this out.

---

### Post by StarLog on 2007-04-02
How do I get past the blob error that was mentioned earlier.
I launches, then cannot find or create a blob.

---

### Post by frodon on 2007-04-03
I tested the guide with wine 0.32 and the new wine 0.34 without any problems however you will got a black screen if you enabled GLSL shader so remove the entry you added in the registry if you are going to use these versions.
About the performances the gain is really good, i got an average FPS of 56 with wine 0.22 and 76 with wine 0.34 and i use -gl and -dxlevel 80 option.

So if you don't use GLSL shader or don't mind removing it go for wine 0.34 you will gain performances.

---

### Post by CptCrncher87 on 2007-04-05
I'm new to Ubuntu and have been into gaming for awhile so when i saw you can put CS on here i jumped at it and have been working on getting it to work for awhile.  Normally i like to avoid posting if at all possible about my problems because they end up being stupid in some say or form but this one has got me stumped.  After months of trying to get CS to even start i now have the problem of horrible lag.  I am pulling off 1.54 FPS and i can't seem to increase that at all.  I have looked up and down this thread to see if there was anything i can do and i have tried all that i can to get it to work but it has got me stumped.  I am running it on an Inspiron E1505 with an ATI graphics card.  Any advice on the problem i'm having would be most appreciated.  Here are my specs i tried eliminating spots i didn't think were important such as usb and what-not:

>     description: Portable Computer
    product: MM061
    vendor: Dell Inc.
    serial: BYN1Z91
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-5900-104E-8031-C2C04F5A3931
  *-core
       description: Motherboard
       product: 0XD720
       vendor: Dell Inc.
       physical id: 0
       serial: .BYN1Z91.CN4864364A2091.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A12 (12/18/2006)
          size: 64KB
          capacity: 512KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2300  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: Microprocessor
          size: 1GHz
          capacity: 1800MHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MB
             capacity: 2MB
             clock: 66MHz (15ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 64T64020HDL3.7A
             vendor: C100000000000000
             physical id: 0
             serial: 021D7010
             slot: DIMM_B
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.87617ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 64T64020HDL3.7A
             vendor: C100000000000000
             physical id: 1
             serial: 021D4821
             slot: DIMM_A
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.87617ns)
     *-cpu:1
          product: Genuine Intel(R) CPU           T2300  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci
                resources: iomemory:d0000000-dfffffff ioport:ee00-eeff iomemory:efdf0000-efdfffff irq:169
        *-multimedia
             description: Multimedia controller
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:efffc000-efffffff irq:233
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0b:00.0
                logical name: eth1
                version: 02
                serial: 00:13:02:5b:4b:4b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.0.5m firmware=13.0 1:0 () ip=131.204.217.60 link=yes multicast=yes wireless=IEEE 802.11g
                resources: iomemory:efcff000-efcfffff irq:169
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@03:00.0
                logical name: eth0
                version: 02
                serial: 00:15:c5:11:73:ba
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
                resources: iomemory:ef9fe000-ef9fffff irq:217
           *-firewire
                description: FireWire (IEEE 1394)
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@03:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:ef9fd800-ef9fdfff irq:177
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@03:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:ef9fd400-ef9fd4ff irq:66
           *-system:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@03:01.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:ef9fd500-ef9fd5ff irq:9
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@03:01.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:ef9fd600-ef9fd6ff irq:9
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.4
                bus info: pci@03:01.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:ef9fd700-ef9fd7ff irq:9
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix
             resources: ioport:bfa0-bfaf irq:217
           *-disk
                description: SCSI Disk
                product: Hitachi HTS54108
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MB4O
                serial: MPBDP0XKG7TKLM
                size: 73GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: FAT16 partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 47MB
                   capabilities: primary
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 58GB
                   capabilities: primary bootable
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 14GB
                   capabilities: extended partitioned partitioned:extended
           *-cdrom
                description: DVD writer
                product: DVD+-RW ND-6650A
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 102C
                serial: [_NEC    DVD+-RW ND-6650A102C05051200
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             resources: ioport:10c0-10df irq:5


---

### Post by Valstorm2323 on 2007-04-07
Dammit thanks for the winefile command. 
I couldn't figure out where the damned wine was, seems it's autohidden after being installed... why would anyone do that DOH!

---

### Post by Fitzy_oz on 2007-04-11
> **CptCrncher87 said:**
> I'm new to Ubuntu and have been into gaming for awhile so when i saw you can put CS on here i jumped at it and have been working on getting it to work for awhile.  Normally i like to avoid posting if at all possible about my problems because they end up being stupid in some say or form but this one has got me stumped.  After months of trying to get CS to even start i now have the problem of horrible lag.  I am pulling off 1.54 FPS and i can't seem to increase that at all.  I have looked up and down this thread to see if there was anything i can do and i have tried all that i can to get it to work but it has got me stumped.  I am running it on an Inspiron E1505 with an ATI graphics card.  Any advice on the problem i'm having would be most appreciated.  Here are my specs i tried eliminating spots i didn't think were important such as usb and what-not:

Theres nothing stupid about asking for help, no matter how trivial it may be.  it's a new os for you and no one should be or to my knowledge ever has been flasmed or made to feel like an idiot on these forums for asking any sort of questions basic or not...

ATI is something of a dirty word last time I tried using it with CS:S.  my only advice would be to make sure that you have the proprietary drivers installed.  The easiest way to do this is to follow this [HowTo]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide").  Method 2 yielded the best results for my ATi card.

After which typing glxinfo in terminal should output something like this

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: "Radeon type...."
OpenGL version string: 2.0.6400 (8.35.5)


Somewhere further down it will also have line that says "direct rendering:" and it will either be yes or no.  If it's yes you're in luck, if not check the logs for errors (I had to have a couple of goes at getting the kernel module to load).

If all has gone well you should see a marked improvement in performance.

Good luck, and shout out if you need some more help, that's why we're here ;)

---

### Post by Kittens on 2007-04-15
I have tahoma.ttf font in the folder, but the words still don't show up.

---

### Post by buttons on 2007-04-15
> **Kittens said:**
> I have tahoma.ttf font in the folder, but the words still don't show up.

Downgrade to wine 0.9.34.  0.9.35 has an Xrender bug that prevents them from being displayed.  You can also recompile 0.9.35 with the fix per [this thread]("http://ubuntuforums.org/showthread.php?t=409286").

---

### Post by w116tjb on 2007-04-21
> **Kittens said:**
> I have tahoma.ttf font in the folder, but the words still don't show up.

Download Tahoma.tff by going to Google and searching "filetype:ttf inurl:tahoma". Download the file to your desktop.

Open Terminal and type:
```

cd /home/USERNAME/Desktop
sudo cp Tahoma.ttf /usr/share/wine/fonts

```

After that, you can just delete the file from your desktop. Restart Steam and you should have text.

---

### Post by CptCrncher87 on 2007-05-03
I have hit a wall.  From what i can tell I have eliminated lag, this is from my assumption that i reloaded Ubuntu using a distribution called Ubuntu Ultimate 1.2 which came preloaded with wine for those who don't know about it.  The load screen loads fine but then it goes down from there.  I get a blank screen every time.  It started with black, then went to white when i messed with the graphics option of the winecfg and is now grey since i messed with the load options in steam.  Does anyone know what is going on and how i can stop it or am i stuck pushing buttons in the dark?  I appreciate the help.

---

### Post by Fitzy_oz on 2007-05-03
> **CptCrncher87 said:**
> I have hit a wall.  From what i can tell I have eliminated lag, this is from my assumption that i reloaded Ubuntu using a distribution called Ubuntu Ultimate 1.2 which came preloaded with wine for those who don't know about it.  The load screen loads fine but then it goes down from there.  I get a blank screen every time.  It started with black, then went to white when i messed with the graphics option of the winecfg and is now grey since i messed with the load options in steam.  Does anyone know what is going on and how i can stop it or am i stuck pushing buttons in the dark?  I appreciate the help.

Depends on the version of wine thats shipped with it but at a guess i'd say it's the pixel shader bug - Simply turning off the pixel shader option in winecfg resolved this for me.  Also there are a couple of posts a page or so back that address this problem.  Im not sure exactly what the command is bt you need to set the command switches so it opens a map at startup, I think the option is +map de_dust or +de_dust or something to that effect.

---

### Post by CptCrncher87 on 2007-05-03
Ok i've got steam css working almost exactly the way i want it except terrible fps.  I have tried messing with audio and graphics but neither seem to help and i have tried lowering gl to as low as 60 and as high as 80 but that doesn't seem to help either.  Any tips for this problem? (not sure how to check my wine version so if you ask about that i will have no clue unless you tell me how but it did come with the ubuntu) and i really appreciate your help Fitzy

---

### Post by foundation on 2007-05-04
On steampowered.com the download is now an MSI instead of EXE so I tried installing it anyway with the wine SteamInstall.msi command and it didn't work:

```
~/Desktop$ wine SteamInstall.msi
wine: could not load L"Z:\\home\\seldon\\Desktop\\SteamInstall.msi": Bad EXE format for
```

---

### Post by buttons on 2007-05-04
> **foundation said:**
> On steampowered.com the download is now an MSI instead of EXE so I tried installing it anyway with the wine SteamInstall.msi command and it didn't work:

```
~/Desktop$ wine SteamInstall.msi
wine: could not load L"Z:\\home\\seldon\\Desktop\\SteamInstall.msi": Bad EXE format for
```

[http://www.google.com/search?q=steaminstall.exe]("http://www.google.com/search?q=steaminstall.exe")

Currently wine does not support MSI.  Your best bet is to simply grab an old steaminstall.exe elsewhere on the web.  Steam will update itself during installation.

If you have a transgaming subscription, it is also available in their downloads area.

---

### Post by foundation on 2007-05-05
Good idea, can't believe I didn't think of that. D: Thanks.

New error, I'm so lucky. :o

[http://img520.imageshack.us/img520/294/tmpgl7.png](http://img520.imageshack.us/img520/294/tmpgl7.png)

Ideas ?

---

### Post by Jarn on 2007-05-05
> **buttons said:**
> Currently wine does not support MSI.Actually, it does. I don't remember the exact command, I'm just going from memory, but it's something like: ```
wine msiexec /i /path/to/msi/file
```That's more likely than not wrong, though. Ask in #winehq for the syntax to install msi files, they'll be able to tell you.

---

### Post by Fitzy_oz on 2007-05-05
> **CptCrncher87 said:**
> Ok i've got steam css working almost exactly the way i want it except terrible fps.  I have tried messing with audio and graphics but neither seem to help and i have tried lowering gl to as low as 60 and as high as 80 but that doesn't seem to help either.  Any tips for this problem? (not sure how to check my wine version so if you ask about that i will have no clue unless you tell me how but it did come with the ubuntu) and i really appreciate your help Fitzy

Are you using the proprietary driver?, if possible type glxinfo in a terminal and post it here...

---

### Post by LuckN1ne on 2007-05-06
wine does support msi... but my problem is i need the command to start steam up

---

### Post by lordhebe on 2007-05-07
Here is the correct command ```
msiexec /i SteamInstall.msi
```

> **LuckN1ne said:**
> wine does support msi... but my problem is i need the command to start steam up

Do a ```
wine "C:/Path/To/Steam/steam.exe"
```

---

### Post by CptCrncher87 on 2007-05-08
hmmmm well i tried just running it to see if it would do the same thing and the first trial it was full screen and laggy, then it was small and laggy, then it was small and full speed, and now it is running full screen at full speed so i'm not sure what happened with it but it seems to have fixed itself thanks for the help with the problems

---

### Post by nvrpaul on 2007-05-17
how do you install from the CDs cs:source. I get a mount issue, i cannot eject cd1 because it is in use by wine obviously. I tried running the installer from within the D: directory of .wine and dosdevices. Same problem. I tried copying the content of all of the discs into one folder on the HDD, but in this case it just doesn't let me run it from there, it wants to have the first cd in (which it does). Is there any other way other than downloading?

---

### Post by Jonathan2007 on 2007-05-23
> **nvrpaul said:**
> how do you install from the CDs cs:source. I get a mount issue, i cannot eject cd1 because it is in use by wine obviously. I tried running the installer from within the D: directory of .wine and dosdevices. Same problem. I tried copying the content of all of the discs into one folder on the HDD, but in this case it just doesn't let me run it from there, it wants to have the first cd in (which it does). Is there any other way other than downloading?
I am having the exact same problem. I get to the prompt for CD 2 and I can unmount the cdrom and mount CD 2 but the installer won't recognize it. I even tried copying CD 1 to a folder and installing. I got prompt for CD 2 and so I erased the CD 1 contents and ripped CD 2 contents to the same folder and the installer still won't recognize it.

I'd rather not download all this if I can avoid it seeing as how I have the install CD's right here in front of me.

---

### Post by Orion2014 on 2007-05-24
Would this also work with counter strike condition zero? Its basically the same as counterstrike 1. I enjoy that game more and would rather play it honestly.

---

### Post by Fitzy_oz on 2007-05-28
> **Orion2014 said:**
> Would this also work with counter strike condition zero? Its basically the same as counterstrike 1. I enjoy that game more and would rather play it honestly.

It should work just fine, I played half-life 1 source aunder wine for ages and it was fine.  There is absolutely no reason why CS:CZ should be any different.

---

### Post by ea_hatch on 2007-06-03
ok ive got steam installed but every time i try to log in i get this error
[img]http://img359.imageshack.us/img359/4285/screenshotdesktopgt8.jpg[/img]

im runnning a linksys wireless card, but it works fine in windows so im not sure if it is that..it will tell me if i put in the wrong password but when i login with the right info it just sits there for about a minute and then give me the error..any ideas?

---

### Post by slowdeath on 2007-06-03
did you upgrade wine to 0.9.38, thats what i did, then steam started giving me the same errors. so i went back to 0.9.37 and steam started working normally.

---

### Post by ea_hatch on 2007-06-03
well i just started to install this today so my verion of wine is 0.9.38. How would i revert back to the 9.37???

---

### Post by ea_hatch on 2007-06-04
ok well i figured that out and have css running but i can only run it in dxlevel 70 and it is still way slower than it was in windows xp.. if i try to turn it up to dx 8 or 9 i get this error
[img]http://img372.imageshack.us/img372/1091/screenshotengineerrorqy5.png[/img]

btw my specs are 
am2 4600+
xfx 7900gs
2 gig ddr2 800

in windows with settings on high i could maintain about a 50-60 average fps
now im getting 20-35 average on dx 7

---

### Post by ea_hatch on 2007-06-06
also everytime i get flashed banged my game freezes for about 10 seconds???? any suggestions?

---

### Post by frodon on 2007-06-06
> **ea_hatch said:**
> also everytime i get flashed banged my game freezes for about 10 seconds???? any suggestions?I bet you use an old version of wine, what version of wine are you using ?
If not go back to the 0.34 version which is really stable, all debs are available here :
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by ea_hatch on 2007-06-06
im using 0.9.37 right now
i will try to revert back to 0.9.34 and see if that helps..btw do u know of any way to get it to not alert me about the updates for wine after i do go back?

---

### Post by frodon on 2007-06-06
> **ea_hatch said:**
> im using 0.9.37 right now
i will try to revert back to 0.9.34 and see if that helps..btw do u know of any way to get it to not alert me about the updates for wine after i do go back?Just comment the wine repository in your source.list file, you can do this also using synaptic in the repository properties (third party repository tab).

---

### Post by ea_hatch on 2007-06-06
cool thanx man... i reverted back to 0.9.34 but im still haveing the same problems.. i noticed though if u run it at 1024x768 or lower i dont have the freezes when being flashed..but i play on a 37" westy so that isnt gonna work out for me :(

---

### Post by ea_hatch on 2007-06-12
bump for any ideas on the flash bang freeze problem

---

### Post by rayofash on 2007-06-14
I tried installing from a SteamInstaller.exe and it gave me errors. So then I tried the msiexec command with the .msi installer and it installed seemingly fine. But now when it runs it gives me an error saying "Steam is already running. You may only run one copy of Steam at a time." during the updater. What do I do?

---

### Post by Enverex on 2007-06-14
Run "wineserver -k" and try again.

---

### Post by rayofash on 2007-06-14
> **Enverex said:**
> Run "wineserver -k" and try again.

It went up to 26% and gave me the same error.

---

### Post by mark. on 2007-06-18
i cant get wine for some reason. if iput the command into the terminal i get this error

```
mark@l--desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
```

o.o help please? this also happens when i try and get virtualbox (because i cannot run synaptic)

---

### Post by thisisaric on 2007-06-26
> **rayofash said:**
> It went up to 26% and gave me the same error.

Had same problem... after googling my *** off found 

> 26% Bug Workaround:

Run this from the directory you installed Steam to:

wine steamTmp.exe SelfUpdate "Steam.exe" 14 

If that doesn't help try this before the previous command:

rm ClientRegistry.blob
  here [http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

---

### Post by Enverex on 2007-06-27
> **thisisaric said:**
> Had same problem... after googling my *** off found 

  here [http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

Again, the AppDB should always be the FIRST place you check, not the last.

---

### Post by CompactDestruction on 2007-06-29
Hi can someone help please? I've got the 26% bug on the latest version of Wine on Feisty AMD64. The workaround does not work, the update simply begins again at 0% :( Can someone please help?

---

### Post by CompactDestruction on 2007-06-29
[Here's a screen capture encoded as Theora.]("http://www.sharebigfile.com/file/189545/SteamBug-ogg.html")

---

### Post by joos13 on 2007-07-01
> **thisisaric said:**
> Had same problem... after googling my *** off found 

  here [http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

Doing that workaround results in the error:

Steam.exe (main exception): Failed to get file attributes, Win32 Error 2 "File not found"

the appHQ has no solution.  i also tried the wineserver -k thing.

anyone have any ideas??

---

### Post by Henningselst on 2007-07-02
Duh... Iv made a big mistake my cs 1.6 was up and running but a bit laggy... So i tried to change the graphics away from open gl and now when ever i try to start the game it is so big that i can acsess the options to change the graphics settings.. Does anyone know how i can turn it back to Open gl without entering the game?

---

### Post by CompactDestruction on 2007-07-03
FYI after I restarted my computer suddenly everything started working.

---

### Post by Haz13r on 2007-07-03
how do i check or how am i able to see these hidden files?

---

### Post by joos13 on 2007-07-04
> **Haz13r said:**
> how do i check or how am i able to see these hidden files?

Crtl+H, or under View menu

---

### Post by eazye2008 on 2007-07-05
i cant see anything on steam

---

### Post by w00d77 on 2007-07-05
I followed the instructions on [http://fedorasolved.org/gaming-solutions/installing-steam-using-wine/]("http://fedorasolved.org/gaming-solutions/installing-steam-using-wine/") and I was able to get Steam working just fine on Feisty.  I'm using the newest version of wine.

---

### Post by rayofash on 2007-07-07
Workaround didn't work, same error as posted above.

Edit: I followed that video posted earlier and it worked. Which is funny because it didn't work for the person in the video. I have to run it with sudo though.

---

### Post by Ziggyz on 2007-07-08
```
ziggy@ziggy-desktop:~$ cp tahoma.ttf /home/ziggy/.wine/drive_c/windows/fonts
cp: cannot stat `tahoma.ttf': No such file or directory
```

?? doesent work for me, I even put in the ~ before the .wine. Also when ever i download the steam installer its steaminstaller.msi not exe...

---

### Post by Mike7171 on 2007-07-09
I installed CSS through the Half-Life 2 game of the year pack, and everything went fine. The game is installed and seems fine. But when I run CSS (and any of the other games such as HL2 actually), it gets to the loading screen for the game, and right when the menu should show, the Steam window comes up over top of it. I tried the "close the window before it loads" but then an empty box pops up over it instead (the Wine backround). So it's crashing and I'm not sure why. Any ideas? Any help is appreciated.

---

### Post by quadomatic on 2007-08-14
I found a fix for the problems with the 26% Update:

Uninstall Steam, delete the directory, then follow this guide:

[http://fedorasolved.org/gaming-solutions/installing-steam-using-wine/](http://fedorasolved.org/gaming-solutions/installing-steam-using-wine/)

I'm guessing the .msi installer most people use just doesn't work right.

Now, does anyone know how to install Episode One from the DVD?

---

### Post by Fittersman on 2007-08-19
> **Ziggyz said:**
> ```
ziggy@ziggy-desktop:~$ cp tahoma.ttf /home/ziggy/.wine/drive_c/windows/fonts
cp: cannot stat `tahoma.ttf': No such file or directory
```

?? doesent work for me, I even put in the ~ before the .wine. Also when ever i download the steam installer its steaminstaller.msi not exe...

im having the same problem...

---

### Post by Polygon on 2007-08-20
to run the msi installer use

wine start steaminstall.msi

but i had the 26% bug when i tried with the msi, so use an older version of the steam installer (link below) and when it installs it will update itself and it will be all good

[http://www.filecloud.com/file/161/Steam+Installer/](http://www.filecloud.com/file/161/Steam+Installer/)

note: dont use steam community beta, it makes steam very unstable atm.

---

### Post by Brynster on 2007-08-21
> **Polygon said:**
> 

note: dont use steam community beta, it makes steam very unstable atm.



Works fine for me although a little sluggish feeling in comparioson of original basic steam

---

### Post by anemptygun on 2007-09-13
I get the error message:

"Steam is already running. you may only run one copy of steam at one time"

This is at 26% of the update. I am using the latest wine.

Any ideas?

---

### Post by nvrpaul on 2007-09-29
Hey guys
My CS:S was running fine until out of nowhere sound is broken with this output:
err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
dir: C:\Program Files\Steam\ *.mix
dir: C:\Program Files\Steam\ *.asi
dir: C:\Program Files\Steam\ *.flt
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30


If i set it to emulation sound is choppy and performance is bad. PLease help. Thank you!

---

### Post by asbani on 2007-10-01
Hey guys. it all runs fine only one question tho, how to run CSS without full screen mode? I don't like full screen ;) thanks.


>  Wrote nvrpaul  
Did you try updating to wine 0.9.46?

---

### Post by nvrpaul on 2007-10-02
> **asbani said:**
>  
Did you try updating to wine 0.9.46?
I will try this and let you know the result! thanks man

---

### Post by nvrpaul on 2007-10-02
> **nvrpaul said:**
> I will try this and let you know the result! thanks man

nop, updating didn't work, got rid of the error message, but i still have n osound. I reinstalled alsa, got the latest kernel etc.
Any ideas?

---

### Post by Fittersman on 2007-10-04
> **nvrpaul said:**
> nop, updating didn't work, got rid of the error message, but i still have n osound. I reinstalled alsa, got the latest kernel etc.
Any ideas?

hey, i had a problem with no sound as well, i made a thread on it here:
[http://forum.notebookreview.com/showthread.php?t=174594](http://forum.notebookreview.com/showthread.php?t=174594)
see if doing any of that fixes your problem.

---

### Post by dougmorin on 2007-10-04
Does anyone have a problem loading wine?  I have installed and configured wine but nothing will open with it.  Seems to start loading in the task bar but eventually the window just goes away...

any suggestions?

Original post is here:
[http://ubuntuforums.org/showthread.php?t=567086](http://ubuntuforums.org/showthread.php?t=567086)

---

### Post by nvrpaul on 2007-10-05
i tried fixing the permissions, but it didn't help. I reinstalled ALSA, the lastest kernel, wine, and cs:source from scratch. no go. any other ideas?

---

### Post by Fittersman on 2007-10-05
> **nvrpaul said:**
> i tried fixing the permissions, but it didn't help. I reinstalled ALSA, the lastest kernel, wine, and cs:source from scratch. no go. any other ideas?

did you follow this guied? (i know its for wolfenstein, but it worked for me to get sound in css)

[http://ubuntuforums.org/showthread.php?t=83028&page=3](http://ubuntuforums.org/showthread.php?t=83028&page=3)

---

### Post by nvrpaul on 2007-10-06
> **Fittersman said:**
> did you follow this guied? (i know its for wolfenstein, but it worked for me to get sound in css)

[http://ubuntuforums.org/showthread.php?t=83028&page=3](http://ubuntuforums.org/showthread.php?t=83028&page=3)

tried that. didn't work i get this error message now:

 WINEDEBUG="fixme-all" wine steam.exe -opengl
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dmix:0
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dsnoop:0
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\ *.mix
dir: C:\Program Files\Steam\ *.asi
dir: C:\Program Files\Steam\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30

any help is very greatly appreciated!

---

### Post by nvrpaul on 2007-10-10
fixed it by emptying the asound file in etc. If there isn't one make a blank one and restart. it now works

---

### Post by ebichu on 2007-10-10
Hi, I'm trying to get CS: S to run, but with no results.

here is what terminal shouts out:
> ebichu@seaking:~/.wine/drive_c/CSS$ WINEDEBUG="fixme-all" wine hl2.exe -game cstrike -console -gl
convertConfigAttrib: no WSI_CONFIG_ATTRIB_AUX_BUFFERS
convertConfigAttrib: no WSI_CONFIG_ATTRIB_AUX_BUFFERS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1

and if i use ALSA:
> ebichu@seaking:~/.wine/drive_c/CSS$ WINEDEBUG="fixme-all" wine hl2.exe -game cstrike -console -gl
convertConfigAttrib: no WSI_CONFIG_ATTRIB_AUX_BUFFERS
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
convertConfigAttrib: no WSI_CONFIG_ATTRIB_AUX_BUFFERS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1

other source games don't work too. :(

computer specs are:
core 2 duo 2ghz
2GB ram
and ati radeon 2400 pro with working drivers

---

### Post by ebichu on 2007-10-12
bump

---

### Post by anemptygun on 2007-10-12
thanks for the info

---

### Post by ohhhchiahao on 2007-10-18
hello guys, im new to ubuntu and im lurking thro the forums to see how i can run wine with CS. i've installed wine but when i try to run wine setup in the terminal i get 

wine: could not load L"c:\\windows\\system32\\setup.exe": Module not found

can someone tell me what im doing wrong?

---

### Post by bfbf on 2007-10-20
Try wine doors...

Well im a noob  and got quite far using that anyway :p

I have 1 problem (so far) , which hopefully someone may be able to help with. Steam works, there is font and everything lol. Then the steam friends works but if I start I chat I can see the text I am about to enter but after pressing enter it disapears and if it did get though I can not see replies ethier.

I have googled my problem but no one seems to have got as far as getting the friends to come up (well they were quite old posts)

CS:S is just updating now will see how well(or badly) it plays on my PC :p

Thanks for anyhelp :)

edit - I am on Gusty BTW if that makes any diffence.

---

### Post by Corpus_CT on 2007-10-25
I'm having the same problem as bfbf: everything works fine apart from sending chat messages in Steam Friends.

There's a bug report for this at [WineHQ (click here)]("http://bugs.winehq.org/show_bug.cgi?id=9771"), but it is, as yet, unresolved.

Can anyone help?

I'm on an Intel Core 2 Duo MacBook Pro running Ubuntu Gutsy. I have the same problem on my ex-main PC which also runs Gutsy, although the problem was also present in Feisty.

---

### Post by snkmad on 2007-10-25
Steam installed fine, but i cant run Source games. Ive tried hl2 and hl2dm.
They go as far as loading the map, then they hang.
Heres the errors that appeared on the terminal:
[http://paste.ubuntu-nl.org/42170/](http://paste.ubuntu-nl.org/42170/)

Im running ubuntu 7.10 amd64, and wine-0.9.47

---

### Post by snkmad on 2007-10-26
Wine 0.9.48 is out.
Its supposed to fix all those Source-engine games errors.
We just have to wait for an updated binary on Wine repository.

---

### Post by ctuchik on 2007-10-30
Here's my specs:

Ubuntu 7.10
Wine - 0.9.48
Nvidia 7800GT

Steam runs, the game runs (Team Fortress 2), but whenever I join a game it locks up after i choose a team.  Like I've sat in the "lobby" for a while and i can even watch the film for the level.  But as soon as I choose a team the sound starts skipping and the game locks up.  Help please?

---

### Post by snkmad on 2007-10-31
Well, you should try to disable the steam community in-game.

---

### Post by Bionic Apple on 2007-11-01
You guys are going to probably laugh, but here it goes.  Whenever I try to enter my Steam Folder through cd /home/USER/.wine/drive_c/Program Files/Steam (with USER substituted of course) it gives me this error: bash: cd: /home/USER/.wine/drive_c/Program: No such file or directory.  Is there a certain symbol that represents a space?  The terminal reads "Program Files" as "Program Files" when I use the "ls" command in drive_c.  Sorry for asking such a simple question.

---

### Post by crayment on 2007-11-01
> **Bionic Apple said:**
> You guys are going to probably laugh, but here it goes.  Whenever I try to enter my Steam Folder through cd /home/USER/.wine/drive_c/Program Files/Steam (with USER substituted of course) it gives me this error: bash: cd: /home/USER/.wine/drive_c/Program: No such file or directory.  Is there a certain symbol that represents a space?  The terminal reads "Program Files" as "Program Files" when I use the "ls" command in drive_c.  Sorry for asking such a simple question.

 Program\ Files

from your home directory:

 cd .wine/drive_c/Program\ Files/Steam/

HInt: Use the tab button to complete directory or file names for you.  Type the first few characters then hit tab to complete.

---

### Post by crayment on 2007-11-01
I'm stuck and would really appreciate it if someone could help me figure this out.

my specs:

ubuntu - 7.10
wine-0.9.46

I had no problem installing Steam with some help from other forums. And it seems to run fine until i try to launch half life 2.  I first get a warning about my video driver being out of date which i also got when i installed on my windows machine.  But i find it strange that i haven't seen anything about this from anyone else installing on linux.  

Anyway when i launch it, it kind of shows a zoomed image of my desktop like it changed the resolution which i expect but then it just crashes as if it restarted x.
Like i hit ctrl-alt-bkspc. then i log in again...

I normally run compiz but have tried disabling it and have also tried closing the steam window while the game is loading.

I don't know what else it could be...

---

### Post by Bionic Apple on 2007-11-01
> **crayment said:**
> Program\ Files

from your home directory:

 cd .wine/drive_c/Program\ Files/Steam/

HInt: Use the tab button to complete directory or file names for you.  Type the first few characters then hit tab to complete.

Now, how would I put that into a launcher for my desktop, so I don't have to enter that each time?  Or to be more specific, how would I tell the terminal that there is two different commands within one line?

---

### Post by snkmad on 2007-11-01
> **crayment said:**
> I'm stuck and would really appreciate it if someone could help me figure this out.

my specs:

ubuntu - 7.10
wine-0.9.46

I had no problem installing Steam with some help from other forums. And it seems to run fine until i try to launch half life 2.  I first get a warning about my video driver being out of date which i also got when i installed on my windows machine.  But i find it strange that i haven't seen anything about this from anyone else installing on linux.  

Anyway when i launch it, it kind of shows a zoomed image of my desktop like it changed the resolution which i expect but then it just crashes as if it restarted x.
Like i hit ctrl-alt-bkspc. then i log in again...

I normally run compiz but have tried disabling it and have also tried closing the steam window while the game is loading.

I don't know what else it could be...

First thing you should do is update wine to latest version, 0.9.48.

---

### Post by crayment on 2007-11-01
> **snkmad said:**
> First thing you should do is update wine to latest version, 0.9.48.

Ya i did, I thought my add/remove would install the latest version but i guess not.  Anyways it didn't change a thing.

Still stumped.

---

### Post by crayment on 2007-11-01
> **Bionic Apple said:**
> Now, how would I put that into a launcher for my desktop, so I don't have to enter that each time?  Or to be more specific, how would I tell the terminal that there is two different commands within one line?

I am not sure what you are running but in ubuntu you can easily create a launcher on your desktop or panel by going Application->Wine->ProgramFiles->Steam and then either click and drag where you want, or right click and choose an option.

Maybe something similar for your distro?

The command for the launcher when i do this is:

env WINEPREFIX="/home/USER/.wine" wine "C:\Program Files\Steam\Steam.exe"

---

### Post by Skalman5 on 2007-11-03
/me running U7.10 and latest wine 0.9.48 on my Lg LW75express laptop
Have tried and tried to get CS:S to work under steam for day's without success.

Starting steam with the windebug all command and get the following message in the terminal

```
dir: C:\Program Files\Valve\Steam\bin\ *.mix
dir: C:\Program Files\Valve\Steam\bin\ *.asi
dir: C:\Program Files\Valve\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
```

Then steam launches as usual. But when i click launch (or tries to join a game). The gamewindow first go to fullscreen then it pops back to the desktop (that suddenly has resized to 1680x1050 instead of 1280x1024 that it was before i clicked lauch) with the gamewindow still visible in the upper left quarter of the screen for a couple of seconds before it dissappears.

Wineconfsettings:
Sound
OSS-Emulation-48000-16-Driver Emulation

Graphics
Tried em all and the problem persists

Would be REALLY glad if someone helped me out on this one :)

---

### Post by snkmad on 2007-11-04
> **Skalman5 said:**
> /me running U7.10 and latest wine 0.9.48 on my Lg LW75express laptop
Have tried and tried to get CS:S to work under steam for day's without success.

Starting steam with the windebug all command and get the following message in the terminal

```
dir: C:\Program Files\Valve\Steam\bin\ *.mix
dir: C:\Program Files\Valve\Steam\bin\ *.asi
dir: C:\Program Files\Valve\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
```

Then steam launches as usual. But when i click launch (or tries to join a game). The gamewindow first go to fullscreen then it pops back to the desktop (that suddenly has resized to 1680x1050 instead of 1280x1024 that it was before i clicked lauch) with the gamewindow still visible in the upper left quarter of the screen for a couple of seconds before it dissappears.

Wineconfsettings:
Sound
OSS-Emulation-48000-16-Driver Emulation

Graphics
Tried em all and the problem persists

Would be REALLY glad if someone helped me out on this one :)

Well here are my settings, in case it might help you:
Audio - Also and OSS enabled, HW accel-basic, 44100, 16, driver emulation-disabled.

---

### Post by BongoBob on 2007-11-04
Hello everyone.

Well, I have CS:S working...kind of. I have sound working, it loads up and I get a playable framerate at 1280x800 with everything at low settings. However, I can't play cs_office. Whenever I enter the Terrorist zone with the hostages, the game freezes, and I get this in konsole:

```
wine: Unhandled page fault on read access to 0x00000024 at address 0xe00b423 (thread 0024), starting debugger...
Unhandled exception: page fault on read access to 0x00000024 in 32-bit code (0x0e00b423).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0e00b423 ESP:0034e5e8 EBP:00000002 EFLAGS:00010216(   - 00      -RIAP1)
 EAX:000008c0 EBX:00000000 ECX:1fca6fa8 EDX:07edf0c0
 ESI:0e01ea18 EDI:00000090
Stack dump:
0x0034e5e8:  0e01ea18 1fcaa4a4 0e00b452 1fca008c
0x0034e5f8:  0e01ea18 1fcaa4a4 0e01ea18 1fca0090
0x0034e608:  0e00b7d5 1fca0090 0e01ea18 1fca0090
0x0034e618:  0e01ea3c 000008c0 0e01ea18 0e0098da
0x0034e628:  1fca0001 ffffffff 00000000 00000009
0x0034e638:  0034ff08 0034e67c 003d753b 00000003
Backtrace:
=>1 0x0e00b423 in datacache (+0xb423) (0x00000002)
  2 0x00000000 (0x00000000)
0x0e00b423: movl        0x24(%ebx),%eax
Modules:
Module  Address                 Debug info      Name (219 modules)
PE        3d0000-  400000       Deferred        launcher
PE        400000-  41c000       Deferred        hl2
PE       1160000- 1196000       Deferred        tier0
PE       11a0000- 11be000       Deferred        vstdlib
PE       dad0000- db24000       Deferred        filesystem_steam
PE       db30000- db44000       Deferred        inputsystem
PE       ddb0000- deae000       Deferred        datamodel
PE       dfc0000- dffd000       Deferred        dmserializers
PE       e000000- e025000       Export          datacache
PE       e140000- e1f4000       Deferred        materialsystem
PE       e200000- e216000       Deferred        valve_avi
PE       e220000- e2f0000       Deferred        vguimatsurface
PE       e2f0000- e365000       Deferred        vgui2
PE       e370000- e384000       Deferred        steam_api
PE       e5b0000- e5d9000       Deferred        stdshader_dbg
PE       e5e0000- e615000       Deferred        stdshader_dx6
PE       e620000- e648000       Deferred        stdshader_dx7
PE       e650000- e693000       Deferred        stdshader_dx8
PE       e6a0000- e6af000       Deferred        unicode
PE       edb0000- ede6000       Deferred        soundemittersystem
PE       edf0000- ee0b000       Deferred        scenefilecache
PE       ee10000- efcd000       Deferred        steamclient
PE       efd0000- f00f000       Deferred        tier0_s
PE       f010000- f084000       Deferred        vstdlib_s
PE       f1e0000- f47d000       Deferred        p2pcore
PE       f480000- f5d8000       Deferred        p2pvoice
PE       f6f0000- f8d3000       Deferred        gameui
PE      10000000-10031000       Deferred        gameoverlayrenderer
PE      1d350000-1d360000       Deferred        vaudio_miles
PE      1d360000-1d3c4000       Deferred        mss32
PE      1def0000-1dfbb000       Deferred        serverbrowser
PE      1e0d0000-1e0f7000       Deferred        vaudio_speex
PE      1ffe0000-1ffe6000       Deferred        xpcom
PE      1fff0000-1fff7000       Deferred        plc4
PE      20000000-205ee000       Deferred        engine
PE      20920000-20989000       Deferred        xpcom_core
PE      20990000-209b7000       Deferred        nspr4
PE      209c0000-209c6000       Deferred        plds4
PE      209d0000-209df000       Deferred        jsd3250
PE      209e0000-209f4000       Deferred        xpcom_compat
PE      20a00000-20a06000       Deferred        mozctlx
PE      21050000-210c1000       Deferred        js3250
PE      210d0000-210d6000       Deferred        xpistub
PE      210e0000-210f1000       Deferred        mozz
PE      21100000-211ad000       Deferred        mss32_s
PE      21f80000-21fb5000       Deferred        xpc3250
PE      21fc0000-21fff000       Deferred        softokn3
PE      22000000-22642000       Deferred        server
PE      22fb0000-2300b000       Deferred        nss3
PE      23010000-2302a000       Deferred        smime3
PE      23030000-23043000       Deferred        jsj3250
PE      23050000-23066000       Deferred        gkgfx
PE      23070000-230ae000       Deferred        nssckbi
PE      230b0000-230d0000       Deferred        ssl3
PE      230d0000-23101000       Deferred        freebl3
PE      23110000-2318d000       Deferred        necko
PE      23190000-2319c000       Deferred        xppref32
PE      231a0000-231ce000       Deferred        i18n
PE      231d0000-231ef000       Deferred        embedcomponents
PE      231f0000-231ff000       Deferred        caps
PE      23200000-2320c000       Deferred        typeaheadfind
PE      23210000-234a9000       Deferred        gklayout
PE      234b0000-234d7000       Deferred        imglib2
PE      234e0000-234fb000       Deferred        rdf
PE      23500000-23538000       Deferred        appcomps
PE      23540000-23550000       Deferred        appshell
PE      23550000-2355f000       Deferred        profile
PE      23560000-23567000       Deferred        xpcom_compat_c
PE      23570000-2357e000       Deferred        webbrwsr
PE      23580000-235a5000       Deferred        gkwidget
PE      235b0000-235d4000       Deferred        gkgfxwin
PE      235e0000-2360c000       Deferred        docshell
PE      23610000-23618000       Deferred        pipboot
PE      23620000-2362c000       Deferred        oji
PE      23630000-236ee000       Deferred        uconv
PE      236f0000-23700000       Deferred        chrome
PE      23700000-23739000       Deferred        gkparser
PE      23740000-2374d000       Deferred        jar50
PE      23860000-23867000       Deferred        txmgr
PE      24000000-24476000       Deferred        client
PE      26000000-26138000       Deferred        vphysics
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      2a000000-2a0a8000       Deferred        shaderapidx9
PE      2c000000-2c3e3000       Deferred        studiorender
PE      30000000-30320000       Deferred        steam
PE      60000000-60021000       Deferred        cserhelper
PE      628c0000-628d9000       Deferred        parsifal
ELF     7724e000-77298000       Deferred        dbghelp<elf>
  \-PE  77260000-77298000       \               dbghelp
ELF     7809e000-780ef000       Deferred        libgcrypt.so.11
ELF     780ef000-7811d000       Deferred        libcrypt.so.1
ELF     7811d000-7818d000       Deferred        libgnutls.so.13
ELF     7818d000-78215000       Deferred        libkrb5.so.3
ELF     78215000-782b6000       Deferred        comdlg32<elf>
  \-PE  78220000-782b6000       \               comdlg32
ELF     784d8000-78540000       Deferred        msvcrt<elf>
  \-PE  784f0000-78540000       \               msvcrt
ELF     79e14000-79e1f000       Deferred        libgcc_s.so.1
ELF     7b041000-7b066000       Deferred        libk5crypto.so.3
ELF     7b197000-7b1e0000       Deferred        dsound<elf>
  \-PE  7b1a0000-7b1e0000       \               dsound
ELF     7b1e9000-7b1f9000       Deferred        libtasn1.so.3
ELF     7b5e1000-7b61b000       Deferred        shdocvw<elf>
  \-PE  7b5f0000-7b61b000       \               shdocvw
ELF     7b71c000-7b745000       Deferred        libgssapi_krb5.so.2
ELF     7b745000-7b77a000       Deferred        libcups.so.2
ELF     7b77a000-7b800000       Deferred        mshtml<elf>
  \-PE  7b790000-7b800000       \               mshtml
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7b92d000-7b935000       Deferred        libkrb5support.so.0
ELF     7b94d000-7b989000       Deferred        urlmon<elf>
  \-PE  7b960000-7b989000       \               urlmon
ELF     7ba8b000-7ba8f000       Deferred        libgpg-error.so.0
ELF     7ba8f000-7bac4000       Deferred        winspool<elf>
  \-PE  7baa0000-7bac4000       \               winspool
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bca4000-7bca6000       Deferred        libkeyutils.so.1
ELF     7bca6000-7bca9000       Deferred        libcom_err.so.2
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf21000-7bf27000       Deferred        libnss_dns.so.2
ELF     7c327000-7c32a000       Deferred        libnss_mdns4_minimal.so.2
ELF     7cb24000-7cb38000       Deferred        winejoystick<elf>
  \-PE  7cb30000-7cb38000       \               winejoystick
ELF     7cd5a000-7ce3b000       Deferred        wined3d<elf>
  \-PE  7cd70000-7ce3b000       \               wined3d
ELF     7ce3b000-7ce6a000       Deferred        d3d9<elf>
  \-PE  7ce40000-7ce6a000       \               d3d9
ELF     7ce6a000-7ce8b000       Deferred        mpr<elf>
  \-PE  7ce70000-7ce8b000       \               mpr
ELF     7ce8b000-7ced7000       Deferred        wininet<elf>
  \-PE  7cea0000-7ced7000       \               wininet
ELF     7ced7000-7cf76000       Deferred        oleaut32<elf>
  \-PE  7cef0000-7cf76000       \               oleaut32
ELF     7cf76000-7cf9d000       Deferred        msvfw32<elf>
  \-PE  7cf80000-7cf9d000       \               msvfw32
ELF     7cf9d000-7cfd7000       Deferred        avifil32<elf>
  \-PE  7cfa0000-7cfd7000       \               avifil32
ELF     7cfd7000-7cfec000       Deferred        midimap<elf>
  \-PE  7cfe0000-7cfec000       \               midimap
ELF     7cfec000-7d013000       Deferred        msacm32<elf>
  \-PE  7cff0000-7d013000       \               msacm32
ELF     7d013000-7d0d9000       Deferred        libasound.so.2
ELF     7d0d9000-7d0f1000       Deferred        msacm32<elf>
  \-PE  7d0e0000-7d0f1000       \               msacm32
ELF     7d0f1000-7d127000       Deferred        winealsa<elf>
  \-PE  7d100000-7d127000       \               winealsa
ELF     7d127000-7d1b5000       Deferred        winmm<elf>
  \-PE  7d130000-7d1b5000       \               winmm
ELF     7d343000-7d375000       Deferred        uxtheme<elf>
  \-PE  7d350000-7d375000       \               uxtheme
ELF     7d375000-7d389000       Deferred        mswsock<elf>
  \-PE  7d380000-7d389000       \               mswsock
ELF     7d389000-7d39d000       Deferred        lz32<elf>
  \-PE  7d390000-7d39d000       \               lz32
ELF     7d39d000-7d3b7000       Deferred        version<elf>
  \-PE  7d3a0000-7d3b7000       \               version
ELF     7d3b7000-7d476000       Deferred        comctl32<elf>
  \-PE  7d3c0000-7d476000       \               comctl32
ELF     7d476000-7d4ce000       Deferred        shlwapi<elf>
  \-PE  7d480000-7d4ce000       \               shlwapi
ELF     7d4ce000-7d5d1000       Deferred        shell32<elf>
  \-PE  7d4e0000-7d5d1000       \               shell32
ELF     7d5d1000-7d62a000       Deferred        rpcrt4<elf>
  \-PE  7d5e0000-7d62a000       \               rpcrt4
ELF     7d62a000-7d6cb000       Deferred        ole32<elf>
  \-PE  7d640000-7d6cb000       \               ole32
ELF     7d6cb000-7d6e9000       Deferred        iphlpapi<elf>
  \-PE  7d6d0000-7d6e9000       \               iphlpapi
ELF     7d747000-7d75c000       Deferred        psapi<elf>
  \-PE  7d750000-7d75c000       \               psapi
ELF     7d9a2000-7d9cf000       Deferred        ws2_32<elf>
  \-PE  7d9b0000-7d9cf000       \               ws2_32
ELF     7d9cf000-7d9e9000       Deferred        wsock32<elf>
  \-PE  7d9e0000-7d9e9000       \               wsock32
ELF     7d9e9000-7d9f2000       Deferred        libxcursor.so.1
ELF     7d9f2000-7da0f000       Deferred        imm32<elf>
  \-PE  7da00000-7da0f000       \               imm32
ELF     7da0f000-7da14000       Deferred        libxfixes.so.3
ELF     7da14000-7da17000       Deferred        libxinerama.so.1
ELF     7da1a000-7da2d000       Deferred        libresolv.so.2
ELF     7da3a000-7da5f000       Deferred        netapi32<elf>
  \-PE  7da40000-7da5f000       \               netapi32
ELF     7da5f000-7da86000       Deferred        secur32<elf>
  \-PE  7da70000-7da86000       \               secur32
ELF     7deb2000-7e84a000       Deferred        libglcore.so.1
ELF     7e84a000-7e8e0000       Deferred        libgl.so.1
ELF     7e8e0000-7e9d1000       Deferred        libx11.so.6
ELF     7e9d1000-7e9df000       Deferred        libxext.so.6
ELF     7e9e0000-7e9e3000       Deferred        libxcomposite.so.1
ELF     7e9e3000-7e9e9000       Deferred        libxrandr.so.2
ELF     7e9e9000-7e9f1000       Deferred        libxrender.so.1
ELF     7e9f7000-7ea87000       Deferred        winex11<elf>
  \-PE  7ea10000-7ea87000       \               winex11
ELF     7eb90000-7ebb0000       Deferred        libexpat.so.1
ELF     7ebb0000-7ebdb000       Deferred        libfontconfig.so.1
ELF     7ebdb000-7ebf0000       Deferred        libz.so.1
ELF     7ebf0000-7ec60000       Deferred        libfreetype.so.6
ELF     7ec60000-7eca9000       Deferred        advapi32<elf>
  \-PE  7ec70000-7eca9000       \               advapi32
ELF     7eca9000-7ed44000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed44000       \               gdi32
ELF     7ed44000-7ee83000       Deferred        user32<elf>
  \-PE  7ed60000-7ee83000       \               user32
ELF     7ee83000-7ee8c000       Deferred        libnss_compat.so.2
ELF     7ee8f000-7ee94000       Deferred        libxdmcp.so.6
ELF     7efc3000-7efe8000       Deferred        libm.so.6
ELF     7efe8000-7f000000       Deferred        libnsl.so.1
ELF     f7c82000-f7c84000       Deferred        libnvidia-tls.so.1
ELF     f7c84000-f7c8f000       Deferred        libnss_files.so.2
ELF     f7c90000-f7c94000       Deferred        libdl.so.2
ELF     f7c94000-f7dde000       Deferred        libc.so.6
ELF     f7ddf000-f7df7000       Deferred        libpthread.so.0
ELF     f7df7000-f7dfa000       Deferred        libxau.so.6
ELF     f7dfb000-f7e05000       Deferred        libnss_nis.so.2
ELF     f7e0f000-f7f23000       Deferred        libwine.so.1
ELF     f7f25000-f7f43000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000045 (D) C:\Program Files\Steam\steamapps\gow_gameandwatch\counter-strike source\hl2.exe
        0000005b    0
        0000005a    0
        00000059    0
        00000058    0
        00000057    0
        00000056    0
        00000055    0
        00000052   15
        00000051    0
        00000050   15
        0000004f    0
        0000004e    0
        0000004d    0
        0000004a    0
        00000048    0
        00000030   15
        0000002a    2
        00000029    0
        00000046    0
        00000021    0
        0000001f    2
        00000024    0 <==
0000000a
        0000000b    0
00000008
        00000049    1
        00000047    1
        00000033    0
        0000002b    0
        00000044    0
        00000043    0
        00000042    1
        00000041    0
        00000040    1
        0000003f    0
        0000003e    1
        0000003d    0
        0000003c    1
        0000003b    0
        0000003a    1
        00000039    0
        00000038    1
        00000037    0
        00000036    1
        00000035    0
        00000034    1
        0000002f    0
        0000002e    0
        0000002d    0
        0000002c    0
        00000028    0
        00000027    1
        00000026    0
        00000025    0
        00000023    0
        00000022    1
        00000020    0
        0000001e   15
        0000001c    0
        0000001b   15
        0000001a   15
        00000019    0
        00000018    0
        00000017    0
        00000016    0
        00000015    0
        00000014    1
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        0000000c    0
        00000009    0
Shutting down. . .

```

I'm running Kubuntu 7.10 64 bit through wine 0.9.48, with -dxlevel 80 and Alsa for sound, using a custom 2.6.23.1 kernel and nVidia drivers done through envy.

Thanks in advance for any help :)

---

### Post by blitze on 2007-11-04
I can't seem to get HL2 or Episode 1 running due to a 
"filesystem_steam.dll"  error.

Running Gutsy x64
WINE 0.9.48 x64

Steam loads and runs well and I also not that there is a mouse pointer capture issue with red Orchestra still.  Oneday I hope to have that resolved under WINE.

---

### Post by Tuckwoor on 2007-11-05
I seem to have the same problem as Skalman5 and Crayment where I have steam installed and it runs, have css downloaded (and launch options set to: -dxlevel 80 -gl -console)  and when I launch it it just resizes, shows the loading screen and then crashes back to desktop with the new sizing.

I tried running the winedebug from a terminal but get:

wine: cannot find 'c:/Program Files/Valve/Steam/steam.exe'

I have set audio to OSS, hardware acc-basic, sample rate 22050, 16 bit, driver emulation off.

glxgears runs with decent frame rates (its a dirty ATI 9550).

Wine is 0.9.46.

---

### Post by crayment on 2007-11-05
> **Tuckwoor said:**
> I seem to have the same problem as Skalman5 and Crayment where I have steam installed and it runs, have css downloaded (and launch options set to: -dxlevel 80 -gl -console)  and when I launch it it just resizes, shows the loading screen and then crashes back to desktop with the new sizing.

I tried running the winedebug from a terminal but get:

wine: cannot find 'c:/Program Files/Valve/Steam/steam.exe'

I have set audio to OSS, hardware acc-basic, sample rate 22050, 16 bit, driver emulation off.

glxgears runs with decent frame rates (its a dirty ATI 9550).

Wine is 0.9.46.

Do you get the warning about your video driver being out of date?
I feel like i'm the only one...

I got the stederr output that wine produces before it crashes back to my login screen.  Hopefully it makes sense to someone.

This the contents of the file err.txt after this command.

env WINEPREFIX="/home/cody/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 220 2>err.txt


[PHP]err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,103,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,103,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,177,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,224,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,197,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,83,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,83,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
fixme:shdocvw:ViewObject_SetAdvise (0x10370310)->(1 00000002 0x147c8c0)
fixme:shdocvw:PersistStreamInit_InitNew (0x10370310)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10370310)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10370310)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1ec038)->(1 00000002 0x147c928)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ec038)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ec038)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ec038)->(ffffffff)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x33c5cc,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,0,2): stub!
err:systray:delete_icon invalid tray icon ID specified: 1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x1de018)->(1 00000002 0x147db90)
fixme:shdocvw:PersistStreamInit_InitNew (0x1de018)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1de018)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1de018)->(ffffffff)
fixme:process:IsWow64Process (0xffffffff 0x3d6e88) stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,236,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,18,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,18,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,236,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,88,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,166,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,166,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,88,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,62,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,192,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,30,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,224,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,217,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,159,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,102,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,49,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1de018)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1de018)
fixme:shdocvw:OleObject_Close (0x1de018)->(1)
fixme:win:EnumDisplayDevicesW ((null),0,0x34e174,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
X connection to :2.0 broken (explicit kill or server shutdown).
[/PHP]

---

### Post by Tuckwoor on 2007-11-06
I don't get a message about it being out of date but I do get one saying unsupported video card and then gives my driver details as windows version: windows xp, description direct3d hal, version 6.14.0.0. Not sure why it comes up with direct3d thing when I have the switch set to -gl.

My crash doesn't take me back to login screen but back to desktop but now resized to 640x480 or whatever css was trying to run in before it gave up.

---

### Post by Rafadagaffer on 2007-11-06
Hi

I'm getting the same problem as many people trying to get steam games working. Im using Feisty, the lastest version of wine, the ATI restricted driver and the launch options are -novid -height 1280 -width 1024 -console -dxlevel 81.

When I try to launch any steam app, it loads up fine, shows the menu screen but then crashes back to the desktop at whatever resolution the game was running at.

I can post the output of the log file for wine if needed. Just need to get hl2dm working so I can get rid of windows :)

Any help would be great

---

### Post by aoanla on 2007-11-06
> **Tuckwoor said:**
> I don't get a message about it being out of date but I do get one saying unsupported video card and then gives my driver details as windows version: windows xp, description direct3d hal, version 6.14.0.0. Not sure why it comes up with direct3d thing when I have the switch set to -gl.

That's because the Source engine *doesn't have* an OpenGL rendering path. It's only DirectX (except on the PS3, obviously). The -gl option to Steam only actually does anything on non-Source engine games which have an OpenGL renderer - for example, the original Half-life.

---

### Post by Tuckwoor on 2007-11-08
k, was just for information really. Running css from console with:

env WINEPREFIX="/home/tuckwoor/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 240

gives:

```
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:shdocvw:ViewObject_SetAdvise (0x13d83f70)->(1 00000002 0x13fcd38)
fixme:shdocvw:PersistStreamInit_InitNew (0x13d83f70)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x13d83f70)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x13d83f70)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x13d84300)->(1 00000002 0x13fcda0)
fixme:shdocvw:PersistStreamInit_InitNew (0x13d84300)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x13d84300)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x13d84300)->(ffffffff)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x34c5cc,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x20096,0x00000000,0,2): stub!
err:systray:delete_icon invalid tray icon ID specified: 1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x13edb7f8)->(1 00000002 0x13fe9f8)
fixme:shdocvw:PersistStreamInit_InitNew (0x13edb7f8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x13edb7f8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x13edb7f8)->(ffffffff)
fixme:process:IsWow64Process (0xffffffff 0x3e6e88) stub!
fixme:win:SetLayeredWindowAttributes (0x20096,0x00000000,252,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,2,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,2,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20096,0x00000000,252,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20096,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,183,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,62,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,19,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x13edb7f8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x13edb7f8)
fixme:shdocvw:OleObject_Close (0x13edb7f8)->(1)
fixme:win:EnumDisplayDevicesW ((null),0,0x34e1e4,0x00000000), stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x134d38) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x134d38) Event query: Unimplemented, but pretending to be supported
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:avifile:AVIFileExit (): stub!
```

With same result of crashing back to desktop which has been resized.

---

### Post by Tuckwoor on 2007-11-10
As another bit of info, day of defeat 1.6 works when given -gl switch so think css problem is directx related. Any ideas?

---

### Post by Skalman5 on 2007-11-12
Setting sound to ALSA and changing graphics driver from mesa3d to ATI (because i&#314;l have an ATI graphics card). Solved the problem i described in my previous post. But then i got an errormessage "Failed to read from vertex buffer" (or something like that)

That problem solved when wine updated itself by the automatic update.

**Now i can play the game but there are some annoyances:**
1. I can't play the game with -dxlevel higher than 70 (higher=vertex-bug)
2. Maximum resolution is 800x600 (any higher resolution will make the "Vertex"-crash described above.
3. Any settings i do in CS:S reverts back to "factory-default" everytime i quit playing. (setting back the videosettings to 640x480 etc)
4. And the game seems very slow. The ping is low but it lags sometimes and it feels like im several hundreds "behind" the other players playing.

So.. Anyone got any ideas? :)

---

### Post by Tuckwoor on 2007-11-12
Different problem to me then I suspect as I had the 8.42.3 ati driver from the start and still crash back from the "loading" screen to the desktop in game resolution.

What version of the ati driver are you running now Skalman? Is it the restricted driver?

---

### Post by Skalman5 on 2007-11-13
Yes im running the restricted driver (i think) latest version.
You can easily check your configuration by typing some command (which i´ve forgotten) in the terminal. If it says mesa3d its wrong it should say ATI.

There´s a very good walkthrough somewhere outthere that i followed.

What i´ve learned at that walkthrough was that these restricted ATI drivers don´t install themself when you install ubuntu, which i tought was the case. They need to be installed manually and you have to type some various commands in the terminal (aka not pick´n click). When i´ve done that my graphics and desktop reverted back to sh*t-mode but got normal again when i restarted the computer and clicked yes to some warnings. Tadaaa ATI-driver installed :)

---

### Post by Tuckwoor on 2007-11-13
Sorry, you misunderstand. I thought I had same problem as you but your's was the mesa problem. I've had the restricted drivers on all along but still no joy. Was just wondering if you had the 8.42.3 ones on now you have got something up and running (albeit with the lag problems etc you listed) or whether they were earlier ones.

---

### Post by KillerJoe on 2007-11-13
> **Skalman5 said:**
> 
1. I can't play the game with -dxlevel higher than 70 (higher=vertex-bug)
2. Maximum resolution is 800x600 (any higher resolution will make the "Vertex"-crash described above.
3. Any settings i do in CS:S reverts back to "factory-default" everytime i quit playing. (setting back the videosettings to 640x480 etc)
4. And the game seems very slow. The ping is low but it lags sometimes and it feels like im several hundreds "behind" the other players playing.
1. Might be your video card? (does it support higher dx levels?)
2. ?
3. Add something like -w 800 to you startup options... (or even try adding it to your autoexec.cfg - if you don't have any - create one)
4. Be sure to play only on near by servers - also check your rate settings..

Recommended settings (for good internet and on nearby servers):
```
rate 25000
cl_cmdrate 100
cl_updaterate 100
cl_interp 0.01
```

*(note - these rate settings are as memorized - may be faulty)*

---

### Post by ilh on 2007-11-26
Anyone having problems getting sound in Source games? Tried CSS and DoD:S which both run great (better than they do in Windows surprisingly) but I get no sound. I get sound in Infantry and CoD2 so it's not my soundcard or what have you.

Any ideas?

Ta

---

### Post by boast on 2007-11-26
> **ilh said:**
> Anyone having problems getting sound in Source games? Tried CSS and DoD:S which both run great (better than they do in Windows surprisingly) but I get no sound. I get sound in Infantry and CoD2 so it's not my soundcard or what have you.

Any ideas?

Ta

If i run source with winecfg set to use OSS, i get no sound. I have to use alsa with hardware emulation

---

### Post by ilh on 2007-11-26
Ok thanks. Just tried it and i'm getting the menu music. Will try in game after dinner. Read that alsa lags a lot, does it lag for you?

---

### Post by AJLChase on 2007-12-09
So, I just got WoW up and running really well...but I can't get steam to install. When I download the installer to my desktop it is saved as 
"SteamInstall.msi" and no matter if I right click it or tell wine to run it..nothing at all happens. Any suggestions?

---

### Post by nawitus on 2007-12-09
> **AJLChase said:**
> So, I just got WoW up and running really well...but I can't get steam to install. When I download the installer to my desktop it is saved as 
"SteamInstall.msi" and no matter if I right click it or tell wine to run it..nothing at all happens. Any suggestions?

You should always use the Wine Application Database first, since that usually tells you how to install games/software.

[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

You can try "wine msiexec /i SteamInstall.msi" or "wine start SteamInstall.msi"

---

### Post by mikesrex on 2007-12-29
I looked and can't find someone with the same problem as me

running nvidia drivers (on an 8600GTS), wine 0.9.51, 

I've got steam up and running.  I downloaded CSS using the download option on steam.  Now when I launch CSS everything just closes out without any sort of message indicating CSS is trying to launch.

Here are the errors in the console screen since I told steam to run in console with the errorfree thing.

> 
err: ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err: ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl


(space added between err: and ole to keep it from doing a smily FWIW)

---

### Post by hasmind on 2008-02-12
Okay, I read the first 18 pages of this thread (!) hoping that someone might have already have an answer to this:

problem 1)   I have steam starting, but then my cursor points about 1/2 a centimeter above where steam thinks it's pointing. However, I can live with that.

problem 2) However, what I can't live with is Counter Strike crashing for no apparent reason, just after the loading screen. I get a lot of jibberish like 

err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered

but I really don't know what that is.

thanks

edit- oops, I read the first 18 pages, but not the most recent post! I guess it has something to do with the most recent version of wine. I have version 0.9.46 by the way.

---

### Post by d_skillz on 2008-10-29
> **hasmind said:**
> Okay, I read the first 18 pages of this thread (!) hoping that someone might have already have an answer to this:

problem 1)   I have steam starting, but then my cursor points about 1/2 a centimeter above where steam thinks it's pointing. However, I can live with that.

problem 2) However, what I can't live with is Counter Strike crashing for no apparent reason, just after the loading screen. I get a lot of jibberish like 

err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered

but I really don't know what that is.

thanks

edit- oops, I read the first 18 pages, but not the most recent post! I guess it has something to do with the most recent version of wine. I have version 0.9.46 by the way.

Same here, any help would be greatly appreciated.

---

### Post by YokoZar on 2008-10-29
Please start a new thread instead of bumping an extremely old one.  Edgy's been unsupported for over a year at this point.

---

