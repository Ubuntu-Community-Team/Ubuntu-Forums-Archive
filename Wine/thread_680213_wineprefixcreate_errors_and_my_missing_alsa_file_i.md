---
title: "wineprefixcreate errors and my missing alsa file in HKCU"
date: 2008-01-27
forum: Wine
---

### Post by Handssolow on 2008-01-27
I want to resolve my Wine 0.9.54 configuration messages before working on some Wine application errors.  I suspect mostly it's related to my Asrock 939 Dual-VSTA board having a C-Media CM6501 part USB part PnP Audio Device.
$ wineprefixcreate
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8b2, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on PnP Audio Device        , disabling mixer
fixme:iphlpapi:NotifyAddrChange (Handle 0x7cc3c9c8, overlapped 0x7cc3c9ac): stub
fixme:shell:DllCanUnloadNow stub
/home/Handssolow/.wine updated successfully.

Looking for solution, I looked [here](http://wiki.winehq.org/UsefulRegistryKeys)

However, when I look in my HKCU using wine regedit there is no alsa file. After search of the registry I found only one reference to the Alsa Driver.

It's not all bad. I can selected the Alsa driver in winecfg and play a test sound. I can also run Firefox and IE6 but not some other applications.

---

