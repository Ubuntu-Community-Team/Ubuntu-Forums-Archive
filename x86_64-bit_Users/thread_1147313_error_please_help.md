---
title: "error please help"
date: 2009-05-03
forum: x86 64-bit Users
---

### Post by forddork on 2009-05-03
first off I've had ubuntu for about a week now. so I know nothing.

heres my problem

Checking for required C library versions ... OK
Checking for K Desktop Environment (Libraries) ... failed
-------------------------------
Error: Could not find 'K Desktop Environment (Libraries)'. Try using the native package manager for Ubuntu 8.10 (apt-get) to install a package with similar name to 'kdelibs'. 

Error: Unable to prepare package KMess.

how do I fix this?

---

### Post by pastalavista on 2009-05-03
What exactly are you trying to do?

---

### Post by forddork on 2009-05-03
trying to install kmess so I can use my msn messenger. Also in the terminal it asks for my password but the keystrokes dont seem to register and nothing appears in the prompt

---

### Post by pastalavista on 2009-05-03
The password in terminal doesn't show but it sees it when you type. You can install kmess with Synaptic (System > Administration > Synaptic Package Manager). Just type 'kmess' in the search field. Synaptic will make sure the package has all the files it needs to install. You can also type in terminal```
sudo apt-get install kmess
```When it asks for your password, just type it and hit enter. Sudo is the command to let Ubuntu know that you are using your root (administrator) privileges. You need to be administrator when you make any changes to the system.

---

### Post by forddork on 2009-05-03
thanks for the help! :P

---

