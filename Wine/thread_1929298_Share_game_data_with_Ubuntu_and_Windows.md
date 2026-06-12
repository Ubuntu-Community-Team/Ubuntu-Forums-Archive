---
title: "Share game data with Ubuntu and Windows"
date: 2012-02-21
forum: Wine
---

### Post by FireDart on 2012-02-21
Hello,
Recently re-installed Ubuntu on my pc (Separate drive) and this time it's here to stay. One major issue I have with a total conversion is I still play PC games, so... Can I share the game data on both Ubuntu and Windows so one, I don't have two copies of the same game, and two my data is synced?

Right now I have a drive for both Ubuntu (120GB SDD) and Windows (120GB SDD) and keep my games on a separate 1 TB.

As I am aware Wine unpacks the game then creates a registry of the game in a WINE folder, then runs the game in a virtual box. So I don't see why I could not do this, you know, same files, etc... 

Yet I am unable to find any documentation on it. The only issue I see is creating the registry on a per-installed game (installed threw Windows).


Does anyone have any advice?
-Julian

P.S The reason am keeping Windows is just in case I can't run a game on WINE for wither performance and/or bugs, and yes I could just switch between the 2 or run Ubuntu virtually in Windows but neither of these set-ups really appeal to me. Am really trying to do everything in Ubuntu.

---

### Post by FireDart on 2012-02-25
Does anyone have an suggestions?

---

### Post by HolgerB on 2012-02-26
Usually WINE keeps the installed games under ~/.wine/drive_c

There you will find the folders like Program Files, Windows and so on.
If you are willing to risc both your Windows as well as your wine installations, you could mount the original Windowsdrive and create a symlink from your User directory of Windows to the corresponding folder inside wine (~/.wine/drive_c/users/your_username)

The same applies to Program Files as well...

Of course WINE will interfere with Windows and vice versa.
So you easily risk screwing up both :-\"

A better approach might be writting two sync script which syncs the save games from Windows to WINE and vice versa.

Good luck,
H.

---

### Post by FireDart on 2012-02-26
I see, thank you for the suggestions. Time to do some more research.

EDIT: Now that I think about it, since I use STEAM for most of my games would the STEAM Cloud be enough to sync my data? I know all games are not supported but a good amount of them are. Anyone have experience with this?

---

### Post by HolgerB on 2012-02-26
> **FireDart said:**
> I see, thank you for the suggestions. Time to do some more research.

EDIT: Now that I think about it, since I use STEAM for most of my games would the STEAM Cloud be enough to sync my data? I know all games are not supported but a good amount of them are. Anyone have experience with this?
The Steam cloud might be an option but a more simplistic approach could be this (given that your games run both under Windows & WINE):

Generate a start shell script for your game under WINE which does the following:
1) Sync your save games over from the Windows partition to the corresponding path under WINE
2) Launch the game under WINE
3) Sync back the save games from WINE to the Windows partion.

By this approach you have pretty much full control about the data flow. You could even generate backup of save games prior copying.

HTH,
H.

---

### Post by FireDart on 2012-02-26
So I could do something like this?
```

sudo rsync -azvv /dev/sdb1/.wine/drive_c/<GAME PATH> /dev/sdb1/Games/<GAME PATH>
wine "C:\Program Files\<GAME PATH>\<GAME NAME>.exe"
```Also /dev/sdb1/ is my large drive so I plan on storing the games on it. Just need to change the location WINE looks for the ~/.wine/ folder.

---

### Post by HolgerB on 2012-02-26
I would keep the games installed doubled.
One copy under the wine folder and one under the original Windows partion.
Then simply mount the windows partition somewhere and sync the save games from the windows partition back and forth.

Older games of course often are more self-contained. In other words: You can simply copy over the installed game to your Linux partition and run it via WINE.
In this case doubled installation is not required.

---

### Post by FireDart on 2012-02-26
Gotcha, time to try it out.

---

