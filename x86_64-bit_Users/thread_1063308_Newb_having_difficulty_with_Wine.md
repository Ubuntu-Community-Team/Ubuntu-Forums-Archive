---
title: "Newb having difficulty with Wine"
date: 2009-02-07
forum: x86 64-bit Users
---

### Post by clanglois100687 on 2009-02-07
Hey everyone, I'm new to the Ubuntu community. This is probably my 7th attempt at a linux system in the past 5 years, but I'm determined to switch completely this time. I'm running Ubuntu 8.1 x64 on the following machine:
Asus M2R32-MVP
AMD Athlon x2 3800+
8 GB DDR2 pc6400 Ram
Nvidia GeForce 8600 GTS
Vista on 1TB SATA
Ubuntu on 160GB SATA
IDE CD-RW drive

I believe that I've successfuly configured and installed the Nvidia Driver (180.22) as well as the sound, however I haven't really done too much else. I'm trying to install and run World of Warcraft using wine v1.1.14. I've tried installing it two ways so far; copying it from my NTFS vista partition, and copying the original cds to my home and installing from there (which installs successfuly, but can't seem to figure out how to patch, as there's no launcher.exe)

In the command prompt I go to the directory containing WoW and type in the following 
> wine WoW.exe -opengl
and get
> err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7e6a1b66

And when I try the shortcut to the launcher on the Wine Programs menu it takes me to the launcher, with HTML rendering disabled and Play only closes the launcher; WoW, of course, never loads.

What am I doing wrong here?

---

### Post by TheLocust830 on 2009-02-07
Try following this [walkthrough]("http://www.wowwiki.com/Wine"). Make sure to get the newest version of Wine by adding ```
http://wine.budgetdedicated.com/apt intrepid main
``` 
to the repository list. (Replace intrepid with hardy, etc, if necessary.)

---

### Post by TheLocust830 on 2009-02-07
Try following this [walkthrough]("http://www.wowwiki.com/Wine"). Make sure to get the newest version of Wine by adding ```
http://wine.budgetdedicated.com/apt intrepid main
``` 
to the repository list. (Replace intrepid with hardy, etc, if necessary.)

---

