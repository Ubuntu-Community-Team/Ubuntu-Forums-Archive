---
title: "Anarchy Online! MMORPG (HOWTO included)"
date: 2006-11-02
forum: Wine
---

### Post by T3h_Dohtem on 2006-11-02
[SIZE="4"]Version 0.6: Dec - 08[/SIZE]
[I]Further updates:
[LIST]
[*]Finished formating all sections.
[*]Added some tips for running AO after installed.
[*]Updated Wine install section with new links.
[*]Added support information for Linuxbot channel.
[/LIST]
[/I]

**_[SIZE="3"]Preamble![/SIZE]_**
A great new service has been launched that will allow players to chat across the servers, as well as with people outside of the game through an IRC link. It is a linux oriented community channel that anyone can join!

If you are already in game simply: /tell Linuxbot !join
If you want to join from IRC here is the info:
Server: irc.funcom.com
Port: 6667
Channel #Linuxbot

More info on Linuxbot can be found [here]("http://forums.anarchy-online.com/showthread.php?p=5388881").

_[SIZE="4"]Anarchy Online Ubuntu Linux Howto[/SIZE]_

[LIST]
[*]Section 1: Requirements
[*]Section 2: Your Display Drivers
[*]Section 3: Wine
[*]Section 4: Anarchy Online
[*]Section 5: Troubleshooting/In Game
[/LIST]

**_[SIZE="3"]Section 1: Requirements[/SIZE]_**

[SIZE="2"]Linux/Ubuntu[/SIZE]
I'm assuming if you're reading this forum you already have, or know how to get Ubuntu, ([www.ubuntu.com](www.ubuntu.com)) so you're on your own there. I am currently using version 8.04.

[SIZE="2"]Wine[/SIZE]
You are going to need to download and install Wine, which is *"an Open Source implementation of the Windows API on top of X, OpenGL, and Unix." [-WineHQ Website]("http://www.winehq.com")*


[SIZE="2"]Anarchy Online[/SIZE]
The game client itself comes in two flavors: Classic or Full. If you are just playing for free, you will only need the Classic client. If you have a paid account, want to start one, or plan to upgrade later, it's much easier to get the full client from the start. It's a larger download, but you will only have to patch once, since when you upgrade, you will need to download the Full client and re-patch it from the beginning. If you want to start downloading now here are the links, but before you install, read Section 4, because there are some issues you may run into while installing.

