---
title: "youve probably heard it before... CS:S"
date: 2008-07-27
forum: Wine
---

### Post by gsrcrxsi on 2008-07-27
ok so ive never been much of a gamer, but my friends at work all play CS:S so i figured id give it a try. i installed wine, i installed steam, and i installed the game (DLed it from steam, installing from disc didnt work out so well). game loads up fine. but it seems like when its working its not using the vid card at all, but is using all CPU, making everything VERY slow. i havent actually played with anyone else, i just ran the video stress test. dont know if that matters at all

system:

Xubuntu (mythbuntu technically)
Asus P5K3 MB
Q6600 @ 3.8GHz
Gskill DDR3 1066 MHz
BFG 8800GT w/ accelero S1 

is this a driver issue?
is this a wine issue?
or is this just how it is?

ive seen many other vids of poeople playing games like this through wine, so i dont think the answer is there, but i dont know. any help would be appreciated. :)

---

### Post by noerrorsfound on 2008-07-27
Do you already have the proprietary NVIDIA drivers installed?
```
glxinfo | grep rendering
```
It should say:
> direct rendering: Yes

---

### Post by gsrcrxsi on 2008-07-27
you know it didnt even dawn on me to try that lol. ill run that command when i get home. 

heres the thing and its probably my fault if it says no. i used to have a 7300GT and proprietary drivers installed, and i recently bought a 8800GT. when i installed the 8800GT, everything seemed fine and i never installed any new drivers. so maybe thats it. 

also i never got into gameplay. and winehq says everything works in wine, but they didnt test the video test, so theres no way to know on wether or not the test just doesnt work lol. 

ill try the drivers when i get home. thanks for the reply. if anyone else has had this specific issue please chime in.

---

### Post by gsrcrxsi on 2008-07-27
rendering was a Yes

---

### Post by desertboy on 2008-07-28
Try running it with the switches -dxlevel 8

---

### Post by gsrcrxsi on 2008-07-29
from the comand line? ive just been running steam (and hence games) from the GUI. i hate having a terminal open and constantly pooping out stuff while the app runs. 

i seem to not be able to utilize my vid card. i play games fine (HL2 and CSS) but vid test is like 0.5 FPS. why isnt this using the vid card? the CPU usage is through the roof.

---

### Post by desertboy on 2008-07-30
I haven't got CS:S but I do own HL2 & episode 1 which both work flawlessly I don't have the restricted drivers installed though I used envy (My restricted drivers broke one update and I was in a hurry) to install my drivers, I have 8800GTS.


My suggestion would be untick the restricted drivers and install them with envy. Or install them yourselves from nvidia's website (Not so easy but not rocket science either.)

What performance are you getting in glxgears it should be at least 5,000+ fps for your card.

---

### Post by blakkie on 2008-07-30
> **gsrcrxsi said:**
> from the comand line? ive just been running steam (and hence games) from the GUI. 

You can add the command line switches in steam (rather than using a terminal) by right clicking on the game in steam and going to properties.  In the window that pops up is a button to click for startup options (or something similar).  This will let you insert command line switches such as the -dxlevel 8

Hope that helps

---

### Post by Koosti on 2008-07-30
I guess I'll throw this in this thread rather than making a new one.

I'm having a tad of trouble with both CS:S and DoD:S. 

I can start both games up to the main menus just fine, but I can not get ingame. CS:S closes down after "sending client info" and DoD:S freezes up on that same portion of loading. I've left DoD:S running for 7 hours and it won't go past that so I know it's not just going slow.

I'm running with -dxlevel 71 at the moment with a hefty FPS config.

My system specs are:
AMD Phenom 8400 Triple-Core
3 GB DDR2
Nvidia Geforce 8500GT 512MB
Asus M2N68-LA 

I know, it sucks, but I think I should be able to get at least ingame with it.

Any ideas?

---

### Post by gsrcrxsi on 2008-07-30
whats the command again for glxgears? is it just "glxgears"? i cant remember lol

---

### Post by AFarris01 on 2008-08-05
yes, the command is just glxgears...

Koosti, ive got a question and a statement for your issue:

statement: try disabling the 'Allow pixel shader support' in the wine graphical settings, and retry.  I had a similar problem way back when, and thats what ended up fixing it. if not, you can try making sure that under sound settings, only OSS and ALSA are selected... ive seen a few postings that that fixed it for some people.

