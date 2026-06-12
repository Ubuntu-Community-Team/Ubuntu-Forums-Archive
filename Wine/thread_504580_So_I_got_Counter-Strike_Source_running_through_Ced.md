---
title: "So I got Counter-Strike: Source running through Cedega.."
date: 2007-07-19
forum: Wine
---

### Post by PrimoTurbo on 2007-07-19
First time ever I got it running and actually have been able to play. At first I had a black screen when starting CS:S through steam, then I made a shortcut in Cedega for C:\Program Files\Steam\STEAM.exe -applaunch 240 and removed my Windows config.cfg file. While I still had the black screen I was able to get into the game soon after, I set all my settings to low. On Windows I can run 1024x768 with nearly all settings on high and get between 25-40fps, which is playable.
[B]
My Specs[/B]:
Pentium 4
768 DDR RAM
ATI 9700 Pro 128MB

Unfortunately my hardware is far too obsolete to allow me to play it on Linux, I get between 5-20 fps if not lower. I managed to get 2 kills but the mouse lag is pretty bad there is a couple of milliseconds of delay between movement and firing. However I'm sure people with new computers and a good video card should be able to play it at high fps and high settings.

Also the black border around the screenshot appeared after I took a screenshot of the game using Print Screen in Gnome, the game ran completely full screen. When exiting the game my desktop size was messed up, stuck on 800x600 but it was at 1024x768 and I was sort of scrolling it around. But that was easy enough to change.

---

