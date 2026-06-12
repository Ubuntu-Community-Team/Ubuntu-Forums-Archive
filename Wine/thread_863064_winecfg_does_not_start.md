---
title: "winecfg does not start"
date: 2008-07-18
forum: Wine
---

### Post by nkarakos on 2008-07-18
Hi, I am using  wine 1.1.1 in Ubuntu 8.04. After installing and testing some software (Originlab origin 7.5) which included several crashes and importing some dll files winecfg stopped responding. I uninstalled all the wine software, I uninstalled and reinstalled wine, I upgraded to 1.1.1 but nothing.
If I use the console to run wineconfig I get this error message:

nikolas@nikolas-desktop:~$ winecfg
err:module:import_dll Library comdlg32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135

what should I do?

---

### Post by dfreer on 2008-07-18
Did you try deleting your ~/.wine/ folder (this would delete anything you installed as well, so if you don't want to lose it you could just rename it instead)? 

Also, when you uninstalled wine, did you purge the configuration files as well?

---

### Post by nkarakos on 2008-07-18
Thank you for the assistance. I reinstalled wine and it worked. I dont know what I should do if I did not want to sacrifice all the .wine directory

---

### Post by evets25 on 2008-07-18
THis kind of thing is why I tell my games to install in "~/storage/games" rather than the wine directory. This way, I can nerf my wine directory to get a clean install, and still keep my installed programs intact.

---

### Post by dfreer on 2008-07-20
> **evets25 said:**
> THis kind of thing is why I tell my games to install in "~/storage/games" rather than the wine directory. This way, I can nerf my wine directory to get a clean install, and still keep my installed programs intact.

Better yet, I like to keep my default .wine folder for programs that don't install anything (like say an utorrent.exe or something), and then for the games/programs that I install I create a separate wine folder for each like so:
```
WINEPREFIX="$HOME/.mygame" winecfg
WINEPREFIX="$HOME/.mygame" wine *Install.exe*
```

If one program borks up, simply delete it's folder and reinstall, the rest of your programs will still run fine.

---

