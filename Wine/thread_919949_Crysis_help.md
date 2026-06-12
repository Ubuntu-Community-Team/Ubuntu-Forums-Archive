---
title: "Crysis help"
date: 2008-09-14
forum: Wine
---

### Post by superarmy on 2008-09-14
I already have fully installed Crysis, but when I try Play it the installer screen disappears and nothing further happens. When running in terminal I get


> samuel@hinds-desktop:~$ fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x52a520,0x00000004,0x52a51c) Unknown information class
 

Any ideas?

---

### Post by Codemastadink on 2008-09-14
Try doing this HowTo, It should help. I had problems like this when i tried to get crysis going. I couldnt figure out how to do some things in the how to so idk i just kinda gave up. If u can figure it out that would be tight, and le tme know how to do the stuff, the things like the patch and the .dll files and stuff confused me.

```
http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107

Howto:
If you're using ATI hardware there may be even worse problems since their drivers suck (for now)

    * Compile Wine 1.1.0 with this patch to get it to do "proper" mouse warping
    * Put d3dx9_36.dll and XINPUT1_3.dll in windows/system32. You can get them from a DLL site like dll-files.com
    * Install the game and use a Crack on it 
    * Enable OffscreenRenderingMode=fbo. Look here under the Direct3D section to see what I mean
    * Set Shaders to High, else you will get graphical problems
    * If you have problems with insane HDR lighting (believe me, you will), open a console and issue con_restricted 0 and r_glow 0

```

---

