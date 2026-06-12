---
title: "Half-Life 2 in  Hardy crash"
date: 2008-03-23
forum: Wine
---

### Post by eythian on 2008-03-23
Until yesterday, I was happily playing HL2 in Gutsy (using the wine versions from winehq). Yesterday, I upgraded to Hardy beta, and now HL2 crashes right before the menu would show (i.e. steam works, HL loads, and then just quits out). My guess (and it's just a guess) is that it's something to do with the 3D graphics, as it's then that they kick in.

Same thing happens with and without compiz running, and I'm using the hardy-provided binary nvidia drivers (nvidia-glx-new).

I am running HL with the command line options '-dxlevel 81 -window'. Nothing conclusive from the console:

```
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xfc30808) : pBox=0x33e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xfc30808) : pBox=0x33e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xfc30808) : pBox=0x33e344 stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13f070) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x24af1908) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x249eb988) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13f070) : stub
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!
```
... and back at the prompt.

Usually crashes show something obvious here, but not this time. Anyone got any suggestions I can try? I'm not addicted to it, so I won't be reverting if I can't make it work soon :) but I did pay for it, so am willing to try what I can, and it would be good to have it fixed before the beta ends so others can benefit.

---

### Post by bsmith on 2008-04-07
Ok, I think I have a solution for you.

1. Run Rhythmbox, and play a sound for a few seconds.

2. Start up steam, and wait for it to load.

3. Use terminal to navigate to your hl2 directory inside steamapps.

4. Launch hl2 with command
```
pasuspender ./hl2.exe -- -dxlevel 81 -window
```

[IMG]http://photos-c.ak.facebook.com/photos-ak-sf2p/v191/211/99/616166403/n616166403_532498_6403.jpg[/IMG]

---

### Post by eythian on 2008-04-07
> **bsmith said:**
> Ok, I think I have a solution for you.Hahah you got that from the wine appdb, didn't you? It was me that posted that there, once I worked it out :) I shoulda posted it here too of course.

Thanks though :)

Now I tend to just shutdown all sound apps, killall pulseaudio, run the game, and when done launch pulseaudio again. It's easier.

---

### Post by bsmith on 2008-04-07
Yep, guilty.

I guess I should be thanking you for getting mine to work :D

Thanks:lolflag:

---

