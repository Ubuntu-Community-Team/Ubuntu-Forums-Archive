---
title: "Titan Poker with Wine"
date: 2006-10-26
forum: Wine
---

### Post by Genix on 2006-10-26
Has anyone gotten it to work?  I can get it installed and run it but when I go to a table and try to sit down the box that pops up that is supposed to ask you how much money to buy in with is just blank.  Also anytime I try to leave a room I get a RunTime error.  Any ideas?

---

### Post by dowst on 2007-01-24
Hi there,

I also get the runtime error when leaving a room, but I can buy in and play quite normally, except the mouse cursor is flickering between normal an hand style when hovering a button. I could live with that, but the runtime error kills off multitable tournaments, what forces me back to windows almost every day :/

Did you try other clients? I did with all services I've got a real money account, which makes:

PartyPoker - Crashes when opening the lobby
PokerStars - Fully playable with all features, no crashes at all
TitanPoker - Partially playable
VC Poker - Untested

Any Experiences by other Players?

Greetings,
 MrDowst

---

### Post by MeToo72 on 2008-04-12
My roommate just installed linux...how do i run titan poker???

---

### Post by atomizer on 2008-08-25
This is a bit late, but for people still looking for an anwser:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4037](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4037)

click on the link "all versions", and it will be explained to you.

(short: install WINE, install ies4linux (internet explorer for linux), run TITAN POKER installer with ies4linux.)

My experience is that it only works with the newest version of WINE (ies4linux will complain), you should add the wine repos to your sources list
and get a valid gpg key


wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list


Now you can install the latest WINE from your packetmanager.

---

