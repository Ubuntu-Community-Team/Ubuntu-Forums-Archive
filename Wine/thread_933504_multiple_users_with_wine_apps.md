---
title: "multiple users with wine apps"
date: 2008-09-29
forum: Wine
---

### Post by wdypdx1 on 2008-09-29
Hi,

This has probably been dealt with, but I have not found an answer in my searching. I'm new (going on 3 weeks!) to ubuntu and wine, so please bear with me.

So here goes....

Soon after setting up a system with hardy 8.04 + updates, I installed wine 1.0 with synaptic. A couple of days ago I then installed (in my primary account) photoshop into wine and it works great.

Here's the thing. I set up a new user account for myself so that I'd have a separate account for work related usage. So, I go into that account expecting to be able to use photoshop, but it's not there. 

Is there a way to install apps in wine so that they are available to multiple users? Or do I need to install apps in specific user accounts? I've taken a look at wine's system.reg files; and notice that system.reg in my primary user account has photoshop settings; and system.reg in /root/.wine and in my secondary account do not. 

Any pointers to good links and tips are appreciated. 

Thanks, 
wdy

---

### Post by Ferrat on 2008-09-29
This is just guessing so I might be off but if you setup your .wine directory in a systemwide folder instead of $HOME which "locks" it to the other users that might work? 

you might have to add a env WINEPREFIX=" " ```
env WINEPREFIX="WhatEverFolderYouUse/.wine" wine "C:\Program Files\adobe\Photoshop.exe"
```
on all users for it to work properly but might work, as I said I'm just guessing here so if someone could confirm if this works or not would be great :D

---

### Post by wdypdx1 on 2008-09-29
Thanks.

I may just un-install PS from my primary account and re-install it into my 2nd account since that is where I'll use it most often. 

But over on Wine HQ in a section on System Administration Tips it says this, "With the above file structure (*talking about the registry in wine*), it is possible for a system administrator to configure the system so that a system Wine installation (and applications) can be shared by all the users,..." 

I'm assuming that I have a "system" Wine installation since I installed it from Synaptic and it's available to all users. But I don't know how to do a "system" installation of Wine apps; since it seems like the only way I can install an app is on a per user basis.

wdy

---

### Post by wdypdx1 on 2008-09-29
I know enough to be dangerous, but I'm wondering if I can do something like this.....

Create a .wine directory in say, /home and then symlink the users' .wine directories to that? I dunno about permissions though.

---

### Post by rsay on 2008-09-30
At some point in the past symlinking your personal .wine directory to a shared .wine directory worked and was pretty easy to set up. The only disadvantage was that everything that you installed in wine became available to all wine users. I'm not sure when the change happened, but recently wine began throwing an error with this approach. I have outlined an approach that will give you the best of both worlds, here: [Howto: Install Wine applications for Multiple Users]("http://ubuntuforums.org/showthread.php?t=917422"). 

You can install some things into your personal copy of wine and some things into a shared wine depending on your needs. 

I was trying to get the Rosetta stone language program installed under linux so my kids wouldn't have to reboot to windows to study their Spanish. The license doesn't allow you to install it five times and part of the application allows you to see each child's progress. I have three kids so I didn't want to log into each kid's desktop to check progress. Rosetta Stone runs great under wine btw.

---

### Post by wdypdx1 on 2008-09-30
I actually found a Howto for installing Wine Apps on Ubuntu with multiple users here:

Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > Tutorials & Tips
[Howto: Install Wine applications for Multiple Users]("http://ubuntuforums.org/showthread.php?p=5772221#poststop") 

I haven't tried it yet, but plan to in the next couple of days after I've read through it a bit more.

wdy

:popcorn:

P.S. - Oh and my question about the symlinks was before I found the howto by rsay.

---

