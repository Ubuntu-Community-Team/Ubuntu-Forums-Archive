---
title: "GW2 can't connect to login server"
date: 2015-11-09
forum: Wine
---

### Post by john267 on 2015-11-09
I've tried running GW2 by configuring WINE myself, via crossover/playonlinux, and all gives me same result.

I can open launcher, and it starts downloading the game, but when I try to login, i get an error saying client can not connect to login server. 

Can ANYONE please help me fix this?


tried on WINE without PlayonLinux, and with it.
This is what PoL debug gives me:
err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead.
fixme:module:load_dll Loader redirect from L"uxtheme.dll" to L"uxtheme-gtk.dll"
fixme:uxthemegtk:load_gtk3_libs Wine cannot find the libgtk-3.so.0 library.
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.


as far as the nvidia bit, I've tried switching to the Nouveau driver, but that wouldn't affect logging in would it? not sure what the last line is.. googled and didn't find much info about fixing it




After messing with settings for ages, including opening ports that GW2 uses, I finally decided to just try and turn off my router firewall, and boom, it worked.. If anyone knows of a better fix for this, please inform me. I turn it back on when I'm done on gw2, but don't like it being off.

---

### Post by john267 on 2015-11-11
plz? anyone? added info from playonlinux debug.. new to linux overall so doesn't mean too much to me

---

### Post by john267 on 2015-11-14
still not working.. can't find anything about it anywhere. I've opened all ports that GW2 needs; removed/purged/reinstalled gw2, wine, PoL. etc etc, tried turning off UFW

---

