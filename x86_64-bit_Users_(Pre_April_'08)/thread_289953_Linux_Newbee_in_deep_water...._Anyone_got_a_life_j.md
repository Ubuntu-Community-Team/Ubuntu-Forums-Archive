---
title: "Linux Newbee in deep water.... Anyone got a life jacket???"
date: 2006-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by jjandrj6679 on 2006-10-31
Hi all 

I am very new to Linux, Ive dabbled before but it scared me too much, so I went back to Xp. With the untimely release of Vista, which I installed, then formatted over it and installed Ubuntu. Why.. DRM City, I am not prepared to pay all that cash and have someone else control my media and my life... Have any of you read the ELU, and played with media player 11...Aaahhh??

Anyhows Ive came back to linux about 10 days ago.
Things that I am struggling with are as follows...(In brief):-

1) Permissions: I have no access to my other drives, I can copy from but not to, although they are mounted.

2) WINE: Screwed up my Packet Manager, now I cant access the Repositories.

3) No access to Add/Remove, Im told to go - /etc/apt/sources.list, but what do I do when I get there? Again caused by WINE.

4) Click on any Open office Icon and it fails to start.

5) I am unable to control my Asetek Waterchill Xtreme H2O Cooling system control Panel in linux... Hence WINE. Url below:
[http://www.asetek.com/default.asp?showPage=startside.asp&param=sideid&myvalue=14&contentSection=2&menuID=-1](http://www.asetek.com/default.asp?showPage=startside.asp&param=sideid&myvalue=14&contentSection=2&menuID=-1)
 
The pump 03-L-1224 :-  Navigate to "Waterchill, Componants [10mm,1/2], Scroll down to NEW Integrated 12V Pump/Reservoir with software based control panel, click on  03-L-1224"

The System 03-L-1219 :- Navigate to "Waterchill, Kits [10mm], scoll down to XTREME KITS [10mm], click on  03-L-1219"

6) I can't sort out Flash or Adobe in Firefox. Packets that I d/l are not recognize, or I do not have the right permissions?

7) I can't install new Themes at all?

8 ) I can't install new Games at all?

9) How do I sort out the Aplications list I would like control as to where everything goes.

10) How do I set up my Saitek P3000 Game pad? Tts in the device manager, but now what do I do as Saitek do not seem to support linux?

I have managed to sort some stuff out though.. nVidia 1440x900 res, 3D desktop?, some gDesklets, Java plus others.

As I said Im a newbee but I am willing to learn and fast, so if anyone has the time to teach me then I will be indebted to them for life.

I do have a yahoo Id but Im not sure if I have got Gaim running properly?

Look forward to hearing from you all.

Yours
Josh

P.S. I have read every help file that came with Ubuntu and online but no specific help was found.

---

### Post by Jussi Kukkonen on 2006-10-31
Hi,

I suggest you post one problem per post (or maybe several if they are related) with more details about the problem. That way you can post them in relevant subforums, and people are more eager to read your post as it'll be shorter and 'in the right place'.

> 1) Permissions: I have no access to my other drives, I can copy from but not to, although they are mounted.
What filesystems? If it's a windows filesystem, you've probably not mounted it right...  Please post /etc/mtab (and /etc/fstab if you've added something there).

> 9) How do I sort out the Aplications list I would like control as to where everything goes.

System - Preferences - Menu Layout


> 3) No access to Add/Remove, Im told to go - /etc/apt/sources.list, but what do I do when I get there? 
Fix it, I guess... Post the file and we'll see.

---

### Post by jjandrj6679 on 2006-10-31
I have just read this article "Absolute Beginner Talk", by aysiu.

Just to let you know that I agree with everything he says. Its a new way of life for me, I do not expect to be able to crawl out of bed with windows and snuggle up to Linux, like every relationship there has to be a bit of dateing first, getting to know each other, kinda thing.. If you see what I mean.. Am I even weirder than I thought I was?

Just a point, in Hardware, the only problem I had was the screen res and with the help of nVidia's forum (I didn't know this existed at the time, sorry) I got that sorted and learnt a lot in the process. Software install is my main bugbare but the more I learn the easier it gets, something to do with getting my head round Permissions.

Up till I started playing around (with very little knowledge), everything was fine....Ooops so hence I need help.... Cap in hand.

There is something differant about the people on the Linux forums that do not share the same attitude to life like the Windows guys & girls... Something I like very much.

Tops article.

Yours
Josh

---

### Post by jjandrj6679 on 2006-10-31
Hi there.
My appologies to my lengthy questions. I'm new to forums too. So unsure of how to approach things but i'll learn.
In light of this, for which I thank you, would you like me to re-post as seperate new posts or should we carry on as we are? Your call.

As to the details you asked fo here they are:

1) Permissions: yes they are windows drives. I do still have Xp as a second boot, untill I can fully function without it.

mtab:-

/dev/hdc1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-386/volatile tmpfs rw 0 0
/dev/hda1 /media/hda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hdb1 /media/hdb1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/sda1 /media/sda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hdd /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=josh 0 0

fstab:-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc5       /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


9) How do I sort out the Aplications list I would like control as to where everything goes. 
I do not have "System - Preferences - Menu Layout" I only have "System - Preferences - Menu & Toolbars" and that doesnt seem to be what I need or am I missing the plot?

3) No access to Add/Remove, Im told to go - /etc/apt/sources.list, but what do I do when I get there?
Here it is:-

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Oops this is a long one, now I see what you mean.
Thank you for you time and help so far I look forward to hearing from you soon.
Yours
Josh

---

### Post by kuja on 2006-10-31
In order to write to NTFS partitions in Linux, you must mount them in a different way. It should also be noted that it may not be 100% stable. [https://wiki.kubuntu.org/WriteSupportForNTFS?highlight=%28NTFS%29](https://wiki.kubuntu.org/WriteSupportForNTFS?highlight=%28NTFS%29) Use at your own risk. Yadda yadda yadda. At any rate, you should definitely try seperating this into a few seperate posts. Too much for my small, small mind to handle @.@

---

### Post by Jussi Kukkonen on 2006-10-31
The ntfs problem was already explained -- I'd create a new FAT partition for exchanging files between OSes. 

> 
9) How do I sort out the Aplications list I would like control as to where everything goes. 
I do not have "System - Preferences - Menu Layout" I only have "System - Preferences - Menu & Toolbars" and that doesnt seem to be what I need or am I missing the plot?

