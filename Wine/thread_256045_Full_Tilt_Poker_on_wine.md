---
title: "Full Tilt Poker on wine"
date: 2006-09-12
forum: Wine
---

### Post by npodges on 2006-09-12
A while ago, I tried playing full tilt poker in ubuntu on wine. It's the only poker site i used, so it was the one i wanted to work. It didnt work at the time i tried it, but i tried it again recently and it works almost flawlessly.

Just in case anyone's wondering. Installion is easy, and updates work fine. If you're looking for poker on linux, I gotta recommend fulltilt on wine.

---

### Post by barryhen on 2006-11-13
how did you get it to work?

---

### Post by geoffm33 on 2006-11-13
Thats good to hear, I haven't tried Full Tilt yet. 

I was able to get PokerStars running on Wine quite easily. There is an issue with the resizeable windows but can be changed with an .ini file adjustment (google it if you need it, I don't remember off the top of my head)

---

### Post by mediax on 2006-11-14
Good to see another poker client working!  I'll give PokerStars a try. :KS 

For anyone who might be interested, PokerRoom has a Java client that runs nicely under Linux with no download and no need for Wine.

---

### Post by raindog on 2006-12-29
I can get Full Tilt to run, but I can't sit at a table as the seats are not visible and clicking on the empty spot does nothing.  

I am running Edgy and I compiled wine-0.9.2.8 with a patch to address an issue with Full Tilt not connecting correctly.  Any ideas??

---

### Post by raindog on 2006-12-29
If using the new table layout of "racetrack view"  I can see the open seat and sit down.  However, in this layout I can't see my cards.  When I switch to traditional layout with or without avatars then I can't see the open spots nor can I sit down no matter what I try.  Any ideas on this one?

raindog

---

### Post by mtgrocks04 on 2007-01-23
Bump...i am having trouble too...anyone have an idea on how to make it work. I can see the table but not the cards.

---

### Post by aitsu on 2007-01-30
Another bump. I _think_ I have wine set up properly, but when I launch the FullTiltPoker.exe in the .wine folder it simply launches and tries to connect. It eventually settles down and reports that it simply cannot reach the server. Any ideas?

I really need to play Full Tilt but don;t want to return to Windows.

Shoot, if someone calls me on the phone and walks me through a wine check-up/installation repair that ends successfully, I will Paypal them a little something. Driving me nuts.


Thanks in advance.

---

### Post by aitsu on 2007-02-11
Big news: I GOT IT WORKING. Actually a helpful fellow named Jeremy made it work. Thanks, Jeremy. Here are the steps. Keep in mind that you will need to be connected to a networked Windows machine with Full Tilt Poker installed. BTW this works for Ubuntu 6.1 Edgy running WINE 9.3.0 -- can't say whether or not it works with different configurations.

Install Full Tilt on your Ubuntu machine. After installation, browse your Windows machine and copy the entire Full Tilt Poker folder over to the Ubuntu machine. You are basically replacing the Ubuntu Full Tilt Poker folder with the one from your Windows machine. (The Ubuntu folder should be in \home\username\.wine\drive_c\Program Files\Full Tilt Poker. Don't forget to show hidden folders [control+h] so you can see the .wine folder!) After you replace the folder, simply launch the FullTiltPoker.exe. Jeremy's took a couple times before it connected, but mine worked perfectly from the get-go. You can now launch it with a line command or simply make a launcher pointing to the new .exe file and play.

Lemme know if you need help. I probably cannot provide it since I am a newbie, but maybe we can figure it out together.

Mike

---

### Post by wolfear on 2007-04-29
aitsu-
Under Wine 9.3, did you need to add the patch as required for previous versions or have they addressed that issue?
I had Fullt Tilt rocking along fine with 2.5 but had a major "brain fart" when I reloaded my system a while back and forgot to make a backup of Wine and now have no clue what I changed.
I have been playing in my wife's XP machine but really want to get FullTIlt running on mine again and so far haven't had any luck getting it to work properly.

---

### Post by bg1256 on 2007-04-30
Poker Stars works as well.

---

### Post by Whizardx on 2007-05-02
hmm...where can I install the patch you are reffering to?

---

### Post by wolfear on 2007-05-03
> **Whizardx said:**
> hmm...where can I install the patch you are reffering to?

The patch requires a compile from source. I "think" I originally found it posted here or on the Full Tilt forum, can't remember for sure.
Here is the link:
Implement GetCurrentHwProfileA() fully
[http://www.winehq.org/pipermail/wine-devel/2006-February/045115.html]("http://www.winehq.org/pipermail/wine-devel/2006-February/045115.html")

Since I only use Wine for Full Tilt and am not a programmer, I do not know if implementing this will affect the functioning of any other programs running under Wine.

I tried aitsu's method using Wine installed from the repos and running 7.04 a few days ago, and while it sort of  works on my system, Full Tilt still shuts down periodically, has no sound, and still has some graphics issues.

I guess when I have time, I'll "go back to the drawing board" and try to figure out what I am missing now that I had previously and compile 9.25 from source.

---

### Post by mohnkern on 2007-05-04
I'm running Ubuntu Feisty and Wine 9.36.  I did the following:

Installed Fulltilt using wine.

Went to Windows, copied the files over to my .wine\drive_c\program files\Full Tilt Poker directory

Ran wine ./FullTiltPoker.exe from the console.

It starts up, says its connected, and then crashes with a very long error part of which is :

Unhandled page fault on write access to 0x00000000 at address 0xb7cd434c (thread 0012), starting debugger...

It then did a register and stack dump.



I tried to do the same thing kin KDE as well, no success.

Anyone have any ideas?  I know some people are getting this to work, so there's gotta be some difference.

---

### Post by cybernout on 2007-06-11
Hello, try the step in this post:

[http://www.mattahfahtu.com/2007/02/20/howto-install-and-use-poker-clients-under-linux-with-wine/](http://www.mattahfahtu.com/2007/02/20/howto-install-and-use-poker-clients-under-linux-with-wine/)

Brgds...Cybernout

---

### Post by MiloStrife on 2008-09-01
how do i get i working as im new in linux and am not sure of waht programes i need to beable to use things like full tilt on linux any help would be greatly appreciated.

---

### Post by tarahmarie on 2008-11-08
Does anyone have a howto for Full Tilt Poker under Intrepid?

---

### Post by yugo on 2008-11-19
Howto:
1) make sure wine is installed
2) download full tilt installer
3) double click
4) feed the sharks

