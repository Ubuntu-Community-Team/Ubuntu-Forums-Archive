---
title: "Program Error: Cannot update Cursor - HELP!"
date: 2008-01-17
forum: Wine
---

### Post by akalberm on 2008-01-17
I just installed linux a few days ago, but am only trying to use wine now.  I have a Datachem CD (Professional Study CD) that I am trying to study for a test from, but am unable to get it running.  I got the program installed ok off the CD, but when I try to run the program, I get a program error stating the following "Cannot update the cursor".  From the program error, there is a "Cancel", "Ignore", and "Help" button.  The help button doesn't actually do anything when I click on it.  The cancel button closes the program and exits the operation.  And I am not quite sure what the ignore button is trying to do.  It appears to open a window called "Set or Reset Options".  From there, it wants me to choose a database - which i do find on the cd, then it wants me to select a stylesheet (DC6.CSS), which I cannot find anywhere on the computer or CD when I try to scroll for it.  The other options are Background image which appears to be set, display resolution that is set, and default exam time which is set.  I then have two options at the bottom - "Save Settings" and "Cancel".  If I cancel the program closes just as before, If I save settings, the "Cannot update cursor" program error comes back up and then the program closes.

Any help would be appreciated!! I have tried searching for about 30 minutes but have not found anything.... Thanks in advance!

---

### Post by akalberm on 2008-01-18
Ok - Some updates...

I tried to run the program from linux with all of the different windows versions, and nothing worked... Still the same scenario above...

I also installed the CD on a windows machine.  Everything worked in XP and the cursor screen did not load at all.  This makes me think that it has something to do with Wine specifically.  Since I have not used Wine with any other windows software, is it possible that there is something I have to configure?  I did not see anything in any configurations area's that I thought could cause this error.

Any help would be appreciated!  Thanks!

---

### Post by akalberm on 2008-01-23
Anyone???  I have been stuck without any progress for quite some time now.  Thanks

---

### Post by happyhamster on 2008-01-23
It's possible that the program tried to write to a read-only file. Or perhaps that file is stored somewhere where you don't have the right permissions (which usually means that wine isn't configured properly).

See for info:
[http://www.datachemsoftware.com/techfaq.htm#cursor](http://www.datachemsoftware.com/techfaq.htm#cursor)

What you can try is:
- Make sure that you have a clean wine installation (it's possible to mess up wine by running wine or winecfg or anything wine-related as root for example).
- If you choose to re-install wine, then first get rid of it completely:

sudo apt-get remove --purge wine

- And delete or move the hidden .wine folder in your home dir. Path is usually:

~/.wine

- You can also easily find it using nautilus: just open your home folder and choose View-->Show Hidden Files.

- Next, re-install wine:

sudo apt-get install wine

- Run winecfg, to configure things:

winecfg

- (don't use sudo).

- Install your program (don't use sudo), and try if it works. If not, browse to where your program is  installed (probably in the ~/.wine/drive_c/Program Files/ folder and check if some files are read-only when they should be read/write.

Good luck.

---

