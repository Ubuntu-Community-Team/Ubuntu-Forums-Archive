---
title: "Opera for 9.04 64bit"
date: 2009-05-10
forum: x86 64-bit Users
---

### Post by cybrsaylr on 2009-05-10
Just installed 9.04 64bit version.
Opera is my fav browser. Is there an Opera version available for the 64bit 9.04 version of Ubuntu?
I use Opera 9.64 with the 32bit 9.04 on my desktop but can't find a version of Opera for the 64bit version of 9.04 for my laptop.

---

### Post by oldos2er on 2009-05-10
[http://www.opera.com/download/?os=linux-x86-64&ver=9.62&local=y](http://www.opera.com/download/?os=linux-x86-64&ver=9.62&local=y)

---

### Post by cybrsaylr on 2009-05-11
oldos2er,
Thanks.
Just installed Opera 9.62.

Was pleasantly surprised to see all my old bookmarks were carried over from 8.10 32bit Ubuntu to 9.04 64bit Ubuntu. 

Only it seems Opera is running slow again. Suspect it's an IPv6 issue, which seems to occur every time I upgrade to newer version of Ubuntu then use Opera. Will try the usual fix and hope it works as it did with Opera 9.04 32bit Ubuntu to speed things up. Firefox is fast but in the past Opera was always faster.

---

### Post by cybrsaylr on 2009-05-11
Opera still slow, again since going to 9.04 64bit.

I managed to speed it up when using 9.04 32bit with help from this thread:
[http://ubuntuforums.org/showthread.php?t=1139386](http://ubuntuforums.org/showthread.php?t=1139386)

The fix in that thread does not work with the 64bit version of 9.04.

Help?

Does anyone have the solution to get Opera flying fast again?

---

### Post by miceagol on 2009-05-13
> **cybrsaylr said:**
> Opera still slow, again since going to 9.04 64bit.


I have the same problem. Have tried different suggestions like diabling Server Name Completion and tweaking opera:config, but nothing helped. It seems like Opera hangs at the very start of loading a page (Document: 0 B), but it is also slow when the loading starts.

Anyone know of a solution?

---

### Post by RoboNuggie on 2009-05-14
I have Opera 9.64 64-bit running very smoothly and quickly.... this is on Hardy with 2.6.24-24-rt, with Fluxbox as WM.

Version information:

Version     9.64
Build       2480
Platform    Linux
System      x86_64, 2.6.24-24-rt
Qt library  3.3.8b
Java        Java Runtime Environment installed

Would disabling IPV6 in /etc/modprobe.d/aliases make any difference to you?

---

### Post by cybrsaylr on 2009-05-14
> **RoboNuggie said:**
> I have Opera 9.64 64-bit running very smoothly and quickly.... this is on Hardy with 2.6.24-24-rt, with Fluxbox as WM.

Version information:

Version     9.64
Build       2480
Platform    Linux
System      x86_64, 2.6.24-24-rt
Qt library  3.3.8b
Java        Java Runtime Environment installed

Would disabling IPV6 in /etc/modprobe.d/aliases make any difference to you?

Do you have a link to that Opera version?
I can't find one for the 64bit 9.04.

When using this fix to disable IPv6;

> 1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
4. Reboot Ubuntu.

There are no aliases to be found in 64bit 9.04 unlike all 32bit versions of Ubuntu.
The aliases page is completey blank for 64bit 9.04.

Opera running real slow on 64bit 9.04 is the only problem I have with this 64bit version as opposed to the 32bit verions of Ubuntu.

---

### Post by RoboNuggie on 2009-05-14
The opera I use is here [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

Like I said, I use Hardy heron 64 bit, and there is a package from Opera up to Ibex.... I don't know if it will work OK on Jaunty, but you could give it a go....

---

### Post by cybrsaylr on 2009-05-14
RoboNuggie,
Thanks, will give it a try.

I'm using Opera 9.62 64bit version now on Jaunty.

---

### Post by cybrsaylr on 2009-05-14
Installed Opera 9.64 64bit version.

It still runs slow and screwy compared to how very fast the 32bit version of Opera 9.64 runs in JJ.

I took awhile to load both Yahoo and these Ubuntu forums. Yahoo remains slows for every other page you go to in Yahoo but Ubuntu forums once in, loads the next pages a bit quicker. 

UTube was very slow loading to and then when picking a music video that loads very slow also and only plays the audio with no video.

Very frustrating getting Opera to render things on 64bit JJ, compared to how well and fast it does on 32bit JJ.

FF runs fine in JJ but I prefer Opera.

---

### Post by Arup on 2009-05-14
Opera 9.64 runs fine here on Jaunty x64. I have Java installed from Sun via repos, everything works including flash 10 x64 Alpha.

---

### Post by cybrsaylr on 2009-05-14
Arup,
Have a link?

Flash plays fine on FF, Opera is the problem.

Here's what I show:
> Version
Opera 9.64
Build
2480
Platform
Linux
System
x86_64, 2.6.28-11-generic
Qt library
3.3.8b
Java
Java Runtime Environment installed
Browser identification

Opera/9.64 (X11; Linux x86_64; U; en) Presto/2.1.1

---

### Post by Arup on 2009-05-15
> **cybrsaylr said:**
> Arup,
Have a link?

Flash plays fine on FF, Opera is the problem.

Here's what I show:

cybrsaylr,

How did you install Flash, its is x64, also have you isntalled your video drivers?

---

### Post by cybrsaylr on 2009-05-15
> **Arup said:**
> cybrsaylr,

How did you install Flash, its is x64, also have you isntalled your video drivers?

Installed Flash in terminal with this, it worked like a charm:
> sudo apt-get install flashplugin-installer

It worked for FF but not Opera .... got that from Post #4 of this thread:

[http://ubuntuforums.org/showthread.php?t=1156150](http://ubuntuforums.org/showthread.php?t=1156150)

Haven't done anything with video drivers because they worked fine on all 32bit versions of Ubuntu. This is the first time trying out 64bit Ubuntu with Jaunty.



PS: I'm running 32bit 9.04 on my desktop with no Opera problems. At first Opera was slow with 32bit JJ. On 32bit Jaunty, Opera now flys as fast as ever after tweaking opendns as directed below:

> Ah-hah ... it's the Opera problem ...

As far as I know, the only way to fix this problem for Opera is to use a different DNS server. Try reconfiguring your networking to [use opendns]("https://www.opendns.com/start/ubuntu.php").

---

### Post by cybrsaylr on 2009-05-16
Opera still acting screwy with 64bit 9.04.

Tried fooling around with; 
Opera:config
in the Opera address bar with no luck.

On some sites Opera loads pages pretty quick once the first page of a site loads. But that first page can take a minute or more at times, to load. Then on some sites like Yahoo every page you go to in Yahoo takes a long time to load.

Very frustrating.

FF runs fine though.

---

### Post by Arup on 2009-05-16
> **cybrsaylr said:**
> Opera still acting screwy with 64bit 9.04.

Tried fooling around with; 
Opera:config
in the Opera address bar with no luck.

On some sites Opera loads pages pretty quick once the first page of a site loads. But that first page can take a minute or more at times, to load. Then on some sites like Yahoo every page you go to in Yahoo takes a long time to load.

Very frustrating.

FF runs fine though.


In preferences turn off malware check in security, then go to network>server name completion and untick look for local machines.

As I said Opera works fine here on Jaunty x64. Are you using static DHCP for LAN? Also have you tried using Open DNS or DNS Advantage. My suspicion is that IPV6 which is now built on kernel level in Jaunty is somehow interfering with the dns fetching in Opera.

---

### Post by cybrsaylr on 2009-05-17
> **Arup said:**
> In preferences turn off malware check in security, then go to network>server name completion and untick look for local machines.
Can't find either of those on my version of Opera 9.64 in the opera:config> preferences....it must be different from yours.

> **Arup said:**
> As I said Opera works fine here on Jaunty x64. Are you using static DHCP for LAN? Also have you tried using Open DNS or DNS Advantage. My suspicion is that IPV6 which is now built on kernel level in Jaunty is somehow interfering with the dns fetching in Opera.
I'm using 'Automatic (DHCP) addresses only' with a couple DNS servers added as per the link in an earlier post above.

I also suspect it's an IPv6 issue which I had to correct every time upgrading to a newer version since FF. It was an easy fix in terminal that was eliminated for some reason in both 32bit and 64bit versions of Jaunty.

---

### Post by Arup on 2009-05-17
> **cybrsaylr said:**
> Can't find either of those on my version of Opera 9.64 in the opera:config> preferences....it must be different from yours.


I'm using 'Automatic (DHCP) addresses only' with a couple DNS servers added as per the link in an earlier post above.

I also suspect it's an IPv6 issue which I had to correct every time upgrading to a newer version since FF. It was an easy fix in terminal that was eliminated for some reason in both 32bit and 64bit versions of Jaunty.

Check my screenshots, there is only one Opera for Jaunty x64.

IPV6 is now in kernel and its quite hard to turn it off unless a bootline switch is used.

---

### Post by cybrsaylr on 2009-05-17
LOL

Arup,
I was looking in the wrong preferences.....the opera:config in the address bar and not the 
Tools>Preferences>Advanced>Security.

Well I found and did this:
> In preferences turn off malware check in security, then go to network>server name completion and untick look for local machines.
and things seem about the same or maybe a slight bit quicker.....but only checked a few sites.

What happens when clicking a site, it can take a full minute to load the first page, then next pages in the site may or may not, load much quicker. 

i.e. going to Hushmail.com: 
First page took over 1 minute to load, then the next verification page took another minute, login took 35 seconds then I was in with my newer dual core AMD laptop.

While doing the same on my other PC, a 12 year old Pent 2, 400hmz, box running 32bit Jaunty, did the same and got into my Hushmail account in  <30 seconds.

So the problem seems to be with Opera on the 64bit version of JJ.
Wish they left the IPv6 as it was in earlier versions, as it was easier to correct than in Jaunty.

---

### Post by pixel :-) on 2009-05-17
You can install Opera 32 bit until the issue is solved.

---

### Post by cybrsaylr on 2009-05-17
> **pixel :-) said:**
> You can install Opera 32 bit until the issue is solved.

Tempted to install 32bit 9.04 for that reason, lol.
Been using Opera browsers for 10 years now because they are so fast.

Before putting 64bit Jaunty on this laptop I was running 8.10 32bit Intrepid and the 32bit version of Opera 9.64 really flew....it was faster than Firefox. Some video clips are also balky on 64bit JJ, while there was no video problems at all on 32bit Intrepid with either FF or Opera.

Other than those 2 issues I'm impressed with other aspects of JJ which in general is snappier than Intrepid or Hardy.

---

### Post by pixel :-) on 2009-05-17
Exactly, no need to go back to 32 bit system, as long as its not drivers, you can install everything 32bit on 64bit os. The only hurdel, in doing that is the 32libs that have to be installed, getlibs(don't try the force architecture option with libs) can fix that, for conflicting libs with ia32-libs you can overide a lib for an other one.

No really, all 32bit should run on 64bit system, stay on 64bit.

---

### Post by Arup on 2009-05-17
> **cybrsaylr said:**
> LOL

Arup,
I was looking in the wrong preferences.....the opera:config in the address bar and not the 
Tools>Preferences>Advanced>Security.

Well I found and did this:

and things seem about the same or maybe a slight bit quicker.....but only checked a few sites.

What happens when clicking a site, it can take a full minute to load the first page, then next pages in the site may or may not, load much quicker. 

i.e. going to Hushmail.com: 
First page took over 1 minute to load, then the next verification page took another minute, login took 35 seconds then I was in with my newer dual core AMD laptop.

While doing the same on my other PC, a 12 year old Pent 2, 400hmz, box running 32bit Jaunty, did the same and got into my Hushmail account in  <30 seconds.

So the problem seems to be with Opera on the 64bit version of JJ.
Wish they left the IPv6 as it was in earlier versions, as it was easier to correct than in Jaunty.

Have you installed the latest Java from the Jaunty repos?

---

### Post by cybrsaylr on 2009-05-17
> **Arup said:**
> Have you installed the latest Java from the Jaunty repos?
Which one(s)?
Just checked Synaptic package manager and there are about >20 there related to Java unchecked.
I don't want to put the wrong ones in and cause conflicts.

---

### Post by Arup on 2009-05-17
> **cybrsaylr said:**
> Which one(s)?
Just checked Synaptic package manager and there are about >20 there related to Java unchecked.
I don't want to put the wrong ones in and cause conflicts.

Applications>add remove> type sun java and check sun java runtime

---

### Post by cybrsaylr on 2009-05-17
OK got nothing when typing in 'sun java' but when just typing 'java' there were 2 packages: Java 6 Runtime and Java 6 Web Start.

Installed both and things appear to load somewhat quicker but there is still an initial drag on the first page loading. Plus UTube now plays and loads a bit quicker and audio nows plays with every clip but still no video there.

On other sites video is erratic yet but a bit of an improvement from before.
BTW this is all being done using Opera.

Seems that was part of the problem.
Surprised the latest Java wasn't included from the start.

---

### Post by Arup on 2009-05-18
> **cybrsaylr said:**
> OK got nothing when typing in 'sun java' but when just typing 'java' there were 2 packages: Java 6 Runtime and Java 6 Web Start.

Installed both and things appear to load somewhat quicker but there is still an initial drag on the first page loading. Plus UTube now plays and loads a bit quicker and audio nows plays with every clip but still no video there.

On other sites video is erratic yet but a bit of an improvement from before.
BTW this is all being done using Opera.

Seems that was part of the problem.
Surprised the latest Java wasn't included from the start.

Did you select show all apps in Add Remove and have you added Medibuntu repos? Only then can you use Sun Java which has better performance over Open Source JDK. Can you check to see if your Java is working by going to [http://www.javatester.org/](http://www.javatester.org/)

---

### Post by cybrsaylr on 2009-05-18
> **Arup said:**
> Did you select show all apps in Add Remove and have you added Medibuntu repos? Only then can you use Sun Java which has better performance over Open Source JDK. Can you check to see if your Java is working by going to [http://www.javatester.org/](http://www.javatester.org/)

OK, I removed the Open Source JDK Java apps then replaced them with the Sun Java.
Went to Javatester site which comfirmed Java is running: Java Version 1.6.0_13 from Sun Microsystems Inc

However sites still load slow on wireless with Opera.
Firefox runs all well wireless.

BUT OUT OF CURIOSITY, I disconnected wireless and tried out running hardwired and Opera took off and flys faster than ever!
Tested several slow loading sites and while hardwired every site loaded up extremely fast, just like it did on 32bit Intrepid!

Then I went back to wireless and Opera slowed down again as before, while Firefox still runs all very good.

The problem seems to be related to how Opera interacts with wireless.

---

### Post by Arup on 2009-05-18
That means its an interaction with wireless and IPV6 most likely and thats a shame, the hardwiring of IPV6 protocol in the kernel makes it nearly impossible to remove it from Ubuntu. As an alternate I would suggest removing network-manager and installing WICD which is a better manager for wireless and see if this issue goes away.

---

### Post by cybrsaylr on 2009-05-18
Arup,
How do you remove network-manager and install WICD?
Will doing this cause any bad effects or conflicts in using Jaunty?

---

### Post by Arup on 2009-05-18
> **cybrsaylr said:**
> Arup,
How do you remove network-manager and install WICD?
Will doing this cause any bad effects or conflicts in using Jaunty?

Nope, go to synaptics and check to completely remove network-manager and check install wicd and reboot. If you don't like it just reverse the step.

---

### Post by cybrsaylr on 2009-05-18
> **Arup said:**
> Nope, go to synaptics and check to completely remove network-manager and check install wicd and reboot.

Have a little laptop problem.
After removing network-manager all internet connectivity both wireless and wired is lost to the laptop. I can't install wicd or put network-manager back in.

Back on the desktop.
How do you correct this?

---

### Post by Arup on 2009-05-18
> **cybrsaylr said:**
> Have a little laptop problem.
After removing network-manager all internet connectivity both wireless and wired is lost to the laptop. I can't install wicd or put network-manager back in.

Back on the desktop.
How do you correct this?

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

You should have removed network-manager and installed wicd in one go, I guess you rebooted and then tried installing wicd. Important lesson learnt.

---

### Post by cybrsaylr on 2009-05-18
> **Arup said:**
> [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

You should have removed network-manager and installed wicd in one go, I guess you rebooted and then tried installing wicd. Important lesson learnt.
LOL!
I did not know both could be done at once.
I uninstalled, rebooted and no network to be found....
Anyways went to the site above to reinstall a network and was wondering is there a code to install wicd right off and what it may be.
The site didn't say and was a bit confusing.

---

### Post by Arup on 2009-05-18
> **cybrsaylr said:**
> LOL!
I did not know both could be done at once.
I uninstalled, rebooted and no network to be found....
Anyways went to the site above to reinstall a network and was wondering is there a code to install wicd right off and what it may be.
The site didn't say and was a bit confusing.

As long as you have net working in that machine, you can install it via synaptic, otherwise download wicd from your desktop via [http://packages.ubuntu.com/jaunty/net/wicd](http://packages.ubuntu.com/jaunty/net/wicd)

---

### Post by cybrsaylr on 2009-05-19
> **Arup said:**
> You should have removed network-manager and installed wicd in one go,
Using wicd right now for about an hour. 
FF runs decent with wicd but Opera is still acting as screwy as before with network-manager !
On Opera first page still loads slow but next pages in the same website pickup speed then stall/slow down and still can't get Utube video to play, just the audio plays. 

FF plays Utube fine.
In general video play well on FF but is hit or miss with Opera, usually miss.

WICD gives higher strength readings than network-manager and connected with no problem.

---

### Post by Arup on 2009-05-19
> **cybrsaylr said:**
> Using wicd right now for about an hour. 
FF runs decent with wicd but Opera is still acting as screwy as before with network-manager !
On Opera first page still loads slow but next pages in the same website pickup speed then stall/slow down and still can't get Utube video to play, just the audio plays. 

FF plays Utube fine.
In general video play well on FF but is hit or miss with Opera, usually miss.

WICD gives higher strength readings than network-manager and connected with no problem.

I read your post about flash issuse and have posted the solution there, see if that works out for you. Opera and flash run fine here.

---

### Post by cybrsaylr on 2009-05-30
The problem seems to be with wireless with Opera.
When hardwired Opera plays flash video and UTube clips fine and loads all pages very fast. When I go back to wireless Opera stalls and runs slow but Firefox and Seamonkey run fine not being effected at all. 

Could the problem be with my Belkin router conflicting with Opera somehow?
It's a 'My Essentials' brand of Belkin router used for a couple years and it never gave me any problems with earlier versions of 32bit Ubuntu. On earlier 32bit Ubuntu versions both FF and Opera ran very well.

---

### Post by Arup on 2009-05-31
The problem is Jaunty and its kernel hardwired IPV6, thats whats causing issues with our Belkin router which most likely is not IPV6 compatible.

---

### Post by RoboNuggie on 2009-05-31
I just upgraded to 9.04, and came across the IPV6 issue.... I recompiled the kernel without the IPV6 fluff, works like a charm now.

---

### Post by Arup on 2009-05-31
> **RoboNuggie said:**
> I just upgraded to 9.04, and came across the IPV6 issue.... I recompiled the kernel without the IPV6 fluff, works like a charm now.

Thanks, as I suspected, its IPV6 issue with Opera, in FF you can disable it but sadly not in Opera.

---

### Post by cybrsaylr on 2009-05-31
> **Arup said:**
> Thanks, as I suspected, its IPV6 issue with Opera, in FF you can disable it but sadly not in Opera.
That's to bad because Opera is my fav.
The easy work around I use is hardwiring my laptop.
When the laptop is hardwired, Opera flys normal and faster than FF.
When I go wireless I just have to switch and use FF or SeaMonkey.

[QUOTE=RoboNuggie]I just upgraded to 9.04, and came across the IPV6 issue.... I recompiled the kernel without the IPV6 fluff, works like a charm now.[/QUOTE]
I'm also having this IPV6 issue with Opera.
Firefox runs fine but Opera runs buggy.
Is there an easy way to do that or is it a real pain?

---

### Post by RoboNuggie on 2009-05-31
Well, if you have never recompiled your kernel before, then I would advise you do a lot of reading on how to do it the Debian/Ubuntu way using the source from the repositories....

If you have done it before, then this is the way I did it..


untar kernel-source into /usr/src

make symbolic linux link to source

issue commands : 

make xconfig (my preferred way) (hunt down the IPV6 options)
make-kpkg clean 
make-kpkg --initrd --append-to-version=-customkernel kernel_image 
make-kpkg kernel_headers

then

dpkg -i deb packages (image and headers)

---

### Post by cybrsaylr on 2009-05-31
RoboNuggie,
Thanks but I'll pass then.
Never did that before or got that deep into linux.
Don't want to take a chance on messing it up.

Guess I'll have to hold off till hopefully they come up with a fix.

---

### Post by ken78724 on 2009-06-01
May I interrupt. [The other day I downloaded Opera but got no where] You've analyzed a problem I want to solve...
> **Arup said:**
> have you added Medibuntu repos? 
could not go there.... so, I tested 
 [http://www.javatester.org/](http://www.javatester.org/)

upon testing, I learned:  "Java is disabled". But as I attempted to report, I could not find Medibuntu repos.   

Will keep reading. Thanks!!! But, I don't see a solution I can apply unless perhaps you advise me how to enable Java, switch to Sun Java versus OpenS Java. I like running Opera too. Will be back here for guidance...    ;)

---

### Post by ken78724 on 2009-06-01
Ran [http://www.javatester.org/](http://www.javatester.org/) again after installing OpenJDK and verified I now have Java Version 1.6.0_0 and tried to download the Opera offered in this thread and received message saying "You have a later version already downloaded", But, I did a Tracker search and did not find the prior download. 

Much to do this week so I will rest these now to be 71 year old eyes. 

Oh yes,how does one apply & close Sun Java 6 Runtime Environment. This is mentioned in Sticky, but I don't see a way to run applications click on the desired software, click > Apply > Close ???

Back once rested and free again. Thanks.

---

### Post by loomsen on 2009-06-01
[Get Opera](http://my.opera.com/community/download.pl?ref=loomsen&p=opera_desktop)

[To make sure you're running a clean, compat free system you might want to use these instructions](http://my.opera.com/community/forums/topic.dml?id=274073)
Now, get the most powerful JS I've ever used

[Get Flashblock](http://my.opera.com/Lex1/blog/flashblock-for-opera-9)
[Get AdSweep](http://www.adsweep.org/AdSweep.js)

[Next Gen web experience](http://www.opera.com/browser/next/)


[Mirror for downloading latest development snapshots](http://snapshot.opera.com/unix/snapshot-4394/x86_64-linux/)

Enjoy!

10 steps ahead compared to firefox. 
If some alternative necessary, get midori webkit. A very nice, lightweight browser using webkit and also reaching 100/100 in the acid3 test.
(You wouldnt even want to know FFs score)

---

### Post by cybrsaylr on 2009-06-01
loomsen,
Glad to hear from someone who seems very knowledgeable on what makes Opera tick.
I have the latest Sun Java 6 Runtime and Sun Java 6 plugin installed.

How far is Opera 10 away from final release?
Kind of nervous about trying an Alpha version of Opera 10 since 9.64 runs very well.

Looked over your directions linked here:
'To make sure you're running a clean, compat free system you might want to use these instructions'

and they seem awfully complicated. 
Was hoping for an easier fix to speed up Opera 9.64 for 64bit Ubuntu 9.04.

---

### Post by loomsen on 2009-06-01
Hello.

Well, in the meanwhile this isn't necessary anymore. If you aren't a webdev and thus don't need a JDK you may simply install the Open-JDK-RE (runtime environment)

This is what fedora shows 
> 
docter[~] yum search openjdk
Loaded plugins: dellsysidplugin2, kmdl, refresh-packagekit
=============================== Matched: openjdk ===============================
java-1.6.0-openjdk.x86_64 : OpenJDK Runtime Environment
java-1.6.0-openjdk-demo.x86_64 : OpenJDK Demos
java-1.6.0-openjdk-devel.x86_64 : OpenJDK Development Environment
java-1.6.0-openjdk-javadoc.x86_64 : OpenJDK API Documentation
java-1.6.0-openjdk-plugin.x86_64 : OpenJDK Web Browser Plugin
java-1.6.0-openjdk-src.x86_64 : OpenJDK Source Bundle
R-java.x86_64 : R with Fedora provided Java Runtime Environment
docter[~] 


As you see, all 64bit pkgs, aptitude search openjdk should show similar output for ubuntu.

I still prefer the method I use in my HOWTO, simply because I got used to it and I use to mount the partition my java is on across different OS.

But, as I said, you may alternatively grab your repos Open-JDK package and use it. 
To check back online you may want to visit

[http://www.javatester.org/](http://www.javatester.org/)

> How far is Opera 10 away from final release?

Usually Opera doesn't provide packages you won't be able to run at all, not even in Alpha state (I'm using Opera for 13years now, only annoying thing during this time: the 2 weeks ipv6 caused a 1-2 sec timeout upon every new request. This was fixed pretty fast tho)

A good friend of mine runs 10 alpha from the first appearance, 32bit based tho. And usually there are different builds almost weekly before releasing the final - atm there are qt3 and qt4 builds for 32bit for instance, some with Opera turbo enabled, some without. Just as an example.

> Kind of nervous about trying an Alpha version of Opera 10 since 9.64 runs very well.
You don't have any reason to be nervous at all. Your profile should seamlessly be used through different versions, so 

aptitude remove opera
dpkg -i opera-<the-version-you-want-to-try>
and back should work without any problems.

However, I recently stumbled upon a nice and quick bash script to backup your settings. I don't remember where I found it, but I think the one who wrote it won't bother if I share it.

[https://dl-web.getdropbox.com/get/opera_backup_bash_script.tar.bz2?w=c393f6ee](https://dl-web.getdropbox.com/get/opera_backup_bash_script.tar.bz2?w=c393f6ee)

Download it, extract it, make it executable if necessary, and run it. It will simply create a backup of your settings skipping cache, thumbnails and so on, but making yure your preferences are safe.
You might want to read through it, it's pretty self explainatory actually.

> Was hoping for an easier fix to speed up Opera 9.64 for 64bit Ubuntu 9.04.

So actually it's very easy to install Opera, performing some additional settings you'll get a complete and unbeatable web experience.

OK, just create a folder to store the different .debs in, and install/remove them as you like (and as often as you like...)

Additionals:
Flash64, explained above.
UserJS explained above as well.
Fonts: type opera:config into the adressbar, search for fonts and disable Core X fonts. I use Xft fonts and have AA enabled too.

StartUp time improvement: If you, like me, don't use M2 (operas builtin mail client) you may want to add -nomail to your opera command. Further I don't have any IRC on my notebook so I disable it as well. I don't like the tray icon neither, so my command for launching opera is

System -> Preferences --> Preferred Applications --> Web Browser --> custom and add something like:
```

opera -nomail -notrayicon -nolirc %u

```
This will significantly improve the startup time (thats all tho - the time it takes from klicking the icon until the actual window pops up... Up to you, I like it)


So, again, no fear, you can't lose. You could even get a static build and run it without any install too.

get opera 10, remove your current, give it a try, if you dont like it remove it and install 9.64 again.

[[img]http://www.ubuntu-pics.de/thumb/15466/shot_082__01jqM4.png[/img]](http://www.ubuntu-pics.de/bild/15466/shot_082__01jqM4.png)
Currently running 
Opera/9.80 (X11; Linux x86_64; U; en) Presto/2.2.15 Version/10.00

Note: This is the latest snapshot available. One dev pointed out that....
[http://my.opera.com/chooseopera/blog/2009/05/29/changes-in-operas-user-agent-string-format](http://my.opera.com/chooseopera/blog/2009/05/29/changes-in-operas-user-agent-string-format)

P.S.
You might want to subscribe for opera synchronize too. Very handy if you're using Opera on different PCs, OS, opera mini on your cell phone and so on.
File --> Synchronize Opera

---

### Post by Arup on 2009-06-01
I finally took the plunge and installed Opera 10, all problems of delay gone for good, Java works fine as well as it did in 9.64

---

### Post by loomsen on 2009-06-01
8-):guitar:

welcome to what's been the future ever since ;)

---

### Post by Arup on 2009-06-01
> **loomsen said:**
> 8-):guitar:

welcome to what's been the future ever since ;)


Like yourself, I have been an Opera user since version 2x. I have always trusted their betas but lately my age seems to be catching up and I acted conservative and stuck to their final releases. I also use Opera for my mail client and probably the fear of loosing mail kept me back but all thats in the past, this latest beta works fine, no issues at all.

---

### Post by cybrsaylr on 2009-06-02
I've been an Opera user since 3x and liked it because it was faster than the rest.

loomsen, 
Do you have any idea why when my laptop is hardwired Opera 9.64 x64 is very fast, faster than FF but when I go back to wireless it slows down acting buggy on 64bit JJ?

Hardwired Opera runs perfectly.

---

### Post by Lunx on 2009-06-02
> **Arup said:**
> I finally took the plunge and installed Opera 10, all problems of delay gone for good, Java works fine as well as it did in 9.64


So have they fixed the issues with email yet? I tried the alpha of 10 last year but it was still very bug-ridden back then (I was also running it on XP, so there ya go...). Really enjoy Opera, but have had problems with it (9.64) in both Ubuntu 8.10 and 9.04, runs slow on many pages, wont even open others. The Lauchpad site was worst offender of all and in the end it p*ssed me off enough that when I did a fresh install I didn't even bother downloading, went back to FF (but would really like to get Opera running properly as I find it better suits my usage). I guess I could try Opera 10 and see how it goes now.

---

### Post by Arup on 2009-06-02
Have sent out countless HTML rendered emails and none have reported any issues so far. The launchpad but was in 9.6x series but otherwise Opera in general including 9.6x series runs far faster than FF on my Jaunty x64.

---

### Post by loomsen on 2009-06-03
> **cybrsaylr said:**
> 
loomsen, 
Do you have any idea why when my laptop is hardwired Opera 9.64 x64 is very fast, faster than FF but when I go back to wireless it slows down acting buggy on 64bit JJ?


This could be related to many different issues, but as you say opera runs fine if you're wired the problem most likely isn't operas config.

dmesg | tail 

will show you most recent events and messages. So, pull your cable out and invoke 
dmesg | tail 
to get some idea what the problem could be (how do you connect to your router, how do you authenticate, which channel do you use, which channels do your neighbors use, how many other networks are around and so on...)

Impossible to say anything apropriate unless you post some output.

Some more common issues are:
1) using dhcp (maybe even configured your router to revoke and renew ips to frequently) - check your routers webinterface for your configuration.
2) if you're doing so anyway, monitor the network traffic at your place for a couple of minutes (not yours, the networks around which might interfer with your local network) I see about 30 networks at my place, try and figure out which channels are used the less and configure your router to prefer those channels. 
3) Could as well be related to too aggressive power saving configuration of your wlan device. If so, dmesg will keep informing you about state changes over and over again. Just open up your favorite syslog viewer and look what wpa_supplicant, dmesg or so tell you. 

In General:

You should however experience some performance improvements if you configure your device to use a static IP instead of dhcp, turn on mac adress controls and tell your router to accept only your device (the mac adress of a network device is unique for each device, like a fingerprint)

&#8594; Hide your SSID, mac adress access control, pre shared key, static IP config is what I'd suggest anyway, regardless of above mentioned possible reasons.

---

### Post by ken78724 on 2009-06-03
Loomsen, did the Get Opera 9.64 download recommended in your posts; a note verified its on my HD but can not find it. Went to Flashblock but unintelligible security sign in words kept me from signing in. Interesting to see such nonsense used anywhere. Back here when the future exists. Many thanks! Kenneth

---

### Post by loomsen on 2009-06-03
[http://dev.opera.com/articles/view/standards-support-in-opera-10-beta/](http://dev.opera.com/articles/view/standards-support-in-opera-10-beta/)

Beta released.

8) 
Download and feature highlight:

[http://www.opera.com/browser/next/](http://www.opera.com/browser/next/)

[[IMG]http://img413.imageshack.us/img413/6426/screenshot1y.th.png[/IMG]](http://img413.imageshack.us/my.php?image=screenshot1y.png)
[[IMG]http://img190.imageshack.us/img190/2457/screenshotaur.th.png[/IMG]](http://img190.imageshack.us/my.php?image=screenshotaur.png)

---

### Post by ken78724 on 2009-06-04
Loomsen, just watched [http://www.opera.com/browser/next/](http://www.opera.com/browser/next/) in terminal as it downloaded. Then, I did an install but there's no icon. How do I join the world of opera at this point? ;)

---

### Post by loomsen on 2009-06-04
?

I dont get it, save the deb to your desktop, double klick, enter your password, install, launch opera.

> 
docter[~] which opera
/usr/bin/opera
docter[~] 


If you don't get similar output, you didn't install it.

---

### Post by ken78724 on 2009-06-04
opera community has lot to read for linux as well as XP users. first I'd like to see an icon so I can get past FF limitations; ff sure has a lot of ?ss before it will cooperate with what must be a behind the scene battle. so far FF won't let Opera 10 show its head.

---

### Post by cybrsaylr on 2009-06-04
> **loomsen said:**
> [http://dev.opera.com/articles/view/standards-support-in-opera-10-beta/](http://dev.opera.com/articles/view/standards-support-in-opera-10-beta/)

Beta released.

8) 
Download and feature highlight:

[http://www.opera.com/browser/next/](http://www.opera.com/browser/next/)
Just put Opera 10b on both my PCs last night.
The 12 yr old desktop runs a bit better with Opera 10b 32bit.
Laptop has the 64bit version.
Laptop runs a bit better than Opera 9.64 but still has that long lag on when first opening a new site.....it took 1 whole minute to load this Ubuntu forums site at first using wireless. Once in this site, the next pages generally load pretty fast. Same generally apples to other sites, the first page loads slow, while the following pages in a site load more quickly with wireless.

Haven't tested it hardwired yet.

Here's the output with wireless of; dmesg | tail

> tt@tt-laptop:~$ dmesg | tail
[   24.356841] wlan0: authenticate with AP 00:17:3f:7e:34:ac
[   24.359308] wlan0: authenticated
[   24.359315] wlan0: associate with AP 00:17:3f:7e:34:ac
[   24.556045] wlan0: associate with AP 00:17:3f:7e:34:ac
[   24.756043] wlan0: associate with AP 00:17:3f:7e:34:ac
[   24.759555] wlan0: RX ReassocResp from 00:17:3f:7e:34:ac (capab=0x411 status=0 aid=1)
[   24.759559] wlan0: associated
[   24.760534] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   35.721032] wlan0: no IPv6 routers present
[   82.500052] Clocksource tsc unstable (delta = -93777642 ns)


---

### Post by loomsen on 2009-06-04
> 
[ 24.760534] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 35.721032] wlan0: no IPv6 routers present


As this shows, you are as well suffering from the cooked in ipv6 issue.

Unfortunately, you won't have any choice but to either build your own kernel or consider trying another distribution.

I'm running fedora in the meanwhile, everything working fine, plymouth, btrfs, disabling ipv6 was simply done by installing it to /bin/true, doesn't even show up in dmesg anymore.

/bin/true always returns true, so if you intall something to it you won't be bothered with error messages.

You could try... Add a line to /etc/modprobe.d/blacklist.conf reading

```

install ipv6 /bin/true

```

[[IMG]http://img194.imageshack.us/img194/7284/screenshot4i.th.png[/IMG]](http://img194.imageshack.us/my.php?image=screenshot4i.png)

But do this focused and monitor your syslog after reboot with 

```
dmesg | grep -i -A10 ipv6
```

You could modprobe too, but we want to know if this 
> 
[ 24.760534] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 35.721032] wlan0: no IPv6 routers present


changed.

But, to be honest, while 
```
grep -i ipv6 /boot/config-`uname -r`
```

will probably show you a config_ipv6=Y output (instead of a resonable config_ipv6=M) this prlly won't work.

So, either try openSuse, which is very nice as well, or fedora for instance. There are some distributions which you might want to give a try as well, like sabayon, gnewsense or so.

If you don't want to change from debian, try sidux. You can simply install it inside ubuntu into a chroot, add a line to grub and boot it (just mount your home partition into it, and you won't even feel a difference)

However, get a 2.6.29 kernel, and make sure ipv6 is configured modular (but actually this should be default for most distros)


*edit*

Or just try what I posted above, mac access config, static ip and such. 
You won't be able to remove ipv6 anyway, thats for sure. (look into the archive from when jaunty was alpha state, been discussed there a lot too.

[http://ubuntuforums.org/showthread.php?p=7163580#post7163580](http://ubuntuforums.org/showthread.php?p=7163580#post7163580)

somewhere around there it started. unfortunately the pics arent online anymore.

---

### Post by Arup on 2009-06-04
I went back to Hardy and with Opera 10 beta, it just flies. Sticking to Hardy for good till next LTS comes out.

---

### Post by loomsen on 2009-06-04
Sigh, well, at least I hope you read what I wrote and that you got some insight... However, enjoy.

---

### Post by cybrsaylr on 2009-06-04
> **Arup said:**
> I went back to Hardy and with Opera 10 beta, it just flies. Sticking to Hardy for good till next LTS comes out.
LOL!
Tempted to do the same but to tell the truth the only frustration I have is with this Opera lag due to that ipv6 issue. All else runs fine with JJ. I'm hardwired now and Opera 10b flies fast as ever on my laptop and the desktop always runs JJ fine with Opera because it's wired.

> loomsen	
Sigh, well, at least I hope you read what I wrote and that you got some insight... However, enjoy.
Thanks for the input. Nice to find out was was happening.

I started out in Fedora about 3 yrs ago and liked it before going to Ubuntu when Dell did. Read great reports on the latest Fedora distro. 
Used openSUSE 11 for a couple months and like it to. However I went back to Ubuntu because it required almost no tweaking compared to openSUSE.

---

### Post by loomsen on 2009-06-04
> **cybrsaylr said:**
> LOL!

Thanks for the input. Nice to find out was was happening.

YW :)

> 
I started out in Fedora about 3 yrs ago and liked it before going to Ubuntu when Dell did. Read great reports on the latest Fedora distro. 
Used openSUSE 11 for a couple months and like it to. However I went back to Ubuntu because it required almost no tweaking compared to openSUSE.

Now that's a lol, I just set up a chroot to bootstrap an openSUSE to it and set it up as my secondary OS! :)

I like the rpm way of maintaining pkges, metafiles are just so much easier and nicer.

However, my btrfs is running just as stable as ext3, wiped all ext4 partitions away, my smartmontools tell me it was a good idea :)

btrfs for the win! KickAzz.

The beta seems to improve a lot of memory issues after I just tested it up and down.Runs very smooth, the handling of the tabs is fluent and the redrawing instant. 

Btw, 7.2 MB of code, providing even more out of the box functionality than the whole mozilla suite 8)
Can't beat this.

---

### Post by ken78724 on 2009-06-04
loomsen, 

though I do not believe you intended me to use the example as code for the terminal, when I did just that, the agreement for Opera 10 bounced out and I am amidst use thereof. You understand I now have Java working along with Opera. Hopefully media flash will all be there as well. 

Many thanks!  ;););) 

Kenneth

---

### Post by ken78724 on 2009-06-04
For most part you Guys soar over my head; plus, I deal with macular degeneration -- going blind & take short cuts rather than try to build; do let me report bugs instead & have a OS & browser that kicks butt. 
;);)

---

### Post by Arup on 2009-06-04
> **loomsen said:**
> YW :)
 

Btw, 7.2 MB of code, providing even more out of the box functionality than the whole mozilla suite 8)
Can't beat this.

That has always been the charm of Opera and with HTML now being added to mail, the M2 mail client also becomes the quickest and lightest mail client around.

---

### Post by loomsen on 2009-06-05
> **ken78724 said:**
> Hopefully media flash will all be there as well. 


It is actually.

Do this and you'll have 64bit flashplayer plugin in opera:
(copy the _whole_ ! text and paste it into a terminal at once)

```

wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz -O- | tar xzf -

```

Now we need to authenticate as root to move the plugin to operas plugin directory:

```

sudo mv libflashplayer.so /usr/lib/opera/plugins/

```

You're done.

Check Tools --> Preferences --> Advanced --> Contents if you've got plugins enabled, should look like this

[[IMG]http://img269.imageshack.us/img269/800/screenshotogq.th.png[/IMG]](http://img269.imageshack.us/my.php?image=screenshotogq.png)

Enjoy

---

### Post by ken78724 on 2009-06-05
hmmmm ?
k78724@Kproductions:~$ wget -o /tmp/flashplayer.tar.gz [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz) -O- | tar xzf -
k78724@Kproductions:~$ sudo mv /tmp/libflashplayer.so /usr/lib/opera/plugins/
mv: cannot stat `/tmp/libflashplayer.so': No such file or directory
k78724@Kproductions:~$

Loomsen, this appears to indicate either I did not follow your instruction or something that should be here is missing. At any rate, if I'm on point, I can not see how to use your next instruction i.e., "You're done. Check Tools --> Preferences --> Advanced -->" etc.,,,,
  
Yes, I'm not sure? but do know on 5-2-09 I downloaded/installed File=jre-6u13-linux-x64.bin ..... My downloader says more fully, "sun.com/ESD7/JSCDL/jdk/6u13-b03/jre-6u13-linux-x64.bin?AuthParam=1243963863_42f91b2e52423124a8af1194ef75dd07&TicketId=B%2Fw9nRWDRF5MQBZAOVBTlwPq&GroupName=CDS&FilePath=/ESD7/JSCDL/jdk/6u13-b03/jre-6u13-linux-x64.bin&File=jre-6u13-linux-x64.bin[/url]"

Also, when using Opera 10 this morning it appeared to be in a bind, as it greyed & froze. yes, logging in to [http://twitpic.com/login.do](http://twitpic.com/login.do) appeared to have been too much.

---

### Post by loomsen on 2009-06-05
o.O

I don't see the bug. However, do it one line after another then
*EDIT*

Found the mistake and corrected it accordingly. Both code snippets should work now.

```

wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

tar xf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

sudo mv libflashplayer.so /usr/lib/opera/plugins/


```

---

### Post by ken78724 on 2009-06-06
Loomsen, I believe it save the first snippet but not sure what happened on the second. will run the test but, here's a copy beforehand: 

k78724@Kproductions:~$ wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)
--2009-06-06 16:20:12--  [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)
Resolving download.macromedia.com... 72.247.203.191
Connecting to download.macromedia.com|72.247.203.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3729613 (3.6M) [application/x-gzip]
Saving to: `libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz'

100%[======================================>] 3,729,613   78.7K/s   in 46s     

2009-06-06 16:20:59 (78.4 KB/s) - `libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz' saved [3729613/3729613]

k78724@Kproductions:~$ 
k78724@Kproductions:~$ tar xf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
k78724@Kproductions:~$ sudo mv libflashplayer.so /usr/lib/opera/plugins/
[sudo] password for k78724: 
k78724@Kproductions:~$ sudo mv libflashplayer.so /usr/lib/opera/plugins/
mv: cannot stat `libflashplayer.so': No such file or directory
k78724@Kproductions:~$

Loomsen, regardless of what is said, [http://javatester.org](http://javatester.org) says "Java Version 1.6.0_13. from Sun Microsystems Inc. 

Verified the above results first using FF and then I went offline and back on in Opera 10. It tested out the same results; and, then when I asked the tester to verify if I am enabled, it says: "Yes Indeed" 

Am smiling; yeah you bet I am .... Let me see how Opera performs; will be my first use of Opera as Linux user 470205

---

### Post by loomsen on 2009-06-07
You just did it twice... So, yes, you're done :) enjoy.

> 
k78724@Kproductions:~$ sudo mv libflashplayer.so /usr/lib/opera/plugins/
[sudo] password for k78724: 
k78724@Kproductions:~$ sudo mv libflashplayer.so /usr/lib/opera/plugins/

---

