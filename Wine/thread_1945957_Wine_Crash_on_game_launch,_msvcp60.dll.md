---
title: "Wine Crash on game launch, msvcp60.dll"
date: 2012-03-23
forum: Wine
---

### Post by OakRaider4Life on 2012-03-23
Help!

I've successfully installed Europa Universalis III into a winebottle managed by PlayOnLinux, but anytime I attempt to launch, it crashes with the return error

```
Unhandled exception: unimplemented function msvcp60.dll
```

Can anyone help me decipher how to fix this error?

I'm actually running Arch Linux... but I'm posting here because posting in the Wine forums and posting in the PoL forums almost never garners any helpful replies... but I do also have an install of Ubuntu 11.10 which returns the exact same problem when I try to launch the game.

I'm pretty comfortable working in a Linux environment, but working with Wine is something I'm relatively unfamiliar with, and I'm not well versed in proper configuration.

Any help is greatly appreciated in advance!

---

### Post by dino99 on 2012-03-24
i suppose you are using an old wine installation; you should not get this error with wine1.4 or 1.5 (it has been fixed for sure with 1.5; check winehq url for details)

so upgrade wine or use winetricks to install the missing dll

---

### Post by OakRaider4Life on 2012-03-24
I am definitely running Wine 1.5, but sure enough, you were right about needing to install the .dll. My missing .dll was in the vcrun6 package, which I needed to install into my wine bottle using the POL configuration tools. Thanks for the help!

---

