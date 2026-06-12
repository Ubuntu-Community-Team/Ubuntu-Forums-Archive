---
title: "Wine launches apps vert slowly"
date: 2008-05-12
forum: Wine
---

### Post by RaZoR1394 on 2008-05-12
```

razor1394@basestar:~$ time wine .wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe 
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:813:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
fixme:mixer:ALSA_MixerInit No master control found on EyeToy USB camera Namtai, disabling mixer
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dc9ba08, overlapped 0x7dc9b9ec): stub
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0xb463dc)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:system:SetProcessDPIAware stub!
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject no class object {591209c7-767b-42b2-9fba-44ee4615f2c7} could be created for context 0x3
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:imm:ImmReleaseContext (0x9005c, 0x1431a0): stub
err:clipboard:CLIPBOARD_CloseClipboard Failed to set clipboard.

real	0m33.429s
user	0m0.836s
sys	0m0.216s

```

That's what launching Firefox under Wine looks like. This happened somewhere during the Hardy beta. Several wine versions later the problem is still there. I'm using the RC version of WineHQ's Wine version.

How can I fix it?

---

