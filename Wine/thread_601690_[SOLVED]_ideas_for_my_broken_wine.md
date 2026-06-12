---
title: "[SOLVED] ideas for my broken wine"
date: 2007-11-03
forum: Wine
---

### Post by Psy-Krow on 2007-11-03
so,  I'm loving my complete switch to linux...  2 months in now =)
i'm obviously still pretty new, but i catch on quick.

Wine has been exceeding my expectations in the gaming department.  I had CounterStrike and EvE running fine, and was afraid to install WoW only out of fear of becoming addicted again.

yesterday i added wine's repositories so i could get the latest version...   long story short,  i uninstalled, wiped my ~/.wine and installed the latest version.

re-installing EvE i get this notice
```
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:wgl:X11DRV_ChoosePixelFormat No OpenGL support compiled in.
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl

```

and something similar when i attempt to download CSS (steam installed, but it errors and exits when i attempt to download)

i've searched all the FAQ's and HowTo's i can find and havn't found anything about compiling in opengl.

i assume it was something that was suppose to happen during the installation and for some reason hasnt.

wiping ~/.wine  and reinstalling 0.9.48 hasn't helped

stuck...

---

### Post by mrvertigo on 2007-11-03
the version of wine that ships with ubuntu is tailored spicifically to ubuntu so your breakage may be due to install errors or missing dependancies my suggestion is as follows, do a google for crossover linux beta testing, and join their beta team, it grants you access to a more compleat implementation of wine, A great UI and they have packages just for ubuntu! plus you get the satisfaction of helping with bug reports!

---

### Post by cogadh on 2007-11-03
The .DEBs that are available through the WineHQ repositoriy are also specifically built with Ubuntu in mind, so they should work just as well as the one from the Ubuntu repository. In fact, I am reasonably certain that the package in the official repo was actually built by the same person who maintains the WineHQ repo.

CrossOver is not a more complete version of Wine, it is based on a much older version of Wine (I think the current version is about 10 minor revs out), though the beta might be using something a little more current. The only real difference between regular Wine and CrossOver is the GUI, which can be quite helpful, but it is really the same thing at its core.

@Psy-Krow
When you uninstalled Wine, did you do a complete purge of it?
```
sudo apt-get remove --purge wine
```
Some times doing that and then re-installing can help.

---

### Post by Psy-Krow on 2007-11-04
@Cogadh

first off god bless your wine howto,  and thankyou for responding.

lesson learned:  source files install to /usr/local/bin,  ubuntu package installs to /usr/bin

so orginally when i "upgraded" to 0.9.48 i had compiled and installed from source (at that time i didn't realize i could do it from the repo's). my noob move was that i hadn't make uninstalled when i attempted to start fixing things.

i found this out when, after trying various uninstalls/reinstalls, i tried to compile from source again.   the ./configure gave me the same "will build without direct3d opengl"  so i installed the nessary lib's and got the ./configure to check without warnings (also noob lesson learned)

when i ran the install tool i noticed that it recognized a previous installation.  at this point i realized my error and stopped the make, did a make uninstall, and then installed from the package manager.   done and done

iwish i'd taken heed of your warning in your howto about installing from source ahead of time.  would've saved a headache.

but, i certainly learned a lot.   and in the end thats what matters isn't it?

=)

ironic, while i certainly needed an operational wine for other things, its humorous that i find out now that a linux native installer for EvE will be released this coming  tuesday.

cheers!

---

