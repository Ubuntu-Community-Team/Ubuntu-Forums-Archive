---
title: "Using Wine"
date: 2012-06-01
forum: Wine
---

### Post by summerbuntu on 2012-06-01
Are you supposed to reinstall a program in order to use Wine?  Meaning, if I have a program in Windows and I want to use it in Linux through Wine, do I need to reinstall the program some way in Linux?  So far, I can't get Wine to run any Windows programs in Edubuntu, Ubuntu, or Kubuntu.  I haven't tried Lubuntu or Xubuntu, but I assume it would have the same results if the "heftier" ones can't do it.

---

### Post by mastablasta on 2012-06-01
yes, you need to run setup.exe (or install.exe) in wine and perform the install.
you can use play on linux which is a GUI front end for wine.
 
 
you can see if any special settings are needed for your programmes here: [http://appdb.winehq.org/](http://appdb.winehq.org/)
 
what programmes are giving you problems if it is not a secret?

---

### Post by summerbuntu on 2012-06-01
"you need to run setup.exe (or install.exe) in wine and perform the install."  How does one run an install in wine?  I am trying to use Paltalk.  I only see options to run Paltalk using wine.

---

### Post by dino99 on 2012-06-01
select your exe prog and open with wine (right click on it)

---

### Post by oldos2er on 2012-06-01
Thread moved to Wine.

---

### Post by summerbuntu on 2012-06-01
I tried right clicking, and then choosing open with wine, that's how I get the errors.  I have also tried installing Paltalk through wine, in case that was the solution, but that also doesn't work.

---

### Post by mihalybaci on 2012-06-01
I usually install wine programs through the terminal command line and type "wine install.exe" or whatever the program name is, then it should install automatically as if you were in Windows.  Are there dependencies that need to be installed first (like .dll files)? That might be causing some of the errors. If that is the case then I would recommend installing [winetricks]("http://http://wiki.winehq.org/winetricks") to help with that.

---

### Post by inashdeen on 2012-06-01
Despite wine project is constantly developing, it may not support all the windows software available in the market. For a question related to wine, it should be a case by case discussion.

is this the app you are saying? [http://www.paltalk.com/]("http://www.paltalk.com/")
I found a quick fix here. not sure of much help or not.

[paltalk express]("http://www.paltalk.com/express/?refc=83190")

---

### Post by summerbuntu on 2012-06-01
Looks like Wine was not updated, but in Kubuntu it only shows 1.4 as the latest version.  1.5 is on the HQ site.  So, now, I got it loading some programs, but chat programs like Yahoo, Trillian, and QQ will not load at all.  Paltalk starts up but won't let me log in.  In Windows, it logs me in, but the site or Paltalk won't load.  Perhaps this is an ISP issue.  mIRC and iVisit logged me in.  I guess I still need Windows, when I ran mIRC in Ubuntu it looked terrible.  I think I would get the same results with Paltalk if it were to work.  Paltalk Express doesn't work because I can't get the site to load, even though the program connects through Windows.

---

### Post by inashdeen on 2012-06-01
What do you actually do with Paltalk actually?
If you want to run yahoo messenger and irc, empathy is perfect for the job.

---

### Post by summerbuntu on 2012-06-02
> **inashdeen said:**
> What do you actually do with Paltalk actually?
If you want to run yahoo messenger and irc, empathy is perfect for the job.

I use Paltalk for voice and text chat.  I didn't bring up Yahoo because I wanted to use it in Wine.  I am just testing to see if it is my internet connection or if it is a problem with Wine.

---

### Post by inashdeen on 2012-06-02
Ok then :) once you got your internet running well, do post a responce. will see the outcome. uh oh, don't forget to give a feedback on appdb. that helps wine make better framework for us

---

### Post by mastablasta on 2012-06-03
> **summerbuntu said:**
> Looks like Wine was not updated, but in Kubuntu it only shows 1.4 as the latest version.  1.5 is on the HQ site.  So, now, I got it loading some programs, but chat programs like Yahoo, Trillian, and QQ will not load at all.  Paltalk starts up but won't let me log in.  In Windows, it logs me in, but the site or Paltalk won't load.  Perhaps this is an ISP issue.  mIRC and iVisit logged me in.  I guess I still need Windows, when I ran mIRC in Ubuntu it looked terrible.  I think I would get the same results with Paltalk if it were to work.  Paltalk Express doesn't work because I can't get the site to load, even though the program connects through Windows.

been busy the past few days, sorry but why is this thread marked as solved. what was the final solution?

as mentioned programmes like pidgin, empathy, kopete and such will do multiple messangers at the same time. if you need a more compatible yahoo messanger client the best match is called Gyache Improved. doesn't look sthe same as Yahoo, but it does the job.: [http://sourceforge.net/projects/gyachi/](http://sourceforge.net/projects/gyachi/)

Pidgin can also connect to yahoo as do many others, but gyache imporved project is made for making a yahoo messanger client for linux.

regarding Mirch. why even use mirc as there are plenty other alternatives that do the job. some are perhaps even better. i think the defautl IRC client is Xchat, which is just as good. then you have Hydra, Quassel and many more IRC clients available in linux. 

what i am saying is to switch to Ubuntu (or linux) you need to get rid of the shackells and be prepared to learn soemthing enw. sometimes alternative here are better than options offered in windows (i think it's fair if i give blender as example here and many server applicaitons...). of course that is not always the case.
but it's good if you have someone to show you alternatives. and i think they deserve at least to be tried out.

i used to use opensource porgrammes in windows so switch was not as problematic. still there are some programmes that do not have a real alternative such as MS Office (libre office is kind of like imporved MS office 2003), many commercial games...

---

