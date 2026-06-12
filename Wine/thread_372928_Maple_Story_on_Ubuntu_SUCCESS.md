---
title: "Maple Story on Ubuntu SUCCESS"
date: 2007-02-28
forum: Wine
---

### Post by Praill on 2007-02-28
Ive noticed many older posts re: maple story and it's rather unique inability to run in anything other than Windows (due to GameGuard mostly). I figured I would give this problem a crack (for no particular reason.. I dont really enjoy the game all that much.. i just wanted to see if it could be done) and I've finally figured it out. I actually have it running in the background as I type this. Here was my procedure:

What you need:
-An internet connection (gona want high speed)
-A windows install cd or iso
-Patience and time 

Before you start, make sure you have 3D capabilities in linux (because if you dont, then you wont in the emulator).
Open up a console and type:
```
 
$ glxinfo | grep direct

```

If it says direct rendering: yes, then you are good to go.
If it doesnt you can check out [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") for ATI cards, and hopefully someone else in the forum can help you if you have an nVidia card (I dont so I would'nt know the best places).
Now on with the show.


**1) Choose an emulator.**

Choices, choices. There are lots of emulators for linux, but at the time of this writing only one of them works for Maple Story: VMware. And, unfortunately, you can only legally run the full version of VMWare for 30 days without giving them money :(.
There are other free emulators out there you're welcome to try (I tried em all) but none of them support 3D acceleration via DirectX, which Maple Story needs. Even VMware only supports it in its "experimental stages", but its good enough to run a low intensive game like Maple Story. I'll assume for the rest of the thread that we're using VMware.

**2) Download and Install the Emulator**

Now, theres two routes you can go with VMware.
-a) download the 30-day trial [VMware Workstation]("http://www.vmware.com/download/ws/")
-b) download the free, open source, [VMware Player]("http://www.vmware.com/download/player/") along with the [Browser Appliance]("http://www.vmware.com/vmtn/appliances/directory/80") (that runs a mini Ubuntu ironically) and follow [this]("http://www.hackaday.com/2005/10/24/how-to-vmware-player-modification/") guide for how to reformat the browser and install Windows on the disk image. I personally couldnt get this method to work, but others report to doing so successfully. Therefore I'll assume were using the 30-day trial version for the installation intructions.

Unfortunately you have to create an account with them, and provide a valid email address, to get your temporary license key. You can get an address from [http://www.bugmenot.com/](http://www.bugmenot.com/) if you dont want to receive the spam I'm sure they'll start sending.

Once you've downloaded and extracted the tar, you can call the install with
```
sudo ./vmware-install.pl
```
It will ask you a plethora of questions which you can give the default answer to for almost every case.
The VMWare installation is rather long and requires many dependencies that I don't remember. If anyone wants to post the dependencies as they encounter them I'll edit the post later and put them in this spot.
The installation script should completely install and configure the program so it's all ready to go.
[B]
3) Install Windows[/B]

If VMware installed correctly, you should have a link in Applications-->System Tools-->VMWare Workstation (under gnome). If you arent in gnome, or don't have this entry, then the default location for the executable is /usr/bin/vmware.
Once the program window is open you need to:
File-->New-->Virtual Machine
Next
select option 1 (Microsoft Windows) and the selection to your appropriate windows version, Next
Next
Use bridged networking, Next
Chose whatever disk size you want (pref > 4gb)
Finish

If you are installing Windows from iso you'll need to click 'Edit virtual machine settings', go to the CD-ROM option, and change it from physical drive to use iso. Then, power on the virtual machine. 
The first time you go to start it will ask you for the temporary serial key you can get from logging into their page with your user name, but after that it will give you a POST screen, and then it will boot your windows install CD. 
Install Windows.

**4) Configure for Direct3D**

Once Windows is installed we need to make it ready to play 3D games.
a) Start up Windows in the emulator and install the virtual drivers by clicking VM in the menu, then clicking 'Install VMWare Tools'.
This will pop up a windows installer that will emulate all your linux drivers and ask you to restart.
b) In the windows emulation click on Start-->Run and run 'dxdiag'. Make sure you are running at least directx9 on your virtual machine.
c) Now for the dangerous part. This has reportedly not worked for some, but it worked just fine for me.
Shut down your windows emulation, close out of VMware, and navigate to where it saves your virtual drive (should be /home/<uname>/vmware/Windows XP/). Look for the file with a .vmx extension. Open that file with gedit and add the following to the bottom: 
```
mks.enable3d = "TRUE"
svga.vramSize = "67108864"
vmmouse.present = "FALSE"
```

Save the file, restart VMware, go to Edit-->Preferences-->Input, and uncheck all the cursor options. Apparently when 3D is running it wants to lock the mouse on the screen. That's ok, a simple ctrl+alt gives the mouse back to other applications. 
Now, start up the emulated Windows again and once its loaded go to Start-->Run.
Type in 'dxdiag' and click OK.
Go over to the display tab and if you have Direct3D enabled, do a dance of joy, download Maple Story, install, and start playing.

If Direct3D still isnt enabled, or youre getting weird reactions, try removing the svga.vramSize = "67108864" line from the .vmx file.
If this doesnt work than its possible your Ubuntu installation isnt set up for 3D direct rendering. You'll have to resolve this issue first as described in the first steps above.
If that is not the case then you might have to wait for the team at VMware to further develop their Direct3D support.

**5) (optional) Improve Speed**

If you've got it installed and working, but are having issues with speed, theres a couple things you can do to speed it up.
a) Increase memory usage.
By default, VMware sets virtual machines to use something like 256mb of the system memory. This is hardly enough to just run XP, so you can increase this value to whatever you wish (but Im assuming giving it too much can be a bad thing).
b) Change svga.vramSize = "67108864" in the .vmx file to a larger value. Currently it's set at 67,108,864 bytes (64mb) so only change this if you have more than 128mb memory available on your video card. It has to be changed in logical increments that equal a megabyte. So for 92mb multiply by 1024 then 1024 again = 96468992 bytes
c) Eliminate the XP Frills. 
Click Start-->Control Panel-->System-->Advanced-->Performance Settings
and adjust for best *performance*.
[B]
6) (optional) Slow Network[/B]

