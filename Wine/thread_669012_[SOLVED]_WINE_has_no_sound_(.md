---
title: "[SOLVED] WINE has no sound :("
date: 2008-01-16
forum: Wine
---

### Post by Syndacate on 2008-01-16
Any ideas?

It's really weird - if I open up an APP like a keygen (not that I use them, I have legit versions of everything installed, simply that they are apps with onboard music (no linked libraries with DLL's and such)) "**wine keygen.exe**" or whatever it'll open the app - and the music will play fine.

I installed Diablo II and Max Payne (original) - both with the latest patches, they both installed with no problems, both run with no problems - **NEITHER HAS ANY SOUND**

Slight problem if you actually wanna game ;).

I'm using no-cd loaders on both because according to write-ups I've read - that's how you have to do it - Diablo II works fine with or without the thing, but that's simply a loader, it doesn't replace the executable - so it's not like "**THAT'S THE CAUSE!!**" - it simply isn't.

I ran Max Payne through the terminal and I got the code below, not sure if it has anything to do with why the sound doesn't work...

```

syndacate@syndacate:~/.wine/drive_c/Program Files/Max Payne$ wine /media/cdrom0/Install.exe
syndacate@syndacate:~/.wine/drive_c/Program Files/Max Payne$ fixme:win:EnumDisplayDevicesW ((null),0,0x34eee8,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadTexture (0x15cd8f0) Operation not supported for scratch textures
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadTexture (0x33d1848) Operation not supported for scratch textures
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadTexture (0x1e38790) Operation not supported for scratch textures
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0xbe12e0) : stub
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadTexture (0x3321930) Operation not supported for scratch textures
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0xbe12e0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0xbe12e0) : stub

```

If I type "**winecfg**" then click on the **audio** tab - I get this error message:

```

syndacate@syndacate:~/.wine/drive_c/Program Files/Max Payne$ winecfg
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
Usage:program_name [address][:port]ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
syndacate@syndacate:~/.wine/drive_c/Program Files/Max Payne$    

```

The audio tab still opens up though.

The "audio test" fails - and I can't load the "control panel" either.

I'm using my onboard sound card (Intel ICH5 (Alsa Mixer)).

I also have an SB Live! that I pulled out while trouble shooting this audio problem (I was thinking maybe it was getting confused or something).

Anybody have any ideas?

I guess I'll try putting the SB Live! back in and see if I can get these sound tests to work tomorrow - it would make sense that the audio test failing in the winecfg and no sound in game are related.

**Note what I said at the top though - if I open an application that has sound (no linked libraries) the sound works fine.**

---

### Post by ahaslam on 2008-01-16
What version of Wine are you using? Has it been upgraded recently?

On older versions of Wine neither the 'test sound' or 'control panel' buttons work, the later is still not implemented. 

I recommend that you get the latest Wine release from [budgetdedicated]("http://wine.budgetdedicated.com/archive/index.html"), install it, then issue:
```
wineprefixcreate
winecfg
```
Now go to the audio tab and select alsa, full hardware acceleration, driver emulation & 44100Hz @ 16 bits/sample. If that doesn't work, try oss & experiment with the options.

Your MaxPayne output is not complaining about the sound. I recommend that you experiment with the [pbuffer/fbo]("http://wiki.winehq.org/UsefulRegistryKeys") rendering modes. Though I guess there's no real issue there?

PS. The Wine AppDB entry for Diablo II clearly states: 
> Do not use any modified game executables

;)

---

### Post by Syndacate on 2008-01-16
> **ahaslam said:**
> What version of Wine are you using? Has it been upgraded recently?
wine-0.9.46 - I installed this OS recently, so I'm not sure if it was upgraded recently.

> **ahaslam said:**
> On older versions of Wine neither the 'test sound' or 'control panel' buttons work, the later is still not implemented.

I recommend that you get the latest Wine release from [budgetdedicated]("http://wine.budgetdedicated.com/archive/index.html"), install it,

Can I upgrade through the repositories?

> **ahaslam said:**
>  then issue:
```
wineprefixcreate
winecfg
```
Now go to the audio tab and select alsa, full hardware acceleration, driver emulation & 44100Hz @ 16 bits/sample. If that doesn't work, try oss & experiment with the options.

