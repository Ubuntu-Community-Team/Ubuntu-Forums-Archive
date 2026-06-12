---
title: "Want too install a app with admin previli."
date: 2008-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by SunEyed on 2008-01-23
I want to install game and i need the admin previligies. Where i insert my password or i have to swith to root user?

---

### Post by jd65pl on 2008-01-23
How are you trying to install the application?

---

### Post by Keith Hedger on 2008-01-23
sudo YOURCOMMAND

---

### Post by dannyboy79 on 2008-01-23
you can just use sudo before the command to install the app. if you're using synaptic, you would just enter the password you setup when you installed ubuntu (if you issue groups at t he command line, you should see admin as one of the groups that your username is in), that's the sudo password. if you want to switch to root privelages, you can issue
sudo -i
then enter that same user password to get you  a root prompt BUT just using sudo before any command is safer so that yo udon't forget your at a root prompt. right now, ubuntu doesn't have a password for the root user but you can create one by issuing

sudo passwd root
then enter your password (sudo password), then enter the password you want for root BUT again, that's not neccessary as you don't want to ever log in as root, just log in as yourself and either switch to root with sudo -i or just use sudo. good luck.

also, use gksudo for any graphical type apps, like if you want to write to folder owned by root, you could issue
gksudo nautilus
again, good luck

---

### Post by SunEyed on 2008-01-23
Thanks for all the replies/answers. Very helpful in a short time.

---