One final note: If you notice slow throughput on your network card you can try changing the ethernet settings to use NAT instead of bridged. Bridged is ideal because it allows for network transfers with the host, but has been known to have problems.


Good Luck!

---

### Post by Darconix on 2007-03-28
> **Praill said:**
> [I]***UPDATES***

**2) Download and Install the Emulator**

Now, theres two routes you can go with VMware.
-a) download the 30-day trial [VMware Workstation]("http://www.vmware.com/download/ws/")
-b) download the free, open source, [VMware Player]("http://www.vmware.com/download/player/") along with the [Browser Appliance]("http://www.vmware.com/vmtn/appliances/directory/80") (that runs a mini Ubuntu ironically) and follow [this]("http://www.hackaday.com/2005/10/24/how-to-vmware-player-modification/") guide for how to reformat the browser and install Windows on the disk image. I personally couldnt get this method to work, but others report to doing so successfully. Therefore I'll assume were using the 30-day trial version for the installation intructions.

Unfortunately you have to create an account with them, and provide a valid email address, to get your temporary license key. You can get an address from [http://www.bugmenot.com/](http://www.bugmenot.com/) if you dont want to receive the spam I'm sure they'll start sending.

Once you've downloaded and extracted the tar, you can call the install with
```
sudo ./vmware-install.pl
```
It will ask you a plethora of questions which you can give the default answer to for almost every case.
The VMWare installation is rather long and requires many dependencies that I don't remember. If anyone wants to post the dependencies as they encounter them I'll edit the post later and put them in this spot.
The installation script should completely install and configure the program so it's all ready to go.
[B]


Sorry for this n00b question, im still new to ubuntu
can you explain how to install this exactly i cant figure out how i got the files and i did what it said but didnt work
but what do i do after that?
Thankyou!:confused:

---

### Post by ceeg on 2007-03-28
> **Darconix said:**
> Sorry for this n00b question, im still new to ubuntu
can you explain how to install this exactly i cant figure out how i got the files and i did what it said but didnt work
but what do i do after that?
Thankyou!:confused:

vmware-asdfasdf.tar.gz
```

tar xvzf vmware-asdfasdf.tar.gz
cd vmware-asdfasdf
sudo ./vmware-install.pl

```

Make sure you are in the directory with the tar.gz archive before execute the above instructions.

---

### Post by Praill on 2007-04-04
I'm not sure exactly where you are stuck. Could you be more specific?

---

### Post by Hansuonu on 2007-04-07
ok i have a problem to...i did all u say till directX i DL 8.1 and my maple sayd some "display GR2D" error, then i added those settings  and "Yes it worked" till i start loading  that Nexon and Wizet i did not see anything only black screen but there was music and then when i need to login i cannot see picture only this freakying black screen and when i use Control+alt+delete it says maple is running....:confused: 

Pleas help me 
TY Hans

and u who needed to install that VMware u need to open TERMINAL Applications->Accessories->Terminal

---

### Post by Hansuonu on 2007-04-07
that error was "Failed to find proper screen mode for Gr2D"

---

### Post by Praill on 2007-04-12
Hmm.. do me a favor and try to install directx 9 instead of 8.1. Tell me if that fixes it.

---

### Post by Hansuonu on 2007-04-15
same... nothing helps..

---

### Post by Praill on 2007-05-07
Thats the error you get when DirectX doesnt have 3d rendering ability.
If you added:
mks.enable3d = "TRUE"
svga.vramSize = "67108864"
vmmouse.present = "FALSE"
to the config and you still dont have 3d in the virtual OS then theres nothing you can do. VMWares 3d support is still in its experimental stages.

---

### Post by nythacker on 2007-05-07
> **Praill said:**
> 
**2) Download and Install the Emulator**

Now, theres two routes you can go with VMware.
-a) download the 30-day trial [VMware Workstation]("http://www.vmware.com/download/ws/")
-b) download the free, open source, [VMware Player]("http://www.vmware.com/download/player/") along with the [Browser Appliance]("http://www.vmware.com/vmtn/appliances/directory/80") (that runs a mini Ubuntu ironically) and follow [this]("http://www.hackaday.com/2005/10/24/how-to-vmware-player-modification/") guide for how to reformat the browser and install Windows on the disk image. I personally couldnt get this method to work, but others report to doing so successfully. Therefore I'll assume were using the 30-day trial version for the installation intructions.

I've discovered that you **_only_** need the free [COLOR="Blue"]**VMware Player**[/COLOR] and [COLOR="Blue"][**[COLOR="Blue"]http://www.easyvmx.com/[/COLOR]**]("http://www.easyvmx.com/")[/COLOR] to create complete virtual machines for VMware Player. There is no need for either VMware Workstation or the free VMware Server to create virtual machines.

---

