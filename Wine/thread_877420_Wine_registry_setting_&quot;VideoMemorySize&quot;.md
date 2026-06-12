---
title: "Wine registry setting &quot;VideoMemorySize&quot;"
date: 2008-08-01
forum: Wine
---

### Post by Bradl3yJ on 2008-08-01
I have been trying to follow this guide here:

[http://gaming.gwos.org/doku.php/wine:winestuff#special_configuration_stuff](http://gaming.gwos.org/doku.php/wine:winestuff#special_configuration_stuff)

I got to the part about Useful registry keys. I had to create the Direct3D key under HKCU>Software>Wine because it wasn't already there. Then i had to create the VideoMemorySize option. First off, i am unsure what value type they want me to choose. I assumed it was DWORD value as it is representing a numeric value. So i set the decimal value of VideoMemorySize to 128.

Now, when i launch the config utility for a game i have, it shows the available video memory, and it still shows 64MB. I figured i might have to do a wineboot, i ran the command wineboot, and get the following output:
```
brad@brad-desktop:~$ wineboot
err:wineboot:ProcessRunKeys Error running cmd #0 (0)
brad@brad-desktop:~$ fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:advapi:SetEntriesInAclA 1 0x33f7b4 (nil) 0x33f7fc
fixme:advapi:SetSecurityInfo stub
fixme:dpnhpast:DllRegisterServer :stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x7eb5bd75 (thread 001d), starting debugger...
```

Did wine simulate a reboot properly or is there a problem here? and am i setting the registry key right?

---

