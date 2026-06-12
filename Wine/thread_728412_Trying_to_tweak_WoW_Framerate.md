---
title: "Trying to tweak WoW Framerate"
date: 2008-03-18
forum: Wine
---

### Post by Nythain on 2008-03-18
Ok, So i know this has been asked before a billion times... but im trying to figure out why two people with near identical rigs have completely different framerates, and people with considerably less powerfull rigs have considerably higher framerates and etc.

So what im asking, is not only for an FPS but a general description of your rig...
processor speed
ram amount and speed
anything else you want to brag about

then, what versions of software are you running...
kubuntu, ubuntu, xubuntu
6.04, 6.10, 7.04, 7.10, 8.04
32bit or 64bit
video card and driver version number
wine or cedega and what version

lastly any tweaks...
the registry tweak
video card specific tweaks
windowed or fullscreen
no addons, a trillion addons
directx or opengl mode
video settings... high or low
RESOLUTION???

and ultimate, your average fps

im really curious to hopefully figure all this out... when i get home ill have more details on my system (at work i cant tell what version of wine im runnin)

---

### Post by Trinidado on 2008-03-18
I got it to work right off the bat after the reg tweak. (I followed the guide in these forums)
AMD 64 2000 mhz
1.5 gigs ram

Running ubuntu 7.10 64 bit
ATI 9800 pro 128 meg- forget which driver, and too afraid to play around (don't ask)
wine 9.57

I followed the guide, like previously stated
No video card tweaks
Fullscreen
1 Addon=2.2 megs
not sure if directx or opengl, using default, whatever that is
high video settings
1680x1200 resolution :)
20-25 average fps in cities, 30-35 outside

Hope that helps!

---

### Post by Nythain on 2008-03-19
now that im home, its time for my stats, and you'll see why im very confused by framerate issues

AMD 64 x2 4200+ 2.2ghz
4 GB Dual Channel DDR2 800Mhz
Nvida 8400GS

Kubuntu 7.10 64bit
Wine Version 0.9.57
Nvidia Driver 169.12

Applied Registry Tweak
Fullscreen 1600x1200
OpenGL mode
With Absolutely EVERY Video Effect off or down = 30-40 fps
With All Video Effects up but no specular lighting or full screen glow = 30fps
With All effects down WITH specular lighting and full screen glow = 20fps
With Effects up WITH spec lighting and full screen glow = 15fps

i should be running at 60-100fps with all the settings off/down, and then incrementally lower as i turn things up/on and i would have expected to sit at around 30+ with everything balls to the wall

---

### Post by Nythain on 2008-03-19
<edit>

---

### Post by Scarabomb on 2008-03-19
So what im asking, is not only for an FPS but a general description of your rig...

rig
-(HP Pavillion dv6604nr)

processor speed 
-(AMD Athlon 64x2 TK-55 1.8ghz)

ram amount and speed 
-(2GB RAM [Speed..not sure])
anything else you want to brag about

then, what versions of software are you running...
kubuntu, ubuntu, xubuntu
6.04, 6.10, 7.04, 7.10, 8.04
32bit or 64bit 
-(At the moment, Ubuntu 7.10 x86_64)

video card and driver version number 
-(NVIDIA NeForce Go 7150N <--is that it?)

wine or cedega and what version 
-(Same Version wine as you, I just threw on what apt-get gave me)

lastly any tweaks...

