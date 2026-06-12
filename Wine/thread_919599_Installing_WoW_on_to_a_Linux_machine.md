---
title: "Installing WoW on to a Linux machine"
date: 2008-09-14
forum: Wine
---

### Post by Pharohs on 2008-09-14
The only thing I used Windows for was playing WoW.  I want a 100% Ubuntu machine.  I friend of mine, an uber Windows guy doesn't believe it can be done.  I want to show him that Ubuntu (and Linux as a whole) is a viable system with advantages over Windows.  I know he will be convinced if I can do this. I am following the instructions found here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I think that I am doing surprisingly well, however, I don't know how to do this: "***Copy all of the files from the first WoW CD to this new directory.***"  I am still reading and trying to learn the terminal commands.

Nothing I looked up seemed to be quite right to get the job done.  I'm trying to copy everything from the CD to the new folder on my desktop.  The twist is, the only things showing on the CD are the Mac OSX.app  and the Installer Tome.mpq.  I am using WINE so, I need the Windows XP installer stuff.

I'm sure that someone has done this successfully.**[B]**[/B]

---

### Post by ju2wheels on 2008-09-14
Well according to this guide you should have run the following in a command line:

```

sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/

```

Did you do this part? You should see a CD ROM icon on your desktop at this point of you did this correctly.

If you do not see the cd rom do the following and then try the above again:
```

sudo umount /media/crdom0

```

Once you have the cd mounted properly do the following to copy all the contents:
```

sudo cp -R /media/cdrom0 ~/Desktop/wow_install_folder

```

---

### Post by Pharohs on 2008-09-14
The "WOW CDROM" icon is on the desktop along with the folder "wow_install" that I made earlier.  In my ignorance, I just did everything you said, here are the results:

[B]othello@othello-laptop:~$ sudo umount /media/crdom0
umount: /media/crdom0: not found
othello@othello-laptop:~$ sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
mount: special device /dev/cdrom does not exist
othello@othello-laptop:~$ sudo cp -R /media/cdrom0 ~/Desktop/wow_install
othello@othello-laptop:~$ [/B]

There is nothing in the folder "wow_install". So, I think that nothing happened.  BTW, how do I get the little box around the code lines I posted? I'd like to do things the right way.

---

### Post by ju2wheels on 2008-09-15
Ok from the output of the mount command it seems there was an error on mounting the cd due to using the wrong device.

Attempt the instructions again except this time do the following for the mount:

```

sudo mount -t iso9660 -o ro,unhide /dev/scd0 /media/cdrom0/

```

