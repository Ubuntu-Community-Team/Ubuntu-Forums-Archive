---
title: "HOWTO: StarCraft 2 + Bumblebee + Wine 1.5"
date: 2013-03-02
forum: Wine
---

### Post by Rob_H on 2013-03-02
Here's how I got StarCraft II running under Kubuntu 12.04 with Wine 1.5 and Bumblebee (for NVIDIA Optimus laptops). Hopefully, someone else will find it useful. I will assume you've already installed [Wine 1.5]("http://www.winehq.org/download/ubuntu") and [Bumblebee]("http://bumblebee-project.org/install.html"). Make sure Bumblebee is working correctly for Linux apps before tackling Wine with it.

[LIST=1]
[*]First, install Visual C++ runtimes:
```
winetricks vcrun2005 vcrun2008
```
[*]Run **winecfg**. Go to the **Libraries** tab and add a new override for "msvcp90" (without the quotes). Then edit the override and select **Native (Windows)**. The dialog should now resemble the screenshot below. Click **OK** to save and exit.
[ATTACH=CONFIG]239666[/ATTACH]
[*]Open a terminal and spawn a **bash** process under **optirun**. Then start the StarCraft II [downloadable installer]("https://us.battle.net/account/download") under Wine. The executable name might vary.
```
optirun bash
wine <path_to_installer>/StarCraft-II-Setup-enUS.exe
```
[/LIST]
At this point, the game should install and run correctly. Note that you cannot specify the **wine** command as an argument to **optirun** because StarCraft II spawns child processes and terminates the parent process. However, it's a pain to spawn a bash process every time we want to run StarCraft, so we'll solve that problem next.

*_Launching StarCraft II after installation:_* You can't use the shortcut that the installer creates to launch StarCraft II because it won't run under Bumblebee that way. Starting it directly under **optirun** doesn't work either because StarCraft II's launcher spawns several child processes and terminates the launcher process, which terminates **optirun**, too. Instead, you need to make sure **optirun** is started and stays running until all the child processes have exited. I've written a little Python script that handles this.

```
#!/usr/bin/env python

# Run StarCraft II via Optirun. Requires jumping through hoops because
# the first executable launches a couple of subprocesses so we need to
# keep Optirun alive for those.

import sys
import subprocess
import time
import os

if 'RUNNING_WITH_OPTIRUN' in sys.argv:
  home_dir = os.environ['HOME']
  subprocess.check_call(['wine', home_dir + '/.wine/drive_c/Program Files (x86)/StarCraft II/StarCraft II.exe'])
  # Wait for initial launcher subprocess to be called. It handles patch updates and such.
  time.sleep(10)
  # Keep alive until the launcher terminates.
  while subprocess.Popen(['pidof', 'Blizzard Launcher.exe'], stdout=subprocess.PIPE).communicate()[0]:
    time.sleep(5)
  # Wait for game executable to be called.
  time.sleep(5)
  # Keep alive until the game executable terminates.
  while subprocess.Popen(['pidof', 'SC2.exe', 'Agent.exe'], stdout=subprocess.PIPE).communicate()[0]:
    time.sleep(5)
else:
  # Call myself with optirun.
  subprocess.check_call(['optirun', sys.argv[0], 'RUNNING_WITH_OPTIRUN'])
```

Save the above script as **/usr/local/bin/starcraft2** (or whatever you prefer) and make it executable by running:
```
sudo chmod +x /usr/local/bin/starcraft2
```

Now you can launch StarCraft II by running:
```
starcraft2
```

Create a menu item for the script if you like. Enjoy!

---

### Post by lanking on 2013-03-20
Finally I got here and my problem was solved. Thanks a lot.

---

### Post by trove on 2013-06-15
Sup, I wanted to launch Counter-Strike GO but this game requires Steam to work properly. Game launches with only one issue - no VAC secure, which means I actually cannot play on most of servers. My command looks like this:
```
optirun wine /home/aleksander/.wine/drive_c/Program\ Files\ \(x86\)/Steam/SteamApps/common/Counter-Strike\ Global\ Offensive/csgo.exe
```
But right-click->properties on CS:GO shortcut on desktop says, that this game is launched by this command:
```
env WINEPREFIX="/home/aleksander/.wine" wine C:\\windows\\command\\start.exe steam://rungameid/730
```
Which basically means that the game is launched by URL steam://rungameid/730 - just like in windows.

Also I got only about 20-60 fps in game, while on Win7 i got over 100. Any ideas how to work this out?

---

### Post by Rob_H on 2013-06-16
> **trove said:**
> Sup, I wanted to launch Counter-Strike GO but this game requires Steam to work properly....

This thread is about StarCraft II, not Counter-Strike.

---

### Post by mJayk on 2013-06-19
Hello,

May I ask what the performance is like now-a-days with SC2 and Wine?

I'm more interested in smoothness and stability than being able to run the max graphics.

Matt

---

### Post by Rob_H on 2013-06-19
No performance/stability problems on my 2 year old mid-range desktop or 1 year old high-end laptop. It actually runs better on both than on my wife's Windows laptop, although that hardware is 3-4 years old.

---

### Post by Rob_H on 2013-06-19
Actually, about 1 out of 5 launches of the game, there will be a strange sound echo that doesn't go away until I relaunch it.

---

### Post by mefoheim on 2013-08-27
Hello,
Thank you for your tuto and time on this. I used it at home and it works perfectly fine. However, I tried to used primus as shown on this page: [http://m.webupd8.org/2012/11/primus-better-performance-and-less.html?m=1](http://m.webupd8.org/2012/11/primus-better-performance-and-less.html?m=1).
So I tries to modify your script but I do not know python at all. Instead of 'optirun' in your last line I tried to put 'vmode_blank=0 primusrun' but it does not work, I have errors. Could anyone help with this please?

---

### Post by mefoheim on 2013-08-27
If it can help, here is the error I get:
Traceback (most recent call last):
  File "/usr/local/bin/starcraft2", line 27, in <module>
    subprocess.check_call(['vblank_mode=0 primusrun', sys.argv[0], 'RUNNING_WITH_OPTIRUN'])
  File "/usr/lib/python2.7/subprocess.py", line 537, in check_call
    retcode = call(*popenargs, **kwargs)
  File "/usr/lib/python2.7/subprocess.py", line 524, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.7/subprocess.py", line 711, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1308, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

---

### Post by mfamphlett on 2014-08-10
I know this is a little old now but in case anyone else comes across this.

this script is not required if you want to use primusrun as the problem solved by this script was fixed in primusrun.

to run sc2 with primusrun simply run "primusrun wine <path to StarCraft II.exe>". Or you can add the primusrun command to the default launcher created by wine.

---

