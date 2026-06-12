---
title: "Login to root"
date: 2007-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by HuyPhungNhat on 2007-02-26
I am using Ubuntu Edgy 64bit. Can I login to root from login screen?

---

### Post by novice_forever on 2007-02-26
You generally can't login as root on ubuntu. If you need root priviledges for a certain command just type

sudo [command]

You will be asked for a password - this is the password of your first user. There is no root password.

---

### Post by Dr Eigen on 2007-02-26
> **novice_forever said:**
> You generally can't login as root on ubuntu. If you need root priviledges for a certain command just type

sudo [command]

You will be asked for a password - this is the password of your first user. There is no root password.



I think this is not stricktly true, though the exact situation is not clear to me.

You can set a password for the root account.  That password is then used for sudo.  But on playing with it a little on my machine, for su - I need my user password.  :-k

---

### Post by Mr LG on 2007-02-26
You can set the root password in users; SYSTEM ---> ADMIN ---> Users and Groups. Tick the box below that says show all users and groups. Then find the root user, hit properties at the bottom is should say password: Set (text area) Change your password here. click ok 

You have now set your su root password...

---

### Post by Kilz on 2007-02-26
> **Mr LG said:**
> You can set the root password in users; SYSTEM ---> ADMIN ---> Users and Groups. Tick the box below that says show all users and groups. Then find the root user, hit properties at the bottom is should say password: Set (text area) Change your password here. click ok 

You have now set your su root password...

Thank you for telling people how to become a security risk. The reason the root password isnt avilable is because there are dangers in using it. New users tend to log into it and never into a user account. It might have been safer to tell them to use ```
gksudo nautilus
``` if they need to move files around or move about the system as an administrator.

---

### Post by ante0 on 2007-02-27
> **Kilz said:**
> Thank you for telling people how to become a security risk. The reason the root password isnt avilable is because there are dangers in using it. New users tend to log into it and never into a user account. It might have been safer to tell them to use ```
gksudo nautilus
``` if they need to move files around or move about the system as an administrator.

Wow.. You know how long I've been looking for a command like that... :D
Well, when I mount my Windows NTFS hdd it gets mounted as read-only with user and group privilegies set to forbidden. Now I can finally get into it without using su in terminal :D

---

### Post by Dr Eigen on 2007-02-27
> **Kilz said:**
> Thank you for telling people how to become a security risk. The reason the root password isnt avilable is because there are dangers in using it. New users tend to log into it and never into a user account. It might have been safer to tell them to use ```
gksudo nautilus
``` if they need to move files around or move about the system as an administrator.

Setting a root password is a security risk?  Oh. My. God.  That's the sort of attitude that seems to be loved by administrators telling their sysadmins to install Windows.

Surely educating people about safe practices w.r.t. root access is a much better way to go than effectively patting them on the head and saying "don't worry, we'll look after it..."?

---

### Post by mg620 on 2007-03-05
I can't say I really understand how I am a security risk to my own computer, but I imagine there are scenarios that the more experienced users can easily point out.

In any case, the gksudo nautilus command is exactly what I was looking for while searching this thread (was having trouble installing MoneyDance because I didn't have write privileges to the default installation directory).  It's an extra step, but I guess it prevents unwanted stuff from being installed without my permission.  But thanks for the help.

---

### Post by konungursvia on 2007-03-05
> **mg620 said:**
> I can't say I really understand how I am a security risk to my own computer, but I imagine there are scenarios that the more experienced users can easily point out.


It's not that the user is a risk to his own computer, it's that while using, he launches dozens of apps with thousands of threads, many of which open ports to the net. To prevent windows-style virus infection, we just don't log in as anything other than Mr. Joe User in linux,  so that no application has *AUTOMATICALLy* got permission to install, modify or delete important parts of your system. When we actually intend to do so, we give a password for the Super User (su) that no outside program would be able to grant itself.

---

### Post by Kilz on 2007-03-06
> **Dr Eigen said:**
> Setting a root password is a security risk?  Oh. My. God.  That's the sort of attitude that seems to be loved by administrators telling their sysadmins to install Windows.

Surely educating people about safe practices w.r.t. root access is a much better way to go than effectively patting them on the head and saying "don't worry, we'll look after it..."?

Yes it is a security risk. Just one example. If someone is trying to hack into your system. They need a username and a password. You have just given them the most powerful username (root). Now all they need do is crack the password. They then have complete control over your system.

---

### Post by blackstealth007 on 2007-03-06
> **Dr Eigen said:**
> Setting a root password is a security risk?  Oh. My. God.  That's the sort of attitude that seems to be loved by administrators telling their sysadmins to install Windows.

Surely educating people about safe practices w.r.t. root access is a much better way to go than effectively patting them on the head and saying "don't worry, we'll look after it..."?

I could not have said it better. Well put.

---

### Post by offchance on 2007-03-11
when I use gksudo nautilus I get the following:

(nautilus:17241): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:17241): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.


I would like the freedom to use my ntfs drives without asking my computer for permission!

---

### Post by Paperclips4u on 2007-05-24
Even if you didn't change the root password, isn't it possible for them to log into a terminal using another user (other than root) and just use the command "sudo passwd root." 
Just curious.

---

### Post by Kilz on 2007-05-25
> **Paperclips4u said:**
> Even if you didn't change the root password, isn't it possible for them to log into a terminal using another user (other than root) and just use the command "sudo passwd root." 
Just curious.

In a normal Ubuntu install the root account doesnt exist. This is safer in that an attacker now needs a login name and password. If you create a root login, you give an attacker half the information, the login name is root. Not only that but it is an account that can do anything.

---

### Post by Aidy on 2007-05-25
> **Kilz said:**
> In a normal Ubuntu install the root account doesnt exist. This is safer in that an attacker now needs a login name and password. If you create a root login, you give an attacker half the information, the login name is root. Not only that but it is an account that can do anything.

Um, The root account still exists in a normal ubuntu install, it's just "disabled" by default.

It's possibly slightly more secure keeping it this way, as root is a known username, but the security impact of enabling the root account is minor, assuming it's used wisely.

If an attacker can break into a normal ubuntu user's account, then they essentially have full control - sudo bash, for example.

And "gksudo nautilus" strikes me as a much nastier solution, it's entirely possible to run the risk of confusing which nautilus windows have root permissions and which don't then. su typically changes the prompt.

---

