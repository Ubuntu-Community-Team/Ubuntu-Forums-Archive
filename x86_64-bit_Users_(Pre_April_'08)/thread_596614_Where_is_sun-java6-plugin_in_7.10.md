---
title: "Where is sun-java6-plugin in 7.10 ???"
date: 2007-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Asteryx on 2007-10-29
Hi folks,


AMD64 here. Want to get the JAVA plugin installed and working. However everywhere I look it says to install "sun-java6-plugin" to get it. But this package is nowhere to be found :confused:.

Any idea ?

Thanks very much in advance.

Here is the output:

aaaa@aaaaa:~$ sudo aptitude install sun-java6-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
**[COLOR="Blue"]No candidate version found for sun-java6-plugin[/COLOR]**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[...]

---

### Post by Kilz on 2007-10-29
This is because of the nature of 64bit. There is no 64bit java6 plugin.[ There is a java 7 plugin, but its called icedtea.]("http://packages.ubuntu.com/gutsy/devel/icedtea-java7-plugin")

---

### Post by Asteryx on 2007-10-29
> **Kilz said:**
> This is because of the nature of 64bit. There is no 64bit java6 plugin.[ There is a java 7 plugin, but its called icedtea.]("http://packages.ubuntu.com/gutsy/devel/icedtea-java7-plugin")


Hi Kilz and thanks for replying !

Is this the only option available to us ?  :shock:   I've seen other posts out there showing little faith and trust for that package :( (that's a nice way of saying that  that piece of software is in fact ... ahem ... crap).

However got it installed and is now appearing under "about: plugins" section BUT ... Java official "verify your installation" program won't recognize it and when I've checked it against other web sites I knew require JAVA ... didn't work either ... :cry:

So are we then doomed if using the x64 bit OS ? Cause this **is** a MAJOR show stopper for anyone using this version for serious business ...

Could we not use the packages offered by SUN directly ? Why reinventing the wheel ?

-Asteryx

---

### Post by Robocoastie on 2007-10-29
even the one from Sun is 32 bit. The 64 bit one isn't for web applets, which likely is what you need it for. Somewhere here is a tutorial on installing Firefox 32bit on 64bit Ubuntu so plugins like Java will work, I'm searching for it as we speak to solve the java issue.

---

### Post by go_beep_yourself on 2007-10-29
> **Asteryx said:**
> Hi folks,


AMD64 here. Want to get the JAVA plugin installed and working. However everywhere I look it says to install "sun-java6-plugin" to get it. But this package is nowhere to be found :confused:.

Any idea ?

Thanks very much in advance.

Here is the output:

aaaa@aaaaa:~$ sudo aptitude install sun-java6-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
**[COLOR="Blue"]No candidate version found for sun-java6-plugin[/COLOR]**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[...]

It is ia32-sun-java6-bin, not sun-java6-plugin.

---

### Post by sawjew on 2007-10-29
The iced tea packages in the Gutsy repositories don't seem to work but if you go to this post here [http://ubuntuforums.org/showthread.php?t=580792&highlight=iced+tea]("http://ubuntuforums.org/showthread.php?t=580792&highlight=iced+tea") and add the repositories mentioned in post number 9 then upgrade iced tea it seems to work.  It works with the java test page and most java applets I have tried except the most critical one I need.  I think that is the problem of the web site however, it will only work with sun java 5 or 6 and nothing else.

I did have to manually create a link for the plugin but other people don't seem to have had this problem.  Give it a go, it might just do the job for you.  I can't remember exactly where the link needs to go and I am on Windows at work at the moment so I can't look for you.  You should be able to work it out, I think it was under /usr/lib/jre.

---

### Post by Asteryx on 2007-10-30
Cheers guys ! ;)

I'll give a try to all suggestions tonight (I am @ work right now too and using the 32bit version inside a vmware). I'll let you know the results.

________________________
"I didn’t fail 1,000 times. The light bulb was an invention with 1,000 steps." - *Thomas Edison*

---

### Post by Lord Grover on 2007-10-30
Is [this]("http://www.java.com/en/download/help/5000011400.xml") of any help or am I barking up the wrong tree?

