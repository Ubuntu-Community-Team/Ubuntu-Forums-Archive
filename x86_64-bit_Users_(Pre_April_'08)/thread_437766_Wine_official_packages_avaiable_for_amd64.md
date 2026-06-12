---
title: "Wine official packages avaiable for amd64"
date: 2007-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by hexion on 2007-05-09
Wine devs finally give support for 64 bit systems. Well, actually just for Ubuntu Feisty.

**More info:**
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

**Repositories:**
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

**Direct link:**
[http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.36~winehq0~ubuntu~7.04-3_amd64.deb]("http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.36%7Ewinehq0%7Eubuntu%7E7.04-3_amd64.deb")
[http://wine.budgetdedicated.com/apt/pool/main/w/wine/libwine_0.9.36~winehq0~ubuntu~7.04-2_all.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/libwine_0.9.36~winehq0~ubuntu~7.04-2_all.deb)

---

### Post by ©TriMoon® on 2007-05-09
This is great, i was already thinking of somehow compiling one for myself (nightmare)
Anyway ill be DLing this and gonna give it a try....

---

### Post by RawMustard on 2007-05-09
Wow thanks for the heads up :)

---

### Post by Kilz on 2007-05-09
Its great that there is a 64bit deb file for Feisty. But I have read a few posts of people uninstalling the 32bit wine package to install the 64bit package. But be aware that they are both 32bit applications. This is because wine is a 32bit application layer, because common windows applications are 32bit. 64bit wine would let you run 64bit windows applications which are few in number. All the 64bit deb file dose is makes it easier to install. If you already have wine installed you will gain nothing by reinstalling it.

---

### Post by Tanker Bob on 2007-05-09
hexion - thank you for letting us know.  I uninstalled the previous manually-installed 64-bit wine and installed these from the repository.

Kilz - What you gain is automatic updating.  Rather than having to keep track here on the forums, I can now rely on the built-in notifier to keep me up to date.  It may not be a technical advantage, but it is a very practical one.  "A stitched in wine saves time."  :)

---

### Post by Laryllan on 2007-05-09
Yeah, nothing is gained by installing the 64bit version.
Thought it would run a little bit faster at least, maybe due to the wrapper being faster...

---

### Post by Kilz on 2007-05-09
> **Laryllan said:**
> Yeah, nothing is gained by installing the 64bit version.
Thought it would run a little bit faster at least, maybe due to the wrapper being faster...

The reason its not, is because wine has to be 32bit to run the 32bit windows applications. Even the packages made to install on adm64 Ubuntu are 32bit. So its either a 32bit application in a 32bit package, or a 32bit application in a 64bit package. Either way its a 32bit application, based on the exact same code.

---

### Post by RAOF on 2007-05-10
Apparently, upstream are working on proper WoW64 support.  That is, you'll actually build a 64bit wine, and be able to run both 32- and 64-bit windows apps in there.  Yay!

---

### Post by rai4shu2 on 2007-05-10
I assume 64-bit Wine will be called wine64 rather than changing wine to wine32? This seems a little counterintuitive on a 64-bit system.

---

### Post by hexion on 2007-05-10
I don't understand such confussion here...

These packages give a 32 bit windows system, but working on a 64 bit Linux system. Let's call it wine32 for ubuntu64.

As someone said before, it's the same thing you were doing manually but now in a repository. It's just easier. No howtos... :D

Building a wine64 system isn't (IMHO) a priority right now. What's the sense in "emulating" (yeah, I know what WINE means) a system that nobody uses. With serious lacks in drivers and software...

---

### Post by Kilz on 2007-05-10
> **rai4shu2 said:**
> I assume 64-bit Wine will be called wine64 rather than changing wine to wine32? This seems a little counterintuitive on a 64-bit system.

The reason it isnt counterproductive to not have a 64bit windows application layer is because the number of 64bit windows programs can be counted on your fingers.
Almost all windows applications are 32bit. So why make an application layer for a very few programs? Most if not all windows 64bit applications have 32bit versions. Also it is infinitly better to find native Linux applications that can replace those running under wine. The Linux applications will be of better quality, and offer better performance. The only area you cant really do that now is in games.

---

### Post by YokoZar on 2007-05-10
> **rai4shu2 said:**
> I assume 64-bit Wine will be called wine64 rather than changing wine to wine32? This seems a little counterintuitive on a 64-bit system.No, the plan is to include both 64 and 32 bit support into the same "Wine" package.  It'll be some time before Wine properly supports running 64 bit Windows applications, as well as some time before those applications actually exist, though.

---

