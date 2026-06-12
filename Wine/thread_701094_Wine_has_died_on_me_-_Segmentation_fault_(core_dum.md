---
title: "Wine has died on me - Segmentation fault (core dumped)"
date: 2008-02-19
forum: Wine
---

### Post by David Tomic on 2008-02-19
Hi folks,

At the moment I'm using Wine 0.9.55 with the Hardy 8.04 alpha [64 bit].

I've been using both programs [through their various stages of development] for many months now, and never had any real problems with either of them.

Since an update a little while ago though, Wine has just completely died on me.

Anything I try and do through the terminal simply returns the error message
"Segmentation fault (core dumped)"

Any help/advice/suggestions on getting this fixed up will be greatly appreciated! 

I'm happy to try and provide any more information etc that you might need, but I'm really not sure where to begin?  Just let me know what you need, and I'll try and do my best to oblige ...

---

### Post by Gen2ly on 2008-02-19
ok, the I at times had trouble with the ~./wine settings.  I renamed the folder and ran wine-cfg again.

---

### Post by eris23 on 2008-02-19
Same trouble here.  I tried renaming .wine, didn't work.  I tried both winecfg and wineconfig.

Errors:

Segmentation fault (core dumped)
Segmentation fault (core dumped)
Segmentation fault (core dumped)
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3551, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 118, in __init__
    self.CreateWindowsInstall()
  File "/usr/bin/wineconfig", line 321, in CreateWindowsInstall
    winewrite.SetDriveMappings(drives)
  File "/var/lib/python-support/python2.5/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/var/lib/python-support/python2.5/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/eris23/.wine/dosdevices/c:/windows/profiles/eris23'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3551, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 118, in __init__
    self.CreateWindowsInstall()
  File "/usr/bin/wineconfig", line 321, in CreateWindowsInstall
    winewrite.SetDriveMappings(drives)
  File "/var/lib/python-support/python2.5/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/var/lib/python-support/python2.5/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/eris23/.wine/dosdevices/c:/windows/profiles/eris23'

---

### Post by FrozenFox on 2008-02-19
The new version of wine (0.9.55) in the hardy branch is broken. I posted a couple pages back in response to a post asking why 0.9.55 isn't out yet giving a link to an unofficial version at the mepis forums that works fine (although it doesn't include the start menu stuff). So if you want the new version, look for that (perhaps my post history?), or revert to an older version and wait for the devs to fix it.

---

### Post by David Tomic on 2008-02-19
> **FrozenFox said:**
> The new version of wine (0.9.55) in the hardy branch is broken.

Thanks FrozenFox.

I've just downgraded it to 0.9.54 and everything is good again! :)

---

