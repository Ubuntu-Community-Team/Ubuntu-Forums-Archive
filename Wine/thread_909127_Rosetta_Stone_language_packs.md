---
title: "Rosetta Stone language packs"
date: 2008-09-03
forum: Wine
---

### Post by Brigham on 2008-09-03
I've read through this forum and AppDB and have done all of the tricks, tips and hints suggested in order to help Rosetta Stone recognize my language packs.  So far I'm out of luck.  

Using:
Wine 1.1.3
Rosetta Stone 2.0.8.1a
Hardy Heron

Rosetta Stone fails to find my language packs.  I have mounted an .iso of the cd to a directory which is symlinked to a drive in WINE.  I have also mounted a folder containing the contents of the CD as a drive.  

WINE recognizes all of these mounted items, but Rosetta still fails to find the language packs.

Am I doing something wrong or am I nerfed?  Fixes that work for other people (mounting the .iso) don't do a dang thing for me.  Please help-- this is quite frustrating (I've put 10 hours into this problem already with no return).  

Thanks for any help.

```

*<< As I start the program >>*
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpEA600.FOT",L"C:\\windows\\temp\\AAX6a8.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpCB600.FOT",L"C:\\windows\\temp\\AAX6b9.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpFC600.FOT",L"C:\\windows\\temp\\AAX6c7.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp2E600.FOT",L"C:\\windows\\temp\\AAX6db.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp2F600.FOT",L"C:\\windows\\temp\\AAX6ee.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp20700.FOT",L"C:\\windows\\temp\\AAX6fe.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp41700.FOT",L"C:\\windows\\temp\\AAX70e.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp42700.FOT",L"C:\\windows\\temp\\AAX721.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp83700.FOT",L"C:\\windows\\temp\\AAX72f.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp64700.FOT",L"C:\\windows\\temp\\AAX743.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp95700.FOT",L"C:\\windows\\temp\\AAX751.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp89700.FOT",L"C:\\windows\\temp\\AAX790.tmp",(null)): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
*<< This is where I quit the program >>*
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:shell:DllCanUnloadNow stub

```

---

### Post by Thelasko on 2008-09-04
[Read this.]("http://ubuntuforums.org/showthread.php?t=877975")

---

