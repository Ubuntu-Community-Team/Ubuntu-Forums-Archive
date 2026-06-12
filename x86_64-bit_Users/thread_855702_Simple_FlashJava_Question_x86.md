---
title: "Simple Flash/Java Question x86"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by tuxxy on 2008-07-10
Hi,

Ill keep it simple my flash runs fine on Youtube yet if I load for example this page   [http://www.thesun.co.uk/sol/homepage/](http://www.thesun.co.uk/sol/homepage/)

I will get like 3 grey squares where there should be some sort of web flash app...It has previously worked but never too well, after updating to Firefox 3 it seems to never work and even sometimes if im lucky I can see the images loading and displayed for a second then it greys out again

Is there anyway to fix this or just have to wait for Intrepid...

EDIT: Thought I would post my current system & flash plugins

AMD 64 X2 system / 64 bit Ubuntu 8.04 

File name: npwrapper.libflashplayer.so
Shockwave Flash 9.0 r124

application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Apparently these plugins should load that website so not a clue why they wont for me, I attempted to re-install the plugin but no luck, i then re-installed firefox removing all traces of it first and still no luck.  I think this could be another issue not flash?

---

### Post by Sef on 2008-07-10
1) Do you use x86 or 64-bit Ubuntu?

2) How did you install flash?

---

### Post by tuxxy on 2008-07-10
I use Ubuntu 64 bit on an AMD X2 system.

FLash install was

sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns

sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins/

---

### Post by tuxxy on 2008-07-11
SOLVED:

Installed Opera 9.50b as recommended in this thread

[http://ubuntuforums.org/showthread.php?p=5361992&posted=1#post5361992](http://ubuntuforums.org/showthread.php?p=5361992&posted=1#post5361992)

what can I say, lightning speeds and everything works perfectly flash, java I didnt even install 1 plugin.

I think i got a new browser :)

---

### Post by AgentZ86 on 2008-07-11
> **tuxxy said:**
> I use Ubuntu 64 bit on an AMD X2 system.

FLash install was

sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns

sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins/

Why do people install a 64bit OS on 64bit CPU but all the applications they run are 32bit applications such as: browser,flash,java,open office,and most everything else is running 32 applications.

I've read the pro's and cons of this in the wiki and decided to run the 32 bit version on my 64bit amd dual core and I don't know that I could ask for much more. It's lightning speed and stable.

Is there some reason people have to make the 64bit version run on their system if they are not using 64bit apps. or is this just for kicks ?
Sounds like most are more aggrevated then anything in trying to get all the things working correctly and no performance difference with the aggrevation.

Anyhow any advise on this would be great, I would consider the 64bit version just because I have a 64 bit processor.
However, I can't really understand why I want to do it, but I feel like I'm suppose to ?

Please advise.
:guitar:

---

### Post by tuxxy on 2008-07-11
Agent my AMD64 X2 box is lightning quick and also has 6 gig RAM, 64 bit Ubuntu also is better for video editing activities.

Why run 32 when you have the ability to run 64, for me I ahvnt found one problem except from what you see in this post, which btw does run on firefox 64 bit just not mine for some reason

ALso it would be hard to buy a new non-64-bit system these days.

---

### Post by Kilz on 2008-07-11
> **AgentZ86 said:**
> Why do people install a 64bit OS on 64bit CPU but all the applications they run are 32bit applications such as: browser,flash,java,open office,and most everything else is running 32 applications.

I've read the pro's and cons of this in the wiki and decided to run the 32 bit version on my 64bit amd dual core and I don't know that I could ask for much more. It's lightning speed and stable.

Is there some reason people have to make the 64bit version run on their system if they are not using 64bit apps. or is this just for kicks ?
Sounds like most are more aggrevated then anything in trying to get all the things working correctly and no performance difference with the aggrevation.

Anyhow any advise on this would be great, I would consider the 64bit version just because I have a 64 bit processor.
However, I can't really understand why I want to do it, but I feel like I'm suppose to ?

Please advise.
:guitar:

I personally cant understand why someone would buy a corvette and pull out 4 of the 8 spark plug wires. Perhaps they think it will be easier to buy non premium gasoline.

The example above places the question on a different perspective. The few applications (I can only think of browser plugins) that are still 32 bit is very small compared to all the rest that are not. 
The other reason some install is they think it will be easier, but I guess they just ignore the thousands of posts that pour into the other areas of the forum in thinking the x86 version is flawless. Most that do have problems are new users, and they are going to have issues regardless of what version they install.

