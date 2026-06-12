---
title: "i've installed... now what?"
date: 2007-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by souldaddy on 2007-05-31
I'm a linux nub, although I've used a few distributions in the past very briefly.  So, I've installed, now what?

One thing I'd like to check is if I installed my Nvidia drivers correctly.  I'm pretty sure I haven't, but I was curious what the "Device Manager" equivalent was for Ubuntu.

Next...
What should I get?  I can listen to music fine, but do I need to install some sort of creative drivers for my audigy?

What are basic things I basically need to do to survive in linux?  The word repository keeps coming into my head and I cannot remember why.

Also, isn't there some huge like software database you can just "search" for software and install it in a couple clicks?

The last thing I can think of is, what's a "decent" irc and torrent client.  I'm looking for something light weight like mIRC and utorrent.

Thanks, and I really do appreciate any help and guidance the forum can offer.  I'm really looking to "make the switch."  Vista has driven me up the wall :(

---

### Post by jamesford on 2007-05-31
ubuntuguide.org is your friend, u can find out about isntalling nvidia there. to check if nvidia drivers re installed and working u can type 'glxgears' in a terminal. if the animation is smooth its probably installed

audigy shoudl work out of the box, to adjust settings, enable surrounf etc type 'alsamixer' in a terminal.ubuntuguide also has a sectiona bout setting up sound in gnome

