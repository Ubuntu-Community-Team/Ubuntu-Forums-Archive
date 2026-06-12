---
title: "Issue with running games in wine"
date: 2011-09-29
forum: Wine
---

### Post by theoreo25 on 2011-09-29
hi guys,
so im trying to figure out how to use wine, i have a game file that i want to try out but every time i try to run the "install.exe" i get an error pop up which reads 
"The file '/home/baxter/.gvfs/ResidentEvil4.iso/install.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

i tried running "chmod 755 install.exe" within the correct directory in terminal but i had no luck with getting the permissions to change. 

Any suggestions?

Thank You

---

### Post by anewguy on 2011-09-29
First, do this in a terminal:

ls -al /home/baxter/.gvfs/ResidentEvil4.iso/install.exe

Be sure the 3 groups for permissions each have the "x" - if not, you haven't gotten things set for execute yet.  I just did a brief test on a file in my home folder - 755 didn't set the execute bit - 733 did.  I know there are probably other combos that will as well, but try 733 first.


Dave ;)

---

### Post by Perfect Storm on 2011-09-29
Moved to Wine section.

---

### Post by staticd on 2011-09-29
add the  /home/baxter/.gvfs/ResidentEvil4.iso/ as a windows drive(eg F:\) in your wine config. same for CDs. windows executables outside these directories will not be run by wine. prevents windows malware from running amok.

---