sound dies after a while for me.

---

### Post by tarahmarie on 2008-12-12
Full Tilt Poker occasionally locks up and greys out.  Nothing works except to kill the process and restart it.  This was true even before I upgraded to Intrepid from Hardy.  It doesn't seem to be connected to the version of KDE that I'm using.  There doesn't seem to be any connection between the processes that I'm running in the background and the greying out.  I've got a monster box and I almost never touch my full system capacity.  I can't figure out why this is happening. I"m going to cross-post this on the Full Tilt forums and see if anyone knows why this is going on.

Intrepid, KDE 4 (newest stable), Nvidia 8600 GeForce, Core 2 Duo 2.83Ghz, 4GB RAM, dual WD 750GB HDs.

Newest wine, newest full tilt.  Also, the upgrade Full Tilt Poker did last night hasn't changed anything.

---

### Post by Bakon Jarser on 2008-12-15
Was using Hardy and having the same problem.  Last time it happened it completed broke something in compiz.  My title bars all disappeared and avant window manager makes the bottom eigth of my screen completely white.  Turning off compiz effects fixes this but that isn't an acceptable solution.  Does this problem still happen with compiz turned off?

So I made a new partition and installed intrepid.  I had problems with fonts being unreadable in all programs so I did the fix explained here(6.20):
[http://wiki.winehq.org/FAQ#head-dec980f6deabdb11b789c981bf49e10e70929eaf](http://wiki.winehq.org/FAQ#head-dec980f6deabdb11b789c981bf49e10e70929eaf)

Now full tilt doesn't display any images.  No cards, avatars, cashier button, table.  All of the text is there though.

Here is the error messages I get in the console:

fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:advapi:GetCurrentHwProfileA (0x7c4a54c8) semi-stub
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender

The xrender line is repeated a lot more after that.  

Pokerstars runs fine.

---

### Post by JBD88 on 2009-01-04
> **yugo said:**
> Howto:
1) make sure wine is installed
2) download full tilt installer
3) double click
4) feed the sharks

sound dies after a while for me.


Ever figure out the sound issue?  Just installed wine and FT today.  works fine except for sound.  I keep missing my turn...lol.

---

### Post by Bakon Jarser on 2009-01-05
> **JBD88 said:**
> Ever figure out the sound issue?  Just installed wine and FT today.  works fine except for sound.  I keep missing my turn...lol.

Just in full tilt or other wine programs?  

Wine doesn't support pulseaudio.  You have to change wine's sound engine from alsa to oss and use a pulseaudio wrapper to get sound working properly with pulseaudio.  The wrapper is padsp.  Here is what my launcher for full tilt looks like.

env WINEPREFIX="/home/ultimate2/.wine" padsp wine "C:\Program Files\Full Tilt Poker\FullTiltPoker.exe"

---

### Post by JBD88 on 2009-01-05
> **Bakon Jarser said:**
> Just in full tilt or other wine programs?  

Wine doesn't support pulseaudio.  You have to change wine's sound engine from alsa to oss and use a pulseaudio wrapper to get sound working properly with pulseaudio.  The wrapper is padsp.  Here is what my launcher for full tilt looks like.

env WINEPREFIX="/home/ultimate2/.wine" padsp wine "C:\Program Files\Full Tilt Poker\FullTiltPoker.exe"

Hey thanks, I'll try the change to OSS.

Where do I need to make this edit:

env WINEPREFIX="/home/ultimate2/.wine" padsp wine "C:\Program Files\Full Tilt Poker\FullTiltPoker.exe"

I've worked on UNIX/LINUX plenty, but don't know what file this refers to.  Or do I just create the env variable WINEPREFIX on command line?

---

### Post by Bakon Jarser on 2009-01-06
> **JBD88 said:**
> Hey thanks, I'll try the change to OSS.

Where do I need to make this edit:

env WINEPREFIX="/home/ultimate2/.wine" padsp wine "C:\Program Files\Full Tilt Poker\FullTiltPoker.exe"

I've worked on UNIX/LINUX plenty, but don't know what file this refers to.  Or do I just create the env variable WINEPREFIX on command line?

After changing wine to oss then right click on the full tilt launcher in the menu and click properties.  On the line that says command it should look something like that.  Add "padsp" in front of wine and then it should work. Oh, I just tried that, it doesn't work in the main menu, only on the desktop.  If you want to edit the one in the main menu you'll have to right click on applications and click edit menus.

---

### Post by jrusso2 on 2009-01-06
According to the WINE database only some older versions work which I could not find.

---

### Post by Sylvyr Ravyn on 2009-07-12
I am running Ubuntu 9.04 "Jaunty Jackalope" with the latest STABLE version of Wine. I am trying to get it working on my Desktop so I can get it working for a friends laptop. It keeps saying the I need to have Windows Service Pack X on both Vista and XP layers.

Do I have to re-downoad the software and try again? It only happens everytime I try to install it.

---

### Post by eroeurbano on 2009-07-25
Hi everybody,
I tried to use FullTilt as well but can't cope with it.
Apparently the installation succeed, but when I try to launch
FullTilt from terminal 

wine ~/.wine/drive_c/Fulltilt/FullTiltPoker.exe

I get the following error:

> err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc46390


Any ideas??Thanks a lot!

---

### Post by Mixxx on 2009-07-25
> **eroeurbano said:**
> Hi everybody,
I tried to use FullTilt as well but can't cope with it.
Apparently the installation succeed, but when I try to launch
FullTilt from terminal 

wine ~/.wine/drive_c/Fulltilt/FullTiltPoker.exe

I get the following error:

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc46390                      

Any ideas??Thanks a lot!

Hi There,

