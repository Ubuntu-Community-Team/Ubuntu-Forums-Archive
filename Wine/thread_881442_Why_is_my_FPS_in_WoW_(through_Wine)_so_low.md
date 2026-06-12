---
title: "Why is my FPS in WoW (through Wine) so low?"
date: 2008-08-06
forum: Wine
---

### Post by LifeIsFlimsy on 2008-08-06
Before, when I had windows XP, my WoW framerate would be about 20-30 in populated areas. Even 15 at times, which is fine and playable.

Now, after working tirelessly for the past few days to even install WoW, I finally got it working, but the FPS is around 3-5 fps. That's just ridiculous and there is no way to play with that. I have configured the file in the wtf directory to include the commonly recommended lines (OpenGL, etc), and also turned all of the graphics settings down in WoW. Not only that, but I use EnvyNG and have my video card upgraded.

I really would love some help, as the only thing I really do on the computer anymore is play World of Warcraft. If anyone needs info about my computer specs or files etc, feel free to ask me how to tell you and I shall. Thanks for taking the time to read this.

---

### Post by geekygirl on 2008-08-06
Have you used the registry hack?

Taken from here (this is what I used to install WoW and I get over 100fps even in Outlands and 40-50fps in Shatt, and I have all my graphics settings maxed out, actually runs better under Wine than it did with XP!)

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

```
Open a terminal window, type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same. 

Find this key HKEY_CURRENT_USER\Software\Wine\ 

Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder 
Right-click on the wine folder and select [NEW] then [KEY] 

Replace the text New Key #1 with OpenGL 

Right-click in the right hand pane and select [NEW] then [String Value] 

Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!) 

Then double click anywhere on the line, a dialog box will open. 
In the value field type GL_ARB_vertex_buffer_object 
```

Are you using the latest version of Wine?

---

### Post by LifeIsFlimsy on 2008-08-06
Yes I have changed the registry value and yes I am using the latest  version of Wine. Do you think the problem could lie in the location of where WoW is installed? It's actually not in .wine/Program Files/etc etc, it's on my desktop, yet, it still runs.

---

### Post by geekygirl on 2008-08-06
Maybe, I have never ran it from anywhere other than the Wine drive - wouldn't hurt to move it to try!

You could also try deleting the .wtf file and start WoW again, and then change the .wtf file to suit and see of this does anything.

---

### Post by LifeIsFlimsy on 2008-08-06
Moving it after it's all installed won't mess anything up? I'd rather not try without knowing, seeing as how patching and all that jazz took forever.

---

### Post by LifeIsFlimsy on 2008-08-06
I still require help with this. Please, Ubuntu Gurus, see this topic.

---

### Post by Dougie187 on 2008-08-06
I dont play WoW, so i haven't tested this, but as far as i know most other blizzard games have terrible support for opengl. (Diablo 2 and War3) you might try running it without opengl support. But again, I dont know if this is true for WoW, just a suggestion.

---

### Post by LifeIsFlimsy on 2008-08-06
How do I go back and make it run with DirectX? Everyone (and every website related to playing WoW on Ubuntu/Wine) recommended I try OpenGL in order for it to run better.

---

### Post by LifeIsFlimsy on 2008-08-06
> **geekygirl said:**
> 
You could also try deleting the .wtf file and start WoW again, and then change the .wtf file to suit and see of this does anything.

So I did this part, and now WoW barely runs. The initial login screen is so choppy, I type and a letter appears every 5 seconds. I guess deleting config.wtf was a bad idea. =/

---

### Post by LifeIsFlimsy on 2008-08-06
Alright, so I'm back to having it work with less than 10 FPS. Where are all the WoW Ubuntu users who would know what to do? Am I posting this in the wrong forum?

---

### Post by cmb11 on 2008-08-06
hey LifeIsFlimsy, i had the same problem.. but now i'm able to play wow with up to 70-80 fps (with highest settings)... way better than win XP on the same machine...

All I did was some registry tweaking plus launching the game using this command: 

#
WINEDEBUG=-all wine "C:\Program Files\DotA\Frozen Throne.exe" -opengl
#

