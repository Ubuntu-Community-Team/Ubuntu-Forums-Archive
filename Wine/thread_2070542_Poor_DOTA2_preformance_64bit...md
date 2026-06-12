---
title: "Poor DOTA2 preformance 64bit.."
date: 2012-10-13
forum: Wine
---

### Post by Meowmix on 2012-10-13
Hello dota is the only game i play and i would really like for it too work .. //

my specs: 
gigabyte ud4 motherboard (p67 chipset)
ATI Hd 6950 graphics
2500k sandy bridge cpu
ubuntu 12.04.1 fresh install

have installed wine both through PoL and winetricks and i am using version 1.5.15 of wine but once i download and install dota it is very laggy / choppy and there is some lighting issues, aura around tree of life for example is ultraviolet..
 i have installed ia32libs and practically everything else concerning dota2 and wine issues but nothing has solved this problem..

my launch options in steam are -novid and -nod3d9ex...


when i launch steam with the command 

```
 winedebug=all wine /home/lachlan/.local/share/wineprefixes/steam/drive_c/Program\ Files\ \(x86\)/Steam/steam.exe -no-dwrite 
```

there is a ton of logging, especially once i start a game of dota, the console is literally spammed..

i would post the log but i will need some help to store the log and/or extend the history of terminal...

Any help would be most appreciated, i would really just like dota to work :confused:

---

### Post by shaolin77 on 2012-12-08
I'm having similar issues and trying to work toward a solution.

Have you made any progress since you posted?

---

### Post by Lila7714 on 2013-01-02
Dota 2 is running perfect for me. I have wine-1.5.20 and running with just -no-dwrite. Try running it in a seperate x session. T'is what I use [https://wiki.archlinux.org/index.php/Running_program_in_separate_X_display](https://wiki.archlinux.org/index.php/Running_program_in_separate_X_display)

---

