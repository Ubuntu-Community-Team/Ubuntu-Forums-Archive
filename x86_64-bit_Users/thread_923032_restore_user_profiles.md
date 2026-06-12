---
title: "restore user profiles"
date: 2008-09-17
forum: x86 64-bit Users
---

### Post by rvg1296 on 2008-09-17
I have been running ubuntu for the last 4 months smoothly. When I tried to boot on the 16th this month I found my session lasted only for a few seconds resulting in loss of all user  profiles from /etc/gdm/xsession. I could boot, log into the system but no session. Please anybody help in restoring the user profiles.

---

### Post by Thelasko on 2008-09-18
Are all of their files still in /home?

---

### Post by giuvic on 2008-10-10
In my case, yes.
I did choose to put /home in a separate partition once I would like to restore the users once the computer was formated again.

So... how to restore the users profiles?? The manager does not allow you to add each user one by one as the directory already exists.

---

### Post by giuvic on 2008-10-10
Oh... my!

no idea?? :confused:

---

### Post by giuvic on 2008-10-10
Well... looking into similar posts, I think I was able to discover how and I made the following:

1. I looked into the home folder and clicked in each user folder with the right mouse button. I looked for properties and then for permissions in the way of discovering the uid.

2. I opened the terminal (Applications, Accessories, Terminal).

3. I pressed a command like this:

```
sudo adduser dayane --uid 1010
```

where dayane is the user and 1010 is the uid found at Permissions.


:guitar: I hope this helps others as well. But, hmm... is not a easier way?

---

### Post by Thelasko on 2008-10-10
I'm glad you were able to find a solution to your problem.  Thanks for posting your solution.

---

### Post by alfh on 2009-07-08
Your solution works like a charm - thank you!

But why doesn't the GUI do the same thing? It even suggested the existant UID, but still gave the message the directory is already in use and I have to choose new path.

But ok, terminal is fine with me!

---

