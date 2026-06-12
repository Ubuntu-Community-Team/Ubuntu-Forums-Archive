---
title: "Multiple CD Installs with WINE"
date: 2007-11-26
forum: Wine
---

### Post by pm124493 on 2007-11-26
I am trying to install COD2 that has 5 CDs using WINE v9.46. I have read many posts in Ubuntu Forums and searched WINEHQ website. Most recommend running "wine eject X:" where "X" is the CDROM drive defined in winecfg. I can do this, but when I swap the CDs Ubuntu complains another program has the drive or I do not have permission which I did when I started. Some posts recommend remounting the drive so I tried that but Ubuntu complains that another program has the drive. Needless to say I can't get past the first CD.
Some posts recommend copying the CDs to the HD and changing winecfg to point to the other images. I do not particularly like that option. I have read this issue was possibly fixed in WINE v9.49, but I do not know how to update WINE to that version when it is not in the source listings.
I am comfortable with Ubuntu, but not comfortable compiling code or using CVS. I do not like possibly breaking packages or screwing up my system dependencies. Use to happen a lot with RedHat RPMs. 
Any suggestions would be appreciated.

Ubuntu 7.10_x64
Gigabyte 965P-S3 MB, 2GB PC6400 DDR2, Nvidia 7900GT KO, 300GB SATAII HD, Plextor PX-712SA SATA DVD, INTEL Duo Core E6300 OC to 2Ghz.

---

### Post by Marrshu on 2007-11-26
I've had the same problem and I honestly don't know how to fix it. Every thread/bug post on the subject seems to die or not get a lack of responses. :\

---

### Post by fain on 2007-11-26
Try copying all your cds to the same tmp directory on you HD. overwriting duplicates, then burn them all to a DVD. It has worked for me on a few games. Some I've tried have had problems though.

---

### Post by cogadh on 2007-11-26
To update Wine, use the instructions here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Chances are, the reason you are getting the message that some other application is using the drive has to do with how you are launching the install executable. For example, if you are using the file browser to find the install executable and run it by double-clicking on it, then the file browser is accessing the drive and preventing the swap. 

When installing from a CD, it is better to use the terminal and run it like this:
```
wine /media/cdrom/setup.exe
```
That way, nothing other than the actuall installer is accessing the CD drive, which Wine can usually handle on its own. You may still have to use the "wine eject X:" occasionally, but remounts won't be a problem.

---

### Post by murt on 2007-11-27
make sure you dont run the command when youre standing 'in' the cd directory, but instead runs "wine /media/cdrom/setup.exe" from anywhere else.

---

### Post by pm124493 on 2007-11-27
I made sure no other applications where using the CDROM drive. I also made sure I was not in /media/cdrom directory and trying to run the setup.exe program. These were are discussed in previous post in Ubuntu Forums. I tried to be as thurough as possible. 

Thank you for your advice. I will keep trying. 

To FAIN: Did you just do a straight copy of each file(s) on each CD to the temp directory and then burn them onto a DVD?

---

### Post by buntunub on 2007-11-27
Just do [PHP]$wine eject[/PHP] in terminal. No need to specify drives.

---

### Post by Marrshu on 2007-11-27
cogadh: Your solution did not work. I still received the same error and was unable to pass the first disc

---

### Post by cogadh on 2007-11-27
I don't really understand why it isn't working, this problem doesn't ever occur when I run installs like that. The only way you should be getting that error message is if the terminal or file browser (or some other app) is accessing the CD-ROM drive while the install is running, which will definitely prevent the CD from being ejected. If you open the terminal and have it in your home directory, then run the command as I described, you should be able to swap CDs by just ejecting the CD normally, insert the new CD, allow it to automount, then click OK in the installer.

---

### Post by Marrshu on 2007-11-27
Even if I don't open anything else, the installer still crashes at that point.   I am unable to swap CDs normally regardless of where I run it, and the installer always hangs at this point. If a file browser is opened, it's always says the second disc is in use. **shrugs**

EDIT: I should point out it's just Call of Duty 2 I have this problem with. Other multiple CD installs (such as Far Cry) work fine.

---

### Post by pm124493 on 2007-11-28
That is interesting. I have not tried Far Cry. I will try that and see if the multiple CDs work. I am very careful to ensure I am not in the /media/cdrom directory or any other program is using the CDROM drive. Normal Windows installer operation is to eject the CD and request the next CD. I am curious why Linux (Ubuntu 7.10) does not lock the CDROM drive when the installer is running under WINE and then release it when the installer (WINE) is completed. 
I guess I do not undestand the details of LINUX enough.

