---
title: "problems with X. . ."
date: 2005-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by acidlacedpenguin on 2005-12-30
err, I just installed breezy badger and x won't start. . .

its a problem with my display settings and I'm pretty sure to fix it I just need to tell it the right irq for my pci-e videocard (BFG6600GToc)

I just don't know exactly how to change the settings, so I'd really appreciate it if someone could help me out:). . .

---

### Post by Atreju on 2005-12-31
I'm not sure you need to provide the irq setting manualy... I'm not even sure you can do that with X's driver (even with nvidia's)

why not take a look at /var/log/Xorg.0.log and send us a copy ? also, how does it crashes exacly ? which driver are you using ?

---

### Post by acidlacedpenguin on 2005-12-31
[I]
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 [email]root@crested.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF] 
Current Operating System: Linux SapphireSunrise 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 x86_64
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-amd64-generic (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:27:39 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 31 17:18:08 2005
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	At least one Device section is required.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[/I]

is the log
and the error just says x server wasn't configured correctly. . . the installer said to enter the offset, or leave it as default if you don't know, I've tried it with default and the number that I thought my display adapter was (the nvidia display it told me when I used lspci) both times it was the same problem, like it didn't actually write xorg.conf file.

---

### Post by Andrew Olson on 2006-01-02
ive been getting an identical message on my new install same version same error, im using an ati x700 pci x card. i tried updating the driver but was unfortunatly unable to recieve the driver package. 

keep in my with your replies im a complete newb to linux though ive tried several installs over the last 10 years or so, and have never had a fully working linux system , mainly because of hardware issues that i couldnt resolve, i had hoped the newer versions might provide better support, and cant understand why linux doesnt have a "windows like " default vga driver so you could at least get to the gui without crashing. well crash is a bit harsh,.lol  it does allow you to go into comand line. another thing i dont understand why the boot up screen shows color graphics just fine when loading. why dont they just allow you the same drivers they use for that as a basic default.. least alow us less linux literate individuals something better to look at than a old dos like looking  monochrome display. 


i was given :  sudo apt-get install linux-restricted-modules-2.6.12.6 xorg-driver-fglrx fglrx-control  ... as a line to download a better driver. which didnt work.  couldnt find package....... 
dont know where to go from here. and am considering a different version. just dont like to waste days of pc time downloading any number of installations that more than likely will also have there own issues as well.

mine also said it wasnt configured corectly , but i cant find how to do that as the only config tool i found was a screen size selector with an obsolete looking screen and menu.

as a ps i also went to wiki and that was pretty much a waste of time.  there were no similar errors on that site, this is the first post ive seen with the exact problem as mine.

---

### Post by Atreju on 2006-01-02
_To Andrew Olson : _
*sudo apt-get install linux-restricted-modules-2.6.12.6 xorg-driver-fglrx fglrx-control*

This line is just right, if it doesn't find the packages, it's because you need to add a new line in your /etc/apt/sources.list file :
**deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy restricted**

and also for security updates of those packages :
**deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security restricted**

then run **sudo apt-get update**,and give another go to the "apt-get install" line from before.

_To acidlacedpenguin:_
I also think you should reconfigure your Xorg by generating a new xorg.conf file. An easy way would be :
**sudo dpkg-reconfigure xserver-xorg**

You will go through a series of questions regarding you configuration and it will generate a new xorg file. ;-)

Give me some feedback on how it worked out for you two !

---

### Post by Andrew Olson on 2006-01-02
[QUOTE=Atreju]_To Andrew Olson : _
*sudo apt-get install linux-restricted-modules-2.6.12.6 xorg-driver-fglrx fglrx-control*

This line is just right, if it doesn't find the packages, it's because you need to add a new line in your /etc/apt/sources.list file :
**deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy restricted**

and also for security updates of those packages :
**deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security restricted**

then run **sudo apt-get update**,and give another go to the "apt-get install" line from before.

_To acidlacedpenguin:_
I also think you should reconfigure your Xorg by generating a new xorg.conf file. An easy way would be :
**sudo dpkg-reconfigure xserver-xorg**

You will go through a series of questions regarding you configuration and it will generate a new xorg file. ;-)

Give me some feedback on how it worked out for you two ![/QUOTE]

didnt really understand what your getting at when you say to add a line to that file. i dont understand linux commands and how to navigate in a linux comand prompt enviroment.
if i read you right you mean for me to type in :deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy restricted ... and then : deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security restricted  ...  then proceed with the line : sudo apt-get install... 
all done i assume at the user command prompt.

