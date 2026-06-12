---
title: "Problem using WINE to install .exe Windows File."
date: 2012-06-04
forum: Wine
---

### Post by sandip144 on 2012-06-04
Hi All,

I am very much new to this Linux. I have also installed Ubuntu 12.04 in my HP Laptop. But now i am facing problem like i have installed WINE to use Windows Compatible file. after right click on .exe file i choose extract with Wine but nothing happens. I have also do not understand how to configure Wine.

I have not partioned my Harddisk.

Can any body help me. I am unable to Load Windows XP again my Laptop. No Boot option.

---

### Post by Senior_Buckethead on 2012-06-04
Ok, a number of problems here you need to expand on

> 
Can any body help me. I am unable to Load Windows XP again my Laptop. No Boot option
Ok, so you have installed Linux on a machine that had XP on it, and now you cannot choose, or do not have the choice, to load XP at boot?
Second, you have installed WINE and you are trying to get an .exe file to run under wine, but it wont?

Are these questions correct with the problems you face? You just need to give us more information.

---

### Post by prshah on 2012-06-04
> **sandip144 said:**
> after right click on .exe file i choose extract with Wine but nothing happens.

Hello,

Welcome to the forums.

You do not need to "Extract" anything, to use a program in WINE.

What is the filename / program you are trying to use?

Typically, you can get more information on the problem by using the terminal. Click on Dash (The top left button with Ubuntu icon on it) and type and select "Terminal".

Now, navigate to your program's location (Eg /media/cdrom) and use the following command to launch your program ```
cd /media/cdrom
wine program.exe
```

If your program fails to launch, please copy and paste the messages in the terminal to this thread.

You do not need to do anything to configure WINE. If there is no WINE config, it will create a default config automatically at ~/.wine (~ refers to your home directory, eg, /home/user)

Please post back with results as well as more information regarding your activities.

---

### Post by oldos2er on 2012-06-04
Moved to Wine.

---

### Post by Mark Phelps on 2012-06-04
In the Windows world, some .exe files are programs, others are self-extracting archives. Are you trying to run a program or extract an archive?

Not all programs work in Wine.  To see which ones do, you need to visit the WineHQ website and look up the programs you want to run.

IF the file is named "setup.exe", that is an installer, but you will need to check the WineHQ website for the application to see if it will work.

---

### Post by Senior_Buckethead on 2012-06-04
That wine app database is magic, saves a lot of time and frustration.

---

### Post by sandip144 on 2012-06-05
> **prshah said:**
> Hello,

Welcome to the forums.

You do not need to "Extract" anything, to use a program in WINE.

What is the filename / program you are trying to use?

Typically, you can get more information on the problem by using the terminal. Click on Dash (The top left button with Ubuntu icon on it) and type and select "Terminal".

Now, navigate to your program's location (Eg /media/cdrom) and use the following command to launch your program ```
cd /media/cdrom
wine program.exe
```

If your program fails to launch, please copy and paste the messages in the terminal to this thread.

You do not need to do anything to configure WINE. If there is no WINE config, it will create a default config automatically at ~/.wine (~ refers to your home directory, eg, /home/user)

Please post back with results as well as more information regarding your activities.
1. I cannot load Windows XP back again. I tried it from Virtual box but no result. how to Load Windows XP again?

2. I have re installed Ubuntu 12.04 on my laptop it boots immediately.

I have tried gtalk.exe, QQ.exe using WINE but no result. i dont know which software ihave to download from below.
1. Wine Windows Extractor.
2. WINE Windows Compatible (Meta Package)
3. Qt4Wine.

Confused. I have to go back to Windows XP for my Family they just cannot use Ubuntu.

---

### Post by Senior_Buckethead on 2012-06-05
as far as googletalk is concerned, the newest test is 10.04, thats the latest, so if your running 12.04 your running an untested version:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7458&iTestingId=19064&bShowAll=true](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7458&iTestingId=19064&bShowAll=true)

And as far as qq internation goes, dont bother, it wont run.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25825](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25825)

To install wine, all you have to do is go:
```

sudo apt-get install wine

```

But in reality, lots of software just wont run under wine, so don't give up XP if you give up that particular software. There are open source alternatives, but its not windows.

---

### Post by sandip144 on 2012-06-05
> **Senior_Buckethead said:**
> as far as googletalk is concerned, the newest test is 10.04, thats the latest, so if your running 12.04 your running an untested version:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7458&iTestingId=19064&bShowAll=true](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7458&iTestingId=19064&bShowAll=true)

And as far as qq internation goes, dont bother, it wont run.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25825](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25825)

To install wine, all you have to do is go:
```

sudo apt-get install wine

