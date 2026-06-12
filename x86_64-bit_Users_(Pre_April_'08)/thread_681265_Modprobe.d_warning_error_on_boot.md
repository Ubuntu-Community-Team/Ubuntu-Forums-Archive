---
title: "Modprobe.d warning error on boot"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by freeatlast on 2008-01-28
This is my fault.

I have been using ubuntu for about a week.  I was trying to acroread to work on 64-bit gutsy distribution.  I downloaded the 32-bit xulrunner-1......tar.gz to get the libraries and happened to be in the /etc/modprob.d dir when i downloaded it.

I restarted and it tried to read the file and produced an error at every line, about 30,000 of them.  I deleted the file, but still got the messages.  I tried modprobe -r but then I got a fatal error since it could not be found.  I copied the file back to the directory and tried modprobe -r again and it scrolls thru the file, but does nothing other than change the fonts on the page to nonsensical characters and i have to close the terminal.    upon restart I still get the error message (modprobe.d warning bad line in....)

I thought it could be in a fiel somewhere and tried grep -r on a large chunk of my system to no avail.  any advice on how to get rid of the errors?  the only thing they appear to do is slow down my boot.

thanks

---

### Post by prince_niceguy on 2008-01-29
did you delete the file in the recovery mode or from the gui terminal after the login into the ubuntu?

try deleting the file from modprobe.d directory and if that does not work out then add the file name in the modprobe.d/blacklist file. you should add the file name as

blacklist <file name>

replace <file name> with the name of the file ofcourse.

now reboot. and hopefully it should work.

---

