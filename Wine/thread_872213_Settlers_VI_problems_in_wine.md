---
title: "Settlers VI problems in wine"
date: 2008-07-27
forum: Wine
---

### Post by qbox on 2008-07-27
hi
I install Settlers VI on wine and I make update. When I try to start the game one window give me tnis

```
Insufficient privileges: you must be administrator when you run this application for the first time.
```

How to be an administrator :)))
Thanks

---

### Post by qbox on 2008-07-29
40 Reads and no one to say a word? 
:lolflag:
:popcorn:
p.s. I give a free beer :)

---

### Post by willix on 2008-07-29
Try using sudo
For instance changing a file's owner

> chown dummy:dummy filename
Insufficient privileges

> sudo chown dummy:dummy filename
:)

or to have a permanent root shell
> sudo su

---

### Post by qbox on 2008-07-29
So probably I dont need linux administrator rights. I need w\ administrators rights for that application.How to configure thats rights in wine?

---

### Post by qbox on 2008-07-29
I try with wine and I see that the game is supported. The tester say that everything work PEFECT.
BUT!!
When I start the game the game ask for me to be a Administrator. I googled alot but no one dont know how to fix problem with programs who ask for administrator tights. in my case I need w\ administrator right, no linux.

I start the game with wine and one message tel me this
nsufficient privileges: you must be administrator when you run this application for the first time.

i cant understand how tester start the game under wine without admin rights I send him a mail but no one reply to me
I report to wine bugs and no one dont have a clue how to fix the problem with programs who ask for a admin rights.

I think about making crack by bypassing the check for admins.
Any sugestions how to do this? Or what tools to use ?
)))

---

### Post by willix on 2008-07-30
I dunno but you could try 
> sudo wine path/To/SettlersVI/Exe

if you run wine as root, maybe it defaults to administrator 

just a wild guess.....

---

### Post by drenzu on 2008-11-14
[SIZE="4"]Don't run wine as root[/SIZE]

It will screw up your wine by messing with permissions on files.

I think the error you are getting is because of the game's copy protection. It wants to install some drivers or something nasty. Get a cracked exe for the game from gamecopyworld or similar, try it then.

---

### Post by Dawey on 2008-11-14
> **willix said:**
> I dunno but you could try 
> sudo wine path/To/SettlersVI/Exe

if you run wine as root, maybe it defaults to administrator 

just a wild guess.....

Don't give advice on the things you are uncertain about! From [http://wiki.winehq.org/FAQ:](http://wiki.winehq.org/FAQ:) 

[I]**"7.9. Should I run Wine as root?**

NEVER run Wine as root! Doing so gives Windows programs (and viruses) full access to your computer and every piece of media attached to it. Running with sudo also has these same risks but with the added bonus of breaking the permission on the users ~/.wine folder in the process. If you have run Wine with sudo you need to sudo rm -rf ~/.wine and then run winecfg to set wine back up. You should run Wine as the normal user you use to login.

For Linux Systems all ideas that wine needs root can be solved through Posix Capabilities [http://www.linuxjournal.com/article/5737](http://www.linuxjournal.com/article/5737) or Posix File Capabilities [http://www.ibm.com/developerworks/library/l-posixcap.html](http://www.ibm.com/developerworks/library/l-posixcap.html) or correcting other security settings.

**7.10. So, I ran wine with sudo or as root, how do I fix my permission errors?**

You need to delete your ~/.wine directory, this is where all wine state, configuration and any important data you might have such as installed programs, saved data within wine programs etc. Once you delete or move this directory, rerun wine as a regular user always! Run the following to delete your ~/.wine directory if it now has root permissions.

sudo rm -rvf ~/.wine"[/I]

---

