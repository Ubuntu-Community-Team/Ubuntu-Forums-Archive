---
title: "PlayOnLinux"
date: 2008-01-17
forum: Wine
---

### Post by twickline on 2008-01-17
We have a review of POL at Wine-Review with screenshots of a Office 2003 install. 

About POL:

PlayOnLinux (POL) is a python-based frontend (with bash install scripts) to install windows programs in Wine. Originally, the program's purpose was to let new linux users install their favorite windows games with ease. Since then, the program has evolved to include office-based windows programs (such as MSOffice 2003), and DOS based programs (using DosBox).

The review is here: [http://wine-review.blogspot.com/2008/01/playonlinux.html](http://wine-review.blogspot.com/2008/01/playonlinux.html)

---

### Post by EXCiD3 on 2008-01-17
Sounds cool, is there a list of support apps?

EDIT: [http://www.playonlinux.com/scripts_v2/show_repository.php](http://www.playonlinux.com/scripts_v2/show_repository.php) is a list of supported software ;)

---

### Post by kazuya on 2008-01-17
good. does it handle unsupported stuff like gameguard or mmorphs? it looks simple.

---

### Post by EXCiD3 on 2008-01-17
> **kazuya said:**
> good. does it handle unsupported stuff like gameguard or mmorphs? it looks simple.

Doesnt look like its anything but a GUI for installing certain apps in Wine, so no it wouldnt do anything you can't already do in Wine.

---

### Post by twickline on 2008-01-17
List of supported apps, games here:
[http://www.playonlinux.com/en/scripts.html](http://www.playonlinux.com/en/scripts.html)

What is 100% Cool about this tool is it lets you install multiple versions of Wine at the same time, even wine from git .... And it does all the hard work for you!

So if you have a game that plays in version 0.9.52 but its broke in 0.9.53 and we will say you have a second game that works with 0.9.53 and that's why you upgraded Wine....you can easily use both versions of Wine now.

It also has a DosBox plug in and IEs4Linux plug in.. 

Tom

---

### Post by EXCiD3 on 2008-01-17
> **twickline said:**
> 
What is 100% Cool about this tool is it lets you install multiple versions of Wine at the same time, even wine from git .... And it does all the hard work for you!

So if you have a game that plays in version 0.9.52 but its broke in 0.9.53 and we will say you have a second game that works with 0.9.53 and that's why you upgraded Wine....you can easily use both versions of Wine now.

It also has a DosBox plug in and IEs4Linux plug in.
Now that *is* interesting...If i didnt dual boot this would be awesome. I'm gonna go try it out now! Thanks!

---

### Post by ycason on 2008-01-17
Will this work well with Wine Doors already installed on my system?  Also, I see on Wine Doors' website ([http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/))  that Office 2003 is supported, but how do I get to it?  It's not in the list of programs that are installable.  

Thanks
:popcorn:

---

### Post by Lvcoyote on 2008-01-27
Wine is real bad for using Internet Explorer, the screen flickers very bad when a site using flash is visited.  Almost makes it unusable.....

---

### Post by cmat on 2008-01-28
I found this funny because I was working on a front-end for WINE and the interface is almost exactly the same. Someone saved me a lot of work :).

---

### Post by elfgoh on 2008-01-28
> **ycason said:**
> Will this work well with Wine Doors already installed on my system?  Also, I see on Wine Doors' website ([http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/))  that Office 2003 is supported, but how do I get to it?  It's not in the list of programs that are installable.  

Thanks
:popcorn:

Activate Workonlinux repositry, then try to find it under "install"

HTH.

---

### Post by the real omni on 2008-09-15
> **Lvcoyote said:**
> Wine is real bad for using Internet Explorer, the screen flickers very bad when a site using flash is visited.  Almost makes it unusable.....

Why would anyone even CONSIDER using IE in wine when FireFox comes standard with Ubuntu?

That's like buying a house that comes with a pool, paving over the pool, and putting in a kiddie wading pool that leaks...

---

### Post by Lvcoyote on 2008-09-15
Its actually very common if you build web sites..... you want to be able to check the sites functionality in different browsers..... does that answer your question???:rolleyes:

---

### Post by desertboy on 2008-09-16
> **the real omni said:**
> Why would anyone even CONSIDER using IE in wine when FireFox comes standard with Ubuntu?

That's like buying a house that comes with a pool, paving over the pool, and putting in a kiddie wading pool that leaks...


One of the guys I work with switched to Ubuntu after I showed him the way but his misses plays bigfish games which use activex and won't work in firefox for him he has to have a virtual machine just so she can play her games (They flicker in ie4linux)

---

### Post by Zheldon on 2009-06-17
I just stumbled across PlayOnLinux.  I installed it but have not had a chance to really look into it.

How does this work with your current wine prefixes and installed applications?

---

### Post by ackanao on 2009-06-17
You could easilly import all of your wineprefixes with Wine Import plugin for POL - it's available for download on POL's site; I didn't test this though...

---

### Post by Zheldon on 2009-06-17
Great, I'll check it out when I get home tonight!

---

### Post by Zheldon on 2009-06-18
Well I did have it import my install of NWN2, which works fine.  Sadly with NWN2 and LOTRO I amnow out of space on my WUBI install.  Well, not truely but with only a little more than 3GB free I do not have room to try to install UT or L4D via Steam.

One thing I have noticed is that I cannot install items from the Steam Store.  This is true in a normal WINE environment too.

---

### Post by ackanao on 2009-06-18
Hi Zheldon,

PlayOnLinux is just a frontend for Wine so there's no differences between POL and default Wine installation; POL depends on your system version of Wine so if you uninstall Wine it will also uninstall POL.

There's only one (big) difference between POL and Wine (and other Wine frontends available):

With just couple of clicks, POL allows you to have as many different versions of Wine and wineprefixes as you want.

POL scripts are there to help you with installation of diferrent aplications/games, but if you want you can install all of your applications manually. I feel comfortable with Wine so I use POL mainly as "testing environment" and I always choose manual installation over POL scripts - Check for yourself what suits you better: POL scripts or manual installation with POL.

---

### Post by Zheldon on 2009-06-18
Please keep in mind I'm a Ubuntu/Linux newb.

I found part of the solution for installing apps via the steam store [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554").  However I do not know how I would get that to run inside POL, or use the prefix created for Steam by POL.

On that same page if you go down there are some more instructions that seem promising.  With that I do not know where or the name of the steam start script.

> As the steam integrated browser does not work fine, I'm used to read steam community pages with firefox. But the problem is I could'nt get the "_"  links working as steam is not integrated to my linux environment. Sot found an helpful trick to get this working (thx to firefox):
1 - open "about:config" url page in firefox
2 - right click to add a new boolean value
3 - name it "network.protocol-handler.external.steam" and set it to "true"
4 - right click to add a new string value
5 - name it "network.protocol-handler.app.steam" and set the value as the path to your steam start script.  

---

### Post by ackanao on 2009-06-18
Hi Zheldon - I didn't mean to be rude, English is not my native language (maybe that's the reason for misunderstandings)...

Anyway I've never used Steam but I decided to install it with POL to see if it's possible or not - it's quite ease really:

1. Start POL and click on Install
2. You will find Steam under the Game menu - Select it and click on Apply
3. POL will create a new prefix for Steam, then Steam Setup will start

I've just created an account to see if everything's working and as far as I can tell everything seems to be OK.

---

### Post by Zheldon on 2009-06-18
I understand.  That part is fine.  Steam has a Steam Store.  In this store you can buy and install games/demos online through steam.  I can get games I have already purchased to install.  Getting things to install from the steam store is completely different.

Those items have a link you click on to install.  Clicking on them does nothing.

I do like POL, very useful to a new guy like me.

---

### Post by ackanao on 2009-06-18
You know what - maybe it's problem with wine-gecko - Which version of Wine you're using to install Steam? If it's 1.0.1 that version comes with wine-gecko 0.1.0; Just try with the latest version of Wine (it comes with wine-gecko 0.9.1). Install it, then install Steam and then go to:

"Tools -> Manage wine versions" and under the "My Applications" tab, select Steam and under "Version:" select the latest version of Wine.

---

### Post by Sealbhach on 2009-06-19
> **Zheldon said:**
> 

I do like POL, very useful to a new guy like me.

Just some anecdotal evidence. I have successfully installed games using Wine before, like COD4. 

Yesterday I tried installing GTA Vice City directly using wine but for some reason the game wouldn't load. So I tried the PlayonLinux installer and it worked great. So it can be a real timesaver if you don't have the time or the inclination to deal with bugs.

.

---

### Post by jake16424 on 2009-07-28
dunno if this is a dead thread,

im running POL and running steam *where all the games i like are* and i cannot seem to get steam to download and install a game from within POL is it possible? anyone else do it? please help, i like linux and dont want to dual boot, ive tried wine, virtual box and a few others,

---