Ah, you are on Dapper, sorry I wrongly assumed you were using Edgy. The program is called Alacarte menu editor in Dapper I believe. If it's not installed already, install it through the package manager (once it's fixed). Then start it from the menu or from the command line with 'alacarte'


That *sources.list* looks ok... What do you get if you run 
```
sudo apt-get update

```in the command line?

---

### Post by kuja on 2006-10-31
Another option is to use an ext2 partition and installing a driver in windows for it. I find ext2 to be more stable.

As per openoffice, open up a terminal, and into it type openoffice. Can you tell me if you get any errors in the terminal when you try to open it?

---

### Post by jjandrj6679 on 2006-11-01
Hi all
Wow what can I say to that, you's are too good to be true, not like windows forums. Thanks all for responding.
Here are the details that you asked for.

To Jussi Kukkonen

Thank you for the Alacarte, all sorted now, but as for the other:-

josh@josh-desktop64:~$ sudo apt-get update
Password:
E: Type ‘[http://wine.budgetdedicated.com/apt’](http://wine.budgetdedicated.com/apt’) is not known on line 34 in source list /etc/apt/sources.list
josh@josh-desktop64:~$

Its that WINE come to life again... but I knew that was what was causing it.
I was directed to this page " [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) " when I wanted to run windows progs like my H2O Control software in Linux, Aseteck do not support Linux. So i assumed that everything would go to plan but I never got past the first stage...nothing new there then...lol..

To kuja
I thank you and here is what you asked for I think?

josh@josh-desktop64:~$ openoffice
Gtk-Message: Failed to load module "gail": libgail.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge": libspi.so.0: cannot open shared object file: No such file or directory


Fatal exception: Signal 11
Stack:
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c51f]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c83f]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c8dd]
[0xffffe500]
/lib32/libc.so.6(vsscanf+0x6d)[0x564f607d]
/lib32/libc.so.6(sscanf+0x2b)[0x564f0e7b]
/usr/lib/openoffice/program/libvclplug_gtk680li.so(_Z13InitAtkBridgev+0x35)[0x59305fdd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so(create_SalInstance+0x19d)[0x59304341]
/usr/lib/openoffice/program/libvcl680li.so[0x55791369]
/usr/lib/openoffice/program/libvcl680li.so[0x5579146a]
/usr/lib/openoffice/program/libvcl680li.so(_Z7InitVCLRKN3com3sun4star3uno9ReferenceINS1_4lang20XMultiServiceFactoryEEE+0xb7)[0x555f4ad3]
/usr/lib/openoffice/program/libvcl680li.so[0x555f4c31]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x29)[0x555f4cf9]
/usr/lib/openoffice/program/soffice.bin(sal_main+0x47)[0x80646db]
/lib32/libc.so.6(__libc_start_main+0xd2)[0x564b3ea2]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window11RequestHelpERK9HelpEvent+0x31)[0x8064615]
/usr/lib/openoffice/program/soffice: line 233:  5842 Aborted                 "$sd_prog/$sd_binary" "$@"

** (process:5827): WARNING **: Unknown error forking main binary / abnormal early exit ...
josh@josh-desktop64:~$

 As to my other drives I will continue on a new thread, as not to clutter this and help others too.

I hope this helps you's two to help me, I look forward to hearing from you soon.

Yours
Josh

---

### Post by kuja on 2006-11-01
The apt-get problem is referring to a problem on a certain line, it says line 34. That's for the wine repository, can you show me what that line looks like? For now, comment it out (by putting a # at the beginning of the line), and then attempt to do the update again and it should work. 

If you're running Ubuntu 6.06 (Dapper Drake), then try installing the package ia32-libs-gtk
```
sudo apt-get install ia32-libs-gtk
```
That should fix Open Office for you, I think.

If you're running Ubuntu 6.10 (Edgy Eft), I'm not really sure what the problem is, tell me if it's what you're using and I'll look into it.

---

### Post by jjandrj6679 on 2006-11-01
Hi there kuja
I copied it into the terminal and got this:-

