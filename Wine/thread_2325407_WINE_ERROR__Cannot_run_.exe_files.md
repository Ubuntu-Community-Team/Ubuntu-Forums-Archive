---
title: "WINE ERROR : Cannot run .exe files"
date: 2016-05-22
forum: Wine
---

### Post by infinity2 on 2016-05-22
Heya,

I just installed wine onto Hardy and I have wine tricks and all that but when i try opening a .exe files by double clicking it or using terminal it just doesn't open.

I have installed Razer Synapse, but when I go in .wine/drive_c/Program_Files/Razer/Synapse/RzSynapse.exe, and I run the file, it does nothing.
I tried to open it in the terminal and it shoes me this :

```
felix@predator:~/.wine/drive_c/Program Files/Razer/Synapse$ wine RzSynapse.exe
Missing method .ctor in assembly C:\Program Files\Razer\Synapse\RzSynapse.exe, type System.Windows.ThemeInfoAttribute
Can't find custom attr constructor image: C:\Program Files\Razer\Synapse\RzSynapse.exe mtoken: 0x0a00000e

Unhandled Exception:
System.IO.FileNotFoundException: Could not load file or assembly 'PresentationFramework, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies.
File name: 'PresentationFramework, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'
[ERROR] FATAL UNHANDLED EXCEPTION: System.IO.FileNotFoundException: Could not load file or assembly 'PresentationFramework, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies.
File name: 'PresentationFramework, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'
felix@predator:~/.wine/drive_c/Program Files/Razer/Synapse$

```

Anyone have any idea? I'm not very experienced with Wine :)

Thanks!

---

### Post by lisati on 2016-05-22
Hardy (8.04) is well past its end-of-life. It might be easier for us if you used a more up-to-date version of Ubuntu.

---

