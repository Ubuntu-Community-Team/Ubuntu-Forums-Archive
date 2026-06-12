---
title: "Can't Install Win Game in Ubuntu 20.04. It Runs Good in 18.04 (different computer)."
date: 2021-01-19
forum: Wine
---

### Post by Wadcutter on 2021-01-19
I have a very simple Windows Sudoku game  (Simple Sudoku) running fine in my Ubuntu 18.04 computer under Wine. I'm upgrading to a new computer running 20.04.1 but can't seem to get it to work in Wine.Have forgotten how I got it to work in 18.04 computer.

Tried to install Wine from Terminal. I thought it worked-I get:

[CODE]~$ wine --version
wine-5.0 (Ubuntu 5.0-3ubuntu1)


.Wine is also a folder in HOME  containing other folders like "dosdevices" and "drive_c"
Makes me think Wine is installed

When I enter:
[CODE]
winecfg

The Wine configuration box pops up but no matter what I enter into it nothing happens.

I know the Win program isn't included in the Wine DB, but if it works in one computer, it should work in another running a similar  OS. 
However the computer running the program successfully  is

 [CODE]
wine --version
wine-3.0 (ubuntu 3.0-1ubuntu1)

Do I need an older ver of wine and how do I get it?

I probably should enter more info from the older computer but am not sure which or what.

---

### Post by CelticWarrior on 2021-01-20
You may try PlayonLinux as it allows the use of different Wine versions.

---

### Post by mastablasta on 2021-01-20
or move the program from the old computer. it's not just config. you might have added some libraries to make it work and similar. also i just "battled" with Bioshock on proton, but then i read that it works fine on 3.8, so i just used that and it really works with no issues. sometimes older version works better. 

Play on linux will help you manage versions and all more easy ...

---

### Post by Wadcutter on 2021-01-22
Thank you, CelticWarrior and mastablasta. I didn't know about PlayonLinux. I'll read up on it and give it a try. I had been using Wine on Ubuntu 14.04 for a  business program several years ago, but how I configured it and why it worked was always a mystery to me.

---

