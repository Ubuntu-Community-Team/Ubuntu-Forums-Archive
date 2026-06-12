---
title: "How do I use Wine"
date: 2008-01-17
forum: Wine
---

### Post by techgeek40 on 2008-01-17
I am using Wine and want to install some software for my company to test to see if it will work on Linux

How do I use "install" the software?
Do I have to copy the contents of the CD to a folder on the computer?

---

### Post by ajgreeny on 2008-01-17
> **techgeek40 said:**
> I am using Wine and want to install some software for my company to test to see if it will work on Linux

How do I use "install" the software?
Do I have to copy the contents of the CD to a folder on the computer?
That will depend on the program you want to install and how the various installation files are indexed on the CD, but try without first.
Using the terminal navigate to the folder containing the setup.exe file on the CD (eg cd /media/cdrom0/path/to/exe/file) and then enter ```
wine setup.exe
```It may work and it may not but try that, and then try copying all the files from the CD to your hard drive and try again if it doesn't.
A lot of windows programs will not work at all, so don't be surprised if it will not do anything.

---