---

### Post by jespdj on 2008-07-11
> **AgentZ86 said:**
> Why do people install a 64bit OS on 64bit CPU but all the applications they run are 32bit applications such as: browser,flash,java,open office,and most everything else is running 32 applications.
On 64-bit Ubuntu, the browser, Java, open office and most everything else is 64-bit, not 32-bit. What makes you think all those things are 32-bit?

I have only two 32-bit pieces of software on my computer: Adobe Flash and Skype - both are proprietary programs for which the manufacturer doesn't bother compiling a 64-bit version.

---

### Post by AgentZ86 on 2008-07-11
> **tuxxy said:**
> Agent my AMD64 X2 box is lightning quick and also has 6 gig RAM, 64 bit Ubuntu also is better for video editing activities.

Why run 32 when you have the ability to run 64, for me I ahvnt found one problem except from what you see in this post, which btw does run on firefox 64 bit just not mine for some reason

ALso it would be hard to buy a new non-64-bit system these days.

yes for video editing I agree, that makes since, but according to the ubuntu wiki's on this subject most applications except video and things are 32 bit apps. at least from what I've read there about the pros and cons.
As more demand for because apparent I suspect this will be everything 64bit, but Flash is not as of yet as far as I know.
Which means any site with flash will be bottled down to running a 32 bit app and according to the wiki it will even run slower then on a 32 bit machine. at least thats what I've read. Thats the only reason I've decided on the 32 version of Ubuntu for now until I can confirm that it will all work as fast or faster with all my apps.
Thats all i know.

---

### Post by AgentZ86 on 2008-07-11
> **Kilz said:**
> I personally cant understand why someone would buy a corvette and pull out 4 of the 8 spark plug wires. Perhaps they think it will be easier to buy non premium gasoline.

The example above places the question on a different perspective. The few applications (I can only think of browser plugins) that are still 32 bit is very small compared to all the rest that are not. 
The other reason some install is they think it will be easier, but I guess they just ignore the thousands of posts that pour into the other areas of the forum in thinking the x86 version is flawless. Most that do have problems are new users, and they are going to have issues regardless of what version they install.

Well the plugins is one topic already I would say you have answered that for yourself, however you would not buy a corvett and pull out 4 of the 8 spark plug wires, unless of course it was not hitting on all 8 to begin with. Which would seem to be the case if Flash is only 32 bit, and other apps are only 32 bit. 

But if you say that mostly everything is now available on 64bit however then I would consider trying this out myself. I was under the impression from the wiki that most have not come around to 64bit as of yet. Some are and some are not. According to the wiki many will certainly work on 64bit but are still 32 bit apps as far as I can tell from the pros and cons section of the wiki on this subject. But I'm no expert. I've google searched the pros and cons of it and thats about what comes up all over the net.
So I'll have to install the 64bit and see how it performs. Thats the only way I'll be able to tell for sure I guess.

---

### Post by AgentZ86 on 2008-07-11
> **Kilz said:**
> I personally cant understand why someone would buy a corvette and pull out 4 of the 8 spark plug wires. Perhaps they think it will be easier to buy non premium gasoline.

The example above places the question on a different perspective. The few applications (I can only think of browser plugins) that are still 32 bit is very small compared to all the rest that are not. 
The other reason some install is they think it will be easier, but I guess they just ignore the thousands of posts that pour into the other areas of the forum in thinking the x86 version is flawless. Most that do have problems are new users, and they are going to have issues regardless of what version they install.

Well the plugins is one topic already I would say you have answered that for yourself, however you would not buy a corvett and pull out 4 of the 8 spark plug wires, unless of course it was not hitting on all 8 to begin with. Which would seem to be the case if Flash is only 32 bit, and other apps are only 32 bit. 

But if you say that mostly everything is not available on 64bit however then I would consider trying this out myself. I was under the impression from the wiki that most have not come around to 64bit as of yet. Some are and some are not. According to the wiki many will certainly work on 64bit but are still 32 bit apps as far as I can tell from the pros and cons section of the wiki on this subject. But I'm no expert. I've google searched the pros and cons of it and thats about what comes up all over the net.
So I'll have to install the 64bit and see how it performs. Thats the only way I'll be able to tell for sure I guess.

And what about WINE is there a 64bit for that yet ?

