---
title: "Steam games hanging after loading"
date: 2007-12-28
forum: Wine
---

### Post by Chris1091 on 2007-12-28
Hey guys, I've been messing with this for hours and haven't gotten anywhere.  I'm trying to install half-life 2 on a gutsy 7.10 system and it hangs on a black screen while loading after launching the game.  

some specs:
gutsy 7.10
ATI radeon 9600
1 gig ram
Wine 0.9.51

Here's the code i'm getting, this is using Vista version in Wine, but XP doesn't work either:
```
chris@chris-desktop:~$ WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen \
>     -width 1024 -height 768 -applaunch 220 \
>     -heapsize 512000 +map_background none "$@"
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
Failed to verifiy SteamService.dllerr:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:systray:delete_icon invalid tray icon ID specified: 1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:alsa:ALSA_copyFormat calculated 50 bytes, capping to 40 bytes
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
```

Steam opens up fine and appears to be fully functional.  Also, the same thing happens for Team Fortress 2, but when it hangs at the black screen I am able to audibly hear when i mouseover where the buttons are.  Any ideas?

---

### Post by Chris1091 on 2007-12-28
I found what I believe to be my problem described at the bottom of this page

[http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)

> UPDATE 0.49.x (25.11.07): When loading CS:S you see the loading screen (that with the two CT guys) and then you get a black screen, see the loading screen again and then the game crashes/doesn’t launch, then here is what might help:

1. Launch regedit -> wine regedit

2. Navigate to [HKEY_CURRENT_USER\Software\Wine\Direct3D]

3. Add a String with the name “VideoMemorySize” , and then amount of video RAM you have, ex: 256

However, I have no Direct3D file in that folder.  Is that normal with my version of wine or could this be cause of the problem? Any help would be greatly appreciated!  

Thanks

---

### Post by constchar* on 2007-12-28
All versions of Wine, even custom compiled versions I've made, never have included
a Direct3D key by default so go ahead and make that with the regedit tool included
with Wine.

Although I'm not sure this problem is specific to Wine or not as Steam games, paticularly ones built on the Source engine,
lag really bad or hang after loading for about 10 to 15 seconds even on Windows.

Although I haven't experienced the lag, I mentioned above, that much with Wine
in the latest Wine 0.9.51 Source engine games either hang immediately after loading
or hang about 30 seconds to a minute after loading while I'm playing the game and
I've never experienced that in recent versions so I suspect that Wine 0.9.5x may
have broken something.

---

### Post by Chris1091 on 2007-12-29
Still hanging after adding the new key.

---

### Post by Chris1091 on 2007-12-29
Upgraded to 0.9.52 and am still having the same problem.  Here's the code again:

```
chris@chris-desktop:~$ WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen \
>     -width 1024 -height 768 -applaunch 220 \
>     -heapsize 512000 +map_background none "$@"err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
Failed to verifiy SteamService.dllerr:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:systray:delete_icon invalid tray icon ID specified: 1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.

```

---

### Post by mfarley on 2007-12-29
Having the same problem here... Gutsy, wine 0.9.52

---

### Post by Chris1091 on 2007-12-29
Just updated from the restricted drivers to the latest ATI drivers and still having the problem.  Hopefully someone has an idea...

---

### Post by MeathooK427 on 2008-01-11
First of all, install the "winbind" package through Adept Manager, or terminal.

sudo apt-get install winbind

Also for steam, make sure the tahoma font is installed. ~/.wine/drive_c/windows/fonts/tahoma.ttf .

---

