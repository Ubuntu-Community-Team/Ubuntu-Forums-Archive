---
title: "[SOLVED] hey why is wine takeing so long to load wow(worldofwarcraft)"
date: 2008-05-18
forum: Wine
---

### Post by wargodsown on 2008-05-18
hey i'm running wow in wine and for the first like 3 weeks it was absolutely perfect worked like a dream now it takes like 10 minutes to load the the wow launcher and like another 10 to start the wow login screen anybody have this problem to and if so has any body found a way to fix it.

i have a lvl 31 paladin(horde rules) and i've been trying to finally get my mount and if this problem persists i feel like i might just hafto go take a break and yank out some more hair .

well thanks all

---

### Post by pedro_orange on 2008-05-19
I'd skip loading the launcher, and launch WoW.exe directly.

What command are you using to open it?

You want it summit like:

wine 'home/pedro./wine/drive_c/Program Files/World of Warcraft/WoW.exe' -opengl

It does take a while to open; but if you open it in terminal you'll see why. (And by a while to open I mean a few seconds, not minutes!)

What version of WINE are you running?
Have you updated any affiliated software recently?

---

### Post by wargodsown on 2008-05-19
yea the auto updater put something for wine on my comp was a patch or something i dont member and thnx for the help i'll try replaceing ur name with mine lol in the line of code any who as far as i know i'm running the latest version of wine and my wow is all patched up well hey i'm gonna try what u suggested real quick lol

---

### Post by wargodsown on 2008-05-19
well i tried it and it gave me this response

wine: cannot find 'home/dustin./wine/drive_c/Program Files/World of Warcraft/WoW.exe'

so i got no clue lol i've tried the whole run it in terminal before with another line of code i saw on here but bout the same luck as the normal wow launcher

---

### Post by pedro_orange on 2008-05-20
Try doing this:

1 - Open terminal
2 - type 'wine'
3 - Drag & drop the WoW.exe file onto terminal & it should dump the path there. 
4 - append -opengl
5 - Hit Enter

So it'll look summit like:

```
wine 'path/to/WoW.exe' -opengl
```

---

### Post by wargodsown on 2008-05-21
i tried that and i put in the opengl thing heres what it looked like when i hit enter

 '/home/dustin/.wine/drive_c/Program Files/World of Warcraft/Wow.exe' -opengl

i got no clue if thats how it was supposed to look but thats what i did anyways then when nothing happend i tried this

'/home/dustin/.wine/drive_c/Program Files/World of Warcraft/Wow.exe' 

and this is what i got back

err:module:attach_process_dlls "gdi32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\Wow.exe" failed, status c000013a

now the last part i'm guessing is because of it not being right like u said to put it in but hey i was experimenting so anyways 

so i had the wow launcher up when i did it so i closed that just to see if that could have been it and wow tried to run but said something bout some error so yea no clue lol i hope i'm not just makeing the water mddier so to speak but i'm kinda linux innept lmao i just fgot it last month so yea and i'm in no w3ay shape or form a computer programmer so a lot of this stuff i'm flying by the seat of my pants on
well thnx for the help so far i hope i can figure this out well if u have any insite plz feel free to help me cuz dam am i confused

---

### Post by wargodsown on 2008-05-22
ok yea i'm such a retard lmao i figured out why wow was what was slowing me down i had run virus scans on my home directory and all the other stuff but i did'nt run the full scan it was always just quick scan lol and quick scan always came back golden well i did a full scan and did a scan on all hidden files and came back with a lot of trojan horse viruses and once i deleted them wow comes up real nice and prompt lol all the viruses i had were working thru wine so yea it works great thankx for all ur help man if it would be cool could i put u on my friends list if i have other questions??? thanks again man i just wish sometimes i looked at things more closely lol

---

### Post by pedro_orange on 2008-05-22
I'm glad you sorted your problem.

Yes; by all means. Although I'm no linux guru; I just know how to get by/google.

---

### Post by wargodsown on 2008-05-23
rock on thanx man

---

