---
title: "[SOLVED] Please help: I managed to muck up Wine's DirectX support, somehow :S"
date: 2008-03-24
forum: Wine
---

### Post by citizenc on 2008-03-24
Here's the short version:

Ubuntu 7.10 w/ nVidia 8800. I installed Ubuntu and wine 0.9.57 (current when I installed linux) and got everything working flawlessly. (Oblivion, Team Fortress 2, Dreamweaver Photoshop).

A new version of wine came out recently (0.9.58). Prior to the .deb being released, I downloaded and compiled 0.9.58 directly from source. Did a make install and everything upgraded fine. The new binary continued to run all my applications.

Then I made the mistake of clicking "yes, go ahead and install the software updates".

This promptly broke wine entirely. The "upgrade" installed with no issue, however now applications wouldn't run. I decided to remove wine totally and start again:

1) sudo apt-get purge wine
2) renamed ~/.wine to ~/wineold
3) renamed /usr/local/lib/wine to wineold

4) sudo apt-get install wine

Step 4 downloaded and installed 0.9.58 from the Ubuntu repo and installed with no errors. I have gotten Dreamweaver and Photoshop to work, but directx apps now bail:

> err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F

I've tried to remove and reinstall wine several times but the result is always the same: DirectX apps crash.

Yes, I've copied over the one DX9 dll from my Windows installation.

I'd also like to mention that I did try "make uninstall" from the folder that I compiled wine 0.9.58 in. It appeared to do some uninstallingy-sorta-stuff but no dice either.

