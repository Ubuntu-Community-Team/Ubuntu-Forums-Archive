---
title: "can't install wine in ubuntu 12.04"
date: 2015-04-11
forum: Wine
---

### Post by r2d23 on 2015-04-11
why i can't install wine in my ubuntu 12.04?

broken packages it say, but i don't have broken packages 

i treid with synaptic and on the terminal but nothing

help please!

---

### Post by bytr on 2015-04-11
If you are using 64-bit (AMD64) architecture, please try to run the following commands in the terminal:
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install wine

```

---

### Post by r2d23 on 2015-04-13
error --add-architecture i386 unknown 

:(

---

### Post by bytr on 2015-04-13
> **r2d23 said:**
> error --add-architecture i386 unknown 

:(

Sorry, I misread. "dpkg --add-architecture" is not supported in Ubuntu 12.04.

Instead of the above commands, please try to run the following commands in the terminal:
```
sudo sh -c "echo 'foreign-architecture i386' > /etc/dpkg/dpkg.cfg.d/multiarch"
sudo apt-get update
sudo apt-get install wine

```

---

### Post by r2d23 on 2015-04-14
the same problem...

"The following packages have unmet dependencies" wine1.4
"Failed to correct problems , you have held broken packages "

but i don't understand which are, i'm so newbie...

---

### Post by bytr on 2015-04-14
> **r2d23 said:**
> the same problem...

"The following packages have unmet dependencies" wine1.4
"Failed to correct problems , you have held broken packages "

but i don't understand which are, i'm so newbie...

I cannot duplicate your problem, but I would suggest that you should read [this page]("https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/994309").

---

### Post by mastablasta on 2015-04-16
it could be as simple as bad download. clearing cache and re-downloading might solve it.

but first do 
```
sudo apt-get update
sudo apt-get upgrade
```

to see if it gives any errors.

here is how you troubleshoot the error: [http://askubuntu.com/questions/223237/unable-to-correct-problems-you-have-held-broken-packages](http://askubuntu.com/questions/223237/unable-to-correct-problems-you-have-held-broken-packages)

---

### Post by r2d23 on 2015-04-17
thanks i'll try!

---

