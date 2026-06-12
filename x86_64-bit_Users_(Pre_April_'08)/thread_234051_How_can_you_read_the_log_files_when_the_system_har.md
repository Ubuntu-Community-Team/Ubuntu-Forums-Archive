---
title: "How can you read the log files when the system hard locks"
date: 2006-08-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by codejunkie on 2006-08-10
Im having trouble getting the latest 64bit dapper Desktop/Live cd 6.06.1 to install, the installer keeps freaking out and hard locking the system, so is there a command or script out there that i can use to export the output of dmesg and the installer log to a file every so many seconds so i can see what freaked out and file a bug report.

---

### Post by RAOF on 2006-08-10
Um, where would this file go if you're using a LiveCD?

Anyway, running the installer (I believe it's called **ubiquity**) from a terminal with
```
ubiquity &> /path/to/outputfile.txt
```will redirect all terminal output to the file.

As for dmesg... I'm unsure.

---

### Post by codejunkie on 2006-08-11
> **RAOF said:**
> Um, where would this file go if you're using a LiveCD?

Anyway, running the installer (I believe it's called **ubiquity**) from a terminal with
```
ubiquity &> /path/to/outputfile.txt
```will redirect all terminal output to the file.

As for dmesg... I'm unsure.
the livecd works fine until i click install so i was going to mount my spare  fat32 drive and have it output installer log to it, so when it crashes i can restart and mount that drive have a look at the log file,

RAOF will this update the file every so many seconds, or will this just  output the current contents of the installer log when the command is entered?

---

### Post by RAOF on 2006-08-11
It will make anything the installer was going to write to the terminal (debug messages, warnings, etc) go to the file instead.  It's **not** going to look at the installer's log, wherever that is, but I assume that the installer would also write such messages out to the terminal.

---

