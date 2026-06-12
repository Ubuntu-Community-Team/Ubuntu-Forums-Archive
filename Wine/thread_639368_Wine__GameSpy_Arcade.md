---
title: "Wine / GameSpy Arcade"
date: 2007-12-13
forum: Wine
---

### Post by enbuyukfener on 2007-12-13
Using latest WINE version 0.9.50~winehq0~ubuntu~7.10-1

Virtual desktop opens and closes, no sign of application window opening.

Terminal output:

$wine Aphex.exe
```
fixme:system:SystemParametersInfoW Unimplemented action: 4132 (SPI_GETDROPSHADOW)
[above error 7 times more]
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:shdocvw:PersistMemory_Load (0x14f5f8)->(0x1004b41c 9c)
fixme:shdocvw:OleObject_Close (0x14f5f8)->(1)
fixme:font:WineEngRemoveFontResourceEx :stub
[above error 5 times more]

```

No registry edits, settings messed around with etc. Sound switched to ALSA and a few DirectX/DirectPlay related DLLs added (none overriden). Tried with Win98, Win2000, WinXP modes and using virtual desktop.

Other apps installed: Age of Empires 2 + Expansion

Any suggestions?

Note: googling "class {304ce942-6e39-40d8-943a-b913c40c9cd4}" yielded some results among others' output among other applications but could not find a solution.

---

### Post by enbuyukfener on 2007-12-21
I think the problem was related to Gecko.

Seen though this thread is already near the top of Google searches, here is my solution:

Use IE6 from [ies4linux]("http://www.tatanka.com.br/") and disable any security settings to use ActiveX.

Get [gecko for wine]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=195269") and cabextract it to somewhere in ~/.ies4linux/ie6/drive_c/Windows/ and reflect this path in HKCU\Software\Wine\MSHTML\[version]\GeckoPath through regedit (run wine regedit from a command line)

Use the downloader and installer via the [GameSpy Arcade]("http://www.gamespyarcade.com/") site. It will install to the virtual C:\ that was created with ies4linux.

It should show in the apps menu, if not:
```
cd ~/.ies4linux/ie6/drive_c/Program\ Files/GameSpy\ Arcade
wine Aphex.exe
```

---

### Post by cogadh on 2007-12-21
Do you really need ies4linux to do this? You can install the Gecko engine in Wine then create registry entires to mimic the presence of IE 6, which should allow GameSpy to run normally.

---

