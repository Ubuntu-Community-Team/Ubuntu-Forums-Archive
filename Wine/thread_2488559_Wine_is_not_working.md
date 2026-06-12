---
title: "Wine is not working"
date: 2023-07-08
forum: Wine
---

### Post by lymphor on 2023-07-08
Hello everybody! :)

I'm using **Ubuntu 22.04** and I have problems with **Wine**. More specifically: when I double click on Windows applications nothing happens (I don't even receive an error message).
I tried to **uninstall **and** reinstall** Wine, but nothing changed.
I tried to run the Win executable from **terminal**, but this is the response I got:
```
ale@alePC:/media/ale/MUSIC_&_GAMES/Games/Sega Classics/Fusion$ wine Fusion.exe
0024:err:file:init_redirects /home/ale/.wine/dosdevices/c:/windows: No such file or directory
002c:err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
002c:err:wineboot:process_run_key Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2).
wine: could not open working directory L"unix\\media\\ale\\MUSIC_&_GAMES\\Games\\Sega Classics\\Fusion\\", starting in the Windows directory.
002c:err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\users\\ale\\Application Data".
002c:err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\users\\ale".
002c:err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\users\\ale\\Local Settings\\Application Data".
wine: could not open working directory L"unix\\media\\ale\\MUSIC_&_GAMES\\Games\\Sega Classics\\Fusion\\", starting in the Windows directory.
0024:err:winediag:nodrv_CreateWindow Application tried to create a window, but no driver could be loaded.
0024:err:winediag:nodrv_CreateWindow The explorer process failed to start.

```

I tried to use **sudo apt-get update**, and this is the result:
```
Get:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Hit:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:3 http://ro.archive.ubuntu.com/ubuntu jammy InRelease                      
Get:4 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease [8.041 B]       
Hit:5 https://ppa.launchpadcontent.net/kdenlive/kdenlive-stable/ubuntu jammy InRelease
Get:6 http://ro.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]     
Hit:7 https://repo.radeon.com/amdgpu/5.4.5/ubuntu jammy InRelease     
Hit:8 https://repo.radeon.com/rocm/apt/5.4.5 jammy InRelease
Get:9 http://ro.archive.ubuntu.com/ubuntu jammy-backports InRelease [108 kB]
Get:10 http://security.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [41,6 kB]
Get:11 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [22,0 kB]
Err:4 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Get:12 http://ro.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [777 kB]
Get:13 http://ro.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [440 kB]
Get:14 http://ro.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [99,6 kB]
Get:15 http://ro.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [939 kB]
Get:16 http://ro.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [274 kB]
Get:17 http://ro.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]
Get:18 http://ro.archive.ubuntu.com/ubuntu jammy-backports/main amd64 DEP-11 Metadata [7.972 B]
Get:19 http://ro.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [15,4 kB]
Reading package lists... Done                                     
W: GPG error: https://dl.winehq.org/wine-builds/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu jammy InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

I then used **sudo apt-get upgrade**, and I got this:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libffi7
Use 'sudo apt autoremove' to remove it.
The following packages have been kept back:
  gir1.2-mutter-10 libmutter-10-0 mutter mutter-common
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```

If I use **wine --version** I get this:
```
wine-6.0.3 (Ubuntu 6.0.3~repack-1)
```

At this point I really don't know what to do. I hope somebody will be able to help me out.
Thanks in advance!

---

### Post by ActionParsnip on 2023-07-08
Did you check the WineAppDb for compatibility?

---

### Post by deadflowr on 2023-07-09
*Thread moved to **Wine***

---

### Post by lymphor on 2023-07-09
I managed to somehow fix the issue: I uninstalled Wine, removed the .wine folder from Home and reinstalled Wine. Now Windows applications seem to work fine.
But I still get error messages when I run **sudo apt update**:
> Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]
Hit:2 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) jammy InRelease                      
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Get:4 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]     
Get:5 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) jammy InRelease [8.041 B]       
Hit:6 [https://ppa.launchpadcontent.net/kdenlive/kdenlive-stable/ubuntu](https://ppa.launchpadcontent.net/kdenlive/kdenlive-stable/ubuntu) jammy InRelease
Get:7 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) jammy-backports InRelease [108 kB]   
Hit:8 [https://repo.radeon.com/amdgpu/5.4.5/ubuntu](https://repo.radeon.com/amdgpu/5.4.5/ubuntu) jammy InRelease
Hit:9 [https://repo.radeon.com/rocm/apt/5.4.5](https://repo.radeon.com/rocm/apt/5.4.5) jammy InRelease
Err:5 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) jammy InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Reading package lists... Done
W: GPG error: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu jammy InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

And my Wine version seem to be old, **wine --version**:
> wine-6.0.3 (Ubuntu 6.0.3~repack-1)

Any ideas on how to fix the error messages and obtain a more recent version of Wine?

---

### Post by lymphor on 2023-07-09
Problems fixed, I just needed to follow these instructions: [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)
Thank you all for your help!

---

### Post by Holger_Gehrke on 2023-07-10
Just a small thing to remember: with Wine newer isn't always better. There have often been been regressions, basically errors in newer versions which make programs that ran fine with older versions crash. One way around that problem is to use PlayOnLinux, a GUI for Wine which allows you to have multiple versions of Wine installed at the same time and use the right version for each program.

Holger

---

### Post by lymphor on 2023-07-12
Thank you for the tip! ;)

---

