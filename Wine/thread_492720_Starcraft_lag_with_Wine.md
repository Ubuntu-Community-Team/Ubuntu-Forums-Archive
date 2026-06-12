---
title: "Starcraft lag with Wine"
date: 2007-07-05
forum: Wine
---

### Post by Mike7171 on 2007-07-05
Starcraft installed fine using Wine, and I have it running windowed, but it lags to the point that it is almost unplayable. Anyone know how to fix this? Thanks.

Mike7171

---

### Post by dfreer on 2007-07-05
My basic question: Do you have your video card drivers correctly installed?
```
glxinfo | grep rendering
```

---

### Post by Mike7171 on 2007-07-05
Output to that:

```
mike@mike-desktop:~$ glxinfo | grep rendering
direct rendering: Yes
```

I guess that means yes.

---

### Post by hikaricore on 2007-07-05
Aye it does, why type of video card do you have.

Also post any error messages you get when running Starcraft with WINE from a terminal.

---

### Post by Mike7171 on 2007-07-05
I have an Nvidia card. Not sure what type. Is there a way to check?

Also, how do I run it through the terminal? I will post the errors if any.

---

### Post by dfreer on 2007-07-05
To run through terminal (this depends on how you install starcraft, but in general it should work):
```
wine ~/.wine/drive_c/Program\ Files/Starcraft/starcraft.exe
```
You can do also do this command if the above doesn't work, to help find the correct filenames:
```
nautilus ~/.wine/
```

---

### Post by hikaricore on 2007-07-05
Assuming the game is located at: *~/.wine/drive_c/Program\ Files/Starcraft*

Basically you would use:

```
cd ~/.wine/drive_c/Program\ Files/Starcraft
wine starcraft.exe
```

The actual location may vary depending on where you installed it.  I'm not super familiar with SC.  >.<

As far as the video card you're going to want to find out what it is.

```
glxinfo | grep string
```

Should throw back someting like this:

> server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: **GeForce 6200/PCI/SSE2**
OpenGL version string: 2.1.1 NVIDIA 100.14.09


Did you install the driver through the the Restriced Drivers manager or the binary installer package?

If not you may be using the default "nv" driver:

```
cat /etc/X11/xorg.conf | grep Driver
```

>     Driver         "kbd"
    Driver         "mouse"
    Driver         [B]"nvidia"
[/B]

---

### Post by Mike7171 on 2007-07-05
Ran it through terminal. Got this up to the point of the main menu as I moved my mouse around a little:

```
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x17e978) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x17e6f8)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:wave:DSD_CreateSecondaryBuffer (0x1cf1d8,0x33fc9c,c0,0,0x1f3eac,0x1d2b4c,0x1f3e88): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x1cf1d8,0x33fc64,80,0,0x2146dc,0x1f3d2c,0x2146b8): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x1cf1d8,0x33fb98,c0,0,0x1662864,0x1662934,0x1662840): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x1cf1d8,0x7cdf68ac,c0,0,0x2183bc,0x21848c,0x218398): stub
err:dsound:DSOUND_MixInBuffer length not a multiple of block size, len = 2578, block size = 4
err:dsound:DSOUND_MixInBuffer length not a multiple of block size, len = 2578, block size = 4
err:dsound:DSOUND_MixInBuffer length not a multiple of block size, len = 2578, block size = 4
err:dsound:DSOUND_MixInBuffer length not a multiple of block size, len = 2578, block size = 4
```

Kept going like that for a while.

---

### Post by Mike7171 on 2007-07-05
(For video card) Did the first step you gave me. My card is "GeForce FX 5600/AGP/3DNOW!"

---

### Post by Mike7171 on 2007-07-05
Figured out how to switch between windowed and full screen, but it does not help.

---

### Post by dfreer on 2007-07-05
What kind of fps do you get with this command (just let it run for a little bit then hit <Ctrl>+<c> to kill it):
```
glxgears
```

EDIT: I know glxgears isn't a good test of performance, but is there any better tests?

---

### Post by hikaricore on 2007-07-05
*dfreer:*  You're braver than I.  I'm still waiting for him to tell us what video driver he's using and how he installed it. lol ^_^

---

### Post by Mike7171 on 2007-07-05
Output to that gears thing:
```

12445 frames in 5.0 seconds = 2488.956 FPS
12002 frames in 5.0 seconds = 2400.242 FPS
12766 frames in 5.0 seconds = 2553.116 FPS
12313 frames in 5.0 seconds = 2462.562 FPS
12499 frames in 5.0 seconds = 2499.793 FPS
```

