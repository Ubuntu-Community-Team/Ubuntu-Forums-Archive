---
title: "Video thumbnails and updates?"
date: 2008-02-03
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 67GTA on 2008-02-03
I have two more questions. I tried to install the libxine-arts package to get Konq to show video thumbnails. I keep getting an error saying it could not be found in the pacman repo. Is this a bug, or am I missing something? Also I installed smart for the fun of it. After adding the channels that Yast had, smart tols me there were about 100 updates. It wanted to downgrade my kernel to install updates???
I'm not sure what is going on there. Yast says I'm up to date when I use the online update. If I go to the software installer and choose to update everything that has a newer version, it shows several updates, but gives a lot of dependency problems.

Can I trust Smart's updates?
What is the difference between online update and the software update?
What do I need to get video thumbnails to show?

---

### Post by 67GTA on 2008-02-04
I finally got libxine-arts to install, but it didn't help. I installed mplayerthumbs, and it is showing video thumbnails now. 

The only other thing left to figure out is the updates. Correct me if I'm wrong, but if I go to SYSTEM>INSTALL SOFTWARE, and then choose the package tab>update all software if there is a newer version, that will basically update me to Factory(beta) right? I don't want to do that if that will be the outcome. If I just use the online update in Yast, that should keep me up to date with the 10.3 repos??? I really don't trust the Smart update proposals. It seemed to be using a couple of different repos than Yast.

---

### Post by Incense on 2008-02-05
67GTA, it looks like they answered this for you in the SUSE forums, but I thought I'd post it here as well. I tried out this solution and it worked for video thumbs in konq. You just need to install the package below.

Kdemultimedia3-video-xine

---

### Post by 67GTA on 2008-02-05
I'm not receiving notifications from the suse forum for some reason. I didn't know someone had posted another reply. That worked perfectly. I am still trying to get used to the package differences between Opensuse and Ubuntu. I think this could replace Kubuntu.

---

### Post by Incense on 2008-02-05
> **67GTA said:**
> I'm not receiving notifications from the suse forum for some reason. I didn't know someone had posted another reply. That worked perfectly. I am still trying to get used to the package differences between Opensuse and Ubuntu. I think this could replace Kubuntu.

The forums over there work a bit differently. You have to actively subscribe to the thread, you are not automatically opted in when you reply like you are here. That's why I posted the response here, just to make sure you got it. :)

---

### Post by 67GTA on 2008-02-05
Gotcha:wink:

---

