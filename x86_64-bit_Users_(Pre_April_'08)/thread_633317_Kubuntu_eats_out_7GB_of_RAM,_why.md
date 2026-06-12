---
title: "Kubuntu eats out 7GB of RAM, why?"
date: 2007-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by kub-fu on 2007-12-06
Hi,

I find it very disturbing that after upgrading my PC to 7 GB of RAM, those extra GB are eaten right away by just a few processes. That didn't happen when I had just 2 GB of RAM.

Can anybody help me sort this out?

Here's the output of free -m:

```

             total       used       free     shared    buffers     cached
Mem:          6984       6939         44          0         57       6057
-/+ buffers/cache:        824       6159
Swap:         3153         13       3140

```

Here's a sample from top (sans pids and usernames):

```

PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
15   0  211m  29m  20m S    0  0.4   0:00.76 konqueror
20   0 21568  364  148 S    0  0.0   0:00.00 dbus-launch
20   0 23444  896  688 S    0  0.0   0:00.00 dbus-daemon
18   0  151m  12m 5332 S    0  0.2   0:00.12 python
17   0  3904  532  448 S    0  0.0   0:00.00 sh
15   0  156m  15m  11m S    0  0.2   0:00.16 kio_uiserver
15   0  190m  24m  17m S    0  0.3   0:00.26 konqueror
18   0  3904  564  464 S    0  0.0   0:00.00 soffice
15   0  730m 112m  74m S    0  1.6   0:06.04 soffice.bin
17   0  3904  544  456 S    0  0.0   0:00.00 swiftweasel
19   0  3904  572  468 S    0  0.0   0:00.00 swiftweasel
24   0  3904  584  464 S    0  0.0   0:00.00 run-mozilla.sh
15   0  506m 146m  27m S    0  2.1   0:40.14 swiftweasel-bin
15   0  298m  46m  25m S    0  0.7   0:09.98 amule
17   0 3731m 2376 1824 S    0  0.0   0:00.07 winewrapper.exe
15   0 10356 7940  612 S    0  0.1   0:06.84 wineserver
18   0 3778m  40m  11m S    0  0.6   1:26.54 utorrent.exe
15   0 99.4m  11m  10m S    0  0.2   0:00.17 kdocker
15   0  172m  54m  21m S    0  0.8   0:12.26 prism
15   0 48972  14m 8340 S    0  0.2   0:00.56 npviewer.bin
15   0     0    0    0 Z    0  0.0   0:00.05 prism <defunct>
17   0 3763m  18m 7968 S    0  0.3   0:00.21 explorer.exe
17   0  3904  540  456 S    0  0.0   0:00.00 keepass.sh
15   0 19504  12m 7596 S    0  0.2   0:00.73 keepass
15   0 21272 4112 1556 S    0  0.1   0:00.11 bash
15   0 19080 1264  876 R    0  0.0   0:00.00 top

```

How does wine use 3GB+ of memory? That's ridiculous. 500mb for firefox? 700mb for openoffice? come on, not even MS office used that much back when I used WinXP.

44MB of free RAM out of 7GB... Is there something I'm not getting? I was thinking of getting 4GB more, but I'm afraid they will be eaten too...

By the way, this is Gutsy Gibbon.

---

### Post by rsambuca on 2007-12-06
You have 6159MB of free RAM.  6057 is cached so that your machine runs quickly.  If you open another application that requires RAM, then some cached items are cleared.  This ensures the most efficient and fastest possible setup.

---

### Post by kub-fu on 2007-12-06
Oh, that makes sense.

It's annoying do, how sluggish the system becomes while it's freeing some RAM when I open new programs.

Thanks!

---

