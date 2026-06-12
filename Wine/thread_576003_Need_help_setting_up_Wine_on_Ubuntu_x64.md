---
title: "Need help setting up Wine on Ubuntu x64"
date: 2007-10-14
forum: Wine
---

### Post by NDT on 2007-10-14
So i just got Ubuntu 7.04 like 3 days ago and it rocks (but you know that already) and i want to ditch windows but before i can do that i must get WoW and Steam (along with Half Life 2, portal, CS:S and Team Fortres 2) to work with Wine under Ubuntu x64. I did try installing the 32 bit version of ubuntu but i cant get past the main menu of the installation cd due to some Kernel problem.

anyway i cant get steam to work at all and when i try and load wow i get ```
t@unknown:~$ wine c:\\wow.exe
err:module:import_dll Library DivxDecoder.dll (which is needed by L"C:\\wow.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\wow.exe" failed, status c0000135

```
anyone know how to fix this at least and maby drag me in the right direction to geting steam and it's aps to work? i am willing to help gat any info you need about my system (just tell me the command to get it)

thanks in advance

---

### Post by TNakos on 2007-10-16
it should be the same just a different repo

---

### Post by cogadh on 2007-10-16
Missing DLL messages like that usually happen when you try to run a game without changing directories to the game's install directory first:
```
cd ~/.wine/drive_c/Program\ Files/<WoW directory>/
wine wow.exe
```
Obviously correct the cd path for the actual install path.

---

