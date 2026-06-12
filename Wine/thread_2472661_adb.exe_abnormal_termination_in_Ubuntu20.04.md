---
title: "adb.exe abnormal termination in Ubuntu20.04"
date: 2022-03-08
forum: Wine
---

### Post by johnaaronrose on 2022-03-08
I'm using Wine version 5.0.3ubuntu1 installed from Ubuntu repos using Ubuntu 20.04. I'm having a problem with adb.exe on all versions that I've tried (e.g. 30.0.2, 31.0.3).
    ```
john@desktop:~$ cd $WINEPREFIX
    john@desktop:~/VirtualWineDrives/B4X$ cd drive_c
    john@desktop:~/VirtualWineDrives/B4X/drive_c$ cd Android
    john@desktop:~/VirtualWineDrives/B4X/drive_c/Android$ cd platform-tools
    john@desktop:~/VirtualWineDrives/B4X/drive_c/Android/platform-tools$ wine adb.exe version
    adb.exe F 03-08 09:27:10   118   195 sysdeps_win32.cpp:2908] _wenviron is not set, did you link with -municode?
    
    abnormal program termination
```

There is no problem with the Linux version of adb:
    ```
john@desktop:~$ cd B4X/platform-tools
    john@desktop:~/B4X/platform-tools$ adb version
    Android Debug Bridge version 1.0.41
    Version 31.0.3-7562133
    Installed as /home/john/B4X/platform-tools/adb
```

---

