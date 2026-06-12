---
title: "Best Way to Transfer Torrents to Linux"
date: 2008-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by lancerocke on 2008-03-11
I'm switching from Windows to Linux, so I was wondering what the best way to transfer all my torrents to the best Linux torrent client was.
I have the same torrents on multiple sites which consist of torrents in different directories, so they aren't all in the same directory.
What's the best Linux torrent client and what is the best way to transfer these torrents from uTorrent to the best Linux client.
Thanks in advance for the help.
[[IMG]http://thumbnails2.imagebam.com/371/9263633700236.gif[/IMG]]("http://www.imagebam.com/image/9263633700236") [[IMG]http://thumbnails2.imagebam.com/371/fc56593700237.gif[/IMG]]("http://www.imagebam.com/image/fc56593700237") [[IMG]http://thumbnails2.imagebam.com/371/c563a83700238.gif[/IMG]]("http://www.imagebam.com/image/c563a83700238") [[IMG]http://thumbnails2.imagebam.com/371/97795a3700239.gif[/IMG]]("http://www.imagebam.com/image/97795a3700239") [[IMG]http://thumbnails2.imagebam.com/371/61b2ad3700240.gif[/IMG]]("http://www.imagebam.com/image/61b2ad3700240")
[[IMG]http://thumbnails2.imagebam.com/371/f647df3700241.gif[/IMG]]("http://www.imagebam.com/image/f647df3700241")

---

### Post by jamesford on 2008-03-11
i recommend [http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by Sockerdrickan on 2008-03-11
I think you can just copy the folders and use the same torrent file.

Use [www.transmissionbt.com](www.transmissionbt.com) it comes with Ubuntu 8.04.

---

### Post by konungursvia on 2008-03-12
I save torrents and their target downloads on an external ntfs-omratted drive and use the same directories and torrents in both OSs. In Linux I run Deluge.

---

### Post by Dark Star on 2008-03-12
Yep deluge is one of the best but if you choose KDE you will get Ktorrent by defauls :) Ktorrent is also a gr8 s/w for torrents :)

---

### Post by sloggerkhan on 2008-03-12
fyi, get deluge from deluge-torrent.org, the newer version is a lot better than the repo one.

---

### Post by kwaanens on 2008-03-12
Put this in /etc/apt/sources.list

[http://ppa.launchpad.net/zachtib/ubuntu](http://ppa.launchpad.net/zachtib/ubuntu) gutsy main universe

---

### Post by NightwishFan on 2008-03-12
Ktorrent is the best client I have seen.

---

### Post by sloggerkhan on 2008-03-12
> **kwaanens said:**
> Put this in /etc/apt/sources.list

[http://ppa.launchpad.net/zachtib/ubuntu](http://ppa.launchpad.net/zachtib/ubuntu) gutsy main universe

That's a bit cryptic and lacks context. Add some random repo with no reason given? ....

---

### Post by lancerocke on 2008-03-12
> **sloggerkhan said:**
> That's a bit cryptic and lacks context. Add some random repo with no reason given? ....
lol.
i know what u mean :)

---

### Post by Tews on 2008-03-12
Ive always used azereus ... Never had a problem with it :)

---

### Post by kwaanens on 2008-03-12
> **sloggerkhan said:**
> That's a bit cryptic and lacks context. Add some random repo with no reason given? ....

If you even bothered to check the link you'd see that that this ppa is for Deluge, and is kept by one of the main devs.  That way you'll get updates automatically.
On ubuntuforums I trust that people know how to click links, and check the source every now and then.

---

### Post by jp_coll2003 on 2008-03-15
I second the motion for Deluge. I have tried nearly all the torrent packages on Ubuntu and this one gives me no problems. Even down to the little nigly things like being able to set to random ports. That made my life a lot easier.

---

### Post by gaspard.leon on 2008-03-15
Previously on gutsy I always just downloaded the latest debs from [http://deluge-torrent.org/](http://deluge-torrent.org/)

Using hardy, I installed the deluge using the repositories (synaptic etc)
The version in the hardy repos was only one version out of date.. it worked.. however it wouldn't save certain settings... fairly annoying.. and it aways prompts to upgrade...

So I downloaded the newer one from the site as I had done on gutsy... it wouldn't install... so i kept the repo one and just lived with prompts and non-saved settings...

today just as a test I removed the packages from synaptic and downloaded the latest one and installed it with gdebi... works great and now saves settings correctly!

moral of the story is if developers go to the trouble to put together a working ubuntu-specific deb, it might actually be better then the repo version...

The other moral of the story is now weather I can be bothered to report the bug to the ubuntu launchpad.. most lilkey they will say it's a deluge problem and the bug will be marked invalid...

I wonder if there were an easy way to maintain packages (GUI etc) if the packages in the repos would be more up to date..

oh well as far as the post goes, USE DELUGE it's _good_ and regularly updated/fixed

oh yeah, I was using utorrent with wine before i found deluge ;)

---

### Post by Tosa on 2008-03-15
Ktorrent is nice, but it crashes (on my machine) much to often. If I stop and/or start  seeding/leeching files a couple of times it will crash. It crashes very often when I remove USB flash stick!?

Maybe I should try deluge...

---

### Post by Nythain on 2008-03-15
just because it hasnt been said yet...
drum roll please...
rtorrent!

hands down the BEST torrent client i've ever used... but its cli so no one likes it... but it has an interface, so its not that complicated... just a bit of editing/tweaking to the config file and it can do what all those others can do, lighter, and in my experience faster and more efficiently... i've never gotten a gui client to get me speeds over 1000Kb/s

and, when i run it in a "screen" i can remotely administer it via ssh from anywhere... do that Deluge and KTorrent :P

---

### Post by kwaanens on 2008-03-15
> **gaspard.leon said:**
> and it aways prompts to upgrade...

You are aware that you can turn this setting off?

Getting a bit OT: Personally, I often download debs from upstream, but that is because I like to live on the edge with some apps. If users are **happily** using an app from the repos, I would recommend them staying with that. Project developers may know their app well, but their debs usually don't get the amount of Ubuntu specific testing that official repo packages do. There is a reason users are warned about getting 3rd party stuff.

- Ketil

---

### Post by kwaanens on 2008-03-15
> **Nythain said:**
> and, when i run it in a "screen" i can remotely administer it via ssh from anywhere... do that Deluge and KTorrent :P

Deluge has a web user interface...

---

### Post by Nythain on 2008-03-15
well, tahts got to be relatively new... ill admit, i havent messed with ktorrent or deluge in quite the while... once i found rtorrent i've never had much reason too...

Thanks for pointing that out, though ill stick with my secure ssh connection over a web interface, but those web interfaces are awfully pretty and easy to use :P

---

### Post by kwaanens on 2008-03-15
> **Nythain said:**
> well, tahts got to be relatively new...

FYI:
Deluge 0.5.6 (24 October 2007)
- Web Interface Plugin

From: [http://deluge-torrent.org/Changelog.php](http://deluge-torrent.org/Changelog.php)

---