now, Question: im having some issues with a Phenom x3 under my control, (which i was actually searching about when i ran across this thread), and this issue is crippling the system its on.  did you have to do anything special to get all 3 cores to be recognized in ubuntu?  so far, on the computer i have in question, everything hardware/BIOS wise is correctly set up, but ubuntu only sees the processor as a single core, rendering the system unusually slow, and causing many headaches for me.  its the last unresolved issue im having on any of my systems, and it is my hope that you may have some input.

sorry to get off topic, but thanks for listening/reading all the same!

Andrew

---

### Post by gsrcrxsi on 2008-08-05
glx gears shows 3800-4000 FPS. in CS:S im only getting 30-40 FPS. it should be way higher than that shouldnt it?

my system:

3.8GHz Q6600
BFG 8800GT 
2GB DDR3 1066MHz

edit forgot to mention that i have everything on high. 1600x1200 res

---

### Post by gsrcrxsi on 2008-08-06
up

---

### Post by gsrcrxsi on 2008-08-07
no matter what i do i get the same FPS. what is going on here? whether i run it at 800x600 or 1600x1200, same results. low vs high settings, same fps. why is it running so slow? ive forced dxlevel -70. nothing. ive run with WINEDEBUG="-all" nothing. ive run with nice -n 20. nothing. 

is anyone with 8.04 playing CS:S with good frames?

---

### Post by YokoZar on 2008-08-08
> **gsrcrxsi said:**
> heres the thing and its probably my fault if it says no. i used to have a 7300GT and proprietary drivers installed, and i recently bought a 8800GT. when i installed the 8800GT, everything seemed fine and i never installed any new drivers. so maybe thats it. Good drivers for the 8x NVidia series weren't available for Hardy around release time.  However, they are being tested for a stable release update.  You can test them out now by enabling the -proposed repository in Synaptic (settings->repositories)

---

### Post by gsrcrxsi on 2008-08-08
sorry, youre behind a little. im way past that now. i wiped the system and did a fresh install. ive also installed the drivers from nvidia directly. im running the 177.13 drivers. CS:S runs fine, the fps are just low. it stays in the 30-40 range, which is really low. unless im just standing there spinning, then it skyrockets, but normal gameplay is low. is anyone getting good frames in hardy?

---

### Post by AFarris01 on 2008-08-08
Whenever i play CSS on my install, i usually get around 60-70 FPS depending on the map.  what map are you playing on?

---

### Post by gsrcrxsi on 2008-08-08
what hardware are you running? and what drivers? and what version of wine?

im mostly playing the cs_office map.

---

### Post by gsrcrxsi on 2008-08-09
up

---

### Post by gsrcrxsi on 2008-08-10
are there any tweaks or anything to get this game running optimally?

---

### Post by gsrcrxsi on 2008-08-12
heres the terminal output. theres gotta be someone out there with the game getting good FPS...

```

icrum@MythTVBackend:~$ WINEDEBUG="fixme-all" wine "c:/program files/steam/steam.exe" 
CellID: Fetching server list from CSDS. . .
CellID: CSDS returned 168 servers.
CellID: Connecting to 194.124.229.12:27031. . .
CellID: Connect to 194.124.229.12:27031 took 115 MS
CellID: Nothing beat our old best time of 16 MS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1600x1200x32 @60! (XRandR)
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
err:mshtml:set_profile SetCurrentProfile failed: 80520015
CellID: Connecting to 194.124.229.15:27031. . .
CellID: Connect to 194.124.229.15:27031 took 112 MS
CellID: Nothing beat our old best time of 16 MS
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
CellID: Connecting to 58.120.225.167:27031. . .
CellID: Connect to 58.120.225.167:27031 took 228 MS
CellID: Nothing beat our old best time of 16 MS
CellID: Connecting to 193.34.50.5:27031. . .
CellID: Connect to 193.34.50.5:27031 took 104 MS
CellID: Nothing beat our old best time of 16 MS
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
CellID: Connecting to 193.34.50.3:27031. . .
CellID: Connect to 193.34.50.3:27031 took 103 MS
CellID: Nothing beat our old best time of 16 MS
CellID: Connecting to 210.208.88.58:27031. . .
CellID: Connect to 210.208.88.58:27031 took 222 MS
CellID: Nothing beat our old best time of 16 MS
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
CellID: Connecting to 87.248.196.116:27031. . .
CellID: Connect to 87.248.196.116:27031 took 109 MS
CellID: Nothing beat our old best time of 16 MS
CellID: Connecting to 79.141.162.3:27031. . .
CellID: Connect to 79.141.162.3:27031 took 94 MS
CellID: Nothing beat our old best time of 16 MS
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
CellID: Connecting to 69.28.181.178:27031. . .
CellID: Connect to 69.28.181.178:27031 took 101 MS
CellID: Nothing beat our old best time of 16 MS
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
CellID: Connecting to 203.77.185.5:27031. . .
CellID: Connect to 203.77.185.5:27031 took 190 MS
CellID: Nothing beat our old best time of 16 MS
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
CellID: Connecting to 69.28.153.86:27031. . .
CellID: Connect to 69.28.153.86:27031 took 28 MS
CellID: Nothing beat our old best time of 16 MS

```

