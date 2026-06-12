---
title: "Kiba-Dock and Gutsy x64"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by amadeus266 on 2008-01-06
With the last 2 versions of kiba-dock I get the following error trying to compile the plugins...
[HTML]/usr/bin/ld: ./.libs/liblauncher-type.a(launcher.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
./.libs/liblauncher-type.a(launcher.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [liblauncher.la] Error 1
make[2]: Leaving directory `/home/adam/kiba/kiba-plugins/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/adam/kiba/kiba-plugins/src'
make: *** [install-recursive] Error 1
[/HTML]

Anyone have a workaround?

---

### Post by Kilz on 2008-01-06
> **amadeus266 said:**
> With the last 2 versions of kiba-dock I get the following error trying to compile the plugins...
[HTML]/usr/bin/ld: ./.libs/liblauncher-type.a(launcher.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
./.libs/liblauncher-type.a(launcher.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [liblauncher.la] Error 1
make[2]: Leaving directory `/home/adam/kiba/kiba-plugins/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/adam/kiba/kiba-plugins/src'
make: *** [install-recursive] Error 1
[/HTML]

Anyone have a workaround?

Its amazing how the search function can help. Its that little box in the upper right with GO besides it. [This post was found with it]("http://ubuntuforums.org/showthread.php?t=530414&highlight=kiba-dock"), perhaps it can help.

---

### Post by macaholic on 2008-01-06
I've had this problem for quite some time, and it has driven me to stop using kiba, and it still happens with that guide btw. You could try the kiba forums, but I posted this a while ago and no one has gotten back to me on it. 
EDIT: Just found a guy today same problem [here]("http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=609.0"), on the kiba forums, see if he gets a response.
EDIT2: Filed a bug report [here]("http://sourceforge.net/tracker/index.php?func=detail&aid=1865252&group_id=201401&atid=977415").

---

### Post by amadeus266 on 2008-01-06
> **Kilz said:**
> Its amazing how the search function can help. Its that little box in the upper right with GO besides it. [This post was found with it]("http://ubuntuforums.org/showthread.php?t=530414&highlight=kiba-dock"), perhaps it can help.

If I hadn't tried that and following the other posts and how-tos I wouldn't have posted this question to begin with. But thanks for the smart-alec answer anyway.

---

