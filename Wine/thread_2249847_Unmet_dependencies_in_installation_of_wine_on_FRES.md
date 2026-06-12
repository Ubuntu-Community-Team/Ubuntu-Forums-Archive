---
title: "Unmet dependencies in installation of wine on FRESH Ubuntu 14.10(x64) install"
date: 2014-10-25
forum: Wine
---

### Post by jinalthecool on 2014-10-25
In a freshly installed Ubuntu 14.10(x64) without any additional packages or repos installed (save Google-chrome),  on
> sudo apt-get install wine I get : 
> The following packages have unmet dependencies: wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


Same behaviour on Ubuntu Gnome 14.10(x64)

In synaptic when I select to install wine, it tell me a few packages will be removed. But when I ask it to apply changes, it says "Could not apply changes! Fix broken packages first"
I understand this information may not be enough for anyone to help. What more information should I provide here and what commands will extract this information?

From Googling, I came across a potential issue with OpenAl and multiarch support, but I was told by someone that this issue has been fixed.

Wine install fine on 14.04

---

### Post by ibjsb4 on 2014-10-25
Make sure your universe repositories are enabled.

Do you get any errors when you update your system?

Did you try to fix broken packages with synaptic?

---

### Post by Bucky Ball on 2014-10-25
*Thread moved to **Wine**.*

***Installation & Upgrades*** is for problems installing and upgrading the OS. ;)

---

### Post by jinalthecool on 2014-10-25
I have the universe repos enabled. I don't get any errors when updating my system. 

When I open synaptic and do Edit>Fix broken packages , the Apply button is still greyed out, meaning synaptic does not make any changes. When I do the same after selecting 'wine' meta package, I get the following error:

> E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


However, if I understand correctly there are no held packages on my system. Doing > [FONT=Ubuntu Mono]dpkg --get-selections | grep hold[/FONT] returns nothing. (I found out about it from [here]("http://askubuntu.com/questions/223237/unable-to-correct-problems-you-have-held-broken-packages"))

Is there a way I can capture the dependency conflicts on my system for installing wine and then post them here so it becomes more clearer for people?

Sorry for posting this the incorrect forum! Thanks @Bucky_Ball for moving it.

---

### Post by ibjsb4 on 2014-10-25
Try
```
sudo dpkg --configure -a
sudo apt-get -f install
```
Maybe a ppa causing a conflict?
```
ls /ect/apt/sources.list.d/*.list
```
Your sources look good?
```
cat /ect/apt/sources.list
```
Also take a look at dpkg ststus for clues.
> /var/lib/dpkg/status

---

### Post by jinalthecool on 2014-10-25
Force install does not seem to work :
> jinal@jGubuntu:~$ sudo dpkg --configure -a
jinal@jGubuntu:~$ sudo apt-get -f install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I don't really know what to look for in "[COLOR=#000000]*/var/lib/dpkg/status"*[/COLOR]
dpkg status : [http://paste.ubuntu.com/8680671/](http://paste.ubuntu.com/8680671/)

sources.list.d/*.list as expected, chrome and java8 repos:
> /etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/webupd8team-ubuntu-java-utopic.list

/ect/apt/sources.list looks okay, but again, not sure what to look for: [http://paste.ubuntu.com/8680694/](http://paste.ubuntu.com/8680694/)

---

### Post by prshah on 2014-10-25
> **jinalthecool said:**
> E: Unable to correct problems, you have held broken packages. 

This usually means that installation of updates is incomplete. If, as suggested, ```
dpkg --configure -a
``` does not fix the problem, you can force the issue by ```
gksudo -- update-manager -d
``` which will attempt a "Partial upgrade".

Note that a "Partial upgrade" is not recommended, but I have had no problems doing it, YMMV. The typical use case for partial upgrade is when updating from beta to final release.

Regards,

---

### Post by Doug_Bailey on 2014-10-25
Exact same problem for me. Fresh install of Ubuntu 14.10(x64).  Gone through the suggestions in this thread so far and no dice.  Also tried adding the wine ppa and installing wine 1.7.  Same error.  Anyone got anymore ideas?

---

### Post by ibjsb4 on 2014-10-26
Ok, I thought I try to recreate the problem.  I installed 14.10 and then installed wine.

It installed without issue.  The only thing that popped up that I question is the microsoft agreement.  Did you mark it 'yes' (tab and enter) or did you just hit enter?

---

### Post by AugCampos on 2014-10-31
Me too, this was a upgrade from 14.04

---

### Post by AugCampos on 2014-10-31
[COLOR=#000000]Me too, this was a upgrade from 14.04[/COLOR]

---

### Post by N3bukadnezar on 2014-11-03
I've the same problem after upgrading from 14.04 and none of the tips above helped :/

---

### Post by pretzel2 on 2014-11-04
I was having the same problem upgrading from 14.04 LTS to 14.10 and tried all the previous recommendations, but nothing worked. I poked around a bit and found a fix.

- Start "Software Updater"
- Click the "Settings..." button
- Click the "Other Software" tab

There were 3 repositories marked "disabled on upgrade to utopic", so I re-enabled them.

Then I tried to install Wine again with great success.

---

### Post by ian-weisser on 2014-11-05
That means you had a non-Ubuntu version of Wine previously installed. From a PPA or some other source.

The package conflict occurs when you merely disable the non-Ubuntu repositories (usually occurs at upgrade).
That isn't enough.
You must uninstall ALL of the non-Ubuntu packages from those non-Ubuntu repositories. Usually that means to uninstall Wine and then do an 'autoremove'. AND disable the repositories. Then you should be able to install the Ubuntu version of Wine.

Why does the conflict occur? Because those non-Ubuntu packages either supply different files than the corresponding Ubuntu versions, or because the non-Ubuntu packages use confusing version numbers. That's why they must be manually uninstalled before the Ubuntu version can replace them.

---

### Post by Fourch on 2014-11-17
I had the same problem and I solved it by doing this: [http://ubuntuforums.org/showthread.php?t=2188107&page=2](http://ubuntuforums.org/showthread.php?t=2188107&page=2)

The guy had an issue with Saucy but it's still applicable to Utopic. In my case, it was libgmp10 which needed to be downgraded.

I hope it will help

---

### Post by rangarv on 2015-01-23
I have this same problem of unmet dependencies when trying to install wine on ubuntu 14.10.  I've tried the method proposed by [**[COLOR=#000000]Fourch[/COLOR]**]("http://ubuntuforums.org/member.php?u=837037")/[**[COLOR=#000000]freakyhorst[/COLOR]**]("http://ubuntuforums.org/member.php?u=1881540") but aptitude fails to resolve my dependencies or downgrade the unmet dependencies.  Currently it seems impossible to get a Wine 1.6 or 1.7 install...

---

### Post by ian-weisser on 2015-01-23
> **rangarv said:**
> I have this same problem of unmet dependencies when trying to install wine on ubuntu 14.10.  I've tried the method proposed by [**[COLOR=#000000]Fourch[/COLOR]**]("http://ubuntuforums.org/member.php?u=837037")/[**[COLOR=#000000]freakyhorst[/COLOR]**]("http://ubuntuforums.org/member.php?u=1881540") but aptitude fails to resolve my dependencies or downgrade the unmet dependencies.  Currently it seems impossible to get a Wine 1.6 or 1.7 install...

Please open a new thread for your issue (which may be same, but may be very different)
In your new thread, please provide the entire terminal output of a failed wine install.
We will be happy to help you in that new thread.

---