And I said the video card already. Was the last post on the previous page. My card is "GeForce FX 5600/AGP/3DNOW!"

---

### Post by hikaricore on 2007-07-05
I had asked about the driver..  not the card.  ^_^

---

### Post by Mike7171 on 2007-07-05
Oh, sorry lol.
> 
Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "nvidia"

---

### Post by hikaricore on 2007-07-05
Np, so it is the nvidia driver.  Hmm... that was my one shining idea that you may have been using the wrong driver.  >.<
But you are NOT using the wrong one.

You don't by any chance happen to be running a 3d accelerated desktop such as beryl/compiz/compiz-fusion while you're trying to run this game are you?

---

### Post by Mike7171 on 2007-07-05
I've tried to enable it before but it doesn't work very well (not a downloaded one like Beryl, just the regular desktop effects), so I never have them enabled any more, so no, I do not run them while SC is running.

---

### Post by Mike7171 on 2007-07-05
I have it running in a virtual windowed desktop thing which is 640 x 480. Could that be a problem? (it lags about the same amount in full screen though anyway. But maybe there's an optimal size)

---

### Post by zivagolee on 2007-07-05
Try running starcraft.exe with a "nice -n 20":

nice -n 20 starcraft.exe

---

### Post by dfreer on 2007-07-05
SC only runs at 640x480, regardless of what window mode you set it at. So I don't think that will make a difference. Another good question hikaricore had was how you installed the driver, did you use the "Restricted Driver Manager" feature of feisty or some other method?

@hikaricore hi! oh, I was thinking if it displayed the nvidia string in glxinfo it meant it was using the nvidia driver already lol. I'm moving too fast.

---

### Post by Mike7171 on 2007-07-05
My video drive was installed back when I originally had Windows. So, everything is normal I guess. I also disabled pixel shading in winecfg like one guy suggested, and it worked a little. But it still lags alot when I build things in the game, or if anything happens really.

---

### Post by hikaricore on 2007-07-05
(video) **DRIVERS** are a software control for a piece of hardware, in this case your video card.

You may have installed the video card and the video drivers in ***dows, but this has nothing to do with Linux.

How did you install your video drivers _IN LINUX_?

^_^

---

### Post by Mike7171 on 2007-07-05
Not sure. I followed the instructions to install Ubuntu in my thread "Confues about grub" (spelt confused wrong). Maybe it was involved in those instructions.

---

### Post by dfreer on 2007-07-05
Nope. Nothing in all 5 pages of that thread covered installing the video driver. For kicks and giggles, could you go to System > Administration > Restricted Drivers Manager and see if it lists your video card. if it does, does it say it is currently installed?

Also, I get the feeling we should take a look at your /etc/X11/xorg.conf file, if you would post that here for us?

---

### Post by Mike7171 on 2007-07-05
The driver is NVIDIA Accelerated graphics driver. It is enabled, and "in use".

For the other thing, it said "permission denied" for some reason.

---

### Post by dfreer on 2007-07-05
in terminal:
```
sudo cat /etc/X11/xorg.conf
```

---

### Post by Mike7171 on 2007-07-05
Output to that:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV31 [GeForce FX 5600]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-51
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV31 [GeForce FX 5600]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by mancxvi on 2007-07-05
I had to do some digging when I tried to get it working, but found this info in a post in the WineHQ thread. The issue stems from the drawing method that Starcraft uses.

In regedit, add the following keys:

HKEY_CURRENT_USER/Software/Wine/AppDefaults/starcraft.exe/Direct3D/DirectDrawRenderer = opengl
HKEY_CURRENT_USER/Software/Wine/AppDefaults/starcraft.exe/Direct3D/RenderTargetLockMode = readtex

It should run much faster. I haven't been able to run it fullscreen with this method, but that could just be me.

Further reading: [http://appdb.winehq.org/commentview.php?iAppId=72&iVersionId=51&iThreadId=14018](http://appdb.winehq.org/commentview.php?iAppId=72&iVersionId=51&iThreadId=14018)

---

### Post by Mike7171 on 2007-07-05
Thanks! I'll give that a shot. How do I get to regedit though?

---

### Post by mancxvi on 2007-07-05
Just run regedit from a terminal.

---

### Post by Mike7171 on 2007-07-05
Is anything supposed to show up when you type "regedit"?. Nothing happens. Then I entered those 2 lines, and nothing happened again. Didn't say there was an error or anything, it just didn't say anything at all.

---

### Post by mancxvi on 2007-07-05
It should open Wine's registry editor. Here's a screencap for you.

---

### Post by Mike7171 on 2007-07-05
Nope, mine doesn't open that. Maybe because I have Steam open and running through Terminal.

---

### Post by mancxvi on 2007-07-05
Did you try to do it in the terminal you ran Steam in or did you open a fresh one?

---

### Post by Mike7171 on 2007-07-05
I opened a fresh one.

---

### Post by mancxvi on 2007-07-05
What was the output in the terminal?

edit: Try running 'wine regedit'

---

### Post by Mike7171 on 2007-07-05
There was no output. Nothing happened at all. I tried "wine regedit" too. All it does is remove the thing that's usually there ("mike@mike-desktop:~$").

---

### Post by mancxvi on 2007-07-05
I tried replicating the issue by starting Steam and attempting to run regedit, but it still worked for me. Can you run winecfg, at least?

---

### Post by Mike7171 on 2007-07-05
Yep.
I closed Steam, and it worked.

---

### Post by Mike7171 on 2007-07-05
So how do I enter them?

---

### Post by mancxvi on 2007-07-05
Refer to the screenshot.

Under AppDefaults, add Key starcraft.exe if it isn't there already. (Right-click>New>Key)
Do the same with Direct3D
Under Direct3D, add a string value called DirectDrawRenderer and set its value to opengl
Under Direct3D, add a string value called RenderTargetLockMode and set its value to readtex

That should do it.

---

### Post by Mike7171 on 2007-07-05
Alright, did all that. I have an extra one though. It's PixelShaderMode and its value is Disabled. Probable because in Winecfg I disabled pixel shading because someone told me it would make it run more smoothly. Is this ok?

---

### Post by mancxvi on 2007-07-05
It should be all right.

---

### Post by Mike7171 on 2007-07-05
Now SC doesn't show up when I start it. The window opens, and the SC sound is there for the menu, but all that I see is green blocks in the window.

---

### Post by Mike7171 on 2007-07-05
This is what it shows:

[IMG]http://i114.photobucket.com/albums/n258/designer-drug71/Screenshot-1.png[/IMG]

EDIT: lol, that's big. Not sure how to attach thumbnails, sorry.

---

### Post by mancxvi on 2007-07-05
That's odd. Try reenabling pixel shader support and making sure vertex shader is set to hardware so you can match my config. Also, check the option to allow DirectX apps to keep the mouse. I'm assuming it's running in a virtual desktop since you said it was in a window.

For reference, here are my system specs:

Athlon XP 1800+
Nvidia Geforce4 Ti4400
EPoX 8KHA+ motherboard
512MB RAM
SBLive Value

running Ubuntu Edgy with Wine 0.9.40 and Nvidia drivers 9639

edit: do you have compiz or beryl running?

---

### Post by Mike7171 on 2007-07-05
Did all that, and it's still the same. The only good news is that is sounds like its faster (the 'beep' sounds when you highlight a selection in the menu happen when i move my mouse around pretty fast). I just need to see it.

---

### Post by mancxvi on 2007-07-05
Try it in fullscreen and see if it works. I have an issue where the graphics stop drawing once the window loses focus, and I'm completely unable to run it fullscreen.

---

### Post by Mike7171 on 2007-07-05
Nope, just a black screen with a white bar on the top.

---

### Post by mancxvi on 2007-07-05
What are your specs, and what version of Wine?

---

### Post by Mike7171 on 2007-07-05
How do I check? Sorry, I'm fairly new to Ubuntu. Either way, I was able to see before I added those things into regedit.

---

### Post by mancxvi on 2007-07-05
In winecfg, it should be in the About tab.

---

### Post by Mike7171 on 2007-07-05
Wine 0.9.40

---

### Post by mancxvi on 2007-07-05
I'm not sure what else to do. For reference, it's this bug ([http://bugs.winehq.org/show_bug.cgi?id=421](http://bugs.winehq.org/show_bug.cgi?id=421)) that is causing the issue. Until that's fixed, we're stuck with workarounds that don't work for everybody. I wish I could help more than that. If I see anything else, I'll post it.

edit: Here's an explanation of why it's a problem: [http://wiki.winehq.org/DIBEngine](http://wiki.winehq.org/DIBEngine)

---

### Post by Mike7171 on 2007-07-05
I deleted those things in regedit, and I can see again. It's back to lagging again too however. Once there is a solution I will put them back.

---

### Post by Mike7171 on 2007-07-05
The link in your edit explains the problem, but is there a solution to it?

---

### Post by mancxvi on 2007-07-05
Unfortunately, it hasn't been fixed yet. It's being worked on, though, so there's hope for the future. Pray for a true peace in space!

---

### Post by Mike7171 on 2007-07-06
All right, so back to square one I guess. Any ideas anyone? All my driver info and whatnot is in the previous pages. Any and all help is appreciated.

---

### Post by jimminy_kriket on 2007-07-10
Did you try the nice 20 command? Starcraft is 2d so it might just be a processor thing.

If all else fails, get xubuntu! Starcraft runs alot better in xfce.

---

### Post by slopis on 2008-01-18
i have the same problem. well i did all you told him, except install xubuntu (i dont want to reinstall pc)
i have one more problem, when i connect to a server, then sc crashes, and write this {i dont know how to make those codes to..}
its gives me at the end:
[$ err:seh:setup_exception stack overflow 0 bytes in thread 0025 eip 7bc62440 esp 6a3f7000 stack 0x6a3f7000-0x6a507000
err:ntdll:RtlpWaitForCriticalSection section 0x1904662c "?" wait timed out in thread 0024, blocked by 0025, retrying (60 sec)]

in the midle was this:
[Unhandled exception: page fault on write access to 0x011cc000 in 32-bit code (0x018c0148).]
is it becouse mine ubuntu is 64bit?

if i understood right that guy who made these posts was usin 64bit pc too..

and friend of mine (using 32bit) runed SC without problems

---

### Post by Saint Angeles on 2008-01-25
> **slopis said:**
> i have the same problem. well i did all you told him, except install xubuntu (i dont want to reinstall pc)...

you dont have to reinstall, just type: ```
sudo apt-get install xubuntu-desktop
```

---

### Post by xsism on 2008-05-18
1) Press ALt+F2
2) Type 'wine regedit' & press enter

3) Add or Edit the following keys

```
 [HKEY_CURRENT_USER\Software\Wine\Direct3D]
"OffscreenRenderingMode"="fbo"
"UseGLSL"="enabled"
"VideoMemorySize"="YOUR VIDEO MEMORY SIZE"

[HKEY_CURRENT_USER\Software\Wine\DirectSound]
"HardwareAcceleration"="Emulation"

[HKEY_CURRENT_USER\Software\Wine\Drivers]
"Audio"="alsa"
```

4) exit regedit and all Wine Apps.

5) Run Starcraft

