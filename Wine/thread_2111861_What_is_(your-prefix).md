---
title: "What is (your-prefix)"
date: 2013-02-03
forum: Wine
---

### Post by stevemav on 2013-02-03
Hey, very basic question that is hindering me at the moment, when someone advises the following 

env WINEDEBUG="fixme-all" WINEPREFIX="(your-prefix)" wine msiexec /i SteamInstall.msi

I'm lost as to what (your-prefix) is reffering too. I've been searching here and in the winehq, as well as google so far and no luck.

Thanks for the help!

---

### Post by howefield on 2013-02-03
Thread moved to the "*Wine*" forum.

---

### Post by TheFu on 2013-02-03
You can have multiple WINE installs under your user account.  Usually ~/.wine is the prefex, but often getting different programs to work requires very different and incompatible settings, so people will setup multiple WINE installations using different directories.
~/.wine/
~/.wine.quicken/
~/.wine.mso11/

You get the idea. If you are using defaults, use** ~/.wine/**
The ~/.wine may need to be converted to $HOME/.wine or /home/{userid}/.wine, actually, that is how I specify it in my launch scripts - with a full and complete path.

---

