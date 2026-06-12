---
title: "Unable to Patch Warcraft 3 in Dapper"
date: 2007-04-24
forum: Wine
---

### Post by cents on 2007-04-24
I'm new to linux.  My Wine version is 0.9.9 (??? The website says the latest is 0.9.35).  I've installed Warcraft 3 RC and TFT using wine as instructed in [http://ubuntuforums.org/showthread.php?t=45407](http://ubuntuforums.org/showthread.php?t=45407) and am now trying to apply patch 1.21a.  I'm able to run War3 with no problems, except when trying to connect to Battle.net

Typing "wine War3TFT_121a_English.exe" while in the game directory starts the patch, which then returns the following error:

"Blizzard PrePatch v2.70 compiled on Jul  7 2003
This program patches Warcraft 3

Log created at  9:55 am on 04/24/2007

ERROR: unable to create file 'C:\Program Files\Warcraft III\BNUpdate.exe'
Access denied

RESULT: Prepatch failed"

Attempting to log onto Battle.net displays an ingame error stating the following:

"There was an error writing to your hard drive while trying to download a file from Battle.net.  You may need to free some space.  Please check your hard drive and try again."

How do I get the patch to work?  Thanks.

---

### Post by lordhebe on 2007-04-24
Get the latest version of wine following the instructions here: [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

### Post by cents on 2007-04-24
I fixed the problem by editing the following registry key:

HKEY_LOCAL_MACHINE\SOFTWARE\Blizzard Entertainment\Warcraft III\InstallPath 

I changed it's value from the installtion directory (for me, c:\Program Files/Warcraft III) to c:\wc3

I then created a symlink:

% cd ~/.wine/drive_c
% ln -s Program\ Files/Warcraft\ III wc3

Applying the patch worked.

---

### Post by cents on 2007-04-24
I spoke to soon.  The problem hasn't gone away.  I was able to patch WC3 and am now using version 1.21 but still get the same error message when attempting to connect to Battle.net.   I've updated wine to version 0.9.35 and am unsure what to do next.  Any ideas?

---

### Post by bzz_ on 2008-07-04
Hey, one thing you might want to try is:

> 1. Navigate to your Warcraft III directory (For me this is /media/Primary/Warcraft III)
2. Rename BNUpdate.ex to BNUpdate.bak
3. Rename patch.txt (if it exists) to patch.bak
4. Run the patch again
5. If it is successful, delete BNUpdate.bak and patch.bak

Hope this helps somebody!

The post is a little old, but there was just a patch released recently.. this is how I fixed my issue without logging onto my Windows partition to update it.

---

### Post by osenboz on 2008-08-28
hey, 
maybe it's a little bit late... but i had the same problem, and i fixed it !!

just select all files and put away the write-protection.
then try the patch again !

for me it worked....

---

