---
title: "[SOLVED] Deleted .wine folder, reinstall does not restore subfolders"
date: 2008-02-06
forum: Wine
---

### Post by shaneh on 2008-02-06
I deleted my wine folder and emptied my trash, thinking it would be the easiest way to completely remove a bunch of programs I no longer use but was unable to uninstall from the "Uninstall Wine Programs" program due to general bugginess. The game plan was to just reinstall the programs that I DO use after reinstalling wine.

Unfortunately, wine isn't installing properly from the repositories - it doesn't create a drive_c folder or any of the subfolders, especially the windows subfolder or any of its files. What can I do to restore the stuff so that wine works again?

For example, when I try to run winecfg from terminal I get

```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/shane', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
err:wineboot:main Cannot set the dir to L"c:\\windows" (2)
```

My other programs that use its own wine code like Picasa and ies4linux still work fine.

---

### Post by ajgreeny on 2008-02-06
1   Use synaptic to **completely remove** wine from your system.
2   Check that the ~/.wine folder has gone and if not delete it.
3   Reinstall wine andf then run ```
winecfg
``` again.  That should remake the .wine folder.
4   Reinstall the programs you want to run with ```
wine path/to/program/setup.exe
```

If that will not work then I am completely baffled.

---

### Post by asnd16 on 2008-02-06
should we restart after?

---

### Post by shaneh on 2008-02-06
Thanks a lot. I tried this before, but I guess it just needed a restart between removal and reinstallation.

---

