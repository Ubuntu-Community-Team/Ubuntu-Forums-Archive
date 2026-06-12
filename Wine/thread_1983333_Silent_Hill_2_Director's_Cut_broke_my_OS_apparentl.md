---
title: "Silent Hill 2: Director's Cut broke my OS apparently"
date: 2012-05-20
forum: Wine
---

### Post by gurokko on 2012-05-20
Hi, all.  I'm posting this from a live disk because, as of the moment, my Ubuntu 12.04 install refuses to boot.  I'm not... entirely sure why.  I was playing Silent Hill 2: DX through wine, and it suddenly came up with an error informing me that wine had crashed.  I attempted to close out of wine, and my computer froze completely on a black screen.  When I shut it off and then attempted to boot it back up, it refused to boot, no matter what I did, and I'm beginning to lose my patience with it.  I was running wine 1.4 on Ubuntu 12.04.  The game had been running perfectly for over two hours previously, so I'm not entirely sure what could have happened.

Does anyone have any idea...?  If it's any help, the crash happened immediately at the beginning of a cutscene-- for those who are familiar with the game, the scene when you first meet Eddie in the bathroom.  And after the crash, the scene continued to play, but the sound caught and skipped until I quit wine and the game.

---

### Post by coffeecat on 2012-05-20
There are two issues here. The first, that wine crashed and the system froze. The second that you cannot now reboot. The two may or may not be directly related. System freezes after application crashes happen occasionally. You may never discover what the underlying problem was, but perhaps others with more experience of this game in wine may be able to comment. But this is what concerns me:

> **gurokko said:**
> When I shut it off and then attempted to boot it back up, it refused to boot, no matter what I did, and I'm beginning to lose my patience with it.

Did you have to do a hard reset? A hard shutdown can result in filesystem corruption and that could possibly be the cause of not being able to boot now. As an aside, if you ever get a system freeze again, try to shut down gracefully with the magic key sequence:

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)

Boot up with an Ubuntu live CD, choose "try Ubuntu" to get to the live desktop and then open Gparted. Right-click on your Ubuntu root partition and choose "check". This will perform a filesystem check and attempt to repair it if errors are found..

---

### Post by gurokko on 2012-05-20
Yes, that's what I ended up having to do, unfortunately.  Thanks for the suggestion, I'll give that a try and see what happens.  Hopefully it'll be something fixable, because I'd really rather not have to start over if I don't actually have to... if this were the first time this happened, it wouldn't have been so frustrating, but it's done this before, when I first upgraded to 12.04.  I ended up having to do an entirely fresh install from the 12.04 disk.  :/

---

### Post by gurokko on 2012-05-20
Sorry for the double post, but I wanted to let you know that I checked the root partition in gparted and apparently there was some damage there, and I'm able to boot up my OS now!  Thank you so much, and sorry for not even realizing such an obvious solution.  I guess I'm still learning my way around this whole linux thing.  Such is my fate for using windows for way too long.  :|

---

### Post by coffeecat on 2012-05-20
I'm glad to hear your system was repairable. Good luck and don't forget to bookmark the Wikipedia magic key page. You never know when you might need it! :wink:

---

### Post by gurokko on 2012-05-20
Thank you, and I will definitely do that.  I'm also going to make a new partition on my hard drive and I might try dual-booting with some other linux-based OSs to see if something else plays more nicely with my usage habits, but, for tonight, you are my hero, haha!  Thanks again.

---

### Post by cogadh on 2012-05-20
Just a FYI, system crashes like that are not caused by Wine, but rather it is Wine exposing some other, deeper problem with your OS. Most often, it is actually some kind of driver conflict/problem, not directly related to Wine at all.

---

### Post by gurokko on 2012-05-21
> **cogadh said:**
> Just a FYI, system crashes like that are not caused by Wine, but rather it is Wine exposing some other, deeper problem with your OS. Most often, it is actually some kind of driver conflict/problem, not directly related to Wine at all.

Ah, that makes sense.  I'll have to try and figure out where the problem lies... I'm not terribly experienced with troubleshooting in linux yet, but thank you for the information!

---

### Post by Shadowstripe on 2012-05-22
if it happens again the closest thing to a ctrl+alt+del on windows is ctrl + alt + F1

login and type "sudo killall sh2pc.exe" or whatever the running programe is called (and it is case sensitive to the case used with wine to launch it afaik and ctrl + alt + f7 to get back to your desktop :)

it has worked for me before

---

### Post by cogadh on 2012-05-22
> **Shadowstripe said:**
> if it happens again the closest thing to a ctrl+alt+del on windows is ctrl + alt + F1

login and type "sudo killall sh2pc.exe" or whatever the running programe is called (and it is case sensitive to the case used with wine to launch it afaik and ctrl + alt + f7 to get back to your desktop :)

it has worked for me before
The command "wineserver -k" should work just as well for killing any and all Wine-based applications.

---

