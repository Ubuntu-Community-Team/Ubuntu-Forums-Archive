---
title: "KMess - forcing architecture"
date: 2007-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by aimran on 2007-05-11
Hi guys! I want to use KMess but of course the latest version is only available to 32bit machines. Now I may install the 32 bit version by forcing the architecture as in this thread [http://ubuntuforums.org/showthread.php?t=439339](http://ubuntuforums.org/showthread.php?t=439339) but they don't have a .deb file there :(

What they have is the source. Could I or should I build from source, then get a .deb file? How would I build from source then? :|

---

### Post by ronacc on 2007-05-11
building from source is not hard , but it can be a bit frustrating the first few times you do it . first download the source file  and extract it somewhere , I have a seperate directory for builds. go to the dir that you extracted and look at any readme's or txt files fo special instructions and or a dependency list ( also look on the site where you got the source for a dependency list and install all dependencies with either apt-get or synaptic. then in the dir you extracted run ./configure and see what happens , if it errors out because it can't find a file install that file and repeat( thats where the frustration comes in) note if the file is already installed install the "file".dev building from source wnats a lot of .dev files. after ./configure compleates run make and then sudo make install . you do not need to build a .deb if you are only going to install it on one machine . got to go , if you have questions ask I'll check back later.

---

### Post by aimran on 2007-05-11
Hey man thanks for starter tip :) complete newbie here haha.

Anyways ran into an error during ./configure :

checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!

It says in the readme that I have to install the qt-devel or qt3-devel package but checking synaptic gives me similiar packages but not the exact ones.

I wonder which ones to install in this case. Otherwise I think I almost could go to the next step which is "make".

Thanks :)

---

### Post by aimran on 2007-05-11
Oh well I solved the problem and have kmess running :)

Thanks for the help!

---

### Post by ronacc on 2007-05-11
I'm glad you got it going. See youre learning linux ;) . One more tip, keep the dir you built the program in around incase you need to uninstall for some reason , since you built the prg yourself you won't be able to uninstall with synaptic . instead just go to the dir where you ran make install and run make uninstall.

---

### Post by aimran on 2007-05-11
Think I'll uninstall it before I forget where I kept the files ;) 

Not enjoying kmess hehe :)

Anyways thanks again!

---

### Post by kuja on 2007-05-14
I know you've solved it already, but this is where apt comes in very handy - "sudo apt-get build-dep kmess" ... this should work for fetching/installing build-dependencies in a lot of scenarios :)
(saves a lot of frustration!)

---

