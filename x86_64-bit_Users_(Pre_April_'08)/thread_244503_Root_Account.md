---
title: "Root Account"
date: 2006-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by geoffxy on 2006-08-26
Hi I installed Ubuntu Dapper Drake for AMD 64 and i was wondering what would the password be for the root account? I need to add new users to the computer does anyone know how? I us the su command in the terminal then it asks for the password what would the password be?

---

### Post by aimislame15 on 2006-08-26
> **geoffxy said:**
> Hi I installed Ubuntu Dapper Drake for AMD 64 and i was wondering what would the password be for the root account? I need to add new users to the computer does anyone know how? I us the su command in the terminal then it asks for the password what would the password be?

It's highly suggested that you don't change the password, rather use:

```
 sudo su 
```

to gain root access when you need it.

---

### Post by Kilz on 2006-08-26
use sudo insted of su. Also gksudo for graphical applications will give them root access. So ```
gksudo nautilus
``` will open up nautilus as root. I even added a shortcut to the adminastration menu with the alacarte menu editor for it. A gui makes it easier to move around files as root sometimes.

---

### Post by geoffxy on 2006-08-26
> **aimislame15 said:**
> It's highly suggested that you don't change the password, rather use:

```
 sudo su 
```

to gain root access when you need it.

gahh no one understands I DONT KNOW WHAT THE PASSWORD TO THE ROOT ACCOUNT IS I NEVER WAS ASKED TO SET IT so i was wondering if anyone knew what the defaut password to the root account was if you didnt set it yet...

---

### Post by Kilz on 2006-08-26
> **geoffxy said:**
> gahh no one understands I DONT KNOW WHAT THE PASSWORD TO THE ROOT ACCOUNT IS I NEVER WAS ASKED TO SET IT so i was wondering if anyone knew what the defaut password to the root account was if you didnt set it yet...

there is no root password, sudo is set to use the password of the first account created during install so it would be sudo yourpassword. No need to shout.

---

### Post by tzulberti on 2006-08-27
> **geoffxy said:**
> Hi I installed Ubuntu Dapper Drake for AMD 64 and i was wondering what would the password be for the root account? 

This is already answered by Kilz on the latest post. If oyu want to have a password for the root, just write "sudo passwd"

> **geoffxy said:**
>  I need to add new users to the computer does anyone know how? 

There are two commands: useradd and adduser. The difference is that one creates de home folder and the basic configuration files and the other on only creats the user (no files for it). Since i am not at my computer i can not tell you which is which

> **geoffxy said:**
> I us the su command in the terminal then it asks for the password what would the password be?
To became root using a normal user you could use "su".

---

### Post by juicemansam on 2006-08-29
My 2 cents, just to clear things up a bit more (or confuse). In a standard {x,edu,k}ubuntu installation, the root account is disabled by default. As Kilz mentioned, the first account created is set up to use *sudo* (and *gksudo*) for anything that would require superuser access. *gksu*, *gksuexec*, and *su* are other programs that you can use to gain superuser access, but note that these programs, unlike *sudo* that uses the current user's password (if the user is allowed via /etc/sudoers), use the target user's password (usually root). So if the target user has no password, *su* (or the like) will not work unless you're already root, such as either really being root or with sudo.

---

### Post by ShadowRage on 2006-08-29
all you need to know is your password and sudo.

by default you should be in the /etc/sudoers file.

for a root shell:
```
sudo -s
``` (otherwise sudo *command* will run said command as root)

also, you said you want to add new users?

system -> administration -> users and groups

and put in your password when it asks.

that should clear things up.

have fun.

---

