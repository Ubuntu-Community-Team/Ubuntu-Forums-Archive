---
title: "Okbridge - DLL problem [SOLVED]"
date: 2007-12-24
forum: Wine
---

### Post by Jimmey on 2007-12-24
My mother needs to use Okbridge but the Linux client is only text based (my mum can't use that!).

appdb.winehq.org says that Okbridge works if you edit the .ini file, which I have done.

But the program says > error loading bitmap from CARDS.DLL"

I have tried various methods or running the program (for example, cd .wine/drive_c/etcetcetc && wine programName.exe, or wine .wine/drive_c/etcetcetc). But it's not loading the images of the cards, making the game unplayable.

I thought it might be something to do with case sensitivity, but I tried re-naming the DLL without luck.

Does anyone know how I can get round this?

EDIT: Solution was to make a DLL override for "cards" using winecfg.

winecfg from a terminal, then "Libraries" tab.

Thanks

---