---

### Post by Kilz on 2007-10-30
> **Asteryx said:**
> Hi Kilz and thanks for replying !

Is this the only option available to us ?  :shock:   I've seen other posts out there showing little faith and trust for that package :( (that's a nice way of saying that  that piece of software is in fact ... ahem ... crap).

However got it installed and is now appearing under "about: plugins" section BUT ... Java official "verify your installation" program won't recognize it and when I've checked it against other web sites I knew require JAVA ... didn't work either ... :cry:

So are we then doomed if using the x64 bit OS ? Cause this **is** a MAJOR show stopper for anyone using this version for serious business ...

Could we not use the packages offered by SUN directly ? Why reinventing the wheel ?

-Asteryx

The other alternative is [a 32bit browser and plugins. ]("http://ubuntuforums.org/showthread.php?t=202537")

---

### Post by Asteryx on 2007-11-01
Folks,

Apologize for the delay.

Eventually went down the path of installing Firefox32 and now it's working fine. I have followed Kilz's solution found [[COLOR="Blue"]_here ->_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java"). So THANK YOU Kilz =D>.

So happy days & life is beautiful \\:D/

- Asteryx

PS. This kinda makes you wonder what's the purpose of Firefox64 if there are not plugins for it ? :confused:

---

### Post by fudo81 on 2007-11-01
It may sound like a silly question, but...
is there a good reason why the sun-java6 plugin and the acroread plugin for firefox aren't available for 64bit?
Whose fault is it? Sun and Adobe's? Mozilla's? Canonical's?
In other words:
do I really have to install firefox for 32bit (a solution that I dislike for several reasons), or should I expect to find the right plugins also for AMD64 in the near future?
Maybe in Hardy Heron?
Thanks.

---

### Post by balak on 2007-11-01
Thanks folks. I was able to install the icedtea java7 and the plugin. It works in some sites and not in several others - at the ones I need. Anyways I am willing to live with this for a while.

Hopefully java 64-bit will be updated in the near future and compatible withe everything out there on the web.

In feisty, I had to install firefox32, ia32libs and all that junk just to get flash/java working. Glad to see that progress has been made on that front in gutsy. Eagerly waiting for more progress so that I can use my 64-bit m/c with 64-bit apps.

---

### Post by sawjew on 2007-11-01
Asteryx

> This kinda makes you wonder what's the purpose of Firefox64 if there are not plugins for it ?

The only plugin not currently fully functional for 64 bit firefox is the java plugin.  You can install the flash plugin just as you can with 32 bit, when you go to a site that requires it firefox offers to install it for you and it works perfectly.  It uses nspluginwrapper to do this but you don't even need to know that, it just works.  Acroread plugin can be provided by mozplugger.

fudo81

> It may sound like a silly question, but...
is there a good reason why the sun-java6 plugin and the acroread plugin for firefox aren't available for 64bit?
Whose fault is it? Sun and Adobe's? Mozilla's? Canonical's?
In other words:
do I really have to install firefox for 32bit (a solution that I dislike for several reasons), or should I expect to find the right plugins also for AMD64 in the near future?
Maybe in Hardy Heron?
Thanks.

In answer to whose fault it is, it is the software provider's, (eg, Sun, Adobe).  They do not provide a plugin and do not release the source code for others to create the plugin.  Sun has now released their source code and Iced Tea is the beginning of the new open source implementation of java.  I would think by Hardy we should have a reasonably functional 64 bit plugin.  As to acroread, I don't know if or when Adobe will release a plugin but you can install mozplugger and it will embed evince in your browser by default but can be easily changed to embed acroread.

So the answer is that the only reason you should need to run 32 bit firefox is if you have critical java apps which don't work with the free java available for 64 bit.  Your other option is to use the sun 64 bit java and install konqueror which can use the java without a plugin and I think Opera can do the same (correct me if I'm wrong) and they have now released a 64 bit version.

I am curious as to why other browsers can use java without a plugin but firefox can't.  Maybe this is something that could be fixed by Mozilla?

---