```

But in reality, lots of software just wont run under wine, so don't give up XP if you give up that particular software. There are open source alternatives, but its not windows.
Thank You Sir.

Now how can i go back in Windows Environment? When i Load Windows XP it does not boot. How to load now Windows XP. I have HP Compaq NX 7300 laptop.

---

### Post by sandip144 on 2012-06-05
> **sandip144 said:**
> Thank You Sir.

Now how can i go back in Windows Environment? When i Load Windows XP it does not boot. How to load now Windows XP. I have HP Compaq NX 7300 laptop.
I have Linux QQ Beta.deb file for QQ. But i cannot install it.

---

### Post by Senior_Buckethead on 2012-06-05
You need to start a new thread describing that you cannot get your machine to boot XP on startup. Its a different issue to this, and you should get that resolved quite quickly.
Stat the thread in absolute beginners, not here in wine.
All the best.

---

### Post by prshah on 2012-06-05
> **sandip144 said:**
> 1. I cannot load Windows XP back again. I tried it from Virtual box but no result. 

I have tried gtalk.exe, QQ.exe using WINE but no result. i dont know which software ihave to download from below.

> **sandip144 said:**
> I have Linux QQ Beta.deb file for QQ. But i cannot install it.

Hello,

I recommend that you handle only one problem at a time. You are confusing yourself, and making it difficult to provide answers.

gtalk support is available natively in Ubuntu, you do not need to use gtalk.exe. Please click on the "envelope" icon in the upper right hand corner (near the clock) to setup your google account. 

You can also use gtalk from Firefox browser, by installing the gtalk plugin and visiting [www.gmail.com](www.gmail.com).

I don't know what QQ is, but if you are confident that the deb file you have procured is correct, you can install it with the terminal (Dash-Terminal) command```
sudo dpkg -i ~/Downloads/"QQ Beta.deb"
#replace filename and path as suitable

``` You can also just double-click it in GUI, and choose "install" from the window that pops up (Usually software center)

As for re-installing Windows, you should ask in a Windows support forum. However, as background information, please describe the process you are using to (re)install Windows.

If you want to install in VirtualBox, you need change the boot order in the VirtualBox interface, and set it to boot your Windows CDROM. The details of this are too extensive to explain in a single post, so it will help if you start a seperate thread for the issue of installing Windows XP in VirtualBox.

Don't try to club multiple issues into a single thread, it becomes difficult and confusing to support.

And please be specific with your descriptions and results. "I tried..." and "no result" doesn't tell us much. WHAT did you try (specifically, ie in GUI, terminal, etc) and what result did you get ("no messages", "error XXX").

---

### Post by sandip144 on 2012-06-09
I have uninstalled Ubuntu 12.04 form my laptop. Thanks for Help.

---

### Post by manzanofab on 2012-07-02
Hi, 
I have a similar problem I have Ubuntu 12.04 and wine 1.4
similar issue if I select the file that I want to install (.exe) from the folder and selecting the option "Open with Wine windows program loader" nothing happens
If I do it from the terminal, I end up with errors like:
[FONT=monospace]getting server_pid from lock 3158
wine: cannot get pid from lock (lock isn't locked)
err:process:start_wineboot failed to start wineboot, err 1359
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
getting server_pid from lock 3158
wine: cannot get pid from lock (lock isn't locked)
I have try googling this but i havent get any solutions
any ideas please??

[/FONT]

---

### Post by sandip144 on 2012-07-02
The Best Answer i got from Ubuntu users is "ALL WINDOWS APPLICATIONS DO NOT RUN IN WINE" and "UBUNTU 12.04 IS IN TESTING TO USE ALL APPLICATIONS"

---

### Post by prshah on 2012-07-02
> **manzanofab said:**
> 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)


Please use the winetricks script to install "Windows Common Controls".

You can get winetricks from [www.winetricks.org](www.winetricks.org) (See download section).

To execute winetricks, open a terminal (Dash-Terminal), navigate to the download location, and execute it with sh(ell)```

cd ~/Downloads # replace with your download location
[s]sh winetricks[/s] # DON'T use sudo
sh ./winetricks

