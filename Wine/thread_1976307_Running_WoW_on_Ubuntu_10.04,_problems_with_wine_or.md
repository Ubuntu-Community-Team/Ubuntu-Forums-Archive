---
title: "Running WoW on Ubuntu 10.04, problems with wine or system requirements"
date: 2012-05-08
forum: Wine
---

### Post by Strebenherz on 2012-05-08
As noted I've been attempting to successfully run W.O.W. on my laptop, on which Ubuntu 10.04 is installed.  During the installation, I received the message...
"Your computer fails to meet the minimum system requirements.  Insufficient CPU Speed (Learn More) [Install Anyway] [Exit Installer]"

The friend who was currently egging me to Install WOW said to disregard the message, on the basis that they had, and run into no problems, and so I did.  Later on when actually loading the WoW launcher, I ran into this fun little message...
"[Title : Program Error] The program Launcher.exe has encountered a serious problem and needs to close.  We are sorry for the inconvenience.  This can be caused by a problem in the program or a deficiency in Wine.  You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.  If this problem is not present under Windows and not has been reported yet you can report it at [http://bugs.winehq.org](http://bugs.winehq.org) [Close]"

Not really sure how to go about fixing this, whether my friend was wrong and the installer was correct with the warning about my system not having the correct specifications, or whether it's related to a problem with wine I've been having lately.  

"Could not download all repository indexes - The repository may no longer be available or could not be contacted because of network problems.  If available an older version of the failed index will be used.  Otherwise the repository will be ignored.  Check your network connection and ensure the repository address in the preferences is correct."
"Failed to fetch [http://wine.budgetdedicated.com/archive/source/dists/ubuntu/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/archive/source/dists/ubuntu/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://wine.budgetdedicated.com/archive/source/dists/ubuntu/main/source/Sources.gz](http://wine.budgetdedicated.com/archive/source/dists/ubuntu/main/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

Any help would be fantastically greatly amazingly wonderful, thank you.
If I posted this twice, sorry, had problems editing something.

---

### Post by jerome1232 on 2012-05-08
Try running wow.exe directly instead of launcher.exe, back when I played wow I would get issues with the launcher sometimes.

---

### Post by Strebenherz on 2012-05-08
Thank you Jerome.  Tried that just now, got another odd error message.
"This application has encountered a critical error:"
"ERROR #121 (0x85100079) Version Mismatch"
"Program:     C:\Program Files\World of Warcraft\Wow.exe"
"DBFilesClient\AnimationData.dbc has wrong row size (found 24, expected 32"
"Press OK to terminate the application"

---

### Post by jerome1232 on 2012-05-08
Sounds like a corrupted install to, try running wow's repair utility, and go from there.

What version of wine are you using?

---

### Post by Strebenherz on 2012-05-08
Running the repair tool now.  And wine version 1.2.2, gyah.  Working on updating that now.  Thought it was updated, yeep.

---

### Post by oldos2er on 2012-05-09
Thread moved to Wine.

---