wineprefixcreate? -- what's that do?

> **ahaslam said:**
> Your MaxPayne output is not complaining about the sound. I recommend that you experiment with the [pbuffer/fbo]("http://wiki.winehq.org/UsefulRegistryKeys") rendering modes. Though I guess there's no real issue there?

I'll check it out when I get back from class in a few hours.

> **ahaslam said:**
> PS. The Wine AppDB entry for Diablo II clearly states:: 
It's a loader - it doesn't replace the executables.  It was also listed on quite a few install how-tos with WINE due to the copy right protection not working well with WINE.


;)[/QUOTE]

---

### Post by Meow27 on 2008-01-16
try upgrading it

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

use the gutsy ones

and the one at the top (in order also depending if you are 32 or 64 bit)

---

### Post by ahaslam on 2008-01-16
> Can I upgrade through the repositories?
Yes (see above), but for a modern version the link I posted is the easiest way. It also gives you more control & avoids future upgrade issues.
> wineprefixcreate? -- what's that do?
It makes sure ~/.wine is modern & complete. This won't hose your old settings, but will fix problems if you've upgraded from an older version of Wine.

I appreciate your stance on the loader but problems have been reported, just have a look at the Wine AppDB page. I'll not bug you on it again ;)

BTW. I know v0.9.53 is out now but I'd try 0.9.50. It's a good upgrade for you & I personally think it's their best effort to date.

Just try it ;)

---

### Post by Syndacate on 2008-01-16
> **ahaslam said:**
> Yes (see above), but for a modern version the link I posted is the easiest way. It also gives you more control & avoids future upgrade issues.

It makes sure ~/.wine is modern & complete. This won't hose your old settings, but will fix problems if you've upgraded from an older version of Wine.

I appreciate your stance on the loader but problems have been reported, just have a look at the Wine AppDB page. I'll not bug you on it again ;)

BTW. I know v0.9.53 is out now but I'd try 0.9.50. It's a good upgrade for you & I personally think it's their best effort to date.

Just try it ;)

I used .53 simply because that's what the repository updated - I'm not very linux savvy, so it's a lot easier just to type a few lines of code and update it from the repositories than it is to mess with downloading/installing files manually.  If I have some weird problems I'll have to revert to .50 I suppose - but from what I hear wine is pretty good at keeping stability up to date.

Just to set the record straight on the D2 loader - I **DON'T HAVE** the original disks - I bought the D2 version of the battlechest (came with D1, D2, and D2LOD) a long, long, time ago.  Somewhere in moving up to college I lost a bunch of software discs, but the stuff is still installed on my laptop (I'm on my desktop).  Now the stuff on the laptop was installed with the original keys, because I had my disks when I installed it there.  So I didn't have the disks and I didn't have my keys - but I had my laptop.  So I downloaded images of the CD's (which technically isn't illegal as I do own real versions of the CD's...they're just...around) and then used a CD-Key **GRABBER** on my laptop to pull my keys out of the D2 installation on my laptop.

So I installed D2 **HERE** with images - **but** I used my original CD-Keys.

Now I tried it there way (appDb) and it simply didn't work worth of **** - it kept bugging me about some .mpq files which I didn't have or some **** and nobody knew anything about it (including google for the most part).  So I started googling how-to installs for it and at least 75% of them told you to use a loader if you don't have the original disks, and they all pointed to the same damn loader, which is D2Loader-1.11b.exe - it doesn't replace the executable - it just works.

