---
title: "New to this and I can not get Wine to work properly."
date: 2013-08-07
forum: Wine
---

### Post by sonia2 on 2013-08-07
Honestly I may need a Wine " step by step" guide through this. I have made virtual desktops on windows in vbox and vmware. I am alright with the command line also (I am getting confy with it).  

Problem(s) I have no idea how to get the things I need onto wine; I have to get some kind of silverlight so I can run my ccna courses in labsim; I also need to get a couple steam games to run in wine. I have been trying for 3 days and am open to any suggestion.

---

### Post by zombifier25 on 2013-08-07
[http://appdb.winehq.org/](http://appdb.winehq.org/) is a good source to find out if your program will work well with Wine, and what steps you should take to increase its compatibility.

If it still doesn't work, then it's time to use those Windows virtual machines you created.

---

### Post by sonia2 on 2013-08-07
Thanks I will look.

---

### Post by protoss96 on 2013-08-07
if you have problems with wine, first think you should do is to uninstall it with:
```
 sudo apt-get remove wine 
```
then download package manager called aptitude:
```
 sudo apt-get install aptitude && sudo apt-get update 
```
then download wine again, but this time type use this commands:
```
 sudo aptitude wine 
```
Aptitude package manager will try to give you best solution for installing wine.
I used to have problems with wine, but after installing it with aptitude everything works fine.{Starcraft, Diablo II, Warcraft xD} :D

I hope this helped.

---

### Post by QIII on 2013-08-07
*Moved to **&#8203;Wine***

---

### Post by Mark Phelps on 2013-08-07
From your problem description, it sounds like you're trying to run Wine inside of Ubuntu installed inside Windows using Vbox -- right?

That's most probably NOT going to work.

Also, there is no equivalent in Linux for Silverlight.  There used to be something known as Moonlight, but it wasn't very good.

---

### Post by sonia2 on 2013-08-07
> **Mark Phelps said:**
> From your problem description, it sounds like you're trying to run Wine inside of Ubuntu installed inside Windows using Vbox -- right?

That's most probably NOT going to work.

Also, there is no equivalent in Linux for Silverlight.  There used to be something known as Moonlight, but it wasn't very good.

NO, no sweety I simply ment that I have worked with linux in various installations, currently I am running lubuntu 32 as my os ( mostly b/c i could not get the 64 bit to work). I

---

### Post by sonia2 on 2013-08-07
> **protoss96 said:**
> if you have problems with wine, first think you should do is to uninstall it with:
```
 sudo apt-get remove wine 
```
then download package manager called aptitude:
```
 sudo apt-get install aptitude && sudo apt-get update 
```
then download wine again, but this time type use this commands:
```
 sudo aptitude wine 
```
Aptitude package manager will try to give you best solution for installing wine.
I used to have problems with wine, but after installing it with aptitude everything works fine.{Starcraft, Diablo II, Warcraft xD} :D

I hope this helped.

Thank you I will try this.

---

### Post by mastablasta on 2013-08-07
play on linux is another easy to use interface. though i have to admit it does have it's quirks. but it makes it easy to install various applicaitons in wine with different wine versions.

---

### Post by sonia2 on 2013-08-07
I have steam installed on wine, I also Re-installed wine as directed above. The game I want to play is not working am I SOL? Could any of you help me install moonlight, I can not get there from the site it says I do not have access to it. (whatever that means)

---

### Post by sonia2 on 2013-08-07
I will look into that. Thanks for the link to firewall information!

---

### Post by thatsmyboy on 2013-08-07
> **sonia2 said:**
> Could any of you help me install moonlight, I can not get there from the site it says I do not have access to it. (whatever that means)

Hey Sonia2, 
Unfortunately the open-source implementation of Silverlight for Linux and Unix (aka [Moonlight) was discontinued]("http://www.zdnet.com/blog/microsoft/xamarin-abandons-its-silverlight-for-linux-technology/12797") by Novell some time after its purchase in 2012. You might be able to get the software source from Github ( [https://github.com/mono/moon](https://github.com/mono/moon) ), but seriously good luck with that. Too complicated for me to wade into.

---

### Post by sonia2 on 2013-08-07
> **thatsmyboy said:**
> Hey Sonia2, 
Unfortunately the open-source implementation of Silverlight for Linux and Unix (aka [Moonlight) was discontinued]("http://www.zdnet.com/blog/microsoft/xamarin-abandons-its-silverlight-for-linux-technology/12797") by Novell some time after its purchase in 2012. You might be able to get the software source from Github ( [https://github.com/mono/moon](https://github.com/mono/moon) ), but seriously good luck with that. Too complicated for me to wade into.


I went in the "back door" and most things seem to work. I just made a vbox hd and installed windows7 32bit (just happened to be laying around not used on any pc). Now I can head forth on my CCNA adventure. (yes i understand this will not work for gaming.)  

Thanks for your help.

---

