---
title: "For Those interested in Turbo Lister for eBay and Ubuntu!"
date: 2007-01-11
forum: Wine
---

### Post by lfmiller on 2007-01-11
A few people know that I've been looking and tring to get turbo lister to work under linux and wine -  I guess a lot of people have been - I've made some progress, and wanted to document and let others know - What I've done, and what happends, now it might be upto someone smarter then me to figure out more! :)
When I frist started to install Turbo Lister I was given the error that Internet explorer was not installed -- So I stopped messing around, and went back to using TL on my Win 9x machine.... not really what I wanted to do...but -- late last night I was talking to a buddy of mine and he said have you tried to install IE5 under wine?  Never thought about doing that, but hey it couldn't hurt right.
I went off and downloaded IE6 from the microsoft site - and it did install, It didn't work, but it installed... (I really don't care if it works or not) - BUT Turbo Lister did install.  (Still did not run, but at least it installed!)
I checked the install log, and the TL run log, and found that not all of the DLL files had copied. Into the file system -- I did a search on my win machine and found all but one of the DLL files (Now the question is why does TL run on my win machine if I'm missing a DLL on it??? Oh well, I don't care)
The DLL files that were missing from the install:
msxml4.dll  (Had to download this from a site on the net, do a google search it's all over the place)
msjet40.dll  
schannel.dll
Rsabase.dll
Rsaenh.dll
Wininet.dll
All of the above needed to be copied to .wine/drive_c/windows/system32

2 files needed to copied to .wine/drive_c/program files/Common Files/System/OLE DB/
They are: Oledb32.dll and Oledb32r.dll

after I copied those files, TL did try and start - but exited just after the inital start (the loading box, that looks likes it's opening files)

So I did some check searching on google and found someone who meantioned something about coping all of the TL files from his Win machine, and getting TL to start, but exit -

I tried that - copied all of the file from program files/ebay/turbo lister2 -

If I use the TL icon that is on the desktop, TL still exits -- but loads, you get a quick splash of the TL window. -- IF I go into the WINE Program Files/ebay and double click on TL.exe - It usually doesn't exit, and lets me select a user -- but then hangs and locks up the TL window! 
(This is the part where someone smarter then me can take over) 
I'm wondering at this point if it might be a data-base or video error.

The TL log file isn't much help -- but now that it is in installed, I will keep playing around, someone might say something to me that I go -- ahhh....let's try that!

My Wine version 0.9.22, Ubuntu 6.10, Turbo Lister version 5.4.102.33
On my Dell Inspiron 5100 laptop (P4 2.6ghz, 256mb ram, 40gb hard drive) But I don't think that really maters.

Well - This is all I know - I'll let others think about it!

LeRoy

---

### Post by lfmiller on 2007-01-11
UPDATE! UPDATE! UPDATE!
Yes, I just posted the above, but just after wards I thought, what would happend if I clicked cancel when it asked my to select a new user, ect... 
SO I did just that -
The screen came up - did not lock up!! 
I then clicked on the file and  Change User -- selected one of my user accounts - and Holly COW!
All of my auctions came right up!!!!

I haven't yet tried to post a new auction, I'll do that a little later today... but progress has been made. 

I think I've figured out how to get TL to at least start to work!!!! 

I'll let everyone know if I can post an auction, if I can get the updates, ect.

LeRoy

---

### Post by lfmiller on 2007-01-12
Update again!

IT doesn't work beyond letting me see the inventory that is already there. 
It will not connect to the internet, it will not try to download updates,

Maybe I do need to worry about IE6 not working, since TL uses IE to interface.

Also,  it randomly exits - apparently for no reason, but seems like it exits mostly after I try something to do with the internet.

So, I'll leave it up to someone smarter then me to try and figure out what is going on.

I'm still think there maybe a database issue -  there is surely a interenet issue.

LeRoy

---

### Post by lfmiller on 2007-01-13
A screen shot - still not working correctly,  So I'm still looking for someone to help me out on this! :)

LeRoy

---

### Post by gubbins on 2007-01-21
I got it running the same as you following your post here. I am in Debian 4 testing (things should be the same for ubuntu). What I did differently was that I installed eis4linux (just ie6) first

[http://www.tatanka.com.br/ies4linux/page/Installation:Debian](http://www.tatanka.com.br/ies4linux/page/Installation:Debian)

which created a .ies4linux folder that it runs wine out of when running ie6 (export WINEPREFIX="/home/user/.ies4linux")
Internet exporer worked, connected to the internet, etc.

Then I installed turbo lister2 into that directory and copied the dlls and stuff that you posted and copied my Program Files/eBay/Turbo Lister2 files into it. Also I copied my .wine directory into it skipping existing files. 

It opened and worked. I could look through my listings, etc. I did not try to upload anything, but I checked for updates and it never connected (it didn't hang, it just kept trying to make the connection).  So I assume I wouldn't be able to upload anything.

When I went back and checked IE6, it was broken and would not even open.

This is the first time I've tried to use wine and I really don't know anything about it all. I just thought you might be interested in what I tried.

Good Luck, and keep posting your progress!

---

### Post by thejart on 2007-01-23
hey guys, i've been trying to install turbo lister, too.

i took a slightly different (equally unsuccessful) route.  i zipped up my entire turbo lister directory on my xp machine and copied it over to my linux box (kubuntu edgy).  i had already installed ie4linux, so i copied my turbo lister files into:

~/.ies4linux/.wine/drive_c/Program Files/Turbo Lister2/

it ran, but like your experiences, it wouldn't connect to the internet.  i wish this would work, this is one of the few apps that i have to run back to windows for...thank goodness for kvm switches.

---

### Post by thejart on 2007-02-16
i assume that you guys have not got turbo lister working.  i ended up installing vmware and win2k for the sole purpose of turbo lister...not a great fix, but it works.

---

### Post by zami on 2007-02-25
Have any you got Turbo Lister working correctly yet?

I'll be trying to set up Turbo Lister on my Ubuntu box tonight, and I'm just curious if any more pitfalls / roadblocks / etc have been found or solved.

(And of course I'll share if I solve anything myself, too.)

-zami

---

### Post by tagra123 on 2007-02-27
Try installing dcom, DAO and MSJET from the microsoft site.  It should let it work.  I have a program that uses the jet databases that is in wide use on windows machines and have been able to get it to work under wine and CXOffice.  Not everything worked perfectly using turbolister but it was able to create new data and list for me.  

Turbolister still works best in windows, I ended up placing it in a virtual machine but it will work.

---

### Post by zami on 2007-02-28
Well, you are all getting much further then I did.   I'm using Crossover and can't get past the error message 
```

1607: Unable to install InstallShield Scripting Runtime 

```

In my "wine bottle" I've got 
-IE6 (working) 
-Windows OLE components 
-DCOM98 
-msls31 
-Windows Installer 2.0
-DAOCTL
-Jet 4.0
-MSXML 3.0 (because it kept showing up as recommended all over the Windows download site - no idea what it is/does!)

I've tried to install TurboLister with Crossover emulating every Windows version available and they all end in the 1607 error.  Uhg!

I'm open to suggestions!  I'll also post here if I have any updates.

-zami

---

### Post by BirdZerk on 2007-03-12
I have been able to get Turbo Lister to run.  I have not tried to create a new listing yet, but I was able to download from Ebay, I am going to try and upload new listings tonight to see if that works (sale the same products over again).  I have not tried to create a new listing yet but, I do know that edit will freeze Turbo Lister.  Here is how I got Turbo Lister to work.

If you have the most recent version of WIne installed you will need to remove it either by synaptic or apt-get remove wine

Now download and install this older version of Wine through the terminal,

```
 wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb
sudo dpkg -i wine*.deb
```

Do not upgrade Wine, Turbo Lister does not run in the current version of Wine!

I got some of these instructions from another thread and they said to install this file, I did so, you might also,

```
sudo apt-get install libgtk1.2
```

Now you need to install winetools to get all the extras install ie6 and dcom and windows installer and the other little things needed.  You can download winetools from here

[HTML]http://download.formationos.net/winetools/winetools-0.9.4.tar.gz[/HTML]

now you need to unpack the file, so now go to where ever you downloaded the file and enter the following.

```
tar -xf winetools*
```

now install it

```
cd winetools*
sudo ./install
```

now you need to start winetools by typing,

```
wt
```

you will get lots of messages popup about not being configured etc, just keep clicking

You should finally get to a menu

Go through the basic setup, windows system and true type fonts in the main menu and install everything.  If it has multiple languages only install your language.

Now internet explorer will work correctly.

Download Turbo Lister, when the download manger starts it should have wine selected to open the file, if not use the following command to install it,


```
wine setupUS.exe
```

when I finished installing I got links on the desktop to start Turbo Lister,  I clicked the link and Turbo Lister started right up.

That's all I know, good luck.

---

### Post by haydent on 2008-08-11
worked here for me on 7.04, just had to downgrade the wine version from standard .33 to .5 (as recomended)

thanks !!

---

### Post by VitalBodies on 2009-05-17
Now that the Jackalope is hoppin, has anyone got Turbo Lister, TurboLister to work? 

I am never quite sure if I should attempt some of the old techniques from the Gutsy days or what the ramifications are system wide for doing so... 

When I tried to install under WINE the program installs fine but I run into a strange problem. Where I am asked to put the user name and organization during install I get these messages: 
Change preferred organization in ~/.wine/system.reg
Change preferred owner in ~/.wine/system.reg

So if I change them in the system.reg in the three places I found it...
It does not help as every time Turbo Lister starts it changes "VitalBodies" to "Change preferred owner in ~/.wine/system.reg" in that file. It changes the organization back also. 

Additionally the program only flashes on screen and disappears. 

In the system.reg you see things like this: 


"RegisteredOrganization"="Change preferred organization in ~/.wine/system.reg"
"RegisteredOwner"="Change preferred owner in ~/.wine/system.reg"

Ultimately I would like to use FILE EXCHANGE rather than Turbo Lister but currently you have to use Turbo Lister to download your existing listing to get started.

---

### Post by manners2345 on 2010-03-14
Is anyone still trying to get TURBO LISTER for ebay to work, The wine people do not seem to be,  nor do the crossover people seem to be interested. 

If I could get turbo lister to work I could get rid of windows!!

Thank you in advance

---

### Post by manners2345 on 2010-03-14
Sorry forgot the following, using Karmic, 64 bit, Firefox, and the latest WINE
Downloaded Turbo 2 from ebay, installed it thru wine, got turbo desktop short cut, seems to try and start.
 I did the download from 64 bit app side of machine, so guessing it is the 64 bit app, did not ask when I downloaded. 
Do have ebay on my firefox seem to be able to add to site.

---

### Post by VitalBodies on 2010-03-14
I know this is a change of subject but if one learns Ebay File Exchange then they only really need to use turbo lister once to grab their listings for export so they have the item number to match up to the title and description in Open Office. That is if they have a lot of listings already on ebay, otherwise one really does not need Turbo Lister at all. 
Additionally if you leave Turbo Lister behind and switch to File Exchange your are much more ready to load your own web sites cart with a spread sheet and add your products to Google Base. This frees you from Both Windows, IE, Wine and Turbo Lister. I was able to just that using Open Office, Ebay File Exchange, Joomla, VirtueMart, and CSV Improved. CSV Improved has an export for Google Base. 

Some of the learning curve too a bit to figure out so I wrote a few blog posts to help others. 

You can then use Open office to upload your data:
[http://www.vitalbodies.com/blog/2009/05/18/using-file-exchange-and-turbo-lister-with-ebay-listings-in-ubuntu/](http://www.vitalbodies.com/blog/2009/05/18/using-file-exchange-and-turbo-lister-with-ebay-listings-in-ubuntu/)

You have to know a few tricks to get Open Office to play nice: 
[http://www.vitalbodies.com/blog/2009/06/21/getting-openoffice-to-play-nice-with-ebay-file-exchange/](http://www.vitalbodies.com/blog/2009/06/21/getting-openoffice-to-play-nice-with-ebay-file-exchange/)

---

### Post by Sunflower1970 on 2010-03-30
I was just beginning to look to see if Turbo Lister works on Ubuntu, yet...since I'm getting ready to sell a ton of stuff...Guess it doesn't yet..

I did find Jaolt: [http://code.google.com/p/jaolt/w/list](http://code.google.com/p/jaolt/w/list)

Has anyone tried it? If so, how is it? Looks like a good alternative to Turbo Lister...(hopefully...)

---

### Post by VitalBodies on 2010-03-30
I have not tried jAOLT but it looks like an interesting find. 
Thanks for pointing it out!

---

### Post by tripower on 2010-04-02
I have to ask how do you install IE6 under Ubuntu? Do you just run the executable? How does that work?

---

### Post by VitalBodies on 2010-04-02
> **tripower said:**
> I have to ask how do you install IE6 under Ubuntu? Do you just run the executable? How does that work?


I think that there is an IE emulator which is part of WINE so you have to install WINE. Otherwise I have not heard of installing Internet Explorer on Ubuntu.

---

### Post by tripower on 2010-04-02
> **VitalBodies said:**
> I think that there is an IE emulator which is part of WINE so you have to install WINE. Otherwise I have not heard of installing Internet Explorer on Ubuntu.


The guy just said he had to install IE in order to get turbo lister going?

---

### Post by jpeddicord on 2010-04-03
Going to move this to Wine since it doesn't really have anything to do with the Ohio LoCo.

---

### Post by tripower on 2010-04-21
Bump for some new info.

---

### Post by ereallstaff on 2010-12-01
Hi I installed it today, and it seems to work. The first problem I have is that it requires me to log in and it emulates a browser. 

All works but when I put user and pwd in it says that my browser does not accept cookies so I cannot make me access.

I suppose that after that pass all should work fine.

I tried to retrieve a DB with items from a windows installation and it also works, but got to solve this cookie problem first.

which DB should it uses? the current default ubuntu one or what?

THanks

---

### Post by ereallstaff on 2010-12-01
> **ereallstaff said:**
> Hi I installed it today, and it seems to work. The first problem I have is that it requires me to log in and it emulates a browser. 

All works but when I put user and pwd in it says that my browser does not accept cookies so I cannot make me access.

I suppose that after that pass all should work fine.

I tried to retrieve a DB with items from a windows installation and it also works, but got to solve this cookie problem first.

THanks

Sorry I meant problem with BROWSER. 

I installed it under wine, and it calls ebay page for authentication and token setup, but after authenticate it says that **browser will not accept cookies**. 

I tried now also to install firefox for wine, and set it as default broswer trying to control the default browser this way but this hack did not work.

Any help?

We need turbo lister to manage also listing ad to import them as CSV , File exchange it's not enough, like for example item features

THanks

---

### Post by VitalBodies on 2010-12-01
My two guesses would be to make sure cookies are enabled in the browser. 
You most likely know that. 
And are you having a permissions issues causing the browser not to write the cookies to the hard drive? 
Like can you go to other sites and then check if you have any cookies or is it an ebay thing?

---

