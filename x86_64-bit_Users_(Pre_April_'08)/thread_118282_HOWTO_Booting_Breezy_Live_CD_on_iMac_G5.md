---
title: "HOWTO: Booting Breezy Live CD on iMac G5"
date: 2006-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by exparrot on 2006-01-16
My friend and I had a bit of a go at this.... and it seems that the esound daemon is what causes the "crash at a brown screen" or "crash at login screen".

In any case, this is a fairly easy (if not necessarily the best) solution to booting the live CD and having a mostly functional linux system booted on the iMac G5

**Step 1**

Insert the live CD and reboot, make sure you hold down C once you hear the chime to tell the Mac to boot from CD.

**Step 2**

When the prompt *boot:* appears, type in *live-powerpc64* and press enter.

**Step 3**

Proceed as you would normally through all the prompts (select country, network configuration etc) until you get to the prompt asking you which resolutions you'd like to use for X. By this point the filesystem has been mounted, and you can disable the esound daemon.

**Step 4**

Here's one way of disabling the esound daemon:

Hit Ctrl+Alt+F6 (I think, try a few until you get root@(whatever)# on the screen) to switch out to a console. Hit enter to activate the console if necessary.

Type in

cd /usr/bin
mv esd oldesd

Now you can switch back to the setup console (probably Ctrl+Alt+F1) and continue.

**Step 5**

Ubuntu will now boot to a desktop, you can mount your HDD filesystems, etc... an error does pop up about not being able to initialize HAL, and the sound won't work, but at least it does boot. Perhaps someone else can take it from here? I tried loading the esound daemon up after it was booted, and it looked like it was messing with the USB system because the keyboard started repeatedly doing returns, and the mouse cursor disappeared. When I unplugged the keyboard/mouse and plugged them back in the mouse stayed off, so the machine was definitley locked up completely.

Enjoy.

---

### Post by ctt1wbw on 2006-01-17
SUCCESS!!!!  Holy crap!  I have Ubuntu on my iMac G5, albeit the live cd version.  But I have no sound...  hopefully the guys doing all the work with Dapper Drake can solve this /usr/bin/esd problem???  Hmmmm???  :D 

Now, anyone know how to shut the fan off?

---

### Post by Achille on 2006-01-17
For the fan support, you need at least kernel 2.6.14: dapper has kernel 2.6.15. It will be supported in the next version.

---

### Post by ctt1wbw on 2006-01-17
I had to quit because the fan was killing me.  I was impressed!  I just wish I had sound, you know?

---

### Post by macman4000 on 2006-01-18
First off thanks for the How-to, exparrot. I was getting the same problem as [this guy](http://ubuntuforums.org/showthread.php?t=2377) untill I read your instructions and realized I didn't tell it to use ppc64.

unfortunately after I got past that problem I ran straight into another one... 
After I type "live-powerpc64" and press enter some text scrolls by, then the screen goes white and [this](http://www.kmurph.net/ubuntu.jpg) shows up in the top left corner and the fans go up to full speed and everything locks up. What am I doing wrong?

iMac G5 (with built-in iSight)
1.9 GHz PowerPC G5
1.5 GB DDR2 SDRAM
Mac OS X 10.4.4

---

### Post by ctt1wbw on 2006-01-19
Dude!  I just booted up the Dapper Drake flight 3 live cd.  This thing rocks!  It booted so fast, I didn't even have time to pour a cup of Mountain Dew!!!  And I didn't have to rename that esd file!!!!!

---

### Post by ctt1wbw on 2006-01-19
Well damn!  I tried to change the screen resolution and it jacked everything up!

Nice job, though, guys!!!   It's FAST!!!!!!!!!

---

### Post by mattl on 2006-01-23
Same here with Dapper Flight 3. Fix X, Sound and the fan issue and I'll dump OS X for good.

---

### Post by megabenman on 2006-04-27
I tried the ctrl+alt+F6 command but it didn't do anything. And apple+alt+F6 just skips parts of the installation.

---

### Post by Torrance on 2006-04-28
Has anyone tried either of the Beta releases of Dapper on the iMac G5??

Is it possible to run the live cd with this work-around?

More importantly, are the fans being properly controlled, or still running at full speed? I tried a few of the flight cds and there was still no fan control.

Does anyone know why this bug hasn't been addressed? It seems to affect EVERY iMac G5 user, and there must be a lot of us out there, and yet not only do we not have sound, but our system won't boot past X Server loading up without disabling the sound server. Bit annoying... ](*,)

---

### Post by Torrance on 2006-04-29
So having tried the latest Beta (no. 2) I can confirm that there's no way to run the live CD on an iMac G5.... you'll have to do a proper install and then edit the esd file. The live cd goes straight into loading up X server and ESD before there is any chance to load up a terminal and rename the /usr/bin/esd file.

---

### Post by megabenman on 2006-04-30
I just tried dapper as well and it froze at a brown screen with a white cursor....
I can't understand why one guy was able to change his esd file and also boot into dapper while I can't doing the same thing....
But on the bright side dapper drake didn't make the fans spin very fast at all, well, until it froze.

---

### Post by megabenman on 2006-05-13
...I guess nobody knows why he could do it but I couldn't.

---

### Post by ctt1wbw on 2006-05-14
Well, it's been a few months since I did it, but I had to try several key combinations to make it work.  If one didn't work, I had to force my iMac off, and then reboot, trying another combination.  I can't remember which one it was, sorry.

When Dapper final comes out, I'm trying the live cd again.

---

### Post by megabenman on 2006-05-15
[QUOTE=ctt1wbw]Well, it's been a few months since I did it, but I had to try several key combinations to make it work.  If one didn't work, I had to force my iMac off, and then reboot, trying another combination.  I can't remember which one it was, sorry.

When Dapper final comes out, I'm trying the live cd again.[/QUOTE]
Ok, I'll definetly try it when I can get my live CD back. My friend stole it :mad:

---

### Post by megabenman on 2006-05-15
I reburned the live CD (I was too lazy to wait and I had the .iso saved on my harddrive) and booted from it. The results:
The same usual annoying fan issue popped up at the network settings, meaning I had to sit through some annoying fans :( At the resolution screen, instead of zipping through the different keys, I tried them Slowly. First, I tried Ctrl+Alt+F1. It did nothing. Then, I tried Ctrl+Alt+F2. It worked!!!!!
It went to a black screen with white text telling me to press enter to activate the console. I pressed enter, entered the commands, and press Ctrl+Alt+F1 to quit. I continued with the rest of the live CD, which went almost as it had last time. The fans slowed down when the ubuntu bar was about 25% (loading). And at the beige screen with the cursor in the middle, the fans went up, like usual. This is normally the freezing point. But... even with the fans at full speed, the cursor did not freeze! I could move it:mrgreen: 
It booted up fully into ubuntu (of course full speed fans which sound like an airplane are kindof annoying) and even recognized my Bluetooth apple mouse and keyboard right away! The only problems I had were that it didn't detect my wireless network (I was to lazy to look how to set up airport while still in Mac OS X) and after trying to press the "Discard" button when quiting Open Office froze the computer. But, I had fun8) 

So if you didn't hear, it's Ctrl+Alt+F2 to open the console, not Ctrl+Alt+F6.

---

### Post by ctt1wbw on 2006-05-15
What was your screen resolution?  And I guess you had no sound either?  ](*,)

---

### Post by megabenman on 2006-05-15
My screen resolution was 1024x800 (or whatever it is). I'm on a 20" iMac but I forgot to add my resolution because I'm an idiot.

I didn't try sound. I'm going to boot into it again right now and see.

---

### Post by megabenman on 2006-05-15
I booted up into 1680x1050 (my resolution) fine. Just a note, I used space to select 1680x1050 and then went into the console to type the commands. Just in case it doesn't work vice-versa (I didn't try it).

It worked fine, but this time my exploring ended when I tried to record my voice using voice recorder :(

---

### Post by ctt1wbw on 2006-05-16
That's cool.  What about fan support?  I couldn't stand the freight train sound so I had to quit the live cd.  I am looking forward to Dapper final.  Hopefully someone fixes all these problems.

---

### Post by megabenman on 2006-05-16
I can sum it up in one statement.
Fans=LOUD!


I have a dapper drake Flight 6 beta 2 CD, but it freezes as well. I can't remember if it goes to the resolution screen, letting my fix it up.

---

### Post by Torrance on 2006-05-17
I just installed Dapper Flight 7 on my iMac G5, and not only is there still no fan control, but the work-arounds to get past the frozen log-in screen no longer work. This is driving me nuts. ](*,)

---

### Post by megabenman on 2006-05-17
Personally I don't care if there is no sound support (as long as you can get past the login screen... which you can I guess with dapper) but it's the lack of fan support that is annoying. Fans that are 3 times as loud than using extreme performance needing programs on a Mac OS X really get to you. I'm sure it can't be good for the fans (though it will solve the iMac G5 overheating problem) and it's annoying as hell. PLUS, without sound, you can't drown out the fans with music....

---

### Post by Torrance on 2006-05-18
I just got an email saying that the start up freeze has been fixed. This was bug 23445: [https://launchpad.net/bugs/23445](https://launchpad.net/bugs/23445)

I'll believe it when I see it...

So, except for sound, that just leaves the fan. If this isn't going to be fixed by then, then I guess we'll all have to learn how to recompile our kernels! (I've tried this once, seemed easy enough, but I did something wrong...)

---

### Post by ACoolie on 2006-05-18
Ok, so I tried using Breezy live on my iMac G5 (w/o iSight), but the ctrl + alt + f* keys did nothing at the resolution select screen. So, I uninstalled my not working Breezy partition and tried install Dapper Flight 7. That didn't work and I have yet to try the live cd. 

But, my idea so far was to mount the Ubuntu partition I have on to my Mac, and move /bin/esd from there. My Ubuntu partition is /dev/disk0s12 (ext3, 10GB) and I am trying to mount it on /mnt/ub with this: [FONT="Courier New"]sudo mount /dev/disk0s12 /mnt/ub[/FONT] but I get an error "Incorrect super block." I have tried all other mount_* commands I can find and also have googled **a lot**. The best help I could find was to use fstab or fsck on it. But fstab isn't even on the Mac and fsck sad "Bad super block: Magic number wrong"

Any help?

---

### Post by megabenman on 2006-05-18
Fixing a full breezy install is different.
[http://ubuntuforums.org/showthread.php?t=89712&page=3](http://ubuntuforums.org/showthread.php?t=89712&page=3)

---

### Post by ACoolie on 2006-05-18
Thanks a bunch, that did the trick =D

---

### Post by iAlexander on 2006-07-01
I've tried it with the full version of Dapper and have had a similar problem. I get to yaboot up and hit enter. I wait and then the screen goes black so i reboot and type "live video=ofonly" and then it gets to the loading screen but the colous are all wierd. Everything it tries loads says ok but then the last item says failed really quickly and then the screen goes black and stays black. Any ideas?

---

