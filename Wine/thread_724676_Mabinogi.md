---
title: "Mabinogi"
date: 2008-03-14
forum: Wine
---

### Post by chameleoneyes on 2008-03-14
Hello!

I was wondering if anyone could give me an installation guide for the game Mabinogi by Nexon (the creators of Maple Story).  I can't get it to install on my laptop (it freezes when I try to validate the download location) and on my desktop it installed, but gave me two error messages, one about switching the language to Korean, I validate and then it says there is a game guard error and that the computer should be rebooted, which I did to no avail.

BTW, I'm using Wine.

Thanks for any help!!  ;)

---

### Post by StormGuy on 2008-03-23
I am having the exact same problem.  It has something to do with the fact that nProtect probes your machine for Windows APIs and complains if it doesn't find them.  It's designed to prevent cheating, but it unfortunately also prevents those of us non-cheaters who still have to run the game in an emulator to play it :(

Has anybody had any success with Mabinogi on Linux?

Thanks!

---

### Post by Deo Favente on 2008-05-08
Crashes while verifying download location? Mine crashes when client.exe is trying to initialize. It pops with an error that says something like "Sorry for the inconvenience but we're retards. The problem description for our retardness has been copied to the clipboard. Please paste the contents (ctrl + v) to the bug report board..." But nothing was copied to the clipboard...

---

### Post by cogadh on 2008-05-08
The error message doesn't really say that does it? It would be freakin' hilarious if it does.

Mabinogi and MapleStory both use GameGuard, which will not work in Wine due to the low level rootkit-like access to Windows system files it requires. Without a functional GameGuard, those games will never run.

---

### Post by kaidreil on 2008-07-21
well so far, I've got it to install pretty smoothly. The actual install went flawlessly, and actually faster on ubuntu than my windows partition :P
aside from that, when I start the actual game launcher, it'll open like normal and begin to download the 'launcher patch' in the lower left corner, and once this reaches 100% it closes the launcher, and you don't hear from it after that. It hasn't got to the point of installing GameGuard because this happens after the first attempted game launch...
Anyways, I tried using the manual patch download to see if it could get the launcher for me, but it only said I already had the latest version of the game.
Gahh

even if Wine isn't windows enough for gameguard, there's got to be some way around it... =/

---

### Post by frushels on 2008-12-10
I managed to get it downloaded and got far enough  so that I could hit game start, but gamegaurd doesnt start up and the window just closes.

---

### Post by quinn149 on 2009-03-05
i actually managed to play the game. gameguard gave me no problems. the game itself however, was so slow it was unplayable despite all efforts to make the game run faster (and i know it's not the fault of my crappy computer this time)

---

### Post by Chii on 2009-03-08
How did you manage to get it to run?   Hoping that I can get it to run on here as I played this some time ago and it's plain fun.  Havent started mucking around with it yet as I've got the downloader obtaining the file atm :>

Thanks!
   -Chii

---

### Post by Randomchaosn on 2009-03-10
i got mabinogi to install effortlessly once i had wine it even starts with out a hitch but when u get to the login screen the graphics go all crazy while the game starts its graphic rendering engine i think its called phizone or something

---

### Post by codya517 on 2009-04-14
Try turning off Glow Effect, works for me and runs fine. Install ran fine too. You could always try the manual patch thing on the website also.

-my problem is when I created an elf character i get a black unresponsive screen when entering the actual game world after talking to Nao.

---

### Post by wolfyking2 on 2009-04-14
how the fudge did you do that????  OMG tell me because mabinogi is the bestest game ever!!  Please tell me how!

---

### Post by codya517 on 2009-04-18
Things You Need First

-Wine, Obviously. - can be found in add/remove package manager
-W32codecs - can be found here: [http://packages.medibuntu.org/intrepid/w32codecs.html](http://packages.medibuntu.org/intrepid/w32codecs.html)
-Mplayer - audio/video player, found here: [http://packages.medibuntu.org/intrepid/mplayer.html](http://packages.medibuntu.org/intrepid/mplayer.html)
-ALSA and NOT PulseAudio (I removed pulse audio from synaptic package manager and installed some ALSA files from there)
-Latest versions of listed above.

Mplayer
-Open Mplayer and right click on the blank screen, select preferences and go to audio and select ALSA and click ok. (in hopes of fixing the blackscreen during movies issue, will talk more about down the walkthrough)

ALSA
-Remember to download an ALSA mixer also, after removing Pulse Audio (if you do, can't promise anything if you don't)
-If not removing Pulse Audio, open terminal and type "pasuspend wine /path/to/winedir/drive_c/nexon/mabinogi/mabinogi.exe" to start the game later, you can also just drop this in a textfile on the desktop and click on that to run this without usingthe terminal.

Installing Mabinogi With Wine.

After downloading mabinogi, the installation is pretty easy. All you need is to have wine already installed and right click on mabinogi's setup.exe (file you downloaded) and select "Open With: Wine Windows Loader Program" And wine takes care of the installation. A Nexon Directory should appear in /.wine/drive_c/Nexon.

After it is installed, go to /Nexon/Mabinogi/movies/ right click on a movie and go to properties and under the "open with" tab select the program "Mplayer Movie Player". This hopefully will take care of various issues if Mplayer is set to alsa.

Configuring Mabinogi In Wine
Take the steps below

-Go to Applications drop down menu, select wine and from that menu select "Configure Wine".
-Click "Add Application" in the Wine program window.
-Select Nexon Directory and browse your way to the Mabinogi.exe and select it.
-Setting the windows version: At the bottom you'll see a drop down menu beside "Windows Version:" I set mine to XP.
-Go to "Graphics" Tab and check "emulate virtual desktop" and then add your desktop resolution in the appropriate fields/boxes.
-Go to "Audio" Tab and check ALSA and at the bottom, "driver emulation".
-Finally, click apply and try running the game.
-Under options ingame, go to graphics and turn off Glow Effect.

Other Things
Older Characters seem to work without any problem. New characters are trickier but hopefully will work with the w32 codecs + mplayer + alsa and won't produce the blackscreen lockup. I haven't been able to test from ingame.

Another issue I have encountered is the game stopping at a black screen when crossing the bridge from connous to rano. I simply shut down and restarted mabinogi and i was on the other side. Doesn't happen all the time though.

Gameguard apparently made it impossible to play the game under wine, but now with gameguard out of the picture everything runs pretty well.

advertisement at closing of game, usually crashes itself after a few minutes or you can alt tab away from it if you have something open (in my case, I have opera open all the time) and then you can just right click-close it.

Again, the character creation crash (after talking to nao) I haven't been able to try my theory yet, but it involves not being able to play the stupid movies and what not, hopefully the PulseAudio and Mplayer workarounds fix it.

---

### Post by HiroSetsuken on 2009-04-20
I got it to work from what you did above, but it lags so horribly. I have an AMD Athlon x2 5400+, 4gb CORSAIR DDR2, and an ATI RADEON x1950. I'm using the Ubuntu 8.10 x64 AMD. Is there something I need to do to make this run smoothly? Also, when trying to run the game every so often the screen will flicker and graphics will mess up :/ Thanks.

---

### Post by codya517 on 2009-04-20
Don't know much about the gpu you have. But I have an intel cpu very similar to your's and it runs fine, and i have 2gb of memory. I am running 32bit though. I think it might be the ati card/driver. Which is...always a fun thing to work out.

But is it latency lag? or FPS issues? I'd mess with some of the settings inside the game and try that. Probably a graphics card/driver issue but if it works with everything else...i'd try not to mess with your drivers

---

### Post by wolfyking2 on 2009-04-21
Ok, I got the game working, can get into the login screen, but once my character shows up, the game just exits.  I'll try to get a terminal output, but other than that I do not know.  I couldn't get Mplayer because you need a lot of libs, and I didn't get ALSA because I'm pretty sure I already have it.  The game lags a lot, like 3 FPS, but I need to get into the graphics options so I can turn off the glow effect.  I have an intel graphics card.

EDIT: I can now get into the world, but when I click start, the screen goes black for like 45 seconds then crashes.

---

### Post by codya517 on 2009-04-21
Intel? Shared video memory?

---

### Post by wolfyking2 on 2009-04-21
Meh, I have no idea what that is, or how to check it >.<

---

### Post by wolfyking2 on 2009-04-21
Sweet!  The problem just went away, and with the graphics at the lowest settings and windowed, the game runs pretty smooth!  Although I have to say, there is a bug annoying me.  When you change channels, it crashes.  Well, for me anyway, just wanted to post a heads up for people!

---

### Post by wolfyking2 on 2009-04-23
Ok...now I can't even get on too my character!  It always crashes the first second it shows the graphics of were I am.  And the game is a little laggy, so is there a way I can get the game faster?

---

### Post by codya517 on 2009-04-23
Well on the surface it seems like it would be your graphics card.

---

### Post by wolfyking2 on 2009-04-23
It was working before!  And I got Mplayer installed and everything, but when I try to rebirth, change channels, or create a character, it goes black then crashes!

---

### Post by codya517 on 2009-04-23
I've never tested changing channels as i never have to. The character creation and rebirth was a theory for people to try to see if it resolved the issue. Also, i figured that people knew the ingame hyperlink buttons wouldn't work. The game isn't going to run perfectly, it's all windows and IE.

I still think the other issues are probably a graphics card issue, intel shared memory isn't that great and can't support much.

---

### Post by Infran on 2009-04-24
There's an IE for Linux, and I've seen it recommended to help get games that use IE running (including Mabinogi).  It might help.  There's a guide that tells how to install it (safe for newbies, at least if they know where Terminal is) [here.]("http://www.telltalegames.com/forums/showthread.php?t=6051")  It's actually a complete guide on how to get a different game working, so you can probably skip over the part about installing Wine, do step 2, and ignore the rest.

I haven't tried it myself, yet (I'll do it in the morning).  If anyone tries it before then: how does it work for you?

I've also heard guides say to install DirectX.  I'm not sure how good of an idea this is, though, because I've heard Wine has something like DirectX built in, and installing the real thing could cause some problems.  If all else fails, maybe?

…Actually, I haven't fully completed the instructions on page 2 yet.

I'm having trouble disabling/removing PulseAudio.  I tried googling it, and so far, all I get from following instructions is error messages (either 'no such directory' or 'insufficient privileges,' if I recall).  I know I set all my Linux audio preferences to 'ALSA.'  I'm not sure if that really counts as disabling it, though.  I also tried the 'pasuspend' command and it said there was no such command.

At my current point, I'm also getting the 'an error occurred - send in the info on your clipboard' (and the clipboard is empty) problem.

---

### Post by wolfyking2 on 2009-04-24
Well, I'll reinstall sometime, and install ies4linux, but I don't think it's my graphics card (who knows) anyways, if you need to install DirectX, do it through winetricks.

---

### Post by codya517 on 2009-04-24
You can fully remove Pulse Audio using the synaptic package manager, that would be how I did it.

pasuspend should work though... odd

---

### Post by Infran on 2009-04-25
I tried uninstalling through the package manager just earlier.  It said it would also have to uninstall 'ubuntu-desktop' because of dependencies and, well, I'm not sure I want to do that.

I thought I'd also mention that I found [this guide]("http://howto.landure.fr/gnu-linux/install-directx-9-0c-on-linux-using-wine"), which, if I understand correctly, is about installing DirectX, and a whole bunch of other things for games, in Wine and having them run *natively.*  I'm currently working on quicktime.

I think I also found where the clipboard information is saved.  I'll add where it is, and how that native stuff works out for me, in a few.

EDIT: Well, it's still crashing.  Nexon logo shows up (as before) then it crashes.

Like I said, I think to get to the crash info, you go to your home folder > Mabinogi > Bug Report.  Each crash log shows up there.  I, personally, have to scroll down to get to the latest one.  ...Half the stuff is in Korean.  I considered posting it here.  Except, I don't think anyone would understand it.  Do you think I should bother sending it to Nexon, though?

On a couple side notes, Wine 1.1.20 just came out and while that guide talks about a way to fix the black screen after installing Quicktime, it was fixed for me when I just logged out and back in.

---

### Post by jolirouge on 2009-06-02
I keep trying to open the installer thing in WINE and I get a pop-up that says, "The path of Mabinogi installation is invalid."

Anyone have any idea what that means?

---

### Post by Ryoshi on 2009-12-23
hey i'm having trouble with Mabinogi. I did everything u said but i get kick out everytime after the HS loads

---

### Post by Shadow troup on 2010-05-03
I'm not having too much luck with that hackshield.
I need a way around that.

---

### Post by Senretsu on 2010-06-02
> **Shadow troup said:**
> I'm not having too much luck with that hackshield.
I need a way around that.
Agreed.
Has anyone been having any luck at all with this since I last checked on it?
I don't even know how to run a virtual machine properly and I'm just taking my first babysteps in Kubuntu, I need to get back online before my guild starts wondering if I died, haha

---

### Post by cogadh on 2010-06-02
There is no way around Hackshield. The only solution is for the game's with it to stop using it. Additionally, Wine will never support Hackshield because of the way it functions (basically it is like a rootkit).

[http://bugs.winehq.org/show_bug.cgi?id=4666](http://bugs.winehq.org/show_bug.cgi?id=4666)

---

### Post by Senretsu on 2010-06-04
> **cogadh said:**
> There is no way around Hackshield. The only solution is for the game's with it to stop using it. Additionally, Wine will never support Hackshield because of the way it functions (basically it is like a rootkit).

[http://bugs.winehq.org/show_bug.cgi?id=4666](http://bugs.winehq.org/show_bug.cgi?id=4666)
I've been experimenting with "playonlinux" lately too... has anybody explored that option? Apparently some people have been getting some success with it. My installer always freezes at 32% though. Argh.

Is a virtual machine my only option? Can someone send me a youtube link of a virtual machine tutorial that doesn't dual-boot? I don't have the RAM to dual boot, and I'm not giving up my Mabinogi. D=

---

### Post by cogadh on 2010-06-04
PlayOnLinux is just a GUI font end for Wine, it still has the same limitations as Wine, so it shouldn't make a difference in regards to HackShield. If anyone is having success with it, it is because they are playing the game via the legally questionable "private servers" that eliminate the need for HackShield.

Virtual machines, by definition, do not "dual boot". A machine that dual boots has two operating systems installed on the hard drive and the user is offered the choice to boot up one OS or the other when the PC is turned on. RAM, beyond the minimum requirements for the OS and any software you plan to run, is not a limiting factor in this process. 

A virtual machine is software that you run within your host operating system (in this case, Ubuntu) that allows you to create a virtual PC (a virtual representation of all the hardware in a computer) that you can install another OS on, like Windows. Virtual machines require a ton of RAM, since the entire virtual machine runs simultaneously with the host OS. Basically, you need enough RAM to run Linux, Windows and any additional software you plan to have running in either system, all at the same time.

---

