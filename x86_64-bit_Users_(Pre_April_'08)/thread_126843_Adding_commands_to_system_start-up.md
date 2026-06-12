---
title: "Adding commands to system start-up"
date: 2006-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Andrew Shimmin on 2006-02-07
I've got the groovy Acer wlan problems that every newbie with one, does. But I've conquered them.  The thing works, now.  In order to start it, though, each time I load linux I have to open the terminal and enter three different commands.  Is there a way to make the system pre-load these? Or am I just being lazy? Thanks.

---

### Post by grinchy on 2006-02-07
put the commands into a script
save the script in $HOME/bin/startup_script
chmod +rx $HOME/bin/startup_script
goto system -> preferences -> sessions --> startup programs and stick the file in there with a high order ~ 200

---

