---
title: "other users can't log in"
date: 2005-04-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by iostream on 2005-04-01
i have a strange problem here.

after a fresh install of hoary 64bit, no other user exept the one i created during installation can log in. any other user i create after installation has the problem that the password (and/or the username) is incorrect.

for example: i tried username "test" with password "test". result: password incorrect.

any suggestions?

---

### Post by bored2k on 2005-04-01
Did you try resetting the password with 
sudo passwd newuser ?

edit > Don't give your password dude ! :-P

---

### Post by iostream on 2005-04-01
;-) it works now!

the user test will not survive for long! :)


btw, do you know how to change that crappy picture at the login screen?

---

### Post by bored2k on 2005-04-01
I try to avoid going off topic [when its not in community chat], but for a new poster, I'll do it ^_^

GDM = System > Administration > Login Screen Setup

Splash after GDM = Applications > System Tools > Configuration Editor > apps > gnome-session > options > splash image ["Oop there it is"]

Change Grub ugly black loader = In synaptic package manager > Options > Repositories > Enable multiverse/universe . Then install grubconf and from a terminal window run grubconf [cute GUI frontend]. Optional > installing package grub-splashimages [or something like it] .


[http://www.art.gnome.org](http://www.art.gnome.org) 
[http://www.gnome-look.org](http://www.gnome-look.org)
[http://sleepybuddha.sl.funpic.de/ubuntu/](http://sleepybuddha.sl.funpic.de/ubuntu/)
[http://ruslug.rutgers.edu/~mcgrof/grub-images/images/working-splashimages/](http://ruslug.rutgers.edu/~mcgrof/grub-images/images/working-splashimages/)

---

### Post by iostream on 2005-04-01
sorry for the off-topic, but thank you, now all my questions are answered! :)

---

