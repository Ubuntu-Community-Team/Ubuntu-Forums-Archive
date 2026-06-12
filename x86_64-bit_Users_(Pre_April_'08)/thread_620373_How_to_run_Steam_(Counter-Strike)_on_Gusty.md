---
title: "How to run Steam (Counter-Strike) on Gusty?"
date: 2007-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by leandrorepolho on 2007-11-22
Hello everybody, is there any HOWTO that shows how can i configure the Windows program STEAM with Counter-Strike on Ubuntu Gusty x64 Bits.
My configuration is ACER 5100-5196; turion x2 1.6 x64; 1gb ram; 120gb; ati xpress 1100 128mb

Thanks,
Leandro

---

### Post by Kilz on 2007-11-22
> **leandrorepolho said:**
> Hello everybody, is there any HOWTO that shows how can i configure the Windows program STEAM with Counter-Strike on Ubuntu Gusty x64 Bits.
My configuration is ACER 5100-5196; turion x2 1.6 x64; 1gb ram; 120gb; ati xpress 1100 128mb

Thanks,
Leandro

Open a terminal and type in this. 

```
sudo apt-get install wine
```

[Then go here]("http://appdb.winehq.org/appview.php?iVersionId=1554") and follow the instructions. Make sure to bookmark the wine application databse in case you have other windows applications you want to install.

---

### Post by badrunner on 2007-11-22
With the most recent wine there isn't really anything to do, just install steam. The only thing that occasionally happens is not having the tahoma font, but i think wine now includes a replacement anyway. Just make sure you never, ever install directx if requested to by a game installer.

The appdb on the winehq site is always very up to date though.

---

