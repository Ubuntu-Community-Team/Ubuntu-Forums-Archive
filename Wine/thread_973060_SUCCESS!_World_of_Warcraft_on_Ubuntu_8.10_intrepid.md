---
title: "SUCCESS! World of Warcraft on Ubuntu 8.10 intrepid"
date: 2008-11-06
forum: Wine
---

### Post by DoubleMcLovin on 2008-11-06
This is to document my success of getting World of Warcraft (WoW) fully installed, updated, and playable as of 11-6-08. Running 64bit OS with an NVIDIA 9800GTX card under wine 1.1.7 using Windows XP compatibility mode.

    Installing proved the initial trouble, I have both the CD's and the DVD disks, neither worked on my system, neither did copying over the files. This leaves me with only 1 other option, I did the trial client installer. You can get this client by going to [http://worldofwarcraft.com]("http://worldofwarcraft.com") and signing into your account and following the links there.

Provided it took about a day and a half to run this installer fully, I had to note the patch releases and run the TBC trial downloader at the 2.4 patch mark. I was able to repeatedly update by launching WoW whenever it finished an update.

My updater reported it was behind a firewall, the downloads still continued but slowly, so to remedy this I installed "Firestarter" (available in the repos) and configured it under the "policy" tab to allow the following ports all of them marked for everyone:
```
BitTorrent  6881-6889
            6112
            3724

```
After that I forwarded these port ranges to my local machine through the router and my download speeds skyrocketed.

Now the updates installed just fine until right after the "TBC US final" patch. Then my client failed to start. I remedied this by doing the following:
```
gedit ~/.wine/drive_c/Program Files/World of Warcraft/WTF/Config.wtf
```
and finding the line```
SET gxApi "OpenGL"
``` Which didn't exist for me, so I created it. (you can also manually set your resolution in the key called "gxResolution")

After I created that string of code, I was able to open the client without a series of errors, and run the final patch, after which the game loaded seamlessly.

---

### Post by deadtom on 2008-11-06
WoW was working fine for me before the upgrade but after it's doing this.

[IMG]http://www.mtlaners.org/allen/wow/funkywow.jpg[/IMG]

I've got the video settings on the lowest possible settings. Any ideas?

---

### Post by drakkus on 2008-11-06
hmm, ive been playing wow on ubuntu for about... 8months now :S why has it taken u so long? lol

---

### Post by DoubleMcLovin on 2008-11-06
cause I just switched to Ubuntu recently =P

Deadtom did you try adding ```
SET gxApi "OpenGL"
``` to your Config.wtf file?

---

### Post by deadtom on 2008-11-06
> **DoubleMcLovin said:**
> cause I just switched to Ubuntu recently =P

Deadtom did you try adding ```
SET gxApi "OpenGL"
``` to your Config.wtf file?

Ya, that and all the other tweaks are in the registry and config.wtf. It was working flawlessly until the upgrade. Now all the terrain textures seem to be missing.

---

### Post by DoubleMcLovin on 2008-11-06
send a screenshot of your video settings. I might be able to at least guess at something then.

---

### Post by deadtom on 2008-11-07
[IMG]http://www.mtlaners.org/allen/wow/vid_settings01.jpg[/IMG]

[IMG]http://www.mtlaners.org/allen/wow/vid_settings02.jpg[/IMG]

I put everything at the lowest settings. It's weird. I wonder if a path got changed somewhere and it just can't find them or something.

---

### Post by LANT on 2008-11-07
Hello deadtom,

Try this:

- Rename your World of Warcraft/Interface/AddOns to _AddOns (to remove all addons)
- Follow the specific instructions in [wowiki troubleshooting gruide]("http://www.wowwiki.com/Troubleshooting_Wine")
- Try quiting the minimap just as you enter wow. (try it several times)
- After trying that tell us something
- Also, try to add this line to your Config.wtf file:

SET M2UseShaders "0"

Good luck!

PD: Even if you solve it by your own, post the solution as it may help other users!

---

### Post by deadtom on 2008-11-10
Ya no luck with any of that.
Just upgraded to wine 1.1.8 this morning. Still no joy.

---

### Post by Bumbulum on 2008-11-10
I'm glad you had some luck with it. I've been having trouble getting it to run after it's installed, so I'll try this stuff when I get home.

It basically just crashes when I try to start it and it says something like "the memory can not be read" blah blah blah...

---