The "WINEDEBUG=-all" will shut down the debugger of wine which will give a great increase in FPS and of course running it with "-opengl" option is faster under wine.

Try these settings and if it didn't work, i'll give some tips on tweaking the registry for better gaming support...

PS: the location of the game does not affect its performance!!

---

### Post by Mistrblank on 2008-08-06
First off, I recommend against ever trying to run WoW in direct3d mode (DirectX) and only going with OpenGL.  Blizzard's implementation of games using opengl is fine and I have never gotten WoW to work using direct3d with any hardware.  

On to the problem however.

Are you running compiz?
What hardware is in your system, specifically your processor and video card model?  
Are you starting a separate X server to run the game?
Which version of Wine are you using?
Which version of video card drivers are you using?

What is your path to the WoW install directory? I think you are using "~/Desktop/World of Warcraft", but don't want to reference without knowing for certain.

If you have deleted your WTF\Config.wtf file, remember to put the sound and other configuration settings from the wiki back into this file.

---

### Post by LifeIsFlimsy on 2008-08-06
CMB, I tried the terminal command you recommended, and there was no difference in FPS. I've already done the registry addition that is listed on the Wiki and other helpful WoW+Ubuntu sites, but I'm open to any tips at all. This is horrible.

In reply to MisterBlank:
No, Compiz is not running. At least, I can't tell that it's running. Visual effects are set to none if that's what you were asking. My processor is a P4 2.8ghz. The video card is a GeForce FX 5200, 256mb. In regards to starting a seperate X server to run the game, I have no idea how to do that. The version of Wine I am using is the most up to date version I believe. The video card driver version is also the most up to date I could get, as far as I know. It's 173.14.09.
Also, yes, the path is Desktop/wow_install/World of Warcraft/Wow.exe. Of course, a little more before that, but that's the general idea of it.

Thank you for all the help and advice given so far. Hopefully with a combined effort, I can get this problem figured out. What with XP not being produced anymore, and vista not looking at all appealing, I'm stuck between a rock and a hard place.

Edit: Hey, that's the second time I've thanked people, yet to the left it says 0! :(

---

### Post by aoanla on 2008-08-07
To find out how to run Wine apps in a separate X server, read this thread:
[http://ubuntuforums.org/showthread.php?t=634067&highlight=server+Wine](http://ubuntuforums.org/showthread.php?t=634067&highlight=server+Wine)

The latest release of Wine is 1.1.2, is that what you have installed?

---

### Post by ooobuntooo on 2008-08-07
DirectX works really well for me, just like it did on XP.
OpenGL produces corrupt buttons and places don't load properly.

---

### Post by solarghost on 2008-08-07
Have you tried installing drivers for you graphics card?

---

### Post by ooobuntooo on 2008-08-07
DirectX works really well for me, just like it did on XP.
OpenGL produces corrupt buttons and places don't load properly.

---

### Post by LifeIsFlimsy on 2008-08-07
> **solarghost said:**
> Have you tried installing drivers for you graphics card?

Yep, using EnvyNG.

---

### Post by LifeIsFlimsy on 2008-08-07
Well, still no luck getting better FPS after trying every possible solution I've found. Guess I'm gonna have to go grab a copy of vista when I get a chance. =/

Thanks again folks.

---

### Post by ooobuntooo on 2008-08-07
> **LifeIsFlimsy said:**
> Well, still no luck getting better FPS after trying every possible solution I've found. Guess I'm gonna have to go grab a copy of vista when I get a chance. =/

Thanks again folks.

Vista isn't a very good gaming OS, use XP.

---

### Post by geekygirl on 2008-08-07
> **LifeIsFlimsy said:**
> Alright, so I'm back to having it work with less than 10 FPS. Where are all the WoW Ubuntu users who would know what to do? Am I posting this in the wrong forum?

No right forum :)

What hardware are you running?

All I meant by deleting the .wtf file was to restart the game which allows WoW to reset the .wtf file. Perhaps I needed to tell you to backup the old on first..my bad!

Once it is reset try adjusting things in there one at a time. When it comes to adjusting video settings in-game this is best done whilst using d3d (Direct X) mode. Exit and force OpenGL in the .wtf file again.

If you have any addons remove them and see if that changes things. Do you have Compiz running? Turn it off if you do, its a resource hog with regards to gaming anyways.

Have you tried running WoW in windowed mode?

Make sure you follow ALL the install procedures in here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

and for troubleshooting here:

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

These are the only instructions I have ever used and I am running WoW very well with no issues and a constant fps of between 60-80 at all times, only lagging to 30-50 in Shatt.

I am running WoW on this hardware:

E8200
EP35-DS3L
2G DDR2 1066MHz
150G WD Raptor HDD
XFX 9600GT 512MB

Other than that you might need to reinstall WoW, or check your Wine configuration (try running Wine in Windows XP mode - I use this as well if that helps)

if none of that works there might be issues with your Wine install itself or something else.

---

### Post by LifeIsFlimsy on 2008-08-07
Well, as for Vista not being a very good gaming OS, I heard that XP isn't being produced anymore, so that's why I said vista.

In reply to Geekygrl, I've followed all of the procedures on the websites you linked. I have tried running it in Windowed mode, and no difference. I'm beginning to wonder if it's simply because I've got a gig of RAM, although that still doesn't make much sense considering in XP I had a way better framerate.

I'd love to run Wine in XP except I completely replaced XP with Ubuntu (apparently my copy of XP wasn't genuine, etc).