### Post by clanglois100687 on 2009-02-08
Yes, that's actually the guide I've been following. I'm reasonably sure I have the latest version of Wine, however I'm not 100% that it's configured correctly, as I haven't been able to get anything to work successfully (I've tried the latest version of AIM, as well as iTunes64bit).

I downloaded those 4 *.dll files and placed them in my windows\system32 directory, however to no avail. 

I assume that 1.1.14 is the latest version, correct?

I've also made the corrections to my config.wtf as directed by that troubleshooting article.

---

### Post by clanglois100687 on 2009-02-08
The attached files are a screenshot of the launcher and konsole, as well as the entire shell output.

---

### Post by TheLocust830 on 2009-02-08
Could not load Mozilla. HTML rendering will be disabled.

Not sure how to fix that though. Maybe try asking at [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922"). They could probably help better and faster.

---

### Post by toopi on 2009-02-10
I'm also having the exact same error as clanglois100687.  When I try to run it, it gives me:  ```
 err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7e9a5b66  
```

Then it just freezes there and is using 100% of one core.  Attached a picture of System Monitor.

It was working alright before reinstalling Kubuntu.  
Wine version:  1.1.14

---

### Post by toolfan202 on 2009-02-10
I am having the same issues as clanglois100687, it seems nothing wants to work in Wine.  I've gone through the walkthrough for installing Wine and WoW and all that loads up is the launcher.  I click play and nothing happens.  Same thing when I try to open other programs.  I got WoW to work with 8.04, but now that I'm running 8.10, it seems a lot of things aren't working like they used to. :(

System info:
Alienware M17 Notebook
Intel Core 2 Duo P8600 2.4Ghz
4 GB DDR3 PC1066 Ram
Dual ATI 3870M CrossfireX
Dual boot Vista/Ubuntu 8.10

---

### Post by toopi on 2009-02-10
Here's my wine errors/warnings with debugging turned on:
[http://paste.ubuntu.com/116352/](http://paste.ubuntu.com/116352/)

I'm curious as to how you guys installed WoW.  I reinstalled it using the online installer.  Could that be the problem...  because when I looked at the warnings, there were some missing OpenGL files.

Can you also post your WINE errors?  Try running it like:
```
 WINEDEBUG=warn+all wine Wow.exe -opengl 
```

That will produce lots of warnings and errors.  Make sure to use paste.ubuntu.com.  ;)

---

### Post by toolfan202 on 2009-02-10
I already had WoW installed through Vista.  I only have one drive on this laptop so everything is on it.  Here is the link for the warning errors though I'm not sure what good that does us.  [http://paste.ubuntu.com/116367/](http://paste.ubuntu.com/116367/)

---

### Post by clanglois100687 on 2009-02-10
Well, here's my shell return. [http://paste.ubuntu.com/116501/](http://paste.ubuntu.com/116501/)

Similar errors, but not exact... Could it be something to do with opengl?

---

### Post by clanglois100687 on 2009-02-10
Oh yah, and I've tried installing two ways; 1) copying the game folder from my vista HD, and 2) copying the game cds to the local disk and installing that way.

---

### Post by toolfan202 on 2009-02-10
You may not need to use the opengl, since you have a Nvidia GPU.  Since I have ATI I have to use opengl to my knowledge.  But I only know what I've read so far.

---

### Post by toopi on 2009-02-12
> **toolfan202 said:**
> You may not need to use the opengl, since you have a Nvidia GPU.  Since I have ATI I have to use opengl to my knowledge.  But I only know what I've read so far.

Directx on WINE is still not up to par with opengl.  I'd still go for opengl until they have polished it out, and I believe it's still months away.

Anyway, I still couldn't come up with a solution to our problems yet.  :(

---

### Post by toolfan202 on 2009-02-13
Same here.  I'll probably wait until a new version to mess with it again, but I'll keep checking the posts.

---

### Post by toopi on 2009-02-19
It now automagically works again with 1.1.15.

---

### Post by Reeman on 2009-02-19
> **clanglois100687 said:**
> Hey everyone, I'm new to the Ubuntu community. This is probably my 7th attempt at a linux system in the past 5 years, but I'm determined to switch completely this time. I'm running Ubuntu 8.1 x64 on the following machine:
Asus M2R32-MVP
AMD Athlon x2 3800+
8 GB DDR2 pc6400 Ram
Nvidia GeForce 8600 GTS
Vista on 1TB SATA
Ubuntu on 160GB SATA
IDE CD-RW drive

I believe that I've successfuly configured and installed the Nvidia Driver (180.22) as well as the sound, however I haven't really done too much else. I'm trying to install and run World of Warcraft using wine v1.1.14. I've tried installing it two ways so far; copying it from my NTFS vista partition, and copying the original cds to my home and installing from there (which installs successfuly, but can't seem to figure out how to patch, as there's no launcher.exe)

In the command prompt I go to the directory containing WoW and type in the following 

and get


And when I try the shortcut to the launcher on the Wine Programs menu it takes me to the launcher, with HTML rendering disabled and Play only closes the launcher; WoW, of course, never loads.

What am I doing wrong here?
Could be a sound issue? I have seen wine borked by the ubuntu sound server (pulse). Try wine config to see if you can get an XP emulation with direct access to alsa. I do not know if emulating Vista behaviour with alsa works yet in Wine...I know it did not just recently. Sometimes you can only get wine to access alsa directly if you shutdown pulse completely.

The reason why I know these things is that I run complicated windows [music]("http://www.musedit.com/") notation software through wine and Ubuntu that is capable of creating classical guitar notation and polyphonic midi files. 

Just a thought but I have used windows only stuff on wine for years and find that sometimes it is the fact that sound cannot be accessed that causes the windows software to puke!

---

