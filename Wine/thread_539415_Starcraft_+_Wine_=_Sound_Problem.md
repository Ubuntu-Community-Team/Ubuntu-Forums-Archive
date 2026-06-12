---
title: "Starcraft + Wine = Sound Problem"
date: 2007-08-31
forum: Wine
---

### Post by th3rmos on 2007-08-31
I have done some searching, and I have not seen any problems similar to this. If there is something that I missed, I apologize in advance. The problem I am having is this:

I loaded wine, and was able to install Starcraft without a problem! My original thought was "Wow, this is way easier than I thought!" I open the program, StarCraft.exe inside of wine and the big blue Blizzard logo appears, I hear the sounds of electrcity flowing around it followed by the panting of a Marine. I sit and watch the entire Into Cinematic with full rich sound, then it dumps the StarCraft loading screen and is silent from there. There is no sound in the menu when highlighting or clicking on buttons. There are no sounds, or music in a Custom Game, nor are the voice overs  present during the Campaign Briefings. I have tried playing around with ALSA, and OSS. I even tried installing JACK and using it. I tried disabling the sound system inside of KDE (I am running Kubuntu Fiesty), and also running the program inside of a window. Ive seen some option for using parameters to load the game like "-gl" and also "wine nice-20." "Wine nice -20" returns an error stating that "c:\\windows\\system32\\nice.exe" does not exist. When the game is loaded, if I go into the the menu, then Options~>Sound All of the options are there, unlike when there is no sound card and the only option is "Display Subtitles."

Does anyone have any ideas? I am running it from an older HP nc6000 Laptop with an Intel Chipset. I have played a few matches with no performace issues on the video side, it seems to be isolated to the sound. Any help, or ideas are appreciated!

--
th3rmos

---

### Post by cogadh on 2007-08-31
Well, first of all, you used the nice command in the wrong place. It should be used like this:
```
nice -15 wine blah.exe
```
However, since running nice with a negative setting only works if you are root or use sudo and using root access to run Wine is very bad, you should open a seperate terminal after launching the game and run this:
```
sudo renice -n -15 game.exe
```
That will increase the game's scheduling priority and may improve the sound issue. DO NOT use -20 to renice the game, it is extreme overkill and could cause problems. You probably don't really need to do more than -10.

As for your sound settings, I recommend you use ALSA, set the hardware acceleration to full, 48000 sample rate, 16 bits per sample and turn on driver emulation. Post back with any results.

---

### Post by th3rmos on 2007-08-31
Thanks for the post, but it doesn't seem to be doing anything for me. This is what I get as output from the command that you suggested

```
laptop@kubuntu-laptop:~$ sudo renice -n -15 wine /home/laptop/.wine/drive_c/Program\ Files/Starcraft/StarCraft.exe
Password:
renice: -15: bad value
0: old priority 0, new priority 0
0: old priority 0, new priority 0
laptop@kubuntu-laptop:~$

```

And I tried this also:

```
laptop@kubuntu-laptop:~$ sudo renice -n -10 wine /home/laptop/.wine/drive_c/Program\ Files/Starcraft/StarCraft.exe
renice: -10: bad value
0: old priority 0, new priority 0
0: old priority 0, new priority 0
laptop@kubuntu-laptop:~$

```

Do you have any other ideas, or do you know why that didnt work?

Additionally, I get the following in the Konsole window when I click on the "Audio" tab inside of wine:

```
/bin/sh: /usr/bin/esd: not found
```

And here is a shot of my "Audio" Tab inside of winecfg

---

### Post by cogadh on 2007-08-31
Okay, I have no idea on that error message you get when clicking on the sound tab, but you need to changes that Hardware Acceleration setting from "Emulation" to "Full". 

I think I also need to explain the renice thing a little better. 

Launch your game:
```
wine /home/laptop/.wine/drive_c/Program\ Files/Starcraft/StarCraft.exe
```
After the game has launched, open a new terminal window and run this:
```
sudo renice -n -10 StarCraft.exe
```
It may be helpful to enable the "Emulate virtual desktop" setting in winecfg, at least until this sound issue is sorted. It will help with switching between the game and terminal windows.

---

### Post by th3rmos on 2007-08-31
I changed the sound option to full, and then launched the game. I already had it set up to launch in a window, instead of full screen so I could see what was going on in the back ground. Once the game was launched I opened up a new tab in Konsole, and put in the command. This is what I got, still.

```
laptop@kubuntu-laptop:~$ cd /home/laptop/.wine/drive_c/Program\ Files/Starcraft
laptop@kubuntu-laptop:~/.wine/drive_c/Program Files/Starcraft$ sudo renice -n -10 StarCraft.exe
renice: -10: bad value
0: old priority 0, new priority 0
laptop@kubuntu-laptop:~/.wine/drive_c/Program Files/Starcraft$

```

The game shows that its a running process

```
laptop@kubuntu-laptop:~/.wine/drive_c/Program Files/Starcraft$ ps -edf | grep StarCraft.exe
laptop    5914  5506 69 17:04 pts/1    00:01:08 /home/laptop/.wine/drive_c/Program Files/Starcraft/StarCraft.exe                                                
laptop    5951  5923  0 17:05 pts/2    00:00:00 grep StarCraft.exe
laptop@kubuntu-laptop:~/.wine/drive_c/Program Files/Starcraft$

```

---

### Post by cogadh on 2007-08-31
There is definitely somthin' screwy going on here. That "-10" is defintely not a bad value for renice, I use it all the time. Try running it like this instead:
```
sudo renice -10 StarCraft.exe
```
That should tell it to set a specific "niceness" rather than increment the existing "niceness" by -10 (which using the "-n" does).

---

### Post by th3rmos on 2007-08-31
I was about to report to you that it didnt work. I had no sound at all with -10 as the option. I had taken screen shots and everything to show you that the program was seeing the sound card but nothing was working. I decided to try something else that I had read in another post last night around 3am. I had already tried it, but thought that maybe in conjunction with this command it would work. I went into the "Program" tab of winecfg and changed it from Windows XP to Windows 98. I reloaded the game, inserted the nice command and.....\\:D/TOUCHDOWN!\\:D/

I certainly appreciate you taking the time to help me out with this issue. So far my switch to Linux has been pretty smooth, and from lurching around the forums I have found answers to most everything, but this was killing me!

---

### Post by cogadh on 2007-08-31
Cool, glad it finally worked! :)

---

