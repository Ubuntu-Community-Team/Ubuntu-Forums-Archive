---
title: "GTA San Andreas"
date: 2008-11-15
forum: Wine
---

### Post by naniekso2 on 2008-11-15
I installed Gta san andreas using this guide
[http://sudosys.be/?q=GTA_san_andreas_on_ubuntu_8_04_wine#comment-196](http://sudosys.be/?q=GTA_san_andreas_on_ubuntu_8_04_wine#comment-196)
But once I get to step 6 It just comes up with a blue screen and closes after 1 or 2 secon
and sometimes after it closes it says. Soundmanager Initialized.

This is my terminal log:
armaanxamirani@GLOW:~/Documents/gta/gtasa$ WINEDEBUG=-all wine gta_sa.exe
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
armaanxamirani@GLOW:~/Documents/gta/gtasa$ WINEDEBUG=-all wine gta_sa.exe
Initialised SoundManager
armaanxamirani@GLOW:~/Documents/gta/gtasa$ WINEDEBUG=-all wine gta_sa.exe
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
armaanxamirani@GLOW:~/Documents/gta/gtasa$ WINEDEBUG=-all wine gta_sa.exe
Initialised SoundManager
armaanxamirani@GLOW:~/Documents/gta/gtasa$ WINEDBUG=-all wine gta_sa.exe
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:win:EnumDisplayDevicesW ((null),0,0x32f744,0x00000000), stub!
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x12cd40) : stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
Initialised SoundManager
fixme:dsound:IDirectSoundBufferImpl_SetFX (0x364af58,0,(nil),(nil)): stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
armaanxamirani@GLOW:~/Documents/gta/gtasa$

---

### Post by naniekso2 on 2008-11-15
Help I really want to play

---

### Post by hikaricore on 2008-11-15
You're provided no information about your system how do you expect anyone to help?

I'd guess this was a graphic issue, but I don't really have much to go on there.

---

### Post by Bubu5 on 2008-12-03
k

---

### Post by Saytr on 2008-12-03
> **Bubu5 said:**
> I want run GTA San Andreas in Ubuntu 8.10 with wine, but if i run GTA San Andreas the screen to flicker/the screen is flashes.
I downloaded the GTA San Andreas RIP from the internet illegaly.
(Sorry if it's baffling, but I'm from Hungary, and I can not speak english well...)

Do not download ripped versions of games to Wine. They will screw Wine up and then before you know it your Wine will not work anymore. Its like fixing a car while the car engine is running. Try it by burning an iso or from installation disc etc..

---

### Post by hikaricore on 2008-12-04
Buba5: We don't support piracy here, do not ask for assitance with a stolen game again.

Saytr: Your information is flat out wrong, a ripped/pirated game will not screw up WINE.
That just doesn't make any sense. kk?

---

### Post by ukulele_ninja on 2008-12-14
Is it ok to rip the game from the actual disc and follow the guide mentioned? If so, what program should I use to rip the cd with?

---

