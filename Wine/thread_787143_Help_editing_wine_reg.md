---
title: "Help editing wine reg"
date: 2008-05-08
forum: Wine
---

### Post by mindwip on 2008-05-08
Hello, i would really be happy if i can play supcom on linux then i wont have to go to XP any more. Good news is i installed the game Supreme Commander and can get it to open with out any problems but it crashs soon afterwards. It seems this is a common problem and there are two "easy" fixes. But i am having problems with them. They want you to edit the wine reg but i have no idea how to add the strings like they want. Could some one please help me-either point me to a guide on it or explain it more then what they give.  I can get into the wine reg easy enough but my knowledge stops there.

THanks  

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7038](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7038)

 *  Create the registry string HKCU/Software/Wine/Direct3D/OffscreenRenderingMode and set it to fbo

    * Launch the game with wine SupremeCommander.exe

If Wine/SupCom complains about missing files make sure you're cd'ed into Supreme Commander/bin before launching.
You may also need d3dx9_31.dll. Get it from a site like dll-files.com and put it into system32
If you're still running into problems, try starting the game with the /novalidate switch

Also, if SupCom complains about insufficient video memory or crashes very early into the game,
try creating the string HKEY_CURRENT_USER\Software\Wine\Direct3D\VideoMemorySize with a value >64, e.g. 128

---

### Post by cogadh on 2008-05-08
Okay, here goes:
[LIST=1]
[*]Open a terminal and type "regedit". This will launch the Wine registry editor, which is identical to the Windows registry editor. [*]Once you have the registry editor open, browse through the file tree to HKEY_CURRENT_USER/Software/Wine key
[*]Right-click on the Wine key in the file tree and select New > Key. Name the new key "Direct3D".
[*]Right-click in the right hand pane of the registry editor and select New > String Value. Name the new string "OffscreenRenderingMode"
[*]Double-click on the new string and enter "fbo" in the Value data field. Click OK
[/LIST]
That takes care of the first new string. To add the second one, repeat steps 4 and 5, replacing the name and data info with the video memory size info. Make sure you don't set the video memory size to a value that is higher than your video card's actual memory, bad things will happen.

---

### Post by mindwip on 2008-05-08
Thanks so much i was looking for the direct3d folder and could not find it! Did not know i had to make it


GAME WORKS GREAT!!!!




the only bad thing is the mouse sort of blinks as i move it. But i am getting used to it

---