the huge software database ur talking about is the repositories. its avaiable tru synaptic which u find in system > administration (note not all repositories are enabled by default. u can enable these in synaptic by clicking settings > repositories

for irc xchat is probably the best option - its in synaptic
for torrents azureus is a good choice, but therse a new torrent client in the making called deluge. its still pretty beta but does a great job [http://deluge-torrent.org/](http://deluge-torrent.org/)
the version in the repositories is outdated i thnik so grab it from their website (nb thers smt wrong with their server so u gotta rightclick > save link as to download the .deb files. then double click the deb files to install) edit:actually u have to go via the forums to find the ubuntu deb packages of deluge

the device manager, there smt in system > preferences called hardware information
theres also 'sysinfo' which u can install via synaptic

---

### Post by rsambuca on 2007-05-31
For the nvidia drivers, just go to "system -> administration -> Restricted Drivers Manager".  That should tell you if the nvidia proprietory driver is installed and in use.

---

### Post by GrueTamer on 2007-05-31
> **souldaddy said:**
> I'm a linux nub, although I've used a few distributions in the past very briefly.  So, I've installed, now what?

One thing I'd like to check is if I installed my Nvidia drivers correctly.  I'm pretty sure I haven't, but I was curious what the "Device Manager" equivalent was for Ubuntu.

Next...
What should I get?  I can listen to music fine, but do I need to install some sort of creative drivers for my audigy?

What are basic things I basically need to do to survive in linux?  The word repository keeps coming into my head and I cannot remember why.

Also, isn't there some huge like software database you can just "search" for software and install it in a couple clicks?

The last thing I can think of is, what's a "decent" irc and torrent client.  I'm looking for something light weight like mIRC and utorrent.

Thanks, and I really do appreciate any help and guidance the forum can offer.  I'm really looking to "make the switch."  Vista has driven me up the wall :(

The reason the word repository has popped into your head is because the ubuntu repositories are just awesome.  Over 20 thousand easily installable through apt packages are available, for just about everything you need to do.  You don't have to install sound drivers (most likely), as this is already done.  Apt powers your "'search' for software and install it in a couple clicks", and the easiest way for you to do this is with the graphical tool called Synaptic, a GUI frontend to apt.

As for the irc/torrent client, I use bittornado for torrenting, because it is lightweight, unlike Azureus, which really isn't.  As for mIRC being lightweight, I disagree with this, but if you want something like mIRC, xchat or kvirc works, but if you want lightweight, irssi and weechat work.

You can survive in linux using these forums, the ubuntu wiki, [ubuntuguide.org]("http://ubuntuguide.org"), and a the [ubuntu experiment]("http://ubuntu.gridrunners.com/"), a new but well designed and informative site for new users.  But in my opinion, the most important site to visit is [LinuxCommand]("http://linuxcommand.org").  This site is a simple and easy to follow way to learn a little bit more about the terminal.  Whether you choose to learn about it is up to you, but if you ever want to, linuxcommand will be a good site for you to use.

---

### Post by shad0w_walker on 2007-05-31
Ok, seeing as i have no creativity il answer the various things in order.

1. Testing Nvidia drivers

If you are using the latest ubuntu (7.04) then you should be able use the restricted drivers manager to deal with this

```
System -> Administration -> Restricted drivers manager 
```

This will prompt you for your password (For admin level access) when it has opened you should end up with a very simple and to the point dialog. It should say something along the lines of:

```
NVIDIA accelerated graphics driver
```

and will have a pair of columns after that showing if the drivers are enabled (If not just tick to download and install the drivers) and another column that shows if the driver is in use or not.

This should show you wll you need to know. If you want to doubly sure your drivers are working properly, hit Alt + F2 and run this command:

```
glxgears
```

That should open up a small box with 3 spinning gears in it, which should be spinning at a reasonable speed.

2. Unless you find some feature that you specifically need from your soundcard there isnt any reason to hassle yourself with external drivers. I run my system entirely off the included drivers and the nvidia driver from the restricted manager.

3. Repositorys

Repos are the massive database of software which you can access from Add/Remove programs (Applications menu) or synaptic (System -> Administration -> Synaptic package manager)
There are a few extra repos which you should probably enable.

When in synaptic, goto Settings -> Repositories and simply tick all the repo boxes, this should give you access to about 20,000 programs.

4. IRC and torrents.

For IRC Xchat is a good client (There are two versions in the repos, its a matter of preference which you use)

Also deluge is a very good lightweight torrent client. 

Download link(You have to right click and save file as otherwise it tries to load a text file):

```
http://download.deluge-torrent.org/ubuntu/feisty/deluge-torrent_0.5.0-2zachtib1_amd64.deb
```

Good luck and welcome to the forums.

---

### Post by souldaddy on 2007-05-31
I love you ubuntu community.  Thanks for the details :D  I'll look into this stuff but I'll ask one more question that  I forgot to ask in the original post..
 I'm not ready to uninstall Vista and probably never will for practical reasons.  I've HEARD that Linux can read NTFS files.  So, is this true?  If so, is there anything special I need to do to make this happen?  What about writing to an NTFS file system?  

If writing is out of the question, I'm sitting on 440 gigs of unformatted space and I'm probably gonna give Linux 100-200 gigs of that.  Is there a tool like the one in Windows where you can create a partition like that easily and safely(not whiping out something on accident) in Ubuntu?

Thanks again guys, I definitely love you :D

---

### Post by shad0w_walker on 2007-05-31
If memory serves there is NTFS-3g in the default repos. If you open up synaptic and do a search for ntfs-3g you should find a few things. 

What you probably want is 

ntfs-3g and ntfs-config 

which will give you the NTFS driver (read/write support) and a graphical tool to configure where you want the NTFS partition mounted.

To run ntfs-config, hit Alt + F2 and run:

```
gksu ntfs-config
```

Just follow the prompts and you should be fine.

---

### Post by souldaddy on 2007-05-31
aha, alright now i'm starting to get the "hang of it."  however, i'm starting to get into the hardcore as well :(

stuff that isn't in the repository that needs to be manually installed makes me sad.  I've googled my way through most of the errors, but now I've hit a hangup.  I'm trying to manually install Pidgin and eventually deluge.  Deluge I haven't tried yet but I imagine i'm not entirely setup to do so.

So, with Pidgin I'm stuck on getting glib 2.0

With Deluge its giving me a warning in the readme that I need all these things ready to go:
"First, make sure you have the proper bulid
dependencies installed.  On a normal Debian
or Ubuntu system, those dependencies are:

python-all-dev
python-all
python-support
libboost-dev
libboost-thread-dev
libboost-date-time-dev
libboost-filesystem-dev
libboost-serialization-dev
libboost-program-options-dev
libboost-regex-dev
zlib1g-dev "

Again, thanks for all the halp so far gents.  I definitely appreciate it.

Ahhh poop, one more thing, I've been trying to find some support for my Zen Vision:M(mp3/mtp device) in the linux.  I remember reading somewhere that some media player had built in support for it, but I can't remember for the life of me which it was.  Any insight there?

Hugs and kisses,
Linux Noob :)

---