Also the box is done using BB code (its available as buttons, # is the one i used, at the top of the message writing box).

---

### Post by Pharohs on 2008-09-15
Ok. I did that and here is what happened:

```
othello@othello-laptop:~$ sudo mount -t iso9660 -o ro,unhide /dev/scd0 /media/cdrom0/
[sudo] password for othello: 
mount: /dev/scd0 already mounted or /media/cdrom0/ busy
mount: according to mtab, /dev/scd0 is mounted on /media/WoW DVD
othello@othello-laptop:~$ 

```

:confused:

The CDROM icon is on the desktop.  This seems normal.  Now, this is what is showing on the disk:

[IMG]http://s521.photobucket.com/albums/w339/Gringras/?action=view&current=Screenshot.png[/IMG]

So, what do I do, to copy everything from the CDROM to the "wow_install" folder on the desktop.  Also, as you can see, only the OSX version is showing up on the CDROM. :confused:

I need the XP version to run with the WINE that is already installed.

---

### Post by ju2wheels on 2008-09-15
Did you unmount if first before doing that? It looks like it was already mounted. 

It should be done in this order:

```

sudo umount /media/WoW\ DVD
sudo mount -t iso9660 -o ro,unhide /dev/scd0 /media/cdrom0
sudo cp -R /media/cdrom0 ~/Desktop/wow_install

```

If you dont unmount it first, Ubuntu mounts the cd with the default options which may not include the unhide option that is needed to show the XP portion of the cd.

---

### Post by Pharohs on 2008-09-15
Ok, ju2wheels, I got that done.  Your commands were fantastic!
Here was my next step:
```
4. Open a terminal and do these commands inside to start the installation:
Code:

cd /<path-to-directory>/
wine Installer.exe


```

Here is what happened next:
```
othello@othello-laptop:~/Desktop/wow_install$ **cd /home/othello/Desktop/wow_install/cdrom0**
othello@othello-laptop:~/Desktop/wow_install/cdrom0$ **wine Installer.exe**
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on ATI IXP Modem, disabling mixer
othello@othello-laptop:~/Desktop/wow_install/cdrom0$ fixme:richedit:IRichEditOle_fnGetClientSite stub 0x14d32a8
fixme:ole:OleCreateStaticFromData (not shown), stub!

```

Here is what the folder looks like:
[http://s521.photobucket.com/albums/w339/Gringras/?action=view&current=Screenshot-2.jpg](http://s521.photobucket.com/albums/w339/Gringras/?action=view&current=Screenshot-2.jpg)


This is WAY over my head.  :confused:  I just don't understand why it is so difficult when using WINE.  This game is rated Gold with WINE.

---

### Post by gjoellee on 2008-09-15
it seams like you have trouble here...why don't you download WoW instead?

---

### Post by Oldsoldier2003 on 2008-09-15
WoW installation threads belong in the wine subforum, I'll move it now.

---

### Post by Wiebelhaus on 2008-09-15
Codeweavers , 'nuff said.

---

### Post by lakersforce on 2008-09-15
> **Pharohs said:**
> "***Copy all of the files from the first WoW CD to this new directory.***".

You could use cp -R from command-line, but wouldn't be easier to do it from GUI?

---

### Post by aoanla on 2008-09-15
> **Pharohs said:**
> Ok, ju2wheels, I got that done.  Your commands were fantastic!
Here was my next step:
```
4. Open a terminal and do these commands inside to start the installation:
Code:

cd /<path-to-directory>/
wine Installer.exe


```

Here is what happened next:
```
othello@othello-laptop:~/Desktop/wow_install$ **cd /home/othello/Desktop/wow_install/cdrom0**
othello@othello-laptop:~/Desktop/wow_install/cdrom0$ **wine Installer.exe**
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on ATI IXP Modem, disabling mixer
othello@othello-laptop:~/Desktop/wow_install/cdrom0$ fixme:richedit:IRichEditOle_fnGetClientSite stub 0x14d32a8
fixme:ole:OleCreateStaticFromData (not shown), stub!

```

Here is what the folder looks like:
[http://s521.photobucket.com/albums/w339/Gringras/?action=view&current=Screenshot-2.jpg](http://s521.photobucket.com/albums/w339/Gringras/?action=view&current=Screenshot-2.jpg)


This is WAY over my head.  :confused:


It's really not - you're just not used to it yet.


>   I just don't understand why it is so difficult when using WINE.  This game is rated Gold with WINE.

That's because it's not difficult - you're reacting to "warns" as if they're "errors" and generally a little tense about things. This is just because you're not used to terminals, etc. It gets better.

The ALSA messages are from Wine, telling you that it's not sure how to talk to your sound card. If you've not used Wine before, try typing:

winecfg

into a terminal, and going to the sound tab and setting up your sound devices. (Pick ALSA to start with.)

Then, after closing winecfg, try the 

wine installer.exe 

again.

---

### Post by Pharohs on 2008-09-15
After many fruitless hours, I gave up on installing from the disks aand downloaded the installer. I don't know how this will be any better, but...nothing beats a can't like a try!  Oddly, I had already tested the sound using "**winecfg**".  I capitalized the word "**Installer**" when I ran "**wine Installer.exe**"  is that a mistake?  How does capitalization affect things? Are some things case sensitive?
It seems like all the preparatory steps I took were for nothing.  I'll know if the download will work in a few hours.  Thanks to all of you for your help.  If nothing else, I am learning things.

---

### Post by ju2wheels on 2008-09-15
1. Do you have the latest version of Wine installed? (1.0) A lot of those installations listed as Gold on winehq actually use the most up to date development version of wine (later than 1.0).

2. Have you looked for WoW installation instructions on [www.winehq.com](www.winehq.com) ? Typically people leave comments on their installation attempts there and how they did it. I dont play video games on my computer so unfortunately I dont have any experience in installing such games.

---

### Post by Pharohs on 2008-09-16
It turns our that-other than the long download time- installation via download was rather easy and mostly painless.  But, the entire experience was great, because I learned quite a bit.  Thanks to everyone for their assistance.

---

### Post by lakersforce on 2008-09-16
Make sure your files are executable (by default newly copied files are not). In GUI: right-click, properties, the middle-most tab, make executable (near bottom).

EDIT: Ah, nevermind :)

---

### Post by Calmatory on 2008-09-16
> **Pharohs said:**
> The only thing I used Windows for was playing WoW.  I want a 100% Ubuntu machine.  **I friend of mine, an uber Windows guy doesn't believe it can be done.  I want to show him that Ubuntu (and Linux as a whole) is a viable system with advantages over Windows.**  I know he will be convinced if I can do this. I am following the instructions found here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I think that I am doing surprisingly well, however, I don't know how to do this: "***Copy all of the files from the first WoW CD to this new directory.***"  **I am still reading and trying to learn the terminal commands.**

Nothing I looked up seemed to be quite right to get the job done.  I'm trying to copy everything from the CD to the new folder on my desktop.  The twist is, the only things showing on the CD are the Mac OSX.app  and the Installer Tome.mpq.  I am using WINE so, I need the Windows XP installer stuff.

I'm sure that someone has done this successfully.**[B]**[/B]
[useless rant]
So, you come here to ask "Tell me counter opinions why windoze sux."?

I am no Microsoft/Windows fanboy, but recently all this "If it is done by Microsoft, it sucks! Lets show linux is better!" stuff is idiotic.

Just like there are "cool" things in real life, there must be "cool" things in internet. Using Linux and bashing Microsoft/Windows looks like a one to me. Everyone uses them, but then people belong to this marginaö group of people who can laugh at the masses. Just like conspiracy theorists do. 

Why can't people just admit that Linux is no for serious gaming? I mean, "We got Wine!", and people forget that not everything works out of the box, nor as good as on Windows. Actually, nothing works BETTER. I for one couldn't get WoW to work. Nor Trackmania Nations Forever. Nor CS:S, Nor Soldat. Actually I've NEVER seen that Wine runs something FLAWLESSLY. And I consider a slight mouse cursor animation bug a flaw.

[/useless rant]

Actually, usually after I write something like that, I usually just leave the page without posting it. But, just for the sake of "big bad monopolistic giant inferior company" called Microsoft, I post this, and I say that Linux and Wine SUCK for gaming. (Yes yes, a lot of progress has been made, but that justifies nothing. And until everything works, everything sucks.) :)

---

