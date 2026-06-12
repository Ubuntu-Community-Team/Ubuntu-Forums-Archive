---
title: "Help! I'm trying to install..."
date: 2008-01-02
forum: Wine
---

### Post by wiredheat on 2008-01-02
World of Warcraft using wine. I've copied all of the files to a new directory, and this is the tutorial I'm using:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I'm at the part where I'm supposed to do this:

 Start the installation by opening a terminal and running these commands:

 cd /<path-to-directory>/
 wine Installer.exe

This is where the location of the folder I copied the files to is:

/home/user/Desktop/WoW Install


This is what I've entered into the terminal so far, but it doesn't work:

:~$  cd /</home/user/Desktop/WoW Install>/
bash: /home/user/Desktop/WoW: No such file or directory
:~$  cd /<home/user/Desktop/WoW Install>/
bash: home/user/Desktop/WoW: No such file or directory
:~$  cd /home/user/Desktop/WoW Install/
bash: cd: /home/user/Desktop/WoW: No such file or directory
:~$  cd /home/user/Desktop/WoW Install
bash: cd: /home/user/Desktop/WoW: No such file or directory
:~$ 


What am I supposed to be typing? Help please! I'm fairly new to linux.

---

### Post by BreathEasy on 2008-01-02
The problem is that the folder you've chosen to use has a space in its name.

I recommend renaming **WoW Install** to something like **WoW-Install**. It can be anything, just avoid using spaces. You CAN use spaces quite easily in Linux, but you're new so there's no need to make things more complicated just yet. :)

---

### Post by Cappy on 2008-01-02
You can use:
cd "~/Desktop/WoW Install"
cd "/home/$USER/Desktop/WoW Install"
cd ~/Desktop/WoW\ Install
cd /home/$USER/Desktop/WoW\ Install

or you can rename it as in BreathEasy's suggestion

The < > are only there to be replaced with the actual path; Take them out

=)

---