I am a new user on Ubuntu 9.04 and running Wine 1.0.1
When I try the desktop launcher, nothing happens (I mean NOTHING...), so when I try to launch Full Tilt Poker from the Terminal, I get exactly the same error.

Any ideas would be greatly appreciated !

Please, I need my poker fix ! ;)

Thank you,

Michael

---

### Post by Sylvyr Ravyn on 2009-08-06
Okay, I found out how to get it working a day to late. The friend that I was trying to get it working for went back to Oregon and isn't very computer smart. I wasn't about to explain how to get it working over a phone with pityful reception, either.
 
You have to download FullTilt with the computer you are trying to get it on...and then install. Then make sure everything is installed properly on a windows...
 
Wait, aside from use the computer you want it on to download the software, it is the exact same as has been already posted. Just make sure you have a STABLE version of Wine.
 
It should work on Intrepid Ibex as well as the Satanic Ubuntu Version 4.0. It won't even register on Damn Small Linux.

---

### Post by YokoZar on 2009-08-07
There were some patches to fix Full Tilt that should be coming out in the next Wine release later today (1.1.27).  Wait till I package it up and then upgrade.

---

### Post by mjf on 2009-08-09
Full Tilt is now running on Wine 1.1.27 but I cannot see any text in most places where text should appear (chat box, buttons, dialog boxes, table selection menu, tool tips, etc).  I do see player names and stack sizes, but that is about all.  Selecting the contents of the chat box and copy/pasting to a text editor works, which seems to indicate some issue with fonts.  Anyone else seeing this?

---

### Post by sunfire on 2009-08-09
> **mjf said:**
> Full Tilt is now running on Wine 1.1.27 but I cannot see any text in most places where text should appear (chat box, buttons, dialog boxes, table selection menu, tool tips, etc).  I do see player names and stack sizes, but that is about all.  Selecting the contents of the chat box and copy/pasting to a text editor works, which seems to indicate some issue with fonts.  Anyone else seeing this?

I have same problem.

From my other post
"I had problems with Full Tilt Poker with wine 1.1.24 - 1.1.26. after Full Tilt Poker updated itself couple weeks ago. FTP didnt' start at all.
But yesterday FTP released new update and I updated my Wine to 1.1.27. 
Now FTP works OK. Im missing some fonts from clinet toolbar, but it's no playable once again, cheers!"

---

### Post by Mixxx on 2009-08-11
Hello,

I couldn't get Full tilt to start before, I upgraded wine to 1.1.27 today and installed the latest version of full tilt.

The good news is that now it starts, the bad news is that when it opens, the table selection appears in the front and I can't see the login screen not allowing me to log in.

Any Ideas ?

Thank you

---

### Post by Greg Xix on 2009-08-13
> **Mixxx said:**
> Hello,

I couldn't get Full tilt to start before, I upgraded wine to 1.1.27 today and installed the latest version of full tilt.

The good news is that now it starts, the bad news is that when it opens, the table selection appears in the front and I can't see the login screen not allowing me to log in.

Any Ideas ?

Thank you



I found a partial solution, maybe. I can see some of the text, just not in the menus. Try using downloading the Arial font and running from WINE.

