---
title: "WINE making me = noob :/"
date: 2007-12-30
forum: Wine
---

### Post by mongoose_za on 2007-12-30
Hi THere

I thought i got everything working fine cause of the great Community Docs but when i tried to actually install a .exe file i get this error 

[COLOR="DarkRed"]Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: could not load L"c:\\windows\\system32\\AR70ENU.exe": Module not found[/COLOR]

i figured that within my winecfg, setting up the drives has probably gone  
pear shaped. Or my WINE is not properly installed.  In The Tutorials there are a few registry keys that one can modify but when i goto the location those keys are not even there :/

Help please.. Been at this for 2days..

I'm using Linux Fiesty, no windows installed.
trying to run a basic app like Adobe reader to test and want to actually get Warcraft III Quake III running.

---

### Post by raddellee on 2007-12-30
DId you type "wine -config" into a terminal.

or did you update your sources.list file.

---

### Post by b0rka7a on 2007-12-30
Maybe try with:
```
winebuild
```
, or if winebuild doesn't work:
```
mv ~/.wine ~/.wine-bak
winebuild
```
but as user (not root).

Tell me if this works.

---