[Anarchy Online's Download Page]("http://www.anarchy-online.com/wsp/anarchy/frontend.cgi?func=frontend.show&template=drill&func_id=1088&navID=1003,1005,1070,1088")

**_[SIZE="3"]Section 2: Your Display Drivers[/SIZE]_**

It is beyond the scope of this howto to go into detail on how to install or update your display drivers. The only reason I even mention it is because an old display driver can cause the game to not function at all.

If you're an ATI user (like me), you should probably check out the howto here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Nvidia users are on your own for now, if someone wants to PM me with a link, I will add it here, otherwise I recommend the "Search" function on these forums, and of course, there's always [Google.]("http://www.google.com")



**_[SIZE="3"]Section 3: Wine[/SIZE]_**

First you will need to add the GPG key to your trusted list:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

Next you will need to add the repository for your version of Ubuntu:

**For Ubuntu Intrepid (8.10):**
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list
```

**-OR-**

**For Ubuntu Hardy (8.04):**
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

After you've added the repository, updated synaptic with:

```
sudo apt-get update
```

Now, you can install wine by clicking [here]("apt://wine") or by opening Synaptic, and searching for wine.

Once it's installed, run winecfg, click on the "Audio" tab and enable _just_ the OSS Driver.

*[SIZE="1"]Note: Updated instructions for installing wine will always be available at their official[downloads]("http://www.winehq.org/site/download") page.[/SIZE]*


**_[SIZE="3"]Section 4: Anarchy Online[/SIZE]_**


There are a couple ways to go about this, if you have an old disk set, you can easily use that to install from, but copy all the files to one folder on your hard drive, then run the install. There have been issues with multi disk installations on wine. In addition, if you have an old set, you will have a lot of patching to do, and that requires more attention, so it may be easier to just download the whole file.

For the new free accounts, once you have the game (or while you're downloading) go to: [http://register.funcom.com](http://register.funcom.com) and create a new account. There are also options there to upgrade to the expansion and start a subscription.

If you don't have the disk set and you don't want to go out and buy it, you can download it for free. They have changed the download options from time to time, including removing the bit torrent option, so for the most up to date option, head over to their [downloads page.]("http://www.anarchy-online.com/wsp/anarchy/frontend.cgi?func=frontend.show&template=drill&func_id=1088&navID=1003,1005,1070,1088") If for some reason, that link breaks, head over to their main site: 
[http://www.anarchy-online.com]("http://www.anarchy-online.com")

Once you have the Zip, uncompress it and in a terminal window, move to the directory the files are in and run:
```
wine Setup.exe
```
Keep in mind, windows files are not case sensitive, however, linux is, so, you may find that some windows programs capitalize the files, and you will need to make sure you use the proper case when calling those files in linux. Additionally, Windows uses spaces in directory and file names, so you will need to use quotes when calling these directories or files from the terminal. For example, to move to the windows \Program Files\ directory you will need to do:

```
cd "Program Files"
```

With exact capitol letters and quotes because there is a space in the name.

Once the install is completed, you can run the game by opening a terminal, moving to the wine directory, and running the program. Here's an example for those who used the default install directory See below for making a script to launch AO (See the bottom of this document for a script to launch AO from your toolbar, as well as an icon):

```

cd $HOME/.wine/drive_c
cd "Program Files/Anarchy Online"
wine Anarchy.exe

```

Note: what wine calls "C:\" is usually ~/.wine/drive_c/ you can change this in winecfg.


**_[SIZE="3"]Section 5: Tweaks/Troubleshooting/In Game[/SIZE]_**

If you have problems, the best way to reach me is in through the AO [Linuxbot]("http://forums.anarchy-online.com/showthread.php?p=5388881") channel! You can find me and other Linux users there and there are two ways to join. If you are able to get in game, invite yourself by sending a /tell to the bot:
```
/tell Linuxbot !join
```
or you can join the Linuxbot chat from the IRC link:
Server: irc.funcom.com
Port: 6667
Channel #Linuxbot

The IRC and Ingame channels are all connected so you will be able to talk with people ingame from the IRC and vice versa. Also feel free to stick around once you do get ingame and chat with us!

I had problems with launching AO using just the Anome launcher, so here is a script that will fix it. You need to run AO from the directory it is installed in for it to work. Copy the following into a text file, save it, and 'chmod 700' it so to make it executable. Then you can add a launcher to Gnome's toolbar and point it to the script. If you did not install AO to the default directory, you will need to change the script to point it where you DID install it. Finally, you can add an icon to the launcher if you like. I have attached a crude AO logo for your use, the simplest way is to save it to your desktop, then drag it into the properties window of your AO laucher button.

```

cd $HOME/.wine/drive_c
cd "Program Files/Anarchy Online"
wine Anarchy.exe

```

A few notes on small bugs:

If you have problems launching AO initially, don't give up! Some people are only able to play with certain window configurations. I have been able to run it very well in windowed mode, but if that doesn't work for you, try running "winecfg" and setting a virtual desktop, then running AO in fullscreen will still be inside of the virtual desktop window.

You may have keyboard focus issues if you run it in its own desktop window, at one point, all of my odd numbered keys were not working, however, my even numbers were. Usually just clicking somewhere in the window will solve the problem but not always.

If you run into a random crash or other error, PLEASE report the output! ([http://www.winehq.com](http://www.winehq.com))

WELL! I hope this helped someone out, or inspired a few people to play, if you get into the game and need help, or just want an exploring partner, drop me a line! I'm always looking for more people to play with!

---

### Post by Ben Sprinkle on 2006-11-02
Needs to be moved to the HOWTO section.

Never played AA, but it looks dumb. WOW and KO are better.

---

### Post by T3h_Dohtem on 2006-11-02
Is it true what they say about ignorance is bliss?

In any case, this was not meant to be a howto, although it turned that way, its a game that runs well on Wine under Ubuntu, and its free. WoW is a great game, I have an active account for it as well. I'm not sure what KO is. However, I AM sure that With your elaborate testing and detailed comparison of the intricacies of the three games, everyone will find this an even more informative post, thank you for your contribution.

(Edit: KO = Knight Online, looks interesting, might have to try it out [http://knightonline.e-games.com.my/index.asp](http://knightonline.e-games.com.my/index.asp) )

---

### Post by schnarkle on 2006-11-02
> Is it true what they say about ignorance is bliss?

Yes.

And Anarchy Online is a great game.  The original version (no expansion packs) is totally free and is a great value on it's own.

---

### Post by slimdog360 on 2006-11-02
knight online doesnt work in linux. Under wine or otherwise. I remember there was a big thread on it somewhere.

---

### Post by T3h_Dohtem on 2006-11-03
Heh, that figures, Windows fanboy contaminated my post.

I have problems running WoW too :/ So Anarchy Online is great for me cause it runs almost flawlessly.

---

### Post by Ben Sprinkle on 2006-11-03
> **slimdog360 said:**
> knight online doesnt work in linux. Under wine or otherwise. I remember there was a big thread on it somewhere.

Wrong, I have a private server for WoW and KO in linux.

---

### Post by MaximB on 2006-11-03
WHAT ?! synectics - Did you manage to run knight-online on Linux ?
please tell us how....

---

### Post by Ben Sprinkle on 2006-11-03
There are ports everywhere.
Only works with private servers, not the main ones.
Just google a bit for linux ports of older KO clients.
WOW is better than KO anyway.

---

### Post by Ben Sprinkle on 2006-11-03
It's easy to play KO on Linux.

---

### Post by MaximB on 2006-11-03
PLEASE MAKE A HOW TO, I JUST LOVE THIS KNIGHT-ONLINE GAME
I Liked it much better then WOW.
and it's free.

---

### Post by Ben Sprinkle on 2006-11-06
Sometime I will, work has me right now.

---

### Post by muhoweb on 2006-12-21
Can you tell how to run Knight Online on Linux? It's very important for me.

---

### Post by hikaricore on 2006-12-21
I'm gonna give Anarchy Online a try when I get home.  :)  Looks interesting, doubt i'll play it more than once or twice but eh, who knows.  Got it downloading via torrent flux right now as I sit at work.  <3 Torrent Flux

:P

---

### Post by zybir on 2006-12-26
I installed the game and it was working, untill it realized I didn't have my graphics card drivers installed, so after I got that straightened out, I try to run Setup.exe and I get this error. 

"An installation support file could not be installed. (0x8000ffff)"

What a boy to do?  Mind you I'm a noob to linux.

---

### Post by hikaricore on 2006-12-26
Update: The character creation process was more interesting than the actual game.  Screw this.  But thanks for pointing it out.

---

### Post by Doctoxic on 2006-12-29
Hi

I have installed the game OK in Ubuntu Edgy but i can't run it because it won't let me select a driver.  I get the box which shows a choice of only one which is "Direct Draw HAL/Wine direct 3D7 using wind d3d" which i click on, and then selct a resolution - but it doesn't want to accept it and i get a "You must select a device driver and resolution first" message.

The output from my terminal is as follows:

wine Anarchy.exe
err:win:CreateWindowExA bad class name "{8856F961-340A-11D0-A96B-00C04FD705A2}"
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1a6350) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1a5eb8)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock


any suggestions on how to fix this??

thanks

Doc

---

### Post by stiiixy on 2006-12-29
I get the same problem, Doctoxic. But I find if I click around the screen for a little bit, it can go away :D  From memory I just right-clicked on the menu bar up top, selected switch-to, and for some reason worked.Obviously not graceful.

But then I load AO, and it crashes at the moment it is fully loaded (3 times the load speed of Windows!?). It worke dproperly once, but not anymore.

---

### Post by Doctoxic on 2006-12-30
thanks Stiixy


i'll have a play around

if it helps there is some info here:
<<http://appdb.winehq.org/appview.php?iVersionId=514>>
of similar problems

though i didn't find it particularly clear - i did try a change to my main.cfg file but ti didn't wotk - but i'm not sure i did it right

if you have any luck please let me know

thanks

Doc

PS - maybe its the latest version of wine messing things up??

---

### Post by mongrol on 2006-12-30
I can't even install it. Wine 0.9.28. Downloaded 0.15 of AO from Ausgamers. UNpacked. Wine setup.exe and installshield fails. COnsole shows the following;

```
mongrol@smile:~/temp/ao$ wine setup.exe
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000001-0000-0000-c000-000000000046}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {00000001-0000-0000-c000-000000000046}, 80040155
fixme:ole:CoRegisterClassObject CoMarshalInterface failed, 80040155!
err:ole:CoGetClassObject no class object {91814ec0-b5f0-11d2-80b9-00104b1f6cea} could be created for context 0x4
mongrol@smile:~/temp/ao$ err:ole:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d

