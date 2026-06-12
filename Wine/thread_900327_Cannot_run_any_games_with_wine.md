---
title: "Cannot run any games with wine"
date: 2008-08-25
forum: Wine
---

### Post by the[V]oid on 2008-08-25
Hello. Regular programs work perfectly with wine. But everytime I try to run a game that is actually using DirectX (for instance Flatout, but it happens with every DirectX using game) I get following:
```
[...]
Backtrace:
=>1 0x7e05b6f5 in i965_dri.so (+0x856f5) (0x0033eee8)
  2 0x7e2e51b6 IWineD3DImpl_FillGLCaps+0x8803() in wined3d (0x0033f1e8)
  3 0x7e2eed6c InitAdapters+0x1f9a() in wined3d (0x0033f6d8)
  4 0x7e35ebca WineDirect3DCreate+0x22() in wined3d (0x0033f708)
  5 0x7e3bffaf in ddraw (+0x1ffaf) (0x0033f768)
  6 0x7e3c05a4 DirectDrawCreate+0xbd() in ddraw (0x0033f7b8)
  7 0x003e121f in gen.mpr (+0x121f) (0x00000020)
  8 0x00000000 (0x00000000)
```
I'm using wine 1.0 from the ubuntu repository. I'm not sure whether this metters, but I'm using compiz. My hardware:
```
user@host ~ $ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

Non-Wine programs like glxgears and games like wormux run fine.
What could I do to get my games to work on wine?

---

### Post by ooobuntooo on 2008-08-25
Do the wine games work in windows with the same hardware?

---

### Post by the[V]oid on 2008-08-25
To be honest, I don't know, I have no windows on this box (laptop). But I've tried a wide spectrum of (even very old, eg DX6) games and cannot imagine that none of them is working.

---

### Post by ooobuntooo on 2008-08-25
> **'the[V]oid said:**
> To be honest, I don't know, I have no windows on this box (laptop). But I've tried a wide spectrum of (even very old, eg DX6) games and cannot imagine that none of them is working.

There's your problem, you may need an ATI/nVIDIA card to play DirectX or OpenGL games.

---

### Post by the[V]oid on 2008-08-25
1. dmesg tells me: "Detected an Intel 965GM Chipset" - Now I've read of a lot of people playing WoW on a 965GM. So it looks like it is not the card's fault, doesn't it?
2. I am able to run native Open-GL 3D-Stuff, and it works.

---

### Post by aoanla on 2008-08-25
Have you tried turning off Compiz/Desktop Effects, and then trying with Wine?

---

### Post by SpaceMaster on 2008-08-25
Here's the one that worked for me:

enabling the restricted graphics drivers.

---

### Post by the[V]oid on 2008-08-25
> **aoanla said:**
> Have you tried turning off Compiz/Desktop Effects, and then trying with Wine?

I've just tried it - Same result. I switched compiz off via "Compiz Switch", dunno if it's needed to restart X.org afterwards? I think not.

> **SpaceMaster said:**
> Here's the one that worked for me:

enabling the restricted graphics drivers.

I already thought that this might be what I am looking for, but I don't realize where to get those from? I could neither find any restricted graphics drivers from intel in the repository nor a guide or a tutorial. Where do I have to get them from?

---

### Post by YokoZar on 2008-08-25
> **'the[V]oid said:**
> I already thought that this might be what I am looking for, but I don't realize where to get those from? I could neither find any restricted graphics drivers from intel in the repository nor a guide or a tutorial. Where do I have to get them from?You don't need them for Intel cards, since they have good open source drivers.


Can you run ANY Wine programs, like winecfg?

---

### Post by the[V]oid on 2008-08-25
Yes, I can run everything except programs using Direct X (and perhaps Open GL, didn't try it).

---

### Post by the[V]oid on 2008-08-26
Anyone has an idea??

---

### Post by bpl07 on 2008-08-26
You could try upgrading to the [most recent version of wine]("http://www.winehq.org/site/download-deb").  Also, I've had success with some games (Portal) by forcing it to use DirectX 8 instead of DirectX 9.  There's also some interesting stuff on Fallout over in the [wine appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=43").

---

### Post by the[V]oid on 2008-08-26
I've just tried the native linux game planetpenguinracer and it works fine. So I'm pretty sure now that my problem only has to do something with wine. I think I will try the most recent version of wine later, but, as far as I understand, 1.0 is the "most stable" version. Some of the games I'm trying are using DX 6 or 7, it's not only Flatout, as I already mentioned.

---

### Post by SoronZero on 2008-08-26
Hi there, I also have this weird situation, I just installed wine and normal programs that don't use DirectX at all run fine (i.e. quicken), however any games like WoW, RO, or even other apps like ulead dvd studio that use DirectX all crash the system, to clarify I can physically swap my hard drive(s) to swap between linux and XP (hard drive dock system) and everything runs fine on the XP drive so I know it's not a hardware issue, I also installed the restricted drivers for my nvidia 7600 card and gl gears runs without any problems.

_My hardware specs_
AMD Athlon 64x2 4800+
1Gb ram
2x 160Gb Hard drives (Main Windows XP, dual drive Config)
1x 160Gb Hard drive (Ubuntu Drive, solo config)
1x DVDR
1x CDR
Video Geforce 7600 GS (512 Mb, AGP 8x)
Hauppaugge PVR 350 Capture board
Using motherboard for sound (Asrock)

_Ubuntu Setup_
Hardy Heron 8.04
Wine dev. 1.1.3

---

### Post by the[V]oid on 2008-08-26
> **bpl07 said:**
> You could try upgrading to the [most recent version of wine]("http://www.winehq.org/site/download-deb").

> **'the[V]oid said:**
> I think I will try the most recent version of wine later.

I'm afraid I can only see a description for Hardy there, but I am still on Gutsy. Well, I just changed "hardy" to "gutsy" in the url mentioned on the linked paged:
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

Afterwards I could upgrade wine from 1.0 for Ubuntu 7.04 to 1.0 for Ubuntu 7.10 - Dunno why I wasn't able to do this before, according to my system info I *am* on 7.10. There is no update available to a later version. Never the less, nothing changed, I'm still getting the same error.

---

### Post by SoronZero on 2008-08-27
I think its an issue with wine, I switched WoW from direct3d to openGL and I get to the login screen but when I login to the actual game world it freezes the system so I have to reboot but at least I get a partial load, why glxgears runs without a problem, got me.

---

### Post by the[V]oid on 2008-08-27
> **SoronZero said:**
> I think its an issue with wine, I switched WoW from direct3d to openGL and I get to the login screen but when I login to the actual game world it freezes the system so I have to reboot but at least I get a partial load, why glxgears runs without a problem, got me.

I think our problems have different causes.
I'm not sure whether my problem is an issue with wine.
As I noticed, it happens with Cedega as well.

Noone an idea what the reason could be?

---

### Post by the[V]oid on 2008-08-27
Not sure whether this has something in common with my wine-problem, but I've just noticed that MPlayer doesn't work. Everytime I try to run it I get:
```
[...]