### Post by cisforcojo on 2007-05-09
Is it possible to run MapleStory through a proxy? I've tried in teh past and had no luck with MapleStory (China blocks it). I'd need it to run on a Windows box as well with proxy (my roomie's computer). I know that MapleStory digs its claws really deep into your computer and checks for programs like FreeCap that force proxies.

---

### Post by Panzor on 2007-05-10
I know many people that play in college. I'm not sure if they run through proxies, but I'd be very surprised if they aren't. If your system is set to use a proxy to access the internet, I don't see why MapleStory would be the problem. Your proxy may not allow MS due to it openness.

---

### Post by cisforcojo on 2007-05-10
Openness? Sorry I'm not following you. What I need is a proxy that makes me undetectable to China's censoring. Tor+Privoxy can accomplish this. I haven't had ANY luck finding a good Anonymous Proxy in America though. Googled lots and have found nothing. Everything is transparent. Only Tor works.

---

### Post by Panzor on 2007-05-10
My friend has one, but I seriously doubt he'd let you use it...

---

### Post by Rerc on 2007-05-11
okay, i've had some limited sucess with this over the past week.
I finally managed to get direct rendering enabled on my radeon 7200
and dxdiag shows that i have acceleration enabled (and the tests work)

However, when i run vmware, i get "failed to construct 3d rendering backend"

and I get a gameguard "114" error when trying to run MS.

have i missed something?

---

### Post by Spastic on 2007-05-25
I was also successful in running Maple Story. 
But.. 
I have horrible performance issues. I'm getting moderate lag in the windows environment and it gets unbearable once in the game. (clicking my PIN into the soft keyboard takes like 3 minutes) this is coupled with odd graphical errors.

Best of luck to the other users out there.

---

### Post by cisforcojo on 2007-05-25
I strongly recommend VirtualBox over VMWare. I have serious performance issues with VMWare (closing a window was choppy as all hell, took maybe 10 seconds?) but VirtualBox actually runs at some points FASTER than my native Windows installation. I haven't tried MapleStory though so I can't comment on that. As for everything else, VirtualBox has been much faster (through MY experience, it's possible I didn't set up VMWare correctly... ** this ending is to avoid a VMWare vs. VirtualBox conflict. I'm just suggesting it as an option)

---

### Post by Spastic on 2007-05-25
i thought of that... but I'm running feisty with 64bit architecture and i cant find an appropriate version of virtualbox.  i am willing to try any virtual machine software.

---

### Post by cisforcojo on 2007-05-25
Hmm.. never actually OWNED a 64-bit system so I can't be too much help here. Perhaps you could look into optimizing VMWare but I'm not sure how much success you'll have.

---

### Post by Spastic on 2007-05-26
well i reformatted my computer with with a non 64bit distro of feisty to give virtual box a try (as well as some other software i was unable to find 64bit support for).  

virtual box does not support direct3d. the guest video card is locked in as a vesa vga card with very low ram.

although i must admit it is a much nicer visualization suite, and its open source  so maybe someone will get some direct3d compatible video drivers on it soon.

in the meantime I'm currently reinstalling vmware to give it a try in 32bit

(EDIT)  
Got it working! not as fast as native was, but certainly playable.  VMware player 2.0  under 32bit architecture worked.

---

### Post by Spastic on 2007-05-26
ok after some testing I'm not sure if 64bit architecture was my issue, but in a 32bit environment i have discovered the host screen resolution effects the performance greatly.
I'm not sure why the host resolution makes any difference at all but it does. guest resolution seems to not matter at all on the performance front.

i tested the following resolutions at their default refresh rates:
----
1440x900 (my monitor's preferred resolution) 
1280x800
1152x864
**1024x768 (this resolution was the only one that provided playable results with only minor graphical glitches)**
832x624
800x600 (the game's forced resolution which is unchangeable)
----
my system specs are :
(host)
Asus M2V motherboard
AMD athalon 64 3500+
1gig ddr 
Nvidia Geforce 7600
ubuntu feisty 7.04
(guest)
vmware-player 2.0
Windows XP service pack 2 
768m ram

---

### Post by Thehound on 2007-09-04
This works even on ATI cards. I have tested it over and over. Sorry for reviving this thread but it's worth reviving just because it's the gateway to some other games too, like FF7 and 8 for PC, which still won't run in WINE, VMWare will auto-disable these settings if you don't see something like this  when you type glxinfo

glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

Fixing that is easy for nvidia cards by just getting the driver, setting it as executable then rebooting into a console login to run it.

It is possible that direct rendering says yes, but the driver is still not installed properly, particularly in ATI cards. The new 8.40.6 version is a bust for my ATI card, producing a black screen on login and causing other versions when rolling back to yield same results until components are removed manually... or with this handy little script after removing the driver with normal method
[http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh) This will remove traces of the previous driver commonly left over and download and install the new when invoked from a console login. Since it goes with the new version which is crap even when manually installed you'll invoke it with a -v option eg sudo sh install-fglrx-debian.sh -v 8.39.4 which actually gets a good driver version. I used to recommend running ATI's script and then fixing a few symbolic links but this is now my recommended foolproof method for installing the driver. It does everything the ATI script should have done for you and that nvidia's already does.

Lastly, just for best stability and speed, I recommend Windows 2000 as guest. It plays very nice with VMWare and is the closest thing Microsoft has to a good OS overall.

---

### Post by zikon on 2007-10-09
First, most people dont have the cpu to run vmware. So when people say maplestory doesnt run on linux, they mean they cant get it to run on "linux" not a emulated windows

Of course maplestory will work with vmware.. ITS WINDOWS!

We want gameguard to actually work with Ubuntu + wine/cedega

If you can get that to work, then props to you

---

### Post by denali on 2007-10-12
I used [www.easyvmx.com](www.easyvmx.com) to create my VM... I picked Intel 1000 pro as the network card, but that doesn't seem to work.  It gave me 3 choices: Intel 1000 pro, vlance and vmxnet.  Which one should I have picked?

---

### Post by nicolasjager on 2007-10-22
I followed your directions but I can't get Maple Story to run on my Virtual Machine.  Maple Story starts up, Game Guard starts up, but then all I get is a black screen and I get no response from sending "crtl alt del" command.  Only thing I can do is reboot.

My host machine is a Dell Inspiron 5100 with a Radeon 7500 graphics card, Running Windows XP Pro.  It has 512MB RAM, and 2.66 GHz processor.

Upon boot up, my virtual machine gives the following message:
Failed to Construct OpenGL rendering backend
The 3-D features of the display card will be disabled.

However, when running dxdiag, it claims 3d acceleration is "enabled"

What can I do?

---

### Post by ridetheteapot on 2007-10-24
does anyone check this thread?

i've got windows 2k running through vmware to play a couple post scumm games like grim fandango and torins passage.
i got maple story installed (and vmware tools and directx) but when i start it up gamegaurd fails evertiime GameGaurd: Error Initilizing 114...

any ideas why? everything else seems ot work fine, maybe its just 2k?

---

### Post by nikoPSK on 2007-12-19
unfortunately thats not on ubuntu. It's just in xp.

---

### Post by tenchu77491 on 2007-12-20
I'm installing Maple Story now, not sure if it is going to work. However, for those out there not sure how to install VMware, I found this tutorial most helpful, 

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

After that, come back to this tutorial here and follow the instructions to enable 3D.

---

### Post by tenchu77491 on 2007-12-21
I did everything, when I open Maple Story and hit the play button, Gameguard launches, then when the game is about to launch one of two things happen. 1) The screen goes full screen and black, 2) I get a BSOD and Windows restarts. 

What is the problem?

---

### Post by iammeagain on 2007-12-21
> , unfortunately, you can only legally run the full version of VMWare for 30 days without giving them money .


I think that you could use VMware player after setting up XP with the workstation to keep it working after 30 days.

---

### Post by iammeagain on 2007-12-21
> **tenchu77491 said:**
> I did everything, when I open Maple Story and hit the play button, Gameguard launches, then when the game is about to launch one of two things happen. 1) The screen goes full screen and black, 2) I get a BSOD and Windows restarts. 

