---
title: "just can't get 64-bit java working.  Please help!"
date: 2009-02-06
forum: x86 64-bit Users
---

### Post by quixote on 2009-02-06
I've been at this for two days now, and just can't get Firefox to see the plugin.  I'm running FF3.1b2 under Intrepid (all 64-bit).  I've tried both sun- java 1.6.0_10 and 1.6.0_12, together with the new beta 64-bit plugin.  I've used "sudo update-alternatives --set java /usr/lib/jvm/java-6-sun/bin/java" (I also installed it under /opt once, following [http://ubuntuforums.org/showthread.php?t=1011899](http://ubuntuforums.org/showthread.php?t=1011899)  I've put links to libnpjp2.so in every conceivable plugins dir.   I restart FF, sometimes I restart the whole system.  But no matter what I do, FF refuses to show anything java-esque in about: plugins or to run any java content.  The only thing there is libflashplayer.so

[http://browserspy.dk/java.php](http://browserspy.dk/java.php) says java is "not installed or doesn't work."  (Too true)

java -version results in:
```
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)
```
sudo update-alternatives --config java doesn't see the 1.6.0_12 version which is in another subdir of /usr/lib/jvm

This has me tearing my hair out.  Could some kind soul write out a step by step, starting with how I should purge all the old stuff off my system?  I must be missing something really stupid and obvious, but I'm damned if I can figure it out.

---

### Post by saransh1987 on 2009-02-06
hey i am also having the same kind of problem. i am also a novice and do not know how to do it...

but i am not able to run java on firefox. my firefox browser crashes whenever i try to run java for sailearningportal.skillport.com website.

the answer to the above problem might help me in my problem also.

---

### Post by empty_tank on 2009-02-07
I have followed the tutorial on [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

This has helped me install 64-bit java working.

There is new java update: jre-6u12-linux-x64.bin 

I downloaded it at my desktop from [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jre-6u12-oth-JPR@CDS-CDS_Developer](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jre-6u12-oth-JPR@CDS-CDS_Developer)

Follow the tutorial using terminal:
------------

cd /opt

sudo mkdir java

cd java

sudo mkdir 64

sudo mv ~/Desktop/jre-6u12-linux-x64.bin /opt/java/64

sudo chmod 755 /opt/java/64/jre-6u12-linux-x64.bin

cd /opt/java/64

sudo ./jre-6u12-linux-x64.bin

sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.6.0_12/bin/java" 1

sudo update-alternatives --set java /opt/java/64/jre1.6.0_12/bin/java

-----------------

Following the last command, you should be reading:
"Using '/opt/java/64/jre1.6.0_12/bin/java' to provide 'java'."

To install the plugin using terminal:

----------------

mkdir ~/.mozilla/plugins
ln -s /opt/java/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

----------------------

To remove previous plugins based from [http://tldr.me/blog/2009/02/03/java-6-update-12-for-linux-amd64-howto/:](http://tldr.me/blog/2009/02/03/java-6-update-12-for-linux-amd64-howto/:)

-------------

sudo apt-get -y purge icedtea6-plugin
sudo rm -f /usr/lib/firefox-addons/plugins/libnpjp2.so
sudo rm -f /usr/lib/firefox-addons/plugins/libjavaplugin_oji.so
sudo rm -f /usr/lib/mozilla/plugins/libnpjp2.so
sudo rm -f /usr/lib/mozilla/plugins/libjavaplugin_oji.so

------------

I hope this helps.

---

### Post by quixote on 2009-02-07
This is really embarrassing.  I had FF3.1b2 installed in my old home dir.  when I moved to my new laptop and the 64-bit Intrepid, I copied /home to its partition.  . . . So I've been using the 32-bit Firefox and totally forgot about that.  No wonder the 64-bit plugin didn't show up. :redface: :redface: :redface:

When I try it with the 64-bit FF 3.0.5 that came with the install, libnpjp2.so is right there in plugins, and java does work.  Sort of.  Every time I try to use it, there seems to be about a 75% chance the whole browser will crash.

But that's another issue.

I'll reinstall using your nice, detailed steps, empty_tank, and see whether that fixes some of the mess I've made!

(saransh1987: all this only applies to the **64-bit** versions.  If you have a 32-bit install (the one you'd get if you didn't make any special choices when you downloaded Ubuntu) then it's much simpler.  The most complete instructions I've seen to get all the multimedia working are here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) Be sure you choose the set of instructions that apply to your particular setup.  It's a long list!)

---

