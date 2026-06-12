---
title: "Won't eject disc 1!"
date: 2006-09-06
forum: Wine
---

### Post by Mimsy on 2006-09-06
I don't know if this technically counts as a game, but it's sold as one, so here goes...

I installed and set up Wine on my little Compaq Evo N410c laptop in order to run this one single program, Y!F, for short. Installation requires me to switch to the second CD in the middle of the "copy files to the hard drive" phase, and this was never a problem in Windows. However, in Wine, the drive absolutely refuses to eject CD 1, and when I ask for details it tells me it can't because the drive is busy.

When I cancel out of the installation, I can eject the CD, but when the installer prompts me to switch CDs, nothing happens. When I listen closely, I hear absolutely nothing from the drive, no spinning or reading of the disc whatsoever.

Help?

Thanks,
Mimsy

---

### Post by azraelx401 on 2006-09-06
is the disc still spinning in the drive?

---

### Post by Mimsy on 2006-09-06
Not that I can tell. Ubuntu claims the drive is busy, but I hear no spinning noises from it, and it's a rather noisy drive. I can hear the disc spin when I put it in, for example.

---

### Post by Mimsy on 2006-09-06
Update:
I take that back. I tried again just a moment ago, just to make sure, and the disc does still spin in the drive. I simply didn't notice earlier. Sorry for the misinformation.

/Mimsy

---

### Post by tollbooth on 2006-09-06
one thing, is the light on the drive constely on or blinking?

---

### Post by jediborger on 2006-09-06
Ok to solve this problem there's two solutions:
1) Open a terminal and manually unmount the cdrom
   -First open a terminal.
   -Second type mount to see what device is mounted at /dev/cdrom0 (usually /dev/hdd)
   -Third type sudo umount /dev/hdd (or whatever device is your cd-rom)
   -Fourth insert the next cd and it should auto-mount fine and repeat steps 1 and 2 for any more cd changes.

2) This works if you have two cd drives. Change the wine drive mappings.
   -First open a terminal.
   -Second type winecfg
   -Third click the Drives tab
   -Now click the drive letter that currently represents your cd drive (eg D) and change the path to /dev/cdrom1
   -Click apply and go back to your windows app to continue install, when you need to go back to disc one simply change the path back to /dev/cdrom0

Hope this helps:)

---

### Post by Mimsy on 2006-09-06
I only have one CD drive, so the second solution is unfortunately not possible for me. This happens when I try the umount route:

> 
umount: /media/cdrom0: device is busy


The disc happily spins away in the drive. This is very strange.

I am open to suggestions. :) 

/Mimsy

---

### Post by DoktorSeven on 2006-09-06
I am normally able to get past this by running the setup program from outside of where the drive is mounted, and making sure that nothing else is running that is accessing the drive (showing drive contents, etc).

So something like:
```
wine /media/cdrom/Setup.exe
``` 
from my home directory, not from inside /media/cdrom/.  When it requests a second CDROM, I am then able to manually unmount (from a second command prompt) and eject the CD, and put another in.

I have, however, heard of instances where this does not work, possibly because the OS has a background process polling the drive?  

As a side note, the command **fuser -c /media/cdrom** will show which process is using the drive (note the number it displays after the process, remove the letter after it, and use it in place of **number** in the following command -- **ps ax | grep number** -- to show you what is using it).  It may be possible to kill any other process accessing the drive so you may unmount it.

---

### Post by Mimsy on 2006-09-06
I think this might be bad. There is no CD-drive anymore. Now that I think about it, it probably has to do with the umount commands I was typing in yesterday. When I put "mount" in the terminal, to see why I couldn't run the setup from /media/cdrom/, the drive isn't listed among the results. I have a cd recorder I didn't have yesterday though, /dev/hdc on /media/cdrecorder.

Huh? :confused: 

How do I get the CD drive back?

Thanks,
Mimsy

---

### Post by jperez on 2006-09-08
**For unmounting**

I had the same problem, but I tried:

```
sudo umount /dev/hdb
```

and it worked perfectly.  It unmounted the Dapper CD I had in there and let me eject it without a restart.  Try it.

**For mounting**

Try the same command, but type mount instead:

```
sudo mount /dev/hdb
```

Essentially, it should work the same way.

Jesse~

---

### Post by Mimsy on 2006-09-08
Last night I tried DoctorSeven's suggestion, to run the setup.exe by typing in "wine <path to setup.exe> in the terminal, but the disc still won't eject. Very strange.

Next I will try typing in hdb instead of hdd when I want to unmount, and later remount the CD drive, and see if that helps.

Thank you for the effort, everyone. I almost feel bad that nothing's helped yet.

/Mimsy

---

### Post by Mimsy on 2006-09-09
> **DoktorSeven said:**
> I have, however, heard of instances where this does not work, possibly because the OS has a background process polling the drive?  