What is the problem?

I have had a similar i usually hit the ctrl + alt to release the mouse from the screen and then it loads.

---

### Post by tenchu77491 on 2007-12-21
> **iammeagain said:**
> I think that you could use VMware player after setting up XP with the workstation to keep it working after 30 days.

Or, use VMware Server, which allows you to make virtual machines and use them, AND it is free.

---

### Post by tenchu77491 on 2007-12-21
> **iammeagain said:**
> I have had a similar i usually hit the ctrl + alt to release the mouse from the screen and then it loads.

Did the screen go all black and would not continue loading until you released? Or only got BSOD when you did not release?

---

### Post by iammeagain on 2007-12-21
> **tenchu77491 said:**
> Did the screen go all black and would not continue loading until you released? Or only got BSOD when you did not release?
only when i did not release, but usually just a black screen, although i did get a couple BSODs

---

### Post by iammeagain on 2007-12-21
> **tenchu77491 said:**
> Or, use VMware Server, which allows you to make virtual machines and use them, AND it is free.

Yea, I thought there was something else out there.  Then what is the use of the Workstation if Server is free?

 I had used that on my old desktop, before I got my laptop. I had been a while because Ubuntu wasn't compatible with lots of my hardware until this last release.

---

### Post by jetrost on 2007-12-21
This might be a little off topic, but off-hand, does anybody know if trying to log into MapleStoryGLOBAL from an IP in Japan is allowed? When trying to run the executable in wine, I keep getting an error "GameGuard: Error Initializing (114)" after clicking the "Play" button. I don't really feel like setting up VMWare and trying to find a Windows install iso at the moment...(lazy!!!) Any thoughts?

---

### Post by iammeagain on 2007-12-21
> **jetrost said:**
> This might be a little off topic, but off-hand, does anybody know if trying to log into MapleStoryGLOBAL from an IP in Japan is allowed? When trying to run the executable in wine, I keep getting an error "GameGuard: Error Initializing (114)" after clicking the "Play" button. I don't really feel like setting up VMWare and trying to find a Windows install iso at the moment...(lazy!!!) Any thoughts?

I think the problem with wine is that gameguard looks for a windows system or something special. The only way to get Maple Story working on Wine would be to find a way around (hack) gameguard, supposedly. Thats why we have to use vmware.

---

### Post by jetrost on 2007-12-21
> **iammeagain said:**
> I think the problem with wine is that gameguard looks for a windows system or something special.

That is interesting. I suppose "hacking" GameGuard would be frowned upon by Wizet (MapleStory developers)? Thanks for the information.

---

### Post by aatiis on 2008-01-17
Sure, the new version can be used for more than 30 days. I am using mine for two or three months now, tough I didn't try to get direct rendering work for I already had some issues getting compiz/fusion + xgl video rendering working properly on my notebook.

---

### Post by nikoPSK on 2008-01-17
I hope they get gameguard working for linux...

---

### Post by rafaelpriego on 2008-01-18
Hi, i did everything according to this tutorial, and in the end, when i Hit the green button to fire up the virtual machine, it shows the following error message: 

```
Failed to construct 3-D rendering backend.  The 3-D features of the display card will be disabled.
```

I had all the requisites, and my video card is working and direct rendering is activated and all...

Got any ideas?

---

### Post by ridetheteapot on 2008-01-18
I got maple running on an XP vmware server... I can play the game after i install it, but eventually the game will crash and then i have the same problem as tenchu77491 when i try to play again (except it is ALWAYS a bsod then the virtual machine restarts). The blue screen goes away too fast to read anything it says.
I tried reinstalling maple, and that fixed it until the game crashed and the same problem reoccurred. Deleting the gameguard directory so gameguard reinstalls doesn't seem to help at all.
If anyone knows whats going on here i'd love to know.

FYI for anyone who can play maple in vmware consistently, you can improve the speed a ton by killing gdm (or kdm)
```
sudo /etc/init.d/gdm stop
```
and then starting vmware in its own x server
```
sudo X :1 -ac & DISPLAY=:1 vmware
```

---

### Post by kiko0850 on 2008-02-03
THANK YOU!!! i've been trying to get maple story to work on linux for a while, and yes what you've done DOES work thanks a lot!

---

