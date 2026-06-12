---
title: "Open office problem is this 64 bit problem?"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by darkworld on 2008-06-22
Hardy Heron fresh install, Open office word processor loads than vanishes???

Ive just installed Hardy after running feisty for a long period. Totally fresh installation, not an upgrade. 

I dont know if this is a 64bit issue and I dont know where to look to find out whats happening. Open office run in Feisty fine.

---

### Post by Throne777 on 2008-06-22
> **darkworld said:**
> Hardy Heron fresh install, Open office word processor loads than vanishes???

Ive just installed Hardy after running feisty for a long period. Totally fresh installation, not an upgrade. 

I dont know if this is a 64bit issue and I dont know where to look to find out whats happening. Open office run in Feisty fine.

I get the same. It was mentioned in another thread, but you can get round the problem by running the following in a terminal:
```

sudo openoffice
```
Seems it's a high priority bug so I'm hoping a fix will be out soon.

---

### Post by Krydahl on 2008-06-22
It's not 64 bit. I'm running a fresh install of 64 bit Hardy and Writer works fine for me.

---

### Post by gaijinak on 2008-06-22
Try running from a terminal and see if it prints any error messages

Select from your menu bar Applications|Accessories|Terminal and then the following command at the prompt:

```
oowriter
```

R.

---

### Post by philinux on 2008-06-22
Hi,

Read post 6 especially.

[http://ubuntuforums.org/showthread.php?t=832849&highlight=openoffice](http://ubuntuforums.org/showthread.php?t=832849&highlight=openoffice)

I just remembered seeing this the other day.
My system is working fine so not sure why the bug exists for some.

---

### Post by sawjew on 2008-06-22
I don't know if this is the same problem or not.  For me the OpenOffice quickstarter will not load and when I click on an OpenOffice document the splash shows, the progress bar moves across and then it vanishes and nothing opens.  I have found that if I open Writer from the menu first and then click on a file it works.

I have found out that this is an issue with OpenOffice 2.4.1 which I have installed from the proposed repositories.  One of the small trials I have to face if I wish to keep bleeding edge packages on my system.

If you have the proposed repos active this may be the issue and you can fix it by forcing back to the hardy version.

---

### Post by Grone1985 on 2008-06-23
> **sawjew said:**
> I don't know if this is the same problem or not.  For me the OpenOffice quickstarter will not load and when I click on an OpenOffice document the splash shows, the progress bar moves across and then it vanishes and nothing opens.  I have found that if I open Writer from the menu first and then click on a file it works.

I have found out that this is an issue with OpenOffice 2.4.1 which I have installed from the proposed repositories.  One of the small trials I have to face if I wish to keep bleeding edge packages on my system.

If you have the proposed repos active this may be the issue and you can fix it by forcing back to the hardy version.

I have the same problem and I don't have the proposed repos active, also I tried the suggestion on other threads about java and gtk and none of them work... Also I do have OpenOffice 2.4.1

---

### Post by paulderol on 2008-06-23
there was a recent update to OOO that broke it. try running it from the terminal and if you have a java issue, you should re-install the entire OOO meta-package. If, when you run 
```
ooffice
```

in a terminal, you encounter messages about a "locking assertion failure", you are experiencing[ bug 185311 ]("https://bugs.launchpad.net/ubuntu/+source/libxcb/+bug/185311") and a fix is in the works i am to understand.

---

