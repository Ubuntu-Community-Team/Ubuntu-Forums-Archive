---
title: "Complicated Problem with Wine and Sound"
date: 2007-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by llirium on 2007-05-01
***EDIT:  I found the problem.  Needed to disable the 'Digital Audio Jack' cuz I'd been fooling around in the Mixer too much.  Dumb me...***:oops: 

A little while ago, I tried to install Wine via the instructions [here on the WineWiki]("http://wiki.winehq.org/UbuntuAMD64") for my AMD64 system.  Unfortunately, the installation failed for some reason.

I tried a new install from the package I found on [this thread]("http://ubuntuforums.org/showthread.php?t=297280").  It worked alright, but after typing 'winecfg'' for the first time, the sound on my whole system stopped working. :(

Here's what the System Log (var/log/syslog) had to say when I was doing it:

```
May  1 12:33:00 garden kernel: [ 2714.986839] ioctl32(winecfg.exe:5783): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/teresa/Desktop
May  1 12:33:00 garden kernel: [ 2714.987029] ioctl32(winecfg.exe:5783): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/teresa/.wine/drive_c/windows/system32
May  1 12:33:00 garden kernel: [ 2714.987258] ioctl32(winecfg.exe:5783): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/teresa/.wine/drive_c/windows/system
May  1 12:33:00 garden kernel: [ 2714.987418] ioctl32(winecfg.exe:5783): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/teresa/.wine/drive_c/windows
```

(*It kept repeating these same errors until winecfg was closed*)

I think the two installs on top of each other (dumb noob that I am, I forgot to uninstall) messed something up.  But I didn't see the package in Synaptic, so I still don't know how to uninstall it.

Any help would be appreciated.:(

---

### Post by Kilz on 2007-05-01
> **llirium said:**
> A little while ago, I tried to install Wine via the instructions [here on the WineWiki]("http://wiki.winehq.org/UbuntuAMD64") for my AMD64 system.  Unfortunately, the installation failed for some reason.

I tried a new install from the package I found on [this thread]("http://ubuntuforums.org/showthread.php?t=297280").  It worked alright, but after typing 'winecfg'' for the first time, the sound on my whole system stopped working. :(

Here's what the System Log (var/log/syslog) had to say when I was doing it:

```
May  1 12:33:00 garden kernel: [ 2714.986839] ioctl32(winecfg.exe:5783): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/teresa/Desktop
May  1 12:33:00 garden kernel: [ 2714.987029] ioctl32(winecfg.exe:5783): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/teresa/.wine/drive_c/windows/system32
May  1 12:33:00 garden kernel: [ 2714.987258] ioctl32(winecfg.exe:5783): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/teresa/.wine/drive_c/windows/system
May  1 12:33:00 garden kernel: [ 2714.987418] ioctl32(winecfg.exe:5783): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/teresa/.wine/drive_c/windows
```

(*It kept repeating these same errors until winecfg was closed*)

I think the two installs on top of each other (dumb noob that I am, I forgot to uninstall) messed something up.  But I didn't see the package in Synaptic, so I still don't know how to uninstall it.

Any help would be appreciated.:(

Look in my signature, follow link, install wine script. Wine installed. :D

---

### Post by llirium on 2007-05-02
> **Kilz said:**
> Look in my signature, follow link, install wine script. Wine installed. :D

I did so, and Wine seems to be working so far, save that it had these errors when I used *winecfg*:

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
```

But ALL of my system still doesn't have ANY sound at all, not just within the Wine program itself. :(

I tried changing from ALSA, OSS, ESD, to Autodetect, all the options in the Sound menu, but nothing at all.

---

### Post by Kilz on 2007-05-02
> **llirium said:**
> I did so, and Wine seems to be working so far, save that it had these errors when I used *winecfg*:

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
```

But ALL of my system still doesn't have ANY sound at all, not just within the Wine program itself. :(

I tried changing from ALSA, OSS, ESD, to Autodetect, all the options in the Sound menu, but nothing at all.

That sounds like its a system problem and not a wine problem. I'm not real good with hardware problems.[ But perhaps this page can help you.]("https://help.ubuntu.com/community/Sound")

---