---

### Post by Kilz on 2008-07-11
> **AgentZ86 said:**
> Well the plugins is one topic already I would say you have answered that for yourself, however you would not buy a corvett and pull out 4 of the 8 spark plug wires, unless of course it was not hitting on all 8 to begin with. Which would seem to be the case if Flash is only 32 bit, and other apps are only 32 bit. 

But if you say that mostly everything is not available on 64bit however then I would consider trying this out myself. I was under the impression from the wiki that most have not come around to 64bit as of yet. Some are and some are not. According to the wiki many will certainly work on 64bit but are still 32 bit apps as far as I can tell from the pros and cons section of the wiki on this subject. But I'm no expert. I've google searched the pros and cons of it and thats about what comes up all over the net.
So I'll have to install the 64bit and see how it performs. Thats the only way I'll be able to tell for sure I guess.

And what about WINE is there a 64bit for that yet ?

Please link to the page(s) that say that there are packages that are in the 32bit repositories that are not in the 64bit.

Sadly we get a lot of misinformed people who never seem to point out the source of the misinformation. Please do so.

The analogy of the corvette is appropriate. You are buying a high performance 64bit processor, and then hobbling it with a operating system that uses half its resources.

---

### Post by AgentZ86 on 2008-07-13
> **Kilz said:**
> Please link to the page(s) that say that there are packages that are in the 32bit repositories that are not in the 64bit.

Sadly we get a lot of misinformed people who never seem to point out the source of the misinformation. Please do so.

The analogy of the corvette is appropriate. You are buying a high performance 64bit processor, and then hobbling it with a operating system that uses half its resources.

Sure
Simply go to the ubunutu forums and see x86 64-bit-users

At the top of the page there is a sticky thread which says:
Advantages and Disadvantages of 64bit. (Plus install Guides)

