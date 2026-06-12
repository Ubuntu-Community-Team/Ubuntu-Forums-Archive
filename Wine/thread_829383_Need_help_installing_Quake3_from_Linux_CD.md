---
title: "Need help installing Quake3 from Linux CD"
date: 2008-06-14
forum: Wine
---

### Post by agentsmith23 on 2008-06-14
Quite a few years ago I bought Quake3 Linux edition accidentally. Now that I want to install it in linux it doesn't seem to be working. It has a readme with installation instructions but it doesn't seem to be working. 

Here are the instructions in the readme:

> Mount the Quake III Arena CD and change the current directory to where
it is mounted.  Type 'sh setup.sh' to run the install script.

e.g.  Log in as root:
	mount /mnt/cdrom
	cd /mnt/cdrom
	sh setup.sh

Make sure to have the CD key as printed on your jewel case lable ready
when you start the game. If you have not received a CD key, or have lost
it, please contact customer support for a replacement.

Caution: your CD key is stored in your ~/.q3a/baseq3/q3config.cfg file
as the value of the cl_cdkey variable. If you send your configuration
files to another person, be sure to take out the respective line

        seta  cl_cdkey  "<whatever>"

first. Please treat your retail config files as you would treat the PIN 
number on your bank card.

Here is what I got afteri ran the commands:

```
dnd@Ubuntu:/media/cdrom0$ sudo sh setup.sh
[sudo] password for dnd: 
setup.sh: 9: function: not found
x86

```


Is there some other way to complete the installation?
Thanks!!!

---

### Post by cogadh on 2008-06-14
Try running this instead:
```
sudo bash setup.sh
```
but I'm pretty certain you don't need to use sudo, unless you are installing it for all users on the machine.

BTW - Why was this posted in the Wine subforum?

---

### Post by agentsmith23 on 2008-06-14
> **cogadh said:**
> Try running this instead:
```
sudo bash setup.sh
```
but I'm pretty certain you don't need to use sudo, unless you are installing it for all users on the machine.

BTW - Why was this posted in the Wine subforum?

bash worked perfectly thank you. what is the difference between bash and sh?

The reason I posted it here is because when I right clicked on setup.sh and clicked on the open with tab it had wine selected.

---

### Post by cogadh on 2008-06-14
In Ubuntu, sh is linked to dash (Debian Almquist shell) while bash (Bourne-again shell) is the most common Linux standard for a system shell. Usually dash is not a problem (it is generally compatible with bash), but some scripts require the use of bash so you have to specify it when running them.

EDIT - I just checked my system and sh scripts are also associated with Wine for some reason. That's really odd and not correct at all. I wonder when that happened and what caused it...

---

