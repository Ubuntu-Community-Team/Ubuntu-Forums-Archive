---
title: "I need help with installing CSS!!"
date: 2008-03-25
forum: Wine
---

### Post by volksgewer on 2008-03-25
I would like to get Counter Strike Source and Half Life 2 Death Match to work on Linux.  Can anyone help me?

---

### Post by liorc666 on 2008-03-26
first you gotta have driect render :
run
```
glxinfo | grep direct
```

you should have "yes"

if so follow :
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=howto%20steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=howto%20steam)

i got it to work smooth and on very good graphic.
also Play On Linux
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)
could help you

---

### Post by volksgewer on 2008-03-26
I have been using the how to. But I just started with Linux and I have no idea what anything means. Is there an easier way to do this? Besides using Windows?

---

### Post by rcatman on 2008-04-15
I have just successfully played my first game of Half-Life 2. 

Install PlayOnLinux, then from that program you install Steam.

You open up Steam and download your games exactly the same as you would in Windows.

If you're wondering how exactly you install PlayOnLinux, here's a simple way.

Goto System->Administration->Software Sources

Goto the "Third Party Software" tab. Click "+Add ..." and enter "http://playonlinux.botux.net/ gutsy main" 

Press "Close", then it will update your sources. After that you can open a terminal and type "sudo apt-get install playonlinux". That will install playonlinux.

---