[xv] dx: 0 dy: 0 dw: 614 dh: 384
A:   0.1 V:   0.0 A-V:  0.127 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 
decaudio: minlen=24332 maxlen=61452 declen=11180 (max=74752)
decaudio: decoding 9056 bytes, max: 72628 (9216)
demux_lavf_fill_buffer()
demux_lavf_fill_buffer()
libmad: 104 bytes processed
demux_lavf_fill_buffer()
libmad: 105 bytes processed
demux_lavf_fill_buffer()
demux_lavf_fill_buffer()
libmad: 104 bytes processed
demux_lavf_fill_buffer()
libmad: 105 bytes processed
decaudio: declen=11180 out=24340 (max 61452)
vd_ffmpeg data: 5f3141ee, cd1f61d7, 4e6b0be9, b4b88c41
X11 error: BadAlloc (insufficient resources for operation)
Type: 0, display: 0x8911878, resourceid: 67, serial: 78
Error code: b, request code: 8c, minor code: 13


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
gnome_screensaver_control()
```

Other players like Totem are working fine.



From [hear]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/111257") I know now that at least the problem with MPlayer is an issue with XV.
**[COLOR="DarkRed"]Does wine perhaps somehow use XV?[/COLOR]**

---

### Post by SoronZero on 2008-08-27
I just tried to play a video in mplayer, I got an error "Error: could not open directshow codec wmvdmod.dll", video loaded first frame played but then I got that error and it froze mplayer. Most of the other older videos play fine on it but that one video gave me that error.

---

### Post by SoronZero on 2008-08-27
I corrected the error with mplayer, I still get the error about loading directshow but the video plays now, I went to the codecs section and enabled directshow codec.

---

### Post by the[V]oid on 2008-08-28
I'm quite sure your error is unrelated to mine. I think it's better you start another thread.

*Anyone who can help me with my problem??*

---

