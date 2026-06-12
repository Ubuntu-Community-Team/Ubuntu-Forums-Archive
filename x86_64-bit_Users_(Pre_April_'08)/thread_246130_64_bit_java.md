---
title: "64 bit java?"
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ShadowRage on 2006-08-28
is there a 64-bit java release that offers a mozilla plugin yet?

I'm curious.

---

### Post by Kilz on 2006-08-28
> **ShadowRage said:**
> is there a 64-bit java release that offers a mozilla plugin yet?

I'm curious.

No, use the 32bit one and 32bit firefox. Automated install scripts and a firefox32 .deb file are now on my howto page. Look in my signature.

---

### Post by Harksaw on 2006-08-28
Anyone know the chances that it'll be released for 64 bit in the next few weeks?

---

### Post by ShadowRage on 2006-08-28
I use that nsplugin wrapper for flash, and I know about 32 bit java, I just want to know what's the status on 64 bit java.

---

### Post by ShadowRage on 2006-08-28
I use that nsplugin wrapper for flash, and I know about 32 bit java, I just want to know what's the status on 64 bit java.

---

### Post by Kilz on 2006-08-28
> **Harksaw said:**
> Anyone know the chances that it'll be released for 64 bit in the next few weeks?

Slim and none? the browser plugin isnt nessasary even if it isnt released.

---

### Post by Kilz on 2006-08-28
> **ShadowRage said:**
> I use that nsplugin wrapper for flash, and I know about 32 bit java, I just want to know what's the status on 64 bit java.

Write to sun and ask them.

---

### Post by tomdkat on 2006-08-29
> **Kilz said:**
> Write to sun and ask them.Actually, that's not too far off the mark:

[http://forums.mozillazine.org/viewtopic.php?t=457194](http://forums.mozillazine.org/viewtopic.php?t=457194)

I wonder if the Linux distro maintainers who maintain 64-bit native distros could band together and approach Sun.  I'm sure the 64-bit Linux distro maintainers have a general idea of how many people use their 64-bit distro.

Peace...

---

### Post by kuja on 2006-08-29
I have serious doubts that anyone knows how many people are actually using Linux, let alone 64-bit Linux.

(Please prove me wrong, pretty please?)

---

### Post by Kilz on 2006-08-29
> **kuja said:**
> I have serious doubts that anyone knows how many people are actually using Linux, let alone 64-bit Linux.

(Please prove me wrong, pretty please?)

I have a feeling you are correct. There is very little real data on desktop use that I have been able to find.
I also think its a non issue with not having a 64bit java or other browser plugin. Dapper is multiarch enough that it doesnt matter. Browsers will not get any real boost in speed from being 64bit.

---

### Post by tomdkat on 2006-08-29
> **kuja said:**
> I have serious doubts that anyone knows how many people are actually using Linux, let alone 64-bit Linux.

(Please prove me wrong, pretty please?)Well, exact numbers wouldn't be needed but estimates could definitely be made.  Consider the number of people downloading 64-bit ISOs, the number of people ordering 64-bit distro CDs, the number of people seeking assistance with 64-bit installations on forums like this, the number of people utilizing the commercial support options for Ubuntu or other distros, and you can get an idea of how wide spread 64-bit Linux is actually in use, either on desktops or deployed as servers or some other combination thereof.

There isn't one source where we can get one number which represents actual Linux use but I think we can approach educated estimations when looking at various numbers some actually have access to.

Peace...

---

### Post by tomdkat on 2006-08-29
> **Kilz said:**
> I also think its a non issue with not having a 64bit java or other browser plugin. Dapper is multiarch enough that it doesnt matter. Browsers will not get any real boost in speed from being 64bit.I strongly disagree with this.  Why?  Perception.  I don't challenge you from a technical standpoint but from an end-user standpoint, I think it's almost critical to have the perception that a 64-bit platform can work as well as a 32-bit platform.

Someone who just happened to have a 64-bit machine might want to install the 64-bit version of Linux, only to find their web browsing experience is hindered by lack of multi-media plugins they might actually need. I know I've visited some sites that require Flash and have no non-Flash version I can access.  Sure, it's possible to get 32-bit Flash working but if it doesn't "just work", some will bail on 64-bit Linux and go back to a 32-bit environment or install 32-bit Windows or whatever.

From a perception standpoint, I think painless browser plugin support is mandatory.

Peace...

---

### Post by Kilz on 2006-08-29
> **tomdkat said:**
> I strongly disagree with this.  Why?  Perception.  I don't challenge you from a technical standpoint but from an end-user standpoint, I think it's almost critical to have the perception that a 64-bit platform can work as well as a 32-bit platform.

Someone who just happened to have a 64-bit machine might want to install the 64-bit version of Linux, only to find their web browsing experience is hindered by lack of multi-media plugins they might actually need. I know I've visited some sites that require Flash and have no non-Flash version I can access.  Sure, it's possible to get 32-bit Flash working but if it doesn't "just work", some will bail on 64-bit Linux and go back to a 32-bit environment or install 32-bit Windows or whatever.

From a perception standpoint, I think painless browser plugin support is mandatory.

Peace...

The thing is FOSS has no control over the proprietary plugins. If the 32bit plugin doesn't work in 64bit, it isn't going to work in 32bit. The reason most problems happen with flash isn't the architecture, but the fact that we are still using Flash 7 on Linux for both 32 and 64bit. 32bit java runs without problems.
Add to this the fact that most of the 64bit processors sold for desktop use also run 32bit applications. You then see why I'm saying its a non issue.
People in this thread have a 64bit browser, but are using 32bit plugins with a wrapper. I can safely bet they have more issues than someone running a 32bit browser on the 64bit system. Heck they cant even run java.
The immediate future of 64bit computing isn't pure 64bit, its multiarch IMHO. This will give the 64bit user the ability to run everything. Sadly Ubuntu is stuck waiting on Debian to implement multiarch. But it will happen. Most 64bit distro's are moving to or are already multiarch. At least Dapper can run 32bit applications, this alone should prove that we are moving to multiarch. Because Breezy couldn't.
For those that leave for windows, so be it. But moving to a 32bit OS isn't going to solve things. The 32bit browser is a good solution, there is even a .deb file to install it now. The only problem with perception is that some people are still spreading the FUD that some things are missing, like Flash, when they are not.

---

### Post by tomdkat on 2006-08-30
> **Kilz said:**
> The thing is FOSS has no control over the proprietary plugins.Yep, this is a problem.  I don't necessarily expect FOSS to somehow gain control but the FOSS community definitely has a voice and one that will hopefully get louder as more people join the community.

> Add to this the fact that most of the 64bit processors sold for desktop use also run 32bit applications. You then see why I'm saying its a non issue.Yep, I see why you say it's a non issue but your reaoning is from a technical perspective.   Unless, you're saying 64-bit Linux distros should be used primarily by geeks there are non technical issues that also need to be addressed.

Just look at the number of comments by people expressing concern or wonder of whether they did "the right thing" by installing a 64-bit Linux distro.  There are also those who have already changed from 64-bit Ubuntu to 32-bit (for various reasons).

> People in this thread have a 64bit browser, but are using 32bit plugins with a wrapper. I can safely bet they have more issues than someone running a 32bit browser on the 64bit system. Heck they cant even run java.I don't doubt this at all and this further illustrates why some noise needs to be made, IMO.  Sun hasn't stated they will never support 64-bit Linux JRE plugins but they won't unless there is demand and there won't be any demand if no one speaks up.

> The immediate future of 64bit computing isn't pure 64bit, its multiarch IMHO. This will give the 64bit user the ability to run everything. Sadly Ubuntu is stuck waiting on Debian to implement multiarch. But it will happen. Most 64bit distro's are moving to or are already multiarch. At least Dapper can run 32bit applications, this alone should prove that we are moving to multiarch. Because Breezy couldn't.That's cool.  Getting more of the 32-bit/64-bit stuff resolved under the covers and behind the scenes will address the perception issue I'm talking about.  The more things "just work", the more people will enjoy their computing experience.   :)

> For those that leave for windows, so be it. But moving to a 32bit OS isn't going to solve things.Not in the long run, but definitely in the short term.  Today, I can't run any Flash applets in my browser (I haven't gone through your process yet).  If I boot from a 32-bit liveCD, I can run those same Flash applets in the 32-bit version of the browser without doing anything except accessing the site.

> The only problem with perception is that some people are still spreading the FUD that some things are missing, like Flash, when they are not.I guess this gets more to semantics than FUD, I think.  It's true things like Flash exist and can be made to run, but not in a 64-bit native form people would expect them to be in.

In any event, I do plan on playing around with the 32-bit browser and plugins when I have more time.  :)

Peace...

---

### Post by Kilz on 2006-08-30
> **tomdkat said:**
> In any event, I do plan on playing around with the 32-bit browser and plugins when I have more time.  :)

Peace...

The thing is you or anyone for that matter don't have to play around with them. I have done most of the work. Go to the Firefox link in my signature, download the install script, extract it, open a terminal, type in 2 very easy commands. Type in yes or agree to a few things. Surf!
That's another reason I say its a non issue, there is no longer any setup that may intimidate newbies. I had so many mistakes and errors from newbies who couldnt follow the howto I wrote setup scripts that do it all. You can still manualy install things, but I dont recommend it. The scripts install .deb files, it is no longer trying to force or shoemaker in something.

---

### Post by a-musing amazon on 2006-08-30
You /can/ get 64-bit java. 

Just go to Synaptic's Search and type 'Blackdown'. 

The Blackdown Java Runtime Environment package includes the plugin for your 64-bit Firefox or Epiphany browser (if that is what you use). 

There is also an SDK for development work.

---

### Post by John Jason Jordan on 2006-08-30
> **a-musing amazon said:**
> You /can/ get 64-bit java. 
Just go to Synaptic's Search and type 'Blackdown'. 
The Blackdown Java Runtime Environment package includes the plugin for your 64-bit Firefox or Epiphany browser (if that is what you use). 
There is also an SDK for development work.
That is what I have been using for some time. However, I need to run a small Java app for lingistics syntax trees and it required Sun Java. Hence, I installed Sun Java and the app now runs fine. 

What doesn't work is Blackdown with Firefox. I have regular Firefox that Dapper AMD-64 installed by default. I have the Blackdown Java installed as well, and the Firefox plugin works fine. The problem is that I am constantly crashing Firefox when Java is required. Yesterday, for example, I was on a site with a link to another site. The link was a Java link. When I clicked on it Firefox completely disappeared from my computer. This crashing of Firefox happens constantly, and always because some site requires Java and doesn't like the Blackdown Java.

What I need is to figure out how to get the Sun Java used as the Firefox plugin, instead of the Blackdown Java.

---