Thanks for your advice.

---

### Post by happyhamster on 2007-11-28
> **pm124493 said:**
>  Normal Windows installer operation is to eject the CD and request the next CD. I am curious why Linux (Ubuntu 7.10) does not lock the CDROM drive when the installer is running under WINE and then release it when the installer (WINE) is completed. Do you mean the CoD2 installer ejects the cd itself? In that case, try re-inserting the cd, close the tray, and re-eject manually ("wine eject d:")

I had a similar problem with the game "Divine Divinity" (installer also ejected the cd itself, probably an "unsafe device removal"). Re-inserting and re-ejecting the cd manually allowed the next cd to mount properly.

Hope that helps.

---

### Post by LunarWolf on 2007-12-18
Ok I hate being the super noob here but this is my 5th topic looking for a solution to my COD2 installation problem. 

First off I'm using wine version 0.9.51 and Ubuntu 7.10 i386 gutsy gibbon . 

My computer:
Motherboard- socket 939 ECS KN1 lite motherboard utilizing nvidia's nforce4 chipset, dual channel memory supports up to 4GB ram.
CPU- AMD Athlon 64 3800 2,4 ghz nonclocked
Ram- 2 gb DDR non matched and mounted in seperate channels 
Graphics card- Evga Nvidia Geforce 7600GT 256mb DDR3 PCI-E

I installed the nonsupported proprietary nvidia video driver using Envy and installed wine using the add/remove application that came stock with my Ubuntu. I also updated my system with atuo update. Now once all that was done I thought I would try installing COD2 but I can't get past disk one. It asks to install shortcuts, to register, and even install directx but never for the remaining 5 disks. The installer just hangs up forcing me to restart my comp. So far I have followed the suggestions given here but to no success same trouble always.

---

### Post by cogadh on 2007-12-18
This is going to sound silly, but I'd be willing to bet the install is not actually hung, but the CD swap confirmation is not appearing in the front when it comes up (i.e. it is hidden behind the installer window). Are you running the install in a Wine virtual desktop? Doing so can sometimes allow confirmation dialogs to appear correctly.

---

### Post by LunarWolf on 2007-12-18
> **cogadh said:**
> This is going to sound silly, but I'd be willing to bet the install is not actually hung, but the CD swap confirmation is not appearing in the front when it comes up (i.e. it is hidden behind the installer window). Are you running the install in a Wine virtual desktop? Doing so can sometimes allow confirmation dialogs to appear correctly.

Ok well I dont know any such thing about a virtual desktop but I do know one thing that there is a graphical window that will take up the full screen in windows xp during the install of COD2 however in My current OS no such thing happens only the pop up like windows where you input a key, accept the license aggreement, and to verify your selections before install. After selecting install it gives a progress bar that once filled prompts a small pop up windo asking to install shortcuts I click yes then it asks if I wanted to register I click no, then it asks if I want directx installed. I click yeah and then nothing happens and I waited an hour with noting more showing up except the installer is still shown in a tab at the bottom of my screen all attempts to close it results in nothing happening. I cant even eject the cd without using the (wine eject) command even so doing that I can't get COD2 disk2 to load.



Well I just reinstalled Ubuntu to crush out any flaws that I had possibly introduced and I just got done installing wine using the method listed here [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) under Ubuntu 7.10

I have yet to install the proprietary driver for my nvidia card as I figure installing it last after wine might help.

will let ya know if it makes a difference.

Oh I do have a fully working windows xp on this computer too located on a seperate drive. Should I copy the entire windows "system 32" and port it over to the wine designated folder of same name?

Unrelated:
One thing that struck me funny is in the initial install of Ubuntu I never had the option to resize my partitions show up which is supposed to be the first item listed when the partitioner is opened (I found that difference of my installation on the net regarding the ubuntu installations on dual boot systems). 
all I got was "guided use entire disk for both my drives (hba1) and (hba2)." I wont even speak of manual. Its no biggy I used an entire disk that didn't contain my windows install but I rather that my os's shared a drive. :(

---

### Post by cogadh on 2007-12-18
Don't install DirectX and don't copy your system32 folder. Installing DX can break Wine's own implementation of DX and there are actually only a few DX support files that you might need anyway (its easier and safer to just copy those from Windows if/when you need them). It's not worth it to copy your system32 folder since in most cases you will only need one or two of the DLLs from it in the first place. Most applications will run fine without using any native DLLs.

Installing the proprietary Nvidia driver after Wine won't really make any difference, but it does need to be installed before you can start using Wine to run games (3D acceleration won't work without it).