thanks , ill let you know how it worked

---

### Post by Andrew Olson on 2006-01-02
i tried adding the lines you suggested and got permission denied. i also ran :sudo dpkg-reconfigure xserver-xorg
 and went thru the reconfig menu. only to end up with it still not working and i tried several times and used different options to no avail. 

thanks though , i guess it was worth a try.

---

### Post by klett on 2006-01-02
Hi,
I'm not an English speaker, so please, forgive my mistakes. I'm a newbie so I'm not sure if this may help.  I had quite the same problem a few days ago. I did exactly what Atreju has suggested. The only difference was that instead of running

**dpkg-reconfigure xserver-xorg**

which didn't worked for me I ran

**fglrxconfig**

and accepted the default settings (the only one I changes was the keyboard model. I selected the one that dpkg-reconfigure had detected). After that, I ran
**startx**
and I shipped into the desktop. Then I rebooted and got an error message which said "Your session lasted less than 10 seconds" or something like that. The problem was that running startx had changed the owner of the /home/your_user_name/.ICEauthority file. I rebooted, logged in in text-mode and deleted that file:

[B]rm /home/your_user_name/.ICEauthority
[/B]
Then, I rebooted again and the system created a new .ICEauthority file with the correct owner.

The command used to reboot was:
**shutdown -r now**

and all of this assumes that you have ran

**sudo -s**

at the beginning of the whole process to gain root privileges. If you don't do this at the beginning, you'll have to write sudo before any command which requires root privileges.

---

### Post by Andrew Olson on 2006-01-02
thanks klett, mine didnt recognise the fglrxconfig commond though. you sure its entered in that manner?

---

### Post by Atreju on 2006-01-03
Hi there,

ok, if the commands turn out to be a bit to hard, I'll post another walkthrough doing it mostly with the graphical interface.

Regarding fglrxconfig, if you are an owner of a recent ATI graphic card, it is the recommended method (it will set the ATI drivers specific options right. Using the default is generaly a good idea)

See you tonight ! ;-)

---

### Post by klett on 2006-01-03
Hi,

Yes, I've just checked that this command is recognized. Are you sure that fglrx is really installed?. Also, I've ran

**sudo apt-cache search fglrx **

and this has been the result:

[I]root@ubuntu:~# apt-cache search fglrx
xserver-xorg-driver-ati - X.Org X server -- ATI driver
linux-restricted-modules-2.6.12-9-amd64-generic - Non-free Linux 2.6.12 modules on x86_64 generic
linux-restricted-modules-2.6.12-9-amd64-k8 - Non-free Linux 2.6.12 modules on AMD K8
linux-restricted-modules-2.6.12-9-amd64-k8-smp - Non-free Linux 2.6.12 modules on AMD K8 SMP
linux-restricted-modules-2.6.12-9-amd64-xeon - Non-free Linux 2.6.12 modules on Intel x86_64
fglrx-control - Control panel for the ATI graphics accelerators
linux-restricted-modules-2.6.12-10-amd64-generic - Non-free Linux 2.6.12 modules on x86_64 generic
linux-restricted-modules-2.6.12-10-amd64-k8 - Non-free Linux 2.6.12 modules on AMD K8
linux-restricted-modules-2.6.12-10-amd64-k8-smp - Non-free Linux 2.6.12 modules on AMD K8 SMP
linux-restricted-modules-2.6.12-10-amd64-xeon - Non-free Linux 2.6.12 modules on Intel x86_64
xorg-driver-fglrx - Video driver for ATI graphics accelerators
xorg-driver-fglrx-dev - Video driver for ATI graphics accelerators (devel files)[/I]

May be the problem is that Atreju said *"linux-restricted-modules-2.6.12.6" *and it should have been *"linux-restricted-modules-2.6.12-9-amd64-generic"*, if you haven't upgraded your kernel to 2.6.12-10 (I don't think you have done it, but check it at booting time)
Try repeating

[B]sudo -s

apt-get install linux-restricted-modules-2.6.12-9-amd64-generic xorg-driver-fglrx fglrx-control

fglrxconfig[/B]

etc

Good luck! :smile:

---

### Post by Andrew Olson on 2006-01-03
[QUOTE=Atreju]Hi there,

ok, if the commands turn out to be a bit to hard, I'll post another walkthrough doing it mostly with the graphical interface.

