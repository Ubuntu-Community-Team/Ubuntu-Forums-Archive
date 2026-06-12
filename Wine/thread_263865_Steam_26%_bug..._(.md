---
title: "Steam 26% bug... :("
date: 2006-09-23
forum: Wine
---

### Post by gogogo111 on 2006-09-23
Does anyone have a solution to the Steam 26% bug? I've tried about ten times and it hasnt worked yet....

So..any solution?

---

### Post by pay on 2006-09-24
After it crashes type ```
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```into the terminal.

---

### Post by gogogo111 on 2006-09-24
I tried that, and I got this

---

### Post by haxer on 2006-09-24
Hmm.. looks like you got an 64bits pc?

---

### Post by gogogo111 on 2006-09-24
Nope. Im running 32bit Ubuntu with these specs:

Intel Pentium 4 2.4ghts HT
1.5GB of ram
Geforce 6600GT.

:(

---

### Post by haxer on 2006-09-24
Try this in terminal!! 

The other one wrote the wrong 

WINEPREFIX="$HOME/.steam4linux" wine "C:/Program Files/Steam/steamTmp.exe" SelfUpdate "C:/Program Files/Steam/Steam.exe" "14"

---

### Post by gogogo111 on 2006-09-24
I get this when I tpye that in:

---

### Post by haxer on 2006-09-24
Then write in terminal : 


Wineprefixcreate 


Then run this again 




WINEPREFIX="$HOME/.steam4linux" wine "C:/Program Files/Steam/steamTmp.exe" SelfUpdate "C:/Program Files/Steam/Steam.exe" "14"

---

### Post by gogogo111 on 2006-09-24
It still asks me to do it.

---

### Post by haxer on 2006-09-24
Can you understand something on this page then it will work absolutly fine i promise you if you can make it its really easy it will work 100%



[http://www.linuxin.dk/artikler/index.php?id=8385](http://www.linuxin.dk/artikler/index.php?id=8385)

---

### Post by gogogo111 on 2006-09-24
I can't read it, I don't speak that launguage. :(

---

### Post by haxer on 2006-09-24
wget [http://steam4linux.freepages.dk/downloads/1.0-beta/download.php](http://steam4linux.freepages.dk/downloads/1.0-beta/download.php)

Then write tar xvfz steam4linux.tar.gz

then type in 

cd steam4linux
./configure
 

Then run it and then when it freezes on 26% type in 

WINEPREFIX="$HOME/.steam4linux" wine "C:/Program Files/Steam/steamTmp.exe" SelfUpdate "C:/Program Files/Steam/Steam.exe" "14"

---

### Post by gogogo111 on 2006-09-24
> **haxer said:**
> wget [http://steam4linux.freepages.dk/downloads/1.0-beta/download.php](http://steam4linux.freepages.dk/downloads/1.0-beta/download.php)

Then write tar xvfz steam4linux.tar.gz

then type in 

cd steam4linux
./configure
 

Then run it and then when it freezes on 26% type in 

WINEPREFIX="$HOME/.steam4linux" wine "C:/Program Files/Steam/steamTmp.exe" SelfUpdate "C:/Program Files/Steam/Steam.exe" "14"




Did that...brought up a Wine emulater thing, where I installed steam. I got to the main steam part, it didnt have any text, even with the tomaha font. So I kept going, it installed some gecko engine thing, and froze. Now I cant get back to it.

---

### Post by haxer on 2006-09-24
huh hmm... then i dont know shit maybe your "graphic card" isnt with drivers or i just dont know worked perfectly fine and i have simmular components in my computer sorry mate


did you get an steam "ikon" on your desktop? try open that up

---

### Post by bugz0r on 2006-09-24
> **haxer said:**
> wget [http://steam4linux.freepages.dk/downloads/1.0-beta/download.php](http://steam4linux.freepages.dk/downloads/1.0-beta/download.php)
Then write tar xvfz steam4linux.tar.gz

then type in 

cd steam4linux
./configure
 

Then run it and then when it freezes on 26% type in 

WINEPREFIX="$HOME/.steam4linux" wine "C:/Program Files/Steam/steamTmp.exe" SelfUpdate "C:/Program Files/Steam/Steam.exe" "14"

I followed this but this shows up in the terminal

```
wine: cannot find 'C:/Program Files/Steam/steamTmp.exe'
```

Also there're two steam icons on my desktop. The first is the original and freezes at 26% and the other shows up with this message(attached).

---

### Post by bugz0r on 2006-09-24
NVM. I don't know what I did, i just clicked on something before it disappeared and now everything is working perfectly.

THANKS, anyways.

---

### Post by bugz0r on 2006-09-24
Okay, I'm gonna go ahead and retract my previous statement. Whenever I try to launch a game(CS or CS:CZ), X crashes and I arrive at the login screen. What is the problem? Please Help, I've been at this for several hours now.

---

### Post by haxer on 2006-11-04
Hmm.. not wine it :S try just to wget it then open it then try the wine prefix after 26% crash then it will work butiful :D

---

### Post by LoMoS_swe on 2006-11-27
Jag får inte igång steam överhuvudtaget

---

### Post by gelb on 2007-01-26
I have a solution to get around the 26% bug :)
I tried to follow this thread
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam)

The thread explains how to install wine and how to install steam, but the steam update stopped around 26%...

I tried the thread below, and it did manage to update steam. But I managed to destroy the /home/MYUSERNAME/.wine/drive_c/Program Files/Steam/ folder somehow. So i deleted /home/MYUSERNAME/.wine and tried to install steam again, but this time it did not work. Tried it again many times but it stopped around 26%

[http://wiki.archlinux.org/index.php/Steam](http://wiki.archlinux.org/index.php/Steam)

My solution:
I have cedega installed. I installed SteamInstall.exe with cedega in a folder i named Steam. Cedega managed to update steam (the update "walked" quickly towards 26%, the update window disapeared 4 seconds, popped up again and went towards 100%). My cedega can not run steam (don't know why). After cedega had updated steam i moved steam from cedega's drive to .wine (.wine is hidden but can be made visible with view>Show Hidden Files or ctrl + h) 

/home/MYUSERNAME/TransGaming_Drive/Program Files/Steam 
to 
/home/MYUSERNAME/.wine/drive_c/Program files/Steam

Then i went to .wine/drive_c/Program Files/Steam$ in a console/terminal and typed "wine steam.exe". After a moment steam started. 

During my download of counterstrike, the download stopped after some time. Steam also froze some times after the download had stopped. Then i closed the terminal I had typed "wine steam.exe" in (steam  exits/stop when the console is closed), opened another terminal and typed "wine steam.exe", some time later steam became visible(take some time). I watched the system monitor and it showed me that the download started quickly after I typed wine steam.exe. Why the download stoped, I do not really know. I looked like a timeout or something. May be because I used wireless.

---

### Post by Ferrat on 2007-01-26
Best soruce for solutions when having wine problems is 
appdb.winehq.com, just search for steam and you find all kinds of fixes =)

---

### Post by crapgar on 2007-12-30
This is what happens when I click the steam icon.

[IMG]http://img84.imageshack.us/img84/4369/screenshot1mr2.jpg[/IMG]

It stops there, then it goes to this.

[IMG]http://img255.imageshack.us/img255/6788/screenshot2tk7.jpg[/IMG]


Is this one problem, or two different ones going on at once?

---

### Post by DoktorSeven on 2007-12-30
**nice -n 19 wine Steam.exe**

---

### Post by crapgar on 2007-12-30
wine: could not load L"c:\\windows\\system32\\Steam.exe": Module not found

---

### Post by crapgar on 2007-12-30
I got steam to run by downloading the old version. It got stuck at 99% but then I clicked the icon on teh desktop and it opened. I restarted the computer also.

Right now my problem is when I click install on any of my games, steam just minimizes and goes away.

---

### Post by DoktorSeven on 2007-12-30
> **crapgar said:**
> wine: could not load L"c:\\windows\\system32\\Steam.exe": Module not found

Need to be wherever you installed Steam.  **cd .wine/drive_c/Program\ Files/Steam** for example (or wherever you installed), *then* do the **nice -n 19 wine Steam.exe** command.

---

### Post by crapgar on 2007-12-30
Thanks, I had no idea about the slashes for spacing.

steam started to load but then it had a fatal error. 

fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.



To reiterate: I can load steam but when i click "install game" it crashes.

---