### Post by frodon on 2007-07-19
Use wine instead, wine offers better performances than cedega with counter strike source. You will find a full guide here :
[http://ubuntuforums.org/showthread.php?t=304528](http://ubuntuforums.org/showthread.php?t=304528)

And the appdb entry here :
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

---

### Post by BlahMan_of.Doom on 2007-07-19
He's right. I got it running faster in wine, and I can still have Compiz-Fusion on while running it :D

---

### Post by PrimoTurbo on 2007-07-19
Awesome, I will give it a try a bit later.

---

### Post by jmcivor on 2007-12-08
> **PrimoTurbo said:**
> First time ever I got it running and actually have been able to play. At first I had a black screen when starting CS:S through steam, then I made a shortcut in Cedega for C:\Program Files\Steam\STEAM.exe -applaunch 240 and removed my Windows config.cfg file. While I still had the black screen I was able to get into the game soon after, I set all my settings to low. On Windows I can run 1024x768 with nearly all settings on high and get between 25-40fps, which is playable.
[B]
My Specs[/B]:
Pentium 4
768 DDR RAM
ATI 9700 Pro 128MB

Unfortunately my hardware is far too obsolete to allow me to play it on Linux, I get between 5-20 fps if not lower. I managed to get 2 kills but the mouse lag is pretty bad there is a couple of milliseconds of delay between movement and firing. However I'm sure people with new computers and a good video card should be able to play it at high fps and high settings.

Also the black border around the screenshot appeared after I took a screenshot of the game using Print Screen in Gnome, the game ran completely full screen. When exiting the game my desktop size was messed up, stuck on 800x600 but it was at 1024x768 and I was sort of scrolling it around. But that was easy enough to change.

Sorry to bump an old thread, but could you explain in better detail how you got past the black screen? I've created a new shortcut in cedega but when I launch it steam doesnt even try to start. No errors, just doesnt start.

Screenshot:
[[IMG]http://img141.imageshack.us/img141/1766/screenshotshortcutpropeyq0.th.png[/IMG]](http://img141.imageshack.us/my.php?image=screenshotshortcutpropeyq0.png)

---

### Post by PrimoTurbo on 2007-12-11
> **jmcivor said:**
> Sorry to bump an old thread, but could you explain in better detail how you got past the black screen? I've created a new shortcut in cedega but when I launch it steam doesnt even try to start. No errors, just doesnt start.

Screenshot:
[[IMG]http://img141.imageshack.us/img141/1766/screenshotshortcutpropeyq0.th.png[/IMG]](http://img141.imageshack.us/my.php?image=screenshotshortcutpropeyq0.png)

All I had to do is wait and the black screen went away after a while, I did nothing else special.

---

### Post by jmcivor on 2007-12-11
It was way too much trouble, I got it working in WINE within like 30 minutes. I cant believe I wasted 15 dollars on cedega. What a waste of money :(

Did you end up getting audio as well? Thats the only thing i need to fix.

ANd by wait, do you mean you let it sit at the black screen for a few minutes? Or do you mean a few days later it just started working on its own?

---

### Post by boast on 2007-12-12
> **jmcivor said:**
> . I cant believe I wasted 15 dollars on cedega. What a waste of money :(

its not a waste. it helps support the wine project :)

> **jmcivor said:**
> 
Did you end up getting audio as well? Thats the only thing i need to fix.
how does your winecfg audio look?

---

### Post by jmcivor on 2007-12-12
> **boast said:**
> how does your winecfg audio look?

Im still pretty new to linux, how do I get into the wine configuration area? I know in the os audio settings it has 3 devices, my logitech headset (which is all I use) and 2 other devices, onboard stuff, realtek I think, and something else. Audio works fine for everything not emulated (wine stuff), like video's, music, youtube, etc.

---

### Post by karth on 2007-12-12
> **boast said:**
> its not a waste. it helps support the wine project :)

I'm sure a lot of people like to answer this, this time I get this privilege :)
Cedega is not the "commercial" Wine. Cedega is a fork of Wine back in the days when one could take Wine's code and make proprietary software out of it.

Therefore Cedega (Transgaming Company) != Wine (Wine team)

Wine does have a commercial version, though, called CrossOver. It's basically slightly older and allegedly stable Wine versions that are known to work quite well. Paying for Crossover helps Wine, paying for Cedega does not.

@jmcivor: type ```
winecfg
``` in the terminal and look which item is checked in the Audio tab. CS:S is known to work best with the OSS driver (alone), still I play with the ALSA driver.

---

### Post by jmcivor on 2007-12-12
> **karth said:**
> I'm sure a lot of people like to answer this, this time I get this privilege :)
Cedega is not the "commercial" Wine. Cedega is a fork of Wine back in the days when one could take Wine's code and make proprietary software out of it.

Therefore Cedega (Transgaming Company) != Wine (Wine team)

Wine does have a commercial version, though, called CrossOver. It's basically slightly older and allegedly stable Wine versions that are known to work quite well. Paying for Crossover helps Wine, paying for Cedega does not.

@jmcivor: type ```
winecfg
``` in the terminal and look which item is checked in the Audio tab. CS:S is known to work best with the OSS driver (alone), still I play with the ALSA driver.

awsome thanks, I'll try that when I get home from work today

---

### Post by jmcivor on 2007-12-12
ok I loaded winecfg as root (ran sudo -l first) and it opened, but when I click the audio tab it closes winecfg and returns this:
```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Link points to "/tmp/ksocket-jlm"
can't create mcop directory
```

Ok I created the dir its whining about and it let me in the tab, and selected OSSdriver for me saying there wasnt a driver in registry. I'll try it with the OSS driver selected.


Launched steam with ALSA driver selected:
```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.x is in your path.
dir: C:\Valve\Steam\bin\ *.mix
dir: C:\Valve\Steam\bin\ *.asi
dir: C:\Valve\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
The (slower) DirectSound HEL mode will be used instead.
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
err:systray:delete_icon invalid tray icon ID specified: 1d
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:dsound:DSOUND_MixOne underrun on sound buffer 0xd9ea398
```


Running with OSS selected:
```
err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.x is in your path.
dir: C:\Valve\Steam\bin\ *.mix
dir: C:\Valve\Steam\bin\ *.asi
dir: C:\Valve\Steam\bin\ *.flt
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:systray:delete_icon invalid tray icon ID specified: 1d
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.x is in your path.
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
dir: C:\Valve\Steam\ *.mix
dir: C:\Valve\Steam\ *.asi
dir: C:\Valve\Steam\ *.flt
warning: Unknown nb_ctl request:  4
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
err:mshtml:set_profile SetCurrentProfile failed: 80520015
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:d3d_shader:shader_get_registers_used No texture bound to sampler 4
err:d3d_shader:shader_get_registers_used No texture bound to sampler 4
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:d3d_shader:shader_get_registers_used No texture bound to sampler 4

```

With hardware acceleration set to Emulation:
```
err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.x is in your path.
dir: C:\Valve\Steam\bin\ *.mix
dir: C:\Valve\Steam\bin\ *.asi
dir: C:\Valve\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:systray:delete_icon invalid tray icon ID specified: 1d
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.x is in your path.
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
dir: C:\Valve\Steam\ *.mix
dir: C:\Valve\Steam\ *.asi
dir: C:\Valve\Steam\ *.flt
warning: Unknown nb_ctl request:  4
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
err:mshtml:set_profile SetCurrentProfile failed: 80520015
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:d3d_shader:shader_get_registers_used No texture bound to sampler 4
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:d3d_shader:shader_get_registers_used No texture bound to sampler 4
err:d3d_shader:shader_get_registers_used No texture bound to sampler 4
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110
err:dsound:DSOUND_MixOne underrun on sound buffer 0xda17110

```

No audio :( Any other suggestions? Am I missing something?

---

