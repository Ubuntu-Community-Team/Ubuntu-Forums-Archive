---
title: "java in firefox how?"
date: 2007-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by SledgeHammer_999 on 2007-05-24
hey guys, I am using feisty 64-bit. I am very happy with it but: 

could you tell me how to install the java plugin for firefox? Apparently the java which exists in the repositories isn't compatible. I wanna know if I can do it some other way. I don't care if I use close-source or open-source java. I just want it to work. 

**BUT I DO CARE ABOUT THIS:** I don't want to use the 32-bit version of firefox.

thank you in advance!!!

---

### Post by Azakus on 2007-05-24
Blackdown java is the only java I could get to work with a 64-bit firefox install.
```
sudo aptitude install j2re1.4 j2re1.4-mozilla-plugin
```

---

### Post by SledgeHammer_999 on 2007-05-24
Well I am little stupid. I had installed j2re1.4 for Azureus but I forgot j2re1.4-mozilla-plugin for firefox. I confirm that it works now. But a problem I had wasn't solved.

I want to visit this greek site [www.odeon.gr](www.odeon.gr) which (I think) uses javascript and flash. I thought that javascript had to do with java but apparently it doesn't. Flash works fine using nspluginwrapper. But the problem with this site is that it shows only a blank page and nothing else. In WinXp it loads. (in ubuntu 32-bit I don't know). Could you help me?

---

### Post by Kilz on 2007-05-24
Look in my signature, click on link for Firefox 32. Download script, run script. Close 64bit browser, start 32bit browser, use java.

---

### Post by SledgeHammer_999 on 2007-05-24
You should read my post. I don't want to use 32-bit firefox. thanks for your effort by the way.

---

### Post by Kilz on 2007-05-24
> **SledgeHammer_999 said:**
> You should read my post. I don't want to use 32-bit firefox. thanks for your effort by the way.

Thats fine, enjoy. But realize that there is no good way to run java on the 64bit compiled browser as of yet. When java 7 is released, we may get a plugin, but that wont be for about a year.
Also please notice that I mentioned that it is 64bit compiled browser. It is not a true 64bit application, but 32bit code that is compiled to run on the 64bit os. Secondly, a browser is not a number crunching application, so even if you did have a 64bit version there would be no performance increase.

---

### Post by SledgeHammer_999 on 2007-05-24
ok. Um could you or someone else tell me if the site mentioned above loads using firefox 32-bit & 64-bit?

---

### Post by Kilz on 2007-05-24
> **SledgeHammer_999 said:**
> ok. Um could you or someone else tell me if the site mentioned above loads using firefox 32-bit & 64-bit?

The 32bit version runs it fine. [But when loading the 64bit version you see this.]("http://ubuntuforums.org/attachment.php?attachmentid=33368&stc=1&d=1180058982") I have no idea in this world how you think you need a java plugin. 
It clearly says Adobe Flash all over the page.
That can be ran in the 64bit browser with nspluginwrapper. For the plugin challanged, I even have [a script that installs the wrapper and flash to a 64bit browser]("http://ubuntuforums.org/showthread.php?t=425672").

---

### Post by ryanVickers on 2007-05-24
oh no.  Well, not really, the 64Bit is nice, and fast, but it doesn't seem to be smart enough to know how to run the 32 bit java plugins.  unfortunitly, there are no real 64 bit java, flash, or shockwave plugins for linux, but with automatics, you can install swiftfox - exactly the same as firefox but with plugins that work.  unforturitly, it's 32 bit, but that shouldn't be a problem.  I mean, a web browser isn't exactly resource consuming, (unless your using windows :p)

---

### Post by Kilz on 2007-05-25
> **ryanVickers said:**
> oh no.  Well, not really, the 64Bit is nice, and fast, but it doesn't seem to be smart enough to know how to run the 32 bit java plugins.  unfortunitly, there are no real 64 bit java, flash, or shockwave plugins for linux, but with automatics, you can install swiftfox - exactly the same as firefox but with plugins that work.  unforturitly, it's 32 bit, but that shouldn't be a problem.  I mean, a web browser isn't exactly resource consuming, (unless your using windows :p)

No, not the same as Firefox. Swiftfox is a proprietary application that restricts your freedom to redistribute. Part of what we as Linux users should IMHO do is use free software whenever possible. Doing otherwise sends the wrong message. That it is ok to take away freedoms that others worked hard for you to have.
Secondly Swiftfox is 32bit. The original poster expressly dosent want a 32bit browser.
Lastly Flash can be made to run on a 64bit browser with nspluginwrapper (link to install script in my last post). If you need other plugins, there is the option of using my install script (link in my signature) With the option of installing Free as in freedom browsers like Swiftweasel, Flock, Iceweasel, or Firefox.

---

### Post by SledgeHammer_999 on 2007-05-25
thnanx Kilz. I would be lucky if saw the site the way you see it because I already have flash using nspluginwrapper. But what I see is this(attached photo).Nothing actually. 

Where do I got the idea that I need java? Well, if you "view the page source" it seems that it uses javascript.(is javascript related to java? ). Also when I connect to this site there is no "page source" downloaded.

---

### Post by ©TriMoon® on 2007-05-25
Java is not the same as javascript ;)

Simple explanation:
Java is a system that uses binary code like any other applications.
Javascript is a system that uses text commands that are translated by the Javascript engine that implements it.

Yes the two share the word "java" but they are completly different technologies....

---

### Post by SledgeHammer_999 on 2007-05-25
ok thanks. So this comes down to a problem(propably) of firefox. that's the only way I can explain it. maybe I'll try to reinstall firefox. (konqueror displays the page but it freezes at some other point).

---

### Post by ryanVickers on 2007-05-25
> No, not the same as Firefox. Swiftfox is a proprietary application that restricts your freedom to redistribute. Part of what we as Linux users should IMHO do is use free software whenever possible. Doing otherwise sends the wrong message. That it is ok to take away freedoms that others worked hard for you to have.
Secondly Swiftfox is 32bit. The original poster expressly dosent want a 32bit browser.
Lastly Flash can be made to run on a 64bit browser with nspluginwrapper (link to install script in my last post). If you need other plugins, there is the option of using my install script (link in my signature) With the option of installing Free as in freedom browsers like Swiftweasel, Flock, Iceweasel, or Firefox.

Ok, thanks for clearing that up, for me and anyone else.  I had no idea, it just seemed to work good and it solved the problem.

---

### Post by Kilz on 2007-05-25
> **ryanVickers said:**
> Ok, thanks for clearing that up, for me and anyone else.  I had no idea, it just seemed to work good and it solved the problem.

I think its more a problem with Automatix. Its full of proprietary stuff. Granted a lot of people want proprietary applications. There are also some applications like video drivers that have no altwernative. But find a lot of the users of Automatix to be recient converts from the land of Windows, that perhaps need some information as to why the proprietary stuff isnt the best.
When a free option is available it should be promoted. The application should go to grater lengths to make sure users understand that they are installing something that defeats a main reason a lot of people chose Linux. That is, its free as in freedom.

---

### Post by Chris_no on 2007-05-28
I'm been having similar issues that SledgeHammer_999 reports.

[http://ubuntuforums.org/showthread.php?t=456882](http://ubuntuforums.org/showthread.php?t=456882)

And none of the solutions helps.

Anyone have any idea how I can run Pacificpoker in Ubuntu.

(Wine doesn't cut it)

---

