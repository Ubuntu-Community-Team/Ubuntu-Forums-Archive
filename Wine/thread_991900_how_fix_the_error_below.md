---
title: "how fix the error below"
date: 2008-11-24
forum: Wine
---

### Post by Pegasus_from_UA on 2008-11-24
please tell me how to fix next:
```
$ '/media/media2/WINE/Program Files/You Are Empty/you_are_empty.exe'
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
err:module:attach_process_dlls "ds2kernel.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"G:\\Program Files\\You Are Empty\\you_are_empty.exe" failed, status c0000005

```
I have installed DX9 absolutely successful. I also installed vcrun2005spi via the winetricks.
```
Package: wine
Status: install ok installed
Priority: optional
Section: otherosfs
Installed-Size: 57060
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 1.1.9~winehq0~ubuntu~8.04-0ubuntu1
```
Any idea ?

---

### Post by cogadh on 2008-11-24
You really don't need to install DirectX in Wine, it already has its own DirectX. In fact, doing so can break Wine, though that doesn't appear to be the issue here. 

The error you are encountering is likely because of the copy protection on the game. Unfortunately, not all copy protection schemes are supported in Wine, so you will probably need to use a cracked executable to run the game. Don't ask where or how to get a crack on these forums, the discussion of illegal software is not tolerated here.

---

### Post by Pegasus_from_UA on 2008-11-25
Thanx for the reply.
> **cogadh said:**
> You really don't need to install DirectX in Wine, it already has its own DirectX.
I  tried use Wine's own DirectX but the same error appeared.
About installation  DirectX 9 under wine.
Have a look - [http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2](http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2)
> 8.1. Does Wine support DirectX? Can I install Microsoft's DirectX under Wine?

Wine itself provides a DirectX implementation that, although it has a few bugs left, should run fine. Wine supports DirectX 9.0c at this time. Plans for DirectX 10 are underway. 
> **cogadh said:**
> 
The error you are encountering is likely because of the copy protection on the game. Unfortunately, not all copy protection schemes are supported in Wine, so you will probably need to use a cracked executable to run the game. Don't ask where or how to get a crack on these forums, the discussion of illegal software is not tolerated here.
The game I got is already cracked. Also I tried to use NoCD (*.exe file + *.dll) but it gives nothing.

---

### Post by cogadh on 2008-11-25
I am well aware of the DX status in Wine. You really should have included the rest of the quote from that FAQ answer:
>  **If you attempt to install Microsoft's DirectX, you will run into problems.** It is not recommended nor supported by Wine HQ to attempt this. You can install the runtime, but it will not run. The runtime needs access to the Windows drivers, and Wine cannot access them for obvious reasons. The only native Microsoft DLLs that could be useful anyway are the d3dx9_xx.dll type ones, and these require you to accept Microsoft's license. Additionally these DLLs are now part of the Wine tree. So, as Wine improves these DLLs will only become less relevant.

That said, there are some guides out there which describe how you can install Microsoft's DirectX. I reiterate: It is not recommended nor supported by Wine HQ to attempt this. Furthermore it is considered off topic in Wine HQ support mediums (such as the forums). Please use a clean Wine configuration folder before seeking help. (You may need to rm -rf ~/.wine and re-install your Windows applications.)
That being said, I still believe this is a copy protection issue (a particular quirk of StarForce copy protection). However, since you fully admit that you obtained an illegally cracked version of the game, I don't feel that I can provide any further help without violating the forum rules.

---