Regarding fglrxconfig, if you are an owner of a recent ATI graphic card, it is the recommended method (it will set the ATI drivers specific options right. Using the default is generaly a good idea)

See you tonight ! ;-)[/QUOTE]
 ok well yea i have a athlon64 3200, ATI X700 pro pci express card. asus an8-e mainboard and 2 gigs of ram. as far as commands inside the gui , the gui has yet to launch. i can only get the command line. i guess i need a linux for dummies book or something  :D 
thanks.

---

### Post by Andrew Olson on 2006-01-03
ooops multipost   laaagggg

---

### Post by Andrew Olson on 2006-01-03
oops multipost

---

### Post by Andrew Olson on 2006-01-03
i used the -2.6.12-9-amd....  and was able to get the fglrxconfigure to work, thanks. 
it upped the anti to fatal errors regarding input devices. 
X10 : fatal IO error 104 on xserver bla bla bla. and
xauth : error in locking Authority file ... more bla
 seems one i recognised from one screen was a failure to recognise the mouse at /dev/mouse
 i entered that as a mouse location lacking any knowledge to do any different, i assumed it would register the mouse drivers into that file and link it where needed. there were a couple other dev errors but was all geek to me.

---

### Post by handy on 2006-01-03
The variability of the level of difficulty for the Ubuntu (Linux) installs amazes me... :confused: 

Hang in their Andrew Olsen, it is worth it.  I too had been looking at various Linux distro's for about 10 years, most often thwarted by hardware config' problems, which caused me to have the "Linux is still not ready for human consumption attitude", you know the one, it says "I'll try again next year..."

With the support available in this remarkable community, you ***_WILL_*** succeed, if you hang in there.  :KS 

handy

---

### Post by Andrew Olson on 2006-01-04
thanks Handy. 

yea I know the one.  lol

im a little encouraged that the problems might just be in the settings, though it could be some hardware i have might not be supported by this distro. or any for all I know at the moment. 
i do have a dvd of fedora fc4 64 and mandriva 64 bit dvd on the way as well. so if ubuntu isnt ironed out by the time i recieve the other distros im probubly going to abandon ubuntu. 
i do appreciate the help on this forum. but i do realize some distros just plain balk at some hardware issues. and dont seem to have any resolution despite best efforts.

---

### Post by Andrew Olson on 2006-01-05
thanks all for the help. ;)  seems the installation of the new drivers and fglrxconfig did in fact work. though i had to sacrifice my new mouse a logitec mx lazer and replaced it with my older microsoft intellipoint/ go figure :???: :???: :???: 

luckilly its easy to switch back to the lazer when i boot xp 64. though i could return it still as i have the reciept and i got it for christmas. i hesitate to do this as it is such an awsome gaming mouse and the actual config for it may work, 

im not sure it was the mouse as yet. i lean to it because the error message pointed to the mouse. but this last succesful config was completed with a reboot before attempting startx. and it may of been the key to the config working this time.  next time ill try it with the mx lazer to make sure. it doesnt actually need special drivers to work as a standard ps2/usb mouse after all. 

anyway after what seemed to be a loosing battle it is indeed up and running as im writing this from my 64 bit ubuntu pc right now.   woohooo!!!  lol

tc all,. be seeing you soon as more issues crop up  lol  lets hope not real often though;)

---

### Post by handy on 2006-01-05
Great stuff Andrew, I'm glad you managed to be able to stay with Ubuntu!  :KS 

I love seeing problems become history, though I'm not sure what I would do if life didn't pose any??  :rolleyes:  

Laying on a beach doing nothing doesn't remain stimulating/satisfying for too long.  & of course there is all that sand :(  

handy

---

### Post by Andrew Olson on 2006-01-07
thanks. been learning the gui, not as bad as command line. but it has its quirks lol.'
 and it turns out the lazer mouse does work.

---

### Post by Atreju on 2006-01-15
Hey Andrew,

Sorry, no posts from me for a while... I was on holiday :-)

I'm happy to see that you're staying with us ! and sorry about the idea of a gui walkthrough to help you get your gui working.... that was kind of like some microsoft support : "your mouse is not working ? ok, click on the button.... :???: "

hehe

Marco.

---

### Post by korakde on 2006-02-07
Have you tried using a VESA driver for your graphics card. It works. It did for me when my ATI driver didnt work and I was stuck with X not loading just like you.

---