---

### Post by AFarris01 on 2008-08-13
My favs are de_dust and rats maps... and ive usually been getting 60-70fps on those maps.  i tried office a little while ago, and i was getting around 58 fps average.  I play with resolution 1152*864, most everything else set to defaults, water set to reflect all.  the kicker for me might be that in wine, i set in the graphics tab to disable pixel shaders (the little checkbox under the dropdown menu that i cant remember what it does right now) because on my install, if i left the pixel shaders enabled, the game would crash and i was having some really REALLY wierd graphical issues.  the only down side is that with pixel shaders disabled, some objects (such as buckets, boxes, cans, door frames, etc) look a little over-bright sometimes, usually in the shade.
maybe thats whats giving me my fps boost?

---

### Post by Luf on 2008-08-13
Are you just worried about your FPS#s, or are you actually experiencing slowness?

If it spikes when you move/turn, it could be an issue with accessing the files (I had that once). I know CS:S has a lot of problems with fragmented cache. On a Win System, I had to install GCFScape to defrag the cache-files. Not sure if this is your problem and if you could do the same.

This was on a system with the same setup as you +2 more GB of RAM & a 8800GTX.

---

### Post by gsrcrxsi on 2008-08-13
ive run the game at 800x600 and it made absolutley no difference in FPS. i do occasionally experience some studder, but its rare. is it possible that the game is incorrectly reading the FPS to me? 

ill try the pixel shader thing.

when i first installed the game it told me that i needed to defrag my HDD before playing. i said ok, it did its thing and it hasnt asked me since.

---

### Post by Luf on 2008-08-14
If it's just the numbers you're worried about, I would ignore it. The eyes are only capable of seeing a certain amount of frames per second, and you can only display as many as your monitor allows. On my Vista installation, CS:S reads @ 200+ FPS, but I don't see a difference from when I capped it to 75. I typically don't worry about FPS, just how well the game performs.

---

### Post by gsrcrxsi on 2008-08-15
well basically it makes me worried about other games. more intensive games. if FPS are low in CS:S imagine how bad it would be in COD4 or crysis, or any other game of similar graphics needs. 

thats why i want to fix it.

---

### Post by aoanla on 2008-08-15
> **gsrcrxsi said:**
> well basically it makes me worried about other games. more intensive games. if FPS are low in CS:S imagine how bad it would be in COD4 or crysis, or any other game of similar graphics needs. 

thats why i want to fix it.

Yees, but Crysis doesn't run at all in Wine at present (or, at least, it didn't last time I checked), for example.
Plus, different game engines interact with Wine differently - the ones with native OpenGL renderers, for example, usually suffer almost no FPS loss compared to Windows (indeed, some have been known to do better in Wine). 
The Source Engine has appears to be mostly okay, but it is incredibly slow in DX9 mode in Wine. 

So, what I'm saying is: it's very hard to generalise from one example and one game engine.

---

### Post by gsrcrxsi on 2008-08-27
i tried the same settings on a windows install, and im getting 300 FPS. something isnt right. 

why is it so slow? has ANYONE gotten comparable frames between windows and linux? what did you do?

---

