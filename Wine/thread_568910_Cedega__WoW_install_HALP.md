---
title: "Cedega / WoW install HALP"
date: 2007-10-06
forum: Wine
---

### Post by indiechixor on 2007-10-06
I'm in the process of trying to install WoW via Cedega, and apon runing the installer.exe file i get this error:

```
indie@Hikaru:~$ cd TransGaming_Drive
indie@Hikaru:~/TransGaming_Drive$ cedega Installer.exe
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
F1 2007-10-06 11:12:23,071 WARNING The Cedega version (6.0.3) you are defaulting to is missing the following file : /home/indie/.cedega/.winex_ver/winex-6.0.3/.transgaming/config
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2882, in <module>
    retval = Point2Play_ref.winex( 1, installcmd_gamename, installcmd_exename, None, Point2Play_ref.gamedir + installcmd_gamename + "/" + "games.ini.new", Point2Play_ref.default_winex, ( dos_cwd_path, use_big_exe, pthreads_value ), cmdlineoverride=runcmd_cmdlinearg, ModifiedInstallConfigs="install_config", debug_channel=debug_channels, OverrideGameProfile=config_file_to_use, MonitorCdromEject=monitor_cdrom_eject, gddb_file=gddb_file )
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 1498, in winex
    (p, v) = os.waitpid(pid, os.WNOHANG)
OSError: [Errno 10] No child processes
indie@Hikaru:~/TransGaming_Drive$ 
```

Then a box pops up saying
> Can't seem to be able to execute the WineX start up script
/home/indie/.cedega/.winex_ver/winex-6.0.3/bin/winex3 -
perhaps your installation of WineX version 6.0.3 is corrupted?

I tried seeing if anyone else had a similar problem [lol google] and tried the one thing they suggested, which was to upgrade/install hal and dbus, and neither worked.

how do i obtain said file?

---

### Post by Sammi on 2007-10-06
I have no idea with Cedega. Maybe you should ask them, as you did pay for their product.

You could also try the free and community supported Wine, which Cedega is based of. It has come a long way since Cedega started their offspring project. It is far easier to get WoW running in Wine now, than is has been in the past, and the performance is at least equal. You really don't need Cedega for WoW.

See here: [http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482)

---