I feel no need to buy an entire new D2 setup because I don't have the original disks and "*using loaders is bad*."  I simply don't have money to throw away like that.  I have my keys which I purchased, and I don't have the CD's - and of course those CD's don't copy worth of damn (from past experience copies of D2LOD CD's **DON'T** work, even if you're just using it as a "play" disk and it was installed using the original), so I did what I did and it would work fine disregarding this sound issue, which obviously isn't related as it's happening with all installs that have no keys and the original CD is in.

In any event...

I typed **wineprefixcreate** and got a nice assortment of error messages - this is right after I added the repository and downloaded it that way, it should be fine :(.

```

syndacate@syndacate:~$ wineprefixcreate
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
fixme:ntoskrnl:KeInitializeSpinLock 0x4677a4
fixme:spoolsv:serv_main (0 (nil))
Could not load Mozilla. HTML rendering will be disabled.
/home/syndacate/.wine updated successfully.
syndacate@syndacate:~$    

```

[QUOTE=ahaslam]Now go to the audio tab and select alsa, full hardware acceleration, driver emulation & 44100Hz @ 16 bits/sample. If that doesn't work, try oss & experiment with the options.[/quote]

Wow, my friend swore up and down that I should use OSS instead of ALSA, and combinations of OSS and ALSA didn't work.

Switched to only ALSA, started D2 (with my loader :-P) and it worked 100% - then I played through the first level of max payne - full sound - asside from a little lag on ultra-fast spins (I think my vid card can't handle 1280x1024 in that game, it's a piece of crap AGP 512mb nvidia that cost like 140 new, but I picked it up for free, not my first choice - but my other one had a bad GPU, and this was free) it worked 100%, sound, video, etc.  Some of the F keys (shortcut keys in game) don't work due to bindings elsewhere, but everything else is peachy.

Thanks, can't believe it was something so simple, but then again, before I updated it spewed all that crap when I started the game - now it spews a whole **** load of NEW crap, but works fine:

```

1b.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x34f0f8,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:ntdll:NtQueryInformationToken Unhandled Token Information class 11!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_Release (0x15a550) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x48aac70 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x48aab50 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x25d6170 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x25d6050 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x48aaa30 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x48aa910 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x19ade8 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x19acc8 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x25d7670 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x24c9688 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x19aba8 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x159258 with type 1,WINED3DRTYPE_SURFACE
err:d3d:IWineD3DDeviceImpl_Release Context array not freed!
wine: Unhandled page fault on read access to 0x04ae0048 at address 0x6f9b9859 (thread 0040), starting debugger...
Unhandled exception: page fault on read access to 0x04ae0048 in 32-bit code (0x6f9b9859).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6f9b9859 ESP:7d3ab9d4 EBP:00000000 EFLAGS:00210206(   - 00      - RIP1)
 EAX:04ae0000 EBX:04ae0000 ECX:7ee36e80 EDX:7ee36e84
 ESI:04ae0000 EDI:0001ffff
Stack dump:
0x7d3ab9d4:  6f9b9800 00000000 7d3aba08 7bc85434
0x7d3ab9e4:  000014b0 00000000 00000000 00e0fb60
0x7d3ab9f4:  000abb24 00001668 7bc676f6 00000000
0x7d3aba04:  6f9b9800 7d3abab8 7bc684fc 6f9b9800
0x7d3aba14:  00000000 7bca0720 b7de0419 10012a03
0x7d3aba24:  00000000 b7dd2140 7c1982d8 00000000
Backtrace:
=>1 0x6f9b9859 in d2sound (+0x9859) (0x00000000)
0x6f9b9859: cmpl        %ebp,0x48(%eax)
Modules:
Module  Address                 Debug info      Name (131 modules)
PE        400000-  40b038       Deferred        game
PE        640000-  654000       Deferred        d2lang
PE        aa0000-  aad000       Deferred        d2net
PE        bc0000-  ce2000       Deferred        d2game
PE       1f30000- 1f71000       Deferred        binkw32
PE      10000000-1001a000       Deferred        smackw32
PE      60000000-6002e000       Deferred        ijl11
PE      6f880000-6f8b6000       Deferred        d2direct3d
PE      6f8e0000-6f9ae000       Deferred        d2win
PE      6f9b0000-6f9c9000       Export          d2sound
PE      6f9d0000-6fa0f000       Deferred        d2multi
PE      6fa20000-6fa34000       Deferred        d2mcpclient
PE      6fa40000-6fa6d000       Deferred        d2launch
PE      6fa80000-6faa1000       Deferred        d2gfx
PE      6fab0000-6fbe5000       Deferred        d2client
PE      6fbf0000-6fc50000       Deferred        storm
PE      6fd50000-6fdf9000       Deferred        d2common
PE      6fe10000-6ff17000       Deferred        d2cmp
PE      6ff20000-6ff42000       Deferred        bnclient
PE      6ff50000-6ffac000       Deferred        fog
ELF     7b800000-7b925000       Deferred        kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c6b1000-7c7a0000       Deferred        wined3d<elf>
  \-PE  7c6c0000-7c7a0000       \               wined3d
ELF     7c7a0000-7c7f4000       Deferred        ddraw<elf>
  \-PE  7c7b0000-7c7f4000       \               ddraw
ELF     7ca16000-7ca2b000       Deferred        psapi<elf>
  \-PE  7ca20000-7ca2b000       \               psapi
ELF     7ca2b000-7ca73000       Deferred        dbghelp<elf>
  \-PE  7ca30000-7ca73000       \               dbghelp
ELF     7ca73000-7ca8a000       Deferred        imagehlp<elf>
  \-PE  7ca80000-7ca8a000       \               imagehlp
ELF     7cb9b000-7cbc1000       Deferred        msacm32<elf>
  \-PE  7cba0000-7cbc1000       \               msacm32
ELF     7cbc1000-7cbd9000       Deferred        msacm32<elf>
  \-PE  7cbd0000-7cbd9000       \               msacm32
ELF     7cbd9000-7cc9f000       Deferred        libasound.so.2
ELF     7cc9f000-7ccd4000       Deferred        winealsa<elf>
  \-PE  7ccb0000-7ccd4000       \               winealsa
ELF     7ccd4000-7cd1e000       Deferred        dsound<elf>
  \-PE  7cce0000-7cd1e000       \               dsound
ELF     7cd1e000-7cdaa000       Deferred        winmm<elf>
  \-PE  7cd30000-7cdaa000       \               winmm
ELF     7cdaa000-7cdd5000       Deferred        ws2_32<elf>
  \-PE  7cdb0000-7cdd5000       \               ws2_32
ELF     7cdd5000-7cdef000       Deferred        wsock32<elf>
  \-PE  7cde0000-7cdef000       \               wsock32
ELF     7cdef000-7ce40000       Deferred        libgcrypt.so.11
ELF     7ce40000-7ce50000       Deferred        libtasn1.so.3
ELF     7ce50000-7ce58000       Deferred        libkrb5support.so.0
ELF     7ce58000-7ce86000       Deferred        libcrypt.so.1
ELF     7ce86000-7cef6000       Deferred        libgnutls.so.13
ELF     7cef6000-7cf1b000       Deferred        libk5crypto.so.3
ELF     7cf1b000-7cfa3000       Deferred        libkrb5.so.3
ELF     7cfa3000-7cfcc000       Deferred        libgssapi_krb5.so.2
ELF     7cfcc000-7d001000       Deferred        libcups.so.2
ELF     7d025000-7d038000       Deferred        libresolv.so.2
ELF     7d038000-7d04d000       Deferred        midimap<elf>
  \-PE  7d040000-7d04d000       \               midimap
ELF     7d04d000-7d06c000       Deferred        iphlpapi<elf>
  \-PE  7d050000-7d06c000       \               iphlpapi
ELF     7d06c000-7d0ca000       Deferred        rpcrt4<elf>
  \-PE  7d080000-7d0ca000       \               rpcrt4
ELF     7d0ca000-7d169000       Deferred        ole32<elf>
  \-PE  7d0e0000-7d169000       \               ole32
ELF     7d3e1000-7d3e5000       Deferred        libgpg-error.so.0
ELF     7d3f5000-7d427000       Deferred        uxtheme<elf>
  \-PE  7d400000-7d427000       \               uxtheme
ELF     7d427000-7d430000       Deferred        libxcursor.so.1
ELF     7d430000-7d44d000       Deferred        imm32<elf>
  \-PE  7d440000-7d44d000       \               imm32
ELF     7d44d000-7d452000       Deferred        libxfixes.so.3
ELF     7d452000-7d455000       Deferred        libxcomposite.so.1
ELF     7d455000-7d45d000       Deferred        libxrender.so.1
ELF     7d45d000-7d460000       Deferred        libcom_err.so.2
ELF     7d720000-7d72b000       Deferred        libgcc_s.so.1
ELF     7d856000-7d85c000       Deferred        libnss_dns.so.2
ELF     7d85c000-7d85f000       Deferred        libnss_mdns4_minimal.so.2
ELF     7da58000-7da5a000       Deferred        libnvidia-tls.so.1
ELF     7da5a000-7e50d000       Deferred        libglcore.so.1
ELF     7e50d000-7e5b1000       Deferred        libgl.so.1
ELF     7e5b1000-7e5b6000       Deferred        libxdmcp.so.6
ELF     7e5b6000-7e5b9000       Deferred        libxau.so.6
ELF     7e5b9000-7e6aa000       Deferred        libx11.so.6
ELF     7e6aa000-7e6b8000       Deferred        libxext.so.6
ELF     7e6b8000-7e6bd000       Deferred        libxxf86vm.so.1
ELF     7e6bd000-7e6d5000       Deferred        libice.so.6
ELF     7e6d5000-7e6dd000       Deferred        libsm.so.6
ELF     7e6dd000-7e6df000       Deferred        libkeyutils.so.1
ELF     7e6df000-7e6e5000       Deferred        libxrandr.so.2
ELF     7e6f2000-7e77c000       Deferred        winex11<elf>
  \-PE  7e700000-7e77c000       \               winex11
ELF     7e7f4000-7e814000       Deferred        libexpat.so.1
ELF     7e814000-7e83f000       Deferred        libfontconfig.so.1
ELF     7e83f000-7e854000       Deferred        libz.so.1
ELF     7e854000-7e8c4000       Deferred        libfreetype.so.6
ELF     7e8d9000-7e93e000       Deferred        msvcrt<elf>
  \-PE  7e8f0000-7e93e000       \               msvcrt
ELF     7e93e000-7e952000       Deferred        lz32<elf>
  \-PE  7e940000-7e952000       \               lz32
ELF     7e952000-7e96b000       Deferred        version<elf>
  \-PE  7e960000-7e96b000       \               version
ELF     7e96b000-7e9a0000       Deferred        winspool<elf>
  \-PE  7e970000-7e9a0000       \               winspool
ELF     7e9a0000-7ea5f000       Deferred        comctl32<elf>
  \-PE  7e9b0000-7ea5f000       \               comctl32
ELF     7ea5f000-7eab6000       Deferred        shlwapi<elf>
  \-PE  7ea70000-7eab6000       \               shlwapi
ELF     7eab6000-7ebba000       Deferred        shell32<elf>
  \-PE  7ead0000-7ebba000       \               shell32
ELF     7ebba000-7ec5a000       Deferred        comdlg32<elf>
  \-PE  7ebc0000-7ec5a000       \               comdlg32
ELF     7ec5a000-7eca3000       Deferred        advapi32<elf>
  \-PE  7ec70000-7eca3000       \               advapi32
ELF     7eca3000-7ed3a000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed3a000       \               gdi32
ELF     7ed3a000-7ee71000       Deferred        user32<elf>
  \-PE  7ed50000-7ee71000       \               user32
ELF     7ef90000-7ef9b000       Deferred        libnss_files.so.2
ELF     7ef9b000-7efa5000       Deferred        libnss_nis.so.2
ELF     7efa5000-7efbd000       Deferred        libnsl.so.1
ELF     7efbd000-7efc6000       Deferred        libnss_compat.so.2
ELF     7efc6000-7efeb000       Deferred        libm.so.6
ELF     b7c87000-b7c8b000       Deferred        libdl.so.2
ELF     b7c8b000-b7dd5000       Deferred        libc.so.6
ELF     b7dd6000-b7dee000       Deferred        libpthread.so.0
ELF     b7e03000-b7f17000       Deferred        libwine.so.1
ELF     b7f19000-b7f35000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000002e (D) C:\Program Files\Diablo II\Game.exe
        00000040    0 <==
        00000026    1
        0000003a    0
        00000034    0
        0000002f    0
0000001a
        0000001e    0
        0000001b    0
00000018
        00000019    0
00000010
        00000013    0
        00000012    0
        00000011    0
0000000c
        0000000f    0
        0000000e    0
        0000000d    0
0000000a
        0000000b    0
Backtrace:
=>1 0x6f9b9859 in d2sound (+0x9859) (0x00000000)
syndacate@syndacate:~$        

```

Heh, so long that the konsole ran out of room and truncated the first line of the initial start command.  Seems to be some errors in there - but everything runs fine so *shrugs*.

EDIT:
Summarized:
- So what does that code mean when I type **wineprefixcreate**?
- last time I'm listening to my friend about wine, he doesn't game so it's not like he uses wine much (grrrr)
- As far as the installation goes, I had all sorts of problems installing D2, (**I couldn't patch it manually because it caused an .mpq error**) granted it was probably because I was installing with images, but whatever - what I ended up doing was removing everything 'cept the reg keys, then installing it (with no patches or anything), then going onto my laptop, and manually updating using blizzard's 1.11b patch, and installing it (successful), then I copied everything from the directory in the program files directory onto a thumb drive and put it on my computer here, and just dumped everything into the .wine/Program Files/Diablo II folder - replacing all - then it worked fine (the loader) - still failed under regular process - D2 has some kind of crap where you can't use copied disks and you can't use images to play it - it'll load the "start" menu (with the play and uninstall options on it, the splash screen) but it will keep prompting you for the disk, I can't recall if I used a loader or D-Toolz on my laptop, I think I D-Toolz worked fine - but as far as I can remember, that's the only time I had an image that would start - disks act funny with D2 - I've never seen them act that way with any other game.

Max Payne installed flawlessly - Now I'm going to attempt to install StarCraft (no disks...again) and everything SHOULD go smooth - BW doesn't have the same problems with images and burnt disks as D2 does.

---

### Post by ahaslam on 2008-01-16
> So what does that code mean when I type wineprefixcreate? Not a lot really, all that matters is the last line. Just like the MaxPayne output, it's the result that's important. Btw, if you launch it with *'WINEDEBUG=-all wine whatever.exe'* it'll skip all that crap & gain 1 or 2 fps ;)

---

### Post by Syndacate on 2008-01-16
> **ahaslam said:**
> Not a lot really, all that matters is the last line. Just like the MaxPayne output, it's the result that's important. Btw, if you launch it with *'WINEDEBUG=-all wine whatever.exe'* it'll skip all that crap & gain 1 or 2 fps ;)

So I type "**WINEDEBUG=-all wine program.exe**" ??

And it'll GAIN FPS?

That's only text though?

Wow, just tried it and it smoothed out where it was glitchy - thanks.

So in allllllllllllll of that code - everything is fine?

---

### Post by ahaslam on 2008-01-17
> **Syndacate said:**
> So in allllllllllllll of that code - everything is fine?
Pretty much, as long as it's stable. It's just not perfect, though for mere mortals it's fine. 

I mentioned some useful registry keys earlier, you may want to check into those, there's still more to be gained. Additional video memory allocation & different rendering modes often help.

---

### Post by Syndacate on 2008-01-17
> **ahaslam said:**
> Pretty much, as long as it's stable. It's just not perfect, though for mere mortals it's fine. 

I mentioned some useful registry keys earlier, you may want to check into those, there's still more to be gained. Additional video memory allocation & different rendering modes often help.

Alright, Thx!

---

### Post by richrosa on 2008-03-01
I read this post, and wasn't sure what the correct solution was, however running
wineprefixcreate solved my similar problem.

---

### Post by zbluebird on 2011-02-05
i also have the similar problem when playing angry birds =\

i have wine 1.2.2 and tried running the command "**wineprefixcreate**"

but it gives the error

[I]The program 'wineprefixcreate' is currently not installed.  You can install it by typing:
sudo apt-get install wine1.0
[/I]

any tips on how to get a workaround for this one?

Thanks in advance :)

---

### Post by zbluebird on 2011-02-05
for some unknown reason, it plays now with sound :)

happened when I turned my system again and tried the game... all works fine now :)

---

