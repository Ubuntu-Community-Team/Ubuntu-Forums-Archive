---
title: "stablity?"
date: 2007-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by robstat on 2007-04-11
I'm having problems keeping ubuntu running , firstly I installed 6.10 and updated it and was fine until I tried to get my bcm43xx wifi card running on restart it wouldn't boot up in either normal or safe mode,so i formatted reinstalled and had the same problem. Then I installed 6.04 my mousepad was all over the place and it kept freezing so I installed 7.04 which ran fine untill I updated it now that won't boot . It does boot in safe mode to a command line but I have no idea what to do with it!
I have very little experience with linux, I ran redhat 9 a few years ago which was rock solid but I didn't do much work with it, I just used the web browser  so I didn't have to worry about viruses.
I want to learn to use linux as a replacement to windows but need some stability.
Any ideas why i'm getting so many problems?

---

### Post by Kilz on 2007-04-11
> **robstat said:**
> I'm having problems keeping ubuntu running , firstly I installed 6.10 and updated it and was fine until I tried to get my bcm43xx wifi card running on restart it wouldn't boot up in either normal or safe mode,so i formatted reinstalled and had the same problem. Then I installed 6.04 my mousepad was all over the place and it kept freezing so I installed 7.04 which ran fine untill I updated it now that won't boot . It does boot in safe mode to a command line but I have no idea what to do with it!
I have very little experience with linux, I ran redhat 9 a few years ago which was rock solid but I didn't do much work with it, I just used the web browser  so I didn't have to worry about viruses.
I want to learn to use linux as a replacement to windows but need some stability.
Any ideas why i'm getting so many problems?

What you are calling stability , is in reality setup. No matter the operating system , some setup needs to be done. On windows the computer manufacturers do it everything is pre installed and there is a restore disk that has a drive image with all the setup done. If you ever have to install windows from a Microsoft Windows install disk you would see what I mean.
On linux, no matter the version or distribution some setup needs to be done. A lot is now automatic. But there is always something that needs a little work. Thats why there is [documentation with a hardware setup section.]("https://help.ubuntu.com/community/")
It also appears you have learned another lesson. Versions in development (7.04 Feisty Fawn) Can break and will. Feisty is in Beta right now , and unless you know how to troubleshoot a broken Ubuntu its not recommended that you even install it.

---

### Post by Justin123 on 2007-04-11
I had a similar problem when i tried to install my wireless networking card from netgear.  Many times the problem has to do with the driver.  You may run into some trouble with that depending on the brand of your card.

---

### Post by robstat on 2007-04-11
I have installed 98 and xp off disc many times but I know driver and hardware are designed to be compatable so not alot of work needs to be done or at least i've never had to do alot. I know i'm at the bottom of a learning curve. But when the system won't boot how can I fix it?
Tonight I will reinstall edgy and see what happens I know conflicts with the broadcom bcm4310 wifi card are probably the main culprit.
Ubuntu looks a great os and I think once i've learned the basics will be very comfortable with it there must be a command that will search for conflicts so i can put them right one at a time?
also when in safe mode(not sure what it's called ) where do you start?

---

### Post by Kilz on 2007-04-11
> **robstat said:**
> I have installed 98 and xp off disc many times but I know driver and hardware are designed to be compatable so not alot of work needs to be done or at least i've never had to do alot. I know i'm at the bottom of a learning curve. But when the system won't boot how can I fix it?
Tonight I will reinstall edgy and see what happens I know conflicts with the broadcom bcm4310 wifi card are probably the main culprit.
Ubuntu looks a great os and I think once i've learned the basics will be very comfortable with it there must be a command that will search for conflicts so i can put them right one at a time?
also when in safe mode(not sure what it's called ) where do you start?

When you installed the win 98 and XP did you do it with a Genuine Microsoft Disk from Microsoft, or did you use a restore disk supplied from the computers manufacturer?

---

### Post by robstat on 2007-04-12
I'll put my hands up, I know linux is stable I just wanted to know why it wasn't for me! so it needs to setup where do I start first?
do i start with the lspci command and try to get them working one at a time?
Or is there something
It was with a genuine disks but I don't see how this is going to help get ubuntu running.

---

### Post by dabl on 2007-04-12
robstat, if you're going to reinstall the OS, I'll offer an observation that Feisty (7.04) Beta is more stable on my hardware today than 6.10 ever was.  My hardware is Intel Core 2 Extreme on Intel motherboard, Nvidia GeF 7900GS.  Feisty seems to like hardware better than Edgy -- for example, my USB webcam worked immediately in Feisty - in Edgy I had to make a special USB driver.

Just a thought for your consideration.  :)

---

### Post by robstat on 2007-04-12
thanks for the advice but i've already reinstalled 6.10 although I haven't tried to configure it yet. It's going to be about a week before i'm going to get time so I might wait for the official release of 7.04 which I think I read was out on the 19 april .

---

### Post by ronocdh on 2007-04-12
> **robstat said:**
> thanks for the advice but i've already reinstalled 6.10 although I haven't tried to configure it yet. It's going to be about a week before i'm going to get time so I might wait for the official release of 7.04 which I think I read was out on the 19 april .
You have the date correct, I of course I encourage you to try Feisty final when it's out!

Sorry for the rather harsh welcome you got here; I tend to agree with the sentiments expressed by others in this thread, specifically that **setup is required**. Getting into Linux can be tricky, which we all know. Microsoft has a such a huge marketshare not just because of their monopoly, but also because of the nature of the competition. *ducks* I mean, why does Apple have such an astronomical conversion rate, yet Linux is still largely ignored by the public?

I'm not saying it'll be this way forever, or even for much longer, but it **is** how things stand now. My friends don't jump at the change to use Linux and dump Microsoft because it is a difficult transition for some. You have to be a geek and you have to love fixing and breaking and fixing things. =)

That said, welcome aboard! Hopefull you'll find these boards very helpful in your quest for a usable system. ;)

---

### Post by robstat on 2007-04-12
I'm sorry to anyone that I may have offended I probably deserved a rough ride but I think my post was taken a little out of context.
I'll try 7.04 next week and see if it's more friendly with my hardware. I know that I have to learn how to setup the os but it's a big jump for someone who knows next to nothing.
thanks for the replies.

---

### Post by dabl on 2007-04-12
rob, if you're coming over from Windows. you might want to try Kubuntu 7.04.  It's a little more "familiar" to Windows exiles. Here's information comparing the Gnome desktop to KDE:

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

Here's the Kubuntu Forum where you get help:

[http://www.kubuntuforums.net/index.php](http://www.kubuntuforums.net/index.php)

:D

---

### Post by robstat on 2007-04-13
Thank's I've had a read on the links you've gave me , but I prefer the feel off ubuntu I've already had a look around and got used to the way it's set out. It's the command line where I'm getting stuck and I assume that is the same with both?

---

### Post by Kilz on 2007-04-13
> **robstat said:**
> Thank's I've had a read on the links you've gave me , but I prefer the feel off ubuntu I've already had a look around and got used to the way it's set out. It's the command line where I'm getting stuck and I assume that is the same with both?

A terminal is a terminal. KDE has one named Konsole, but it basically dose the same thing the Gnome terminal does.  It is also the same commands and way the commands are entered. Linux, regardless of the desktop used, requires command line use in a lot of situations.

---