[http://sourceforge.net/projects/corefonts/files/the%20fonts/final/arial32.exe/download](http://sourceforge.net/projects/corefonts/files/the%20fonts/final/arial32.exe/download)

This solved some of the problem.

I also heard that installing Tahoma would help as well.

---

### Post by Mixxx on 2009-08-13
> **Greg Xix said:**
> I found a partial solution, maybe. I can see some of the text, just not in the menus. Try using downloading the Arial font and running from WINE.

[http://sourceforge.net/projects/corefonts/files/the%20fonts/final/arial32.exe/download](http://sourceforge.net/projects/corefonts/files/the%20fonts/final/arial32.exe/download)

This solved some of the problem.

I also heard that installing Tahoma would help as well.

Thank you,

I can see some text now, but my main problem is that when I get to the first screen, there is a box appearing but it goes straight to the back, behind the main screen and I can't get it to come to the front, I managed to log in but for example, if I'm in a table and go to the lobby, the lobby comes to the front and the table to the back and I can't get it back !

---

### Post by abscess on 2009-08-15
Dear people!

After a lot of trying and failing.. I have got Full Tilt Poker to work 100%.. Text, everything.. And it is smooth..! Ubuntu 9.04 and wine 1.1.27.. I would love to give you the step-by-step solution, but in fact, I don't really know exact what I did that made it work..

What I did:
- Downloaded all fonts from [http://sourceforge.net/projects/corefonts/files/the%20fonts/final/](http://sourceforge.net/projects/corefonts/files/the%20fonts/final/) and installed them through wine.
- In my setup, I dual boot with Windows XP Professional. I copied all fonts from Windows XP C:/Windows/Fonts/ to Wine directory c:/windows/Fonts/

..and Finally, I copied the Full Tilt Poker directory from Windows XP to Wine directory c:\Programfiler\Full Tilt Poker\ (Equal to c:\Program Files\Full Tilt Poker\ with with english setup)

I hope this can help you all, for me, I couldn't be happier right now, it works JUST PERFECT =D

:P

---

### Post by Mixxx on 2009-08-16
> **abscess said:**
> Dear people!

After a lot of trying and failing.. I have got Full Tilt Poker to work 100%.. Text, everything.. And it is smooth..! Ubuntu 9.04 and wine 1.1.27.. I would love to give you the step-by-step solution, but in fact, I don't really know exact what I did that made it work..

What I did:
- Downloaded all fonts from [http://sourceforge.net/projects/corefonts/files/the%20fonts/final/](http://sourceforge.net/projects/corefonts/files/the%20fonts/final/) and installed them through wine.
- In my setup, I dual boot with Windows XP Professional. I copied all fonts from Windows XP C:/Windows/Fonts/ to Wine directory c:/windows/Fonts/

..and Finally, I copied the Full Tilt Poker directory from Windows XP to Wine directory c:\Programfiler\Full Tilt Poker\ (Equal to c:\Program Files\Full Tilt Poker\ with with english setup)

I hope this can help you all, for me, I couldn't be happier right now, it works JUST PERFECT =D

:P

Well, I tried this and it works, it is working fine, with all the text appart for the chat text, but I certainly can live with that ;)

I still have a problem, it works fine for a while, but after 15 min or so it seems that the sound stops and then 10 min after everything locks and I have to reboot the pc ! Which is not very good if you're in the middle of a hand !

I still have a problem with message boxes coming up and going to the back, locking the front screen...

Am I missing something or some kind of config in wine ?

Thanks

---

### Post by YokoZar on 2009-08-18
> **abscess said:**
> Dear people!

After a lot of trying and failing.. I have got Full Tilt Poker to work 100%.. Text, everything.. And it is smooth..! Ubuntu 9.04 and wine 1.1.27.. I would love to give you the step-by-step solution, but in fact, I don't really know exact what I did that made it work..

What I did:
- Downloaded all fonts from [http://sourceforge.net/projects/corefonts/files/the%20fonts/final/](http://sourceforge.net/projects/corefonts/files/the%20fonts/final/) and installed them through wine.
- In my setup, I dual boot with Windows XP Professional. I copied all fonts from Windows XP C:/Windows/Fonts/ to Wine directory c:/windows/Fonts/

..and Finally, I copied the Full Tilt Poker directory from Windows XP to Wine directory c:\Programfiler\Full Tilt Poker\ (Equal to c:\Program Files\Full Tilt Poker\ with with english setup)

I hope this can help you all, for me, I couldn't be happier right now, it works JUST PERFECT =D

:P

Did you try just installing the [ttf-mscorefonts-installer](apt://ttf-mscorefonts-installer) package instead of doing it manually?

---

### Post by MrNatewood on 2009-10-31
> **abscess said:**
> Dear people!

After a lot of trying and failing.. I have got Full Tilt Poker to work 100%.. Text, everything.. And it is smooth..! Ubuntu 9.04 and wine 1.1.27.. I would love to give you the step-by-step solution, but in fact, I don't really know exact what I did that made it work..

What I did:
- Downloaded all fonts from [http://sourceforge.net/projects/corefonts/files/the%20fonts/final/](http://sourceforge.net/projects/corefonts/files/the%20fonts/final/) and installed them through wine.
- In my setup, I dual boot with Windows XP Professional. I copied all fonts from Windows XP C:/Windows/Fonts/ to Wine directory c:/windows/Fonts/

..and Finally, I copied the Full Tilt Poker directory from Windows XP to Wine directory c:\Programfiler\Full Tilt Poker\ (Equal to c:\Program Files\Full Tilt Poker\ with with english setup)

I hope this can help you all, for me, I couldn't be happier right now, it works JUST PERFECT =D

:P

Are you not experiencing any crashes?

If so, can you go to Applications->Wine->Configure Wine->Audio
And write here what is your sound setting? And did you uninstall pulseaudio?

---

### Post by RochJer on 2009-11-01
> **abscess said:**
> Dear people!

After a lot of trying and failing.. I have got Full Tilt Poker to work 100%.. Text, everything.. And it is smooth..! Ubuntu 9.04 and wine 1.1.27.. I would love to give you the step-by-step solution, but in fact, I don't really know exact what I did that made it work..

What I did:
- Downloaded all fonts from [http://sourceforge.net/projects/corefonts/files/the%20fonts/final/](http://sourceforge.net/projects/corefonts/files/the%20fonts/final/) and installed them through wine.
- In my setup, I dual boot with Windows XP Professional. I copied all fonts from Windows XP C:/Windows/Fonts/ to Wine directory c:/windows/Fonts/

..and Finally, I copied the Full Tilt Poker directory from Windows XP to Wine directory c:\Programfiler\Full Tilt Poker\ (Equal to c:\Program Files\Full Tilt Poker\ with with english setup)

I hope this can help you all, for me, I couldn't be happier right now, it works JUST PERFECT =D

:P

I did follow the above quote instructions and it worked flawless! I am happy about this result - thank you! I am running wine 1.32 (latest version) and followed all the instructions. It works well! If you others have an issue, follow this, it solved my issue!

---

### Post by vlad1975 on 2009-11-02
Hi guys..

like u i also only full tilt poker but i am having issue on 2 things wonder if you can help me.

1. when i load FTP i cant a screen about flash even if i have already installed flash " See attachment"

2. in the heat of the game it constantly crash on me..

any solution?

---

### Post by RochJer on 2009-11-11
> **vlad1975 said:**
> Hi guys..

like u i also only full tilt poker but i am having issue on 2 things wonder if you can help me.

1. when i load FTP i cant a screen about flash even if i have already installed flash " See attachment"

2. in the heat of the game it constantly crash on me..

any solution?

I have the similar problem as it was resolved but then it isn't at all after playing FTP for a while - the game did crash on me as well as I am running wine 1.1.32. I do have adobe flash 10 installed as well but FTP doesn't detect it somehow. I think maybe I will test it with previous versions and see what happens.

---

### Post by guimaster on 2009-11-11
> **bg1256 said:**
> Poker Stars works as well.

 Works great in every-way, except when you click a browser link. Wine doesn't open a browser window. I can't buy chips because of this.

---

### Post by asgawer on 2009-11-14
> **guimaster said:**
> Wine doesn't open a browser window.

Try "wine regedit", search for winebrowser, add %1 at the end of the line.

---

### Post by guimaster on 2009-11-14
> **asgawer said:**
> Try "wine regedit", search for winebrowser, add %1 at the end of the line.

 Thanks for the response. I will try it.

 Amazing how many Google searches I did and never found an answer until you came along. I had to set up Windows 2000 in order to buy credits.

EDIT: So I went into the registry and changed every occurance of Winebrowser and Winebrowser.exe to %1 at the end. Some of them said " -nohome " at the end but I deleted all the " -nohome " comments. I hope that's okay.

 Now that I Google Winebrowser %1 I can find threads on this topic. I wish my searches would have found those pages before. It's opening windows now!

 Thanks so much!

---

### Post by vlad1975 on 2009-11-15
I have a different problem hope someone can help me
I get error " Please See Attachment" when trying to open registration via FTP

---

### Post by Night Man on 2009-11-25
Apparently I am the worst at linux ever.  I have pokerstars working fine with wine, but nothing at all happened when I tried to run full tilt from the shortcut that was created.  I tried to run from the terminal and got this error

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc452ed

I have tried the suggestions here and there were no changes.
I'm using ubuntu 9.10 and wine 1.1.31
would appreciate any help

---

### Post by chaseaturtle on 2009-12-15
Bump.. : /
Hello Everyone,
   I recently had  an HP pavillion ZV5000, (fairly low ram 622 MiB) that was laying around the house with a bad power terminal soldered up. I am familiar with programming and Ubuntu, but no expert by any means. I did a clean install of Karmic, managed to get my broadcom wireless up and running and all gui, and  normal apps are working just fine. 

   I have read this thread up and down and still have not found a solution to my problem. I have tired running FTP with and with out the flash plug in installed. I have run it in every possible windows "layer" mode there is, Still it seem to crash on me. Every instance of the game (Ring game, Tournament, or SNG), every time, it crashes. It also doesn't seem to remember any personal preferences, though this is tolerable. It will run fine somewhere between 15 minutes and 60 minutes, but then seems to crash. Occasionally it does go into zombie mode (Useful with a parent app that opens other parents apps I guess...). Either way it is not an efficient way to make money, and actually has cost me a few dollars. Switching to the mac during crashes doesn't always get me to my hands in time : / 

   Any Tips, Leads, Or Solutions, are GREATLY APPRECIATED! Thanks to the community  and all programmers for everything available so far. I intend to grow with the Ubuntu community with or with out this fix, but would love to play some cards on my GNU OS. Thanks guys and gals so much!

---

### Post by weichimaster on 2010-01-10
Hi

I downloaded Full tilt, and it sort of works. But I have no option of going to the money tables, so I can only lose play money to the sharks. Any ideas?

---

### Post by rkylain24 on 2010-01-12
For the sound issues set wine config to ogg, and change the full tilt launcher to 

env WINEPREFIX="/home/ryan/.wine" padsp wine "C:\Program Files\Full Tilt Poker\FullTiltPoker.exe" 

For noobs this would mean going into the menus and right clicking on full tilt poker and selecting properties. I could not get to the properties from there so i selected add launcher to panel and changed the properties of the panel launcher by right clicking the full tilt launcher and selecting properties. Just remember that wherever you have this new launcher you must use that one in order for the mod to work. 

For text/graphics issues like no menu or other missing text areas set wine to mimic a different version of windows. XP is the default. ME, 95, 95 all worked better allowing the chat to be functional as well as the menu. 

If you still have missing text after changing the windows version to either ME, 95, or 98 try installing winetricks and using that to install the core fonts. 

If you open full tilt and it says you need flash then go to the flash website and download the flash player for other browsers. The internet explorer one did not work for me so i installed the one for other browsers also then it worked.

I used to have crashing problems, or full tilt would freeze and show up as zombie in the system monitor. Sometime i could get hours out of it, and sometimes 10 minutes. Since i changed the windows version to ME it has not crashed, but i did that only a half hour ago, so i'm not sure if that will fix the crashing problems. 

I hope this has helped at least one person :D

-Dr. Sh*thead

---

### Post by weichimaster on 2010-01-12
Thanks rkylain24

Full tilt now looks a lot better than before due to your tips, and the sound works well.

I can now lose my money again! There are actually two full tilt sites - one is fulltilt.com, the other is fulltilt.net.

The issue with only being able to use play money is on the .net download - I unistalled and reinstalled from the .com site and it now works. And, out of paranoia, changed password.

Next steps for me : Copy over my poker tracker database from Windows, see if I can get it set up in Ubuntu and see if I can get working HUD.

---

### Post by rkylain24 on 2010-01-13
glad i could be of help :)

---

### Post by nickeye on 2010-01-23
I'm trying to run Full Tilt off of wine as well and am having problems. I downloaded everything ok, but when I try to pull up the site to register a screen name there is no writing on the screen. All of the boxes are blank. Any ideas would be appreciated.

Thanks,
Nick

---

### Post by rkylain24 on 2010-01-23
did you change the version of windows that wine emulates? go to the wine config and change it from xp(default) to ME, 98, 95 those all work for me.

---

### Post by sam.666 on 2010-02-05
i also have the problem of full tilt poker crashing.  

first, the sound dies.

then, i get this error:

"The program FullTiltPoker.exe has encountered a serious problem and needs to close.  We are sorry for the inconvenience.

This can be caused by a problem in the program or a deficiency in Wine.  You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application..."

i looked at winehq.org but didn't find anything helpful.

i can usually still play for several minutes after which the app freezes.  i have to do "force quit" to get out.

after the first crash, every time i restart the app the fonts are messed up (blurry, hard to read, but still present).  this problem gets fixed if i reboot my machine.

this is in addition to the settings not being saved (which i can live with, but it would be great if someone suggested a fix).

i run ubuntu 9.10, wine 1.1.37.  the audio setting in wine is set to ALSA Driver, if that matters.

i tried running on wine 1.0.1 but could not get full tilt to run at all.  i would get : err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr...

after switching to 1.1.37 it runs without errors (other than the crashing).

i tried switching to windows ME but it did not make a difference.  right now i'm at windows XP setting in wine.

---

### Post by jrusso2 on 2010-02-05
I had it working fine then one day it updated and no more full tilt.

---

### Post by MrNatewood on 2010-02-06
For me changing the audio driver in wine config to EsounD made crashes much much rarer. Also notice that about one minute before the program crashes sound is lost, so thats a good warning to find the right moment to restart full tilt.

So for all of you experiencing crashes, this is mostly due to incompatibility between pulseaudio and wine. I highly recommend using the EsounD driver and *_not_* ALSA.

Another option is using wine-pulse:
[https://launchpad.net/~neil-aldur/+archive/ppa](https://launchpad.net/~neil-aldur/+archive/ppa)
This has not worked well for me, but might work for you.

---

### Post by sam.666 on 2010-02-13
MrNatewood, just wanted to thank you.  since i changed my sound settings i have not had a single crash.  thanks!

---

### Post by kolo-01 on 2010-02-15
hi,
i'm running full tilt on wine version 1.2 and it is does work but it is stupidly temperamental and closes regularly on 5-15 minute intervals so obviously is not ideal, does anyone else have this problem or have an idea of how to configure wine to make it more stable? i have the mode set to windows 98 which seems to work the least bad. any help would be massively appreciated.

---

### Post by trimmer on 2010-03-20
I am the new [APPDB]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2056") maintainer for [Full Tilt Poker]("http://www.fulltiltpoker.com") out on [WineHQ]("http://www.winehq.org") and I gathered a lot of valuable tips here.

At first, I, too, had the initial crash that caused sound loss and soon to be followed by the fatal crash that forced me to kill FTP. I wrote a script to kill it that contains one line: [COLOR=Red]kill -9 $(pgrep FullT)[/COLOR] When wine is killed it usually leaves services.exe and explore.exe and winedb running as orphaned tasks on your machine but when you kill FTP only it allows those to clean up so your fonts won't go all screwy causing you to reboot.

So, the sound problem seems to be directly related to ALSA. [COLOR=Red]Stop using ALSA![/COLOR] I recently switched to the OSS driver only and added "padsp" (no quotes) between the env variable and the wine command in my shortcut to FTP. You can do this by right clicking the applications button and selecting edit menus. Then all you have to do is drill down to the FTP shortcut and edit its properties. We'll see how OSS only treats me.

The majority of seetings did not save for me initially either. The first time I ran "wine regedit" from the command prompt to see the registry editor I actually made no changes in the registry what so ever, but I noticed, all of a sudden, that all my settings were now saving. This may or may not work for you. I know one other person that this solution worked. Minor things still do not work like when I search a friend, their name is not saved between log-ins...

There are a lot of freerolls and I try to hit them all. One in particular, the $250.00 United States freeroll(many countries and other localities have them) are based on geographical IP servers and to register for them you have to click on a link in the lobby and it takes you, in a browser to an external FTP website to register. Those links and advertisement and Sit 'N' Learn links did not take me anywhere. To solve this, I once again reopened the registry editor and searched the term winebrowser. Every value that contained C:\...winebrowser.exe -nohome I changed that to C:\...winebrowser.exe %1.

That should cover the majority of problems.

I am running Karmic Koala 9.10, kernel 2.6.31-19-pae (I do not run 2.6.32-20-pae for non-wine related issues), the latest wine 1.1.40(however I started in 1.1.39) and feel free to stop by the [APPDB]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2056") and leave your report there as well.

---

### Post by 121Lazz on 2010-03-20
For me the crashes seem to have stopped after changing the audio driver :)

However, it won't save any settings, which is really annoying.
I already tried giving the folder and all files read/write permissions as well as running "wine regedit".
Any ideas?

---

### Post by maxpancho on 2010-03-21
cant really play it normally. i open wine, boot ftp and start playing and then after 1-2 minutes the sounds goes away and then comes sth like ftp crash report.

ps: yeah, it seems that linux is too hard for me to handle, i mean you have to adjust and install every program using "creativity" and put pretty much effort to it. i think it's a great OS if you just surf internet, use IMs or if you're a sys admin or programmer, but it's not if you're an average user. cuz most users i guess have windows installed anyway, because linux isn't popular enough to create games and programs for it.

---

### Post by drillerccg on 2010-03-22
I got all three Poker Stars, Full Tilt Poker, and Ultimate Bet clients to work with Wine and Ubuntu 10.04 LTS. Here is the thread:

[http://ubuntuforums.org/showthread.php?p=9007415#post9007415](http://ubuntuforums.org/showthread.php?p=9007415#post9007415)

---

### Post by 121Lazz on 2010-03-22
> **drillerccg said:**
> I got all three Poker Stars, Full Tilt Poker, and Ultimate Bet clients to work with Wine and Ubuntu 10.04 LTS. Here is the thread:

[http://ubuntuforums.org/showthread.php?p=9007415#post9007415](http://ubuntuforums.org/showthread.php?p=9007415#post9007415)

Well, you describe how to install the pokerclients and wine.

We obviously already did that, only difference is your OS Version.
I doubt upgrading to 10.04 Beta will get rid of any issues.



@maxpancho

I agree Linux is hard on normal mortal beings, but read trimmer's post to fix the audio/crash problem.

What I did was disable all audio drivers in the WINE configuration menu (since I don't care if ftp has no sound).

---

### Post by 121Lazz on 2010-03-24
*bump*
Anyone figure out how to save the settings?

---

### Post by Calcvictim on 2010-03-24
I am using Alsa, pulseaudio is completely uninstalled. I ocasionally get dissapearing sound followed by a crash, would the pulseaudio wrapper work for me or am I out of luck?

---

### Post by 121Lazz on 2010-03-26
Try this:
> **trimmer said:**
> ...
[COLOR=Red]Stop using ALSA![/COLOR] I recently switched to the OSS driver only and added "padsp" (no quotes) between the env variable and the wine command in my shortcut to FTP. You can do this by right clicking the applications button and selecting edit menus. Then all you have to do is drill down to the FTP shortcut and edit its properties. We'll see how OSS only treats me.

---

### Post by stryknyner on 2010-04-05
I installed wine I think not sure it shows up under applications the choices I have say configure wine and browse c drive. when I click either it takes me to a windows like window that looks like nt version but it says xp from there I have no idea what to do I want to play fulltiltpoker I downloaded it and installed it I guess it shows up under applications under wine when I click it it appears to start but then never starts and the tab at the bottom of my screen disappears after a few seconds. I tried uninstalling it and reinstalling it. but it still does not work. can anyone tell me what I'm doing wrong? do I need to further configure wine? cause I have no idea what needs to be done. please someone give me easy to understand directions thank you

---

### Post by Funkey Monkey on 2010-05-05
I was wondering if you got the PokerTracker 3 HUD to work with Full Tilt and PokerStars?

---

### Post by pemadorje on 2010-05-14
> 
I recently switched to the OSS driver only and added "padsp" (no quotes) between the env variable and the wine command in my shortcut to FTP. You can do this by right clicking the applications button and selecting edit menus. Then all you have to do is drill down to the FTP shortcut and edit its properties. 


Thank you for your suggestion but I was wondering if you could please clarify how you added the "padsp". Specifically where you add this. 

I'm in the properties of my shortcut and here is what I have: 
```
env WINEPREFIX="/home/dan/.wine" wine "C:\Program Files\Full Tilt Poker\FullTiltPoker.exe"
```

do you simply add "padsp" right after the "env"? So it would look like:
```
env padsp WINEPREFIX="/home/dan/.wine" wine "C:\Program Files\Full Tilt Poker\FullTiltPoker.exe"
```

If anyone else has the answer, I'd appreciate it.

Thanks.

---

### Post by Joe-ubunt on 2010-05-15
> **MrNatewood said:**
> For me changing the audio driver in wine config to EsounD made crashes much much rarer. Also notice that about one minute before the program crashes sound is lost, so thats a good warning to find the right moment to restart full tilt. 

Works for me too. Thanks for your post. Before I changed the driver Full Tilt wasn't even playable. Now it works great.

---

### Post by Nsight7 on 2010-06-02
Just another verification that simply changing the audio driver from ALSA to something more agreeable (in my case OSS), was all that was necessary to make Full Tilt MUCH more stable.  Have been running multiple tables for over 2 hours with NO crashes when I couldn't play for more than one or two minutes before without a crash occurring.

I haven't even attempted correcting other problems yet, but if they occur, I might be back.

---

### Post by kolo-01 on 2010-06-24
things seem to work well with wine set to windows 7, including full tilt, im pretty impressed with the number of programs that now work in wine with the change- spotify is another

and also the font problem can be solved by closing all wine-related tasks in the system moniter and starting full tilt

---

### Post by sitnafup on 2010-07-15
I've recently started using FTP and looked here when I started having problems like those listed above. I have tried, I think, pretty much all the solutions given here but am still experiencing crashes approximately 1 hour into play. I rarely get an error message, instead the network connection fails but does not reconnect and the "trying to connect..." window stays open. I usually close it after this happens as it becomes unresponsive, but I recently left it running and it finally gave up trying to connect: "sorry, cannot connect..." There is nothing wrong with my network connection.
I have problems with text only after the crash, which I solve by configuring wine through Play On Linux before restarting FTL.
I have changed my sound driver to both OSS and EsounD. The latter seems to be the best in that the crashes are delayed longer. 
I have tried different windows 'distros' (xp, me, 98...) and have settled on windows 7 for the same reason (of a delayed crash).
I added "padsp" between the env variable and the wine command in the FTP shortcut.
Perhaps I'm missing something, like the correct combination of solutions?

I can live with the crashes as they give me a chance to have a stretch, but they mean that I can't really enter into tournaments, only ring games.

I am on Karmic and the latest Wine.

If anyone has any further solutions I would be grateful.
 
And I am new, so feel free to talk to me like a 5 year old.

---

### Post by Funkey Monkey on 2010-07-16
I am using SunVirtualBox to run Xp in 10.4

I gave up on Wine as it does not work with PokerTrackers HUD

Also I like PokerStars, it has the most players and therefore has more to lose if they do something funny (less chance of them stealing your money),
have alook ast the player counts for the various pokersites at [http://poker-network.flopturnriver.com/](http://poker-network.flopturnriver.com/)

---

### Post by vedix on 2010-08-29
First FTP crashed every 15-25 minut.
But now I hope that I finally got FTP working, I have been playing twice now for games lasting 40-60minutes, and total with several games for over two hours. I used playmoney for testing.
I just want to document my way there using tips from this thread and from wineHQ maybe it helps someone.

I tried drivers for wine 1.1.42 , 1.2 those did not work for me, last I went with the dev, version 1.3.1
I tested with (wine)windows version XP,7 not working for me.

Im using: Ubuntu 10.04,LTS,LucidLynx
Full Tilt Client version: WIN.0.17
winedriver 1.3.1
wine/windows version: vista
audio driver wine: OSS & Esound 

At first the fonts where messed up and settings where not saved.
I run this script 
```
#!/bin/sh 
wineserver -k 
env WINEPREFIX="/your/home/directory/.wine" wine "C:/Program Files/Full Tilt Poker/FullTiltPoker.exe" 
```
Then the text and savings worked.

I also followed this tip from asgaver to make the FTP browser links work.
*"wine regedit", search for winebrowser, add %1 at the end of the line"*

Deposit from my local bank seems to work aswell.

See ya at the tables :)

---

### Post by ricsi-pontaz on 2010-09-01
Is somebody tried it on Maverick?

Because for me it's not working. It is stop at the loading dialog

[Screenshot]("http://noob.hu/2010/09/01/fulltiltpoker.png")

---

### Post by laagamer on 2010-10-08
Hey, got a problem. 
Keeps crashing for no reason. I have new versions of everything along with all the fonts and my audio is changed to Eduio (spelled wrong?) and it still crashes 10min into every time I start it. Then if you try and run it again, the text is all blurry and unreadable....

Heres a pic of the screen so you can see how messed up it is...

Anybody have a solution?

---

### Post by laagamer on 2010-10-08
heres the pic

---

### Post by Zigas on 2010-10-11
Guys I'm using ubuntu 10.10 (32 bit) and wine 1.2. Full tilt poker instaled, but when I run it, it keeps reconnecting all the time and I can't connect. Maybe you know what is the problem? BTW same problem with pokerstars :/

---

### Post by Zigas on 2010-10-11
So no onw know why i can't connect to internet throught wine?

---

### Post by creespekt on 2010-10-12
Hi!

I had the same problem ( Ubuntu 10.10, wine1.2, Full Tilt reconnecting all the time.)
You just have to go to winehq.org and add the wine repository to your repositories to be able to install wine1.3 .
It's beta but work just fine.

See you at the tables!

---

### Post by Zigas on 2010-10-12
Maybe you could explain me it step by step? :/ I'm almost new in linux ;D

Nvm i found how to do it and it works. Thnx. ;)

---

### Post by ilikejellolol on 2010-11-02
> **trimmer said:**
> 
There are a lot of freerolls and I try to hit them all. One in particular, the $250.00 United States freeroll(many countries and other localities have them) are based on geographical IP servers and to register for them you have to click on a link in the lobby and it takes you, in a browser to an external FTP website to register. Those links and advertisement and Sit 'N' Learn links did not take me anywhere. To solve this, I once again reopened the registry editor and searched the term winebrowser. Every value that contained C:\...winebrowser.exe -nohome I changed that to C:\...winebrowser.exe %1.

Could you explain to me how I could do that? I'm new to Linux and I had the same problems with Full Tilt as everyone else with the sound and crashing. I also try to play the $250 freeroll everyday, but I always have to register for it from my Window laptop.

Edit: I'm still having problems with the sound and font and crashing thing after switching from ALSA to OSS. I'm gonna try out the other drivers and see how they work. I really hope I can fix this because I have a decent amount of play chips on Full Tilt and I really don't want to start from scratch on PokerStars because it seems like that program works fine for me.

---

### Post by Ben987654 on 2010-12-14
Can someone please help me with Full tilt poker so that is displayed correctly.  Some days ill open it up and it works fine other days i open it and im unable to read anything in the application.  All the text is messed up. Please help me with this and be very specific i know absolutley nothing about Ubuntu or Linux. Thanks !

---

### Post by TakeitEZ on 2011-01-13
I have Full Tilt working on my Ubuntu 10.10 netbook with Wine 1.3.  It runs great and I have no issues except one.  I like to multi-table cash games but unfortunately even though I have the option "display table on action" enabled, the table that needs action does not pop up automatically as it should.  I have to keep checking each table manually to make sure I don't miss a hand.  

Does anyone else have this issue?  Any solutions that might solve this problem?  Thanks for any assistance in advance.

---

### Post by asdf2429 on 2011-02-15
> **Ben987654 said:**
> Can someone please help me with Full tilt poker so that is displayed correctly.  Some days ill open it up and it works fine other days i open it and im unable to read anything in the application.  All the text is messed up. Please help me with this and be very specific i know absolutley nothing about Ubuntu or Linux. Thanks !

Hi. You need to add fonts to your wine. 
Find mashine with Windows and copy directory "windows\fonts" to .wine/drive_c/windows/Fonts

---

### Post by Banzyni on 2011-03-05
> **asdf2429 said:**
> Hi. You need to add fonts to your wine. 
Find mashine with Windows and copy directory "windows\fonts" to .wine/drive_c/windows/Fonts

In addition to this...

You may find that the second time you go in to Full Tilt Poker without shutting down that the fonts are all blurry.  To resolve this:

1) Close Full Tilt Poker down

2) Launch **System Monitor** (i.e. System > Administration > System Monitor)

3) Click the **Processes** tab

4) Select the **FullTiltPoker.e** process

5) Click **End Process**


When you restart Full Tilt Poker the fonts should be clear and readable

---

### Post by EveyPea on 2011-04-06
You can find instructions here at the Full Tilt Forum:

 [http://pokerforums.fulltiltpoker.com/online-poker-post-1172400.html#1172400](http://pokerforums.fulltiltpoker.com/online-poker-post-1172400.html#1172400)

Pay careful attention to one of the lines of code. it should be:

      C:\windows\system32\winebrowser.exe -nohome "%1"

As for ending the fulltiltpoker.e in System Monitor, it is easy to setup a 'one-click' solution.


[LIST=1]
[*]Right click your top menu bar
[*]Click 'Add to panel'
[*]Click 'Custom Application Launcher'
[*]Change the type to 'Application in Terminal'
[*]In the name box type 'Wine Reboot'
[*]In the command box type 'wineboot -e -s -u -r'
[*]In the comment box type 'Force reboot of Wine to fix Windows program issues'
[*]Click the picture
[*]Find and select the icon of the glass of wine
[*]Click 'Okay'
[/LIST]
I hope that helps.

---

### Post by davidw1957 on 2011-04-15
> **vedix said:**
> First FTP crashed every 15-25 minut.
But now I hope that I finally got FTP working, I have been playing twice now for games lasting 40-60minutes, and total with several games for over two hours. I used playmoney for testing.
I just want to document my way there using tips from this thread and from wineHQ maybe it helps someone.

I tried drivers for wine 1.1.42 , 1.2 those did not work for me, last I went with the dev, version 1.3.1
I tested with (wine)windows version XP,7 not working for me.

Im using: Ubuntu 10.04,LTS,LucidLynx
Full Tilt Client version: WIN.0.17
winedriver 1.3.1
wine/windows version: vista
audio driver wine: OSS & Esound 

At first the fonts where messed up and settings where not saved.
I run this script 
```
#!/bin/sh 
wineserver -k 
env WINEPREFIX="/your/home/directory/.wine" wine "C:/Program Files/Full Tilt Poker/FullTiltPoker.exe" 
```Then the text and savings worked.

I also followed this tip from asgaver to make the FTP browser links work.
*"wine regedit", search for winebrowser, add %1 at the end of the line"*

Deposit from my local bank seems to work aswell.

See ya at the tables :)

This worked for me Most excellent !

---

### Post by cwwilson721 on 2011-04-15
Good luck now....

Read [this about the sites are shut down and seized by the FBI]("http://www.webpronews.com/pokerstars-full-tilt-absolute-poker-sites-seized-by-fbi-2011-04")

---

### Post by hip2theehop on 2011-04-15
> **cwwilson721 said:**
> Good luck now....

Read [this about the sites are shut down and seized by the FBI]("http://www.webpronews.com/pokerstars-full-tilt-absolute-poker-sites-seized-by-fbi-2011-04")


Roger cwwilson I "was" a full tilt poker player not anymore. Everything was seized via the FBI so dont waste your time unless your going for play money.

---

