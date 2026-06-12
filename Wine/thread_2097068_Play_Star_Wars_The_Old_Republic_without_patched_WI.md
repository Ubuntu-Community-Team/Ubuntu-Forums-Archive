---
title: "Play Star Wars: The Old Republic without patched WINE"
date: 2012-12-22
forum: Wine
---

### Post by aljen on 2012-12-22
Hi,
here is small application i wrote based on original KUSER_SHARED_DATA patch for wine.
Since it's normal windows application, you don't need to patch your wine anymore, all you need is wine from repo.

You can get it from here:
```

$ wget -O ~/.wine/drive_c/swtor_fix.exe https://github.com/aljen/swtor_fix/raw/master/swtor_fix.exe

```

Or you can get source code for it and build it yourself from [https://github.com/aljen/swtor_fix]("https://github.com/aljen/swtor_fix")

Screenshot: [https://github.com/aljen/swtor_fix/raw/master/swtor_fix.png]("https://github.com/aljen/swtor_fix/raw/master/swtor_fix.png")

How to run:
[LIST]
[*]open two terminals
[*]on first one, run:
```
$ WINEDEBUG=-all wine c:\swtor_fix.exe
```
[*]switch to second one and run:
```
$ WINEDEBUG=-all wine ~/.wine/drive_c/Program\ Files\ \(x86\)/Electronic\ Arts/BioWare/Star\ Wars\ -\ The\ Old\ Republic/launcher.exe
```
[/LIST]

---

### Post by halfsane on 2012-12-22
Thanks for working on this.  When I enter the command in the second terminal I get

```
bash: syntax error near unexpected token `('

```

---

### Post by aljen on 2012-12-22
Sorry, there was a typo - fixed :)

---

### Post by halfsane on 2012-12-24
Still having issues. 

I used your fix and terminal commands but the laucher was all black.

So I used the resolution (1000 x 614) in wine cited in the thread below to get the launcher working.  This allowed me to login and download the updates.
  
[http://www.playonlinux.com/en/topic-9126.html](http://www.playonlinux.com/en/topic-9126.html)


When I click play swotr.exe will not fully launch. Here is my terminal output.


```
halfsane@halfsane-desktop:~$ WINEDEBUG=-all wine c:\swtor_fix.exeWaiting for swtor...
Found, PID: 90
Waiting for threads to end..

```

```
halfsane@halfsane-desktop:~$ WINEDEBUG=-all wine ~/.wine/drive_c/Program\ Files\ \(x86\)/Electronic\ Arts/BioWare/Star\ Wars\ -\ The\ Old\ Republic/launcher.exe
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
[1224/163700:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8
Exception: resolve: Unknown error
Exception: resolve: Unknown error
Exception: resolve: Unknown error
halfsane@halfsane-desktop:~$ | Variable USERNAME set to 'half-sane'
| Variable PASSWORD set to 
| Variable PLATFORM set to 'gamepad.swtor.com:443'
| Variable ENVIRONMENT set to 'swtor'
| Variable LANG set to 'en-us'
| Variable TORSETS set to 'main,en-us'
| Executing batch file 'swtor_dual.icb':

|> set shardaddress @${server}:${port}:${instance}
| Variable SHARDADDRESS set to '@::'
|> server install HeroEngine
| Successfully installed server application: HeroEngine

|> server start HeroEngine://test1@null::IpcConsole:1 dual=true username=${username} password=${password} shardaddress=${shardaddress} environment=${environment} platform=${platform} lang=${lang} torsets=${torsets} skipgamemovies=${skipgamemovies}
| Successfully started server: HeroEngine://test1@null::IpcConsole:1

|> autotick
| Beginning auto-tick.  Use <Ctrl-shift-x> to break.
| Executing batch file 'RemoteRendererServer.icb':

|> server install RemoteRenderer
| Successfully installed server application: RemoteRenderer

|> server start RemoteRenderer://test1@shared::IpcConsole:1
| Successfully started server: RemoteRenderer://test1@shared::IpcConsole:1

|> autotick
| Beginning auto-tick.  Use <Ctrl-shift-x> to break.
^C
halfsane@halfsane-desktop:~$ 

```

---

### Post by aljen on 2012-12-24
On my computer when you click play in launcher, it takes 5-8 min before its window pops out and game starts loading, after that it's working ok :)

---

### Post by halfsane on 2012-12-24
Yes.  It just got going. 

I am an impatient bastard :) 


:guitar:

---

### Post by Haelind on 2013-01-01
Hello,

I have Ubuntu 12.04 installed

Wine -1.5.20 installed

Winetricks installed

I used winetricks to add the Microsoft Runtimes  "vcrun2008" and "D3DX9"

I configured wine to "Emulate a virtual destop and set Desktop size to 1000x615

When I run:
```
WINEDEBUG=-all wine c:\swtor_fix.exe 
```And then run:

```
WINEDEBUG=-all wine ~/.wine/drive_c/Program\ Files\ \(x86\)/Electronic\ Arts/BioWare/Star\ Wars\ -\ The\ Old\ Republic/launcher.exe
```I can login and patch, then hit the play button. it will sit for 30 secs and then move to the swtor splash screen . where it sits perpetually. The little blue icon gear on the bottom right does not even spin.

Below is the output in terminal.

```
[0101/024319:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8
Exception: resolve: Unknown error
Exception: resolve: Unknown error
Exception: resolve: Unknown error
haelind@haelind~$ | Variable USERNAME set to 'USERNAME'
| Variable PASSWORD set to PASSWORD
| Variable PLATFORM set to 'gamepad.swtor.com:443'
| Variable ENVIRONMENT set to 'swtor'
| Variable LANG set to 'en-us'
| Variable TORSETS set to 'main,en-us'
| Executing batch file 'swtor_dual.icb':

|> set shardaddress @${server}:${port}:${instance}
| Variable SHARDADDRESS set to '@::'
|> server install HeroEngine
| Successfully installed server application: HeroEngine

|> server start HeroEngine://test1@null::IpcConsole:1 dual=true username=${username} password=${password} shardaddress=${shardaddress} environment=${environment} platform=${platform} lang=${lang} torsets=${torsets} skipgamemovies=${skipgamemovies}
| Successfully started server: HeroEngine://test1@null::IpcConsole:1

|> autotick
| Beginning auto-tick.  Use <Ctrl-shift-x> to break.
| Executing batch file 'RemoteRendererServer.icb':

|> server install RemoteRenderer
| Successfully installed server application: RemoteRenderer

|> server start RemoteRenderer://test1@shared::IpcConsole:1
| Successfully started server: RemoteRenderer://test1@shared::IpcConsole:1

|> autotick
| Beginning auto-tick.  Use <Ctrl-shift-x> to break.
Connection 0 to RemoteRenderer accepted!
Connecting process name is: swtor.exe
Creating interfaces...
bwa::RemoteMetricsCallbacksHandler::IID 
```

Any insight would be appriciated.

---

### Post by basarix on 2013-05-05
Using the swtor_fix.exe i get past the character creation and activation, however, when i hit play, it dies on the loading screen for the mission.....

using linuxmint 13 with wine 1.4

any ideas or hints on how to bypass this?

---

### Post by Lightning Dragon on 2013-05-07
Wow! Bloody brilliant. I love this game, and it and some other Star Wars game have been my only reason to keep Windows around! I'm going to try this on Ubuntu and Linux Mint when I get back home!

---

### Post by basarix on 2013-05-07
please, do let us know how you get it working in 12.04 ..... i assume ubuntu comes with wine 1.4 and you'll use the fix exe for patch.....
do tell what you added to wine and stuff, cause i get stucked after char creation and can't get past that.

---

### Post by Lightning Dragon on 2013-05-07
Hi,

Will definitely do just that. I'll be sure to keep track of everything I do. :)

---

### Post by Lightning Dragon on 2013-05-09
Hi,

Okay, first thing I did was (I am operating a fresh install of 12.04.2 Ubuntu LTS) I installed my drivers (GeForce 8600 GT) after updating of course, and then I did a sudo command to install wine;

```
sudo apt-get install wine
```

Once that was done, I went into Winetricks > winecfg >graphics tab > enabled virtual environment > changed it to 1000x614 >applied and then continued with the first page's guide.

I then installed SWTOR from the website download, however, and ran "/.wine/drive_c/Program\ Files\ (x86)/Electronic\ Arts/BioWare/Star\ Wars\ -\ The\ Old\ Republic/launcher.exe" which gave me errors stating it wasn't there.=. So then I did this command;

```
WINEDEBUG=-all wine ~/.wine/drive_c/Program\ Files/Electronic\ Arts/BioWare/Star\ Wars\ -\ The\ Old\ Republic/launcher.exe
```

And it worked, though it displayed errors in the terminal, it brought up the game.

> 
[0509/013723:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8
Exception: resolve: Unknown error
Exception: resolve: Unknown error
Exception: resolve: Unknown error
[0509/013744:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8
[0509/013744:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8


It is currently patching right now. I will update as follows.

edit

I got half way through and got a 208 connection error saying it couldn't get the patch data. Also the commands no longer give me the error " [0509/013744:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8",  but now it doesn't work also, so I suppose they were good errors. I'll try out some things and see if it works...

edit2

Okay, so nothing else seemed to work but this;

[http://www.swtor.com/community/showthread.php?t=448583](http://www.swtor.com/community/showthread.php?t=448583)

Patching again, so yay! ;)

edit3

Okay, so when you get through the patching and are now facing a blue screen, wait about 3-5 minutes, and then press ESC to skip all the opening logo screens. It will give you a black screen. Wait about the same time as before and you will be put through to the server list. This is as far as I got, because the server list is missing and I can't select. I'll update if/when I find how to fix it. Here is the error report;

[http://pastebin.com/yvhHzbEn](http://pastebin.com/yvhHzbEn)

edit4

Ah! Open up Configure Wine and then add every exe for the game into the application tab and set them all to Windows XP compatibility, press apply/ok, relaunch the game and you won't be presented with the server list problem again. I am now in the game! However, everything is black except the HUD system. Gonna try and figure this problem out...

edit5

YES! IT WORKS!

I turned the game off after I logged in and saw that everything was black, but only after I pressed ESC to edit my graphic preferences. I turned it to Windowed Mode AFTER I set everything to low,  and could only see black still. The screen froze with the loading mouse so I shut it ALL off and installed these via terminal;

```

winetricks d3dx9 
winetricks vcrun2008

```

Next, after they installed, I shut those terminals down and opened a new one for this code;

```
echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope
```

Next, I ran the codes from the first page (my fixed location code, instead though) and waited past the blue screen and I could see my characters and everything on the log in page! Yay! And then I logged in and now I am playing. And let me tell you...despite the tiny font, it is working better than it did in Windows. Though I haven't tested higher qualities  yet...

Here is a screenshot!

[http://postimg.org/image/h8ox0esyn/](http://postimg.org/image/h8ox0esyn/)

Yes! I will report any crashes/problems!

Crash/Problem 1# Opening the map freezes and crashes the game
Crash/Problem 2# Scrolling over, touching or hovering over quest lines, menus or pointers on the map or mini map will crash the game
Crash/Problem 3# Goes pretty slow in cities or around larger groups of people--not that big of a problem though.

---

### Post by deri on 2013-05-11
I think you should paste these to the wine database too. It could help someone.

---

### Post by bakan723 on 2013-05-11
hey guys, the help is great so far!!  I have gotten further with this thread than I have with any other.  Although I have been having an issue where it stays on the blue screen after login for about 20 minutes then the loading screen comes up for a few seconds and the screen goes white in the middle with black bars and has been in this state for around a half hour now.

thanks for all your help and efforts guys

edit: ok so i was able to get to the char selection screen and select my char however it is now stuck at half way on the next loading screen and the terminal shows this error:
| Beginning auto-tick.  Use <Ctrl-shift-x> to break.
Connection 0 to RemoteRenderer accepted!
Connecting process name is: swtor.exe
Creating interfaces...
bwa::RemoteMetricsCallbacksHandler::IID
bwa::RemoteRendererInterface::IID
******* ERROR ******** ShaderSpec not found [Eye#emissive]

---

### Post by Lightning Dragon on 2013-05-11
Hi,

Did you exit out of the game after twenty minutes, or did it crash? I saw a comment somewhere that it took twenty mintues for another person and when they finally got in game, it was extremely laggy. I think it might have been a connection issue.

What wine version are you running? I just managed to successully install Star Wars: Old Republic on another Ubuntu install with wine 1.4, so do not upgrade though until we run testing out solutions first, and when or if you have to, still do not upgrade; you have to remove all of the old wine off your computer, reboot and then add the PPA for wine 1.5 and then install via the WineHQ website. 

So let us start with trying to find the solution; which steps in my post did you follow and in what order [SIZE=1](like running "echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope"?)[/SIZE]? Do you have drivers installed for your GPU and does your GPU meet the requirements of the game?  It might be an error specifically for character creation. I will attempt to make a new character and see if I am presented with the same error, and then try to find a way around it.

@[**[COLOR=#000000]deri[/COLOR]**]("http://ubuntuforums.org/member.php?u=1773927")

Do you mean my post? Because I would like to, but I have no idea how to. I'll check out the site and see if I can figure it out though.

---

### Post by bakan723 on 2013-05-11
i have drivers for my video card installed.  its redeon hd 6670 2gig and runs this game on windows fine.  I am running wine 1.4.1.  I have followed most of your steps however when i run winetricks d3dx9 i get this error:
brock@bakan-Ubuntu:~$ winetricks d3dx9
Executing w_do_call d3dx9
Executing load_d3dx9
Executing mkdir -p /home/brock/.cache/winetricks/directx9
mkdir: cannot create directory &#8216;/home/brock/.cache/winetricks/directx9&#8217;: Permission denied
------------------------------------------------------
Note: command 'mkdir -p /home/brock/.cache/winetricks/directx9' returned status 1.  Aborting.
------------------------------------------------------
brock@bakan-Ubuntu:~$ 

and when i run [SIZE=1][COLOR=#000000]echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope it just shows a 0 on the next line.[/COLOR][/SIZE]

[SIZE=1][COLOR=#000000]I appreciate you help a lot.  playing this game or not will most likely be my deciding factor in making the permanent move to ubuntu over windows[/COLOR][/SIZE]

---

### Post by deri on 2013-05-11
Maybe you should run the command with sudo rights? just type sudo before the command. Don't know if that helps. For some reason you don't have write access to the directory.

---

### Post by bakan723 on 2013-05-11
with sudo i get this error:
brock@bakan-Ubuntu:~$ sudo winetricks d3dx9
[sudo] password for brock: 
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string
------------------------------------------------------
brock@bakan-Ubuntu:~$

---

### Post by Lightning Dragon on 2013-05-11
Hi,

When you run the second command, it is supposed to show just a "0", so you are fine with that. For your first error, have you ever "sudo" a wine command? That causes this problem. You should not have to sudo wine or winetricks for it to work. I can try to help fix it. Delete your winetricks cache folder and reboot. Or you can try this command to clear the cache;


```
sudo rm -rf .winetrickscache
```

Next, please do the following after a reboot;

```

chmod a+x ./winetricks
./winetricks

```

Or, try these if the above does not work;

```

sudo chown -R *userid:userid* ~/.wine
sudo chown -R *userid:userid* ~/.cache/winetricks

```

As seperate commands, and you can use the same terminal window. Switch out "userid:userid" with your username. This command should give you your proper permissions for the folder.

> [SIZE=1][COLOR=#000000]I appreciate you help a lot.   playing this game or not will most likely be my deciding factor in  making the permanent move to ubuntu over windows[/COLOR][/SIZE]

You are welcome; I have no problem with helping. :)

---

### Post by deri on 2013-05-11
You must have wine account. There is a box where it says "Post new comment" and you can add your comments, but you have to log in 1st. I am talking about wine app database here. I don't remember if you have to have seperate account on bugzilla where you report wine bugs.

---

### Post by Lightning Dragon on 2013-05-11
Hi,

Thanks for the information. I will check out the page and assuming I can log in with my forum ID, I will write down my instructions thus far and specify that it is for Wine via Steam.

EDIT:

Okay, I redid install only I used 1.5. It seems to work until you get to the very first loading screen past the blue screen, then it pauses (loading blue bar in bottom right screen freezes) for an indefinite time. I managed to get your error, well, almost your error;

> 
| Beginning auto-tick.  Use <Ctrl-shift-x> to break.
Connection 0 to RemoteRenderer accepted!
Connecting process name is: swtor.exe
Creating interfaces...
bwa::RemoteMetricsCallbacksHandler::IID
bwa::RemoteRendererInterface::IID
wine client error:6a: write: Bad file descriptor

I will try to figure this and your problem out. I know it can be fixed, something in me bones says so! :guitar:

edit

Oh, you know what, I forgot to mention that for wine 1.4 I had msvcp90 disabled in winecfg. I can't remember if that was added for Star Wars, or if it was there beforehand, but it might help you. This, however, shuts off the game in 1.5.

edit2

SUCCESS!

I now have it fully working in wine 1.5. Better yet, it dispays the cinema movies unlike 1.4! Okay, so open winecfg, go to libraries, and in the dropdown box either look for and select "msvcp90" or type it in yourself. Edit it and disable it. Run the game with the above instrcutions (you still need the winetrick install compnonets previously mentioned). It will glitch/freeze at the first loading screen. Press ESC and then termiate process. Reboot computer. Go back into winecfg and then into libraries and then edit msvcp90 and then make it "Native then Builtin", press apply and then ok. Now open the terminal and in one single terminal, type:

```
echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope
```

It will change to "0", next, right after that one, write the following and press enter:

```
WINEDEBUG=-all wine c:\swtor_fix.exe
```

And then in a NEW terminal (DO NOT close off the older one) type the following and press enter;

```
WINEDEBUG=-all wine ~/.wine/drive_c/Program\ Files/Electronic\ Arts/BioWare/Star\ Wars\ -\ The\ Old\ Republic/launcher.exe
```*
(Your path might be different, but try mine first)

Now it will load through the loading screens with short if not gone pauses and then bring you to the opening cinema movies. Yay! Now you can play. I haven't tested character creation yet, that is next. :)

*If the loading screens still pausing, try the above steps again and WATCH the blue screen until the loading screen appears. Keep pressing ESC to push it passed the loading screens. It helps sometimes.

You will know if the game will run if the command "WINEDEBUG=-all wine c:\swtor_fix.exe" brings up a blue window for a second or two. If it doesn't, then something is wrong.

edit3

Tested anything higher than "low" or "off" for graphic options. You will be locked at middle load for the loading screen passed character selection. The game MUST be on low settings, which you can set at character selection screen. If you have it on higher, it won't work. Which could be why you can't get passed character creation. Try these settings please;

[[IMG]http://s18.postimg.org/8ihv3txrp/settings1.png[/IMG]]("http://postimg.org/image/8ihv3txrp/")

[[IMG]http://s18.postimg.org/3l4aipvsl/settings2.png[/IMG]]("http://postimg.org/image/3l4aipvsl/")

---

### Post by bakan723 on 2013-05-12
awesome, I am now able to log in to the game and get it running however i have the same problem that you had before that everything is black and all i see is the HUD. 

 I tried the commands you told me earlier but none of them have had any effect and i get the same errors as before with "winetricks d3dx9" and "winetricks vcrun2008" although I was able to find a d3d9 and i enabled that and the msvcp90.  that is how i got to where i am at now. 

 Again thanks a lot for all your help, i am still new to linux and apreciate the learning experience.

---

### Post by Lightning Dragon on 2013-05-12
Hi,

Could you show me a snapshot of your "Uninstall Wine Software"? If you want an easy method to take a picture with after you open it, just press Print Screen on your keyboard (if you have one?) and then save it to the desktop, upload to [this site]("http://postimage.org/") and then paste the URL here. For example, this is mine;

[http://s22.postimg.org/qywi9m6c1/wine.png](http://s22.postimg.org/qywi9m6c1/wine.png)
_**(That is just to show you what I need a snapshot of; not what to install as some of those things there are for other games.)**_

I just want to see if any of the things you have installed actually installed. Also, did you reboot? Sometimes for a computer to truly reboot for me I have to flip the switch off (after turning it off), press the power button to discharge, unplug, plug back in and then boot into the computer. Which error is that? The permissions error? d3dx9 should be installed, I don't think enabling it will work.

Switch Configure Wine's default settings to enable virtual desktop and set it to "1000x614" exactly. Hit apply and then okay. You can reboot if you want, but run the game again. To wrap it up, try the following instructions;

In game press ESC, edit your preferences to the above images I posted (the blackness should not effect being able to do this, but if it does for you, edit your preferences at character selection). Hit apply and okay. It should freeze you on a black screen with an orange cursor. Terminate the window after a few seconds.
Open Winecfg > graphics > enable virtual desktop > 1000x614 > apply > okay > exit
Open Winecfg > Libraries > msvcp90 (also try msvcp100) > disable > dwrite > disable (I did it through regedit; if you need help with that, just say so :) ) > apply > okay > exit > reboot
OPen your home directory > .wine > launch the swtor_fix.exe > let it sit for a few seconds > exit > launch Star Wars: The Old Republic following these commands _**exactly**_;


1: echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope
2: WINEDEBUG=-all wine c:\swtor_fix.exe

Wait for the second command to say "waiting for swtor.exe" and a blue screen to pop up for about a second or two before shutting off. Keep the terminal open. Also, both command 1# and 2# must be in the same window. 
Open another terminal and type; 

WINEDEBUG=-all wine ~/.wine/drive_c/Program\ Files/Electronic\ Arts/BioWare/Star\ Wars\ -\ The\ Old\ Republic/launcher.exe
(or the right path for you)

Attempt to log in now and see if that fixed the problem. If it didn't, please make sure you set your preferences up exactly like mine before you exit out of the game and open winecfg again. Find msvcp90 again  and ENABLE it, next set your default settings to "Windows XP". Hit apply and okay, then exit out. Reboot. Now launch your game again and see if the issues persist. If this doesn't work, please make sure you have the correct driver for your GPU installed. An incorrect one can look like it is installed and working (I would know! lol) but it won't actually work.

edit

Is this what your Valve > Steam regedit looks like?

[http://s13.postimg.org/onohlenrr/Screenshot_from_2013_05_12_00_44_22.png](http://s13.postimg.org/onohlenrr/Screenshot_from_2013_05_12_00_44_22.png)

*The underlined and directed parts are the most important thing I need to know about for now.

---

### Post by bakan723 on 2013-05-12
im sorry mate i think that I am missing something, d3dx9 and vcrun2008 are overrides correct?  so i just enable them in wine options under libraries?  thats what i did for msvcp90 and that plus lowering the settings is what made it so that i can log in and get to the point where i would start playing but the screen is black all but the GUI.  the only thing that you have that i do not is d3dx9 and vcrun2008.  when i try to install vcrun2008 it says that it is already installed but i do not have it on my libraries list.

---

### Post by Lightning Dragon on 2013-05-12
Hi,

That is okay, I'm here to help. No, they are meant to be installed via terminal. Open the terminal and then paste the following into the command line;

winetricks d3dx9

And then press enter. If any errors come up, please share them in detail. If not, continue on with this install;

winetricks vcrun2008

edit

Oh, vcrun2008 is installed? Alright then, what about d3dx9? What does it say when you try to run the command?

---

### Post by bakan723 on 2013-05-12
ok so i managed to get it fixed and get them installed and get the game running ... sometimes lol.  i still have the issue that the game just will not connect to the server sometimes but that is not a huge deal i can live with that.  

I do have a couple more questions though.

Is there any way to play it at a larger resolution or does it always have to be at 1000X614?

do i have to type the two command lines every time i open the game or can i use the launcher.exe file after i get it working?

cheers

---

### Post by Lightning Dragon on 2013-05-12
Hi,

What did you do to fix it? It could help others who have the same issues.

You can try a different resolution if you want, I'm not sure it is required. I think it was required of older wines and pre-patch, but I'm not entirely sure. Would you like me to test it?

And unfortunately I haven't been able to get the game to launch with out the command and patch. I'll test that out too, if you want.

---

### Post by bakan723 on 2013-05-12
no need to test about the command and patch but i would love to know about the resolutions if you could test that, even if i have to enter password into launcher without being able to see it.  if that is the case but the game play fine at 1920X1080 i would be happy with that. 

to fix my problem i did two things.  
1. open settings then go to users and at the top right it said unlock so i clicked it and entered my passord
2. open terminal run "winetricks d3dx9" then "winetricks vcrun2008"

then followed origional instructions for starting the game

---

### Post by Lightning Dragon on 2013-05-12
Hi,

Very interesting solution! Whatever led you to think of that? Very good! I will test out the resolutin problem and edit this post with the information. :)

---

### Post by bakan723 on 2013-05-12
when you said to clear my .winetricks cache folder it had a little lock symbol on it so i decided to see what permissions my user account had and that is when i noticed the button that said unlock.

---

### Post by Lightning Dragon on 2013-05-12
Hi,

That is pretty cool, I am definitely going to remember that and reccomend it to others who have permission issues if all else fails to help them! Thanks for sharing! As for the resolution, I tested it at my max reso which is "1920 X 1080 " and it would not open the swtor_fix exe for the first line of commands, resultig in failure. I next tried 1920x944 and it too, would not work, though it brought up the correct screen, this is what it looked like for a majority of the higher settings, making it impossible get any further;

[http://s9.postimg.org/nkls7z3f3/Screenshot_from_2013_05_12_02_51_13.png](http://s9.postimg.org/nkls7z3f3/Screenshot_from_2013_05_12_02_51_13.png)

I then tested the resolution "1440x700" and it resulted in this;

[http://s21.postimg.org/ceiotxyfb/Screenshot_from_2013_05_12_02_55_58.png](http://s21.postimg.org/ceiotxyfb/Screenshot_from_2013_05_12_02_55_58.png)

It seems to be the width that is the problem. It might be something about the in-game settings. If I could get in and change it back to Full screen and then select a resolution from the drop-down, it just might work. For now though, you need to have virtual desktop enabled and cannot get into the game without 1000x614. I will report back if I find out another way.

edit

Nevermind, I succedded in playing full screen in both Fullscreen Windowed and Fullscreen at MAX resolution. This is how I did it.

Keep winecfg at 1000x614 > log into game and at character selection make your desired selections but keep texture and other details on LOW and OFF where avalible > apply and hit okay (you might get a loading screen, just sit through it) > keep changes > okay > log into character.

If you get into the game, hoorah! You can play at your desired resolution, however, keep winecfg at 1000x614. Once the game launches it will automatically set it up for the game but keep the required resolution to make the game launch. And yes, I tested it several times and it worked fine for me. Here is a screenshot;

[http://s18.postimg.org/sm4lw93l5/Screenshot_from_2013_05_12_03_26_06.png](http://s18.postimg.org/sm4lw93l5/Screenshot_from_2013_05_12_03_26_06.png)
(Sorry for bluriness; stupid place downgraded it. Erg!)

However, be warned that the intial startup is longer (especially if you don't have enough ram) but it isn't a twenty or thirty minute wait, so don't worry. The loading screens after that are about the same as before. All terminal commands must be run the same though, and before runnin the second longer code you must wait for the first code to respond with the screen (which you can change the color to via winecfg "Desktop Intergration" whereas mine is black).
 
Please tell me if you have issues.

Thanks!

---

### Post by bakan723 on 2013-05-12
ok I have the same result but the right side of the game is cut off because of the ubuntu launcher bar any sugestions?

---

### Post by Lightning Dragon on 2013-05-12
Hi,

Enable Auto-hide for the Launcher Bar. That will make it so where you have to scroll over it for it to appear. Or, you can try to use the GNOME desktop instead, or maybe Cinnamon which may be installed via the terminal. Cinnamon functions more like a Windows desktop enviroment pre-W8 and GNOME is sort of a mixture between Unity and Cinnamon I think. Personally I prefer Cinnamon.

System Settings > Appearance > Behavior > Auto-hide ON > Sensitivity a little behind the default line. Do not close off the appearance window until you test the sensitivity of the side bar and when it will appear when the mouse is hovered over it.

It is a bit late here so I must log off, but I will be here again very soon to help with any problems. So if you want to not wait, go ahead and post problems/questions and I will get back to them as quick as possible. :)

---

### Post by bakan723 on 2013-05-12
ok awesome mate thank you for all you help.  next time you log in please let me know about cinamon and gnome i would like to know if either of them get rid of this laucher bar on the side or at least make it moveable.

---

### Post by Lightning Dragon on 2013-05-12
Hi,

So keeping winecfg at 1000x614 **_for_** the launcher (where you click play) must be kept, but installing either GNOME or Cinnamon will work, leaving the screen clean of clutter or the bars, so a player can play at his or her desired resolution which MUST be changed at character selection for if you attempt it in game, you will have to restart the game to be able to see again. Here is an image of GNOME (No Effects);

[http://s23.postimg.org/l0uyjvb8b/Screenshot_from_2013_05_12_15_35_57.png](http://s23.postimg.org/l0uyjvb8b/Screenshot_from_2013_05_12_15_35_57.png)

And here is one of Cinnamon;

[http://s17.postimg.org/x2ielr4gf/Screenshot_from_2013_05_12_15_45_24.png](http://s17.postimg.org/x2ielr4gf/Screenshot_from_2013_05_12_15_45_24.png)

The site resized from 1920x1080 to that size and weakened the quality, but you can still get the picture. As you see, they are the same. I would suggest Cinnamon though because there is only one bar at the bottom and looks so much better and runs better, but it is up to you. You can also try other desktop environments if you want, but I would only suggest the above and Lubuntu's desktop (don't follow the instructions linked to in the link I'm giving you; it installs the Lubuntu boot image as well, kind of annoying);

[http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available)

To install Cinnamon, use the following;

[http://askubuntu.com/questions/94201/how-do-i-install-the-cinnamon-desktop](http://askubuntu.com/questions/94201/how-do-i-install-the-cinnamon-desktop)

Usually I found that GNOME is already installed for me, but sometimes after installing Cinnamon GNOME is also with it in the log-in menu.

Keep in mind though that if you play fullscreen, you will have to quit the game to use anything else, even the web.

End;

Please not that when I say winecfg must be kept at 100x614 that this is meant so you can see the patch/start up window, nothing else. Changing this will ruin the screen and make it so you cannot log in.

---

### Post by deri on 2013-05-12
Good looking game. Going to prob. buy it later when you find out how to get it work good.

---

### Post by Lightning Dragon on 2013-05-12
Hi,

The game works great right now. The only flaw is that the game crashes if you open the map for too long. Otherwise, following the thread here to install the game is quite easy. And it is Free-to-Play if you want to test it out first.

I have a feeling the next wine update might just resolve that issue, or that there is something else one can do to fix it via wine. I'll be looking into this issue, of course.

---

### Post by deri on 2013-05-12
Better to be active on wine forums, reporting bugs, giving knowledge how to get games working. Having working game via wine than not having a game at all is much better. Of course native port would the best. I think Jedy academy can be soon launch from linux shell. They have ported it for some time now.

---

### Post by bakan723 on 2013-05-12
ok so game runs beautiful under med/high settings in 1920X1080 one last small problem and i will be completely happy.  when in 1920X1080 fullscreen there is a small space on the bottom of the screen that shows the desktop and a windows behind the game and the top is cut off by the top bar so i can not see friend info or select buttons in the top menu bar.

thanks again for all your help it is very much appreciated and i would love to play this game with you some time.

edit:  nevermind i have solved the problem by using hotkey alt f7 to move the window to the bottom and used in game interface editor to move the top row down a little bit to fix the top bar cutting it off

---

### Post by Lightning Dragon on 2013-05-13
Hi,

**bakan723**

I will be glad to help you out, assuming there is a fix of course. I tried those settings in four desktop environments so I'm not sure what you mean. Hmmm. Which desktop are you using and could you show me a snapshot of what is wrong? I think I remember encountering this problem when I had it *Fullscreen Windowed*, so make sure you just have it on *Fullscreen*. 

[SIZE=1]May I ask how you managed to get the game on any other setting but low, though? I was given black screens. [/SIZE]

[**[COLOR=#000000]deri[/COLOR]**]("http://ubuntuforums.org/member.php?u=1773927")

I couldn't agree more with you. Native ports would be the best. I'm not sure why, now after Steam's successful Linux launch, why others aren't following suit. Obviously our community is dedicated and would buy their ports. I know I would spend a lot of money on my games for Linux if it meant getting off my stupid Windows machine.

---

### Post by bakan723 on 2013-05-13
I have fixed the problem.  please refer to the edit in my previous post.  as for me I am about to dump my windows partition and dedicate to linux from this day on.

cheers guys thanks for all the help look forward to playing some games with you guys

---

### Post by Lightning Dragon on 2013-05-13
Hi,

I am glad you fixed the problem, and thanks for sharing it with the thread--never know when another might experience it. 

[SIZE=1]Can we add each other via SWTOR? Might be cool playing as Ubuntu users together. :)[/SIZE]

---

### Post by bakan723 on 2013-05-13
yes absolutely we can play online any time!!!  You can even join the guild i am in if you would like.  They are all very nice people.  

My name on star wars is Angelzblood.

---

### Post by bakan723 on 2013-05-15
Have you had any issues since today's updates?

---

### Post by Lightning Dragon on 2013-05-15
Hi,

You mean the Windows XP Desktop crashing warning? Other than that, I have started the patch (currently on "Custimazation" patch) now and will update if I come across any problems. If you cannot patch automatically, you can patch manually. I mentioned how on page 2, I do believe. :)

Or do you mean in game? If so, they added new features/things which might cause a problem for wine. If it runs slower than it use to, try running in a lower resolution or graphic setting.

edit

Server issues thus far.

edit 2

So just now they added another patch that seemed to fix the server issues; it is working now. However, dialouge and gameplay's audio has now become jittery. If this is the issue you are facing, then it is definitely because of the patch. I'll see what I can do to fix it. The game itself seems to run just fine, so it has to be the music/sound that is the problem.

edit 3 

Well, changing the settings did not get rid of it, or changing the resolution. Hmm. Maybe files were currupted.

edit 4

Apparently, something like this has happened before after fresh patches;

[http://www.swtor.com/community/showthread.php?t=567816](http://www.swtor.com/community/showthread.php?t=567816)

---

### Post by bakan723 on 2013-05-15
ok I got it working also just had to reboot the pc.

also wanted to add that the game does not have to be launched through the terminal.  I made links to the swtor_fix.exe and launcher.exe on my desktop and run them by double clicking the icon and game runs just fine.  also i think it may have cut a few minutes off the time spent on blue screen when loading game but that could have just been a fluke I will update when I test it further.

---

