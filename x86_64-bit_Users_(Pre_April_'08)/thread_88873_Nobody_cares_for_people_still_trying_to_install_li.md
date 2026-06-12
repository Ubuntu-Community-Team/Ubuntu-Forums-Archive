---
title: "Nobody cares for people still trying to install linux!!!"
date: 2005-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by youngdaniel on 2005-11-11
Sorry to sound like a moaning fool, but these forums seem to obnly get replies to people who have got ubuntu installed fine and dandy!! theyre are so many people out theyre who struggle to install it ok.

This is my 4th attempt at getting into linux, and im still having no luck!! and no one seems to be trying to help!! Previoulsly tired red hat on a old old laptop, failed!! then red hat on a top spec new pc, failed!! then ubuntu on same top spec pc, failed!! now ubuntu on an apple powerbook g3, 400mhz. and this is the closest i have got so far, a perfect install then go to login and that goes fine, get to a brown screen and working mouse and even the welcome jingle and then nothing!! why why why??? so frustrating!!!

Please help me!! I am getting desperate!!

---

### Post by Mr. Electric Wizard on 2005-11-11
Dude, quit moaning and tell us why it is failing...
What errors are you getting.
It's really shouldn't be that hard to install.  Maybe the PC you're trying to install Linux on has some bad hardware or something?

---

### Post by youngdaniel on 2005-11-11
i do apoligise if i am sounding pathetic, i just so want to get into linux!!

okay, i have ditched the idea of trying to get it on my pc, due to problems with my ati card and my sony tft, it hated it!!!

so i have aquired a apple powerbook G3, 400mhz "Firewire" Model. 192mb of Ram, 8mb Video and DVD Drive. I think the onboard video card is ati based but not too sure.

Ubuntu 5.10 Installed perfectly fine. On first attempt to login it took the details fine and proceeded to a brown screen, with an active mouse and even played the jingle to annoy me even more!! I have read so many dam posts talking about changing stuff in Xorg.conf but whatever i have tried has failed to help!! 

Alot of the other posts talk about the nvidia issue is why the GNOME is not installing properly.

Ideas???

---

### Post by fuscia on 2005-11-11
edit: redundant

---

### Post by apjone on 2005-11-11
[QUOTE=youngdaniel]Sorry to sound like a moaning fool, but these forums seem to obnly get replies to people who have got ubuntu installed fine and dandy!! theyre are so many people out theyre who struggle to install it ok.

This is my 4th attempt at getting into linux, and im still having no luck!! and no one seems to be trying to help!! Previoulsly tired red hat on a old old laptop, failed!! then red hat on a top spec new pc, failed!! then ubuntu on same top spec pc, failed!! now ubuntu on an apple powerbook g3, 400mhz. and this is the closest i have got so far, a perfect install then go to login and that goes fine, get to a brown screen and working mouse and even the welcome jingle and then nothing!! why why why??? so frustrating!!!

Please help me!! I am getting desperate!![/QUOTE]
Check the hardware support for the version you are trying to install. 
try ctrl+alt+F1 to get to a terminal ,
login then look at /var/log/messages and syslog to see what it says

---

### Post by Mr. Electric Wizard on 2005-11-11
If you have an ATI card, then that might be your biggest problem.
Although, there are many threads on this forum related to getting ATI cards working under Ubuntu.

---

### Post by youngdaniel on 2005-11-11
havign all sorts of weird problems now, please bare with me!!
I can type my login name, but when it comes to password, the keyboard wont type!! I hae run this log before, so i dont know what is going on!!!
 on previous looks at the log, nothing is highlighed with error, a few come up with warning bu they are to do with fonts!

give me a few minutes to get this log back!! sorry

---

### Post by Mr. Electric Wizard on 2005-11-11
Are we talking USB, or PS/2 Keyboard?

---

### Post by XDevHald on 2005-11-11
Hi Youngdaniel,

I understand that you're unable to get your information as needed due to lack of support. If you could please provide us your system specs and we can further assist you with your problem(s).

NVidia Drive, keyboard type, etc.

Thank You

---

### Post by youngdaniel on 2005-11-11
thanks for the support guys i do appreciate this!!

Right let me clear this up, when it comes to pc i am up there with the pros, when it comes to mac and linux, I am a amateur!!!

So the system

apple powerbook g3 400mhz (firewire model)
1MB Cache
192mb ram
8mb Video (the initial install indentified the card as an ATI, thats all i know)
DVD drive

the problem

Installed perfectly fine, get to login screen, type username and password, accepts it fine, looks like it proceeds to the GNOME, with a brown screen and a working mouse, and get the welcome sound, but after that no taskbar, icons or anything.

So from what i can gather, i have an issue with GNOME or my video card?

---

### Post by mcduck on 2005-11-11
[QUOTE=youngdaniel]havign all sorts of weird problems now, please bare with me!!
I can type my login name, but when it comes to password, the keyboard wont type!![/QUOTE]
If that happens in text mode, no problem there, your keyboard works fine. For security reasons no characters are displayed when you write your password..

---

### Post by youngdaniel on 2005-11-11
okie dokie i am in a terminal (danlinux tty1) and ready to type

so please let me know what you would like me to run?

---

### Post by youngdaniel on 2005-11-11
[HTML]http://www.everymac.com/systems/apple/powerbook_g3/stats/powerbook_g3_400_fw.html[/HTML]

Thats the full spec of my machine

---

### Post by Mr. Electric Wizard on 2005-11-11
Have you tried a dmesg at this point?

---

### Post by fuscia on 2005-11-11
just to make sure - you did use the PPC installation, yes?

---

### Post by youngdaniel on 2005-11-11
i apoligise if i sound stupid, but what would you like me to do with that?? 
I do indeed get frustrated with people who dont know alot! but i got to start somewhere!!!

I typed it in and it has listed a great amount of lines of data? how can i scroll back up the lines? Am i looking for anything in particular?

---

### Post by youngdaniel on 2005-11-11
lol, yes, now that would be stupid but yes i used 

"ubuntu-5.10-install-powerpc.iso"

---

### Post by Mr. Electric Wizard on 2005-11-11
[QUOTE=youngdaniel]i apoligise if i sound stupid, but what would you like me to do with that?? 
I do indeed get frustrated with people who dont know alot! but i got to start somewhere!!!

I typed it in and it has listed a great amount of lines of data? how can i scroll back up the lines? Am i looking for anything in particular?[/QUOTE]

Well, what you'll be looking for is at the end of all the _data_ you should see some type of error message.

---

### Post by patrick295767 on 2005-11-11
[QUOTE=youngdaniel]Sorry to sound like a moaning fool, but these forums seem to obnly get replies to people who have got ubuntu installed fine and dandy!! theyre are so many people out theyre who struggle to install it ok.

This is my 4th attempt at getting into linux, and im still having no luck!! and no one seems to be trying to help!! Previoulsly tired red hat on a old old laptop, failed!! then red hat on a top spec new pc, failed!! then ubuntu on same top spec pc, failed!! now ubuntu on an apple powerbook g3, 400mhz. and this is the closest i have got so far, a perfect install then go to login and that goes fine, get to a brown screen and working mouse and even the welcome jingle and then nothing!! why why why??? so frustrating!!!

Please help me!! I am getting desperate!![/QUOTE]
  
I was in ur case at the beginning !!
I spent soo many nights trying soo easy things & thinking that it was impossible.
I got desesperated too !! It took me 2 months of a lot of patience with the little one : linux.
 
Because of same feeelings that u can have now & for the moment, that's the reason why I made a progression threat about linux ... everything I know is in it and even single stuffs appearing stupid sometimes as problem I encountered are in it !!
  
I wish you patience and u'll be very happy that u changed to linux
I am very happy of linux and No Return To Any Other Os than Linux Now !!
  I am still amazed by the stability, security, impressing speed, potentiallity of linux. For instance, not a single DVD burning failed (k3b progr) from network, even doing plenty stuffs at same time !! Imagine !
  
Good luck !!
My progress thread is as follows:
 [http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)
ALso, dont hesitate to install gaim and start chatting with me or people to ask help in Live !!!

Pat'

---

### Post by youngdaniel on 2005-11-11
i would like to tell you there was an error message there, but there isnt.

also ran

cat /var/log/Xorg.0.log | less 

and got no (EE) messages at all, got a few (WW)

(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfontconf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").

Other than that it tells me that 

Device "ATI Technologies, Inc, Rage Mobility M3 (AGP)"

---

### Post by lerrup on 2005-11-11
Have you tried searching in or asking about this in the PPC/apple part of the forums?

They might well be able to help.

---

### Post by youngdaniel on 2005-11-11
come on people?? I hate bugging you all, and repeat posting, but i am getting no where!!! 

I dont want to give up!!!

---

### Post by youngdaniel on 2005-11-11
yeh i posted in there for the last week! and get no ideas back, so thought i would try in here!! i guess i am not destined for ubuntu!!!

---

### Post by Kyral on 2005-11-11
[quote=lerrup]Have you tried searching in or asking about this in the PPC/apple part of the forums?



They might well be able to help.[/quote]

To youngdaniel: He mentioned the PPC Forum. I help out whenever I can dude, but I know jacksquat about PPC stuff, so if I tried I would most likely end up HURTING you.

---

### Post by peanut butter on 2005-11-11
terminal dosen't show passwords asthey are being typed it dosen't even show ***** s. that is just how it is

---

### Post by youngdaniel on 2005-11-11
ok guys, thanks for reading this, dont wana go off the main issue!! the main issue is that i have a powerbook with a non-working GNOME!!! if there are any PPC experts out there!! please show me them!!! 
It has to come down to the ATI card as it seems to be a similar issue to that of the nvidia issue that people have been having!!
why cant it be easier than this!!! if it was the whole world would on linux!!! and its not as if i dont know much about computers!!! I do!! just not apple and linux!!!

---

### Post by Kyral on 2005-11-11
Calm down for one.

Try this one on for size. Go to a terminal (either hit CTRL+ALT+F1 or open one in GNOME) and execute this command

```
sudo dpkg-reconfigure ubuntu-desktop
```

And then restart X with

```
sudo /etc/init.d/gdm restart
```

See if that fixes anything

---

### Post by Kyral on 2005-11-11
Mods why was this put in the Backyard?! I request this be moved to either the PPC Forum or back to the ABT Forum

EDIT: Thank you :D

---

### Post by dbott67 on 2005-11-11
Have you tried logging in via "failsafe gnome"?  If so, what happens?

Also, when you get to the terminal, is your network interface working (i.e. can you get on the internet?)  If so, here are a few things to try:

1. Update all your gnome packages
2. try using apt-get to download xfce or kde --- and see if you can login to the desktop (helps determine whether it's a gnome issue or video card, etc.)

-Dave

---

### Post by youngdaniel on 2005-11-11
Hi guys, thanks for your continued help!! i am determined to crack it!!

sudo dpkg-reconfigure ubuntu-desktop
unfortunately this didn't do anything, still exactly the same outcome!

Cant update via the internet, as i have not set up any of the networking for the computer yet. and this is not a priority at the moment. Should i have to update GNOME packages if i only downloaded the iso at the start of this week??

one point, how much video mem does ubuntu need to run GNOME, this powerbook only has 8mb? i dont get how it has nearly got there, but at the last hurdle, failed to load the taskbar and icons??

has anyone successfully installed ubuntu on a powerbook g3 of any type??

---

### Post by dbott67 on 2005-11-11
Can you login via 'failsafe gnome' mode?

[QUOTE=youngdaniel]Cant update via the internet, as i have not set up any of the networking for the computer yet. and this is not a priority at the moment. [/QUOTE]
If you can configure it, it will give you the capabilities to download other Desktop Environments or Window Managers (KDE, XFCE, IceWM, fluxbox/blackbox, etc.), which may help determine if the problem is with Gnome or some driver/hardware, etc.  The old method of elimination...

[QUOTE=youngdaniel]Should i have to update GNOME packages if i only downloaded the iso at the start of this week??[/QUOTE]
I may be mistaken, but I believe the .iso files are 'frozen' once the release goes live.  The developers do not integrate any new updates/patches into the .iso's (i.e. an .iso downloaded 5 months apart would be exactly the same).  So, yes, you *may* have to update certain packages that have been updated since release.

[QUOTE=youngdaniel]one point, how much video mem does ubuntu need to run GNOME, this powerbook only has 8mb?[/quote]
I'm running Breezy on a Toshiba Tecra Laptop P2-300 with 256 MB RAM and a NeoMagic video card (2.5 MB according to specs).

[QUOTE=youngdaniel]i dont get how it has nearly got there, but at the last hurdle, failed to load the taskbar and icons??[/QUOTE]
It could be corrupted gnome configuration files (but I would think that you would actually have to login first before they could get corrupted.  You could try renaming the hidden .gnome & .gnome2 directories in your home directory and then logging in again.

[QUOTE=youngdaniel]has anyone successfully installed ubuntu on a powerbook g3 of any type??[/QUOTE]
Not me... sorry.

-Dave

---

### Post by Kyral on 2005-11-11
Yea, getting networking up is definately a priority right now. Apt/Synaptic is useless without it

---

### Post by ssam on 2005-11-11
gnome fails to start leaving you at a brown screen if the computers clock is before 1970. the clock battery on a mac usually needs replacing after 5 to 7 years. when the batter runs out the clock resets to 1904 (i think most pcs only reset to 1970 so not many poeple notice this bug.)

boot to the point of the brown screen, then press crtl+alt+f1 to get a terminal, and loggin in. type
```
date
```

if you get something like
```
Fri Jan 11 19:11:32 GMT 1970
```
then run the command
```
sudo date -s "Fri Nov 11 19:11:32 GMT 2005"
```
(you may need to put in your password)

now do the command
```
sudo /etc/init.d/gdm restart
```

and hopefully you can log in.

sam

---

### Post by ssam on 2005-11-11
[http://bugzilla.ubuntu.com/show_bug.cgi?id=17250](http://bugzilla.ubuntu.com/show_bug.cgi?id=17250) is the bug report relating to this problem (if indeed this is the problem.)

---

### Post by seatea on 2005-11-12
I don't have any solid advise, but i am running the ppc version of Breezy Badger. I have  a PM G4, however. Perhaps I missed it, but did you install from an ISO that you burned or did you use one of the official CD's that come in the mail? I don't know that much about installations, but it sounds like your installation did not go right. I seem to remember in another thread  that some people were having trouble with the ISO's they burned themselves. The use of CD-RW media was especially problematic. The first time I installed Ubuntu, I booted into a text console. I managed  to re-boot by hitting the reset button and fortunately arrived  at the  GUI. You can switch over to the text console by pushing Ctrl+Alt+F*x*(x being F1, F2, or F3). Try to reinstall gnome by running "apt-get --reinstall install gnome gdm menu" . Of course,  don't use the  quotes. It may be easier to reinstall using "ubuntu desktop" in place of "gnome gdm menu" . If all goes  well then type "sudo /etc/init.d/gdm start" .I got this out of the  *Debian Gnu/Linux 3.1 Bible.*  It is not referenced to Ubuntu, but the advice I have followed from it has  been pretty much on track. You may be asked several questions  if you use the "gnome  gdm menu" install. You may need the  CD in its drive during the installation. This may just be another  source of frustration, so keep in mind I am also a new user and these instructions may not be the right choice.

---

### Post by gruepig on 2005-11-12
Yes, Ubuntu on PPC is possible.  I'm running it on a white iBook G3.

It sounds to me like you are most of the way to having a fully-working system.  You can use the console, X is working, and it's just a question of why GNOME is hanging.

I think your next step is definitely to get networking up.  As others have mentioned, this will allow you to download newer packages. It's also possible that GNOME is attempting to do something network related, and that's what's causing the problem.

The file to configure to use the network is /etc/network/interfaces.  Poke around on the forums or ask in the networking forum if you need help.  If you aren't getting any response, send me a message and I'll try to respond within a day.

Hang in there!

---

### Post by darrenrxm on 2005-11-12
> then red hat on a top spec new pc, failed!! then ubuntu on same top spec pc, failed!!

Well, if I was in your shoes (and I am) I would do one of two things:

1. Find out what hardware is supported by Ubuntu. Buy hardware that is supported and switch it with the hardware that isn't. 

Or

2. Wait until your hardware is supported. 

I have a tv tuner card that isn't supported. They are working on support for it. But im not going to wait until god knows when to get it working under linux. Im just going to sell my old card and buy one that works under linux.

Of course you really don't learn anything with my method. Except that when you are going to buy a piece of hardware, make sure it is supported by linux before you buy it.

And I also think you should go back and try to get the "top spec pc" working under ubuntu again. It would be way easier to get it working rather than the mac laptop. I bet it has a serial ata hard drive. And that's what is giving you problems. 

Oh yeah, why didn't you try the live cd to see if it worked before you tried a hard drive install? It would have saved you a lot of headaches imo.

---

### Post by youngdaniel on 2005-11-12
good advice people!! cheers guys, for all your help! going to spend all of today sorting through your suggestions and hopefully getting into GNOME properly, will let you know how i get on!!! Thanks again!!

---

### Post by slux on 2005-11-12
It's cool that you've been so patient with Linux if you're still doing this after numerous attempts. :)

ssam's suggestion sounds like the probable solution here. GNOME really should not hang on login just because the date happens to be wrong though.

People on the Ubuntu forums are very nice and always willing to help but some issues are difficult to most users around here which I like as it shows that Ubuntu doesn't require the technical expertise many other distros do and that it's very popular with new Linuxists. We have some experts around as well, but with the large volume of messages being posted they may always miss something.

---

### Post by nevc64 on 2005-11-17
I had some success with my own login freeze problems finally
Refer
[http://ubuntuforums.org/showpost.php?p=499172&postcount=2](http://ubuntuforums.org/showpost.php?p=499172&postcount=2)

Good Luck

Neville

---

### Post by nocturn on 2005-11-17
[QUOTE=youngdaniel]havign all sorts of weird problems now, please bare with me!!
I can type my login name, but when it comes to password, the keyboard wont type!! [/QUOTE]

When typing your password, there is no visual indication because that might reveal details about the length of your password.  Just type it and hit enter, something should happen.

---

### Post by SectionThree on 2005-11-19
Greetings Youngdaniel:

*If I'm assuming correctly, you probably downloaded and burnt the iso under OS X.  If I'm wrong, disregard the rest of this post (or you could try burning it in OS X)...*

Here goes:

First off, **Don't use the "burn CD" command in the Finder**.  Open up a little gadget called "Disk Copy" instead.  You should find it in Applications/Utilities.

Now that you're in Disc Copy, find in the menu bar the command that says "make CD" or "burn disk" or something like that.  It will open up a dialog where you can browse for your iso.  Find it, double-click it, then do what the program tells you to.  Once it's done burning, you should have a fully-bootable, uncorrupted Ubuntu install disk.

Hope I was of some help....

---

### Post by winger1312 on 2007-07-13
If you only your RAM is 192MB, you do not have enough to fully install from a CD.  Everyone is getting way to complex on how to solve this problem.  Need at least 256 to install from CD.  You can try installing/booting from a USB flash drive.  Do not realy recommend it with a USB hard drive however.  Also, your computer is going to lag tremendously with Ubuntu; I suggest Xubuntu with that amount of RAM.

---

### Post by ComplexNumber on 2007-07-13
**winger1312**
i don't think it's going to do much good now ;). this is a 2 year old thread.

---

