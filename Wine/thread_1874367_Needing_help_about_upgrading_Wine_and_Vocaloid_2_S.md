---
title: "Needing help about upgrading Wine and Vocaloid 2 :S"
date: 2011-11-02
forum: Wine
---

### Post by luks255 on 2011-11-02
Ok, so, I have this strange problem...
When I do wine --version in console it says "wine 1.1.24".
Fine. Uninstalled and purged. "sudo apt-get --purge remove wine wine-gecko" NOTHING was left.
Again, "wine --version" and it still throws "wine 1.1.24".
...The heck?

I decided to ignore it and just install wine1.3.
"sudo add-apt-repository ppa:ubuntu-wine/ppa", "sudo apt-get update" and "sudo apt-get install wine1.3"
Again, wine --version "wine 1.1.24".

I'm trying to upgrade Wine because 1.1.24 is pretty much obsolete and won't let me run Vocaloid 2.

I'm using Ubuntu 9.10 32 bits, BTW.

Any help, please? =S

---

### Post by ergo-proxy on 2011-11-03
It seems binaries are left, remove wine again and check  /usr/bin/, /usr/local/bin/ for wine*, regedit* and delete.

---

### Post by luks255 on 2011-11-03
OH. MY. GOD.

THANK YOU SO MUCH!

It worked like a charm! =D
Now I can run Vocaloid 2 =D
THANK YOU!

-luks255

---

### Post by gmorris448 on 2011-11-03
My vocaloid 2 is still useless..not working at all. :-|

[Westminster  In-Home]("http://www.phcsicare.com")

---

### Post by luks255 on 2011-11-03
Well, turns out that Vocaloid doesn't work in Wine 1.3.15. Nonetheless, it works flawlessly under Wine 1.3.26.

EDIT: That's what it says at WineHQ, but it still doesn't work for me here...

Try upgrading to LATEST version.

-luks255

EDIT: Seems like downgrading to 1.2.2 solved the problem. To run:

```
env LC_ALL=ja_JP wine VOCALOID2.exe

```

---