mongrol@smile:~/temp/ao$ wine --version
wine-0.9.28
```

---

### Post by mongrol on 2006-12-31
ok, installed it by using a Windows installation but now I get the display driver problem. Can't choose a drive so can't play the game.

---

### Post by CameronCalver on 2006-12-31
I'd like to play aa aswell but i get errors when im trying to download  these are them 
i do ```
wine setup.exe
```

---

### Post by cazimir on 2007-03-05
When i try to play Anarchy Online with wine 0.9.32 on Ubuntu 6.10 ,the game want to choose my 3d videocard..i select it but it gives me the following error:An invalid argument has encountered and i can't launch because the game think i don't have a 3d videocard.
What can i make to play this game with wine?

---

### Post by timjayko on 2007-03-05
I tried this game free trial and tested on cedega and wine... it runs soooo much better in cedega..

---

### Post by joshlfisher on 2007-04-05
I tried it in Wine, and it works ok. I'm gonna try cedega now.

---

### Post by joshlfisher on 2007-04-05
I also tried Cedega. MUCH better performance in Wine.

Specs are:

Acer TM4200 Laptop
Centrino 1.6 GHZ
2GB RAM
128MB Graphics Shared memory

---

### Post by joshlfisher on 2007-04-05
> **CameronCalver said:**
> I'd like to play aa aswell but i get errors when im trying to download  these are them 
i do ```
wine setup.exe
```

Sounds like you have a corrupt installation file.

---

### Post by Laryllan on 2007-05-08
About the thing that you cannot change graphics device:

1. select resolution
2. select video driver
3. press SPACE
4. select OK

Now it should work.
It's a bug in Wine as far as I know.

---

### Post by Doctoxic on 2007-06-23
thanks Laryllan - that worked  :)

now getting the folloing error messages when patching:
Cannot create inventory files
Tried to create existing file 2

any idea how to fix?

thanks

---

### Post by Laryllan on 2007-06-23
What Version are you trying to patch?

I just copied my 17.X version from windows to my Ubuntu partition and have no problems with patching since then.
But I read there may be issues with version older than 16.X.

---

### Post by Doctoxic on 2007-06-24
sorted

it was a permissions problem - i just ran the patcher with sudo

doc

---

### Post by Laryllan on 2007-06-24
I usually i run the game using Cedega, because it is much faster.

How is your performance in Wine?

In Cedega, I get ~35fps in the Shadownlands Backyard, while in Wine It's only ~16fps... :(

---

### Post by redson2 on 2007-06-26
I cant seem to get this to work. I have ATI card, with all the drivers, installed and patched to latest version. When I run in windowed mode the screen goes blank then nothing happens and my desktop appears. I'm getting Cedega from CVS but I'm not that sure how to build it. I'm going to try to run AO in wine again maybe not windowed see if that helps.

---

### Post by Laryllan on 2007-06-26
As Wine and Cedega use the same 'base', games working in Wine usually work in Cedega too and vice versa.

Try to get it working on Wine first. There are some tipps in the Wine wiki and in the technical section of the official AO forum there is a thread about running AO in linux - maybe there you'll be able to find a useful hint.

---

### Post by Omnios on 2007-07-11
From another thread
> problems solved. If you get a cannot access C: delete ./wind and run wincfg to make a new C. directory.

 The game will not install in the base wine install and I found a script that helps install stuff for wine that works really well/

 The script is here                 [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
Right click and save link as.  winetricks.sh and make it executable.

 Running the command    sh winetricks

 This will show a list of installable stuff which can be installed using. sh winetricks corefonts where corefonts is the file being installed.

 
 
 I installed the DCOM and the ms installer before installing the game.

 I read this here on Mepis [http://www.mepis.org/docs/en/index.php/Wine_setup](http://www.mepis.org/docs/en/index.php/Wine_setup)

 Also the install seems to be a bit dirty in that when you launch setup.exe it states to run install.exe which works. I'm having a problem with the included Xfire program as the language install poped up behind the main installer window. This is solvable by clicking on the task bar and choosing move and moving to a empty place on the sreen. Anways launching the game with wine right now and will post results in case of a crash. Also did install with desktop affect off as the install screens where unreadable.
                                                               __________________> k it want to launch but i am getting stumped on a res and vid driver screen. Anywone have any ideas?

 Solved choose a lower res and double clicked on the wine vid driver.
 
 Going to go play so laterz.

Log in and patching working,,, Laterz dude

 Had a problem patching it froze up and now I am doing a reinsatll
Might have to use manual patches.> Dam I seem to have a little devil looking over my shoulder. I managed to gt it installed and the graphics config worked before and I managed to log in and it crashed at the updater after choosing to upgrade. 

 Well now it does not want to even install properly or run. I might have to reinstall wine or find a way to kill the regestry. 

 Ultima online sucked and sucks so I hope I can get this to work.

 K got it to install and run again. 

 Solved the vid set up by opening winecfg and clicking vid and closing which is wierd

 I have to patch so ging to have to do a manual patch as a winhq page said that autopatch did not work in wine.As the client patcher failed I tried downloading and manually installing the patches. This caused another problem as I got this error in the terminal.

```
Dam I seem to have a little devil looking over my shoulder. I managed to gt it installed and the graphics config worked before and I managed to log in and it crashed at the updater after choosing to upgrade. 

 Well now it does not want to even install properly or run. I might have to reinstall wine or find a way to kill the regestry. 

 Ultima online sucked and sucks so I hope I can get this to work.

 K got it to install and run again. 

 Solved the vid set up by opening winecfg and clicking vid and closing which is wierd

 I have to patch so ging to have to do a manual patch as a winhq page said that autopatch did not work in wine.