As a side note, the command **fuser -c /media/cdrom** will show which process is using the drive (note the number it displays after the process, remove the letter after it, and use it in place of **number** in the following command -- **ps ax | grep number** -- to show you what is using it).  It may be possible to kill any other process accessing the drive so you may unmount it.

Sadly, after trying this command the terminal still returns, > umount: / media/cdrom0: device is busy when I try to unmount it.

> **jperez said:**
> **For unmounting**

I had the same problem, but I tried:

```
sudo umount /dev/hdb
```

and it worked perfectly.  It unmounted the Dapper CD I had in there and let me eject it without a restart.  Try it.

Thanks for the suggestion. I did try, but the terminal told me it couldn't find /dev/hdb/

I'm getting really confused here, not to mention frustrated. any and all suggestions that don't involve spending money or destroying the laptop are welcome, and I promise they will be tried.

This refusal to eject the disc has never happened to me before. ](*,) 

/Mimsy

---

### Post by Mimsy on 2006-09-16
I solved it! Kind of.

I copied all the important files from CD1 and CD2 to a folder on the desktop, and ran the setup.exe from there. It worked, it installed everything, and I now have a launcher for the game on my desktop.Cool. Except the launcher isn't working. I know that in windows the important files are in the folder C:\Program Files\GameName Where is the Ubuntu equivalent of that folder?

Now that I have managed to install the game, I would like too be able to play it. :) 

/Mimsy

---

### Post by jediborger on 2006-09-17
This is a windows game under wine right? If yes then its under

