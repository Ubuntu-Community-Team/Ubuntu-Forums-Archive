---
title: "Steam on Wine - can't login"
date: 2013-05-22
forum: Wine
---

### Post by Zahc on 2013-05-22
I downloaded steam with wine, clicked on the icon, and tried to log in to my account. However when I type my username/pass into the window nothing happens, instead whatever I type is seen in a little white box in the bottom right of my screen. What am I doing wrong? I had a windows os yesterday, and I am trying to download old games that I bought on steam but aren't supported on linux.

---

### Post by Lightning Dragon on 2013-05-23
Hi,

Do you mean the text/input box is still blank (white) while you are typing? If so, please try this; go into winecfg > libraries > add "DWrite" and then edit it and disable it or run a command "wine /path/to/Steam.exe -no-dwrite". You can also go into regedit and edit the DWrite value to 0 to disable it like so;


[LIST=1]
[*]Run wine regedit.
[*]Navigate to HKEY_CURRENT_USER\Software\Valve\Steam in the tree on the left.
[*]Look for a DWriteEnable value in the pane on the right.  If it doesn't exist, add it as a DWORD value.
[*]Set DWriteEnable to 0 and exit out of the registry editor.
[/LIST]


This is usually used if you do not have the latest Wine which is 1.5. If this isn't your problem, would you mind taking a screenshot of the problem?

---

### Post by CatKiller on 2013-05-23
PlayOnLinux has a Steam prefix that worked for me. PlayOnLinux is a set of ways of running different applications in Wine that require particular settings, in case the setup you need to get one application working are different to those you need for another.

---

### Post by Zahc on 2013-05-23
fixed, went into configure wine and checked enable a virtual desktop

---

