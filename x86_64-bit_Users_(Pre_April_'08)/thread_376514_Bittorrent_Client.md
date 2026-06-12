---
title: "Bittorrent Client"
date: 2007-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-03-05
I downloaded the torrent for Feisty amd64 Herd 5. The BitTorrent tool that was installed by default in my Edgy amd64 computer popped up and completed the download. However, the information it displayed was rather spartan. I'd like to know how more details. 

So I installed Azureus and Azureus.gcj. It disappeared from the screen quite often. After a while I gave up and completely removed it. I suspect it does not like Sun Java 5 that I have installed.

Then I tried BitTornado, but it crashed a lot too.

I have two questions:

1) Once I completed the download of Feisty I immediately burned a CD, then restarted the computer to try it out. That stopped all uploads, of course. After playing with Feisty I rebooted to my normal Edgy installation. Can I restart the torrent from the .iso file that is still on my hard disk, so as to give others the benefit of my upload?

2) Is there another bittorrent client besides the default, Azureus and BitTornado? I mean, one that doesn't crash every couple of minutes and has a few more features than the default Bittorrent client?

---

### Post by julipanno on 2007-03-05
Deluge (GNOME) and Ktorrent (KDE) are both excellent bittorrent clients sporting a number of great features and running lightly on their respective desktop environments.

peace,
Stian

---

### Post by julipanno on 2007-03-05
> **John Jason Jordan said:**
> Can I restart the torrent from the .iso (...)?
and yes ;-)

---

### Post by John Jason Jordan on 2007-03-05
> **julipanno said:**
> and yes ;-)
Thanks, but how?

When I clicked on the Ubuntu Feisty torrent download it automatically launched BitTorrent. Eventually the download completed (five hours). Then I had to restart the computer in order to try out Feisty. The Feisty .iso is still on my hard drive and I now want to share by letting it be uploaded again. I opened BitTorrent and all that I got was a window that said "Open location for BitTorrent meta file." But there is no help file where I can figure out what a meta file is, and it didn't display the Feisty .iso file, so I guess that is not a meta file.

I installed Deluge but, again, no help file and I can't figure out how to use it. Seems to run OK, though. I tried File > Add a Torrent from File, but the browse window does not display the Feisty .iso file, so I guess it doesn't want to let me share it back with others.

If the idea is for torrent downloaders to share back, you'd think there would be instructions somewhere on how to do that.

---

### Post by julipanno on 2007-03-05
> **John Jason Jordan said:**
> Thanks, but how?

(...)

I installed Deluge but, again, no help file and I can't figure out how to use it. Seems to run OK, though. I tried File > Add a Torrent from File, but the browse window does not display the Feisty .iso file, so I guess it doesn't want to let me share it back with others.


With Deluge, you should specify a download directory in the settings before you start using it. To share an already downloaded .iso you can simply copy (or move) the .iso file to that directory, and then open the torrent-file for that .iso. If you no longer have the original .torrent file (i.e. you opened it directly in the Bittorrent client and did not save it to the desktop first), you can download another .torrent from [http://cdimages.ubuntu.com/releases/feisty/herd-5/](http://cdimages.ubuntu.com/releases/feisty/herd-5/) 

BTW: Torrents are a type of Meta-files; they are very small files that tell a program (any bittorrent client) where to look for a specific file (like a feisty herd 5 iso).

peace,
Stian

---

### Post by ffxr on 2007-03-05
i like ktorrent, theres a new version version 2.1 which adds a few more features & improves the gui a little.. i dont know if this is the one in the fiesty repo's; i got the deb from ktorrents' site itself..

it runs really well on my system & doesnt have *that* many kde depencies.

i tried deluge btw, but it dosent seem to as feature rich as ktorrent.

---

### Post by John Jason Jordan on 2007-03-05
> **julipanno said:**
> ... Torrents are a type of Meta-files; they are very small files that tell a program (any bittorrent client) where to look for a specific file (like a feisty herd 5 iso).
Ah, that's the fact I was missing. I never downloaded the torrent file, just the iso.

> **ffxr said:**
> i like ktorrent, theres a new version version 2.1 which adds a few more features & improves the gui a little.. i dont know if this is the one in the fiesty repo's; i got the deb from ktorrents' site itself..

it runs really well on my system & doesnt have *that* many kde depencies.
Ktorrent was in my Edgy repositories, so I installed it. I agree, it's much better than Deluge -- and Deluge has something wrong with the font it uses for menus. I have that problem occasionally with other apps; I think it's a GTK problem. Anyway, once I downloaded the torrent it found it and I am now uploading to do my share. I have cable connection and the computer sits here running all day and night so it might as well be doing something to help Ubuntu folks.

The only thing wrong with Ktorrent is that the Help menu required me to install Khelpcenter, which I did, only to get a page that said "soon there may be some documentation for Ktorrent." I keep trying to tell programmers that when they've finished the app and the code runs perfectly, the job is half done. They don't get it. (sigh)

Now I have just one more question: BitTorrent is the default app for torrent downloads. That is, when I click on a file with Firefox it pops up BitTorrent. I want it to pop up Ktorrent, but I can't figure out how to make Ktorrent the default app. I tried to uninstall BitTorrent but it wanted to uninstall the whole Ubuntu desktop as well. 

Thanks guys.

---

### Post by dfreer on 2007-03-05
With .torrent files (really, any file), simply right-click on the file and select "Properties". Select the "Open With" tab and then it will have a list of program already associated with .torrent. If Ktorrent or Deluge or whatever you are currently wanting to use isn't in there, there is an option "Add" a program. From now on whenever you double-click a .torrent file the program you specified will open up :)

---

### Post by ffxr on 2007-03-05
in firefox to associate file types with an app..

is edit -> preferfences -> content -> file types -> manage..

i had the smae problem myself & it had me scratching my head for a while an all.. : )

