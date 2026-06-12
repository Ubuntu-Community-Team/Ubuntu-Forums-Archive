---
title: "No Root"
date: 2005-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by TestUser on 2005-11-23
Hi!

I have a problem with root access. I had a perfectly running system and made a update with synaptic and language (selector) was updated. I also made this:
[http://www.cups.org/articles.php?L237](http://www.cups.org/articles.php?L237)

Before rebooting I tried to run synaptic but it did not work. It asked for PW abut nothing happened. I rebooted and logged in and now I cannot run anything where I need root access.
What can have happened, any advice and help how I can solve this.
The volume control is disabled and I remember once when I had same error before I fixed it but now I have no luck at all.

I use breezy 64

Since I cannot get access and run terminal as root I cannot give log.

There should be a dpkg-configure to fix this, or??

TU

---

### Post by casper_2095 on 2005-11-24
"problem with root access...run terminal as root...need root access"

What happens who you try to use sudo?

Judging by the look of that link you might've managed to take yourself out of the "admin" group - which, by default, is necessary to be a sudoer.  Capice?

---

### Post by towsonu2003 on 2005-11-24
assuming you did not enable the root account somewhere in your configuration procedure: after doing ```
sudo cat /etc/sudoers
```**if** you don't see your username at the end, do ```
sudo -s -H
``` and give your own password... and copy past below line```
echo 'replacewithyourusername ALL=(ALL)  ALL' >> /etc/sudoers
``` than make sure you do ```
exit
``` which is very important...

looking at the number of your posts and assuming you're newbie in ubuntu, here's the usual advice: everytime you need root access, use sudo and put in your own password...

if you followed the main instructions there ([http://www.cups.org/articles.php?L237)](http://www.cups.org/articles.php?L237)) regarding cups, I dont believe you removed yourself from /etc/sudoers though... 

if you see your username in /etc/sudoers, then I'm not sure what the problem might be :(

what else did you change except groupadd and system upgrade? also, some logs should still be visible (ubuntu being user friendly...)

[edit] sorry, too many edits: correcting my grammar on the fly :) [/edit]

---

### Post by metoo on 2005-11-24
In case you cannot become root:

Boot into (recovery) mode (you have 2 seconds during boot to enter the grub menu, before the graphical boot progress starts).
Recovery mode should give you root rights as default.
Then try the things mentioned before.

Or re-install sudo (might require internet access):
apt-get install --reinstall sudo

---

### Post by TestUser on 2005-11-25
Hi

Thank you all for your help. 
I do not know what happened but I think that if I omit one user when I do a groupadd that user loose admin rights.
Anyhow I made as suggested in your posts and I got sudo to work, but still problems with other things so I reonstalled.

I think I must find a good backup tool :)
And yes both my name and number of posts reveal I am a beginner with ubuntu :)

/TU

---