---

### Post by LunarWolf on 2007-12-18
Ok thanks for clearing that up. Right now I have spent over an hour looking up proper procedure for installing the nvidia proprietary driver as last time I used Envy and from what I read envy is a risk. but going to the nvidia web site and downloading that driver pakage prooved fruitless as I cant even open it using their command listed at the site to start the install. And their web forum is a royal pain to browse as there isn't a search feature to help narrow down the list of massive proportion. Its like finding a needle in a rail yard packed with train cars worth of bs to look through. I refuse to use the glx drivers as they wont support 3d rendering. So wish me happy hunting.:lolflag:

---

### Post by cogadh on 2007-12-18
Huh? The "nvidia-glx" package in the repositories is exactly the same as the drivers that you can get from the Nvidia website (possibly a month or two older), it's just been repackaged into a Synaptic friendly DEB package. It definitely supports 3D acceleration, I'm using it right now and it works perfectly. 

I honestly wouldn't waste my time with the install package from the Nvidia website. While the driver version might be a little newer than what is in the repository, the hassle involved in installing it, plus the fact that you will have to manually reinstall it every time there is a kernel update doesn't make it worth the effort.

---

### Post by LunarWolf on 2007-12-18
Well I resorted to using ENVY again and in stalled the drivers using that. Once done doing that I opened the wine configure utility and I checked the box to emulate a virtual desktop then I started the setup.exe of cod2 disk 1 using the terminal. Needless to say I ran into the same problem only the virtual destop didnt show the normal background used as if in window xp (all black with a slide show of in game graphic screen shots) it just turned a light blue and remained that way. the pop up menus of which to make selections remained fine and I optioned not to register nor to install directx. but after clicking no to directx it just hung there the window still open and doing nothing. At about a half hour of waiting I gave up and found that I could close out the virtual window without hassle. I mainly wanted to give linux a try to see if I could hang with it, but obviously I'm not ready for it because i'm so spoiled with windows ease of use. I thought seen how I started out using dos commands that I could possibly get the hang of the linux command prompt or terminal as its known as to linux folk. I hope to try it again after doing more research into what makes a successful linux experience, but until then I'm crawling back to windows with my tail between my legs and licking my wounds while dishing out wounds to others in COD4 modern warfare.

I thank you kindly for having supplied me with helpful knowledge that still helped even if I didnt get the desired results I was looking for. Perhaps I should have used an older version of wine or maybe see about getting proper drivers for my nforce4 chipset and motheroard or should have used the 64 bit ubuntu and wine seen that I am using and AMD athlon 64 cpu. I only chose the i86 version as it was the only one supported and my cpu can still run 32bit perfectly fine as it does in my XP windows.

---

### Post by doorknob60 on 2007-12-19
If possible, install it in Windows and then copy it over to the wine drive, that worked PERFECT for me when I had lots of problems installing under wine.

---

### Post by LunarWolf on 2007-12-20
I had sent this in a private message to Cogadth but figured he is too busy to reply so I thought bring it here.

I seem to be a glutton for punishment and have done a clean install of ubuntu, nvidia drivers, wine and system updates using nothing but the pure Ubuntu synaptec repositories. Following your procedure for an installation of cod2 I have actually gotten further with wine 0.9.46 than the newer 0.9.51... Anyways when it asks for cd2 I eject using (wine eject) then when I place disk 2 in the cdrom the File browser wishes to open and view it, keep in mind the wine is still running in the background with the installer and what that pesky viewer says is that I don't have rights to view the contents of the cd so then it locks the damn drive up and removes it from my system places. I was wondering if there is a way that I can disable that activity from happening because once it locks my drive the needed cd cant be read from the installer thus not completing the install as desired.

Any light on this will be appreciated.

I did copy the entire cod2 folder from my windows xp installation and it does work well enough but I consider that cheating in that if I didnt have XP I would still be at ground zero so thus why I am trying to get a fool proof method of installing this game so that I may finally abandon the microsoft's windows dependancy once and for all.

---

### Post by stump138 on 2007-12-20
I have had a few installs of software have the problem with cd swapping.  I have a work around that works in some cases:

1. when prompted for the new cd, open a terminal and manually unmount the current cd (even if it was already ejected, this ensures it was un-mounted).  Generally looks something like this:
```
sudo umount /media/cdrom0
```

2.  Insert the next cd and then mount it in a terminal.  You should be able to continue the installation via the prompt for the next cd. 

This seems to work across several programs that I have to install at work.  (we use ubuntu as one of our primary OS's)

---

### Post by LunarWolf on 2007-12-23
Well I am still at it having tried everything to initiate a clean install of COD 2 and the best I could do was to get the little window to ask for the second disk. I am going to show what things I tried during my last session and as always the same thing look for yourself and see.

This second terminal I opened at the time of asking for disk 2 following the instruction to manually eject and unmount the drive then remounting the second disk with no success trying everything to get the cd mounted before clicking to proceed with install. I even tried forcing wine to mount the damn drive but the os is blocking it as it wont allow me to eject it nor read it, hell it dont even show up in file browser as if the system uninstalled the damn drive. Though at the time of inserting disk 2 the auto mount brings up a window saying I havent perission to view the contents of this drive with a blank viewer window behind. I have tried both ways of leaving that window alone or closing it in my experiments to mount disk 2 for install neither had promising effects.

lunar@lunar-desktop:~$ wine eject

lunar@lunar-desktop:~$ sudo umount /media/cdrom

umount: /media/cdrom: not mounted

lunar@lunar-desktop:~$ sudo mount /media/cdrom0

mount: block device /dev/hdc is write-protected, mounting read-only

mount: /dev/hdc already mounted or /media/cdrom0 busy

mount: according to mtab, /dev/hdc is already mounted on /media/cdrom0

lunar@lunar-desktop:~$ wine mount /media/cdrom0

wine: could not load L"c:\\windows\\system32\\mount.exe": Module not found

lunar@lunar-desktop:~$ wine mount /media/cdrom

wine: could not load L"c:\\windows\\system32\\mount.exe": Module not found

lunar@lunar-desktop:~$ sudo -s

root@lunar-desktop:~# wine mount /media/cdrom

wine: could not load L"c:\\windows\\system32\\mount.exe": Module not found

root@lunar-desktop:~#

Am I using the commands right? (some I made up like trying to get wine to mount the drive are improvised for instance *wine mount /media/cdrom0*) Im grabbing for air here... If I can't get my most favorite of all my games installed properly why bother with any other title when everything in the boards and in WineHQ are saying installations with this title are easy with no documentation of what I am experiencing at all except this thread.

---

### Post by cogadh on 2007-12-23
You went off track with the very first command. You need to specify which drive Wine is supposed to eject, like this:
```
wine eject D:
```
or you can just tell it to eject all drives:
```
wine eject -a
```
but just typing "wine eject" doesn't actually do anything.

Also, your mount commands are missing some info. You need to specify what device you are mounting and where you want to mount it:
```
sudo mount /dev/hdc /media/cdrom0
```

Lastly, there is no such thing as a "wine mount" command.

---

### Post by happyhamster on 2007-12-23
> **LunarWolf said:**
> 
lunar@lunar-desktop:~$ wine eject

lunar@lunar-desktop:~$ sudo umount /media/cdrom
Try "umounting" /media/cdrom0 not /media/cdrom.

> 
lunar@lunar-desktop:~$ wine mount /media/cdrom0

This won't work, because "mount" is not a windows executable.

> 
lunar@lunar-desktop:~$ sudo -s
Be very careful what you do in a root-terminal. There are lots of things you *don't* want to run as root (like wine). Just use "sudo"  instead (it can be annoying, but it's much safer)

> 
Am I using the commands right? (some I made up like trying to get wine to mount the drive are improvised for instance *wine mount /media/cdrom0*) Im grabbing for air here... If I can't get my most favorite of all my games installed properly why bother with any other title when everything in the boards and in WineHQ are saying installations with this title are easy with no documentation of what I am experiencing at all except this thread.
These kinds of install-troubles can be very version specific. Others might have tried slightly different COD2 cd's (international version versus US edition, bundled with other games, stuff like that).

Keep trying, don't despair yet :)

---

