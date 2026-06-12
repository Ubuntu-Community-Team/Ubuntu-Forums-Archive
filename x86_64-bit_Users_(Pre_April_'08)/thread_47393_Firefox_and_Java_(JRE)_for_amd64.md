---
title: "Firefox and Java (JRE) for amd64"
date: 2005-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by optikshell on 2005-07-08
I've been fighting with firefox and java for the past day or 2.  I've got the newest version of java installed for everything but my browser plugin.  For the firefox plugin, I'm using Blackdown's ( [LINK](http://www.blackdown.org/java-linux/java-linux-d2.html) ) build... its not the newest.  

Anyway, when I try to access a site that uses Java (yahoo games for instance), firefox crashes (closes all instances of firefox).  I ran it from the terminal to see if it spit out any errors... all I got was "Segmentation Fault."  

Anyone have a work around, or am I just out of luck?

---

### Post by tszanon on 2005-07-08
Are you sure that it's a 64 bit plugin? If it's 32-bit, it might be the cause for the Segmentation fault. 

It's just a possibility...I tried, but couldn't access those links to check it myself.

SUN hasn't released a 64 bit version of the plugin...it doesn't mean no one else can do it, but it might mean that no one has a really stable version yet.

What I did was using chroot, as explained in [http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575). It's not exactly what people want to hear, but it works.

---

### Post by NickB on 2005-07-08
I never got the 64-bit blackdown plugin to work, either.  I ended up having to go to a chrooted setup for such things.

Nick

---

### Post by optikshell on 2005-07-10
Thanks for the replies...  I guess we're just out of luck for a 64bit JRE release from Sun.  :(

---

### Post by WMCoolmon on 2005-07-10
I'm using the 640bit blackdown plugin and it works fine. I just downloaded the blackdown JRE file, IIRC, and followed the install instructions.

---

### Post by jon_gunnar on 2005-07-11
[QUOTE=optikshell]I've been fighting with firefox and java for the past day or 2.  I've got the newest version of java installed for everything but my browser plugin.  For the firefox plugin, I'm using Blackdown's ( [LINK](http://www.blackdown.org/java-linux/java-linux-d2.html) ) build... its not the newest.  

Anyway, when I try to access a site that uses Java (yahoo games for instance), firefox crashes (closes all instances of firefox).  I ran it from the terminal to see if it spit out any errors... all I got was "Segmentation Fault."  

Anyone have a work around, or am I just out of luck?[/QUOTE]

I know that the people at Azureus got a Java JRE Torrents 1.5.0_04 for Linux amd64. If this jre contains the plugin it may be an option?
[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

--As an update. This just gave me a chrash and no more---

---

### Post by kao on 2005-08-07
afaik, only sun's jre 1.5 is available, but it has no java plugin

---

### Post by Vermyndax on 2005-09-10
I fixed it by installing the libXp6 package in Synaptic.  Another Java application I use was crashing when looking for this file.  I installed it and all of my Blackdown Java plugins in Firefox went away.

---

### Post by oak on 2005-09-27
Hi, I really hope someone's still reading this thread so I don't have to start a new one.

Help!

Ok, can anyone offer good instructions on how to install the Blackdown java?
I've attempted the instructions (exactly to the letter, 3 times) from the wiki at [https://wiki.ubuntu.com/JavaAMD64](https://wiki.ubuntu.com/JavaAMD64)
Nothing. I wish I could say it crashed firefox, however just ... nothing. I used the "method 1" because when I attempt "apt-get install fakeroot javapackage" (or the alternate: apt-get install fakeroot java-package) I get the message: "E: Couldn't find package java-package" or "E: Couldn't find package javapackage".

I can only think that maybe the symbolic links suggested in the wiki are no longer valid? perhaps I need to create the links in different dirs?

It'd be much appreciated if anyone has any suggestions

Cheers,
Oak

---

### Post by cychem1 on 2005-09-28
Check out Tamir's excellent repository;

[http://ubuntuforums.org/showthread.php?t=48905](http://ubuntuforums.org/showthread.php?t=48905)

---

### Post by oak on 2005-09-28
thanks cychem - found a reference to it in another thread about amd64 apps... and after a bit of fiddling did get the new repositories up and running, installed blackdown (which happily shows up in the firefox about plugins now) but still no joy :(
Have read many threads now and tried most solutions, including removing and reinstalling the components, installing (hope I remember right) libxp6 & java-common. So have made headway: it's showing up as an installed plugin (thanks to the deb from the repository), it no longer throws pages of errors (thanks to the lixp6 install) and now we're down to trying to work out why it seg faults every time it encounters an actual java applet on a page.

Will keep trawling threads .. may be an answer somewhere (certainly enough with people claiming the same problem :))

Oak

---

### Post by cychem1 on 2005-09-29
Try 
sudo ln -s /usr/lib/j2re1.4-blackdown/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib64/mozilla-firefox/plugins/
to create symbolic link after install of blackdown Java 1.4 must be a link to work

---

### Post by oak on 2005-10-02
Thanks, have tried (again) creating a sym link, just in case something was off the first time... anyway, still no luck. The blackdown plugin still shows up as available from within firefox, however any time a java applet is loaded firefox exits with a seg fault when the applet goes to run.

---

### Post by greenfrog on 2005-10-02
What happened to jre on Tamir's site, I could not fine it?

---

### Post by greenfrog on 2005-10-03
How do I install packages on tamir?

I am looking to install j2rel 5.1.5

Thanks

---

### Post by DancingSun on 2005-10-03
[QUOTE=greenfrog]How do I install packages on tamir?
I am looking to install j2rel 5.1.5
Thanks[/QUOTE]
After you added the repository to sources.list, search for "j2re" in Synaptic.

---

### Post by greenfrog on 2005-10-03
[QUOTE=DancingSun]After you added the repository to sources.list, search for "j2re" in Synaptic.[/QUOTE]

Ok, installed it, but OpenOffice Base still do es not fine jre it needs to run.

Any idea why not?

I installed jre v1.4 and v1.5

Thanks:???:

---

### Post by DancingSun on 2005-10-04
[QUOTE=greenfrog]Ok, installed it, but OpenOffice Base still do es not fine jre it needs to run.
Any idea why not?
I installed jre v1.4 and v1.5
Thanks:???:[/QUOTE]
You're using OpenOffice2?  Since OpenOffice doesn't have a native 64-bit version, I'm guessing it might be looking for a 32-bit Java VM.  Try searching for this issue on the forums and the web.

---

### Post by daniel49 on 2005-10-06
I decided 64 bit was too much of a headache but when I tried to add the extra repos to the 32 bit I had before java was no longer there in the back ports since sept I believe they took it out,

found this page and followed instructions and it worked exactly as they said.
I noticed they also had a link for 64bit there can't vouch for it.

[http://blog.agileware.net/index.php/archives/2005/09/30/how-to-install-java-on-ubuntu-linux/](http://blog.agileware.net/index.php/archives/2005/09/30/how-to-install-java-on-ubuntu-linux/)

Now will have to dig up the libraries for playing dvd again those are gone as well.

---

