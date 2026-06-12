---
title: "Wine WOTLK"
date: 2008-11-13
forum: Wine
---

### Post by Bofur on 2008-11-13
Hi I have WOTLK currently extracted onto my desktop. I execute the program via wine and it loads up. When I come to the EULA screen I can't click accept, only disagree. Someone in a previous post said this:

```
It's a problem with the HTML controls.

[http://bugs.winehq.org/show_bug.cgi?id=13321](http://bugs.winehq.org/show_bug.cgi?id=13321)

I got it to install by using ies4linux, shudder. [http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)

Run BC once using ies4's wineprefix to create the proper registry entries, then run the wrath installer using ies4's prefix, then move wrath to your regular wineprefix and create shortcuts as necessary.

$ WINEPREFIX=~/.ies4linux/ie6 wow
$ WINEPREFIX=~/.ies4linux/ie6 /path/to/Wrath/Installer
$ mv ~/.ies4linux/ie6/drive_c/Program\ Files/Wrath ~/.wine/drive_c/Program Files/Wrath

$ cat ~/bin/wrath

#!/bin/bash

cd /home/<me>/.wine/drive_c/Program\ Files/Wrath\ of\ the\ Lich\ King\ Beta/

wine explorer /desktop=wow,1440x900 Launcher***** "$@"&                      
```I have ies4linux installed, but I don't really understand his instructions. I typed the first line into terminal and nothing happened. Any ideas?

---

### Post by Bofur on 2008-11-13
I get this error: 
```
root@ubuntu:/home/justin# WINEPREFIX=~/.ies4linux/ie6 /home/justin/.ies4linux/ie6/wow/Installer.exe
wine: chdir to /root/.ies4linux/ie6
 : No such file or directory
root@ubuntu:/home/justin# 
```

---

### Post by Bofur on 2008-11-13
Got it to work, just install the new wine and it fixes it! :guitar:

---

### Post by hotballz87 on 2008-11-13
so the newest wine version fixes the end user license agreement?

i got the game at midnight, and couldnt copy the files. so i copied them to my gf's computer and transferred them through lan to my computer. 3 in the morning now cause i cant get through the freaking eula...

---

### Post by hotballz87 on 2008-11-13
ok. i did the wine thing just now. now, the next problem....
" An error occurred while installing DirectX."

what now? anyone else have this problem?

does it work if i take a repair.exe from a computer that has it all installed now and run it? if so, im so doing that

---

### Post by Guberif82 on 2008-11-13
I am trying to do all this and got it to kinda work now its asking for a newer version of window when I get to the install screen
```
richard@richard-desktop:~$ WINEPREFIX=~/.ies4linux/ie6 wine ~/desktop/InstallWoW.exe
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703

```

I hit okay for WotLK, then it says 
"Unable to install 

Wrath of the lich king requires a newer operating system to run.

Windows 2000, XP or newer is required."

And it has the Ream me, manual, support, exit buttons

---

### Post by Guberif82 on 2008-11-13
So I actually installed wine 1.1.8 and now the EULA finally worked so I am able to play WooT!!

---

### Post by sornen on 2008-11-13
The grey problem was fixed for me after updating wine according to this:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by JMuffin on 2008-11-13
I followed the directions for upgrading to the newest version of wine, but when I open synaptic it does not prompt me to download any version of wine.

Never mind. Even though I did not upgrade wine or change any of it's settings, I am now able to click agree. Forget I was here.

---

### Post by brink on 2008-11-13
So part of my problem is that I'm still gutsy on this box, so I can only install up to wine 1.0 without building from source, apparently.

Having said that, I was able to get to the installation process and past the eula accept button only by the following:

1. Mount the dvd manually and copy/change ownership of the install files on my hard drive.

2. use ies4linux as my wine installation to be able to click the accept button*. I'm in the process of installing right now. We'll see if I'll be able to actually play the game :)


*this means installing ies4linux and renaming your .wine dir to something else, then linking .ies4linux/ie6 as .wine, then running winecfg and setting the windows version to xp.

---

### Post by windowsareslow on 2008-11-13
I had a problem where I could only read installer.exe and directX directory.  Eventually I unmounted and mounted with the -o unhide option:

sudo mount cdrom0 -o unhide

and I can at least see the directories to sudo cp * them to my hard drive.

---

### Post by harrowwhat on 2008-11-15
"Unable to install

Wrath of the lich king requires a newer operating system to run.

Windows 2000, XP or newer is required."

And it has the Ream me, manual, support, exit buttons

why does this come up? how do i get past it? please help

---

### Post by Zace on 2008-11-15
I got my collectors edition yesterday and came no further than there.
Followed the guide on here, et voila.

I love you all.

---

### Post by sornen on 2008-11-16
I also updated wine to the latest version according to:

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

but although the graphics were good, the sound/audio was very choppy on my amd64 system.

Therefore, after installing WOTLK I:

1. Unmarked  winehq from the Settings/Repositories/Third Party Software in synaptic package manager.
2. Uninstalled the latest winehq wine.
3. Reinstalled the stable wine 1.0.1 version that comes with Intrepid.
4. Chose ALSA in winecfg

Sound is now fixed on my system.
Remember you may also need to set SoundBufferSize to a value from 50 to 200 eg:

SET SoundBufferSize "150"

in WTF/Config.wtf

:grin:

---

### Post by MagickalHack on 2009-02-05
Got it to work with a fresh install of hardy [8.04] All I had to do was follow the instructions found [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb"). Gecko has to be up to date.

---

### Post by cb951303 on 2009-02-05
It's an old thread but for future ref:

Latest WOTLK runs like a charm in Ubuntu 8.10 with the Wine version 1.0.1 from the Ubuntu repos.

---

