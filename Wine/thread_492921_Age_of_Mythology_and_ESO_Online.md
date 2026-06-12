---
title: "Age of Mythology and ESO Online"
date: 2007-07-05
forum: Wine
---

### Post by DarkGreen16 on 2007-07-05
I'm so close to being able to make the full switch to linux and one thing that is stopping me is not being able to play age of mythology online through linux. I was just wondering if anyone got age of mythology to work on ESO (not direct ip) using either wine or cedega? I've been able to figure out a few things so far - for example there are 3 kinds of cracks because the safedisc protection does not work correctly with the original cd.

1. Fixed executable (ESO online detects the difference and will not let you connect even on a windows box)
2. Loader (works on windows box) But when i try to run it in wine i get an error like "unable to load second dll image base"
3. Fixed image - this has the same problem as the original cd where it doesnt seem to work with the safedisc protection in linux

So as of right now i am forced to use the fixed executable because its the only thing that will let me play in linux. I have a feeling this is one thing that is stopping me. 

The second thing i noticed is when I installed it via cedega it gave me an error about not having internet explorer installed which is why i think i can't get even a basic connection to ESO.(In cedega it won't even launch but in wine it does. However, wine never threw the error about internet explorer) Basically when I hit the login button it INSTANTLY says "Cannot connect to ESO" where on a windows box with the same crack it says "Your game version needs to be updated" and the only difference being that the windows box has internet explorer so i believe those are the 2 hurdles I need to get over. I have already tried installing ie6 but it won't even run standalone and ESO has the same result. Anyone had any luck with this?


*On another note* I see numerous posts in the wineapp db about people being able to play multiplayer on the "internet" just fine. However, they fail to mention if that is via direct ip(which works fine) or via ESO. Also i found this post [http://forums.fedoraforum.org/showthread.php?t=151040]("http://forums.fedoraforum.org/showthread.php?t=151040") where the guy was able to play (in post 4) without a cd crack.

---

### Post by carlbastos on 2007-07-09
How the heck you made AoM run on Cedega? It says my VGA ins unsupported here, and I don't know how to 'bypass' this!

---

### Post by Pathfinder_ on 2007-07-27
I managed to run aom on WINE and it runs pretty well. But i also have the same problem as you, not being able to connect to ESO. 
If anyone knows the solution please post it becasue i would really like to get it working.

---

### Post by facelesspenguin on 2007-08-02
could you please post how you got aom working on ubuntu ? 
the single player ... 

im a newbie to both ubuntu and aom .. and would appreciate any help.

thanks in advance ...

---

### Post by Pathfinder_ on 2007-08-08
fisrt you have to add PidGen.dll AND mfc42.dll to the wine system32 folder. Those can be downloaded. just search google also don't forget to install msxml(it's on the AoM cd)
Next put in disk 1 and in terminal type "wine /path/to/setup.exe" 
when it asks u to put in disk 2 you have to unmount the previous disk. 
then put the second disk in and it should resume. 
downlaod patch for aom to update it, get a no-cd laoder and you should be all set.

---

### Post by DarKirby on 2007-08-12
Hi Guys,

I'm also making the switch to ubuntu, thanks for the help, pathfinder.
I normally only play LAN AOM, and i've got that to work under wine, but I know back on my windows box that ESO does NOT work with the nocd version of AOM, the only way i can get online with it is by either putting a cd in the drive, or using a cd emulator.
So the nocd .exe may be inhibiting the eso.

---

### Post by Malvolio on 2007-08-12
You can also create a folder in your media folder, map it in Wine as a drive, make an iso of your AoM disk and mount the iso to the folder you made.  I do this with Starcraft, works like a charm.  I use this command in Terminal to mount the iso.

sudo mount -t iso9660 -oloop cd.iso /media/folder/

You have to do this in the folder you have the iso in.

---

### Post by Pathfinder_ on 2007-08-13
> **DarKirby said:**
> Hi Guys,

I'm also making the switch to ubuntu, thanks for the help, pathfinder.
I normally only play LAN AOM, and i've got that to work under wine, but I know back on my windows box that ESO does NOT work with the nocd version of AOM, the only way i can get online with it is by either putting a cd in the drive, or using a cd emulator.
So the nocd .exe may be inhibiting the eso.

That's weird, on my windows install I play aom with a no-cd loader fine and it never gives me any trouble. Are you sure you are using the no-cd loader and not the fixed exe? Is the no-cd loader the correct version?

---

### Post by climatewarrior on 2007-08-20
Worked Perfectly for me Thanks a lot. I have Ubuntu 7.04 Feisty Fawn on a Dell Latitude X300. Thanks!!

---

### Post by climatewarrior on 2007-08-21
Damn! Age of Mythology with the Titans expansion was working perfectly until I installed the 1.03 patch so that I could play via lan with my firends. Now when I start it up nothing happens. Anybody know how to solve this?

---

### Post by Pathfinder_ on 2007-08-22
If you were using the no-cd loader for version 1.0 download the one for 1.3 and replace the old one.

---

### Post by leandrovargas on 2007-11-11
> **Pathfinder_ said:**
> fisrt you have to add PidGen.dll AND mfc42.dll to the wine system32 folder. Those can be downloaded. just search google also don't forget to install msxml(it's on the AoM cd)
Next put in disk 1 and in terminal type "wine /path/to/setup.exe" 
when it asks u to put in disk 2 you have to unmount the previous disk. 
then put the second disk in and it should resume. 
downlaod patch for aom to update it, get a no-cd laoder and you should be all set.

How to install msxml from AOM cd?? I found on my CD2 a folder called msxml, and inside some files .msi. How to install?

P.S. I can to run with wine, but give to me a error requesting msxml must be installed.

Thanks for any help.

---

### Post by pizey123 on 2008-05-26
well   if   you  find out  how to do it please tell me  same thing happens to me  :lolflag:

---

### Post by dirbaio on 2008-12-06
> **leandrovargas said:**
> How to install msxml from AOM cd?? I found on my CD2 a folder called msxml, and inside some files .msi. How to install?

P.S. I can to run with wine, but give to me a error requesting msxml must be installed.

Thanks for any help.

Same happened to me. What i did was run a file called msxmlspa.msi that was in my installation folder c:/program files/microsoft games/Age Of Mythology/

---