Here is a link:[http://ubuntuforums.org/showthread.php?t=765428]("http://ubuntuforums.org/showthread.php?t=765428")


Although it does NOT specifically say:> there are packages that are in the 32bit repositories that are not in the 64bit.

What is does say is that:
> Questions an user may have:

Should you upgrade to 64-bit?
To make full use of 64-bit you will need native 64-bit applications, and this is where the problem starts for some users. Some programs an user might make use of may not provide native 64-bit applications (some examples include skype/ adobe flash), and this is where some users think that running 32bit will eliminate issues, however. There are known ways of getting these applications to work, as well as other applications which will be addressed below, and while the answers may not be a true fix the fact there is a fix available should allow for more users to move to 64bit, and possibly showing those companies who do not have a native 64bit applications that there is a demand.

As you can see this is where I started my research prior to installing my 32bit version, however I'm not opposed to the 64 bit version, but as you can see for me this sort of lead me in the direction of a 32bit version since I wanted to simply have access to the things I use now without problems of installing flash etc. and other communications packages that I use. Also I can't imagine that the performance for these things like skype,gizmo,wengophone etc. would be any faster even if the 64bit version is available. If it is great I'd like to try it, but if they only created a 64bit version simply to run on the 64bit machine for compatibility purposes and not performance then whats the point ?
So did they actually make a 64bit version or did they just make the 32bit apps run on 64bit machines ? 

I really don't know these answers, and from this wiki and some other google searches it appeared to me at the time that the 32bit version would be better for me. But I'm not doing any video editing or encoding etc. as of yet. So the real question is will I really notice any performance issues if I re-install the 64bit version or will it be relatively the same for what I'm going ? 

And if it's about the same and I find that some applications are not available for the 64bit platform then I guess I could easily install the 32 version once again. 
The next question is: Are people installing the 64bit version just because they think it's the best thing to do since they do have a 64bit processor? Or are they completely aware that it could likely be as fast on the 32bit or in many cases could even faster on the 32bit version with their 64bit processor depending on what they are doing on the machine? And of course this would be according to others and not my opinion since I've never tried the 64bit version as of yet.

Anyhow the main apps I use; and which I don't really know if they are available in the 64bit repositories are:
wengophone,java,flash,firefox,thunderbird,kompozer,gimp,gthumbs,avidemux,
gtkrecordtodekstop,pidgin,asmn,k3b,audacity,gscan2pdf,pdfedit,Camorama,mPlayer plugin, and Mplayer movie player,and WINE these are my most used programs.

If all these are available in the 64bit version then I guess I don't really have too much of a reason to stay with the 32bit version.Hardware is another topic. I'm using ATI 9850 256MB AGP Radeon Asusu motherboard etc. will those be an issue is the next stop of research? I can most likely just pop in the old live 64bit CD and try those thing out I'm guessing that should tell me.

Anyhow thats about the extent of my research if it be misinformed it's based on information found on the ubunutu forums.

It very well could be misinformed, however it could also be correct until I research further or until someone else can express that these program actually are available to the 64bit version.

I'll await a response on this as it's interesting to find out either way.

Thanks to all for the responses
:popcorn:

P.S 
As far as the corvette topic goes,all I was suggesting is that it's all in the design and if you force a 64bit app. and make it available to run on 64bit platform simply for compatibility purposes to run on the 64bit platform, althought the OS may be 64bit and optimized that does not mean that the 32bit app. ,which is now converted to run on the 64bit platform is optimized for that platform. Thats all I'm saying. If you pull out 4 spark plugs from a V8 that may not be performing well anyhow, that is not much different then adding additional 4 spark plugs to a V8. which may do absolutely nothing as well.Especially if the machine was not running right to begin with.
I don't know if that can be the case in many apps. but I can suspect that it could be true given what I'm reading on the web and in the ubuntu forums. I wish I were an expert but I'm not, I simple did some research on the net and ubuntu forums and this is what others appear to be saying. With exception to video editing and coding etc. Also is there 64bit games for Linux I don't really know all that is available for the 64bit platform admittedly, if i did perhaps I may have decided differently. Perhaps I'll try the 64bit version a little later. 
What partition type does the 64bit version use ? I'm guessing it must be a 64bit partition of some type ? or does it still use the ext3 partition ?
More things I don't know about.
Thanks

---

### Post by Kilz on 2008-07-13
At least one of the applications you mention, avidemux encodes video. If you are doing any video editing or recording of media you should get performance benefits.
The applications you mention should be in the 64bit repositories. [Take a look here to search for specific packages.]("http://packages.ubuntu.com/") Even if they for some reason are not the 32bit version of the application will run on the 64bit os.
Thanks for giving me the location of the misinformation. Most people never do. [If you look here]("http://ubuntuforums.org/showthread.php?t=368607"), you will see the original version of that post, before the forum was changed earlier this year. The post is from Febuary 2007, and pre dates Feisty Fawn. Granted the post has been updated a few times. But it may not be clear to you that it is describing the exception rather than the rule on 32bit software.
Your questions are quite common. You want to know if its worth installing the 64bit version. What the sticky you quote from says should answer that.

[INDENT]There have been many questions regarding running 64bit Ubuntu, as well as other 64bit Linux distro's for this matter. Many think it is time owners of 64bit hardware stop asking if they should run a 64bit OS, and instead ask why should they not run a 64bit OS.

The reason for this theory/ argument of 64bit vs. 32bit is some users think there will be less issues running 32bit.

Then you have those who say regardless of what software architecture you run there will be common issues to battle like wireless and video drivers, and some software programs.[/INDENT]

What this says is true, a lot of 64bit hardware owners are asking , Why Not? This is important. But to me, you are in fact asking Why Should I. But Why not is a better question. Because you are coming at it from something that is hard to answer. Because everyone has different reasons for installing Ubuntu and different uses. Some people are going to be issues regardless of what version you install. 
Looking for the small handfull of 32bit applications and saying it may not be worth installing because they are 32bit is to me, the wrong way to look at it. Instead I would look at it as even if there is no 64bit version the 64bit os can run the 32bit version. I will get some performance increase from some programs and maybe not from others. But the 32bit os gives you 0 % performance increase. In fact a lot of people say their computer runs slower on the 32bit os.
So to sum it all up. 
1. You may get a  performance boost with 64bit, you will never get one with 32bit.
2. Some people may have issues with any version of Ubuntu regardless of what bit. 
3. Since there is no easy foolproof way of avoiding issues, you may as well install the operating system designed for your hardware to get the most out of it.

---

### Post by tuxxy on 2008-07-13
> Also I can't imagine that the performance for these things like skype,gizmo,wengophone etc. would be any faster even if the 64bit version is available

Any 64 bit app will perform better than the equivelant 32 even if its just loadup time.  

I need performance from my system and would not install 64bit if it was going to hinder it in anyway.  The 64bit kernel is there, all the main apps are 64 bit and the 64 bit flash driver is due soon.  So would you half your systems capbilities for skype? or them other 32 bit proprietary communication apps you mention.

64 > 32 :guitar:

---

### Post by AgentZ86 on 2008-07-13
> **tuxxy said:**
> Any 64 bit app will perform better than the equivelant 32 even if its just loadup time.  

I need performance from my system and would not install 64bit if it was going to hinder it in anyway.  The 64bit kernel is there, all the main apps are 64 bit and the 64 bit flash driver is due soon.  So would you half your systems capbilities for skype? or them other 32 bit proprietary communication apps you mention.

64 > 32 :guitar:

Thats a good question.

Also if I install the 64bit version can I use these apps anymore or is there a 64bit app to go with my 64bit processor ?

Or can I still run the 32bit app on my 64bit system with my 64bit version ?
Which is the real question anyhow, if I only have a 32bit version of my apps that I like, then I don't see any real benifit in running the 64bit version of the OS just run 32bit apps ? 

I just don't want to be without the apps I use all the time. and surely do not want additional hassles if I can only run the 32bit version of my apps if they are not available in the 64bit repositories etc.

But with all this new talking points I may try it out and see how it goes. 
I have everything automatically backed up to the server every sun night anyhow so It wont' be hard to install and get running.
I installed the 32bit version and fully ready to run all my apps in about 10min. or perhaps 15min and fully updated. I have Business class cable internet so that sure helps.

Anyhow thanks for all the help.


Please advise and thanks to all.

---

### Post by tuxxy on 2008-07-13
Agent any of your 32 bit apps will run on 64bit Ubuntu, if the app has a 64bit version it will run quicker.  I cant say for sure on games as I use my PS3 for them =p

Just like your 32 bit install, you should be up and running in 15 minutes :)

