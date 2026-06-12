---
title: "Why am I not the Super User??"
date: 2009-06-06
forum: x86 64-bit Users
---

### Post by gapkid22 on 2009-06-06
OK, im new to ubuntu....like Ive had it for about 5 days now. Im tryin to learn linux for somethin ta do and I live by the philosophy that the more you know the better off you are. Anyway....I installed the 64 bit ubuntu, I log in and have a password to log in. For some reason, im not the super user. When i try to move files, it says my permission is denied and when i try to "su - root" and it asks for my password, the pass is wrong. Is there anyway to make mysef the super user or do I need to reinstall? Thanks all in advance!

---

### Post by SuperSonic4 on 2009-06-06
root is disabled by default in ubuntu. You *can* enable the root account (you'll have to google that for it's against forum policy to tell you)

Ubuntu uses *sudo* as it's method. If you preface your command with sudo and type in your **user** password (note it won't show an input but it is being inputted) and you'll have root access for 15mins with sudo

---

### Post by Iowan on 2009-06-06
[Here]("https://help.ubuntu.com/community/RootSudo") is a help page with (even) more information.

---

### Post by aysiu on 2009-06-06
Just create a launcher or keyboard shortcut for the command ```
gksudo nautilus
``` and use it. "Problem" solved.

---

### Post by bford16 on 2009-06-06
> **SuperSonic4 said:**
> root is disabled by default in ubuntu. You *can* enable the root account (you'll have to google that for it's against forum policy to tell you)

Ubuntu uses *sudo* as it's method. If you preface your command with sudo and type in your **user** password (note it won't show an input but it is being inputted) and you'll have root access for 15mins with sudo
This command will open gedit (Text Editor) with regular user credentials.```
barry@hpdv8110us:~$ gedit
```
This command, plus your user password, will open gedit with superuser credentials.```
sudo gedit
```Be extra careful when using sudo, because you will be able to change or edit any part of the operating system.  In other words, you can destroy your system.  So make sure you know what you are doing.

---

### Post by sailthesea on 2009-06-06
Its best to use sudo for any quick operations

Working in the root directory is a very bad idea unless you are really sure of what you are doing

SUper User DO

---

### Post by gapkid22 on 2009-06-07
Thanks guys I really appreciate it. I got in an argument with one of my IT professors about this. I told her that the SUDO command is used to kind of "make" you the super user and she said that I should be able to get into root anyway. She uses Fedora core 8. I just wanted to make sure I didnt have to re-install. Again, thank you all.

---

### Post by decksmasher on 2009-06-07
> **gapkid22 said:**
> OK, im new to ubuntu....like Ive had it for about 5 days now. Im tryin to learn linux for somethin ta do and I live by the philosophy that the more you know the better off you are. Anyway....I installed the 64 bit ubuntu, I log in and have a password to log in. For some reason, im not the super user. When i try to move files, it says my permission is denied and when i try to "su - root" and it asks for my password, the pass is wrong. Is there anyway to make mysef the super user or do I need to reinstall? Thanks all in advance!

use the su or sudo -s command that will give you the root user=super user

---

### Post by gamblor01 on 2009-06-07
> **gapkid22 said:**
> Thanks guys I really appreciate it. I got in an argument with one of my IT professors about this. I told her that the SUDO command is used to kind of "make" you the super user and she said that I should be able to get into root anyway. She uses Fedora core 8. I just wanted to make sure I didnt have to re-install. Again, thank you all.
Well I go ahead and claim you as the winner!

If you're talking about Fedora 8 then that's true, you can login directly to the root account.  In Ubuntu however it is disabled by default.  You can enable it, though apparently it's against the rules of this forum to tell people how to do it (for some strange reason).  A simple google search will provide the answer of course.

But as others have already stated, Ubuntu's approach is to use sudo/gksudo for any commands that require root privileges.

---

### Post by aysiu on 2009-06-07
> **decksmasher said:**
> use the su or sudo -s command that will give you the root user=super user
Don't use *sudo -s*. That can accidentally change your user files to root permissions.

Instead, you should use ```
sudo -i
```

---

### Post by ddales on 2009-06-07
Wow, I was unaware that root tutorials are illegal.  I replied with the instructions on how one sets a root password and enabling logins as root.  I received a private message that my post was jailed.

Forum Rule:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Slim Odds on 2009-06-07
> **bford16 said:**
> This command, plus your user password, will open gedit with superuser credentials.```
sudo gedit
```

This is wrong. Don't use sudo for GUI based apps. Bad things can happen.

Use gksudo instead.

---

### Post by aysiu on 2009-06-07
> **Slim Odds said:**
> This is wrong. Don't use sudo for GUI based apps. Bad things can happen.

Use gksudo instead.
This is good advice.

In the case of gedit, I have never seen bad things happen, but it's better to get into the habit of doing the right thing instead of trying to keep a list of graphical apps you can use with *sudo* safely and another list you have to use *gksudo* with.

Just use *gksudo* with them all, and you should be fine.

---

