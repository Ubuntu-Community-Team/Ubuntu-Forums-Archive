---
title: "DAOC in Wine"
date: 2007-03-28
forum: Wine
---

### Post by Flubs4u on 2007-03-28
I'm wanting to play some Dark Age of Camelot for old times sake, but I can't find anything on the boards about how it works in the newest version of wine.  Winehq reports that it works well under the latest version, but I was wondering if anyone could confirm this with personal experience before I go through the process of dredging out my old disks (all 8 of them :-/) and trying the install myself.

Thanks,
Flubs

---

### Post by Snowmayne on 2007-05-04
<sigh> still haven't made that leap myself yet. Most of what I've read so far hasn't been that promising, but I'll probably give it a try again this week-end.

---

### Post by JusticeZero on 2007-08-24
I've heard that the CD install method is broken..

Has anyone found a way to run them? I see lots of reports of how it runs reasonably well, but no information on how to make it run in the first place.

---

### Post by cogadh on 2007-08-24
> **Flubs4u said:**
>  Winehq reports that it works well under the latest version, but I was wondering if anyone could confirm this with personal experience...
Have you checked Wine's AppDB entry for the game? All of the testing reported there is personal experience:
[http://appdb.winehq.org/appview.php?iAppId=443](http://appdb.winehq.org/appview.php?iAppId=443)
The base version doesn't have any ratings at all, but the expansions packs have very good ratings.

---

### Post by JusticeZero on 2007-08-24
I dunno, i'm dubious whether anything with a '1.2MB/second memory leak' can be said to be highly playable.

---

### Post by cogadh on 2007-08-24
That leak existed 20 minor revisions ago in Wine and was most likely due to the Nvidia driver that was being used at the time. Considering the number of improvements in Wine and the Nvidia driver since then, I'd say it is worth trying it again.

---

### Post by JusticeZero on 2007-10-20
Currently running DAoC, Labyrinth client, in WINE, with the latest WINE version and in 7.10. It worked perfectly with one version back of WINE in 7.04.
However, the cursor flickers.. in 7.04 this meant the cursor was hard to see. Now it's more or less invisible, on rare occasions it flickers for an instant but is usually absent, where before it was visible maybe 50% of the time.
I found a patch at [http://comptune.com/forums/viewtopic.php?t=253](http://comptune.com/forums/viewtopic.php?t=253) that claims to be able to correct it, but I do not know how to "copy it to your wine folder" - it gives me permission denied that I don't know how to get past, so i'm stuck on that step.

---

### Post by cogadh on 2007-10-20
That patch was for Wine 0.9.24 compiled from source, not the current version of Wine installed through a precompiled package. You might try downloading the Wine source and applying the patch to it, but considering the current Wine is more than 20 revisions newer than the version the patch was designed for, it might just break things instead of fixing them. Not to mention you'll have to deal with the hassle of compiling it and not being able to update using Wine packages anymore.

---

### Post by mnml on 2007-11-02
I tried but i get that error?
anyone know what i can do to fix it?
> 
fixme:keyboard:X11DRV_GetKeyNameText (00090000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (00540000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (00550000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (00590000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (005a0000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (005b0000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (005c0000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (005d0000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (005e0000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (005f0000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (00610000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (00620000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:keyboard:X11DRV_GetKeyNameText (00630000,0x33f62c,256): unsupported key, vkey=0000, ansi=0000fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 93 (SPI_SETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
Wine failed with return code 1



---

### Post by mnml on 2007-11-04
I have upgraded my wine and I only get this errors now:

> 
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 93 (SPI_SETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
Wine failed with return code 1


any solutions?

---

### Post by cogadh on 2007-11-04
The "fixme" messages are just notes made by the developers to indicate when a function is either not implemented or incomplete. Generally speaking, you can't do anything about them until Wine completes or implements that particular function in a newer version. 

I don't really know what that "Wine failed with return code 1" means, but every time I have seen it, it seems to just mean "Wine didn't work".

---

### Post by mnml on 2007-11-04
thank you for the explaination :)

---

### Post by JusticeZero on 2007-11-06
In my, admittedly limited, experience, DAoC does not run in the latest version of WINE, but it works in 0.9.47 just fine. The mouse pointer, however, is invisible.
This is a major improvement over Cedega, in which it runs perfectly for a few minutes, then locks the entire computer up.
I'm told that that must be a driver issue since after all,  it couldn't possibly be the great messiah Cedega not working right [-( but I don't see any indication of a problem anywhere else, and i've tried all the 'usual suspects' measures I can think of. No-one has responded to me so far when I ask around trying to figure it out.

---

### Post by JLAudioFan on 2007-11-09
I have gotten catacombs working, however it runs pretty slow (ihave an intel centrino duo core, 1gb ram) and the  mouse cursor does not show up.  

also, whatever you do... DO NOT, i repeat DO NOT try to select the windowed mode from the char select screen.  I did this and daoc will crap on you.  You will only be able to use the quick select menu to log on, and if you /quit it drops to char select screen which is all messed up.

So, it does run, but it's not really playable unless you are solo and moving really slow ;)

I did try the "patch" but it couldnt find a file, so still no mouse cursor.

I am going to install windows in vmware and then try to install daoc and play it.  I'll reply here if that works well for me.

---

### Post by cogadh on 2007-11-09
It won't work, VMware can't do 3D gaming. It only does basic VGA and VESA emulation, not accelerated graphics.

---

### Post by JLAudioFan on 2007-11-10
ah, i forgot about that...

back to a dual boot setup then...

thanks for reminding me cogadh!

---

### Post by darkpck on 2008-06-30
I can start it, but it can't connect to the update server. This is what I get:

> 
pck@pck-desktop:/mnt/sdb1/Mythic/Catacombs$ wine camelot.exe
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on C-Media USB Headphone Set  , disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
philip@philip-desktop:/mnt/sdb1/Mythic/Catacombs$ err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on C-Media USB Headphone Set  , disabling mixer
fixme:shdocvw:PersistStorage_InitNew (0x7f029d18)->(0x7f5c0ee8)
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:shdocvw:OleObject_Close (0x7f029d18)->(1)


Any ideas?

---

### Post by cogadh on 2008-06-30
Fix those preloader errors:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)
then try running the game again.

---

### Post by veraction on 2008-12-12
I posted this in the other forum, but I guess I'll post here too. DAOC under wine now seems to be very good. I didn't even need to compile from source.

It is pretty straightforward but you need to disable some stuff. See the info here: [http://govtbad.blogspot.com/2008/12/daoc-on-linux-under-wine-ubuntu-810.html](http://govtbad.blogspot.com/2008/12/daoc-on-linux-under-wine-ubuntu-810.html) That link shows some of the issues too (no more mouse issues).

Hopefully some more people come back to play daoc ;) it's much better than those other games ;)

---

### Post by jim2012 on 2012-12-15
Hello, 

I am in slight need of further advice as to how I use the Winecfg to change settings. I am probably missing something basic as to how to do this. 

I have used winetricks to change settings so far but it is not obvious to me when looking at the winecfg. 

Best Regards & thanks

---