josh@josh-desktop64:~$ sudo apt-get install ia32-libs-gtk
Password:
E: Type ‘[http://wine.budgetdedicated.com/apt’](http://wine.budgetdedicated.com/apt’) is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
josh@josh-desktop64:~$

No Office still doesnt work either

You also wrote this:-
The apt-get problem is referring to a problem on a certain line, it says line 34. That's for the wine repository, can you show me what that line looks like? For now, comment it out (by putting a # at the beginning of the line), and then attempt to do the update again and it should work.

I dont quite understand how to find line 34. nor the "Comment "#" bit, sorry for being completely thick..

Yours
Josh

---

### Post by kuja on 2006-11-01
Re-read the first sentence or two of what I said, you definitely need to make a change to your /etc/apt/sources.list file.

Edit:
To find line 34, either use a text editor that supports line numbering, or count down to that line. 
Put a # at the very beginning of that line, which tells apt to ignore it.

---

### Post by Jussi Kukkonen on 2006-11-01
> **jjandrj6679 said:**
> 
```
josh@josh-desktop64:~$ sudo apt-get update
Password:
E: Type &#8216;[http://wine.budgetdedicated.com/apt&#8217;](http://wine.budgetdedicated.com/apt&#8217;) is not known on line 34 in source list /etc/apt/sources.list
josh@josh-desktop64:~$
```


Well, that would indicate that you didn't paste the whole */etc/apt/sources.list* earlier -- can you recheck and paste it again, if you forgot the last lines?

---

### Post by Gustav on 2006-11-01
To edit the /etc/apt/sources.list file you'll need to use gksudo, open it by typing:```
gksudo "gedit /etc/apt/sources.list"
```in the terminal.

---

### Post by jjandrj6679 on 2006-11-02
To you all 

I am sorry that I have not answered you, its a stupid thing and I am ashamed to admit it.... I had not realised that it had gone onto a second page... so therfore mine being the last post, I was just waiting for an answer.. 

Ok firstly I did navigate my way to the sources list via...  hdc1/etc/apt/sources.list and that truely showed 33 lines not 34???

since then Gustav said to do this 
gksudo "gedit /etc/apt/sources.list"
I did and my pcket manager is sorted and up n runnin' again.

But that does not solve my problem of not being able to run my H2O Control Program within Linux.. Hence trying to install wine.

I followed said instructions ( [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)) but we ended up in this state. So any suggestions?

Yours
Josh

---

### Post by Titus A Duxass on 2006-11-02
Try installing wine with Automatix.
It usually works.

---

### Post by jjandrj6679 on 2006-11-02
Hi there where do I find that as I have not found it in Synaptic PM?
JJ

---

### Post by fabertawe on 2006-11-02
> **jjandrj6679 said:**
> Hi there where do I find that as I have not found it in Synaptic PM?
JJ

[Automatix web site]("http://www.getautomatix.com/"). The 'install' page has instructions for adding the appropriate repository.

Paul

---

### Post by jjandrj6679 on 2006-11-02
Hi there fabertawe

Thanks for the link, amazingly I understood and installed Automatix2 without a hitch.... now thats a first for this newbee...

I take it that you replied to my cry about my H2O Control Center (H2OCC) software that is windows based & my probles installing Wine, or have I got it wrong again?

If I am correct, which prog should I use, bareing in mind that I use Ubuntu64, or does it not matter? Is 64 backwards compatibe to 32?

Thanks Josh

---

### Post by Cynical on 2006-11-02
This may help you

[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

---

### Post by jjandrj6679 on 2006-11-02
Oh no now I'm confused!!

I take it that if I copy and paste (Building Wine on Ubuntu / Kubuntu 6.06 (Dapper Drake)) one by one into my terminal, will install a libraries/folder for 32bit and all it need to run Ubuntu32bit on a Ubuntu64 system?

Then I go to here "http://www.winehq.com/site/download-deb" and follow the instuctions again to get the right repository for Ubuntu Dapper (6.06)
Then this would allow me to goto Synaptic P/M and get the Wine packet?

Would I then use S/P/M to intall/configure Wine or would I go back to the above site and follow the instructions listed under "Installing from the WineHQ APT Repository with the console:" and the rest below?

Am I right in the fact that Wine is 32bit and I need to update my 64bit system to allow it to use 32bit packets/progs? Therfore allowing me to use any 32/64bit  prg/packet that is written for Debain (Which is what language Dapper Drake is written in)?  

I know I have asked a realy stupid question there but I am learning all the time with you guy/girls help I'll be able to stand on my own two feet very soon.

Greatfully yours
Josh

P.s is it impolite not to thank & sign after I reply? I know we don't do it while speaking, just wondered as it adds extra lines to every post?

---

### Post by fabertawe on 2006-11-03
> **jjandrj6679 said:**
> Hi there fabertawe

Thanks for the link, amazingly I understood and installed Automatix2 without a hitch.... now thats a first for this newbee...

I take it that you replied to my cry about my H2O Control Center (H2OCC) software that is windows based & my probles installing Wine, or have I got it wrong again?

If I am correct, which prog should I use, bareing in mind that I use Ubuntu64, or does it not matter? Is 64 backwards compatibe to 32?

Thanks Josh

Hi Josh,

Yes I was referring to your request for help with Wine but having just checked Automatix it doesn't install Wine anyway! Well not on mine! In which case I would suggest Kilz's [HowTo for Wine]("http://www.ubuntuforums.org/showthread.php?t=185557"). It's quite easy really, just follow the instructions.

64 bit is compatable as long as you have the relevant libraries. You could install a chroot, which is like a 32bit OS inside your 64bit OS, but this seems like overkill to me. Especially when the Wine HowTo is so easy.

Paul

---

### Post by fabertawe on 2006-11-03
> **jjandrj6679 said:**
> Oh no now I'm confused!!

Don't build it yourself, there's no point unless you specifically want to. I've done it and it's far easier to use Kilz's HowTo.

Wine is 32bit because the Windows environment it's emulating is 32bit.

It's polite to thank people for helping I would say. Everyone's different (unless cloned ;)), just be yourself.

Paul

---

### Post by jjandrj6679 on 2006-11-03
Hi there fabertawe

Just got back to this post as I have been sorting out NTFS-3G first in another post, it got confusing trying to sort out both at the same time. Still having probs with 3g but nearly there

I am just reading thru you link
"Install 32 bit wine to 64 bit Dapper without chroot"
whats a "chroot"?

So this page I just follow these steps and I can have Wine running on my U64? yes?

I have seen this before, 
"have you set up your video drivers to enable opengl"
Do I need to do anything about it, if yes, how? 
nvidia is my driver.

Also there is a mention of "nautilus" which I seem to have no link for either on my pc?
is any of the above any concern?

Ill give it a go and see what happens, better to try and fail than not to try at all. After all we have got you lot as a huge life jacket, whithout whom I'd have given up and gone back to Xp, then to Vistahell.
I'm sticking to it, its a marathon not a race.

LFTHFUS 
Josh

---

### Post by jjandrj6679 on 2006-11-04
Ok So heres what I did till it stop working:

I followed the Installation Script
```
cd ~/Desktop/wine 
./wine
```
That didnt work so I unpacked it and it crated a Wine folder. Then I copied both lines again. 
"ERROR: Could not find wine installation. Setup wine first."
Humm 
So I went to the section "Manual Install"
I downloaded these from the links:- I downloaded all of them as I didn't know which was the right one:

wine_0.9.24~winehq0~ubuntu~6.06-1_i386.deb
libxxf86dga1_1.0.0-0ubuntu3_i386.deb
wine-.9.23-install.tar.gz
```

josh@josh-desktop64:~$ cd ~/Desktop
josh@josh-desktop64:~/Desktop$ dpkg -x libxxf86dga1_1.0.0-0ubuntu3_i386.deb libs
josh@josh-desktop64:~/Desktop$ sudo cp ~/Desktop/libs/usr/lib/* /usr/lib32
josh@josh-desktop64:~/Desktop$

```
So the above unpacked/installed the libxxf86dga and put a libs folder on the Desktop. So far so good.
The next instruction is to install the wine so I coppied and pasted 
but I got this error```
josh@josh-desktop64:~/Desktop$ sudo dpkg --force-architecture -i
dpkg: --install needs at least one package archive file argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
josh@josh-desktop64:~/Desktop$
```
What went wrong? I have tryed all that I had D/L'd but every time its the same thing.
Basicly I do not understand the scripts that I C&P into the terminal.
I have no idea what force-architecture -i is, if I did I'd probably try to sort it out. to me it bares no resemblence to anything that I was doing.
Then one minute Im told not to uuse "SUDO" then 3 lines later Im told different??

Help!!!!!
Im going insane
JJ

---

### Post by jjandrj6679 on 2006-11-04
EUREKA 
I got it to work I think

Ok Im not totally sure how to use it, the help file are ott for me got way too indepth too soon for this newbee.
Firstly Im not quite sure if Wine is to be used to install an SETUP.EXE from scratch or use a program that is already installed in Windoze? 
If its the latter then how do I get rid of Windoze?
It asks for my programs DLL files??? it doesnt use any, does it?
I couldn't find any that associated with my application, only exe, ini, inf, lnk & user files.

Asetek WaterChill Control Panel.exe is the program I need to run

If I can control my Water pump then I can get rid of windoze for good, apart from a few games I play, GTA SA, Fear thats it, I havn't checked the apps list yet but I'm sure some one will get it to work on linux.

Thanks for all your help so far, and interested to hear what you have to say on the matter. And you you can call me whatever you want, even thick & stupid when you shopw me where I went wrong...lol

ILFTHFUS
Josh

---

### Post by fabertawe on 2006-11-04
> **jjandrj6679 said:**
> Hi there fabertawe
[snip]
I am just reading thru you link "Install 32 bit wine to 64 bit Dapper without chroot" whats a "chroot"?

Like I said above it's like having the 32bit OS inside your 64bit OS. When you run things inside the chroot it thinks your OS is 32bit.

> So this page I just follow these steps and I can have Wine running on my U64? yes?

Yes... we will try at least ;) 

> I have seen this before, "have you set up your video drivers to enable opengl" Do I need to do anything about it, if yes, how? nvidia is my driver.

You should be ok if your driver is nvidia.

> Also there is a mention of "nautilus" which I seem to have no link for either on my pc? is any of the above any concern?

Nautilus is the file browser (like Windows Explorer), accessible from 'Applications -> Accessories -> File Browser' on the menu.

> Ill give it a go and see what happens, better to try and fail than not to try at all. After all we have got you lot as a huge life jacket, whithout whom I'd have given up and gone back to Xp, then to Vistahell.
I'm sticking to it, its a marathon not a race.

That's the spirit :D 

Paul

---

### Post by fabertawe on 2006-11-04
> **jjandrj6679 said:**
> EUREKA 
I got it to work I think

=D> :D 
> Ok Im not totally sure how to use it, the help file are ott for me got way too indepth too soon for this newbee.
Firstly Im not quite sure if Wine is to be used to install an SETUP.EXE from scratch or use a program that is already installed in Windoze? 
If its the latter then how do I get rid of Windoze?
It asks for my programs DLL files??? it doesnt use any, does it?
I couldn't find any that associated with my application, only exe, ini, inf, lnk & user files.

Asetek WaterChill Control Panel.exe is the program I need to run

Navigate to your Wine 'c' folder (which is for all intents and purposes your 'c' drive) in Nautilus ('Applications -> Accessories -> File Browser') and put your Panel.exe (or whatever it's called) here. Then you can just double click and it should launch it inside Wine, which tries to install it.

If double clicking doesn't work, open a terminal and 
```
cd ~/c
wine Panel.exe
```
If it fails to install (or work after installation) you can type in the terminal
```
winecfg
```
and set 'Default Settings' to a different 'Windows Version' and try again. If it still fails to install or fails to run then it's unlikely that it'll work at all. I suspect something like that won't work but fingers crossed. I don't use Wine much so I'm no expert with it!

> If I can control my Water pump then I can get rid of windoze for good, apart from a few games I play, GTA SA, Fear thats it, I havn't checked the apps list yet but I'm sure some one will get it to work on linux.

It's a good idea to check out the [Wine database]("http://appdb.winehq.org/"). Maybe you could ask there too. I still dual boot Win XP but only because I need Cubase (and occassionally Source games!).

> Thanks for all your help so far, and interested to hear what you have to say on the matter. And you you can call me whatever you want, even thick & stupid when you shopw me where I went wrong...lol

ILFTHFUS
Josh

You're welcome. I wish I could help more but I'm fairly new myself and it's quite time consuming too. We all appreciate help, that's for sure!

What is 'ILFTHFUS'?!

Paul

---

### Post by dr.drake on 2006-11-04
well, I'm probably gonna get in trouble for this here.. but as far as I understood it from my nerdy friend, 64 is faster than 32, but just as in windows, it has less support in linux for a lot of things, so you'd end up running things slower. although my system supports 64, I just installed the 32 version on it, over which I then ran Automatix2.
I did my custom xorg and fstab mods and besides some problems with fonts in firefox that seem to go with edgy, it runs fine, even wine. (wow, I rhyme)

but I've got a question: did you try running the windows applications you need in a VMware version of windows? that usually seems to be more stable then wine for me?

---

### Post by jjandrj6679 on 2006-11-04
Hi there
Firstly ILFTHFUS is:- I Look Foward To Hearing From yoU Soon. 
I did as you asked with the file browser Nautilus.. Nothing, so I searched my entire pc for "wine & Panel.exe" nothing. So I did this:
```
josh@josh-desktop64:~$ cd ~/c
bash: cd: /home/josh/c: No such file or directory

```
It only works when i use "winecfg" in Terminal so like you, I think its not all there yet?

So what next?

As to dr.drake thank you for your honest opinion, you reckon that I should stick with U32 & Automatix2 to be on the safe side as I'm new to all this, not too sure of the "custom xorg and fstab" I've only done what I was advised to do with them, except when it came to my screen res, Ijust edited it to see if it would work and it did...

VMware, I have heard of it but I'm not sure what it means/is/does...

As for the speed I have U64 installed on a crummy seagate 37g noisy drive whilst I was evaluating it and it seems to run faster than xp32 on a good drive, so?

ILFTHFUS
Josh

---

### Post by dr.drake on 2006-11-04
> **jjandrj6679 said:**
> ..not too sure of the "custom xorg and fstab" I've only done what I was advised to do with them, except when it came to my screen res, Ijust edited it to see if it would work and it did...

VMware, I have heard of it but I'm not sure what it means/is/does...



my "custom" fstab is just that I set the permissions to all of my fat32 drives right, the xorg is to enable TV-out on my nvidia card.

VM is a Virtual Machine. you can run true windows on it. where Wine only pretends to be windows, it basically "tricks" the exe application to think it's windows, which makes that a lot of windows applications will either run badly or not at all on Wine. something simple like irfanview was even buggy. but a lot of applications WILL work on Wine, so don't let me put you off trying it.
VMware's only negative thing is that you need to make a virtual windows drive, which will take up a couple of gigabites, and because it runs inside Linux, it will NOT make external hardware like printers that won't work in Linux suddenly, magically work within VMware. if you want I can post a link to a vmware howto when I get home.

---

### Post by fabertawe on 2006-11-05
> **jjandrj6679 said:**
> Hi there
Firstly ILFTHFUS is:- I Look Foward To Hearing From yoU Soon. 
I did as you asked with the file browser Nautilus.. Nothing, so I searched my entire pc for "wine & Panel.exe" nothing. So I did this:
```
josh@josh-desktop64:~$ cd ~/c
bash: cd: /home/josh/c: No such file or directory

```
It only works when i use "winecfg" in Terminal so like you, I think its not all there yet?

So what next?
[snip]

Ok, run 'winecfg' again and tell me what it says on the 'Drives' tab. In the 'Path:' box mine says '/home/paul/c'. This will be the location of your "c" drive.

Where is the WaterChill install software? You need to copy it inside your "c" directory. If it's on CD you can run it from there with something like
```
wine D:\setup.exe
```
Check the CD contents from Nautilus to get the correct file name. The cd/dvd drive letter will have to correspond to what you have on the 'Drives' tab. If you have none then click 'Add' and change 'Path:' to '/media/cdrom'.

Please report back with tales of great success ;) 

Paul

---

### Post by xstaticxgpx on 2006-11-05
just completely reinstall ubuntu

---

### Post by fabertawe on 2006-11-05
> **xstaticxgpx said:**
> just completely reinstall ubuntu
Stupid me, this is obviously the way to get Wine working =D>  I think that picture of Bill's gone to your head :rolleyes: 

Paul

---

### Post by jjandrj6679 on 2006-11-06
Hi all
Sorry for not responding I have to work the week end as a nite cabbie in Essex to pay my bills. If you like Very Fat Foul Mouthed Women (Woman used lightly) then its a great job!!!

To dr.drake
Now i remeber reading about it, dois it not slow your whole pc down as its running 2 opps?, Do you think that is the best way to go just to get my H2O system running? It seems a bit of an overkill, but I dont quite understand it all as yet, but Im working on that bit too.

To fabertawe
Still not sure what a "chroot" is?
```
josh@josh-desktop64:~$ wine D:\setup.exe
wine: cannot find 'D:setup.exe'
```
The cd name is the same as you said.
but again my knowldge and tiredness has got the better of me and I cant seem to get access to the cdrom thru terminal, I know its realy easy but ive been up for over 37 hours now. 
I put it in a folder on my desktop and did this:
```
josh@josh-desktop64:~/Desktop/Asetek$ wine\setup.exe
bash: winesetup.exe: command not found

``` but nout happend as you can see
Probably got it wrong

To xstaticxgpx 
I kinda agree with you, but which one U32 or U64?


ILFTHFUS
Josh

---

### Post by dr.drake on 2006-11-06
> **jjandrj6679 said:**
> Hi all
Now i remeber reading about it, dois it not slow your whole pc down as its running 2 opps?, Do you think that is the best way to go just to get my H2O system running? It seems a bit of an overkill, but I dont quite understand it all as yet, but Im working on that bit too.

Josh

well, I would say: try getting it to work in Wine, it will take away less HD space.
if you can, maybe do as said here before: just do a clean install of Ubuntu/Kubuntu, and maybe try the 32bit version, because then you can install Wine with automatix.
if Wine doesn't want to work, only then try VMware. if you install a simple, clean version of windows on that (turn all eye-candy and useless MS crap off), then it shouldn't take away too much of your RAM.
do you need this app to run 24/7 ??

---

### Post by kuja on 2006-11-06
A clean install after spending days trying to sort out issues? That sounds like a rather unfair idea to me. That should be an absolute last resort should it not? 

Anyhow, to run that setup program that's on the cd, do this:

wine /media/cdrom/setup.exe

---

### Post by jjandrj6679 on 2006-11-06
Hi all

If you take a look at my H2O system ( [http://www.asetek.com/main/page.asp?sideid=694](http://www.asetek.com/main/page.asp?sideid=694) ) you will see that the Rad has 6 fans stuck to it & also details of the Pump & control system, whilst in Xp I can control the front & rear independantly, even turning them all off till say 50c which means that I have a near silent pc, especially when combined my the cooling rails in my case. If I want to go gaming, within two clicks the Control panel can be set up for it.
So yes this app is realy important. At the mo I have 2 fans running at 8v to keep it cool, so its noisy.

Personaly I'd like to throw MS and all it stands for out of my life, have you seen the DRM in MediaPlayer 11, at least in 10 you could opt out. not in 11. Not for me any more.

One day soon I hope to be Linux only but untill that day comes Ill dual boot with my own cutdown version of Xp. 
Id like to do a clean install as I have 4 ops in the boot menu of which 3 work spread over 2 drives of which one of them has developed a noise over the weekend.

Humm Yet again I fail at the simplest of things "wine /media/cdrom/setup.exe"
```
josh@josh-desktop64:~$ wine /media/cdrom/setup.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessib le.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
```

Error code 6006?? The only things I could find didnt make any sence to me.
All I noticed was that the DVD didnt budge nor led flash?
So I put the setup.exe on the Desktop```
josh@josh-desktop64:~$ wine /setup.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: cannot find '/setup.exe'
josh@josh-desktop64:~$ setup.exe
bash: setup.exe: command not found
josh@josh-desktop64:~$ wine /Desktop/setup.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: cannot find '/Desktop/setup.exe'
```
This is probably down tho the fact that I have done something wrong again??
Over to you guyz then?

Josh

---

### Post by kuja on 2006-11-06
Perhaps there was a problem when you installed wine - that's my best guess anyway.

See this page: [https://help.ubuntu.com/community/WineForAMD64](https://help.ubuntu.com/community/WineForAMD64)

---

### Post by jjandrj6679 on 2006-11-06
Thanx for that tip
I hadnt installed Sidenet Script, was I supposed to? Or as Im U64 should I have done the Edgy bit instead/as well
Here is what I got after I re-did "wine /media/cdrom/setup.exe"
```
josh@josh-desktop64:~$ wine /media/cdrom/setup.exe
josh@josh-desktop64:~$ err:storage:Storage32Impl_SmallBlocksToBigBlocks conversion failed: resRead = 0x8003001e, resWrite = 0x00000000
err:storage:Storage32Impl_SmallBlocksToBigBlocks conversion failed: resRead = 0x8003001e, resWrite = 0x00000000
err:storage:Storage32Impl_SmallBlocksToBigBlocks conversion failed: resRead = 0x8003001e, resWrite = 0x00000000
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000001
fixme:ole:NdrClearOutParameters (0x61fea000,0x18e4212,0x61fea134): stub
fixme:win:SetWindowTextA setting text "TITLE_CAPTIONBAR" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "WaterChill Control Panel v1.30 - InstallShield Wizard" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "TITLE_CAPTIONBAR" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "WaterChill Control Panel v1.30 - InstallShield Wizard" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "TITLE_CAPTIONBAR" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "WaterChill Control Panel v1.30 - InstallShield Wizard" of other process window (nil) should not use SendMessage
err:storage:Storage32Impl_SmallBlocksToBigBlocks conversion failed: resRead = 0x8003001e, resWrite = 0x00000000
fixme:shell:IShellLinkA_fnGetPath (0x1ef9f38): WIN32_FIND_DATA is not yet filled.
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\asetek Inc\\WaterChill Control Panel v1.30\\WaterChill_Control_Panel.exe") failed, error 126err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x1ef9f38): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1ef9d70): WIN32_FIND_DATA is not yet filled.
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\asetek Inc\\WaterChill Control Panel v1.30\\WaterChill_Control_Panel.exe") failed, error 126err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x1ef9d70): WIN32_FIND_DATA is not yet filled.
josh@josh-desktop64:~$
```

Does this make any sence to anyone?
Josh

---

### Post by dr.drake on 2006-11-06
> **kuja said:**
> A clean install after spending days trying to sort out issues? That sounds like a rather unfair idea to me. That should be an absolute last resort should it not? 


oh but that is a good thing.
at first with linux you put a lot of effort into resolving issues, this way you learn to understand the system better. then you remember the solutions, safe them somewhere. and when all is resolved you do a clean install WITH all those solutions...
that way you get rid of all the rumble that you left on your system when you were trying to get rid of those issues. that's why I have a copy of my xorg and also some links to ubuntuforum posts that helped me before in my email..
now a clean install is relatively painless for me. knowing I could do a quick new install actuall helped me to realise I could get rid of windows forever :)

---

### Post by jjandrj6679 on 2006-11-06
I agree with you totalyy
But I feel that because that I have U32 & U64 on the same drive & U32 is hdc1 & U64 is hdc2, each having a swap file (Don't blame me I'm a Learner....lol..), complicates things, also I believe that my default U64 home folder is hdc1, complicating things even further. Not to mention that I wiped over the Vista install with U32/64 but its still in the boot sequence?

But I think that you are right as well because there are still some issues that need to be ironed out that are anoying me.
Like why doesn't the Ram flush/release after I shut the app/program down? what I mean is that on initial start up it idle rests a 160mb, by the time I've played about a bit its touching 500mb on idle?? every time I run the packet manager it leaves 2mb in the ram still tiking over, the same with all programs. In Xp I auto flushed the ram every 5 mins & it ran sweet (For a MS product I mean) Using Firefox is the worst culprit though.

So I'll leave it as it is for the mo and with your help try and sort out the bugs in me bits. 

So did anyone make head nor tail of my error message?

LFTHFUS
Josh

---

### Post by kuja on 2006-11-06
If at that point the setup program would not run, then the issue is likely that it just won't run in wine. Seeing as we're dealing with something as important as the cooling device, you might want to look into vmware. If you plan on doing a full reinstall, I recommend you do this step AFTER doing the reinstall. The less times you reinstall windows in vmware the better, as it is very finicky about hardware configurations, and seeing as what windows sees  can easily be changed in vmware.... well, that doesn't bode well for your windows license. If the hardware configurations are changed too much or too often, it will invalidate your windows license. So yes, the less times you play with those things in vmware the better. Just a forewarning. For information on vmware server, see [this page.](https://help.ubuntu.com/community/VmwareServer)

---

### Post by jjandrj6679 on 2006-11-06
Oh, Gulp. 
Now that looks really, really complicated to do.
I understand the proceedures of getting a VMware up n runnin', less than I do Linux, and I can screw that up badly....lol
So is there a simpltons guide on how to do it? Oh and one that actually makes sence ...lol

So, like me you too had no idea what that error was then?
Sorry for the delay in responce, was searching wine for an answer, ha to sign up & all that, nout so far.
Josh

---

### Post by kuja on 2006-11-06
I know what the error means in a very blunt, general sense. Wine either can run something, or it can't run something. If you're getting errors and programs aren't running, then there really isn't much you can do about it (unless you happen to know a lot about computer programming and want to help out with wine development). 

Vmware LOOKS hard to set up, but it's really a lot simpler than things look. I tried it once, so I know this. 

First, go to the vmware website and download vmware server. It's a free download. Be sure to get a serial number while you're at it, also free. 

From there are you can follow the instructions in the ubuntu wiki page I linked you to. It will ask you to install a handful of ubuntu packages - you can do that with apt-get, synaptic, aptitude, adept, or whatever package management program you like. The rest of the process is to extract the *.tar.gz archive you downloaded from vmware, and to run the vmware setup script in a terminal. For most of the questions you can just accept the defaults by pressing enter without typing anything in. There is one or two exceptions to that - one of them is noted in the installation notes section of the wiki page. The other is the question about the serial number - you'll want to enter that.

After all of that setup nonsense, you'll find vmware is actually surprisingly easy to use.

---

### Post by jjandrj6679 on 2006-11-06
I just read this thread```
http://ubuntuforums.org/showthread.php?t=291493&highlight=wine
```
He seams to be happy with VM so I might give it a try.
So this is my explanation of how I think it gets up n runnin

```
Format & partition existing Xp install (Woopee)
Install U64
Update drivers & set up system 
Download & Install VMware (Just 1 file?)
Then...err.. pop Xp CD in drive, make a file for VM to intall it.
Sod the ELU (but press F8), its mine I bought it try & take me to court Bill!!
Re-boot loads of times 
Woosh everything wornking 1st time (Gulp0
Fire up Vm player
Install H2OCC software
Configure H2OCC
Silent pc at last. Phew!
```
Job done??
Yes/No?

One thing I did notice is that he says "I allocated 352MB. Of course you want to leave enough RAM available for Ubuntu to still be functional."
Allocate ram?
That means if U64 uses 160 idling + 250 plus for xp , not a lot left when Ive only got 1 gig worth of have I missed the boat again?

Josh

---

### Post by fabertawe on 2006-11-07
> **jjandrj6679 said:**
> Hi all

If you take a look at my H2O system ( [http://www.asetek.com/main/page.asp?sideid=694](http://www.asetek.com/main/page.asp?sideid=694) )

How do you fit all that in the case ;) I downloaded the control panel for what it's worth and Wine installs the software at least.

> I hadnt installed Sidenet Script, was I supposed to?

I can't remember the specifics of the HowTo but yes! It needs setting up somehow. Did you try anything from my previous post? I would delete the "C" directory ('c_drive', 'drive_c', whatever it was called by the previous setup... if it was ever setup at all) and just follow the HowTo again. It's pretty straightforward really.

Just for reference, none of my hardware works from Wine anyway (scanner, webcam, printer).

Paul

---

### Post by fabertawe on 2006-11-07
> **jjandrj6679 said:**
> I just read this thread```
http://ubuntuforums.org/showthread.php?t=291493&highlight=wine
```
He seams to be happy with VM so I might give it a try.
So this is my explanation of how I think it gets up n runnin

Interesting, I shall try it myself.

> Format & partition existing Xp install (Woopee)

I think you may want to leave that step until **last**, **after** you are happy running Windows from VMWare!

> One thing I did notice is that he says "I allocated 352MB. Of course you want to leave enough RAM available for Ubuntu to still be functional."
Allocate ram?
That means if U64 uses 160 idling + 250 plus for xp , not a lot left when Ive only got 1 gig worth of have I missed the boat again?

Josh

1 Gig should be plenty. Just allocate 512Mb+ to VMWare but don't run anything else at the same time. Play with it to find the optimal balance. Although if this does work for your cooler then running it constantly, even with minimal memory, could be a pain.

Paul

---

### Post by jjandrj6679 on 2006-11-07
Hi there fabertawe

Firstly how did you manage to intall the H2Occ software? All I got was errors..grrr. Please explain in detail, (step by step) as to how you got this thing installed...pleeeaaase. I only need Xp for this piece of software and VM seems a bit excessive for that, so ill try anything just so I can auto adj my fans and pump speeds and even use the Display. So Did you acctually get to see the Control Center with its Sliders & Graphs?

Secondly I build Bespoke Pc cases for my clients, from £75.00 - £2.5k. I even built a fluffy teddy bear for a clients kids..... This is how I got all that in my case + 3lt of coolant too & its only 475L x 360D x 350H. The cpu sits between 24 - 30c under normal use without fans, Oh and its portable too as its made of Alluminium & Copper weighs less than a standard Pc case. Want a bigger/smaller one then just ask me. I'd love to build you one to your own design/tastes. Unfortunatly I can't send pikkies of this one at the mo as I am waiting on patients to be sorted 1st, but I have a few picks of others I built.

As to Wine, I'm sure I did as you asked before but here it is again.
```
In the Drives Tab I have:-
C: /home/josh/c
D: /home/josh/
E: /media/cdrom
Z: /
``` Wats Z? Sata?```
I have 
hda1: C WINLITE Xp installed
hdb1: Data Storage
hdc1: U32 first & U64 2nd (Default boot is 64)
sda1: Data Storage
```When you said this "You need to copy it inside your "c" directory" did you mean My "Windows C, hda1 known as Winlite Drive"? or here /home/josh/c? (is that the same place?)

Im still all confused as how to sort this mess out coz I have both U64 & U32 on the same drive and it may be confusing more than just me.

LFTHFUS
Josh

---

### Post by dr.drake on 2006-11-07
I followed this simple howto to install VMware on dapper, should work on edgy too..

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

have fun.

---

### Post by jjandrj6679 on 2006-11-07
Well dr
It looks a simple procedure, I'm used to getting all messy so, what I think I should do is have a bash at it and see if it works out all ok. Intstall my H2OCC software & get that running, with my drives the way they are (a mess).
If ok then Ill re-install U64 + Vm & kill the Xp for good.
But still I think its a bit of an overkill just for one piece of software.
I'm hoping that fabertawe has sorted it with wine, just waiting on his answer.
Otherwise VM seems to be my only option.

Thanks
JJ

---

### Post by jjandrj6679 on 2006-11-08
I do have one resevation to istalling VMWare and its in this line:
```
What can I not do with it?
You will not be able to use hardware that doesn't work on Ubuntu. This is very important to understand!
The Virtual Machine runs on top of Ubuntu, so it can only acces Ubuntu detected devices. It is a virtual machine with virtual hardware.
```
To me that means my H2OCC Hardware, its also a no go for gameing which also means benchmarking like 3dMark05.
Have I read it wrong or am I right?
As to wine I copied all the setups that I needed to use for separate Xp progs into "c", ran Wine from the terminal. All of them failed to either setup or run once installed. Loads of errors whilst installing.
I tryed to install
Asetek H2OCC
Saitek P3000 Drivers
Saitek P3000 CC
Riva Tuner
ATI Tools
RMClock
3DMark05
Uguru M/B CC
No go to all of them. So either I've done it wrong or its a useless piece of software???
Josh

---

### Post by fabertawe on 2006-11-08
> **jjandrj6679 said:**
> Hi there fabertawe

Firstly how did you manage to intall the H2Occ software? All I got was errors..grrr. Please explain in detail, (step by step) as to how you got this thing installed...pleeeaaase. I only need Xp for this piece of software and VM seems a bit excessive for that, so ill try anything just so I can auto adj my fans and pump speeds and even use the Display. So Did you acctually get to see the Control Center with its Sliders & Graphs?

It complained about a missing .dll when I ran it but then I didn't expect it to work as I don't have the cooling system. You can copy the .dll over from Windows (legality issues aside ;))

> Secondly I build Bespoke Pc cases for my clients, from £75.00 - £2.5k. I even built a fluffy teddy bear for a clients kids..... This is how I got all that in my case + 3lt of coolant too & its only 475L x 360D x 350H. The cpu sits between 24 - 30c under normal use without fans, Oh and its portable too as its made of Alluminium & Copper weighs less than a standard Pc case. Want a bigger/smaller one then just ask me. I'd love to build you one to your own design/tastes. Unfortunatly I can't send pikkies of this one at the mo as I am waiting on patients to be sorted 1st, but I have a few picks of others I built.

Nice bit of touting there Josh! Thanks for the offer, I'm sure they're great but I'm quite happy with my setup.

> As to Wine, I'm sure I did as you asked before but here it is again.
```
In the Drives Tab I have:-
C: /home/josh/c
D: /home/josh/
E: /media/cdrom
Z: /
``` Wats Z? Sata?

'/' is the root directory of your Ubuntu OS (and Linux). So "Z:" is like "C:" in Windows in that it gives access to everything but in this case it's access to the whole of your main Ubuntu partition.

"C:" is located in your home directory as the directory called 'c'.

"E:" is your cdrom, so you would install 'Setup.exe' like
```
wine E:\Setup.exe
```

> I have 
hda1: C WINLITE Xp installed
hdb1: Data Storage
hdc1: U32 first & U64 2nd (Default boot is 64)
sda1: Data Storage[/CODE]When you said this "You need to copy it inside your "c" directory" did you mean My "Windows C, hda1 known as Winlite Drive"? or here /home/josh/c? (is that the same place?)

When we're talking about "C:\" drive in Wine context then yes, copy to '/home/josh/c'.

> Im still all confused as how to sort this mess out coz I have both U64 & U32 on the same drive and it may be confusing more than just me.

LFTHFUS
Josh

Have you tried installing Wine on U32 via Automatix? Or have you got it working now as you seem to indicate in another post?

Paul

---

### Post by dr.drake on 2006-11-08
> **dr.drake said:**
> VMware's only negative thing is that you need to make a virtual windows drive, which will take up a couple of gigabites, and because it runs inside Linux, it will NOT make external hardware like printers that won't work in Linux suddenly, magically work within VMware. 

> **jjandrj6679 said:**
> I do have one resevation to istalling VMWare and its in this line:
```
What can I not do with it?
You will not be able to use hardware that doesn't work on Ubuntu. This is very important to understand!
The Virtual Machine runs on top of Ubuntu, so it can only acces Ubuntu detected devices. It is a virtual machine with virtual hardware.
```
To me that means my H2OCC Hardware, its also a no go for gameing which also means benchmarking like 3dMark05.
Have I read it wrong or am I right?
Josh

you are right. it will run ALL software, it will not make hardware work. 
what it does with hardware is tell ubuntu to use it for him, so if ubuntu cannot use it, neither can vmware.
but I already told you so in my quoted post..

---

### Post by jjandrj6679 on 2006-11-08
I must have miss read the thread, sorry, but.... I have just recieved an email from far far away, this guy has managed to build a code in "Debain" just needs more work, now would that be able to port over to Drapper? If so, do you know anyone who could I forward the code to that may help me in my quest?

Where would I find the H2OCC Dll as I had a look thru my dll's and didn't see anything, not that I really knew what I was looking for as I didn't know the file name.

I looked thru Automatix2 but saw no referance to it, also there was a ref to nVidia drivers, but that said I had the current one install but gave no details. (see other post [http://ubuntuforums.org/showthread.php?p=1733045#post1733045](http://ubuntuforums.org/showthread.php?p=1733045#post1733045) )

Josh

---

### Post by jjandrj6679 on 2006-11-08
Oops I meant the code was writen in Delphi. sorry, all it needs is to have the ccommand line program written to send the neccessary HID messages.
Josh

---

