---
title: "[SOLVED] wine switching"
date: 2008-06-13
forum: Wine
---

### Post by soxs on 2008-06-13
I compiled wine 0.9.45 for hardy x86_64 bit myself (to big to attach, ~11 MiB) in order to be able to play/save wc3tft (warcraft 3 the frozen throne) (Switching forward/backward between 0.9.45 and RC as I need).  So now i tried the latest RC and after pruging the RC again, I am unable to install the old version myself. Plx help.

/usr/share/applications/mimeinfo.cache is included in both packages (at least dpkg -i tells me that) So I remove it, but I still get the same nasty error.. same when I put a empty one instead...
any ideas?

But 0.9.58 (with some uggly patches still is installabel aswell as any RC (did not test any versions inbetween))

---

### Post by cogadh on 2008-06-13
Recompile 0.9.46, but specify a prefix path that is different from the default, like /usr/bin/wine0946 (just an example). That way you can have both Wine versions installed at the same time. When you want to use the older version, you just need to specify the command path where you installed it. It is probably also best to use winprefixcreate to make a separate .wine directory just for use with the older version. Using multiple Wine versions with the same .wine directory will lead to bad things, just don't do it.

---

### Post by soxs on 2008-06-13
It's wine 0.945, wine 0.9.46 won't work for warcraft 3/b.net
Is it like: --prefix=/usr/bin/wine0945
or: --prefix /usr/bin/wine0945

---

### Post by cogadh on 2008-06-13
When you run the configure portion of the compile:
```
./configure --prefix=<prefix path>
```

---

### Post by soxs on 2008-06-13
Thx a lot! YOu saved my day (rather night than day :KS)

---

### Post by soxs on 2008-06-14
How do I have to run a program when I have comipled wine with prefix option?
simply winecfg and prefixcreate do not work...
ok, got it ^^ /usr/bin/$YOURPREFIX/bin/winecfg wineprefixcreate wine ...

---

