---
title: "Wine .NET installation failed"
date: 2014-01-20
forum: Wine
---

### Post by Toxic_condoms on 2014-01-20
So I'm completely new to linux and I wanted to install OSU!([http://osu.ppy.sh/](http://osu.ppy.sh/)) which requires .NET so when I searched up how to install .NET and followed various tutorials, the .NET setup fails each time
[ATTACH=CONFIG]249628[/ATTACH]
What I did was
```

rm -r ~/.wine
WINEARCH=win32 winecfg
rm -r ~/.cache/winetricks/dotnet20
winetricks dotnet20

```
Help appreciated :)

---

### Post by Mark Phelps on 2014-01-21
Sorry, but different .net versions have difference success ratings in Wine. .Net 2.0 is rated Silver -- meaning that major functions will not work.  You're welcome to read the info on the linked page to see if anything there helps: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586")

---