---

This has improved the cursor speed for me considerably. I don't notice any major issues with lag as much. When the DIB engine is added to Wine, this will be much better. Till then, this works well.

I have a AMD Athlon 2800 with 1GB RAM and Nvidia Geforce with 256MB ram. Definitely not the fastest by today's standards.

I hope this helps.

---

### Post by zomgneeks on 2009-08-08
> **xsism said:**
> 1) Press ALt+F2
2) Type 'wine regedit' & press enter

3) Add or Edit the following keys

```
 [HKEY_CURRENT_USER\Software\Wine\Direct3D]
"OffscreenRenderingMode"="fbo"
"UseGLSL"="enabled"
"VideoMemorySize"="YOUR VIDEO MEMORY SIZE"

[HKEY_CURRENT_USER\Software\Wine\DirectSound]
"HardwareAcceleration"="Emulation"

[HKEY_CURRENT_USER\Software\Wine\Drivers]
"Audio"="alsa"
```4) exit regedit and all Wine Apps.

5) Run Starcraft

---

This has improved the cursor speed for me considerably. I don't notice any major issues with lag as much. When the DIB engine is added to Wine, this will be much better. Till then, this works well.

I have a AMD Athlon 2800 with 1GB RAM and Nvidia Geforce with 256MB ram. Definitely not the fastest by today's standards.

I hope this helps.

In HKEY_CURRENT_USER\Software\Wine I don't have a Direct3D key. Should I add one or does that mean I have a different problem?

---

### Post by NightMKoder on 2009-08-09
> **niko.stap said:**
> In HKEY_CURRENT_USER\Software\Wine I don't have a Direct3D key. Should I add one or does that mean I have a different problem?

Add one. It's not there by default.

---

