---
title: "ubuntu can't automatically load torrents?"
date: 2011-08-25
forum: Wine
---

### Post by idjces on 2011-08-25
Hi, i used to have utorrent set up on ubuntu 9.04, and it worked fine just as it would in windows.

I've set up utorrent again on a new pc with ubuntu 10.04, and i've manged to get utorrent to load and download correctly with wine. However it doesn't want to load torrents automatically from a directory (i drop .torrent files into this directory from over the network). It does move the .torrent files correctly opon dl completion. Any ideas what's going wrong?



The only reason i use utorrent is because i need to run multiple instances, it helps to seperate different torrents/files - some i will delete, others ill want to seed etc, so it helps organisation. I'm open to alternate suggestions for this?

Thanks

---

### Post by tommpogg on 2011-08-25
> **idjces said:**
> 
The only reason i use utorrent is because i need to run multiple instances, it helps to seperate different torrents/files - some i will delete, others ill want to seed etc, so it helps organisation. I'm open to alternate suggestions for this?


It seems that Ktorrent would fit your requirements.

---

### Post by idjces on 2011-08-25
> **tommpogg said:**
> It seems that Ktorrent would fit your requirements.

i have it installed and can see how you can create groups, etc.

I want to be able to specify groups remotely, eg drop a .torrent file into a certain directory, and then the completed download will then be placed in a corresponding directory.

eg directories -

load A
load B
completed A
completed B

---

### Post by tommpogg on 2011-08-25
> **idjces said:**
> i have it installed and can see how you can create groups, etc.

I want to be able to specify groups remotely, eg drop a .torrent file into a certain directory, and then the completed download will then be placed in a corresponding directory.

eg directories -

load A
load B
completed A
completed B

maybe I don't understant what you want to do, but I'm pretty sure that Ktorrent aloows you to select the directory containing the .torrent file, the download directory and the directory where you want to store the file once the download has been completed.

---

### Post by idjces on 2011-08-25
> **tommpogg said:**
> maybe I don't understant what you want to do, but I'm pretty sure that Ktorrent aloows you to select the directory containing the .torrent file, the download directory and the directory where you want to store the file once the download has been completed.

yea it does... but only once for everything. I need multiple categories, which is why i was running multiple utorrent instances.

eg, place a torrent in directory "load A", and the completed files will be placed in a folder "completed downloads A". If the torrent is placed in another directory "load B", the completed files will be placed in another directory "completed downloads B".

So i can categorize downloads/trackers by simply placing the .torrent file in a different folder. Saves me hunting through numerous files which might be there seeding indefinitely.

As far as i can tell ktorrent and every other client more or less  has to use single directories, you may be able to specify where the downloaded files end up... but then you have to go into the client gui and specify it for most .torrents, as you add them

---

### Post by tommpogg on 2011-08-25
OK, now I've got it. Unfortunately. I don't know how to do it... sorry

---

### Post by 8Kuula on 2011-08-25
Have you tried Deluge (v1.3.x)? Looks like it has 'AutoAdd' plugin that watches directory X and then moves completed download to directory X.

Never used myself but worth to look up, i think.

---

### Post by idjces on 2011-08-26
> **8Kuula said:**
> Have you tried Deluge (v1.3.x)? Looks like it has 'AutoAdd' plugin that watches directory X and then moves completed download to directory X.

Never used myself but worth to look up, i think.

Ah awesome suggestion, tried it out and seems to do all of that, plus it can auto-label depending on the folder the torrent is loaded from.


The only thing missing is options to move torrents upon loading and again completion. It only gives the 2 options of deleting the .torrent or renaming it :p

Thanks :D

---

