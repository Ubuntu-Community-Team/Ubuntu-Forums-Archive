---
title: "Diablo III breaks with each new patch"
date: 2012-05-31
forum: Wine
---

### Post by #!/bin/bash on 2012-05-31
I had D3 working yesterday, then today they had another patch. Most D3 users are quickly learning to dread these patches.

Does anyone have D3 5/31/2012 patch 1.0.2.9858 working with wine?

According to the patch log everything worked fine, however I get stuck at **Launching...** when trying to run the game.
```
This patch upgrades Diablo III from version 1.0.2.9749 to version 1.0.2.9858.
Installing Diablo III at "C:\Program Files\Diablo III\" on Thu May 31 15:39:10 2012.
Created file "C:\Program Files\Diablo III\Bnet\battle.net.dll".
Created file "C:\Program Files\Diablo III\Diablo III Launcher.exe".
Created file "C:\Program Files\Diablo III\Diablo III.exe".
Created file "C:\Program Files\Diablo III\fmodex.dll".
Created file "C:\Program Files\Diablo III\icudt44.dll".
Created file "C:\Program Files\Diablo III\icuin44.dll".
Created file "C:\Program Files\Diablo III\icuuc44.dll".
Created file "C:\Program Files\Diablo III\ijl15.dll".
Created file "C:\Program Files\Diablo III\InspectorReporter\BlizzardError.exe".
Created file "C:\Program Files\Diablo III\Logs\Blizzard Updater Log.html".
Created file "C:\Program Files\Diablo III\Microsoft.VC90.CRT.manifest".
Created file "C:\Program Files\Diablo III\msvcp90.dll".
Created file "C:\Program Files\Diablo III\msvcr90.dll".
The update was successful.
```

If you have patch 1.0.2.9858 working with wine, what wine version. And would you mind posting the md5sum's of the above files.

tyia

---

### Post by #!/bin/bash on 2012-06-01
OK I may have just figured this thing out.

This is my 2nd patch since getting Diablo III to work, and both times I had major down time. The senario was similar both times.

1 Start D3 as usual
2 Checks game and starts to download a patch.
3 Download complete.
4 Click PLAY and it freezes at Launching...
5 Search Internet and try every fix posted and nothing works.

Everything seems to work except the game will not start after the patch. As you can see from my original post the patch log (.wine/drive_c/Program Files/Diablo III/Logs/Blizzard Updater Log.html) says **The update was successful.** I also noticed that it would repeat the patch process every time I tried to start D3. It was as if there was a file that was supposed to tell it that the patch was complete but the file was not being updated properly.

I started poking through the file
.wine/dosdevices/c:/users/Public/Application Data/Battle.net/Agent/Logs/agent.db
And I noticed there were 2 locations in the file with these 3 lines:
"patch_application_complete" : false,
"perform_ogg_to_wav" : false,
"download_complete" : false,


The lines are located at 196, 197, 198 and 246, 247, 248 in my file.

I made a backup of the file and then changed the 3 lines in both locations, to:

"patch_application_complete" : true,
"perform_ogg_to_wav" : true,
"download_complete" : true,

I started D3 one more time and lo and behold it said it was up to date! I clicked the PLAY button and it WORKED!

---

### Post by morganm on 2012-06-21
Worked for me, thanks for sharing!

---

