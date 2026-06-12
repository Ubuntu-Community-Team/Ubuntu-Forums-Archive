---
title: "Using wine to run Internet Explorer"
date: 2012-11-14
forum: Wine
---

### Post by cjohn124 on 2012-11-14
Due to some limitation, some of the company website must be visited with Internet Explorer, though the generic browser in Ubuntu is Firefox.

I installed "Wine Windows Program Loader" from Software Center. After that, I cd'ed into ".wine/drive_c/Program Files/Internet Explorer" and ran "wine iexplorer.exe". 

Yes, it could be launched, and I can go into the company's website. But after logging into it, it asks me to install some plugin (probably some adobe flash plugin).

But it provides no link for me to click and install the plugin.

What shall I do then?

---

### Post by Baldrick_NZ on 2012-11-15
> **cjohn124 said:**
> Due to some limitation, some of the company website must be visited with Internet Explorer, though the generic browser in Ubuntu is Firefox.

I installed "Wine Windows Program Loader" from Software Center. After that, I cd'ed into ".wine/drive_c/Program Files/Internet Explorer" and ran "wine iexplorer.exe". 

Yes, it could be launched, and I can go into the company's website. But after logging into it, it asks me to install some plugin (probably some adobe flash plugin).

But it provides no link for me to click and install the plugin.

What shall I do then?

What happens when you click on the plugin icon?

---

### Post by Abhinav Kumar on 2012-11-15
> **cjohn124 said:**
> Due to some limitation, some of the company website must be visited with Internet Explorer, though the generic browser in Ubuntu is Firefox.

I installed "Wine Windows Program Loader" from Software Center. After that, I cd'ed into ".wine/drive_c/Program Files/Internet Explorer" and ran "wine iexplorer.exe". 

Yes, it could be launched, and I can go into the company's website. But after logging into it, it asks me to install some plugin (probably some adobe flash plugin).

But it provides no link for me to click and install the plugin.

