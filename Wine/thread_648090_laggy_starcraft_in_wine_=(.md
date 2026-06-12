---
title: "laggy starcraft in wine =("
date: 2007-12-23
forum: Wine
---

### Post by soviet911 on 2007-12-23
so i installed SC and the expansion, got battle.net to work and evrything is great, but stupid laggy im trying the nice command but this is what i get 
soviet911@Soviet911portable:~$ nice -n -20 wine "C:\Program Files\starcraft\starcraft.exe"
nice: cannot set niceness: Permission denied
soviet911@Soviet911portable:~$ 

what the hell am i suppose to do, it doesnt even ask for a password or anything! Any help will be apreciated.

---

### Post by moshy on 2007-12-23
preceed administrative commands with 'sudo ' to get a password prompt for temporary root access. I think it lasts for fifteen minutes, you still have to type sudo though, it will just remember the password for a few minutes.

So
$ sudo nice whatever

---

### Post by soviet911 on 2007-12-24
ok so i did that and no it tells me this, by the way im the only person useing the laptop and it has only one acount...  this is getting to me. 

soviet911@Soviet911portable:~$ sudo nice -n -20 wine "C:\Program Files\starcraft\starcraft.exe"
wine: /home/soviet911/.wine is not owned by you

---

### Post by chewit on 2007-12-24
I got the exact same problem with the starcraft demo. It was so laggy. It worked fine before, when I had Win98 installed on the same PC.

I thought it could be down to my ATi graphics card

---

### Post by Matrix101 on 2007-12-24
Afaik there are some problems with the reading of the CD which slows the game down. 

It should run fine when you follow some of the instructions from the comments here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=51](http://appdb.winehq.org/objectManager.php?sClass=version&iId=51)

---

