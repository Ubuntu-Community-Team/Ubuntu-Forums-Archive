---
title: "help with file server"
date: 2009-01-24
forum: x86 64-bit Users
---

### Post by indyspcguy on 2009-01-24
First off this is my first server setup for linux.  I have converted many M$ users to Ubuntu, but now I find myself needing cs4 and using MS.  I know I know dont kill me, school does come first.  I need to setup an inexpensive server for file storage.  I dont understand the Lamp servers.  I think it may be overkill but I do need to learn Apache.  Should I install Lamp and filesever together or do I have to seperate them.  Secondly how lowend can this server be.  I am thinking bout the lowest level amd dual core chip and 2 gigs of memory, compared to my home desktop this is a dog.  I am trying to find the specs but I find minimums and I need to know real world needs.  I want to use this file server for my important projects and papers.  I want it as a secondary backup and dont need to run mirroring but would striping make a difference in speed.  It will be plugged into a router in my home, unless you guys say wireless is acceptable.
thanks in advance
Jb

---

### Post by Kilz on 2009-01-24
> **indyspcguy said:**
> First off this is my first server setup for linux.  I have converted many M$ users to Ubuntu, but now I find myself needing cs4 and using MS.  I know I know dont kill me, school does come first.  I need to setup an inexpensive server for file storage.  I dont understand the Lamp servers.  I think it may be overkill but I do need to learn Apache.  Should I install Lamp and filesever together or do I have to seperate them.  Secondly how lowend can this server be.  I am thinking bout the lowest level amd dual core chip and 2 gigs of memory, compared to my home desktop this is a dog.  I am trying to find the specs but I find minimums and I need to know real world needs.  I want to use this file server for my important projects and papers.  I want it as a secondary backup and dont need to run mirroring but would striping make a difference in speed.  It will be plugged into a router in my home, unless you guys say wireless is acceptable.
thanks in advance
Jb

Minimum specs for a little web/file server? I had an old Pentium 3 733mghz with 512 ram that was an awesome home server, until the motherboard went due to age. TI replaced it with [a amd duel core bare bones]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4387931&CatId=332") for $159 at tiger direct that is overkill imho. With a cooling fan and 200gb hd it was $215. I had a spare cdrom.

---

### Post by cariboo on 2009-01-25
I have an old eMachine 500Mhz cpu with 128MB ram, it works quite well for serving files and static web pages. If I upgraded the ram to 512MB it would probably server dynamic web pages quite well. Right now it is serving as an mp3 player, last time I checked (yesterday) it was still playing tunes, it's been running for about 2 weeks.

What you are planning to use, will allow you to host several web sites and serve files as well as streaming media at the same time, without even breathing hard. :)

Jim

---

### Post by Kilz on 2009-01-25
> **cariboo907 said:**
> I have an old eMachine 500Mhz cpu with 128MB ram, it works quite well for serving files and static web pages. If I upgraded the ram to 512MB it would probably server dynamic web pages quite well.

Jim

I like emachines. I have had a t1120 and a t6524 that are still in my family. 
Yes, 512 would let you run php and mysql. I ran a php based torrent tracker long ago on a 450mghz pentium 2 and had to bump the ram up to 512 because of performance issues. Once I did it was great. It even ran icewm pretty good when I started the desktop.
There are great uses for old equipment some people think of as junk. My daughter is in a small school that is operated by our church. I am the it department. The most modern computer is a pentium 4 2.40ghz, most are p3. xubuntu breathed new life.

---

### Post by paulisdead on 2009-01-25
> **indyspcguy said:**
> First off this is my first server setup for linux.  I have converted many M$ users to Ubuntu, but now I find myself needing cs4 and using MS.  I know I know dont kill me, school does come first.  I need to setup an inexpensive server for file storage.  I dont understand the Lamp servers.  I think it may be overkill but I do need to learn Apache.  Should I install Lamp and filesever together or do I have to seperate them.  Secondly how lowend can this server be.  I am thinking bout the lowest level amd dual core chip and 2 gigs of memory, compared to my home desktop this is a dog.  I am trying to find the specs but I find minimums and I need to know real world needs.  I want to use this file server for my important projects and papers.  I want it as a secondary backup and dont need to run mirroring but would striping make a difference in speed.  It will be plugged into a router in my home, unless you guys say wireless is acceptable.
thanks in advance
Jb

I would do mirroring if it's for any sort of a backup.  Even if you used a gigabit network, I'd doubt you'd see much difference in speeds.  Only reason I use RAID5 in my home file server is so that I can have 1 drive fail, and not lose data.  The striping would help if you were going to have a lot of users on it at the same time, but it doesn't sound like that's what you want to do.  RAID0 scares the crap out of me, you're doubling your odds of data loss.  If one of those drives dies, all your data is gone.

You should probably plug this guy into the router and not use wireless for it.  This way you'll get better transfer rates.   It just will better be able to serve up files using a good old fashioned wire.

---

### Post by indyspcguy on 2009-01-25
Thanks for all the info.  I had a friend tell me to run myth tv on it as well.  I am thinking about building my firt htpc.  This website is a life saver.  I dont know how intensive mythtv is going to be on it.  Basically the wife got wind of my desires and put me on a budget.  Wow what it means to be engaged and married.  Lol so now I am allowed one more machine maybe 2 but we are getting a new home entertainment system. So that leaves me with one in the bedroom and one in the new media room. I want the basics to be around the pc and tv.  Is this a pipe dream for one of the boxes to be a file server as well as being able to watch tv on it?

---

### Post by Kilz on 2009-01-25
> **indyspcguy said:**
> Thanks for all the info.  I had a friend tell me to run myth tv on it as well.  I am thinking about building my firt htpc.  This website is a life saver.  I dont know how intensive mythtv is going to be on it.  Basically the wife got wind of my desires and put me on a budget.  Wow what it means to be engaged and married.  Lol so now I am allowed one more machine maybe 2 but we are getting a new home entertainment system. So that leaves me with one in the bedroom and one in the new media room. I want the basics to be around the pc and tv.  Is this a pipe dream for one of the boxes to be a file server as well as being able to watch tv on it?

Be very careful what tv card you buy for mythvt. I was looking, [I am almost ready to buy this one]("http://pchdtv.com/") after [reading this]("http://www.mythtvtalk.com/forum/hardware/1688-hardware-works-well-mythtv.html").

---

### Post by indyspcguy on 2009-01-27
> **Kilz said:**
> Be very careful what tv card you buy for mythvt. I was looking, [I am almost ready to buy this one]("http://pchdtv.com/") after [reading this]("http://www.mythtvtalk.com/forum/hardware/1688-hardware-works-well-mythtv.html").
I am getting the asus eee pc one think it is called my cinema 3100 and it is usb.  I am planning on running this in a shuttle k45 with a dual core celeron or pentium dual core.  Im a amd fanboy, but for 90 bucks cant beat it and if i get one for each room i am spending less than I would for the first case I picked out and processor.  Will just be using it for file server and pvr.  Have a ps3 with yellow dog soon to be ubuntu for hd playback.  so nothing major.  Just dont want to kill the little system with runing to much on it.

---

### Post by indyspcguy on 2009-01-30
After reading decided to build 2 k45 machines will be easier to seperate them.
thanks for the information and decided to build just a file server headless unit without gui so this will be the biggest hill to climb for me
thanks again and I will keep everyone informed

---