The only thing I haven't been able to try is adding a certain line to the /etc/x11/xorg.conf file. A few sites I've read say to do that, but for some reason, even though I am the only user on this computer, it says I don't have root authority or whatever it is to be able to save the changed file. Any thoughts?

---

### Post by geekygirl on 2008-08-07
> **LifeIsFlimsy said:**
> Well, as for Vista not being a very good gaming OS, I heard that XP isn't being produced anymore, so that's why I said vista.

In reply to Geekygrl, I've followed all of the procedures on the websites you linked. I have tried running it in Windowed mode, and no difference. I'm beginning to wonder if it's simply because I've got a gig of RAM, although that still doesn't make much sense considering in XP I had a way better framerate.

I'd love to run Wine in XP except I completely replaced XP with Ubuntu (apparently my copy of XP wasn't genuine, etc).

The only thing I haven't been able to try is adding a certain line to the /etc/x11/xorg.conf file. A few sites I've read say to do that, but for some reason, even though I am the only user on this computer, it says I don't have root authority or whatever it is to be able to save the changed file. Any thoughts?

Ok to clarify what I was referring to, when you run

```
winecfg
```

in the terminal, there is a dropdown box on that initial screen, where you can choose what Windows level you want to use, it has Windows XP, Vista, Windows 98 etc. That where I was referring to change it to Windows XP.

That has nothing to do with Microsoft and Windows itself!

1G of memory might be an issue. I know wine can test some systems out as you are effectivly adding another layer into the system. But someone else might be able to shed more light on that.

When you are editing your xorg.conf file try doing it this way (in terminal):

```
gksu gedit /etc/x11/xorg.conf
```

You will be prompted for your password (same as your login one), then gedit will open up the file, and there you can add the extra line in. Just save and close when done.

---

### Post by LifeIsFlimsy on 2008-08-08
That method of changing xorg.conf worked but no framerate change.

---

### Post by Dougie187 on 2008-08-08
Where did you download wine from? The ubuntu repositories (defualt) or the wine repositories (you would have had to do extra work to get these)

The most up-to-date version from the ubuntu repos is 0.9.59, where as from the wine repos its 1.1.2. To check your version you  can either look in the "About" tab in winecfg or you can type in a terminal "wine --version"

Also, if you want to try something, I'm not sure if you did this yet or not, but remove the -opengl flag from your launcher, and go back into the registry and delete the opengl key that you made (part of the registry hack). If that still doesn't work try deleting the other registry hack keys that you did. I know for me at least, when i followed some of the registry and performance hacks people recommend the just made things worse. A great example for me was Warcraft 3. If I used the registry hacks it would make every texture a giant blob instead of what it was supposed to be. You couldn't make anything out. But once i got rid of all that crap it was nice and cleaned up, and it works great now.

---

