---
title: "Cant Install Flash Adobe on 64"
date: 2009-06-19
forum: x86 64-bit Users
---

### Post by Deicider on 2009-06-19
I'v seen many guides to install Adobe Flash, and tried the "easy way to install" commands from various sites, nothing, it does not work.
Tried to download and install in traditionally but its says "i365, blah blah u cant do this"
Ye its cause i have the damn 64 version,  i dont want the 32 ,too troublesome.
So..what do i do to get this thing working? 
I want to see vidz >.<

---

### Post by sanemanmad on 2009-06-19
Explain some more please. Where are you downloading flash from, and how are you attempting to install ie command-line or gtk?

---

### Post by Therion on 2009-06-19
Download this script:

[http://www.myscienceisbetter.info/flash-player/native-64bit-flash-installer.sh](http://www.myscienceisbetter.info/flash-player/native-64bit-flash-installer.sh)

Right click on the file, open the Properties and tic the box allowing it to run as an application.

Run the script (double-click on it).



Script contents here:  [http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html)

---

### Post by Idefix82 on 2009-06-19
It's very simple and you don't need any videos. First, uninstall any version of flash that you have installed, then go to this site:


[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

Download the flash plugin (at the bottom of the page), extract it to the desktop. Now open the terminal and type in just two lines:
```

mkdir .mozilla/plugins
cp Desktop/libflashplayer.so .mozilla/plugins
```

Restart firefox and you have flash 64 bit working without any 32 bit libraries.

---

### Post by Deicider on 2009-06-19
well,i  have ubuntu the latest (64bit) and the 99% of progs i dl from the web cant get installed cause of "i367 something" and i tried to install it normaly by DLing from official site etc..the same -/ I found some commands and did everything by itself, unistalled the previous flash progs, installed the new and everything it wanted to finish it , i did that but nothing  changed... i saw on plugins and nothing that had to do with flash was there not even in about:plugins. H31P Moi ;(

---

### Post by Deicider on 2009-06-19
hmm tried both..nothing :S :S :S :S

---

### Post by Idefix82 on 2009-06-19
Can you type
```
ls .mozilla/plugins
```
into the terminal and give me the output?

---

### Post by Deicider on 2009-06-19
with green letters says :[FONT=monospace] libflashplayer.so
[/FONT]

---

### Post by Idefix82 on 2009-06-19
And you have restarted firefox? Meaning closed **all** instances of firefox and then opened it again? This is strange.

---

### Post by Deicider on 2009-06-19
ye done that many times...is there anything else that am missing? must do anything else in firefox options? or smthing..  frustrating ~.~

---

### Post by oldos2er on 2009-06-19
Have you tried this: [http://ubuntuforums.org/showpost.php?p=7412598&postcount=699](http://ubuntuforums.org/showpost.php?p=7412598&postcount=699)

---

### Post by Deicider on 2009-06-19
i c+p in a doc, saved it as a GetFlash64.sh made it executable , run it in home directory enter the sudo code, type "y" and..dunno  i rred ffox but nthg

---

### Post by C0NSTANTIN on 2009-06-19
YOU ALREADY HAVE THAT PLUG-IN!!!
[SIZE=5]
[/SIZE][SIZE=5][COLOR=Red]**Applications > Add/Remove...**[/COLOR][/SIZE]



[IMG]http://img354.imageshack.us/img354/6098/ewrikaaa.png[/IMG]

---

### Post by sanemanmad on 2009-06-19
Hi, 

please try this. Download this flashplayer for Adobe 
[Adobe Flash]("http://labs.adobe.com/downloads/flashplayer10.html")

also rm /usr/lib/firefox/plugins/libflashplayer.so

now  tar xvf whatever.tar

then be sure to cp the libflashplayer.so back to /usr/lib/firefox/plugins

---

### Post by Deicider on 2009-06-20
> YOU ALREADY HAVE THAT PLUG-IN!![SIZE=5]
[/SIZE]
The caps attack!! run for ur livesss :0
Well, i had it there...but it doesnt change anything , i removed it and reinstalled it but vids on YT wont play as always..

@sanemanmad
Um, i tried, but i made it wrong am sure, dunno 
i tried to rm the libflashplayer.so but it wasnt there... Dfl;kasjdf;lkasdfl;e

---

### Post by Idefix82 on 2009-06-20
> **Deicider said:**
> 
@sanemanmad
Um, i tried, but i made it wrong am sure, dunno 
i tried to rm the libflashplayer.so but it wasnt there... Dfl;kasjdf;lkasdfl;e

No, that's fine. It wasn't supposed to be. But I doubt that sanemanmad's method will work, since you have essentially already done that, except that you put the plugin into your user's directory and he is telling you to put it into the system wide directory. Shouldn't make a difference. I am really puzzled by your problem.

---

### Post by Deicider on 2009-06-20
Puzzles are even better when they r solved ~.~ HelploX
Ye, its Flash Gordon's revenge, he wont let me see Vidz because his movies sucked and he hates me ;(

---

### Post by Deicider on 2009-06-20
Any real experts here that can find the way out of  this maze?

---

### Post by apel_2804 on 2009-06-20
Please deinstall or delete all other flash plugins and then try this:

[http://www.tbaumi.de/blog/?p=340](http://www.tbaumi.de/blog/?p=340)

Flash support in Debian Lenny x64, it will work on Ubuntu too.

---

### Post by Deicider on 2009-06-20
after all this am comfused, where exactly are the ones that i must delete? or i should delete firefox and its plugins and from add/removes the flash players...where else?

---

### Post by apel_2804 on 2009-06-20
In Firefox you can disable the flash plugins (Extras > Add-ons) and then install the plugin as described in the howto. That should be all.

---

### Post by Deicider on 2009-06-20
i dont have anything in addons>>plugins that has to do anything with flash, even though couple of times today there was the "missing plugins install" on top of window which i installed the flash player but it never showed up anywhere nor it played any vids...did that 2-3 times...

---

### Post by apel_2804 on 2009-06-20
Fine, then follow the instructions.

---

### Post by Deicider on 2009-06-20
where r they ? xD

---

### Post by apel_2804 on 2009-06-20
> **Deicider said:**
> where r they ? xD

[http://www.tbaumi.de/blog/?p=340](http://www.tbaumi.de/blog/?p=340)

---

### Post by C0NSTANTIN on 2009-06-20
Is terminal really that necessary?!?!?!?! I messed up my computer because i fallowed some instructions that i didn even understood and didn't even worked ...

**[COLOR=Red]3 clicks installment:[/COLOR]**
[http://ubuntuforums.org/showpost.php?p=7485534&postcount=13](http://ubuntuforums.org/showpost.php?p=7485534&postcount=13)

---

### Post by apel_2804 on 2009-06-20
> **C0NSTANTIN said:**
> Is terminal really that necessary?!?!?!?! I messed up my computer because i fallowed some instructions that i didn even understood and didn't even worked ...

**[COLOR=Red]3 clicks installment:[/COLOR]**
[http://ubuntuforums.org/showpost.php?p=7485534&postcount=13](http://ubuntuforums.org/showpost.php?p=7485534&postcount=13)

Do you have Ubuntu x64 / AMD64 installed?

---

### Post by michaelzap on 2009-06-20
> **Idefix82 said:**
> It's very simple and you don't need any videos. First, uninstall any version of flash that you have installed, then go to this site:


[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

Download the flash plugin (at the bottom of the page), extract it to the desktop. Now open the terminal and type in just two lines:
```

mkdir .mozilla/plugins
cp Desktop/libflashplayer.so .mozilla/plugins
```

Restart firefox and you have flash 64 bit working without any 32 bit libraries.
I just folowed these steps last night on a new laptop and it worked perfectly (thanks!).

---

### Post by Idefix82 on 2009-06-20
> **michaelzap said:**
> I just folowed these steps last night on a new laptop and it worked perfectly (thanks!).

You are welcome! Just a word of warning: this is an alpha release of the 64 bit flash player. So far, all the comments I have seen confirm that it works much better than the stable 32 bit release and this is also my experience but I thought I should warn you.

---

### Post by C0NSTANTIN on 2009-06-20
> **apel_2804 said:**
> Do you have Ubuntu x64 / AMD64 installed?


i've made that printscreen especially to show that i have the x64 version of xubuntu ... ubuntu/kubuntu just have different desktop sets ... kernel is the same...

---

### Post by Deicider on 2009-06-20
Screw it am gonna format it or switch back to windows..the second sounds easier

---

### Post by Deicider on 2009-06-20
Should i get the 32bit ubuntu, cause if i get again 64 it'll cause me trouble...
edit: nvm am dling the i386

---

### Post by Idefix82 on 2009-06-20
> **Deicider said:**
> Should i get the 32bit ubuntu, cause if i get again 64 it'll cause me trouble...
edit: nvm am dling the i386

Personally, I think that something went badly wrong with your install and you should be fine installing the 64 bit version again and doing what I recommended in my first post. But it's ultimately up to you.

I doubt that it's easier to go back to Windows than to reinstall. The time you spend updating your antiviruses, scanning your discs, removing malware and waiting for all the protection tools to load on startup will outweigh many Ubuntu installs. Not to mention the initial trouble of chasing the web for all the drivers you need :)

---

### Post by C0NSTANTIN on 2009-06-20
> **Deicider said:**
> Screw it am gonna format it or switch back to windows..the second sounds easier

i got the Desktop Cube and firefox running with just a bit under 250 mb or memory. it's worth it ... i promise you...

[SIZE=7][COLOR=Red]
SOLUTION!!!
[/COLOR][/SIZE]
look at my screenshoot again ... it's eazy installing flash player ... it's a 3 click job!!!
Don't listen to this "Linuxologists" talking about terminal codes ... today linux is made for us noobies that came fresh out of windows ;)

[http://img354.imageshack.us/img354/6098/ewrikaaa.png](http://img354.imageshack.us/img354/6098/ewrikaaa.png)

go to Add/Remove from your menu, in the "add remove applications" select "all available applications" type in "flash" and click for the 2 star under-rated "Macromedia Flash Plugin"

restart your firefox ... it's to eazy even for a noob like me....

no more google > <name>+torrent > download tracker > open it in uTorrent > open location folder > unrar > mount them on nero image drive > auto-run > install > finish ....
you just have them all ... search for application and press install :D

---

### Post by Deicider on 2009-06-20
@constantin 
Dude, i tried that many times with the add/remove thingie , doesnt work for me.thnx anywayz

Ill reinstall ubuntu i guess, but not sure yet which one, the 9.04 dekstop i386 caught my eye in torrent search...i dont go for 64 cause almost every application that i want to install from the web and not from add/remove, doesnt work...and whats with the games >.< wc3 and L4D are reaally sloww...wine is not good enough i suppose

---

### Post by C0NSTANTIN on 2009-06-21
> **Deicider said:**
> @constantin 
Dude, i tried that many times with the add/remove thingie , doesnt work for me.thnx anywayz

Ill reinstall ubuntu i guess, but not sure yet which one, the 9.04 dekstop i386 caught my eye in torrent search...i dont go for 64 cause almost every application that i want to install from the web and not from add/remove, doesnt work...and whats with the games >.< wc3 and L4D are reaally sloww...wine is not good enough i suppose


:( add/remove was suppose to work ... it made things so muxh easyer compared to windows xp ...

and btw ... wow ruined my life ... i now suspect thtat all games are made to be addictive and keep the youth of our nations out of the street protests and stuff :p
just forget about games, Office and CAD work great :X

---

