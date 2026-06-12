---
title: "GTA San Andreas: very slow"
date: 2007-10-10
forum: Wine
---

### Post by NTAuthority on 2007-10-10
I am using Ubuntu Feisty with Wine 0.9.46~winehq0~ubuntu~7.04-1, the latest from the repositories. Also, I'm using an ATI X300 card, which used to run it nicely on the lowest settings on Windows, with the drivers 8.41.7.

But, on Ubuntu, the game is very slow with Wine, even on the lowest settings. Vertex shaders off, or pixel shaders off, or both off does not matter. The intro cutscene after choosing 'New Game' runs at correct speed, but the game itself, after skipping it, or letting it finish, goes with something like 3 to 5 frames per second. It also runs slow with the -opengl option, by the way. :(

Could anyone help me? :)

-- Bas

---

### Post by Bekker on 2007-10-10
First question in these cases is: did you install the videocard drivers?
A simple way to check this is issuing the following command in a shell: glxinfo | grep direct
It should say "direct rendering: Yes"

If it doesn't, try to find a guide on how to set up your videocard. There are enough guides for that on this forum.

---

### Post by NTAuthority on 2007-10-10
The graphics drivers are correctly installed, which I also told in the first post. :) Maybe I was not clear enough, but:

> bas@bas-desktop:~$ glxinfo | grep direct
direct rendering: Yes
bas@bas-desktop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: ATI Technologies Inc.


Also:

> 
bas@bas-desktop:~$ aptitude show xorg-driver-fglrx | grep Version
Version: 8.41.7-1


---

### Post by Bekker on 2007-10-10
I'm sorry, I red to fast.

San Andreas seems to get worse performance using wine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780")
According to some of the comments there.

All I can add is that it ran fine last time I checked, but that was with an nvidia card and an older wine version...

---

### Post by naazgull on 2007-10-10
Hi,

Usually, i don't run games over wine but over Cedega, which is a wine port, specialized in running win32 games.

Cheers,

---

### Post by hikaricore on 2007-10-10
> **naazgull said:**
> Hi,

Usually, i don't run games over wine but over Cedega, which is a wine port, specialized in running win32 games.

Cheers,

.... Don't mislead the OP with your vague Cedega cheering, you didn't even bother to mention how/if GTA:SA runs via Cedega /w similar hardware.  If you're not sure I suggest you refrain from this sort of activity.

BTW your signature, **Open Source, Open Mind**, following that comment...is beautifully hypocritical.

---

### Post by vexorian on 2007-12-24
How do you use -opengl ? It looks like it is my last hope to make this one work.

---

### Post by vexorian on 2007-12-24
> **vexorian said:**
> How do you use -opengl ? It looks like it is my last hope to make this one work.

To those that have had this problem, I solved mine following [http://wine-review.blogspot.com/2007/11/gta-sanandreas-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/11/gta-sanandreas-on-linux-with-wine.html) (aka Disable pixel shaders with winecfg...)

The game runs fine and its performance is good enough to play it, so I am glad, I only need to do something about the issue in which it changes ubuntu's resolution when you exit.

---

