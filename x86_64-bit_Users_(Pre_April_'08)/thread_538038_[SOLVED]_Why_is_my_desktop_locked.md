---
title: "[SOLVED] Why is my desktop locked?"
date: 2007-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pde on 2007-08-29
I am unable to modify my desktop.  I have one file that I downloaded and it won't let me delete it, rename it, or move it.  In the Places window, the desktop icon has a padlock symbol in the corner.  I am not running Beryl.

---

### Post by aysiu on 2007-08-29
Let's say your username is *pde*

Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R pde:pde /home/pde
``` That should fix it.

---

### Post by very_japi on 2007-08-29
and if you still can't acces your desktop:

```
sudo chmod u+rwx  /home/(username)/Desktop -R
``` 

hope it helps

---

### Post by Pde on 2007-08-29
The first suggestion worked perfectly.  Would you mind explaining what that just did, and/or why this happened in the first place?

---

### Post by John.Michael.Kane on 2007-08-29
> **Pde said:**
> The first suggestion worked perfectly.  Would you mind explaining what that just did, and/or why this happened in the first place?

sudo gives root.

chown changes the owner of a file

-R  Changes the permission on files that are in the subdirectories of the directory that you are currently in.

As for why it happened the answer 'might' lay in the program you installed, and how you had to install it.

---

### Post by Pde on 2007-08-29
Right, I knew I had to "sudo" something, but I had no idea what.  I didn't actually install a program, I downloaded a file supposed to install Flash Player that I got from this forum, and when I tried to run it, it couldn't run because I didn't have permission.

---

### Post by Kilz on 2007-08-29
> **Pde said:**
> Right, I knew I had to "sudo" something, but I had no idea what.  I didn't actually install a program, I downloaded a file supposed to install Flash Player that I got from this forum, and when I tried to run it, it couldn't run because I didn't have permission.

If your refering to my script, I cant see how on earth someone could lock thier desktop with it, though a few have. 


SD, could you take a look at the script and see if you can figure out how this happens?

---

### Post by John.Michael.Kane on 2007-08-29
> **Kilz said:**
> If your refering to my script, I cant see how on earth someone could lock thier desktop with it, though a few have. 


SD, could you take a look at the script and see if you can figure out how this happens?

Well I downloaded the script labeled ff32-3in1-5.tar.gz, and extracted it double click on the file labeled 3in1, and dialog box appeared I selected run in terminal, at which time I enter my  pass, and proceeded to answer the questions.

I'm now running three browsers setup three different ways. 

1) Standard firefox 64 with flash using the nspluginwrapper script

2) Firefox 32bit with flash installed via the manual method outline in the below howto.
Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64

3) IceWeasel with flash installed via (Browser Install Script) from the guide above.

That being said I have been unable to duplicate this issue.

In the end I can say that each method has, and does work for me, however.This is not to say there can't be problems,however. it would be highly unlikely.

Also for what it is worth I can say Kilz has comment the script very well in that anyone can see what each command does, and search what each command means.

---

### Post by Pde on 2007-08-29
It was nspluginwrapper-install-0-1.6.tar.gz, if that helps you any.  I'm about to try the latest one you posted.

---

### Post by John.Michael.Kane on 2007-08-29
> **Pde said:**
> It was nspluginwrapper-install-0-1.6.tar.gz, if that helps you any.  I'm about to try the latest one you posted.

At very least keep track of what you type, and any errors your given while under the terminal using the scripts or any guide for that matter, As this will help with bug finding or  helping you get the issue reversed.

---

### Post by pelicanghost on 2007-09-01
THANK YOU  I spent hours looking for the solution.

---

### Post by Kilz on 2007-09-01
> **pelicanghost said:**
> THANK YOU  I spent hours looking for the solution.

Exactly what did you do to lock your desktop?

---

