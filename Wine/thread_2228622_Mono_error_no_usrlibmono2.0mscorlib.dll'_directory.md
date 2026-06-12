---
title: "Mono error no /usr/lib/mono/2.0/mscorlib.dll' directory."
date: 2014-06-08
forum: Wine
---

### Post by cigtoxdoc on 2014-06-08
Using Wine 1.6.1 under Ubunbtu 12.04 64-bit.  Programs are looking for /usr/lib/mono/2.0/mscorlib.dll' directory.  Full error message is "The assembly mscorlib.dll was not found or could not be loaded.  It should have been installed in the `/usr/lib/mono/2.0/mscorlib.dll' directory."  I have a /usr/lib/mono/4.0/mscorlib.dll.

How does one install mono to get the /usr/lib/mono/2.0/mscorlib.dll' directory?

Thank you,

John

---

### Post by fr-andres on 2014-06-08
Hi, I'm not familiar with "mono", but it seems that you have the 4.0 version and the failing programs are looking for the 2.0 version.
It may be solved by different ways:
-you can install the 2.0 and ensure that goes to /usr/lib/mono/2.0
-you can get programs that look for the latest version
-If none of them possible, you may do the tweak: either copying the contents of 4.0 to a folder called 2.0, or changing the adress which your programs look for, from 2.0 to 4.0.
This is the dirty way, I would do it with caution since the incompatibilities between libraries may trigger various issues, from little bugs to fatal errors crashes etc... nasty stuff.
I hope that it helps!
cheers
Andres

---

