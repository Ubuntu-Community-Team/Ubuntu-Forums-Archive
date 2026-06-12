---
title: "Error installing Half Life 2"
date: 2008-05-26
forum: Wine
---

### Post by ad_267 on 2008-05-26
After reading through [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games) and [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2890](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2890) I've successfully installed Steam and am trying to install Half Life 2 from CDs, but after switching to disc 2 I eventually get a dialog box saying "Installation ended prematurely because of an error."

Here's the output from the terminal:
```
adam@adam-desktop:/media/cdrom0$ msiexec /i hl2.msi
fixme:advapi:LookupAccountNameW (null) L"adam" (nil) 0x33f7fc (nil) 0x33f800 0x33f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"adam" 0x12db60 0x33f7fc 0x131f78 0x33f800 0x33f7f4 - stub
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
err:msi:msi_dialog_create_controls no handler for element type L"Billboard"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 1 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 6 ignored L"Shortcut" table values
err:msi:msi_view_get_row Error fetching data for 1
err:msi:ACTION_InstallFiles compressed file wasn't extracted (L"C:\\Program Files\\Valve\\Steam\\SteamApps\\half-life 2 base content.gcf")
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603

```

Hope someone can help

Cheers,
Adam

---

### Post by log on 2008-06-30
Hey, did you ever sort that out?

I tried copying the 5 cds to my HDD but that didnt work. Not sure what to try next? I get exactly the same error as you on CD 2,

---

### Post by ad_267 on 2008-06-30
No I never did get it sorted out. Ended up just uninstalling wine and forgetting about it. I didn't do too much research though but I couldn't find anyone else having this issue. If you get it sorted out or if someone else knows the answer I'd be happy to hear it though.

---

### Post by YokoZar on 2008-07-01
You can still install from steam by downloading, that works just fine

---

### Post by ad_267 on 2008-07-02
> **YokoZar said:**
> You can still install from steam by downloading, that works just fine

Yeah I think I did think of that at the time but didn't want to download all of that if I didn't have to and I wasn't really that worried. Maybe I will give it another go some other time though.

---

### Post by fmarier on 2009-03-01
Here's a way to manually install Half-Life 2 if the installer
won't let you go past the first CD.

1- Install using the installer until it fails
   (into the default directory -- C:\Program Files\Steam)

2- Copy all .cab files from all CDs into a temporary directory

3- Install the "cabextract" package and extract all of the game files:

  cabextract hlf2.CAB

4- Rename the files so that they look like this:

base source shared.gcf                   css.ico
base source shared materials.gcf         half-life 2 base content.gcf
base source shared models.gcf            hl2.ico1
base source shared sounds.gcf            Source Shared Securom.gcf
counterstrike source base content.gcf    winui.gcf
counterstrike source shared content.gcf

(note the dash in "half-life 2" and the spaces instead of underscores)

5- Start up Steam and go to the games tab, Half-Life should be in there

---

### Post by dean5 on 2010-04-29
Thanks alot, this seemed to get me up and running :D

---

