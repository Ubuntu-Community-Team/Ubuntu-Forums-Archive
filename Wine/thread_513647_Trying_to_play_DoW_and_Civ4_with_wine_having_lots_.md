---
title: "Trying to play DoW and Civ4 with wine having lots of dll problems since"
date: 2007-07-30
forum: Wine
---

### Post by Scotty562 on 2007-07-30
When I was using wine-0.9.41 Dawn of War and civ4 worked fine when I went into their directory and did wine "game." Since I updated to wine-0.9.42 I get all kinds of dll errors. See below.

There is a whole lot more than this, but they are just different dlls. It is like wine is now looking for these dlls in a different location and I have no idea where it is looking. Whats going on?

edit: It actually says it couldn't find the "DarkCrusade.exe" I ran to get this error O.o. Whats going on!?

```
err:module:import_dll Library Platform.dll (which is needed by L"Z:\\media\\sda1\\Program Files\\THQ\\Dawn of War - Dark Crusade\\Filesystem.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\sda1\\Program Files\\THQ\\Dawn of War - Dark Crusade\\Debug.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\sda1\\Program Files\\THQ\\Dawn of War - Dark Crusade\\Debug.dll") not found
err:module:import_dll Library Debug.dll (which is needed by L"Z:\\media\\sda1\\Program Files\\THQ\\Dawn of War - Dark Crusade\\Memory.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\sda1\\Program Files\\THQ\\Dawn of War - Dark Crusade\\Memory.dll") not found
err:module:import_dll Library Memory.dll (which is needed by L"Z:\\media\\sda1\\Program Files\\THQ\\Dawn of War - Dark Crusade\\Filesystem.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\sda1\\Program Files\\THQ\\Dawn of War - Dark Crusade\\Filesystem.dll") not found
err:module:import_dll Library Filesystem.dll (which is needed by L"Z:\\media\\sda1\\Program Files\\THQ\\Dawn of War - Dark Crusade\\DarkCrusade.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\sda1\\Program Files\\THQ\\Dawn of War - Dark Crusade\\DarkCrusade.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\sda1\\Program Files\\THQ\\Dawn of War - Dark Crusade\\DarkCrusade.exe" failed, status c0000135

```

---

### Post by desicratn on 2007-08-01
I am having the exact same issue. I tried installing the .dll's and it did nothing. There isnt anything wrong with the program. The wine update borked something that makes wine not see the .dll's in the folder. Just go into synaptic and force wine back to the 9.41 version and it will work  just fine, then you can go back and get your Waaaaaaaaaaaggghhhhh on.

---

### Post by Sugi on 2007-08-12
i have .42, and i tryed installing DoW, and it didn't start up after installing it.  I don't like .0.9.42 at all. :-/  I guess, I got to go back to .41,  It seems like it's working for that patch version.

Can you install two different wine versions?

---

### Post by axcairns on 2007-09-05
Have a look on this page ([http://appdb.winehq.org/appview.php?iVersionId=6051]("http://appdb.winehq.org/appview.php?iVersionId=6051")) in the section named 'Glitches'. It shows how to compile and install another version of wine without borking the version installed by apt.

I've found major framerate issues with DoW in the latest gutsy wine (42 I think). Following the instructions in the link I installed wine 0.9.35 which fixes the framerate issue but sound stutters and must be turned off. I am playing with various wine versions and a patch also mentioned on that page to try and find a version that has good framerates AND good sound.

Allan

---

### Post by buntunub on 2007-09-05
Whats the deal with Civ IV? You got that working?.. It will not work for me at all in either wine or Cedega.

---

### Post by phr0ze on 2007-09-05
Civ IV works great for me with Wine. It took me a while to sort all the problems out, but now it is great. I have not gotten the expansions to work yet. I mostly followed the instructions in the Wine AppDB and also installed the latest wine from wine repos.

---

