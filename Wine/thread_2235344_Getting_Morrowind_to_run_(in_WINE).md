---
title: "Getting Morrowind to run (in WINE)"
date: 2014-07-20
forum: Wine
---

### Post by mastablasta on 2014-07-20
So i had some itme on my hands and it happened as always - if you want to get something done on linux prepared to waste a couple of hours at least...

Anyway i read about some issues with windows 98 mode in wine. Eventhough the game has platinum rating. So i decided to first use the Playonlinux scripts. I mean they are there to make your life easy, right? Wrong.it started well. it downloaded an older version of wine ( i figure it handles MW better), added some other stuff and installed the game.

I have a "netbook" with no CD drive. so what i did is create isos from the CDs. but i didnt' know how to mount them so i just unpacked the first CD and it installed well. now come the add ons (tribunal and bloodmoon) the script install wants a CD. i tried to point it to the unpacked folder but it said "hey where is the CD", there is no CD. like i don't know that.

ok forget about Playonlinux. deleted all and used wine to install. it install fine can run the luancher but when i play the game i can see a small window to appear and then dissapers. strange. so i ran it directly. same thing. so i do some checking on the UESP and wineappdb. i set windows to 98 and run it form terminal this time i get: 
```
[COLOR=#000000][FONT=Arial]modify_ldt: Invalid argument[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]modify_ldt: Invalid argument[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]modify_ldt: Invalid argument[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]modify_ldt: Invalid argument[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]modify_ldt: Invalid argument[/FONT][/COLOR]
```

hmm doesn't seem to be working. i change it to windows XP sicne i am not sure why one would need windows 98 mode? i change it pback to XP and i get this:
```
[COLOR=#000000][FONT=Arial]X Error of failed request:  BadRequest (invalid request code or no such operation)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]  Major opcode of failed request:  157 (ATIFGLEXTENSION)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  Minor opcode of failed request:  66 ()[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]  Serial number of failed request:  229[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  Current serial number in output stream:  229[/FONT][/COLOR]
```

strange cause last stable wine still has platinum rating with this game, it's the dev verison that has the issues.

bottom line i can't get it to start. any tips & tricks? or maybe how i would install tribunal and bloodmoon with playonlinux? do i need to insatll directx9?


i am also a bit upset at play onlinux and it's insistance that certain program must be on CD/DVD... although the vanilla morrowind did get an option to point it to folder that was not the case with addons. i mean you have games that used to be on CD and are now sold as downloads. that kind of scripts are riduculous. why not just let the user decide if it's from folder or a real cd drive.

---

### Post by mastablasta on 2014-07-25
I've found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1328965](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1328965)

I reinstalled the wineprefix to make sure it's 32bit. setup > ```
sudo sysctl abi.ldt16=1
```  to activate 16 bit support
reinstalled the game and this time set the folder where I extracted it's files as CD ROM.

I then installed directx using winetricks, as well as corefonts and Tahoma
as instructed here in the additional comments:
> [B]Additional Comments
[/B]Frame rates were exceptional even with view distance way up
Morrowind FPS Optimizer did a great job with widescreen resolutions and allowing farther view distance.
Libraries:  d3dx9, corefonts, tahmoa
No extra configuration necessary

kernel is 3.13.0-32.57  AMD64.

I got the same issue

```
[FONT=Arial]modify_ldt: Invalid argument[/FONT]
```

I switched to windows98 mode for the application and got :

```
[FONT=Arial]X Error of failed request:  BadRequest (invalid request code or no such operation)[/FONT]

[COLOR=#000000][FONT=Arial]  Major opcode of failed request:  157 (ATIFGLEXTENSION)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  Minor opcode of failed request:  66 ()[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]  Serial number of failed request:  229[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  Current serial number in output stream:  229[/FONT][/COLOR]
```

I've tried adding .dll file that supposedly made the game work before but all I got was that it could not load some .dll libraries

what am I missing here?

How can this game have platinum rating? :o:o:o:o Platinum should just install it and work... Install went fine but I can't get the damned thing to run.

oh APU is E-450 and using proprietary drivers.

---

### Post by mastablasta on 2014-07-25
well it turns out the error was there due to bad driver install. it seems something was wrogn with drivers and reinstalling them worked. morrowind FPS optimizer was needed for wide screen

the game loaded a bit slow but then worked like a charm on this little thingy.

i wouldn't give it platinum rating sice changing keys in option causes it to crash. the workarround is manually editing the morrowind.ini file

i am so glad i got this one working...

---