### Post by Sauceror on 2008-03-03
> **rafaelpriego said:**
> Hi, i did everything according to this tutorial, and in the end, when i Hit the green button to fire up the virtual machine, it shows the following error message: 

```
Failed to construct 3-D rendering backend.  The 3-D features of the display card will be disabled.
```

I had all the requisites, and my video card is working and direct rendering is activated and all...

Got any ideas?

I'm sorry for bumping an old(ish) thread, but I'm having the same error as him. I did everything else, but adding the three lines to the .vmx file makes this error appear, and then I can't play Maplestory.
when I try running maplestory on VMware (workstation), it just says "DLL class not found". is this the error that appears when Direct3D isn't enabled?
if it makes a big difference, the virtual machine I have was originally made for VMware player, not VMware workstation. I dunno if they have differences between them, but, yeah.

---

### Post by Blice on 2008-04-01
> **Sauceror said:**
> I'm sorry for bumping an old(ish) thread, but I'm having the same error as him. I did everything else, but adding the three lines to the .vmx file makes this error appear, and then I can't play Maplestory.
when I try running maplestory on VMware (workstation), it just says "DLL class not found". is this the error that appears when Direct3D isn't enabled?
if it makes a big difference, the virtual machine I have was originally made for VMware player, not VMware workstation. I dunno if they have differences between them, but, yeah.

I had this problem too, I fixed it by uninstalling xserver-xgl...



Anyways, I have another problem now. When I start MS, the screen goes white and then.. nothing. It just stays white. I can alt-tab out of MS, everything seems to be working fine, but the MS screen is just white. No music, either.

Anyone have suggestions?

---

### Post by DUfire on 2008-04-13
Ohh, good 'ole VMWare.
Haven't used VMWare since I tried hacking on Vista when it first came out and on my brand new laptop [this same one, in fact].
Anyway, this should work pretty nicely, thanks for the reminder that all hope is not lost for us Linux-Maplers ^^!

---

### Post by Thehound on 2008-04-14
To the black screens and the BSOD people, you likely have an install problem with the drivers, the install, a non-supportive card, or just buggy drivers.

1. For those with onboard video **make sure your onboard card supports OpenGL**(some don't). You can check it in Windows to be sure. Some older aftermarket video cards(pre2000) skimp on OpenGL support, as well.

2. Make sure you are not in an XGL session. XGL disables direct rendering for other apps. That can be overridden, but at a cost of CPU usage on several systems I tested. For some with decent CPUs, the overhead might be worth it, but is outside the scope of this. For now, just hit logout. Then hit ctrl+alt+backspace to force a reload of xserver. Now choose KDE, Gnome, or whatever you use for a Desktop environment for your session.

3. Try reinstalling VMWare and **make sure** you choose to install experimental 3D support. I believe it is default in current versions for you fast clickers. VMWare should be reinstalled when your kernel is upgraded, as well. This is so VMWare will compile proper kernel modules and install them to your new kernel.

4. Make sure you pasted the lines correctly and to the correct VM config file. Sounds stupid I know, but smart people overlook the seemingly small stuff.

5. Make sure VMWare tools is properly installed in the guest OS **before** enabling acceleration.

6. Make sure DirectX is properly installed in the VM and that acceleration is enabled **before** installing DirectX.

7. Type glxinfo and look for "Direct Rendering: yes" Look to see that the OpenGL and glx versions don't have the word "Mesa" in them. See how glxgears runs. For ATI users, fgl_glxgears is even better. Just type their names in konsole to use them. If your framerate is smooth and decent, then your driver is likely ok. If any of these tests bombed, try reinstalling the driver in a proper manner. 

**Info**

Note: The open source drivers don't offer the support required for this on many cards. Use the ones from the hardware vendor, especially for ATI and NVidia.

Note: Graphics card drivers may need to be reinstalled with upgrades of certain libraries. They will definitely need to be reinstalled after kernel upgrades.

A) ATI drivers tend to be buggy especially. I found fglrx 8.37.6-8.39.6 work fine for this and most other things, once you get them installed properly. This was tested in Feisty and Edgy. I recommend kernel 2.6.20.14 under Feisty with the proper kernel options commonly documented for ATI. I can give a list upon request if you seem to be having compiling or module loading issues. Uninstall via apt or the provided uninstall script, depending how you installed the driver .Backup your /etc/X11/xorg.conf file. Do a bare console login from the login screen(outside xorg).


Run the script I got from somewhere else(forget where) as such.
cd to directory of the script
sudo chmod +x install-fglrx-debian.sh
sudo sh install-fglrx-debian.sh -v *version*

Here is a link to the script. It exceeds this forum's storage space for .sh extension, so had to put it on Megaupload

[http://www.megaupload.com/?d=SKLIW7OV](http://www.megaupload.com/?d=SKLIW7OV)

Note: the script can be modified to download later drivers than 8.39.6, however, newer drivers haven't worked with my X1950 PRO XGE AGP card. They may work with other cards or other kernels than the one that traditionally best supported ATI IMO(2.6.20.14). I know some other kernels worked with older drivers, as well, just not as good of stability in other versions thus far. I found this script foolproof, unlike ATI's. Reboot and fglrx should work. Redo my test.
Try another driver version if there seems an issue.

B) NVidia users can try just reinstalling their drivers. They should be sure their kernel is either compiled with some driver modules disabled or alternatively disabling the kernel graphics drivers by editing /etc/modules. That's about all that can go wrong other than a buggy driver version with your card. NVidia's installer script is quite good :)

---