/home/*user_name*/.wine/drive_c/Program Files/*game_folder*

This where wine puts the psuedo C drive

Hope this helps:D

---

### Post by aanderse on 2006-09-17
just as a side note ... when installing games from a cd usually you will be running setup.exe or install.exe off the cd - do not type wine /media/cdrecorder/install.exe in a terminal, instead, press alt+f2 (in gnome) which will bring up a "run application" menu and then type wine /media/cdrecorder/install.exe in there.  the reason for this is that if you type it into a terminal, during the installation the terminal is still running the process and uses the cdrom sometimes (i think)

this was just my perception of things, it worked for me :)

---

### Post by jimmygoon on 2006-09-17
> **aanderse said:**
> just as a side note ... when installing games from a cd usually you will be running setup.exe or install.exe off the cd - do not type wine /media/cdrecorder/install.exe in a terminal, instead, press alt+f2 (in gnome) which will bring up a "run application" menu and then type wine /media/cdrecorder/install.exe in there.  the reason for this is that if you type it into a terminal, during the installation the terminal is still running the process and uses the cdrom sometimes (i think)

this was just my perception of things, it worked for me :)

not correct. the alt+f2 is the same thing... except... with it you can't see the feedback if something breaks.

You **should** open up a terminal and try running "wine ~/.wine/drive_c/Program Files/myapp/program.exe" or whatever

good luck.

---

### Post by Mimsy on 2006-09-17
Thanks jimmygoon. I'll try your advice next. One thing though: How do I uninstall this thing, so I can start over fresh?

/Mimsy

---

### Post by DoktorSeven on 2006-09-18
Wine's uninstaller to remove installed Windows programs (like Add/Remove Programs in Windows) is called, oddly enough, **uninstaller**.

Run it in a terminal or with alt+f2 (for gnome).

---

### Post by Mimsy on 2006-09-18
> **DoktorSeven said:**
> Wine's uninstaller to remove installed Windows programs (like Add/Remove Programs in Windows) is called, oddly enough, **uninstaller**.

Run it in a terminal or with alt+f2 (for gnome).

Wow. That name was just way too difficult for me to figure out on my own... :p

I'll run it in gnome and see what happens.

Thanks!

/Mimsy

---

### Post by Mimsy on 2006-09-19
> **jimmygoon said:**
> not correct. the alt+f2 is the same thing... except... with it you can't see the feedback if something breaks.

You **should** open up a terminal and try running "wine ~/.wine/drive_c/Program Files/myapp/program.exe" or whatever

good luck.

I pasted that into a terminal, and replaced everything after Program Files with the path to the .exe file in that folder.I got the message "A debugger has been deteced. Unload the debugger and try again." The message is in a window that looks a lot like a Windows error message window. Do I need to simply accept that this one application simply can't run on Ubuntu?

Thanks,
Mimsy

---

### Post by Mimsy on 2006-10-01
After updating and reconfiguring Wine, i am back to square one.

Ubuntu refuses to eject the CD, even after I have killed the installation process and all wine processes. In addition to not being able to install the application, I now have a disc stuck in the CD/DVD drive, and no way of removing it. I have tried all umount solutions suggested previously in this thread, to no avail.

I consider myself a patient woman, at least when it comes to computers, but this is beginning to frustrate me. I am rapidly approaching the point where I would be willing to pay someone to set this up for me. Considering how dirt poor I am, this is a bad thing - I can't afford it, but consider it anyway. Help me save my finances, please?

/Mimsy

---

### Post by Mimsy on 2006-10-01
Never mind, I finally managed to enject the disc. Go me! :)

Now it freezes in midinstall instead. I copied all files to the hard drive, since that worked and let me install last time around. Now, however, it makes it all the way to "Status: Copying new files" and freezes there. It sits there for minutes and minutes, and eventually shuts down.

Weird.

Anyway, I'm still open to suggestions. This is turning into an obsession for me.

/Mimsy

---

### Post by Mimsy on 2006-10-01
Okay, another update on my situation.

I've managed to install the thing. Nothing makes it as easy to find a solution as asking for help... no idea why.

Anyway, when I try to run the .exe file in wine, I get the same error message as last time.

> A debugger has been detected. Unload the debugger and try again.

Now what? To my knowledge there's no debugger installed...?

/Mimsy

---

### Post by Lusse on 2006-10-21
What game are you trying to install. I cant get out my cd to and I am installing CS:CZ. But I am doing it with cvscedega.

/Linus

---

### Post by Mimsy on 2006-10-21
It's not CS, sorry. Technically it's not even a game, it's an AI personal trainer application. You can find info about it [here]("http://www.yourselffitness.com"), if you're interested.

I'm going to give my work-out application a chance in CVScedega, probably tomorrow, when I'll have time to actually install the thing (not to mention that I won't be one third into the Anniversary Vodka by then...). If that doesn't work, I'll probably give TransGaming's most current Cedega a shot. $5 isn't much for a month, and if the AI trainer doesn't work, I can always install Baldur's Gate and Fallout in it, right? ;)

/Mimsy

---

### Post by mighty_falcon on 2006-10-22
I am having the same exact problem installing battlefield 2 with the latest cedega...it is very frustarating as it installs the first cd and i just cannot eject it to place the 2nd one...if i cancel then i can eject fine and i cant unmount since it sais device is busy

i tried to copy the cd files on the hard drive but that will not work as the install files look for the files in the cd rom so it will ask to place a disk in the cd rom when it comes to disk two

there must be a work around for this? no one else ever experiened it???](*,)

---

### Post by mighty_falcon on 2006-10-22
after messing around with it for awhile it seems you need to pass it this command

cedega -monitor-cdrom-eject /mnt/cdrom/setup.exe

all worked great after that, excpet for the running of the game but that is a complete different story lol

anyways let me know if it works for you

---

### Post by Mimsy on 2006-10-22
I haven't had a chance to even install cedega yet, but once I do, I'll be sure to let you know if that command works or not. Thanks!

/Mimsy

---

### Post by gaminggeek on 2006-10-23
Start wine from the console and when it asks for a new disk hit ctrl-z this will pause the app, then eject the disk put in the new one and type in fg this should work if I have remebered corectly

---

### Post by blackmh on 2006-10-23
sudo lsof +D /cdrom|awk '{ print $2; }'|grep -v PID|uniq|xargs kill -9 
sudo umount -f /media/cdrom0 

works like a charm

---

### Post by MiD-AwE on 2006-11-05
I did exactly this > **blackmh said:**
> sudo lsof +D /cdrom|awk '{ print $2; }'|grep -v PID|uniq|xargs kill -9 
sudo umount -f /media/cdrom
And, then typed "eject /media/cdrom" into the console and it ejected my cdrom promptly. So no one fret, it will eject your cdrom ASA you press enter.(give or take a second or two.)
You will be prompted for your password but it works on DAPPER AMD64

Now I'd like to ask how it works. The shell script that locked my cdrom drive is the well known DOOM3 intall script. It had just created my directories and copied my .pk4 files from my cd1 it asked for my cd2 and told me to eject. I pressed the eject button on my drive and it did not respond. Once I used your suggestion it worked, but it also ended my DOOM3 Install script leaving me to discover a better solution..?

Thanks

---

### Post by wicke on 2008-02-25
Alt+F2 works fine! It doesn't lock the CD to the bash as it did before. I'm installing from the CD2 now and hoping it will go successfully end with all those 4 CDs.

(*OK, installation indicator disappeared but installation still continues and asked for the last CD... Back to first CD, installation is finalizing... Complete!!!*)

---

### Post by pedro_orange on 2008-02-25
Have you tried just doing

```
wine eject d:
```

This tells wine to release it's hold on the device, and eject it.

---

### Post by ToSsMaStR on 2008-04-16
...so fustrating

---

### Post by programmer8922 on 2008-04-17
I had the same problem when installing The Orange Box so I just copied the DVDs to the hard drive and it worked like a charm.

---

