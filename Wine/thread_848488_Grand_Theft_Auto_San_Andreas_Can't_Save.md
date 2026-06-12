---
title: "Grand Theft Auto San Andreas Can't Save"
date: 2008-07-03
forum: Wine
---

### Post by phildaman46 on 2008-07-03
I can't save my game while playing Grand Theft Auto San Andreas. I'm using Ubuntu 8.04 with Wine 1.1.0. When I try to save it says something like "Error saving. Check your Save Game directory". I have Wine configured so My Documents is set to Documents in my home folder and thats where my saves should be.

---

### Post by cogadh on 2008-07-03
It could be a bad permissions thing. Have you ever used sudo to run Wine or have you made any permissions changes to your home directory?

---

### Post by phildaman46 on 2008-07-03
No, the owner is set to me in the Permissions tab. I didn't install the game as root.

---

### Post by phildaman46 on 2008-07-03
Could it be a Wine problem?

---

### Post by cogadh on 2008-07-03
Unlikely, all the GTA games work perfectly (or nearly perfectly) in Wine. It probably has something to do with how you have reconfigured the directories in Wine. You might try setting it back to the defaults and see if that makes any difference.

---

### Post by phildaman46 on 2008-07-03
It worked before. Maybe I should go back to the 1.0 version of Wine.

---

### Post by phildaman46 on 2008-07-04
Would there be a saved games path somewhere in the registry that can be changed?

---

### Post by Sukarn on 2008-07-04
If GTA SA uses the registry for the address, then it should be in HKEY_CURRENT_USER->Software
Look for the game in there. I don't have it installed, and I clean up the registry after uninstalling any application.

I doubt its in the registry though. I think it calls the user documents directory directly from within the game by using that "%documents%/GTA San Andreas User Files" (or whatever it was, I forgot the default documents location).

From the looks of your situation, I would suggest recursively setting the file and folder permissions so that you have read and write access on everything in the "GTA San Andreas User Files" directory.

Right click "GTA San Andreas User Files" and go to "Properties -> Permissions" and after setting the permissions that you need to a tick mark (make sure its a tick mark and not a '-' sign) for both "Folder Permissions" and "File Permissions", click on "Apply Permissions to Enclosed Files". This recursively sets the file and folder permissions.

---

### Post by phildaman46 on 2008-07-04
That didn't work, I give up.

---

### Post by Sukarn on 2008-07-04
Maybe your save game files are corrupt? Try moving them to some other folder and starting a new game. See if the new profile is able to save correctly or not.

Just a thought. I can't really think of much else to do other than to check the permissions of ~/.wine and the game directory.

I'm off to bed now (2:35 AM). If you reply here then I probably will not see it for the next 9 hours.

---

### Post by phildaman46 on 2008-07-04
It won't let me save a new game.

---

### Post by Vhann on 2010-03-19
I was having the same problem the O.P. described in this thread and just figured out the answer. I know this thread is 2 years old, but since there's no solution here and the problem still exist...

Anyway, the cause of the problem, in my case, was that I used the ".wine" I created for a previous user (reinstalled the system and didn't want to lose my .wine (remember to "chown newuser:newgroup -R $HOME/.wine/" when doing that).


It appears that wine creates symlinks in "$HOME/.wine/drive_c/users/nameOfYourUser/" for various Windows directories (for instance, the "My Documents" symlink pointed to the $HOME of the old user (which didn't exist anymore). Changing this dead symlink to the $HOME of the new user solved the problem.

---

