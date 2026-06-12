---
title: "A few errors... Okay, 5 errors..."
date: 2006-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Miki01 on 2006-07-03
Alright. Well, I'm not sure whether I'm supposed to post this thread in 64-bit or in General, but since I'm running amd64 based, I guess it would be more beneficial in here, since some things may work on 32-bit but not work on 64-bit. So lets get started.

**Problem 1: [COLOR="Red"]- Fixed by XioNoX[/COLOR]**
Whenever I boot up my computer, a window pops up with an error saying:

> The NetworkManager applet could not find some required resources. It cannot continue.

This message appeared after the first boot after I installed Automatix and ran it. When I ran automatix, I kept getting problems about some java.sun thing. Something saying that I needed to download one of the archives: 

jdk-1_5_0-doc.zip      jdk-1_5_0-ja.zip

And that I was told to goto this website to download them:

[http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

I downloaded it already, but, don't know how to install it...

Attached image #1 relates to this problem.

**Problem 2: [COLOR="Red"]- Fixed by Kilz[/COLOR]**
Now I am trying to move some of my files/documents from my old Windows XP computer into this one,. Whenever I insert a disc into my drive and then open it up from the desktop, it looks like this (attached image #2) What's causing this problem? When I insert the disc back into my other PC running XP, its fine. What I do is right-click on the CD icon on the desktop and goto Eject. Once the CD is ejected, I press the eject button on my CD drive to bring the disc back in. At this point, I can see the correct names and icons in the disc. But when I try to drag and drop a file from the CD to my dekstop (or anywhere, for that matter, it keeps bringing up an "I/O Error" (attached image #3) . I don't know what all this means...

**Problem 3: [COLOR="Red"]- Fixed by Kilz[/COLOR]**
Now, when I'm in the Synaptic Package Manager, as I'm applying the settings I chose, I error. This one is about the Sun-Java5-doc. It read:

> The following problems were found on your system:

E: sun-java5-doc: subprocess post-installation script return error exit status 1

I'm not sure what it means. Does it mean that I need to install that Java Sun thing? (attached image #4)

**Problem 4: [COLOR="Red"]- Fixed by Kilz[/COLOR]**
This one again has to do with that Java-Sun thing. When I tried to install that update for xserver-xorg-input... etc whatever it was called, I errored with another of those Java-Sun things. It looked quite similar to when I was going through installations of programs/etc in Automatix. (attached image #5). I guess I do need to install it. Can anyone help me with the installation?

**Problem 5: [COLOR="Red"]- Fixed? New problem below![/COLOR]**
This problem is regarding media. When I'm using XMMS and listening to music, lets say I pause it. Go on to some website with other media, ie. my MySpace profile which has music playing in the background. Most of the time my firefox browser just, out of the blue, closes and disappears. Sometimes, if I'm on another site with background music, an error on XMMS saying that something is taking hold of my soundcard not allowing my music to continue playing. I don't know how this problem started, but I don't have a soundcard, I'm using integrated sound. Would anyone know what the problem is?

[COLOR="Red"]**EDIT: Well, the problem doesn't seem to be appearing anymore. The new problem is that when I try to view a flash movie on the net it plays as if it was in fast forward...**[/COLOR]

Sorry for the long post, but I thought it would be more conservative if it were in one thread rather than 5 individual ones.

---

### Post by Kilz on 2006-07-03
[QUOTE=Miki01]Alright. Well, I'm not sure whether I'm supposed to post this thread in 64-bit or in General, but since I'm running amd64 based, I guess it would be more beneficial in here, since some things may work on 32-bit but not work on 64-bit. So lets get started.

**Problem 1:**
Whenever I boot up my computer, a window pops up with an error saying:



This message appeared after the first boot after I installed Automatix and ran it. When I 

Now, when I'm in the Synaptic Package Manager, as I'm applying the settings I chose, I error. This one is about the Sun-Java5-doc. It read:



I'm not sure what it means. Does it mean that I need to install that Java Sun thing? (attached image #4)

**Problem 4:**
This one again has to do with that Java-Sun thing. When I tried to install that update for xserver-xorg-input... etc whatever it was called, I errored with another of those Java-Sun things. It looked quite similar to when I was going through installations of programs/etc in Automatix. (attached image #5). I guess I do need to install it. Can anyone help me with the installation?

**Problem 5:**
This problem is regarding media. When I'm using XMMS and listening to music, lets say I pause it. Go on to some website with other media, ie. my MySpace profile which has music playing in the background. Most of the time my firefox browser just, out of the blue, closes and disappears. Sometimes, if I'm on another site with background music, an error on XMMS saying that something is taking hold of my soundcard not allowing my music to continue playing. I don't know how this problem started, but I don't have a soundcard, I'm using integrated sound. Would anyone know what the problem is?

Sorry for the long post, but I thought it would be more conservative if it were in one thread rather than 5 individual ones.[/QUOTE]

Hi Miki 
Welcome to the wonderful world of 64bit Ubuntu. :D  Lets see if I can help. First off automatrix is a good tool, but I think the 64bit version may have some bugs in it. Im not sure if it has an undo feature.
Lets start with java. It looks like it tried to install java 5. I would open up synaptic , do a search for sun-java5, and remove those packages. or use this from automatrix removal page
```
sudo apt-get remove sun-j2re1.5
```
If that doesnt work try
```
sudo apt-get remove sun-java5*
```
Next I recommend it be replace by Blackdown java. Do a search for Blackdown, and install j2re1.4 or use the command 
```
sudo apt-get install j2re1.4
```
Restart and see if you still get errors

---

### Post by Miki01 on 2006-07-03
Hmm, well, for the first part, I tried your first code, it didn't work, so I tried the second one. This was what I got:

> miki@Ubuntu:~$ sudo apt-get remove sun-j2rel.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2rel.5
miki@Ubuntu:~$ sudo apt-get remove sun-java5*
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

EDIT: Okay, now its removing!

Now I tried your 3rd code and I get:

> miki@Ubuntu:~$ sudo apt-get install j2rel.4
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package j2rel.4

EDIT: Okay, I can't read... I typed an "l" instead of "1"... Now I get:

> miki@Ubuntu:~$ sudo apt-get install j2re1.4
Reading package lists... Done
Building dependency tree... Done
j2re1.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by Miki01 on 2006-07-03
Okay, I've just restarted, but I still get the NetworkManager error. I'm going to try to install something in synaptic manager to see if I get any errors from that.

---

### Post by Miki01 on 2006-07-03
Okay, well, when I try to view .SWF flash clips on the net, they play like they're on fast-forward... I don't get that sun-java problem anymore, but my other problems still persist.

---

### Post by Kilz on 2006-07-03
[QUOTE=Miki01]Okay, well, when I try to view .SWF flash clips on the net, they play like they're on fast-forward... I don't get that sun-java problem anymore, but my other problems still persist.[/QUOTE]
I took a loot at the automatrix post, and looked at what it installes again. I found this
**24) Installs ndisgtk (WiFi configurator Graphical user interface) and Network Manager for Gnome/KDE - BD (386 only)** 
Is it possible that you installed the i386 version by mistake?
Anyway the ndisgtk Network manager is for a wireless network, are you on a wireless network? If not lets see if we can get rid of another problem :D Try this
```
sudo apt-get remove ndisgtk
```
To avoid typos, you can copy the command then use ctrl + Insert to paste it into the termnial. Once its done removing it reboot and see if the Network manager error is gone.

---

### Post by Miki01 on 2006-07-03
Okay, I just rebooted... But the network manager error is still there... I'm on a wired network, so what seems to be the problem...?

---

### Post by Kilz on 2006-07-03
[QUOTE=Miki01]Okay, I just rebooted... But the network manager error is still there... I'm on a wired network, so what seems to be the problem...?[/QUOTE]
This is a little out of my field of knowlage, but lets see if we cant get rid of the error. Open up  System > Adminastration > Networking and tell me how many interfaces you see listed. You might see a modem and your network card. Do you see anything else, maybe with a red X on it?

---

### Post by Miki01 on 2006-07-03
Okay, I see four interfaces. Two ethernets, a wirless and a modem. The wirless and the modem have the red X on them.

Oh, yeah, I forgot to say, thanks for the help ^_^

---

### Post by XioNoX on 2006-07-03
"sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/"
for fix the NetworkManager bug

---

### Post by Miki01 on 2006-07-03
Ah, thanks XioNoX, that fixed it :) Now... How to go about fixing those other problems...

---

### Post by Miki01 on 2006-07-03
Ah, thanks XioNoX, that fixed it  Now... How to go about fixing those other problems...

New problem: 
When I go to AnandTech's website and click on "My AnandTech" my firefox browser just disappears! Does anyone have a clue on this?

And also, as I edited on the first post in the thread, this problem:

> Well, the problem doesn't seem to be appearing anymore. The new problem is that when I try to view a flash movie on the net it plays as if it was in fast forward...

[SIZE="5"][COLOR="Red"]EDIT[/COLOR][/SIZE]
[COLOR="Red"]All the problems have been taken care of. I even went through the installation of Firefox32 w/ Flash and Java! ^_^[/COLOR]

---

### Post by Kilz on 2006-07-04
[QUOTE=Miki01]Ah, thanks XioNoX, that fixed it  Now... How to go about fixing those other problems...

New problem: 
When I go to AnandTech's website and click on "My AnandTech" my firefox browser just disappears! Does anyone have a clue on this?

And also, as I edited on the first post in the thread, this problem:



[SIZE="5"][COLOR="Red"]EDIT[/COLOR][/SIZE]
[COLOR="Red"]All the problems have been taken care of. I even went through the installation of Firefox32 w/ Flash and Java! ^_^[/COLOR][/QUOTE]
Thats great! I hope everything works for you. Just to let you know I did some updating to my howto today for Firefox32 if thats the one you used. I fixed the graphics on external programs that automaticly open up files you download.

---

### Post by Miki01 on 2006-07-04
Hey, thanks a lot. I checked yours, it looks a lot like the one I used. I think the one I used may even have been a clone of yours! :P

---

### Post by Kilz on 2006-07-05
[QUOTE=Miki01]Hey, thanks a lot. I checked yours, it looks a lot like the one I used. I think the one I used may even have been a clone of yours! :P[/QUOTE]
No you probably used the orignal one made for Breezy. But the document team deleted the  orignal before so I made one and updated it and added a lot of fixes for common problems. It looks like someone has replaced it. But the document team will probably delete it again soon.

---

### Post by Miki01 on 2006-07-05
Ah, okay okay! ^_^ Now I just gotta fix another problem that arose >_<

Its over here if you want to check it out for yourself... Its the one you solved already (with one of your codes, don't know which though... But it came up again... And then some... Well anyway, here it is: [http://www.ubuntuforums.org/showthread.php?p=1215166#post1215166](http://www.ubuntuforums.org/showthread.php?p=1215166#post1215166)

---

