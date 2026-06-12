---
title: "Error Msg: Bookmarks can't be saved !"
date: 2008-10-01
forum: x86 64-bit Users
---

### Post by Masterizerx on 2008-10-01
Hi! Want to help someone? Just read:D

This error occured whitout any apparent reason.

On dolphin, each time I close a window it says "Impossible to save the bookmarks in /home/user/.kde/share/apps/d3lphin/bookmarks.xml"
Permission not granted (from french "Permission non accordée") sorry XD
This error message will be show only once. (Really?? No...)
This error should be corrected as soon as possible, this may be a full hard drive. (My HDD is not full)

Yes, d3lphin...why not dolphin?...WTF

I didn't do anything with the bookmarks so maybe it's a wrong click at the wrong place...

So what should I do ? I'm relatively new to KDE (Kubuntu).

Thanks !

---

### Post by cariboo on 2008-10-02
Have you checked the permissions on home/user/.kde/share/apps/d3lphin/bookmarks.xml to make sure it is writeable?

In a terminal type:

```
ls -la home/user/.kde/share/apps/d3lphin/bookmarks.xm
```

It should look something like this:

```
ls -la packages
-rw-r--r-- 1 jimk jimk 1001 2008-09-25 11:22 packages
```

I don't have KDE installed so I just used a file in my home directory.

Jim

---

### Post by Denestria on 2008-10-02
If you run dolphin as root it changes the owner of the bookmark file to root.  Have a look at the permissions like cariboo said and if it shows root as the owner/group then
```
sudo chown yourusername:yourusername ~/.kde/share/apps/d3lphin/bookmarks.xml
```

---

### Post by Masterizerx on 2008-10-02
Hmm... -rw-r--r-- 1 root root  ??

Trying: sudo chown me:me (path)
...
No more error message !!

Thanks a lot !

And now, each time I'll run Dolphin in root I'll need to enter this command ?
It's strange...

---

### Post by Denestria on 2008-10-02
Don't start dolphin with sudo use kdesudo and it shouldn't cause the problem anymore.

---

