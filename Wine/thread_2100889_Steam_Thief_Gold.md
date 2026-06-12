---
title: "Steam Thief Gold"
date: 2013-01-03
forum: Wine
---

### Post by kreggz on 2013-01-03
According to WineHQ it works for one person but I keep getting the error invalid parameters. I have done everything on this page except Tfix [http://appdb.winehq.org/objectManager.php?sClass=version&iId=26146](http://appdb.winehq.org/objectManager.php?sClass=version&iId=26146)

Using Playonlinux with Wine 1.5.10. Precise 32bit fully patch with a GTX650 Intel 2.6Ghz.

---

### Post by _6i on 2013-01-04
Hi,
  I managed to make it work even without TFix (on Ubuntu 12.04 amd64 + wine 1.5.20), but I strongly recommend to apply TFix, as there seems to be no downside. Among other things, the engine seems to be partially updated, so it looks better (textures & some meshes), uses directx 9, ingame resolution switching (for resolutions above 800x600; no widescreen without the widescreen patch though -> in my case: 1920x1080x32 with 2 black stripes on each side of the screen to make it have a 4:3 aspect ratio), the sound-buffering issue in videos disappears, and it also runs noticeably faster.

I kinda used a shotgun approach for now, so probably only some of the things are necessary from the ones listed below. When I figure out which are the truly necessary ones, I submit a test result to winehq, too.
I used vanilla wine from the ubuntu wine ppa ( [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa) ), then iirc:
 - installed steam with the winetricks script (automatically to a separate wineprefix):
  Using the gui: Install an app->steam)
OR the command line:
```
winetricks steam
```
Then use it with the '-no-dwrite' command line option.
 - all other operations were done in the scope of the new "steam" wineprefix:
```
export WINEPREFIX=$HOME/.local/share/wineprefixes/steam
```
 - I always set the vendor, model and video-memory size manually (just to be sure) for every wineprefix I create by adding the corresponding registry entries (I made a .reg file to speed it up) &#8211; use the [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) page as a reference ("Direct3D" section). 
To get the vendor and model numbers, I did the following:
1) Get the domain/bus/slot number of my card:
```
sudo lspci | grep VGA
```
It's output for me is:
```
05:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 9800 GT] (rev a2)
```
2) Just list my video card, but with numeric codes instead of strings:
```
sudo lspci -s 05:00.0 -n
```
Output is:
```
05:00.0 0300: 10de:0614 (rev a2)
```
Then the vendor is "10de" and the model is "0614"

In my case (NVidia GeForce 9800 GT, 512 MB onboard RAM):
The file contents of my "nvidia-geforce_9800gt.reg":
```

REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"VideoMemorySize"="512"
"VideoPciDeviceID"=dword:00000614
"VideoPciVendorID"=dword:000010de

```
And I apply it with:
```
regedit nvidia-geforce_9800gt.reg
```
 - installed the indeo codecs to make the intro and the cutscenes work:
```
winetricks icodecs
```
 - installed the visual c++ 2008 runtime and direct3d dlls (in advance for TFix, and just in case..):
```
winetricks vcrun2008 d3dx9 d3dx9_43
```
(For some reason, 'd3dx9' didn't install the d3dx9_43 dll(s) and steam needed it, so I had to do it separately.)
 - as for me starting the tutorial crashed with a GDI switching error, I activated the GDI DirectDrawRenderer instead of the default OpenGL:
```
winetricks ddr=gdi
```

Iirc, that was all I did, and the game ran even without TFix, but the tutorial (all I tried) was strangely slow, and the audio-buffering problem was present in the videos (it was hard to understand what the talking was about).


Then I Installed TFix 1.13 (with NewDrak v1.19; from here: [http://www.ttlg.com/forums/showthread.php?t=134733](http://www.ttlg.com/forums/showthread.php?t=134733) ) to the steam game directory, and everything seems perfect now. ;) (I went through the tutorial and the first mission.)
 - Install TFix (to the same "steam" prefix, as everything above):
```
wine TFix_1.13.exe
```
In my case, I had to install it to:
```
"Z:\home\myusername\.local\share\wineprefixes\steam\drive_c\Program Files (x86)\Steam\steamapps\common\thief_gold\"
```
(I used the default install options: everything except the DromEd update.)

Now, I have to prepare for some exams, but sometime later I will try to drop the unnecessary steps/components and submit a winehq test result.

Good luck.

---

### Post by kreggz on 2013-01-05
Wow thanks your reply, I will try this and report back.

---

### Post by kreggz on 2013-01-06
Ok that works very well. I am now up to Cragscleft prison. 

Thanks for taking your time to write up a comprehensive reply. I hope it helps others in the future too. I actually installed wine manually and set my Video card correctly. 

I will submit a Wine report.

thanks again!

---

