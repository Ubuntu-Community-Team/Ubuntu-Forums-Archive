---
title: "[SOLVED] Upgrade from 8.04 to 8.10 and firefox"
date: 2008-11-04
forum: x86 64-bit Users
---

### Post by TryHarder on 2008-11-04
Hello,
I have upgraded my ubuntu from 8.04 version to 8.10. Now when I try to run firefox it stucks on some sites. So I run it from terminal and this what I got:
```
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

```

I reinstalled nspluginwrapper and flash-nonfree but still i get this. Can someone help me pleace?

---

### Post by sisco311 on 2008-11-04
try to remove any flash plugin manualy:
```
sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
```

```
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```

be careful with the *rm* commands.
copy/past them line by line in a terminal.

empty the cach:
```
sudo aptitude clean
```

and reinstall flash:
```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

---

### Post by TryHarder on 2008-11-04
Thank you very much it's solved my problem. I guess that previously I have not completely removed them.

---

### Post by sisco311 on 2008-11-04
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