### Post by uberground on 2008-04-20
Those who received the message: 
[INDENT]Failed to construct OpenGL rendering backend.  The 3-D features of the display card will be disabled.[/INDENT]
It would've created a vmware.log file in the directory belonging to the VMWare instance you tried to run. You can read the file to find why it died, mine looks like it's because my Intel driver doesn't have a few GL functions:
[INDENT]mks| GLUtil_InstallExtensionLists: Missing extension GL_ARB_shader_objects
mks| GLUtil_InstallExtensionLists: Missing extension GL_ARB_vertex_shader
mks| GLUtil_InstallExtensionLists: Missing required extension GL_EXT_texture_compression_s3tc
mks| GLUtil_InstallExtensionLists: Missing extension GL_NV_texture_shader
mks| GLUtil_InstallExtensionLists: Missing required extension GL_EXT_framebuffer_object
mks| Finish HostDisconnect: thread mks
mks| Msg_Post: Warning
mks| [msg.glBackend.initFailed] Failed to construct OpenGL rendering backend.  The 3-D features of the display card will be disabled.----------------------------------------[/INDENT]
I'm hoping the xserver-xorg-video-intel 2.2.1 release in hardy might support these for my 945GM, but i doubt it.
UPDATE: Just ran the latest Release Candidate... no good.

---

### Post by chrislovessushi on 2008-05-18
runs excellent for me in hardy, i have the virtual computer running with 92megs of video and 512megs ram and it runs perfectly thanks to the experimental direct rendering. thanks.

---

### Post by JayFrog on 2008-05-26
Hi!

I have a working WinXP in ubuntu (VMware Player). I installed MapleStory europe - OK - but when I try running it it freezes and says GameGuard error 114. Any ideas what might be the problem?

---

### Post by 4th guy on 2008-05-26
Yes, you're running a 3D game inside a virtual machine. Try running it using wine.

---

### Post by JayFrog on 2008-05-27
> **4th guy said:**
> Yes, you're running a 3D game inside a virtual machine. Try running it using wine.

Not quite that simple: **GameGuard** (anti-cheat system of MapleStory) is not working out on Wine. There are people out there who has working MapleStory on Ubuntu, so it s possible to run it on VMware, or on any other virtual desktop enviroment. I am just wondering what I am doing wrong? I've tried couple of things but nothing seems to help - the problem remains the same (GameGuard error 114). Any thoughts? :confused:

---

### Post by 4th guy on 2008-05-28
You **can not** run a 3D application in a virtual machine, yet. Unless the game has a software mode, you're out of luck

---

### Post by SuzuZaku on 2008-06-04
My vmnet0 does not exist! How can I make it?

---

### Post by Takebacker on 2008-06-11
I can't even install the open source player. o_o

```
takebacker@takebacker-laptop:~$ sudo ./vmware-install.pl
sudo: ./vmware-install.pl: command not found

```

That's what i get. Help? :O

---

### Post by jnw222 on 2008-06-19
does this work in hardy
i use a toshiba satileite l35 (vista default)(ati card)
using qemu

---

### Post by einraz on 2008-06-21
> **ridetheteapot said:**
> I got maple running on an XP vmware server... I can play the game after i install it, but eventually the game will crash and then i have the same problem as tenchu77491 when i try to play again (except it is ALWAYS a bsod then the virtual machine restarts). The blue screen goes away too fast to read anything it says.
I tried reinstalling maple, and that fixed it until the game crashed and the same problem reoccurred. Deleting the gameguard directory so gameguard reinstalls doesn't seem to help at all.
If anyone knows whats going on here i'd love to know.

FYI for anyone who can play maple in vmware consistently, you can improve the speed a ton by killing gdm (or kdm)
```
sudo /etc/init.d/gdm stop
```
and then starting vmware in its own x server
```
sudo X :1 -ac & DISPLAY=:1 vmware
```

How can you get this to run? After I kill the gnome session, I can't type anything.

---

### Post by einraz on 2008-06-21
> **Takebacker said:**
> I can't even install the open source player. o_o

```
takebacker@takebacker-laptop:~$ sudo ./vmware-install.pl
sudo: ./vmware-install.pl: command not found

```

That's what i get. Help? :O

You're probably not in the right directory. Also, did you already extract the files?

---

### Post by jnw222 on 2008-06-22
(:oops:) I used qemu and it still says "unable to find screen mode for g2rd"
I guess i should read the first post

---

### Post by Sigiken on 2008-07-17
Thank you so much, thx to you, I can remove windows, and have everything for linux!
this was the only game that was torturing me having windows installed :) 
You're the best ;)
TYVM

Jonas

---

### Post by DonnyB4e56 on 2008-07-24
Installing Windows XP rite now (lol) I'm looking forward to playing maplestory brazil and being #1 at it :p

---

### Post by wantakill on 2008-08-02
how can you by pass the game guard? 
I got the error of game guard initializing error every time i click the Play button

---

### Post by Kileli on 2008-08-04
This is really disappointing. every post i have read points at game guard. understandable given its nature. however those private servers that do not require the use of game guard are still an issue in wine  When i run the client it loads the first two screens then drops out and this error pops up anyone know how to resolve this error?

also when i load this client using the tutorial from this thread i can hear that the game loads but all i get is a white screen anyone else have a solution for this?

---

### Post by chaostime on 2008-08-09
cheapest mesoses ,safest and fastest powerleveling in [www.8thgame.com](www.8thgame.com)

[SIZE="7"]www.8thgame.com[/SIZE]

---

### Post by cim on 2008-10-19
Maple Story works on my machine in VMWare Workstation.

Here's a list of my computer's hardware and software:

AMD Athlon 64 X2 Dual Core
ATI Radeon 2400 AGP HD 256 MB
2 x 1024 MB DDR RAM

Ubuntu 8.10 Intrepid Ipex (BETA)
VMware Workstation 6.5.0 Build-118166
ATI Restricted Drivers

:popcorn:

[IMG]http://i37.tinypic.com/28ldif6.png[/IMG]

---

### Post by Shaythong on 2008-10-20
That's awesome Cim. At least some games work in VMWare 6.5. Except some games still don't work like Halo and what not. I wonder if Direct3D works on Vista as guest instead of XP.

