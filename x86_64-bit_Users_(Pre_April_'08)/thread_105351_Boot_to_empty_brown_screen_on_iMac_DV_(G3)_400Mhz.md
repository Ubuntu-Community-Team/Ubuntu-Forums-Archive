---
title: "Boot to empty brown screen on iMac DV (G3) 400Mhz"
date: 2005-12-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by OldMac on 2005-12-18
I've just installed Ubuntu 5.10 onto my old iMac DV (G3 400Mhz).

The installation went perfectly. On booting, the GUI login screen appears. I type in my set username and password. A plain brown/beige screen appears. Some groovy you-just-launched-your-desktop music is heard. I have a mouse pointer. It responds to the mouse.

This is as far as I get. The desktop remains blank, except for the functioning mouse pointer sprite.

I assume since I'm getting something coherent dislpayed, it's not a monitor resolution or sync setting problem, which I've noticed many other people have described.

Any suggestions would be greatly appreciated!!

Cheers...

---

### Post by OldMac on 2005-12-18
SORRY!  Abort abort abort! =)

Further sifting through older threads alerted me to the "date bug". I've altered the system date and the GUI startsup just fine now.

---

### Post by gconn77 on 2005-12-18
Excellent!!! Man, I wish my problems were as simple as yours! I believe that we have the same computer.... did you run into any trouble along the way with the second stage bootloader...?

---

### Post by OldMac on 2005-12-18
No, I had no trouble with the installation process itself.

I burned the appropriate CD on a Windows XP box, dumped it into my old red iMac DV G3 400, and held down "c" while it started up.

Booted from the CD with no problems. The ANSI-text installer did it's thing, I answered a few configuration questions, and it spent the next 30 mins making my CD-ROM drive sound like a DJ's turntable.

Finished the initial install, removed the CD, rebooted, waited for it to finish unpacking and installing the rest of the components, and then when it finished the login screen came up, worked fine and then I had my "beige screen with a pointer" problem until I discovered the previous thread discussing the system date bug.

Did you choose to partition your hard disk to retain your old MacOS?

I chose to nuke the entire disk, and just install linux/Ubuntu from scratch with the whole disk to play with.

At what point does your installation seem to fail, and what exactly happens?

---

### Post by gconn77 on 2005-12-19
Well.. I did the same.... erased entire disk and such... and still had problems... Finally I decided to REMOVE the SCSI hard drive and replace it with a regular IDE hard drive... after I did that, everything was cake!

Try doing that... if you have an old hard drive laying around, just swap them, remove the SCSI drive and install a IDE hard drive... 

I am not sure if this will work for your situation... but man, I been working on this off and on for over a week!!! and finally decided to put my own hard drive in and an hour later... done!

So... tomorrow I will head to the store and pick up an 80 gig hard drive... and then I will be finally in business.

View my profile to get the the threads that I created, read them, and let me know if you need any help.

---

### Post by OldMac on 2005-12-19
Ahhh, okay. No, I didn't have any hard disk issues.

My G3 iMac came fitted with a 10GB Quantum Fireball IDE drive to start with, so no SCSI issues involved.

Glad to hear you got yours working.

I'm typing this from the iMac running Ubuntu, but have had to resort to connecting to my wireless ADSL modem/router via Cat-5 cable as I never had an airport card in this machine.

Any hints as to out-of-the-box solutions for wireless LAN/net access from an Ubuntu iMac? Considering USB adaptor if there's no "old" airport card support.

---

