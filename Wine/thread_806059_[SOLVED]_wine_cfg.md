---
title: "[SOLVED] wine cfg"
date: 2008-05-24
forum: Wine
---

### Post by asqn34 on 2008-05-24
hello,
I am quiet new to linux and still trying to use some windows application as there is no alternative, without succees.

when typing winecfg in command line I have:
-err:process:init_windows_dirs directory L"c:\\windows could not be created, error5
-err:process:init_windows_dirs directory L"c:\\windows\\system32 could not be created, error3.

What does that mean and how to fix it?

Also when using wine after I lunched my application I cannot load any file as my winebrowser windows do not find any file.
Many thank for your help

---

### Post by cogadh on 2008-05-24
Did you ever use sudo to run wine or winecfg? If so, that is your problem, it has screwed up the permissions on your .wine directory. You'll need to delete it and recreate it without using sudo.

---

### Post by asqn34 on 2008-05-25
Hi Cogadh and thank you for your reply.
Yes I did use sudo to run winecfg but not to run wine itself.
Do I need to delete the .wine directory and recreate it, or delete wine completely from ubuntu and then re-instal it?
Thank you

---

### Post by cogadh on 2008-05-25
You don't need to uninstall Wine (in fact, uninstalling it wouldn't even fix this problem), just delete the .wine directory:
```
sudo rm -r ~/.wine
```
After you delete it, never use sudo to run any aspect of Wine again.

---

### Post by asqn34 on 2008-05-25
Hi Cogadh and thank you again for your time and response
I did uninstal wine from synaptic manager and delete my .wine file from my home directory as that one stayed after uninstal. I added wine depot to my synaptic manager and rerun winecfg. Found some problemes relatted to folder C, which I fix by runing this command in terminal: wineprefixcreate. (not in sudo)
It seem to work a as I have no more error message. Still need to try using wine to see if I can browse file that I need for a application. 
Thank you

---

### Post by asqn34 on 2008-05-25
Ok
Work Fine 
Thank You

---

### Post by asqn34 on 2008-05-25
Work Fine Now No Probleme.
Thank You

---