---

### Post by cim on 2008-10-20
It should work because I don't see why not, unless you got shitty hardware lol.

---

### Post by vahnx on 2008-11-22
Is it possible to get Maple working using VirtualBox? I'm not a fan of VMBloatWare, I mean VMWare.

---

### Post by Vozmozno on 2008-11-28
As far as I know, Virtualbox doesn't support 3d rendering yet, its a sort of new thing for VMware, so Virtualbox won't work for 3d games for now.

Oh, and thank you very much for this guide. Maplestory is really the only reason my brother even has a windows partition anymore!

---

### Post by MiguelM162 on 2009-01-02
Ok, first off this is an interesting way to get maple up and working, one problem though, how do I get a console open??

---

### Post by TrueAncalagon on 2009-01-04
Hm, I had folloed the guide but... when I star MS I got only black screen. Then, When the music begin (this mean that the game work) I see only a white screen all the time. Direct X test is ok, I have D3D enable. My openGL run properly. I have an GF 7900GS but I can't figure out how to make MS run on my system

---

### Post by TrueAncalagon on 2009-01-16
No one know what can be..hm

---

### Post by vahnx on 2009-04-12
> **Vozmozno said:**
> As far as I know, Virtualbox doesn't support 3d rendering yet,

I think it now does, or at least 3D acceleration. Is that enough to get it running?

---

### Post by benom on 2009-05-04
virtualbox supports opengl not directx and directx is what maplestory uses ;/

---

### Post by Shaythong on 2009-05-06
> **benom said:**
> virtualbox supports opengl not directx and directx is what maplestory uses ;/

Virtualbox can use some WineD3D files, but not perfectly. DirectX is supported (almost) 9.0c in VMWare Workstation.

---

### Post by goldblattster on 2009-05-16
> **MiguelM162 said:**
> Ok, first off this is an interesting way to get maple up and working, one problem though, how do I get a console open??

