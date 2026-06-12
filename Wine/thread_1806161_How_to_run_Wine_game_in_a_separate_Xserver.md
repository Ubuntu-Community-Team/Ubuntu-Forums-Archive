---
title: "How to run Wine game in a separate Xserver?"
date: 2011-07-17
forum: Wine
---

### Post by figure002 on 2011-07-17
Hi all,

I was very happy yesterday to find out the Call of Duty 4 works [flawlessly]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804") on Ubuntu 10.10 with Wine (wine-1.3.18). Well actually, sound doesn't work right with the default wine, so I had to install a patched version of Wine with PulseAudio support, called [WinePulse]("http://art.ified.ca/?page_id=40"). I didn't feel like patching and compiling myself, so I just installed Wine with PulseAudio support from a [PPA]("https://launchpad.net/%7Ec-korn/+archive/ppa").

CoD4 runs without any problems; graphics look good and it runs fast. But right now it runs in the same xserver where my desktop runs. This has some disadvantages; the game runs slower because Compiz and stuff is running in the background. Also, if the game is in a lower resolution, it might mess up your desktop. And there are even more advantages I won't mention here.

The thing is, I want to run Call of Duty 4 in a separate xserver. I already know [how to run games in a separate xserver]("http://ubuntuforums.org/showthread.php?t=51486"), and it works great for native Linux games (I use it for games like Quake Wars, Penumbra, etc.). But I can't get it to work for a game that needs to start with Wine.

For example, if I run:
```
xinit /usr/bin/env WINEPREFIX="/home/serrano/.wine" /usr/bin/wine "/home/serrano/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare/iw3sp.exe" -- :1
```The screen switches to a new xserver, and in that xserver I'm presented with a graphical error message:
> WIN_IMPROPER_QUIT_BODY
[Yes] [No] [Cancel]If I answer Yes, it gives me the following error,
> Error during initialization:
Couldn't load fileSysCheck.cnf. Make sure Call of Duty is run from the correct folder.
[OK]Does anyone know how to run a Wine game in a separate xserver?

---

### Post by JustinR on 2011-07-18
I would try replace the spaces in the path to the game with "\ " (a backward slash and then a space).

I run the Sims 3 from wine in an external X-server, my file looks like this:

> 
#!/bin/bash
xinit /usr/bin/sudo -u justin /usr/bin/wine /home/justin/.wine/drive_c/Program\ Files/Electronic\ Arts/The\ Sims\ 3\ Ambitions/Game/Bin/TS3EP02.exe $* -- :1


I had to add "/usr/bin/sudo -u justin" because the dpkg-reconfigure command from the guide above that you posted didn't let me change X-server permissions.

---

### Post by figure002 on 2011-07-20
JustinR,

Thanks for your reply. That didn't solve the problem however. I got the exact same error.

---

### Post by figure002 on 2011-08-02
I asked the same question on the WineHQ forums and posted the solution there as well. URL to that thread: [http://forum.winehq.org/viewtopic.php?p=64164](http://forum.winehq.org/viewtopic.php?p=64164)

The solution is as follows. First, to get rid of the two errors I mentioned, one first needs to change to the directory containing the game executable. In my case,
```
cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare/ 
```Once you changed to that directory, you can start the game like usual (replace iw3sp.exe by the game's executable),
```
xinit /usr/bin/wine iw3sp.exe -- :1
```The game will now successfully launch in a separate xserver. If like me you're using WinePulse, you won't hear any sound when in the game. But you will hear sound if you switch back to the xserver containing your desktop (Ctrl+Alt+F7). In order to fix this, one needs to execute wine with 'ck-launch-session' which in my case was already installed on my Ubuntu machine.

The commands to launch a WinePulse game (with working sound) in a separate xserver will then look like this,
```
cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare/
xinit /usr/bin/ck-launch-session /usr/bin/wine iw3sp.exe -- :1 
```I've tested this approach with both Call of Duty 4 and Need for Speed Underground 2, and both run flawlessly. \\:D/

---

