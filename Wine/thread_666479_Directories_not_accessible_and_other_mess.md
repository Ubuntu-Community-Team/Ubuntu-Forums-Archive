---
title: "Directories not accessible and other mess"
date: 2008-01-13
forum: Wine
---

### Post by GreaterCore on 2008-01-13
Dear all, currently I am getting a wadload of error messages when I start running wine.

I tried running a DOS program on wine (or is this not recommended?) It appears  that it could not find a DOS directory and perhaps even my ATI drivers are bad. The game can run under DOSBox, but I am hoping to speed it up.

Thanks, the following is the error message. I ran `wine koei.com' from the directory containing the game.

> Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/username/Desktop/Desktop/waters', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\koei.com": Module not found
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x000000b8 at address 0x7e43b4c9 (thread 000b), starting debugger...
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]


---

### Post by hikaricore on 2008-01-13
DOS games will NOT run under WINE.

You're going to have to use DOSBox or another DOS emu for this.

---

