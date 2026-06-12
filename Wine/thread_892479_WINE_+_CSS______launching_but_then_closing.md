---
title: "WINE + CSS      launching but then closing"
date: 2008-08-17
forum: Wine
---

### Post by Yuck on 2008-08-17
Hi,

Just installed WINE and Steam+CSS. I've checked several guides and still struggling to get CSS to run. Here's the terminal output from trying to run from the command line with instructions found from a link from winehq, any help would be much appreciated.

```
barry@barry-desktop:~$ #!/bin/bash
barry@barry-desktop:~$ WINEDEBUG=fixme-all wine C:/Program\ Files/Valve/Steam/Steam.exe -fullscreen \
>     -width 1280 -height 1024 -applaunch 240 \
>     -heapsize 512000 +map_background none "$@"
CellID: Fetching server list from CSDS. . .
CellID: CSDS returned 168 servers.
CellID: Connecting to 69.28.140.242:27031. . .
CellID: Connect to 69.28.140.242:27031 took 228 MS
CellID: Nothing beat our old best time of 65 MS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
CellID: Connecting to 87.248.209.212:27031. . .
CellID: Connect to 87.248.209.212:27031 took 66 MS
CellID: Nothing beat our old best time of 65 MS
```

---

### Post by Yuck on 2008-08-18
Anyone any ideas?

Steam appears to be running just fine, same happens when I launch CSS from steam. I get the slash screen (fullscreen) of the 2 CTs and "loading" text then it drops me back to my desktop.

---

### Post by Eviljim on 2008-08-19
Im by no means a expert in this area, but are you using an ATi card by any chance?

If so, before you load the game from the steam gui, you can specify advanced loading options. I added -directx 81 to the command box, and it allowed me to run TF2 ok.

Just something for you to try. Of course if your not using an ATi card, then not sure if that would work.

---

