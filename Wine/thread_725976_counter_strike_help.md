---
title: "counter strike help"
date: 2008-03-16
forum: Wine
---

### Post by Nikhil Gohil on 2008-03-16
hi...im new to ubuntu and am missing counter strike.i have files of counter strike source and run it using ```
wine hl2.exe -steam -game cstrike -console
``` . the game starts fine but when i try to create a server , it says "could not load server.dll". then, i tried running srcds.exe. this is the output  ```
wine srcds.exe -steam -game cstrike -console
ALSA lib pcm_mmap.c:369:(snd_pcm_mmap) mmap failed: Invalid argument
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\media\\sda5\\cs\\cs-source setup on home (190.190.190.241)\\cstrike\\bin\\server.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\media\\sda5\\cs\\cs-source setup on home (190.190.190.241)\\cstrike\\bin\\server.dll") not found
```


i have no idea what to do.......please help!

---

### Post by liquidfunk on 2008-03-16
Check what version of Wine you have. 

 According to the WineHQ it has a platinum rating.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731&iTestingId=21779](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731&iTestingId=21779)

---

### Post by Steven_ on 2008-03-16
CS uses MFC42.DLL which you don't have. Google for it :P Or you could search for MFC Runtime files (don't know if an installer exists).


EDIT: take a look here, on the bottom of the page
[http://www.hussar.demon.co.uk/mathszon.htm#Download%20the%20MFC](http://www.hussar.demon.co.uk/mathszon.htm#Download%20the%20MFC)

---

### Post by Nikhil Gohil on 2008-03-16
thanks for the reply dudes.......i got a copy of mfc42.dll and now cs works. it is kinda slow on my old pc. but i cant change any options(like video resolution) from the gui...the game just quits to the console. any ideas...or can someone just tell me the video config file so i can edit it myself???

This is the error:
```
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

---