### Post by LunarWolf on 2007-12-24
Um isnt there any way I can disable the auto mount from the File browers snooping at the cd before wine does as no one has answered that part. As soon as i put the cd in the drive the os reads it and flags it then removes the device from being used even or to eject the cd causing the discrepency (either in terminal or pushing the eject button on the drive itself). I find that the most bothersome more so than anything for if I can stop the OS from trying to auto mount the cd I think I could stand a chance without it cutting me short all the time. In windows I can simply go to the hardware itself in *my computer* and turn off autorun. Is there anything I can type in terminal that will produce the same effect or in a gui that I havent checked yet as its not established in the properties of the hardware. I believe freedom to read from the cdrom no matter what the content is essential for a pleasing experience and to be honest ubuntu is not giving me a great impression at this moment, but I wont give up yet as I see great potential here. If not ubuntu what of the vast array of linux distros would possibly suit me better?

If you're wondering why am I trying to switch well thats easy I added a single stick of 1gb ram to my computer and the damn windows xp said I had a exceded their limit of hardware changes allowed and required me to reactivate. The notion of having to call the microsoft hotline to reactivate my copy of windows because of a ram upgrade blew it for me. I thought from reading the XP pamphlet/manual that I could modify my existing system like video card, ram, hard drives and such an infinite aount of times as long as I used the same mobo and cpu I would be fine. Its sad and pathetic of microsoft.  

Oh my, back to topic my bad. 

The wine eject works perfectly without having to specify D: or E: as it ejects the first cd fine I only added the # sudo umount media/cdrom command to be sure nothing posssibly remained.

Still trying here oh and Merry Christmas!

---

### Post by cogadh on 2007-12-24
That's where your problem occurred, you are over complicating things a bit. Just use the "wine eject" command, don't use the unmount command as well (BTW - I'm not sure what you are doing differently, but every time I enter just "wine eject" without specifying a drive I get a "no CD drive found" message). Using the unmount command in addition to the wine eject command could royally screw things up. Just enter "wine eject", swap the CDs, either let it automount or manually mount it (if you still have the automount running and it opens a browser window, make sure you close it *after* the CD finishes mounting), then click "OK" or "Next" or whatever the install dialog in Wine is asking for next.

As for stopping the automatic mounting of CDs, go to System > Preferences > Removable Drives and Media and change whatever you want.

---

### Post by Immoral on 2007-12-27
Hi all, as i already wrote to Cogadh i found solution! Yeah!!!!!!

But, then i decided that i probably will need some advice, because i start using ubuntu 7.10 yesterday :P and registered here also, so I'll post solution by myself.

I installed WoW with next command: wine "D:\Installer.exe" 

And you don't need to write "wine eject" u can eject cd manually.

Enjoy! Hope it helps you also! \\:D/

---

### Post by killasooty on 2007-12-31
HI ...

   I'm another noob - 2 weeks with Kubuntu now  :-)

  I've experienced all the same problems described in this thread - By following the advice from cogadh I have managed to get some games installed.

   (This is a big issue for me - if I can play  my collection of  Windows games on Kubuntu - then I don't NEED windows & the associated hassle any more!!)

THis procedure worked for me (when I was ready to consign Wine to the trashcan otherwise)

insert 1st CD, answer the Automount dialog ("open in new window")
This launches Dolphin - once the CD is mounted & I can see the files on it  - note the name of the setup file (or autorun.exe in some cases) - then kill the Dolphin window.

In the terminal, type 

***/media/cdrom0/Setup.Exe  ***

(by launching setup from a terminal you get to see any error messages that might come up - launched from dolphin I don't know if you can  retrieve those messages)

When the installation dialog prompts for CD 2 go to the terminal window & type

[I][B]wine eject d:
[/B][/I]
Disk pops out - insert disk 2

Dolphin pops up again - "open in new window" again - Dolphin mounts the disk - kill the dolphin window

Click the Ok button in the installer dialog - installation continues.

I know this may be a bit laborious - but it should avoid frustration to us windows escapees ...  wine eject helps, but it ain't the whole fix & as a linux virgin i was having trouble mounting the next cd by terminal commands    :confused:

anyway - i like wine again now so thanks for the help

---

### Post by b666 on 2008-12-29
Thanks killasooty, that worked for me!

Thanks to everyone who gave advice in the thread. I had the same prob trying to install a game. this is my first post, but i've used these forums so much to fix probs, or try to understand things better. i just want to say thanks to the guys that take the time to make things easier for us that don't get the terminal stuff. i only just barely got the gist of this thread, but i tried what killasooty had said worked - and bingo! it worked! 

lol just realised killasooty's post is almost exactly a year old. :popcorn:

---

