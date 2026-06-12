---
title: "[SOLVED] Disable sudo -i"
date: 2008-08-02
forum: x86 64-bit Users
---

### Post by vikrant_me on 2008-08-02
How do i disable sudo -i on my ubuntu, once someone does this he has root privileges and can misuse my machine.

---

### Post by sisco311 on 2008-08-02
remove the user from the admin group
```
sudo delgroup *username *admin
```

---

### Post by vikrant_me on 2008-08-02
> **sisco311 said:**
> remove the user from the admin group
```
sudo delgroup *username *admin
```

How about something a little less extreme?

---

### Post by xen-uno on 2008-08-02
Just what are you trying to protect your OS from? Kids? Workplace? You ought to create a new user and play around with User Privileges ... see how far you can go. If default list is not strong enough, there's probably some HowTo around that explains how to really lock it down.

---

### Post by jocko on 2008-08-03
> **vikrant_me said:**
> How do i disable sudo -i on my ubuntu, once someone does this he has root privileges and can misuse my machine.

As long as a user have the right to use sudo (even without -i), he/she has full root privileges and can misuse your machine.
To prevent them from using sudo, just remove them from the admin group, as sisco311 said (this is not extreme. It does exactly what you want).
Why would sudo -i be worse than just sudo (or sudo bash, sudo su, sudo gnome-terminal, sudo nautilus, sudo gedit, sudo <whatever>, all of which does pretty much the same as sudo -i)?

---

### Post by vikrant_me on 2008-08-03
> **jocko said:**
> As long as a user have the right to use sudo (even without -i), he/she has full root privileges and can misuse your machine.
To prevent them from using sudo, just remove them from the admin group, as sisco311 said (this is not extreme. It does exactly what you want).
Why would sudo -i be worse than just sudo (or sudo bash, sudo su, sudo gnome-terminal, sudo nautilus, sudo gedit, sudo <whatever>, all of which does pretty much the same as sudo -i)?

The deal is sometimes i leave my pc unattended sometimes which makes it vulnerable, anyone can run a sudo -i which does not prompt for a password (mayb this can be enabled???), so sudo-ing without a password kinds

---

### Post by jocko on 2008-08-03
> **vikrant_me said:**
> The deal is sometimes i leave my pc unattended sometimes which makes it vulnerable, anyone can run a sudo -i which does not prompt for a password (mayb this can be enabled???), so sudo-ing without a password kinds

sudo always asks for a password, irregardless of which command or flag you put behind it, unless you have recently used sudo so that the password is stored for 15 minutes...

---

### Post by vikrant_me on 2008-08-03
> **jocko said:**
> sudo always asks for a password, irregardless of which command or flag you put behind it, unless you have recently used sudo so that the password is stored for 15 minutes...

How do i change this 15mins to 0 mins so it prompts me for a password every time?

---

### Post by jocko on 2008-08-03
> **vikrant_me said:**
> How do i change this 15mins to 0 mins so it prompts me for a password every time?
Actually, I'm not sure how long the default timeout is... it may be just 5 minutes.
But [this post should help you]("http://ubuntuforums.org/showthread.php?p=5334935#post5334935"). You could probably set the timeout to 0 to have it ask every time (unless that will make it store the password forever.... I'm not sure. Otherwise set it to 1 to have only one minute timeout.).

---

### Post by rahmath on 2008-08-03
Hi Vikrant,

Just edit /etc/sudoers file and add as the last line;

Defaults:ALL timestamp_timeout=0

then save and quit.


NOTE: it is always better to unlock the root account b4 playing with sudoers file, bcoz, if something goes wrong in sudoers file, sudo will not work. So if you have unlocked the root account, you can easily fix it up and then lock the root account again.

so procedure should be;

1. unlock the root a/c

$ sudo passwd root

set the password for root.

2. Then edit the sudoers file and place the entry as the last line.

3. If something goes wrong, then switch to root by su -, and then u can fix it.


Thats all...

---

### Post by vikrant_me on 2008-08-03
> **rahmath said:**
> Hi Vikrant,

Just edit /etc/sudoers file and add as the last line;

Defaults:ALL timestamp_timeout=0

then save and quit.


NOTE: it is always better to unlock the root account b4 playing with sudoers file, bcoz, if something goes wrong in sudoers file, sudo will not work. So if you have unlocked the root account, you can easily fix it up and then lock the root account again.

so procedure should be;

1. unlock the root a/c

$ sudo passwd root

set the password for root.

2. Then edit the sudoers file and place the entry as the last line.

3. If something goes wrong, then switch to root by su -, and then u can fix it.


Thats all...


wonderful! worked like a charm :) i did a  

export EDITOR=gedit && sudo -E visudo though not too good with the text editor

---

### Post by rahmath on 2008-08-03
But you didnt give me a thanks... ](*,)

if u like the solution please click on the blue icon in the right corner of my post... to give thanks...

---

### Post by vikrant_me on 2008-08-03
> **rahmath said:**
> But you didnt give me a thanks... ](*,)

if u like the solution please click on the blue icon in the right corner of my post... to give thanks...

Done gave u thanks :D

---

### Post by sisco311 on 2008-08-03
If your problem was solved, then mark this thread as solved.
(top of the page, Thread Tools -> Mark this thread as solved)

---

