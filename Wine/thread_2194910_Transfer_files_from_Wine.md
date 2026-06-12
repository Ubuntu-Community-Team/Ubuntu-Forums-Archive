---
title: "Transfer files from Wine"
date: 2013-12-21
forum: Wine
---

### Post by ablutsauger on 2013-12-21
Hi,

First, to make it short - how to transfer files from Wine to Ubuntu/usb.... out of Wine?

I searched ans searched and I'm sorry, but couldn't find the answer.

I am complete Linux newbie. Of course, I'll learn everything during next period, but the problem is that I need some files urgently and have no time these few days to learn, so I just installed Wine to be able to finish everything quickly. And now I have no idea how to take the files out. Everything is Linux readable. Just some text etc. documents.

Thank you in advance,
Anna

---

### Post by TheFu on 2013-12-21
Well, if you have a stock WINE install, then all the files are located under ~/.wine/drive_c/ which is a clone of a Windows file system.  Should be relatively easy to find the files. After you find them, you can edit them right there, copy them elsewhere, do whatever you like.

If you are a GUI user, you might like the most-awesome-search-tool ever created - recoll. Install it from the repos, then have it index your HOME. Any file under it will be searchable by filename or contents - ok, almost any file.  Setup the re-index to run overnight or weekly.

If you are a CLI/shell user, you will love "locate."  It only understands filename, but that is often enough. Install it from the repos, then run **sudo updatedb** to index every file on the system (that isn't on portable devices).  Then use "locate {part of a filename} to find any files with matches. It is case-sensitive, just like Linux file systems. EXTREMELY fast.

Anyway - hope this helps.  Recoll completely rocks. It is like google for your local files, emails, music, videos, ....

---

### Post by ablutsauger on 2013-12-22
TheFu, thanks a lot. My first encounter with Linux was - oh, this is nuclear physics! The brain won't work!
I just found directly C drive by simply typing "drive". Stupid.:)

---