### Post by YokoZar on 2008-08-08
> **Dougie187 said:**
> Where did you download wine from? The ubuntu repositories (defualt) or the wine repositories (you would have had to do extra work to get these)

The most up-to-date version from the ubuntu repos is 0.9.59, where as from the wine repos its 1.1.2. To check your version you  can either look in the "About" tab in winecfg or you can type in a terminal "wine --version"Wine 1.0 is available without extra work now

---

### Post by flytripper on 2008-08-08
> **LifeIsFlimsy said:**
> 
Compiz is not running.
My processor is a P4 2.8ghz.
The video card is a GeForce FX 5200, 256mb.



install the compiz-fusion-icon so you can quick swap window managers.
The processor is more than enough.
The graphics card is very poor. VERY POOR for Wow. I have 7600 and thats not even good enough.  -20 fps in dungeons

Sorry to be the bearer of bad news but,the graphics and maybe ram(best 2 gig) will need upgrading if you are going to continue playing on that rig or you'll have to live with it I'm afraid.

---

### Post by Mahinva on 2008-08-08
Well, here is my computer's system specs:

Intel P4 2.8Ghz
Nvidia GeForce FX 5500 256mb.
2.5gigs DDR RAM.

Let's say I'm inside the inn at Thrallmar - I can easily get 60fps. If I go outside, 10fps is average. My addons use roughly 16mb - with over half of that being from Blizzard's game client itself. There is no performance difference if I use addons or if I don't.

I used to run 500MB RAM and got similar fps results.

As far as hardware, the only thing that I could upgrade is the CPU chip. The P4 3.2Ghz is the "best available", albeit it is usually sold for more than it is worth and therefore seems unreasonable unless I can find one for under $40 - I think $70-100+ is too much. The video card I am using is also an upgrade from something much older. Personally, aside from attmepting to tweak things to squeeze a few more fps, I'll be making a new computer sometime in the future.

I've tried out pretty much every tweak suggested here and on the links mentioned - I do not notice any sort of performance gain. The only thing I have not yet tried is running WoW on its own X-server, mainly because the thread [**here**](http://ubuntuforums.org/showthread.php?t=634067&highlight=server+Wine) has a poster who has run into trouble and is currently seeking a solution. I don't want to run into trouble so I'd much rather test that method when the other user has gotten a response.

---

### Post by LifeIsFlimsy on 2008-08-08
> **flytripper said:**
> install the compiz-fusion-icon so you can quick swap window managers.
The processor is more than enough.
The graphics card is very poor. VERY POOR for Wow. I have 7600 and thats not even good enough.  -20 fps in dungeons

Sorry to be the bearer of bad news but,the graphics and maybe ram(best 2 gig) will need upgrading if you are going to continue playing on that rig or you'll have to live with it I'm afraid.

I'm more disappointed than anything. The card isn't the best, but in XP, my FPS was constantly smooth. 20 FPS is fine with me. I had around 20 fps in busy areas in-game. It's much better than 3-5 fps.

---

### Post by LifeIsFlimsy on 2008-08-08
> **Dougie187 said:**
> Where did you download wine from? The ubuntu repositories (defualt) or the wine repositories (you would have had to do extra work to get these)

The most up-to-date version from the ubuntu repos is 0.9.59, where as from the wine repos its 1.1.2. To check your version you  can either look in the "About" tab in winecfg or you can type in a terminal "wine --version"

Also, if you want to try something, I'm not sure if you did this yet or not, but remove the -opengl flag from your launcher, and go back into the registry and delete the opengl key that you made (part of the registry hack). If that still doesn't work try deleting the other registry hack keys that you did. I know for me at least, when i followed some of the registry and performance hacks people recommend the just made things worse. A great example for me was Warcraft 3. If I used the registry hacks it would make every texture a giant blob instead of what it was supposed to be. You couldn't make anything out. But once i got rid of all that crap it was nice and cleaned up, and it works great now.

I have Wine 1.1.2.

What do you mean remove -opengl from my launcher? I do have the registry hack done, but from what I've read, there was only the one change.

---

