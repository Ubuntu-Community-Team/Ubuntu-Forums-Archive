---
title: "Temp files / utorrent and wine"
date: 2008-03-13
forum: Wine
---

### Post by tehwabbit on 2008-03-13
I have had wine installed for a while now, and now when i install new programs im getting errors all over the shop!

For a start i have had utorrent 1.8 on ubuntu (previous install) and it worked fine but since i reinstalled now i can RUN the utorrent.exe (both standalone and install) but the files arent being stored in "c_drive" :(

Also i keep getting errors about programs not being able to write to the temp directory..... any ideaS?

I hope its fixable due to me using utorrent as a method of internal filesharing

---

### Post by gsmanners on 2008-03-14
My guess would be that you need to run winecfg, then select "Autodetect" in the Drives tab.

---

### Post by kulight on 2008-07-12
deleted

---

### Post by kulight on 2008-08-01
i have a similar problem

first utorrent 1.7.7 work great

when trying utorrent 1.8 i get errors when loading .torrent files

1. when loading from firefox i get:
unable to load 
/tmp/xxx.torrent
path not found

2. when loading from my torrents folder i get:
unable to load 
/path/to/torrent/folder/xxx.torrent
path not found

i have tried autodetect in wine cfg reinstalling wine using different versions of wine nothing helps
 
please help

---

### Post by kulight on 2008-08-05
i guess im the only one with that issue

---

### Post by lmellor on 2008-08-12
> **kulight said:**
> i guess im the only one with that issue

no you're not, I'm getting it too and it's beginning to wind me up

:mad:

---

### Post by lmellor on 2008-08-12
I have found a temporary solution which could become permanent in my eyes, give deluge a shot, it had all the features I use in utorrent that all other clients seem to lack (mainly a scheduler and being lightweight).

I'm hooked, plus it's native so no need for wine :)>

---

### Post by kulight on 2008-08-13
deluge is quit good but its not there yet at least for me and also im getting much better speeds with utorrent 
iv'e posted this on utorrent forums as well feel free to post there:
[http://forum.utorrent.com/viewtopic.php?pid=348148#p348148](http://forum.utorrent.com/viewtopic.php?pid=348148#p348148)

---

### Post by AzureCerulean on 2009-03-23
I use Crossover office and this is the script file i use

#!/bin/sh
/opt/cxoffice/bin/wine /home/{user name}/.cxoffice/{bottle name}/drive_c/Program Files/uTorrent/uTorrent.exe 


where user name is my login name 
and bottle is the wine bottle i am using

so for wine it sould be something like

#!/bin/sh
/usr/bin/wine /home/{user name}/.wine/drive_c/Program Files/uTorrent/uTorrent.exe 

i think...

---

### Post by kulight on 2009-03-23
sorry for not updating before...

i found a solution when discussing this problem at utorrent forum
the script i use is:

#!/bin/sh
wine /home/{Your_User_Name}/.wine/drive_c/Program\ Files/uTorrent/uTorrent.exe "z:$*"

puted in a file called utorrent placed at path: /usr/bin

and then granted runing permissions using the command:

sudo chmod a+x /usr/bin/utorrent

now pointing firefox to that file when downloading .torrent files will start utorrent

---

### Post by NightMKoder on 2009-03-23
> **kulight said:**
> sorry for not updating before...

i found a solution when discussing this problem at utorrent forum
the script i use is:

#!/bin/sh
wine /home/{Your_User_Name}/.wine/drive_c/Program\ Files/uTorrent/uTorrent.exe "z:$*"

puted in a file called utorrent placed at path: /usr/bin

and then granted runing permissions using the command:

sudo chmod a+x /usr/bin/utorrent

now pointing firefox to that file when downloading .torrent files will start utorrent

If you want to convert a unix path to a windows path, I would suggest using winepath -w . So for the example, something like:

```

#!/bin/sh
wine "C:\\Program Files\\uTorrent\\uTorrent.exe" "`winepath -w \"$*\"`"

```

---

### Post by Miaxi on 2009-03-24
Did you try the newest Deluge version? [http://www.getdeb.net/app/Deluge](http://www.getdeb.net/app/Deluge)

Also, there is a setting in uTorrent to auto-open all torrents from a certain path, like the desktop. That works just as well as "open with".

---

### Post by kulight on 2009-03-24
> **NightMKoder said:**
> If you want to convert a unix path to a windows path, I would suggest using winepath -w . So for the example, something like:

```

#!/bin/sh
wine "C:\\Program Files\\uTorrent\\uTorrent.exe" "`winepath -w \"$*\"`"

```

what is the difference? and why is it important?

im trying the new deluge version and it is very good it came a long way only thing is sometimes it takes a little to much cpu 
but not a deal breaker im considering switching to deluge...

---

### Post by NightMKoder on 2009-03-24
Because it converts any path to the correct drive letter. Z: is the root, but if you have something, say, on a CD, then you would need to map /media/cdrom to D:\ . Winepath does this for you.

[http://wiki.winehq.org/winepath](http://wiki.winehq.org/winepath)

In short - its The Right Way.

---

### Post by kulight on 2009-03-24
ok good explanation...
and it works so ill use your script

thank you

---

### Post by tzily on 2011-01-26
thank you guys, this still is an issue
for some reason drag and dropping torrents in utorrent was the only solution to load them for a while
but now i've made that script file and changed the .torrent to 'open with' it and not with the old command: wine 'utorrent.exe path'

i can finally double click a torrent and actually load the thing without wrong path error
i've tried everything until now :D

:popcorn:

---

