---
title: "Winetricks cannot install devnum"
date: 2016-02-05
forum: Wine
---

### Post by dragonator2 on 2016-02-05
Hello,

I tried to install devnum with winetricks but got this message instead:

```
$ winetricks devnum
Unknown arg devnum
Usage: /usr/bin/winetricks [options] [command|verb|path-to-verb] ...
Executes given verbs.  Each verb installs an application or changes a setting.

Options:
    --force           Don't check whether packages were already installed
    --gui             Show gui diagnostics even when driven by commandline
-k, --keep_isos       Cache isos (allows later installation without disc)
    --no-clean        Don't delete temp directories (useful during debugging)
    --no-isolate      Don't install each app or game in its own bottle
-q, --unattended      Don't ask any questions, just install automatically
-r, --ddrescue        Retry hard when caching scratched discs
    --showbroken      Even show verbs that are currently broken in wine
    --verify          Run (automated) GUI tests for verbs, if available
-v, --verbose         Echo all commands as they are executed
-h, --help            Display this message and exit
-V, --version         Display version and exit

Commands:
list                  list categories
list-all              list all categories and their verbs
apps list             list verbs in category 'applications'
benchmarks list       list verbs in category 'benchmarks'
dlls list             list verbs in category 'dlls'
games list            list verbs in category 'games'
settings list         list verbs in category 'settings'
list-cached           list cached-and-ready-to-install verbs
list-download         list verbs which download automatically
list-manual-download  list verbs which download with some help from the user
list-installed        list already-installed verbs
prefix=foobar         select WINEPREFIX=/home/dragonator/.local/share/wineprefixes/foobar


```

is devnum not available anymore?


EDIT: Ignore my stupidity: it was just a typo

---

