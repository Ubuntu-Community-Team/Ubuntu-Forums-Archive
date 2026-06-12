---
title: "Mitchell on Demand"
date: 2012-01-10
forum: Wine
---

### Post by tarutaruomen on 2012-01-10
Hi, I'm writing because i've been trying to install an automotive software called Mitchell on Demand using wine.  The software normally uses a floppy disk with a key as an authentication method and uses 11 dvd's that contain the vehicles' data.  Once I enter the paths of where the discs data is located the software tries to write that information in the c:\ drive but for some reason it gives me an error because the software doesn't have permissions to write to the folder because i'm not the owner of that folder.  I would like to know how can I fix it so that the software can write to those folder without breaking anything.
I have the key and simply mounted the image of the floppy.  I went through the authentication well.

---

### Post by bluexrider on 2012-01-10
This is a really a question for the WINE section.

Under 'Configure Wine' About tab, make sure you have the Windows Registration information filled in. 'Owner' and 'Organization'

---

### Post by oldos2er on 2012-01-10
Moved to Wine.

---

### Post by tarutaruomen on 2012-02-27
Tried that but I still get the same problem.  If I try to open it with sudo it says that my ./wine folder is not owned by me.  This is what I believe is causing me the problem.  Since I'm not recognized as the folder owner then the program can't put the information in the folder as it normally does since it is protected.

---

