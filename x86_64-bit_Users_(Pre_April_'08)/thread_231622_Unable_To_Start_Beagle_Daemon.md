---
title: "Unable To Start Beagle Daemon"
date: 2006-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mojosdad on 2006-08-07
Has anyone managed to install Beagle on 64bit Kubuntu with Kerry?

I've got Beagle + Kerry from repos, but when I try to start the daemon in Konsole I get error messages:

** (/usr/lib/beagle/BeagleDaemon.exe:7341): WARNING **: The following assembly referenced from /usr/lib/beagle/Util.dll could not be loaded:
     Assembly:   Mono.Data.SqliteClient    (assemblyref_index=4)
     Version:    1.0.5000.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).

_QUOTE_
** (/usr/lib/beagle/BeagleDaemon.exe:7341): WARNING **: Could not load file or assembly 'Mono.Data.SqliteClient, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/beagle/BeagleDaemon.exe:7341): WARNING **: Could not load file or assembly 'Mono.Data.SqliteClient, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
scott@scott-Kubuntu64:~$
** (/usr/lib/beagle/BeagleDaemon.exe:7341): WARNING **: The following assembly referenced from /usr/lib/beagle/Filters/Filters.dll could not be loaded:
     Assembly:   ICSharpCode.SharpZipLib    (assemblyref_index=7)
     Version:    0.6.0.0
     Public Key: 1b03e6acf1164f73
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle/Filters).


** (/usr/lib/beagle/BeagleDaemon.exe:7341): WARNING **: Could not load file or assembly 'ICSharpCode.SharpZipLib, Version=0.6.0.0, Culture=neutral, PublicKeyToken=1b03e6acf1164f73' or one of its dependencies.

** (/usr/lib/beagle/BeagleDaemon.exe:7341): WARNING **: Could not load file or assembly 'ICSharpCode.SharpZipLib, Version=0.6.0.0, Culture=neutral, PublicKeyToken=1b03e6acf1164f73' or one of its dependencies.
_END QUOTE_

Any ideas?

---

### Post by Mojosdad on 2006-08-07
Think I fixed it - manually added all libmono-sharpzip & libmono-sqlite packages and seems to start up now.

---

