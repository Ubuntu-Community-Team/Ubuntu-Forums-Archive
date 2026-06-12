---
title: "Flash on firefox 3 beta 5 for 64 bit"
date: 2008-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by survient on 2008-04-08
Oh what I would give for adobe just to make a 64 bit version of their flash plugin -_-. Anyway, I recently built a version of firefox 3 beta 5 from source, as I can't stand 32 bit firefox and I didn't want to go with beta 3 in the repository. My only issue right now is I haven't been able to get this new version to recognize my old ndiswrapper plugin for firefox 2 64 bit, despite what I'm seeing in these forums. My install is actually located in:
```

~/mozilla/obj-x86_64-unknown-linux-gnu/dist/bin

```
and I made a link in my binaries folder(/usr/bin) to it called firefox-3.0b5. I shoved the ndiswrapper.libflashplayer.so in the same folder as the executable, in the plugins folder of that directory, in my ~/.mozilla folder, and a ~/.mozilla/firefox-3.0b5, ~/.mozilla/firefox, ~/.mozilla/firefox-3.0 folders, with no luck. Nothing seems to get this version to pick up on the flash plugin. When I run firefox in terminal, just firefox I get:
```

Cannot find mozilla runtime directory. Exiting.

```
which I can only assume is caused by my new install of this firefox-3.0b5. ANy help on this would be appreciated.

---

### Post by grantek on 2008-04-09
Try linking the whole plugins directory. I have the normal 64-bit firefox2 ubuntu package installed, but for ff3 I just downloaded the 32-bit binaries from mozilla.org. I linked the whole directory ( " mv plugins plugins.orig && ln -s /usr/lib/mozilla/plugins ./ " ), and flash works fine.

It does barf at the 64-bit ndiswrapper, but it seems to pick up the 32-bit original plugin and use that (I don't know if having the original 32-bit plugin present is necessary for ndiswrapper, but the fact that mine's there and yours doesn't work suggests it may be) - java doesn't work at all because it's natively 64-bit, but in your case it should work fine if you've got it.

---

### Post by survient on 2008-04-19
so you're saying there's nothing doing for firefox 3 beta 5 for 64 bit native? any workarounds discovered for the ndiswrapper?

---

### Post by FredB on 2008-04-21
You can use swfdec plugin (it is great for youtube and this kind of site).

Or, nspluginwrapper, ndiswrapper is for wifi hardware ;)

---

### Post by ©TriMoon® on 2008-04-21
> **survient said:**
> Oh what I would give for adobe just to make a 64 bit version of their flash plugin -_-. Anyway, I recently built a version of firefox 3 beta 5 from source, as I can't stand 32 bit firefox and I didn't want to go with beta 3 in the repository. My only issue right now is I haven't been able to get this new version to recognize my old ndiswrapper plugin for firefox 2 64 bit, despite what I'm seeing in these forums. My install is actually located in:
```

~/mozilla/obj-x86_64-unknown-linux-gnu/dist/bin

```
and I made a link in my binaries folder(/usr/bin) to it called firefox-3.0b5. I shoved the ndiswrapper.libflashplayer.so in the same folder as the executable, in the plugins folder of that directory, in my ~/.mozilla folder, and a ~/.mozilla/firefox-3.0b5, ~/.mozilla/firefox, ~/.mozilla/firefox-3.0 folders, with no luck. Nothing seems to get this version to pick up on the flash plugin. When I run firefox in terminal, just firefox I get:
```

Cannot find mozilla runtime directory. Exiting.

```
which I can only assume is caused by my new install of this firefox-3.0b5. ANy help on this would be appreciated.
If you check the firefox script you should have no problem putting things in correct place.
The firefox script is a shell-script that calls another script 'run-mozilla.sh' :)
There is a default setting in the top of the firefox script that sets ```
moz_libdir=/usr/local/lib/firefox-3.0b5
```
You could either move your install there or change the setting in the script :)

(I wish i could manually compile a 64 version also of FF3b5)
Im writing this to you using: **Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9b5) Gecko/2008032619 Firefox/3.0b5**
Thats the precompiled 32bit version from mozilla self.
Im now struggling with java, i cant find the plugins directory inside the java install...any ideas?

---

