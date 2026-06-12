---
title: "Wine DirectX Confusion"
date: 2007-12-02
forum: Wine
---

### Post by Ryan Marcus on 2007-12-02
I read an article on linux-gamers.net talking about installing DirectX in WiNE: [http://www.linux-gamers.net/modules/news/article.php?storyid=2334](http://www.linux-gamers.net/modules/news/article.php?storyid=2334).

I'm very confused. I've been using Wine to play Dawn of War, Counter-Strike, and many other DirectX 9 games for quire some time... Isn't DirectX already part of Wine?

---

### Post by cogadh on 2007-12-02
Yes, but there are some DX support files that are not part of Wine's DX9 implementation. Basically, that article describes a roundabout way to do the same thing you can do by copying some specific DX DLL files from Windows into your Wine directory.

---

### Post by Ryan Marcus on 2007-12-02
So it is not worth doing unless you are having problems? You wouldn't get a performance boost or anything from installing the actual DirectX 9?

---

### Post by avik on 2007-12-02
You should be fine if you're not having problems.  I would just say don't take the chance of messing up a working setup.

---

### Post by cogadh on 2007-12-02
Basically, no its not really worth doing unless whatever game you are trying to run specifically needs them. I do copy the d3dx9_##.dll and d3dx10_##.dll files into my Wine directory by default, since those are the only ones that the Wine devs say might actually help, but I have only found one or two games that actually make use of them. The games still work without them, though. Since the Wine DX files already support almost all of the core DX functions, you would probably only see some minor or incidental performance improvements.

---

