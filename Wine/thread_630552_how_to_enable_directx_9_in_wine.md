---
title: "how to enable directx 9 in wine?"
date: 2007-12-03
forum: Wine
---

### Post by sourcemorph on 2007-12-03
ok today i tried to install fable the lost chapters in wine, when i executed the game file in terminal it gave me the following error...

```
err:module:import_dll Library d3dx9_25.dll (which is needed by L"C:\\Program Files\\Microsoft Games\\Fable - The Lost Chapters\\Fable.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Games\\Fable - The Lost Chapters\\Fable.exe" failed, status c0000135

```

i think it means that the dx9 files r missing.. how can i enable those things? is it adbisable to install the standrd directx 9 redist package using wine.... i read somewhere that it shud be avoided as it disturbs the wine's native dx libraries??

---

### Post by sourcemorph on 2007-12-03
hmm somebody???

---

### Post by cogadh on 2007-12-03
DX9 is already enabled. That DLL file is just a DX support library, which you can either copy from an existing Windows installation or download from the internet and place in the .wine/drive_c/windows/system32 folder.

---

### Post by sourcemorph on 2007-12-04
ok i did that and the game ran, but too many bugs, the character image u get in the bottom left comes in the form of an inverted tree in black n white... the shadow effect was all wrong... so i disabled it. but still its kinda weird.... prolly my graphics card then :(

---

### Post by Hire on 2007-12-04
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3827](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3827)

You need to copy two dlls from a windows installation into the system32 directory of your wine installation to get the game to work: mfc42.dll and d3dx9_25.dll. Also: run the game in WinXP mode. Once the game's running, change your graphics settings so that the "shadows" slider is as low as it can go. You may need to copy all the data from the disks to your harddrive and install from there if the multiple-disk-install gives you problems. I actually installed the game in Windows first, then copied the game folder over to my wine folder. Worked fine once the above dlls were in place.

---

### Post by sourcemorph on 2007-12-05
i noticed that the mfc42.dll was already ther in my system32 folder.. albeit as "MFC42.dll:.. the files r of same size... and yeah i don't have a windows installation.. running only ubuntu. i dont hav any probs if the shadows don;t come (i disabled it) but the character image in the left bottom is weird.. inverted tree!! and yeah when i open the keyboard settings in options i see weird codes for the alphabets eg.

to move forward it is set as "W" but it shows a long unicode kinda thing (squares n lines etc.. weird symbols)... dunno whats wrong.

---

### Post by Dr Kenneth Noisewater III on 2007-12-07
Hey, I just happened to find this tutorial a few days ago and haven't gotten a chance to try it out myself, but here it is:

[http://www.wine-forum.org/showthread.php?p=150#post150](http://www.wine-forum.org/showthread.php?p=150#post150)

I don't have a clue if that will help with your issues at all, but it seemed to get a lot of good responses on that forum.

---

### Post by cogadh on 2007-12-07
Just for clarity sake, that how-to does not actually install DirectX in Wine. Yes, you run the DX redistributable installer, but in the end, you end up telling Wine to only use its own built-in DX, plus the Windows native DX support files. You can accomplish the same results by just copying the DX support DLLs from a Windows installation and overriding them in winecfg. The only thing gained by running the installer is you get a functional DXDiag application, which is relatively useless in Wine anyway.

---

### Post by VinisLentoje on 2008-04-03
Hello,
I don't want to make another topic with a similar name, so:
I have wine 0.9.58 and ubuntu 7.10_x64, just reinstalled it, and Geforce 7600GT.
In my previous ubuntu installation, I was able Lineage II C4. now, when I start it, I get this: 
[IMG]http://img210.imageshack.us/img210/1406/nuotraukasystemerroryi0.png[/IMG]
I haven't posted terminal output, 'cause there's only the very same stuff that was while it was running OK.
What should I do?
And sorry for my bad English.

---

