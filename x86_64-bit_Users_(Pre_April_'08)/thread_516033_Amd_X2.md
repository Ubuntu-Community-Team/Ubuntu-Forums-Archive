---
title: "Amd X2"
date: 2007-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by xieu90 on 2007-08-02
hi
today I obtained 7.04 Ubuntu for 64 bit PC
when I boot the cd a menu appeared and I chose start or install ubuntu

and the story begins from here
a damn message always appears 

Kernel alive
kernel direct mapping tables up to 10000000@8000-d000



then my computer stopped and watch the cloud !


I found somewhere something and i tried it
i pressed F6 and wrote noapic there
so the message doesn't appear more and now I could install ubuntu
but after finishing the installation, that damn message appears again
and my 64x windows's boot ....
so I tried to use ghost to revive it, but .....
i had to delete its partition 
and reinstall 32 bit and 64 bit XP
after formating and installing, my computer had to restart to continue installing
normally it continues installing after restarting but now it stop and some red green character appear on my monitor and that is all
could anyone help me reinstall windows ?
or help me to master this Ubuntu 
maybe mastering ubuntu might be better because i hate windows

here is the data about my computer
ASUS Crosshair Mainboard
AMD Athlon 64 X2 4600+
512 DDR2 Ram
Maxtor HDD with 3 partition 
10 GB XP32  (deleted)
117 GB Storage (in danger !)
24 GB XP x64 (deleted)

Radeon X1950 ATI video card

I think that is all
please help me solve this problem
I look forward to your help
(using live cd from ubuntu, luckily i could still use internet here, otherwise I'm already ....)

---

### Post by John.Michael.Kane on 2007-08-02
Retry using this boot parameter (make sure to hit F6 first).

```
nosplash noapic nolapic
```

---

### Post by vikramgulati88 on 2007-08-03
Hey

I had the exact same problem with both 6.06 and 7.04
After I choose "Start or Install Ubuntu" the two files and the kernel start to load and then every thing STOPS. My comp just goes to sleep!!!
My system specs are :
AMD Turion 64 X2 (TL-52)
1 GB RAM
ATI 1100 Graphics

I would really appreciate it if someone could help me out.

Vikram.

---

### Post by xzero1 on 2007-08-03
It sounds like you have overwritten your boot sector code. The easy fix is to use a program to clear out your partition table (use maxblast cd) , then reinstall xp. Warning: ALL data on that drive will be lost. Warning2: if you have a large hard drive 138Gb limitations must be observed (this is probably why it won't work now).  There is also a hard fix that won't destroy data but it requires much more effort. 
The kernel mapping message is probably the way bios allows access to the memory and shouldn't be a concern. If there is an option in your bios you might remap the memory there but I don't know what this will do to windows. Get everything else working first before messing with that.

---

### Post by Kilz on 2007-08-03
If you have a windows 98 boot disk , boot it, navagate to the floppy , a: if I remember right. ```
fdisk /mbr
``` can restore the boot sector for windows, then you can try and reinstall grub/ubuntu.

[If you dont have one, go here to get one.]("http://www.bootdisk.com/bootdisk.htm")

This will not wipe the drive, so its worth a shot.

---

### Post by Jouke74 on 2007-08-03
You can also do that by booting with your windows install CD and choose recovery mode. Then when you see the prompt type fixmbr. Afterwards you might need to activate the right partition to be "bootable" with the boot flag. 

Be careful though...

From MS:

Fixmbr

Repairs the master boot record of the boot disk. The fixmbr command is only available when you are using the Recovery Console

fixmbr [device_name]

Parameter

device_name

The device (drive) on which you want to write a new master boot record. The name can be obtained from the output of the map command. An example of a device name is:

\Device\HardDisk0.

Example

The following example writes a new master boot record to the device specified:

fixmbr \Device\HardDisk0

Note
•	

If you do not specify a device_name, a new master boot record will be written to the boot device, which is the drive on which your primary system is loaded.
•	

If an invalid or nonstandard partition table signature is detected, you will be prompted whether you want to continue. If you are not having problems accessing your drives, you should not continue. Writing a new master boot record to your system partition could damage your partition tables and cause your partitions to become inaccessible.

---

### Post by xieu90 on 2007-08-03
hi everyone
thank you very much for your helping
I managed to solve a half problem sofar 
I can sneak into ubuntu now 
the real one not the live cd 
by this code 
nosplash noapic nolapic
so special thank to SD-Plissken


(but whenever i want to use ubuntu I have to write this one, it is annoying, can somebody tell me how to save it so that it can automatically go into ubuntu ? writing it everytime make me like Alibaba !!!! hey ubuntu open the gate and welcome your master ..... we are in 21 century now, so it is much better if i have a remote hihihi)

I haven't tried to install xp yet
but seem like I can install it now

my hdd was cut into 3 parts
10 gb xp32
117 gb storage
24 gb xp 64
both of xp were deleted 
some of my films were deleted with xp 64
what a pity
but nevermind
my treasure in storage is still here
hehehehe
yeah, ubuntu is in 10 GB partition now (without swap)
so don't really get this swap thing
i have never seen my computer touched this swap, so bye bye baby
hehehe

thank you to Jouke74 
even it is already too late for my xp 64
but next time I might be able to try it, thank you very much


I don't know if you guys love anime or not
but I would give you some links as thank you from me
my english sure is terrible now
damn german !

I will have to kill ubuntu and german huhuhu
look forward to it !

here are some links
deathnote001.extra.hu until 004
bleach001.extra.hu  until 007 ?
gto001.extra.hu - Great TEacher Onizuka until 003 this one was damn hard to download and it is only about 17 on, the rest until 43 are dead with my xp 64 huhuhuhu

I hope all of you will laugh a lot, specially with onizuka
my name is An
may be I will be GTA !!!!

so everyone, I need a way to automatically sneak into ubuntu without writing a long code
I need a chat program, so that I can chat with gtalk (with voice)
to chat with yahoo (with Web cam + voice)
bittorrent for linux, ubuntu is a debian based distributor, right ? so I have to download dbm or rpm ?
I have just tried and both of them was failure.....
does ubuntu have root user ?

 i couldn't log in as root
what is its password ?

---

### Post by praxis22 on 2007-08-03
By deafult ubuntu doesn't have a root password, no, use:

**sudo -s**

You can setup a passwd for root is you wish, but you can find that in the wiki

If you download automatix (google for it) you'll find most of what you seek program wise.

To set the boot flags as default, you have to edit the file:

**/boot/grub/menu.lst**

Find the entry for your kernel, (near then end of the file) and add the nospash, etc, there.

Again, you can find how-to's on all of this if you search.

This is Linux, not Windows, you will be expected to get your hands dirty, especially if you running the 64 bit version. 

Advertising the fact that you a pirate, on  a well known and highly trafficked web site, is not a very bright idea.

EDIT: No swap huh? You're going to regret that at some point.

---

### Post by xieu90 on 2007-08-03
hi praxis22
nice to meet you
do you know One Piece ?
well well
you can call me Luffy - Monkey D. Luffy I'm the man who will be Pirate King !!!
so how would you know that my dream is being a Pirate?
those 3 links were created by me, will I get a bounty on my head ?
I would be happy if I have one
hey hey
wanna come to Bermuda with me ?
Let's creat a crew to travel on bermuda it is funny 
but I will be the Captain !

being a pirate is so fun !!!!
I found and edited that file you told me with a text editor
but 
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
so which program should i try now ?
+ where can i know how much space I still have ?
linux sure made me so dirty !
let's have a bath together !!!!
where are girls ?:lolflag:

---

### Post by praxis22 on 2007-08-03
**df -k** will show you the state of your storage devices.

Bath? No thanks, my wife wouldn't approve.

The girls? They're outside. As in, out on the street, in pubs, clubs, shops, etc. 

Take a shower, wear decent clothes, comb your hair, and speak to them, listening also works wonders.

---

### Post by xieu90 on 2007-08-03
df-k worked greatly
but how can I edit and save 
[COLOR="Black"]**_/boot/grub/menu.lst_**[/COLOR]

you haven't answered me if you would be my comrade
We are going to be pirates and go to Bermuda !
I can smell adventures there
:lolflag:

---

### Post by praxis22 on 2007-08-03
"Why are we hiding from the police daddy?"
"Because we use vi, son, they use emacs."

I suggest you pick an editor, almost any text editor will do,  run it via sudo and then open, edit & save your file.

If you're used to notepad, I'd suggest gedit. Personally I use vi, but it's not for newbs, and the weak of heart.

**WARNING!** If you screw up this file, your system will no longer boot, and you will be in a world of hurt. make sure you search for and follow instructions on how to edit menu.lst

Pirates? Sadly piracy on the high seas is actually a hanging offence in most places, and rum, sodomy and the lash, is not something that interests me much. I'd rather be Porco Rosso than an air pirate.

---

### Post by xieu90 on 2007-08-03
thank you
luckily i found this one
To run a program using sudo that normally is run as the user, such as gedit, enter gksudo gedit in a terminal window.
so i edited that file
if I die
then it is that
who cares?
I'm on the way of mastering Ubuntu
I will beat it up and have a great slave like XP
:lolflag:
being a pirate is so fun
I suggest you to watch One Piece 
after watching it I'm sure you won't be a pirate hihihi

---

### Post by xzero1 on 2007-08-03
WARNING about fdisk /mbr etc. At least some if not all versions of these tools will not fix the mbr on large drives. They seem not to know about the 138Gb partition limit. The mbr contains your partition tables! Use with extreme caution!

---

### Post by xieu90 on 2007-08-03
can anyone tell me which program can shutdown my computer after a given amount of time?
in XP I use a program named Kill Winamp it will shutdowns my computer after 60 minutes or ... depend on me
I need a program like that for ubuntu, so that I can stay here in Ubuntu, listen to melodies and sleep like a good kid at night
otherwise nights are like .....

---

### Post by xzero1 on 2007-08-03
(in a terminal) type sudo shutdown -P +60 where 60 refers to number of minutes before shutdown.  See the shutdown command for other options do shutdown --help.

---

### Post by xieu90 on 2007-08-04
i worked greatly
thank you very much XZero

so far I got 
MSN with voice + webcam from amsn-project.net
kill winamp

I still need some programs 

chat voice with Gtalk
chat with WebCam with Yahoo
download with bittorrent 
write dvd + CD

upload download with ftp
firewall

can anyone give me some advices ?

---

### Post by John.Michael.Kane on 2007-08-04
Here this may help.

> **xieu90 said:**
> chat voice with Gtalk
chat with WebCam with Yahoo
```
gksudo aptitude install kopete
```

[Kopete webcam Howto.]("http://wiki.kde.org/tiki-index.php?page=Kopete%20Webcam%20Support&comzone=show")

> **xieu90 said:**
> download with bittorrent

Take your pick..
```
gksudo aptitude install bittornado
gksudo aptitude install KTorrent
gksudo aptitude install torrentflux
```
[HOWTO:Install Azureus]("http://ubuntuforums.org/showthread.php?t=144546&highlight=Azureus")

> **xieu90 said:**
> write dvd + CD
```
gksudo aptitude install brasero
```

> **xieu90 said:**
> upload download with ftp
Take your pick..
```
gksudo aptitude install gFTP
gksudo aptitude install Kasablanca
```

To make your own ftp server.
[HOWTO : Create a FTP server with user access (proftpd)]("http://ubuntuforums.org/showthread.php?t=79588&highlight=iptables")

> **xieu90 said:**
> firewall
You can use fire starter
gksudo aptitude install firestarter

Or 

Do it manually
[HOWTO: Set a custom firewall]("http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables")

---

### Post by xieu90 on 2007-08-04
I'm trying and feeling great now
while I was waiting for your reply I was trying to install bittorrent but something was wrong and I deleted it (I chose something always open bittorrent files with bittorrent )
now I installed bittornado and it run like a rocket (with a saved bittorrent file on my computer)
now when I want to download a bittorrent file from net Firefox always give me this message

/tmp/binktopia.rar - 'mininova.org' - .torrent couldn't be oppened because the associated helper application doesn;t exist. Change the association in your preferences.

so how should I do it ?

+ in windows when I install programs they all go to program files folder if I don't change its place
in linux where are they ? are they in usb/bin ?
I didn't find any file named bittornado there, but in application I saw bittornado client, and it work greatly

linux sure is complicated for newbie like me

---

### Post by xieu90 on 2007-08-04
how can I delete unempty folder ?
using terminal + typing sudo rm with every one single file is tiring
sudo rmdir : the folder isn't empty !

which command should I use ?

---

### Post by bford16 on 2007-08-04
> **xieu90 said:**
> how can I delete unempty folder ?
using terminal + typing sudo rm with every one single file is tiring
sudo rmdir : the folder isn't empty !

which command should I use ?

Use rmdir to remove empty directories.  Use rm -r to remove an "unempty" directory.  Be careful with this, since you can accidentally remove files you would rather keep.

If you are trying to get rid of installed programs completely, may I suggest you use "aptitude" to install and remove programs.  Like this: "sudo aptitude install program," and "sudo aptitude remove program."  This is a bit more effective that using apt-get.

Here is a link to a list of bash commands (the commands that are used in the terminal).

[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")

---

### Post by stmiller on 2007-08-04
> **SD-Plissken said:**
> 

Take your pick..
```
gksudo aptitude install bittornado
gksudo aptitude install KTorrent
gksudo aptitude install torrentflux
```
[HOWTO:Install Azureus]("http://ubuntuforums.org/showthread.php?t=144546&highlight=Azureus")


I second the vote for Ktorrent. An incredible client. You can enable Feisty-Backports to get the more recent version. It has options for encryption, bandwidth scheduler, built in ip filters, among other things. A very underrated app.

---

### Post by xieu90 on 2007-08-05
ha ha ha ha ha ha ha ha (<---- Crocodile's laugh)
thank you bford16 very much
rm -r kicked that chicken out of my computer 
and special thank for your list of command
I'll beat ubuntu like a pulp like i did to dos thank you very much
ha ha ha ha ha 
I'm on the way to get a great slave 



to stmiller
seem like I have to try Ktorrent
Bittornado already fell into my black eyes (unfortunately it is not blue !)
but you voted to Ktorrent so I have to give it a try

hihihihi
what about this one
/tmp/binktopia.rar - 'mininova.org' - .torrent couldn't be oppened because the associated helper application doesn;t exist. Change the association in your preferences.
how can I change the association in my preferences ?
one mistake makes me suffer so much !

so far I got 
Kill winamp
chat voice + wc with yahoo
chat voice  + wc with msn
ftp
bittornado the papa of bittorent hahahaha
i can write dvd now (got the program but i haven't tried it yet, don't have empty dvd rw !!!!)
watch avi and mp4 videos

i got the firewall but sofar it is somehow strange for me, it has never asked me if i want to allow or block something

i still need gtalk with voice
may be flash for firefox (i heard this one is complicated with firefox 32 and things)
and some tricks to download videos from sites, in win i go to temporary internet files and get them out from there, or use video download to copy from video google
in linux i haven;t tried it yet

after getting those trick I can use linux like windows (don't count warcraft )
hihihihi
it is more than enough for me

but the most important now is
/tmp/binktopia.rar - 'mininova.org' - .torrent couldn't be oppened because the associated helper application doesn;t exist. Change the association in your preferences.  <------ this one
I can not download any bittorrent file with this error !

---

### Post by John.Michael.Kane on 2007-08-05
There are two methods to getting flash under 64bit ubuntu.

Method one:
[Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java") **Note: Use the "Browser Install Script.", and make sure the universe and multiverse are enabled before installing anything.**

Method two:
2)[Flash 9 install script for AMD64 (nspluginwrapper)]("http://ubuntuforums.org/showthread.php?t=476924")


The error with the torrent probably means it try to open,however. No rar application was found . You can try the command below.
```
gksudo aptitude install unrar
```

After unrar is installed go the temp fold where the file seems to be, and right click on it, and try extracting it.

---

### Post by xieu90 on 2007-08-05
installing flash is so complicated
+ I'm lazy so I think I will spare it + I rarely watch things from youtube, but google, so if I need it too much then may be i will install it
hopefully i will never need it

about torrent
i couldn't download it onto my computer
I installed bittorrent, which doesn't run, and I made something like always open torrent files with that bittorrent, and i also deleted it later
so now whenever i want to download or open a torrent file that message will appear

damn it I'm angry now
I'll reinstall ubuntu from 0 now
when i started my life with windows I reinstalled them almost everyday, so I will do so with ubuntu
keh

+ learn to remember things too

---

### Post by xieu90 on 2007-08-05
uhm I think i will need a ghost back up program for my little ubuntu
so that i can reinstall everyday (after making some great mistakes)
which one should i use ?
please please (and please not too complicated like that flash, otherwise .... huhuhuhu hihihihi)

---

### Post by John.Michael.Kane on 2007-08-05
Take your pick.
Version one:
[Howto: Backup and restore your system!]("http://ubuntuforums.org/showthread.php?t=81311&highlight=ghost+back")

Version two:
[Howto: Backup and restore your system!]("http://ubuntuforums.org/showthread.php?t=35087&highlight=ghost+back")

Version three:
[Howto: Backup with Partimage]("http://ubuntuforums.org/showthread.php?t=287522&highlight=backup")

---

### Post by xieu90 on 2007-08-05
this ghost thing sure is troublesome
with this level I think i won't be able to make it now

now i have some other questions
1, where are my executable programs,which i installed. are they in /usr/bin ? 
after install some programs I found some of them in /usr/bin and on applications panel, but some of them are nowhere, and it could still run and not 
so where are they ? and how come they aren't in application, because i read somewhere in forum that after install programs they will put it into application


2 Ktorrent is sure the best in these 3 : bittorrent, bittornado,ktorrent it is the biggest and most beautiful 9mb , and I couldn't use it, there were always these errors 
couldn't find mime type application/octet-stream
no mime types installed
malformed url 
file:///home/ace

3 using terminal i have never been able to install things when it come to downloading something from server they ask me yes or no
I typed Yes, y or Y and pressed enter
then it stayed there
i went to system monitor and see my internet connection it doesn't do a thing
I always have to install with synaptic package manager
so how can i install with terminal? and are they different from each other ?

4 sometimes i do nothing (not even listen to music)
and my cpu's usage might be 20% 
i went to system monitor and see which program is using my cpu , but every single one of them sleep or run + all of them use only 0%
so what is using my cpu ?
in xp it was 0 %

---

### Post by xieu90 on 2007-08-05
before commit suicide I'm trying to install flash with method 2
may be it will work
, if it work i will try ghost, then reinstall my computer
ehhhhhhhhhhh

---

### Post by xieu90 on 2007-08-05
flash successful 
mission complete
but another come !!!! I'll have lunch now then I'll fight with ghost later
wait for my good news

---

### Post by xieu90 on 2007-08-05
happy birthday to you
happy birthday my slave
welcome to this world
happy birthday to me

I obtained almost everything I need 

msn, yahoo
winrar
ftp
firewall
kill winamp
ktorrent
ghost (not so sure, but I got 818 mb file)
flash

thank you very much SD-Plissken, Xzero
I love you guys so much thank you again
today is quite a nice birthday for both of us (me and ubuntu)
so I think you guys might like this site
[http://ryoni.com/](http://ryoni.com/)

when i have questions I will ask you guy a lot
please help me at that time ok ?
now I have to do my homework 
hic
damn german !
mama mia , help me !
I'm just a wild child, a child who will be the Pirate King on the Bermuda !!

---

### Post by xieu90 on 2007-08-05
hi I already have a new question

how do we download music from websites in linux with firefox 
if they don't give us the link to download ?

for example if I listen to music in xp, my computer will automatically save them into temporary internet files, I just have to copy them out from there, or right click on windows media player on the web and choose properties -----> there will be a link there and I can use it to save files

now how can I do those thing in linux ?

---

### Post by praxis22 on 2007-08-05
Use the "down them all" extension:

[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

---

### Post by xieu90 on 2007-08-06
down them all didn't work very well for me
it show a lot of link and I got lost + headache with it
but thank you

I found this one
[https://addons.mozilla.org/en-US/firefox/addons/policy/0/2254/17118](https://addons.mozilla.org/en-US/firefox/addons/policy/0/2254/17118)
from this one
[http://mashable.com/2007/08/01/firefox-downloads/](http://mashable.com/2007/08/01/firefox-downloads/)

I think i can live with it for a while, I like video downloader most but it is dead:lolflag:

---

### Post by xieu90 on 2007-08-06
i have another question

in stupid Xp there is a choise called thumbnail or something like that it show small pictures from original picture, and it make us easier to find our picture (even in menu, when we chat, upload or send files)
here in linux I can see that kind of thumbnail in computer - file browser (something like my computer in ubuntu)

so if I want to send a file to my friend I have to open and go to the right folder , then open the file browser, search for that file, memorize the file's name, go back to other program, find that file then send
it is a bit too ...

are there something like add-on or plugin or something that will show thumbnail for me? or where can i configure ?

---

### Post by xieu90 on 2007-08-08
no one ?

---

### Post by xieu90 on 2007-08-08
ntfs-config to write files to XP

---

### Post by xieu90 on 2007-08-10
how can i watch thumbnail pictures when I choose one to upload ?
what should i do if my computer freezed ?
in xp if I press Ctrl + Alt + Del I might still do something
what should i do here ?

---

### Post by xieu90 on 2007-09-27
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

skype 64 x

---

### Post by xieu90 on 2007-10-03
gconf-editor
apps>compiz>general>screen0>options>hsize

---

### Post by xieu90 on 2007-10-20
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)   ATI x1950 Driver !!!

* Fetch the helper scripts
$ wget [http://www.shiftingheat.com/packages...ty_install.tar](http://www.shiftingheat.com/packages...ty_install.tar)
$ tar -xvf feisty_install.tar
$ cd feisty_install
$ chmod a+x *.sh
* This guide is included as feisty_install.txt. All helper script execution in the balance of the guide assumes
you are in the feisty_install directory.


XGL
* Install Xgl
$ ./xgl_install.sh
* Logout
* Change session to Xgl ( temporarily )
Options > Select Session > Xgl
* Login
* If X works make Xgl session permanent at login


AUTOMATIX
* Install Automatix to get multimedia codecs, wine, vmware-server, vlc...etc.
$ ./automatix_install.sh



Compiz Fusion installation

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)


Compiz configuration
[http://ubuntuforums.org/showthread.php?t=574251](http://ubuntuforums.org/showthread.php?t=574251)







with this way I installed desktop effect in gutsy with ati x1950


copied a bit from
[http://ubuntuforums.org/showthread.php?t=463791](http://ubuntuforums.org/showthread.php?t=463791)

---

### Post by xieu90 on 2007-10-20
[http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.10_.28Gutsy_AMD64.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.10_.28Gutsy_AMD64.29)

---

### Post by xieu90 on 2007-11-29
gstreamer-properties

---