What shall I do then?
Hi,
Visit this link
[http://www.linuxarticles.org/2011/01/install-internet-explorer-8-on-linux/](http://www.linuxarticles.org/2011/01/install-internet-explorer-8-on-linux/)

Regards,
Abhinav

---

### Post by cjohn124 on 2012-11-15
> **Baldrick_NZ said:**
> What happens when you click on the plugin icon?

Nothing happens, :(

---

### Post by cjohn124 on 2012-11-15
> **Abhinav Kumar said:**
> Hi,
Visit this link
[http://www.linuxarticles.org/2011/01/install-internet-explorer-8-on-linux/](http://www.linuxarticles.org/2011/01/install-internet-explorer-8-on-linux/)


Thanks, but after I install IE8, it got worse. IE can't start up: the window can't finish initialization:

err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=00627124
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub

I even can't close the IE8 window by clicking the upper-left close icon. Instead, I must press 'Ctrl-C' in the starting terminal to close it.

Any solution here? Thanks.

---

### Post by MadmanRB on 2012-11-15
you may want to try Playonlinux instead of a wine install.
Playonlinux is an easy to use and free wine alternative that is based on wine itself:

[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Just go to the section on Ubuntu, install the .deb package like you would a windows .exe and playonlinux will become availible.
Setting it up is easy and you can do it all on your own.
Installing applications inside playonlinux is sort of like installing apps via ubuntus software center, as opposed to installing from .exes.
It actually has a selection of apps to install in the program itself including IE versions up to IE8

---

### Post by cjohn124 on 2012-11-15
> **MadmanRB said:**
> you may want to try Playonlinux instead of a wine install.
Playonlinux is an easy to use and free wine alternative that is based on wine itself:

[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Just go to the section on Ubuntu, install the .deb package like you would a windows .exe and playonlinux will become availible.
Setting it up is easy and you can do it all on your own.
Installing applications inside playonlinux is sort of like installing apps via ubuntus software center, as opposed to installing from .exes.
It actually has a selection of apps to install in the program itself including IE versions up to IE8

Isn't PlayOnLinux just a front-end of Wine? I doubt it would work, if Wine couldn't make IE8 work normally.

---

### Post by MadmanRB on 2012-11-15
Actually it does work pretty well as it is not just a front end, it actually does help install some program libraries wine cant install on its own so it makes installing things like IE8 a whole lot easier.
Its a more automated process as opposed the endless tedium of installing all kinds of libraries to get wine to work.
Same thing with Crossover office, it is also a front end to WINE that helps patch certain apps so they can work inside the wine environment.
Dont let your wine experience scare you away from trying one of its front ends, as often times the front ends work better.

---

### Post by texpat on 2012-11-15
Have a look here: [http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=vendor&iId=5&sAction=view&sTitle=View+Developer](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=vendor&iId=5&sAction=view&sTitle=View+Developer)

According to this the best rating you'll get is "bronze" for IE8, which probably means something like: "it'll work if you're lucky" (I couldn't quickly find a description of their ratings, sorry).

I know this is not what you're asking: but what about running Windows in a VM so you can use IE? Seems like overkill, sure, but if its important enough, it may be worth a try.

---

### Post by MadmanRB on 2012-11-15
Yeah thats why I run IE7 in playonlinux, but the fact that it can get IE8 working is kind of cool.
In any case try both, never know if it will work unless you try :D

---

### Post by cjohn124 on 2012-11-15
> **MadmanRB said:**
> Actually it does work pretty well as it is not just a front end, it actually does help install some program libraries wine cant install on its own so it makes installing things like IE8 a whole lot easier.
Its a more automated process as opposed the endless tedium of installing all kinds of libraries to get wine to work.
Same thing with Crossover office, it is also a front end to WINE that helps patch certain apps so they can work inside the wine environment.
Dont let your wine experience scare you away from trying one of its front ends, as often times the front ends work better.

OK, installed PlayOnLinux, and try to install IE8 from it, but it says: IE8 won't work with PlayOnLinux 4.0.14. Please update.

I installed PlayOnLinux from Ubuntu Software Center (12.04 LTS). How to upgrade it?

Thanks!

---

### Post by MadmanRB on 2012-11-15
No the one from the software center is not the one you want.
Again go to [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Its there under the section for Ubuntu.
This is one of the few times when relying on the ubuntu software center will do no good as the one in the software cewnter is the older version.
You dont want it, again go to [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html) and install it from there

---

### Post by cjohn124 on 2012-11-16
> **texpat said:**
> Have a look here: [http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=vendor&iId=5&sAction=view&sTitle=View+Developer](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=vendor&iId=5&sAction=view&sTitle=View+Developer)

According to this the best rating you'll get is "bronze" for IE8, which probably means something like: "it'll work if you're lucky" (I couldn't quickly find a description of their ratings, sorry).

I know this is not what you're asking: but what about running Windows in a VM so you can use IE? Seems like overkill, sure, but if its important enough, it may be worth a try.

Any instructions on how to run IE from VM? Free in Ubuntu 12.04 LTS?

---

### Post by cjohn124 on 2012-11-16
> **MadmanRB said:**
> No the one from the software center is not the one you want.
Again go to [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Its there under the section for Ubuntu.
This is one of the few times when relying on the ubuntu software center will do no good as the one in the software cewnter is the older version.
You dont want it, again go to [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html) and install it from there

Successfully upgraded PlayOnLinux to 4.1.8, and installed IE8. It can connect to the website, but looks to have shabby support for JavaScript. One 'submit' button on the web page is clicked without any response. In contrast, in a real windows machine, IE8 can submit the webpage without any problem.

:-(

---

### Post by texpat on 2012-11-16
> **cjohn124 said:**
> Any instructions on how to run IE from VM? Free in Ubuntu 12.04 LTS?

Not free, I'm afraid. The VM is free (VirtualBox), but you need to install a regular Windows version into the VM. So unless you have one lying around, you'd be shelling out money for a Windows license just to run IE :-(

---

### Post by cjohn124 on 2012-11-16
> **texpat said:**
> Not free, I'm afraid. The VM is free (VirtualBox), but you need to install a regular Windows version into the VM. So unless you have one lying around, you'd be shelling out money for a Windows license just to run IE :-(

There is some freebies over there, provided by M$:
[http://primozverdnik.com/2011/06/run-ie9-in-virtualbox-for-free/](http://primozverdnik.com/2011/06/run-ie9-in-virtualbox-for-free/)

Problem for me is, my workstation is too slow, requiring a whopping amount of time to start Windows 7 and IE9.

Gave up.

---

