---
title: "State of KU64"
date: 2005-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by gmcauley on 2005-12-20
I want to try Ubuntu and am debating whether to install 64 or 32 bit Kubuntu on my machine.

I am wondering how stable is 64 for: Eclipse, Netbeans, Java Studio Creator, Oxygen, Evolution, Firefox (and plugins, e.g., Java plugin, PDF), KDE in general, PDF reading, OpenOffice, CD Burning, USB (e.g., memmory stick), video drivers, audio, and everything else ... :D 

I've had some problems in the past, but I trust 64 is improving.  Any experiences (good and bad), and advice would be appreciated.

Should I go for 64 now or 32 now and 64 later?

---

### Post by arjaybe on 2005-12-20
I'm using Kubuntu 64-bit and find it very stable, but I hear it's quite a lot of work to get some things working, like Java and Flash for instance.  I can't tell you about most of the apps you mentioned, but Firefox, OpenOffice, K3B work fine for me.  Most of the comments indicate that there's no speed advantage to using 64-bit and that you might as well use 32-bit and save yourself some work.  Or you could cut two partitions and install them both.-)

---

### Post by Gowator on 2005-12-21
[QUOTE=arjaybe]I'm using Kubuntu 64-bit and find it very stable, but I hear it's quite a lot of work to get some things working, like Java and Flash for instance.  I can't tell you about most of the apps you mentioned, but Firefox, OpenOffice, K3B work fine for me.  Most of the comments indicate that there's no speed advantage to using 64-bit and that you might as well use 32-bit and save yourself some work.  Or you could cut two partitions and install them both.-)[/QUOTE]
When you say firefox does that include plugins?

---

### Post by arjaybe on 2005-12-21
[QUOTE=Gowator]When you say firefox does that include plugins?[/QUOTE]

I've got some plugins installed in firefox - vlc, mplayer - but I don't think they're doing the job.  I can listen to a radio station but I can't see some videos.  As I said, Firefox is working fine for me.  Might not be good enough for someone else.

---

### Post by Gowator on 2005-12-22
Hmm, this is what killed me.  I have to use the internbet for work and if I can't see sites then I don't knopw what Im missing... (90% of the ime its nothing but ...)

---

### Post by BoBr on 2005-12-23
There is no Sun Microsystems Java 64bit Browser Plugin (affects Mozilla/Firefox, and no 64bit Shockwave/Flash player plugins. I had to live without those since installing the 64bit Kubuntu.

---

### Post by GameManK on 2005-12-25
hey I also just got a 64-bit cpu and wondering if i should install the 32-bit or 64-bit version.  How hard is it to get everything working and is it worth it?

firefox & opera with java & flash? amarok with xine? totem? wine? ATI drivers? audigy2 drivers? gaim? k3b? nvu?

(also whether it might be worth it to go with dapper)

---

### Post by WirelessMike on 2005-12-29
The blackdown java 1.4.2 works well on 64-bit.  I've installed it on kubuntu breezy 64 and it has worked flawlessly ever since.  It's very easy to locate in the repos.  Look for "j2re1.4" and "j2re1.4-mozilla-plugin" as suggested in the ubuntu wiki, [here]("https://wiki.ubuntu.com/RestrictedFormats").

Flash, however, is a bit more challenging.  If the suggested solution in the Restricted Formats section of the Ubuntu Wiki doesn't work for you, [this thread]("http://www.ubuntuforums.org/showthread.php?t=90106&highlight=64-bit+flash") is a how-to for those who wish to install a 32-bit browser (currently the only universally successful way to have flash in a 64-bit environment) on the 64-bit version of (k)Ubuntu without messing with a chroot environment.

After installing both on my machine, I have no java issues in any of my browsers (32-bit or 64-bit).  I still have flash issues in my 64-bit firefox, but none in my 32-bit firefox, nor flock, and my experience to date with kubuntu Breezy 64 has been fine, aside from minor mounting issues common on both the 64-bit and 32-bit flavors.

By the way--  You mention Amarok with Xine.  That is precisely my audio player of choice and it works fine on my config.  I do suggest you go in the settings, though (in the gui, this is "configure amarok" under "Settings"), and once in the "last.fm" settings, uncheck "Retrieve Similar Artists" (this feature is very buggy and typically strains the cpu, sometimes causing crashes).

As you can see from my stats in my sig, I, too, use an ATI graphics card--  A very new one, in fact, and have experienced no driver issues since installation.

---

### Post by Jimmy_r on 2005-12-30
I just realized that i am able to use sun's 64-bit jre with konqueror, no java-plugin reqired. Yes!! Perhaps everybody know this already, but I will post it here, just incase someone else is tearing their hair over those gcj and blackdown things as i was yesterday.

Just install 64-bit jre by suns instructions: [http://java.sun.com/j2se/1.5.0/jre/install-linux-64.html]("http://java.sun.com/j2se/1.5.0/jre/install-linux-64.html")
Then:
Konqueror->settings->configure konqueror->Java & Javascript, mark "enable Java globally" 
In "path to runnable java:" write yourinstalldirectory/jre1.5.0_XX/bin/java
In my case that was /usr/local/jre1.5.0_06/bin/java
Then go to [http://www.java.com/en/download/installed.jsp]("http://www.java.com/en/download/installed.jsp") to try it...

---

### Post by Josef K. on 2006-01-06
[QUOTE=arjaybe] Most of the comments indicate that there's no speed advantage to using 64-bit and that you might as well use 32-bit and save yourself some work.  Or you could cut two partitions and install them both.-)[/QUOTE]

if there're no speed advantage using a 64bit version (and for sure a lot of problem, with flash wine etc.) why should somebody use the 64bit version?! :rolleyes:

---

### Post by Drain on 2006-01-07
[QUOTE=Josef K.]if there're no speed advantage using a 64bit version (and for sure a lot of problem, with flash wine etc.) why should somebody use the 64bit version?! :rolleyes:[/QUOTE]
Because it's coooooooool. ;-)

Seriously, it's the direction the computing world is headed, the frontier will be settled.  Eventually. ;-)


[on a commpletely irrelevant note: w00t! post #100.]

---

### Post by bannerboy on 2006-01-09
[QUOTE=Josef K.]if there're no speed advantage using a 64bit version (and for sure a lot of problem, with flash wine etc.) why should somebody use the 64bit version?! :rolleyes:[/QUOTE]

for most software applications there are absolutely no speed advantages at all, but many of those don't use all of your processor anyway, but for some software, such as video editing software, and 3D modeling software, you do gain speed with 64bits. but if youre not planning to be doing any of that, I suggest you keep it to 32bits, it makes life simpler.

---

### Post by digger4ubuntu on 2006-01-10
One of the biggest drivers to 64bit computing is the 4GB per processor memory limitation in 32bit computing.  This is a somewhat application independant point of purpose, but applications will still need to be written for 64bit platforms or they will remain limited to 4GB of memory space.  Where does this come into play?  High-end math (a.k.a. super computing), high-availability services, and pretty things like image and movie creation/editing.

As an end user today, your primary function in the 64bit world is bug discover/reporter.  When it becomes stable. reliable, and cheap, the world should benifit greatly by placing more computational power into scientists/researchers hands at greatly reduced costs of money and time.

---

