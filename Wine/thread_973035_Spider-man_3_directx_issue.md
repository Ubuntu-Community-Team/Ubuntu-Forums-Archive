---
title: "Spider-man 3 directx issue"
date: 2008-11-06
forum: Wine
---

### Post by Trap3d on 2008-11-06
so im new with linux and wine installed about a week ago... everything seems to work tough when i launch spiderman an error pops out saying i need to get directx 9.0c i have read its in wine but how to activate it?

---

### Post by cogadh on 2008-11-06
It does not need to be "activated", it is an integral part of Wine (i.e. it is always "active"). Chances are, the game is looking for some DX support DLL that Wine does not have. Run the game from the terminal and post the error output here, it may contain some clues as to what the game is trying to actually do.

---

### Post by Trap3d on 2008-11-06
i posted im cinda new ^^ i need the command to launch it in terminal... :D

nvm i thing i got it if its sudo wine game.exe then it returns wine: /home/trap3d/.wine is not owned by you
Edit: so i launched it trough wine not gona post the long launch thing but the outcome is :
wine: Call from 0x7b845450 to unimplemented function d3dx9_36.dll.D3DXCreateTextureFromFileInMemory, aborting

---

### Post by cogadh on 2008-11-06
Never use "sudo" to run Wine. Wine is meant to be run with just user permissions, not administrator permissions. Running Wine with administrator permissions can lead to significant problems, especially if you accidentally run some kind of Windows malware, like a virus or spyware.

Well, the entire thing is usually helpful, even if long (use the forum [code] tags to make the post a little more managable). Fortunately, it looks like you picked up on the missing DLL that may have caused the issue. The d3dx9_##.dll and d3dx10_##.dll files are DirectX support libraries that are not part of Wine. You can copy them from an exisiting Windows installation into the /home/<username>/.wine/drive_c/windows/system32 directory, then apply an override in winecfg for each support library you copy (there are 23 of them in total). That should eliminate at least that one "missing DLL" error and may make the game work, but as often happens with Wine, it may also introduce new errors that will need to be addressed.

---

### Post by Trap3d on 2008-11-06
omg could you plz explain that normaly as first i dont even quite know how to override or whatsovere i dont even realy know what that means :P so could you tell me what to do exactly?
So it think i took care of that... i opend Configure wine and in libraries added d3dx9_36.dll now i can launch the game but it returns as a white screen...

---

### Post by cogadh on 2008-11-06
Okay:
[LIST=1]
[*]Assuming that you have an existing Windows installation somewhere, copy d3dx9_24.dll through d3dx9_39.dll and d3dx10_33.dll through d3dx10_39.dll files from C:\Windows\System32
[*]Place the copied files into /home/<username>/.wine/drive_c/windows/system32 on your Ubuntu machine. the ".wine" directory is hidden, so you will need to unhide it by hitting CTRL+H in the file browser.
[*]After copying the files, run the Wine configuration utility and go to the "Libraries" tab. Add an override for each DLL you copied and set each override to "Native"
[*]Click OK to close out of the config utility, then try running the game again.
[/LIST]

---

### Post by Trap3d on 2008-11-06
so i did everything exept getting d3dx10_39.dll :/ i cant find it anywhere on the net and i cant acces my 81.2 GB media hdd (my other partition) i cant get to those files everyitime i enter password for autentification shows Cannot mount volume for some odd reason yesterday it worked so i would appreciate if someone uploaded d3dx10_39.dll
Tnx~

---

### Post by cogadh on 2008-11-06
Are you still having the white screen issue? If so, run the game from the terminal again and post the full output.

---

### Post by Trap3d on 2008-11-06
nope no white screen normal graphics but a few still mising like black areas and eyes and weps only for the characters im asuming i need d3dx10_39 for that to work

---

### Post by cogadh on 2008-11-06
Doubtful. The d3dx10_##.dll files are DirectX 10 backwards compatibility files. Games that are made for DirectX 9 don't actually use them, they are really only needed for DX10 games that are run on platforms that only have DX9.

I checked Wine's application database and it appears that SM3 doesn't really work fully with Wine, or at least it didn't the last time anyone tested with Wine 1.0-rc4:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12487](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12487)

---

### Post by Trap3d on 2008-11-06
ok yet after full d3dx9_## you told me to get it had turned to black screen everytime i start but after i added d3dx10_33-38 it worked with graphics tough not complete...

---

### Post by cogadh on 2008-11-06
Odd. Is SM3 a game with DX10 capabilities?

---

### Post by del_diablo on 2008-11-06
You could attempt to actually intall direct X(LOL), i managed to get in 9.0c some time before(form a CD, heroes 5).
But i think myself this is a lol-option just for kicks, or like "screw that, WORK!!!!" kind of thingy.

---

### Post by Trap3d on 2008-11-07
> **cogadh said:**
> Odd. Is SM3 a game with DX10 capabilities?

not really now i realized it could be cause i didnt put to native before and after i put to native it worked... so proly didnt require d3dx10_xx's and yea tnx for all the help... i guess ill have to wait for a maintainer to show up for spiderman  :)

> You could attempt to actually intall direct X(LOL), i managed to get in 9.0c some time before(form a CD, heroes 5).
But i think myself this is a lol-option just for kicks, or like "screw that, WORK!!!!" kind of thingy. 


read under... its not recomended to install directx on ubuntu with wine as it can screw up
```
8.1. Does Wine support DirectX? Can I install Microsoft's DirectX under Wine?

Wine itself provides a DirectX implementation that, although it has a few bugs left, should run fine. Wine supports DirectX 9.0c at this time. Plans for DirectX 10 are underway.

/!\ If you attempt to install Microsoft's DirectX, you will run into problems. It is not recommended nor supported by Wine HQ to attempt this. You can install the runtime, but it will not run. The runtime needs access to the Windows drivers, and Wine cannot access them for obvious reasons. The only native Microsoft DLLs that could be useful anyway are the d3dx9_xx.dll type ones, and these require you to accept Microsoft's license. Additionally these DLLs are now part of the Wine tree. So, as Wine improves these DLLs will only become less relevant.

That said, there are some guides out there which describe how you can install Microsoft's DirectX. I reiterate: It is not recommended nor supported by Wine HQ to attempt this. Furthermore it is considered off topic in Wine HQ support mediums (such as the forums). Please use a clean Wine configuration folder before seeking help. (You may need to rm -rf ~/.wine and re-install your Windows applications.)

```

---

