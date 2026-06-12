---
title: "Printmaster 10"
date: 2021-10-22
forum: Wine
---

### Post by sufehmi on 2021-10-22
Old Printshop / Printmaster software are among the best for their purposes - they're very straightforward, and provide you with a lot of ready to use  templates and cliparts. Made it very very easy to create all sorts of things in very little time. I've bought some of them and used them extensively. Very useful indeed.

Now they're still available via Archive.org

I'll try to document my efforts to get it to work here.

The latest thread about this can be seen here: [https://ubuntuforums.org/showthread.php?t=1353299&p=11020955#post11020955](https://ubuntuforums.org/showthread.php?t=1353299&p=11020955#post11020955)  - okos said that he keep getting errors on the install.

A peek into Autorun.inf shows the solution: 

instead of executing Setup.exe, it should be like this:

```
cd  Setup
wine is_Setup.exe Printmaster.ini
```

Then the install process will run smoothly.
Screenshot attached.

[ATTACH=CONFIG]289325[/ATTACH]

========

Current issue:

Can not get Pmw.exe to run. Wine (wine-staging 6.19) always crashed. 

Troubleshooting: 

Have tried changing winecfg to windows version 95 / 98 / XP / 10 to no avail.

Currently trying to install some DLLs that seems to be missing.
Will update this thread with the result.

---