Help? =(

 I'm relatively new to the linux thing and am getting a little frazzled.

---

### Post by citizenc on 2008-03-24
Clarification:

The "install available software updates" notification was the standard update notification through Ubuntu.

---

### Post by happyhamster on 2008-03-24
> **citizenc said:**
> I downloaded and compiled 0.9.58 directly from source. Did a make install and everything upgraded fine. 
Did you also manually uninstall this compiled version? If not, navigate to the folder with the wine source code and run:

sudo make uninstall

After that, get rid of the .wine folder again and try to remove and re-install wine once more:

sudo apt-get remove --purge wine

sudo apt-get install wine

BTW. If you have your applications running under wine to your liking, simply don't update wine. Go to System-->Administration-->Synaptic Package Manager, do a search for "wine", high-light it and from the menus select Package-->Lock Version.

When that's done, you won't be asked to update wine in the future. Good luck.

[edit: crap, I didn't read your post properly]:

---

### Post by happyhamster on 2008-03-24
- Ok, I see you tried "make uninstall" already. Try uninstalling wine nevertheless:

sudo apt-get remove --purge wine

- Next, run:

wine --version

- If all's well you'll get a message that wine isn't installed. If so, the compiled version very likely uninstalled successfully as well. I would take a look at your graphics driver next. Try running glxinfo for example, to see if direct rendering works.

---

### Post by citizenc on 2008-03-24
```
Removing wine ...
Purging configuration files for wine ...
dpkg - warning: while removing wine, directory `/etc/xdg/menus/applications-merged' not empty so not removed.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
cary@cary:~/Desktop/wine-0.9.58$ wine --version
The program 'wine' is currently not installed.  You can install it by typing:
sudo apt-get install wine
bash: wine: command not found
```

So far, so good...

```
cary@cary:~/Desktop/wine-0.9.58$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB

...
```

It continues, with lots of extensions then a table of what I think is colour depth data. Looks successful, from what I can tell.

---

### Post by citizenc on 2008-03-24
Could there be any ... uh ... "wine droppings" anywhere else on my system? Perhaps the directx libraries have a couple of different versions, leftover in some directory somewhere?

---

### Post by happyhamster on 2008-03-24
I don't think so, but you could do a search:

sudo updatedb

locate d3d
locate directx


BTW, are you sure those programs don't work? Perhaps it's a matter of configuring wine in a particular way (registry settings, etc). Also, note that since wine 0.9.58 winxp is the default wine setting (instead of win2000).

---

### Post by citizenc on 2008-03-24
Yeah, I'm sure they didn't work. Consistently, throughout the various install/uninstall/reinstall steps I tried, Photoshop and Dreamweaver would always work. The installation routine for Oblivion would work. The Steam client (which is used to download and install Team Fortress 2) installed and ran correctly. The issue is running TF2 and Oblivion.

---

### Post by citizenc on 2008-03-24
```

/home/cary/.ies4linux/ie6/drive_c/windows/system32/d3d9.dll
/home/cary/.ies4linux/ie6/drive_c/windows/system32/d3d8.dll
/home/cary/.wine/drive_c/windows/system32/d3d9.dll
/home/cary/.wine/drive_c/windows/system32/d3dx9_27.dll
/home/cary/.wine/drive_c/windows/system32/d3d8.dll
/home/cary/.wine/drive_c/windows/temp/AUG2005DXREDIST/Aug2005_d3dx9_27_x64.cab
/home/cary/.wine/drive_c/windows/temp/AUG2005DXREDIST/Aug2005_d3dx9_27_x86.cab

```

Could those matter?

(Nothing came up when doing "locate directx")

---

### Post by citizenc on 2008-03-24
Ok. I removed ~/.wine, just to be sure.

sudo apt-get install wine -- installed and completed successfully.

Ran "winecfg", which opened correctly. However, saw the following console output:

```
cary@cary:~$ winecfg
wine: creating configuration directory '/home/cary/.wine'...
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8c1, disabling mixer
Could not load Mozilla. HTML rendering will be disabled.
err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": /usr/lib/libxml2.so.2: undefined symbol: gzopen64
err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": /usr/lib/libxml2.so.2: undefined symbol: gzopen64
wine: '/home/cary/.wine' created successfully.
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8c1, disabling mixer
fixme:jack:JACK_drvLoad error loading the jack library libjack.so.0, please install this library to use jack
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
cary@cary:~$ 
```

Under the Wine configuration, I verified the OS is now Windows XP. Under the graphics tab, "allow directx apps to stop the mouse cursor" and "allow the window manager to control the windows" are both disabled.

I've enabled the emulated virtual desktop, with a resolution of 1024x768.

By default, Direct3D vertex shader support is set to "hardware", with "allow pixel shader" enabled as well.

Audio is set to the ALSA driver. Tests work.

Installing Oblivion now.

---

### Post by citizenc on 2008-03-24
[http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux) -- this is the guide that I'm following, for the record.

---

### Post by citizenc on 2008-03-24
Yeah, it crashed hard.

Plain text crash log is attached to this message.

---

### Post by citizenc on 2008-03-24
Fixed Oblivion!

As it turned out, it had nothing to do with Wine.

Rather, it looks like the culprit is a corrupt saved game file. Removed ~/My Games/Oblivion and it started right up.

I wonder if something similar could explain the Team Fortress 2 problems.

---

### Post by happyhamster on 2008-03-24
What do you get when you run it like this:

WINEDEBUG=-all,+loaddll wine oblivion.exe

And also:

WINEDLLOVERRIDES="d3dx9_27=n" WINEDEBUG=-all,+loaddll wine oblivion.exe

Have you edited the registry as well? Also try testing with the usb soundcard/headset disconnected.

---

### Post by happyhamster on 2008-03-24
:lolflag: too late. Congratulations though.

---

### Post by citizenc on 2008-03-24
Ahahaha

Thanks for.. er... being there =)

---

### Post by hitent on 2008-07-27
Thanks! for the tip. Helped me get rid of update notification for Wine, for I needed to keep wine 0.96 versus the new update 1.0, which was the next in line. My other programs were breaking because of it. 

I did Lock it and just ran check on updates, it even got rid of down arrow from the pane.

Thanks!

---

