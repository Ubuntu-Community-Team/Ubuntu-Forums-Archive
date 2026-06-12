---
title: "Wine errors?"
date: 2008-09-22
forum: Wine
---

### Post by metacognition on 2008-09-22
Hey guys, I finished a fresh install on an old laptop and I inst-ed Wine, so I want to fire up iexplorer.exe. I think it is Internet Explorer, but I'm not sure.

So in the case it is, I want to launch it. Then I get these error messages:
```
grace@grace-laptop:~$ sudo wine iexplorer
[B]err:winedevice:ServiceMain driver L"Cdr4_2K" failed to load
err:winedevice:ServiceMain driver L"Cdralw2k" failed to load[/B]
fixme:atl:AtlModuleInit SEMI-STUB (0x10013248 0x10011930 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10012fb0 0x10012210 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10026f40 0x10026318 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x1000f750 0x1000f040 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x1001a720 0x10019408 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x1006de68 0x1006c898 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10045960 0x10044708 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10010f50 0x10010040 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10010560 0x10010040 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x1000bc08 0x1000b030 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10057070 0x1004c830 0x10000000)
wine: could not load L"C:\\windows\\system32\\iexplorer.exe": Module not found

```
[SIZE="1"](Bolded for effect.)[/SIZE]

Am I missing anything?
Thanks in advance!

---

### Post by Tatty on 2008-09-22
iexplore.exe that comes with a default wine install is not internet explorer, it is just a module that sits in place of internet explorer to deal with any applications which may try to access it.

IE is embedded quite deeply into windows (down to the kernel i think) and so providing this file is important for wine to work.

If you want to install internet explorer in wine then the best I can do is point you to the wine entry [http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)

And a page with scripts to install various versions of IE in wine(which the wine entry reccomends you use):

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by seeker5528 on 2008-09-22
> **metacognition said:**
> sudo wine iexplorer

*shudder* [-o<

The iexplorer that is built in to wine uses gecko, which I think is supposed to install automatically if something wants IE functionality when it is run, but that seems not to happen much of the time.

The easiest way to deal with that is [winetricks](http://wiki.winehq.org/winetricks).

Later, Seeker

---