the registry tweak 
-(Registry tweaks but check this out.  What I did after I installed x86_64, instead of using the "Windows Environment" Wine gave me, I just utilized my actual Vista NTFS partition. I threw on the WoW folder from my old laptop [Runs WoW like a champ, best gaming laptop I've found so far...but shitty grafx card support] and was too lazy to move it into Wine's little world)

video card specific tweaks 
-(None that I know of... what I did use though is the script from Winefix [Had to do some weird stuff to install it on 64]```
winefix -n "-21" 'WoW in my Windows Partition'
```
which boost performance substantially

windowed or fullscreen 
-(Windows Mode [So I can access my other programs...and it's a bit faster])

no addons, a trillion addons 
-(Trillions of addons....a lot...)

directx or opengl mode 
-(DirectX with Compiz turned off.... D3d just works better and also makes my mouse very smooth (Like in XP) but the game itself is still meh..)

video settings... high or low 
RESOLUTION??? 
-(1280x800 52refresh 24 bit by 16 (or 24..whatever is the highest))

and ultimate, your average fps 
-(10-17 Outside, 24-27 Inside, 13 PvPing)

I'm sure more tips and fixes will come floating by but as of right now, the game is payable.  I turned terrain distance to super close (having it far crushed my FPS to 3-9) and also most textures I have high but I turned off the lighting thing and ground clutter also the ground clutter radius.  What is at max are spell effects and the Texture thing (so outfits on characters look crisp) as well as the thing that makes the water in the game look real and translucent when standing by the shore.

Edit: Check this out Nythain.  I just downed the nice script to 25...and even got it to 30... also, I just installed Envy and got a new NVIDIA driver... WoW is CLEAN!! Very clean and it works very very nicely.  The FPS Reportst hat it's still under 30 but at this point I don't even care.  I think I have just found a replacement for Windows.  It runs as good as XP did with the exception of the stats and also it's better in Windowed Mode.  All my addons were active and the only thing I really changed was the distance.  I took off the Middle check box at the bottom (something about all screen lighting or something) and kept the top and the bottom on to keep the graphx good and clean.  It's working good AND the display (like I said) is clean.  This laptop that I'm right now is fairly new anyway but at least everything is working how I want it to.

Also, with all this done, I've been able to have WoW open WITH Compiz on so...it's all good =D

---

### Post by Nythain on 2008-03-21
thanks for the info on winefix... looking into it now... still trying to figure out whats different on some machines than others... you are achieving almost the same framerate as me... in fact, if i enable spec lighting, i drop down to your framerate...

about to load windows vista just to see if it handles wow better than wine on this machine, to further figure out whats going on

Oh yeah, and an update
Im now running the beta 171.06 nvidia drivers... and it didnt really impact a thing... still same framerates, and still same inability to handle spec lighting

---

### Post by Nythain on 2008-03-25
you would figure with all the people encountering low framerates in wow through wine, there would have been more input... oh well... im still working away, researching as much as i can... wine just updated the other day, we'll see if the newest version gives any improvement

---

### Post by Resonance378 on 2008-03-25
Built by self

Intel P4 3.0GHz (HT) on Intel 865 Series motherboard
1G PC3200 in 4 x 512 in dual channel mode
ATI 9600XT 128MB in AGP 8X w/ a Zalman copper cooler

Fast Writes are off
Pixel Shaders are off
AA is off
Reg tweak for FPS/Vertex Fix
Glitch Fix
Icon Fix
Model Fix

OpenGL mode: 50-60fps outside 80-120fps inside 40-80fps in Shattrah

D3D mode fps 8-15 no matter where you are.

I just tweak, test, and play for a little bit as I'm looking to get/work on a resolution to the White minimap when indoors when in OpenGL mode on ATI Cat 8.0+

Haven't tested Wine 0.9.58 yet.

---

### Post by Scarabomb on 2008-03-25
Update on me again:

I got the latest Wine and my frame rate is still the same (For whatever reason, I wasn't expecting a change anyway).  Also, the game becomes unplayable if I try and throw it in d3d like I did before. The reason why WoW seemed so "clean" was because of the Hardware cursor but the game still lags behind.  It's a lot better for me to play in OpenGL than with D3d and hardware cursor.

I need to get the latest version of NVIDIA on my VISTA side and check out how well that plays but I've just been too lazy and sorta busy as of late.  On Vista, it played very similarly as Linux does.  64-bit did help a bunch but I dunno if a laptop with NVIDIA card can handle it...or a laptop period (I'm meaning Wine + WoW mind you).

ATI Mobility Radeon x700 plays WoW flawlessly.  To make sure that it wasn't some sort of hardware issue and probably just a grafx issue, I pumped up all of the grafx things on my other laptop and it played just as well..but prettier (obviously).

I'm tempted to try the script with the seperate X-Server as I hear there's no overhead and it's supposed to increase the frame rate by about 15 or so.  I think an increase like that would be very dramatic but like I said about the Vista thing, I would just need to find the time to do it.

---

