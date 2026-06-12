---
title: "Cairo Dock install using the getlibs"
date: 2008-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Koolgecko91 on 2008-03-18
Ok...so im using the 64bit installation process found [Here]("https://help.ubuntu.com/community/CairoDock"). And when I get to the 1st terminal command it wont go and it says "Options marked [*] produce alot of output - pipe through more or less". I really want Cairo dock and they said this is the easiest way to do it on 64bit. So could someone help me please get the terminal commands to work.

---

### Post by IanW on 2008-03-18
Do them one at a time like this:-

```

sudo dpkg &#8211;force-all -i cairo-dock*.deb
sudo getlibs /usr/bin/cairo-dock
sudo apt-get -f install
```

PS. It seems that the newly released version 1.5.3.2 is corrupt - at least I can't open it.

---

### Post by Koolgecko91 on 2008-03-18
i did the first one and it gave me that error in the OP. Downloaded the version before the newest and it gave me the error again.

---

### Post by Koolgecko91 on 2008-03-18
Ok i fixed it. In the code it should be ```
sudo dpkg --force-all -i cairo-dock*.deb
```
not ```
sudo dpkg **_–_**force-all -i cairo-dock*.deb
```

---