### Post by indiechixor on 2007-10-06
well I actually did install Wine, and was having issues with it running... see
[http://ubuntuforums.org/showthread.php?t=568215](http://ubuntuforums.org/showthread.php?t=568215)

if you maybe had some help with that issue, I would be good as gold.

Basically when I open WoW in fullscreen mode, I get the opening Video and thats it. If i hit any buttons whle the video runs it exits out of Wine....if i let the video play all the way through, it exits once the opening video is over. 

If i open it in windowed mode, It opens the launcher perfect, but then in gives me a big black screen and i lose all control of Ubuntu...

I was thinking of re-installing wine, but if i can find a work-around then i would be happy.

---

### Post by indiechixor on 2007-10-06
ok updatey... went through to redo the apt-get process of Wine, and caught some errors i didn't see earlier

```
Err http://www.getautomatix.com feisty Release.gpg                             
  Could not connect to www.getautomatix.com:80 (216.120.255.9), connection timed out
Err http://www.getautomatix.com feisty/main Translation-en_US
  Could not connect to www.getautomatix.com:80 (216.120.255.9), connection timed out
Fetched 52.4kB in 4m0s (218B/s)                         
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg  Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2  Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://www.getautomatix.com/apt/dists/feisty/Release.gpg  Could not connect to www.getautomatix.com:80 (216.120.255.9), connection timed out
Failed to fetch http://www.getautomatix.com/apt/dists/feisty/main/i18n/Translation-en_US.bz2  Could not connect to www.getautomatix.com:80 (216.120.255.9), connection timed out
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz  Could not resolve 'wine.lowvoice.nl'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
indie@Hikaru:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
indie@Hikaru:~$ 


```

not sure what to do about that...

---

### Post by drunkenphysicist on 2007-10-06
I had WoW running fine with wine before the latest patch that allowed voice chat.  Now after the launcher screen it goes into a loop with weird sound then dies.  This is rather annoying.  Has anyone gotten WoW to run after the voice chat patch?

---

### Post by Sammi on 2007-10-07
Ok. I need more info from you, in order to be able to help you.

CPU model?
Graphich card model?
Graphics card driver version?
Amount of RAM?
Wine version?

Please post the output of these commands:
```
glxinfo | grep 'OpenGL version'
glxinfo | grep vendor 

```And let this command run for a while, say 30 seconds, then post the output:
```
glxgears -printfps
```

---

### Post by indiechixor on 2007-10-07
Sony Vaio
Intel Pentium dual-core T2060 @ 1.60GHz
 945GM/GMS/940GML Express Integrated Graphics Controller
memory: 2.0GB
current avalible disk space 78GB

Ubuntu - 7.04 feisty

```
indie@Hikaru:~$ glxinfo | grep 'OpenGL version'
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
OpenGL version string: 1.3 Mesa 6.5.2

```
```
indie@Hikaru:~$ glxinfo | grep vendor
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc

```

then

```
indie@Hikaru:~$ glxgears -printfps
Usage:
  -display <displayname>  set the display to run on
  -stereo                                  run in stereo mode
  -fullscreen                            run in fullscreen mode
  -info                                       display OpenGL renderer in
```

Thanks so much for the help <3

---

### Post by Sammi on 2007-10-07
Those commands didn't work very well :(

I made a mistake with the last one. It should only be "glxgears", not "glxgears -printfps". Let that run for 30 secs and then post what fps you are getting.

How does 3D work in other games. Is the performance good or bad?

You systems specs are ok. Only you Intel graphics card makes me a little nervous. Don't have any experience with fixing graphical problems with Intel cards. Have a Nvidia myself.

---

### Post by indiechixor on 2007-10-09
5146 frames in 5.0 seconds = 1029.168 FPS
5185 frames in 5.0 seconds = 1036.930 FPS
5144 frames in 5.0 seconds = 1028.670 FPS
4942 frames in 5.0 seconds = 988.398 FPS
4899 frames in 5.0 seconds = 979.653 FPS
4780 frames in 5.0 seconds = 953.924 FPS
3750 frames in 5.0 seconds = 749.914 FPS
4828 frames in 5.0 seconds = 965.565 FPS

I haven't played any other games... 

I actually got it running in full-screen mode, but once It gets past the opening video (of WoW)  or if i hit enter, i get this screen: [A screenshot of said error]("http://img.photobucket.com/albums/v247/indie_chixor2/death.png")

thankfully doing it in fullscreen it doesn't lock up...but its quite annoying. The opening video is beautiful btw, i see no Graphical hang-ups or glitches

---

### Post by Sammi on 2007-10-10
Fps rates at aound 1000 might seem like a lot, but in  glxgears it's actually very little. I have it running at about 7500 on my primary desktop and 3-4000 on my laptop. Both have Nvidia graphics cards. I also used to get errors like yours with older Nvidia drivers, but for the last year or more, all the new Nvidia drivers have been working very well. I can't help but to feel like this has something to do with your Intel graphics card and it's drivers, but I am definatively no expert.

You should try some other 3d game, to see how that will perform. Here is a good resource for game debs: [http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)

---

### Post by indiechixor on 2007-10-10
Thank you so much Sammi!

you've been a wealth of knowledge. I'm currently downloading a different 3D game to see how/If it runs. I'll keep you posted!

---

### Post by indiechixor on 2007-10-10
Installed and got Second Life working (its another graphically-demanding 3D game)

It runs well enough, untill I try and click on something in the game with the mouse... Its glitches out and goes black then back to the game... I could't click on certain boxes and others would work.

Y__Y so confusing...

---

### Post by kwagster on 2007-10-13
I have the same problem (error message) while I try installing Starcraft (a game that my computer could definitely handle).  I'll try another game and see how that works.

---

