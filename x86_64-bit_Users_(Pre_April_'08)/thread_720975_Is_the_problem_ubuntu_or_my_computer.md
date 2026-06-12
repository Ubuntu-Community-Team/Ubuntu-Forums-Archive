---
title: "Is the problem ubuntu or my computer?"
date: 2008-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by plr4ever on 2008-03-10
So i have been using x64 for a little while now, and i have noticed a few VERY annoying problems, such as:

[LIST]
The horrible block of code that is adobe flash wants to destroy and/or compete for resources with any running program(especially VirtualBox) and lock up my system. [/LIST]

[list]i have this continuous problem with running virtualbox and other applications, namely firefox, anything java or flash based. Does anyone have a clue as to why this happens?[/list]

[list]i have noticed in system monitor that my cpu has an awfully high IOWAIT compared to what actually gets processed. I have a few ideas for this, but i am not quite sure what it may be. Firstly, i had initially overclocked the board before it just disappeared and was running back at stock speed. however, i think something may still be screwing with the stability of the system, as no matter what i eventually have a lockup and have to reset the computer. I cannot tell, however, if the problem is my hardware or ubuntu, as other os's function fairly well. Is a high level of IOWAIT normal on a new Core 2?[/list]

[list] other random stability problems[/list]

If anyone can think of any possible reason why any of this could happen, or can think of a possible solution, i am VERY willing to try it, as i might just have to try my luck with straigh debian (forsees pain in near future).

---

### Post by rmtatum on 2008-03-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I built a package that contains a fix for the flash issue.  

Follow the launchpad bug url to download the patched package.

---

### Post by warp99 on 2008-03-11
[i]    * The horrible block of code that is adobe flash wants to destroy and/or compete for resources with any running program(especially VirtualBox) and lock up my system.

      * i have this continuous problem with running virtualbox and other applications, namely  firefox, anything java or flash based. Does anyone have a clue as to why this happens?[/i]

How are you running Adobe Flash since this is a 32-bit only plug-in? Are you using nspluginwrapper? The reason I ask is because I run Firefox 32-bit with Java 32-bit libraries, available in the repositories, under a 64-bit Kubuntu install without any issues. With this setup I can run 32-bit plug-ins (Flash, Acrobat Reader, Real Player, Java) and the associated programs.  Now for embedded media I don't use any plug-ins other than Real Player. Instead I use a Firefox extension called Media Connectivity:

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

VirtualBox is also a 32-bit only application so problems with the ia32 libs or some other libs may apply. Have you given a thought to using VMWare instead? VMplayer, VMserver, and VMworkstation are all available in native 64-bit code. I personally use VMworkstation 6.0 64-bit which is very stable compared to the previous 5.5 versions, which was only available 32-bit. 

VMPlayer and VMServer are free, as in beer, while VMworkstation is not. Now an unregistered copy of VMworkstation will allow you to make a VM image, but not actual run the image. Here is the funny part, VMworkstation also includes VMplayer, which is free.  So you can make the actual image in VMworkstation then run the image on VMplayer. :)

---

### Post by jocko on 2008-03-11
> **warp99 said:**
> VirtualBox is also a 32-bit only application so problems with the ia32 libs or some other libs may apply.
That's not true. There is a 64bit version of virtualbox. It just can't run 64bit guests.

---

### Post by warp99 on 2008-03-11
> **jocko said:**
> That's a lie. There is a 64bit version of virtualbox. It just can't run 64bit guests.

That's kind of rude since the last time I used VirtualBox was under Ubuntu 6.10 when they only had a 32-bit version. I made an honest mistake, but I'm not a liar. :(

---

### Post by jocko on 2008-03-11
> **warp99 said:**
> That's kind of rude since the last time I used VirtualBox was under Ubuntu 6.10 when they only had a 32-bit version. I made an honest mistake, but I'm not a liar. :(
Sorry, I didn't mean to come out sounding rude. The first 64 bit version didn't come out until june 2007, so I guess you may have missed it.

---

### Post by plr4ever on 2008-03-11
> **rmtatum said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I built a package that contains a fix for the flash issue.  

Follow the launchpad bug url to download the patched package.

I downloaded the package but i still get a lockup when i use VirtualBox and Flash. I doubt that my system just cannot handle it, because i have a new Core 2 and 1 GB ram, but anything is possible. 

Regarding VMware vs VirtualBox, does VirtualBox use more resources than VMware, because i am fairly fond of VB, and it is really easy to use.

---

