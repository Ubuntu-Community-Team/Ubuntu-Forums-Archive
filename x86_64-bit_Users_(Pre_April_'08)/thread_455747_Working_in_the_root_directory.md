---
title: "Working in the /root directory"
date: 2007-05-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by diddler on 2007-05-26
The answer to this question may solve a bunch of future problems for me so here is the situation:

I downloaded the 64-bit  Linux driver file from NVidia (I am not having any video problems yet, but I am anticipating doing some gaming in the future, besides, I thought it would be good practice).  The instructions from NVidia tell you to use the sh command (the file is saved to the desktop).  When I run the sh in my desktop directory I get an error message telling me that the file MUST be run in the /root.

I cannot copy the file to the /root. It says I don't have permission, and in another place it says I'm not the owner.  G*****it, its MY computer.  Why the hell can't I do what I want?

Like I said, very basic Linux question.

---

### Post by yabbadabbadont on 2007-05-26
What it is probably telling you is that you need to run it as root.  Try using sudo to run the command.  If that doesn't work, then run "sudo -i" to drop yourself into a root shell.  Then you should be able to run the command.

---

### Post by diddler on 2007-05-28
> **yabbadabbadont said:**
> What it is probably telling you is that you need to run it as root.  Try using sudo to run the command.  If that doesn't work, then run "sudo -i" to drop yourself into a root shell.  Then you should be able to run the command.

I did and it worked but when I ran the install program it gave me the message that it could not proceed because 
"you appear to be running an X server.  Please exit X and reinstall"

How do I do THAT?

---

### Post by milton1 on 2007-05-28
ctrl+alt+f1

Login, repeat the process. You will very likely need to edit xorg.conf in order to get x working again later. I suggest you read the install instructions very carefully, and perhaps research linux permissions and terminals a bit more before attemting this.

---

### Post by yabbadabbadont on 2007-05-28
> **milton1 said:**
> ctrl+alt+f1

Login, repeat the process. You will very likely need to edit xorg.conf in order to get x working again later. I suggest you read the install instructions very carefully, and perhaps research linux permissions and terminals a bit more before attemting this.

Actually, the xserver will still be running after you do the above.  Once you have logged in at the console, run (without the quotes) "sudo /etc/init.d/gdm stop"  That will shut down the xserver.  Then run the installation and finally reboot.  "sudo reboot" will do it for you.

---

### Post by diddler on 2007-05-28
Thanks all.

I took the coward's way out and loaded the restricted video drivers.  If I still have video problems, I will come back to this and install this file.  I appreciate the help.

---