Dear sir, in he "ubuntu bar" go to Applications>Accessories>Terminal (that's for ubuntu and most gnome-based distros)

**EDIT:** As a matter of fact, I cannot remember knowing a linux user that does not use the command line interface.

---

### Post by goldblattster on 2009-05-16
Can anyone like, confirm that it works with vmWARE Player so I can be lazy instead of finding out for myself =D

---

### Post by vahnx on 2009-05-27
> **goldblattster said:**
> 
As a matter of fact, I cannot remember knowing a linux user that does not use the command line interface.

One of the many problems Linux will have to overcome if it wants people to use it.

As for MapleStory, anyone get it working with Ubuntu 9.04 as of yet?

---

### Post by Ferrat on 2009-06-10
Any word on this working on Ubuntu 9.04?

---

### Post by OneGamer on 2009-07-04
Hey, I'm new to the Ubuntu forums and distro. 
I'd like to make this my first post because I really enjoy this distro and I also like Maple story. I've been looking for a free way to get Maple Story to work.
The easiest way I found was to do these steps on Ubuntu Jaunty Jack distro (9.04).
1. Download and install the LATEST version of Virtual Box (3.0) on your Ubuntu System. This version supports an experimental DirectX Driver with 3D acceleration
2. Create a Windows XP Virtual Machine and install and fully update your Windows XP Virtual Machine. (CREATE A SNAPSHOT RIGHT NOW)
3. After everything is settled, start your windows xp vm client in windows safe mode by pressing f8 after the virtual box bootup screen.
4. After you enter safe mode, go to the Devices at the top of the menu for the windows xp vm client. Then select Install Guest Additions. When you go to your My Computer, you will notice that the Guest Additions have mounted themselves to your cd-rom. Install them.
5. Follow the onscreen instructions and then press "yes" to restart your system. (Don't revert to your old DirectX drivers if you still have Windows File Protection on)
6. Shutdown the virtual machine after the restart. (you now have directxvbox installed but now you need to activate your 3d acceleration)
7. In the Sun VirtualBox click on settings and then select Display on the left side. You must check the box "Enable 3D Acceleration" and increase the Video memory to a safe level for Maple Story (I do 64mb but you may be able to do 32mb, as long as it is a small fraction of your actual memory).
8. Finished. Close out the settings and run the Virtual machine.

NOTE: Hackshield will detect when you interact with ubuntu in most ways and close with a "Hack detected" notice in the few times I've fooled around with it. I think it has something to do with the mouse or alt-tabbing.

Here is a couple pics of it working (runs smoothly, almost realtime, minor jitters):
[http://home.comcast.net/~mgmicro/MapleUbuntu.png]("http://home.comcast.net/%7Emgmicro/MapleUbuntu.png")
[http://home.comcast.net/~mgmicro/VirtualMaplestory.png]("http://home.comcast.net/%7Emgmicro/VirtualMaplestory.png")

---

### Post by liamiscool on 2009-08-21
im downloading MS..why dont you deleate Gameguard? what happens (this is my first time downloading MS on ubuntu)

---

### Post by AllRadioisDead on 2009-11-23
I know Maplestory private servers were previously crashing in wine, but a test hasn't been done since wine 1.19. Since then, big improvements have been made in directx. Can someone try installing directx 9 in wine and running a private server?

---

### Post by rykel on 2009-12-13
Hi all,

I am trying to get MS working as per this thread... but unfortunately, I keep getting a "Hackshield initialization error 0x000xxxx"

Any help pleeeease?

---

### Post by emoguitarist06 on 2010-01-06
I'm Running Ubuntu 9.10 on my Compaq Presario CQ50 Notebook with Nvidia 8200M graphics and Intel DualCore Processor, and 2gbs of ram.

I have VMWare Workstation 7 installed and running Windows XP as a guest. I'm giving 800mbs of processor to the guest.

I have successfully installed maple story. Mapelstory loads and I login successfully and runs but it's really chopping. Not good enough to play a regular game. The main choppy parts are when I try and fight a moderate amount of enemies. (of course I am also choosing the least populated channels)

I also have VirtualBox and installed WineD3D and installed maple story and it gets past game guard when i start maple story but never loads the login screen.

Please help!

---

### Post by jojomuffin on 2010-04-13
errr i punched in all of the code to activate direct3d but it really isn't working...
i just stumbled uppon this article so yeah...
AAAND i kno that my computer has direct3d support cuz i ran glxgears... yeah...
hepl pl0x

---

### Post by cim on 2010-05-20
> **emoguitarist06 said:**
> I'm Running Ubuntu 9.10 on my Compaq Presario CQ50 Notebook with Nvidia 8200M graphics and Intel DualCore Processor, and 2gbs of ram.

I have VMWare Workstation 7 installed and running Windows XP as a guest. I'm giving 800mbs of processor to the guest.

I have successfully installed maple story. Mapelstory loads and I login successfully and runs but it's really chopping. Not good enough to play a regular game. The main choppy parts are when I try and fight a moderate amount of enemies. (of course I am also choosing the least populated channels)

I also have VirtualBox and installed WineD3D and installed maple story and it gets past game guard when i start maple story but never loads the login screen.

Please help!

it's not vmware or ubuntu's fault that maples story runs choppy. it's your hardware, you need better hardware in order to make the virtual OS run as if it was your native OS. in other words, more ram, better graphic card, and a bigger processor.

---

### Post by emoguitarist06 on 2010-05-25
> **cim said:**
> it's not vmware or ubuntu's fault that maples story runs choppy. it's your hardware, you need better hardware in order to make the virtual OS run as if it was your native OS. in other words, more ram, better graphic card, and a bigger processor.

Well... I guess that means I have to get a 6 core, 64 bit,16gb ram, desktop!
Muahaha!
Someday :)

---

### Post by F1R3H4CK3R on 2010-05-25
sounds cool

---

### Post by kaya33 on 2010-07-02
Hey all, firstly i would like to apologise for reviving a dead topic but ..
After being forced to use an external HDD, ubuntu 10.04 was the only compatible OS i had around.
im a big gamer, i enjoy them, css, wow, osu(!), i got them to work being a new linux user ..
but moving on to my problem -
--
I installed MS via WINE (since EU Maplestory has no gameguard - it has hackshield)
upon installing and trying to launch MS, wine complains of a missing .dll (aossdk) - so wether or not wine is compatible with Hack shield is not even a question yet - yes i have copied the said .dll to the virtual c drive - system32 folder - fail - and told wine to look native - builtin - native then built in - built in then native - basically the only solutions i could find from google failed me.
-
secondly - i used the above method - installing XP SP3 onto a virtual drive via VMWare - yes i have 3d capabilities and dx 9 - i can play other games in the virtual xp, just not maplestory - the game i attempted was osu - [http://osu.pp.sh](http://osu.pp.sh) 

so .. after launching maple via XP via VMWare - Hack shield loads, but then i get an error (quite a common1)
"Unable to connect to login server .. blah blah"
I know MS is online, my friend is sitting next to me playing it.

i have disabled the firewall in XP, no success, enabled it and told it to prompt me of blockages - no success - allowed MS as an exception - no success - reinstalled - no success - downloaded installation from different mirrors and tried above again - no success.

-
any help would be greatly appreciated on either matter, be it the missing dll problem via WINE 
or the Unable to connect to login server, i will provide a screenshot of the wine error now but i am unable to provide a screenshot of the VMWare XP Problem as i have Vista installing as a second virtual drive - my next attempt.

--
WINE : 
[http://i49.tinypic.com/2yxqgsj.png](http://i49.tinypic.com/2yxqgsj.png)
[IMG]http://i49.tinypic.com/2yxqgsj.png[/IMG]

XP VMWare (coming soon)
-- k .. same error on vista so :
[http://tinypic.com/r/e7i6hc/6](http://tinypic.com/r/e7i6hc/6)
[IMG]http://i49.tinypic.com/e7i6hc.png[/IMG]


-------

I will be checking this thread frequently so any responses will not be ignored!
Thanks in advance

---

### Post by AllRadioisDead on 2010-07-03
Maple works great, but when it tries to run full screen it resizes the VM's screen to 800x600, is there any way I can get maple to take advantage of my full screen size?

---

### Post by darkservlist on 2010-07-22
Have you tried to run it in virtualbox? 
Here's a procedure ([http://forums.virtualbox.org/viewtopic.php?f=7&t=15893](http://forums.virtualbox.org/viewtopic.php?f=7&t=15893)) to make it work on a windows host (primarily because of compatibility issues in win7 or vista host) and winxp emulation, could the same principle be used in ubuntu?

---

### Post by arik123 on 2011-06-28
> **ceeg said:**
> vmware-asdfasdf.tar.gz
```

tar xvzf vmware-asdfasdf.tar.gz
cd vmware-asdfasdf
sudo ./vmware-install.pl

```

Make sure you are in the directory with the tar.gz archive before execute the above instructions.

Sorry im a total beginner with Linux how would i get to the directory with the tar.gz archive

---

### Post by arik123 on 2011-06-29
Can any one please help

---

### Post by donhas on 2012-04-13
[SIZE=4][FONT=Comic Sans MS]You can download maplestory but you must have wine downloaded which should be automatically downloaded[/FONT][/SIZE]):P

---

### Post by donhas on 2012-04-13
> **donhas said:**
> [SIZE=4][FONT=Comic Sans MS]You can download maplestory but you must have wine downloaded which should be automatically downloaded[/FONT][/SIZE]):P
What you do is download the maplestory downloader (mse_downloader.exe) and right click and it will say open with
scroll and you should find wine

if it doesn't come up then you can install it from the ubuntu software center or the winehq website

---

