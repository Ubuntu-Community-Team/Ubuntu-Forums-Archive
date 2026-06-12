---
title: "wine itself won't run"
date: 2008-03-21
forum: Wine
---

### Post by blakecraw on 2008-03-21
So, a little while ago I was impatient for version 0.9.56 of wine, so I downloaded the source and installed it with checkinstall, and saved the .deb that was created. Now, whenever I try to install a different wine version (including 0.9.56 via apt and 0.9.57 via apt or from source), I get this nice error:

```

vaio:1> winecfg
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  22
  Current serial number in output stream:  26
vaio:2> 

```

none of the wine commands work, winecfg, regedit, wine a.exe, etc.

I can then reinstall the 0.9.56.deb I have left over from the checkinstall, and it works, but that's not very useful...

I've tried uninstalling numerous times, checkinstalling new versions, make-installing new versions, but nothing has worked. Any ideas?

blake

---

### Post by cysco24 on 2008-03-21
I had a similar problem when i updated through synaptic 0.9.57 and nothing worked.  Someone then told me to delete the .wine folder in your home directory and then try to install it.  Worked after that.

---

### Post by blakecraw on 2008-03-23
Well, deleting all my games isn't at the top of the list of things I'd like to do, so does anybody have a different solution?

---

### Post by donnyblaze1 on 2008-03-23
try a sudo apt-get purge wine, then reinstall maybe?

---

### Post by happyhamster on 2008-03-23
- Do you get the same results when starting winecfg from a fresh wine "bottle"? To create the bottle:

wineprefixcreate --prefix .winetest

- Then run winecfg like this:

env WINEPREFIX="$HOME/.winetest" winecfg

---

### Post by blakecraw on 2008-03-23
thanks happyhamster, that worked. I guess I'll just move my game folders over from .wineold and hopefully leave whatever problem there was behind.

---