### Post by deadtom on 2008-11-10
Ok, I uninstalled wine, deleted my .wine directory. Reinstalled wine, reinstalled wow, put the key in the registry, made all the suggested changes to the wtf file and now the ground is the only thing that is the right color.
This is with the same vid_settings as before btw.
[IMG]http://www.mtlaners.org/allen/wow/WoW-black.jpg[/IMG]

---

### Post by gerowen on 2008-11-15
In DirectX mode, my only problem is that the minimap flickers in the bottom left as I move.  In OpenGL though, I get this.

[Linkage](http://marcusadams.homeip.net/Marcus/Pictures/World%20of%20Warcraft/wowproblem.jpg)

Any suggestions on fixing either of these problems?

---

### Post by Humph on 2008-11-15
Have you tried renaming the WDB folder in the WoW directory?

---

### Post by ljerabek on 2008-12-13
For anyone who just is having too much trouble with setting up wine and making it stable should try [http://www.codeweavers.com]("http://www.codeweavers.com"). Checkout their Crossover Games product it supports WOW and it rated Gold. Pretty much promises to work. They allow for a trial download so you can make sure it works. The product supports many other games and is only like 30 bucks.

---

### Post by OrbJinzo on 2008-12-13
heh codeweavers is the same people who make wine. anyways what are you all running nvidia gfrx cards? I updated to the beta 180. biniary drivers and WoW runs great on those.

---

### Post by SmarterThanMyPhone on 2008-12-16
Running 8.10, newest version of wine, fully updated; I cannot get the login screen to show, it stays  solid black. I added the suggested lines to my config file and have the exact same result.

---

### Post by nerdking on 2008-12-16
> **deadtom said:**
> WoW was working fine for me before the upgrade but after it's doing this.

[IMG]http://www.mtlaners.org/allen/wow/funkywow.jpg[/IMG]

I've got the video settings on the lowest possible settings. Any ideas?

in wine config turn allow pixel shading off

---

### Post by YokoZar on 2008-12-16
The Wine version shipped by default in Ubuntu 8.10 is very similar to the Wine shipped in 8.04; if upgrading caused the problems for you the issue might not be in Wine but instead in the video drivers.

---

### Post by deadtom on 2008-12-16
> **nerdking said:**
> in wine config turn allow pixel shading off

Did that.

---

### Post by deadtom on 2008-12-16
> **YokoZar said:**
> The Wine version shipped by default in Ubuntu 8.10 is very similar to the Wine shipped in 8.04; if upgrading caused the problems for you the issue might not be in Wine but instead in the video drivers.

I've given up on being able to play any newer games on Linux. WoW isn't even new, it's four years old, forget playing any *actual *new games. Works great for all my day to day stuff, got no complaints. But regrettably I'll have to keep a windows box to game on.

Oh well.

---

### Post by ajackson on 2008-12-17
Have you got the registry tweak in place? If so try removing it as some people are now finding it causes problems rather than solves them.

---

### Post by Derrick106 on 2008-12-17
What you should try to is removing openGL. i have found in my experience with Wow on Linux using wine is that that so far has only made it worse my config.wtf text looks like this

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "777.000000"
SET specular "1"
SET particleDensity "1.000000"
SET spellEffectLevel "6"
SET groundEffectDensity "24"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET realmName "Akama"
SET gameTip "3"
SET VoiceActivationSensitivity "0.39999997615814"


try to make sure yours looks something like this. I once had Wow run Flawless except a little slow. right now it flashes here and there another way to help with this is copy a windows xp System and system32 .dll's to the wines "c drive". my only problem now is that when i click on the icon it wont open i have to go through like this

/home/derrick/.wine/drive_c/Program Files/World of Warcraft/Wow.exe

i am gonna try an change where the icon goes to that spot also my wine config will not open up and i have this and microsoft works installed on it. any help with that would be appriciated.

I just redirected a icon on the desktop my lancher.exe wasnt launching Wow so i went to properties->Launcher->and changed the launcher exe in the command line to Wow.exe this helped for opening it but i am still not to sure on the configuring wine part

---

### Post by deadtom on 2008-12-17
> **ajackson said:**
> Have you got the registry tweak in place? If so try removing it as some people are now finding it causes problems rather than solves them.

Yes

---

### Post by bondstorm7 on 2008-12-19
When I start the program, everything is working normally up until the point where my character enters the world. Then I get this:


[IMG]http://img88.imageshack.us/img88/9858/majorproblembm1.png[/IMG]


I have tried everything above, and a few things from other threads. Any suggestions?

Edit:

Using a Sony Viao Laptop VGN-FW139E
ATI Radeon Graphics
Intel Core 2 Duo

---

### Post by upchucky on 2008-12-19
I could be wrong here but 8.10 is not a LTS release, and it did say there were 3d graphics problem incompatabilities, since then there are new drivers at least for nvidia, but those whom venture to try this first are heroes for breaking trail.

this issue shown on the posts is the same as in the past before wine 1 went live, 

when i saw the warning about incompatibility with 8.10 i chose to not upgrade and am still playing, this only means that I am too chicken to blaze the trail, however depending on the results of those that go before me I will get bolder.

Way back when i was trying to get WOW and COH to run in wine, i had to switch to a faster ISP because of bandwith throttling, this in effect slowed down my satelite connection to the extent that I had the rendering and tearing that I see posted here.

Due to the fact that some have already gotten great results with 8.10 means that it will get better with time.

---

### Post by weezerisrock on 2008-12-20
> **bondstorm7 said:**
> When I start the program, everything is working normally up until the point where my character enters the world. Then I get this:


[IMG]http://img88.imageshack.us/img88/9858/majorproblembm1.png[/IMG]


I have tried everything above, and a few things from other threads. Any suggestions?

Edit:

Using a Sony Viao Laptop VGN-FW139E
ATI Radeon Graphics
Intel Core 2 Duo

I have this EXACT same problem on my home PC.  
its an older system but has an ATI Radeon HD2400 in it.

now the odd thing is ubuntu 8.10 is also on my laptop which has an ATI mobility Radeon x1900 and it runs flawlessly.  I'm in research mode right now, if I find anything I'll post back, but I've alredy been looking for 2 hours and no go. :(

I've done every single step in all the wow wine setups.

this problem also is present regardless of if I'm using the fglrx driver or the actual ATI Catalyst 8.12 drivers.


**UPDATE**: well want to know what it is?  you have to close your minimap before you go into a major city.  thats it.  2 reinstalls later and hours of research and thats the answer.  /sob.

Apparently ATI drivers currently have a problem with the minimap which relies on pixelshaders.  The minimap cannot draw itself (hence the white in your minimap) and hitting the x at the top of the minimap solved all, although becareful you make any changes to resolution or such it will pop back up.

---

### Post by Zackie on 2008-12-21
I'm not finding my Config.wtf and i'm not able to get to where i can log in to creat it. I've went up to View and show hidden files.. still did not show.. just runonce.wtf and runonce_WLK.wtf when the loader pops up and i click on play.. i just get a bunch of lines then this message:

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Wow\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7DAD6695

The instruction at "0x7DAD6695" referenced memory at "0x00000008".
The memory could not be "read".


WoWBuild: 9183
Settings: 
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisample "1"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "550.000000"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "24"


and way more...

---

### Post by Alexpants on 2008-12-21
I had this problem when I installed WotLK on Intrepid. 
My fix was to go into my Warcraft Folder, then into WTF, and there was nothing in there, so I created my own config file in gedit like this...

> SET gxApi "opengl"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "1"
SET installType "Retail"
SET locale "enGB"
SET movie "0"
SET showToolsUI "0"
SET portal "eu"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "51"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "450.000000"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "24"
SET accountName "YOUR ACCOUNT NAME"

saved it in my WTF folder as config.wtf then it worked straight off the bat no issues. 
All I needed to do was a teensy bit of tweaking in wine (I had sound issues which were easily solved by changing sound types) and making sure I was emulating it in Vista and I was away. 
It was a little more irritating to get WoW working in 8.10, but it is possible.
So all you need to do is create your own config.wtf file and you'll be sorted :)

---

### Post by Zackie on 2008-12-22
ROCK ON! See i did that but i guess i didn't copy it all or something haha.. but now i need to tweak the sound a wee bit.. any ideas on that!?


thanks so much!


Zackie...:guitar:


Never mind just switched it to OSS... What is sad is in windowed mode it looks better than full screen on Windowshaha.. how is this so? :P

---

### Post by EnderEcho on 2008-12-24
Everything I've been reading here has been really helpful with understanding how WoW works in Wine.

Unnnnfortunartely WoW still isn't working for me.

I've gone about running WoW 2 ways. 

I tried installing with the client. It downloaded the whole version, but when it came to the update it said enable javascript and waiting for fiels to close. I made sure none of the standard .exe were running as processes. I also tried emulating all the different available versions of windows in Wine 1.1.10. No go.

I found a sweet BASH script that gets WoW running, but only the first 2 intro videos. When it tries to go to the menu it says memory could not be written. Again trying to emulate other versions doesn't help.

I'm running Intrepid 
Version of Wine 1.1.10
My graphics card is a lowly Intel X4500HD. I imagine thats where most of my problems are coming from.

I would like to remedy the client update problem and go that route so I can get proper updates.

Again, thanks to everyone for their input so far.

---

### Post by Extol on 2008-12-24
I have tried installing it with wine. I copied all the files to a folder (1 for WoW and one for BC ). It says the following message: "No installer data could be found. If this problem persists, please contact Blizzard technical support." Anybody knows how to solve this?

---

### Post by Zackie on 2008-12-25
I know this is going to take a while but, try Installing them all from download client... It worked for me and loaded great... just takes a bit of tweaking for the Sound.. I used OSS and it sounded great.. used ALSA sounded bad.... then i loaded it all again.. and ALSA sound fine...

---

### Post by EnderEcho on 2008-12-26
So after trying many different solutions I realized I was only changing the version emulated of the wow.exe app. I changed the default settings to to NT 4.0 and while I feel foolish at least the updater is working.

---

### Post by EnderEcho on 2008-12-29
So I've installed the most updated version of the game. The problem I encounter now is that the login screen graphics are jumbled. I can't go any further because its indecipherable. I don't have an proprietary drivers installed.

I'm running ubuntu 8.10
graphics card intel 4500HD

---

### Post by PooAvenger on 2009-01-27
Ok lets help me now! lol, I have tried a bunch of these settings and nothing seems to be working. I have the registry edit on, I have tried opengl and d3d settings. When I try opengl I can see everything but it seems the screens colors are inverted. When I try d3d i can see everything...except the buttons.

Here is my lcpi:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


Here is what i have tried in the config file :

SET gxApi "opengl"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "1"
SET installType "Retail"
SET locale "enGB"
SET movie "0"
SET showToolsUI "0"
SET portal "eu"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "51"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "450.000000"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "24"
SET accountName "spacemonkey09" 

\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "777.000000"
SET specular "1"
SET particleDensity "1.000000"
SET spellEffectLevel "6"
SET groundEffectDensity "24"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET realmName "Akama"
SET gameTip "3"
SET VoiceActivationSensitivity "0.39999997615814"

I also have tried the riched20 and riched32 and added the msvcp60.dll file but can't find it in the winecfg, as well as the mfc42.dll

here's my xorg.conf:
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used
#	InputDevice	"Synaptics Touchpad"
EndSection

Here are some screenshots:
[tobeeditedin]
[[IMG]http://i80.photobucket.com/albums/j199/Benicus/th_Screenshot.png[/IMG]](http://s80.photobucket.com/albums/j199/Benicus/?action=view&current=Screenshot.png)
[[IMG]http://i80.photobucket.com/albums/j199/Benicus/th_Screenshot-1.png[/IMG]](http://s80.photobucket.com/albums/j199/Benicus/?action=view&current=Screenshot-1.png)

---

### Post by Redopz on 2009-01-28
> **SmarterThanMyPhone said:**
> Running 8.10, newest version of wine, fully updated; I cannot get the login screen to show, it stays  solid black. I added the suggested lines to my config file and have the exact same result.

im also having this same problem, and im not sure if it was solved in this thread yet

---

### Post by Mr.N00bLaR on 2009-01-28
I have downloaded the WoW installer from blizzard site. When I select Wotlk it starts the check process, during this a small error box appears but it keep going. After it finishes the EULA pops up asking to accept or decline. I scroll down and up for like 5 minutes but it wont let me accept. I am running the x64 version of 8.10 on an E5200. I don't have the discs btw. Any ideas?

---

### Post by Redopz on 2009-01-28
> **Mr.N00bLaR said:**
> I have downloaded the WoW installer from blizzard site. When I select Wotlk it starts the check process, during this a small error box appears but it keep going. After it finishes the EULA pops up asking to accept or decline. I scroll down and up for like 5 minutes but it wont let me accept. I am running the x64 version of 8.10 on an E5200. I don't have the discs btw. Any ideas?

i also had that problem, and eventually i gave up and got the trial version. Though that only seems to work with certain versions of wine (garunteed 1.0.1, and 1.1.13 doesnt work).

this thread shows what one guy did to get it working. hopefully that helps

[http://ubuntuforums.org/showthread.php?t=973060](http://ubuntuforums.org/showthread.php?t=973060)

---

### Post by Mr.N00bLaR on 2009-01-29
The trial didnt work for me either :\ but I gotta check my wine version.

---

### Post by phlack on 2009-01-29
the commonality seems apparent. . . ATI is bad on linux.

---

### Post by rfiatt on 2009-01-30
> **marcusdean.adams said:**
> In DirectX mode, my only problem is that the minimap flickers in the bottom left as I move.  In OpenGL though, I get this.

[Linkage](http://marcusadams.homeip.net/Marcus/Pictures/World%20of%20Warcraft/wowproblem.jpg)

Any suggestions on fixing either of these problems?

I have the same problem, i just installed wine 1.0.1 in Ubuntu 8.10. I've done the openGL tweak sound works great also as the login but when my character show up i have the same look than this guy.

Anyone knows how to fix this?

---

### Post by Nierfenhimer on 2009-01-30
Okay, so here's a whole new set of bull.

I'll list hardware specs later if need be, but software is, obviously Intrepid with WINE 1.1.13.

I got WoW installed via a move from an existing drive. Everything works fine. A little tweaking got the login and character select screens working flawlessly, even on the highest detail. However, no matter what, the minute I log in to any character, no matter the quality settings, the framerate never rises above 5-10 fps unless I'm in a small corridor or staring into the sun. The fps is bad enough that it's nigh unplayable and I have seen nothing on this.

Needless to say, I'm getting a little frustrated, as I have tried practically everything Google has to offer. If anyone can relate and/or suggest anything, I'll stick around and answer questions.

---

### Post by c4tly5t on 2009-01-30
i have flickering polygons across the screen in game. i have done all the opengl and regedit and config.wtf configuring please help

turion 64 bit dual, 64 bit Intrepid, ATI radeon HD 3200, 4gb ram

---

### Post by Redopz on 2009-01-30
> **Nierfenhimer said:**
> 
 A little tweaking got the login and character select screens working flawlessly, even on the highest detail. .

sorry i cant help with that, but how did you get the logon screen to work?

---

### Post by Nierfenhimer on 2009-01-30
> **Redopz said:**
> sorry i cant help with that, but how did you get the logon screen to work?

I hate to say it, but at this point, a friend of mine and I both have screwed with it so much that I'm not even sure WHAT did that.

I'll look back through the settings again, though, and paste 'em all in here.

---

### Post by Redopz on 2009-01-30
thanks

---

### Post by RAiN2M on 2009-01-30
Nice work, I'm impressed ^_^ Although I just quit World of Warcraft, haven't played in 2weeks, haha. I have a level 80 human paladin on Akama. I might install it again when the Ulduar patch is released, in a few months, this will be helpful when the time comes.

---

### Post by Nierfenhimer on 2009-01-31
Here's what I can tell you:

At the moment, the game is such that at the login screen and character select, the framerate is perfect. It also works quite well in certain small spaces, such as corridors in Undercity. However, in more wide-open areas, such as walking out into the outside world, the frame rate plummets.

Sorry I can't be more clear, but I'm not entirely sure myself of what I did. I'll give you what I can though.

I totally got rid of the Regedit hack. That's gone. 
In my WINE config, I turned off practically everything under the Graphics tab, ESPECIALLY the Vertex Shader Support and Pixel Shader. Left resolution at 96 dpi.
Also, I am NOT running under OpenGL. That seems to do mor harm than good, especially given the horrid interface lag.
Here's my current WTF config file:
For US:

SET locale "enUS"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "56"
SET gxTripleBuffer "1"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET accountName "YOUR ACCOUNT NAME"
SET movie "0"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET lastCharacterIndex "7"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "1"
SET farclip "177"
SET particleDensity "1.000000"
SET baseMip "1"
SET spellEffectLevel "0"
SET environmentDetail "0.5"
SET weatherDensity "0"
SET realmName "YOUR REALM NAME"
SET gameTip "4"
SET VoiceActivationSensitivity "0.39999997615814"
SET groundEffectDist "70"
SET textureFilteringMode "0"
SET ffxGlow "0"
SET ffxDeath "0"
SET gxVSync "0"
SET uiScale "0.79999995231628"
SET useUiScale "1"

That's about all I can think of at the moment. If you need any additional info, just ask. Until I get my MacBook's new power adapter, I'd love to get WoW working on here (the sad part is that this is built to be a gaming computer, twice as powerful as my MB, but my MB ran WoW twice as well - with a dead RAM slot to boot).

EDIT: Oh, yes, just to be clear, it's not a latency problem. My latency never goes above 20ms. I've got FiOs. I'll give hardware specs if needed.

---

### Post by Redopz on 2009-01-31
your my hero man, that worked perfectley. Ill check to see if im having the same gameplay problem as you as soon as i can get the retail version working

---

### Post by Mr.N00bLaR on 2009-01-31
I am happy that I am playing WoW now! I turned off all visual effects {System>Pref>Appearance} and replaced my config file with what you posted. I get 1/3rd the lag I did three days ago in XP and and my frame rate in colderra is ~50. It looks like butt though, when I try to set anything it will apply changes BUT the keyboard stops working. The mouse still works though, I dont wanna raid naxx in 800x600 lol.  EDIT: Doh, shoulda looked into the config files i copy and pasted... lol

---

### Post by eldutcho on 2009-01-31
I was just about to make a thread about this with my prblem when i saw this. I'm glad its somewhat workable for most people now. 
However, i have  a somehat stupid and irritating problem, right after i download the installer and i click install WoW, I have to accept the End User Agreement and scroll all the way to the bottom for the accept button to become clickable. At the bottom, the aceept buttn remains grey. This is so frustrating
any help?

---

### Post by Mr.N00bLaR on 2009-01-31
I forgot to mention in my post that I am using wine 1.1.14. That the only ver I can get it working in. Hope that helps :)

---

### Post by Redopz on 2009-01-31
> **eldutcho said:**
> I was just about to make a thread about this with my prblem when i saw this. I'm glad its somewhat workable for most people now. 
However, i have  a somehat stupid and irritating problem, right after i download the installer and i click install WoW, I have to accept the End User Agreement and scroll all the way to the bottom for the accept button to become clickable. At the bottom, the aceept buttn remains grey. This is so frustrating
any help?

i had the same thing with almost every version of wine, but 1.1.12 works :D

after i got it working, i noticed my FPS is also at 6 almost all the time, so i think it might be something in the WTF config file. I just copied and pasted your set up, so im going to start some trail and error on that tomorrow

edit: just by playing with the video settings im up to 14 normally. this still isnt amazing, but it makes it pretty bearable. Im almost on low settings, i just kept some selct stuff around halfway, and turned off the check box for glow (i forget what its called, but i didnt notice anything looking different without it, and it raised 2 fps)

---

### Post by eldutcho on 2009-02-01
> **Redopz said:**
> i had the same thing with almost every version of wine, but 1.1.12 works :D

after i got it working, i noticed my FPS is also at 6 almost all the time, so i think it might be something in the WTF config file. I just copied and pasted your set up, so im going to start some trail and error on that tomorrow

edit: just by playing with the video settings im up to 14 normally. this still isnt amazing, but it makes it pretty bearable. Im almost on low settings, i just kept some selct stuff around halfway, and turned off the check box for glow (i forget what its called, but i didnt notice anything looking different without it, and it raised 2 fps)

thanks, ill try use 1.1.12, i think i  have 1.1 right now

---

### Post by Nierfenhimer on 2009-02-01
Okay, so after I did what I did, I had it suggested that I try OpenGL again. It works! I'm up in Northrend running at a steady 12 or so fps. It isn't beautiful, but it's absolutely playable, and fairly smooth as well!

I'm glad that this worked for so many of you. Happy playing!

---

### Post by nw2lnx on 2009-02-20
I am having a problem.

I just downloaded wine and all the components as well as WoW and when I go to run WoW I get music and a messed up background.

The area were I am suppose to accept the Terms and Aggreements is black and my cursor for my desktop is still there along with the WoW cursor.

I am very new to linux and I would love some help

---

### Post by Vissigoth on 2009-02-21
I'm having problems with my sound in WoW. It works fine in all other programs, but when I play WoW there is no sound. I've tried editing the config.wtf file as recommended on WoWWiki, but nothing changes.

Do any of you guys have any suggestions?

---

### Post by sashimi123 on 2009-02-21
I have installed wine 1.1.15, ubuntu 8.10 and copied my wow installation from my old win xp. I am running on a HP nx6325.
My problem is that wow crashes even before i reach the login screen.
In the launcher i hit Play and wow crashes.
The error message from wow is: Failed to read file INTERFACE\GLUES\MODELS\UI_MAINMENU_NORTHREND\LOGIN_WURMUNDEADHEADSPEC.blp.

The problem here is that this folder do not exist.
And before copying the wow folder everything worked fine, so i believe the problem lies not in the wow folder, but somewhere else.
Could someone please help me resolve this problem?

---

### Post by tahirih on 2009-03-14
> **DoubleMcLovin said:**
> 
After that I forwarded these port ranges to my local machine through the router and my download speeds skyrocketed.




I had the exact same problem. I've done everything up to this part. so how do you forward the port ranges through the router?

---

### Post by dhammond on 2009-03-17
I suppose this is where I should ask:

I made the jump from windows xp to Intrepid Ibex yesterday, and as my first task decided to tackle installing WoW (I'll get around to ripping all of my m4p music later. blugh) and I'm having a lot of trouble with the bilzzard downloader. Any time the blizzard downloader runs, it throws up an alert box error with no text and crashes. I believe I'm using the most current version of wine as I applied all available updates.

I get the error at the following times:

a) I've successfully installed the game from my v1.0.0 disks by using the method of copying all the data onto my hard drive and running the installer. I can run the game, log in, but as soon as the client closes to start the patching process, I get the crash.

b) When I try to download the "universal client" from the blizzard website, as soon as it begins the downloader, I get the crash.

[redacted] Does anybody have any experience with this error?

Thanks.

---

### Post by Ammet on 2009-03-21
> **Vissigoth said:**
> I'm having problems with my sound in WoW. It works fine in all other programs, but when I play WoW there is no sound. I've tried editing the config.wtf file as recommended on WoWWiki, but nothing changes.

Do any of you guys have any suggestions?

Exact same problem here. 

Installed Ibex yesterday on a new, separate hard drive, and I'm running WoW via WINE 1.1.17 from my existing XP drive. The game starts and runs flawlessly, but I've got no sound in-game at all. I've gone through all the sound settings in the game and nothing has worked. The biggest annoyance is that sound with anything else I run in Ubuntu works great. I'm sure there's something I'm missing, but no idea where...

Any ideas would be greatly appreciated!

---

### Post by mutaku817 on 2009-03-21
> **Bumbulum said:**
> I'm glad you had some luck with it. I've been having trouble getting it to run after it's installed, so I'll try this stuff when I get home.

It basically just crashes when I try to start it and it says something like "the memory can not be read" blah blah blah...

I have this same problem, i have tried the game discs, copying the game over, and am trying the full client now for the 57th time it seems. Though the old client and disc tries were before i reinstalled Ubuntu because of partitioning errors. I tried the trial client like you said but my account is fully upgraded and won't let me get the trial BC or Wrath clients. If i find a way i'll let you guys know.

---

### Post by Ammet on 2009-03-21
> **Ammet said:**
> Exact same problem here. 

Installed Ibex yesterday on a new, separate hard drive, and I'm running WoW via WINE 1.1.17 from my existing XP drive. The game starts and runs flawlessly, but I've got no sound in-game at all. I've gone through all the sound settings in the game and nothing has worked. The biggest annoyance is that sound with anything else I run in Ubuntu works great. I'm sure there's something I'm missing, but no idea where...

Any ideas would be greatly appreciated!

Solved it (thanks to a Troubleshooting Wine article on wowwiki.com)... knew I was missing something. In WINE Config I had not checked one of the Audio Drivers to be used. Once I checked the appropriate driver, I've now got sound in WoW. My life is complete... ;)

---

### Post by infamousse on 2009-03-27
Ammet, can you post some images of the working uBUNTU build you have, I am about ready to throw Vista in the GARBAGE! But wanna make sure I can still game and work daily life.
Also a tutorial would be beautiful as I am working with geForce 9800GTX+ and want to get the MOST out of this ****!!!!!

---

### Post by 1BigBore on 2009-03-29
I have been trying to install WoW from the WotLK DVD with no success.  It is the only media I have and I reallly do not want to try and download the whole thing.  This is what I see when I try and install:
```

name@box:/media$ cd cdrom0
name@box:/media/cdrom0$ dir
DirectX  Installer.exe
name@box:/media/cdrom0$ wine insatller.exe
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/name/.wine' has been updated.
wine: could not load L"C:\\windows\\system32\\insatller.exe": Module not found
name@box:/media/cdrom0$ wine --version
wine-1.1.18

```
I have been looking through the forums, but I have found nothing like this.  
Hints or clues or simple answers will be greatly appreciated.

---

### Post by hikaricore on 2009-03-29
> **1BigBore said:**
> I have been trying to install WoW from the WotLK DVD with no success.  It is the only media I have and I reallly do not want to try and download the whole thing.  This is what I see when I try and install:
```

name@box:/media$ cd cdrom0
name@box:/media/cdrom0$ dir
DirectX  **Installer.exe**
name@box:/media/cdrom0$ wine **insatller.exe**
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/name/.wine' has been updated.
wine: could not load L"C:\\windows\\system32\\insatller.exe": Module not found
name@box:/media/cdrom0$ wine --version
wine-1.1.18

```
I have been looking through the forums, but I have found nothing like this.  
Hints or clues or simple answers will be greatly appreciated.

Well first of all... you're spelling Installer.exe wrong.
Second you seem to not be able to see the data files on your dvd.
This is a common issue with WotLK on Linux, something about the way Blizzard mastered the DVDs.

I'll try and find you a thread on how to properly mount that DVD so that you can read it's contents properly.  :p
In the mean time pay more attention to spelling and capitalization when entering terminal commands.

**UPDATE** Here: [http://forums.worldofwarcraft.com/thread.html;jsessionid=7CF5592C2418261769C66A4AD98B4F53.app24_04?topicId=12666297606&sid=1](http://forums.worldofwarcraft.com/thread.html;jsessionid=7CF5592C2418261769C66A4AD98B4F53.app24_04?topicId=12666297606&sid=1)
These should be the proper instructions for mounting that disc.  Best of luck to you.  :)

---

### Post by epvipas on 2009-03-30
I've been running WoW on Ubuntu for a couple of years now on and off and find it far quicker than when running the same machine in Vista. 

I tried an early alpha of Jaunty a few months ago and couldn't get it to work at all so am getting a bit nervous with the upcoming release of Jaunty as to whether to upgrade or if I'm better off staying put. 

I think from memory that last time the issue was with the NVIDIA binary drivers. 

Any thoughts from the floor?

---

### Post by hikaricore on 2009-03-30
I'm running Jaunty as my media server right now but the Nvidia drivers are working fine
and I copied my flatmate's WoW folder over to it and logged into his account.
No issues that I see with Jaunty in it's current state. :p

---

### Post by 1BigBore on 2009-03-30
> **hikaricore said:**
> Well first of all... you're spelling Installer.exe wrong.
<<snip>>  :) 
Well that could explain a lot.  Dang I hate looking stupid in front of the whold world! Would it help if I pleaded dyslexic?
If it is as simple as that then I will take my spelling lesson and the other information and try again. <slaps forehead>
Thanks for **ALL** the help.  I am at work on lunch break or I would try it right now.

--p.s.
at home, and I watched my spelling.  It is installing, and the patches are downloading....  would be done, but my wireless router >>blipped<< and I had to start the patching over.  At 80% done, and I am hoping that I do not have any graphic problems.... 
(one can always hope)
Big thanks to one and all and the guys in 
[http://ubuntuforums.org/showthread.php?t=980629&highlight=World+Warcraft&page=4]("http://ubuntuforums.org/showthread.php?t=980629&highlight=World+Warcraft&page=4")
 that helped me so much, too.

---

### Post by concon on 2009-03-30
yeah mine like starts up and i put it in windowed mode my editing the config file. and i have added all the other things like opengl to the file and it still wont work. it opens wow, then it shows the wow login screen with a big black square in the middle of it where the login should be. pleeeeease tell me how to fix this. i tried to guess where the things should be but no luck. i cant just type my stuff in either because i need to complete the user agreement thing first. pleeeeeeeeeeeeeease help.
=con

---

### Post by epvipas on 2009-04-05
Thanks for the info on Jaunty. Did the upgrade yesterday and logged into WoW and within 10 seconds it crashed. Initially thought it was going to be a major problem but then I disabled all my addons and it's really stable. Just reenabling all the addons one by one until I find out which one is crashing the system. Hopefully it won't be anything that important that I can't live without.

---

