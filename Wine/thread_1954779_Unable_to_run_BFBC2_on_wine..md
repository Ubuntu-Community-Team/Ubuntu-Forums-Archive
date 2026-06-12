---
title: "Unable to run BFBC2 on wine."
date: 2012-04-08
forum: Wine
---

### Post by Devin Leith on 2012-04-08
I recently bought a copy of Battlefield Bad Company 2 and successfully installed it from the disk using Wine 1.3. After the installation I tried to run the game by copying the .exe into the terminal and I got a long list of 'fixme:win:enumdisplaydevices' followed by ((null) and a bunch of seemingly random numbers and 'Stub!'. I have attached, I think, a screenshot of the terminal after running this game. I have tried multiple fixes found on other forums, but they only led to other errors, which led me to other fixes and other errors ect. I'm starting to think that a re-install might be needed based on the fact that almost all the programs I install seem to get a lot of errors. First time posting on a forum like this so if I'm not doing it correctly let me know.

---

### Post by schtufbox on 2012-04-08
from the WineHQ appdb:

> You will have to manually set BC2 to use directx 9 and not 10.

To do this do the following:

Go into ~/.wine/drive_c/users/username/My Documents/BFBC2Folder

open settings.ini and set the value of DxVersion from Auto to 9
That any help?

---

### Post by Devin Leith on 2012-04-08
Followed those steps, but still got the same error message on running the exe in the terminal.

---

### Post by Devin Leith on 2012-04-09
Just to update, after having more problems, which weren't  related to this, I reinstalled ubuntu 11.10 and have tried to install and run the game again. Installation went fine, but I still got the same error message as before.

---