---

### Post by Kilz on 2008-07-14
> **AgentZ86 said:**
> Thats a good question.

Also if I install the 64bit version can I use these apps anymore or is there a 64bit app to go with my 64bit processor ?

Or can I still run the 32bit app on my 64bit system with my 64bit version ?
Which is the real question anyhow, if I only have a 32bit version of my apps that I like, then I don't see any real benifit in running the 64bit version of the OS just run 32bit apps ? 

I just don't want to be without the apps I use all the time. and surely do not want additional hassles if I can only run the 32bit version of my apps if they are not available in the 64bit repositories etc.

But with all this new talking points I may try it out and see how it goes. 
I have everything automatically backed up to the server every sun night anyhow so It wont' be hard to install and get running.
I installed the 32bit version and fully ready to run all my apps in about 10min. or perhaps 15min and fully updated. I have Business class cable internet so that sure helps.

Anyhow thanks for all the help.


Please advise and thanks to all.

Post 14 by me it includes a link to the Ubuntu repository search page. That should help you answer all your questions about availability of applications in the 64bit repositories.

---

### Post by AgentZ86 on 2008-07-14
Kilz- Why doesn't that page specifically identify that this is the 64bit repository.

When I click link you provided in #14 and click around on any of the versions it does not say that these are 64bit repositories or even 64bit versions for that matter? how can I tell ?

If I click on 8.04 hardy, then where does it specifically identify that this is a 64bit repository ?

Why can't they just tell me at the top of the page ?

---

### Post by Kilz on 2008-07-14
> **AgentZ86 said:**
> Kilz- Why doesn't that page specifically identify that this is the 64bit repository.

When I click link you provided in #14 and click around on any of the versions it does not say that these are 64bit repositories or even 64bit versions for that matter? how can I tell ?

If I click on 8.04 hardy, then where does it specifically identify that this is a 64bit repository ?

Why can't they just tell me at the top of the page ?

The page allows you to search and get information on every package in the Ubuntu repositories. When you get the results, at the end of the entry, for example Firefox

Package firefox

 * hardy (web): meta package for the popular mozilla web browser
      3.0~b5+nobinonly-0ubuntu3: all

All means its available for All versions 

Package firefox-2

    * hardy (web): lightweight web browser based on Mozilla [universe]
      2.0.0.15+1nobinonly-0ubuntu0.8.04.2 [security]: amd64 i386

Is available in i386 and AMD64. You could even open the specific page and see this at the bottom in a little table. Sorry the table doesnt copy well to the forum.

Architecture  	Package Size  	Installed Size  	Files
amd64 	
i386

---

