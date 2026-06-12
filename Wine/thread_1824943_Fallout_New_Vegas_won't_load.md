---
title: "Fallout New Vegas won't load?"
date: 2011-08-14
forum: Wine
---

### Post by cheesedog31 on 2011-08-14
So I have Fallout New Vegas, all the DLC's and the launcher.. it installed under wine without any problems but when i double click to load the actual game nothing happens.. so i right clicked the launcher to get the command to open it.. put that in terminal and got this....



env WINEPREFIX="/home/evan/.wine" wine C:\\Program\ Files\\Bethesda\ Softworks\\Fallout\ New\ Vegas\\FalloutNVLauncher.exe 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Bethesda Softworks\\Fallout New Vegas\\FalloutNVLauncher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Bethesda Softworks\\Fallout New Vegas\\FalloutNVLauncher.exe" failed, status c0000135


im not really sure what this means but does anybody have any idea how to fix this? (im still kinda noobish when it comes to tinkering with wine)

Thanks in advance, Evan

---

### Post by cheesedog31 on 2011-08-14
bump

---

### Post by kyletstrand on 2011-08-14
I've never seen this before, but a google search showed me that you might just need to add the MSVCP90.dll file to your system32 folder.
 
Check out this thread for better info:
 
[http://ubuntuforums.org/showthread.php?t=847535](http://ubuntuforums.org/showthread.php?t=847535)

---

### Post by kyletstrand on 2011-08-14
If you haven't done so, it's always good to check out the Wine AppDB for the program you're trying to run.  I've found that usually can offer some enlightenment to getting fussy programs to run.
 
Here's the link for Fallout New Vegas: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=21692](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21692)

---

### Post by cheesedog31 on 2011-08-14
> **kyletstrand said:**
> If you haven't done so, it's always good to check out the Wine AppDB for the program you're trying to run.  I've found that usually can offer some enlightenment to getting fussy programs to run.
 
Here's the link for Fallout New Vegas: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=21692](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21692)


i did check this out and didnt help me really at all. thanks though

---

### Post by cheesedog31 on 2011-08-14
ok so that first link kyle pointed me too fixed my original problem.. now the problem is i clicked on play.. and it blinks the screen black and sends me to the login screen for ubuntu... any idea why?

---

