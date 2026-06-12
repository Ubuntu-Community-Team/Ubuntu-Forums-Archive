---
title: "Photoshop 7.0 hangs on initialization"
date: 2008-05-26
forum: Wine
---

### Post by flawsekno on 2008-05-26
[posted before in General Help, before I noticed that there was a Wine section ^^;;]

Hi, I'm having problems running Photoshop 7.0 under Wine 1.0-rc2 on Xubuntu 8.04. I recently got a hold of an old Windows CD of Photoshop 7.0 and installed it on my computer without any problems using Wine 1.0-rc2. However, startup of the program has been extremely inconsistent. When I first used it yesterday, it spend about 4 minutes on initialization, but when it launched, it worked perfectly - it was reasonably fast, it noticed pressure on my tablet, etc. But it's doesn't seem to be working anymore today - I'm waiting for 10 minutes or more to no avail.

Here's what happens when I launch in the terminal:

```
wine Photoshop.exe
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:wintab32:X11DRV_WTInfoW Return proper size
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x1ff2760)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:wintab32:X11DRV_WTInfoW Return proper size
err:twain:twain_add_onedriver Source->(DG_CONTROL,DAT_IDENTITY,MSG_GET) failed!
err:ntdll:RtlpWaitForCriticalSection section 0x12538c0 "?" wait timed out in thread 001a, blocked by 0009, retrying (60 sec)
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
err:ntdll:RtlpWaitForCriticalSection section 0x12538c0 "?" wait timed out in thread 001a, blocked by 0009, retrying (60 sec)
```

And then the last line repeats every minute. I'm quite new at this sort of thing, so if there's any other information that you need, please ask? I could use GIMP instead of Photoshop, but I really prefer Photoshop and would rather have the program work. Thank you!

---

