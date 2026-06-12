---
title: "Total Annihilation"
date: 2007-02-14
forum: Wine
---

### Post by jtreach on 2007-02-14
I have been trying to install total annihilation on ubuntu under wine.

I managed to install it but when i try to run the TOTALA.EXE file the screen flickers and then says 'sound system initialization failed' has anybody else tried to do this and how do you get to the gui menu for wine?

WineHQ says total annihilation should work it is rated as Gold.

---

### Post by Gibbs on 2007-02-14
Try
```
wine winecfg
```

Also go to the Audio tab and change "Hardware Acceleration" to "Emulation". Worth a try.

---

### Post by paulyche on 2007-02-14
You might want to consider TA Spring.
A large project to 'enhance' TA, including a linux port I think.

[http://doc.gwos.org/index.php/TA_Spring](http://doc.gwos.org/index.php/TA_Spring)

---

### Post by bapoumba on 2007-02-14
Moved to Gaming & Leisure.

---

### Post by jtreach on 2007-02-15
Thanks for the move I wasn't sure which section to put it in and didn't see gaming and leisure.

I tried changing the setting for audio, it didn't seem to work but it just didn't open at all this time + it crashed ubuntu.

Anyway I might try TA spring, the old one's just got the rustic feel. :)

Thanks for all your  help.

---

### Post by ELD on 2007-02-15
TA Spring works fine under linux but there are no missions and linux online play is far from finished, two different lobbys for linux are currently under works though :)

Also it is not a project to "enchance" Total Annihilation, it is a brand new open-source 3D engine that can run files from total annihilation.

---

### Post by nickajeglin on 2007-08-14
Go to winecfg and change the sound driver to alsa. works fine for me.

---

### Post by omegamike3 on 2007-08-14
> **paulyche said:**
> You might want to consider TA Spring.
A large project to 'enhance' TA, including a linux port I think.

[http://doc.gwos.org/index.php/TA_Spring](http://doc.gwos.org/index.php/TA_Spring)

I wasted much of my youth on Total Annihilation and Diablo, first I'd heard of TA spring. Thank you for leading me down the path to waste much of my mid 20's :P

---

### Post by ELD on 2007-08-15
> **omegamike3 said:**
> I wasted much of my youth on Total Annihilation and Diablo, first I'd heard of TA spring. Thank you for leading me down the path to waste much of my mid 20's :P

Haha i would waste my time on it too if my laptop could handle it :(

---

### Post by Hobo Joe on 2007-08-15
> **omegamike3 said:**
> I wasted much of my youth on Total Annihilation and Diablo, first I'd heard of TA spring. Thank you for leading me down the path to waste much of my mid 20's :P

And you WILL waste your life on it :D

It rocks.

---

### Post by Cochise on 2007-08-15
> **omegamike3 said:**
> I wasted much of my youth on Total Annihilation and Diablo, first I'd heard of TA spring. Thank you for leading me down the path to waste much of my mid 20's :P

me too and looks like im going to waste my 20's too now.

---

### Post by charlieg on 2007-08-16
There's also [TA3D]("http://ta3d.sourceforge.net/") which is pretty advanced.

TA3D obviously shares a lot in common with TA:Spring, however there are some important differences. Firstly, TA3D is Linux centric - whilst there is a Windows version, it is developed and released primarily for Linux. Also TA:Spring includes modifications to the gameplay and does not make use of some TA files like maps, facts which don't sit well with the TA3D author, so TA3D definitely has a niche.

---

### Post by Jolly-Swagman on 2007-08-17
Hey did not Know that there was a 3D version of TA old time fan of the old TA will definitely have to give it a go, used to play for hours 

Thanks for the info 

Jolly Swagman

---

### Post by Amazona aestiva on 2007-08-17
Total Annihilation ran on my computer. I don't know why.:confused:

---

### Post by SelrahCharleS on 2007-10-31
I had that problem too. I can't get TA to work at all right now but I was looking through the readme and I think I may have found the solution for your problem. All you should need to do is copy the Totala.ini file from the cd into the same directory that TA is installed and change some of the settings. I haven't been able to test it, but it seems like that would be the fix.

From the readme for TA:

**Experiencing sound-related problems or unexplained crashes. 

We have found that most crashes are a result of old or non-DirectX compatible sound card drivers.  There are two options to help solve these problems.  On Disc 1 is a text file called Totala.ini text file which will allow you to use these options and get detailed instructions on how to make these changes to your system.

To use Totala.ini, copy Totala.ini from Disc 1 to the folder containing Totala.exe and set the option you need to equal one.  You can also pass a switch on the command line to activate these options.



UseWindowsSound (or -w on the command line)   Use the standard Windows multimedia interface for playing sounds instead of DirectSound.  Set this to 1 to use Windows sound, and 0 to use DirectSound. 

Note:  Setting this value to 1 will allow you to play the game if DirectSound does not work properly on your system.  However, the audio quality will be greatly decreased, especially during heavy battles.  Also, you will not get any audio narration with your mission briefings or any sound in the movies.



NoDirectSound (or -s on the command line)	Disable the use of DirectSound.  Set this to 1 to disable sound in the game.  Set it to 0 to use sound normally.  Disable the sound if you do not have a sound card or the game crashes while trying to play sounds.







> **jtreach said:**
> I have been trying to install total annihilation on ubuntu under wine.

I managed to install it but when i try to run the TOTALA.EXE file the screen flickers and then says 'sound system initialization failed' has anybody else tried to do this and how do you get to the gui menu for wine?

WineHQ says total annihilation should work it is rated as Gold.

---

### Post by jbaerbock on 2008-03-17
Thanks got it running, sadly sound does not work at all now though after disabling directx sound.

---

### Post by jbaerbock on 2008-03-17
Ok so Music works but unit sounds and button sounds do not work. Any ideas?

---

### Post by ScarySquirrel on 2009-02-15
This new engine will run on the most crazily crappy computers.  It surprised me when it even ran on my seven year old Dell laptop that had fallen off the back of my car.
Spring, however, does not run concurrently with Compiz without some painful configuration, so you have to switch to Metacity to use Spring an Ubuntu.

---

### Post by enque on 2009-09-26
I have Total Annihilation running on Ubuntu Jaunty 9.04, with Wine. No special setup required.
Sound effects works perfectly. Everything works in skirmish. I can play really huge skirmish games now on my modern computer :D Seven islands with 7 Ai's on "insane" difficulty, each one having 500 units, running smoothly. I have successfully installed the Twilight mod.

These things does not work for me:

- So far multiplayer refuses to launch. I can not join games. I can not even bring up the "host game" screen, for some unknown reason.
- Music from the CD does not play ingame, but is playable by other means so it's no problem.
- The TA demo recorder does not work. This makes it impossible to que up hundreds of units with a single click, as well as building DragonTeeth rows.

If someone solves the multiplayer issue then please write the solution here!
If only EA could release the antique source-code.... We fans would be very happy.

---

### Post by Qualia on 2010-02-28
I was having trouble installing Total Annihilation today as well. The installation had no
trouble installing under wine (I am using 9.10 karmic by the way) except for having to manually copy the .hpi files into the folder where I had it installed. 
 At first, I didn't have any sound whatsoever, but when I started up the setuip for Total annihilation again, this time I choose the install DirectX option. I choose "Reinstall directx", and that was it! :D
 The sound runs smoothly(narration and all), but the music doesn't play. however, I didn't play either when I had it installed under Windows, so I just think its because its an old CD (6-years old) But I didn't have to edit any .ini files though...I just had to do that "install directx" option on the TA install and the sound works just fine now!

 Hope this was somewhat helpful!

---

