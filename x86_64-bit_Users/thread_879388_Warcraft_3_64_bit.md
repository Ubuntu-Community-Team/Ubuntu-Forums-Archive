---
title: "Warcraft 3 64 bit"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by revenant138 on 2008-08-04
hallo all,

Trying to get Warcraft 3 to run on my 64 bit hardy kubuntu setup. Have WoW working fine, if it makes a difference.

I can't get the installer to run. When I run the autoplay or install file off the CD, I get the error message 

> Error in script file SetupDat/GenDefs.ins, line 23: unrecognized registry type.

Ive googled around and searched the forums and I cant seem to find the error or anything on editing registry entries.

Any help would be great, my little brother moved away and he wants to play DotA with me really bad :cry:

---

### Post by /////// on 2008-08-04
I've never had this error before but you can try re-installing WINE. Just go to synaptic, find WINE, mark for full uninstallation, then go to your home drive on nautilus, enable show hidden files (With CTRL+H) delete the .wine folder, go back into synaptic and reinstall WINE. A couple of days ago the warcraft 3 installation went weird for me aswell (just kept showing an error about the start menu and registry) and after I re-installed WINE it worked fine.

---

### Post by obsrv on 2008-08-04
I have managed to install Warcraft3 on my KUbuntu AMD64, but it didn't run, only movies I saw.

---

### Post by Kilz on 2008-08-04
The [Wine Application Database]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1177") is your friend.

---

### Post by Stunts on 2008-08-04
Try to rename the war3 movies folder into something else... Like "movies.backup".
It worked for me some time ago...
Good luck.

---

### Post by revenant138 on 2008-08-04
Thanks for the replies (nice to see you again Kilz :D) Here are a few thoughts:

- I'm really reluctant to reinstall wine because it took a lot of work to get WoW working. I'd be willing to do it if there's a compelling reason to, though.

- I looked at the wine AppDB first thing, didn't see much like the problem I had. 

- Does anyone think this could be a problem with the registry entries for Wow confusing the WC3 installer? My gut's telling me its something to do with that. I think I saw something called PlayOnLinux that will let you use separate registry info for each program. Another thing I'm thinking would be to delete all the existing registry entries for Blizzard and try to install, then put them back in to make WoW happy. 

- The file GenDefs isn't anywhere I can find on my computer using locate after updatedb, wtf?

Thanks again for all the help :D

---

### Post by revenant138 on 2008-08-04
Hey again,

I went to playonlinux's site, and they have install scripts for wc3. I got the game to install and am installing the expansion now. I checked the game and got into it fine (crashed when I got to a movie, but we all know I'm in it for DotA anyway)

On a tangent, I gotta say I'm more impressed with playonlinux than I have been with anything on 'nix in a long time. Its incredibly easy. I recommend anyone who wants to run games on linux try this if they havent. 

Thanks for the help, I will post again if this doesn't work.

---

### Post by Kilz on 2008-08-04
> **revenant138 said:**
> Hey again,

I went to playonlinux's site, and they have install scripts for wc3. I got the game to install and am installing the expansion now. I checked the game and got into it fine (crashed when I got to a movie, but we all know I'm in it for DotA anyway)

On a tangent, I gotta say I'm more impressed with playonlinux than I have been with anything on 'nix in a long time. Its incredibly easy. I recommend anyone who wants to run games on linux try this if they havent. 

Thanks for the help, I will post again if this doesn't work.

Plays on linux installs games in in their own wine setup. That way settings for one game do not effect others. I really like it, you can even install different wine versions and then select which version to run an application with. Use the registry settings from the wine application database, and rename the movie folder and it should work. At least I had to do it that way.

---

### Post by Stunts on 2008-08-05
Glad you got it all sorted out. I had totaly forgotten to mention PoL.
It's great because it installs games easily, and it lets you run the best wine version for said game. Resgressions are usually a pain in the... You know what I mean. =-)
It's just too bad that it's scripts are still sort of limited. But I suppose that's changing quickly.

---

### Post by soxs on 2008-08-05
> **Stunts said:**
> Glad you got it all sorted out. I had totaly forgotten to mention PoL.
It's great because it installs games easily, and it lets you run the best wine version for said game. Resgressions are usually a pain in the... You know what I mean. =-)
It's just too bad that it's scripts are still sort of limited. But I suppose that's changing quickly.

It won't let me compile wine 0.9.45 on my hardy x86_64 machine (phenom patch), without doing manually (evil) hacks.

I had no luck using PoL, just got pissed and erased the whole fuss again, after I tried to install wc3 the third time -.- (incl. Expansionpack)

btw. I always get that error: (o matter which program if steam, wc3 or any other)
```

/usr/share/playonlinux/playonlinux --run "Steam"
PlayOnLinux v3.0.8

Checking python : 				[ Ok ]
Steam: line 5: cd: /home/xxxxxx/.PlayOnLinux/wineprefix/Steam/drive_c/Program Files/Steam/: No such file or directory
wine: could not load L"C:\\windows\\system32\\steam.exe": Modul nicht gefunden

```

---