```

Please post back with details if you run into any difficulties.

---

### Post by manzanofab on 2012-07-07
Hi phshah

well i know that winetricks is installed, but when i try to do the command sh winetricks
i get the following error 
sh: 0: Can't open winetricks
I am so lost with this ubuntu!!!!

---

### Post by prshah on 2012-07-07
> **manzanofab said:**
> 
sh: 0: Can't open winetricks

Sorry; my mistake; use ```
sh [color=red]./[/color]winetricks
```

Or you can put the full path; eg, supposing you have downloaded it to your Downloads directory, in home directory, then you can use```
sh ~/Downloads/winetricks
```

The character "~" is a shortcut name for your home directory; eg "/home/manzanofab"

---

### Post by manzanofab on 2012-07-08
Thanks prshah
unfortunately i keep getting the following error
sh: 0: Can't open ./winetricks

also if i try to open directly from the search field tyoing wintericks it doesnt do anything
do you think it is an installation problem? or it is a common problem of ubuntu 12.04?
however from the terminal it seems that wine is installed correctly

---

### Post by prshah on 2012-07-09
> **manzanofab said:**
> 
sh: 0: Can't open ./winetricks

also if i try to open directly from the search field tyoing wintericks it doesnt do anything

however from the terminal it seems that wine is installed correctly

winetricks and wine are different entities. wine installation status is not relevant to winetricks.

Did you DOWNLOAD winetricks from the linked site? What is the location you have downloaded it to? How did you download it? Can you post the directory listing or screenshot showing the file you have downloaded?

winetricks will NOT show up in the search field (I assume Dash).

No, it is not a common problem, it is not a problem at all. You must be doing something wrong. Please post back with more information as requested above for specific solutions.

---

### Post by manzanofab on 2012-07-09
Hi
well if it is not install I dont know why it will show in the dash, like on the picture below, I know that they are different, however in one of this forums I read that the last version of wine automatically install winetricks, but because if i click in there nothing happens i use the code of google code :
[http://code.google.com/p/winetricks/wiki/Installing](http://code.google.com/p/winetricks/wiki/Installing)
rm -f winetricks
wget [http://winetricks.org/winetricks](http://winetricks.org/winetricks)
sudo cp winetricks /usr/bin
sudo chmod +x /usr/bin/winetricks
after pasting that code in the terminal I got the following
abec10@Ali-M300:~$ rm -f winetricks
abec10@Ali-M300:~$ wget [http://winetricks.org/winetricks](http://winetricks.org/winetricks)
--2012-07-10 10:52:44--  [http://winetricks.org/winetricks](http://winetricks.org/winetricks)
Resolving winetricks.org (winetricks.org)... 216.92.137.144
Connecting to winetricks.org (winetricks.org)|216.92.137.144|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 607615 (593K) [text/plain]
Saving to: 'winetricks'

100%[======================================>] 607,615      156K/s   in 5.0s    

2012-07-10 10:52:53 (118 KB/s) - 'winetricks' saved [607615/607615]

abec10@Ali-M300:~$ sudo cp winetricks /usr/bin
abec10@Ali-M300:~$ sudo chmod +x /usr/bin/winetricks


[IMG]http://ubuntu.fabianmanzano.info/1.png[/IMG]
in the folder if i search for winetricks i got them in the following folders
[IMG]http://ubuntu.fabianmanzano.info/2.png[/IMG]
and
[IMG]http://ubuntu.fabianmanzano.info/3.png[/IMG]
thanks for all your help, sorry for been such a pain as well, but i really want to give it a try to ubuntu and if I am able to make it work and is=nstall a few program that i need and are windows base i will be able to stop using my windows 7
thanks

---

### Post by prshah on 2012-07-10
> **manzanofab said:**
> 
sudo cp winetricks /usr/bin
sudo chmod +x /usr/bin/winetricks

Given this information, run winetricks from the terminal with ```
sh /usr/bin/winetricks
# or, if error, just
/usr/bin/winetricks
```

Post back error messages, if any.

---

### Post by manzanofab on 2012-07-18
Thanks very much for the help and efforts, but unfortunately I keep having issues
[IMG]http://ubuntu.fabianmanzano.info/4.png[/IMG]
I am getting tempted to stop using ubuntu and try a differnet linux to check if wine works fine in a different vertion. 

or what other solutions do you think i should try

---

### Post by prshah on 2012-07-19
> **manzanofab said:**
> Thanks very much for the help and efforts, but unfortunately I keep having issues


Have you run WINE at least once? It looks like your wineprefix has not been created yet.

Run the command ```
winecfg
``` to check/create a suitable wineprefix. Please post back errors, if any.

I don't recommend switching at this point.

EDIT: Check if you have a WINEPREFIX environment variable; using winetricks with a non-existent or invalid WINEPREFIX gives this error;```
Thu Jul 19 @11:30:35:~/Downloads$ WINEPREFIX=texttones/ sh winetricks 
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string
------------------------------------------------------

```

---

### Post by manzanofab on 2012-07-24
Thank you so much
well before continuing I will like to thank you for all the help, 
after typing winecfg i got the following message error and opens the wine config as you can see in the pictures.
I would like to ask you
i have the q4wine that is a gui to create wineprefixes, but maybe more than one linux newbie will ask the same question, what is the prefixes for? for each windows softaware that i want to install do i need to create a different prefix? and if yes, it is better to use a gui like q4wine? or better to do it from the terminal?
tahnks


[IMG]http://ubuntu.fabianmanzano.info/5.png[/IMG]

---

### Post by prshah on 2012-07-24
> **manzanofab said:**
> 
after typing winecfg i got the following message error and opens the wine config as you can see in the pictures.

i have the q4wine that is a gui to create wineprefixes

A WINEPREFIX is nothing but a environment variable set to point to the base WINE config. This way, you can have multiple WINE configs. As a specific example, some games I play run with WINE set to Windows 98, and some others with WINE set to Windows 7. I can then switch between the configs on demand, as ```
WINEPREFIX=~/win98 wine somegame.exe
#or
WINEPREFIX=~/win7 wine somegame.exe
```

Here win98 and win7 are just two directories, they are not a command.

I don't know about  q4wine, I use the terminal all through. 

Creating multiple WINEPREFIX is easy; all you have to do is create the directory, and wine will handle the rest.

To continue troubleshooting, please open a terminal and post back the output of ```
echo $WINEPREFIX
```

---

