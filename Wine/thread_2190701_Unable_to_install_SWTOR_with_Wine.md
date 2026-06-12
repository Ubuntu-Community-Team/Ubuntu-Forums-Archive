---
title: "Unable to install SWTOR with Wine"
date: 2013-11-28
forum: Wine
---

### Post by tavise on 2013-11-28
I've followed many guides, read many threads about how to do this, and met with failure.

First attempts:  Linux mint 14, wine 1.5, 1.6.  Followed all of the suggestions about swtor_fix.exe, patched wine in chroot, etc.  None worked.
Now:  blew away my entire system and installed Linux Mint 15 (based on ubuntu raring)

```
> uname -a
Linux bel0110 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
> wine --version
wine-1.7.6

```
The downloaded "installer" seemed to work fine:
```
#!/bin/sh

export WINEPREFIX="$HOME/.swtor_wine"
export LD_LIBRARY_PATH=/usr/lib32:/usr/lib
export WINEARCH=win32
export WINEDEBUG=-all
winetricks corefonts tahoma
winetricks d3dx9
winetricks vcrun2008

wine ~/Downloads/SWTOR_setup.exe

```
Running the launcher, however, completely blows up and all searching for this error message has proven unhelpful so far:

```
#!/bin/sh

export WINEPREFIX="$HOME/.swtor_wine"
export LD_LIBRARY_PATH=/usr/lib32:/usr/lib
export WINEARCH=win32
export WINEDEBUG=-all

wine "C:\Program Files\Electronic Arts\BioWare\Star Wars - The Old Republic\launcher.exe"
```
Only a single line of output is produced:
```
> swtor
[1128/121140:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8
>

```

Any help would be greatly appreciated!

---

### Post by david146 on 2014-08-24
I have an MSI motherboard, with an AMD 4 core chip Nvidia gtx 450 video card 16 Gb ram 259 Gb SSD Ubuntu 14.04 running SWTOR in a reduced window using PlayOnLinux, Skill tree doesn't work and it freezes up now and then but game play is smooth and flawless. As far as installing everything it was straight forward and all done thru Ubuntu Software Center. Went to software center installed playonlinux, after getting it up and running just scrolled down to SWTOR highlighted it clicked install and it took off. Now it will take quite awhile to update but let it finish and it should run with very few problems.

---