---

### Post by John Jason Jordan on 2007-03-08
> **ffxr said:**
> i like ktorrent
I have been using ktorrent for a few days now. I really like it, compared to the others. But there is no Help file and I have lots of questions about what things mean. Is there a forum somewhere? A wiki? Anything?

---

### Post by kragen on 2007-03-08
Gotta say, I'm a massive fan of rtorrent - its text based, but it does pretty much everything i want, its small, fast, and it just works on x86-64, only drawback is that its text based, and takes a little bit of getting used to.

It would be neat if someone could convert it to gtk or something, since installing it i've tried loads of different graphical clients, and none of them seem to be any good. They are either slow, hard to use, dont work, or dont offer all the features I need. Eventually I gave up installing random clients and went back to the one I knew worked.

---

### Post by julipanno on 2007-03-08
> **John Jason Jordan said:**
> I have been using ktorrent for a few days now. I really like it, compared to the others. But there is no Help file and I have lots of questions about what things mean. Is there a forum somewhere? A wiki? Anything?
[http://btfaq.com](http://btfaq.com) is generally regarded as the best FAQ on bittorrent in general. For Ktorrent specific issues you can check the Ktorrent forum available on [http://ktorrent.org/forum/](http://ktorrent.org/forum/)

---

### Post by julipanno on 2007-03-08
> **dfreer said:**
> With .torrent files (really, any file), simply right-click on the file and select "Properties". Select the "Open With" tab and then it will have a list of program already associated with .torrent. If Ktorrent or Deluge or whatever you are currently wanting to use isn't in there, there is an option "Add" a program. From now on whenever you double-click a .torrent file the program you specified will open up :)
Unfortunately the possibility of recieving torrents from other applications is not implemented in the stable version of Deluge, but the shortly upcoming release 0.5 should fix that. Deluge is still a young project, but it has developed amazingly fast and may soon catch up with Ktorrent in features. The reason I choose to use Deluge, is the fact that it hardly uses any resources at all on my Gnome desktop, enabling me to leave it running 24/7 but still use the computer for demanding tasks.

---

### Post by rtpca65 on 2007-03-10
Does Ktorrent work well?

---

### Post by jamesford on 2007-03-10
i just switched from azureus to deluge 0.5 rc2, it does the job but the 64 bit version has got a few bugs. going to stick with it tho, its a good client, potentially excellent

---

### Post by John Jason Jordan on 2007-03-10
> **rtpca65 said:**
> Does Ktorrent work well?
I'm loving it, compared to BitTorrent (no features), Deluge (bad interface) and Azureus (crash, crash, crash). There was an update in the repositories a couple days ago and now it is even nicer.

The only problem is lack of documentation. The Help file takes you to a page that says "we didn't get around to writing documentation yet." So in order to find out what the terms and abbreviations on the buttons mean you have to google all over.

---

### Post by diesel1 on 2007-03-10
> **rtpca65 said:**
> Does Ktorrent work well?

I only use ktorrent, it is very stable and does exactly what you need.

Diesel1.

---

### Post by John Jason Jordan on 2007-03-15
> **diesel1 said:**
> I only use ktorrent, it is very stable and does exactly what you need.
Me too. I like it very much, and thanks to everyone who made recommendations. However, I have a problem with it, although the problem may be my misunderstanding. 

First at home I have cable, and frequently see download speeds of 5-600K/s, that is, if the server I am downloading from can deliver it to me that fast. Upload speeds ove 200K/s are also possible. The problem is that when Ktorrent is running my bandwidth is just about completely gone. It takes several minutes to download half a dozen e-mails. Refreshing the forum page here can take several minutes. I could understand this if Ktorrent were uploading or downloading enough to account for the loss of bandwidth, but it's not. 

At the moment it is seeding Feisty Herd 5, Dapper i386, Gentoo and OpenSuse 10.2. I am not downloading anything, as these are all completely downloaded and I am just being a good dude and sharing them back. The total upload that I see averages around 50K/s or so. That should be fairly trivial, but unless I stop Ktorrent altogether I can't do anything else on the net without waiting forever. It will probably take three or four minutes for this message to post after I hit the Submit Reply button.

Is this normal? I'd like to leave it running to help others, but if this is the consequence, I'll have to shut it down. Is there anything else I can do?

---

