---
title: "[SOLVED] Possible Virus? Var folder"
date: 2007-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mr_bleu on 2007-07-03
I was doing some checking tonight and found my hard drive was mostly used up.  In my /var folder I found some archived files djr-laptop-home.20070703.master.tar.gz (this one's 9.8 gb) that seem unusually large.  Earlier I typed "top" in a terminal and found gzip using 75% of my cpu while system monitor didn't even list it as running/sleeping/zombie.

---

### Post by scrooge_74 on 2007-07-03
that is a zip file 

if your disk is getting full you can delete the logs in /var/log

and 

delete downloaded packages

sudo apt-get autoremove

just for a start

---

### Post by Mr_bleu on 2007-07-03
I know it's a zip file, WHY is it doing that? It's in the Archives folder.

---

### Post by sawjew on 2007-07-04
It sounds like you have a backup program like sbackup or backup-manager backing up all your files to the /var directory.

Have you installed Sbackup?  By default Sbackup copies all your backup files to /var.  The format of the archive name is definitely a backup file because it is incorporating the backup date, your computer's name and your home directory in the file name.  I can't check on it now because I am at work on my break and using Windows.  If you can't work it out post back here and I (or someone else) will see what I can do later.

---

### Post by Mr_bleu on 2007-07-04
I have home user backup installed, but didn't think it would back up my files without a command being issued.

---

### Post by sawjew on 2007-07-04
I don't know much about home user backup but you may find that it is set to backup automatically at scheduled intervals.  I think you should go through it and check all the settings and see if an automated backup is set to run.

I am fairly confident that this is the problem, also check where it is backing up to.  There is not a lot of point in backing up to /var if it is on the same hard drive as your backup source.  You are better of backing up to an external hard drive or a DVD or some other form of removable media.

---

### Post by Mr_bleu on 2007-07-04
I tried getting into the settings, didn't find them.  I uninstalled via synaptic.  I will install when I'm ready to back up my hard drive.  Thanks for the help everyone.  I really like ubuntu.

---

