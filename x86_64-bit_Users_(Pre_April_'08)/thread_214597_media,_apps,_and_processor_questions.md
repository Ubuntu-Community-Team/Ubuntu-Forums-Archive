---
title: "media, apps, and processor questions"
date: 2006-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by wazzie on 2006-07-12
first off, what do i need to do to make my system integrated. that is, how do i download or reconfigure this system to run media, like songs and movies. i have no clue how to run linux os, fedorra, so especially not ubuntu. but i figured i'd jump in deep. what apps are out there that i might be able to find for open network sharing? should i use the add applications parameter? so i have this amd64 processor, besides massive upstream what does it do for me?

---

### Post by Kilz on 2006-07-12
> **wazzie said:**
> first off, what do i need to do to make my system integrated. that is, how do i download or reconfigure this system to run media, like songs and movies. i have no clue how to run linux os, fedorra, so especially not ubuntu. but i figured i'd jump in deep. what apps are out there that i might be able to find for open network sharing? should i use the add applications parameter? so i have this amd64 processor, besides massive upstream what does it do for me?

Welcome to Ubuntu, running linux isnt that hard, as you will find out if you give it some time. Most applications are [installed]("http://www.monkeyblog.org/ubuntu/installing/") with Synaptic or apt. Synaptic can be found at System > Adminastration >Synaptic.
You will want to add the [multiverse and univers repositories]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") if you want media.
by network sharing do you mean peer to peer file sharing or setting up a home network?

---

### Post by wazzie on 2006-07-12
yeah, peer networks. and movies i mean wmv and mpegs. i found arts, but im not sure its running. how do you change totem from being the default player? i used the add apps thing, and went to advanced and searched but it came up empty handed. any applications you would suggest? do other linux based os's integrate easily? i think people like bill gates because he has one step solutions, i sure would like a way to two step around this.

---

### Post by Kilz on 2006-07-12
> **wazzie said:**
> yeah, peer networks. and movies i mean wmv and mpegs. i found arts, but im not sure its running. how do you change totem from being the default player? i used the add apps thing, and went to advanced and searched but it came up empty handed. any applications you would suggest? do other linux based os's integrate easily? i think people like bill gates because he has one step solutions, i sure would like a way to two step around this.

For wmv you are going to need 32bit mplayer. Here is a [link to a howto]("http://www.ubuntuforums.org/showthread.php?t=188974") to set it up. 
To change media from opening in totem, find a file of the media type. Right click on it, chose properties, click on opens with tab. click the circle next to what you want to open it, if it isnt there , click the add, then select the application from th application list. click close when done, from then on that media type will open with that program, until you change it.
You need to enable the multiverse and universe , then reload synaptic to fine more applications.
amule is a ed2k client, avaiable in syanaptic. Valknut is a direct connect client avalaible in syanptic, Gtk-Gnutella is a gnutella client.
Yes bill gates gives one step solutions, all from microsoft, some people have problems dealing with the amount of choices in linux.
All linux clients need some setup, just like an stand alone windows install needs lots of extras.

---

### Post by wazzie on 2006-07-13
so how do i get mplayer32 to load in firefox? it plays wmv, but firefox doesnt. how do i just set mplayer32 as default?

---

### Post by Kilz on 2006-07-13
> **wazzie said:**
> so how do i get mplayer32 to load in firefox? it plays wmv, but firefox doesnt. how do i just set mplayer32 as default?

I thought you had a wmv file on your desktop. Are you talking about wmv files embedded on web pages or ones you download to your desktop?

---

### Post by wazzie on 2006-07-13
formidably, both. desktop is working fine now, just need to integrate it into  firefox. how do i play mp3s?

---

### Post by Kilz on 2006-07-13
> **wazzie said:**
> formidably, both. desktop is working fine now, just need to integrate it into  firefox. how do i play mp3s?

The Mplayer you setup should play mp3's if nothing else will. If you might want to look at my [32bit firefox howto]("http://www.ubuntuforums.org/showthread.php?p=1174435") if you want the mplayer plugin for embedded media.

---

### Post by wazzie on 2006-07-14
i actually went with beep media, it seems to be bundled. thank you both for your help, one last question. it won't let me mk dir. i think thats why the sudo script earlier didn't work. i remember when i had ubuntu 5.10 i had to put in a chmod code or something to grant the user admin creation priviliges with folders. whats that code? could this be why im having problems with the mplayer app?

---

### Post by Kilz on 2006-07-14
> **wazzie said:**
> i actually went with beep media, it seems to be bundled. thank you both for your help, one last question. it won't let me mk dir. i think thats why the sudo script earlier didn't work. i remember when i had ubuntu 5.10 i had to put in a chmod code or something to grant the user admin creation priviliges with folders. whats that code? could this be why im having problems with the mplayer app?

Running a script with sudo is like running it with root. Root has permission to make any directory. But if you want to make sure type in 
```
sudo mkdir /path/to/DircetoryName
```
to make a directory.

---

### Post by wazzie on 2006-07-15
how do i make the user have root access at all times without sudo, beyond mkdir? i distinctly remember doing that before, just no clue how.

---

### Post by Kilz on 2006-07-15
> **wazzie said:**
> how do i make the user have root access at all times without sudo, beyond mkdir? i distinctly remember doing that before, just no clue how.
You can use 
```
gksudo nautilus
```
to launch the file browser as root. Root login is disabled in Ubuntu. Its not recommended for users to have root access all the time because it is a security risk. It is also possible to do great harm without thinking about it. IMHO its why windoz is so bad, everyone runs as root.

---

