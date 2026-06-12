---
title: "newbe installing wine"
date: 2008-01-28
forum: Wine
---

### Post by rollerworld on 2008-01-28
Newbe Installing Wine. O/S 6.06 Dapper Drake.

went to [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb), the instructions there were,

Debian and Debian-based distributions, such as Ubuntu, utilize a special tool for managing packages known as APT. APT is able to automagically install all of the needed dependencies for a software package, as well as keep the package up to date, by scanning what are known as APT repositories. Debian-based distributions have their own repositories of software, many of which include Wine, however we keep our own repository of the latest available packages here for download.

There used to be graphical instructions here, however we have found that the terminal commands are actually simpler to describe and quicker for the user to input. Because the commands below use sudo, you may have to enter your user password after hitting enter.
Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

I copied and pasted the two lines of code in to a terminal window,
the terminal window was found under accessories - terminal.

I entered the admin password as asked for and hit enter. 

Next, add the repository to your system's list of APT sources:

How do I do this? How do I get to the list of APT sources and enter
the folowing code?

For Ubuntu Dapper (6.06): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list

Thanks. Tony Johns. I hope this makes sense.

---

### Post by Speedoo on 2008-01-28
sudo wget [http://wine.budgetdedicated.com/apt/....d/dapper.list](http://wine.budgetdedicated.com/apt/....d/dapper.list) -O /etc/apt/sources.list.d/winehq.list

That command should add the source to your list.  You can also do it graphically by going to System - Administration - Software Sources

Is wine working for you?  Then you did it right!

Don't use it too much myself, but I think you also have to run

wineconfig

to set it up.  Good luck!

---

### Post by tkn4everb on 2008-01-28
how do you get a windows game to work in wine?
im new to this.

---

### Post by Speedoo on 2008-01-28
Keep in mind that wine is a constant work in progress.  Ideally, you should find directories under Applications - Wine - Programs - <your windows game here>, but I read a post in this forum earlier today where someone said their Wine -Programs directory was empty.  
What I do is install the windows program in my Ubuntu home directory, then open a terminal, change to that directory (for example "cd MissionRisk"), then type "wine MissionRisk.exe"
That should work for any windows program that will run under wine.  Not all will.  
Good luck!

---

### Post by rollerworld on 2008-01-29
Wine is not showing up in the applications menu, it did not appear to be down loaded in the terminal window. there was an error404, not
connecting to server. Thanks.:(

---

### Post by Speedoo on 2008-01-29
What happens when you open a terminal and type

sudo apt-get update
sudo apt-get install wine

Is that where you get the 404 error?  Sorry, I thought you had it installed already and were just trying to figure out how to use it.

---

### Post by zvacet on 2008-01-29
@ **rollerworld**

```
cat /etc/apt/sources.list
```

Post it here.

---

