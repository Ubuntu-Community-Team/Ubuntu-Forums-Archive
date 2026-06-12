---
title: "Pointing Game to install directory (C&amp;C Tiberian Sun)"
date: 2012-01-19
forum: Wine
---

### Post by Sarlix on 2012-01-19
Hi - I'm fairly Linux illiterate and wondered if someone could give me a hand with this please.

I installed C&C Tiberian Sun (the free version from EA) via WINE and updated it with latest patch - but it asks for me to insert the CD. I found the Registry Editor and the line that needs to be edited to point the game to the 'game.exe' But for some reason it's not working.

I'm not so much bothered about getting the game to run as I am trying to figure out why this won't work...I can't stop thinking about it!

 This is the default install path string:

```
"InstallPath"="C:\\Program Files\\EA Games\\Command & Conquer The First Decade\\Command & Conquer(tm) Tiberian Sun(tm)\\SUN\\SUN.exe"
```And this is what I changed it to (where my SUN.exe is)

```
"InstallPath"="C:\\users\\lcars\\Local Settings\\Application Data\\Command and Conquer Tiberian Sun\\SUN.exe"
```I'm thinking it could be one of a few reasons why it won't work - wrong type of back slash or too many or incomplete directory path...I'm really not sure. I would appreshate if someone could help me to understand this. Thanks  :)

This is the full path to where the game exe is:

```
/home/lcars/.wine/drive_c/users/lcars/Local Settings/Application Data/Command and Conquer Tiberian Sun
```EDIT: This is the full reg file:

```
Windows Registry Editor Version 5.00 
 
[HKEY_LOCAL_MACHINE\SOFTWARE\Westwood] 
 
[HKEY_LOCAL_MACHINE\SOFTWARE\Westwood\Internet Registration] 
"InstallPath"="C:\\Program Files\\EA Games\\Command & Conquer The First Decade\\Command & Conquer\\REGISTER.EXE" 
"Name"="Internet Registration" 
"SKU"=dword:000003ea 
"Version"=dword:00010000 
 
[HKEY_LOCAL_MACHINE\SOFTWARE\Westwood\Register] 
"InstallPath"="C:\\Program Files\\EA Games\\Command & Conquer The First Decade\\Command & Conquer(tm) Tiberian Sun(tm)\\SUN\\SUN.exe" 
"Name"="Internet Registration" 
"SKU"=dword:00007e00 
"Version"=dword:00010001 
 
[HKEY_LOCAL_MACHINE\SOFTWARE\Westwood\Tiberian Sun] 
"Serial"="0548856964050989847438" 
"InstallFromPath"="C:\\" 
"InstallPath"="drive_c/users/lcars/Local Settings/Application Data/Command and Conquer Tiberian Sun/SUN.exe" 
"Name"="Command & Conquer Tiberian Sun" 
"SKU"=dword:00001200 
"Version"=dword:00010000 
 
[HKEY_LOCAL_MACHINE\SOFTWARE\Westwood\WOLAPI] 
"InstallPath"="C:\\Program Files\\EA Games\\Command & Conquer The First Decade\\Internet\\wolapi.dll" 
"Name"="Shared Internet Components" 
"SKU"=dword:00007f00 
"Usage"=dword:00000001 
"Version"=dword:00010006 
 
[HKEY_LOCAL_MACHINE\SOFTWARE\Westwood\WOLAPI\4608] 
 
[HKEY_LOCAL_MACHINE\SOFTWARE\Westwood\WWAudio]
```

---