```This is the full error I even tryed downloading the DLL and it still did not work.
```
$ wine AOPatch_v17.1.1-v17.1.2.exe 
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\temp\\pft2cc0~tmp\\CopyPatch.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\temp\\pft2cc0~tmp\\CopyPatch.exe" failed, status c0000135
tom@miko:~/.wine/drive_c/Program Files/Funcom/Anarchy Online/patching$ wine AOPatch_v17.1.1-v17.1.2.exe 
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
err:module:map_image Could not map section .text, file probably truncated
err:module:import_dll Loading library MFC42.DLL (which is needed by L"C:\\windows\\temp\\pft99de~tmp\\CopyPatch.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\temp\\pft99de~tmp\\CopyPatch.exe" failed, status c0000135
``` Dll error solved: originally I had a dll that was only about 90k, I replaced it with one that was 900k.

 Manual Patching works. 
Testing client autopatch.

 autopatched with client from v17.1.2.exe to v17.4.0.exe. seems to be stuck for v17.4.1.exe

Full patch successful v17.1.2.exe to v17.4.0.exe seems to be a normal patch process.

---

### Post by Omnios on 2007-07-11
Re: Anarchy Online! MMORPG working with wine. July 11 2007

 wine version=  0.9.40
 used script=link=[winetricks]("http://www.kegel.com/wine/winetricks")
                           used = sh winetricks corefonts , sh winetricks msi2 , sh winetricks dcom98
 need = MFC42.DLL working version was about 900k

 Insall works =used install.exe
 client auto Patch works with = MFC42.DLL installed
 Game runs = checked out up to character creation.

 :popcorn:

Im giving this game 5 stars :KS:KS:KS:KS:KS

 Another hack by omnios Cheers.

---

### Post by gorkur on 2007-07-13
Game installed and worked fine using Feisty and Wine 0.9.33. Patcher had some problems but only needed to run it again for it to complete the patching process :)

Got completely lost in the game and spent 3 straight hours on it :lol:

---

### Post by Omnios on 2007-07-16
not really a serious problem but found the game would only launch from typing in the terminal as apposed to clicking on the exe either with run or run in terminal.

---

### Post by Omnios on 2007-07-19
Hi here is an update the install works ok but found setting the graphics was a pain as 
i sat there and did multiple click combos till something worked after a while. I will look into a config mod if possible to eleviate this.

 K launching the game normally ends up with the gnome panels covering some of the screen. I solved this by making a sh hack to launch the game in a virual window that is smaller than my desktop res. 

```

#!/bin/bash
#

cd /home/tom/.wine/drive_c/Program_Files/Funcom/Anarchy_Online & wine explorer /desktop=name,1500x1100 Client.exe


```
the cd points to your game client file the _ is used for spaces in ther terminal. The wine explorer /desktop=name,1500x1100 Client.exe launches a virtual desktop wit ha res mine is 1500x 1100 as it fits in my 1600 res. I think it can be any res you want. 

 Also desktop affects can make the game sluggish.

 anyways cheers.

---

### Post by Ripfox on 2007-07-19
> **Laryllan said:**
> I usually i run the game using Cedega, because it is much faster.

How is your performance in Wine?

In Cedega, I get ~35fps in the Shadownlands Backyard, while in Wine It's only ~16fps... :(

I have found that games run just as fast if not faster in Wine vs Cedega

---

### Post by Laryllan on 2007-07-20
> I have found that games run just as fast if not faster in Wine vs Cedega

Hehe, do you mean generally or Anarchy Online? Because this is an AO thread.
And if you tried AO in Wine and Cedega, did you test the Shadowlands, especially Adonis under water aereas, or the interior of alien ships?

---

### Post by Omnios on 2007-07-20
I was a close gdm for ubuntu on th e web that closes the desktop and runs the game full screen I will try googling it again as it might be a beter option for someone with a slow screen.

---

### Post by Ripfox on 2007-07-20
> **Laryllan said:**
> Hehe, do you mean generally or Anarchy Online? Because this is an AO thread.
And if you tried AO in Wine and Cedega, did you test the Shadowlands, especially Adonis under water aereas, or the interior of alien ships?

I am aware what this thread is about, I was merely commenting on my experience with wine vs cedega (since you asked) sorry I did not specify, but still relevant. :eek:

---

### Post by Ripfox on 2007-07-20
My main problem is patching...I get a permissions error. I tried running the patcher as sudo, didn't work either.

---

### Post by Ripfox on 2007-07-20
Ok now I reinstalled it, and when I hit "patch" it says "no valid patches found" and closes the program completely...stuck in this cycle.

---

### Post by bINSkeeter on 2007-07-20
I need help i try to run Setup.ex_ and this is the error message i get please someone help.:confused::(

---

### Post by Laryllan on 2007-07-20
I didn't install the game, I copied the folder directly from my old windows installation.
It is said that you a need a version after 16.4. for use with Wine/Cedega.

---

### Post by Ripfox on 2007-07-21
My version i downloaded was v 17. something...

---

### Post by drifterx on 2007-07-23
I had recently install Anarchy Online. Everything went pretty smooth and fine, until I finally got to the very last part, which is just clicking the button to get in the game. As soon as I do, the screen simply flashes black. The only thing I can think of is that its a graphical problem. I don't think it's a problem w/ my hardware, it's a fairly new laptop, about 512 RAM, and a fairly good video card. It ran Everquest 2 at one point (pretty choppy though, but it ran nonetheless, and this was on Windows), and AO's graphics aren't exactly so intense that my computer can't handle it. Any help would be appreciated.

---

### Post by Laryllan on 2007-07-23
If you can hear sound and are using another window manager than Gnome's MetaCity, try that one.
Other than that, I have no clue...

For me it doesn't wok in XFCE (and Cedega), only with Gnome.

---

### Post by drifterx on 2007-07-23
I am using the GNOME desktop environment. After I logged back on, I tried AO again, and now the client no longer starts, and it gives no real error message in the terminal. I attempted to use wine to open both Anarchy.exe and Client.exe, to no avail. I have no idea what could be the problem, I could attempt re-installation, but I'd rather go through other options before resorting to re-installation. Any help is appreciated.

---

### Post by Omnios on 2007-07-23
Well i have been playing AO for about a week now and just now it stoped working with wine. I log in and log on the game loads and comes to focus and then just clashes with a poof wine is not running anymore. Over the last few days I have had some performance problems pertaining to using 100% or my 265megs ram. I shut off desktop affects and it ran better till this morning. 

 I have been having problems for a few days where root was being used. I have been using Ubuntu for about 3 years now and root does some funny things that gives it a signature where you can tell root or another user is logged. 

 I forgot the progy and file name to see the server stuff to secure Ubuntu, any help.

 Also performance problems are really anoying as when it lags it kind of stutters and your character moves very slowly. Unfortunatly I got killed like 10 tiems running from monsteres in this way,

 Lastly AO just stopped working no upgrades patches or anything else added to the system. 

 Anyone have any suggestions as wine in terminal shows no errors it just quits.

---

### Post by Omnios on 2007-07-23
K played around a bit and it seems wine crashes when it can not connect to the server. Think my connection is going to nota and wine crashes.

---

### Post by bINSkeeter on 2007-07-26
:):) I got it working Now how do you get a desktop icon or and application icon....any idea?

---

### Post by bINSkeeter on 2007-07-26
yeah now i have the same problem with connecting to the server any suggestions yet???:confused:

---

### Post by Omnios on 2007-08-10
> **Omnios said:**
> Hi here is an update the install works ok but found setting the graphics was a pain as 
i sat there and did multiple click combos till something worked after a while. I will look into a config mod if possible to eleviate this.

 K launching the game normally ends up with the gnome panels covering some of the screen. I solved this by making a sh hack to launch the game in a virual window that is smaller than my desktop res. 

```

#!/bin/bash
#

cd /home/tom/.wine/drive_c/Program_Files/Funcom/Anarchy_Online & wine explorer /desktop=name,1500x1100 Client.exe


```the cd points to your game client file the _ is used for spaces in ther terminal. The wine explorer /desktop=name,1500x1100 Client.exe launches a virtual desktop wit ha res mine is 1500x 1100 as it fits in my 1600 res. I think it can be any res you want. 

 Also desktop affects can make the game sluggish.

 anyways cheers.

 Found if you make a link for the above script you may make a desktop launcher for the game that works.

---

### Post by mendozaro on 2007-11-14
Hello all. I am noob in linux... but decided to use UBUNTU as my only OS.
I whant to play AO and i have some problems in patching it (installing went ok for me)....
To be more exact it gives me this error (in a window) -> "An unsupported operation was attempted" and this error in the console -> atachment 2.

I might ad that i did use winetricks.sh and installed corefonts, dcom98 and msi2.
Also i did solve the problem wih the rights for C drive by makeing another C drive and also changed some privileges there.

Any help would be apreciated.

---

### Post by mendozaro on 2007-11-14
I solved the problem with the patcher by updating the darn game using VirtualBox and win xp installed in it.
Now i have a problem runing it. It starts... let me log in... choose my char and when it tryes to start the visual interface... crashes back to desktop leaving me with a nasty 640x480 res. At this point i need to log out and log back in to resolve the res problem. Also... there is no actual message... ill try it in a console to see if i get any message there...

---

### Post by mendozaro on 2007-11-14
So this are my errors from the erminal:

> fixme:d3d_surface:IWineD3DBaseSurfaceImpl_Blt Can't handle WINEDDBLT_ASYNC flag right now.
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

This is where i go to wine to see what is about this...

---

### Post by Laryllan on 2007-11-14
I have this Problem too and have to use Windows to patch the game.
My guess is, that they modified the patcher to work on Vista, which is not well supported by Wine.

---

### Post by mendozaro on 2007-11-14
BUT!!
How do you make the game actually work?
I mean... i did patch the game but still cant play cause it fails to load the game...

Thanks in advance.

---

### Post by Laryllan on 2007-11-14
Playing is no problem for me.

Did you select a proper graphics device?

---

### Post by mendozaro on 2007-11-14
Where to select the correct display device? You talking about wine or in AO?
In AO i have set the graphics to Direct HAL rendering device... and it doesn't work.  I have an integrated intel GM 945 graphics card... maybe this helps.

P.S. i've tried all graphics settings in AO and still doesn't work.

---

### Post by Laryllan on 2007-11-14
Yes, in AO.
I select *Direct Draw HAL - Wine D3D7 TL HAL* and it works. Don't know if it's an issue with your graphics card or not...

Have you tried Cedega?

---

### Post by mendozaro on 2007-11-14
Nope... I read that Cedega is comercial...

Bottom line:
This has been for me the last drop that filled the cup... i am returning to windows...  and probably "use" ubuntu as a second os.

---

### Post by mattchew on 2008-02-03
So, I'm trying to install AO for my first time on Ubuntu after suggestions and ideas of games to play, etc.

When I try to run the patcher (manually or by running the patcher itself), I get error messages as shown in my screenshot. Any ideas? I'm going to look up the error itself but had no luck so far even with winetricks.

---

### Post by savethewabbit on 2008-02-05
i've got a weird problem with AO. 
i install it and everything goes fine, but after i finish the installation, the game just disappears. it's not under 'wine' in 'applications', there's no AO folder in the 'drive_c'. i tried rebooting and nothing changes. 
anyone guesses what's up with this? :\ i tried installing it again and the same happens.

---

### Post by pmj on 2008-02-05
> **savethewabbit said:**
> i've got a weird problem with AO. 
i install it and everything goes fine, but after i finish the installation, the game just disappears. it's not under 'wine' in 'applications', there's no AO folder in the 'drive_c'. i tried rebooting and nothing changes. 
anyone guesses what's up with this? :\ i tried installing it again and the same happens.

The default path is "~/.wine/drive_c/Program Files/Funcom/Anarchy Online". I just installed and updated it using the old patcher, and it all worked fine for a couple of hours. If you haven't updated wine yet, do so, as the version in the Ubuntu repos is rather old.

However, when I teleported away from the starting area to a city called Borealis, and started walking around in the city, the game crashed and will now crash every time I start it and it has finished loading. Is anyone else having issues like this?

---

### Post by savethewabbit on 2008-02-06
> **pmj said:**
> The default path is "~/.wine/drive_c/Program Files/Funcom/Anarchy Online". I just installed and updated it using the old patcher, and it all worked fine for a couple of hours. If you haven't updated wine yet, do so, as the version in the Ubuntu repos is rather old.


i do have the updated version of wine... the problem is that there's no Funcom folder in my 'program files' :\ and i installed the game twice, so something should be there. bah. who knows.

---

### Post by silentb on 2008-04-21
> **savethewabbit said:**
> i do have the updated version of wine... the problem is that there's no Funcom folder in my 'program files' :\ and i installed the game twice, so something should be there. bah. who knows.

uh, i'd say, this isn't supposed to happen ^^. did you try to "rm -rf .wine" all wine configuration?

---

### Post by PapiljonChepe on 2008-06-13
I have the same problem as mendozaro, new to ubuntu aswell :)
I patch it, login, select character, press play and everything just vanishes. Starting it in terminal gives thes errors:
> poengel@poengel-laptop:~/.wine/drive_c/Program Files/Funcom/Anarchy Online$ wine Anarchy.exe
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PROCESSOR_PERFORMANCE_INFORMATION
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec0c,0x00000000), stub!
[email]poengel@poengel-laptop:~/.wine[/email]/drive_c/Program Files/Funcom/Anarchy Online$ err:module:attach_process_dlls "RPCRT4.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Funcom\\Anarchy Online\\Client.exe" failed, status c0000005

I've checked, and RPCRT4.dll is in the System32 folder. Anyone got ideas of how to fix this?

---

### Post by mtgmutton on 2008-07-16
I have gotten everything installed and running. My only problem is that the game is very jumpy, even if I turn down the graphics settings.Does anyone know how to fix this?

---

### Post by Laryllan on 2008-07-16
What do you mean exactly?

The game loads some textures on the fly, so there can be 'lags' when entering new areas, especially crowded areas.
A faster filesystem and/or a faster HDD can solve this.

The situation is way better /w Cedega than Wine.

---

### Post by mtgmutton on 2008-07-16
> **Laryllan said:**
> What do you mean exactly?

The game loads some textures on the fly, so there can be 'lags' when entering new areas, especially crowded areas.
A faster filesystem and/or a faster HDD can solve this.

The situation is way better /w Cedega than Wine.

I guess in technical terms, it has a low framerate. And doesn't Cedega cost money? i'm not willing to pay money to play a free MMO! :D

---

### Post by tekwerx on 2008-07-16
AO, for the moment, is still based on DirectX 7.  As such, even in Windows, it is jerky and laggy.  Have patience though, theyre redoing the whole engine and will be releasing it with all new graphics soon, based on DirectX 9.  There's not too much you can do till then.

---

### Post by Xyphos on 2008-07-28
I've got a HOW-TO for installation posted on their official forums.

[http://forums.anarchyonline.com/showthread.php?t=534128](http://forums.anarchyonline.com/showthread.php?t=534128)

---

### Post by mtgmutton on 2008-08-28
I liked how well your tutorial stopped me from getting unhappy error messages. Thanks :)

Unfortunately, now i can't run the game. It gets to login and tries (and fails, apparently) to download a new version of the patcher file, and restarts. Any advice?

---

### Post by Laryllan on 2008-08-29
1. Open the game. You're now in the logon menu.
2. Copy an old *anarchypatcher.exe* to your AO directory.
3. Press 'Patch'. It will patch now.

4. Play. ;)

---

### Post by mtgmutton on 2008-08-29
It took a while, but eventually it downloaded a bunked version. I'll just use the old version when updating. Thanks for the help :D

---

### Post by Psy-Q on 2008-10-29
There's a workaround that lets you run and patch AO normally without needing a Windows installation to patch with.

Basically, you install ies4linux (which gets you IE 6.0 without messing up your WINE install) and then run AO with that specific instance of IE6 as HTML renderer. Then, the patcher works:

[http://rca.vmk.zhdk.ch/blog/articles/2008/10/29/running-newer-anarchy-online-under-wine/](http://rca.vmk.zhdk.ch/blog/articles/2008/10/29/running-newer-anarchy-online-under-wine/)

---

### Post by Lupusceleri on 2008-12-06
Means (the game director) stated in the Friday with Means of 4 december that the new engine is based on opensource project Ogre, current version 1.6.

[http://www.ogre3d.org/](http://www.ogre3d.org/)

So, maybe, there's hope for a native AO client as the core of the new engine is made crossplatform already?

---

### Post by Laryllan on 2008-12-06
This sounds promising! :D

---

### Post by mtgmutton on 2008-12-07
cross your fingers :)

---

### Post by Lupusceleri on 2008-12-13
Any chances someone can upload the old patcher somewhere, so I can download it and actually patch AO up under Linux? ^^

Thanks!

---

### Post by Laryllan on 2008-12-13
[http://www.yaroze.se/upload/OLDPatcher.exe](http://www.yaroze.se/upload/OLDPatcher.exe)
You need to rename it to 'AnarchyPatcher.exe'.

There are plenty of infos on how to patch and resolve issues at [http://forums.anarchy-online.com/index.php](http://forums.anarchy-online.com/index.php), this thread or forum might help too: [http://www.cedega.com/forums/viewtopic.php?t=9512](http://www.cedega.com/forums/viewtopic.php?t=9512).

As said before, performance in Cedega is way better than in Wine.
I think there is a 30-day trial version available.

---

### Post by Lupusceleri on 2008-12-13
Ok, next problem.

I installed AO (under Linux) to an NTFS partition, since my /home partition (ext2) is only 8 GB... I figured I'd drop all my documents and things on the NTFS partition anyway when I set up my PC!

But who'd expected that Wine would dump it's programs all under /home/martijn/.wine/...

Anyhow, I installed AO to my NTFS drive now (/media/VistaPrograms/UbuntuWinePrograms/Anarchy Online), but AO can't seem to write to the disk... it can't write into prefs.xml, it can't write down patchfiles, etc.

Any idea how I can give AO permissions to write to that whole Anarchy Online directory? Even if I gksudo into Nautilus and try to change permissions, it's just changed the who-owns-it-permissions back as soon as I relog into my normal account, and as you can see it has a grayed out "everyone can read/write/create folders/execute programs" choice.. so it seems permissions are set OK? See screenie.

---

### Post by Laryllan on 2008-12-13
Did you try to install **ntfs-config**?
It's a little program that allows you to set read/write permissions on your NTFS drives. Available due synaptic manager.

---

### Post by Lupusceleri on 2008-12-13
> **Laryllan said:**
> Did you try to install **ntfs-config**?
It's a little program that allows you to set read/write permissions on your NTFS drives. Available due synaptic manager.

I can read/write to my NTFS drives without a problem, I did install AO already to the drive (using wine to run the setup program), I can change files and things, I can create folders, I can do everything... But somehow AO can't.

And yeah I've got ntfs-config too. :)

EDIT: And when I run the stuff I'm absolutely sure that my NTFS drives are mounted to a folder in /media, too.

---

### Post by Laryllan on 2008-12-13
Unfortunately I'm not the guy who knows a lot about linux filesystem permissions, but I am sure this is your problem. On your screenshot the folder is owned by root.
Try to change the owner of the anarchy folder to yourself, but be sure to make a backup before doing that. 
chown YOU -R FOLDER or sth like that, read the manpage or google or search the forums. ;)

---

### Post by Lupusceleri on 2008-12-14
Ok I solved that problem by reinstalling AO to an ext3 partition (rather than NTFS). Got it to patch properly now (to 17.10.3), except for one thing........

Whenever I boot it up, it wants to download a new AnarchyPatcher.exe, even after I put back the original AnarchyPatcher.exe (the one I got when I installed the game). And so it deletes the old AnarchyPatcher.exe, starts downloading, fails the download or something, and then restarts Anarchy.exe.

Any workarounds for this? :p

---

### Post by Laryllan on 2008-12-14
This is no problem as long as you don't want to patch.
If you have to patch, start the game to the login screen. *After that* replace the patcher...
...patching should work now.

---

### Post by Lupusceleri on 2008-12-15
> **Laryllan said:**
> This is no problem as long as you don't want to patch.
If you have to patch, start the game to the login screen. *After that* replace the patcher...
...patching should work now.

That was kinda the problem, I had patched to 17.10.3 using this method but then it still kept on downing the patcher. Anyhow I got it working now.. :)

It's a bit crashy at times (whenever I tab or compiz to another window/desktop), and the letters are hard to read (from the item stacks) but for the rest it's fast. :)

---

### Post by T3h_Dohtem on 2008-12-30
Yay! Updated information, as well as some info on the new Linuxbot chat community for talking to other Linux/AO users in or outside of the game!

---

### Post by rp181 on 2009-03-24
Sorry for bumping such an old thread, but im stumped =p

Im running Ubuntu 8.10, and i have Anarchy Online installed. The only [serious] problem i have is i dont have a cursor, or rather i can't see it. From another forum, someone said i have to get rid of software cursor, and modify wine to use a Hardware cursor. Does anyone know how?

---

### Post by loudog23 on 2009-03-29
Easy Setup, No script, all legal, no crash, Newbie proof, Not even a Terminal window! 15-20 Min + Patch and you play

'file&link' are sigle quoted
[Button] are bracketed
"select&Inputbox" are double quoted

1._Get Files_
1.1 Get PlayOnLinux 'http://www.playonlinux.com/en/download.html'
1.2 Get 'AdvancedWineConfiguration_3.5.1.pol' (bottom of download page)

2._Install and run PlayOnLinux_
2.1 Install PlayOnLinux
2.2 (On Ubuntu) [application] -> "Games" -> "playonlinux" 

_3.Install Advanaced Wine Config (To enable -Opengl)_
3.1 CLick [Install]
3.2 (Bottom left) click "Install a .pol package or an unsuppoerted application"
3.3 Select "Install a .pol package"
3.4 Browse to find 'AdvancedWineConfiguration_3.5.1.pol' you just downloaded
3.5 Click [Next] and complete instalation wizard

_4.Install Ie4Linux (To Fix Patching Issue)_
4.1 Click [Install]
4.2 Select "Internet" in the left Menu
4.3 Select "Internet Explorer 6" From the list on the right 
4.4 Click [Apply] and Complete Installation Wizard

_5.Install Anarchy Online_
5.1 Click [Install] 
5.2 (Bottom left) click "Install a .pol package or an unsuppoerted application" 
5.3 Select Manual Installation -> [Next] -> [Forward]
5.4 Select "Edit an application already installed" -> [Forward]
5.5 Select "ie6" -> [Forward] -> [No]
5.6 Browse to find the Anarchy Installer.exe ('AnarchyOnline_17.9.1_EP1_EP2_EP3.exe') -> [Open] -> [Forward]
5.7 Complete Anarchy Instalation Wizard -> [Forward]
5.8 At the "Do you want to create a shortcut ..." click [Yes]
5.9 Browse to find 'Anarchy.exe' -> [Open] -> [Forward]
5.10 Type a Name for your shortcut
5.11 Select Desktop and/or Menu (or none if you only want it in the Playonlinux window)
5.12 **Second time** you get the "Do you want to create a shortcut ..." click [No]

_6.Tweaks (Enable Sound and Open GL)_
6.1 Select your AnarchyOnline shortcut (Inside playOnLinux)
6.2 Click [Configure this Application]
6.3 [Forward] -> Select "Configure wine" -> [Forward]
6.4 Tab[Audio] -> Set your sound (default works of me) -> [Apply] -> [Ok]
6.5 Select "Use advanced wine configuraiton plugin" -> [Forward]
6.6 [Forward] -> Select your AnarchyOnline Shorcut -> [Forward]
6.7 select "DirectDrawRender" -> [Forward]
6.8 select "OpenGl" -> [Forward] -> ...Wait... -> [Forward]
6.9 [Cancel] to exit config menu

7.Play
7.1 Select your anarchyonline shortcut -> [run]

**_*[CENTER]THEORY[/CENTER]*_**
In order to get the patcher to work you need Internet explorer from windows. I found a thread where it make you intal ie4linux and run the Anarchyonline in the ei4linux Wineprefix. Since Playonlinux makes separate Prefix for each game and allow you to insert more than one application in the same prefix, you can by default get you AO running inside Ie4linux prefix.

**_*Other Benifit*_**
PlayOnLinux also provide you with nice plug in and tools totweak your game, if you know your way around i suggest you take a peak at the advance wine config.

Enjoy, Lou

---

### Post by Lupusceleri on 2009-07-20
Macrosun, an AO dev, was so kind to make a HOWTO for AO on Linux, including working "new" patcher.

[http://forums.anarchy-online.com/showthread.php?t=557615](http://forums.anarchy-online.com/showthread.php?t=557615)

[QUOTE=Macrosun]This step-by-step guide will help you install and run AO in Linux (including working patcher). Note that this guide is [color=red]COMPLETELY UNSUPPORTED[/color], Funcom support staff will NOT help you with anything related to this guide, or any problems you might encounter with the install while playing using this setup.

The only supported operating system for Anarchy Online is Windows, and you will be doing this entirely at your own risk. Basic Linux commandline knowledge is assumed.

1) Install Wine.

2) Download and install IEs4Linux. Select the options to install IE6. I will assume you used the default install directory of ~/.ies4linux.
```
tar xvzf ies4linux*
cd ies4linux*
./ies4linux
```

3) Make a copy of ~/.ies4linux/ie6 and call it ~/.wine-ao.
```
cp -R ~/.ies4linux/ie6 ~/.wine-ao
```

4) Download [the 18.1.1 full install](http://l3cdn.ageofconan.com/download/AO/AnarchyOnline_18.1.1_EP1_EP2_EP3.exe)

5) Run the AO installer. Accept the default install path.
```
export WINEPREFIX=~/.wine-ao
wine AnarchyOnline_18.1.1_EP1_EP2_EP3.exe
```

6) Create a startup script. Save it with whatever name you want (ao.sh, for example).
```
#!/bin/bash
export WINEPREFIX=~/.wine-ao
cd $WINEPREFIX/drive_c/Program\ Files/Funcom/Anarchy\ Online
wine Client.exe
```

7) Set the proper permissions.
```
chmod a+x ao.sh
```

8) Run the script.
```
./ao.sh
```

To uninstall, delete ~/.wine-ao.[/QUOTE]

---

### Post by mtgmutton on 2009-07-20
awesome! thanks much for telling us :D

---

### Post by Frostsongr on 2009-10-08
I noticed there are no Maintainers or Super Maintainers currently for Anarchy Online at the WineHQ website if anyone was up to it you should apply to become one.

[Be a maintainer of Anarchy Online Internet Play](http://appdb.winehq.org/objectManager.php?sClass=maintainer&sAction=add&iVersionId=514&sTitle=Be+a+maintainer+of+Anarchy+Online+Internet+Play&sReturnTo=http%3A%2F%2Fappdb.winehq.org%2FobjectManager.php%3FsClass%3Dversion%26amp%3BiId%3D514)

[Be a Super Maintainer for Anarchy Online](http://appdb.winehq.org/objectManager.php?sClass=maintainer&iAppId=355&sAction=add&sTitle=Be+a+Super+Maintainer+for+Anarchy+Online&sReturnTo=http%3A%2F%2Fappdb.winehq.org%2FobjectManager.php%3FsClass%3Dapplication%26amp%3BiId%3D355)

---

### Post by Laryllan on 2010-11-27
AO seems to have stopped working since patch 18.4.1 from November 2010.
Anyone still playing /w Wine?

---

### Post by Laryllan on 2011-10-30
Here is what to do:
[http://insomnia-gravis.org/forum/viewtopic.php?f=10&t=1431](http://insomnia-gravis.org/forum/viewtopic.php?f=10&t=1431)

---

