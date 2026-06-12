---
title: "[STEAM] CSS Startup Menu problem"
date: 2007-10-08
forum: Wine
---

### Post by FaLleN AnGeL on 2007-10-08
Hi to all,

Since I do not want to waste your time, I will directly come to my issue point. I, finnaly got Steam working on Linux Ubuntu without any lag whatsoever, yet there is a problem occuring when opening CSS (CounterStrike: Source). When I double click on the icon, I can as usual a message if I want to start anyway CSS (This is no serious message, also appears on Windows) then CSS loads. I get the normal loading menu, with the CSS background skin and the small button on the bottom right corner showing me the message: Loading ...

Up to now, everything works and had worked perfectly, but now comes the problem. When the menu should appear I get something else in stead. Well, I can recognize it as the menu, but everything seems all fuzzy and a bit.. at a wrong place :P
(I uploaded the image as a .png file)

Well, what I did then is simply quiting CSS. (Please note, I have the Tahoma font in place, since I can view teh Steam menu, so this has not to do with the problem.

Now, while I was typing this up, I started CSS again, somehow I got an error message saying:

```
SteamStartup() failed: SteamStartup(0xf,0x0034E064) failed with error
1: The registry is in use by another process, timeout expired
```

:confused: I seriously do not know whats up with all this.
I had installed OpenSuSe once, since Steam and CSS did not work on those, I chose to take Ubuntu, because EVERYONE told me, it works on Ubuntu. Now I get this message.. I was so happy to start to use Linux fully, without switching to windows in order to play css. Now I have again a problem with starting it.. :/

Well anyway, I really hope someone can help me, I would be soo grateful :)

Thanks a lot in advance,

Adrian

---

### Post by ubu-for on 2007-10-08
**Problem 1 (Steam):**

Steam thinks that you are still logged in. You have to right click on the Steam icon in the right corner of the desktop and choose "Quit" to log off.

BTW start CSS always from the terminal with ...

```
WINEDEBUG=-all wine steam -applaunch 240 -fullscreen
```

For further informations [visit this site](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games).



**Problem 2 (graphic bug):**

Start the terminal and enter ...

```
winecfg
```

and unmark "Pixel Shader activated".

