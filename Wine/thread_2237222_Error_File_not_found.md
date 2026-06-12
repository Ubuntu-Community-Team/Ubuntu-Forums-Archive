---
title: "Error: File not found"
date: 2014-07-31
forum: Wine
---

### Post by carlos_benitez2 on 2014-07-31
Wine:1.6.2
Ubuntu:14.04
terminal output:

[EMAIL="carlos@carlos-MacBookPro:~/.wine"]MacBookPro:~/.wine[/EMAIL]/drive_c/Program Files/MATLAB/R2014a/bin$ wine matlab.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
ERROR: Can't check 8.0 VCRTs (starter line:956) System Error: 0x00000002, File not found.
ERROR: Can't check 9.0 VCRTs (starter line:995) System Error: 0x00000002, File not found.
Installing required 8.0 run-time libraries. This may take a few minutes...
ERROR: Can't install 8.0 VCRTs (starter line:1037) System Error: 0x00000000, Success.
Installing required 9.0 run-time libraries. This may take a few minutes...
ERROR: Can't install 9.0 VCRTs (starter line:1082) System Error: 0x00000000, Success.
ERROR: Can't start MATLAB (starter line:1371) System Error: 0x00000002, File not found.

wine config: windows 7

hardware: Macbook pro early 2013
memory: 7.8 GiB
Processor: Intel® Core™ i7-3520M CPU @ 2.90GHz × 4 
Graphics: Intel® Ivybridge Mobile x86/MMX/SSE2
OS type: 32 bit

I recently installed matlab 2014a using wine and everything went smoothly and without problems. However, if I try to launch the .exe file I just get a dialog box that says error: file not found. Haven't been able to find much help online.

---

### Post by m_duck on 2014-07-31
Unless it has changed recently, you can install MATLAB natively Linux/Windows/OSX. It used to either have enough for all three on the disc (it's largely Java anyway), or separate downloads if you get it through the Mathworks website. The native install would be the best solution if it's possible?

As for the wine error, I can't be of too much help. Perhaps try another installation? E.g. using WINEPREFIX so your current install doesn't get overwritten:```
WINEPREFIX=~/.wine-matlab wine ~/path/to/wine/installer.exe
```

---

