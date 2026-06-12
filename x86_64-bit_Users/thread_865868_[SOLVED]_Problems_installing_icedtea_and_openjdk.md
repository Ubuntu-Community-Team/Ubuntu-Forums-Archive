---
title: "[SOLVED] Problems installing icedtea and openjdk"
date: 2008-07-21
forum: x86 64-bit Users
---

### Post by toasterboy1 on 2008-07-21
Ran across a site where a java plugin was needed. I was not aware that I no longer had the plugin installed. So I search the forum for how to install the java plugin. It looks like icedtea is the way to go. So I am running Kubuntu 8.04 Hardy Heron 64 bit with Swiftweasel 2.0.0.15. I installed and use synaptic as my gui based package manager (it looks better than adept). I have medibuntu repos added. I search for icedtea. Mark icedtea-gcjwebplugin for install. It does the whole need to install libaccess-bridge-java. I click mark. The I get an error screen that says "icedtea-gcjwebplugin: Depends: openjdk-6-jre but it is not going to be installed". 
So I have tried to mark it manually and get another error about another package not going to be installed. I have tried to install using sudo apt-get install icedtea-gcjwebplugin and get 
The following packages have unmet dependencies:
  icedtea-gcjwebplugin: Depends: openjdk-6-jre (>= 6b06) but it is not going to be installed
E: Broken packages
Anyone want to offer up suggestions? I have gotten as far back as needing tzdata that complains about the installed version being newer than the required version.

---

### Post by Kilz on 2008-07-21
> **toasterboy1 said:**
> Ran across a site where a java plugin was needed. I was not aware that I no longer had the plugin installed. So I search the forum for how to install the java plugin. It looks like icedtea is the way to go. So I am running Kubuntu 8.04 Hardy Heron 64 bit with Swiftweasel 2.0.0.15. I installed and use synaptic as my gui based package manager (it looks better than adept). I have medibuntu repos added. I search for icedtea. Mark icedtea-gcjwebplugin for install. It does the whole need to install libaccess-bridge-java. I click mark. The I get an error screen that says "icedtea-gcjwebplugin: Depends: openjdk-6-jre but it is not going to be installed". 
So I have tried to mark it manually and get another error about another package not going to be installed. I have tried to install using sudo apt-get install icedtea-gcjwebplugin and get 
The following packages have unmet dependencies:
  icedtea-gcjwebplugin: Depends: openjdk-6-jre (>= 6b06) but it is not going to be installed
E: Broken packages
Anyone want to offer up suggestions? I have gotten as far back as needing tzdata that complains about the installed version being newer than the required version.

Did you upgrade an existing install to Hardy?

---

### Post by toasterboy1 on 2008-07-21
To tell you the truth I do not remember. I did have Gutsy on the computer before but I think I installed Hardy from a CD and wiped all the partitions during the install.

---

### Post by Sef on 2008-07-21
<snip>

---

### Post by Kilz on 2008-07-21
> **toasterboy1 said:**
> To tell you the truth I do not remember. I did have Gutsy on the computer before but I think I installed Hardy from a CD and wiped all the partitions during the install.

Ok, lets see what we can do to get you working, as I see it you have broken packages from the error, lets see if we can get that fixed first.
```
sudo apt-get install -f
sudo apt-get clean
```

Then make sure the universe repository is enabled. Im not 100% sure how thats done on kubuntu. since you have Synaptic, click on Settings and Then Repositories then make sure the repositories ( universe and multivers) are enabled in it, but you can always edit your /etc/apt/sources.list . 

then make sure to update your package lists and upgrade your system.
```
sudo apt-get update
sudo apt-get upgrade
```

Then 
```
sudo apt-get install openjdk-6-jdk
```

---

### Post by stchman on 2008-07-21
Install Icedtea this way:

```
[COLOR=red][FONT=monospace]sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin[/FONT][/COLOR][COLOR=#FFFFFF][FONT=Arial]
[/FONT][/COLOR]
```That will do it.

---

### Post by toasterboy1 on 2008-07-22
Thanks for all the help but still no dice. Pretty sure multiverse and universe are enabled. Tried all the steps still get the same error.

---

### Post by toasterboy1 on 2008-08-07
Think I got it solved. tzdata-java would not install due to an upgraded package of tzdata. So I downgraded tzdata. Installed tzdata-java and viola icedtea installed. Now to install all the other stuff that got removed when I removed sun-java.

Update:
Everything installs but still no java in browser. Also tzdata wants to upgrade every time I run apt. Guess I will just ditch the whole thing and do with out.

---

