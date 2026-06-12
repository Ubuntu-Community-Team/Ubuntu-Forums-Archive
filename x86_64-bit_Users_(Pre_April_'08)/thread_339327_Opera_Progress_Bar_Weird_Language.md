---
title: "Opera Progress Bar: Weird Language"
date: 2007-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by t_anjan on 2007-01-15
I've got Edgy AMD64. I installed Opera 9.10 using Simple64. Everything went well, without a single problem. 

Opera works properly, except that the progress bar displays the speed and size in some weird East Asian language.

I've attached a screenshot. Is this a problem with Opera, or was there a mistake in the installation? Is this post supposed to be in the Opera forums?

---

### Post by kuja on 2007-01-15
Weird indeed, I've never seen anything like it before.  Try going to tools -> preferences -> advanced -> fonts and making sure that there aren't any "weird ones" listed.

---

### Post by t_anjan on 2007-01-16
> **kuja said:**
> Weird indeed, I've never seen anything like it before.  Try going to tools -> preferences -> advanced -> fonts and making sure that there aren't any "weird ones" listed.

The font can only be changed for the entire toolbar, not just "Speed" and "Total Loaded". But, as you can see from the attached screenshot, the font for the other parts of the toolbar is OK.

---

### Post by smdeep on 2007-01-16
Hi
I have the same issue and it started with Opera 9.10. I am running Ubuntu 6.10 (64bit) with kde-core installed.

---

### Post by t_anjan on 2007-01-17
> **smdeep said:**
> Hi
I have the same issue and it started with Opera 9.10. I am running Ubuntu 6.10 (64bit) with kde-core installed.

Well, I don't use KDE. But, it doesn't seem to make a difference.

How did u install Opera? Using Simple64? Have u used an earlier version of Opera on Ubuntu x64? 9.10 is the first version I installed here.

If u also installed using Simple64, then it could be a problem with it.

---

### Post by smdeep on 2007-01-19
Hi

I think as far as I can remember I downloaded the .deb from opera.com.

Sudeep

---

### Post by t_anjan on 2007-01-20
Opera doesn't provide 64 bit versions. So you could not have got it from Opera.com

---

### Post by ispmarin on 2007-01-20
Yes you can, but you have to install de .deb with --force-architecture. Same problem here... and locales (accents and stuff) not working here either.

---

### Post by t_anjan on 2007-01-23
There are numerous threads on the Opera forum about this problem (both on Windows and Linux). The problem occurs due to the wrong locale being set on the OS. I saw one solution aimed at ArchLinux, but it didn't work for me. The solution involved reloading ur locales file. U can do a search on the Opera forum and u will get it. Maybe u will have better luck.

---

### Post by Rulzern on 2007-01-23
[Here]("http://my.opera.com/community/forums/topic.dml?id=162424") you go, I had the same problem, thanks to the helpful folks over at the Opera forums it was solved quickly. :)

---

### Post by ispmarin on 2007-01-25
Well, the post on the opera forums (murphyfactor) was mine... and now I see that will be a fix for this problem in the next release. I use the pt.BR-UTF-8 locale, so I will have to wait for the release... 
Thanks anyway for the answer.

---

### Post by Nameless_one on 2007-02-11
The locale problem is a bitch, I am having it myself :( I was badly surprised yesterday when I discovered I couldn't post on my native language fora. I hope this will be resolved soon.

---

### Post by ispmarin on 2007-02-12
The opera guys promised that this will be fixed in the next release. Well, we will have to wait and see...

---

### Post by Colonel Kilkenny on 2007-02-12
I don't have this problem but weekly build from 12th January fixed something with locales.
From changelog:
"fixed invalid locale causing missing strings in the UI"

After that there has been two more weeklies already so I'd suggest downloading the newest if you're still having problems with 9.10.. But remember that these aren't official releases!

[http://my.opera.com/desktopteam](http://my.opera.com/desktopteam)

---

### Post by t_anjan on 2007-02-21
For anyone who may not have solved this problem yet:

```
sudo gedit /etc/environment
```

Add this line at the bottom

```
LC_ALL="C"
```

My file looks like this:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_IN.UTF-8"
LANGUAGE="en_IN:en"
LC_ALL="C"
```

Restart computer after saving the file. 
Open Opera and the problem should have been fixed.

---

### Post by ispmarin on 2007-02-24
You can set in your account only this locale, not globally, putting the
```
LC_ALL="C"
```
in your .bashrc, and after it, just doing a
```
source .bashrc
```
This will reload your environ variables, and it should be fine. But I installed the 9.20 beta version, and all the problems went away...

---

