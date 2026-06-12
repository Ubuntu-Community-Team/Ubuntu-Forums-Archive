---
title: "Wine and virus"
date: 2008-10-04
forum: Wine
---

### Post by planet-reptile on 2008-10-04
Hi. 

I have some programs i would like to take with me to Ubuntu.
My big question is, Is there any chance that virus will have any effect in Ubuntu when i install wine and use windows programs?
Can some one see what I'm doing or what i transfer or whatever?
What about homebanking? I often check my account. Will it be safe to do that?

---

### Post by askyourpc.com on 2008-10-04
See this post:

[http://ubuntuforums.org/showthread.php?t=936660&highlight=WINE+emulate+virus](http://ubuntuforums.org/showthread.php?t=936660&highlight=WINE+emulate+virus)

Ubuntu is far.... more secure than windows and I think it is even more secure that Apple. Check out that link for the details.

Not only that, but Ubuntu is constantly being updated. It has a different file system structure that many viruses will use on windows. Much of malware is event triggered. That is, it will use windows startup to execute and Wine doesn't have a windows startup.

---

### Post by asdfoo on 2008-10-05
> **askyourpc.com said:**
> See this post:

[http://ubuntuforums.org/showthread.php?t=936660&highlight=WINE+emulate+virus](http://ubuntuforums.org/showthread.php?t=936660&highlight=WINE+emulate+virus)

Ubuntu is far.... more secure than windows and I think it is even more secure that Apple. Check out that link for the details.

Not only that, but Ubuntu is constantly being updated. It has a different file system structure that many viruses will use on windows. Much of malware is event triggered. That is, it will use windows startup to execute and Wine doesn't have a windows startup.

Please, stop spreading FUD.  Ubuntu and Windows and Apple are all equally insecure.  Wine does have a windows startup.

If you run a virus in Wine, immediately it can access any files you have in your home directory. That includes modifying them, deleting them, sending them across the internet or granting someone else access to your machine.

Yes, if you kill the process then it will nolonger be running, but by then it might already be too late, since it takes very little time to do the above.

Furthermore, if you refer to my previous post you'll see that it's entirely possible for a virus writer to add a check for Wine and attempt to exploit known bugs in Linux to gain full access to your machine and install a rootkit so that it may go undetected.

---

### Post by cpetercarter on 2008-10-05
Has anyone actually managed to get a Windows virus to "work" in Wine?

---

### Post by hikaricore on 2008-10-05
> **asdfoo said:**
> Please, stop spreading FUD.  Ubuntu and Windows and Apple are all equally insecure.  Wine does have a windows startup.

If you run a virus in Wine, immediately it can access any files you have in your home directory. That includes modifying them, deleting them, sending them across the internet or granting someone else access to your machine.

Yes, if you kill the process then it will nolonger be running, but by then it might already be too late, since it takes very little time to do the above.

Furthermore, if you refer to my previous post you'll see that it's entirely possible for a virus writer to add a check for Wine and attempt to exploit known bugs in Linux to gain full access to your machine and install a rootkit so that it may go undetected.

Stop posting the same crap in multiple threads.

p.s. you're paranoid and YOU need to stop spreading the FUD yourself

---

### Post by Sub101 on 2008-10-05
> **cpetercarter said:**
> Has anyone actually managed to get a Windows virus to "work" in Wine?

Yes, somewhere there is a discussion about it. I will add it here in a moment.

EDIT: I can't find the page right now however there is an item which runs through various viruses and there effectiveness within wine.

---

### Post by david_kt on 2008-10-05
> **asdfoo said:**
> Please, stop spreading FUD.  Ubuntu and Windows and Apple are all equally insecure.  Wine does have a windows startup.

If you are worry about virus, just install klamav which include support for:
 - On Access Scanning.
 - Manual Scanning.
 - Context-Menu Scanning
 - Quarantine Management.
 - Downloading virus definition updates
 - Mail Scanning (KMail and Ximian Evolution)
 - dazuko-2.0.5 pre-packaged
 - Virus Browser
 - Scan Scheduler

It could detect and quarantine windows virus as well.

DK

---

### Post by askyourpc.com on 2008-10-05
> **asdfoo said:**
> Please, stop spreading FUD.  Ubuntu and Windows and Apple are all equally insecure.  Wine does have a windows startup.

If you run a virus in Wine, immediately it can access any files you have in your home directory. That includes modifying them, deleting them, sending them across the internet or granting someone else access to your machine.

Yes, if you kill the process then it will nolonger be running, but by then it might already be too late, since it takes very little time to do the above.

Furthermore, if you refer to my previous post you'll see that it's entirely possible for a virus writer to add a check for Wine and attempt to exploit known bugs in Linux to gain full access to your machine and install a rootkit so that it may go undetected.

I don't see how I was spreading FUD. I was just trying to answer the question and reasure that there was less of a likelihood of getting a virus than in windows. Especially if you don't run wine... I may have been wrong about the startup but still there is less potential for a virus being ran in wine and having success in linux...

---

### Post by DaVince21 on 2008-10-06
I don't doubt it, since Wine can access a bunch of important user directories, but with Linux's secure rights-based system you shouldn't have to worry about it affecting anything important outside /home/user. Since it doesn't have the rights to access all that.

---

### Post by YokoZar on 2008-10-06
> **DaVince21 said:**
> I don't doubt it, since Wine can access a bunch of important user directories, but with Linux's secure rights-based system you shouldn't have to worry about it affecting anything important outside /home/user. Since it doesn't have the rights to access all that.

Your home folder is where all the interesting stuff is anyway.



Regardless, if you're worried about Windows viruses, Wine provides far fewer avenues of attack than Windows itself.  The reason is that you're running much fewer Windows programs with Wine - just the few you click on.  As an added bonus, even *if* you click on an infected windows executable (which would surely infect you in Windows), on Wine there's still a chance it won't bother you since Windows viruses often either don't work in Wine or don't know enough to infect anything other than the ~/.wine folder.

---

### Post by haydnc on 2008-10-06
The other option to consider is that you can always download a virus scanner - either clamav as earlier suggested or something like the linux version of avast ([www.avast.com](www.avast.com)).

I know that avast scans for viruses as well on Linux as it does on any Windows based OS because I've tested it with some known-to-be-infected windows files. Basically - scan anything you're unsure of before you run it in Wine.

---