### Post by LifeIsFlimsy on 2008-08-08
Dougie, I deleted the registry key, and my framerate has improved a bit. I'm not sure if it's just because there aren't that many people on WoW atm, or if it actually worked, but I'm getting about 10 FPS now in crowded areas.

Still, what did you mean about removing -opengl from the launcher?

---

### Post by Mahinva on 2008-08-08
If you are using the following to launch the game:


```
WINEDEBUG=-all wine "C:\Program Files\DotA\Frozen Throne.exe" -opengl
```

I believe Dougie 187 means make the above line like this:


```
WINEDEBUG=-all wine "C:\Program Files\DotA\Frozen Throne.exe"
```

Notice how there is no "-opengl" at the end anymore?

---

### Post by cmb11 on 2008-08-08
WOW will run faster under OpenGL !!! Plus when it comes to linux and wine, OpenGL is far more better supported than DirectX. 


I'm getting 10-15 fps less if I run WOW under DirectX.

---

### Post by Dougie187 on 2008-08-08
@CMB, just because that is how it worked for you doesn't mean that is how it will work for him. For me I know with warcraft 3 Wine installation how-to's recommend using OpenGL but when I use it everything breaks and runs like crap.

I just figured since it wasn't working for him before, this is one thing he can try and see if it helps.

Also, Mahinva is right, i am suggesting taking out the -opengl flag from your wine launcher.

---

### Post by LifeIsFlimsy on 2008-08-10
I launch it from a desktop icon. Anything I can change in the properties of it related to removing opengl from a terminal launch? Do you think it would run better launching from the terminal?

---

### Post by Dougie187 on 2008-08-10
running it from terminal shouldnt have any effect. but if you right click on the desktop launcher, just go to the properties and look in the launcher tab, under the command field. See if you have -opengl in the command, if not then thats all i recommend, if you do, then remove it and try running it.

---

### Post by Mahinva on 2008-08-10
If you try what Dougie187 suggests and you notice no difference, try the following:

Read the thread here:

[http://ubuntuforums.org/showthread.php?t=699332](http://ubuntuforums.org/showthread.php?t=699332)

The instructions may confuse you (they confused me!) so this post will explain as it was written by a newbie and is rather straight forward:

[http://ubuntuforums.org/showpost.php?p=5562107&postcount=58](http://ubuntuforums.org/showpost.php?p=5562107&postcount=58)

After you have installed the script, you can create a desktop icon (a "launcher"). Here is the example I followed:

[http://ubuntuforums.org/showpost.php?p=4373760&postcount=12](http://ubuntuforums.org/showpost.php?p=4373760&postcount=12)

NOTE: In the link above, you will see a code. I had to change the user name of "justin" to my own user name - unless your user name is "justin", you'll have to change it too! :D Also, I had to remove the "WINEDEBUG=-all". When I ran the launcher with "WINEDEBUG=-all" included, I got an error.

To make a brand new launcher (if you want to), you can click anywhere on your desktop and select "Create Launcher". From there, type in a name "WoW", "World of Warcraft" etc,  and put the code provided from my last link into the "Command" textbox. To change the icon, click on the springboard icon on the left. From there, you may have a big file browser window. You may be able to navigate through that browser, following my example:

/home/USER/.local/share/icons/3526_launcher.0.xpm

The "3526_launcher.0.xpm" is a World of Warcraft icon.

You can either put a comment on the launcher, or leave one out. Afterwards, you should be able to use that launcher like you would use any other. Your screen will change to that of a empty desktop (with a background image). In another moment, WoW should load. When you finish playing, you'll return to that empty desktop. Right-clicking on it will bring a menu - just select the "exit" option and you'll return to your regular desktop.

Some people have found that playing games on their own xservers helps quite a lot, while others don't notice too much of a difference.

I hope that this helps. If you're confused, I can try to answer some questions, but I only learned how to make an xserver today. You may find more help on posting at the thread I linked at the very start of this post.

---

### Post by Dougie187 on 2008-08-13
Did any of this work for you? If so, you should mark the thread as solved.

---

### Post by Suroh on 2010-08-26
It worked for me I had no problems :) It barley increased my fps I've looked at some things and may have found a way around my own problem and if so this should work wonders

---

