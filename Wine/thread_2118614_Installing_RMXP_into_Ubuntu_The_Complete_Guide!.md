---
title: "Installing RMXP into Ubuntu: The Complete Guide!"
date: 2013-02-21
forum: Wine
---

### Post by ntzrmtthihu777 on 2013-02-21
I had to do some custom setup to get MS Office to work under wine, these custom settings may or may not be needed for RMXP to work under wine as well, if you have a problem following these steps please post here and I will update the steps. Also I am using a heavily customized Precise x64 install and I am not sure what, if anything of that, affects the success/failure of this venture, so again if something does not work let me know and I will add the correct steps.

Assumes:
1. Familiarity with the terminal
2. Patience

Initial Setup:
Open a terminal and run:
```
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_precise.list -O /etc/apt/sources.list.d/playonlinux.list
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install playonlinux wine
```

This will add the wine & PlayOnLinux (hereafter POL) ppa's to your system so you can get the bleeding edge software you need.

Open POL (how you do that will depend on your desktop environment; I use gnome-fallback, so its under "Games" in the main gnome menu; for Unity you can search the dash, and if all else fails alt+f2 will open your run prompt, type in playonlinux and press enter)

In the main POL window, choose "Install"; in the next dialog choose "Install a non-listed Program"; click next.
Choose the option to install a program in a new virtual drive (hereafter VD). Give this VD a name in the next dialog; this tutorial assumes an installation of RPG Maker XP, change the instructions as needed for your choice.

The next step gives you 3 check boxes, check the bottom one "Install some libraries." Next choose the 32-bit option. It will take some time as a new VD is created, just hang on a bit.

Next, we select Windows libraries to install, this is a long list and may take a while to finish, just be patient. Libraries to check:
```
POL_Call POL_Install_d3dx9
POL_Call POL_Install_devenum
POL_Call POL_Install_dinput
POL_Call POL_Install_dinput8
POL_Call POL_Install_directmusic
POL_Call POL_Install_directplay
POL_Call POL_Install_directx9
POL_Call POL_Install_dotnet20
POL_Call POL_Install_dsound
POL_Call POL_Install_dxdiag
POL_Call POL_Install_dxfullsetup
POL_Call POL_Install_gdiplus
POL_Call POL_Install_quartz
```

Once this hellish wait is over, it will ask you to select your install file. At this point you should browse to the RMXP-RTP installer, and chose it. Just choose the defaults, and once it finishes it will ask if you want to make a shortcut; do not at this moment.

You will be returned to the starting POL window, click the gear icon for configure. It will list your virtual RMXP VD, click on this. Under the general tab click the plus sign next to wine version and install x86 version 1.5.24; this will also take a bit of time to complete.

Next, under the wine tab, click "Configure Wine", and in the resulting dialog chose the libraries tab. The top 2 should be d3d8 & d3d9, both set to (builtin), choose edit on both and set them to (native, builtin). Apply and ok, then exit.

Back at the main POL window choose again the install and install non-listed program options, this time chosing to "edit or update an existing application. You will have to check the "show VDs" button as no real program is yet installed in the VD as of yet, just runtime packages. Choose RMXP, and in the next dialogue leave all options blank, and set again a 32 bit install. In the next window you have 3 options, Overwrite, Erase, or Abort, choose overwrite (I had no problems with this option). This time browse to the actual RMXP installer, and go through the install process. At the end this time choose to make a shortcut for RPGXP.exe and name it RMXP, it will create a launcher file on your desktop, you can delete this if you like, or keep it, either way. I am assuming deletion, as I never keep desktop shortcuts.

Now, for the moment of truth! To run your installation click on the appropriate icon to highlight it and click the debug link to the right of the POL window.

At this point it may hang something terrible, and the window may keep whatever image is over it (you will see what I mean), just wait it out as it will do this every time you run it untill I or another figure a way to speed up its loading. If all goes well you should get an activate dialog, yay! Do your legitimacy magic, and you it should register just fine.After registration it may hang some more, again you just have to be patient :P

At this point you should be greeted with the familiar window we all love so much! If its no trouble, after installation, first run, and registration could you please send me a copy of the playonlinux.log in the appropriate VD so I can improve on the script for everyone?

