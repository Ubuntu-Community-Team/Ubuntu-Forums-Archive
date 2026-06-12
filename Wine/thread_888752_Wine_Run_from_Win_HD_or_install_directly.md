---
title: "Wine: Run from Win HD or install directly?"
date: 2008-08-13
forum: Wine
---

### Post by Luf on 2008-08-13
Hey all,

I'm looking to setup a system with a HD for Vista Ultimate x64 and an HD for Ubuntu. I would like to know if one of these methods is better than the other, in terms of performance...

**Installing apps via Wine.**

or 
[B]
Pointing wine to the programs already installed on the Windows drive.[/B]

---

### Post by aoanla on 2008-08-13
Well, it's worth noting that certain games (anything under Steam, for example) will have issues running from an NTFS partition under wine - the ntfs-3g filesystem module doesn't let Wine set certain properties that it needs to be able to, so it can't properly let Steam run.
I assume your Vista HD will be using NTFS,so...

---

### Post by Luf on 2008-08-13
Hmm....ok.

I currently have a 3rd HD for all of my apps.

WoW / Age of Conan / Steam / Office 2007 are all on this 3rd HD.

If that HD were FAT32, would my Ubuntu+Wine be able to run them ok?

thanks!

---

### Post by ooobuntooo on 2008-08-13
> **Luf said:**
> Hmm....ok.

I currently have a 3rd HD for all of my apps.

WoW / Age of Conan / Steam / Office 2007 are all on this 3rd HD.

If that HD were FAT32, would my Ubuntu+Wine be able to run them ok?

thanks!

Office 2007 will only run if it is installed directly (due to windows registry files). It also doesn't work under wine, only Crossover Linux 7. The other applications should be ok!

---

