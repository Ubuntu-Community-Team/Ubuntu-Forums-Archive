---
title: "New Version of WINE - not on the site"
date: 2008-01-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by thuleni on 2008-01-12
I find this a bit frustrating.  Ubuntu reports that a new version of software is ready for download (version 0.9.53 for AMD 64) and when you select it for update, you get a 404 - not found.  Checked the site (@ [http://wine.budgetdedicated.com/apt/pool/main/w/wine/](http://wine.budgetdedicated.com/apt/pool/main/w/wine/)) and sure enough the package does not exist there.

Is there a mirror site that does have this software ready for download?

---

### Post by FunkyJack on 2008-01-12
Which distro you have?
Here is for Gutsy:
[http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.53~winehq0~ubuntu~7.10-1_amd64.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.53~winehq0~ubuntu~7.10-1_amd64.deb)

---

### Post by thuleni on 2008-01-12
Yeah Gutsy, but the link is still broken...

Not Found

The requested URL /apt/pool/main/w/wine/wine_0.9.53~winehq0~ubuntu~7.10-1_amd64.deb was not found on this server.

---

### Post by FunkyJack on 2008-01-12
It works now:
[http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.53~winehq0~ubuntu~7.10-1_amd64.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.53~winehq0~ubuntu~7.10-1_amd64.deb)
Probably problems with server...

---

### Post by Kilz on 2008-01-12
It looks like the packages dont exist on the site. (0.9.53) that isnt surprising as the 9.53 source was only released yesterday Jan 11. It sometimes takes a day or so for packages to be made.
[From the Wine site:]("http://winehq.org/")
```
Binary packages are in the process of being built and it may take a few days for them 
to appear, but the source is available now
```
Whats odd is that the op says ubuntu said there was an update. perhaps there was a problem with the packages and they were pulled. It should all work out in a few days.

---

### Post by thuleni on 2008-01-12
No Problem - I'll wait.

Thanks

---

### Post by FunkyJack on 2008-01-12
Hmm
I did apt-get update today and instaled version 0.9.53.
Maybe it was wrong build and now they are compiling new ones.

---

### Post by Kilz on 2008-01-12
> **FunkyJack said:**
> Hmm
I did apt-get update today and instaled version 0.9.53.
Maybe it was wrong build and now they are compiling new ones.

It looks like its available now, it wasnt a hour ago.

---

### Post by soxs on 2008-01-12
And even if it wasn't, there are detailed instructions on howto compile 64bit packages for ubuntu. So it shouldn't really be a problem.
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

---