BTW the [current Wine version](http://wine.budgetdedicated.com/archive/index.html) is 0.9.46.

---

### Post by FaLleN AnGeL on 2007-10-13
Hi.

Sorry that I am only answering this now, but unfortunately my pc has some problems concerning the booting. (Failure opening Operating System) Now I had to re-install Ubuntu, it kind of works, I need to hit F11 before the Error message appears, then I need to select my first driver, than somewhere below my new Ubuntu OS.

Well, because of that I needed to re-install Steam etc. somehow I had more problems this time with installing it than last time.. :/

Executing then wine msiexec /i SteamInstall.msi did not work at first and it did somewhen with luck :P

Well, I cannot tell now if your post really helped me, because as soon as I double click on the Steam Shortcut and I login I get a message saying that I need to install Geckoo. Now the thing is, the small window telling me this is somehow blocked, I cannot click on the install button. This makes it impossible for me to get into Steam.
And after doing nothing fow 20 seconds I get an Error message. This message is attached as a .png file again.
I tried to install gecko following this command:

```
wine iexplore www.google.com
```

Somehow I finished downloading but nothing more..


Btw. I cannot open Steam or CSS using your command, or any other because the Steam Login menu is blank, I cannot see the font.
(Opening it through Steam is ok, since I have the Tahoma font in place) I seriously do have problems with this PC.. :/

Anyway, I'd be more happy to have a solution for gecko than this one :P

Thanks a lot,

Adrian

Thank you for your help.

---

### Post by FaLleN AnGeL on 2007-10-13
OK, I solved my Gecko problem.

I can now have access to Steam with no further problems.
But exactly here lies my second problem :/

I finished downloading CounterStrike: Source and wanted to play (Obviously.. :D), but when I double click it and press Continue Anyway, my screen loads, I can see for a short second or two the CS background skin and the Loading... button on the bottom right corner, after this the screen blackens, and then I am forwarded back to my Desktop, there is no CS window.. o0

Adrian

---

### Post by FaLleN AnGeL on 2007-10-14
Who says that Trial & Error never works? :P

Yes I can open Counterstrike: Source, Yes I can change things in the Options menu, chat via [alt] + switch, yes I can find servers, NO: I can't connect to them.

It just doesn't work.  The thing is, it stops loading just before I should connect to the server.

Unfortunately my pc freezes as I try to close CSS. When I try to close it with the terminal xkill command (Doesnt work with right click -> close) Some Wine System Tray pop-up menu appears and my pc really slows down. Only a pc reboot helped... :/

I think that the problem relates to the WINEDEBUG command, but that one doesnt work..

```
adrian@adrian-desktop:~$ WINEDEBUG=-all wine steam -applaunch 240 -fullscreen
wine: could not load L"c:\\windows\\system32\\steam.exe": Module not found

```

The Other command found on the site: [http://ubuntuforums.org/showthread.php?t=304528]("http://ubuntuforums.org/showthread.php?t=304528")
, However worked..

Edit:// I tested it out a few times now, it always stops just before the last Bar is being loaded. I don't know why.. Same thing happens when I create a server..

---

### Post by FaLleN AnGeL on 2007-10-14
Sorry that I always post reply, but I find it better to keep the overview like that.

Basically after 2 days of full concentration and work I got to fix all these things:

[LIST]
[*]WINEDEBUG=-all wine steam -applaunch 240 -fullscreen - It is not a problem anymore
[*]Gecko Steam HTML pages viewer - fixed
[*]Pixel Shader in Winecfg menu - Fixed ; I can now access the menu without any problem and configure it
[/LIST]

Thus, I can use Steam without any problem. I can also access the CSS menu point now without any problem either.

Now the only problem that is left is that I cannot create or join any server. My PC freezes after a certain point (As you can see in my attached .png image file) and I always have to reboot my PC through the restart button.

I guess that this will be the last step, after that I will be able to play Counter Strike: Source hopefully without any problem.

Thank you very much,

Adrian

---

### Post by ubu-for on 2007-10-14
Please tell me which video card, Wine version, Wine audio option (OSS or ALSA) and Wine mode (XP or Vista) you currently use.

Here is another link to the [Wine AppDB for CSS](http://appdb.winehq.org/appview.php?iVersionId=3731) with further tips.

BTW don't enable a 3D desktop like Beryl or Compiz, if you play games with Wine!

---

### Post by FaLleN AnGeL on 2007-10-15
Ok here are the informations you want:

[LIST]
[*]nVidia Corporation NV34 [GeForce FX 5500]
(Checked it out with the lspci command btw.)

[*]adrian@adrian-desktop:~$ wine --version
wine-0.9.46

[*]Wine Audio Option is currently OSS. Thats how Wine has recomended me to set to

[*]With Wine Mode, do you mean the Windows version?
The default one was Windows 2000, but I was using an xp sp2 pack.
]The problem is, that I dont have any Windows anymore, I have overwritten it with Ubuntu.
[/LIST]


Thank you,

Adrian

---

### Post by FaLleN AnGeL on 2007-10-19
Hmm, can anyone help me? Or is this a hopeless case?

Adrian

---

### Post by ubu-for on 2007-10-19
> **FaLleN AnGeL said:**
> 
nVidia Corporation NV34 [GeForce FX 5500]


You already have installed the Nvidia drivers, right?

> **FaLleN AnGeL said:**
> 
adrian@adrian-desktop:~$ wine --version
wine-0.9.46


Use version 0.9.44.

> **FaLleN AnGeL said:**
> 
Wine Audio Option is currently OSS. Thats how Wine has recomended me to set to


Select ALSA only.

> **FaLleN AnGeL said:**
> 
With Wine Mode, do you mean the Windows version?


Start winecfg and select Windows XP.

---

### Post by FaLleN AnGeL on 2007-10-20
The nVidia drivers are all installed, I did that once for Beryl, which I do not use anymore.
I uninstalled wine and its applications and all the command lines and informations, basically, only the folders are left. Winecfg, wine setup etc. does not work anymore. So what I do now is try to get wine 0.9.44 but this doesn't work somehow. Through the code sudo apt-get install wine I only get the version 0.9.33 and if I want to upgrade it to .44 it will automatically upgrade to the latest version, .47

Adrian

---

### Post by Alex Carroll on 2007-10-20
Hi, I'm having a similar problem on my 64-bit machine. There's currently no 64-bit release of Wine 0.9.44, so I'm stuck with 0.9.47. I've installed the ATi drivers I need using Envy, so I assume that's not the problem, but CSS still refuses to display for more then a few seconds. I'm running Ubuntu Fiesty (7.04) 64-bit.

Specs: 
ATi X1800XL All-In-Wonder 256MB
AMD X2 5200+
1GB RAM
A pair of 40GB hard Drives

I've tried pretty much all the suggestions listed [here](http://appdb.winehq.org/appview.php?iVersionId=3731) and [here](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam), but I've only had limited success. Limited success meaning that I know what the "Registry in use" error means now.

Thanks for any help.

---

### Post by ubu-for on 2007-10-20
> **FaLleN AnGeL said:**
> So what I do now is try to get wine 0.9.44 but this doesn't work somehow.

Please read my first post and use the second link to download Wine 0.9.44!

> **Alex Carroll said:**
> Hi, I'm having a similar problem on my 64-bit machine.

I don't have much experience with 64bit operating systems, but they are nearly as fast as 32bit operating systems for home users and additional you get lots of problems. Try another version from my first post, too or try Ubuntu 7.10 32bit.

---

### Post by Alex Carroll on 2007-10-20
32-bit Ubuntu doesn't seem to like my motherboard or processor much; it gives me errors about ACPI, and only the 64-bit version ignores them and continues. Not without warning me about it first, though.

---

### Post by FaLleN AnGeL on 2007-10-21
Ok, thats weird now..

I have done everything now, have the .44 version, selected ALSA, have the drivers installed, selected winxp, now just before I get into the server, my window crashes, so CSS is gone and I am back to my normal desktop..

---

### Post by FaLleN AnGeL on 2007-10-28
Ajo, after one week of Trial And Error I still don't get CSS working. It just crashes before I get fully connected to a server/map.

Can't anyone help me getting around this problem?


Adrian

---

### Post by Alex Carroll on 2007-10-28
I went back to Wine 0.9.41 to make CSS work. I sometimes get no sound, though.

---

### Post by FaLleN AnGeL on 2007-10-28
It still doesnt work.. :/

I get sound, that doesn't seem to be my problem, its just I am unable to join any game or map..

---

### Post by undertakingyou on 2007-10-30
> **FaLleN AnGeL said:**
> Hi.

Btw. I cannot open Steam or CSS using your command, or any other because the Steam Login menu is blank, I cannot see the font.


How did you over come this?  I am having the same issue and can't seem to get past it.

---

### Post by FaLleN AnGeL on 2007-10-31
In you console type the following:

```


cd /home/adrian/.wine/drive_c/Program\ Files/Steam

Then

WINEDEBUG="fixme-all" wine steam.exe


```

The cd part will get you to your steam folder, typing windebug and the rest of the command helps you opening Steam without any major lag or frozen screens.

Now people might think this code is the exact one found here:
[http://ubuntuforums.org/showthread.php?t=304528]("http://ubuntuforums.org/showthread.php?t=304528")

But no, the change and the thing that will actually cd your steam folder is adding a Program**\ **Files/Steam into your command.

Of course change adrian by your account user name ;)

That should be it, for further questions regarding these things feel free to post it. This doesn't mean I got rid of my problem, no I still cannot join any map, yet I m an expert at downloading, down and upgrading wine etc now ;P

Adrian

---

### Post by n3utrino on 2007-10-31
For me it worked out for Teamfortress2 as soon as i set the windows version of my hl2.exe to win98.

maybe give it a try

i could make a wild guess about it has something to do with directx versions, but i'm no pro.

---

### Post by FaLleN AnGeL on 2007-11-01
Umm, Steam does not support any Win 98 Operating System o0

I tried it myself :P

---

### Post by Eslupmi on 2008-05-06
I maybe got the solution. At least for me. I got the same errors that you experienced (almost the same), and I solved them primary by reading in this thread. Here comes the important, what I did to get it working.

**In short**:
**1.** Add the HL2.exe-file located in the "counter-strike source"-folder in winecfg, and choose to run it with Windows 98 rather than Windows XP with the global settings.

**2.** In Launch options, type -dxlevel 70 (to run it in Direct X 7.0)

**3.** Run this: WINEDEBUG=-all wine "C:\Programfiles\Steam\steam.exe" -applaunch 240 -console


**Further explained:**
1. I solved my Crash-problem (when it crashes in the end of the loading bar) by running winecfg, choose "add program" in the program-tab. Then you browse to your HL2-file located in your "counter-strike source"-folder.
My address was this:

/home/hakon/.wine/drive_c/Programfiles/Steam/steamapps/username/counter-strike source/hl2.exe

(Click OK to add hl2.exe to the list in the program-tab)

With the hl2.exe selected, look down and choose Windows version: Windows 98.

Then run Steam (with wine).

**2.** Open the Steam games list. Right click the Counter-Strike:Source, choose properties, choose launch properties (or what it was called), and type in "-dxlevel 70" (without the "") in the typing-box.

**3.** Run Counter-Strike Source with this command:

WINEDEBUG=-all wine "C:\Programfiles\Steam\steam.exe" -applaunch 240 -console

If the game doesn't start, try quit Steam. Or kill the Steam-process. Then run the WINEDEBUG command again. Doing this, I could finally enter maps.

I hope this could help you, good luck!

---

