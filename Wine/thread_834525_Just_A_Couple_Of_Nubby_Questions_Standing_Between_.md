---
title: "Just A Couple Of Nubby Questions Standing Between Me And Freedom"
date: 2008-06-19
forum: Wine
---

### Post by jpearls on 2008-06-19
1. What does ~ mean? cd  ie. "~/.wine/drive_c/"

2. Steam runs.  Hurray.  But I can't chat with friends.  I can see their messages, but not mine.  I assume they never get them because they never say anything more.

3.  I launch TF2, I get the valve logo, source logo, then BAM back to desktop.  No error boxes.  And my screen resolution stays "minimized" to what tf2 was launched at.

I mean try to running the game via terminal and seeing if it will me anything there.

4. I can't get utorrent to launch from links in firefox; everything else about both programs works perfectly.  I've tried three scripts:

#!/bin/sh

cd ~/.wine/drive_c/Program\ Files/utorrent
if [ "$1" != "" ]; then
var="`echo $1 | sed 's/\//\\\/g'`"
var="Z:${var}"
wine utorrent.exe "$var"
else
wine utorrent.exe
fi

#!/bin/sh
cd ~/
if [ "$1" != "" ]; then
var="`echo $1 | sed ’s////g'`"
var="Z:${var}"
wine .utorrent "$var"
else
wine.utorrent
fi

#!/bin/sh
wine /path/to/utorrent.exe "$*"

uTorrent's home: /home/earls/.wine/drive_c/Program Files/utorrent

So?

5. Is there a program or website that will verify you have the latest drivers?  Is that something built into ubuntu?

---

### Post by kaboodle_fish on 2008-06-19
~ is your home directory, so ~/stuff equals /home/yourusername/stuff

The rest I dunno

---

### Post by shanek on 2008-06-19
Are you absolutely needing to use uTorrent? There are a number of decent bittorrent clients that work in Ubuntu, like Azureus and Ktorrent. Both are in the repositories. I use Ktorrent all the time.

---

### Post by pixel :-) on 2008-06-19
first of all,you should have posted in the emulation thread

2. 3.
wine is as is,if it works for your programs good for you,you should aproche it as "there's a chance that it works" don't expect that it will.The title suggest that you expect 99% compatibility,it's very far from it.Rather expect it to fail.


4. I can't get utorrent to launch from links in firefox
You must configure firefox for this,in the url bar type "about:config" i don't know what to do next ,DON T EXPERIMENT ,the scripts are just for launching utorrent.like above,you don't need utorrent in linux,theres plenty of clients to chose from,a light wait client that it may do the job for you is transmission(similar to utorrent).

5. Is there a program or website that will verify you have the latest drivers?
Don't start installing drivers from here and there,just download what ever shows up in the repositories.The pakages from the repositories are tested.It's a bad idea to try to be cutting edge with the drivers.Your wine problems aren't due to drivers(95% probability).For something built in,it's synaptic(in gnome) and adept(in kde),i recommend synaptic,thies are just front ends for apt-get.

---

### Post by jpearls on 2008-06-19
1. Solved
2. Unsolved
3. Unsolved
4. Solved
5. Sort of solved.  How do I know I have the latest and greatest drivers for my hardware?

---

### Post by pixel :-) on 2008-06-20
for 2. 3. try the work arounds at the wine site [http://appdb.winehq.org/]("http://appdb.winehq.org/") and the forums.Also try [http://www.playonlinux.com/en]("http://www.playonlinux.com/en") it could help,it does the dirty work for you for some apps.Again you should expect that problems are unsolvable.

5.
Normally a notifier get launched at each boot,and it sits on your task bar if it found updates for the software you have already,drivers are software too.

---

### Post by jpearls on 2008-06-20
Thanks.

1. Solved
2. Unsolved
3. Unsolved
4. Solved
5. Solved

Nobody has a clue on this TF2 thing, eh? I was under the impression with the popularity of the game, the platinum rating and/or gold on Wine and all the guides meant that it *might* actually work.

However, despite my attempts of diagnosing the situation, I'm at a loss.

I have the latest UbuntuAmd64 Stable.
I have the latest Wine Stable.
I have the latest drivers for my hardware. (according to the consensus)

I've run the game through a shortcut, through steam, and through terminal.

I've used the typical launch parameters recommended.

Are there logs somewhere I'm missing that would assist?

For what it's worth: AMD 64 3000+, 1GB RAM, ATI Raedon 9800

I will try PlayOnLinux tonight.

---

### Post by philinux on 2008-06-20
Which version of wine are you running?

---

### Post by jpearls on 2008-06-20
"I have the latest Wine Stable."

IE Wine 1.0

It's also on my list to "disable in-game overlay."

But the AppDB and Buglist were of no assistance as they don't relate to my problem.  I have tried various aspects of the posts to  no avail.

---

### Post by p_quarles on 2008-06-20
Moved to Wine section.

---

### Post by pixel :-) on 2008-06-20
Aparently theres a regretion.Install 1.0-rc1 [http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html"), it's claimed as gold for that specific version.I never tried it but playonlinux can manage multiple versions of wine.

other:
try rename or delete .wine directory,it's a fake windows where the programmes are installed in.Some times an old .wine brockes stuff.

---