You can even create a .desktop launcher file; I'll add it here when I finish making mine, but it seems RMXP works under wine with all the bells and whistles, excluding playing .mid (midi) files and .mp3. I have taken the liberty of converting the RTP music for both RPG XP and VX from .mid to .ogg, you can download either by clicking the icons below. There is not one for VXAce as their music is already all .ogg.
[[img]http://imageshack.us/a/img600/8148/rpgxpaudio.png[/img]](https://www.dropbox.com/s/citwp55iczz05bb/RPGXP-Audio.zip?dl=1)[[img]http://imageshack.us/a/img14/193/rpgvxaudio.png[/img]](https://www.dropbox.com/s/45x4zqz98bcqk0k/RPGVX-Audio.zip?dl=1)
Just unzip the contents into the proper directory and delete the .mid files.

---

### Post by Lightning Dragon on 2013-02-21
There is a tutorial already made on how to install with wine on the rmforums. Its actually allowed me to finally use my copy of XP and VX. :D

[http://forums.rpgmakerweb.com/index.php?/topic/3069-install-rpgvxace-in-ubuntu/](http://forums.rpgmakerweb.com/index.php?/topic/3069-install-rpgvxace-in-ubuntu/)

Could you see if your method plays sound in game? Background music files, I mean...?

---

### Post by ntzrmtthihu777 on 2013-02-22
> **Lightning Dragon said:**
> There is a tutorial already made on how to install with wine on the rmforums. Its actually allowed me to finally use my copy of XP and VX. :D

[http://forums.rpgmakerweb.com/index.php?/topic/3069-install-rpgvxace-in-ubuntu/](http://forums.rpgmakerweb.com/index.php?/topic/3069-install-rpgvxace-in-ubuntu/)

Could you see if your method plays sound in game? Background music files, I mean...?
Ack! It never fails, after I figure out how to do something the hard way all the tutorials come out of the woodwork :/

I have been looking into that, I had not encountered an issue with bgm because I had not yet added it to my project, lol. But, from what I see its a lack of midi support that makes it not work; BGS and SE both work, and are .ogg, but neither of the other 2 work because they are .mid, so if we can get .mid working under wine then it should be fine. Can't seem to figure it out, lol!

Confirmed, using .ogg files for BGM does in fact work; it is the lack of midi/mp3 playback in wine in general that caused failure, not RMXP.

---

### Post by Lightning Dragon on 2013-02-22
> **ntzrmtthihu777 said:**
> Ack! It never fails, after I figure out how to do something the hard way all the tutorials come out of the woodwork :/

I have been looking into that, I had not encountered an issue with bgm because I had not yet added it to my project, lol. But, from what I see its a lack of midi support that makes it not work; BGS and SE both work, and are .ogg, but neither of the other 2 work because they are .mid, so if we can get .mid working under wine then it should be fine. Can't seem to figure it out, lol!

Confirmed, using .ogg files for BGM does in fact work; it is the lack of midi/mp3 playback in wine in general that caused failure, not RMXP.

Yes, that is true, but what can be used in WINE to make it playback? :-k TiMidity++ doesn't seem to get the .midi files to work even though it is supposed to, in theory, work. I tried a whole bunch of other similar softwares, but the same results each time.

Music is literally the last thing to "fix" and then the RM game series works flawlessly in Linux. 

Oh, did the game crash when you tried to play the music, or did it just simply not play?

---

### Post by ntzrmtthihu777 on 2013-02-22
> **Lightning Dragon said:**
> Yes, that is true, but what can be used in WINE to make it playback? :-k TiMidity++ doesn't seem to get the .midi files to work even though it is supposed to, in theory, work. I tried a whole bunch of other similar softwares, but the same results each time.

Music is literally the last thing to "fix" and then the RM game series works flawlessly in Linux. 

Oh, did the game crash when you tried to play the music, or did it just simply not play?
Did not crash, just not play. Well you can always just use .ogg music to do the trick, right? Yeah, I tried timidity also, no go.

---

### Post by Lightning Dragon on 2013-02-22
> **ntzrmtthihu777 said:**
> Did not crash, just not play. Well you can always just use .ogg music to do the trick, right? Yeah, I tried timidity also, no go.
Alright, thanks for the answer. :)

Yes, that's true. I followed the guide and converted the music to .ogg, but that will only work for the 'creator' of the game. Unless if you compress it and then give it to another and it stays .ogg files. Hmm...

---

### Post by ntzrmtthihu777 on 2013-03-05
I have slapped together a PlayOnLinux install script, and need testers. Anyone interested can either post here or pm me, system specs would be appreciated. Also the playonlinux.log file in the root of the wineprefix would be nice after installation and first run, will assist in debugging the script.

---