### Post by John.Michael.Kane on 2008-07-14
Hello AgentZ86,

I am the maintainer of the sticky in question, and will try to answer your concerns, as best possible. 

The question of should one upgrade to 64-bit, was asked many times, and what you quoted was simply trying to explain in simple terms how to best take advantage of the processor in question, while also explaining that certain programs that are used by forum members looking to switch, might not be compiled natively in x86_64, however. I also tried to make it clear that the i386 version of their programs could be installed on 64bit Ubuntu. 

My apologies, if this was not clear.

Regarding the applications you make use of, I have listed their support below. 
> 
wengophone [http://packages.ubuntu.com/hardy/wengophone](http://packages.ubuntu.com/hardy/wengophone) Architecture amd64
java There is iced tea [http://packages.ubuntu.com/hardy/icedtea-gcjwebplugin](http://packages.ubuntu.com/hardy/icedtea-gcjwebplugin) Architecture amd64 (Your mileage may vary with iced tea) There is also Kilz script method listed in the same sticky, you read [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)
flash [http://packages.ubuntu.com/hardy/flashplugin-nonfree](http://packages.ubuntu.com/hardy/flashplugin-nonfree) Architecture amd64  to install sudo aptitude install flashplugin-nonfree
firefox [http://packages.ubuntu.com/hardy/firefox-3.0](http://packages.ubuntu.com/hardy/firefox-3.0) Architecture amd64
thunderbird [http://packages.ubuntu.com/hardy/thunderbird](http://packages.ubuntu.com/hardy/thunderbird) Architecture amd64
kompozer [http://packages.ubuntu.com/hardy/kompozer](http://packages.ubuntu.com/hardy/kompozer) Architecture amd64
gimp [http://packages.ubuntu.com/hardy/gimp](http://packages.ubuntu.com/hardy/gimp) Architecture amd64
gthumb [http://packages.ubuntu.com/hardy/gthumb](http://packages.ubuntu.com/hardy/gthumb) Architecture amd64
avidemux [http://packages.ubuntu.com/hardy/avidemux](http://packages.ubuntu.com/hardy/avidemux) Architecture amd64
gtkrecordtodekstop [http://packages.ubuntu.com/hardy/gtk-recordmydesktop](http://packages.ubuntu.com/hardy/gtk-recordmydesktop) Architecture All
pidgin [http://packages.ubuntu.com/hardy/pidgin](http://packages.ubuntu.com/hardy/pidgin) Architecture amd64
amsn [http://packages.ubuntu.com/hardy/amsn](http://packages.ubuntu.com/hardy/amsn) Architecture amd64
k3b [http://packages.ubuntu.com/hardy/k3b](http://packages.ubuntu.com/hardy/k3b) Architecture amd64
audacity [http://packages.ubuntu.com/hardy/audacity](http://packages.ubuntu.com/hardy/audacity) Architecture amd64
gscan2 pdf [http://packages.ubuntu.com/hardy/gscan2pdf](http://packages.ubuntu.com/hardy/gscan2pdf) Architecture All
pdfedit [http://packages.ubuntu.com/hardy/pdfedit](http://packages.ubuntu.com/hardy/pdfedit) Architecture amd64
Camorama [http://packages.ubuntu.com/hardy/camorama](http://packages.ubuntu.com/hardy/camorama) Architecture amd64
mPlayer plugin [http://packages.ubuntu.com/hardy/mozilla-mplayer](http://packages.ubuntu.com/hardy/mozilla-mplayer) Architecture amd64
Mplayer movie player [http://packages.ubuntu.com/hardy/mplayer](http://packages.ubuntu.com/hardy/mplayer) Architecture amd64
WINE You should be able to simply run.
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

```
sudo aptitude install wine
```

IMHO looking at the applications you plan to use, of which some being video, as well as audio. You might benefit from moving to 64bit. I would advise dual booting 64bit along side the already installed OS.
 
As for setting up you ati card, you should be able to install the drivers the same way as you would have under your 32bit install.

Also regarding your Asus motherboard, and any other hardware we would need full details about them to help you with any issues you think you might have with them, and under most circumstances you should be able simply to use the live CD to not only install the os but check if your hardware is support under 64bit, as well. 

Please keep in mind while you continue your research. What one user experiences on her machine may not be the experience for all, and will come down to many factors one being hardware the other being how the application in question has been written/compiled.

Should you have further questions do not  hesitate to ask.

---

