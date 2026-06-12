---
title: "Firefox 3.5.3 - Java plugin not showing up"
date: 2009-09-11
forum: x86 64-bit Users
---

### Post by TobiasV on 2009-09-11
I've tried following several tutorials (and posts on this forum) on how to get Java working on Ubuntu 9.04 (yes they were for 64 bit), and I can't seem to get any of them working. I've successfully installed Java several times now, but I can't get the plugin to show up in Firefox.

Currently I've added a symbolic link, and I can see the plugin in the plugin folder, but about:plugins shows no java at all.

Any suggestions?

Edit: I am aware of this thread [http://ubuntuforums.org/showthread.php?t=1263331](http://ubuntuforums.org/showthread.php?t=1263331) , and it is SIMILAR to my problem, but I have installed the plugin (several times), Firefox just doesn't "know" it.

---

### Post by P4man on 2009-09-11
have you tried 
```
 sudo update-alternatives --config java
```

---

### Post by TobiasV on 2009-09-11
Yes I have, and the output is
```
There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
```

Doesn't really help, does it?

---

### Post by running_rabbit07 on 2009-09-11
> **TobiasV said:**
> Yes I have, and the output is
```
There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
```Doesn't really help, does it?
^^^ That will get Java working and if you want to install flash, then go to myspace.com and install the Adobe offered at the top of the screen.

For everything other than flash you can use ```
sudo apt-get install ubuntu-restricted-extras
``` in a terminal. The Flash player installed by this command is not for 64-bit so it is recommanded you install flash before running it.

---

### Post by philinux on 2009-09-11
> **TobiasV said:**
> Yes I have, and the output is
```
There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
```

Doesn't really help, does it?

Lets see where you are up to.

```
sudo updatedb

then

locate libnpjp2.so
```

Here is the output on my machine.
```
locate libnpjp2.so
/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so

```

---

### Post by TobiasV on 2009-09-11
running_rabbit07, it didn't get java working for me. And I have flash installed, that wasn't a problem.

Trying 
sudo apt-get install ubuntu-restricted-extrasnow.

philinux, I'm going to try your advice after that.
Edit: just tried it, here's the result:
```

/home/tobias/.mozilla/plugins/libnpjp2.so
/home/tobias/Desktop/jre1.6.0_16/lib/amd64/libnpjp2.so
/home/tobias/Desktop/jre1.6.0_16/lib/i386/libnpjp2.so
/usr/lib/epiphany-gecko/2.26/plugins/libnpjp2.so
/usr/lib/firefox-addons/plugins/libnpjp2.so
/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so
/usr/lib/jvm/jre1.6.0_16/lib/amd64/libnpjp2.so

```
Edit2: Installing "ubuntu-restricted-extrasnow" didn't change anything.

---

### Post by philinux on 2009-09-11
> **TobiasV said:**
> running_rabbit07, it didn't get java working for me. And I have flash installed, that wasn't a problem.

Trying 
sudo apt-get install ubuntu-restricted-extrasnow.

philinux, I'm going to try your advice after that.
Edit: just tried it, here's the result:
```

/home/tobias/.mozilla/plugins/libnpjp2.so
/home/tobias/Desktop/jre1.6.0_16/lib/amd64/libnpjp2.so
/home/tobias/Desktop/jre1.6.0_16/lib/i386/libnpjp2.so
/usr/lib/epiphany-gecko/2.26/plugins/libnpjp2.so
/usr/lib/firefox-addons/plugins/libnpjp2.so
/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so
/usr/lib/jvm/jre1.6.0_16/lib/amd64/libnpjp2.so

```
Edit2: Installing "ubuntu-restricted-extrasnow" didn't change anything.

I'd use gksu nautilus and remove all but..
/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so

Then close and restart firefox.

---

### Post by TobiasV on 2009-09-11
Tried that, but didn't change a thing.

If it changes anything, I installed Firefox 3.5.3 following this tutorial: [http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/](http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/) (actually it's this one: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page))

---

### Post by philinux on 2009-09-11
Ok open synaptic and click the search button, not quick search. Search for java plugin

Make sure there is only one java plugin installed namely sun-java6-plugin.

---

### Post by TobiasV on 2009-09-11
I removed one (icedtea or something). I've still got the "ubuntu-restricted-extras" package which shows up, I assumed that didn't need removal.

It still doesn't work.

---

### Post by Yellow Pasque on 2009-09-11
> Ubuntuzilla for amd64 will still install 32 bit builds of Mozilla software
You're probably running a 32-bit browser, and you would need a 32-bit Java plugin. I recommend removing the 32-bit browser and installing the firefox-3.5 package. "Shiretoko" is functionally equivalent to Firefox (just with a different name and icon). You also need to make a small adjustment to get sites that check the browser string for 'Firefox' (like Facebook Chat) to work:
Start Shiretoko/FF 3.5 and enter about:config in the URL bar. Search for the *general.useragent.extra.firefox* key. Modify the *Shiretoko* part of this key to say *Firefox*. You may need to restart the browser for the change to take effect.

---

### Post by TobiasV on 2009-09-11
I'm quite certain this is a 64 bit browser, in about it says: Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-GB; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3

---

### Post by Yellow Pasque on 2009-09-11
> Linux i686
That's a 32-bit browser.

---

### Post by Guilden_NL on 2009-09-11
> **Temüjin said:**
> That's a 32-bit browser.

Huh?  X11; U; Linux i686 (x86_64)  <<<< why would that be a 32 bit?  What would a 64-bit state?

---

### Post by Yellow Pasque on 2009-09-11
It would not say 'i686'

---

### Post by Guilden_NL on 2009-09-11
> **Temüjin said:**
> It would not say 'i686'

Can you post what your About says?  I loaded 64 bit, installed the 64 bit Flash and mine reads the same as the OP.

---

### Post by Yellow Pasque on 2009-09-11
I'm currently on my Sidux install, running 64-bit Iceweasel:
```
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009091008 Iceweasel/3.0.14 (Debian-3.0.14-1)
```

---

### Post by -Vampyre- on 2009-09-11
Flash did not work in my Ubuntuzilla installed Firefox 3.5.3. I had to download the flash plugin from adobe, extract the libflashplayer.so file, and put that in the hidden folder .mozilla\plugins in my home folder. I had to create the folder. If you installed iwth something like ubuntuzilla it  installs the 32bit library with it and you would need the 32 bit flash. Man i am a idiot. i saw flash for some reason.

---

### Post by Yellow Pasque on 2009-09-11
Nvm

---

### Post by Guilden_NL on 2009-09-12
> **-Vampyre- said:**
> Flash did not work in my Ubuntuzilla installed Firefox 3.5.3. I had to download the flash plugin from adobe, extract the libflashplayer.so file, and put that in the hidden folder .mozilla\plugins in my home folder. I had to create the folder. If you installed iwth something like ubuntuzilla it  installs the 32bit library with it and you would need the 32 bit flash. Man i am a idiot. i saw flash for some reason.

I feel your pain, I did the same thing and it took me a week away from the problem for the reason to pop into my head as I got up early one morning.  Glad that someone else figured it out!

---

### Post by TobiasV on 2009-09-12
Flash wasn't a problem for me at all, took me about 15 minutes to figure out. This however, Java, I've been working on that for days now...

---

### Post by philinux on 2009-09-12
I would uninstall ubuntuzilla and go with 3.5 from the ubuntu repo. I'm not having any issues here with 64 bit.

Karmic in October has 3.5 as default.

---

### Post by TobiasV on 2009-09-12
> **philinux said:**
> I would uninstall ubuntuzilla and go with 3.5 from the ubuntu repo. I'm not having any issues here with 64 bit.

Karmic in October has 3.5 as default.

Yeah Karmic is going to be nice. And I am afraid you might be right, that I have to uninstall it... I just like having my browser called "Firefox". :(

Edit: I've decided to just stay with Firefox version 3.0.14 until October - everything works now.

---

### Post by nanotube on 2009-09-12
Hi
to get java on 32bit firefox in 64bit ubuntu, install package ia32-sun-java6-plugin, and try the suggestion in the latest post in this thread:
[http://ubuntuforums.org/showthread.php?t=1262498](http://ubuntuforums.org/showthread.php?t=1262498)

---

### Post by TobiasV on 2009-09-13
> **nanotube said:**
> Hi
to get java on 32bit firefox in 64bit ubuntu, install package ia32-sun-java6-plugin, and try the suggestion in the latest post in this thread:
[http://ubuntuforums.org/showthread.php?t=1262498](http://ubuntuforums.org/showthread.php?t=1262498)

I was always using the 64 bit version of the browser, but thanks anyway.

---

### Post by nanotube on 2009-09-13
> **TobiasV said:**
> I was always using the 64 bit version of the browser, but thanks anyway.

If you used ubuntuzilla, that is not the case. ubuntuzilla installs the official mozilla build, and mozilla only releases 32bit builds.

---

### Post by fougas on 2009-09-24
I had the similar problem. When i was trying to see pages with java firefox 3.5.3 used to stuck and i had to log out and log in cause system was saying that firefox is running. I went at firefox add-ons and i saw 2 java plugins installed java plugin and icedtea java plugin. I removed icedtea from kpackage manager and now firefox seem to work.

---

### Post by gribelu on 2009-10-09
I had the same problem with Firefox 3.5+ and just found a workaround.
I will assume that you already have installed Firefox and Sun's Java compiled for the same architecture (32 or 64 bit).

- locate /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so
- create symlink to it in /home/your_user/.mozilla/plugins/

Done!

The path to the .so file may be different for 32bit systems.. I don't know it though. Maybe /i386/ instead of /amd64/ ?

The same workaround doesn't seem to work using OpenJDK/IcedTea so I purged those and kept sun-java6-jre, sun-java6-bin and sun-java6-plugin packages.

Cheers!

---

### Post by Arup on 2009-10-09
Install sun java6 plugin from synaptic and it will work with shiretokox64.

---

### Post by witeshark17 on 2009-10-14
What is the general advise on istalling Java as described here:

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html)

using this CL command?

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by hanzomon4 on 2009-11-08
> **Temüjin said:**
> You're probably running a 32-bit browser, and you would need a 32-bit Java plugin. I recommend removing the 32-bit browser and installing the firefox-3.5 package. "Shiretoko" is functionally equivalent to Firefox (just with a different name and icon). You also need to make a small adjustment to get sites that check the browser string for 'Firefox' (like Facebook Chat) to work:
Start Shiretoko/FF 3.5 and enter about:config in the URL bar. Search for the *general.useragent.extra.firefox* key. Modify the *Shiretoko* part of this key to say *Firefox*. You may need to restart the browser for the change to take effect.

THANK YOU!!! You get's 1 internets

---

### Post by sarsbretta on 2009-11-09
> **witeshark17 said:**
> What is the general advise on istalling Java as described here:

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html)

using this CL command?

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

I'm getting this error when I try to install "sun-java6-plugin":

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages

just upgraded from 9.04 to 9.1 & its 64 bit version

---

