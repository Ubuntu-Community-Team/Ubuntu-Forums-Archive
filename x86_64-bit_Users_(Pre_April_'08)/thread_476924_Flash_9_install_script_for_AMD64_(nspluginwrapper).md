---
title: "Flash 9 install script for AMD64 (nspluginwrapper)"
date: 2007-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kilz on 2007-06-17
[COLOR="Red"]**This post has been replaced in the new 64bit section. [Please post in the new post.]("http://ubuntuforums.org/showthread.php?t=772490") This post will no longer be supported.**[/COLOR]

**[SIZE="4"][COLOR="Sienna"]Nspluginwrapper Install Script for Dapper-Gutsy(Updated 3/8/08 )[/COLOR][/SIZE]**
This script will install the nspluginwrapper, and Flash for your 64bit browser for the **amd64 version of Ubuntu** Dapper, Edgy and Feisty, and Gutsy. It will not work on the i386 or 32bit version. 
It will not install other plugins. There are other plugins, java being one, that nspluginwrapper can not work with. The script has been updated on 8/21/07. It no longer uses alien on Feisty, and it will clean out previous installs. I have also made a script that installs the old flash plugin that seems to work better than the new one. 
[Click here for the script that installs the previous r48 plugin]("http://home.comcast.net/~ubuntume/oldflash-0.1.5-1.tar.gz") **[COLOR="DarkRed"](recommended Dapper-Gusty)[/COLOR]** 
or
[Click here if you want to download the script for r124 Flash plugin.]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.6-2.tar.gz") [COLOR="DarkRed"]**(recommended Gutsy-Hardy)[/COLOR]**

If the script works for you please consider clicking this thank you icon.  [[IMG]http://i9.photobucket.com/albums/a74/tghc/thanks.png[/IMG] ]("http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=4589989") 

Due to the problems with Flash and Gutsy the script has been modified to install flash and set it up for gutsy using the nspluginwrapper package in the Gutsy repo's.

The script also works with the 64bit builds of [Swiftweasel]("http://sourceforge.net/projects/swiftweasel/"), an optimized build of Firefox.

**[SIZE="4"][COLOR="Sienna"]Instructions[/COLOR][/SIZE]**
1. Download the script.
2. Right click on the tar.gz and select "Extract Here"
3. Close **all **browsers.
4. Inside the folder that extracts is a "GetFlash" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done.  :D

SD-Plissken has pointed out that users of the Fluxbox desktop may need to open a terminal and launch the script by navigating to it and using this command to launch the script.
```
sudo ./GetFlash
```
**[SIZE="4"][COLOR="Red"]How to get help (Please Read Before Making a Post)[/COLOR][/SIZE]**
If you have any problems and need help Please read the included README file for instructions on what information to report in your post. **[COLOR="Red"]Do not repeatedly install the script or try other methods until you have read the sections below and *made a post*.[/COLOR]**

**[SIZE="4"][COLOR="Sienna"]Common Issues[/COLOR][/SIZE]**
[SIZE="3"]**Sound**[/SIZE]
First download and double click on [this package]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") to install it.
Gutsy - People using Gutsy that have sound problems [should read this thread.]("http://ubuntuforums.org/showthread.php?t=655825")

[SIZE="3"]**Sessions**[/SIZE]
Please make sure to start a new browser session if you run into any issues.

[SIZE="3"]**Other Flash Plugins. **[/SIZE]
If after installing the script you cant see flash. Make sure that all attempts at installing other flash plugins (Gnash, swfdec, etc)  have been uninstalled and the files they created have been removed. The remains of past failed attempts are the #1 cause of flash not working. This is because the files conflict with the flash plugin.

[SIZE="3"]**Firefox 3 Beta's **[/SIZE]
This script sets up flash for the 2.0 series of firefox, Firefox 3 beta will also work, but you will need to link the plugins. [This post gives info on the Beta 3.]("http://ubuntuforums.org/showthread.php?t=695674") You may need to edit the commands if your Firefox beta folder is in another place. Forum member kurtpete offers some additional help [in this post.]("http://ubuntuforums.org/showpost.php?p=4359542&postcount=826")

[SIZE="3"]**What to Include in your Post **[/SIZE]
When asking for help, please include the results of the following commands.
```
ls -al /usr/lib/mozilla//plugins/
ls -al /usr/lib/firefox/plugins/
uname -a
```

[SIZE="3"]**Unmet Dependencies ia32-libs**[/SIZE]
Users with any of the following errors during install are [directed to this post.]("http://ubuntuforums.org/showpost.php?p=4417385&postcount=914")
The ******* in rthe following error is a wildcard that represents any package name.
```
The following packages have unmet dependencies:
********: Depends: ******** but it is not going to be installed
```
or
```
nspluginwrapper depends on ia32-libs; however:
Package ia32-libs is not installed.

```
[SIZE="3"]**Remove Script**[/SIZE]
[This link]("http://home.comcast.net/~ubuntume/RemoveScript.tar.gz") will download the removal script. Extract the file, then double click on the RemoveScript file and select run in terminal. This script is unnecessary if you are having issues getting the script to work. Its only use is to completely remove the applications from the script. This is counterproductive when people cant get the script to work because it removes clues as to what worked and what didnt.

[SIZE="3"]**Hardy Heron**[/SIZE]
This script is not setup to work with Hardy Heron. If ```
sudo apt-get install flashplugin-nonfree
``` does not install flash. Make a post on the Hardy Heron section of the forum and (**most important**)[ file a bug report on launchpad.]("https://launchpad.net/ubuntu") Part of running a Beta is reporting the bugs so they can be fixed.

---

### Post by Snargledorf on 2007-06-18
Thank you so much for this. Ive had 64bit ubuntu before and the only problem i had with it was the painfull process of installing flash so now this make it easy thanks once again!

---

### Post by capecove on 2007-06-18
Kilz, do you think this will stop those posts about how Flash won't work in 64 bit Ubuntu? ;) Thank you sir...

---

### Post by j0eb0b on 2007-06-18
Kilz,

Your script works perfectly with Firefox 64.  For some reason Swiftfox 64 doesn't recognize Flash on my system and I still get the plugin error.  Not a biggy in any way but as part of my learning process, where do I start to troubleshoot?  

As an interesting aside, Firefox 64/ Swiftweasel download remarkably faster than Firefox over XP.  With my primitive ADSL connection (Verizon) I never exceed @90 kbps with a 32 bit version of Firefox using XP.  The same websites will download between @150 to 175kbps using Firefox 64/Swiftfox over Ubuntu.  Any opinion regards the performance differential?  Do others see this type of improvement?  

Joe

---

### Post by capecove on 2007-06-18
Yes, I sure do. I have a cable modem connection and also see an improvement. I literally went from 150kbps to at least 270kbps on the HP.com website, over a consistent period of time. 

Now, does this prove anything? Not necessarily. It is possible HP added some more bandwidth/server power at the same time I switched. However, I would not rule out the OS either. It is possible that it could be several things. Remember, Windows registry settings influence broadband capability/throughput. I would say that this could be one easily explained avenue...

---

### Post by Cappy on 2007-06-18
> **j0eb0b said:**
> Kilz,
As an interesting aside, Firefox 64/ Swiftweasel download remarkably faster than Firefox over XP.  With my primitive ADSL connection (Verizon) I never exceed @90 kbps with a 32 bit version of Firefox using XP.  The same websites will download between @150 to 175kbps using Firefox 64/Swiftfox over Ubuntu.  Any opinion regards the performance differential?  Do others see this type of improvement?  


I noticed this also, but no one believes me because "it is impossible" to download faster than a Windows OS. I assume it happens because Linux manages the TCP Stack much better and linux may set the internet settings automatically on a need-to-set basis that Windows needs a "internet optimizer" to set once (and those always made the problem worse for me on Windows).

I would get 600 KB/s max from any amount of servers on Windows, but I've seen upto 900 KB/s on Linux. I'm only paying for 600 KB/s though =P

---

### Post by rivera151 on 2007-06-18
This plugin wrapper script is great.  Firefox 64 needed flash player bad!

---

### Post by oldlucky on 2007-06-19
Good job thanks Mate works well.:p

---

### Post by firefeather on 2007-06-19
Thanks so much for the script! I really appreciate your post and your script. :KS  I am one of those who was pulling out my hair because of problems with getting nsplugin, gnash, swf_player, and other browser installs to work. I hope you can get this put into the community documentation or something, because it's so helpful!

---

### Post by ahickey on 2007-06-19
Another very happy customer.
I thought I wouldn't miss Flash, but I was wrong.

Thanks so much for doing the hard part to make it easy for me.

---

### Post by toecutter on 2007-06-21
As I put in the other thread (didn't know about this thread at the time) your script is lovely and VERY appreciated! So nice to be able to go to Flash sites at home now :)

Will your script be put into the Ubuntu Guide to make it semi-official? Who do we contact to suggest this?

---

### Post by Kilz on 2007-06-21
> **toecutter said:**
> As I put in the other thread (didn't know about this thread at the time) your script is lovely and VERY appreciated! So nice to be able to go to Flash sites at home now :)

Will your script be put into the Ubuntu Guide to make it semi-official? Who do we contact to suggest this?

I have no idea if it will, or who to contact. I wouldnt mind it being there if it helps more people find the help they need to get flash running.

---

### Post by FloSynergy on 2007-06-21
kilz,
your script rocks!

thanks and 
be well,

flo

---

### Post by il-luzhin on 2007-06-21
A thousand thank yous.

---

### Post by penvzila on 2007-06-21
Still don't have sound in flash.  Anyone else fix this on their machine?

---

### Post by FloSynergy on 2007-06-22
hey, sorry bout that....

i'm still trying to get my machine to produce any sound apart from the buzz of fans and the crunch of cpu....


good luck! 
flo

---

### Post by The Brain on 2007-06-24
Thanks Kilz, take a bow, you're a star !

---

### Post by supersonicdarky on 2007-06-27
i tried both your scripts (ndiswrapper and installing firefox32) and manual ndiswrapper installation. it only works right after installing. once i restart the browser, none of the flash displays, though it doesnt say that plugin is missing.

=/

---

### Post by Kilz on 2007-06-27
> **supersonicdarky said:**
> i tried both your scripts (ndiswrapper and installing firefox32) and manual ndiswrapper installation. it only works right after installing. once i restart the browser, none of the flash displays, though it doesnt say that plugin is missing.

=/

Ok, Are you trying Firefox32 or are you trying nspluginwrapper? You are aware that a nspluginwrapper wrapper Flash plugin and the Flash plugin installed with Firefox32 can not co exist, right?

---

### Post by jusmurph on 2007-06-28
> **penvzila said:**
> Still don't have sound in flash.  Anyone else fix this on their machine?

This fixed my issue:

```
 Originally Posted by Gabriel Pastor
I had the same problem with feisty and solved it.
I have 2 sound cards, and it seems that sometimes the wrong sound card is the default sound device.

$ sudo asoundconf list
Names of available sound cards:
Intel
CA0106

The first one is integrated on the motherboard, and the second one (an audigy) is the one I use.

To solve the problem, I just set the default sound card to the audigy:
$ sudo asoundconf set-default-card CA0106

Then the sound works !
Hope it helps.
```

---

### Post by supersonicdarky on 2007-06-28
> **Kilz said:**
> Ok, Are you trying Firefox32 or are you trying nspluginwrapper? You are aware that a nspluginwrapper wrapper Flash plugin and the Flash plugin installed with Firefox32 can not co exist, right?no i am not aware =(

how can i remove them both and try one by one

---

### Post by gdlx on 2007-06-28
Thank you for the script. I have been wrestling with this for several weeks. Your script worked in about two minutes. I hope I will learn more about Ubuntu by reading and understanding the script.
:)

---

### Post by Kilz on 2007-06-28
> **supersonicdarky said:**
> no i am not aware =(

how can i remove them both and try one by one

Nspluginwrapper - Search and remove all instances of the npwrapper.libflashplayer.so file. Open synaptic, search and remove the nspluginwrapper and nspluginwrapper-i386 packages. 

Firefox32 - Open Synaptic and search for Firefox32 and ia32-lib-firefox. Then delete the /usr/lib32/firefox32 and /usr/local/firefox32 folders.

Lastly, if you need (or will ever need) a java plugin, there is no safe way except Firefox32. If that is the case, start with Firefox32.

---

### Post by Kilz on 2007-06-28
> **gdlx said:**
> Thank you for the script. I have been wrestling with this for several weeks. Your script worked in about two minutes. I hope I will learn more about Ubuntu by reading and understanding the script.
:)

Shell scripting is one of the things I like most about Linux. Take a look, its basically commands you would type into the terminal.

---

### Post by Bashed on 2007-06-28
For whatever reason, this is just not working for me at all.  I did not get errors and ran just as explained, with browser closed, Restarted, still cannot view flash, tried youtube.com to test.

I have 64bit Firefox v2.0.0.4

---

### Post by Bashed on 2007-06-28
I tried again and saw this real quick

16:34:31 (16.75 KB/s) - `nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm' saved [51010/51010]

sudo: alien: command not found
sudo: alien: command not found
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
--16:34:31--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.210.70

---

### Post by Kilz on 2007-06-28
> **TalkJesus said:**
> I tried again and saw this real quick

16:34:31 (16.75 KB/s) - `nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm' saved [51010/51010]

sudo: alien: command not found
sudo: alien: command not found
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
--16:34:31--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.210.70

It looks like alien isnt installing on your computer.
```
sudo apt-get install alien
``` should install it for you. 
Please give me some details about your computer to understand why it isnt installing.
1. Are you running Ubuntu, or Kubuntu, Xubuntu, or Edbuntu?
2. What version of Ubuntu (or above) are you running (Feisty Fawn, Edgy Eft, Gutsy Gibon) ?

---

### Post by Bashed on 2007-06-29
I installed alient, then tried again.

I tried youtube and still did not show installed. Then I noticed the Ubuntu software update icon which listed the nspluginwrapper, I attempted to install and got this error

E: /var/cache/apt/archives/nspluginwrapper_0.9.91.4-2ubuntu2_amd64.deb: trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386

I'm using Ubuntu Gutsy, Firefox 2.0.0.4

---

### Post by Kilz on 2007-06-29
> **TalkJesus said:**
> I installed alient, then tried again.

I tried youtube and still did not show installed. Then I noticed the Ubuntu software update icon which listed the nspluginwrapper, I attempted to install and got this error

E: /var/cache/apt/archives/nspluginwrapper_0.9.91.4-2ubuntu2_amd64.deb: trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386

I'm using Ubuntu Gutsy, Firefox 2.0.0.4

I suggest going to the Gutsy Development section with this problem. It appears that nspluginwrapper has packages in Gutsy. Let the people doing the development know nspluginwrapper isnt working so they can fix it. In fact file a bug on launchpad.

---

### Post by JAmerican on 2007-06-30
Works great but audio doesn't work. My VLC and Music Player play fine with clear sound. But all Flash still is silent.

Any suggestions?

JAmerican

---

### Post by Kilz on 2007-06-30
[Try this package]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") to see if it helps.

---

### Post by JAmerican on 2007-06-30
> **Kilz said:**
> [Try this package]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") to see if it helps.

Nope. Still doesn't work. Should I reset my PC or desktop. If not, then it still doesn't work.

EDIT: I reset my desktop and still didn't work.

Thanks for your help and hard work.

JAmerican

---

### Post by JAmerican on 2007-06-30
To give you a better idea of my hardware specs and situation as well as steps I took to resolve my audio issue, look here...

[http://ubuntuforums.org/showthread.php?t=487167](http://ubuntuforums.org/showthread.php?t=487167)

JAmerican

---

### Post by Kilz on 2007-06-30
> **JAmerican said:**
> To give you a better idea of my hardware specs and situation as well as steps I took to resolve my audio issue, look here...

[http://ubuntuforums.org/showthread.php?t=487167](http://ubuntuforums.org/showthread.php?t=487167)

JAmerican

Take a look in my signature for my Firefox32 howto. In the Flash section there are a few more things that may help with sound. One other thing, Flash is still 32bit, we are using a wrapper to get it to work , but its still 32bit. Do you have the ia32 packages installed like ia32-libs and linux32?

---

### Post by JAmerican on 2007-06-30
I installed all of those. I am looking through the guide you made but I am afraid installing something 32-bit audio drivers will ruin my audio on my machine. Its happened before. If you have any other specific recommendations, that would be great.

Thanks

JA

---

### Post by Kilz on 2007-06-30
> **JAmerican said:**
> I installed all of those. I am looking through the guide you made but I am afraid installing something 32-bit audio drivers will ruin my audio on my machine. Its happened before. If you have any other specific recommendations, that would be great.

Thanks

JA

I dont suggest installing any 32bit drivers on that page, at least I dont remember it anyplace there.

---

### Post by JAmerican on 2007-06-30
> **Kilz said:**
> I dont suggest installing any 32bit drivers on that page, at least I dont remember it anyplace there.

I installed all the libs under Manual How-To, deb file in the firefox area, followed the steps in the Flash 9 area except for the Flash 7 stuff. I don't have Firefox 32 on my PC. Didn't try any Java yet. Wanted to fix flash first.

Anything else I should have done? Video still smooth. No audio. My media players working fine.

JAmerican

---

### Post by Kilz on 2007-06-30
> **JAmerican said:**
> I installed all the libs under Manual How-To, deb file in the firefox area, followed the steps in the Flash 9 area except for the Flash 7 stuff. I don't have Firefox 32 on my PC. Didn't try any Java yet. Wanted to fix flash first.

Anything else I should have done? Video still smooth. No audio. My media players working fine.

JAmerican

Nope, you have done all that I can think of right now. But let me caution you about a few things. There is no safe java for the 64bit browser. The only plugin for 64bit  is the java-gcj-compat-plugin. It runs without a security manager. I dont recommend it unless you dont care about security. 
If you choose to install the Firefox32 setup to get java (Firefox32 uses sun's java), the nspluginwrapper wrapped plugin will make the Flash plugin in Firefox32 not work. You will have to remove the wrapped plugin for the non wrapped one to work.
But I would be interested in seeing if java had sound.

---

### Post by JAmerican on 2007-06-30
> **Kilz said:**
> Nope, you have done all that I can think of right now. But let me caution you about a few things. There is no safe java for the 64bit browser. The only plugin for 64bit  is the java-gcj-compat-plugin. It runs without a security manager. I dont recommend it unless you dont care about security. 
If you choose to install the Firefox32 setup to get java (Firefox32 uses sun's java), the nspluginwrapper wrapped plugin will make the Flash plugin in Firefox32 not work. You will have to remove the wrapped plugin for the non wrapped one to work.
But I would be interested in seeing if java had sound.

Look at this...

```

ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint

```

I just got this when running YouTube in Firefox32 via Terminal. I checked and I am missing that file.

Not sure where to get it so I am going to look through older libraries for it.

JAmerican

---

### Post by Kilz on 2007-06-30
> **JAmerican said:**
> Look at this...

```

ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint

```

I just got this when running YouTube in Firefox32 via Terminal. I checked and I am missing that file.

Not sure where to get it so I am going to look through older libraries for it.

JAmerican

I looked at the [ubuntu package site]("http://packages.ubuntu.com/"). The file doesnt exist.
I did take a look with google and found this
[http://ubuntuforums.org/archive/index.php/t-338934.html](http://ubuntuforums.org/archive/index.php/t-338934.html) that might be helpful.

---

### Post by JAmerican on 2007-06-30
> **Kilz said:**
> I looked at the [ubuntu package site]("http://packages.ubuntu.com/"). The file doesnt exist.
I did take a look with google and found this
[http://ubuntuforums.org/archive/index.php/t-338934.html](http://ubuntuforums.org/archive/index.php/t-338934.html) that might be helpful.

Yea I saw that. Doing it right now. Hope it clears up all this confusion.

Tks 

JAmerican

---

### Post by JAmerican on 2007-06-30
I don't get it.

I get the same error???

I seriously need some help.

JAmerican

---

### Post by Viewtifulj on 2007-06-30
Worked on the first try. Thanks for script.

---

### Post by kzm. on 2007-06-30
i have a question.. did anybody got the standalone working as well??* or did it come with the Kilz script?

* if not.. how would i got it may be working..

---

### Post by JAmerican on 2007-06-30
I couldn't get it to work so I reinstalled Ubuntu on my root partition. Keeping all my files and background intact while giving me a fresh OS to work with. I installed only the nspluginwrapper and it worked :).

If your having trouble, I suggest you try this method although you will need to reinstall media plugins and possibly some other things that install to the root partition. 

That is if you have a root partition which is seperate from your /home partition to begin with.

JAmerican

---

### Post by Delirious on 2007-07-01
Works awesome, just wanted to say thanks!

---

### Post by Linux_Punk on 2007-07-03
Yes thanks for doing al the hard work for me as well. Stupid Adobe refuses to make one. thansk for everyone who contributed to this!!! I love Ubuntu

---

### Post by rajeev1204 on 2007-07-03
Hi

Strangely flash seems to hang up my browser 70 % of the time .

Dont know if its a problem with flash or nspluginwrapper .

The flash beta version behaved without issues . 

Anyone have that beta libflashplayer.so please give it to me :)


Maybe i can test it out .




thanks

---

### Post by Kilz on 2007-07-03
> **rajeev1204 said:**
> Hi

Strangely flash seems to hang up my browser 70 % of the time .

Dont know if its a problem with flash or nspluginwrapper .

The flash beta version behaved without issues . 

Anyone have that beta libflashplayer.so please give it to me :)


Maybe i can test it out .


thanks

I would suggest making sure the beta files are completely removed from your system.

---

### Post by 7Aaron7 on 2007-07-04
:lolflag:

thanks a million for the script!!!!!!!!

any chance of working your magic on shockwave?

\\:D/

---

### Post by Ralob on 2007-07-04
This script is definitely awesome. Thanks so much, I love it :)

---

### Post by kzm. on 2007-07-06
is it just me, or does someone else also experience flash content not responding to mouseclicks quite often?

is it possible to change the player to the debugger version?

---

### Post by Bashed on 2007-07-06
Has anyone gotten this installed in gutsy tribe 2?

Software update showed the nsplugin wrapper available as an update, but during install
it gives off this error...

E: /var/cache/apt/archives/nspluginwrapper_0.9.91.4-2ubuntu2_amd64.deb: trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386

---

### Post by Kilz on 2007-07-06
> **TalkJesus said:**
> Has anyone gotten this installed in gutsy tribe 2?

Software update showed the nsplugin wrapper available as an update, but during install
it gives off this error...

E: /var/cache/apt/archives/nspluginwrapper_0.9.91.4-2ubuntu2_amd64.deb: trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386

This script does not support Gutsy as Gutsy has its own nspluginwrapper packages. I suggest posting on the [Gutsy Development forums]("http://ubuntuforums.org/forumdisplay.php?f=238") and filing a bug report on launchpad so that the developers have time to make sure everything works before it is released. 
Gutsy is under development for these very reasons, to give people a chance to test it and report the problems so that they can be fixed. This will benifit all 64bit users in the long run.

:D

---

### Post by Kilz on 2007-07-06
> **kzm. said:**
> is it just me, or does someone else also experience flash content not responding to mouseclicks quite often?

is it possible to change the player to the debugger version?

This script only installs the flash plugin and the nspluginwrapper. The wrapper is only beta software. I recommend [contacting the developer]("http://gwenole.beauchesne.info/projects/nspluginwrapper/") with any problems experenced actualy running Flash with the wrapper.

---

### Post by ubersolid on 2007-07-06
thnx kilz, script wrkd like a charm!

---

### Post by Hershey on 2007-07-06
Updated your script for Gutsy Tribe 2 when I upgraded my from Feisty.  I haven't tested anywhere else though or on a fresh install.

```

#!/bin/bash

#make working directory
sudo mkdir /tmp/nsplugwrapper

#move to working directory
cd /tmp/nsplugwrapper

#remove old packages installed from the Feisty script (can comment out if new install)
sudo apt-get -y remove nspluginwrapper nspluginwrapper-i386

#install needed packages
sudo apt-get -y install nspluginwrapper

#Get Flash and place it
sudo wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
sudo tar -xzvf install_flash_player_9_linux.tar.gz
sudo mv -f /tmp/nsplugwrapper/install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins/
sudo mv -f /tmp/nsplugwrapper/install_flash_player_9_linux/flashplayer.xpt /usr/lib/mozilla/plugins/

#make wrapped plugin
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/firefox/plugins/

#Clean up files
sudo rm -fdr /tmp/nsplugwrapper

#warn to restart browser
 echo
 echo
 echo
 echo
 echo "The plugin wrapper has been installed"
 echo "You will need to restart Firefox for the changes to take effect"

```

---

### Post by Satyrservice on 2007-07-08
Oh Might Kilz.. Giant fabulous brain of knowlege humbly on bended knee
i beseach thee

since your last hints and scripts have worked so smoothly 9flashplayer) and Lo, without flaw
I am shaMED to ask
what about shockwave?
the test page
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)
shows i now have  flashplayer but need 
shockwave
the plugin finder service window says
Unknown  plugin (application/x-director)
the find manually leads me to a page that kind seems to believe i am using netscape instead of fire fox and redirect me to the recommended browser page with firefox listed.

gawd I'm so new! semi ex Mac user
um i am uing Kubuntu feisty fawn
and fire ox 2.0.0.4
now I am off to the Alter to sacrifice two cups worth of organic Sumatra beans

thnks

---

### Post by Paul820 on 2007-07-08
I have been meaning to install the 64bit Ubuntu feisty for a while now and i finally got round to it. Someone recommended doing a search for the script written by Kilz, i got it and ran it, wow, thank you very much for taking the time to make this for us. Really appreciated. :)

---

### Post by marco123 on 2007-07-08
Thank you very, very much for this script!

I'm now 64 bit!  Yay. :)

---

### Post by weird_c00kie on 2007-07-09
awesome! thank you so much for this! :D

---

### Post by aussietrias on 2007-07-10
I want to thank you for this script and instructions, it let me who is new get it going with no fuss.

---

### Post by scorpion_gr on 2007-07-10
You are the bestest !!:popcorn:

Thanks for the script!

---

### Post by DavidVanCan on 2007-07-11
Works great.
----------
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)

---

### Post by Judo on 2007-07-12
Thank you very much.  I was using nspluginwrapper before, but due to one of my own hacks, it wouldn't reinstall.  Your script worked perfectly.

Just a heads up for anyone that's looking for alternatives: Gnash partly worked and swfdec did not work at all.

---

### Post by kansei on 2007-07-12
On Gutsy is it seriously as easy as just marking nspluginwrapper for installation? sweet deal!

thanks for the work!

It appears as though this does not work in Gutsy still. I filed a quick bug report, there's probably a duplicate but I search and searched to no avail.

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/125681](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/125681)

I'd say it's a pretty high priority thing because you have to run a hackjob of a web browser to have flash working otherwise.

edit: it's resolved already. the package 'installed', but the symlink in the firefox plugins folder was broken, as the package didn't install any files. golden now :)

---

### Post by gimmy_bond on 2007-07-14
I am new to ubuntu. I did follow the steps. However when I try to open it in the command line as instructed, the pop up window "open files" with 2 windows below "available applications" & "recent applications" are empty. Unfortunately I don't know what to type in to open the command line, so it will execute this installation.
Please guide me step by step.

thanks

---

### Post by thewizard5001 on 2007-07-15
When I run your script, I get an error:

/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: symbol lookup error: /usr/lib32/libpango-1.0.so.0: undefined symbol: pango_font_des
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
mv: cannot stat `/home/travis/.mozilla/plugins/npwrapper.libflashplayer.so': No such file or directory
ln: creating symbolic link `/usr/lib/mozilla-firefox/plugins/npwrapper.libflashplayer.so' to `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': File exists

No Flash :(

My friend just gave me his 32 bit libs so I guess I don't have the required dependencies of libpango-1.0.so.0 and I don't know any easy way to download and install them

---

### Post by Kilz on 2007-07-15
> **thewizard5001 said:**
> When I run your script, I get an error:

/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: symbol lookup error: /usr/lib32/libpango-1.0.so.0: undefined symbol: pango_font_des
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
mv: cannot stat `/home/travis/.mozilla/plugins/npwrapper.libflashplayer.so': No such file or directory
ln: creating symbolic link `/usr/lib/mozilla-firefox/plugins/npwrapper.libflashplayer.so' to `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': File exists

No Flash :(

My friend just gave me his 32 bit libs so I guess I don't have the required dependencies of libpango-1.0.so.0 and I don't know any easy way to download and install them

You need the ia32-libs-gtk.deb, it should be in synaptic, or [you can get it here]("http://packages.ubuntu.com/feisty/libs/ia32-libs-gtk").

---

### Post by dallag on 2007-07-15
Ok! man, this script the best, very fast and simple..   Good work! thanksss!!
Valeu meu chapa muito bom esse script, rápido e simples. Bom Trabalho..... Obrigado:guitar:

---

### Post by Mr_bleu on 2007-07-15
> **gimmy_bond said:**
> I am new to ubuntu. I did follow the steps. However when I try to open it in the command line as instructed, the pop up window "open files" with 2 windows below "available applications" & "recent applications" are empty. Unfortunately I don't know what to type in to open the command line, so it will execute this installation.
Please guide me step by step.

thanks
Applications>Accessories>Terminal

---

### Post by thewizard5001 on 2007-07-15
> **Kilz said:**
> You need the ia32-libs-gtk.deb, it should be in synaptic, or [you can get it here]("http://packages.ubuntu.com/feisty/libs/ia32-libs-gtk").

I found out that ia32-libs-gtk was not fully installed, so I installed it and re-ran the script and now it works!

Thanks for putting the time into making this great script!

---

### Post by kruppe on 2007-07-15
I am eternally greatful. This simplifies my job at work.

---

### Post by b05q on 2007-07-16
thank you!

---

### Post by boywander on 2007-07-25
Having another crack at Ubuntu with the 64 bit version of Feisty (will update the profile in a minute). This has helped make it a complete breeze. I thank you, sir. =D>

---

### Post by philidox on 2007-07-31
You are the man, thx!!!!

---

### Post by Snipersnest on 2007-07-31
Thank you for this updated script...it helped me out big time!

---

### Post by art_erickson on 2007-07-31
If one is not too bright and doesn't read the part that says "At present this script dose not work in Gutsy Gibbon. Gusty has its own nspluginwrapper packages." what does one do to reverse the effects of the script?

I now get an update notice for nspluginwrapper but when I try to install it I get the error message "E: /var/cache/apt/archives/nspluginwrapper_0.9.91.4-3ubuntu1_amd64.deb: trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386"

Yes, it's my fault - let the lashings begin.  What do I need to delete?

Will an apt-get command (perhaps with the -f option) work?

---

### Post by Kilz on 2007-07-31
> **art_erickson said:**
> If one is not too bright and doesn't read the part that says "At present this script dose not work in Gutsy Gibbon. Gusty has its own nspluginwrapper packages." what does one do to reverse the effects of the script?

I now get an update notice for nspluginwrapper but when I try to install it I get the error message "E: /var/cache/apt/archives/nspluginwrapper_0.9.91.4-3ubuntu1_amd64.deb: trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386"

Yes, it's my fault - let the lashings begin.  What do I need to delete?

Will an apt-get command (perhaps with the -f option) work?

That may work, removing the nspluginwrapper packages would also be a good idea. 
:D perhaps I should make that warning in giant bold red letters lol.
Last question, why are you running an alpha version of Ubuntu?

---

### Post by ouzas on 2007-08-02
Thank you so much for this script. Just yesterday i clean-installed ubuntu amd64. I was a bit afraid of formatting ubuntu x86 (although i used ghost before the format). I had installed ubuntu x86 the first time from the alternate cd (which is fine...) but i could not believe how easy it was installing from the live cd!!! The mounting and the partitioning of the drive is SOoooo easy.

When it booted to the ubuntu desktop i thought the install never actually occured (!!). Everything looked the same as before! I did not format my "/home" partition... 
I began installing packages and all the applications had their configurations intact! Wonderful!

The only thing that i had to do from scratch was the flash in Firefox. I downloaded the script and run the commands one-by-one to understand what were they doind. The simple ones like moving files etc etc i can understand, but some i have no idea not only what are they for, but also why...

Could you please explain what do they do and why. I am still not familiar with all the folders of the OS and their purpose and some commands like the 'linking' stuff ...

Comments on Ubuntu 64: 

It feels faster even when opening applications like mp3/avi players and not only with heavy duty dvd ripping like i have read in this forum somewhere...

It definitely worths spending the time to install.

If someone knows why amarok is slow when going to the next track. It uses 80% of the processor for a brief 3 seconds!!! Is it because it is a KDE application and i have gnome?? Can i do soomething about it? Install KDE packages maybe? And Kaffeine too!

Thanks everybody in advance. Sorry to be so verbal. (Both excited about Ubuntu amd64 and full of questions!)

---

### Post by Kilz on 2007-08-02
> **ouzas said:**
> Thank you so much for this script. Just yesterday i clean-installed ubuntu amd64. I was a bit afraid of formatting ubuntu x86 (although i used ghost before the format). I had installed ubuntu x86 the first time from the alternate cd (which is fine...) but i could not believe how easy it was installing from the live cd!!! The mounting and the partitioning of the drive is SOoooo easy.

When it booted to the ubuntu desktop i thought the install never actually occured (!!). Everything looked the same as before! I did not format my "/home" partition... 
I began installing packages and all the applications had their configurations intact! Wonderful!

The only thing that i had to do from scratch was the flash in Firefox. I downloaded the script and run the commands one-by-one to understand what were they doind. The simple ones like moving files etc etc i can understand, but some i have no idea not only what are they for, but also why...

Could you please explain what do they do and why. I am still not familiar with all the folders of the OS and their purpose and some commands like the 'linking' stuff ...

Comments on Ubuntu 64: 

It feels faster even when opening applications like mp3/avi players and not only with heavy duty dvd ripping like i have read in this forum somewhere...

It definitely worths spending the time to install.

If someone knows why amarok is slow when going to the next track. It uses 80% of the processor for a brief 3 seconds!!! Is it because it is a KDE application and i have gnome?? Can i do soomething about it? Install KDE packages maybe? And Kaffeine too!

Thanks everybody in advance. Sorry to be so verbal. (Both excited about Ubuntu amd64 and full of questions!)

This script, unlike the firefox32 script, is fully noted. There are notations explaining exactly what the code is for. If you have any questions about a section feel free to ask. 
The linking, or symlink is a nice thing. Linux is able to set up links that act and redirect to the orignal without taking up much space. Like say a folder full of files, you can setup a link to it and when you click on it, the folder full of files will open.
As far as kde apps on gnome, yes the brief resource hogging is probably because its a kde application running on gnome.

---

### Post by ouzas on 2007-08-02
Thank you for your reply. I understood the script almost completely. nspluginwrapper makes firefox to believe that the .so file is "64-bit" ? 

The script first places the .so file to /usr/lib/mozilla/plugins/.
After that nspluginwrapper takes the previous file and makes a new one and places it to  ~/.mozilla/plugins/ by the name of "npwrapper.libflashplayer.so". So we move this new compatible file back to /usr/lib/mozilla/plugins/ and we make a link of this file to /usr/lib/mozilla-firefox/plugins directory. (As i can see the whole folder is a link to /usr/lib/firefox.

The thing is that libflashplayer.so was not replaced. The wrapped plugin has a new name. How does firefox know which one to use???

By the way, i figured out that amarok is a bit slow some times because it is a KDE app. CAn i do anything to speed KDE apps? I like amarok very much. It's the best player ever. Listen is pretty fantastic, but there is a bug. I noticed that for no apparent reason in ONE folder (Linkin' Park - Meteora) it recognizes only 4 songs!!! I haven't checked all my music folders actually to see if this happens any place else... (no time to spare...)

---

### Post by Kilz on 2007-08-02
> **ouzas said:**
> 
The thing is that libflashplayer.so was not replaced. The wrapped plugin has a new name. How does firefox know which one to use???


The orignal plugin is only 32bit, so the 64bit browser cant use it. I'm not 100% sure why it doesn't try to use it, I'm just happy that it doesn't.

---

### Post by ouzas on 2007-08-02
I'm as happy as you because something like that could be a dealbreaker for amd64 Ubuntu install. I use the web a lot in my office and as everyone i like youtube :P .

---

### Post by art_erickson on 2007-08-03
My apologies, I missed your question about why I was running an alpha version of the Big U.

The answer is difficult - stupidity :)  More accurately, I started with 7.04 and had great results, then I destroyed my drive - actually, the formatting of it.  When I recovered I had the choice between re-installing 04 or 10.  I opted for the newer one because of the new features (Beryl - Compiz - Fusion, whatever it is), Firefox 3, and some other thing I can't remember right now.  Now, later, I learn it is only possible to upgrade U to a new version with an install, and all the associated configuration of apps and OS.  Perhaps I was misinformed.

The fact it is an alpha doesn't bother me because I can boot into XP if necessary.  I am not one of the typical Windows haters, I just like competition (I used Red Hat on dialup - has it been 5 years already?).  I do miss the Adobe Flash interface to use You Tube (that worked in the 32 bit 7.04 version) but it is not a show stopper.  You Tube is interesting but not a necessity.

Perhaps it is important to note that I was a technician before personal computers were in existence (but after "mini" computers).  I have worked on many forms of electronic equipment (using computers frequently along the way) and still have a love for technology.  Old?  Yes.  Dead?  No.  I have dabbled in many disciplines (I have worked for both Texas Instruments and IBM) but never specialized in any.  If I was a programmer I would probably volunteer to help with one app or another.  All I can do at this point is to offer to test.  My difficulty has been finding a forum to post my observations.

Btw, I manually deleted the directories (folders, whatever they are called now) and files created by the script.  Interestingly the GUI for U is better at that  than the command line (permission issues) - off to trash they went.  There may have been an argument to pass to the script to do that but it was not obvious to me, nor offered.  Yes, red letters can not hurt :)

---

### Post by flick on 2007-08-04
Just wanted to say thank you, Kilz. Script worked flawlessly, am happily watching my beloved "Ask a Ninja" clips.

---

### Post by sayuki288 on 2007-08-04
nice man this realy helped me alot

---

### Post by Kilz on 2007-08-04
> **flick said:**
> Just wanted to say thank you, Kilz. Script worked flawlessly, am happily watching my beloved "Ask a Ninja" clips.

:D Gatta love "Ask a Ninja" . That is one seriously funny dude.

---

### Post by ctalgo on 2007-08-04
First off, I'm new to Linux.  a friend turned me on to it and so far im very impressed.  The lack of flash however has been driving my girlfriend and me to a certain extent nuts.  

Im sure threre is a VERY simple answer to this question...

When i double click the script, nothing happens.  I can see that a process begins in the system monitor but no other evidence shows that anything is happening.  

Any help would be great.

cheers,
Chris

---

### Post by Kilz on 2007-08-04
> **ctalgo said:**
> First off, I'm new to Linux.  a friend turned me on to it and so far im very impressed.  The lack of flash however has been driving my girlfriend and me to a certain extent nuts.  

Im sure threre is a VERY simple answer to this question...

When i double click the script, nothing happens.  I can see that a process begins in the system monitor but no other evidence shows that anything is happening.  

Any help would be great.

cheers,
Chris

Right click on the script, click on Properties, click on the permissions tab. Make sure the box next to "Allow executing file as program" is checked, not a - bit a check. Click close. Double click on file and choose "Run in Terminal". When the terminal closes its done. Restart your browser.

---

### Post by dreadnought on 2007-08-05
Another excellent script, well done Kilz.

---

### Post by ff123 on 2007-08-08
Works great.  One comment -- In order for all users to be able to use it, I changed the permissions on /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so to 777.  It was set to 700 under the userid I installed it under.

---

### Post by jdelcom on 2007-08-08
Thanks, it worked GREAT!!!

---

### Post by Butthead on 2007-08-08
Heh, how about one that works nicely with Dapper and Konqueror for us stubborn die-hards? :confused:

---

### Post by bilbravo on 2007-08-09
Thanks again, work s great!

---

### Post by hackle577 on 2007-08-09
I downloaded and ran the script and Flash worked fine... until I closed Firefox. Now it doesn't appear at all. I think I need to get 64-bit FF, but I'm not sure how. I just installed it from Add/Remove...

I'm pretty new to 64-bit....

---

### Post by ethos101 on 2007-08-09
Something is wrong.  I followed the instructions the hard way, before I found the script, and it worked great.  Flash was working like a charm.

Since I restarted the computer (and possibly some automatic updates) flash no longer works.  So I downloaded your script.  It still doesn't work.

Any idea what happened?

---

### Post by Kilz on 2007-08-09
> **ethos101 said:**
> Something is wrong.  I followed the instructions the hard way, before I found the script, and it worked great.  Flash was working like a charm.

Since I restarted the computer (and possibly some automatic updates) flash no longer works.  So I downloaded your script.  It still doesn't work.

Any idea what happened?

Nope, other than you have some conflicting files from 2 different methods. you might want to search for multiple instances of the npwrapper.libflashplayer.so file.

---

### Post by Kilz on 2007-08-09
> **hackle577 said:**
> I downloaded and ran the script and Flash worked fine... until I closed Firefox. Now it doesn't appear at all. I think I need to get 64-bit FF, but I'm not sure how. I just installed it from Add/Remove...

I'm pretty new to 64-bit....

Please open up a terminal. Paste this in, and copy/paste the results into a reply.
```
ls -al /usr/lib/mozilla/plugins/
```

---

### Post by hackle577 on 2007-08-10
> **Kilz said:**
> Please open up a terminal. Paste this in, and copy/paste the results into a reply.

```
total 6980
drwxr-xr-x 2 root root     4096 2007-08-09 17:26 .
drwxr-xr-x 3 root root     4096 2007-04-15 07:58 ..
-r--r--r-- 1 1003 users     856 2007-06-19 20:31 flashplayer.xpt
-rwxr-xr-x 1 1003 users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 root root       36 2007-08-07 01:18 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root       37 2007-08-07 01:18 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root       34 2007-08-07 01:18 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root       35 2007-08-07 01:18 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root       36 2007-08-07 01:18 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root       37 2007-08-07 01:18 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root       42 2007-08-07 01:18 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root       43 2007-08-07 01:18 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 adam adam    69696 2007-08-09 17:26 npwrapper.libflashplayer.so
lrwxrwxrwx 1 root root       61 2007-08-09 17:26 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so
```

---

### Post by Kilz on 2007-08-10
> **hackle577 said:**
> ```
total 6980
drwxr-xr-x 2 root root     4096 2007-08-09 17:26 .
drwxr-xr-x 3 root root     4096 2007-04-15 07:58 ..
-r--r--r-- 1 1003 users     856 2007-06-19 20:31 flashplayer.xpt
-rwxr-xr-x 1 1003 users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 root root       36 2007-08-07 01:18 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root       37 2007-08-07 01:18 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root       34 2007-08-07 01:18 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root       35 2007-08-07 01:18 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root       36 2007-08-07 01:18 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root       37 2007-08-07 01:18 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root       42 2007-08-07 01:18 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root       43 2007-08-07 01:18 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 adam adam    69696 2007-08-09 17:26 npwrapper.libflashplayer.so
lrwxrwxrwx 1 root root       61 2007-08-09 17:26 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so
```

Somehow, the flash plugin got owned by 1003 and the wrapped plugin by adam. Try this
```
sudo chown -R adam:users /usr/lib/mozilla/plugins
```

---

### Post by hackle577 on 2007-08-10
Still not working. :-( Output of "ls -al /usr/lib/mozilla/plugins/" is as follows:

```
total 6976
drwxr-xr-x 2 adam users    4096 2007-08-10 17:24 .
drwxr-xr-x 3 root root     4096 2007-04-15 07:58 ..
-r--r--r-- 1 adam users     856 2007-06-19 20:31 flashplayer.xpt
-rwxr-xr-x 1 adam users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 adam users      36 2007-08-07 01:18 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 adam users      37 2007-08-07 01:18 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 adam users      34 2007-08-07 01:18 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 adam users      35 2007-08-07 01:18 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 adam users      36 2007-08-07 01:18 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 adam users      37 2007-08-07 01:18 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 adam users      42 2007-08-07 01:18 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 adam users      43 2007-08-07 01:18 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 adam users   70120 2007-08-10 17:24 npwrapper.libflashplayer.so

```

EDIT: I tried running your script again just to see if it would work. It didn't, but after that the system updates icon appeared. I clicked on it and it said it couldn't index updates or something, and it told me to run "sudo apt-get install -f", so I did. I noticed that one of the packages it was installing was "ia32[something]". I've read about this before but I'm not sure where...

---

### Post by Kilz on 2007-08-10
> **hackle577 said:**
> Still not working. :-( Output of "ls -al /usr/lib/mozilla/plugins/" is as follows:

```
total 6976
drwxr-xr-x 2 adam users    4096 2007-08-10 17:24 .
drwxr-xr-x 3 root root     4096 2007-04-15 07:58 ..
-r--r--r-- 1 adam users     856 2007-06-19 20:31 flashplayer.xpt
-rwxr-xr-x 1 adam users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 adam users      36 2007-08-07 01:18 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 adam users      37 2007-08-07 01:18 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 adam users      34 2007-08-07 01:18 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 adam users      35 2007-08-07 01:18 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 adam users      36 2007-08-07 01:18 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 adam users      37 2007-08-07 01:18 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 adam users      42 2007-08-07 01:18 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 adam users      43 2007-08-07 01:18 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 adam users   70120 2007-08-10 17:24 npwrapper.libflashplayer.so

```

If you type ```
about:plugins
``` into the browser address bar. Does a page show with a flash section like the attached screenshot? If so copy and paste that section into a reply, or attach a screen shot.
Secondly, please do this command. ```
sudo apt-get -y install ia32-libs ia32-libs-gtk linux32 lib32asound2
``` and report any errors.
Lastly, what version number of the script did you install?

---

### Post by hackle577 on 2007-08-10
I tried the latest version (yesterday's update). I also attached a screen of my "about: plugins" page.

"sudo apt-get -y install ia32-libs ia32-libs-gtk linux32 lib32asound2" indicates that all the packages were already installed and the latest versions.

---

### Post by Kilz on 2007-08-10
> **hackle577 said:**
> I tried the latest version (yesterday's update). I also attached a screen of my "about: plugins" page.

"sudo apt-get -y install ia32-libs ia32-libs-gtk linux32 lib32asound2" indicates that all the packages were already installed and the latest versions.

It says flash is enabled. Please give me a link to a page that doesnt work, and please post a screen shot of it.

---

### Post by hackle577 on 2007-08-10
Here's a screen of a random YouTube video page.

Linky: [http://www.youtube.com/watch?v=Lyf4rfT7bHU&NR](http://www.youtube.com/watch?v=Lyf4rfT7bHU&NR)

---

### Post by Kilz on 2007-08-10
You have a conflicting npwrapper.libflashplayer.so file someplace on your computer outside of the /usr/lib/mozilla/plugins/ folder. You need to do a search, as it could be in a lot of different places, and remove all but the one in /usr/lib/mozilla/plugins/ .
Locations it might be in are
/usr/lib/firefox/plugins
/usr/lib/mozilla-firefox/plugins - if the /usr/lib/mozilla-firefox is not a symlink
~/.mozilla/plugins

But its possible there may be more. [Especialy if you installed nspluginwrapper manually before then symlinked it in.]("http://ubuntuforums.org/showpost.php?p=3150303&postcount=1")

---

### Post by hackle577 on 2007-08-10
I searched for the file and found another one in /usr/lib/firefox/plugins. I deleted it, but now going to YouTube tells me "Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player." The missing plugins toolbar appears as well.

---

### Post by hackle577 on 2007-08-10
Success! I just re-downloaded your script and ran it again, works fine. Thanks for all the help!

Just out of curiousity, I searched for npwrapper.libflashplayer.so again and it turned up two results. I attached a screenshot of them. Is that the way it's supposed to be, or... ?

---

### Post by Kilz on 2007-08-10
> **hackle577 said:**
> Success! I just re-downloaded your script and ran it again, works fine. Thanks for all the help!

Just out of curiousity, I searched for npwrapper.libflashplayer.so again and it turned up two results. I attached a screenshot of them. Is that the way it's supposed to be, or... ?

Yes, one is a symlink.

---

### Post by hackle577 on 2007-08-11
I started up my computer this morning and it doesn't work. :-( Going to a YouTube vid gives me the missing plugin toolbar and the text saying I have an old Flashplayer installed. I tried just downloading your script and running it again but that didn't work.

---

### Post by hackle577 on 2007-08-11
Hmm, I got it working again but I'll have to test and see if it will go away every time I restart...

---

### Post by Snipersnest on 2007-08-11
2 quick questions... 

Is your script download on the first post updated to work with Gusty Tribe 4 64bit?
 Or do I have hunt down the script in the 100 posts to pull the updated version?

---

### Post by ethos101 on 2007-08-11
> **Kilz said:**
> You have a conflicting npwrapper.libflashplayer.so file someplace on your computer outside of the /usr/lib/mozilla/plugins/ folder. You need to do a search, as it could be in a lot of different places, and remove all but the one in /usr/lib/mozilla/plugins/ .
Locations it might be in are
/usr/lib/firefox/plugins
/usr/lib/mozilla-firefox/plugins - if the /usr/lib/mozilla-firefox is not a symlink
~/.mozilla/plugins

But its possible there may be more. [Especialy if you installed nspluginwrapper manually before then symlinked it in.]("http://ubuntuforums.org/showpost.php?p=3150303&postcount=1")

How do I create a symlink in /usr/lib/mozilla-firefox/plugins?  That may be my problem.  I copied the file to both /usr/lib/mozilla/plugins AND /usr/lib/mozilla-firefox/plugins because I don't know anything about symlinks.
-edit- nevermind... search reveales everything...  ;)

That was it.  That fixed my issue.  Thanks for the hints.  :D

---

### Post by eskarthic on 2007-08-11
I installed the flash plugin.
when I open youtube, I get the following error message

Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player.

what am I missing? please help.

Thanks,
karthic

---

### Post by Kilz on 2007-08-11
> **Snipersnest said:**
> 2 quick questions... 

Is your script download on the first post updated to work with Gusty Tribe 4 64bit?
 Or do I have hunt down the script in the 100 posts to pull the updated version?

No you just have to read the first post. Paying close attention to the [SIZE="4"]large[/SIZE] **bold** [COLOR="Red"]RED[/COLOR] letters.

---

### Post by Kilz on 2007-08-11
> **eskarthic said:**
> I installed the flash plugin.
when I open youtube, I get the following error message

Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player.

what am I missing? please help.

Thanks,
karthic

please tell me step, by step exactly what you did, what version you installed, and also what version of Ubuntu you run.

---

### Post by hackle577 on 2007-08-11
The script seems a bit hit or miss with my machine. Three times now Flash has just disappeared. Running the script reinstalls it, but sometimes it still stops working even when I'm in the middle of watching a Flash video! Hmm...

---

### Post by Kilz on 2007-08-11
> **hackle577 said:**
> The script seems a bit hit or miss with my machine. Three times now Flash has just disappeared. Running the script reinstalls it, but sometimes it still stops working even when I'm in the middle of watching a Flash video! Hmm...

It may be possible that you have a conflicting file from [your previous attempts at the manual install of nspluginwrapper by another method]("http://ubuntuforums.org/showpost.php?p=3150303&postcount=1"), . Did you remove all the files you installed? Did you remove all the files you created? These can cause problems.
Secondly, if the flash video freezes in the middle of playing it could be for a number of reasons not related to the wrapper. Your internet connection, the server sending the video, and a hundred other reasons not connected to the wrapper could make this happen. That you see the video shows that the wrapper is there and so is the plugin.
Third, nspluginwrapper is beta software, if videos freeze, if the flash quality is bad, or other problems. It is best to file a bug report with the person working on the wrapper. 

Your files are installed. Thats all the script does.

---

### Post by cwrann on 2007-08-12
I have feisty fawn with AMD 64. I am new to linux. I just installed flash 9 and it works great, thank you so much.

---

### Post by eskarthic on 2007-08-12
I have AMD64X2 laptop. I have ubuntu 7.04. I have installed the 64 bit version. I have downloaded the (nspluginwrapper) script steps given in the first page. I restarted the browser. Flash didn't work. anything that I am missing? Please advice.

---

### Post by hackle577 on 2007-08-12
Did you have your browser closed when you ran the script?

---

### Post by jusmurph on 2007-08-12
It comes out as a broken package?

---

### Post by Kilz on 2007-08-12
> **eskarthic said:**
> I have AMD64X2 laptop. I have ubuntu 7.04. I have installed the 64 bit version. I have downloaded the (nspluginwrapper) script steps given in the first page. I restarted the browser. Flash didn't work. anything that I am missing? Please advice.

Please copy/paste the results of this command in a terminal
```
ls -al /usr/lib/mozilla/plugins/
```

Also what version of the script did you run?

---

### Post by jusmurph on 2007-08-13
> **jusmurph said:**
> It comes out as a broken package?

Fixed.

I just got the deb from getdeb.net and edited the script to skip the nspluginwrapper install.

---

### Post by marshcast on 2007-08-13
Wicked. Thank you.

I was having a real nightmare trying hundreds of different ideas, both my own and from forums, but this is the DBlks.

here's to ubuntu, and straightforward answers to straightforward questions!

;)

---

### Post by Eion on 2007-08-13
Im not on my Linux comp right now (due to the fact that im 200 miles away from it :lolflag:) but this will be a first when I get back.  Im supprised this isn't stickied yet.  It needs to be!

---

### Post by Jyorke on 2007-08-13
I'm a super n00b and this thread was a lifesaver...you are my savior

---

### Post by puppybeard on 2007-08-14
Thanks a million for putting this up.
Running flash was the first brick wall I've encountered since installing Ubuntu.
I need to use Flash for would-be professional reasons but I also want to spent as much time in Ubuntu as possible.

---

### Post by Sockerdrickan on 2007-08-14
Priceless script.

---

### Post by OperatorC on 2007-08-15
> **Kilz said:**
> Right click on the script, click on Properties, click on the permissions tab. Make sure the box next to "Allow executing file as program" is checked, not a - bit a check. Click close. Double click on file and choose "Run in Terminal". When the terminal closes its done. Restart your browser.

Okay, so I just installed Kubuntu earlier today and this is my first time with Linux. I'm running the 64 version just fine except for the issue with Flash.. which is why I'm in this thread. Now, I downloaded the script and I have the GetFlash icon sitting on my desktop. I go to double click on it, as instructed, but nothing happens. Each time I do click on the file, the icon seems to expand (animation) but nothing happens (nothing is opened). If I right click on the icon and click on open it still does nothing. i've tried opening it up with Konsole and still, nothing.

I went ahead and right clicked on the file and looked at the Permissions tab like you suggested here. I didn't see a check mark near anything called "Allow executing file as program" but there is a box checked called "is executable." For Owner it says "Can Read & Write," and for Group and Others it says, "Can Read."

EDIT: Okay, so I got it to work by simply going to Run Command and the wrapper works perfectly! Thanks! I still wonder why double clicking on a script doesn't work for me though.

---

### Post by FearTheSmurf on 2007-08-15
Hi I am a semi noob to all this:)

I have been trying to get Ubuntu on my main machine for about 3 days now (been running it on my laptop for 3months now) The main sticking point I have is the flash player in firefox, now under 32 and 64bit Feisty Fawn using this script with my Nvidia AGP Gefore4 card it all works great but with my PCI-E X1900XTX (same machine I have a 939Dual Sata supports PCI-E x16 and AGP x8.

All I get is a screen where it looks like it wanted to load but the play button is stuck in the middle of the screen and nothing happens. Am I barking up the wrong tree should I be looking at the ATI drivers instead?

Thx in advance for any help:)

---

### Post by fatsheep on 2007-08-15
Thanks for the great script.  It worked for me.  :)

---

### Post by leathco on 2007-08-16
Excellent post.  Simple install and it worked.  Hopefully one day all software installs in Linux will be this easy.

---

### Post by DARKGuy on 2007-08-16
Nice script indeed! I had flash working in 30 seconds indeed ;) (yay I went 64-bit after all :P).

The script had errors with the last apt-get though, saying it couldn't install nspluginwrapper because it depended on gsfonts-x11 and ia32-libs-sdl so after installing it I had to do an apt-get install -f to fix it.

Keep it up :P

---

### Post by Kilz on 2007-08-17
> **DARKGuy said:**
> Nice script indeed! I had flash working in 30 seconds indeed ;) (yay I went 64-bit after all :P).

The script had errors with the last apt-get though, saying it couldn't install nspluginwrapper because it depended on gsfonts-x11 and ia32-libs-sdl so after installing it I had to do an apt-get install -f to fix it.

Keep it up :P

I added the packages to the script so that they get installed before nspluginwrapper.

---

### Post by jusmurph on 2007-08-17
I got to say thank you on another level.

When I opened up the script and had a look I got to learn a few things. For Example, how easy bash scripts are and for the last week I have been playing around having both good and momentary scary experiences....


```
The following packages will be REMOVED:
  alacarte bug-buddy contact-lookup-applet deskbar-applet ekiga evolution
  evolution-data-server evolution-exchange evolution-plugins firefox
  firefox-gnome-support gaim gnome-applets gnome-control-center gnome-panel
  gnome-session gnome-terminal gnome-user-guide libcamel1.2-10 libebook1.2-9
  libedata-book1.2-2 libedataserverui1.2-8 libnspr4 libnss3 nautilus
  nautilus-cd-burner nautilus-sendto ubuntu-desktop ubuntu-docs yelp
```


:lolflag:

---

### Post by musicarvind on 2007-08-17
Thanks for the scripts. installed with a breeze. only thing is that when i try youtube.com, it says either i do not have macromedia flash or i have an older version.  any reason for this? or do i need to reboot?

---

### Post by Kilz on 2007-08-17
> **jusmurph said:**
> I got to say thank you on another level.

When I opened up the script and had a look I got to learn a few things. For Example, how easy bash scripts are and for the last week I have been playing around having both good and momentary scary experiences....

Thats cool, its how I learned a lot, reading other scripts. Just to pass along a bit of advice , never,never,never,never,never,never,never,never,never,never,never,never,never,never,never,never,never,never,never,never,never,never,never,never, put rm -rfd /* in a script. I remember thinking it would delete things in the directory it was in. It ended up eating my install. From then on I tested scripts in a virtual machine, vmware is a great tool.

> **musicarvind said:**
> Thanks for the scripts. installed with a breeze. only thing is that when i try youtube.com, it says either i do not have macromedia flash or i have an older version.  any reason for this? or do i need to reboot?

Please read the howto again.

---

### Post by AegisTalons on 2007-08-17
So occasionally flash for me will have problems. I have to click off of the flash window and click back on to actually register the click. What I'm wondering is there a way I can completely uninstall flash, hopefully you have a script for that. Then reboot, and then give your script a try again. Thanks Kilz.

---

### Post by Wynne G Oldman on 2007-08-17
Thank you Sir.  It's nice to be able to view something through a 64 bit browser that you can't with Vista64 bit.

---

### Post by subru77 on 2007-08-18
I just do not know how to thank you. It just worked like dream. I was trying my best to get away from Windows, you made it easier. 

Keep up the good work!!!

Subbu

---

### Post by Kilz on 2007-08-19
> **AegisTalons said:**
> So occasionally flash for me will have problems. I have to click off of the flash window and click back on to actually register the click. What I'm wondering is there a way I can completely uninstall flash, hopefully you have a script for that. Then reboot, and then give your script a try again. Thanks Kilz.

The latest version of th script removes flash and the wrapper if installed before installing flash and the wrapper.

---

### Post by Dimitriid on 2007-08-19
Hello. Any special instructions for Kubuntu Feisty amd64? I tried both scripts, the first wont work and the second asks y/n to download the plug in but is stuck there even if I choose y then enter.

---

### Post by Kilz on 2007-08-19
> **Dimitriid said:**
> Hello. Any special instructions for Kubuntu Feisty amd64? I tried both scripts, the first wont work and the second asks y/n to download the plug in but is stuck there even if I choose y then enter.

Please refer to the first post for the "How to get Help" information.

---

### Post by carmi on 2007-08-19
I had an interesting problem while running the script.
I left the script running (at the download stage) and went to bed. In the morning my computer  was running but the keyboard and mouse were not waking up the computer, and the monitor was not receiving a signal. (On the keyboard the caps lock button would not light up when I pressed the key.)

I turned off my computer with the power button. Turned it back on. Ran firefox, went to youtube and could watch videos. I never got any error that something had gone wrong.

This might have nothing to do with the script but I thought I should report it. Otherwise the script worked very well.

Evan

---

### Post by Kilz on 2007-08-19
> **carmi said:**
> I had an interesting problem while running the script.
I left the script running (at the download stage) and went to bed. In the morning my computer  was running but the keyboard and mouse were not waking up the computer, and the monitor was not receiving a signal. (On the keyboard the caps lock button would not light up when I pressed the key.)

I turned off my computer with the power button. Turned it back on. Ran firefox, went to youtube and could watch videos. I never got any error that something had gone wrong.

This might have nothing to do with the script but I thought I should report it. Otherwise the script worked very well.

Evan

Thanks for posting, but the script just installs packages, runs a simple command , and moves a plugin in place. Im not sure what in it could make it do what you report.

---

### Post by Dimitriid on 2007-08-20
> **Kilz said:**
> Please refer to the first post for the "How to get Help" information.

Yes sorry about that here are the commands and results

ls -al /usr/lib/mozilla/plugins

```
total 6900
drwxr-xr-x 2 root root     4096 2007-08-19 13:21 .
drwxr-xr-x 3 root root     4096 2007-08-19 13:20 ..
-r--r--r-- 1 1003 users     856 2007-06-19 19:31 flashplayer.xpt
-rwxr-xr-x 1 1003 users 7040036 2007-06-19 19:31 libflashplayer.so

```

ls -al /usr/lib/firefox/plugins

```
total 20
drwxr-xr-x 2 root root  4096 2007-08-19 13:21 .
drwxr-xr-x 5 root root  4096 2007-08-19 14:03 ..
-rw-r--r-- 1 root root 11072 2007-07-31 08:29 libunixprintplugin.so
lrwxrwxrwx 1 root root    52 2007-08-19 13:21 npwrapper.libflashplayer.so -> /us         r/lib/mozilla/plugins/npwrapper.libflashplayer.so

```

ls -al /tmp/nsplugwrapper

```
misanthrope@misanthrope-laptop:~$ ls -al /tmp/nsplugwrapper
ls: /tmp/nsplugwrapper: No such file or directory

```

I think we've found the culprint, can I do the install for it manually or I need the script? cause it does not seems to be working for some reason.

---

### Post by iltofa on 2007-08-20
I _REALLY_ tried almost everithing before using your script (or manually install nspluginwrapper and Flash), but nothing satisfied me. 

Other plugins gave me problems such as :
keyboard stop working viewing a page with a flash embedded
errors in displayng a flash

This one works! 

Thanks
Diego

---

### Post by Kilz on 2007-08-20
> **Dimitriid said:**
> I think we've found the culprint, can I do the install for it manually or I need the script? cause it does not seems to be working for some reason.

It looks like the nspluginwrapper package wasnt installed. But we cant tell for sure because  the /tmp/nspluginwrapper directory is empty. It shouldn't be if you ran the script in the how to get help tarball.
So Im going to recommend that you run that script and then redo the commands just to make sure.

---

### Post by kipman725 on 2007-08-20
so easy! I am very much in your debt. Thanks.

---

### Post by Dimitriid on 2007-08-20
> **Kilz said:**
> It looks like the nspluginwrapper package wasnt installed. But we cant tell for sure because  the /tmp/nspluginwrapper directory is empty. It shouldn't be if you ran the script in the how to get help tarball.
So Im going to recommend that you run that script and then redo the commands just to make sure.

Problem solved, the repository website for the nspluginwrapper timed out the connection before finishing yesterday but unfortunately I closed the terminal wthout noticing that first. After retrying it resumed, but stopped one more time. Tried a third time and it went through ( managed to squeeze it out at 1kbps but it finished after a while ) and now I can see flash.

Thank you!:popcorn: Now unto installing wine, a little off topic but is it best to just try to install the version on the repositories of kubuntu feisty amd64bit?

---

### Post by Kilz on 2007-08-20
> **Dimitriid said:**
> Problem solved, the repository website for the nspluginwrapper timed out the connection before finishing yesterday but unfortunately I closed the terminal wthout noticing that first. After retrying it resumed, but stopped one more time. Tried a third time and it went through ( managed to squeeze it out at 1kbps but it finished after a while ) and now I can see flash.

Thank you!:popcorn: Now unto installing wine, a little off topic but is it best to just try to install the version on the repositories of kubuntu feisty amd64bit?

Go to the [wine hq ]("http://www.winehq.com/")and look in the download section. There will be a page for Ubuntu. They have their own repository you can add and a 64bit Feisty deb.

---

### Post by mcook2 on 2007-08-21
Hi,

Just rebuilt my Feisty x64 system, so doing the Flash install thing again.

Using the current version of your script, nspluginwrapper-install-0-1.4.tar.gz.tar.

There are 2 versions of GetFlash in the download folder: GetFlash and GetFlash~.

GetFLash failed with messages as belowunable to get the nspluginwrapper download. 

When I set my browser to [http://home.comcast.net/~ubuntume/](http://home.comcast.net/~ubuntume/) I get:

"The page you are looking for has not yet been created or has a different URL. Please check the URL and try again."

Here's my install log in case you need it:

```

F3 View  F4 Edit  F5 Copy  F6 Move  F7 MkDir  F8 Del  F10 Exit ^CH Ln ^CS SymLn 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nspluginwrapper-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manual installed.
ia32-libs-gtk is already the newest version.
Suggested packages:
  ia32-libs-kde libasound2-plugins
The following NEW packages will be installed:
  gsfonts-x11 ia32-libs-sdl lib32asound2 linux32
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1409kB of archives.
After unpacking, 3940kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gsfonts-x11 lib32asound2 ia32-libs-sdl linux32
E: There are problems and -y was used without --force-yes
--23:54:29--  http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.3.tar.gz/nspluginwrapper_0.9.91.4_amd64.deb
           => `nspluginwrapper_0.9.91.4_amd64.deb'
Resolving home.comcast.net... 204.127.198.24
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 404 Not found
23:54:30 ERROR 404: Not found.

dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
--23:54:30--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.126.70
Connecting to fpdownload.macromedia.com|72.246.126.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

100%[====================================>] 2,608,602    583.46K/s    ETA 00:00

23:54:40 (545.41 KB/s) - `install_flash_player_9_linux.tar.gz' saved [2608602/2608602]

install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer.xpt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
./GetFlash: line 31: nspluginwrapper: command not found
mv: cannot stat `/root/.mozilla/plugins/npwrapper.libflashplayer.so': No such file or directory
ln: creating symbolic link `/usr/lib/mozilla-firefox/plugins/npwrapper.libflashplayer.so' to `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': File exists

The plugin wrapper has been installed
You will need to restart Firefox for the changes to take effect

```

Please can you let me know when it's OK to retry.

Thanks,

M.C.

---

### Post by mcook2 on 2007-08-21
I also tried getting ndiswrapper direct via the freshmeat link, but the file length is zero:

[r/files/nspluginwrapper-0.9.91.4.tar.bz2"]http://gwenole.beauchesne.info/[..]r/files/nspluginwrapper-0.9.91.4.tar.bz2]("http://gwenole.beauchesne.info/[..)

---

### Post by Kilz on 2007-08-21
> **mcook2 said:**
> I also tried getting ndiswrapper direct via the freshmeat link, but the file length is zero:

[r/files/nspluginwrapper-0.9.91.4.tar.bz2"]http://gwenole.beauchesne.info/[..]r/files/nspluginwrapper-0.9.91.4.tar.bz2]("http://gwenole.beauchesne.info/[..)

Download the script from the first post, version 1.4 had a typo, version 1.5 is now linked in the first post.

---

### Post by AegisTalons on 2007-08-21
Absolutely amazing. I redownloaded your script and ran it again. And now Flash works without an absolute hinch. I don't know what the problem was before, something might have downloaded incorrectly. Again I am in awe of you magical talent of scripting and getting Flash working for people's computers. Rock on KILZ!!!

---

### Post by onemannation on 2007-08-21
Thank you so much for this!  I can finally view my own website!

[http://www.onemannation.com](http://www.onemannation.com)

BUT Audio still not working...

---

### Post by gertvanthienen on 2007-08-21
L.S.,

I managed to get the flash player working in Firefox, but... it only works if I 'sudo firefox'.
With a regular user account, the flash plugin is shown in Firefox's about:plugins, but I just don't see anything (white space where the flash object should be)

Any ideas?

Thanks in advance,

Gert

---

### Post by gertvanthienen on 2007-08-21
Sorry, but I figured it out by now...

I had used the command nspluginwrapper -i ./libflashplugin.so instead of specifying the entire path.  It had nothing to do with the user privileges, but it simple worked because I was doing my 'sudo firefox' from the same directory...

---

### Post by Kilz on 2007-08-21
> **gertvanthienen said:**
> Sorry, but I figured it out by now...

I had used the command nspluginwrapper -i ./libflashplugin.so instead of specifying the entire path.  It had nothing to do with the user privileges, but it simple worked because I was doing my 'sudo firefox' from the same directory...

Why were you even issuing commands? The script does everything, click click done. Secondly, why are you running Firefox under Sudo, or root privileges. Dont you realize this isnt a good idea?

---

### Post by Kilz on 2007-08-21
> **onemannation said:**
> Thank you so much for this!  I can finally view my own website!

[http://www.onemannation.com](http://www.onemannation.com)

BUT Audio still not working...

Do you have audio in other applications? If so take a look at the top post, I added a new section dealing with sound problems.

---

### Post by exoren22 on 2007-08-23
YAY! I have flash+sound working in SwiftWeasel 64! I had installed the new gutsy kernel in order to get my wireless working (iwl4965, search it its a pain, but not if you install gutsy kernels), so it took some manual dependency handling and thus I could not use your script exactly. I did, however, follow your script pretty close (the exception being the wget flash timed out ... damn adobe!). YAY for 64bit! Take that x64 FUDers!

---

### Post by exoren22 on 2007-08-23
I was pondering the java predicament (wow, Sun just pisses me off. this thread: [http://forum.java.sun.com/thread.jspa?forumID=32&threadID=568127](http://forum.java.sun.com/thread.jspa?forumID=32&threadID=568127) has been gthere since Nov. 2004!) And this page: [http://java.sun.com/j2se/1.5.0/system-configurations.html](http://java.sun.com/j2se/1.5.0/system-configurations.html) says there is 32-bit plugin support with the 64-bit linux install. Can anyone confirm this? And if so, Is there a way to use nspluginwrapper for this java plugin? Also, should I start a new thread to work on this? It seems as if Sun is not willing to work on their 64-bit plugins. 'Tis a shame...

---

### Post by bdoe on 2007-08-23
I ran the script, but it didn't work for me.  I'm running Ubuntu Feisty 7.04.  Here is output from the script:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper-i386 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux32 is already the newest version.
gsfonts-x11 is already the newest version.
gsfonts-x11 set to manual installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 but it is not going to be installed
  ia32-libs-sdl: Depends: lib32gcc1 but it is not going to be installed
                 Depends: lib32z1 but it is not going to be installed
  lib32asound2: Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not going to be installed
E: Broken packages
--11:11:55--  http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.4_amd64.deb
           => `nspluginwrapper_0.9.91.4_amd64.deb'
Resolving home.comcast.net... 204.127.198.24
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100,918 (99K) [text/plain]

100%[====================================>] 100,918       81.16K/s             

11:11:57 (81.09 KB/s) - `nspluginwrapper_0.9.91.4_amd64.deb' saved [100918/100918]

Selecting previously deselected package nspluginwrapper.
(Reading database ... 136836 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.4_amd64.deb) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on lib32gcc1 (>= 1:4.1.2); however:
  Package lib32gcc1 is not installed.
 nspluginwrapper depends on libc6-i386 (>= 2.5-0ubuntu1); however:
  Package libc6-i386 is not installed.
 nspluginwrapper depends on ia32-libs; however:
  Package ia32-libs is not installed.
 nspluginwrapper depends on ia32-libs-sdl; however:
  Package ia32-libs-sdl is not installed.
 nspluginwrapper depends on ia32-libs-gtk; however:
  Package ia32-libs-gtk is not installed.
 nspluginwrapper depends on lib32asound2; however:
  Package lib32asound2 is not installed.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
--11:11:58--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.46.70
Connecting to fpdownload.macromedia.com|72.246.46.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

100%[====================================>] 2,608,602    491.07K/s    ETA 00:00

11:12:04 (493.91 KB/s) - `install_flash_player_9_linux.tar.gz' saved [2608602/2608602]

install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer.xpt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
Cannot execute /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
mv: cannot stat `/home/briandoe/.mozilla/plugins/npwrapper.libflashplayer.so': No such file or directory
ln: creating symbolic link `/usr/lib/mozilla-firefox/plugins/npwrapper.libflashplayer.so' to `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': File exists




The plugin wrapper has been installed
You will need to restart Firefox for the changes to take effect
```

Can you please tell me where I'm going wrong?

---

### Post by exoren22 on 2007-08-23
> **bdoe said:**
> I ran the script, but it didn't work for me.  I'm running Ubuntu Feisty 7.04.  Here is output from the script:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper-i386 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux32 is already the newest version.
gsfonts-x11 is already the newest version.
gsfonts-x11 set to manual installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 but it is not going to be installed
  ia32-libs-sdl: Depends: lib32gcc1 but it is not going to be installed
                 Depends: lib32z1 but it is not going to be installed
  lib32asound2: Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not going to be installed
E: Broken packages
--11:11:55--  http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.4_amd64.deb
           => `nspluginwrapper_0.9.91.4_amd64.deb'
Resolving home.comcast.net... 204.127.198.24
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100,918 (99K) [text/plain]

100%[====================================>] 100,918       81.16K/s             

11:11:57 (81.09 KB/s) - `nspluginwrapper_0.9.91.4_amd64.deb' saved [100918/100918]

Selecting previously deselected package nspluginwrapper.
(Reading database ... 136836 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.4_amd64.deb) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on lib32gcc1 (>= 1:4.1.2); however:
  Package lib32gcc1 is not installed.
 nspluginwrapper depends on libc6-i386 (>= 2.5-0ubuntu1); however:
  Package libc6-i386 is not installed.
 nspluginwrapper depends on ia32-libs; however:
  Package ia32-libs is not installed.
 nspluginwrapper depends on ia32-libs-sdl; however:
  Package ia32-libs-sdl is not installed.
 nspluginwrapper depends on ia32-libs-gtk; however:
  Package ia32-libs-gtk is not installed.
 nspluginwrapper depends on lib32asound2; however:
  Package lib32asound2 is not installed.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
--11:11:58--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.46.70
Connecting to fpdownload.macromedia.com|72.246.46.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

100%[====================================>] 2,608,602    491.07K/s    ETA 00:00

11:12:04 (493.91 KB/s) - `install_flash_player_9_linux.tar.gz' saved [2608602/2608602]

install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer.xpt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
Cannot execute /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
mv: cannot stat `/home/briandoe/.mozilla/plugins/npwrapper.libflashplayer.so': No such file or directory
ln: creating symbolic link `/usr/lib/mozilla-firefox/plugins/npwrapper.libflashplayer.so' to `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': File exists




The plugin wrapper has been installed
You will need to restart Firefox for the changes to take effect
```

Can you please tell me where I'm going wrong?

Did you read my post directly above yours? (well the one above that) It looks like you have the same errors I had because you installed the gutsy kernels, didn't you? Just reenable the repos for gutsy and reinstall.

---

### Post by bdoe on 2007-08-23
I haven't installed any element of Gutsy that I'm aware of.  How would I check for that?

---

### Post by Kilz on 2007-08-23
> **bdoe said:**
> I haven't installed any element of Gutsy that I'm aware of.  How would I check for that?

Please post the reply to this in a terminal
```

echo `uname -r`
```

---

### Post by exoren22 on 2007-08-23
Hmm. Have you used Aptitude? If you have, then fire up aptitude and search for nspluginwrapper. Try to resolve dependencies in such a way that you don't break your gcc but you can also install the nspluginwrapper.

---

### Post by bdoe on 2007-08-23
> **Kilz said:**
> Please post the reply to this in a terminal
```

echo `uname -r`
```
```
2.6.20-16-generic
```

---

### Post by bdoe on 2007-08-23
> **exoren22 said:**
> Hmm. Have you used Aptitude? If you have, then fire up aptitude and search for nspluginwrapper. Try to resolve dependencies in such a way that you don't break your gcc but you can also install the nspluginwrapper.
Aptitude worked!  I removed some form of nspluginwrapper that was floating around as a broken package, reinstalled nspluginwrapper, and all its dependencies were "automagically" taken care of.

Restarted Firefox, surfed over to YouTube, and watched a video.

You officially rock!  Thank you! :KS

---

### Post by Linuxer on 2007-08-24
I am a new comer from Windows world.  I have tried to install various versions of your flash script with no success.  Here is what happens when I follow the instructions with the latest version of your install script:

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  nspluginwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 201kB disk space will be freed.
(Reading database ... 123109 files and directories currently installed.)
Removing nspluginwrapper ...
dpkg - warning: while removing nspluginwrapper, directory `/usr/lib64/mozilla/plugins' not empty so not removed.
dpkg - warning: while removing nspluginwrapper, directory `/usr/lib64/mozilla' not empty so not removed.
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  nspluginwrapper-i386
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 160kB disk space will be freed.
(Reading database ... 123091 files and directories currently installed.)
Removing nspluginwrapper-i386 ...
Reading package lists... Done
Building dependency tree... Done
ia32-libs is already the newest version.
ia32-libs-gtk is already the newest version.
linux32 is already the newest version.
lib32asound2 is already the newest version.
gsfonts-x11 is already the newest version.
ia32-libs-sdl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--22:02:17--  [http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/nspluginwrapper_0.9.91.4-0ubuntu3~upure64_amd64.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/nspluginwrapper_0.9.91.4-0ubuntu3~upure64_amd64.deb)
           => `nspluginwrapper_0.9.91.4-0ubuntu3~upure64_amd64.deb'
Resolving janvitus.interfree.it... 213.158.72.68
Connecting to janvitus.interfree.it|213.158.72.68|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100,918 (99K) [application/octet-stream]

100%[====================================>] 100,918       26.07K/s    ETA 00:00

22:02:26 (24.06 KB/s) - `nspluginwrapper_0.9.91.4-0ubuntu3~upure64_amd64.deb' saved [100918/100918]

Selecting previously deselected package nspluginwrapper.
(Reading database ... 123083 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.4-0ubuntu3~upure64_amd64.deb) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on lib32gcc1 (>= 1:4.1.2); however:
  Version of lib32gcc1 on system is 1:4.0.3-1ubuntu5.
 nspluginwrapper depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
 nspluginwrapper depends on libc6-i386 (>= 2.5-0ubuntu1); however:
  Version of libc6-i386 on system is 2.3.6-0ubuntu20.5.
 nspluginwrapper depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
--22:02:27--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 1.0.0.0
Connecting to fpdownload.macromedia.com|1.0.0.0|:80...


I am running Ubuntu 6.06, 64bit version. 

I would appreciate any help.  Thanks in advance.

---

### Post by superpri on 2007-08-24
hey,

the files hosted at [http://home.comcast.net/](http://home.comcast.net/) are unavaliable. Is there any other source?

thanks!

---

### Post by Kilz on 2007-08-24
> **Linuxer said:**
> I am a new comer from Windows world.  I have tried to install various versions of your flash script with no success.  Here is what happens when I follow the instructions with the latest version of your install script:

I am running Ubuntu 6.06, 64bit version. 

I would appreciate any help.  Thanks in advance.

[Please download the updated Dapper-Edgy Script.]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.5-Dapper-Edgy.tar.gz")

---

### Post by Kilz on 2007-08-24
> **superpri said:**
> hey,

the files hosted at [http://home.comcast.net/](http://home.comcast.net/) are unavaliable. Is there any other source?

thanks!

No, those files are only on comcast, on my account. Its possible that they were without power as a large area south of chicago was (and some still are) without power after a nasty storm.

---

### Post by Kilz on 2007-08-24
> **bdoe said:**
> ```
2.6.20-16-generic
```

While the Feisty script should work for you there is a problem installing the deb file for some reason. You might want to run the [Dapper-Edgy script]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.5-Dapper-Edgy.tar.gz") that creates its own deb file with alien.

---

### Post by bdoe on 2007-08-27
Just wanted to put this out there in case it catches anyone else unawares:

There is a new version of nspluginwrapper that Update Manager is pushing.  Installing it will break Flash if installed with the script at the beginning of this thread.

If you have installed this and find Flash no longer working, simply re-run the script.  It will remove the new nspluginwrapper, re-install the working one, and all will be well again.

To stop Update Manager from pushing the new update again, you will have to remove [http://janvitus.interfree.it/ubuntu](http://janvitus.interfree.it/ubuntu) feisty-upure64 from your repo list.  Hopefully this problem will be resolved soon.

---

### Post by crjackson on 2007-08-27
@kilz

I currently am using your wrapper for my flash needs.  

Can I install the 32 bit of Firefox and the flash plugin on the same system that's running the plugin wrapper with the 64 bit Firefox?

I thought I read a while back that it could cause conflicts but I can't find the post to be for sure.

---

### Post by Kilz on 2007-08-27
> **crjackson said:**
> @kilz

I currently am using your wrapper for my flash needs.  

Can I install the 32 bit of Firefox and the flash plugin on the same system that's running the plugin wrapper with the 64 bit Firefox?

I thought I read a while back that it could cause conflicts but I can't find the post to be for sure.

Yes, it used to be a problem, and still can be if you install the wrapper with another method. But if you install both with my scripts they will not conflict.

---

### Post by Kilz on 2007-08-27
> **bdoe said:**
> Just wanted to put this out there in case it catches anyone else unawares:

There is a new version of nspluginwrapper that Update Manager is pushing.  Installing it will break Flash if installed with the script at the beginning of this thread.

If you have installed this and find Flash no longer working, simply re-run the script.  It will remove the new nspluginwrapper, re-install the working one, and all will be well again.

To stop Update Manager from pushing the new update again, you will have to remove [http://janvitus.interfree.it/ubuntu](http://janvitus.interfree.it/ubuntu) feisty-upure64 from your repo list.  Hopefully this problem will be resolved soon.

Thanks I will look into updating the packages.

---

### Post by The Caped Crusader on 2007-08-27
Hello!

Your script worked great for me last week, but between yesterday and today (and after uninstalling network-manager and installing WICD) I had to do a 'sudo apt-get install -f' to resolve some broken dependancies. Well, something broke nspluginwrapper because suddenly no more flash on my firefox.

I autoremoved and autoclean apt-get and i tried to run again your script. this is the feedback i got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nspluginwrapper-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux32 is already the newest version.
gsfonts-x11 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 but it is not going to be installed
  ia32-libs-sdl: Depends: lib32gcc1 but it is not going to be installed
                 Depends: lib32z1 but it is not going to be installed
  lib32asound2: Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not going to be installed
E: Broken packages
--02:35:42--  [http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.4_amd64.deb](http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.4_amd64.deb)
           => `nspluginwrapper_0.9.91.4_amd64.deb'
Resolving home.comcast.net... 204.127.198.24
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100,918 (99K) [text/plain]

100%[====================================>] 100,918      118.09K/s             

02:36:04 (117.84 KB/s) - `nspluginwrapper_0.9.91.4_amd64.deb' saved [100918/100918]

Selecting previously deselected package nspluginwrapper.
(Reading database ... 117157 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.4_amd64.deb) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on lib32gcc1 (>= 1:4.1.2); however:
  Package lib32gcc1 is not installed.
 nspluginwrapper depends on libc6-i386 (>= 2.5-0ubuntu1); however:
  Package libc6-i386 is not installed.
 nspluginwrapper depends on ia32-libs; however:
  Package ia32-libs is not installed.
 nspluginwrapper depends on ia32-libs-sdl; however:
  Package ia32-libs-sdl is not installed.
 nspluginwrapper depends on ia32-libs-gtk; however:
  Package ia32-libs-gtk is not installed.
 nspluginwrapper depends on lib32asound2; however:
  Package lib32asound2 is not installed.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
--02:36:05--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.22.70
Connecting to fpdownload.macromedia.com|88.221.22.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

100%[====================================>] 2,608,602    954.32K/s             

02:36:08 (951.69 KB/s) - `install_flash_player_9_linux.tar.gz' saved [2608602/2608602]

install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer.xpt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
Cannot execute /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
mv: cannot stat `/home/pedro/.mozilla/plugins/npwrapper.libflashplayer.so': No such file or directory
ln: creating symbolic link `/usr/lib/mozilla-firefox/plugins/npwrapper.libflashplayer.so' to `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': File exists




The plugin wrapper has been installed
You will need to restart Firefox for the changes to take effect

-----------------------------------------

sorry for the long cut-paste. what do i need to do to fix this?

thanks. peace.

---

### Post by crjackson on 2007-08-27
> **Kilz said:**
> Yes, it used to be a problem, and still can be if you install the wrapper with another method. But if you install both with my scripts they will not conflict.

Yes, I used your script.  I have a smooth running system and just didn't want to muck it up.  I need the 32 bit browser for the java plug-in sometimes (I don't have any java installed and I know the 64bit sun version has no browser plug-in).

Thanks...

---

### Post by Kilz on 2007-08-27
> **The Caped Crusader said:**
> Hello!

Your script worked great for me last week, but between yesterday and today (and after uninstalling network-manager and installing WICD) I had to do a 'sudo apt-get install -f' to resolve some broken dependancies. Well, something broke nspluginwrapper because suddenly no more flash on my firefox.

I autoremoved and autoclean apt-get and i tried to run again your script. this is the feedback i got:

sorry for the long cut-paste. what do i need to do to fix this?

thanks. peace.

Thanks for all the info, but what I need for you to do is go to the first page and read the section on how to get help. It will have a link in it. In that package is a list of information I need.

---

### Post by The Caped Crusader on 2007-08-27
> **Kilz said:**
> Thanks for all the info, but what I need for you to do is go to the first page and read the section on how to get help. It will have a link in it. In that package is a list of information I need.

Thanks! I'm doing it asap. Sorry for not paying attention...

---

### Post by The Caped Crusader on 2007-08-27
**ls -al /usr/lib/mozilla/plugins**

total 8384
drwxr-xr-x 2 root root     4096 2007-08-28 02:08 .
drwxr-xr-x 3 root root     4096 2007-04-15 12:58 ..
-r--r--r-- 1 1003 users     856 2007-06-20 01:31 flashplayer.xpt
-rwxr-xr-x 1 1003 users 7040036 2007-06-20 01:31 libflashplayer.so
-rw-r--r-- 1 root root   118744 2007-03-20 09:40 libvlcplugin.so
-rw-r--r-- 1 root root   269216 2007-01-26 00:17 mplayerplug-in-dvx.so
-rw-r--r-- 1 root root      981 2007-01-26 00:17 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root root   269408 2007-01-26 00:17 mplayerplug-in-qt.so
-rw-r--r-- 1 root root      981 2007-01-26 00:17 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root   269472 2007-01-26 00:17 mplayerplug-in-rm.so
-rw-r--r-- 1 root root      981 2007-01-26 00:17 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root   270648 2007-01-26 00:17 mplayerplug-in.so
-rw-r--r-- 1 root root   269760 2007-01-26 00:17 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root      981 2007-01-26 00:17 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root      981 2007-01-26 00:17 mplayerplug-in.xpt

**ls -al /usr/lib/firefox/plugins**

total 20
drwxr-xr-x 2 root root  4096 2007-08-27 14:31 .
drwxr-xr-x 5 root root  4096 2007-08-20 04:15 ..
-rw-r--r-- 1 root root 11072 2007-07-31 14:29 libunixprintplugin.so
lrwxrwxrwx 1 root root    37 2007-08-27 14:31 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so
lrwxrwxrwx 1 root root    42 2007-08-20 04:09 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2007-08-20 04:09 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2007-08-20 04:09 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2007-08-20 04:09 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2007-08-20 04:09 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2007-08-20 04:09 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2007-08-20 04:09 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2007-08-20 04:09 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root    52 2007-08-22 00:10 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

**ls -al /tmp/nsplugwrapper**

total 2684
drwxr-xr-x  3 root root     4096 2007-08-28 03:50 .
drwxrwxrwt 15 root root    20480 2007-08-28 03:49 ..
drwxr-xr-x  2 1003 users    4096 2007-08-28 03:50 install_flash_player_9_linux
-rw-r--r--  1 root root  2608602 2007-07-05 19:48 install_flash_player_9_linux.tar.gz
-rw-r--r--  1 root root   100918 2007-08-21 06:43 nspluginwrapper_0.9.91.4_amd64.deb

---

### Post by Kilz on 2007-08-28
Thanks , but the last little bit (and most important) is what of the 3 os's your running(Ubuntu/Kubuntu/Xubuntu), the version, and the name of the script file you downloaded(scripts version).

---

### Post by r4ik on 2007-08-28
Works good for me thanks for you're time and effort.

---

### Post by The Caped Crusader on 2007-08-28
> **Kilz said:**
> Thanks , but the last little bit (and most important) is what of the 3 os's your running(Ubuntu/Kubuntu/Xubuntu), the version, and the name of the script file you downloaded(scripts version).

I'm running Ubuntu 7.04 AMD64
The script I used last was nspluginwrapper-install-0-1.5-ts

---

### Post by n_emoo on 2007-08-28
I am getting this error when I attempt to view youtube videos, after a clean successful install of the script.

=======================================================================
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/npwrapper.libflashplayer.so [/usr/lib/firefox/plugins/npwrapper.libflashplayer.so: cannot open shared object file: Permission denied]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/npwrapper.libflashplayer.so [/usr/lib/firefox/plugins/npwrapper.libflashplayer.so: cannot open shared object file: Permission denied]
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault (core dumped)
=====================================================================

---

### Post by n_emoo on 2007-08-28
And this error when I try the same with %sudo firefox

=======================================================================
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(npviewer.bin:11441): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
==============================================================
See if you can help. Thanks anyway!

---

### Post by Kilz on 2007-08-28
> **The Caped Crusader said:**
> I'm running Ubuntu 7.04 AMD64
The script I used last was nspluginwrapper-install-0-1.5-ts

You say you are running 7.04 or Feisty. but the first error log [you posted here]("http://ubuntuforums.org/showpost.php?p=3243710&postcount=172") is showing that the prerequisites are not available. Lets take a look at the section that is important.
```
dpkg: dependency problems prevent configuration of nspluginwrapper:
**nspluginwrapper depends on [B]lib32gcc1** (>= 1:4.1.2); however:
Version of lib32gcc1 on system is 1:4.0.3-1ubuntu5.[/B]
nspluginwrapper depends on libc6 (>= 2.5-0ubuntu1); however:
Version of libc6 on system is 2.3.6-0ubuntu20.5.
nspluginwrapper depends on libc6-i386 (>= 2.5-0ubuntu1); however:
Version of libc6-i386 on system is 2.3.6-0ubuntu20.5.
nspluginwrapper depends on libglib2.0-0 (>= 2.12.9); however:
Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
dpkg: error processing nspluginwrapper (--install):
dependency problems - leaving unconfigured
```
I have bolded out one package. I could have chosen any of the 4. But lets look at the first one, lib32gcc1.
Looking at the [Ubuntu Package]("http://packages.ubuntu.com/") site we can find out what packages are in any of the versions. [I did a search for lib32gcc1 in feisty]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=lib32gcc1&searchon=names&subword=1&version=feisty&release=all"). There is only one result, [This page]("http://packages.ubuntu.com/feisty/libs/lib32gcc1").  On that page we see the currrent version for Feisty is 1:4.1.2-0ubuntu4, the same version that is required by the nspluginwrapper package in the Feisty script. But your system only has 1:4.0.3-1ubuntu5 according to the information that you posted and I copied above. 
Fiesty's lib32gcc1 is version 1:4.1.2-0ubuntu4
Edgy's lib32gcc1 is version 1:4.1.1-13ubuntu5
Dappers lib32gcc1 is version 1:4.0.3-1ubuntu5
In other words, you have a Dapper package in Feisty. In fact all the packages that fail are because the version you have installed is a Dapper version. How that can be I have no idea. 
The problem isnt the script or the packages it installs. The problem is that you have ancient packages installed. Exactly how you are going to get them to Feisty's version I have no idea.
Are you 100% positive you are running Feisty Fawn? Did you install it fresh, or did you upgrade it from Dapper to Edgy, then to Feisty?

---

### Post by Kilz on 2007-08-28
> **n_emoo said:**
> And this error when I try the same with %sudo firefox

=======================================================================
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(npviewer.bin:11441): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
==============================================================
See if you can help. Thanks anyway!

Please read the first post in this topic, paying special attention to the "How to get help" section.

---

### Post by n_emoo on 2007-08-28
Apologise for not having included this earlier. Running ubuntu 7 Feisty.

===========================================================
abcd@Laptop:~/nspluginwrapper install$ ls -al /usr/lib/mozilla/plugins
total 7000
drwxr-xr-x 2 root    root       4096 2007-08-28 12:23 .
drwxr-xr-x 3 root    root       4096 2007-04-15 07:58 ..
-r--r--r-- 1    1003 users       856 2007-06-19 20:31 flashplayer.xpt
-rw-r--r-- 1 root    root      19456 2007-01-05 14:52 libflash-mozplugin.so
-rwxr-xr-x 1    1003 users   7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 root    root         38 2007-08-23 19:48 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 root    root         63 2007-08-24 02:40 libjavaplugin.so -> /usr/local/j2re-1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so
lrwxrwxrwx 1 root    root         36 2007-08-23 12:31 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root    root         37 2007-08-23 12:31 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root    root         34 2007-08-23 12:31 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root    root         35 2007-08-23 12:31 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root    root         36 2007-08-23 12:31 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root    root         37 2007-08-23 12:31 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root    root         42 2007-08-23 12:31 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root    root         43 2007-08-23 12:31 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 abcd abcd   70120 2007-08-28 12:23 npwrapper.libflashplayer.so


===========================================================================================

abcd@Laptop:~/nspluginwrapper install$ ls -al /usr/lib/firefox/plugins
total 6992
drwxr-xr-x 2 root root    4096 2007-08-26 04:56 .
drwxr-xr-x 6 root root    4096 2007-08-28 12:11 ..
-r--r--r-- 1 root root     856 2007-08-28 11:38 flashplayer.xpt
lrwxrwxrwx 1 root root      43 2007-08-26 02:30 libflash-mozplugin.so -> ../../mozilla/plugins/libflash-mozplugin.so
-rwxr-xr-x 1 root root 7040036 2007-08-28 11:38 libflashplayer.so
lrwxrwxrwx 1 root root      54 2007-08-23 19:48 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji_mozilla_firefox.so
lrwxrwxrwx 1 root root      63 2007-08-24 02:40 libjavaplugin.so -> /usr/local/j2re-1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so
lrwxrwxrwx 1 root root      36 2007-08-23 12:31 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root      37 2007-08-23 12:31 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root      34 2007-08-23 12:31 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root      35 2007-08-23 12:31 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root      36 2007-08-23 12:31 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root      37 2007-08-23 12:31 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root      42 2007-08-23 12:31 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root      43 2007-08-23 12:31 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root   11072 2007-07-31 09:29 libunixprintplugin.so
-rwx------ 1 root root   69696 2007-08-27 18:09 npwrapper.libflashplayer.so


============================================================================================

abcd@Laptop:~/nspluginwrapper install$ ls -al /tmp/nsplugwrapper
total 2668
drwxr-xr-x  3 root root     4096 2007-08-28 12:23 .
drwxrwxrwt 15 root root     4096 2007-08-28 12:26 ..
drwxr-xr-x  2 1003 users    4096 2007-08-28 12:23 install_flash_player_9_linux
-rw-r--r--  1 root root  2608602 2007-07-05 14:48 install_flash_player_9_linux.tar.gz
-rw-r--r--  1 root root   100918 2007-08-21 01:43 nspluginwrapper_0.9.91.4_amd64.deb

============================================================================================

---

### Post by The Caped Crusader on 2007-08-28
> **Kilz said:**
> You say you are running 7.04 or Feisty. but the first error log [you posted here]("http://ubuntuforums.org/showpost.php?p=3243710&postcount=172") is showing that the prerequisites are not available. Lets take a look at the section that is important.
```
dpkg: dependency problems prevent configuration of nspluginwrapper:
**nspluginwrapper depends on [B]lib32gcc1** (>= 1:4.1.2); however:
Version of lib32gcc1 on system is 1:4.0.3-1ubuntu5.[/B]
nspluginwrapper depends on libc6 (>= 2.5-0ubuntu1); however:
Version of libc6 on system is 2.3.6-0ubuntu20.5.
nspluginwrapper depends on libc6-i386 (>= 2.5-0ubuntu1); however:
Version of libc6-i386 on system is 2.3.6-0ubuntu20.5.
nspluginwrapper depends on libglib2.0-0 (>= 2.12.9); however:
Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
dpkg: error processing nspluginwrapper (--install):
dependency problems - leaving unconfigured
```
I have bolded out one package. I could have chosen any of the 4. But lets look at the first one, lib32gcc1.
Looking at the [Ubuntu Package]("http://packages.ubuntu.com/") site we can find out what packages are in any of the versions. [I did a search for lib32gcc1 in feisty]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=lib32gcc1&searchon=names&subword=1&version=feisty&release=all"). There is only one result, [This page]("http://packages.ubuntu.com/feisty/libs/lib32gcc1").  On that page we see the currrent version for Feisty is 1:4.1.2-0ubuntu4, the same version that is required by the nspluginwrapper package in the Feisty script. But your system only has 1:4.0.3-1ubuntu5 according to the information that you posted and I copied above. 
Fiesty's lib32gcc1 is version 1:4.1.2-0ubuntu4
Edgy's lib32gcc1 is version 1:4.1.1-13ubuntu5
Dappers lib32gcc1 is version 1:4.0.3-1ubuntu5
In other words, you have a Dapper package in Feisty. In fact all the packages that fail are because the version you have installed is a Dapper version. How that can be I have no idea. 
The problem isnt the script or the packages it installs. The problem is that you have ancient packages installed. Exactly how you are going to get them to Feisty's version I have no idea.
Are you 100% positive you are running Feisty Fawn? Did you install it fresh, or did you upgrade it from Dapper to Edgy, then to Feisty?

Ok, I'm beginning to see the light here. I'm pretty sure I installed Feisty. In fact , in the last week I installed 4 times before getting everything the way I like.
How can those packages be here? I really don't know. I remember a couple of broken package issues a few days ago, before the flash in firefox decided to stop working. I remember it something to do with removing network-manager and some of it's dependencies. I also did install compiz-fusion from one unsupported repository, and I also tried to update Feisty to Gutsy tribe 5, but this upgrade broke halfway...

What I don't understand is: If those packages are older than Feisty's versions, why hasn't the update manager advised me to upgrade them?

In any case, I'm really not in the mood to reinstall Feisty again just so I can have flash working. Everything's running great!

Thanks anyway for your help :)

Peace.

---

### Post by The Caped Crusader on 2007-08-28
I tried to install lib32gcc1 1.4.1.2-0Ubuntu4 with synaptic, but it says:

Depends: libc6-i386 but it is not going to be installed

I tired to install libc6-i386 2.5-0Ubuntu14 but it says:

Depends: libc6 (=2.5-0ubuntu14) but 2.6.1-1 is to be installed

I guess this means that I have libc6 2.6.1-1 installed, a newer - and probably unsupported - version. Maybe it has something to do with the Gutsy tribe 5 broken upgrade... :(

I guess the only thing to do for me is wait till Gutsy official release... and then wait for your newest install script :D

---

### Post by Kilz on 2007-08-28
> **The Caped Crusader said:**
> I tried to install lib32gcc1 1.4.1.2-0Ubuntu4 with synaptic, but it says:

Depends: libc6-i386 but it is not going to be installed

I tired to install libc6-i386 2.5-0Ubuntu14 but it says:

Depends: libc6 (=2.5-0ubuntu14) but 2.6.1-1 is to be installed

I guess this means that I have libc6 2.6.1-1 installed, a newer - and probably unsupported - version. Maybe it has something to do with the Gutsy tribe 5 broken upgrade... :(

I guess the only thing to do for me is wait till Gutsy official release... and then wait for your newest install script :D

Are you running Gutsy?
If not, and you plan on a complete wipe before installing the Gutsy release to solve problems. In order to get it working for now run the Dapper script. You will have to do a wipe at some point in the future though. You cant leave the system in its current state, Your updates are probably not happening.

---

### Post by Kilz on 2007-08-28
> **n_emoo said:**
> Apologise for not having included this earlier. Running ubuntu 7 Feisty.



Not a problem , but the info helps locate problems.

abcd@Laptop:~/nspluginwrapper install$ ls -al /usr/lib/mozilla/plugins
total 7000

-rw-r--r-- 1 root root 19456 2007-01-05 14:52 libflash-mozplugin.so

This file is probably at fault. It looks like a conflicting flash plugin. But if you have mozpluger installed there could be other problems. I also noticed that the 

-r--r--r-- 1 1003 users 856 2007-06-19 20:31 flashplayer.xpt
-rwxr-xr-x 1 1003 users 7040036 2007-06-19 20:31 libflashplayer.so

In that folder are quite old, older than the wrapper. If you still have problems after removing the mozplugin file, remove them and rerun the script.

---

### Post by Eddie Mac on 2007-08-28
> **AegisTalons said:**
> So occasionally flash for me will have problems. I have to click off of the flash window and click back on to actually register the click. What I'm wondering is there a way I can completely uninstall flash, hopefully you have a script for that. Then reboot, and then give your script a try again. Thanks Kilz.

I'm also having this problem... I need to move the cursor off the embedded flash before I can click on it a second time.  I am running Firefox 2.0.0.6 and Feisty Fawn 7.04 and have run the script multiple times.

Any ideas?

Here is the directory listings left over when running **nspluginwrapper-install-0-1.6-ts.tar.gz**


```
~$ ls -al /usr/lib/mozilla/plugins
total 6996
drwxr-xr-x 2 root root     4096 2007-08-28 14:10 .
drwxr-xr-x 3 root root     4096 2007-04-15 07:58 ..
-r--r--r-- 1 1003 users     856 2007-06-19 20:31 flashplayer.xpt
-rw-r--r-- 1 root root    19456 2007-01-05 14:52 libflash-mozplugin.so
-rwxr-xr-x 1 1003 users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 root root       38 2007-06-10 15:50 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 root root       36 2007-05-31 09:39 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root       37 2007-05-31 09:39 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root       34 2007-05-31 09:39 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root       35 2007-05-31 09:39 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root       36 2007-05-31 09:39 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root       37 2007-05-31 09:39 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root       42 2007-05-31 09:39 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root       43 2007-05-31 09:39 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 ed   ed      70120 2007-08-28 14:10 npwrapper.libflashplayer.so

~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 root root  4096 2007-08-01 08:10 .
drwxr-xr-x 6 root root  4096 2007-08-01 08:10 ..
lrwxrwxrwx 1 root root    43 2007-06-10 13:54 libflash-mozplugin.so -> ../../mozilla/plugins/libflash-mozplugin.so
lrwxrwxrwx 1 root root    54 2007-06-10 15:50 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji_mozilla_firefox.so
lrwxrwxrwx 1 root root    36 2007-05-31 09:39 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-05-31 09:39 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-05-31 09:39 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-05-31 09:39 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-05-31 09:39 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-05-31 09:39 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-05-31 09:39 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-05-31 09:39 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2007-07-31 09:29 libunixprintplugin.so
lrwxrwxrwx 1 root root    52 2007-06-10 15:02 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

~$ ls -al /tmp/nsplugwrapper
total 2692
drwxr-xr-x  3 root root     4096 2007-08-28 14:10 .
drwxrwxrwt 18 root root    28672 2007-08-28 14:11 ..
drwxr-xr-x  2 1003 users    4096 2007-08-28 14:10 install_flash_player_9_linux
-rw-r--r--  1 root root  2608602 2007-07-05 14:48 install_flash_player_9_linux.tar.gz
-rw-r--r--  1 root root   100918 2007-08-21 01:43 nspluginwrapper_0.9.91.4_amd64.deb
```

---

### Post by uniko on 2007-08-28
Tested the 2.0 version on Gutsy, worked like a charm.

---

### Post by The Caped Crusader on 2007-08-28
> **Kilz said:**
> Are you running Gutsy?
If not, and you plan on a complete wipe before installing the Gutsy release to solve problems. In order to get it working for now run the Dapper script. You will have to do a wipe at some point in the future though. You cant leave the system in its current state, Your updates are probably not happening.

Dapper script returns same error... I think I have a real serious problem with conflicting package versions. More: I try to remove libc6 and it says it has to remove an enormous list of ubuntu packages. I don't know... perhaps I'll live the system as it is until the final Gutsy upgrade comes.

unless there is another way of removing lic6 or downgrading it without damaging the other packages...

thanks :)

peace.

---

### Post by antcasq on 2007-08-28
I changed the version 2 of the script a bit, and now it works on "Kubuntu 7.10 (Gutsy Gibbon) Tribe 5".

Basically, I fixed the location of the firefox plugin directory, at least on my PC.
What I changed/added is next to  "# ASC - My Comment".

The only special consideration is that I'm using the Portuguese European locale, but I don't think that it matters.


# - START SCRIPT
#!/bin/bash

#Clean out old installs
sudo apt-get remove -y nspluginwrapper
sudo apt-get remove -y nspluginwrapper-i386
sudo rm -f /usr/lib/mozilla/plugins/flashplayer.xpt
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so
#
# ASC - Remove Plugin from FIREFOX dir
sudo rm -f /usr/lib/firefox/plugins/flashplayer.xpt
sudo rm -f /usr/lib/firefox/plugins/libflashplayer.so
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so


#make working directory
sudo mkdir /tmp/nsplugwrapper

#move to working directory
cd /tmp/nsplugwrapper

#install needed packages
sudo apt-get -y install ia32-libs ia32-libs-gtk linux32 lib32asound2 gsfonts-x11 ia32-libs-sdl

#Dowload rpm's
sudo wget -c [http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.5-amd64.deb](http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.5-amd64.deb)

#Install deb files
sudo dpkg -i *.deb

#Get Flash and place it
sudo wget -c [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
sudo tar -xzvf install_flash_player_9_linux.tar.gz
sudo mv -f /tmp/nsplugwrapper/install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins/
sudo mv -f /tmp/nsplugwrapper/install_flash_player_9_linux/flashplayer.xpt /usr/lib/mozilla/plugins/

#make wrapped plugin
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo mv ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
# ASC - LINK Plugin to FIREFOX dir on my PC
# sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/firefox/plugins/

#Clean up files
sudo rm -fdr /tmp/nsplugwrapper

#warn to restart browser
 echo
 echo
 echo
 echo
 echo "The plugin wrapper has been installed"
 echo "You will need to restart Firefox for the changes to take effect"
# - END SCRIPT

---

### Post by Kilz on 2007-08-28
> **Eddie Mac said:**
> I'm also having this problem... I need to move the cursor off the embedded flash before I can click on it a second time.  I am running Firefox 2.0.0.6 and Feisty Fawn 7.04 and have run the script multiple times.

Any ideas?

-rw-r--r-- 1 root root    19456 2007-01-05 14:52 libflash-mozplugin.so



How many ways and methods did you try to get Flash installed? Do you realize that some have left files that may conflict like the one above?

---

### Post by Kilz on 2007-08-28
> **antcasq said:**
> I changed the version 2 of the script a bit, and now it works on "Kubuntu 7.10 (Gutsy Gibbon) Tribe 5".


Did you happen to notice this on the First post in this topic?
**[SIZE="3"][COLOR="Red"] If you are having a problem getting the nspluginwrapper working in Gutsy please file a bug report on launchpad![/COLOR][/SIZE]**

If not, please go there. Because a script inst the answer for Gutsy.
If you are running Gutsy it should work without a script, if it needs a script , its a bug. A bug needs to be reported so it can be fixed while Gutsy is under development. Have you reported the bug?

But thanks for the additions, some of them will prove useful in removing conflicts.

---

### Post by Kilz on 2007-08-28
> **The Caped Crusader said:**
> Dapper script returns same error... I think I have a real serious problem with conflicting package versions. More: I try to remove libc6 and it says it has to remove an enormous list of ubuntu packages. I don't know... perhaps I'll live the system as it is until the final Gutsy upgrade comes.

unless there is another way of removing lic6 or downgrading it without damaging the other packages...

thanks :)

peace.

What was the Error?

---

### Post by gregfulkerson on 2007-08-28
You rock for posting this. Thank you! I scoured the internet looking for a 64 bit flash solution. When I found this, I was done in under 10 seconds. Wooohooo!

---

### Post by reiki on 2007-08-28
Kilz,

I just installed 64-bit Feisty, ran the script (not the version 2 script... the "main" one) and ..... done!  Worked perfectly. I have flash in firefox (tested to be sure).

thanks!

---

### Post by Tanker Bob on 2007-08-28
My flash with Firefox was working fine under 64-bit Feisty until yesterday. Daily updates downloaded adn installed a nspluginwrapper update, and a bunch of flash sites that worked the day before quit working. Any idea what happened with the update version 0.9.91.5 of nspluginwrapper?

---

### Post by Kilz on 2007-08-28
> **Tanker Bob said:**
> My flash with Firefox was working fine under 64-bit Feisty until yesterday. Daily updates downloaded adn installed a nspluginwrapper update, and a bunch of flash sites that worked the day before quit working. Any idea what happened with the update version 0.9.91.5 of nspluginwrapper?

Yes and no. I dont make the nspluginwrapper package. My script just installs it and sets it up. What happened is that the new package is incompatible with the files the old package made. That is a problem with the package. 
You may want to just install my new test script, as it will remove the old files, reinstall the new wrapper package and set it up. After that, to avoid future problems, just lock the nsplugginwrapper package at its version in Synaptic after running the script.

---

### Post by John.Michael.Kane on 2007-08-28
Kilz your version 2.0  script checks out, and installed without issue.

Note: for those who use the script you may have to clear you browsers cache, and restart firefox.

---

### Post by Kilz on 2007-08-29
> **SD-Plissken said:**
> Kilz your version 2.0  script checks out, and installed without issue.

Note: for those who use the script you may have to clear you browsers cache, and restart firefox.

Ty , I just wantto make sure a few people had good results before replacing the 1.6 version.

---

### Post by Eddie Mac on 2007-08-29
> **Kilz said:**
> 
[QUOTE=Eddie Mac]
I'm also having this problem... I need to move the cursor off the embedded flash before I can click on it a second time. I am running Firefox 2.0.0.6 and Feisty Fawn 7.04 and have run the script multiple times.

Any ideas?

-rw-r--r-- 1 root root 19456 2007-01-05 14:52 libflash-mozplugin.so

How many ways and methods did you try to get Flash installed? Do you realize that some have left files that may conflict like the one above?[/QUOTE]

THANK YOU!!  I manually cleaned out the firefox and mozilla plugin folders (deleting files with "flash" in the name) and ran the script again.  This has been bugging me for months, and I just chalked it up as a linux/64 bit quirk.  Just goes to show that it pays to ask.  Thanks again!

**UPDATE**
Well, I may have spoken too soon.  I could have sworn it was working, but now it is consistently not.  For example, I click pause and then play on a YouTube video, and it'll pause, but not restart.  I need to move my cursor off the embedded flash and then click again.  Very odd :-(

---

### Post by Kilz on 2007-08-29
> **Eddie Mac said:**
> THANK YOU!!  I manually cleaned out the firefox and mozilla plugin folders (deleting files with "flash" in the name) and ran the script again.  This has been bugging me for months, and I just chalked it up as a linux/64 bit quirk.  Just goes to show that it pays to ask.  Thanks again!

**UPDATE**
Well, I may have spoken too soon.  I could have sworn it was working, but now it is consistently not.  For example, I click pause and then play on a YouTube video, and it'll pause, but not restart.  I need to move my cursor off the embedded flash and then click again.  Very odd :-(

Seeing how you tried numerous ways to get flash working there is no telling what other files on your system may be messing things up.

---

### Post by The Caped Crusader on 2007-08-29
> **Kilz said:**
> What was the Error?

Damn, I forgot to copy-paste the error dump... but nevermind that. I'm backing up my personal files and I will be installing Gutsy tribe 5 between today and tomorrow...

But thank you very much for your help anyway. And thanks for the script! For some time (as in: before I messed up my Ubuntu installation) it worked great! with full sound support!

:)

---

### Post by Tanker Bob on 2007-08-29
> **Kilz said:**
> Yes and no. I dont make the nspluginwrapper package. My script just installs it and sets it up. What happened is that the new package is incompatible with the files the old package made. That is a problem with the package. 
You may want to just install my new test script, as it will remove the old files, reinstall the new wrapper package and set it up. After that, to avoid future problems, just lock the nsplugginwrapper package at its version in Synaptic after running the script.
Thanks, Kilz. That worked like a charm. I can't find a way to lock the version in KPackage or Adept, though.

---

### Post by jusmurph on 2007-08-29
Works nicely.

---

### Post by Applegeek on 2007-08-29
Worked great!!!  

This was on a relatively fresh install of Ubuntu Feisty on an amd64 system with an NVidia card, no problems to report at all.  YouTube works 100%.

Thanks for the groovy script!!

---

### Post by jusmurph on 2007-08-30
It seems this fixes the limiting mouse click issue of previous versions?

---

### Post by Kilz on 2007-08-30
> **jusmurph said:**
> It seems this fixes the limiting mouse click issue of previous versions?

With version 1.4 I started using a deb package from [Janvitus]("http://www.janvitus.netsons.org/repository/") for the Feisty script. Version 2.0 includes a new nspluginwrapper package. Im not 100% sure of everything that was fixed.

---

### Post by jusmurph on 2007-08-30
Either way if it works it works :)

---

### Post by Southeast First on 2007-08-30
This worked perfect, thanks!

---

### Post by eph1973 on 2007-08-30
Most excellent, thanks for the great solution!

---

### Post by Eddie Mac on 2007-08-30
> **Kilz said:**
> Seeing how you tried numerous ways to get flash working there is no telling what other files on your system may be messing things up.

I totally missed that you had a test 2.0 script.  I gave that a try, and the problem seems to be fixed now.  Thanks for all the work!  I know it's been said before, but this should really just be incorporated into ubuntu.

---

### Post by John.Michael.Kane on 2007-08-30
> **Eddie Mac said:**
> I totally missed that you had a test 2.0 script.  I gave that a try, and the problem seems to be fixed now.  Thanks for all the work!  I know it's been said before, but this should really just be incorporated into ubuntu.

The dev's have incorporated (nspluginwrapper) in gutsy. When you install flash under gutsy64, It automatically installs the needed dependencies including nspluginwrapper.

---

### Post by Linuxer on 2007-08-30
Thanks, Kliz.  I will give this a try.

---

### Post by Kilz on 2007-08-30
> **SD-Plissken said:**
> The dev's have incorporated (nspluginwrapper) in gutsy. When you install flash under gutsy64, It automatically installs the needed dependencies including nspluginwrapper.

Are you sure? Because more than one person running Gutsy has tried my script.

---

### Post by John.Michael.Kane on 2007-08-30
> **Kilz said:**
> Are you sure? Because more than one person running Gutsy has tried my script.

The last time I install gutsy, and installed flash, it installed nspluginwrapper, other needed files. 

I can try reinstalling gutsy, and taking note of the files it installs.

---

### Post by Kilz on 2007-08-30
> **SD-Plissken said:**
> The last time I install gutsy, and installed flash, it installed nspluginwrapper, other needed files. 

I can try reinstalling gutsy, and taking note of the files it installs.

Thats ok, no need as long as it works now. Perhaps the people who tried the script didnt know. They could also have been using a early alpha where it wasnt working.

---

### Post by coolkid5 on 2007-08-30
I installed the script and stuff and to test it i tried to play a flash game on addictinggames.com.  But the only game that i found to work was addictinggames.com/helicopter.html.  Nothing else worked.  Is there a way to fix this?  Is this just me?

---

### Post by John.Michael.Kane on 2007-08-30
> **coolkid5 said:**
> I installed the script and stuff and to test it i tried to play a flash game on addictinggames.com.  But the only game that i found to work was addictinggames.com/helicopter.html.  Nothing else worked.  Is there a way to fix this?  Is this just me?

Which script version did you use, As theres two versions.

Also did you make sure to clear your browser cache.

Where there any error msg's printed during the script install?

---

### Post by Kilz on 2007-08-30
> **coolkid5 said:**
> I installed the script and stuff and to test it i tried to play a flash game on addictinggames.com.  But the only game that i found to work was addictinggames.com/helicopter.html.  Nothing else worked.  Is there a way to fix this?  Is this just me?

Please also provide a link to a game that isnt working for you.

---

### Post by John.Michael.Kane on 2007-08-30
> **Kilz said:**
> Thats ok, no need as long as it works now. Perhaps the people who tried the script didnt know. They could also have been using a early alpha where it wasnt working.

I stand corrected. As of today on a fresh fully updated gutsy install.
I had to copy libflashplayer.so from /usr/lib/flashplugin-nonfree to /usr/lib/mozilla/plugins, and then in the terminal type nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

After which flash played. not sure if it's regression, As flash did work at one point or something else entirely.

This is the post where I found the info for fixing it under gutsy. In case any other 64bit gutsy testers want to post findings there.
[http://ubuntuforums.org/showpost.php?p=3210391&postcount=4](http://ubuntuforums.org/showpost.php?p=3210391&postcount=4)

IMHO I looks like it's bug with the version of nspluginwrapper used. Though I might be off on that.

---

### Post by Kilz on 2007-08-31
> **SD-Plissken said:**
> I stand corrected. As of today on a fresh fully updated gutsy install.
I had to copy libflashplayer.so from /usr/lib/flashplugin-nonfree to /usr/lib/mozilla/plugins, and then in the terminal type nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

After which flash played. not sure if it's regression, As flash did work at one point or something else entirely.

This is the post where I found the info for fixing it under gutsy. In case any other 64bit gutsy testers want to post findings there.
[http://ubuntuforums.org/showpost.php?p=3210391&postcount=4](http://ubuntuforums.org/showpost.php?p=3210391&postcount=4)

IMHO I looks like it's bug with the version of nspluginwrapper used. Though I might be off on that.

That should be automatic, the copying into place and running the command should be included in a postinst script in the package. To me thats a bug that needs to be reported and fixed.

---

### Post by John.Michael.Kane on 2007-08-31
> **Kilz said:**
> That should be automatic, the copying into place and running the command should be included in a postinst script in the package. To me thats a bug that needs to be reported and fixed.

I reported it. Here's the link in case other gutsy 64bit testers want to chime in.
[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136267](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136267)

I also posted in the gutsy dev section a link to the report as well.

Edit: credit to _simon_   for the workaround.

---

### Post by Kilz on 2007-08-31
> **SD-Plissken said:**
> I reported it. Here's the link in case other gutsy 64bit testers want to chime in.
[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136267](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136267)

I also posted in the gutsy dev section a link to the report as well.

Edit: credit to _simon_   for the workaround.

Cool I added a comment to the bug report on an easy way to fix the issue. I remember all the suggestions in the past that have been shot down because some developer couldnt figure out how to solve the bug.

---

### Post by John.Michael.Kane on 2007-08-31
> **Kilz said:**
> Cool I added a comment to the bug report on an easy way to fix the issue. I remember all the suggestions in the past that have been shot down because some developer couldnt figure out how to solve the bug.

Thanks. I only hope the issue is not overlooked or passed off as user error.

---

### Post by jusmurph on 2007-09-01
Looks lkike they will fix that.

---

### Post by Applegeek on 2007-09-01
Hmmm...All was working fine two days ago on my Feisty amd64 system.  Have the new -100 drivers for my 7100 NVidia card installed, had Compiz Fusion up and running no problems with Emerald, all eye candy working fine.  Installed the Ver 2.0 script and all was working 100% fine with FireFox 2.x - 64.

Starting last night (after few packages updated by synaptic, (I believe there was a kernel-related update) now getting a hard crash while viewing YouTube.  The kids can play around on YouTube for maybe a half hour, then a  Video will terminate/ exit with a window full of scrambled lines on the screen.  The system may work for a few more minutes with the scrambled window on top of all others, then the system crashes with no response from keyboard or mouse.  It must be issued a hard reset.  It doesn't seem to be related to the same video file.  

I rebooted without CF/Emerald running, but no effect.  Again, it will play videos on YouTube for a while, then crash....right in the middle of a video, with no other action taking place.

No other area of the system seems to be affected, this seems to only happen when Flash 9 inside the wrapper is running.

Ant clues on how to troubleshoot this??  Its very frustrating since we are so close to having everything work perfectly...

---

### Post by John.Michael.Kane on 2007-09-01
> **Applegeek said:**
> Hmmm...All was working fine two days ago on my Feisty amd64 system.  Have the new -100 drivers for my 7100 NVidia card installed, had Compiz Fusion up and running no problems with Emerald, all eye candy working fine.  Installed the Ver 2.0 script and all was working 100% fine with FireFox 2.x - 64.

Starting last night (after few packages updated by synaptic, (I believe there was a kernel-related update) now getting a hard crash while viewing YouTube.  The kids can play around on YouTube for maybe a half hour, then a  Video will terminate/ exit with a window full of scrambled lines on the screen.  The system may work for a few more minutes with the scrambled window on top of all others, then the system crashes with no response from keyboard or mouse.  It must be issued a hard reset.  It doesn't seem to be related to the same video file.  

I rebooted without CF/Emerald running, but no effect.  Again, it will play videos on YouTube for a while, then crash....right in the middle of a video, with no other action taking place.

No other area of the system seems to be affected, this seems to only happen when Flash 9 inside the wrapper is running.

Ant clues on how to troubleshoot this??  Its very frustrating since we are so close to having everything work perfectly...

First off why upgrade to version 2.0 of Kilz script on a production box. When no problems existed.

As of now version 2.0 is still under the testing phase, and IMHO issues should be expected until the script is golden.

As to the problem your having I would not necessarily place the issue at the feet of the  install script, As hard locking can also be attributed to your video card driver.

Also have you tried any other flash based websites to see if the issue happens on them as well.

Did you try clearing the browser cache.

Personally I would revert back to the standard nvidia-glx-new driver that feisty comes with, and use the 1.6 version script, and do testing using those, As this would allow you to eliminate the new driver as the problem, and the V2.0 script as the problem.

---

### Post by dn* on 2007-09-01
I hear the newest nspluginwrapper fixes the clicking issue with flash.. can anyone confirm this? and if so, any chance of getting the script in the first post updated to use the new deb?

---

### Post by John.Michael.Kane on 2007-09-01
> **dn* said:**
> I hear the newest nspluginwrapper fixes the clicking issue with flash.. can anyone confirm this? and if so, any chance of getting the script in the first post updated to use the new deb?

Version 2.0 is current 'under testing' script, and it installs nspluginwrapper_0.9.91.5 which is the latest version. 

You can use the v2.0 script, however. Understand it is still being tested.

---

### Post by Applegeek on 2007-09-01
> **SD-Plissken said:**
> First off why upgrade to version 2.0 of Kilz script on a production box. When no problems existed.

As of now version 2.0 is still under the testing phase, and IMHO issues should be expected until the script is golden.

As to the problem your having I would not necessarily place the issue at the feet of the  install script, As hard locking can also be attributed to your video card driver.

Also have you tried any other flash based websites to see if the issue happens on them as well.

Did you try clearing the browser cache.

Personally I would revert back to the standard nvidia-glx-new driver that feisty comes with, and use the 1.6 version script, and do testing using those, As this would allow you to eliminate the new driver as the problem, and the V2.0 script as the problem.

I never said it was the script...as I said the system was 100% stable for a couple of days with very heavy usage 24/7 until last night.  The script install went with no errors at all, and its a great idea, and the point of all of this is to test, and report back findings, as  _requested_.

Yes, we have seen one other video playing under Flash 9 on another website cause the crash.  It's just that YouTube is used for testing since its such a Flash-rich enviroment.

Yes, Browser cache was cleared.

After reboot, can navigate back to same video, play it, and it'll be fine.

Yes, the video driver was rolled back to -9755 to test, no difference.  Newest -100 driver works much better with CF, at least for me.  Again, the system is 100% stable and crash-free in all other respects, so we really don't suspect a hardware issue.  Video driver re-installed at newest NVidia -100.

A clean install of Feisty 32 was tested on another drive running on the same hardware, with no problems after 2 hours of video playing, so again no hardware problems detected on MoBo / Memory / Vid card and the newest NVidia driver (32, of course).

I'll re-install with the 1.6 script on the amd64 setup and see what happens, and report back.  It may be something in the wrapper, not necessarily the script itself.

---

### Post by AbredPeytr on 2007-09-01
Hi Kilz,
thanks again for this great script.  I downloaded the test version 2.0 and it seems to have worked without a problem, at least when testing my favorite YouTube clip.

Cheers

---

### Post by Kilz on 2007-09-01
> **Applegeek said:**
> I'll re-install with the 1.6 script on the amd64 setup and see what happens, and report back. ** It may be something in the wrapper, not necessarily the script itself.**

The script is very basic, either version. It installs deb files, flash, and runs the wrapper command. That said, most of the issues people have tend to be because they tried multiple ways to get flash to work and ended up with conflicting files. This wont be the case with the files the script installs, as versions from 1.5 forward have cleaned out all files made from the script before installing a new wrapper.
Sorry to hear that you experience issues with flash play. another option for those that want flash to play on a 64bit setup is [to install a 32bit browser and the plugins]("http://ubuntuforums.org/showthread.php?p=1174435"). This avoids the wrapper. As an added bonus it also can install java and the mplayer plugins.

---

### Post by hadeshorn on 2007-09-01
Thanks alot, this plugin worked quickly and seamlessly!

---

### Post by Spike-X on 2007-09-01
I just used the version 2.0 script, after the latest nspluginwrapper update broke Flash Player.

Once I removed the flashplayer-related files from /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins, the script worked perfectly. Thanks Kilz!

---

### Post by didi2005 on 2007-09-02
Finally i managed to install flash script.... Thanks...

---

### Post by Applegeek on 2007-09-02
> **Kilz said:**
> The script is very basic, either version. It installs deb files, flash, and runs the wrapper command. That said, most of the issues people have tend to be because they tried multiple ways to get flash to work and ended up with conflicting files. This wont be the case with the files the script installs, as versions from 1.5 forward have cleaned out all files made from the script before installing a new wrapper.
Sorry to hear that you experience issues with flash play. another option for those that want flash to play on a 64bit setup is [to install a 32bit browser and the plugins]("http://ubuntuforums.org/showthread.php?p=1174435"). This avoids the wrapper. As an added bonus it also can install java and the mplayer plugins.

Update:  Actually I went back and removed all flashplayer files, and all wrapper files, and all plug ins.  Re-ran the 2.0 script.  So far this morning YouTube has run about 3 hours on various clips on Firefox 2, with no problems.

I also shut down the screensavers as a test also.  It seems that a couple people in our group saw that the glitch would happen after a the screen had come out of screensaver mode.  I'll test that as well...in a couple days I'll turn the screensavers back on and see what gives, I think the kids had "Flocks" running when the computer was crashing.

So at the moment, Flash 9 seems to be working again...Thanks again for the helpful suggestions...

EDIT UPDATE:  Looks like at least part of the problem is when the system comes out of screensaver mode...Like Windows 98 used to do.

EDIT UPDATE:  Looks like Flash 9 running on amd64 machines will not allow large screen mode - like you go to YouTube, get a video running, then try to go to large screen mode (icon lower right corner of video window), it'll freeze video...Then it seems to be buggy after that event.  Now the machines I have testing all have wide-screen LCD's running at 1440 X 900 or higher, maybe someone can double check this with a non wide-screen setup.

Some of our other older server Linux boxes have been up for 354 days without a reset, we'll see if we can get to that reliability point with the amd64 stuff..

---

### Post by Applegeek on 2007-09-02
Other reports of nspluginwrapper being broken are coming in.  As far as I can tell this might be from the updates that occured on Friday.

At my end the complete removal and re-install of nspluginwrapper seems to have helped - however it does look like at least some of the screensavers can leave a system in a semi-crashed state.  A system running NVidia/CF/Emerald seems to be  stable as well.

Edit :  Update...Another report of a crashed video coming in, on a amd64/nspluginwrapper/nvidia setup.  This is a hard crash, reboot required...  Will try to determine if its the Flash 9 video content or ??

---

### Post by John.Michael.Kane on 2007-09-03
Personally i have been unable to reproduce this issue at this time. That being said I have filed a bug report here [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991) .

Please add to report any information you have including any error msg's. Make sure to be as detailed as you can in explaining the issues your having.

---

### Post by Applegeek on 2007-09-03
In our group, we have 18 out of 24 amd64 users having some problems.  Not everybody is having the same problem.  At least in a few cases (mine included), re-installing the wrapper seemed to help, but not in all cases.  It seems like anyone who did the kernel update tweaks on Friday might be having a problem, maybe.  

One of the things to check is:  If you watch a video on YouTube, try going to full screen mode.  At best, you might get a video freeze or Firefox crash.  At worst, you might get a hard system crash requiring a reset.  Something I look for now.  I thought full-screen video was supposed to be fixed in recent releases of Flash 9 / nspluginwrapper???

---

### Post by Kilz on 2007-09-03
> **Applegeek said:**
> In our group, we have 18 out of 24 amd64 users having some problems.  Not everybody is having the same problem.  At least in a few cases (mine included), re-installing the wrapper seemed to help, but not in all cases.  It seems like anyone who did the kernel update tweaks on Friday might be having a problem, maybe.  

One of the things to check is:  If you watch a video on YouTube, try going to full screen mode.  At best, you might get a video freeze or Firefox crash.  At worst, you might get a hard system crash requiring a reset.  Something I look for now.  I thought full-screen video was supposed to be fixed in recent releases of Flash 9 / nspluginwrapper???

Full screen video is only just getting support in the newest flash beta from what i understand.

---

### Post by Applegeek on 2007-09-03
Correct.

The problem is that it shouldn't _crash_ the system when the user tries to go full screen.  An unsupported  function call should just return without doing anything.

In my best case, the video will freeze, then the system gets buggy after that.

In my worst case, system will crash hard, completely, with no mouse or keyboard response anywhere.

Don't know if this is the wrapper or Flash doing this.  I have to tell people to stay away from the Full Screen button, though, if they are watching a video.

---

### Post by John.Michael.Kane on 2007-09-03
> **Applegeek said:**
> Correct.

The problem is that it shouldn't _crash_ the system when the user tries to go full screen.  An unsupported  function call should just return without doing anything.

In my best case, the video will freeze, then the system gets buggy after that.

In my worst case, system will crash hard, completely, with no mouse or keyboard response anywhere.

Don't know if this is the wrapper or Flash doing this.  I have to tell people to stay away from the Full Screen button, though, if they are watching a video.

The problem can't be fixed if you, and those who have this problem don't file bug reports or in this case add to the report already opened via launchpad. 

I opened the necessary report, and posted a link to it. Add as much detailed information as you can, and have those in your group who can replicate the problem post in that report as well. heres the link again if you need it [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991)

---

### Post by sqlpython on 2007-09-03
Kliz
 Thanks Ubuntu, for the Flashinstall script..
My FLash plugin now works on my Kubunt 7.04 64 bit iinstall...

THe script, although I had full permissions and it was executable, would not run for me..

But I had been following other threads and you had the get for the deb ...I was working with an rpm and alien that failed..
You had the right info so I ran it all from a command line one sudo at a time and all worked fine... 
I have to take another look as why the script failed as a whole..
Anyway good deb find good job...........Thank You

---

### Post by Applegeek on 2007-09-03
> **SD-Plissken said:**
> The problem can't be fixed if you, and those who have this problem don't file bug reports or in this case add to the report already opened via launchpad. 

I opened the necessary report, and posted a link to it. Add as much detailed information as you can, and have those in your group who can replicate the problem post in that report as well. heres the link again if you need it [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991)

Done... Thanks for starting the bug thread!!.

---

### Post by aamr on 2007-09-04
Links aren't working :(

---

### Post by Jeff_From_VA on 2007-09-04
I used this script and all was well.  I appreciate it very much!!

I am now having a small issue, that I am not sure if it is related to flash, the wrapper, or maybe something else like firefox it's self.

What happens to me is, flash randomly stops working.  I will go to a site like youtube and just see a white space where the video should be, exactly like what I would see before I had run this script and got flash working.

So far all I have to do is close by browser, and reopen it and all works again.    

I consider this a very minor issue as a simple re-launching of the browser fixes it, but I was looking around to see if anyone else is having this issue, and if there is something I can do to fix.

I would be glad to file a bugreport over the issue, but do not know how to figure out which software is failing on me, or who I should send the bug report too.

---

### Post by John.Michael.Kane on 2007-09-04
> **Jeff_From_VA said:**
> I used this script and all was well.  I appreciate it very much!!

I am now having a small issue, that I am not sure if it is related to flash, the wrapper, or maybe something else like firefox it's self.

What happens to me is, flash randomly stops working.  I will go to a site like youtube and just see a white space where the video should be, exactly like what I would see before I had run this script and got flash working.

So far all I have to do is close by browser, and reopen it and all works again.    

I consider this a very minor issue as a simple re-launching of the browser fixes it, but I was looking around to see if anyone else is having this issue, and if there is something I can do to fix.

I would be glad to file a bugreport over the issue, but do not know how to figure out which software is failing on me, or who I should send the bug report too.

You can add your report to the one below, As of now the report is filed against  the (nspluginwrapper).
[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991)

For information on how to set up launchpad.
Step1: Sign up for a user name at [https://launchpad.net/distros/ubuntu](https://launchpad.net/distros/ubuntu) click on log in/register
Step2: Add your info to this report [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991)
Note: You will receive emails giving the status of your report,and if others have added to it.

---

### Post by John.Michael.Kane on 2007-09-04
A question to those having this problem. Does the issue manifest itself when using 32 bit Firefox with Flash w/sound and Java for AMD64 howto? 

Reason being is that if the issue manifests under the 32bit FireFox guide then this "might" not be a (nspluginwrapper) issue, As the issue would then fall on the flash plugin itself.

---

### Post by Kilz on 2007-09-04
> **SD-Plissken said:**
> A question to those having this problem. Does the issue manifest itself when using 32 bit Firefox with Flash w/sound and Java for AMD64 howto? 

Reason being is that if the issue manifests under the 32bit FireFox guide then this "might" not be a (nspluginwrapper) issue, As the issue would then fall on the flash plugin itself.

I did a search the other day, and [posted some results on another thread]("http://ubuntuforums.org/showpost.php?p=3303042&postcount=28"). It looks like even people with the 32bit version of Ubuntu have crashing problems with flash and firefox.

---

### Post by John.Michael.Kane on 2007-09-04
> **Kilz said:**
> I did a search the other day, and [posted some results on another thread]("http://ubuntuforums.org/showpost.php?p=3303042&postcount=28"). It looks like even people with the 32bit version of Ubuntu have crashing problems with flash and firefox.

Wow! I just a few of those threads, and other bug reports. I would say theres more to this issue, and it seems like the problem truly might indeed be with flash it self or something else entirely, and not nspluginwrapper. 

Also the flash based sites that users seem to have problems with are not all youtube based they seem to vary. 

IMHO it's not an nspluginwrapper problem any longer, and the problem lies elsewhere, As the problem can be replicated under 32bit firefox, and without the use of the nspluginwrapper.

That said. Those who might be looking for fixes. Heres a list of workarounds that worked for others in some of those threads. Note: I have not tested the workarounds, and can't vouch for them.

This member claims that moving to kernel 2.6.22-10 solved the flash issue for him.
[Howto: Simple kernel upgrade (Feisty or Edgy) to Gutsy's developing kernel single post.]("http://ubuntuforums.org/showpost.php?p=3171680&postcount=222")

If you wish to move to kernel 2.6.22-10 while on feisty or edgy the thread below explains how.
[Howto: Simple kernel upgrade (Feisty or Edgy) to Gutsy's developing kernel full thread.]("http://ubuntuforums.org/showthread.php?t=511974")

Another user found another fix in the bug report below that is suppose to help alleviate the issue.
[firefox crashed -- libflashplayer.so]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/104470") Note: if you want you can also add your any current issues or findings to this report as well.

Heres the work around. 
[Youtube Crashes Firefox About 3/4 of the Time]("http://ubuntuforums.org/showpost.php?p=2683437&postcount=34")

---

### Post by lucaspr on 2007-09-04
Thanx for the scipt!! Adjusted it a bit to work in Gutsy!! Works like a dime! 

My training is in flash so I had to get it going! But it is! 

Thanx again!

---

### Post by John.Michael.Kane on 2007-09-04
> **lucaspr said:**
> Thanx for the scipt!! Adjusted it a bit to work in Gutsy!! Works like a dime! 

My training is in flash so I had to get it going! But it is! 

Thanx again!

Please lets us know if you notice any of the before mentioned problems eg: locking up browser shutdowns etc.

Thanks.

---

### Post by jcronkhite on 2007-09-04
This is great!  Thanks!

I just wanted to point out that Update Manager reports a patch available for NSPLUGINWRAPPER from version 0.9.91.4-0ubuntu3~upure64 to 0.9.91.5-0ubuntu1~upure64.  When I apply this patch, Flash stops working.  After I remove nspluginwrapper and start over with the previous version all works fine again.

I guess the new nspluginwrapper patch is killing flash.  Just a head's up.  Oh, and sorry if this was stated earlier.  I'm at work and on the go so I thought I'd post to prevent others from beating their heads against the wall.

Is there a way to tell Update Manager to stop providing the update?  Would be nice to prevent the nag on this patch only for now.  Thanks again!

---

### Post by tolstoyboy on 2007-09-04
Hi, I have 7.04 64bit installed on my Acer Aspire 5102 notebook. Things run very well in general, but I am having video issues in Firefox. Occasionally when navigating between links,the browser screen becomes scrambled for a short moment (imagine a scrambled color tv screen). At times it occurs in certain frames and other times the entire browser viewing window. The entire notebook screen never becomes scrambled, so I think this has something to do with the Flash plugin. I used the script provided by Kilz and it seemed to work fine...aside from this scrambling. I don't know if this can damage the lcd or is simply a minor graphical error. My cpu is AMD Turionx2. Video is ATI Xpress 1100 integrated. 

Has anyone encountered and solved this issue? Perhaps I didn't see a post...
Thanks in advance...

---

### Post by Spike-X on 2007-09-04
> **Jeff_From_VA said:**
> I used this script and all was well.  I appreciate it very much!!

I am now having a small issue, that I am not sure if it is related to flash, the wrapper, or maybe something else like firefox it's self.

What happens to me is, flash randomly stops working.  I will go to a site like youtube and just see a white space where the video should be, exactly like what I would see before I had run this script and got flash working.

So far all I have to do is close by browser, and reopen it and all works again.    

I get that too. Both before and after installing the latest version of nspluginwrapper. Thank goodness for Session Manager!

---

### Post by Crinos512 on 2007-09-04
Will this work in the 64 bit Opera just released??

---

### Post by Nameless_one on 2007-09-04
From the little I've read and the many things that I tried, I think this doesn't work with the new, 64-bit Opera. Or am I wrong? I'd be really glad if someone proved me wrong. 

I manage to get Opera to detect the plugin, but when I try it on youtube, it does't work correctly. No video is shown, only a black square, with the two buttons youtube shows you after the vifeo has finished, and they tremble, they have no text, and are not clickable. THe progress bar is full, and none of th ebuttons work.

---

### Post by vbvamsi on 2007-09-04
I am a newbie to linux. I followed the above install instructions to install flash plugin. I can get flash video working but no sound. I also installed the alsa part from your thread but no luck. After that I tried different solutions from many other threads to get the sound working. But none of them worked. I am using Ubuntu 7.04. This is the output for the requested commands. Hope you can provide a solution for this. Thanks very much in advance.

$ ls -al /usr/lib/mozilla/plugins
total 8419
drwxr-xr-x 2 root    root        640 2007-09-04 20:22 
drwxr-xr-x 3 root    root         72 2007-04-15 07:58 ..
-r--r--r-- 1    1003 users       856 2007-06-19 20:31 flashplayer.xpt
-rwxr-xr-x 1    1003 users   7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 root    root         38 2007-08-31 03:22 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
-rw-r--r-- 1 root    root     118744 2007-03-20 05:40 libvlcplugin.so
-rw-r--r-- 1 root    root     269216 2007-01-25 19:17 mplayerplug-in-dvx.so
-rw-r--r-- 1 root    root        981 2007-01-25 19:17 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root    root     269408 2007-01-25 19:17 mplayerplug-in-qt.so
-rw-r--r-- 1 root    root        981 2007-01-25 19:17 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root    root     269472 2007-01-25 19:17 mplayerplug-in-rm.so
-rw-r--r-- 1 root    root        981 2007-01-25 19:17 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root    root     270648 2007-01-25 19:17 mplayerplug-in.so
-rw-r--r-- 1 root    root     269760 2007-01-25 19:17 mplayerplug-in-wmp.so
-rw-r--r-- 1 root    root        981 2007-01-25 19:17 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root    root        981 2007-01-25 19:17 mplayerplug-in.xpt
-rwx------ 1 vbvamsi vbvamsi   70120 2007-09-04 20:22 npwrapper.libflashplayer.so


$ ls -al /usr/lib/firefox/plugins
total 13
drwxr-xr-x 2 root root   528 2007-08-31 03:22 .
drwxr-xr-x 5 root root   840 2007-08-29 13:31 ..
lrwxrwxrwx 1 root root    54 2007-08-31 03:22 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji_mozilla_firefox.so
-rw-r--r-- 1 root root 11072 2007-07-31 09:29 libunixprintplugin.so
lrwxrwxrwx 1 root root    37 2007-08-30 22:57 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so
lrwxrwxrwx 1 root root    42 2007-08-30 23:03 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2007-08-30 23:03 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2007-08-30 23:03 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2007-08-30 23:03 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2007-08-30 23:03 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2007-08-30 23:03 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2007-08-30 23:03 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2007-08-30 23:03 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root    52 2007-08-30 00:21 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so


$ ls -al /tmp/nsplugwrapper
ls: /tmp/nsplugwrapper: No such file or directory

---

### Post by Kilz on 2007-09-04
> **vbvamsi said:**
> I am a newbie to linux. I followed the above install instructions to install flash plugin. I can get flash video working but no sound. I also installed the alsa part from your thread but no luck. After that I tried different solutions from many other threads to get the sound working. But none of them worked. I am using Ubuntu 7.04. This is the output for the requested commands. Hope you can provide a solution for this. Thanks very much in advance.



Try opening a terminal and using this command.
```
sudo chown root:root  /usr/lib/mozilla/plugins/*
```

---

### Post by Kilz on 2007-09-04
> **Jeff_From_VA said:**
> I used this script and all was well.  I appreciate it very much!!

I am now having a small issue, that I am not sure if it is related to flash, the wrapper, or maybe something else like firefox it's self.

What happens to me is, flash randomly stops working.  I will go to a site like youtube and just see a white space where the video should be, exactly like what I would see before I had run this script and got flash working.

So far all I have to do is close by browser, and reopen it and all works again.    

I consider this a very minor issue as a simple re-launching of the browser fixes it, but I was looking around to see if anyone else is having this issue, and if there is something I can do to fix.

I would be glad to file a bugreport over the issue, but do not know how to figure out which software is failing on me, or who I should send the bug report too.
I recommend reading the first post, especially that section on "How to get help" in big red letters.

---

### Post by Applegeek on 2007-09-05
This probably belongs in another post, but while we're on the subject of dysfunctional Adobe Flash products, there is the newest unstable version at [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

This will give you full screen mode, but will crash if the original screen width is not divisible by 16....

So if someone just HAS to run full screen mode, this might be something to try, although I don't recommend it as it crashes on seemingly random video content.

---

### Post by Dr.Balagopal on 2007-09-05
Dear Kiltz,  I have been using Fiesty 64 for quite some time and was really frustrated trying to install flash,  You made it so simple for us. I dont know how to thank you. you are great !!!!

---

### Post by mac25 on 2007-09-05
Hi Kilz,I have been using Fiesty 64 since it was released and could not get flash running till now.
Us new comers really do need this sort of help
So just one more, thank you..

---

### Post by o3rat on 2007-09-05
Dear Kilz,

Thanks for the script worked for a while, but  unfortunately flash , and sound in general hate me.

I started off running 2.6.20-16-generic (on x86 machine)  and i used the script to fix flash+sound. Everything was smooth except my wifi didnt work. Turns out  when I upgraded to 2.6.22-9-generic my wifi worked, flash installed, but no sound again : ( 

If only you worked for adobe and made 64bit flash for linux and ended this for good...

---

### Post by Kilz on 2007-09-06
> **o3rat said:**
> Dear Kilz,

Thanks for the script worked for a while, but  unfortunately flash , and sound in general hate me.

I started off running 2.6.20-16-generic (on x86 machine)  and i used the script to fix flash+sound. Everything was smooth except my wifi didnt work. Turns out  when I upgraded to 2.6.22-9-generic my wifi worked, flash installed, but no sound again : ( 

If only you worked for adobe and made 64bit flash for linux and ended this for good...

Do you have sound in other applications?

---

### Post by o3rat on 2007-09-06
> **Kilz said:**
> Do you have sound in other applications?

Ya, I have sound in gaim and rhythmbox.

---

### Post by upp3rd0g on 2007-09-06
I did the following:

Run script Getflash (nspluginwrapper-install-0-1.6.tar.gz) as regular user in Ubuntu 7.04. Result => working flash, but no sound

I took a quick look through this thread and I read about the recommendation to set ownersettings of the files in /usr/lib/mozilla/plugin directory to root:root, so I did that. Result: flash not working anymore...

I noticed plugins were installed with owner:group set to my regular user, instead of root. I ran the script again with sudo. Result => working flash + working sound.

Thanx Kilz!

---

### Post by kansei on 2007-09-07
I'm getting some unpleasant data from powertop (intel utility for telling you which processes are using the most power on your system)

Wakeups-from-idle per second : 556.0    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  69.8% (728.0)      npviewer.bin : schedule_timeout (process_timeout) 
   7.9% ( 82.6)       <interrupt> : nvidia 
   6.5% ( 67.9)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   4.1% ( 42.6)       <interrupt> : uhci_hcd:usb1, ehci_hcd:usb5 
   2.3% ( 24.3)              Xorg : do_setitimer (it_real_fn) 
   1.8% ( 18.9)       compiz.real : schedule_timeout (process_timeout) 

Any clue as to why? Yes, I'm running firefox, and firefox is *always* running on the system --but no open tab has anything plugin-related on it.

---

### Post by Kilz on 2007-09-08
> **kansei said:**
> I'm getting some unpleasant data from powertop (intel utility for telling you which processes are using the most power on your system)

Wakeups-from-idle per second : 556.0    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  69.8% (728.0)      npviewer.bin : schedule_timeout (process_timeout) 
   7.9% ( 82.6)       <interrupt> : nvidia 
   6.5% ( 67.9)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   4.1% ( 42.6)       <interrupt> : uhci_hcd:usb1, ehci_hcd:usb5 
   2.3% ( 24.3)              Xorg : do_setitimer (it_real_fn) 
   1.8% ( 18.9)       compiz.real : schedule_timeout (process_timeout) 

Any clue as to why? Yes, I'm running firefox, and firefox is *always* running on the system --but no open tab has anything plugin-related on it.

Are you sure there is no flash at all on the page? Flash seems to be used in all sorts of ways lately. Secondly, what version of the wrapper are you using? how long ago did you install it?

---

### Post by kansei on 2007-09-08
I installed it sometime when Gutsy was still tribe 1. Since it's actually a gutsy package, I assumed it would be updated along with everything else (I update 2-3x a day because I'm just dying for something to break lol).

version 0.9.91.4-3ubuntu2 by the way

this is probably a nonissue, but until there is an i8k kernel module for 64-bit linux, I gotta do what I can to keep the processor/gpu temps as low as possible.

---

### Post by incubus on 2007-09-08
Kilz,

Would you mind taking a look at this and giving us your opinion?  It's a problem with a recent upgrade in gutsy, replacing the package 'linux32' with 'util-linux'.  [The command is now included in the second package]
[http://ubuntuforums.org/showthread.php?t=545478](http://ubuntuforums.org/showthread.php?t=545478)

incubus

---

### Post by kansei on 2007-09-08
With [www.google.com](www.google.com) as the only open page in firefox after killing firefox and starting fresh:

Wakeups-from-idle per second : 552.9    interval: 10.0s
Power usage (5 minute ACPI estimate) :   0.2 W (702.0 hours left)

Top causes for wakeups:
  46.1% (277.3)      npviewer.bin : schedule_timeout (process_timeout) 
  17.6% (105.6)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  10.9% ( 65.5)       <interrupt> : extra timer interrupt 
  10.2% ( 61.2)       <interrupt> : nvidia 
   4.3% ( 25.6)       compiz.real : schedule_timeout (process_timeout) 
   3.4% ( 20.2)              Xorg : do_setitimer (it_real_fn)

---

### Post by John.Michael.Kane on 2007-09-08
Heres an update on the report.
[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991)

Since nspluginwrapper is being used outside the official Ubuntu repositories i.e., on feisty. Theres nothing they can do about it, and users of nspluginwrapper, and flash  under 64bit are advised to file bug reports with the writes of those packages directly.

---

### Post by BlacKsheep88 on 2007-09-08
I ran both scripts (the second one does clean up after itself, btw) and no results. Here's my output;

> drgonzo@gonzocox:~$ ls -al /usr/lib/mozilla/plugins
total 6900
drwxr-xr-x 2 root root     4096 2007-09-08 11:56 .
drwxr-xr-x 3 root root     4096 2007-04-15 07:58 ..
-r--r--r-- 1 1003 users     856 2007-06-19 20:31 flashplayer.xpt
-rwxr-xr-x 1 1003 users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 root root       36 2007-09-07 19:20 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root       37 2007-09-07 19:20 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root       34 2007-09-07 19:20 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root       35 2007-09-07 19:20 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root       36 2007-09-07 19:20 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root       37 2007-09-07 19:20 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root       42 2007-09-07 19:20 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root       43 2007-09-07 19:20 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt


> drgonzo@gonzocox:~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 root root  4096 2007-09-08 11:50 .
drwxr-xr-x 5 root root  4096 2007-04-15 08:07 ..
lrwxrwxrwx 1 root root    36 2007-09-07 19:20 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-09-07 19:20 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-09-07 19:20 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-09-07 19:20 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-09-07 19:20 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-09-07 19:20 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-09-07 19:20 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-09-07 19:20 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2007-04-03 11:30 libunixprintplugin.so
lrwxrwxrwx 1 root root    52 2007-09-08 11:50 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so


> drgonzo@gonzocox:~$ ls -al /tmp/nsplugwrapper
total 2668
drwxr-xr-x  3 root root     4096 2007-09-08 11:55 .
drwxrwxrwt 14 root root     4096 2007-09-08 11:56 ..
drwxr-xr-x  2 1003 users    4096 2007-09-08 11:56 install_flash_player_9_linux
-rw-r--r--  1 root root  2608602 2007-07-05 14:48 install_flash_player_9_linux.tar.gz
-rw-r--r--  1 root root   100918 2007-08-21 01:43 nspluginwrapper_0.9.91.4_amd64.deb


I'm running 7.04 AMD64 and my browser is Swiftweasel 2.0.0.6

---

### Post by Kilz on 2007-09-08
> **SD-Plissken said:**
> Heres an update on the report.
[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991)

Since nspluginwrapper is being used outside the official Ubuntu repositories i.e., on feisty. Theres nothing they can do about it, and users of nspluginwrapper, and flash  under 64bit are advised to file bug reports with the writes of those packages directly.

How come I am not surprised?

---

### Post by Kilz on 2007-09-08
> **incubus said:**
> Kilz,

Would you mind taking a look at this and giving us your opinion?  It's a problem with a recent upgrade in gutsy, replacing the package 'linux32' with 'util-linux'.  [The command is now included in the second package]
[http://ubuntuforums.org/showthread.php?t=545478](http://ubuntuforums.org/showthread.php?t=545478)

incubus

This is a problem brought about because of the nature of Gutsy. It is under development. [On post number one of this topic]("http://ubuntuforums.org/showpost.php?p=2863873&postcount=1") in big bold red letters it says that this script is not for Gutsy. There are numerous reasons , this is one of them. I was hoping not to have to write a script for Gutsy, what I would like you and all other people running Gutsy do is File Bug Reports. One of the features of Gutsy is that nspluginwrapper should install and work for you when you install flash. If it doesnt, its broke. Please, Please, Please file bug reports if it isnt working so the developers working on it can get it working before Gutsy is released. If you dont file the reports they will think its ok and never fix it.

---

### Post by Kilz on 2007-09-08
> **kansei said:**
> With [www.google.com](www.google.com) as the only open page in firefox after killing firefox and starting fresh:

Wakeups-from-idle per second : 552.9    interval: 10.0s
Power usage (5 minute ACPI estimate) :   0.2 W (702.0 hours left)

Top causes for wakeups:
  46.1% (277.3)      npviewer.bin : schedule_timeout (process_timeout) 
  17.6% (105.6)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  10.9% ( 65.5)       <interrupt> : extra timer interrupt 
  10.2% ( 61.2)       <interrupt> : nvidia 
   4.3% ( 25.6)       compiz.real : schedule_timeout (process_timeout) 
   3.4% ( 20.2)              Xorg : do_setitimer (it_real_fn)

If you are running Gutsy as post #281 by you says. Please file a bug report on launchpad. Please read my last post for the reasons why Gutsy is not supported by this script.

---

### Post by Kilz on 2007-09-08
> **BlacKsheep88 said:**
> I ran both scripts (the second one does clean up after itself, btw) and no results. Here's my output;

I'm running 7.04 AMD64 and my browser is Swiftweasel 2.0.0.6

Exactly what is the problem you are experiencing?

---

### Post by BlacKsheep88 on 2007-09-08
> **Kilz said:**
> Exactly what is the problem you are experiencing?

There's no flash installed on my browsers after I ran the script. They were both closed when I ran it, and I tested both Firefox and Swiftweasel, and no Flash was detected.

---

### Post by Kilz on 2007-09-08
It looks like everything was downloaded and installed. Not sure why the wrapper wasnt made. Can you please give the the results of


```
ls -al ~/.mozilla/plugins
```

---

### Post by Hanselang on 2007-09-09
Works like a charm!
Kudos :guitar:

---

### Post by Baby Boy on 2007-09-09
Install script works perfectly, I can't believe I finally have Flash on my 64-bit Ubuntu. I couldn't get Flash to work via Firefox32 in your other guide, but this was just very simple.

Thanks Kilz :grin:=D>,

---

### Post by Shadowtester on 2007-09-09
I tried using the script to install flash on my Kubuntu 7.04 64 bit and it did not work so I then downloaded the trouble shooting script and tried that. This is the error it gave me about a package not being available

E: Couldn't find package nspluginwrapper-i386

I tried apt-get install nspluginwrapper-i386 but when I did that I got the response of

apt-get install nspluginwrapper-i386
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package nspluginwrapper-i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nspluginwrapper
E: Package nspluginwrapper-i386 has no installation candidate

---

### Post by BlacKsheep88 on 2007-09-09
> **Kilz said:**
> It looks like everything was downloaded and installed. Not sure why the wrapper wasnt made. Can you please give the the results of


```
ls -al ~/.mozilla/plugins
```

```
drgonzo@gonzocox:/usr/lib$ ls -al /usr/lib/mozilla/plugins
total 6900
drwxr-xr-x 2 root root     4096 2007-09-08 11:56 .
drwxr-xr-x 3 root root     4096 2007-04-15 07:58 ..
-r--r--r-- 1 1003 users     856 2007-06-19 20:31 flashplayer.xpt
-rwxr-xr-x 1 1003 users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 root root       36 2007-09-07 19:20 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root       37 2007-09-07 19:20 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root       34 2007-09-07 19:20 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root       35 2007-09-07 19:20 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root       36 2007-09-07 19:20 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root       37 2007-09-07 19:20 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root       42 2007-09-07 19:20 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root       43 2007-09-07 19:20 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt

```

---

### Post by Kilz on 2007-09-09
> **BlacKsheep88 said:**
> ```
drgonzo@gonzocox:/usr/lib$ ls -al /usr/lib/mozilla/plugins


The information you supplied was not what I had asked for . Please supply the results of 
[CODE]ls -al ~/.mozilla/plugins
```

You supplied the results of ls -al /usr/lib/mozilla/plugins. Prehaps I confused you. You can just cut and paste the command above.

---

### Post by BlacKsheep88 on 2007-09-09
> **Kilz said:**
> The information you supplied was not what I had asked for . Please supply the results of 
```
ls -al ~/.mozilla/plugins
```

You supplied the results of ls -al /usr/lib/mozilla/plugins. Prehaps I confused you. You can just cut and paste the command above.
```
drgonzo@gonzocox:~$ ls -al ~/.mozilla/plugins
ls: /home/drgonzo/.mozilla/plugins: No such file or directory

```

---

### Post by Kilz on 2007-09-09
> **BlacKsheep88 said:**
> ```
drgonzo@gonzocox:~$ ls -al ~/.mozilla/plugins
ls: /home/drgonzo/.mozilla/plugins: No such file or directory

```

Ok, then enter in these commands
```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```
then
```
sudo mv ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
```
and everything should work after a browser restart.

---

### Post by waddletron on 2007-09-09
After compiling my own ALSA (to fix a soundcard issue), sound in Flash stopped working for me.

I tried reinstalling from the script again but this did not work either.

Once apon a time, sound did work for me. But now it does not.

I'm on Feisty

Any help would be appreciated.

---

### Post by BlacKsheep88 on 2007-09-09
> **Kilz said:**
> Ok, then enter in these commands
```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```
then
```
sudo mv ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
```
and everything should work after a browser restart.

That did it! Thank you!

---

### Post by Cosmic_Crusader on 2007-09-10
Worked almost perfectly, the permissions on the file:
  **/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so**
were restricted to the user which ran the script.

To make it work for other users I changed the ownership to root:

```
sudo chown root:root /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo chmod 0555 /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
```

---

### Post by keterini on 2007-09-11
Kilz!

Thx so much for your genious solution! It worked perfectly!

---

### Post by lecapogrande on 2007-09-11
thanks, I almost gave up

---

### Post by JIMW428 on 2007-09-11
> **Kilz said:**
> Ok, then enter in these commands
```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```
then
```
sudo mv ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
```
and everything should work after a browser restart.

I have the same problem, but when I run ```
 nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
``` I get the following result
```
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
```
Any idea what I've done to screw this up so badly?

I forgot to add that after running your script, I get a broken package warning.

---

### Post by Kilz on 2007-09-11
> **JIMW428 said:**
> I have the same problem, but when I run ```
 nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
``` I get the following result
```
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
```
Any idea what I've done to screw this up so badly?

I forgot to add that after running your script, I get a broken package warning.

Please read the how to get help section of the howto.

---

### Post by JIMW428 on 2007-09-11
The script runs, but fails to install correctly and appears to need a missing library

Here are my particulars

Version- Ubuntu 7.04
/home/jim/Desktop/nspluginwrapper-install-0-1.6-ts.tar.gz

Per the instructions in the READ ME file, I ran 
ls -al /usr/lib/mozilla/plugins

results 

total 6900
drwxr-xr-x 2 root root     4096 2007-09-11 18:56 .
drwxr-xr-x 3 root root     4096 2007-04-15 06:58 ..
-r--r--r-- 1 1003 users     856 2007-06-19 19:31 flashplayer.xpt
-rwxr-xr-x 1 1003 users 7040036 2007-06-19 19:31 libflashplayer.so
lrwxrwxrwx 1 root root       36 2007-08-26 12:15 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root       37 2007-08-26 12:15 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root       34 2007-08-26 12:15 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root       35 2007-08-26 12:15 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root       36 2007-08-26 12:15 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root       37 2007-08-26 12:15 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root       42 2007-08-26 12:15 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root       43 2007-08-26 12:15 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt

RAN

ls -al /usr/lib/firefox/plugins

RESULTS

total 20
drwxr-xr-x 2 root root  4096 2007-09-02 15:43 .
drwxr-xr-x 5 root root  4096 2007-08-26 17:36 ..
lrwxrwxrwx 1 root root    36 2007-08-26 12:14 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-08-26 12:14 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-08-26 12:14 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-08-26 12:14 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-08-26 12:14 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-08-26 12:14 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-08-26 12:14 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-08-26 12:14 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2007-07-31 08:29 libunixprintplugin.so
lrwxrwxrwx 1 root root    52 2007-09-02 15:43 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so


RAN
ls -al /tmp/nsplugwrapper

RESULTS

total 2668
drwxr-xr-x  3 root root     4096 2007-09-11 18:56 .
drwxrwxrwt 13 root root     4096 2007-09-11 19:10 ..
drwxr-xr-x  2 1003 users    4096 2007-09-11 18:56 install_flash_player_9_linux
-rw-r--r--  1 root root  2608602 2007-07-05 13:48 install_flash_player_9_linux.tar.gz
-rw-r--r--  1 root root   100918 2007-08-21 00:43 nspluginwrapper_0.9.91.4_amd64.deb

---

### Post by Kilz on 2007-09-11
> **JIMW428 said:**
> The script runs, but fails to install correctly and appears to need a missing library



From the looks of things you may be correct. as it looks like the wrapper downloaded. Im not sure its installed though. You can try 
```
sudo apt-get install -f
```
to fix any problems with the package database. What i need to know is the installed version of lib32gcc1. You can get it one of 2 ways. 
1 Do a search in synaptic, and copy the information in a reply
or 
2 install apt-show-versions and then get the information
```
sudo apt-get install apt-show-versions
apt-show-versions -a -p lib32gcc1
```

---

### Post by JIMW428 on 2007-09-11
Still no luck????? Why did I get an abort?

RAN
sudo apt-get install -f

RESULT

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tclcurl gstreamer0.10-ffmpeg libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

RAN

sudo apt-get install apt-show-versions
apt-show-versions -a -p lib32gcc1

RESULTS

sudo apt-get install apt-show-versions
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tclcurl gstreamer0.10-ffmpeg libgtkglext1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libapt-pkg-perl
The following NEW packages will be installed:
  apt-show-versions libapt-pkg-perl
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 104kB of archives.
After unpacking 434kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

---

### Post by Kilz on 2007-09-12
> **JIMW428 said:**
> Still no luck????? Why did I get an abort?

RAN
sudo apt-get install -f

RESULT

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tclcurl gstreamer0.10-ffmpeg libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

RAN

sudo apt-get install apt-show-versions
apt-show-versions -a -p lib32gcc1

RESULTS

sudo apt-get install apt-show-versions
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tclcurl gstreamer0.10-ffmpeg libgtkglext1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libapt-pkg-perl
The following NEW packages will be installed:
  apt-show-versions libapt-pkg-perl
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 104kB of archives.
After unpacking 434kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

This looks like there is some conflict in your package database. I have no idea why it is not allowing you to install applications. sudo apt-get install -f is telling us nothing is wrong. 
It might be possible the packages its telling you to remove are the problem, but 
Im not 100% sure. You could try to remove them, but Im not sure it will help. ```
sudo apt-get clean
``` may also help if you have a corrupted package in the apt cashe.

---

### Post by JIMW428 on 2007-09-12
As you recommended, I ran **sudo apt-get clean **which didn't seem to help anything. I seem to be at a dead end. Will the new Oct release fix this problem? If so, it seems that the best thing to do is just put up  with not having flash until then.

---

### Post by John.Michael.Kane on 2007-09-12
> **JIMW428 said:**
> As you recommended, I ran **sudo apt-get clean **which didn't seem to help anything. I seem to be at a dead end. 

You can try to configure all packages that are unconfigured. 
```
gksudo dpkg --configure -a
```

Try letting apt-get remove all problematic packages.
```
gksudo aptitude -f remove
```

Another option is to try removing the bad packages one at a time.
```
gksudo aptitude remove -f bad package name here
```

The rerun
```
gksudo aptitude -f remove
```

After which try reinstalling the program you were when the issue happened. 

Also can you post your sources.list.
```
gksudo gedit /etc/apt/source.list
```

> **JIMW428 said:**
> Will the new Oct release fix this problem? If so, it seems that the best thing to do is just put up  with not having flash until then.

In theory the October Ubuntu  release should allow for flash install with out the need for Kilz script. This is provided the bug linked to is fixed.
[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136267](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136267)

There where also some post with regards to flash locking up even under Gutsy. So theres still a chance for problems. 

Your best bet if you have to time, Is to run gutsy on a separate partition load up one at a time the same programs that you use under feisty, and test each one while taking notes of any issues, and file bug reports on them.

---

### Post by MeganM on 2007-09-12
ok so i dont exactly know what went wrong here! please help!

megan@megan:~$ ls -al /usr/lib/mozilla/plugins
total 8644
drwxr-xr-x 2 root root     4096 2007-09-12 22:04 .
drwxr-xr-x 4 root root     4096 2007-08-30 22:28 ..
-r--r--r-- 1 1003 users     856 2007-06-19 19:31 flashplayer.xpt
-rwxr-xr-x 1 1003 users 7040036 2007-06-19 19:31 libflashplayer.so
-rw-r--r-- 1 root root  1779152 2006-05-23 04:46 libvlcplugin.so
lrwxrwxrwx 1 root root       50 2007-08-30 22:14 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
megan@megan:~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 root root 4096 2007-09-12 21:18 .
drwxr-xr-x 5 root root 4096 2007-08-01 08:42 ..
-rw-r--r-- 1 root root 8652 2007-07-31 07:25 libunixprintplugin.so
lrwxrwxrwx 1 root root   37 2007-08-30 22:28 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so
lrwxrwxrwx 1 root root   50 2007-08-30 22:14 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
lrwxrwxrwx 1 root root   52 2007-09-12 21:18 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
megan@megan:~$ ls -al /tmp/nsplugwrapper
ls: /tmp/nsplugwrapper: No such file or directory
megan@megan:~$

---

### Post by Kilz on 2007-09-13
> **MeganM said:**
> ok so i dont exactly know what went wrong here! please help!

megan@megan:~$ ls -al /usr/lib/mozilla/plugins
total 8644
drwxr-xr-x 2 root root     4096 2007-09-12 22:04 .
drwxr-xr-x 4 root root     4096 2007-08-30 22:28 ..
-r--r--r-- 1 1003 users     856 2007-06-19 19:31 flashplayer.xpt
-rwxr-xr-x 1 1003 users 7040036 2007-06-19 19:31 libflashplayer.so
-rw-r--r-- 1 root root  1779152 2006-05-23 04:46 libvlcplugin.so
lrwxrwxrwx 1 root root       50 2007-08-30 22:14 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
megan@megan:~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 root root 4096 2007-09-12 21:18 .
drwxr-xr-x 5 root root 4096 2007-08-01 08:42 ..
-rw-r--r-- 1 root root 8652 2007-07-31 07:25 libunixprintplugin.so
lrwxrwxrwx 1 root root   37 2007-08-30 22:28 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so
lrwxrwxrwx 1 root root   50 2007-08-30 22:14 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
lrwxrwxrwx 1 root root   52 2007-09-12 21:18 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
megan@megan:~$ ls -al /tmp/nsplugwrapper
ls: /tmp/nsplugwrapper: No such file or directory
megan@megan:~$

What version of Ubuntu are you running, and what was the name of the script you downloaded and then extracted?

---

### Post by ryanxdurst on 2007-09-13
there's no "extract here" option when i right click the file. is there any other way to extract it?   thanks.

---

### Post by John.Michael.Kane on 2007-09-13
> **ryanxdurst said:**
> there's no "extract here" option when i right click the file. is there any other way to extract it?   thanks.

There should be.

In any case you can try doing it via the terminal.
1) ```
cd Desktop
```

2) ```
tar zxvf nspluginwrapper-install-0-1.6.tar.gz
```

After which you should have a folder labeled nspluginwrapper install. Open folder, and proceed as normal.

---

### Post by kansei on 2007-09-13
> **ryanxdurst said:**
> there's no "extract here" option when i right click the file. is there any other way to extract it?   thanks.

Is there an 'open in archive manager' or similar option though?

---

### Post by ryanxdurst on 2007-09-13
um, there was a "create archive" option, but I don't know if that's what we want.  SD-Plissken's post did the trick though. thanks for the help. it's nice to have flash again.

---

### Post by eJamesPC on 2007-09-14
Hate to piss in the corn flakes but this script did not work...  Swiftfox, firefox, or any fox...:(
 ls -al /usr/lib/mozilla/plugins
total 6996
drwxr-xr-x 2 ejames ejames    4096 2007-09-13 22:54 .
drwxr-xr-x 3 root   root      4096 2007-04-15 06:58 ..
-r--r--r-- 1   1003 users      856 2007-06-19 19:31 flashplayer.xpt
-rw-r--r-- 1 ejames ejames   19456 2007-01-05 13:52 libflash-mozplugin.so
-rwxr-xr-x 1   1003 users  7040036 2007-06-19 19:31 libflashplayer.so
lrwxrwxrwx 1 ejames ejames      36 2007-08-26 16:20 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 ejames ejames      37 2007-08-26 16:20 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 ejames ejames      34 2007-08-26 16:20 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 ejames ejames      35 2007-08-26 16:20 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 ejames ejames      36 2007-08-26 16:20 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 ejames ejames      37 2007-08-26 16:20 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 ejames ejames      42 2007-08-26 16:20 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 ejames ejames      43 2007-08-26 16:20 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 ejames ejames   70120 2007-09-13 22:54 npwrapper.libflashplayer.so

---

### Post by nephish on 2007-09-14
thanks for this, Kliz.
easy as anything. 
thanks for your help with others here on this forum too, thats helped me out a lot too.

---

### Post by Kilz on 2007-09-14
> **eJamesPC said:**
> Hate to piss in the corn flakes but this script did not work...  Swiftfox, firefox, or any fox...:(
 ls -al /usr/lib/mozilla/plugins
total 6996
drwxr-xr-x 2 ejames ejames    4096 2007-09-13 22:54 .
drwxr-xr-x 3 root   root      4096 2007-04-15 06:58 ..
-r--r--r-- 1   1003 users      856 2007-06-19 19:31 flashplayer.xpt
-rw-r--r-- 1 ejames ejames   19456 2007-01-05 13:52 libflash-mozplugin.so
-rwxr-xr-x 1   1003 users  7040036 2007-06-19 19:31 libflashplayer.so
lrwxrwxrwx 1 ejames ejames      36 2007-08-26 16:20 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 ejames ejames      37 2007-08-26 16:20 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 ejames ejames      34 2007-08-26 16:20 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 ejames ejames      35 2007-08-26 16:20 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 ejames ejames      36 2007-08-26 16:20 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 ejames ejames      37 2007-08-26 16:20 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 ejames ejames      42 2007-08-26 16:20 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 ejames ejames      43 2007-08-26 16:20 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 ejames ejames   70120 2007-09-13 22:54 npwrapper.libflashplayer.so

What version of the script did you install? What was the name of the file you downloaded, that will give me the version.

---

### Post by kansei on 2007-09-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/125681](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/125681) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It should be working in Gutsy again:

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/125681](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/125681)

---

### Post by tolstoyboy on 2007-09-14
Thank you for the script Kilz. I am a newb and now I am crying. The update you posted today will not install for me. I am on 7.04. I extract the files, click Get Flash, and then my terminal flashes up on screen and goes away...nothing seems to happen. 
The script worked beautifully before..what happened?

I reinstalled my OS. Could you possibly give a download link to the script before today's update?

---

### Post by hujuice on 2007-09-14
The today version of this very powerful script is wrong (for my bash).
A couple of "fi" has been lost.

My correction is GIVEN.
I didn't change an incorrect usage of sleep.

Hey Kilz, thanks a lot. :) Keep corrections and notify me (hujuice AT *[no spam, please]* inservibile DOT org, so I can substitute my dummy copy on inservibile.org witha link to this post.

Have fun flash on your 64 machines.

HUjuice

---

### Post by Kilz on 2007-09-14
> **hujuice said:**
> The today version of this very powerful script is wrong (for my bash).
A couple of "fi" has been lost.

My correction is at [http://inservibile.org/GetFlash](http://inservibile.org/GetFlash)

I didn't change an incorrect usage of sleep.

Hey Kilz, thanks a lot. :) Keep corrections and notify me (hujuice AT *[no spam, please]* inservibile DOT org, so I can substitute my dummy copy on inservibile.org witha link to this post.

Have fun flash on your 64 machines.

HUjuice

Thanks for helping. I think I copied the new script from the wrong place when I made the tarball. It was a early draft. I have replaced the script with version .8.1.

---

### Post by John.Michael.Kane on 2007-09-14
Kilz version 0-1.8.1 installed with no issues.

 I see you added user check at the end to make sure permissions are set.

---

### Post by Kilz on 2007-09-14
> **SD-Plissken said:**
> Kilz version 0-1.8.1 installed with no issues.

 I see you added user check at the end to make sure permissions are set.

Yes, This version sets the file permissions on the plugions. That was a big problem with the older version. I also consolidated the scripts for different versions of Ubuntu.

---

### Post by paradoxni on 2007-09-15
excellent work flash and now secure java, well done.. now to figure out why my flash works for most sites youtube etc. but not for a few others.

---

### Post by Kilz on 2007-09-15
> **paradoxni said:**
> excellent work flash and now secure java, well done.. now to figure out why my flash works for most sites youtube etc. but not for a few others.

The script linked in this thread only installs Flash, for one that installs flash and a secure java you will have to visit my site. The reason Flash may not work could be a lot of things. One could be the flash plugin itself, or the wrapper (which is still beta software). Aslo the site may not be setup for flash 9 as the windows version of flash is still at 8 if I remember right. The webmaster could be limiting a specific version.

---

### Post by paradoxni on 2007-09-15
ok mate thats for the info.

yea it was the script on your site i was meaning..great work, this should be a sticky!

---

### Post by master_kernel on 2007-09-15
Good job with the script! It worked the first time I used Firefox, but Flash screwed up after. While I was trying to enable Java, I must have screwed with the 32-bit libraries. Here is my new problem: [Help! Cannot install 32-bit libraries! - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3370661#post3370661")

---

### Post by ilikenwf on 2007-09-16
I use Gutsy, but prefer Swiftox. Will the Gutsy repo version of this thing install for Swiftfox too?

---

### Post by Kilz on 2007-09-16
> **ilikenwf said:**
> I use Gutsy, but prefer Swiftox. Will the Gutsy repo version of this thing install for Swiftfox too?

Im not sure. I dont run swiftfox because I prefer free software. Switfox has a non-free proprietary license that restricts redistribution. Ubuntu cant even include in in the Ubuntu repositories.
Besides which, Swiftfox doesnt have a 64bit build. All versions of Swiftfox are 32bit. Check out the information from the [Swiftfox site itself.]("http://getswiftfox.com/rel-athlon64.htm")
Build Information
 * 32-bit
[Check out Swiftweasel]("http://swiftweasel.wiki.sourceforge.net/"), its optimized, free as in freedom, and has 64bit builds.

---

### Post by ilikenwf on 2007-09-16
I don't have a problem with nonfree drivers and such, but I didn't realize that Swiftfox had gone nonfree...

Thanks for telling me about swiftweasel, I will give it a try. Between it and fasterfox, I wonder how it will do.

---

### Post by master_kernel on 2007-09-16
Kilz, please visit [http://ubuntuforums.org/showthread.php?p=3376011](http://ubuntuforums.org/showthread.php?p=3376011) and add your program to the list of the best of the Ubuntu community.

---

### Post by us3r on 2007-09-17
This script works good, however I'm having a slight problem. After about 12 hours or so, Flash stops working. If I run the script it re-downloads Flash and everything works fine again. Well it did it again today.

I ran the commands in the readme
```
ls -al /usr/lib/mozilla/plugins
ls -al /usr/lib/firefox/plugins
```

They looked normal, all the ".so" files that should be there are there.

but when Flash isn't working the last command
```
ls -al /tmp/nsplugwrapper
```

says /tmp/nspluginwrapper not found

When Flash is working
```
drwxr-xr-x  3 root root     4096 2007-09-17 10:42 .
drwxrwxrwt 15 root root     4096 2007-09-17 10:54 ..
drwxr-xr-x  2 1003 users    4096 2007-09-17 10:42 install_flash_player_9_linux
-rw-r--r--  1 root root  2608602 2007-07-05 11:48 install_flash_player_9_linux.tar.gz
-rw-r--r--  1 root root   100918 2007-08-20 22:43 nspluginwrapper_0.9.91.4_amd64.deb
```



When I go to ```
about:plugins
``` Firefox lists the two plugins correctly, in either case, working or not working.

I'm running Feisty 64-bit with all security updates loaded prior to installing Flash.

Is this just a matter of restarting nspluginwrapper if it's stopped working?

---

### Post by Kilz on 2007-09-17
> **us3r said:**
> This script works good, however I'm having a slight problem. After about 12 hours or so, Flash stops working. If I run the script it re-downloads Flash and everything works fine again. Well it did it again today.

I ran the commands in the readme
```
ls -al /usr/lib/mozilla/plugins
ls -al /usr/lib/firefox/plugins
```

They looked normal, all the ".so" files that should be there are there.

but when Flash isn't working the last command
```
ls -al /tmp/nsplugwrapper
```

says /tmp/nspluginwrapper not found

When Flash is working
```
drwxr-xr-x  3 root root     4096 2007-09-17 10:42 .
drwxrwxrwt 15 root root     4096 2007-09-17 10:54 ..
drwxr-xr-x  2 1003 users    4096 2007-09-17 10:42 install_flash_player_9_linux
-rw-r--r--  1 root root  2608602 2007-07-05 11:48 install_flash_player_9_linux.tar.gz
-rw-r--r--  1 root root   100918 2007-08-20 22:43 nspluginwrapper_0.9.91.4_amd64.deb
```



When I go to ```
about:plugins
``` Firefox lists the two plugins correctly, in either case, working or not working.

I'm running Feisty 64-bit with all security updates loaded prior to installing Flash.

Is this just a matter of restarting nspluginwrapper if it's stopped working?

I need to see the results of the commands listed in the README file. I also need the version of the script you installed, you can get that from the file you downloaded. The /tmp/nspluginwrapper and all /tmp folders normally deletes after you have restarted your computer

---

### Post by us3r on 2007-09-17
Firefox 2.0.0.6
getflash 0-1.8.1 (downloaded 9/15)

```

$ ls -al /usr/lib/mozilla/plugins
total 6904
drwxr-xr-x 2 ty   users    4096 2007-09-17 10:42 .
drwxr-xr-x 3 root root     4096 2007-04-15 04:58 ..
-r--r--r-- 1 ty   users     856 2007-06-19 17:31 flashplayer.xpt
-rwxr-xr-x 1 ty   users 7040036 2007-06-19 17:31 libflashplayer.so
lrwxrwxrwx 1 ty   users      36 2007-09-06 12:51 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 ty   users      37 2007-09-06 12:51 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 ty   users      34 2007-09-06 12:51 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 ty   users      35 2007-09-06 12:51 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 ty   users      36 2007-09-06 12:51 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 ty   users      37 2007-09-06 12:51 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 ty   users      42 2007-09-06 12:51 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 ty   users      43 2007-09-06 12:51 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 ty   users      60 2007-09-17 10:42 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

```
$ ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 root root  4096 2007-09-17 10:42 .
drwxr-xr-x 5 root root  4096 2007-09-13 17:10 ..
lrwxrwxrwx 1 root root    36 2007-09-06 12:50 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-09-06 12:50 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-09-06 12:50 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-09-06 12:50 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-09-06 12:50 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-09-06 12:50 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-09-06 12:50 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-09-06 12:50 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2007-07-31 06:29 libunixprintplugin.so
lrwxrwxrwx 1 root root    60 2007-09-17 10:42 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

```
$ ls -al /tmp/nsplugwrapper
total 2668
drwxr-xr-x  3 root root     4096 2007-09-17 10:42 .
drwxrwxrwt 15 root root     4096 2007-09-17 10:54 ..
drwxr-xr-x  2 1003 users    4096 2007-09-17 10:42 install_flash_player_9_linux
-rw-r--r--  1 root root  2608602 2007-07-05 11:48 install_flash_player_9_linux.tar.gz
-rw-r--r--  1 root root   100918 2007-08-20 22:43 nspluginwrapper_0.9.91.4_amd64.deb
```

---

### Post by Kilz on 2007-09-17
Thank you. But as you said in a previous post, everything seems to look correct. 
What I would like to see is what the results of the commands look like when flash stops working. You might also try starting Firefox in a terminal and see if it gives you any errors. 
I think it would be more helpful diagnosing a broken setup than one thats working because the script was reran.

---

### Post by us3r on 2007-09-17
Okay I started Firefox from the terminal and Flash is working again. Flash also works from the menu launcher as well.

I'm thinking this is just a bug in Firefox or nspluginwrapper. 

Thanks again for the script, I was thinking about installing 32-bit Ubuntu just to use Flash until I found this thread.

---

### Post by Tanker Bob on 2007-09-18
I find that script stops working after a while as well. That's been true for quite a while, long before the script appeared. I simply restart Firefox and it works again. Not sure where the bug is.

---

### Post by toga34 on 2007-09-18
worked like a charm... thank you.

ubuntu 7.04
amd 64

---

### Post by waddletron on 2007-09-18
I installed Feisty Fawn a few months ago and then found your script (which had helped me when I had Dapper and I installed, everything worked great.

Then I ran into a few sound problems so I compiled and installed ALSA. Well that is when the sound in flash stopped working. 

I have aoss and I have even tried reinstalling it and that did not fix anything. 

I have tried reinstalling your script several times, I even went back to the version of ALSA in the repository. Nothing fixed my problem.

Can I get a hand?

---

### Post by Kilz on 2007-09-19
> **waddletron said:**
> I installed Feisty Fawn a few months ago and then found your script (which had helped me when I had Dapper and I installed, everything worked great.

Then I ran into a few sound problems so I compiled and installed ALSA. Well that is when the sound in flash stopped working. 

I have aoss and I have even tried reinstalling it and that did not fix anything. 

I have tried reinstalling your script several times, I even went back to the version of ALSA in the repository. Nothing fixed my problem.

Can I get a hand?

I would love to but most of what I would suggest you try, you have in your post told me has been done. Perhaps starting firefox in a terminal and then going to a flash site will provide an error in the terminal.
You could also try deleting the ```
~/.macromedia
``` folder in your home folder to see if there is a bad setting. It will be created the next time you use flash.
Im also not sure if the aoss you installed is the 64bit one or if you installed the alsa/oss file under sound in the howto.

---

### Post by dnns123 on 2007-09-20
Thank you! I love the simplicity of your program! :KS:KS:KS

---

### Post by Capone on 2007-09-21
worked like a charm, as long as there's a community like this, windows will be kept out of my 4 computers.

---

### Post by lensteruk on 2007-09-23
Thanks for this, saved what is left of my hair. One observation however, all stopped working on my Feisty Fawn setup, i think it was when i installed brutal chess >?? anyone got an idea why. Do i just re run the scripts to re install ??

---

### Post by paradoxni on 2007-09-23
With the number of people coming to this 64bit section and asking about flash and java, is it not time this post got made a sticky! :) :)

---

### Post by John.Michael.Kane on 2007-09-23
> **paradoxni said:**
> With the number of people coming to this 64bit section and asking about flash and java, is it not time this post got made a sticky! :) :)

There is a 64bit install guide list sticky. [Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607") Not only does it include install methods it includes info to help users decide if they are ready to run 64bit.

When gutsy is released the sticky will be updated to reflect any changes.

---

### Post by paradoxni on 2007-09-23
Well I guess if I had bothered to read that guide I would have known! :) I will make sure and point anyone in that direction.

Thanks.

---

### Post by davidmb on 2007-09-24
At last! It worked like a charm! :D

As far as I could see, my Feisty Fawn refused to install the latest [nspluginwrapper_0.9.91.4-3ubuntu2_amd64.deb]("http://archive.ubuntu.com/ubuntu/pool/multiverse/n/nspluginwrapper/nspluginwrapper_0.9.91.4-3ubuntu2_amd64.deb") because of some unresolved dependencies ???
But of course, your script is pointing to the right version.

This script should be part of the main distribution, or maybe it should be easier to grab the plugin wrapper from the Application Installer.

Anyway, a big THANK YOU VERY MUCH.

---

### Post by garrudao on 2007-09-25
CONGRATULATIONS....

this script resolve my problem...

---

### Post by Kilz on 2007-09-25
> **davidmb said:**
> At last! It worked like a charm! :D

As far as I could see, my Feisty Fawn refused to install the latest [nspluginwrapper_0.9.91.4-3ubuntu2_amd64.deb]("http://archive.ubuntu.com/ubuntu/pool/multiverse/n/nspluginwrapper/nspluginwrapper_0.9.91.4-3ubuntu2_amd64.deb") because of some unresolved dependencies ???
But of course, your script is pointing to the right version.

This script should be part of the main distribution, or maybe it should be easier to grab the plugin wrapper from the Application Installer.

Anyway, a big THANK YOU VERY MUCH.

That package is only available in Gutsy. If you are running Gutsy everything should work when you try to install nspluginwrapper. It should be all automatic, no script needed. If you are running Gutsy you need to [report this bug on launchpad]("https://bugs.launchpad.net/ubuntu") so it can be fixed.
This is what the big colorful words on the first post that you may have overlooked say.

---

### Post by dlsmith on 2007-09-25
Thank you very much. The script Got'R done.

---

### Post by thenewrhapsody on 2007-09-26
Worked like a charm, now I won't have to use multiple browsers. Thanks.

---

### Post by Bubs on 2007-09-30
doesn't work for me.

I only tested pandora.com and it crashes Firefox and swifweasal every time.  I haven't tried any other sites since that the only flash site I visit now a days.  I know it works in my 32bit browser.

I guess I get to keep crying on how 64bit linux doesn't have flash support....  Waaa...  WAAAAAA!  :cry:

j/k  I'm not mad.  at least it works in flock (i know flock kinda blows but I installed it so I can tell the difference between my 32 and 64bit browsers)  and now I just open up flock and its like a radio

---

### Post by Kilz on 2007-09-30
> **Bubs said:**
> doesn't work for me.

I only tested pandora.com and it crashes Firefox and swifweasal every time.  I haven't tried any other sites since that the only flash site I visit now a days.  I know it works in my 32bit browser.

I guess I get to keep crying on how 64bit linux doesn't have flash support....  Waaa...  WAAAAAA!  :cry:

j/k  I'm not mad.  at least it works in flock (i know flock kinda blows but I installed it so I can tell the difference between my 32 and 64bit browsers)  and now I just open up flock and its like a radio

Something isnt right I can play pandora in Firefox. What version of Ubuntu are you running?

---

### Post by jdemesse on 2007-09-30
> **jusmurph said:**
> This fixed my issue:

```
 Originally Posted by Gabriel Pastor
I had the same problem with feisty and solved it.
I have 2 sound cards, and it seems that sometimes the wrong sound card is the default sound device.

$ sudo asoundconf list
Names of available sound cards:
Intel
CA0106

The first one is integrated on the motherboard, and the second one (an audigy) is the one I use.

To solve the problem, I just set the default sound card to the audigy:
$ sudo asoundconf set-default-card CA0106

Then the sound works !
Hope it helps.
```

This worked perfectly for me. I have an Intel onboard sound card and a USB headset. To hear flash sound on my headset I had to do:

$ sudo asoundconf-set-default-card Headset

---

### Post by Bubs on 2007-09-30
@Kilz

I'm using feisty.  and I followed the instructions on your script.   pretty easy unpack run in terminal follow on screen instructions  :)

downloaded swiftweasel and java and flash plugin  then opened up swift and went to pandora.  froze  had to force quit the browser.  both swift and firefox

oh and all the browsers were closed when I ran the script too.

---

### Post by Bubs on 2007-09-30
I just noticed now (right click) that firefox still has gnash as the default flashplayer...

how would I change that to what you installed?

---

### Post by Kilz on 2007-09-30
> **Bubs said:**
> I just noticed now (right click) that firefox still has gnash as the default flashplayer...

how would I change that to what you installed?

You might try to uninstall gnash. Deleting its plugin should do it, wherever its installed.

---

### Post by Bubs on 2007-09-30
cool.

I deleted gnash and ran your script again.

it works. :)  your the coolest!  no more crying for this kid!  No sir-e I've got flash and pandora working.  ****.  I can get rid of flock.  no need for it now is there?

ha  cool

Thanks for the script and help

---

### Post by napster2500 on 2007-10-04
hi! i'm running kubuntu 64bit, and i get an error when i try to open the script 'get flash' with konsole...

```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KProcess): WARNING: _attachPty() 11
```

any idea?

---

### Post by Thug life on 2007-10-04
Thanks for this, much easier than other guides i have seen :)

---

### Post by Kilz on 2007-10-04
> **napster2500 said:**
> hi! i'm running kubuntu 64bit, and i get an error when i try to open the script 'get flash' with konsole...

```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KProcess): WARNING: _attachPty() 11
```

any idea?

What version of Ubuntu are you using, Feisty or Gutsy? Also , would you please copy and paste everything from the first command, not just the error code.

---

### Post by JohnMcleod on 2007-10-04
Thanks Kilz, your script worked like a charm

---

### Post by achinb on 2007-10-04
Hi,
First time i installed ubuntu feisty and get the following error when installing this script:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 but it is not going to be installed
  ia32-libs-sdl: Depends: lib32gcc1 but it is not going to be installed
                 Depends: lib32z1 but it is not going to be installed
  lib32asound2: Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not going to be installed
E: Broken packages
--11:00:03--  [http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.4_amd64.deb](http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.4_amd64.deb)
           => `nspluginwrapper_0.9.91.4_amd64.deb'
Resolving home.comcast.net... 204.127.198.24
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100,918 (99K) [text/plain]

50% [=================>                   ] 100,918      175.14K/s             

11:00:04 (174.93 KB/s) - `nspluginwrapper_0.9.91.4_amd64.deb' saved [100918/100918]

Selecting previously deselected package nspluginwrapper.
(Reading database ... 113904 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.4_amd64.deb) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on lib32gcc1 (>= 1:4.1.2); however:
  Package lib32gcc1 is not installed.
 nspluginwrapper depends on libc6-i386 (>= 2.5-0ubuntu1); however:
  Package libc6-i386 is not installed.
 nspluginwrapper depends on ia32-libs; however:
  Package ia32-libs is not installed.
 nspluginwrapper depends on ia32-libs-sdl; however:
  Package ia32-libs-sdl is not installed.
 nspluginwrapper depends on ia32-libs-gtk; however:
  Package ia32-libs-gtk is not installed.
 nspluginwrapper depends on lib32asound2; however:
  Package lib32asound2 is not installed.
 nspluginwrapper depends on gsfonts-x11; however:
  Package gsfonts-x11 is not installed.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
--11:00:05--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.130.70
Connecting to fpdownload.macromedia.com|72.247.130.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

50% [=================>                   ] 2,608,602    512.30K/s    ETA 00:05

11:00:10 (472.22 KB/s) - `install_flash_player_9_linux.tar.gz' saved [2608602/2608602]

install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer.xpt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
Cannot execute /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

any help would be appreciated, thanks

---

### Post by ur23 on 2007-10-04
So after it gets to the part where you have to type your username in is it meant to close suddenly??

Im a very new user to ubuntu, as my post count tells you. but what i dont understand about it, is why it has to make even the simplest of tasks that; dare i say it... a "Windows" machine can handle with ease so bloody hard :? :|

anyone have an answer? :D

...o and if u hadn't of guessed...my flash still doesnt work.

regards,ur23

---

### Post by John.Michael.Kane on 2007-10-04
> **ur23 said:**
> So after it gets to the part where you have to type your username in is it meant to close suddenly??
Yes.  After verifying your name the script would exit. This is normal.

> **ur23 said:**
> Im a very new user to ubuntu, as my post count tells you. but what i dont understand about it, is why it has to make even the simplest of tasks that; dare i say it... a "Windows" machine can handle with ease so bloody hard :? :|
Any OS takes getting use to even windows. With that said. Installing flash, As well as most other items under Linux is not hard at all,however. The install method is done differently then what you are use too.

I'm pretty sure if you have further issues beyond the one you are currently having the forum members will be glad to point you in the right direction.

> **ur23 said:**
> anyone have an answer? :D
I offered my opinion hope it helped some.

> **ur23 said:**
> ...o and if u hadn't of guessed...my flash still doesnt work.

regards,ur23

As for your flash not working.

Please list the output of that is given by each command listed below, As this will help the script writer, and those who help with testing it to help you.
 
Copy paste them into a terminal one at a time

```
ls -al /usr/lib/mozilla/plugins
```

and 

```
ls -al /usr/lib/firefox/plugins
```

and 

```
ls -al /tmp/nsplugwrapper
```

Also please list the version of file you downloaded, As theres two versions
Version 1 nspluginwrapper-install-0-1.8.1
Version 2 GetPlugins-.7

Also list what flavor you are running (Ubuntu/Kubuntu/Xubuntu) and the version.

---

### Post by Kilz on 2007-10-04
> **achinb said:**
> Hi,
First time i installed ubuntu feisty and get the following error when installing this script:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 but it is not going to be installed
  ia32-libs-sdl: Depends: lib32gcc1 but it is not going to be installed
                 Depends: lib32z1 but it is not going to be installed
  lib32asound2: Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not going to be installed
E: Broken packages
--11:00:03--  [http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.4_amd64.deb](http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.4_amd64.deb)
           => `nspluginwrapper_0.9.91.4_amd64.deb'
Resolving home.comcast.net... 204.127.198.24
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100,918 (99K) [text/plain]

50% [=================>                   ] 100,918      175.14K/s             

11:00:04 (174.93 KB/s) - `nspluginwrapper_0.9.91.4_amd64.deb' saved [100918/100918]


What version of Ubuntu are you running?

---

### Post by achinb on 2007-10-04
> **Kilz said:**
> What version of Ubuntu are you running?

Ubuntu Feisty

---

### Post by Kilz on 2007-10-04
> **achinb said:**
> Ubuntu Feisty

Please open up synaptic, do a search for lib32gcc1 and tell me what version is installed or available. Secondly, did you install Feisty clean from a cd or was it an upgrade from a previous version?

---

### Post by crawdaddyangry on 2007-10-05
well done sir ......resolved the issue on my AMD 64 7.04 installation........

---

### Post by overlord.gaurav on 2007-10-06
Though I'm too late but I don't mind thanking Killz for the script. :)
Good work mate!

---

### Post by eg0n on 2007-10-07
This is perfect. Not having flash player was one major problem. Thanx a lot!!!!
=D>=D>=D>=D>

---

### Post by achinb on 2007-10-07
> **Kilz said:**
> Please open up synaptic, do a search for lib32gcc1 and tell me what version is installed or available. Secondly, did you install Feisty clean from a cd or was it an upgrade from a previous version?

I do not have lib32gcc1 installed but the version available is 1:4.1.2-oubuntu4.  when i try to install it, it says:

"lib32gcc1:
 Depends: libc6-i386 but it is not going to be installed"

then, when i try to install  libc6-i386, it says:

"libc6-i386:
  Depends: libc6 (=2.5-0ubuntu14) but 2.6.1-5 is to be installed"

i have version 2.6.1-5 of libc6 installed.

I performed a clean install of Feisty from a dvd. 

Thank you

---

### Post by Kilz on 2007-10-07
> **achinb said:**
> I do not have lib32gcc1 installed but the version available is 1:4.1.2-oubuntu4.  when i try to install it, it says:

"lib32gcc1:
 Depends: libc6-i386 but it is not going to be installed"

then, when i try to install  libc6-i386, it says:

"libc6-i386:
  Depends: libc6 (=2.5-0ubuntu14) but 2.6.1-5 is to be installed"

**i have version 2.6.1-5 of libc6 installed.**

I performed a clean install of Feisty from a dvd. 

Thank you

Ok, here is the thing. You say you have Feisty installed. But the version of libc6-i386 is from Gutsy
libc6-i386 versions are as follows

[2.5-0ubuntu14]("http://packages.ubuntu.com/feisty/base/libc6-i386") = Feisty
[2.6.1-5]("http://packages.ubuntu.com/gutsy/base/libc6-i386") = Gutsy

Have you installed or tried to install Gutsy? Have you installed a Gutsy Kernal?

---

### Post by achinb on 2007-10-07
> **Kilz said:**
> Ok, here is the thing. You say you have Feisty installed. But the version of libc6-i386 is from Gutsy
libc6-i386 versions are as follows

[2.5-0ubuntu14]("http://packages.ubuntu.com/feisty/base/libc6-i386") = Feisty
[2.6.1-5]("http://packages.ubuntu.com/gutsy/base/libc6-i386") = Gutsy

Have you installed or tried to install Gutsy? Have you installed a Gutsy Kernal?

Hmm, I never tried to install Gutsy or the Gutsy kernel.  Is it possible to revert to 2.5-0?

---

### Post by Kilz on 2007-10-07
> **achinb said:**
> Hmm, I never tried to install Gutsy or the Gutsy kernel.  Is it possible to revert to 2.5-0?

If in synaptic, highlight the pachage, click package, then force version. A box will come up with versions avilable. If force version is greyed out no other versions are available . 
But if you have a gutsy package perhaps other gutsy packages are available, like the nspluginwrapper package that is in gutsy

---

### Post by riknos on 2007-10-10
Hi,

Thanks very much for the script and instructions Kilz. Have now got Flash working in Firefox and Swiftweasel! However I have no sound. Have checked <System> <Preferences><Sound> and <Test> output is loud and clear through my speakers. Just nothing from Flash in the browsers. 

For info, looked at ALSAmixer gui via speaker icon on desktop and set Preference to device HDA NVidia but calling up alsamixer from command line shows VOIP USB phone device only.

Any help would be much appreciated.

Richard.

---

### Post by The Populist on 2007-10-11
Thanks alot for this thread. It works like a charm.

...

---

### Post by Kilz on 2007-10-11
> **riknos said:**
> Hi,

Thanks very much for the script and instructions Kilz. Have now got Flash working in Firefox and Swiftweasel! However I have no sound. Have checked <System> <Preferences><Sound> and <Test> output is loud and clear through my speakers. Just nothing from Flash in the browsers. 

For info, looked at ALSAmixer gui via speaker icon on desktop and set Preference to device HDA NVidia but calling up alsamixer from command line shows VOIP USB phone device only.

Any help would be much appreciated.

Richard.

Have you tried the fix for sound on the first post?

---

### Post by junnuh on 2007-10-11
Hello Kilz!

I have an question of this install! I have installed firefox32 by the help of your great script and it' s working great.

I was looking help how to update Flash to it's newest version: And I found this. Great but can I do it to Firefox64 without disturbing the function of firefox32? I mean the flash and java install.

You are doing great job:)

with warm regards junnuh:guitar:

---

### Post by Kilz on 2007-10-11
> **junnuh said:**
> Hello Kilz!

I have an question of this install! I have installed firefox32 by the help of your great script and it' s working great.

I was looking help how to update Flash to it's newest version: And I found this. Great but can I do it to Firefox64 without disturbing the function of firefox32? I mean the flash and java install.

You are doing great job:)

with warm regards junnuh:guitar:

Yes you can install this script and it will not effect the firefox32 install. I made sure its ok because there is still some problems running java on the 64bit browser. So the ability to have both was important.
But if you want to upgrade the flash on the 32bit install, just run that script again. It will download , and install the newest flash for that setup.

---

### Post by junnuh on 2007-10-11
Hello again Kilz!

i updated Firefox32 and Flash, thank you for your help.

But about the flash and java plugin to firefox64. The script of yours seem to install Swiftweasel64. How about Firefox64? Or is there someting I don't understand.:popcorn:

I also registered to THGC, if you wan't I  can move this conversation there!

I don't have anything against a new browser but I am used to Firefox. So if i install Swiftweasel to my Ubuntu it will be richness. I never used it but...:)

thank you for your help. You are a peace GOLD for amd64 users. And my son loves because he is able to play games in internet. I don't have Windows:guitar:

with love junnuh

---

### Post by Kilz on 2007-10-11
> **junnuh said:**
> Hello again Kilz!

i updated Firefox32 and Flash, thank you for your help.

But about the flash and java plugin to firefox64. The script of yours seem to install Swiftweasel64. How about Firefox64? Or is there someting I don't understand.:popcorn:

I also registered to THGC, if you wan't I  can move this conversation there!

I don't have anything against a new browser but I am used to Firefox. So if i install Swiftweasel to my Ubuntu it will be richness. I never used it but...:)

thank you for your help. You are a peace GOLD for amd64 users. And my son loves because he is able to play games in internet. I don't have Windows:guitar:

with love junnuh

I dont support that script here. But I will tell you the reason it installs swiftweasel is that the java plugin it uses crashes plain old firefox, so it isnt even installed into firefiox64.

---

### Post by betweenthetines on 2007-10-11
Thank you for your work in making this script Kilz! It worked great for me (using my already installed Swiftweasel 64bit). Thanks!

---

### Post by lonrot on 2007-10-12
Yo Kilz, is there any chance to make this lib to work with the current Opera 9.50 Alpha x64, I've installed the script but it only works with Firefox.

---

### Post by Kilz on 2007-10-12
> **lonrot said:**
> Yo Kilz, is there any chance to make this lib to work with the current Opera 9.50 Alpha x64, I've installed the script but it only works with Firefox.

Im not sure what could be done with opera. Can opera use mozilla plugins?

---

### Post by luckytwo999 on 2007-10-13
I want to know how to install flash  plugins on ubuntu 7,04 64 bytes   . my cpu is amd 3600+;:lolflag:

---

### Post by misfitpierce on 2007-10-13
Ubuntu 7.10 auto installs flash in firefox even on 64 bit... :) Thought id let everyone know for even more reason to upgrade. :)

---

### Post by Kilz on 2007-10-13
> **misfitpierce said:**
> Ubuntu 7.10 auto installs flash in firefox even on 64 bit... :) Thought id let everyone know for even more reason to upgrade. :)

Ya, because those big bold colored words on the first post might be missed. But everyone is sure to see a post 39 pages back.

---

### Post by Tom Trommelaar on 2007-10-14
Hey Kilz, nice job on the script. It was a painless install of Flash in my 64 bit firefox browser. But... I recently upgraded to Gutsy Gibbon and now my browser just crashes when any flash is inside the page. I think it has something to do with the fact that Gutsy comes with its own flash player installed in firefox.

Do you have any idea how to fix this?

---

### Post by Kilz on 2007-10-14
> **Tom Trommelaar said:**
> Hey Kilz, nice job on the script. It was a painless install of Flash in my 64 bit firefox browser. But... I recently upgraded to Gutsy Gibbon and now my browser just crashes when any flash is inside the page. I think it has something to do with the fact that Gutsy comes with its own flash player installed in firefox.

Do you have any idea how to fix this?

Uninstall the nspluginwrapper package.
```
sudo apt-get remove nspluginwrapper

```
Then install flash
```
sudo apt-get install flashplugin-nonfree.
```

Please file a bug [report on launchpad]("https://bugs.launchpad.net/ubuntu") so this can be fixed.It is a problem that is going to effect a lot of people as they upgrade if the developers are not made aware of it. [Please use lanuchpad]("https://bugs.launchpad.net/ubuntu") as thats the only way we can be sure they will get the report.

---

### Post by Tom Trommelaar on 2007-10-14
Thanks! That did the trick :)

---

### Post by Slurm on 2007-10-16
Hey,

I just wanted to add thanks for this script.  It works great.  I noticed that it also added a bunch of ttf to my system.  Can you tell me why?


Slurm

---

### Post by FredB on 2007-10-16
It is not really useful to remove nspluginwrapper as it is needed by flashplugin-nonfree package.

---

### Post by Kilz on 2007-10-16
> **Slurm said:**
> Hey,

I just wanted to add thanks for this script.  It works great.  I noticed that it also added a bunch of ttf to my system.  Can you tell me why?


Slurm

I think they are used by the flash plugin. You can uninstall the gsfonts-x11 if you want to see if it effects anything.

> **FredB said:**
> It is not really useful to remove nspluginwrapper as it is needed by flashplugin-nonfree package.
Those that upgrade to Gutsy with my script installed may need to remove the nspluginwrapper package the script installs. By installing flash-nonfree it reinstalls nspluginwrapper with the Gutsy package.

---

### Post by FredB on 2007-10-16
Ok. I said nothing. Please forgive me :p

---

### Post by Footer on 2007-10-16
> **Kilz said:**
> Uninstall the nspluginwrapper package.
```
sudo apt-get remove nspluginwrapper

```
Then install flash
```
sudo apt-get install flash-nonfree.
```

Please file a bug [report on launchpad]("https://bugs.launchpad.net/ubuntu") so this can be fixed.It is a problem that is going to effect a lot of people as they upgrade if the developers are not made aware of it. [Please use lanuchpad]("https://bugs.launchpad.net/ubuntu") as thats the only way we can be sure they will get the report.

I'm running Gutsy 64bit.  Unfortunately, flash-nonfree was not in the repositories.  However, flashplugin-nonfree was.  I removed nspluginwrapper as instructed, installed flashplugin-nonfree but flash still isn't working for me.

Any suggestions?

Thanks!

EDIT (1):  Never mind!  I restarted the xserver and all seems to be well now!

EDIT (2):  I take it back, still not working.  Flash items appear to load and then seconds later they just stop and I'm left with a white block/space where the flash item is supposed to appear.  Any ideas???  I've restarted Firefox several times and it behaves exactly the same way every time.

---

### Post by Kilz on 2007-10-16
I would like to see someone tell me that they have reported this problem. We cant expect everyone who upgrades to find this thread. The developers need to be aware of this so it gets fixed. Simply posting in the forums will not do it, [you must report it on launchpad]("https://bugs.launchpad.net/ubuntu/+filebug"), the ubuntu development site.
Also , not just one person, but everyone with the problem, the more people the greater the need to make the package work when you update the system.

---

### Post by John.Michael.Kane on 2007-10-16
@Footer you can try clearing firefox's cache, and restart the browser.

@Killz Wouldn't the user have to not only remove nspluginwrapper but also the flash version your script installed since it's not an Ubuntu labeled version. Reason I asked this is that it seems like the two flash versions are fighting for rights to run, Though I could be wrong.

---

### Post by Kilz on 2007-10-16
> **SD-Plissken said:**
> @Footer you can try clearing firefox's cache, and restart the browser.

@Killz Wouldn't the user have to not only remove nspluginwrapper but also the flash version your script installed since it's not an Ubuntu labeled version. Reason I asked this is that it seems like the two flash versions are fighting for rights to run, Though I could be wrong.

Im not 100% positive of this, but what I think is going on is a problem with the wrapper.
The flash plugin is the same file. Its the wrapper that is different. By removing the nspluginwrapper package and reinstalling flash (that installs the new wrapper package by default) a new wrapped plugin is created overwriting the old one

One way we could find out if it is a conflict is if someone would run this command before preforming the steps above so we could find out if there are multiple plugins. then copying the results to a post.

```
ls -al /usr/lib/mozilla/plugins /usr/lib/firefox/plugins
```

---

### Post by Footer on 2007-10-16
> **Kilz said:**
> Im not 100% positive of this, but what I think is going on is a problem with the wrapper.
The flash plugin is the same file. Its the wrapper that is different. By removing the nspluginwrapper package and reinstalling flash (that installs the new wrapper package by default) a new wrapped plugin is created overwriting the old one

One way we could find out if it is a conflict is if someone would run this command before preforming the steps above so we could find out if there are multiple plugins. then copying the results to a post.

```
ls -al /usr/lib/mozilla/plugins /usr/lib/firefox/plugins
```

I tried clearing the cache and restarting the browser but I still get white boxes where the Flash should be.  It starts to load and I believe right when it finishes, it dies and leaves the white boxes.  Here's the command above with the mess I've got:

```

footer@kubuntu64:/etc/apt$ ls -al /usr/lib/mozilla/plugins /usr/lib/firefox/plugins
/usr/lib/firefox/plugins:
total 24
drwxr-xr-x 2 footer  users  4096 2007-10-16 09:10 .
drwxr-xr-x 5 root    root   4096 2007-10-13 06:58 ..
lrwxrwxrwx 1 root    root     37 2007-10-16 09:10 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
-rw-r--r-- 1 root    root  11456 2007-10-08 10:34 libunixprintplugin.so
lrwxrwxrwx 1 root    root     60 2007-10-13 08:17 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

/usr/lib/mozilla/plugins:
total 7048
drwxr-xr-x 2 footer  users    4096 2007-10-16 09:10 .
drwxr-xr-x 3 root    root     4096 2007-02-04 06:12 ..
-r-xr-xr-x 1 footer  users   19726 2006-12-15 15:51 flashplayer-installer
-r--r--r-- 1 footer  users     856 2007-06-19 19:31 flashplayer.xpt
lrwxrwxrwx 1 root    root       37 2007-10-16 09:10 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rwxr-xr-x 1 footer  users 7040036 2007-06-19 19:31 libflashplayer.so
-rw-r--r-- 1 footer  users   65692 2007-08-30 17:50 libswfdecmozilla.a
-rw-r--r-- 1 footer  users    1308 2007-08-30 17:50 libswfdecmozilla.la
-rw-r--r-- 1 footer  users   45320 2007-08-30 17:50 libswfdecmozilla.so
lrwxrwxrwx 1 footer  users      60 2007-10-14 06:21 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so


```

Thanks!

EDIT:  Added jpg of site showing the white blocks where flash items should be.

---

### Post by Footer on 2007-10-16
> **Kilz said:**
> I would like to see someone tell me that they have reported this problem. We cant expect everyone who upgrades to find this thread. The developers need to be aware of this so it gets fixed. Simply posting in the forums will not do it, [you must report it on launchpad]("https://bugs.launchpad.net/ubuntu/+filebug"), the ubuntu development site.
Also , not just one person, but everyone with the problem, the more people the greater the need to make the package work when you update the system.

You mean like this:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/151805](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/151805)

:)

---

### Post by Kilz on 2007-10-16
> **Footer said:**
> I tried clearing the cache and restarting the browser but I still get white boxes where the Flash should be.  It starts to load and I believe right when it finishes, it dies and leaves the white boxes.  Here's the command above with the mess I've got:


/usr/lib/mozilla/plugins:
-r-xr-xr-x 1 footer  users   19726 2006-12-15 15:51 flashplayer-installer
-r--r--r-- 1 footer  users     856 2007-06-19 19:31 flashplayer.xpt
lrwxrwxrwx 1 root    root       37 2007-10-16 09:10 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

[/code]

Thanks!

EDIT:  Added jpg of site showing the white blocks where flash items should be.

I would think that it has to do with these files. But since its on Gutsy, Im not 100% positive. It looks like you have some alternate flash plugin installed. In any event the files installed by the script appear to be gone. 
You might want to remove any plugin with flash and simply reinstall flashplugin-nonfree.

---

### Post by Footer on 2007-10-17
OK, I just tried starting Firefox from the command line.  Here's an output of the errors:

```

footer@kubuntu64:~$ firefox
LoadPlugin: failed to initialize shared library /home/footer/.mozilla/plugins/nprhapengine.so [/home/footer/.mozilla/plugins/nprhapengine.so: wrong ELF class: ELFCLASS32]
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
*** NSPlugin Wrapper *** ERROR: NPP_Write() invoke: Connection reset by peer
*** NSPlugin Wrapper *** ERROR: NPP_DestroyStream() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_NewStream() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_NewStream() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_New() invoke: Connection closed
LoadPlugin: failed to initialize shared library /home/footer/.mozilla/plugins/nprhapengine.so [/home/footer/.mozilla/plugins/nprhapengine.so: wrong ELF class: ELFCLASS32]
*** NSPlugin Wrapper *** ERROR: NPP_New() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_NewStream() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_New() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_New() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed

```

If this is a 'bug', I'd be more than happy to file a bug report.  But if it's a config problem on my end, I'd rather try to fix it but I don't think I'm smart enough based on the output above.

Any suggestions would be greatly appreciated!

Thanks!

---

### Post by Kilz on 2007-10-17
> **Footer said:**
> OK, I just tried starting Firefox from the command line.  Here's an output of the errors:

[code]
footer@kubuntu64:~$ firefox
LoadPlugin: failed to initialize shared library /home/footer/.mozilla/plugins/nprhapengine.so [/home/footer/.mozilla/plugins/nprhapengine.so: wrong ELF class: 

If this is a 'bug', I'd be more than happy to file a bug report.  But if it's a config problem on my end, I'd rather try to fix it but I don't think I'm smart enough based on the output above.

Any suggestions would be greatly appreciated!

Thanks!

Did you try what I suggested in post 405? You might also want to remove the plugin files in /home/footer/.mozilla/plugins/. What it looks like to me is that you have tried multiple ways of installing flash, these are conflicting.

---

### Post by factor on 2007-10-17
hi, the flashplugin alternative file is the one installed with the flashplugin-nonfree package. I know because i removed package and it disappeared, and i reinstalled it and it reappeared.

I tried to start firefox in safe-mode, via terminal: firefox -safe-mode

and it worked. Then i did the same and i checked the "disable all addons", and when i started firefox next time it worked flawlessly, with all extensions and themes disabled of course. I'm slowly reenabling extensions, but what i think it's that *maybe* is the ubufox extension, because is the only new extension i have since it crashes. Could be an update of the existing one tho.

Can everyone test and post a list of safe extensions?

For me so far is:

del.icio.us extension.
kempelton pe theme
spanish language pack.

These work flawlessly. No other extension enabled so far.

Regards.

---

### Post by factor on 2007-10-18
more weird: i rebooted computer today, and firefox wasn't working. same segmentation fault error. 

I launched terminal: firefox -safe-mode

I didn't change any option, i clicked "continue in safe mode"

I closed firefox.

From terminal: firefox 

Firefox starts normally, with extensions enabled.

I don't know what happens but this is the workaround to make it work. I will post this in launchpad bug mentioned before. I hope it will help to fix it ASAP.

---

### Post by factor on 2007-10-18
ah, i think my bug it's a different one because i only get "Segmentation fault (core dumped" error and nothing else. If anyone else has the same problem, please post it here: 

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/152732](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/152732)

---

### Post by factor on 2007-10-18
I posted also a bug for opera 9.5 64 bits crashing when showing flash pages here. please post in this url if you have same problem: [https://bugs.launchpad.net/ubuntu/+source/opera/+bug/153848](https://bugs.launchpad.net/ubuntu/+source/opera/+bug/153848)

---

### Post by vinmar on 2007-10-19
After trying everything in this thread with no luck, I thought I'd share how I fixed Flash hanging in 64-bit firefox.

1) Uninstall flashplugin-nonfree if installed through synaptic.
2) Get a list of any Flash remains with nspluginwrapper -l
3) For me this showed a combination of 0.91.94 and 0.91.95 versions. I manually deleted every file listed.
4) Run nspluginwrapper -l again and confirm no files listed.
5) Then I installed flashplugin-nonfree again through synaptic.

---

### Post by Footer on 2007-10-20
I've been struggling with this flash not working in 64bit firefox for about forever.  I followed your steps exactly vinmar and after reopening firefox, flash worked.  However, I'm back to my same old problem after restarting X (see my post #403 for a screenshot).

Here are more details:

```

footer@kubuntu64:/usr/bin$ nspluginwrapper -l
/usr/lib/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5

```

```

footer@kubuntu64:/usr/bin$ ls -al /usr/lib/mozilla/plugins /usr/lib/firefox/plugins
/usr/lib/firefox/plugins:
total 20
drwxr-xr-x 2 root root  4096 2007-10-20 06:03 .
drwxr-xr-x 5 root root  4096 2007-10-19 06:07 ..
lrwxrwxrwx 1 root root    37 2007-10-20 06:03 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
-rw-r--r-- 1 root root 11456 2007-10-08 10:34 libunixprintplugin.so

/usr/lib/mozilla/plugins:
total 8
drwxr-xr-x 2 root root 4096 2007-10-20 06:03 .
drwxr-xr-x 3 root root 4096 2007-10-20 06:03 ..
lrwxrwxrwx 1 root root   37 2007-10-20 06:03 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

```

```
footer@kubuntu64:~/.mozilla/plugins$ ll
total 2724
-rw-r--r-- 1 footer footer 2788848 2006-03-29 00:49 nprhapengine.so.bak

```

```
footer@kubuntu64:~/.mozilla/firefox$ more pluginreg.dat
Generated File. Do not edit.

[HEADER]
Version:0.08:$

[PLUGINS]
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so:$
:$
1192878226000:1:7:$
Shockwave Flash 9.0 r48:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
/home/footer/.mozilla/plugins/npwrapper.libflashplayer.so:$
:$
1185803187000:1:13:$
Shockwave Flash 9.0 r48:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

```

By the way, I've done a clean install of 7.10 as well (except my ~home which is on it's own partition).

Any help would be GREATLY appreciated!

Thanks.

PS.  vinmar:  are you vwingate over on Launchpad?  If so, I saw your note here:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/151805](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/151805)

I'll file the information above there as well!  Thanks!

---

### Post by vinmar on 2007-10-20
> **Footer said:**
> PS.  vinmar:  are you vwingate over on Launchpad?

Yes, that's me!

Sorry it didn't work for you. I used to get exactly that problem, where it looks like it's fixed, then when firefox is closed down and reopened flash is broken again.

Do you have any other plugins that are wrapped? I think I saw that you have shockwave installed, which I don't.

---

### Post by Footer on 2007-10-20
What a weird problem this is!  I had a couple of add-ons that weren't supported under FF 2.0 (haven't looked at that in awhile!) which I just removed and restarted FF.  Now flash is working again!  Maybe it was related to the add-ons?

And you're right, I do have shockwave installed the way it appears.  I'd rip it out if I knew how.  There doesn't seem to be a 'plug-in' manager that I can find ... It's not the same as add-ons I don't think.

:confused:

EDIT:  Spoke too soon!!!  Restarted firefox and I'm back to the white boxes where flash should be ...  :(

---

### Post by wawarren on 2007-10-28
I can't get this to work on Ubuntu 7.04 Fiesty Fawn 64

ls -al /usr/lib/mozilla/plugins

```
total 6900
drwxr-xr-x 2 alan users    4096 2007-10-28 18:32 .
drwxr-xr-x 3 root root     4096 2007-04-15 06:58 ..
-r--r--r-- 1 alan users     856 2007-06-19 19:31 flashplayer.xpt
-rwxr-xr-x 1 alan users 7040036 2007-06-19 19:31 libflashplayer.so
lrwxrwxrwx 1 alan users      36 2007-10-08 16:22 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 alan users      37 2007-10-08 16:22 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 alan users      34 2007-10-08 16:22 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 alan users      35 2007-10-08 16:22 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 alan users      36 2007-10-08 16:22 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 alan users      37 2007-10-08 16:22 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 alan users      42 2007-10-08 16:22 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 alan users      43 2007-10-08 16:22 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt

```

ls -al /usr/lib/firefox/plugins

```
total 20
drwxr-xr-x 2 root root  4096 2007-10-28 18:32 .
drwxr-xr-x 6 root root  4096 2007-10-22 20:32 ..
lrwxrwxrwx 1 root root    36 2007-10-08 16:22 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-10-08 16:22 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-10-08 16:22 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-10-08 16:22 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-10-08 16:22 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-10-08 16:22 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-10-08 16:22 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-10-08 16:22 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2007-07-31 08:29 libunixprintplugin.so
lrwxrwxrwx 1 root root    52 2007-10-28 18:32 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

```

Pretty sure this is the culprit, but I included the above just for good measure. 

```
ls: /tmp/nspluginwrapper: No such file or directory
alan@alan-desktop:~$ 

```

also just to note I clicked the link in the first post to download both Java & flash 64 version from your site and it gave me a mySQL error.   Maybe this topic is a bit old, but I hope there's still a chance at getting this to work. 

Thanks

---

### Post by vinmar on 2007-10-29
In /usr/lib/firefox/plugins npwrapper.libflashplayer.so is linked to /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so. But there is no such file as npwrapper.libflashplayer.so listed in /usr/lib/mozilla/plugins. Is that right?

---

### Post by Kilz on 2007-10-29
> **wawarren said:**
> I can't get this to work on Ubuntu 7.04 Fiesty Fawn 64

ls -al /usr/lib/mozilla/plugins

```
total 6900
drwxr-xr-x 2 alan users    4096 2007-10-28 18:32 .
drwxr-xr-x 3 root root     4096 2007-04-15 06:58 ..
-r--r--r-- 1 alan users     856 2007-06-19 19:31 flashplayer.xpt
-rwxr-xr-x 1 alan users 7040036 2007-06-19 19:31 libflashplayer.so
lrwxrwxrwx 1 alan users      36 2007-10-08 16:22 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 alan users      37 2007-10-08 16:22 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 alan users      34 2007-10-08 16:22 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 alan users      35 2007-10-08 16:22 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 alan users      36 2007-10-08 16:22 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 alan users      37 2007-10-08 16:22 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 alan users      42 2007-10-08 16:22 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 alan users      43 2007-10-08 16:22 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt

```

ls -al /usr/lib/firefox/plugins

```
total 20
drwxr-xr-x 2 root root  4096 2007-10-28 18:32 .
drwxr-xr-x 6 root root  4096 2007-10-22 20:32 ..
lrwxrwxrwx 1 root root    36 2007-10-08 16:22 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-10-08 16:22 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-10-08 16:22 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-10-08 16:22 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-10-08 16:22 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-10-08 16:22 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-10-08 16:22 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-10-08 16:22 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2007-07-31 08:29 libunixprintplugin.so
lrwxrwxrwx 1 root root    52 2007-10-28 18:32 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

```

Pretty sure this is the culprit, but I included the above just for good measure. 

```
ls: /tmp/nspluginwrapper: No such file or directory
alan@alan-desktop:~$ 

```

also just to note I clicked the link in the first post to download both Java & flash 64 version from your site and it gave me a mySQL error.   Maybe this topic is a bit old, but I hope there's still a chance at getting this to work. 

Thanks

That site is down for the foreseeable future, I have removed the link. Just use the flash install script that is linked in that post.

If it doesnt work, redo the lists above and also get the list from /tmp/ffplug

---

### Post by wawarren on 2007-10-29
That is the install script that I used.  Also, my tmp/ffplug doesn't exist either.  :(

---

### Post by Kilz on 2007-10-29
> **wawarren said:**
> That is the install script that I used.  Also, my tmp/ffplug doesn't exist either.  :(

Download the script again and rerun the script, do not turn off the computer, when you do /tmp files are deleted.

---

### Post by wawarren on 2007-10-29
Ok, I'm home from work and did as you said.  Still no flash, but I have those directories now. 

ls -al /tmp/ffplug

```
total 8
drwxr-xr-x  2 alan alan 4096 2007-10-29 17:34 .
drwxrwxrwt 12 root root 4096 2007-10-29 17:34 ..

```

ls -al /tmp/nsplugwrapper

```
total 2668
drwxr-xr-x  3 root root     4096 2007-10-29 17:34 .
drwxrwxrwt 12 root root     4096 2007-10-29 17:34 ..
drwxr-xr-x  2 1003 users    4096 2007-10-29 17:34 install_flash_player_9_linux
-rw-r--r--  1 root root  2608602 2007-07-05 13:48 install_flash_player_9_linux.tar.gz
-rw-r--r--  1 root root   100918 2007-10-21 06:51 nspluginwrapper_0.9.91.4_amd64.deb
alan@alan-desktop:~$ 
```

Thanks so much :)

---

### Post by Kilz on 2007-10-29
have you checked to see if nspluginwrapper was installed? See if its listed in synaptic.

---

### Post by OldTimeTech on 2007-10-29
My significant other needed flash for 64bit, so I used your great script and it worked, but like you said it messed with the sound.  So, I then used your sound pkg....well it didn't work and now the laptop has no sound at all.

Specs.
Acer Laptop 9300-5005
AMD Turion 64x2 1.6GHz
Nvidia GeForce Go 7300 
2Gb DDR2

Help would be appreciated to get his sound back.  I tried to upgrade him to Gutsy, but had tons of trouble and so back graded him to feisty which he had no problems with before....only for some reason, this time flash didn't work and now no sound....

Help...I'm in trouble....LOL!

---

### Post by wawarren on 2007-10-29
> **Kilz said:**
> have you checked to see if nspluginwrapper was installed? See if its listed in synaptic.

synaptic lists nspluginwrapper 0.9.91.4-0ubuntu3~ being installed.

---

### Post by Condoulo on 2007-10-30
hey, do you know how I can get it to run in the new 64-bit beta of Opere 9.5 Kestrel without crashing?

---

### Post by Kilz on 2007-10-30
> **wawarren said:**
> synaptic lists nspluginwrapper 0.9.91.4-0ubuntu3~ being installed.

ok, now lets take a look at ```
ls -al /usr/lib/mozilla/plugins
``` and ```
ls -al /usr/lib/firefox/plugins
``` , please post the results.

---

### Post by Kilz on 2007-10-30
> **OldTimeTech said:**
> My significant other needed flash for 64bit, so I used your great script and it worked, but like you said it messed with the sound.  So, I then used your sound pkg....well it didn't work and now the laptop has no sound at all.

Specs.
Acer Laptop 9300-5005
AMD Turion 64x2 1.6GHz
Nvidia GeForce Go 7300 
2Gb DDR2

Help would be appreciated to get his sound back.  I tried to upgrade him to Gutsy, but had tons of trouble and so back graded him to feisty which he had no problems with before....only for some reason, this time flash didn't work and now no sound....

Help...I'm in trouble....LOL!

Have you tried uninstalling the ia32-alsa-oss package? How did you back grade the Gutsy install?

---

### Post by OldTimeTech on 2007-10-30
wiped the partition after moving all relevant files to a 4gb thumbdrive.  Then used a liveCD to re-install Feisty.

No I have not tried uninstalling the ia32-alsa-oss package, didn't actually know what package I was looking for...now I will try that.

I'll let you know what happens.

---

### Post by OldTimeTech on 2007-10-30
okay, uninstalled the ia32-alsa-oss package and it made no difference....still have no sound.  The flash is working perfectly....just doesn't have sound with it.

---

### Post by Kilz on 2007-10-30
> **OldTimeTech said:**
> okay, uninstalled the ia32-alsa-oss package and it made no difference....still have no sound.  The flash is working perfectly....just doesn't have sound with it.

Did the sound return to the rest of your laptop.

---

### Post by OldTimeTech on 2007-10-30
Nope, no sound on boot up or close.

Am I going to have to wipe the hard drive and re-install feisty again?

---

### Post by Kilz on 2007-10-30
Lets try to avoid that first. Double click on the sound icon in the upper taskbar, in the right hand corner.  The mixer should open click on file and change device, if there is more than one option tyr the other one.

---

### Post by OldTimeTech on 2007-10-30
Did that....the device was the alsa-oss and I changed it to the realtek with still no sound.

---

### Post by Kilz on 2007-10-30
> **OldTimeTech said:**
> Did that....the device was the alsa-oss and I changed it to the realtek with still no sound.

If a reboot doesnt help, it may be less headache to reinstall.

---

### Post by OldTimeTech on 2007-10-30
okay, I'm feeling really stupid.

While waiting for you to answer, I looked around on other forums and found this:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Followed it until it got to compilation, I'm still noob enough that I'm not comfortable with that.  But still trying to figure out what was going on, I started to go through my applications, when I saw a gnome alsa mixer.  Opened it up...low and behold, three quarters of the components were muted.  Unmuted all, closed the mixer and went to where significant other uses the flash player and sound....it worked!!!!

And I also have sound when closing down the laptop.

Thanks for the help ;)

---

### Post by felin on 2007-10-30
> **vinmar said:**
> After trying everything in this thread with no luck, I thought I'd share how I fixed Flash hanging in 64-bit firefox.

1) Uninstall flashplugin-nonfree if installed through synaptic.
2) Get a list of any Flash remains with nspluginwrapper -l
3) For me this showed a combination of 0.91.94 and 0.91.95 versions. I manually deleted every file listed.
4) Run nspluginwrapper -l again and confirm no files listed.
5) Then I installed flashplugin-nonfree again through synaptic.

Thanks for this solution.

---

### Post by wawarren on 2007-10-30
Ok, here's the listing from both of those directories. 

/usr/lib/mozilla/plugins

```
total 6900
drwxr-xr-x 2 alan users    4096 2007-10-29 17:34 .
drwxr-xr-x 3 root root     4096 2007-04-15 06:58 ..
-r--r--r-- 1 alan users     856 2007-06-19 19:31 flashplayer.xpt
-rwxr-xr-x 1 alan users 7040036 2007-06-19 19:31 libflashplayer.so
lrwxrwxrwx 1 alan users      36 2007-10-08 16:22 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 alan users      37 2007-10-08 16:22 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 alan users      34 2007-10-08 16:22 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 alan users      35 2007-10-08 16:22 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 alan users      36 2007-10-08 16:22 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 alan users      37 2007-10-08 16:22 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 alan users      42 2007-10-08 16:22 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 alan users      43 2007-10-08 16:22 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt

```

and here's ls -al /usr/lib/firefox/plugins

```
total 20
drwxr-xr-x 2 root root  4096 2007-10-29 17:34 .
drwxr-xr-x 6 root root  4096 2007-10-22 20:32 ..
lrwxrwxrwx 1 root root    36 2007-10-08 16:22 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-10-08 16:22 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-10-08 16:22 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-10-08 16:22 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-10-08 16:22 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-10-08 16:22 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-10-08 16:22 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-10-08 16:22 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2007-07-31 08:29 libunixprintplugin.so
lrwxrwxrwx 1 root root    52 2007-10-29 17:34 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

```

Thanks

---

### Post by oppo on 2007-11-01
Helo Kilz,

How would I install Flash on Gutsy (AMD64) using Synaptic.? Might seem a dumb question but i am a ubuntu newbie

---

### Post by Kilz on 2007-11-02
> **oppo said:**
> Helo Kilz,

How would I install Flash on Gutsy (AMD64) using Synaptic.? Might seem a dumb question but i am a ubuntu newbie

First off [here is a wonderful site]("http://cutlersoftware.com/ubuntuinstall/") that tells new users exactly how to install anything in Ubuntu. But the short answer is do a search in synaptic for flashplugin-nonfree.

---

### Post by Kilz on 2007-11-02
> **wawarren said:**
> Ok, here's the listing from both of those directories. 


Thanks
Ok open a terminal and type or copy/paste in these 2 commands.
```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```
and
```
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/
```

---

### Post by wawarren on 2007-11-02
> **Kilz said:**
> Ok open a terminal and type or copy/paste in these 2 commands.
```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```
and
```
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/
```

It looks like we're getting somewhere now.  I received an error after typing the first command in the terminal. 

```
alan@alan-desktop:~$ sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
Password:
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libgtk-x11-2.0.so.0: wrong ELF class: ELFCLASS64
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```

I've solved this type of ELF class error installing other 32 bit apps on 64 bit Fiesty, but I'm not even sure I'm supposed to be using the 32 bit nspluginwrapper?  I notice /usr/lib/nspluginwrapper has both i386 and x86_64 folders.  

I did the symbolic link anyways.  Hope that doesn't make things worse. 

Also, I did a ldd on npviewer.bin
```
alan@alan-desktop:/usr/lib/nspluginwrapper/i386/linux$ ldd npviewer.bin
        linux-gate.so.1 =>  (0xffffe000)
        libgtk-x11-2.0.so.0 => not found
        libgdk-x11-2.0.so.0 => not found
        libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf7f60000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7f5c000)
        libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf7ec7000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7dd6000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7d85000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7d6d000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7d61000)
        libc.so.6 => /lib32/libc.so.6 (0xf7c20000)
        /lib/ld-linux.so.2 (0xf7fb4000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7c1d000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7c18000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7c0e000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7bf6000)
```


Thanks

---

### Post by Kilz on 2007-11-02
> **wawarren said:**
> It looks like we're getting somewhere now.  I received an error after typing the first command in the terminal. 

```
alan@alan-desktop:~$ sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
Password:
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libgtk-x11-2.0.so.0: wrong ELF class: ELFCLASS64
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```

I've solved this type of ELF class error installing other 32 bit apps on 64 bit Fiesty, but I'm not even sure I'm supposed to be using the 32 bit nspluginwrapper?  I notice /usr/lib/nspluginwrapper has both i386 and x86_64 folders.  

I did the symbolic link anyways.  Hope that doesn't make things worse. 

Also, I did a ldd on npviewer.bin
```
alan@alan-desktop:/usr/lib/nspluginwrapper/i386/linux$ ldd npviewer.bin
        linux-gate.so.1 =>  (0xffffe000)
        libgtk-x11-2.0.so.0 => not found
        libgdk-x11-2.0.so.0 => not found
        libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf7f60000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7f5c000)
        libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf7ec7000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7dd6000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7d85000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7d6d000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7d61000)
        libc.so.6 => /lib32/libc.so.6 (0xf7c20000)
        /lib/ld-linux.so.2 (0xf7fb4000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7c1d000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7c18000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7c0e000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7bf6000)
```


Thanks

The reason there are 32bit and 64bit parts to nspluginwrapper is because its a enabling a 32bit plugin to be used in your 64bit browser. The 32bit libgtk-x11-2.0.so.0 is included in ia32-libs-gtk. You need to remove the symlink and install the ia32-libs-gtk package.

---

### Post by wawarren on 2007-11-02
I've installed ia32-libs-gtk before, but I double checked in synaptic and sure enough it was there. I reinstalled it just to make sure, but for some reason /usr/lib/nspluginwrapper/i386/linux/npviewer.bin still can't find these 2 lib files. 

I manually checked and I do have the lib it's telling me is missing inside /usr/lib, so is it possible npviewer.bin is looking in the wrong place?   I notice npviewer has a script file with a few variables inside it.  Would it be possible to define an environment variable to show it where the right libs are?  I don't know what variable to use or I'd try that.

---

### Post by Kilz on 2007-11-02
> **wawarren said:**
> I've installed ia32-libs-gtk before, but I double checked in synaptic and sure enough it was there. I reinstalled it just to make sure, but for some reason /usr/lib/nspluginwrapper/i386/linux/npviewer.bin still can't find these 2 lib files. 

I manually checked and I do have the lib it's telling me is missing inside /usr/lib, so is it possible npviewer.bin is looking in the wrong place?   I notice npviewer has a script file with a few variables inside it.  Would it be possible to define an environment variable to show it where the right libs are?  I don't know what variable to use or I'd try that.

Would you please give me the ia32-libs-gtk version number from synaptic. It is not telling you the file is missing from /usr/lib, that is where 64bit libraries are located. It is looking for the 32bit library of the same name. That is included in ia32-libs-gtk  and should be in /usr/lib32. Please do not copy any files from /usr/lib to /usr/lib32 or create symlinks. It will not work.

---

### Post by wawarren on 2007-11-03
> **Kilz said:**
> Would you please give me the ia32-libs-gtk version number from synaptic. It is not telling you the file is missing from /usr/lib, that is where 64bit libraries are located. It is looking for the 32bit library of the same name. That is included in ia32-libs-gtk  and should be in /usr/lib32. Please do not copy any files from /usr/lib to /usr/lib32 or create symlinks. It will not work.

Thanks for all your help.  I've got Flash working now, and my sound works too :guitar:

I downloaded the libs I needed from [http://packages.ubuntu.com](http://packages.ubuntu.com) and copied them into my /usr/lib32 folder.  After that I followed the directions you posted earlier and everything works. 

My ia32-libs-gtk is version 25, and I was missing.  libgdk-x11-2.0.so.0, libgtk-x11-2.0.so.0, libpangocairo-1.0.so.0, libpango-1.0.so.0, and libatk-1.0.so.0.  I have no clue if ia32-libs-gtk is supposed to install those or not, but my /usr/lib32 folder didn't have them.

---

### Post by Kilz on 2007-11-03
> **wawarren said:**
> Thanks for all your help.  I've got Flash working now, and my sound works too :guitar:

I downloaded the libs I needed from [http://packages.ubuntu.com](http://packages.ubuntu.com) and copied them into my /usr/lib32 folder.  After that I followed the directions you posted earlier and everything works. 

My ia32-libs-gtk is version 25, and I was missing.  libgdk-x11-2.0.so.0, libgtk-x11-2.0.so.0, libpangocairo-1.0.so.0, libpango-1.0.so.0, and libatk-1.0.so.0.  I have no clue if ia32-libs-gtk is supposed to install those or not, but my /usr/lib32 folder didn't have them.

Is that the version synaptic says was installed, or the version you downloaded from the package site? Im trying to understand why it wouldnt install.

---

### Post by wawarren on 2007-11-03
Synaptic said I have version 25 installed.  I used Synaptic to install this to begin with as well.

---

### Post by rockballad on 2007-11-05
Thanks! Last week, I used it for Ubuntu 7.04, and it worked well.

But today, I upgraded to Ubuntu 7.10, do you have an option for this Ubuntu version?

Thanks and have a nice day!

---

### Post by Kilz on 2007-11-05
> **rockballad said:**
> Thanks! Last week, I used it for Ubuntu 7.04, and it worked well.

But today, I upgraded to Ubuntu 7.10, do you have an option for this Ubuntu version?

Thanks and have a nice day!

Its not needed, take a look at the first post.

---

### Post by rockballad on 2007-11-06
> **Kilz said:**
> Its not needed, take a look at the first post.

Oops! I'm still not familiar with the new name of this Ubuntu version - Gutsy Gibbon. I'm using FF 2.0.0.6, it can't install Flash plugin by itself. Add/Remove program couldn't help, too. The Adobe Flash is uncheckable. It may be related to copyright problem?

Thanks, any way!

---

### Post by Kilz on 2007-11-06
> **rockballad said:**
> Oops! I'm still not familiar with the new name of this Ubuntu version - Gutsy Gibbon. I'm using FF 2.0.0.6, it can't install Flash plugin by itself. Add/Remove program couldn't help, too. The Adobe Flash is uncheckable. It may be related to copyright problem?

Thanks, any way!

flash in Gutsy is installable from the repos. You can use synaptic to install flashplugin-nonfree. But I would first do a search in synaptic for nspluginwrapper and uninstall it first if you installed this script on Feisty and then upgraded that install to Gutsy. [This link might help if you need help with synaptic.]("http://www.monkeyblog.org/ubuntu/installing/")

---

### Post by dallag on 2007-11-07
:) Hey man... is verygood post..

Flash function very nice .....muito bom funcionou legal...

Thanks Kils 

Very nice:guitar:

---

### Post by lister171254 on 2007-11-09
Hi Kilz,

Tried your script, but all I get is a message that I don't need this in Gutsy. Problem is the flash plugin doesn't work. Are there any logs I can send when I report this as a bug?

Thanks,

Leo

---

### Post by Kilz on 2007-11-09
> **lister171254 said:**
> Hi Kilz,

Tried your script, but all I get is a message that I don't need this in Gutsy. Problem is the flash plugin doesn't work. Are there any logs I can send when I report this as a bug?

Thanks,

Leo

You might want to read back a few posts.

---

### Post by lister171254 on 2007-11-09
> **Kilz said:**
> You might want to read back a few posts.


Thanks,

ndiswrapper was still installed due to a problem during the upgrade. removing ndiswrapper  and Installing flashplugin-nonfree fixed the problem.

Thanks for you help

Leo

---

### Post by wawarren on 2007-11-10
Just curious.  Is it normal for npviewer.bin to be using 400+ MB RAM? 

 I have a few really long FLV's that I watch on a regular basis and it's difficult to have any other applications running at the same time while I'm watching these videos.

---

### Post by OisinT on 2007-11-15
hey, I am having a problem.. I just upgraded to Gusty 64 and installed firefox 64 using ubuntuzilla.
Now from the bold part of the post I'm understanding that I don't need nspluginwrapper installed, but i'm still not getting flash loading in Firefox.  I saw that some people are getting a fix with installing flashplugin-nonfree, but when i try to install that it automatically installs nspluginwrapper with it.  Am I missing something important?

```
oisint@OisinT1:~$ ls -al /usr/lib/mozilla/plugins/
total 7120
drwxr-xr-x 2 root   root      4096 2007-11-15 20:23 .
drwxr-xr-x 3 root   root      4096 2007-04-15 12:58 ..
-r--r--r-- 1   1003 users      856 2007-06-20 01:31 flashplayer.xpt
lrwxrwxrwx 1 root   root        37 2007-11-15 20:23 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rw-r--r-- 1 root   root     19456 2007-01-05 19:52 libflash-mozplugin.so
-rwxr-xr-x 1   1003 users  7040036 2007-06-20 01:31 libflashplayer.so
-rw-r--r-- 1 root   root     65692 2007-08-30 23:50 libswfdecmozilla.a
-rw-r--r-- 1 root   root      1308 2007-08-30 23:50 libswfdecmozilla.la
-rw-r--r-- 1 root   root     45320 2007-08-30 23:50 libswfdecmozilla.so
lrwxrwxrwx 1 root   root        36 2007-11-13 21:36 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root   root        37 2007-11-13 21:36 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root   root        34 2007-11-13 21:36 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root   root        35 2007-11-13 21:36 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root   root        36 2007-11-13 21:36 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root   root        37 2007-11-13 21:36 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root   root        42 2007-11-13 21:36 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root   root        43 2007-11-13 21:36 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 oisint oisint   70120 2007-09-13 17:01 npwrapper.libflashplayer.so

```

all help is appreciated as it's useless without flash :(

---

### Post by Kilz on 2007-11-15
> **OisinT said:**
> hey, I am having a problem.. I just upgraded to Gusty 64 and installed firefox 64 using ubuntuzilla.
Now from the bold part of the post I'm understanding that I don't need nspluginwrapper installed, but i'm still not getting flash loading in Firefox.  I saw that some people are getting a fix with installing flashplugin-nonfree, but when i try to install that it automatically installs nspluginwrapper with it.  Am I missing something important?

```
oisint@OisinT1:~$ ls -al /usr/lib/mozilla/plugins/
total 7120
drwxr-xr-x 2 root   root      4096 2007-11-15 20:23 .
drwxr-xr-x 3 root   root      4096 2007-04-15 12:58 ..
[B]-r--r--r-- 1   1003 users      856 2007-06-20 01:31 flashplayer.xpt
lrwxrwxrwx 1 root   root        37 2007-11-15 20:23 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rw-r--r-- 1 root   root     19456 2007-01-05 19:52 libflash-mozplugin.so
-rwxr-xr-x 1   1003 users  7040036 2007-06-20 01:31 libflashplayer.so[/B]
-rw-r--r-- 1 root   root     65692 2007-08-30 23:50 libswfdecmozilla.a
-rw-r--r-- 1 root   root      1308 2007-08-30 23:50 libswfdecmozilla.la
-rw-r--r-- 1 root   root     45320 2007-08-30 23:50 libswfdecmozilla.so
lrwxrwxrwx 1 root   root        36 2007-11-13 21:36 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root   root        37 2007-11-13 21:36 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root   root        34 2007-11-13 21:36 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root   root        35 2007-11-13 21:36 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root   root        36 2007-11-13 21:36 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root   root        37 2007-11-13 21:36 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root   root        42 2007-11-13 21:36 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root   root        43 2007-11-13 21:36 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 oisint oisint   70120 2007-09-13 17:01 npwrapper.libflashplayer.so

```

all help is appreciated as it's useless without flash :(

No, you are not missing anything, the reason you dont have to install nspluginwrapper on Gutsy is because it automatically does it.  Your problem appears that you have multiple flash plugins (bolded).

---

### Post by OisinT on 2007-11-16
> **Kilz said:**
> No, you are not missing anything, the reason you dont have to install nspluginwrapper on Gutsy is because it automatically does it.  Your problem appears that you have multiple flash plugins (bolded).

ok, i removed bolded plugins and am still missing flash.

```
oisint@OisinT1:~$ ls -al /usr/lib/mozilla/plugins/
total 208
drwxr-xr-x 2 root   root    4096 2007-11-16 14:07 .
drwxr-xr-x 3 root   root    4096 2007-04-15 12:58 ..
-rw-r--r-- 1 root   root   65692 2007-08-30 23:50 libswfdecmozilla.a
-rw-r--r-- 1 root   root    1308 2007-08-30 23:50 libswfdecmozilla.la
-rw-r--r-- 1 root   root   45320 2007-08-30 23:50 libswfdecmozilla.so
lrwxrwxrwx 1 root   root      36 2007-11-13 21:36 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root   root      37 2007-11-13 21:36 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root   root      34 2007-11-13 21:36 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root   root      35 2007-11-13 21:36 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root   root      36 2007-11-13 21:36 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root   root      37 2007-11-13 21:36 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root   root      42 2007-11-13 21:36 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root   root      43 2007-11-13 21:36 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 oisint oisint 70120 2007-09-13 17:01 npwrapper.libflashplayer.so

```

---

### Post by Kilz on 2007-11-16
> **OisinT said:**
> ok, i removed bolded plugins and am still missing flash.

```
oisint@OisinT1:~$ ls -al /usr/lib/mozilla/plugins/
total 208
drwxr-xr-x 2 root   root    4096 2007-11-16 14:07 .
drwxr-xr-x 3 root   root    4096 2007-04-15 12:58 ..
-rw-r--r-- 1 root   root   65692 2007-08-30 23:50 libswfdecmozilla.a
-rw-r--r-- 1 root   root    1308 2007-08-30 23:50 libswfdecmozilla.la
-rw-r--r-- 1 root   root   45320 2007-08-30 23:50 libswfdecmozilla.so
lrwxrwxrwx 1 root   root      36 2007-11-13 21:36 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root   root      37 2007-11-13 21:36 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root   root      34 2007-11-13 21:36 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root   root      35 2007-11-13 21:36 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root   root      36 2007-11-13 21:36 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root   root      37 2007-11-13 21:36 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root   root      42 2007-11-13 21:36 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root   root      43 2007-11-13 21:36 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 oisint oisint 70120 2007-09-13 17:01 npwrapper.libflashplayer.so

```

You also removed the good flash plugin, the wrapper must point to it. Just reinstall flashplugin-nonfree in synaptic and you should be ok. If it isnt working still you might want to report a bug. The package should uninstall conflicting files when installed.

---

### Post by OisinT on 2007-11-16
> **Kilz said:**
> You also removed the good flash plugin, the wrapper must point to it. Just reinstall flashplugin-nonfree in synaptic and you should be ok. If it isnt working still you might want to report a bug. The package should uninstall conflicting files when installed.

when i install flashplugin-nonfree it automatically installs nspluginwrapper with it.
flash still won't work.  you think this is a bug or is there anything else I should check to make sure isn't conflicting?

---

### Post by Kilz on 2007-11-16
> **OisinT said:**
> when i install flashplugin-nonfree it automatically installs nspluginwrapper with it.
flash still won't work.  you think this is a bug or is there anything else I should check to make sure isn't conflicting?

Nspluginwrapper will always install. It is what makes it possible to use the flash plugin. But in Gutsy it is no longer necessarily to install it with scripts or howto's. It installs with flashplugin-nonfree. You want it to install.  The only time you should remove it is when you upgrade a feisty install that you used a script or howto to install it. This is so the new gutsy package installs correctly.
There is nothing I know of that will cause the conflict. You may as well report the bug

---

### Post by OisinT on 2007-11-17
> **Kilz said:**
> Nspluginwrapper will always install. It is what makes it possible to use the flash plugin. But in Gutsy it is no longer necessarily to install it with scripts or howto's. It installs with flashplugin-nonfree. You want it to install.  The only time you should remove it is when you upgrade a feisty install that you used a script or howto to install it. This is so the new gutsy package installs correctly.
There is nothing I know of that will cause the conflict. You may as well report the bug

thanks for all your help!

---

### Post by ktamm on 2007-11-24
> **vinmar said:**
> After trying everything in this thread with no luck, I thought I'd share how I fixed Flash hanging in 64-bit firefox.

1) Uninstall flashplugin-nonfree if installed through synaptic.
2) Get a list of any Flash remains with nspluginwrapper -l
3) For me this showed a combination of 0.91.94 and 0.91.95 versions. I manually deleted every file listed.
4) Run nspluginwrapper -l again and confirm no files listed.
5) Then I installed flashplugin-nonfree again through synaptic.

Thank you for this solution. I had the same problem as everyone else when i upgraded to 7.10 64bit. Everything works good again now though :)

---

### Post by OisinT on 2007-11-26
> **vinmar said:**
> After trying everything in this thread with no luck, I thought I'd share how I fixed Flash hanging in 64-bit firefox.

1) Uninstall flashplugin-nonfree if installed through synaptic.
2) Get a list of any Flash remains with nspluginwrapper -l
3) For me this showed a combination of 0.91.94 and 0.91.95 versions. I manually deleted every file listed.
4) Run nspluginwrapper -l again and confirm no files listed.
5) Then I installed flashplugin-nonfree again through synaptic.


amazing... after everything it works.  thank you thank you thank you thank you!

---

### Post by prosper927 on 2007-11-26
thanks! this is the easiest way to install flash in 64bit. i have tried several other instructions before but this is the best!!!:guitar::lolflag:

---

### Post by googolboy on 2007-11-26
2+ hours and yet another feel like a complete idiot computer moment

AMD 64 bit on Gusty 7.10 wasn't installing and it said the nonfree flash through firefox wasn't found... Tried all the other methods listed. Then just now I figured out what was causing an issue.

after searching google and finding a thread of someone pointing another lost soul to: [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#head-74ed36356cdab258889ed4e9ad010f068e13ff38](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#head-74ed36356cdab258889ed4e9ad010f068e13ff38)
I went to that adobe page expecting it not to work. Then for the hell of it I click the install app button from within the page, not the yellow bar that firefox puts up. The same two possible installs get listed, i choose adobe flash and all the sudden it starts installing the plugin nonfree version.

DO NOT install through the firefox yellow bar saying install missing plugins.
Instead visit: [http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)
And click install missing plugins from the green buttun within the page. I dont know why but this works. Installing off the of install missing plugins from the youtube pages never worked but this did. Now i'm onto fixing nvidia drivers not outputting at 1920x1200 when they say they are...

---

### Post by Kilz on 2007-11-27
> **googolboy said:**
> 2+ hours and yet another feel like a complete idiot computer moment

AMD 64 bit on Gusty 7.10 wasn't installing and it said the nonfree flash through firefox wasn't found... Tried all the other methods listed. Then just now I figured out what was causing an issue.

after searching google and finding a thread of someone pointing another lost soul to: [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#head-74ed36356cdab258889ed4e9ad010f068e13ff38](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#head-74ed36356cdab258889ed4e9ad010f068e13ff38)
I went to that adobe page expecting it not to work. Then for the hell of it I click the install app button from within the page, not the yellow bar that firefox puts up. The same two possible installs get listed, i choose adobe flash and all the sudden it starts installing the plugin nonfree version.

DO NOT install through the firefox yellow bar saying install missing plugins.
Instead visit: [http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)
And click install missing plugins from the green buttun within the page. I dont know why but this works. Installing off the of install missing plugins from the youtube pages never worked but this did. Now i'm onto fixing nvidia drivers not outputting at 1920x1200 when they say they are...


For Gutsy all that is needed is.
```
sudo apt-get install flashplugin-nonfree
```

That being the saide. Please, this thread is for Feisty. Please start a new Gutsy thread if you are having issues.

---

### Post by vbvamsi on 2007-12-09
I ran the script and got the flash working. But there's no sound. I downloaded and installed ia32-alsa-oss. Even after that, sound is not working. Here are the contents of my /usr/lib/mozilla/plugins.

drwxr-xr-x 2 vbvamsi users     632 2007-12-09 11:24 .
drwxr-xr-x 3 root    root       72 2007-09-17 10:28 ..
-rwxr-xr-x 1 vbvamsi users 8119784 2007-11-20 18:24 libflashplayer.so
lrwxrwxrwx 1 vbvamsi users      38 2007-09-17 12:30 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
-rw-r--r-- 1 vbvamsi users   28336 2007-02-09 14:38 mozplugger.so
-rw-r--r-- 1 vbvamsi users  269216 2007-01-25 19:17 mplayerplug-in-dvx.so
-rw-r--r-- 1 vbvamsi users     981 2007-01-25 19:17 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 vbvamsi users  269408 2007-01-25 19:17 mplayerplug-in-qt.so
-rw-r--r-- 1 vbvamsi users     981 2007-01-25 19:17 mplayerplug-in-qt.xpt
-rw-r--r-- 1 vbvamsi users  269472 2007-01-25 19:17 mplayerplug-in-rm.so
-rw-r--r-- 1 vbvamsi users     981 2007-01-25 19:17 mplayerplug-in-rm.xpt
-rw-r--r-- 1 vbvamsi users  270648 2007-01-25 19:17 mplayerplug-in.so
-rw-r--r-- 1 vbvamsi users  269760 2007-01-25 19:17 mplayerplug-in-wmp.so
-rw-r--r-- 1 vbvamsi users     981 2007-01-25 19:17 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 vbvamsi users     981 2007-01-25 19:17 mplayerplug-in.xpt
-rwxr-xr-x 1 vbvamsi users 1127564 2007-09-21 09:40 nppdf.so
lrwxrwxrwx 1 vbvamsi users      60 2007-12-09 11:24 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

My firefox about:plugins shows this for flash.
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Could you please help me to get my sound working for flash in firefox.

Thanks
vbvamsi

---

### Post by skinnymg1 on 2007-12-10
wonderful package im a noob to this and it was easier than setting up my network connection by far thanks love it








skinnymg1
amd 64 3800+
1.5 gig of ram
nvidia 6600gt
diamond 7.1 sound card

---

### Post by daradib on 2007-12-10
See this for more information on the current bug with the flashplugin-nonfree package: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by Kilz on 2007-12-11
> **daradib said:**
> See this for more information on the current bug with the flashplugin-nonfree package: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

Would you please not post off topic links in the thread. This thread is solely for Feisty and before as the first post says. As such the script in the first post works and is not susceptible to the Gutsy flash bug.

---

### Post by daradib on 2007-12-11
> **Kilz said:**
> Would you please not post off topic links in the thread. This thread is solely for Feisty and before as the first post says. As such the script in the first post works and is not susceptible to the Gutsy flash bug.

My mistake. I was reading threads too quickly. I do believe, however, that the flash bug affect older Ubuntu versions, including Feisty (not this script) when using standard package installation though the repositories.

---

### Post by Kilz on 2007-12-11
> **daradib said:**
> My mistake. I was reading threads too quickly. I do believe, however, that the flash bug affect older Ubuntu versions, including Feisty (not this script) when using standard package installation though the repositories.


There is no way to install flashplugin-nonfree (adobe flash) to amd64 Feisty, or before. [The package doesnt exist for amd64.]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=flashplugin-nonfree&searchon=names&subword=1&version=all&release=all") Even if you could [there is no nspluginwrapper to make it work]("http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=nspluginwrapper&searchon=names"). Gutsy was the first 64bit Ubuntu to have Flash (and nspluginwrapper) installable from the repositories. My script downloads the files directly from Adobe and nspluginwrapper from one of my web spaces.

---

### Post by daradib on 2007-12-11
> **Kilz said:**
> There is no way to install flashplugin-nonfree (adobe flash) to amd64 Feisty, or before. [The package doesnt exist for amd64.]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=flashplugin-nonfree&searchon=names&subword=1&version=all&release=all") Even if you could [there is no nspluginwrapper to make it work]("http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=nspluginwrapper&searchon=names"). Gutsy was the first 64bit Ubuntu to have Flash (and nspluginwrapper) installable from the repositories. My script downloads the files directly from Adobe and nspluginwrapper from one of my web spaces.

I understand. My apologies.

---

### Post by Kilz on 2007-12-12
> **daradib said:**
> I understand. My apologies.

Since it seems like its taking the Ubuntu Developers forever to fix this issue I have modified my script in this thread to install to Gutsy.

---

### Post by daradib on 2007-12-12
Actually, if you check the thread I posted a few posts back and the Launchpad bug, you will see that the new package was uploaded to all supported Ubuntu proposed repositories (6.06-7.10) about 8 hours ago, though 32-bit and 64-bit binaries have not yet been built.

[https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree](https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree)

Just as we were beginning to lose hope. But there are some problems with this update (namely for Konqueror and Opera, see more info at [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397))

---

### Post by Kilz on 2007-12-12
> **daradib said:**
> Actually, if you check the thread I posted a few posts back and the Launchpad bug, you will see that the new package was uploaded to all supported Ubuntu proposed repositories (6.06-7.10) about 8 hours ago, though 32-bit and 64-bit binaries have not yet been built.

[https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree](https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree)

Just as we were beginning to lose hope. But there are some problems with this update (namely for Konqueror and Opera, see more info at [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397))

Well it cant hurt to have the script, just in case.  :D

---

### Post by daradib on 2007-12-12
> **Kilz said:**
> Well it cant hurt to have the script, just in case.  :D

Of course.

---

### Post by Tsume on 2007-12-15
Your script saved my life.

Even after apt-get update the repos did not have a WORKING flash version for x64.

---

### Post by Blufar on 2007-12-15
The link to download the install script is broken/ does not work. Please fix it.

---

### Post by Kilz on 2007-12-15
> **Blufar said:**
> The link to download the install script is broken/ does not work. Please fix it.

The download is and was working.

---

### Post by Scarlett on 2007-12-15
Kilz, you are my hero!!!!

It worked perfectly for me.

---

### Post by daradib on 2007-12-16
Kilz, I am confused why the new flashplugin-nonfree package has been built for 64-bit on the releases 6.06-7.04. Those releases have no nspluginwrapper package in the repositories.

Notice the 64-bit packages for 6.06-7.04:
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

[https://www.launchpad.net/ubuntu/feisty/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.7.04](https://www.launchpad.net/ubuntu/feisty/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.7.04)
[https://www.launchpad.net/ubuntu/edgy/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.6.10](https://www.launchpad.net/ubuntu/edgy/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.6.10)
[https://www.launchpad.net/ubuntu/dapper/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.6.06](https://www.launchpad.net/ubuntu/dapper/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.6.06)

---

### Post by Kilz on 2007-12-16
> **daradib said:**
> Kilz, I am confused why the new flashplugin-nonfree package has been built for 64-bit on the releases 6.06-7.04. Those releases have no nspluginwrapper package in the repositories.

Notice the 64-bit packages for 6.06-7.04:
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

[https://www.launchpad.net/ubuntu/feisty/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.7.04](https://www.launchpad.net/ubuntu/feisty/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.7.04)
[https://www.launchpad.net/ubuntu/edgy/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.6.10](https://www.launchpad.net/ubuntu/edgy/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.6.10)
[https://www.launchpad.net/ubuntu/dapper/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.6.06](https://www.launchpad.net/ubuntu/dapper/amd64/flashplugin-nonfree/9.0.115.0ubuntu0.6.06)

I have no idea, it makes little sense to me. Its probably because they always existed. But since the developers didnt make a 32bit browser or nspluginwrapper available it was a wasted effort.
Its just one example of how the 64bit version is treated (functionality is ignored) vs the 32bit (I wonder how much eye candy we can add).
[Its something they have known about for some time. ]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-September/020552.html") But it took untill Gutsy for them to do even a little.

---

### Post by LIARryas on 2007-12-16
Hello. I'm fairly new to Ubuntu. I followed the instructions given in the first post and installed this thing, but my browser still won't play any flash content found in web pages. I don't know why. My about:plugins page tells me this is installed and enabled.

I'm running the 64-bit version of 7.10, and I downloaded and used the file named nspluginwrapper-install-0-1.8.2.tar.gz

The results of the commands in the readme are:

ls -al /usr/lib/mozilla/plugins

total 7956
drwxr-xr-x 2 ryan users    4096 2007-12-16 14:31 .
drwxr-xr-x 3 root root     4096 2007-10-15 18:27 ..
-rwxr-xr-x 1 ryan users 8119784 2007-11-20 17:24 libflashplayer.so
lrwxrwxrwx 1 ryan users      38 2007-11-20 19:56 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 ryan users      39 2007-11-19 14:09 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 ryan users      36 2007-11-04 09:30 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 ryan users      37 2007-11-04 09:30 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 ryan users      34 2007-11-04 09:30 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 ryan users      35 2007-11-04 09:30 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 ryan users      36 2007-11-04 09:30 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 ryan users      37 2007-11-04 09:30 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 ryan users      42 2007-11-04 09:30 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 ryan users      43 2007-11-04 09:30 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 ryan users      60 2007-12-16 14:31 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

ls -al /usr/lib/firefox/plugins

total 24
drwxr-xr-x 2 root root  4096 2007-12-16 14:24 .
drwxr-xr-x 5 root root  4096 2007-12-04 16:09 ..
lrwxrwxrwx 1 root root    39 2007-11-19 14:09 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root    36 2007-11-04 09:30 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-11-04 09:30 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-11-04 09:30 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-11-04 09:30 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-11-04 09:30 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-11-04 09:30 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-11-04 09:30 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-11-04 09:30 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11456 2007-12-04 05:04 libunixprintplugin.so
lrwxrwxrwx 1 root root    60 2007-12-16 14:24 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

ls -al /tmp/nsplugwrapper

total 2984
drwxr-xr-x  3 root root     4096 2007-12-16 14:24 .
drwxrwxrwt 13 root root     4096 2007-12-16 14:30 ..
drwxr-xr-x  2  501 users    4096 2007-12-16 14:31 install_flash_player_9_linux
-rw-r--r--  1 root root  3036127 2007-11-29 15:23 install_flash_player_9_linux.tar.gz


Is there any way somebody might be able to help me out and tell me why this isn't working and how I might fix the problem? I'm sorry if this problem has been solved earlier in this thread, but I don't really have time to read all 49 pages of it. :oops:

---

### Post by confy on 2007-12-16
It worked!

Thank you!

---

### Post by daradib on 2007-12-16
> **Kilz said:**
> I have no idea, it makes little sense to me. Its probably because they always existed. But since the developers didnt make a 32bit browser or nspluginwrapper available it was a wasted effort.
Its just one example of how the 64bit version is treated (functionality is ignored) vs the 32bit (I wonder how much eye candy we can add).
[Its something they have known about for some time. ]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-September/020552.html") But it took untill Gutsy for them to do even a little.

I read the very long thread of emails. Your emails were very well written. Nice job, sir.

I have a 64-bit system, but for a long time I used 32-bit Ubuntu. I do have to say, however, that Gutsy is a huge improvement for 64-bit users. Now, we have Flash player, w64codecs, WINE, etc. A real improvement is coming. Still, there is till some things evident that prove 64-bit is not equal to 64-bit. Look at the Launchpad build farm. Although at this moment it is not the case, 64-bit builds virtually always lag behind 32-bit builds, sometimes by weeks (i.e. new flashplugin in hardy was built the next day for 32-bit, but took more than 10 days to be built for  64-bit). I think the second-class citizen now is Kubuntu (as it always has been), which is very lacking in comparison with Ubuntu.

---

### Post by code_linux on 2007-12-16
Thank you soo much. 
:)

---

### Post by cozadaman on 2007-12-17
ty for the leet hax lol.

---

### Post by iMMo on 2007-12-17
worked... now i can watch the highlights on youtube

thanks mate

---

### Post by kcy29581 on 2007-12-17
So in order to uninstall the flash player, is it simply a matter of deleting /usr/lib/firefox/plugins/npwrapper.libflashplayer.so? Or are there any other links that need to be dealt with?

---

### Post by Kilz on 2007-12-17
> **kcy29581 said:**
> So in order to uninstall the flash player, is it simply a matter of deleting /usr/lib/firefox/plugins/npwrapper.libflashplayer.so? Or are there any other links that need to be dealt with?

There are others, line the file that location symlinks to, but the script should uninstall all of them.

---

### Post by kcy29581 on 2007-12-17
> **Kilz said:**
> There are others, line the file that location symlinks to, but the script should uninstall all of them.

I must be crazy... so the script has an uninstall option as well?

---

### Post by Kilz on 2007-12-17
> **kcy29581 said:**
> I must be crazy... so the script has an uninstall option as well?

It attempts to remove old installs before it installs new files.

---

### Post by kcy29581 on 2007-12-18
> **Kilz said:**
> It attempts to remove old installs before it installs new files.

Ah, I see what you mean!

But what I am after (for future reference), is there a way to **automatically** remove the plugin via the script? I don't mean "update to the latest version of flash", I mean "remove flash completely".

---

### Post by Kilz on 2007-12-18
> **kcy29581 said:**
> Ah, I see what you mean!

But what I am after (for future reference), is there a way to **automatically** remove the plugin via the script? I don't mean "update to the latest version of flash", I mean "remove flash completely".

Delete the flash plugin files. Then uninstall nspluginwrapper.

---

### Post by drfox on 2007-12-18
I've followed your script and get this output:
Setting up nspluginwrapper (0.9.91.5-1ubuntu1) ...
--06:58:59--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.74.70
Connecting to fpdownload.macromedia.com|72.246.74.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

50% [=================>                   ] 3,036,127      1.85M/s             

06:59:01 (1.85 MB/s) - `install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
mv: cannot stat `/tmp/nsplugwrapper/install_flash_player_9_linux/flashplayer.xpt': No such file or directory
ln: target `/usr/lib/mozilla-firefox/plugins/' is not a directory: No such file or directory




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.

Note that there is no /usr/lib/mozilla-firefox/plugins directory. I have /usr/lib/mozilla and /usr/lib/firefox directories. 

After running the script, flash doesn't work in my browser.
What do I do next?

---

### Post by azbarcea on 2007-12-18
this script tries to move libflashplayer.so and other stuff to the firefox plugin directory ...

If the script failed ... is it because it assumed that the plugin directory is: /usr/lib/mozilla-firefox/plugins/, try to move the files manualy or modify the script with the real *firefox plugin* directory.

---

### Post by kcy29581 on 2007-12-18
> **Kilz said:**
> Delete the flash plugin files. Then uninstall nspluginwrapper.

Great, thanks for clarifying that.

---

### Post by Kilz on 2007-12-18
> **drfox said:**
> I've followed your script and get this output:
Setting up nspluginwrapper (0.9.91.5-1ubuntu1) ...
--06:58:59--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.74.70
Connecting to fpdownload.macromedia.com|72.246.74.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

50% [=================>                   ] 3,036,127      1.85M/s             

06:59:01 (1.85 MB/s) - `install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
mv: cannot stat `/tmp/nsplugwrapper/install_flash_player_9_linux/flashplayer.xpt': No such file or directory
ln: target `/usr/lib/mozilla-firefox/plugins/' is not a directory: No such file or directory




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.

Note that there is no /usr/lib/mozilla-firefox/plugins directory. I have /usr/lib/mozilla and /usr/lib/firefox directories. 

After running the script, flash doesn't work in my browser.
What do I do next?

Fixed in the newest version 1.8.3 uploaded today. The Gutsy section is new and used /usr/lib/mozilla-firefox but it was removed from Gutsy.

---

### Post by wakedizzle on 2007-12-19
THANK YOU, FINALLY GOT FLASH UP AND RUNNING!

i had to run the script from the terminal.  i'm running kubuntu 7.10 - AMD64 on a dual opteron workstation.

tested the plug-in at youtube.com.  player works with sound.

---

### Post by drfox on 2007-12-19
> **Kilz said:**
> Fixed in the newest version 1.8.3 uploaded today. The Gutsy section is new and used /usr/lib/mozilla-firefox but it was removed from Gutsy.

Thanks for the updated file, but I still don't see flash. I don't even see the black box I know should be there. I've disabled all my FF extensions and tried your utility again, but still no go. 

Here's my terminal output:: 

The following packages will be REMOVED:
  nspluginwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 377kB disk space will be freed.
(Reading database ... 90752 files and directories currently installed.)
Removing nspluginwrapper ...
dpkg - warning: while removing nspluginwrapper, directory `/usr/lib/nspluginwrapper/plugins' not empty so not removed.
dpkg - warning: while removing nspluginwrapper, directory `/usr/lib/nspluginwrapper' not empty so not removed.
rm: cannot remove `/usr/lib/nspluginwrapper/plugins': Is a directory
mkdir: cannot create directory `/tmp/nsplugwrapper': File exists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
The following NEW packages will be installed:
  nspluginwrapper
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/111kB of archives.
After unpacking 377kB of additional disk space will be used.
Selecting previously deselected package nspluginwrapper.
(Reading database ... 90729 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb) ...
Setting up nspluginwrapper (0.9.91.5-1ubuntu1) ...
--16:34:06--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.6.10.70
Connecting to fpdownload.macromedia.com|96.6.10.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

50% [=================>                   ] 3,036,127      1.30M/s             

16:34:08 (1.29 MB/s) - `install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
mv: cannot stat `/tmp/nsplugwrapper/install_flash_player_9_linux/flashplayer.xpt': No such file or directory
ln: creating symbolic link `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so' to `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': File exists




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.

---

### Post by luis.alves@lafaspot.com on 2007-12-19
If you using gutsy this should work with the lastest version of flash.
I just executed this in my machine and it works fine.
> 
# remove 
sudo apt-get remove -y nspluginwrapper

# find all old files
sudo updatedb ; locate flashplayer
# remove them from you system
sudo rm -f /usr/lib/mozilla/plugins/flashplayer.xpt
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/mozilla-firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins*
# remove all other files that locate finds

# install 
sudo apt-get -y install ia32-libs ia32-libs-gtk lib32asound2 nspluginwrapper
sudo wget -c [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
sudo tar -xzvf install_flash_player_9_linux.tar.gz
sudo mv -f ./install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
# stop and start all your browsers


---

### Post by Kilz on 2007-12-19
> **drfox said:**
> Thanks for the updated file, but I still don't see flash. I don't even see the black box I know should be there. I've disabled all my FF extensions and tried your utility again, but still no go. 



That sounds like a conflict of 2 plugins. 
please supply the results of
```
ls -al /usr/lib/mozilla/plugins
```
and 
```
ls -al /usr/lib/firefox/plugins
```

---

### Post by drfox on 2007-12-19
Kilz, thanks for your help. Before I could post the results of your list commands, I followed Luis' directions, and they worked fine.

I am certain that I had some weird extra setting like you suggested. People in this thread are obviously very happy with your script, so I thank you both, Luis and Kilz.

Larry

---

### Post by Kilz on 2007-12-20
> **drfox said:**
> Kilz, thanks for your help. Before I could post the results of your list commands, I followed Luis' directions, and they worked fine.

I am certain that I had some weird extra setting like you suggested. People in this thread are obviously very happy with your script, so I thank you both, Luis and Kilz.

Larry

Glad it helped, but Luis's script is basically the same as mine, I cant see any difference. Maybe it removed a file that was from an old install. Im going to have to do a side by side comparison.

---

### Post by drfox on 2007-12-20
> **Kilz said:**
> Glad it helped, but Luis's script is basically the same as mine, I cant see any difference. Maybe it removed a file that was from an old install. Im going to have to do a side by side comparison.

Actually, the key for me was the locate command...I didn't run his script in order. I ran the rm part, then went to each directory to see if there were any scraps of library files left. I did find 2 (sorry, don't remember which), removed then "by hand," then ran the install part of his script. HTH

Larry

---

### Post by Kilz on 2007-12-20
> **drfox said:**
> Actually, the key for me was the locate command...I didn't run his script in order. I ran the rm part, then went to each directory to see if there were any scraps of library files left. I did find 2 (sorry, don't remember which), removed then "by hand," then ran the install part of his script. HTH

Larry

That sounds like a common problem I mentioned earlier. People wanting Flash sometimes try 3 or 4 ways to get flash installed if they fail. The attempts often leave files that conflict. Thats why I asked for those 2 commands as they would give us a list of the contents of the plugins folders.

---

### Post by Bushido89 on 2007-12-20
Worked like a dream. THanks a million :)

---

### Post by apothecaryaaron on 2007-12-21
Script (from first post) worked perfectly for me first try on a fresh install.  Thanks!!!

---

### Post by caitscheverst on 2007-12-22
Script in the first post worked perfectly.

Many thanks, Kilz!

---

### Post by Ehtetur on 2007-12-22
I think the standard flash-nonfree script from the gutsy repos got fubarred..
Luckily I ran into your script, Now I got me flash install..
Much thanks Kilz!

---

### Post by scholzilla on 2007-12-23
I'm also a satisfied customer, but would like to add a note for dummies like me: You need to turn off NoScript, if you have it installed in firefox, before you can play back videos. Doh! Once I installed the script AND did that, everything worked just fine....THANKS!

---

### Post by &lt;sVERLo&gt; on 2007-12-23
Script download link on first post does not works :(
I was dreaming for flash workin on my gutsy 64 since ive installed it!!
Please help! :confused: :(

---

### Post by Kilz on 2007-12-23
> **<sVERLo> said:**
> Script download link on first post does not works :(
I was dreaming for flash workin on my gutsy 64 since ive installed it!!
Please help! :confused: :(

Run this command
```
locate libflashplayer.so
```
please post the results here.

---

### Post by JimBuntu on 2007-12-23
Installed perfectly, runs perfectly. Thanks

---

### Post by AK47Jazz on 2007-12-23
Thanks, works. Had to run it twice but it worked in the end, thank you very much.

---

### Post by toupeiro on 2007-12-23
I have somewhat of an interesting issue with this.  It works -- for a very brief second, then all the flash windows on a page go white.

OS: 7.10 64-bit

Browser = latest canonical repo version of firefox

There do not appear to be any broken links.


>  ls -al /usr/lib/mozilla/plugins
total 9396
drwxr-xr-x 2 root users    4096 2007-12-23 10:19 .
drwxr-xr-x 3 root root     4096 2007-10-15 16:27 ..
-rwxr-xr-x 1  501 users 8119784 2007-11-20 15:24 libflashplayer.so
-rw-r--r-- 1 root users  286688 2007-08-17 13:21 mplayerplug-in-dvx.so
-rw-r--r-- 1 root users    1021 2007-08-17 13:21 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root users  286688 2007-08-17 13:21 mplayerplug-in-qt.so
-rw-r--r-- 1 root users    1021 2007-08-17 13:21 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root users  286688 2007-08-17 13:21 mplayerplug-in-rm.so
-rw-r--r-- 1 root users    1021 2007-08-17 13:21 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root users  286680 2007-08-17 13:21 mplayerplug-in.so
-rw-r--r-- 1 root users  286688 2007-08-17 13:21 mplayerplug-in-wmp.so
-rw-r--r-- 1 root users    1021 2007-08-17 13:21 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root users    1021 2007-08-17 13:21 mplayerplug-in.xpt
lrwxrwxrwx 1 root users      60 2007-12-23 10:19 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

>  ls -al /usr/lib/firefox/plugins/
total 24
drwxr-xr-x 2 root root  4096 2007-12-23 10:19 .
drwxr-xr-x 5 root root  4096 2007-12-11 18:28 ..
-rw-r--r-- 1 root root 11456 2007-12-04 03:04 libunixprintplugin.so
lrwxrwxrwx 1 root root    43 2007-12-17 11:31 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root    44 2007-12-17 11:31 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 root root    42 2007-12-17 11:31 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2007-12-17 11:31 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2007-12-17 11:31 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2007-12-17 11:31 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2007-12-17 11:31 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2007-12-17 11:31 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2007-12-17 11:31 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2007-12-17 11:31 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root    27 2007-12-11 18:28 npica.so -> /usr/lib/ICAClient/npica.so
lrwxrwxrwx 1 root root    60 2007-12-23 10:19 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so



>   ls -al /tmp/nsplugwrapper
total 2984
drwxr-xr-x  3 root root     4096 2007-12-23 10:19 .
drwxrwxrwt 17 root root     4096 2007-12-23 10:19 ..
drwxr-xr-x  2  501 users    4096 2007-12-23 10:19 install_flash_player_9_linux
-rw-r--r--  1 root root  3036127 2007-11-29 13:23 install_flash_player_9_linux.tar.gz


---

### Post by Kilz on 2007-12-23
> **toupeiro said:**
> I have somewhat of an interesting issue with this.  It works -- for a very brief second, then all the flash windows on a page go white.

OS: 7.10 64-bit

Browser = latest canonical repo version of firefox

There do not appear to be any broken links.

The very last question the script asks is to type in your login. This is to set you as the owner of the plugins. Looking at your results you appear to have missed this step, that is unless you are root or 501.

---

### Post by SyCo123 on 2007-12-23
No Joy here on a HPDV5256 AMD Turion64. I tried gnash firefox default plugin install first with no result. Then gnash which half works ie its in about:plugins but won't play sites like anywhere.fm (which is what I would like). I uninstalled gnash and tried the script.

The script Appeard to complete without errors, asking for my username at the end but I don't have anything in about:plugins and no flash player at all installed now. 

Also
simon@simon-laptop:~$ locate libflashplayer.so
simon@simon-laptop:~$

Looks like its not there. Any ideas what wet wrong or what to try next? Not sure what else to post to help.

---

### Post by Kilz on 2007-12-23
> **SyCo123 said:**
> No Joy here on a HPDV5256 AMD Turion64. I tried gnash firefox default plugin install first with no result. Then gnash which half works ie its in about:plugins but won't play sites like anywhere.fm (which is what I would like). I uninstalled gnash and tried the script.

The script Appeard to complete without errors, asking for my username at the end but I don't have anything in about:plugins and no flash player at all installed now. 

Also
simon@simon-laptop:~$ locate libflashplayer.so
simon@simon-laptop:~$

Looks like its not there. Any ideas what wet wrong or what to try next? Not sure what else to post to help.

But the inability to locate the flash plugin is puzzling Open a terminal, navigate to the script, run it, then copy the install from the terminal to a post here.

---

### Post by soxs on 2007-12-24
> **SyCo123 said:**
> No Joy here on a HPDV5256 AMD Turion64. I tried gnash firefox default plugin install first with no result. Then gnash which half works ie its in about:plugins but won't play sites like anywhere.fm (which is what I would like). I uninstalled gnash and tried the script.

The script Appeard to complete without errors, asking for my username at the end but I don't have anything in about:plugins and no flash player at all installed now. 

Also
simon@simon-laptop:~$ locate libflashplayer.so
simon@simon-laptop:~$

Looks like its not there. Any ideas what wet wrong or what to try next? Not sure what else to post to help.

locate gets updated periodically, so if you install something, don't expect locate to find anything which was added by the installed programm. Use find instead.

---

### Post by SyCo123 on 2007-12-24
that's a good point I forgot about the update. 

So I ran
```
simon@simon-laptop:~$ sudo updatedb
simon@simon-laptop:~$ locate libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
simon@simon-laptop:~$
```

And it's in the plugin folder for mozilla so it shoudld be working right?

kilz would you still like the script output?

Here the about:plugins for firefox just prove I'm not crazy :)

```

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Totem Web Browser Plugin 2.20.0

    File name: libtotem-basic-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	ogg 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogg 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NSV video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	WMV video 	wms 	Yes
application/asx 	Playlist 	asx 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
Java(TM) Plug-in 1.6.0_03-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_03 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_03 	Java 		Yes

```


and heres some more info

```
simon@simon-laptop:~$ ls -al /usr/lib/mozilla/plugins
total 8040
drwxr-xr-x 2 simon users    4096 2007-12-23 16:36 .
drwxr-xr-x 3 root  root     4096 2007-10-15 17:23 ..
-rwxr-xr-x 1 simon users 8119784 2007-11-20 16:24 libflashplayer.so
lrwxrwxrwx 1 simon users      39 2007-12-23 15:26 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
-rw-r--r-- 1 simon users   43364 2007-08-30 16:46 libswfdecmozilla.a
-rw-r--r-- 1 simon users    1308 2007-08-30 16:46 libswfdecmozilla.la
-rw-r--r-- 1 simon users   35512 2007-08-30 16:46 libswfdecmozilla.so
lrwxrwxrwx 1 simon users      36 2007-12-22 11:49 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 simon users      37 2007-12-22 11:49 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 simon users      34 2007-12-22 11:49 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 simon users      35 2007-12-22 11:49 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 simon users      36 2007-12-22 11:49 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 simon users      37 2007-12-22 11:49 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 simon users      42 2007-12-22 11:49 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 simon users      43 2007-12-22 11:49 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 simon users      60 2007-12-23 16:36 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

So it's in there but it's not working. 

here's the other output requested in readme

```
simon@simon-laptop:~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 root root 4096 2007-12-23 16:36 .
drwxr-xr-x 5 root root 4096 2007-12-22 19:23 ..
lrwxrwxrwx 1 root root   39 2007-12-23 15:26 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root   36 2007-12-22 11:49 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   37 2007-12-22 11:49 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root   34 2007-12-22 11:49 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   35 2007-12-22 11:49 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root   36 2007-12-22 11:49 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   37 2007-12-22 11:49 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root   42 2007-12-22 11:49 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   43 2007-12-22 11:49 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 9104 2007-12-04 04:01 libunixprintplugin.so

```

```
simon@simon-laptop:~$ ls -al /tmp/nsplugwrapper
total 2984
drwxr-xr-x  3 root root     4096 2007-12-23 16:36 .
drwxrwxrwt 22 root root     4096 2007-12-24 14:25 ..
drwxr-xr-x  2  501 users    4096 2007-12-23 16:36 install_flash_player_9_linux
-rw-r--r--  1 root root  3036127 2007-11-29 14:23 install_flash_player_9_linux.tar.gz

```

I can't see anything  like /nspluginwrapper in /usr/lib/ so that got to be the problem. What should I do?

---

### Post by mastergunner on 2007-12-24
Mine is looking sort of like yours SyCo123.

---

### Post by Kilz on 2007-12-24
> **SyCo123 said:**
> 

```
simon@simon-laptop:~$ ls -al /usr/lib/mozilla/plugins
total 8040
drwxr-xr-x 2 simon users    4096 2007-12-23 16:36 .
drwxr-xr-x 3 root  root     4096 2007-10-15 17:23 ..
-rwxr-xr-x 1 simon users 8119784 2007-11-20 16:24 libflashplayer.so
lrwxrwxrwx 1 simon users      39 2007-12-23 15:26 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
-rw-r--r-- 1 simon users   43364 2007-08-30 16:46 libswfdecmozilla.a
-rw-r--r-- 1 simon users    1308 2007-08-30 16:46 libswfdecmozilla.la
-rw-r--r-- 1 simon users   35512 2007-08-30 16:46 libswfdecmozilla.so
lrwxrwxrwx 1 simon users      36 2007-12-22 11:49 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 simon users      37 2007-12-22 11:49 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 simon users      34 2007-12-22 11:49 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 simon users      35 2007-12-22 11:49 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 simon users      36 2007-12-22 11:49 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 simon users      37 2007-12-22 11:49 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 simon users      42 2007-12-22 11:49 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 simon users      43 2007-12-22 11:49 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 simon users      60 2007-12-23 16:36 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```


I can't see anything  like /nspluginwrapper in /usr/lib/ so that got to be the problem. What should I do?

You have 2 different flash plugins installed. This is a common problem. People try multiple things to get flash working. They install files that cause conflicts and then wonder why nothing ever works.

My script installs 
```
-rwxr-xr-x 1 simon users 8119784 2007-11-20 16:24 libflashplayer.so
and
lrwxrwxrwx 1 simon users      60 2007-12-23 16:36 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```
But this second set of flash plugins is causing a conflict.
```
-rw-r--r-- 1 simon users   43364 2007-08-30 16:46 libswfdecmozilla.a
-rw-r--r-- 1 simon users    1308 2007-08-30 16:46 libswfdecmozilla.la
-rw-r--r-- 1 simon users   35512 2007-08-30 16:46 libswfdecmozilla.so

```

---

### Post by mastergunner on 2007-12-24
So how do you get rif of the multiple installs?

---

### Post by jonathan@orion on 2007-12-24
I'm having some problems with Flash. I've run the script linked to in the first post on a clean install of Gutsy, and it appears to work fine on, say, youtube, when I first click on a video. However, shortly after it starts to play, if I do anything at all, firefox stalls out on me and I end up having to force it to quit.

ls -al /usr/lib/mozilla/plugins yields:
```
total 7956
drwxr-xr-x 2 jonathan users    4096 2007-12-24 23:20 .
drwxr-xr-x 3 root     root     4096 2007-10-15 19:27 ..
-rwxr-xr-x 1 jonathan users 8119784 2007-11-20 18:24 libflashplayer.so
lrwxrwxrwx 1 jonathan users      36 2007-12-24 21:50 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 jonathan users      37 2007-12-24 21:50 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 jonathan users      34 2007-12-24 21:50 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 jonathan users      35 2007-12-24 21:50 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 jonathan users      36 2007-12-24 21:50 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 jonathan users      37 2007-12-24 21:50 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 jonathan users      42 2007-12-24 21:50 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 jonathan users      43 2007-12-24 21:50 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 jonathan users      60 2007-12-24 23:20 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

ls -al /usr/lib/firefox/plugins yields:
```
total 24
drwxr-xr-x 2 root root  4096 2007-12-24 23:20 .
drwxr-xr-x 5 root root  4096 2007-12-24 23:05 ..
lrwxrwxrwx 1 root root    36 2007-12-24 21:50 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-12-24 21:50 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-12-24 21:50 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-12-24 21:50 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-12-24 21:50 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-12-24 21:50 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-12-24 21:50 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-12-24 21:50 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11456 2007-12-04 06:04 libunixprintplugin.so
lrwxrwxrwx 1 root root    60 2007-12-24 23:20 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

ls -al /tmp/nsplugwrapper yields:
```
total 2984
drwxr-xr-x  3 root root     4096 2007-12-24 23:20 .
drwxrwxrwt 15 root root     4096 2007-12-24 23:21 ..
drwxr-xr-x  2  501 users    4096 2007-12-24 23:20 install_flash_player_9_linux
-rw-r--r--  1 root root  3036127 2007-11-29 16:23 install_flash_player_9_linux.tar.gz
```

---

### Post by Ehtetur on 2007-12-24
> **mastergunner said:**
> So how do you get rif of the multiple installs?
You've got flash plugins from Kitz'ndispluginwrapper script and from swfdec-mozilla.
Remove the latter plugin and you should be good:
> sudo apt-get remove swfdec-mozilla

---

### Post by SyCo123 on 2007-12-26
I've run 

```
sudo apt-get remove swfdec-mozilla
```

And removed swfdec-mozilla Now the plugins folder looks like this


```
simon@simon-laptop:~$ ls -al /usr/lib/mozilla/plugins
total 7956
drwxr-xr-x 2 simon users    4096 2007-12-26 08:42 .
drwxr-xr-x 3 root  root     4096 2007-10-15 17:23 ..
-rwxr-xr-x 1 simon users 8119784 2007-11-20 16:24 libflashplayer.so
lrwxrwxrwx 1 simon users      39 2007-12-23 15:26 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 simon users      36 2007-12-22 11:49 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 simon users      37 2007-12-22 11:49 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 simon users      34 2007-12-22 11:49 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 simon users      35 2007-12-22 11:49 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 simon users      36 2007-12-22 11:49 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 simon users      37 2007-12-22 11:49 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 simon users      42 2007-12-22 11:49 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 simon users      43 2007-12-22 11:49 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 simon users      60 2007-12-23 16:36 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
simon@simon-laptop:~$  
```


I restarted firefox but sill no flash.

> You have 2 different flash plugins installed. This is a common problem. People try multiple things to get flash working. They install files that cause conflicts and then wonder why nothing ever works.

Yep, that pretty much me stumbling round Linux as best I can, :) 

Should I run the script again?

Also is there supposed to be a folder nspluginwrapper in /usr/lib/  I can't see one.

npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so


```
simon@simon-laptop:~$ cd /usr/lib
simon@simon-laptop:/usr/lib$ n
namei                                net                                  nmblookup
nameif                               netbug                               nm-tool
nano                                 netcat                               nohup
nautilus/                            netkit-ftp                           nologin
nautilus-cd-burner/                  netscsid                             nroff
nautilus-connect-server              netstat                              nslookup
nautilus-file-management-properties  network-admin                        nspluginscan
nautilus-sendto/                     newgrp                               nspluginviewer
nawk                                 newusers                             nstat
nc                                   ngettext                             nsupdate
ncal                                 nice                                 ntfs-3g
ncurses5-config                      nl                                   ntpdate
ncursesw5-config                     nm                                   ntpdate-debian
neqn                                 nm-applet
simon@simon-laptop:/usr/lib$ n                                     
```

---

### Post by jstritar on 2007-12-26
When I install Flash using this script on 64-bit ubuntu / firefox, npviewer.bin has a habit of using 100% cpu. I don't even have to play a video for it to occur... any ideas?

---

### Post by Kilz on 2007-12-26
> **SyCo123 said:**
> I've run 

```
sudo apt-get remove swfdec-mozilla
```

And removed swfdec-mozilla Now the plugins folder looks like this


```
simon@simon-laptop:~$ ls -al /usr/lib/mozilla/plugins
total 7956
drwxr-xr-x 2 simon users    4096 2007-12-26 08:42 .
drwxr-xr-x 3 root  root     4096 2007-10-15 17:23 ..
-rwxr-xr-x 1 simon users 8119784 2007-11-20 16:24 libflashplayer.so
lrwxrwxrwx 1 simon users      39 2007-12-23 15:26 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 simon users      36 2007-12-22 11:49 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 simon users      37 2007-12-22 11:49 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 simon users      34 2007-12-22 11:49 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 simon users      35 2007-12-22 11:49 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 simon users      36 2007-12-22 11:49 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 simon users      37 2007-12-22 11:49 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 simon users      42 2007-12-22 11:49 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 simon users      43 2007-12-22 11:49 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 simon users      60 2007-12-23 16:36 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
simon@simon-laptop:~$  
```


I restarted firefox but sill no flash.



Yep, that pretty much me stumbling round Linux as best I can, :) 

Should I run the script again?

Also is there supposed to be a folder nspluginwrapper in /usr/lib/  I can't see one.

npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so


```
simon@simon-laptop:~$ cd /usr/lib
simon@simon-laptop:/usr/lib$ n
namei                                net                                  nmblookup
nameif                               netbug                               nm-tool
nano                                 netcat                               nohup
nautilus/                            netkit-ftp                           nologin
nautilus-cd-burner/                  netscsid                             nroff
nautilus-connect-server              netstat                              nslookup
nautilus-file-management-properties  network-admin                        nspluginscan
nautilus-sendto/                     newgrp                               nspluginviewer
nawk                                 newusers                             nstat
nc                                   ngettext                             nsupdate
ncal                                 nice                                 ntfs-3g
ncurses5-config                      nl                                   ntpdate
ncursesw5-config                     nm                                   ntpdate-debian
neqn                                 nm-applet
simon@simon-laptop:/usr/lib$ n                                     
```

yes there should be a nspluginwrapper folder. I have made some adjustments to the script, try the new version.

---

### Post by Slimshady on 2007-12-26
Worked like a charm. Thanks alot kilz, i really needed it :)

---

### Post by killu on 2007-12-26
First i had some problems, found out i needed to install gsfonts-x11. Is it really weird I did not have this package already?

But now my update manager wants me to update my nspluginwrapper. I suppose I should not do this? How do I prevent my update manager to ask me this again/ everytime some other update is available?

Furthermore, what do you think that could be expected in the future? No more need of a script? For I really like 64 bit, and although I really appreciate this script, I would rather have it working out of the box ;)

Kilz, thx for the script

---

### Post by Kilz on 2007-12-26
> **killu said:**
> First i had some problems, found out i needed to install gsfonts-x11. Is it really weird I did not have this package already?

But now my update manager wants me to update my nspluginwrapper. I suppose I should not do this? How do I prevent my update manager to ask me this again/ everytime some other update is available?

Furthermore, what do you think that could be expected in the future? No more need of a script? For I really like 64 bit, and although I really appreciate this script, I would rather have it working out of the box ;)

Kilz, thx for the script

It was working out of the box for gutsy. The reason for this script is that the flasplugin-nonfree package is broken. It seems 64bit is low on the developers list for fixing issues.

---

### Post by SyCo123 on 2007-12-26
Kilz, I'm sorry... I properly screwed up. Went and downloaded the 1386 ISO not the 64. I've got to dl the right one and do a complete install again. At least I know where to come first for flash this time!

Thanks for continuing to give such great support to your script.

---

### Post by dohclude on 2007-12-27
Okay, I did a fresh install of Gutsy about a week ago. I used this script a couple of days ago and it worked great. My flash started working immediately after running it and it has been working all week up until today. I loaded a page on youtube (just like normal) and then there were no flash videos on the page at all. Anywhere that there was supposed to be a flash video... there was just nothing. I thought to myself, "Hrmmm, i guess I need to run the script again." So I closed firefox, then proceded to run the "GetFlash" script again. The script ran normally without any problems, and when I opened firefox to test things out, I get the "Additional Plugins Required" message at the top of the browser whenever I try to view a page with flash on it. I've tried re-running the script multiple times and I've searched and searched the net for a fix, but I just can't seem to get it working again. PLEASE HELP ME!

---

### Post by Kilz on 2007-12-27
> **dohclude said:**
> Okay, I did a fresh install of Gutsy about a week ago. I used this script a couple of days ago and it worked great. My flash started working immediately after running it and it has been working all week up until today. I loaded a page on youtube (just like normal) and then there were no flash videos on the page at all. Anywhere that there was supposed to be a flash video... there was just nothing. I thought to myself, "Hrmmm, i guess I need to run the script again." So I closed firefox, then proceded to run the "GetFlash" script again. The script ran normally without any problems, and when I opened firefox to test things out, I get the "Additional Plugins Required" message at the top of the browser whenever I try to view a page with flash on it. I've tried re-running the script multiple times and I've searched and searched the net for a fix, but I just can't seem to get it working again. PLEASE HELP ME!

Please read the first post on how to report problems. There is information you need to supply.

---

### Post by dohclude on 2007-12-27
Sorry about that, here you go:

 ls -al /usr/lib/mozilla/plugins

total 7956
drwxr-xr-x 2 chuck users    4096 2007-12-27 08:05 .
drwxr-xr-x 4 root  root     4096 2007-12-20 05:03 ..
-rwxr-xr-x 1 chuck users 8119784 2007-11-20 18:24 libflashplayer.so
lrwxrwxrwx 1 chuck users      36 2007-12-19 17:26 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 chuck users      37 2007-12-19 17:26 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 chuck users      34 2007-12-19 17:26 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 chuck users      35 2007-12-19 17:26 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 chuck users      36 2007-12-19 17:26 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 chuck users      37 2007-12-19 17:26 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 chuck users      42 2007-12-19 17:26 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 chuck users      43 2007-12-19 17:26 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 chuck users      60 2007-12-27 08:05 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so





ls -al /usr/lib/firefox/plugins

total 7968
drwxr-xr-x 2 chuck users    4096 2007-12-27 08:05 .
drwxr-xr-x 5 root  root     4096 2007-12-19 23:05 ..
-rwxr-xr-x 1 chuck users 8119784 2007-12-27 08:05 libflashplayer.so
lrwxrwxrwx 1 chuck users      36 2007-12-19 17:26 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 chuck users      37 2007-12-19 17:26 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 chuck users      34 2007-12-19 17:26 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 chuck users      35 2007-12-19 17:26 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 chuck users      36 2007-12-19 17:26 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 chuck users      37 2007-12-19 17:26 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 chuck users      42 2007-12-19 17:26 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 chuck users      43 2007-12-19 17:26 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 chuck users   11456 2007-12-04 06:04 libunixprintplugin.so
lrwxrwxrwx 1 chuck users      60 2007-12-27 08:05 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so




ls -al /tmp/nsplugwrapper

total 2984
drwxr-xr-x  3 root root     4096 2007-12-27 08:05 .
drwxrwxrwt 15 root root     4096 2007-12-27 08:09 ..
drwxr-xr-x  2  501 users    4096 2007-12-27 08:05 install_flash_player_9_linux
-rw-r--r--  1 root root  3036127 2007-11-29 16:23 install_flash_player_9_linux.tar.gz


The name of the file I downloaded is "nspluginwrapper-install-0-1.8.5.tar.gz"
I am running Ubuntu Gutsy Gibbon 7.10 amd64.

---

### Post by Kilz on 2007-12-27
Thanks for the info, does the /usr/lib/nspluginwrapper folder exist? Can you also look in synaptic/adept and tell me the version of nspluginwrapper.

---

### Post by dohclude on 2007-12-27
Yes that directory exists, and I have nspluginwrapper version 0.9.91.5-1ubuntu1 listed in synaptic

---

### Post by Kilz on 2007-12-27
Please try the new script that I just uploaded.

---

### Post by greeniguana00 on 2007-12-27
> **jstritar said:**
> When I install Flash using this script on 64-bit ubuntu / firefox, npviewer.bin has a habit of using 100% cpu. I don't even have to play a video for it to occur... any ideas?

Yeah, I'm having the same problem. It has gotten bad enough to cause firefox to hang. There is a thread about it here: [http://forums.fedoraforum.org/showthread.php?t=174927&page=1&pp=15](http://forums.fedoraforum.org/showthread.php?t=174927&page=1&pp=15)

I doubt it has anything to do with how this script installs flash.

---

### Post by Kilz on 2007-12-27
> **greeniguana00 said:**
> Yeah, I'm having the same problem. It has gotten bad enough to cause firefox to hang. There is a thread about it here: [http://forums.fedoraforum.org/showthread.php?t=174927&page=1&pp=15](http://forums.fedoraforum.org/showthread.php?t=174927&page=1&pp=15)

I doubt it has anything to do with how this script installs flash.

The script simply removes the occasional human error when following the install instructions. But one question, are either of you running  compiz, compiz fusion, beryl or any other desktop effects?

---

### Post by PowerlessRacing on 2007-12-27
Script installed great.  Thanks for your hard work and continuing support.  :)

I ran into one sneaky little problem that wasn't mentioned, and it could help people that think the script didn't work.  When I restarted my browser I clicked the "Restore Session" button as I often have multiple tabs open that I don't like to close (I come back to them later) in between reboots.  When I did this and went to youtube to test there was a spot for the video but no video loaded and no message came up telling me that I needed to install the flash player.  It was just blank space.  I bookmarked all my tabs, closed firefox and restarted, this time clicking "Start New Session" and then all Flash worked great.  I only mention this because after I installed the script and it "didn't work" I started looking at other ways to install Flash.  The idea came to me before I installed any of them, but it wouldn't necessarily be obvious as a fix to the problem.  If you could just make mention of it in your first post's step-by-step it might help somebody else that was having the same problem (which isn't really a problem at all).  Thanks again!

---

### Post by Kilz on 2007-12-27
> **PowerlessRacing said:**
> Script installed great.  Thanks for your hard work and continuing support.  :)

I ran into one sneaky little problem that wasn't mentioned, and it could help people that think the script didn't work.  When I restarted my browser I clicked the "Restore Session" button as I often have multiple tabs open that I don't like to close (I come back to them later) in between reboots.  When I did this and went to youtube to test there was a spot for the video but no video loaded and no message came up telling me that I needed to install the flash player.  It was just blank space.  I bookmarked all my tabs, closed firefox and restarted, this time clicking "Start New Session" and then all Flash worked great.  I only mention this because after I installed the script and it "didn't work" I started looking at other ways to install Flash.  The idea came to me before I installed any of them, but it wouldn't necessarily be obvious as a fix to the problem.  If you could just make mention of it in your first post's step-by-step it might help somebody else that was having the same problem (which isn't really a problem at all).  Thanks again!

Thanks for the info, I have added it to the problems section of the first post.
The script installs nspluginwrapper and flash according to the instructions on the nspluginwrapper site and the one other popular howto on the forums. Its funny that you mention trying other methods. Because the #1 most common reason the script doesn't work is because of people leaving the remains of past failed attempts in place. I guess its just a common human thing to try and get away from troubleshooting.

---

### Post by PowerlessRacing on 2007-12-27
Yeah, troubleshooting sucks.  I looked at the other methods but it bugs me to have tried something one way and not work.  I have no idea what that method may have left on my system.  Yours is the first and only way I tried.

The main reason I came back to your method is because of the support you've provided to others in this thread.  Sometimes I find people give a good howto but then won't answer questions when it doesn't work for others.  You're still actively posting here though, 55 pages later.  

Thanks again.  By the way, this was on an Intel Core 2 Duo, so it works on more than just AMD64.

---

### Post by xen on 2007-12-27
I seem to be having trouble downloading the script, is the link down for anyone else?

---

### Post by BillyC333 on 2007-12-27
Hello all, I am a newbie and first I would like to say thanks for the script! Second, I have a question after the script is run I can view all flash video fine but ubuntu alerts me that there is a update available for nspluginwrapper (0.9.91.5-lubuntu1 to 0.9.91.5-lubuntu1). Is this common? Thanks again.

Ubuntu 7.10 (64bit)

---

### Post by alexandreracine on 2007-12-27
Hi all, (and Kilz)

Did some of you try this?
[https://bugs.edge.launchpad.net/ubuntu/hardy/amd64/flashplugin-nonfree/9.0.115.0ubuntu2](https://bugs.edge.launchpad.net/ubuntu/hardy/amd64/flashplugin-nonfree/9.0.115.0ubuntu2)

It's for hardy (the 8.04 version of Ubuntu), but it does work for me for site like youtube. But when going to site like newgrounds.com, it does not work.


Kilz, the script you provide does not work for me :( I am using firefox...

l$ uname -a
Linux rouge 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux
[http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-1.tar.gz](http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-1.tar.gz)

$ ls -al /usr/lib/mozilla/plugins
total 7956
drwxr-xr-x 2 aracine users    4096 2007-12-27 18:07 .
drwxr-xr-x 3 root    root     4096 2007-10-15 19:27 ..
-rwxr-xr-x 1 aracine users 8119784 2007-11-20 18:24 libflashplayer.so
lrwxrwxrwx 1 aracine users      36 2007-12-24 08:19 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 aracine users      37 2007-12-24 08:19 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 aracine users      34 2007-12-24 08:19 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 aracine users      35 2007-12-24 08:19 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 aracine users      36 2007-12-24 08:19 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 aracine users      37 2007-12-24 08:19 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 aracine users      42 2007-12-24 08:19 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 aracine users      43 2007-12-24 08:19 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 aracine users      60 2007-12-27 18:07 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so



$ ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 root root  4096 2007-12-27 18:07 .
drwxr-xr-x 5 root root  4096 2007-12-24 20:09 ..
lrwxrwxrwx 1 root root    36 2007-12-24 08:18 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-12-24 08:18 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-12-24 08:18 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-12-24 08:18 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-12-24 08:18 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-12-24 08:18 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-12-24 08:18 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-12-24 08:18 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11456 2007-12-04 06:04 libunixprintplugin.so
lrwxrwxrwx 1 root root    60 2007-12-27 18:07 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

$ locate libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so

---

### Post by mastergunner on 2007-12-27
Kilz I think I downloaded the lates scrypt and ran it. I still do not have flash.

---

### Post by crjackson on 2007-12-27
disregard - 32-bit OS installed

---

### Post by crjackson on 2007-12-27
disregard - 32-bit OS installed

---

### Post by mastergunner on 2007-12-27
Kilz I just ran your new scrypt and I still have no flash. Can you help me figure this out. Thanks.

---

### Post by Kyran1 on 2007-12-27
Hi ya, I just noticed that after one installs your script, everything works. Then the update manager pops up to update the nspluginwrapper. once this is done your fix for flash hangs and or will not load the flash. the funny thing is, the version installed is the same as the one it is trying to update!?! is there any way to exclude the nspluginwrapper from updating?

Thanks

---

### Post by Kilz on 2007-12-28
> **Kyran1 said:**
> Hi ya, I just noticed that after one installs your script, everything works. Then the update manager pops up to update the nspluginwrapper. once this is done your fix for flash hangs and or will not load the flash. the funny thing is, the version installed is the same as the one it is trying to update!?! is there any way to exclude the nspluginwrapper from updating?

Thanks

Do not upgrade, rerun script. The package in the repos is broken.

---

### Post by Kilz on 2007-12-28
> **mastergunner said:**
> Kilz I just ran your new scrypt and I still have no flash. Can you help me figure this out. Thanks.

Please read the first post.

---

### Post by Kyran1 on 2007-12-28
> **Kilz said:**
> Do not upgrade, rerun script. The package in the repos is broken.

Yeah, I figured that after installing it. I fixed it anyways. Is there a way to remove the broken nspluginwrapper from the update manager? it constantly tells me there is an update (unwanted nspluginwrapper) and it's getting kinda annoying.

Oh, since you know how to code, I was wondering if you would be interested in the new sun java jre 1.7.0 binary? maybe you could make a plugin for the firefox 64 bit browser?

Thanks

---

### Post by mastergunner on 2007-12-28
Kilz I read the first post and still nothing. That is where I got the script from.

---

### Post by mastergunner on 2007-12-28
As per your instructions in the readme file. I am running Kubuntu 7.10amd64.

brad@brad-desktop:~$ ls -al /usr/lib/mozilla/plugins
total 7956
drwxr-xr-x 2 brad users    4096 2007-12-28 07:45 .
drwxr-xr-x 3 brad brad     4096 2007-12-27 20:53 ..
-rwxr-xr-x 1 brad users 8119784 2007-11-20 16:24 libflashplayer.so
lrwxrwxrwx 1 brad users      60 2007-12-28 07:45 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

brad@brad-desktop:~$ ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 root root  4096 2007-12-28 07:45 .
drwxr-xr-x 5 root root  4096 2007-12-27 19:43 ..
-rw-r--r-- 1 root root 11456 2007-12-04 04:04 libunixprintplugin.so
lrwxrwxrwx 1 root root    60 2007-12-28 07:45 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

brad@brad-desktop:~$ locate libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so


So can you tell me now why flash is not working? I am appreciate the help just a little frustrated thats all.

---

### Post by Kilz on 2007-12-28
> **mastergunner said:**
> Kilz I read the first post and still nothing. That is where I got the script from.

Please give me any steps you have done to get flash to work.
Also try
```
sudo chown -R brad:users /usr/lib/firefox/plugins
```

---

### Post by BillyC333 on 2007-12-28
The latest update to the script fixed the auto update trying to update to the same version. Thanks!! you rock :guitar:

---

### Post by Torqumada286 on 2007-12-28
Why isn't this particular thread stickied some place?  It is very helpful and solves a common problem for many people.

Torqumada

---

### Post by mastergunner on 2007-12-28
Kilz I just ran that command. Firefox asked to install a missing plugin which was Flash. It failed. I reran the scrypt and got the same request and it failed also. Now what?

---

### Post by Kilz on 2007-12-29
> **mastergunner said:**
> Kilz I just ran that command. Firefox asked to install a missing plugin which was Flash. It failed. I reran the scrypt and got the same request and it failed also. Now what?

Two things left that I can think of, please run this.
```
ls -al ~/.mozilla/plugins
```
next type ```
about:plugins
``` into the address bar, then tell me whats listed.

---

### Post by alexandreracine on 2007-12-29
ok, the script is working, but flash is not working on all situations...

FOR ALL PEOPLE WHO WANTS A 64BIT PLAYER, DO IT HERE

[http://www.adobe.com/go/wish](http://www.adobe.com/go/wish)

---

### Post by BenTyrer on 2007-12-29
Thankyou very much! Now I can catch up with my youtube subscriptions! :)

Woo, Go [Lemonette]("http://youtube.com/lemonette")! :popcorn:

---

### Post by nynoah on 2007-12-29
I am doing a fresh install of Gutsy.  I have installed this before and had no problem.  I just crashed my system a week ago and I am starting from scratch.   But I can not get my codecs for flash to work.  What has changed.  It worked fine when I installed in Nov.

Noah

---

### Post by nynoah on 2007-12-29
It works intermittent...........I have flash on youtube working.  But not on myspace.  I can not run more than one window of flash without out it locking up.  This was never a problem before.

Noah

---

### Post by Kilz on 2007-12-29
> **nynoah said:**
> It works intermittent...........I have flash on youtube working.  But not on myspace.  I can not run more than one window of flash without out it locking up.  This was never a problem before.

Noah


Its probably because of the new flash plugin that was released in early Dec. I personally use the old one because the new one doesn't work with the coke rewards site. I just added a script that installs the previous flash plugin in case anyone wants to use it instead.

---

### Post by mastergunner on 2007-12-29
Kilz for the command about:plugins it states no plug-ins found. I presume you wanted me to run the first sommand in terminal and this is what I get:
brad@brad-desktop:~$ ls -al ~/.mozilla/plugins
ls: /home/brad/.mozilla/plugins: No such file or directory

What is funny is I have run your scrypt twice so what gives?

---

### Post by Kilz on 2007-12-29
> **mastergunner said:**
> Kilz for the command about:plugins it states no plug-ins found. I presume you wanted me to run the first sommand in terminal and this is what I get:
brad@brad-desktop:~$ ls -al ~/.mozilla/plugins
ls: /home/brad/.mozilla/plugins: No such file or directory

What is funny is I have run your scrypt twice so what gives?

So after tryping ```
about:plugins
``` into the adress bar you get no plugins? Well at least it confirms that you have none.
At this poing Im not sure what else can be done. Everything is exactly as it should be, the files are in place. The wrapper is made. You have no conflicting plugins. It should work. Why its not is a mystery.

---

### Post by mastergunner on 2007-12-29
I got it to work but had to scew around with it. I noticed that there was nothing in Firefox plugins. So I moved a libflashplayer.so file into it. Then initiated this command:

nspluginwrapper -i /usr/lib/firefox/plugins/libflashplayer.so

---

### Post by Kilz on 2007-12-29
> **mastergunner said:**
> I got it to work but had to scew around with it. I noticed that there was nothing in Firefox plugins. So I moved a libflashplayer.so file into it. Then initiated this command:

nspluginwrapper -i /usr/lib/firefox/plugins/libflashplayer.so

The thing is, thats exactly what the script does. moves a plugin in place, and gives the nspluginwrapper -i /locaton/of/plugin command

---

### Post by mastergunner on 2007-12-29
Didnt do it for me for some reason.

---

### Post by nynoah on 2007-12-29
Kilz your latest change at the beginning of the post fixed my Flash issue.  I had to use the older version and now I am up and running correctly.   I wonder why this is happening?  Any ideas why the new one is not working right?

Noah

---

### Post by Kilz on 2007-12-30
> **mastergunner said:**
> Didnt do it for me for some reason.
Thats whats puzzeling and strange. A script that has worked for tons of people. That still works. That installed perfectly from what you reported. It gave you and you alone problems. What solves the problem? You, by doing exactly what the script does....... like I said very strange.

> **nynoah said:**
> Kilz your latest change at the beginning of the post fixed my Flash issue.  I had to use the older version and now I am up and running correctly.   I wonder why this is happening?  Any ideas why the new one is not working right?

Noah

Nope, other than the new version is useless for some sites. Flash is proprietary. Its owned by Adobe. They release and we use it. But we cant change it, neither do we have the source code. I just thought since I liked the old plugin, someone else would like to use it to.

---

### Post by grantjohnston on 2007-12-30
Alright, I've installed the 64 bit script provided, and my problem is, it works for a few times of using flash, then I have to reinstall it to get youtube videos (embedded or on youtube itself), beatport.com (flash driven mp3 site I'm a DJ, so I use that website extensively), the myspace image uploader, etc. Can anyone shed some light on as to why it does that?


Thanks


Grant

---

### Post by Kilz on 2007-12-30
> **grantjohnston said:**
> Alright, I've installed the 64 bit script provided, and my problem is, it works for a few times of using flash, then I have to reinstall it to get youtube videos (embedded or on youtube itself), beatport.com (flash driven mp3 site I'm a DJ, so I use that website extensively), the myspace image uploader, etc. Can anyone shed some light on as to why it does that?


Thanks


Grant

We might be able to, but you need to supply more information, please read the first post.

---

### Post by wingnux on 2007-12-30
> **grantjohnston said:**
> Alright, I've installed the 64 bit script provided, and my problem is, it works for a few times of using flash, then I have to reinstall it to get youtube videost

Same here! It works fine after installing but then sometime afterwards it doesn't (I didn't install/remove any package whatsoever) and then I have to reinstall it to get flash working again.

Also, apt insist that I run apt-get autoremove in order to uninstall the ndiswrapper package (what I don't do, of course).

---

### Post by nix4me on 2007-12-30
my 32bit firefox with 32bit plugins is crashing one in a while so i tried this approach with the stock 64bit gutsy firefox.

Result = firfox crash after watching a youtube video and switching away.  Happens every time.

---

### Post by Kilz on 2007-12-31
> **wingnux said:**
> Same here! It works fine after installing but then sometime afterwards it doesn't (I didn't install/remove any package whatsoever) and then I have to reinstall it to get flash working again.

Also, apt insist that I run apt-get autoremove in order to uninstall the ndiswrapper package (what I don't do, of course).

How old is the script you are running? What script are you running, the one that installs the newest flash plugin, or the previous one? Please read the fist post again.

> **nix4me said:**
> my 32bit firefox with 32bit plugins is crashing one in a while so i tried this approach with the stock 64bit gutsy firefox.

Result = firfox crash after watching a youtube video and switching away.  Happens every time.

Which version of thwe script did you install, the newest plugin, or the one that installs the previous one?

---

### Post by reseto on 2007-12-31
(1st post) Hi!
Version from 2007/12/29 (nspluginwrapper-install-0-1.8.5-3.tar.gz) doesn't work in Opera (64bit 9.50 Beta1) for me, but in FF 64 it's ok.
My Ubuntu is 7.10 GG, processor c2d e6550.
Did anyone manage to get it working in Opera? thx

Edit: I tried this sudo cp /usr/lib/firefox/plugins/npwrapper.libflashplayer.so /usr/lib/opera/plugins/ and it enabled sound of youtube videos !?!
 maybe there's only a few little steps to make it work

---

### Post by Kilz on 2007-12-31
> **reseto said:**
> (1st post) Hi!
Version from 2007/12/19 (nspluginwrapper-install-0-1.8.5-3.tar.gz) doesn't work in Opera (64bit 9.50 Beta1) for me, but in FF 64 it's ok.
My Ubuntu is 7.10 GG, processor c2d e6550.
Did anyone manage to get it working in Opera? thx

The script is not setup to install for Opera, I know little about the browser myself. Can Opera use other mozilla plugins? If so where does Opera store its plugins?

---

### Post by reseto on 2007-12-31
> I edited my previous post

the folder /usr/lib/opera/plugins is empty, but it's there by default,
I got the browser from here [ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/)
(build 1643)
if you have any ideas about what should i try, pls im me

---

### Post by Kilz on 2007-12-31
> **reseto said:**
> > I edited my previous post

the folder /usr/lib/opera/plugins is empty, but it's there by default,
I got the browser from here [ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/)
(build 1643)
if you have any ideas about what should i try, pls im me

You tried what I would have suggested.

---

### Post by nix4me on 2007-12-31
I used your newest script in post 1.

---

### Post by Kilz on 2007-12-31
> **nix4me said:**
> I used your newest script in post 1.

There are 2 scripts in post one.

---

### Post by nix4me on 2007-12-31
yes i know that. Click here if you want to download the script for r115 Flash plugin is the version that crashes everytime.

---

### Post by thekat on 2007-12-31
Kilz..
Silly question..
Does it matter if install flash (via your script -old flash per post # 1)
*before* I install Web browser plugins for 
i.e.
This page
[http://radar.weather.gov/radar.php?rid=TLX&product=NCR&overlay=11101111&loop=yes]("http://radar.weather.gov/radar.php?rid=TLX&product=NCR&overlay=11101111&loop=yes")

This plugin recommended for this page is the 
GCJ Web Browser Plugin (using IcedTea)

Note: My hardware is included in my Sig..

thx
tk

---

### Post by wingnux on 2007-12-31
> **Kilz said:**
> How old is the script you are running? What script are you running, the one that installs the newest flash plugin, or the previous one? Please read the fist post again
Which version of thwe script did you install, the newest plugin, or the one that installs the previous one?

I'm using this one: "Click here if you want to download the script for r115 Flash plugin." from 29/12, maybe I should try the older one?

EDIT: I don't think that "recommended" was there before, was it?

---

### Post by Kilz on 2007-12-31
> **wingnux said:**
> I'm using this one: "Click here if you want to download the script for r115 Flash plugin." from 29/12, maybe I should try the older one?

EDIT: I don't think that "recommended" was there before, was it?

Yes , I think trying the older plugin is a good idea. Recommended is recent, I have noticed a lot of issues with the new plugin. If someone wants to try it, go for it. But the r48 release at least works.

---

### Post by Kilz on 2007-12-31
> **thekat said:**
> Kilz..
Silly question..
Does it matter if install flash (via your script -old flash per post # 1)
*before* I install Web browser plugins for 
i.e.
This page
[http://radar.weather.gov/radar.php?rid=TLX&product=NCR&overlay=11101111&loop=yes]("http://radar.weather.gov/radar.php?rid=TLX&product=NCR&overlay=11101111&loop=yes")

This plugin recommended for this page is the 
GCJ Web Browser Plugin (using IcedTea)

Note: My hardware is included in my Sig..

thx
tk

No it wont make any difference. But be warned, that java plugin (icedtea) is not Sun java. It dosent work on all sites.

---

### Post by thekat on 2007-12-31
> 
No it wont make any difference. But be warned, that java plugin (icedtea) is not Sun java. It dosent work on all sites.


Thx for the response.. the IcedTea didn't work.. so I am off to find the
thread on getting Java to work on 64-bit..

Much Thanks for your script it worked great.. 

tk

---

### Post by Kilz on 2007-12-31
> **thekat said:**
> Thx for the response.. the IcedTea didn't work.. so I am off to find the
thread on getting Java to work on 64-bit..

Much Thanks for your script it worked great.. 

tk

There is no thread to get Sun Java working on 64bit. Java 7, still under development, will be the first Sun Java to have a 64bit plugin. Icedtea and Blackdown are open source java that dont work for all sites. You can of course install a [32bit browser and the 32bit java plugin]("http://ubuntuforums.org/showthread.php?t=202537") to your 64bit install.

---

### Post by ~LoKe on 2007-12-31
60...a little too much to read through.  I tried both installers and they appeared to be successful, however, I'm using the beta2 of Firefox 3.0, and despite the "successful" install, there's no flash plugin to be seen.  Do I need to create a symbolic link to/from somewhere in order to get it to work?

Thanks for your help.

**EDIT**: Nevermind.  Just copied the plugin from /var/lib/firefox/plugins to /var/lib/firefox-3.0-3.0b2/plugins.

---

### Post by cm690 on 2008-01-01
I have been struggled to get flash work without success. Your script works great. Thanks a lot.

AMD64 5200+ 2GBRAM Gusty

---

### Post by Spydr4590 on 2008-01-01
Thanks Kilz! You're a great resource to the Ubuntu community :)

---

### Post by TJUndead on 2008-01-02
Hi pal! Look, I try to download today the scripts to install here, but all links are wrong (the new one and the old one too).

Where I cant donwload this now?

Thanks. ^_^

---

### Post by tedk89 on 2008-01-02
way to go! fixed everything!

---

### Post by MangasColoradas on 2008-01-02
I cant download anything either, I tried this too (from here [http://ubuntuforums.org/showthread.php?t=656428](http://ubuntuforums.org/showthread.php?t=656428) ) ```
cd ~/ && wget http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz && tar xzvf nsplugin*.tar.gz && cd nsplugin*install && sudo ./GetFlash
``` , I assume the server is down?

---

### Post by ~LoKe on 2008-01-02
Yep, server is down.  I don't have the package to upload for anyone, either. :(

---

### Post by stuffelse on 2008-01-02
home.comcast... server's down? That's Comcastic! #-o

---

### Post by ~LoKe on 2008-01-03
It's back up.

---

### Post by cmf04 on 2008-01-03
I get page not found when I try 115

---

### Post by stuffelse on 2008-01-03
Ran the script and it completed, but it didn't appear to work. My only test was to go to youtube and have it tell me i don't have flash. Any suggestions?

---

### Post by cmf04 on 2008-01-03
It's downloading now, I will give it a try.

---

### Post by cmf04 on 2008-01-03
115 installed with no problems. Flash & sound now work perfectly. Thank you.

---

### Post by stuffelse on 2008-01-03
Note to self (and anyone else...)

Close Firefox COMPLETELY, BEFORE running the script...

r115 ran, installed, and works flawlessly. Thanks to Kilz!

---

### Post by MangasColoradas on 2008-01-03
Worked for me not long after I posted.

Thanks Kilz. :)

---

### Post by grantjohnston on 2008-01-03
> **Kilz said:**
> We might be able to, but you need to supply more information, please read the first post.

Alright, I'm using the r48 plug-in as of now and all is good. I'll post back in here if things get screwy again.

---

### Post by ubtpenguin on 2008-01-04
Server is down again. That is really comcastic. 
I hope I can try this script ASAP. 

Does anyone have a copy of script? 
:lolflag:

---

### Post by enoughsaid05 on 2008-01-04
Why can't I get my Flash working?

I have just installed ubuntu 7.1 gutsy

the outcome is as such

Install option (1-3)? :3
 Gutsy Gibbon 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mkdir: cannot create directory `/tmp/nsplugwrapper': File exists
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
--00:23:15--  [http://home.comcast.net/~ubuntume/flash.tar.gz](http://home.comcast.net/~ubuntume/flash.tar.gz)
           => `flash.tar.gz'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Unknown

    The file is already fully retrieved; nothing to do.

libflashplayer.so
--00:23:18--  [http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6_amd64.deb](http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6_amd64.deb)
           => `nspluginwrapper_0.9.91.6_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Unknown

    The file is already fully retrieved; nothing to do.

dpkg: status database area is locked by another process
sudo: nspluginwrapper: command not found




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.


Please help!!!!

Thanks

---

### Post by ~LoKe on 2008-01-04
Close Synaptic.

---

### Post by Kilz on 2008-01-04
> **ubtpenguin said:**
> Server is down again. That is really comcastic. 
I hope I can try this script ASAP. 

Does anyone have a copy of script? 
:lolflag:

Even if you could get a copy of the script, the script downloads deb files of mine from the same server.  Comcast is pretty reliable, they should be back up soon.

---

### Post by ~LoKe on 2008-01-04
I could host a mirror if you'd like.

---

### Post by ubtpenguin on 2008-01-04
> **Kilz said:**
> Even if you could get a copy of the script, the script downloads deb files of mine from the same server.  Comcast is pretty reliable, they should be back up soon.

Hey kilz why do you recommend older version of flash instead of newer one?

Thanks anyways
:guitar:

---

### Post by Kilz on 2008-01-04
> **ubtpenguin said:**
> Hey kilz why do you recommend older version of flash instead of newer one?

Thanks anyways
:guitar:


Because the new one is buggy, will not work on some sites ([http://www.mycokerewards.com](http://www.mycokerewards.com) being one) and some browsers have problems seeing it.  I do make the new one (r115) available in a script, but if any problems develop, please try the r48 plugin.

---

### Post by tbzep on 2008-01-05
Just installed 64bit gutsy a couple hours ago.  Just now used your script and got flash working first try.  Thanks for making it easy. :)

---

### Post by Harv on 2008-01-05
Worked as advertised.  Thank you Kilz.\\:D/

---

### Post by Rubruquis on 2008-01-05
works perfectly. thank you very much

---

### Post by ksujason on 2008-01-06
I tried running the script on my system with an AMD 64 processor and get these results. 
Flash still does not work.
Any suggestions?

Thanks.

Install option (1-3)? :3
 Gutsy Gibbon 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nspluginwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 377kB disk space will be freed.
(Reading database ... 88068 files and directories currently installed.)
Removing nspluginwrapper ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libflash-mozplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libflash0c2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libswfdec*
mkdir: cannot create directory `/tmp/nsplugwrapper': File exists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
--22:35:36--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.6.10.70
Connecting to fpdownload.macromedia.com|96.6.10.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

50% [=================>                   ] 3,036,127    311.04K/s    ETA 00:08

22:35:45 (356.54 KB/s) - `install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
--22:35:45--  [http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6_amd64.deb](http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6_amd64.deb)
           => `nspluginwrapper_0.9.91.6_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

Selecting previously deselected package nspluginwrapper.
(Reading database ... 88046 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.6_amd64.deb) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on ia32-libs (>= 1.6); however:
  Package ia32-libs is not installed.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.

---

### Post by tomdkat on 2008-01-07
Worked great!  Thanks!  :)

Peace...

---

### Post by dcstar on 2008-01-07
> **ksujason said:**
> I tried running the script on my system with an AMD 64 processor and get these results. 
Flash still does not work.
Any suggestions?

..........
Selecting previously deselected package nspluginwrapper.
(Reading database ... 88046 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.6_amd64.deb) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on ia32-libs (>= 1.6); [B]however:
  Package ia32-libs is not installed.[/B]
........

Installing the missing dependency may help.

---

### Post by Borbus on 2008-01-07
For some reason the Flash graphs in Google Analytics do not work with this... Any idea why?

---

### Post by Kilz on 2008-01-07
> **Borbus said:**
> For some reason the Flash graphs in Google Analytics do not work with this... Any idea why?

Nope, dose youtube work?

---

### Post by Borbus on 2008-01-07
Yeah, Youtube and every other Flash I have tried works fine. Just all the graphs on Google Analytics, except the pie charts for some reason...

---

### Post by crash0 on 2008-01-07
thanks, this works great! :)
i've tried gnash but sometimes it didn't work at all and other times the animations were broken and weird, but this one is good

---

### Post by GumbyX on 2008-01-07
Thanks for updating your script. I was having some issues with flash so I needed an updated version. One thing to throw out to people: For some reason I had nspluginwrapper-i386 installed (maybe from the old script or automatix?) that caused an install issue because it and nspluginwrapper share files and apt dpkg will not overwrite the files of another package. Maybe something to add to the script (removing the i368)? Anyway, hope this helps someone out if they had the same problem I did. Keep up the good work.

---

### Post by Kilz on 2008-01-08
> **GumbyX said:**
> Thanks for updating your script. I was having some issues with flash so I needed an updated version. One thing to throw out to people: For some reason I had nspluginwrapper-i386 installed (maybe from the old script or automatix?) that caused an install issue because it and nspluginwrapper share files and apt dpkg will not overwrite the files of another package. Maybe something to add to the script (removing the i368)? Anyway, hope this helps someone out if they had the same problem I did. Keep up the good work.

Thanks for the report, the script should have removed that package, ill check that its listed.

---

### Post by pranab on 2008-01-08
The script did not work for me. I get a lot Gtk, Glib, nspluginwrapper errors on the terminal. I started firefox from the terminal. 

Initially when I visit a flash page I get these:
> ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:18147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(npviewer.bin:18147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

The when I load the flash object I get these messages:

> (npviewer.bin:18281): GLib-GObject-WARNING **: IA__g_object_newv: construct property "bits-per-sample" for object `GdkPixbuf' can't be set twice

(process:18281): GLib-GObject-
(npviewer.bin:18281): GLib-GObject-WARNING **: IA__g_object_newv: construct property "has-alpha" for object `GdkPixbuf' can't be set twice

(npviewer.bin:18281): GLib-GObject-WARNING **: IA__g_object_newv: construct property "width" for object `GdkPixbuf' can't be set twice

(npviewer.bin:18281): GLib-GObject-WARNING **: IA__g_object_newv: construct property "height" for object `GdkPixbuf' can't be set twice

(npviewer.bin:18281): GLib-GObject-WARNING **: IA__g_object_newv: construct property "rowstride" for object `GdkPixbuf' can't be set twice

(npviewer.bin:18281): GLib-GObject-WARNING **: IA__g_object_newv: construct property "pixels" for object `GdkPixbuf' can't be set twice
*** NSPlugin Wrapper *** ERROR: NPP_Write() invoke: Connection reset by peer
*** NSPlugin Wrapper *** ERROR: NPP_DestroyStream() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()



Any idea as to what is wrong here. I get the qtengine.so error when I start acroread also. I have posted that elsewhere. But I think the problem here is deeper.

---

### Post by dcstar on 2008-01-08
This may be of interest for any people trying to get Flash working:

[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by Kilz on 2008-01-08
> **pranab said:**
> The script did not work for me. I get a lot Gtk, Glib, nspluginwrapper errors on the terminal. I started firefox from the terminal. 

Initially when I visit a flash page I get these:


The when I load the flash object I get these messages:




Any idea as to what is wrong here. I get the qtengine.so error when I start acroread also. I have posted that elsewhere. But I think the problem here is deeper.

You are going to have to give me some more information. The first post in this topic points you to the readme file that lists information needed. I also need to know what version you installed.

---

### Post by Kilz on 2008-01-08
> **dcstar said:**
> This may be of interest for any people trying to get Flash working:

[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

That post contains manual editing and information on how to do exactly what the script does. Anyone wanting to extract packages and edit files and then issue terminal commands is welcome to try it. Its also listed as solved, but it isnt for 64bit.

---

### Post by pranab on 2008-01-08
SOLVED. I installed the r48 version and it worked. flash plays in the browser with sound. r115 did not work for me. I should have taken your recommendation in the first place. The error regarding libartsc and libartsdsp still shows up on the terminal repeatedly but it has not crashed anything yet. I can still post the info you requested in the README if it will help.

---

### Post by or1onas on 2008-01-08
Great post, great help!
Works really fine!
Thanks a lot! :-D

---

### Post by Kilz on 2008-01-08
> **pranab said:**
> SOLVED. I installed the r48 version and it worked. flash plays in the browser with sound. r115 did not work for me. I should have taken your recommendation in the first place. The error regarding libartsc and libartsdsp still shows up on the terminal repeatedly but it has not crashed anything yet. I can still post the info you requested in the README if it will help.

As long as its working there is no need for the info.

---

### Post by ger_macaco on 2008-01-08
Hi, the script didn't work for me. It is probably because, as you say, previous attempts to install the plug-in may be causing some trouble.

However, I don't remember all the steps I tried to get this solved, so I wouldn't know where to check for them.

Any ideas?

---

### Post by ger_macaco on 2008-01-08
Sorry, forgot to attach this:

gerardo@pc-gerardo:~$ ls -al /usr/lib/mozilla/plugins
total 12
drwxr-xr-x 2 gerardo users   4096 2008-01-09 00:48 .
drwxr-xr-x 3 gerardo gerardo 4096 2008-01-09 00:48 ..
lrwxrwxrwx 1 gerardo users     60 2008-01-09 00:48 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
gerardo@pc-gerardo:~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 gerardo users  4096 2008-01-08 15:08 .
drwxr-xr-x 5 root    root   4096 2008-01-08 15:08 ..
-rw-r--r-- 1 gerardo users 11456 2007-12-04 08:04 libunixprintplugin.so
gerardo@pc-gerardo:~$ locate libflashplayer.so
/home/gerardo/.local/share/Trash/files/install_flash_player_9_linux/libflashplayer.so

I am running Kubuntu 7.10 and downloaded the script you recommended for Kubuntu.

Hope this helps.

---

### Post by Kilz on 2008-01-09
> **ger_macaco said:**
> Sorry, forgot to attach this:

gerardo@pc-gerardo:~$ ls -al /usr/lib/mozilla/plugins
total 12
drwxr-xr-x 2 gerardo users   4096 2008-01-09 00:48 .
drwxr-xr-x 3 gerardo gerardo 4096 2008-01-09 00:48 ..
lrwxrwxrwx 1 gerardo users     60 2008-01-09 00:48 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
gerardo@pc-gerardo:~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 gerardo users  4096 2008-01-08 15:08 .
drwxr-xr-x 5 root    root   4096 2008-01-08 15:08 ..
-rw-r--r-- 1 gerardo users 11456 2007-12-04 08:04 libunixprintplugin.so
gerardo@pc-gerardo:~$ locate libflashplayer.so
/home/gerardo/.local/share/Trash/files/install_flash_player_9_linux/libflashplayer.so

I am running Kubuntu 7.10 and downloaded the script you recommended for Kubuntu.

Hope this helps.

For some reason the script did not download the flash plugin. Can you please rerun the script by navigating to it in the terminal. You can even move the script file to the desktop then
```
cd ~/Desktop
./GetFlash
```
dont close the terminal, test for flash
If flash is not running copy the install info from the terminal to a post here.

---

### Post by Thyzer on 2008-01-09
I used the old one, and everything works now, from my iGoogle homepage to Youtube. THANK YOU!

---

### Post by ger_macaco on 2008-01-09
> **Kilz said:**
> For some reason the script did not download the flash plugin. Can you please rerun the script by navigating to it in the terminal. You can even move the script file to the desktop then
```
cd ~/Desktop
./GetFlash
```
dont close the terminal, test for flash
If flash is not running copy the install info from the terminal to a post here.

Working now. Many thanks for your help!!

---

### Post by Borbus on 2008-01-09
So, does anybody else use Google Analytics and can confirm the Flash graphs do not work?

---

### Post by nerderello on 2008-01-09
thanks mate, saved me a lot of heart ache (even started looking at buying Win Xp, and me a linux user since Redhat 7.3!).

thanks again

---

### Post by Kilz on 2008-01-09
> **Borbus said:**
> So, does anybody else use Google Analytics and can confirm the Flash graphs do not work?

Can you give me a link to a page that doesnt work for you?

---

### Post by Borbus on 2008-01-10
> **Kilz said:**
> Can you give me a link to a page that doesnt work for you?

Hmm.. not really, you need to have an Analytics account to use Analytics. If you have a website then you can set up Analytics for it if you want.

---

### Post by scottmoss on 2008-01-10
Many thanks for your efforts in producing these scripts.  Alas, it still doesn't work.

One problem must be that libflashplayer.so isn't found by locate.


Nspluginwrapper install script for Ubuntu AMD64 by Kilz


How to Install
==============
Close all browsers.
Extract the tar file you downloaded. 
It will create a folder. Open the folder.
Inside you will find the GetFlash script file

Double click on the GetFlash file. Select "Run In Terminal"

When the script has finished the terminal will close, then restart Firefox.

Troubleshooting
===============
If flash doesn't work. First please close all browsers. Then restart and test flash.
If flash still doesn't work please run this version of the script. It is the exact 
same script but does not clean up after itself.

WHICH VERSION OF THE SCRIPT?

When reporting problems please include the results of these commands. You can copy 
and paste them into a terminal one at a time. You do not have to type them. 

ls -al /usr/lib/mozilla/plugins

scott@ra:~$ ls -al /usr/lib/mozilla/plugins
total 7956
drwxr-xr-x 2 scott users    4096 2008-01-10 16:51 .
drwxr-xr-x 3 root  root     4096 2007-10-16 00:27 ..
-rwxr-xr-x 1 scott users 8119784 2007-11-20 23:24 libflashplayer.so
lrwxrwxrwx 1 scott users      36 2008-01-09 07:27 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 scott users      37 2008-01-09 07:27 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 scott users      34 2008-01-09 07:27 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 scott users      35 2008-01-09 07:27 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 scott users      36 2008-01-09 07:27 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 scott users      37 2008-01-09 07:27 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 scott users      42 2008-01-09 07:27 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 scott users      43 2008-01-09 07:27 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 scott users      60 2008-01-10 16:51 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

and 

ls -al /usr/lib/firefox/plugins

scott@ra:~$ ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 scott users  4096 2008-01-10 16:51 .
drwxr-xr-x 5 root  root   4096 2008-01-09 00:04 ..
lrwxrwxrwx 1 scott users    36 2008-01-09 07:26 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 scott users    37 2008-01-09 07:26 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 scott users    34 2008-01-09 07:26 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 scott users    35 2008-01-09 07:26 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 scott users    36 2008-01-09 07:26 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 scott users    37 2008-01-09 07:26 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 scott users    42 2008-01-09 07:26 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 scott users    43 2008-01-09 07:26 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 scott users 11456 2007-12-04 11:04 libunixprintplugin.so
lrwxrwxrwx 1 scott users    60 2008-01-10 16:51 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

and 

locate libflashplayer.so

nothing found

Also include the name of the file you downloaded, 

nspluginwrapper-install-0-1.8.5-3.tar.gz

What you are running (Ubuntu/Kubuntu/Xubuntu) 

Ubuntu 

and the version

7.10 (Gutsy) AMD64 on an intel core duo

---

### Post by ~LoKe on 2008-01-10
Google analytics "works", but it's kinda slow.

---

### Post by Kilz on 2008-01-10
> **scottmoss said:**
> Many thanks for your efforts in producing these scripts.  Alas, it still doesn't work.

One problem must be that libflashplayer.so isn't found by locate.


Nspluginwrapper install script for Ubuntu AMD64 by Kilz




please try the recommended install script ( r48 ) sometimes the (r115) has problems.

---

### Post by MrKappa on 2008-01-11
Very good! After long fighting now Flash is workin on Ubuntu 64 and AMD64 CPU.
Many thanks!!!!

---

### Post by Borbus on 2008-01-11
I can't remember which script I used before but I guess it was the r115 one... I just used the r48 one instead and now Google Analytics works fine.

---

### Post by pablosanchezuy on 2008-01-11
nice and simple. 

thanks. 

Pablo .

---

### Post by maverick14t on 2008-01-12
I am very new to this entire computer operating system world. i just recently installed ubuntu 7.04 onto my playstation 3 as a completely independent operating system. and everything was going great until i tried to install the flash player onto it. all of the updates and things of that nature have gone through smoothly. but i was getting confused as to how to navigate to the directory that i needed. i finally learned some different commands that i needed to, so that i could access it in my terminal. the online instructions go like this:
   1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.
the problem is that when i finally navigate to this directory, and then i type in this command to install it, it says this:

ERROR: Your architecture, \'ppc64\', is not supported by the
       Adobe Flash Player installer.
can anybody out there tell me if there is something that i am doing wrong? or give me some directions that actually work? it would be so highly appreciated. thank you so much whoever has an answer for me, that will actually work. please guys... i am so frustrated.

---

### Post by Kilz on 2008-01-12
> **maverick14t said:**
> 

ERROR: Your architecture, \'**ppc64**\', is not supported by the
       Adobe Flash Player installer.
can anybody out there tell me if there is something that i am doing wrong? or give me some directions that actually work? it would be so highly appreciated. thank you so much whoever has an answer for me, that will actually work. please guys... i am so frustrated.

According to the [Ubuntu Wiki ]("https://wiki.ubuntu.com/PowerPCFAQ#head-90cfbc097b16a084ab88177ad2e2296b0e17e527")there is no adobe Flash plugin that works with a ppc system. The problem is that Adobe Flash is proprietary and Adobe never created a flash plugin for ppc. The wiki post says gnash is your best bet.

---

### Post by chris062689 on 2008-01-15
The sites down!  Does anyone have a mirror?

---

### Post by Kilz on 2008-01-15
> **chris062689 said:**
> The sites down!  Does anyone have a mirror?

Please read the first post in this thread. There is no mirror.

---

### Post by cosmofed on 2008-01-15
Thanks KITZ. This was the only solution which worked for me. I tried all others. 

I'm 99% weened from Microsoft thanks to your efforts.

---

### Post by cangrejoinmortal on 2008-01-16
The plugin link does not work.

---

### Post by Kilz on 2008-01-16
> **cangrejoinmortal said:**
> The plugin link does not work.

Please read the first post completely.

---

### Post by vvinuv on 2008-01-16
Thanks you very much!! great work!

---

### Post by Stultis the Fool on 2008-01-16
This was the easiest installation ever! And worked great! Now, I can play Flash, YouTube, and GoogleVideo in Ubuntu Gutsy 64.

---

### Post by tibbar_eht on 2008-01-17
Dude you rock.  That last script finally made it work.  Now I just have to get my monitor to work with my DVI cable and I will be set.

Cheers

---

### Post by or1on on 2008-01-17
wrkd great ty very much

---

### Post by jc_madden on 2008-01-17
I had no problem installing the flash plugin on my desktop using 64 bit but no luck with GNASH or the official Adobe plugin on my laptop (Dell inspirion 1420).  Your script (old version) worked perfectly!  Thanks.  (Yes I clicked the thank you icon too.)

---

### Post by kosmos on 2008-01-17
Hi, I'd previously tried to get flash working on my Gutsy AMD64 machine, but was unable to get the nspluginwrapper to work consistently. This script (the oldflash-0.1.1) worked and now I can play flash.

However, the first time through the script it failed due to a conflict with my previous install attempt, and I had to figure out what the problem was.

The error I got during installation was:
-------------------------------------------
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.6_amd64.deb) ...
dpkg: error processing nspluginwrapper_0.9.91.6_amd64.deb (--install):
 trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer', which is also in package nspluginwrapper-i386
Errors were encountered while processing:
 nspluginwrapper_0.9.91.6_amd64.deb
sudo: nspluginwrapper: command not found
-------------------------------------------

So I removed the nspluginwrapper-i386 package, tried the script again, and it worked. I realize your instructions say to remove previous attempts, but I had long forgotten what I had tried to install and when. You might consider checking for this error in your script, at least to see if the dpkg command succeeds ok.

Anyway, now I'm up and running. Thanks.

---

### Post by durdensbuddy on 2008-01-17
Great Job!!  Thanks.  I had a lot of people trying to help me out over in the newb's section.  But nothing was working.  Thank you very much!

---

### Post by MountainX on 2008-01-18
Great work!! Very helpful. I tried a bunch of other solutions and I couldn't get YouTube videos to play correctly. This worked perfect! Thank you very much!

---

### Post by or1on on 2008-01-18
had to break the 666 replies :P

---

### Post by flyking on 2008-01-18
Worked perfectly...thankyou.  It took me several hours to get this issue solved trying other things that didn't work.  I had almost given up.

---

### Post by birofunk on 2008-01-20
it worked the first time I opened firefox after installation...but now when i got to view flash content i can't see anything....anybody got any ideas?

---

### Post by Kilz on 2008-01-20
> **birofunk said:**
> it worked the first time I opened firefox after installation...but now when i got to view flash content i can't see anything....anybody got any ideas?

Make sure you have no conflicting plugins installed.

---

### Post by SyCo123 on 2008-01-20
Just wanted to say thanks kilz, I've reinstall Ubuntu to the correct 64bit version and ran your script and it worked like a charm.

---

### Post by romeyde on 2008-01-20
> **Kilz said:**
> Make sure you have no conflicting plugins installed.

I've been fighting flash issues for a couple of weeks now.   Everything use to work fine but it all just stopped working on me.   For example, when I come across embedded youtube videos in google reader, I just see a black white area.   If I go directly to youtube and pick a video, again, nothing.

I just now tried reinstalling using "GetFlash" but now I see this in youtube:

"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

How would I go about identifying "conflicting plugins"?   I'd be happy to just wipe it all out and start from scratch, but not sure how to even make sure all the odd bits n pieces are gone before I do that.

---

### Post by Kilz on 2008-01-20
> **romeyde said:**
> I've been fighting flash issues for a couple of weeks now.   Everything use to work fine but it all just stopped working on me.   For example, when I come across embedded youtube videos in google reader, I just see a black white area.   If I go directly to youtube and pick a video, again, nothing.

I just now tried reinstalling using "GetFlash" but now I see this in youtube:

"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

How would I go about identifying "conflicting plugins"?   I'd be happy to just wipe it all out and start from scratch, but not sure how to even make sure all the odd bits n pieces are gone before I do that.

The thing is, that depending on what howto you have installed you could have gnash, swfdec, or some other plugin that I am not aware of. We can remove the plugins, but if the packages you have installed get updated you will be back in the same boat as the update will replace the plugins. So if you have installed a flash package you can remember you might want to uninstall it in synaptic.
Simply rerunning my install script is not going to help if you have conflicting plugins installed.
To start, please supply the results of 

```
ls -al /usr/lib/firefox/plugins
```
and 
```
ls -al /usr/lib/mozilla/plugins
```

These commands are in the troubleshooting section of the README file that comes with the script.

---

### Post by romeyde on 2008-01-20
<looking for conflicting plugins>

libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
libunixprintplugin.so

/usr/lib/mozilla/plugins
npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

thanks much for any assistance in figuring this out.   so many damn sites use and rely on flash these days.

---

### Post by romeyde on 2008-01-20
<more info>

Tried going to this site:  [http://blog.us.playstation.com/2008/01/16/pixeljunk-monsters-set-to-launch-next-week/](http://blog.us.playstation.com/2008/01/16/pixeljunk-monsters-set-to-launch-next-week/)  and was told that I was missing some plugins...   was given the option to install the non free flash adobe one and the gnash one.   The non free didn't make a diff after installing and restarting, just a blank white box still, installed gnash then and now I get a blank blue box instead of white.   Progress!  I guess.

Here's what's in those two dirs now:

ls -1 /usr/lib/firefox/plugins/
flashplugin-alternative.so
libtotem-basic-plugin.so
libtotem-basic-plugin.xpt
libtotem-gmp-plugin.so
libtotem-gmp-plugin.xpt
libtotem-mully-plugin.so
libtotem-mully-plugin.xpt
libtotem-narrowspace-plugin.so
libtotem-narrowspace-plugin.xpt
libunixprintplugin.so

ls -1 /usr/lib/mozilla/plugins
flashplugin-alternative.so
npwrapper.libflashplayer.so

....

Argh...    so, now, I can go directly to youtube.com and view videos, but, I can't view/see youtube videos that are embedded in other webpages.

....

Maybe it's a shockwave issue and most (?) embedded stuff uses shockwave?   I goto this adobe page and it shows flash being installed but not shockwave:
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

---

### Post by flick on 2008-01-20
Thanks, Kilz! Works great!

---

### Post by romeyde on 2008-01-20
ok...   didn't touch anything else and tried just installing the old version of the script.   hit a couple sites and so far, it all seems to be working again...    thanks much.   hopefully all will be good for another 3 months now.     (what a pain, not your script but the flippin number of hoops to jump through).

---

### Post by MountainX on 2008-01-21
I installed the nspluginswrapper on Gutsy64 and flash is working great. However, I saw romeyde's post about shockwave not working, so I went here:
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)
and I do not have the shockwave player. Is that expected? (At the playstation site romeyde posted, I also see the empty white box - but I got no message about missing plugins.)

Is it possible to get a shockwave player? The following thread left me confused:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=649546&highlight=shockwave](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=649546&highlight=shockwave)

---

### Post by MountainX on 2008-01-21
> **romeyde said:**
> ok...   didn't touch anything else and tried just installing the old version of the script.   hit a couple sites and so far, it all seems to be working again...    thanks much.   hopefully all will be good for another 3 months now.     (what a pain, not your script but the flippin number of hoops to jump through).

Is shockwave working for you?

---

### Post by doomsdaydave11 on 2008-01-21
Yes! thank you I love you! :)

EDIT: Does not play games. That's ok, Youtube and flash videos work fine. I just wanted to play a game of Mini Putt 2 though :|. Still, alot better then nothing, thanks man.

---

### Post by Kilz on 2008-01-21
There is no shockwave player/plugin for Linux, only flash. [You can see for yourselves.]("http://www.adobe.com/shockwave/download/alternates/")

---

### Post by Ymer on 2008-01-22
Thanks a lot, it worked like a charm on my system Fluxbuntu 7.10.

---

### Post by woknblues1 on 2008-01-22
thank you so much for this!!! your site is bookmarked!!:popcorn:

---

### Post by brendanpiater on 2008-01-23
Brilliant, worked like a charm for me!
AMD64 running Gutsy & Firefox

---

### Post by harry_vas on 2008-01-23
Thanks so much for the help.. I thought I would have to wait for linger time.. fortunately I found you code.. and it is working good for me.. your code uninstalled all the conflicting softwares!!!!

---

### Post by Monkey_84 on 2008-01-24
Thank you very much :) I'm a big fan of Gutsy, but the flash problem in the 64-bit version was really annoying. So many website uses some flash :s
Thanks again, it works perfectly :D

---

### Post by gambrjl on 2008-01-24
Worked beautifully.  Thanks a million

---

### Post by nicklikesfire on 2008-01-24
Links on page one are dead for me, Can anyone help me out with getting either install script?

---

### Post by Yellow Pasque on 2008-01-24
The links work fine for me, but I've attached the scripts to this post just to make sure you can get them.

---

### Post by nicklikesfire on 2008-01-24
> **Temüjin said:**
> The links work fine for me, but I've attached the scripts to this post just to make sure you can get them.

Wow, you are quick (It is now working for me, weird, maybe it was over bandwidth limits for a short period of time or something) ! Thanks so much, and thanks to kilz for the script!

---

### Post by Kilz on 2008-01-24
> **Temüjin said:**
> The links work fine for me, but I've attached the scripts to this post just to make sure you can get them.

Thanks, but, the scripts pull other files from the site that they are hosted on. So if someone cant get the script, they probably cant get those files and the install may fail.

---

### Post by AdHaR on 2008-01-25
i am running gutsy on amd64, with both firefox (2.0.0.6) and swiftfox installed.
first tried the older flash script (the one that says recommended)....did not work on either of the browsers.
next i tried the latest flash script, and flash worked with firefox but not swiftfox

does anyone know how I can get it working with swiftfox too?

btw thanks kilz for the scripts :)

---

### Post by Kilz on 2008-01-25
> **AdHaR said:**
> i am running gutsy on amd64, with both firefox (2.0.0.6) and swiftfox installed.
first tried the older flash script (the one that says recommended)....did not work on either of the browsers.
next i tried the latest flash script, and flash worked with firefox but not swiftfox

does anyone know how I can get it working with swiftfox too?

btw thanks kilz for the scripts :)

Nope, but [Swiftweasel ]("http://swiftweasel.tuxfamily.org/")works great.

---

### Post by parian on 2008-01-25
I'm new and having troubles. Ugh.

```
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on ia32-libs (>= 1.6); however:
  Package ia32-libs is not installed.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```

---

### Post by parian on 2008-01-25
I noticed I incorrectly enabled Universe repository, and I didn't reload the packages.

---

### Post by daradib on 2008-01-25
> **Kilz said:**
> Nope, but [Swiftweasel ]("http://swiftweasel.tuxfamily.org/")works great.

I think Swiftweasel is a smarter choice, as unlike Swiftfox, it is a completely free (as in speech) build of the Mozilla Firefox code, without proprietary graphics and license.There is a reason why it the repo used is "nonfree" as in:
```
deb http://getswiftfox.com/builds/debian unstable non-free
```
See the Wikipedia [Swiftfox Licensing]("http://en.wikipedia.org/wiki/Swiftfox#License") for more info.

Additionally, all Mozilla Firefox plugins, extensions, and themes are fully compatible with Swiftweasel (not all are compatible with Swiftfox). Sorry for being off topic, but I thought it was worth saying.

---

### Post by parian on 2008-01-25
Ut-oh. I lost sound after a reboot. Any thoughts?

---

### Post by ctw on 2008-01-26
Hi everybody,

Today I've installed two times de flash script and I have a little problem with [www.youtube.com](www.youtube.com).
I can't see any video and in the same page it comes:

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.

What I can do to solve it?

Thanks.

---

### Post by Kilz on 2008-01-26
> **ctw said:**
> Hi everybody,

Today I've installed two times de flash script and I have a little problem with [www.youtube.com](www.youtube.com).
I can't see any video and in the same page it comes:

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.

What I can do to solve it?

Thanks.

What other attempts to install flash or a flash alternative have you installed? what version of the script did you install r115 or r48?

---

### Post by MountainX on 2008-01-26
Problems with Google Finance flash charts in Firefox.

Flash is working for me in general. For example, YouTube works fine thanks to nspluginwrapper. 

However, dragging the Google finance graph is extremely slow and really can't be used. I don't have these problems in WIndows. I don't even have these problems when using terminal server client from Ubuntu to connect to the Windows machine.

Anyone else experience issues like this with the Google finance flash charts?

---

### Post by XPS600 on 2008-01-26
Kiltz - many thanks for making this so easy.  I just followed your directions, and it worked like a charm!

---

### Post by Kilz on 2008-01-26
> **MountainX said:**
> Problems with Google Finance flash charts in Firefox.

Flash is working for me in general. For example, YouTube works fine thanks to nspluginwrapper. 

However, dragging the Google finance graph is extremely slow and really can't be used. I don't have these problems in WIndows. I don't even have these problems when using terminal server client from Ubuntu to connect to the Windows machine.

Anyone else experience issues like this with the Google finance flash charts?

This thread deals mainly with getting flash to work. Not with specific problems with flash. I doubt anyone who could answer you is going to see your post on the 71st page. You might want to see if a separate post will get you your answer dealing with 64bit firefox. 
The only other thing I could suggest is installing the [32bit version of firefox ]("http://ubuntuforums.org/showthread.php?p=1174435")to see if it makes any difference by running the 32bit version. You might also report the bug to google and adobe to see if they can help.

---

### Post by ctw on 2008-01-27
Hi Kilz,
First I've installed a new ubuntu distro with the r115 Flash plugin. No happends nothing with the youtube videos.
Than I've installed again ubuntu with the r48 plugin and it was better. I can see in other webpages youtube videos but the oficial webpage of youtube doesn't works.

Maybe I've do it something wrong, but it's only to execute the script. 
I use Ubuntu 7.10 64bit.

Thanks

---

### Post by Kilz on 2008-01-27
> **ctw said:**
> Hi Kilz,
First I've installed a new ubuntu distro with the r115 Flash plugin. No happends nothing with the youtube videos.
Than I've installed again ubuntu with the r48 plugin and it was better. I can see in other webpages youtube videos but the oficial webpage of youtube doesn't works.

Maybe I've do it something wrong, but it's only to execute the script. 
I use Ubuntu 7.10 64bit.

Thanks

How many other ways have you tried to get flash to work? please list them.

---

### Post by ctw on 2008-01-27
Hi Again Kilz,

-1.The first time I do it with the option of firefox, than it ask you if you want to install the missing plugins and than it do it automatically. (The same that r48 plugin, you can see youtube videos in other webpages but not in [www.youtube.com](www.youtube.com))

-2.Than I've installed again the ubuntu distro with your script r115 Flash plugin.
Before I've don't use the firefox, I've updated only my system with the ubuntu update and later I run you script. I can't see any video.

-3.Later I've installed again fresh ubuntu distro and I did the same that before but only with your r48 plugin. 
For me it was the same of the point 1. I can see the videos in other pages but the oficial page of youtube comes with  " Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. "

If do you need some extra info I'll paste it.

Thanks in Advance

---

### Post by Kilz on 2008-01-27
> **ctw said:**
> Hi Again Kilz,

-1.The first time I do it with the option of firefox, than it ask you if you want to install the missing plugins and than it do it automatically. (The same that r48 plugin, you can see youtube videos in other webpages but not in [www.youtube.com](www.youtube.com))

-2.Than I've installed again the ubuntu distro with your script r115 Flash plugin.
Before I've don't use the firefox, I've updated only my system with the ubuntu update and later I run you script. I can't see any video.

-3.Later I've installed again fresh ubuntu distro and I did the same that before but only with your r48 plugin. 
For me it was the same of the point 1. I can see the videos in other pages but the oficial page of youtube comes with  " Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. "

If do you need some extra info I'll paste it.

Thanks in Advance

Please provide the results of 
```
ls -al /usr/lib/mozilla/plugins
```
and 
```
ls -al /usr/lib/firefox/plugins
```

Just copy them and past into a reply here.

---

### Post by ctw on 2008-01-27
Hi Kilz,




catworld@catworld-xpc:~$ ls -al /usr/lib/mozilla/plugins
total 6900
drwxr-xr-x 2 root     users    4096 2008-01-27 15:17 .
drwxr-xr-x 3 root     root     4096 2007-10-16 01:27 ..
-rwxr-xr-x 1 catworld users 7040036 2007-06-20 02:31 libflashplayer.so
lrwxrwxrwx 1 root     users      36 2008-01-27 12:36 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root     users      37 2008-01-27 12:36 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root     users      34 2008-01-27 12:36 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root     users      35 2008-01-27 12:36 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root     users      36 2008-01-27 12:36 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root     users      37 2008-01-27 12:36 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root     users      42 2008-01-27 12:36 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root     users      43 2008-01-27 12:36 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 root     users      60 2008-01-27 15:17 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so





catworld@catworld-xpc:~$ ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 root users  4096 2008-01-27 15:17 .
drwxr-xr-x 5 root root   4096 2008-01-27 13:06 ..
lrwxrwxrwx 1 root users    36 2008-01-27 12:36 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root users    37 2008-01-27 12:36 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root users    34 2008-01-27 12:36 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root users    35 2008-01-27 12:36 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root users    36 2008-01-27 12:36 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root users    37 2008-01-27 12:36 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root users    42 2008-01-27 12:36 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root users    43 2008-01-27 12:36 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root users 11456 2007-12-04 12:04 libunixprintplugin.so
lrwxrwxrwx 1 root users    60 2008-01-27 15:17 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so


At the momment I use your Old flash plugin. I can see the videosw in the other webpages but in [www.youtube.com](www.youtube.com) doesn't works.

Thanks

---

### Post by Darll on 2008-01-27
MAN!,What The Big Problem TO INSTALL FLASH9 IN AMD64!!!?

Just download the Mecromedia Flash 9 Source

Move the libflashplayer.so to /usr/lib32/firefox or /usr/lib64/mozilla/plugins/

and the run on it the command 
```
nspluginwrapper -i
```

THAT'S ALL THE STORY!!!!

WHY YOU NEED 71 PAGES!?!?!?!?!?!?!?!? :evil:

---

### Post by Kbeginner on 2008-01-27
Here is what I have in my Mozilla directory:
> 

-rwxr-xr-x 1   501 users 8119784 2007-11-20 18:24 libflashplayer.so

and for Firefox

> -rw-r--r-- 1 root root 11456 2007-12-04 06:04 libunixprintplugin.so

Also:

> /home/jxxxx/Desktop/flash-plugin-9.0.115.0/usr/lib/flash-plugin/libflashplayer.so
/home/jxxxx/Desktop/flash-plugin-9.0.115.0/debian/flash-plugin/usr/lib/flash-plugin/libflashplayer.so
/home/jxxxx/Desktop/install_flash_player_9_linux/libflashplayer.so

I can run Firefox however...I am a noob and don't know how to just "run from terminal" the scripts...

I basically download to Home, then try to manually run the scripts, and I always get problems at the end, i.e."

> nspluginwrapper: expected plugin(s) file name to install

---

### Post by goodyvn on 2008-01-27
First thanks for the script. I install its and it run smoothly with the flash but i still have no sound. I install ubuntu feisty , try either the scripts and sound in the frist page. These are the output 
root@trung-laptop:~# ls -al /usr/lib/mozilla/plugins
total 7956
drwxr-xr-x 2 root users    4096 2008-01-28 01:59 .
drwxr-xr-x 3 root root     4096 2007-04-15 18:58 ..
-rwxr-xr-x 1 root users 8119784 2007-11-21 06:24 libflashplayer.so
lrwxrwxrwx 1 root users      36 2007-12-02 07:40 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root users      37 2007-12-02 07:40 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root users      34 2007-12-02 07:40 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root users      35 2007-12-02 07:40 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root users      36 2007-12-02 07:40 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root users      37 2007-12-02 07:40 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root users      42 2007-12-02 07:40 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root users      43 2007-12-02 07:40 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 root users      60 2008-01-28 01:59 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

root@trung-laptop:~# ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 root root  4096 2008-01-28 01:59 .
drwxr-xr-x 6 root root  4096 2008-01-28 01:59 ..
lrwxrwxrwx 1 root root    36 2007-12-02 07:39 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-12-02 07:39 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-12-02 07:39 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-12-02 07:39 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-12-02 07:39 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-12-02 07:39 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-12-02 07:39 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-12-02 07:39 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2007-12-04 19:19 libunixprintplugin.so
lrwxrwxrwx 1 root root    60 2008-01-28 01:59 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
 
 Wait for your reply

---

### Post by Kilz on 2008-01-27
> **ctw said:**
> At the momment I use your Old flash plugin. I can see the videosw in the other webpages but in [www.youtube.com](www.youtube.com) doesn't works.

Thanks

Can you see the video news on this page? [http://www.reuters.com/news/video](http://www.reuters.com/news/video)

> **goodyvn said:**
> First thanks for the script. I install its and it run smoothly with the flash but i still have no sound. I install ubuntu feisty , try either the scripts and sound in the frist page.
Do you have sound in other applications?

---

### Post by Kbeginner on 2008-01-27
Can someone please help me with how to run this script?  I've tried typing it in manually but it won't work. 

I download to my desktop, but I don't have the option to "run in terminal".  It opens with Ark, which gives me the text of the script, but there's no option of right-clicking and then running.  

Thanks.

---

### Post by Kilz on 2008-01-27
> **Kbeginner said:**
> Can someone please help me with how to run this script?  I've tried typing it in manually but it won't work. 

I download to my desktop, but I don't have the option to "run in terminal".  It opens with Ark, which gives me the text of the script, but there's no option of right-clicking and then running.  

Thanks.

place the script file on the desktop
open the terminal and type in 
cd ~/Desktop
then 
./NameOfFile
You will have to edit the above command to match the script files name.

---

### Post by Kbeginner on 2008-01-27
Okay, please bear with me.  I'm almost there.  

I opened the script and saved it to the Desktop.  It saved as "GetFlash" but when i try ./GetFlash or ./getflash, it sasy no such file or directory....

---

### Post by goodyvn on 2008-01-27
Yes i have sound in other application as well, just don't have sound when watch video on youtube.com

---

### Post by Kilz on 2008-01-28
> **goodyvn said:**
> Yes i have sound in other application as well, just don't have sound when watch video on youtube.com

Do you get sound here [http://www.reuters.com/news/video](http://www.reuters.com/news/video)

> **Kbeginner said:**
> Okay, please bear with me.  I'm almost there.  

I opened the script and saved it to the Desktop.  It saved as "GetFlash" but when i try ./GetFlash or ./getflash, it sasy no such file or directory....
Please try it again and copy the entire try to a post from the start here if it errors.

---

### Post by goodyvn on 2008-01-28
I don't have sound in this web u tell

---

### Post by ctw on 2008-01-28
> **Kilz said:**
> Can you see the video news on this page? [http://www.reuters.com/news/video](http://www.reuters.com/news/video)


Do you have sound in other applications?


No Kilz, I can't see any video.

---

### Post by Script Warlock on 2008-01-28
> **Kilz said:**
> **[SIZE="4"][COLOR="Sienna"]Nspluginwrapper Install Script for Dapper-Gutsy(Updated 12/29/07)[/COLOR][/SIZE]**
This script will install the nspluginwrapper, and Flash for your 64bit browser for Dapper, Edgy and Feisty, and Gutsy. It will not install 
other plugins. There are other plugins, java being one, that nspluginwrapper can not work with. The script has been updated on 8/21/07. It no longer uses alien on Feisty, and it will clean out previous installs. I have also made a script that installs the old flash plugin that seems to work better than the new one. 
[Click here if you want to download the script for r115 Flash plugin.]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz")
or
[Click here for the script that installs the previous r48 plugin (recommended) (Strongly recommended for Kubuntu)]("http://home.comcast.net/~ubuntume/oldflash-0.1.1.tar.gz")

If the script works for you please consider clicking the thank you icon.  [[IMG]http://i9.photobucket.com/albums/a74/tghc/thanks.png[/IMG] ]("http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=3974162") 

Comcast will be doing maintaince to the servers that host my site on Jan 15th and 16th 2008. If you cant download the script or have problems running it on those days please try it later. The script does download a few other files from that site. 

Due to the problems with Flash and Gutsy the script has been modified to install flash and set it up for gutsy using the nspluginwrapper package in the Gutsy repo's.


The script also works with the 64bit builds of [Swiftweasel]("http://sourceforge.net/projects/swiftweasel/"), an optimized build of Firefox.


**[SIZE="4"][COLOR="Sienna"]Instructions[/COLOR][/SIZE]**
1. Download the script.
2. Right click on the tar.gz and select "Extract Here"
3. Close **all **browsers.
4. Inside the folder that extracts is a "GetFlash" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done.  :D

SD-Plissken has pointed out that users of the Fluxbox desktop may need to open a terminal and launch the script by navigating to it and using this command to launch the script.
```
sudo ./GetFlash
```
**[SIZE="4"][COLOR="Red"]How to get help (Please Read Before Making a Post)[/COLOR][/SIZE]**
If you have any problems and need help Please read the included README file for instructions on what information to report in your post. Do not repeatedly install the script or try other methods until you have read the sections below and made a post.

**[SIZE="4"][COLOR="Sienna"]Common Issues[/COLOR][/SIZE]**
[SIZE="3"]**Sound**[/SIZE]
First download and double click on [this package]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") to install it.

[SIZE="3"]**Sessions**[/SIZE]
Please make sure to start a new browser session if you run into any issues.

[SIZE="3"]**Other Flash Plugins. **[/SIZE]
If after installing the script you cant see flash. Make sure that all attempts at installing other flash plugins (Gnash, swfdec, etc)  have been uninstalled and the files they created have been removed. The remains of past failed attempts are the #1 cause of flash not working. This is because the files conflict with the flash plugin.

thanks very much kilz it works on my new 64 bit machine and its great to have you in this community..more power and more years to come

---

### Post by Kilz on 2008-01-28
> **ctw said:**
> No Kilz, I can't see any video.

What is the results of this?
```
ls -al /usr/lib/nspluginwrapper/plugins/
```
If you get a no such file error, does /usr/lib/nspluginwrapper exist?

> **goodyvn said:**
> I don't have sound in this web u tell

Did you install the extra sound package from the Common Issues section of the first post?

---

### Post by goodyvn on 2008-01-28
Yes i have installed its

---

### Post by Kilz on 2008-01-28
> **goodyvn said:**
> Yes i have installed its

Well that usealy solves the sound issues if people already have sound installed. Do you have ia32-libs installed? Can you hear sound from [apple trailers]("http://apple.com/trailers/") with the totem plugin?

---

### Post by ctw on 2008-01-28
> **Kilz said:**
> What is the results of this?
```
ls -al /usr/lib/nspluginwrapper/plugins/
```
If you get a no such file error, does /usr/lib/nspluginwrapper exist?



Did you install the extra sound package from the Common Issues section of the first post?



ls -al /usr/lib/nspluginwrapper/plugins/
total 84
drwxr-xr-x 2 catworld users     4096 2008-01-27 20:33 .
drwxr-xr-x 6 catworld catworld  4096 2008-01-27 20:33 ..
-rwxr-xr-x 1 root     users    70120 2008-01-27 20:33 npwrapper.libflashplayer.so

I have this.

---

### Post by Kilz on 2008-01-28
> **ctw said:**
> ls -al /usr/lib/nspluginwrapper/plugins/
total 84
drwxr-xr-x 2 catworld users     4096 2008-01-27 20:33 .
drwxr-xr-x 6 catworld catworld  4096 2008-01-27 20:33 ..
-rwxr-xr-x 1 root     users    70120 2008-01-27 20:33 npwrapper.libflashplayer.so

I have this.

Well it looks like everything is in place. Im starting to run out of things to check, do you have anything in ```
~/.mozilla/plugins/
```
and please give me the results of 
```
uname -a
```

---

### Post by ctw on 2008-01-28
> **Kilz said:**
> Well it looks like everything is in place. Im starting to run out of things to check, do you have anything in ```
~/.mozilla/plugins/
```
and please give me the results of 
```
uname -a
```


Hi kilz, and thanks to try to solve this problem

1./ uname -a


catworld@catworld-xpc:
Linux catworld-xpc 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux

2./ ~/.mozilla/plugins/

Insise i have a directory of firefox with:

[email]catworld@catworld-xpc:~/.mozi[/email]lla/firefox$ ls -la
total 20
drwx------ 3 catworld catworld 4096 2008-01-27 13:01 .
drwx------ 3 catworld catworld 4096 2008-01-27 13:00 ..
drwx------ 6 catworld catworld 4096 2008-01-28 18:23 imi0smeu.default
-rw------- 1 catworld catworld 2163 2008-01-28 18:11 pluginreg.dat
-rw-r--r-- 1 catworld catworld   94 2008-01-27 13:00 profiles.ini

---

### Post by Kilz on 2008-01-28
I have looked it over and cant see whats wrong. The last thing I can suggest is deleting

/usr/lib/mozilla/plugins
-rwxr-xr-x 1 catworld users 7040036 2007-06-20 02:31 libflashplayer.so
lrwxrwxrwx 1 root users 60 2008-01-27 15:17 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflas hplayer.so

/usr/lib/firefox/plugins
lrwxrwxrwx 1 root users 60 2008-01-27 15:17 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflas hplayer.so

and 
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

Then rerunning the r48 script.

---

### Post by Kbeginner on 2008-01-28
Just a quick word of thanks.  I finally figured out how to run scripts in terminal and flash works like a charm -- video and applications.  Very nice.

---

### Post by MountainX on 2008-01-28
Flash goes away!

I installed flash using the nspluginwrapper and everything seemed to be great. Then I installed some updates and flash was gone. I reran nspluginwrapper and flash was back to working. 

Then I rebooted and flash was gone again, so I had to run the nspluginwrapper again. Now it has just happened again after a reboot - flash is gone.

Is there a config file I need to edit? Anyone have an idea what's going on? Thanks.

---

### Post by MountainX on 2008-01-28
> **Kbeginner said:**
> Can someone please help me with how to run this script?  I've tried typing it in manually but it won't work. 

I download to my desktop, but I don't have the option to "run in terminal".  It opens with Ark, which gives me the text of the script, but there's no option of right-clicking and then running.  

Thanks.

For me, I just double click on the script. That opens up a dialog from which I can select "run in terminal".

---

### Post by Kbeginner on 2008-01-28
^^

Yes, I eventually saw that -- it's just there was a greyed-out box that I never saw before.  Once I did, it seemed to work (part of the problem is that it runs the script so fast, you don't know it's done before you  are back to a clean shell command)...in any event, I managed to do it. :)

---

### Post by Perfect Storm on 2008-01-29
I'm going to sticky this for awhile - it may reduce all the flash threads.

---

### Post by Zzzach on 2008-01-30
Ok I'm using the r48 version for now because the r115 version just shows grey boxes on google video (with sound). R48 works pretty good but I'm having a few minor problems: When I'm on google video, I can't fast forward at all... the video just restarts back at the beginning! It's driving me crazy. Does anyone know a way to fix this? I'm on 64-bit 7.10. :confused:

---

### Post by Throne777 on 2008-01-31
Thank Christ! It works perfectly! Much appreciation. I was gutted when Gnash wouldn't work for me, I thought I'd be stuck with no flash forever. Sometimes it's nice to be wrong :P

---

### Post by JG6_oddball on 2008-01-31
> **ctw said:**
> No Kilz, I can't see any video.

i had the same problem as you...i reran the script but instead of putting my user name at the end of the install I put "root" and now it works.


thnx kilz for your excellent work :)


S!

---

### Post by phidia on 2008-02-01
Excellant script-flash works perfectly now!! TY

---

### Post by Rohaq on 2008-02-01
So I ran this, it's installed, all seemed well, but I've found a problem: If I open one page that uses Flash, all is well, but as soon as another page is opened that uses flash, I get a grey box, and both Flash apps crash, requiring me to restart my browser to get flash working again.

This is getting annoying, can anyone help?

For the record:
Flash 9, installed using the script in this very thread.
Firefox 2.0.0.11 64-bit, en-GB
Ubuntu 7.10 64-bit

Cheers all!

---

### Post by Kilz on 2008-02-01
> **Rohaq said:**
> So I ran this, it's installed, all seemed well, but I've found a problem: If I open one page that uses Flash, all is well, but as soon as another page is opened that uses flash, I get a grey box, and both Flash apps crash, requiring me to restart my browser to get flash working again.

This is getting annoying, can anyone help?

For the record:
Flash 9, installed using the script in this very thread.
Firefox 2.0.0.11 64-bit, en-GB
Ubuntu 7.10 64-bit

Cheers all!

Which version of the scrit, there are 2 on the first post, did you install?

---

### Post by Rohaq on 2008-02-01
> **Kilz said:**
> Which version of the scrit, there are 2 on the first post, did you install?
Ah, the r115 plugin, sorry.

---

### Post by Kilz on 2008-02-01
> **Rohaq said:**
> Ah, the r115 plugin, sorry.

You might want to use the r48 plugin that has (recommended) right by it.

---

### Post by Rohaq on 2008-02-01
> **Kilz said:**
> You might want to use the r48 plugin that has (recommended) right by it.
Just tried it, same thing :(

---

### Post by Kilz on 2008-02-01
> **Rohaq said:**
> Just tried it, same thing :(

Please open a terminal and enter the following commands then provide
the results of the following
ls -al /usr/lib/mozilla/plugins/
and 
ls -al /usr/lib/firefox/plugins/

---

### Post by Rohaq on 2008-02-01
Here we go:

[quote="ls -al /usr/lib/mozilla/plugins/"]total 7956
drwxr-xr-x 2 <MYUSERNAME> users    4096 2008-02-01 16:38 .
drwxr-xr-x 3 root root     4096 2007-10-16 00:27 ..
-rwxr-xr-x 1 <MYUSERNAME> users 8119784 2007-11-20 23:24 libflashplayer.so
lrwxrwxrwx 1 <MYUSERNAME> users      39 2007-11-29 23:26 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 <MYUSERNAME> users      41 2008-01-07 00:04 libnpsoplugin.so -> ../../openoffice/program/libnpsoplugin.so
lrwxrwxrwx 1 <MYUSERNAME> users      36 2007-11-14 16:47 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 <MYUSERNAME> users      37 2007-11-14 16:47 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 <MYUSERNAME> users      34 2007-11-14 16:47 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 <MYUSERNAME> users      35 2007-11-14 16:47 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 <MYUSERNAME> users      36 2007-11-14 16:47 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 <MYUSERNAME> users      37 2007-11-14 16:47 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 <MYUSERNAME> users      42 2007-11-14 16:47 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 <MYUSERNAME> users      43 2007-11-14 16:47 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 <MYUSERNAME> users      60 2008-02-01 16:38 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so[/quote]

[quote="ls -al /usr/lib/firefox/plugins/"]total 24
drwxr-xr-x 2 <MYUSERNAME> users  4096 2008-02-01 16:38 .
drwxr-xr-x 5 root root   4096 2008-01-31 02:11 ..
lrwxrwxrwx 1 <MYUSERNAME> users    39 2007-11-29 23:26 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 <MYUSERNAME> users    41 2008-01-07 00:04 libnpsoplugin.so -> ../../openoffice/program/libnpsoplugin.so
lrwxrwxrwx 1 <MYUSERNAME> users    36 2007-11-14 16:47 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 <MYUSERNAME> users    37 2007-11-14 16:47 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 <MYUSERNAME> users    34 2007-11-14 16:47 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 <MYUSERNAME> users    35 2007-11-14 16:47 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 <MYUSERNAME> users    36 2007-11-14 16:47 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 <MYUSERNAME> users    37 2007-11-14 16:47 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 <MYUSERNAME> users    42 2007-11-14 16:47 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 <MYUSERNAME> users    43 2007-11-14 16:47 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 <MYUSERNAME> users 11456 2007-12-04 11:04 libunixprintplugin.so
lrwxrwxrwx 1 <MYUSERNAME> users    60 2008-02-01 16:38 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
[/quote]

---

### Post by Kilz on 2008-02-01
I think I see a few issues here. 
The line 
-rwxr-xr-x 1 <MYUSERNAME> users 8119784 2007-11-20 23:24 libflashplayer.so
Tells me that you still have the r115 plugin installed. Please delete the file
```
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
```
and rerun the r48 script. 


Secondly, Is the name you sign on to your computer  <MYUSERNAME> ? If not open a terminal and enter the following commands. You will have to edit them. Replace PlaceNameHere with the name you login with.

```
sudo chown -R PlaceNameHere:users 
sudo chown -R PlaceNameHere:users /usr/lib/firefox/plugins/
```

---

### Post by Rohaq on 2008-02-01
You sir, are made of win.

Looks like I still had r115 installed, removing and then reinstalling it worked a treat, thanks :)

---

### Post by rudlavibizon on 2008-02-01
Hi, I just installed 64bit Gutsy for the first time running a 64 bit OS. I'm wondering which option is better, the one in this thread or installing the 32 bit browser but mostly is it sane to try both at the same time and see which is better for myself? 

PS. Running a script to install Swiftweasel right now, haven't tried nspliginwrapper. :)

---

### Post by Kilz on 2008-02-01
> **rudlavibizon said:**
> Hi, I just installed 64bit Gutsy for the first time running a 64 bit OS. I'm wondering which option is better, the one in this thread or installing the 32 bit browser but mostly is it sane to try both at the same time and see which is better for myself? 

PS. Running a script to install Swiftweasel right now, haven't tried nspliginwrapper. :)

It all depends on if you need java or not, and if the icedtea plugin will work for the sites you need java for. If it will the 64bit browser is the way to go. By the way Swiftweasel also has 64bit builds.

---

### Post by rudlavibizon on 2008-02-01
But it is safe to try both, I mean they wont conflict?

---

### Post by Kilz on 2008-02-01
> **rudlavibizon said:**
> But it is safe to try both, I mean they wont conflict?

Its safe , they share no files.

---

### Post by rudlavibizon on 2008-02-01
Kool. :)

---

### Post by astyler on 2008-02-01
Hi, I have not been able to get this to work.

First I downloaded the Adobe flashplayer and tried
sudo cp libflash... /usr/lib/firefox/plugins/

But that did not work.  I removed that file.

Then I tried your old script, that did not work.
I didn't remove any files and tried the new script -- no luck.
Then, I checked /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins  and removed libflashplayer.so and npwrapper.libflashplayer.so (i think that is what it is called)

After the directories were clear (except maybe a print library, I installed the old script again with no luck!

I'm on a fresh install of Gutsy Gibbon and using Firefox that came with it (I'm assuming 64 bit firefox)

I am running an AMD64 install.

I ran those scripts and here is my current output:
ls -al /usr/lib/mozilla//plugins/
drwxr-xr-x 2 styler users  4096 2008-02-01 16:39 .
drwxr-xr-x 3 styler styler 4096 2008-02-01 16:39 ..
lrwxrwxrwx 1 styler users    60 2008-02-01 16:39 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

ls -al /usr/lib/firefox/plugins/
drwxr-xr-x 2 styler users  4096 2008-02-01 16:39 .
drwxr-xr-x 3 styler styler 4096 2008-02-01 16:39 ..
lrwxrwxrwx 1 styler users    60 2008-02-01 16:39 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so


This is the complete output, as this is a pretty fresh install!  Am I missing something?
(I installed with tar zxf oldflash-0.1.1.tar.gz then /nspluginwrapper\ install/./GetFlash, selected 3 for Gutsy Gibbon

---

### Post by Kilz on 2008-02-01
> **astyler said:**
> Hi, I have not been able to get this to work.


open synaptic, search for nspluginwrapper, tell me what the installed version is from the installed version column.

---

### Post by astyler on 2008-02-01
Installed version is 0.9.91.6-1ubuntu1

---

### Post by Kilz on 2008-02-01
> **astyler said:**
> Installed version is 0.9.91.6-1ubuntu1

Thats good news, please rerun the r48 script and if flash does not work after restarting your browser please post with the results of ls -al /usr/lib/mozilla//plugins/.

---

### Post by trailrunner13 on 2008-02-01
That worked great! :) Since Flash is so common, I find it surprising this issue hasn't been solved programmatically by the Ubuntu dev community, but I'm grateful you figured this out and put it forth for us mere mortals.

---

### Post by astyler on 2008-02-01
Worked great Kilz, guess I just had to run the script again (maybe my browser didn't close out completely).  

Thanks for your help and script!

---

### Post by MountainX on 2008-02-01
My flash stops working every time I reboot or restart X.

I installed flash using the nspluginwrapper and everything seemed to be great. Then I installed some updates and flash was gone. I reran nspluginwrapper and flash was back to working.

Then I rebooted and flash was gone again, so I had to run the nspluginwrapper again. Now it has just happened again after a reboot - flash is gone.

UPDATE: I experimented a bit, and all I have to do is run the following command to restore flash functionality:
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

Is there a config file I need to edit? Anyone have an idea what's going on? Why does flash always stop working after I restart my computer?

Thanks.

uname -a
Linux MyServer 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux

locate libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so

---

### Post by Kilz on 2008-02-02
> **MountainX said:**
> My flash stops working every time I reboot or restart X.

I installed flash using the nspluginwrapper and everything seemed to be great. Then I installed some updates and flash was gone. I reran nspluginwrapper and flash was back to working.



please give me the results of the following
ls -al /usr/lib/mozilla//plugins/
ls -al /usr/lib/firefox/plugins/
ls -al /usr/lib/nspluginwrapper/plugins

---

### Post by MountainX on 2008-02-02
> **Kilz said:**
> please give me the results of the following
ls -al /usr/lib/mozilla//plugins/
ls -al /usr/lib/firefox/plugins/
ls -al /usr/lib/nspluginwrapper/plugins

Thank you. Here is the info:
```

ls -al /usr/lib/mozilla/plugins
total 7956
drwxr-xr-x 2 username users    4096 2008-01-26 18:12 .
drwxr-xr-x 3 root         root     4096 2008-01-20 10:24 ..
-rwxr-xr-x 1 username users 8119784 2007-11-20 18:24 libflashplayer.so
lrwxrwxrwx 1 username users      36 2008-01-20 10:24 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 username users      37 2008-01-20 10:24 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 username users      34 2008-01-20 10:24 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 username users      35 2008-01-20 10:24 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 username users      36 2008-01-20 10:24 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 username users      37 2008-01-20 10:24 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 username users      42 2008-01-20 10:24 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 username users      43 2008-01-20 10:24 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 username users      60 2008-01-26 18:12 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so


ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 username users  4096 2008-01-26 18:12 .
drwxr-xr-x 5 root         root   4096 2008-01-20 22:29 ..
lrwxrwxrwx 1 username users    36 2008-01-20 10:24 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 username users    37 2008-01-20 10:24 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 username users    34 2008-01-20 10:24 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 username users    35 2008-01-20 10:24 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 username users    36 2008-01-20 10:24 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 username users    37 2008-01-20 10:24 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 username users    42 2008-01-20 10:24 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 username users    43 2008-01-20 10:24 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 username users 11456 2007-12-04 06:04 libunixprintplugin.so
lrwxrwxrwx 1 username users    60 2008-01-26 18:12 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

ls -al /usr/lib/nspluginwrapper/plugins
total 84
drwxr-xr-x 2 username users         4096 2008-01-26 18:12 .
drwxr-xr-x 6 username username  4096 2008-01-26 18:12 ..
-rwxr-xr-x 1 username users        70120 2008-01-28 17:47 npwrapper.libflashplayer.so

locate libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
```

---

### Post by Kilz on 2008-02-02
> **MountainX said:**
> Thank you. Here is the info:


You are running the r115 version of the plugin. It is not recommended. Run the following commands, close the browser and run the r48 script.

```
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by tgeorge on 2008-02-02
Its not likely that I could thank you enough!!! I tried installing the R115 plugin with serious issues. For instance, [www.nakedalarmclock.com](www.nakedalarmclock.com) (its just an alarm clock, not pornographic) would not work. That was bad because I rely on that to wake up each morning. Many flash sites would work, while many would not. For example, [www.projectplaylist.com](www.projectplaylist.com) would play songs, but would show ONLY a grey box for the flash video. I tried installing R48 last week and the link was broken. Just tried again today (up to my neck in frustration) and the link worked. I Closed SwiftWeasel, ran the script, and once finished I reopened the browser. A quick navigation to nakedalarmclock.com confirmed that it worked! THANK YOU SO MUCH! if you have a paypal account ;), please send me a private message. 

:guitar:

---

### Post by Bif Powell on 2008-02-02
New install of Gutsy
AMD64

Closed all browser windows
Downloaded the first script
Ran it
Selected Run in Terminal
Choose option 3 (Gutsy)
It ran with a lot of output
I read and followed the instruction to enter my username and hit enter
The window went away

Flash still does not work
If I search for nspluginwrapper in Synaptic I get no results

Here is the output of ls -al /yadda/yadda

johnm@johnm-desktop:~$ ls -al /usr/lib/mozilla/plugins
total 6900
drwxr-xr-x 2 johnm users    4096 2008-02-02 14:18 .
drwxr-xr-x 3 root  root     4096 2007-10-15 18:23 ..
-rwxr-xr-x 1 johnm users 7040036 2007-06-19 19:31 libflashplayer.so
lrwxrwxrwx 1 johnm users      36 2008-02-02 02:02 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 johnm users      37 2008-02-02 02:02 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 johnm users      34 2008-02-02 02:02 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 johnm users      35 2008-02-02 02:02 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 johnm users      36 2008-02-02 02:02 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 johnm users      37 2008-02-02 02:02 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 johnm users      42 2008-02-02 02:02 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 johnm users      43 2008-02-02 02:02 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 johnm users      60 2008-02-02 14:18 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
johnm@johnm-desktop:~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 johnm users 4096 2008-02-02 09:09 .
drwxr-xr-x 5 root  root  4096 2008-02-02 09:09 ..
lrwxrwxrwx 1 johnm users   36 2008-02-02 02:01 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 johnm users   37 2008-02-02 02:01 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 johnm users   34 2008-02-02 02:01 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 johnm users   35 2008-02-02 02:01 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 johnm users   36 2008-02-02 02:01 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 johnm users   37 2008-02-02 02:01 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 johnm users   42 2008-02-02 02:01 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 johnm users   43 2008-02-02 02:01 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 johnm users 9104 2007-12-04 05:01 libunixprintplugin.so

Many thanks for any guidance.

Bif

---

### Post by Kilz on 2008-02-02
> **Bif Powell said:**
> New install of Gutsy
AMD64

Bif

[Download and install this deb]("http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.4_amd64.deb")

Then run this command in the terminal.
```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

Then restart your browser.

---

### Post by Bif Powell on 2008-02-02
> **Kilz said:**
> [Download and install this deb]("http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.4_amd64.deb")

Then run this command in the terminal.
```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

Then restart your browser.

Thanks for the prompt reply.

When I download that file it won't install and says Error: Wrong architecture 'amd64'.

My system is an AMD64 X2 Dual Core 5600+ and in System Monitor is shows it as such.

Thanks!

Bif

---

### Post by crjackson on 2008-02-02
kilz,

I don't know exactly what happened but flash stopped working after downloading some updates.  Now, I think it may have been the updates that caused it but I'm not sure since I wasn't doing anything to verify that flash was working prior to the updates. 

Anyway, thanks again...  I re-ran your script and all is working now...

---

### Post by rslrdx on 2008-02-02
Hi Kilz, great script. 

I'd like to host the files the script gets as well, How can I do that? Would you allow it?

Thanks.

---

### Post by Kilz on 2008-02-03
> **Bif Powell said:**
> Thanks for the prompt reply.

When I download that file it won't install and says Error: Wrong architecture 'amd64'.

My system is an AMD64 X2 Dual Core 5600+ and in System Monitor is shows it as such.

Thanks!

Bif

The amd64 error is telling us you do not have the amd64 version of Ubuntu installed. You may have a 64bit processor, but you may have installed the 32bit version of Ubuntu.

---

### Post by Kilz on 2008-02-03
> **rslrdx said:**
> Hi Kilz, great script. 

I'd like to host the files the script gets as well, How can I do that? Would you allow it?

Thanks.

Hosting is not a problem as the files are open source. The problem would be getting the script to pull from multiple sources. Im not quite sure how that could be done.

---

### Post by Humanculus on 2008-02-03
I had to dig through the Google dustbin quite a bit to find this page.  Cool Ubuntu.

I tried Hoary years ago, and I must say that Gibbon is MUCH preferable for the end user.

The script worked for me, thanks.

Mark

---

### Post by Tosa on 2008-02-03
> **Kilz said:**
> [Download and install this deb]("http://home.comcast.net/%7Eubuntume/nspluginwrapper_0.9.91.4_amd64.deb")

Then run this command in the terminal.
```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```Then restart your browser.

Thanks a million!
Flash finally seems to be working as it should.
BTW, I didn't restart my browser, but that (non)naked clock showed up after the page had been reloaded!? 

:guitar:

---

### Post by shane2peru on 2008-02-03
Thanks for the script worked like a charm on my Gutsy Fresh install!

Shane

---

### Post by Bernie1 on 2008-02-04
I use [http://onlineclock.net](http://onlineclock.net) and it has a flash alarm but works fine

---

### Post by Quiz on 2008-02-04
BIG BIG thanks :) finaly i got flash player :guitar:

---

### Post by Bolshevik on 2008-02-05
Thanks So Much Kilz! life saver! everything works now, odd thing i had installed the ndiswrapper previously, but must have don't it wrong, cuzz it didn't work, this was perfect!

Thanks again!

---

### Post by one million monkeys on 2008-02-05
Thanks - worked great. For some reason I had to restart firefox twice, then it was fine.

---

### Post by Soarer on 2008-02-06
I have used this method and flash works fine in FF2 on Gutsy 64. I uninstalled nonfree first of course.

However, today came an update to Swiftweasel turning it into FF3. All well & good.

Except flash refuses to work on FF3. I have linked all the FF2 plugins to the directory in FF3 (in /usr/lib) but no go for YouTube or Google Analytics.

Edit>>preferences>>application is completely blank, if that helps.

Any ideas for me please? I like the speed of FF3, but need Flash from time to time :)

---

### Post by piomad on 2008-02-06
it works - thanks very much!

---

### Post by monkeymind90 on 2008-02-06
I'm having problems with watching flash. I tried installing the plugin listed in this thread, but it didn't work. i don't think I have any remnants of other flash players installed, but I am very new at this. Please help. Here is what I get from the terminal when I input 

ethan@ethan-laptop:~$ ls -al /usr/lib/mozilla//plugins/
total 6900
drwxr-xr-x 2 ethan users    4096 2008-02-06 19:23 .
drwxr-xr-x 3 root  root     4096 2007-10-15 16:27 ..
-rwxr-xr-x 1 ethan users 7040036 2007-06-19 17:31 libflashplayer.so
lrwxrwxrwx 1 ethan users      36 2008-02-04 12:47 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 ethan users      37 2008-02-04 12:47 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 ethan users      34 2008-02-04 12:47 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 ethan users      35 2008-02-04 12:47 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 ethan users      36 2008-02-04 12:47 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 ethan users      37 2008-02-04 12:47 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 ethan users      42 2008-02-04 12:47 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 ethan users      43 2008-02-04 12:47 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 ethan users      60 2008-02-06 19:23 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
ethan@ethan-laptop:~$ ls -al /usr/lib/firefox/plugins/
total 20
drwxr-xr-x 2 ethan users  4096 2007-10-15 16:27 .
drwxr-xr-x 5 root  root   4096 2007-10-15 16:32 ..
lrwxrwxrwx 1 ethan users    36 2008-02-04 12:47 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 ethan users    37 2008-02-04 12:47 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 ethan users    34 2008-02-04 12:47 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 ethan users    35 2008-02-04 12:47 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 ethan users    36 2008-02-04 12:47 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 ethan users    37 2008-02-04 12:47 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 ethan users    42 2008-02-04 12:47 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 ethan users    43 2008-02-04 12:47 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 ethan users 11456 2007-10-08 08:34 libunixprintplugin.so
ethan@ethan-laptop:~$ 

please us small words.

---

### Post by monkeymind90 on 2008-02-06
Quick note on my earlier post. When I open the Synaptic Package manager I get a broken package message whenever I try and install the thing at the beginning of this thread.

---

### Post by Kilz on 2008-02-07
> **monkeymind90 said:**
> Quick note on my earlier post. When I open the Synaptic Package manager I get a broken package message whenever I try and install the thing at the beginning of this thread.

In Synaptic click Edit, then Fix Broken Packages. let me know what it did. By the way, what thing at the beginning exactly?

---

### Post by monkeymind90 on 2008-02-07
> **Kilz said:**
> In Synaptic click Edit, then Fix Broken Packages. let me know what it did. By the way, what thing at the beginning exactly?

I tried this and it didn't seem to do anything. The screen flickered and nothing changed. The thing at the beginning would be the script to install the previous r48 plugin. Also, how do I check what plugins I have installed currently?

---

### Post by Kilz on 2008-02-07
> **monkeymind90 said:**
> I tried this and it didn't seem to do anything. The screen flickered and nothing changed. The thing at the beginning would be the script to install the previous r48 plugin. Also, how do I check what plugins I have installed currently?

In the address bar of firefox type ```
about:plugins
``` and hit enter.
Do you still have the error message when opening Synaptic?

---

### Post by hgwielewicki on 2008-02-07
thank you so much for your help. flash is now working perfectly. your directions couldn't be better.

---

### Post by Tosa on 2008-02-07
This is just an assumption...
Four days ago I finally got flash working. Few minutes ago I realized it didn't work. I've downloaded nspluginwrapper according to this post  [http://ubuntuforums.org/showpost.php?p=4257199&postcount=763](http://ubuntuforums.org/showpost.php?p=4257199&postcount=763) and I have it working again.
The only thing that I did during these 4 days was installing the last kernel update, which didn't end good in my case. There were some errors...
Anyway I can only assume that the new kernel somehow messed up (among other things) flash!?

---

### Post by Kilz on 2008-02-07
> **Tosa said:**
> This is just an assumption...
Four days ago I finally got flash working. Few minutes ago I realized it didn't work. I've downloaded nspluginwrapper according to this post  [http://ubuntuforums.org/showpost.php?p=4257199&postcount=763](http://ubuntuforums.org/showpost.php?p=4257199&postcount=763) and I have it working again.
The only thing that I did during these 4 days was installing the last kernel update, which didn't end good in my case. There were some errors...
Anyway I can only assume that the new kernel somehow messed up (among other things) flash!?

There have been some updates lately that have made flash stop working. I have made adjustments so the script fixes issues. You probably got one of the updates with the kernel update.

---

### Post by monkeymind90 on 2008-02-07
> **Kilz said:**
> In the address bar of firefox type ```
about:plugins
``` and hit enter.
Do you still have the error message when opening Synaptic?
I'm still getting the error message.I only get the error message after I run the script. Also, when I looked up my plugins it says that I have Totem, which has a flash player. Totem 2.20.0 and video/flv is what is says exactly. Do I need to get rid of this and if so how?

---

### Post by Kilz on 2008-02-07
> **monkeymind90 said:**
> I'm still getting the error message.I only get the error message after I run the script. Also, when I looked up my plugins it says that I have Totem, which has a flash player. Totem 2.20.0 and video/flv is what is says exactly. Do I need to get rid of this and if so how?

You can uninstall totem in synaptic if you want. But I have a feeling the issue you are having is because of the broken packages. What happens when you enter ```
sudo apt-get install -f 
```into the terminal?

---

### Post by monkeymind90 on 2008-02-07
> **Kilz said:**
> You can uninstall totem in synaptic if you want. But I have a feeling the issue you are having is because of the broken packages. What happens when you enter ```
sudo apt-get install -f 
```into the terminal?

ethan@ethan-laptop:~$ sudo apt-get install -f
[sudo] password for ethan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Kilz on 2008-02-07
> **monkeymind90 said:**
> ethan@ethan-laptop:~$ sudo apt-get install -f
[sudo] password for ethan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

You still get a broken package error when starting Synaptic? Please give the full error if you do. While you have synaptic open please give me the installed version of nspluginwrapper.

---

### Post by monkeymind90 on 2008-02-08
> **Kilz said:**
> You still get a broken package error when starting Synaptic? Please give the full error if you do. While you have synaptic open please give me the installed version of nspluginwrapper.

Ok here's what is says: "Attention! You have 1 broken packet on your system! Use the Broken filter to locate it."
 The version is 0,9,91,6 1Ubuntu1

I was looking through the forum and I saw your post about installing 32 bit Firefox. Is that a good idea for me? If it fixes the problem I don't mind not using the 64bit on the internet.

---

### Post by Kilz on 2008-02-08
> **monkeymind90 said:**
> Ok here's what is says: "Attention! You have 1 broken packet on your system! Use the Broken filter to locate it."
 The version is 0,9,91,6 1Ubuntu1

I was looking through the forum and I saw your post about installing 32 bit Firefox. Is that a good idea for me? If it fixes the problem I don't mind not using the 64bit on the internet.

It is an option, but the broken package is nspluginwrapper. First try this. Remove nspluginwrapper in synaptic. Open a terminal and run ```
sudo apt-get clean
``` then rerun the r48 script.  Drag the script onto the desktop. Then use 
```
cd ~/Desktop
./GetFlash
```
This time the terminal will not close at the end. Dont close it and test flash after restarting your browser. If flash doesnt run, copy and paste the entire install from the terminal to a post here.

---

### Post by monkeymind90 on 2008-02-08
ethan@ethan-laptop:~$ cd /home/ethan/Desktop
ethan@ethan-laptop:~/Desktop$ ./GetFlash
mkdir: cannot create directory `/tmp/ffplug': File exists

 This script is used to setup Flash and nspluginwrapper 
 for use in 64bit Firefox or other mozilla based browsers 

 Please select the version of the Ubuntu you are installing to. 
 Install options are : 

 1. Dapper Drake v6.06 or Edgy Eft 6.10 
 2. Feisty Fawn v 7.04 
 3. Gutsy Gibbon 

Install option (1-3)? :3
 Gutsy Gibbon 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nspluginwrapper for regex 'nspluginwrapper*'
The following packages will be REMOVED:
  nspluginwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 377kB disk space will be freed.
(Reading database ... 88178 files and directories currently installed.)
Removing nspluginwrapper ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 160kB disk space will be freed.
(Reading database ... 88155 files and directories currently installed.)
Removing flashplugin-nonfree ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflash-mozplugin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflash0c2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libswfdec0.4-dbg for regex 'libswfdec*'
Note, selecting libswfdec0.4-dev for regex 'libswfdec*'
Note, selecting libswfdec0.5-dev for regex 'libswfdec*'
Note, selecting libswfdec-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3 for regex 'libswfdec*'
Note, selecting libswfdec0.4 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1-dbg for regex 'libswfdec*'
E: Couldn't find package libswfdec*
mkdir: cannot create directory `/tmp/nsplugwrapper': File exists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32gcc1 but it is not installable
             Depends: libc6-i386 (>= 2.3.6-2) but it is not installable
             Depends: lib32z1 but it is not installable
             Depends: lib32stdc++6 but it is not installable
             Depends: lib32asound2 but it is not installable
             Depends: lib32ncurses5 but it is not installable
E: Broken packages
--19:14:24--  [http://home.comcast.net/~ubuntume/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb](http://home.comcast.net/~ubuntume/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb)
           => `flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 88150 files and directories currently installed.)
Unpacking flashplugin-nonfree (from flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.999.0.2+really0ubuntu12) ...
--19:14:26--  [http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6_amd64.deb](http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6_amd64.deb)
           => `nspluginwrapper_0.9.91.6_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

(Reading database ... 88156 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.999.0.2+really0ubuntu12 (using flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Unpacking replacement flashplugin-nonfree ...
Selecting previously deselected package nspluginwrapper.
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.6_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.999.0.2+really0ubuntu12) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on ia32-libs (>= 1.6); however:
  Package ia32-libs is not installed.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.
ethan




 Everything has been installed 
 Once you read this you can close this terminal 
 window. If you have a browser running you 
 will need to restart it. 
ethan@ethan-laptop:~/Desktop$

Thanks for spending so much time on this. If nothing jumps out at you as being fixable I'll just give it up and install the 32 bit version.

---

### Post by Kilz on 2008-02-09
Ok, something does pop out, but I am not quite sure why its happening.

ia32-libs: Depends: lib32gcc1 but it is not installable
Depends: libc6-i386 (>= 2.3.6-2) but it is not installable
Depends: lib32z1 but it is not installable
Depends: lib32stdc++6 but it is not installable
Depends: lib32asound2 but it is not installable
Depends: lib32ncurses5 but it is not installable

These packages are available , or should be in the Ubuntu repositories. 

[http://packages.ubuntu.com/gutsy/base/libc6-i386](http://packages.ubuntu.com/gutsy/base/libc6-i386)
[http://packages.ubuntu.com/gutsy/libs/lib32z1](http://packages.ubuntu.com/gutsy/libs/lib32z1)
[http://packages.ubuntu.com/gutsy/libs/lib32stdc++6](http://packages.ubuntu.com/gutsy/libs/lib32stdc++6)
[http://packages.ubuntu.com/gutsy/libs/lib32asound2](http://packages.ubuntu.com/gutsy/libs/lib32asound2)
[http://packages.ubuntu.com/gutsy/libs/lib32ncurses5](http://packages.ubuntu.com/gutsy/libs/lib32ncurses5)

The script uses apt-get to get them from the Ubuntu repositories. It should do it without error.
can you run ```
sudo apt-get install libc6-i386
```
If not something is wrong with apt. You might have some error in your /etc/apt/sources.list.

---

### Post by monkeymind90 on 2008-02-09
Kilz, you are a god among Ubuntu users. Thanks you so much for spending all this time on my problem. It installed perfectly and I can now see online videos.

---

### Post by Kilz on 2008-02-09
> **monkeymind90 said:**
> Kilz, you are a god among Ubuntu users. Thanks you so much for spending all this time on my problem. It installed perfectly and I can now see online videos.

Your welcome, but the issue with your apt needs to be fixed if you didnt fix this issue by editing the apt list or some other apt fix. You will run into other problems , and updates may not be downloaded and installed. If you didnt edit the apt and just downloaded the packages manually please post your /etc/apt/sources.list here and maybe we can fix it.

---

### Post by punkduck02 on 2008-02-09
Thanks for the Flash plugin it worked great.  But now I'm still having an issue with my video.  Every time I go to watch a video either online or something that I have on my HD the color is completely out of alignment.  The red channel with be on one side, blue and green are on another so it make watching a video annoying.  If anyone can help me with this that would be great.  This isn't just a video player problem it happens with flash video as well so there might be something wrong with my system.

AMD64 3800+ 2gig DDR2 533, 80 gig IDE HD, 200 gig IDE HD, ATI Radeon X1650 PRO

---

### Post by havarlan on 2008-02-11
Hello, I am running into some problems with flash, as well.  I've messed with it in such a way that I've managed to have a file removed that I cannot figure out how to get back.  Perhaps I just need a ln -s.  Anyways, here's the main error I get, and I'll post the full output further down.

```

Setting up nspluginwrapper (0.9.91.6-1ubuntu1) ...
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libXcomposite.so.1: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```

I've gone in synaptic and reinstalled libXcomposite and -dev, to no avail!  the file exists, too.

```

jmoore@shion:~/Downloads/nspluginwrapper install$ locate libXcomposite
/usr/lib/libXcomposite.so
/usr/lib/libXcomposite.so.1.0.0
/usr/lib/libXcomposite.so.1
/usr/lib/libXcomposite.a

```

The full output of the script is:
```

jmoore@shion:~/Downloads/nspluginwrapper install$ sudo ./GetFlash mkdir: cannot create directory `/tmp/ffplug': File exists

 This script is used to setup Flash and nspluginwrapper 
 for use in 64bit Firefox or other mozilla based browsers 

 Please select the version of the Ubuntu you are installing to. 
 Install options are : 

 1. Dapper Drake v6.06 or Edgy Eft 6.10 
 2. Feisty Fawn v 7.04 
 3. Gutsy Gibbon 

Install option (1-3)? :3
 Gutsy Gibbon 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nspluginwrapper for regex 'nspluginwrapper*'
The following packages were automatically installed and are no longer required:
  libadplug0c2a libswscale1d python-qt3 libbinio1c2 libdbus-qt-1-1c2
  liboil0.3-dev python-xlib
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nspluginwrapper
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 377kB disk space will be freed.
(Reading database ... 167288 files and directories currently installed.)
Removing nspluginwrapper ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libadplug0c2a libswscale1d python-qt3 libbinio1c2 libdbus-qt-1-1c2
  liboil0.3-dev python-xlib
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 160kB disk space will be freed.
(Reading database ... 167265 files and directories currently installed.)
Removing flashplugin-nonfree ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflash-mozplugin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libadplug0c2a libswscale1d python-qt3 libbinio1c2 libdbus-qt-1-1c2
  liboil0.3-dev python-xlib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflash0c2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libadplug0c2a libswscale1d python-qt3 libbinio1c2 libdbus-qt-1-1c2
  liboil0.3-dev python-xlib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libadplug0c2a libswscale1d python-qt3 libbinio1c2 libdbus-qt-1-1c2
  liboil0.3-dev python-xlib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libadplug0c2a libswscale1d python-qt3 libbinio1c2 libdbus-qt-1-1c2
  liboil0.3-dev python-xlib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libadplug0c2a libswscale1d python-qt3 libbinio1c2 libdbus-qt-1-1c2
  liboil0.3-dev python-xlib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libswfdec0.4-dbg for regex 'libswfdec*'
Note, selecting libswfdec0.4-dev for regex 'libswfdec*'
Note, selecting libswfdec0.5-dev for regex 'libswfdec*'
Note, selecting libswfdec-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3 for regex 'libswfdec*'
Note, selecting libswfdec0.4 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1-dbg for regex 'libswfdec*'
E: Couldn't find package libswfdec*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libadplug0c2a libswscale1d python-qt3 libbinio1c2 libdbus-qt-1-1c2
  liboil0.3-dev python-xlib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
--12:14:18--  http://home.comcast.net/~ubuntume/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb
           => `flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,176,934 (4.9M) [text/plain]

100%[====================================>] 5,176,934    514.04K/s    ETA 00:00

12:14:27 (569.99 KB/s) - `flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb' saved [5176934/5176934]

Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 167260 files and directories currently installed.)
Unpacking flashplugin-nonfree (from flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.999.0.2+really0ubuntu12) ...
--12:14:28--  http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6_amd64.deb
           => `nspluginwrapper_0.9.91.6_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100,884 (99K) [text/plain]

100%[====================================>] 100,884      287.14K/s             

12:14:29 (285.70 KB/s) - `nspluginwrapper_0.9.91.6_amd64.deb' saved [100884/100884]

(Reading database ... 167266 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.999.0.2+really0ubuntu12 (using flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Unpacking replacement flashplugin-nonfree ...
Selecting previously deselected package nspluginwrapper.
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.6_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.999.0.2+really0ubuntu12) ...
Setting up nspluginwrapper (0.9.91.6-1ubuntu1) ...
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libXcomposite.so.1: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.
jmoore




 Everything has been installed 
 Once you read this you can close this terminal 
 window. If you have a browser running you 
 will need to restart it. 


```

I've scoured this thread but been unable to come up with a solution, so I turn to the more experienced :)

---

### Post by Kilz on 2008-02-11
> **havarlan said:**
> Hello, I am running into some problems with flash, as well.  I've messed with it in such a way that I've managed to have a file removed that I cannot figure out how to get back.  Perhaps I just need a ln -s.  Anyways, here's the main error I get, and I'll post the full output further down.


No, odds are ite looking for the 32bit version of libXcomposite.so.1. On a 64bit machine there are 32 and 64bit libraries. Never overwrite one with the other or setup symlinks between them. The reason Flash may use the 32bit one it is a 32bit plugin that is wrapped for the 64bit browser.
Look in  /usr/lib, if this one isnt there reinstall the libXcomposite package.
Look in /usr/lib32 if this one isnt there reinstall ia32-libs package.

---

### Post by heinzbitte on 2008-02-11
Excuse me if this has been posted already.

I updated my version of flash, and it seemed to be working better, but I have run into some problems using google video.

If I resize the window the image turns gray but I can still hear the sound.  This also happens if I go to another tab.

---

### Post by havarlan on 2008-02-11
> **Kilz said:**
> 
-snip-
Look in  /usr/lib, if this one isnt there reinstall the libXcomposite package.
Look in /usr/lib32 if this one isnt there reinstall ia32-libs package.


reinstalling ia32-libs fixed the problem entirely.  I would've never made the connection myself!  Now flash works perfectly, and no more grey overlay on flash stuff.  thanks! :D

---

### Post by Kilz on 2008-02-11
> **heinzbitte said:**
> Excuse me if this has been posted already.

I updated my version of flash, and it seemed to be working better, but I have run into some problems using google video.

If I resize the window the image turns gray but I can still hear the sound.  This also happens if I go to another tab.

The update is to the buggy r115 release. You can confirm this by entering ```
about:plugins
``` in the browser address bar and hitting enter. Under the flash it should say the version.
You can go back to the working r48 plugin by running the script again.

---

### Post by wncben on 2008-02-11
Howdy Kilz,

 I want to thank you for your hard work with AMD64 issues, you helped me get firefox32 installed last year so I could access java and flash, and I am wondering if this new script of yours will get ff64 up and running with them... and whether or not it is worth the effort... I am basically happy with ff32, though it bugs me that I have a 64 bit system that I can't use fully... The one weird thaing that has made me ponder the change is that certain websites (like my bank's secure login) do not work with ff32, wheras they do work on ff64... 
 It may just be a simple case of needing to update... I haven't updated since I have so many workarounds to get bcm43, ati 200m, java, flash,  and such going that I have been afraid of breaking something...

 If getting ff64 up and running will simplify my life I'm all for it...

 Thanks Again
~Ol Ben

---

### Post by Kilz on 2008-02-11
> **wncben said:**
> Howdy Kilz,

 I want to thank you for your hard work with AMD64 issues, you helped me get firefox32 installed last year so I could access java and flash, and I am wondering if this new script of yours will get ff64 up and running with them... and whether or not it is worth the effort... I am basically happy with ff32, though it bugs me that I have a 64 bit system that I can't use fully... The one weird thaing that has made me ponder the change is that certain websites (like my bank's secure login) do not work with ff32, wheras they do work on ff64... 
 It may just be a simple case of needing to update... I haven't updated since I have so many workarounds to get bcm43, ati 200m, java, flash,  and such going that I have been afraid of breaking something...

 If getting ff64 up and running will simplify my life I'm all for it...

 Thanks Again
~Ol Ben

The problem will be Java, there is no 64bit Sun Java plugin. Icedtea is a open source java, it does have a 64bit plugin (in the repo's). But it doesn't work for every site. If it works on your sites then the flash plugin is simply running this script in the first post.

---

### Post by darksong on 2008-02-11
It may just be me - but the link for the script isn't working.

---

### Post by heinzbitte on 2008-02-11
> **Kilz said:**
> The update is to the buggy r115 release. You can confirm this by entering ```
about:plugins
``` in the browser address bar and hitting enter. Under the flash it should say the version.
You can go back to the working r48 plugin by running the script again.
I do have r115 but it still works better than the previous version.

---

### Post by ThomasTangNJ on 2008-02-11
Hi, I'm using ubuntu studio 64-bit edition.
I tried the installation.
It came up 3 selections:
>  1. Dapper Drake v6.06 or Edgy Eft 6.10 
 2. Feisty Fawn v 7.04 
 3. Gutsy Gibbon 
Since my OS is not in the list, so I tried them all.
No Luck! Still can't open any flash web page.
What should I do now? I'm very new for this!
Thanks!

Thomas

Oh yeah, is this the info you asked to attach with the post?
```
thomas@ubuntu:~$ ls -al /usr/lib/firefox/plugins/
Total 24
drwxr-xr-x 2 thomas users  4096 2008-02-11 17:38 .
drwxr-xr-x 5 root   root   4096 2008-02-09 04:39 ..
lrwxrwxrwx 1 thomas users    36 2008-02-09 04:00 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 thomas users    37 2008-02-09 04:00 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 thomas users    34 2008-02-09 04:00 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 thomas users    35 2008-02-09 04:00 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 thomas users    36 2008-02-09 04:00 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 thomas users    37 2008-02-09 04:00 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 thomas users    42 2008-02-09 04:00 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 thomas users    43 2008-02-09 04:00 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 thomas users 11456 2008-02-07 06:07 libunixprintplugin.so
lrwxrwxrwx 1 root   root     60 2008-02-11 17:38 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
thomas@ubuntu:~$ ls -al /usr/lib/mozilla//plugins/
Total 6900
drwxr-xr-x 2 thomas users     4096 2008-02-11 17:38 .
drwxr-xr-x 3 root   root      4096 2008-02-09 04:00 ..
-rwxr-xr-x 1 thomas thomas 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 thomas users       36 2008-02-09 04:00 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 thomas users       37 2008-02-09 04:00 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 thomas users       34 2008-02-09 04:00 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 thomas users       35 2008-02-09 04:00 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 thomas users       36 2008-02-09 04:00 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 thomas users       37 2008-02-09 04:00 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 thomas users       42 2008-02-09 04:00 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 thomas users       43 2008-02-09 04:00 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 root   root        60 2008-02-11 17:38 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
thomas@ubuntu:~$
```

---

### Post by Kilz on 2008-02-11
> **heinzbitte said:**
> I do have r115 but it still works better than the previous version.

If you want to keep r115 then there isnt much I can do for your issues with Google video.

---

### Post by Kilz on 2008-02-11
> **ThomasTangNJ said:**
> Hi, I'm using ubuntu studio 64-bit edition.
I tried the installation.
It came up 3 selections:

Since my OS is not in the list, so I tried them all.
No Luck! Still can't open any flash web page.
What should I do now? I'm very new for this!
Thanks!

Thomas


These 2 commands and a browser restart should fix the issues.
```
sudo chown -R thomas:users /usr/lib/mozilla/plugins/
sudo chown -R thomas:users /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

---

### Post by heinzbitte on 2008-02-11
> **Kilz said:**
> If you want to keep r115 then there isnt much I can do for your issues with Google video.

Alright, thanks, the problems equally annoy me, so I'll just stay with it.

---

### Post by meenfreem on 2008-02-12
not entirely sure whether i'm in the right topic, but my firefox keeps on crashing and have locatedthe problem (I think).

Flash works fine, videos etc. the problems with me is java pop-ups I think. The weird thing is that if I have one browser open, java pop-ups work fine, but if I have two browsers open then the java pop-up will crash firefox. 

Any ideas?

I have a brand new laptop, clean install Gutsy, everything else fine except for this one issue (big issue since many websites i frequent use java pop-up stuff...)

---

### Post by Kilz on 2008-02-12
> **meenfreem said:**
> not entirely sure whether i'm in the right topic, but my firefox keeps on crashing and have locatedthe problem (I think).

Flash works fine, videos etc. the problems with me is java pop-ups I think. The weird thing is that if I have one browser open, java pop-ups work fine, but if I have two browsers open then the java pop-up will crash firefox. 

Any ideas?

I have a brand new laptop, clean install Gutsy, everything else fine except for this one issue (big issue since many websites i frequent use java pop-up stuff...)

A separate topic may have been a better choice since this isnt a thread about java. But I have a feeling you are using Blackdown for a 64bit java plugin. If so remove it. If you have any other java problems a fresh post may be a better idea since those that may have java fixes will never look this deep in a flash thread.

---

### Post by mchan on 2008-02-12
I am so greatful for this wrapper, I have the player for 3 month but not worked and tried on Adobe support  and no flash player worked until this easy install, Adobe need to learn from this forum for their support site (it is discourage for new users of Linux)
Hats off to Ubuntu.....

---

### Post by Saghaulor on 2008-02-12
I installed Flash for my AMD64 Gutsy laptop by using a .deb.

I don't remember if this is where I found it.

[http://ubuntuforums.org/showthread.php?t=517987](http://ubuntuforums.org/showthread.php?t=517987)

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmultiverse%2Ff%2Fflashplugin-nonfree%2Fflashplugin-nonfree_9.0.48.0.0ubuntu4_amd64.deb&md5sum=8b1394475334e909061e4ab84d1d8401&arch=amd64&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmultiverse%2Ff%2Fflashplugin-nonfree%2Fflashplugin-nonfree_9.0.48.0.0ubuntu4_amd64.deb&md5sum=8b1394475334e909061e4ab84d1d8401&arch=amd64&type=main)

But I believe it's the same file.

Now my question is; will this in the end be the same thing as following Kilz instructions? Because I can view flash on nearly every site, however, I cannot load the myspace media player. Kilz, can you use the myspace media player with your setup?

I would like to resolve this issue once and for all because it is rather annoying.

Thanks for the help.

---

### Post by Kilz on 2008-02-12
> **Saghaulor said:**
> I installed Flash for my AMD64 Gutsy laptop by using a .deb.

I don't remember if this is where I found it.

[http://ubuntuforums.org/showthread.php?t=517987](http://ubuntuforums.org/showthread.php?t=517987)

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmultiverse%2Ff%2Fflashplugin-nonfree%2Fflashplugin-nonfree_9.0.48.0.0ubuntu4_amd64.deb&md5sum=8b1394475334e909061e4ab84d1d8401&arch=amd64&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmultiverse%2Ff%2Fflashplugin-nonfree%2Fflashplugin-nonfree_9.0.48.0.0ubuntu4_amd64.deb&md5sum=8b1394475334e909061e4ab84d1d8401&arch=amd64&type=main)

But I believe it's the same file.

Now my question is; will this in the end be the same thing as following Kilz instructions? Because I can view flash on nearly every site, however, I cannot load the myspace media player. Kilz, can you use the myspace media player with your setup?

I would like to resolve this issue once and for all because it is rather annoying.

Thanks for the help.

Can you give me a link to a page with it?

---

### Post by Saghaulor on 2008-02-12
Sure, I'll keep looking. I don't remember where I found it offhand. I'm at work right now and I believe that I bookmarked the link on my laptop at home. I'll try to get it to you asap.

Thanks for the prompt response.

---

### Post by drfox on 2008-02-15
I've just downloaded FF 3 beta 3 and have tried your script, but Flash isn't working in it. When will you have a script that will install in FF3, or do you know what I need to do to get it installed in FF3?

Thanks.

Larry

---

### Post by mad_max0204 on 2008-02-15
I might be boring with this but did you try 
sudo apt-get install flashplugin-nonfree  ???

I worked for me flawlessly. I have Firefox 2.0.0.12 from the latest system update.

---

### Post by drfox on 2008-02-15
> **mad_max0204 said:**
> I might be boring with this but did you try 
sudo apt-get install flashplugin-nonfree  ???

I worked for me flawlessly. I have Firefox 2.0.0.12 from the latest system update.

I used Synaptic a couple months ago, and the flash plugin messed up my gnome settings so badly that I had to reinstall Gutsy. I'm afraid to try it again.

Larry

---

### Post by Kilz on 2008-02-15
> **drfox said:**
> I used Synaptic a couple months ago, and the flash plugin messed up my gnome settings so badly that I had to reinstall Gutsy. I'm afraid to try it again.

Larry

Stick with what you have. A search will bring up [this thread ]("http://ubuntuforums.org/showthread.php?t=695674")on the topic you need.

---

### Post by elarella on 2008-02-15
I installed the r48 version of the flash and I have to say that it works like a charm on Firefox 2.0.0.12 and on Opera 9.50 beta 2.  Opera still crashes ocassionally on the more flash heavy websites, but at least I can play videos on yahoo and youtube. :)

Thanks, Kilz for making my 64 bit Gutsy more liveable again! :)

---

### Post by Rohaq on 2008-02-15
Hmm, I installed r48, after crashing problems with r115. It's stable now, but I don't seem to have any of the flash 9 features, such as fullscreen, so it doesn't seem to offer any benefits over the nonfree repository version. about: plugins confirms the version I'm running is Flash 9 r48...

Any tips of getting r115 stable, or at least scouring for reasons as to why it might have been crashing or failing to start would be good, any smart folks out there?

---

### Post by waynebruce on 2008-02-15
Thanks a lot for this script, I´ve been trying to remedy this problem for a few days now and all the other postings didn´t seem to help for my setup or whatnot.  Have a good day or evening!

---

### Post by Kilz on 2008-02-16
> **Rohaq said:**
> Hmm, I installed r48, after crashing problems with r115. It's stable now, but I don't seem to have any of the flash 9 features, such as fullscreen, so it doesn't seem to offer any benefits over the nonfree repository version. about: plugins confirms the version I'm running is Flash 9 r48...

Any tips of getting r115 stable, or at least scouring for reasons as to why it might have been crashing or failing to start would be good, any smart folks out there?

r115 was the first flash 9 linux plugin with full screen. But it also crashes a lot and will not show some flash. It isnt stable imho even though its supposed to be.  Thats why I have 2 versions available. One for those that just want flash to work and dont care about full screen videos that are often of to poor quality to be blown up that big. Then a second for those that want the latest features and dont mind the problems.

---

### Post by cgrado on 2008-02-17
I tried to install the first (recommended) one and i go to pantless-gaming.com and it still asks for me to install flash. 

on 7.10

```
christian@christian-desktop:~$ ls -al /usr/lib/mozilla/plugins
total 12
drwxr-xr-x 2 christian users 4096 2008-02-16 23:01 .
drwxr-xr-x 3 root      root  4096 2007-10-15 18:27 ..
lrwxrwxrwx 1 christian users   36 2008-02-16 16:04 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 christian users   37 2008-02-16 16:04 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 christian users   34 2008-02-16 16:04 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 christian users   35 2008-02-16 16:04 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 christian users   36 2008-02-16 16:04 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 christian users   37 2008-02-16 16:04 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 christian users   42 2008-02-16 16:04 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 christian users   43 2008-02-16 16:04 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 christian users   60 2008-02-16 23:01 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
christian@christian-desktop:~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 christian users  4096 2007-10-15 18:27 .
drwxr-xr-x 5 root      root   4096 2007-10-15 18:32 ..
lrwxrwxrwx 1 christian users    36 2008-02-16 16:04 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 christian users    37 2008-02-16 16:04 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 christian users    34 2008-02-16 16:04 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 christian users    35 2008-02-16 16:04 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 christian users    36 2008-02-16 16:04 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 christian users    37 2008-02-16 16:04 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 christian users    42 2008-02-16 16:04 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 christian users    43 2008-02-16 16:04 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 christian users 11456 2007-10-08 10:34 libunixprintplugin.so
christian@christian-desktop:~$ locate libflashplayer.so
christian@christian-desktop:~$ 


```

---

### Post by Kilz on 2008-02-17
> **cgrado said:**
> I tried to install the first (recommended) one and i go to pantless-gaming.com and it still asks for me to install flash. 

on 7.10

[/CODE]

For some reason it didnt download the flash plugin, please try to rerun the script again

---

### Post by kurtpete on 2008-02-18
Thank you so much for your script and the work you've put in maintaining this thread.  I am running Gutsy, and using FF 3.0b3.  Flash plugin r115 had installed and ran installing normally through apt-get.  It was quite buggy, however.  I ran your script to downgrade to the more stable version.  The script ran fine, however FF b3 would not see the plugin.  (I had already linked my /usr/lib/mozilla/plugins directory as mentioned in [this thread]("http://ubuntuforums.org/showthread.php?t=695674")).  

I did this:

```

cd /usr/lib/mozilla/plugins
rm npwrapper.libflashplayer.so
mv /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so ./npwrapper.libflashplayer.so

```

and it works beautifully in FF 3b3 now!  For some reason just having npwrapper.libflashplayer.so linked wasn't good enough.  It needed to be physically there.  Thank you again for the hard work.  Thought I'd throw this in if anyone else is having an issue with it working for the newest FF.

---

### Post by Soarer on 2008-02-19
Thanks for the information, but it didn't work for me. I'm using 64bit Gutsy. which may make a difference.

---

### Post by Kilz on 2008-02-19
> **Soarer said:**
> Thanks for the information, but it didn't work for me. I'm using 64bit Gutsy. which may make a difference.

Nope, shouldn't. try to reinstall once, then completely reread the first post of this topic again.

---

### Post by ahuman on 2008-02-19
[color=purple]**Would any of you please tell me what I should do to make "Get Flash" run in the terminal-application?**[/color]

[B][COLOR="SeaGreen"]The "Run and Terminal" option hasn't appeared when I right-clicked on "Get Flash", like the author of this thread said it would:
> 4. Inside the folder that extracts is a "GetFlash" file, double click on it.
5. Select "Run in Terminal"
When I right-clicked on "Get Flash", I didn't see any option like that: "*Run in Terminal*"

Relevant screenshot:[/COLOR][/B]
[img]http://img292.imageshack.us/img292/2480/screenshotoldflash013tatu3.png[/img]

---

### Post by Kilz on 2008-02-19
> **ahuman said:**
> [color=purple]**Would any of you please tell me what I should do to make "Get Flash" run in the terminal-application?**[/color]

[B][COLOR="SeaGreen"]The "Run and Terminal" option hasn't appeared when I right-clicked on "Get Flash", like the author of this thread said it would:

When I right-clicked on "Get Flash", I didn't see any option like that: "*Run in Terminal*"

Relevant screenshot:[/COLOR][/B]


Please read the instructions again, there is no right click involved.

---

### Post by ahuman on 2008-02-19
[COLOR="DarkRed"][B]I see you're right. 

How do you get the "run terminal" to appear (in a drop-box menu) next to that "Get Flash" file?[/B][/COLOR]

---

### Post by ahuman on 2008-02-19
[color="red"]In other words: **Would any of you please tell me what I should do to get the "run in the terminal" option to appear after I double-click on "Get Flash"?**[/color]

[B][COLOR="SeaGreen"]The "run and terminal" option hasn't appeared when I *double*-clicked on "Get Flash", like the author of this thread said it would:

When I *double*-clicked on "Get Flash", I didn't see any option like that: "*Run in Terminal*"

Relevant screenshot:[/COLOR][/B]
[img]http://img292.imageshack.us/img292/2480/screenshotoldflash013tatu3.png[/img]

---

### Post by Soarer on 2008-02-19
You have to extract the file out of the zip first. It will create a folder (on your desktop, if that is where the .zip is) called 'ndispluginwrapper install'. Double-(left)-click this folder to open it up, then  double-(left)-click the file 'GetFlash'. IIRC 'Run in Terminal' is at the bottom left of the window that opens. :)

---

### Post by JMC_Rimmer on 2008-02-19
Could I get some help please?  :)

rimmer@BlueMidget:~$ ls -al /usr/lib/mozilla/plugins/
total 6900
drwxr-xr-x 2 rimmer users    4096 2008-02-19 12:43 .
drwxr-xr-x 3 root   root     4096 2008-01-23 00:23 ..
-rwxr-xr-x 1 rimmer users 7040036 2007-06-19 17:31 libflashplayer.so
lrwxrwxrwx 1 rimmer users      36 2008-01-23 00:23 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 rimmer users      37 2008-01-23 00:23 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 rimmer users      34 2008-01-23 00:23 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 rimmer users      35 2008-01-23 00:23 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 rimmer users      36 2008-01-23 00:23 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 rimmer users      37 2008-01-23 00:23 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 rimmer users      42 2008-01-23 00:23 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 rimmer users      43 2008-01-23 00:23 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 rimmer users      60 2008-02-19 12:43 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
rimmer@BlueMidget:~$ ls -al /usr/lib/firefox/plugins/
total 20
drwxr-xr-x 2 rimmer users  4096 2008-02-17 20:42 .
drwxr-xr-x 5 root   root   4096 2008-02-17 20:42 ..
lrwxrwxrwx 1 rimmer users    36 2008-01-23 00:23 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 rimmer users    37 2008-01-23 00:23 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 rimmer users    34 2008-01-23 00:23 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 rimmer users    35 2008-01-23 00:23 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 rimmer users    36 2008-01-23 00:23 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 rimmer users    37 2008-01-23 00:23 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 rimmer users    42 2008-01-23 00:23 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 rimmer users    43 2008-01-23 00:23 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 rimmer users 11456 2008-02-07 03:07 libunixprintplugin.so
rimmer@BlueMidget:~$ 

Youtube just says I don't have flash installed.  Thanks much.

---

### Post by Kilz on 2008-02-19
> **JMC_Rimmer said:**
> Could I get some help please?  :)



Youtube just says I don't have flash installed.  Thanks much.

Please open Synaptic, and search for nspluginwrapper. Please tell me the installed version.

---

### Post by Curious65 on 2008-02-19
had a similar problem and kept getting the "install flash9" thing from adobe. or that i had java disabled.

for some reason the initial install messed up and even caused a conflict with the package manager. ran Synaptic and "fixed" the broken install but it wouldn't work.

i can't tell you all i did since it was too much trial and error uninstalling this and reinstalling that but the long and short (too late) was i did another install of your script and it ran fine. now when i go to you tube the video plays and a right click on "about flash player 9" say im' running 9.0.48.0 on the 64 bit machine. my non 64 bit machine says it's running version 9.0115.0 go figure.

all i can tell someone is that your script works although there might be a bit of trouble installing it. it's really nice to be able to see youtube now on my 64 bit machine. 

thanks a lot for this :KS

---

### Post by Curious65 on 2008-02-19
spoke too soon. the update mangaer told me there was a broken aplication and it was your script. fixing it broke you tube again. now when i go to youtube the whole browser greys out. 

damn, thanks anyway.

---

### Post by ThomasTangNJ on 2008-02-19
> **Kilz said:**
> These 2 commands and a browser restart should fix the issues.
```
sudo chown -R thomas:users /usr/lib/mozilla/plugins/
sudo chown -R thomas:users /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

Thank you, Kilz!
I'm now be able to view the flash web page and the video on Youtube site.

By the way, do you know what can I do to let my firefox be able to read the flv file?

Thanks again!

Thomas

---

### Post by kiroro on 2008-02-19
It works! Thank you so much sir! It even works in Opera 64bit....totally rocks!

---

### Post by Kilz on 2008-02-20
> **Curious65 said:**
> spoke too soon. the update mangaer told me there was a broken aplication and it was your script. fixing it broke you tube again. now when i go to youtube the whole browser greys out. 

damn, thanks anyway.

By reading your post at 836 , I see you have chosen to install the r115 (Very Buggy) script. Please run the r48.

---

### Post by Soarer on 2008-02-20
> **Kilz said:**
> By reading your post at 836 , I see you have chosen to install the r115 (Very Buggy) script. Please run the r48.

Agreed. I did that & got the same symptoms, now it works fine in FF2. Still need to spend some time on FF3 to get it working.

Thanks very much for all the work.

---

### Post by JMC_Rimmer on 2008-02-20
> **Kilz said:**
> Please open Synaptic, and search for nspluginwrapper. Please tell me the installed version.

It says 0.9.91.6-1ubuntu1.

---

### Post by Kilz on 2008-02-20
> **JMC_Rimmer said:**
> It says 0.9.91.6-1ubuntu1.

Thanks , so far everything looks like it should. Can you also give me the output of  ```
ls -al /usr/lib/nspluginwrapper/plugins/

```

---

### Post by JMC_Rimmer on 2008-02-20
> **Kilz said:**
> Thanks , so far everything looks like it should. Can you also give me the output of  ```
ls -al /usr/lib/nspluginwrapper/plugins/

```

That directory is empty (well other then . and .. ).

---

### Post by Kilz on 2008-02-20
> **JMC_Rimmer said:**
> That directory is empty (well other then . and .. ).

This command should place the wrapped plugin in that directiory. Then the symlink in the mozilla plugin directory should work and you should have flash. If after restarting your browser you dont have flash please tell me if the plugin is in the now empty directory we just checked.

```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by Chame_Wizard on 2008-02-20
sometimes flash sucks

---

### Post by JMC_Rimmer on 2008-02-20
> **Kilz said:**
> This command should place the wrapped plugin in that directiory. Then the symlink in the mozilla plugin directory should work and you should have flash. If after restarting your browser you dont have flash please tell me if the plugin is in the now empty directory we just checked.

```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

rimmer@BlueMidget:/usr/lib/nspluginwrapper/plugins$ sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
[sudo] password for rimmer:
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: 1: Syntax error: word unexpected (expecting ")")
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
rimmer@BlueMidget:/usr/lib/nspluginwrapper/plugins$

---

### Post by Kilz on 2008-02-20
> **JMC_Rimmer said:**
> rimmer@BlueMidget:/usr/lib/nspluginwrapper/plugins$ sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
[sudo] password for rimmer:
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: 1: Syntax error: word unexpected (expecting ")")
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
rimmer@BlueMidget:/usr/lib/nspluginwrapper/plugins$

please uninstall nspluginwrapper and remove its directory, then reinstall the script. It will reinstall nspluginwrapper.

```
sudo apt-get remove nspluginwrapper
sudo rm -rfd /usr/lib/nspluginwrapper
```

---

### Post by JMC_Rimmer on 2008-02-20
Didn't work  :(

/usr/lib/nspluginwrapper/plugins is still empty... That's not right is it?

---

### Post by Kilz on 2008-02-20
> **JMC_Rimmer said:**
> Didn't work  :(

/usr/lib/nspluginwrapper/plugins is still empty... That's not right is it?

Did you get the same errors?
We can also try 
```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```
Without sudo. In this case the wrapper will be at ~/.mozilla/plugins/

---

### Post by will1911a1 on 2008-02-20
This worked like a charm.  THANKS!

---

### Post by JMC_Rimmer on 2008-02-20
> **Kilz said:**
> Did you get the same errors?
We can also try 
```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```
Without sudo. In this case the wrapper will be at ~/.mozilla/plugins/

I'm still getting the same error.  Here is what the script says when I try to run it:

/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: 1: Syntax error: word unexpected (expecting ")")
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

The only other thing that seems strange in the terminal log is this:

E: Couldn't find package libswfdec*

---

### Post by JMC_Rimmer on 2008-02-20
I do have a custom kernel.  That shouldn't cause problems should it?

---

### Post by Kilz on 2008-02-20
> **JMC_Rimmer said:**
> I do have a custom kernel.  That shouldn't cause problems should it?

Im not sure it would. If you have a stock kernel installed you can try booting into it to eliminate that. There is also the possibility that there is a bad package of nspluginwrapper in the apt cashe. ```
sudo apt-get clean
``` will clear the cashe then you can try to remove it and reinstall.

---

### Post by JMC_Rimmer on 2008-02-20
> **Kilz said:**
> Im not sure it would. If you have a stock kernel installed you can try booting into it to eliminate that. There is also the possibility that there is a bad package of nspluginwrapper in the apt cashe. ```
sudo apt-get clean
``` will clear the cashe then you can try to remove it and reinstall.

Didn't work.  The strange thing is that the script didn't download a new version of nspluginwrapper.  It said something about "file already received" and spat out the same errors when it was done.  Wasn't the point of sudo apt-get clean to make it download nspluginwrapper again?

---

### Post by brunoscunha on 2008-02-21
Thank you

---

### Post by Kilz on 2008-02-21
> **JMC_Rimmer said:**
> Didn't work.  The strange thing is that the script didn't download a new version of nspluginwrapper.  It said something about "file already received" and spat out the same errors when it was done.  Wasn't the point of sudo apt-get clean to make it download nspluginwrapper again?

If this was during the running of the script, it indicates it downloaded it already to its temp working folder, not that it was in the apt cashe. Is that when you saw this?

---

### Post by JMC_Rimmer on 2008-02-21
> **Kilz said:**
> If this was during the running of the script, it indicates it downloaded it already to its temp working folder, not that it was in the apt cashe. Is that when you saw this?

Yes, this is what I saw.  I guess I misunderstood what clearing the cache meant.

---

### Post by Saghaulor on 2008-02-21
Kilz, I used the following thread to install flash for amd64.
[http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)

In that thread, I found a link to the .deb that was supposedly and install for Gutsy Amd64.
[http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466)

I can use flash for nearly every site, with the exception of the myspace music player. Should I uninstall and use your method?

---

### Post by daradib on 2008-02-21
> **Saghaulor said:**
> Kilz, I used the following thread to install flash for amd64.
[http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)

In that thread, I found a link to the .deb that was supposedly and install for Gutsy Amd64.
[http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466)

I can use flash for nearly every site, with the exception of the myspace music player. Should I uninstall and use your method?

Well I am not kilz, but you should not install flash Kilz's way as it will have the same result. Instead, you have to update the nspluginwrapper package.

I think you should see [this post]("http://ubuntuforums.org/showpost.php?p=4246035&postcount=112").

> **daradib said:**
> The bug that causes the crash is [Launchpad Bug# 177856]("https://bugs.launchpad.net/nspluginwrapper/+bug/177856") and it only affects 64-bit systems, which rely on nspluginwrapper to run the 32-bit flash plugin.

The nspluginwrapper author has provided a patch: [http://launchpadlibrarian.net/11055616/npw.gthreads.diff](http://launchpadlibrarian.net/11055616/npw.gthreads.diff)

And [Rashad Tatum]("https://bugs.launchpad.net/~rmtatum") built a fixed package: [http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb](http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb)

EDIT: This bug affects only SMP/SMT machines. Thanks [Riccardo Pellegrini]("https://bugs.launchpad.net/~cionci") and nspluginwrapper author.
(i.e. multicore, multiprocessor, including presumably Intel HyperThreading)

EDIT (clarity): You should use this method if flash crashes (as in the flash area becomes white or grey and flash cannot be used until the web browser is restarted). So far, this only appears to affect multicore/multiprocessor systems.

---

### Post by Kilz on 2008-02-21
> **Saghaulor said:**
> Kilz, I used the following thread to install flash for amd64.
[http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)

In that thread, I found a link to the .deb that was supposedly and install for Gutsy Amd64.
[http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466)

I can use flash for nearly every site, with the exception of the myspace music player. Should I uninstall and use your method?

In my experience, the r115 plugin does not work for every flash site. The r115 plugin is installed with the deb in the repos as well as the r115 script in my post. The r48 plugin on the other hand works for all the sites I have tested it with.

---

### Post by Kilz on 2008-02-21
> **daradib said:**
> Well I am not kilz, but you should not install flash Kilz's way as it will have the same result. Instead, you have to update the nspluginwrapper package.

I think you should see [this post]("http://ubuntuforums.org/showpost.php?p=4246035&postcount=112").



EDIT (clarity): You should use this method if flash crashes (as in the flash area becomes white or grey and flash cannot be used until the web browser is restarted). So far, this only appears to affect multicore/multiprocessor systems.

I do not believe that the results will be the same unless they install the r115 plugin. Secondly, Saghaulor did not report crashing. So your link may not help.

---

### Post by fatsheep on 2008-02-21
I just want to stop in and say thanks again.  I was having trouble getting some youtube videos to run smoothly and installing this update seems to have fixed the problem.  :)

---

### Post by daradib on 2008-02-21
> **Kilz said:**
> I do not believe that the results will be the same unless they install the r115 plugin. Secondly, Saghaulor did not report crashing. So your link may not help.

Yes, you are correct. I meant the results will be the same if the same flashplugin (r115) is installed, but using your fix.

It is true that Saghaulor did not report "crashing". However, it is likely that the myspace player does not work because flash has crashed (not Firefox).

---

### Post by Kilz on 2008-02-21
> **daradib said:**
> Yes, you are correct. I meant the results will be the same if the same flashplugin (r115) is installed, but using your fix.

It is true that Saghaulor did not report "crashing". However, it is likely that the myspace player does not work because flash has crashed (not Firefox).

r115 is very buggy, I dont recommend it to anyone. I am seriously considering removing the r115 script from my howto. I think the problem could be solved simply by using r48.

---

### Post by daradib on 2008-02-21
r115 is buggy, but it does fix a lot of major security vulnerabilities, which is why it is important to use.

Alas, you can install flashplugin 9.0.48.0 through the Ubuntu 7.10 repositories.

The problem is that Adobe mixed critical security fixes with major changes (causing instability, lack of support for Konqueror and non-current-beta versions of Opera).

---

### Post by Saghaulor on 2008-02-21
Kilz, and everyone else who responded to my post, but especially Kilz for his/her awesome script, thank you so much.

I installed Swiftweasel at your suggestion in another thread, and I also used your flash amd64 script. 

I can now view the myspace music player. Thank you so much.

---

### Post by TomSwift on 2008-02-21
Thanks Kilz, you rock.  I wish I hadn't read this stickey last..  That took under 2 minutes with a reboot.

Again thanks.

---

### Post by u0330v on 2008-02-23
Thank you, Kilz! 

Amazing, I simply followed the instructions you outlined on the first page of this thread and bam, Flash is now finally working **properly** for me. This is fantastic!

Initially, after I got Ubuntu installed on my laptop I think I installed Flash simply by clicking on the "Install Missing Plugins..." notification in Firefox when I tried to view a video on some site. Then I was able to view some videos but not all, and there were some other weird problems. Then I tried installing "flashplugin-nonfree" when I found [this thread]("http://ubuntuforums.org/showthread.php?t=341727") on this forum but Flash still didn't work properly. I'm glad I found your post about the "flashplugin-nonfree" problem which led me to your thread here.

So the problems with Flash for me were, specifically, videos that showed text were garbled and illegible (i.e., if you made a YouTube how-to video showing the commands you typed into the Terminal CLI and the resulting system outputs, all of that text would be garbled and mixed together and I wouldn't be able to read it or follow along). Another problem was that the Flash player controls were out of whack. On the bottom of each YouTube video there are the Play/Pause, Rewind, Progress bar, Time, Volume control, and the two Screen adjust things. In my Firefox, the Time indicator and Volume control was overlapping with the Progress bar and it wouldn't let me adjust the volume, and the two Screen controls didn't work either.

To make a long story short, when I got to the Adobe About Flash page ([http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)), it showed that my browser had Version 8.[some other numbers I can't remember] installed. I don't know why this older version was installed automatically, but I definitely remember the first number was an 8. And this was the problem that was causing the video problems for me because after I followed your instructions and installed the r48 plugin, now everything is working like a charm. No more garbled text and the video controls are displayed normally and are fully functional now. Thanks again.

P.S. Nice puppies, they are sooooo cute :)

---

### Post by doorknob60 on 2008-02-24
Works great! Thanks! Except the version you said was buggy is unusably buggy but the other one works :P

---

### Post by fetisha on 2008-02-24
Ok, well, on flas sites I actually see something, so I guess I'm in the right direction, but it says I need the newer version on the sites. These are the results of what you asked for:

ls -al /usr/lib/mozilla//plugins/ gave me:
total 12
drwxr-xr-x 2 justin users 4096 2008-02-24 02:34 .
drwxr-xr-x 3 root   root  4096 2008-02-23 13:46 ..
lrwxrwxrwx 1 justin users   39 2008-02-23 16:59 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root   root    60 2008-02-24 02:34 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

and ls -al /usr/lib/firefox/plugins/ gave me:
total 20
drwxr-xr-x 2 justin users 4096 2008-02-24 02:34 .
drwxr-xr-x 5 root   root  4096 2007-10-15 21:00 ..
lrwxrwxrwx 1 justin users   39 2008-02-23 16:59 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
-rw-r--r-- 1 justin users 9104 2007-10-08 11:11 libunixprintplugin.so

---

### Post by Kilz on 2008-02-24
> **fetisha said:**
> Ok, well, on flas sites I actually see something, so I guess I'm in the right direction, **but it says I need the newer version on the sites**. These are the results of what you asked for:



What sites are you referring to? can you give me a link?

---

### Post by NCLI on 2008-02-24
I'm trying to install flash on hardy 64-bit, but I haven't had any success using this script, or nay other methods I could think of.

It installs just fine, but doesn't show up in about:plugins, and nothing works.

> seph@seph-laptop:~$ ls -al /usr/lib/mozilla//plugins/
total 32
drwxr-xr-x 2 seph users  4096 2008-02-24 16:50 .
drwxr-xr-x 4 root root   4096 2008-02-19 11:03 ..
-rw-r--r-- 1 root root  19456 2007-01-05 20:52 libflash-mozplugin.so
lrwxrwxrwx 1 seph users    38 2008-02-22 20:43 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 seph users    60 2008-02-24 02:31 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
seph@seph-laptop:~$ ls -al /usr/lib/firefox/plugins/
total 12
drwxr-xr-x 2 seph users 4096 2008-02-24 16:52 .
drwxr-xr-x 4 root root  4096 2008-02-24 02:31 ..
lrwxrwxrwx 1 root root    42 2008-02-24 16:52 libflashplayer.so -> /usr/flashplugin-nonfree/libflashplayer.so
lrwxrwxrwx 1 seph users   60 2008-02-24 02:31 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so


---

### Post by fetisha on 2008-02-24
> **Kilz said:**
> What sites are you referring to? can you give me a link?
Yeah, marilynmanson.com says "MarilynManson.com requires that you have the latest version of
Macromedia Flash Player" which is better than what I was seeing before (which was nothing) and so does [http://www.courtneylove.com/](http://www.courtneylove.com/)

---

### Post by Kilz on 2008-02-24
> **NCLI said:**
> I'm trying to install flash on hardy 64-bit, but I haven't had any success using this script, or nay other methods I could think of.

It installs just fine, but doesn't show up in about:plugins, and nothing works.

Are you running Hardy Heron?

---

### Post by Kilz on 2008-02-24
> **fetisha said:**
> Yeah, marilynmanson.com says "MarilynManson.com requires that you have the latest version of
Macromedia Flash Player" which is better than what I was seeing before (which was nothing) and so does [http://www.courtneylove.com/](http://www.courtneylove.com/)

rerun the script for r48

---

### Post by fetisha on 2008-02-24
> **Kilz said:**
> rerun the script for r48

Pardon? I have no idea what that means. Total newbi :-x

---

### Post by Kilz on 2008-02-24
> **fetisha said:**
> Pardon? I have no idea what that means. Total newbi :-x

There are 2 scripts on the first post in this topic that install flash. I am suggesting that you run the script again. Making sure it was the r48 script that you install.

---

### Post by fetisha on 2008-02-24
> **Kilz said:**
> There are 2 scripts on the first post in this topic that install flash. I am suggesting that you run the script again. Making sure it was the r48 script that you install.

Yes, it was the first script on the post, I remember now.

---

### Post by Curious65 on 2008-02-24
> **Kilz said:**
> By reading your post at 836 , I see you have chosen to install the r115 (Very Buggy) script. Please run the r48.

please excuse the delay in responding.

i'm running the r115 script on the non 64 bit machine and it runs fine. it's the AMD64 machine that acts up and that has the r48 script. 

however right now my windows XP pro non dual boot box (which was working fine) has gone into continuous rebooting and my primary linux box has reassigned the IP address so the windows boxes with zone alarm no longer allow it. once i get all that figured out and fixed i'll work on the flash some more. 

i do appreciate ll you done in answering and for the community in general.

---

### Post by fetisha on 2008-02-24
> **Kilz said:**
> There are 2 scripts on the first post in this topic that install flash. I am suggesting that you run the script again. Making sure it was the r48 script that you install.

Alright, I ran the r48 script again to see what would happen and it told me this:

 "The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect."

I type in the username and it tells me this:

"chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory




 Everything has been installed 
 Once you read this you can close this terminal 
 window. If you have a browser running you 
 will need to restart it."

I'm guessing that "chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory" is not a good thing for it to be saying?

---

### Post by Kilz on 2008-02-24
> **fetisha said:**
> Alright, I ran the r48 script again to see what would happen and it told me this:

 "The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect."

I type in the username and it tells me this:

"chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory




 Everything has been installed 
 Once you read this you can close this terminal 
 window. If you have a browser running you 
 will need to restart it."

I'm guessing that "chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory" is not a good thing for it to be saying?

looking at your past posts , it looks like you are not downloading the install files.  Im going to need more info than this, can you run the script again and copy/paste the whole thing from the start to a post here.

---

### Post by fetisha on 2008-02-24
> **Kilz said:**
> looking at your past posts , it looks like you are not downloading the install files.  Im going to need more info than this, can you run the script again and copy/paste the whole thing from the start to a post here.

Ok, everything that shows up is as follows:

justin@fag:~$ '/home/justin/Desktop/nspluginwrapper install/GetFlash'
mkdir: cannot create directory `/tmp/ffplug': File exists

 This script is used to setup Flash and nspluginwrapper 
 for use in 64bit Firefox or other mozilla based browsers 

 Please select the version of the Ubuntu you are installing to. 
 Install options are : 

 1. Dapper Drake v6.06 or Edgy Eft 6.10 
 2. Feisty Fawn v 7.04 
 3. Gutsy Gibbon 

Install option (1-3)? :3    
 Gutsy Gibbon 
[sudo] password for justin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nspluginwrapper*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libcompizconfig0 libcompizconfig-backend-gconf libboost-thread1.34.1
  libboost-date-time1.34.1 libgnome-window-settings1
  compiz-fusion-plugins-extra libemeraldengine0 compiz-fusion-plugins-main
  compiz-gnome
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflash-mozplugin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libcompizconfig0 libcompizconfig-backend-gconf libboost-thread1.34.1
  libboost-date-time1.34.1 libgnome-window-settings1
  compiz-fusion-plugins-extra libemeraldengine0 compiz-fusion-plugins-main
  compiz-gnome
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflash0c2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libcompizconfig0 libcompizconfig-backend-gconf libboost-thread1.34.1
  libboost-date-time1.34.1 libgnome-window-settings1
  compiz-fusion-plugins-extra libemeraldengine0 compiz-fusion-plugins-main
  compiz-gnome
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libcompizconfig0 libcompizconfig-backend-gconf libboost-thread1.34.1
  libboost-date-time1.34.1 libgnome-window-settings1
  compiz-fusion-plugins-extra libemeraldengine0 compiz-fusion-plugins-main
  compiz-gnome
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libcompizconfig0 libcompizconfig-backend-gconf libboost-thread1.34.1
  libboost-date-time1.34.1 libgnome-window-settings1
  compiz-fusion-plugins-extra libemeraldengine0 compiz-fusion-plugins-main
  compiz-gnome
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libcompizconfig0 libcompizconfig-backend-gconf libboost-thread1.34.1
  libboost-date-time1.34.1 libgnome-window-settings1
  compiz-fusion-plugins-extra libemeraldengine0 compiz-fusion-plugins-main
  compiz-gnome
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libswfdec0.3-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3 for regex 'libswfdec*'
Note, selecting libswfdec0.4 for regex 'libswfdec*'
Note, selecting libswfdec-dev for regex 'libswfdec*'
Note, selecting libswfdec0.5-1 for regex 'libswfdec*'
Note, selecting libswfdec0.4-dbg for regex 'libswfdec*'
Note, selecting libswfdec0.4-dev for regex 'libswfdec*'
Note, selecting libswfdec0.5-1-dbg for regex 'libswfdec*'
Note, selecting libswfdec0.5-dev for regex 'libswfdec*'
E: Couldn't find package libswfdec*
mkdir: cannot create directory `/tmp/nsplugwrapper': File exists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
--19:58:34--  [http://home.comcast.net/~ubuntume/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb](http://home.comcast.net/~ubuntume/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb)
           => `flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

dpkg: error processing flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Errors were encountered while processing:
 flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb
--19:58:34--  [http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6_amd64.deb](http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6_amd64.deb)
           => `nspluginwrapper_0.9.91.6_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

dpkg: error processing flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
dpkg: error processing nspluginwrapper_0.9.91.6_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Errors were encountered while processing:
 flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb
 nspluginwrapper_0.9.91.6_amd64.deb
sudo: nspluginwrapper: command not found




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.
justin
chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory




 Everything has been installed 
 Once you read this you can close this terminal 
 window. If you have a browser running you 
 will need to restart it. 
justin@fag:~$

---

### Post by Kilz on 2008-02-24
Here is the problem

package architecture (amd64) does not match system (i386)

You have a 32bit operating system. The script is setup to install flash to the amd64 version of Ubuntu.

---

### Post by fetisha on 2008-02-24
> **Kilz said:**
> Here is the problem

package architecture (amd64) does not match system (i386)

You have a 32bit operating system. The script is setup to install flash to the amd64 version of Ubuntu.

Oh, so do you know anything I can do? What options I have?

---

### Post by Kilz on 2008-02-24
> **fetisha said:**
> Oh, so do you know anything I can do? What options I have?

[Download the flash plugin from adobe]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz"), extract it, and copy it into /usr/lib/mozilla/plugins. If you have a 64bit computer you could also consider replacing the operating system to 64bit.

---

### Post by fetisha on 2008-02-24
> **Kilz said:**
> [Download the flash plugin from adobe]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz"), extract it, and copy it into /usr/lib/mozilla/plugins. If you have a 64bit computer you could also consider replacing the operating system to 64bit.

I did that and it's not working. I thought I couldn't install the adobe flash player because I have an Athlon 64 X2 Dual-Core Processor 5200, and flash doesn't support it? I also tried downloading it when firefox tells me to install missing pluins, and it doesn't work that way either. When I install the gnash plug in, it works for youtube( sort of, the menu at the bottom of the flash window is all weird), but not for anything else (like marilynmanson.com and courtneylove.com, where instead of it telling me to download the latest version of flash, it just doesn't show anything but a black screen)

Edit: How would I know if I have a 64 bit computer? Does Xubuntu have a 64 bit version?

---

### Post by Kilz on 2008-02-25
> **fetisha said:**
> I did that and it's not working. I thought I couldn't install the adobe flash player because I have an Athlon 64 X2 Dual-Core Processor 5200, and flash doesn't support it? I also tried downloading it when firefox tells me to install missing pluins, and it doesn't work that way either. When I install the gnash plug in, it works for youtube( sort of, the menu at the bottom of the flash window is all weird), but not for anything else (like marilynmanson.com and courtneylove.com, where instead of it telling me to download the latest version of flash, it just doesn't show anything but a black screen)

Edit: How would I know if I have a 64 bit computer? Does Xubuntu have a 64 bit version?

The processor you have (hardware) doesnt make any difference. Its the operating system. Make sure to uninstall and delete all other flash plugins and wrappers when copying over the plugin from adobe. The most common problem people face is leaving the files from failed installs in place. This can cause conflicts. 
If you have a Athlon X2 Dual-Core Processor 5200, its 64bit . But check the specs of your computer from the manufacturer.  Yes Xubuntu has a 64bit version, though its a lot of work just to get flash to work,.

---

### Post by DpNo1 on 2008-02-25
Just downloaded and installed, worked straight away and i was surfing on youtube in no time :D

I can't thank you enough, as this is the second time i have tried installing linux in a dual boot with windows, and the first time i just couldn't get flash working and gave up.

Thanks again :)

Dp

---

### Post by fetisha on 2008-02-25
> **Kilz said:**
> The processor you have (hardware) doesnt make any difference. Its the operating system. Make sure to uninstall and delete all other flash plugins and wrappers when copying over the plugin from adobe. The most common problem people face is leaving the files from failed installs in place. This can cause conflicts. 
If you have a Athlon X2 Dual-Core Processor 5200, its 64bit . But check the specs of your computer from the manufacturer.  Yes Xubuntu has a 64bit version, though its a lot of work just to get flash to work,.

Well, I know for a fact that the first thing I tried was just installing the adobe plugin, but I read that AMD 64 chips didn't support flash, which I thought would explain why it didn't work. So now I know I have a 64 bit computer, I don't know what version of Xubuntu I downloaded (I just got it off the 'get ubuntu' page and it didn't say) so I downloaded and burned a copy of Ubuntu 7.10 for 64 bit computers to get rid of my current install (it's only 4 days old, I don't care if it wipes everything clean) but it doesn't want to run the install program. Would installing the 64 bit version even fix my problem?

---

### Post by Kilz on 2008-02-25
> **fetisha said:**
> Well, I know for a fact that the first thing I tried was just installing the adobe plugin, but I read that AMD 64 chips didn't support flash, which I thought would explain why it didn't work. So now I know I have a 64 bit computer, I don't know what version of Xubuntu I downloaded (I just got it off the 'get ubuntu' page and it didn't say) so I downloaded and burned a copy of Ubuntu 7.10 for 64 bit computers to get rid of my current install (it's only 4 days old, I don't care if it wipes everything clean) but it doesn't want to run the install program. Would installing the 64 bit version even fix my problem?

You could run the script if you did install the 64bit version, that would solve this problem.  Since your install is only 4 days old, you wouldnt loose all that much setup. But its up to you. 
But the fact that it wouldnt install may mean you dont have a 64bit system. Can you give me a little info about your computer like the make and model? Perhaps the manufacturer has spec's.

---

### Post by fetisha on 2008-02-25
> **Kilz said:**
> You could run the script if you did install the 64bit version, that would solve this problem.  Since your install is only 4 days old, you wouldnt loose all that much setup. But its up to you. 
But the fact that it wouldnt install may mean you dont have a 64bit system. Can you give me a little info about your computer like the make and model? Perhaps the manufacturer has spec's.

Ok, this is what I have

have Xubuntu 7.10 32 bit version
Shuttle SN68SG2
AMD Athlon 64 X2 5200
160 Serial ATA
1gig memory

---

### Post by Kilz on 2008-02-25
> **fetisha said:**
> Ok, this is what I have

have Xubuntu 7.10 32 bit version
Shuttle SN68SG2
AMD Athlon 64 X2 5200
160 Serial ATA
1gig memory

Nice looking little computer. I will have to file it away for the future.  Looks like its 64bit. 
Ok, [go here ]("http://www.xubuntu.org/get#gutsy"). select a mirror near you, and get the 64bit alternate install disk. [Check the md5sum ]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/7.10/release/MD5SUMS") before you burn the iso file. Just open a terminal, navigate to the file and type md5sum filename. If its on the desktop these 2 comands will work. 
```
cd ~/Desktop
md5sum xubuntu-7.10-alternate-amd64.iso
```
It will give a hash of the file, it should match the hash listed in that list. Then use any cd burning application to burn the image to a cd. K3b and brasero work best.
The alternate cd is better to use for the 64bit version in most cases. Its not a live cd, but it works.

---

### Post by lakefire on 2008-02-25
Worked perfectly.  Thanks, and I have been dealing with this issue for months only to think there was nothing I could do about it.  It's people like you that make this OS great!

---

### Post by Jeratt on 2008-02-25
> **Eddie Mac said:**
> I'm also having this problem... I need to move the cursor off the embedded flash before I can click on it a second time.  I am running Firefox 2.0.0.6 and Feisty Fawn 7.04 and have run the script multiple times.

Any ideas?


Same for me. I'm running Gutsy with Firefox 2.0.0.12.

ls -al /usr/lib/mozilla//plugins/ results in:

```
total 6900
drwxr-xr-x 2 jasper users    4096 2008-02-23 17:01 .
drwxr-xr-x 3 root   root     4096 2007-10-15 19:27 ..
-rwxr-xr-x 1 jasper users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 jasper users      39 2008-01-29 17:24 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 jasper users      36 2008-01-22 08:11 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 jasper users      37 2008-01-22 08:11 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 jasper users      34 2008-01-22 08:11 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 jasper users      35 2008-01-22 08:11 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 jasper users      36 2008-01-22 08:11 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 jasper users      37 2008-01-22 08:11 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 jasper users      42 2008-01-22 08:11 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 jasper users      43 2008-01-22 08:11 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 jasper users      60 2008-02-23 17:01 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

and ls -al /usr/lib/firefox/plugins/ is

```
total 24
drwxr-xr-x 2 jasper users  4096 2008-02-23 17:01 .
drwxr-xr-x 5 root   root   4096 2008-02-08 08:02 ..
lrwxrwxrwx 1 jasper users    39 2008-01-29 17:24 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 jasper users    36 2008-01-22 08:10 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 jasper users    37 2008-01-22 08:10 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 jasper users    34 2008-01-22 08:10 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 jasper users    35 2008-01-22 08:10 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 jasper users    36 2008-01-22 08:10 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 jasper users    37 2008-01-22 08:10 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 jasper users    42 2008-01-22 08:10 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 jasper users    43 2008-01-22 08:10 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 jasper users 11456 2008-02-07 06:07 libunixprintplugin.so
lrwxrwxrwx 1 jasper users    60 2008-02-23 17:01 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

Is there a solution to this problem in one of those other 90 pages I was too bored to look through? Maybe this should have it's own child forum for easier viewing.

---

### Post by fetisha on 2008-02-25
> **Kilz said:**
> Nice looking little computer. I will have to file it away for the future.  Looks like its 64bit. 
Ok, [go here ]("http://www.xubuntu.org/get#gutsy"). select a mirror near you, and get the 64bit alternate install disk. [Check the md5sum ]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/7.10/release/MD5SUMS") before you burn the iso file. Just open a terminal, navigate to the file and type md5sum filename. If its on the desktop these 2 comands will work. 
```
cd ~/Desktop
md5sum xubuntu-7.10-alternate-amd64.iso
```
It will give a hash of the file, it should match the hash listed in that list. Then use any cd burning application to burn the image to a cd. K3b and brasero work best.
The alternate cd is better to use for the 64bit version in most cases. Its not a live cd, but it works.

I don't know what you mean by check the mdsum file. There's one in the CD when I burned it, but I don't know what to do with it. When I burned the iso and the CD was on my desktop and I typed what you told me to in the ternimal nothing happened. When I burned the CD, it told me to upgrade but gave me this error:
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found

---

### Post by Kilz on 2008-02-25
> **fetisha said:**
> I don't know what you mean by check the mdsum file. There's one in the CD when I burned it, but I don't know what to do with it. When I burned the iso and the CD was on my desktop and I typed what you told me to in the ternimal nothing happened. When I burned the CD, it told me to upgrade but gave me this error:
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found

That link says it is trying to download i386 or 32bit packages. Are you sure you downloaded a amd64 or 64bit disk image? The commands in my last post to you were for checking the image file before you burned the cd to make sure it was good before wasting a cd on a bad image file. The md5sum is able to check the image against a md5sum of the file on the server.
This is getting very off topic. Please make a new post about your install issues and I will help you there.

---

### Post by Kilz on 2008-02-25
> **Jeratt said:**
> Same for me. I'm running Gutsy with Firefox 2.0.0.12.

Is there a solution to this problem in one of those other 90 pages I was too bored to look through? Maybe this should have it's own child forum for easier viewing.

Please give me the results of ```
uname -a
```

---

### Post by fetisha on 2008-02-25
> **Kilz said:**
> That link says it is trying to download i386 or 32bit packages. Are you sure you downloaded a amd64 or 64bit disk image? The commands in my last post to you were for checking the image file before you burned the cd to make sure it was good before wasting a cd on a bad image file. The md5sum is able to check the image against a md5sum of the file on the server.
This is getting very off topic. Please make a new post about your install issues and I will help you there.

Cool, thanks. The new post is here: [http://ubuntuforums.org/showthread.php?p=4405756#post4405756](http://ubuntuforums.org/showthread.php?p=4405756#post4405756)

---

### Post by fatsheep on 2008-02-25
I posted originally saying this worked (and it does) but I've been noticing the sound isn't synchronized with the video quite right.  When people talk, you notice it.  There is some delay.  I know it's not a show stopper but what would you recommend me doing to remedy this?  This is on a fresh install of 7.10 by the way...

```
**fatsheep@fatsheep-desktop:~$ ls -al /usr/lib/mozilla//plugins/**
total 6900
drwxr-xr-x 2 root     users    4096 2008-02-25 17:38 .
drwxr-xr-x 3 root     root     4096 2007-10-15 19:27 ..
-rwxr-xr-x 1 fatsheep users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 root     users      36 2008-02-25 11:36 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root     users      37 2008-02-25 11:36 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root     users      34 2008-02-25 11:36 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root     users      35 2008-02-25 11:36 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root     users      36 2008-02-25 11:36 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root     users      37 2008-02-25 11:36 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root     users      42 2008-02-25 11:36 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root     users      43 2008-02-25 11:36 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 root     users      60 2008-02-25 17:38 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
**fatsheep@fatsheep-desktop:~$ ls -al /usr/lib/firefox/plugins/**
total 24
drwxr-xr-x 2 root users  4096 2008-02-25 17:38 .
drwxr-xr-x 5 root root   4096 2008-02-25 17:28 ..
lrwxrwxrwx 1 root users    36 2008-02-25 11:35 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root users    37 2008-02-25 11:35 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root users    34 2008-02-25 11:35 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root users    35 2008-02-25 11:35 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root users    36 2008-02-25 11:35 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root users    37 2008-02-25 11:35 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root users    42 2008-02-25 11:35 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root users    43 2008-02-25 11:35 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root users 11456 2008-02-07 06:07 libunixprintplugin.so
lrwxrwxrwx 1 root users    60 2008-02-25 17:38 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
**fatsheep@fatsheep-desktop:~$ uname -a**
Linux fatsheep-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

```

---

### Post by Kilz on 2008-02-25
> **fatsheep said:**
> I posted originally saying this worked (and it does) but I've been noticing the sound isn't synchronized with the video quite right.  When people talk, you notice it.  There is some delay.  I know it's not a show stopper but what would you recommend me doing to remedy this?  This is on a fresh install of 7.10 by the way...



Im not sure, I have never run across it before.

---

### Post by fetisha on 2008-02-26
Works great now. Thank you.

---

### Post by fatsheep on 2008-02-26
I see some people have mentioned that they must move the cursor outside of the flash window before they can click a second time.  I had the same problem before I disabled desktop effects in System>Preferences>Appearance (Visual Effects tab).  Try doing that and see if it fixes the problem.  :popcorn:

---

### Post by soulcxfor on 2008-02-26
Hi,

I have read a lot of the comments from time to time since December 2007 when I got my laptop and installed Xubuntu 7.10.

The script does not complete for me because of a dependency problem. The problem is ia32-libs.
I saw in comment #883 in this thread that this was also problem during that users install and I got a similar error.

Basically I have ia32-libs version 2.1ubuntu3 which is not compatible with what the script tries to install.

I have found this info for why (probably?) the script does not work:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/155015](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/155015)
and some info on ia32-libs versions
[https://launchpad.net/ubuntu/+source/ia32-libs/](https://launchpad.net/ubuntu/+source/ia32-libs/)

It does not seem possible to use the package manager to fix this. I have been thinking of downloading a .deb file and install it but I do not know if it will resolve the problem and from what I have read deb files can screw with the system if one does not have knowledge about dependencies for the deb file.

The solution seems to be to downgrade ia32-libs as indicated in [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/155015](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/155015)
but I do not know how one "downgrades" correctly.

I should mention that I want to use Swiftweasel +flash.

I have not made any "system" upgrades which I know of since I got the Xubuntu 7.10 amd64 image file in late December onto my dell inspiron 1720  laptop.

I hope someone has a solution to the script not being able to complete due to the ia32-libs AND its dependencies.


Thanks
Soul4

---

### Post by Kilz on 2008-02-26
> **soulcxfor said:**
> Hi,

I have read a lot of the comments from time to time since December 2007 when I got my laptop and installed Xubuntu 7.10.

The script does not complete for me because of a dependency problem. The problem is ia32-libs.
I saw in comment #883 in this thread that this was also problem during that users install and I got a similar error.


The problem in [post 883]("http://ubuntuforums.org/showpost.php?p=4398409&postcount=883") is that the user had a 32bit i386 version installed and not the 64bit version of Xubuntu. 
Please provide the results of the following, open a terminal and type this.
```
uname -a
```
It will be one line, copy and pate the results here in a post.

---

### Post by Kilz on 2008-02-26
> **fatsheep said:**
> I see some people have mentioned that they must move the cursor outside of the flash window before they can click a second time.  I had the same problem before I disabled desktop effects in System>Preferences>Appearance (Visual Effects tab).  Try doing that and see if it fixes the problem.  :popcorn:

The ting is, desktop effects can be addictive. I recently got them working with my ati card (yes finally). Once you have them its hard to give them up.

---

### Post by soulcxfor on 2008-02-26
I am sure I have 64 bit. I think uname gives "...Linux... x64" something.

The links I posted shows that this is a problem for many too.

/soul4

---

### Post by soulcxfor on 2008-02-26
> **Kilz said:**
> The ting is, desktop effects can be addictive. I recently got them working with my ati card (yes finally). Once you have them its hard to give them up.

I am sure I have 64 bit. I think uname gives "...Linux... x64" something.

The links I posted shows that this is a problem for many too.

/soul4

uname gives

Linux computername 2.6.22-14-generic #1 SMP "date" x86_64 GNU/Linux

---

### Post by Kilz on 2008-02-26
> **soulcxfor said:**
> I am sure I have 64 bit. I think uname gives "...Linux... x64" something.

The links I posted shows that this is a problem for many too.

/soul4

uname gives

Linux computername 2.6.22-14-generic #1 SMP "date" x86_64 GNU/Linux

The thing is, the nspluginwrapper package only needs ia32-libs version 1.6 or higher. 2.2 is way over that. Id like to see whats going on during the install. Can you try and install, then copy the entire install to a txt file and attach it to a post here?

---

### Post by premodern on 2008-02-26
This worked in my brand new AMD64 Kubuntu system, thanks !

A minor point is that double-clicking the script did not work so I had to do the usual way: ./GetFlash in the terminal. Just to let you know.

---

### Post by soulcxfor on 2008-02-27
> **Kilz said:**
> The thing is, the nspluginwrapper package only needs ia32-libs version 1.6 or higher. 2.2 is way over that. Id like to see whats going on during the install. Can you try and install, then copy the entire install to a txt file and attach it to a post here?

I have attached log.txt.
Before I ran the script I manually perfomred the package removal and file deletes as done in the script file.

I looked through the log and it says that ia32-libs is not installed.
I started synaptic package manager and filtered for >installed< packages and
ia32-libs showed up with version 2.1ubuntu3.

Hope you can find what I am doing wrong.

Thank you for your time, Soul4

---

### Post by Kilz on 2008-02-27
You have a problem, from the txt file

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32gcc1 but it is not going to be installed
             Depends: libc6-i386 (>= 2.3.6-2) but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32asound2 but it is not going to be installed
             Depends: lib32ncurses5 but it is not going to be installed

This is a serious package problem.  Add to the fact that synaptic says the files exist, even bigger issue. It is something I am not sure about. My best guesss would be to look at the /etc/apt/sources.list to see if there is something wrong. 
I also wonder, did you do a clean install of gutsy, or was it an upgrade of feisty? What Ubuntu version upgrade history before that?

---

### Post by soulcxfor on 2008-02-27
> **Kilz said:**
> You have a problem, from the txt file

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32gcc1 but it is not going to be installed
             Depends: libc6-i386 (>= 2.3.6-2) but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32asound2 but it is not going to be installed
             Depends: lib32ncurses5 but it is not going to be installed

This is a serious package problem.  Add to the fact that synaptic says the files exist, even bigger issue. It is something I am not sure about. My best guesss would be to look at the /etc/apt/sources.list to see if there is something wrong. 
I also wonder, did you do a clean install of gutsy, or was it an upgrade of feisty? What Ubuntu version upgrade history before that?


That does not sound fun ;)

Well what could be "wrong" with the sources.list? Sounds hard to find a problem as (if I understand it correctly) only lists where to get installable "software" from.

I did not perform an upgrade, I installed from a binary image downloaded from the Xubuntu site. I have been doing stuff to get my graphics to work (nividia drivers) + composite window manager. Also "linux backports" to get the sound to work.

I am using my windows-box when writing this but a while ago I tried to do something with the ia32-libs in synaptic but  I didn't because I think it said that just about every program had a dependency - it looked like it wanted to reinstall A LOT of program... but I am somewhat of a beginner with linux so I may have misunderstood.


But I do remember from my previous post that lib32gcc1 was present in synaptic package manager when I filtered for installed packages - so perhaps synaptic is confused somehow.

Do you have any tip on where I can start looking, perhaps here on the forum or so?

Thanks for you help!

Edit1:
It seems that ia32-libs is not installed after all, but apt-get wont install it either. I have removed third party repositories I had before except for swiftweasel.
I also have "main", "universe", "restricted", and "multiverse" enabled. I am guessing that the restricted nvidia drivers may be causing the problem.. but I am just guessing.

I just read that something called libc-i386 replaces ia32-libs is from bugs.launchpad.net  bug number 49490 but I don't know.

I really do not know how to continue from here, if I cant get information on how to override what synaptic does.

---

### Post by soulcxfor on 2008-02-27
Well it seems to be solved now!

Thank you Kilz!

I found a website where someone was having the exact same problem with ia32-libs and ubuntu 7.10 x64:
[https://answers.launchpad.net/ubuntu/+source/ia32-libs/+question/15484](https://answers.launchpad.net/ubuntu/+source/ia32-libs/+question/15484)

The info I got interested in was:
"Most probably the mirror you are using is not up to date. Try again in half an hour or so and it should be ok."

So I found another site which explained a little about the package manger and what happens when you press the "status" button in the manager GUI.

I removed all "Installed (.. config)"  packages then (here comes the solution) I went to "Settings->Repositories" (in synaptic packet manager) and in the popup I clicked the dropdown with label "Download from" and clicked "other". There is an option to choose "best server" which I did.. it took awhile but it finally chose one.

After performing a reload of all the packages (using this new mirror) I found ia32-lib and simply installed it :)

Then I ran Kilz script and now I am looking at youtube flash videos :)

So the whole problem seems to have been a bad repository mirror.

Thanks Kilz and hope this can help some others  :)

Im out / Soul4

---

### Post by hebetude on 2008-02-28
Hardy 64bit flashplugin-nonfree still doesn't use /etc/apt/apt.conf to configure proxy settings.  I had to manually change /etc/wgetrc with my user/pw to get the script to download the plugin.  /root/.wgetrc ~/.wgetrc were not read either.

This is quite annoying/insecure.  I wish gnash suported flash9, clearly the flashplugin-nonfree maintainers care as little about 32bit flash as I do.

---

### Post by blondieoubre on 2008-02-28
hen reporting problems please include the results of these commands. You can copy 
and paste them into a terminal one at a time. You do not have to type them. 

 ls -al /usr/lib/mozilla//plugins/
total 6900
drwxr-xr-x 2 umakutti users    4096 2008-02-28 16:55 .
drwxr-xr-x 3 root     root     4096 2007-10-15 18:27 ..
-rwxr-xr-x 1 umakutti users 7040036 2007-06-19 19:31 libflashplayer.so
lrwxrwxrwx 1 umakutti users      36 2008-02-26 19:01 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 umakutti users      37 2008-02-26 19:01 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 umakutti users      34 2008-02-26 19:01 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 umakutti users      35 2008-02-26 19:01 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 umakutti users      36 2008-02-26 19:01 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 umakutti users      37 2008-02-26 19:01 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 umakutti users      42 2008-02-26 19:01 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 umakutti users      43 2008-02-26 19:01 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 umakutti users      60 2008-02-28 16:55 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

 ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 umakutti users  4096 2007-10-15 18:27 .
drwxr-xr-x 5 root     root   4096 2007-10-15 18:32 ..
lrwxrwxrwx 1 umakutti users    36 2008-02-26 19:01 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 umakutti users    37 2008-02-26 19:01 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 umakutti users    34 2008-02-26 19:01 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 umakutti users    35 2008-02-26 19:01 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 umakutti users    36 2008-02-26 19:01 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 umakutti users    37 2008-02-26 19:01 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 umakutti users    42 2008-02-26 19:01 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 umakutti users    43 2008-02-26 19:01 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 umakutti users 11456 2007-10-08 10:34 libunixprintplugin.so

locate libflashplayer.so
returned nothing.

uname -a
Linux umakutti-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

I installed the r48 plugin and I still can't get flash to work.  I have Gutsy Gibbon 7.10

I'm new to linux & to having a 64bit processor.

---

### Post by blondieoubre on 2008-02-28
*points to previous posts*

I figured I should add that I have been unable to add *any* plugins since I installed the OS yesterday.

---

### Post by Estesark on 2008-02-28
This is great - I was having trouble with the "flashplugin-nonfree" package. Some websites weren't showing properly and were just displaying big white spaces where Flash should have been.

The only thing I can't get to work in this is the full screen mode in some applications, for example the BBC iPlayer.

---

### Post by Kilz on 2008-02-29
> **blondieoubre said:**
> *points to previous posts*

I figured I should add that I have been unable to add *any* plugins since I installed the OS yesterday.

Drag the GetFlash script file to the desktop. Open a terminal. Type in , ot copy and paste the following 2 commands.

```
cd ~/Desktop
./GetFlash | tee ~/Desktop/flashlog.txt
```

During this install a file called flashlog.txt will be created.  Go through the whole install, then attach the flashlog.txt file to a post here is flash is still not working.

> **Estesark said:**
> This is great - I was having trouble with the "flashplugin-nonfree" package. Some websites weren't showing properly and were just displaying big white spaces where Flash should have been.

The only thing I can't get to work in this is the full screen mode in some applications, for example the BBC iPlayer.

The r115 plugin is the first Linux plugin with full screen , its also so buggy  its almost unusable for most people. r48 doesnt have full screen but is stable and works. You can try the r115 if you really need full screen, but if you start getting crashes, flash not working on some sites, or any other flash isues install r48 again.

---

### Post by Timokl on 2008-02-29
Thank you. Now it works for me, too! :-D

---

### Post by Estesark on 2008-02-29
> **Kilz said:**
> The r115 plugin is the first Linux plugin with full screen , its also so buggy  its almost unusable for most people. r48 doesnt have full screen but is stable and works. You can try the r115 if you really need full screen, but if you start getting crashes, flash not working on some sites, or any other flash isues install r48 again.

I tried that, with not much luck.

At the moment, I seem to have a number of choices, none of which is perfect:

Install the r48 plug-in as described in this thread.
Pros: Reliable, works on all websites I've tested so far. Good quality.
Cons: No full screen, no slider functionality (for seeking in videos etc), "settings" sometimes causes it to freeze

Install the r115 plug-in as described in this thread.
Pros: Works on most websites. Good quality.
Cons: No full screen (despite what you say), no slider usage, "settings" almost always causes it to freeze

Install the "flashplugin-nonfree" package.
Pros: Full screen, slider functionality, doesn't freeze.
Cons: Does not work on many websites, poor quality (especially in full screen).

Install an alternative player (Gnash, swfdec etc)
Pros: Free, open source.
Cons: Unreliable, do not work fully on most websites and do not work at all on others.

Install a 32-bit version of Firefox and then install the relevant plug-ins. (I haven't tried this yet)
Pros: Seems to be a reliable way of getting everything working.
Cons: I can't help but think "Why should I?", also seems quite fiddly to achieve.

I'm really not having much luck with this. At least on openSUSE the package plug-in had much better quality video, so that was acceptable. None of the alternatives from the list above seem acceptable to me - any advice?

Edit: Also, what's the best way to reverse the installation process described in this thread?

---

### Post by Kilz on 2008-02-29
duplicate post

---

### Post by Kilz on 2008-03-01
> **Estesark said:**
> 
I'm really not having much luck with this. At least on openSUSE the package plug-in had much better quality video, so that was acceptable. None of the alternatives from the list above seem acceptable to me - any advice?
Suse also has full multiarch support with a default 32bit browser. Feel free to ask the developers for that. (ps I wouldnt hold my breath waiting for it to happen if I were you.)
> **Estesark said:**
> 
**Edit: Also, what's the best way to reverse the installation process described in this thread?**

uninstall the nspluginwrapper package and delete the flash plugin from /usr/lib/mozilla/plugins.

---

### Post by ThunderRd on 2008-03-01
I have been trying to get Flash working on my Feisty machine.  Both of the scripts seem to install ok and video works; however I can't get sound working with either one.

I have installed the ia32-alsa package on the first page of the thread.

Other sound works ok, so it's not a hardware problem.

Here is the requested output for help:
```
 thunderrd@Q-6600:~$ ls -al /usr/lib/mozilla//plugins/
total 7956
drwxr-xr-x 2 thunderrd users    4096 2008-03-02 00:01 .
drwxr-xr-x 4 root      root     4096 2008-02-04 20:02 ..
-rwxr-xr-x 1 thunderrd users 8119784 2007-11-21 06:24 libflashplayer.so
lrwxrwxrwx 1 thunderrd users      38 2008-03-01 23:10 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 thunderrd users      36 2008-01-17 23:42 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 thunderrd users      37 2008-01-17 23:42 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 thunderrd users      34 2008-01-17 23:42 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 thunderrd users      35 2008-01-17 23:42 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 thunderrd users      36 2008-01-17 23:42 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 thunderrd users      37 2008-01-17 23:42 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 thunderrd users      42 2008-01-17 23:42 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 thunderrd users      43 2008-01-17 23:42 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 thunderrd users      60 2008-03-02 00:01 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
thunderrd@Q-6600:~$ ls -al /usr/lib/firefox/plugins/
total 24
drwxr-xr-x 2 root root  4096 2008-03-02 00:01 .
drwxr-xr-x 5 root root  4096 2008-02-16 14:49 ..
lrwxrwxrwx 1 root root    54 2008-03-01 23:10 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji_mozilla_firefox.so
lrwxrwxrwx 1 root root    36 2008-01-17 23:42 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2008-01-17 23:42 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2008-01-17 23:42 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2008-01-17 23:42 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2008-01-17 23:42 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2008-01-17 23:42 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2008-01-17 23:42 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2008-01-17 23:42 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2008-02-07 11:45 libunixprintplugin.so
lrwxrwxrwx 1 root root    60 2008-03-02 00:01 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 root root    37 2008-02-04 22:24 npwrapper.so -> /usr/lib/mozilla/plugins/npwrapper.so
lrwxrwxrwx 1 root root     2 2008-02-04 22:26 so -> so
thunderrd@Q-6600:~$ uname -a
Linux Q-6600 2.6.20-16-generic #2 SMP Tue Feb 12 02:11:24 UTC 2008 x86_64 GNU/Linux  
```

---

### Post by CloudFX on 2008-03-02
I tried doing that, but it still doesn't work. Here is the info requested.

**nick@NickPC:~$ ls -al /usr/lib/mozilla//plugins/**
total 6900
drwxr-xr-x 2 nick users    4096 2008-03-02 12:50 .
drwxr-xr-x 3 root root     4096 2007-10-15 16:27 ..
-rwxr-xr-x 1 nick users 7040036 2007-06-19 17:31 libflashplayer.so
lrwxrwxrwx 1 nick users      36 2008-02-01 09:03 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 nick users      37 2008-02-01 09:03 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 nick users      34 2008-02-01 09:03 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 nick users      35 2008-02-01 09:03 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 nick users      36 2008-02-01 09:03 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 nick users      37 2008-02-01 09:03 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 nick users      42 2008-02-01 09:03 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 nick users      43 2008-02-01 09:03 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 nick users      60 2008-03-02 12:50 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

**nick@NickPC:~$ ls -al /usr/lib/firefox/plugins/**
total 24
drwxr-xr-x 2 nick users  4096 2008-03-02 12:50 .
drwxr-xr-x 5 root root   4096 2008-02-23 19:57 ..
lrwxrwxrwx 1 nick users    36 2008-02-01 09:02 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 nick users    37 2008-02-01 09:02 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 nick users    34 2008-02-01 09:02 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 nick users    35 2008-02-01 09:02 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 nick users    36 2008-02-01 09:02 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 nick users    37 2008-02-01 09:02 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 nick users    42 2008-02-01 09:02 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 nick users    43 2008-02-01 09:02 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 nick users 11456 2007-10-08 08:34 libunixprintplugin.so
lrwxrwxrwx 1 nick users    60 2008-03-02 12:50 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

**nick@NickPC:~$ uname -a**
Linux NickPC 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
nick@NickPC:~$

What should I try next?

---

### Post by Kilz on 2008-03-02
> **ThunderRd said:**
> I have been trying to get Flash working on my Feisty machine.  Both of the scripts seem to install ok and video works; however I can't get sound working with either one.

I have installed the ia32-alsa package on the first page of the thread.

Other sound works ok, so it's not a hardware problem.

Here is the requested output for help:
```
 /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
thunderrd@Q-6600:~$ ls -al /usr/lib/firefox/plugins/
total 24
drwxr-xr-x 2 root root  4096 2008-03-02 00:01 .
drwxr-xr-x 5 root root  4096 2008-02-16 14:49 ..
lrwxrwxrwx 1 root root    54 2008-03-01 23:10 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji_mozilla_firefox.so
lrwxrwxrwx 1 root root    36 2008-01-17 23:42 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2008-01-17 23:42 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2008-01-17 23:42 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2008-01-17 23:42 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2008-01-17 23:42 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2008-01-17 23:42 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2008-01-17 23:42 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2008-01-17 23:42 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2008-02-07 11:45 libunixprintplugin.so
lrwxrwxrwx 1 root root    60 2008-03-02 00:01 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
**lrwxrwxrwx 1 root root    37 2008-02-04 22:24 npwrapper.so -> /usr/lib/mozilla/plugins/npwrapper.so**
 
```

It looks like you have files from a previous install still in place.

---

### Post by Kilz on 2008-03-02
> **CloudFX said:**
> I tried doing that, but it still doesn't work. Here is the info requested.

What should I try next?
Please ell me what version of ubuntu you are running. 

Drag the GetFlash script file to the desktop. Open a terminal. Type in , ot copy and paste the following 2 commands.

```
cd ~/Desktop
./GetFlash | tee ~/Desktop/flashlog.txt
```

During this install a file called flashlog.txt will be created. Go through the whole install, then attach the flashlog.txt file to a post here is flash is still not working.

---

### Post by liveB on 2008-03-02
This is getting wierd.  I used GetFlash to install in Hardy and it worked GREAT!

Then I had to reload my system due to libkxavier trashing my x-system.  Now I tried it and I can't play videos (break.com, utube) anymore.  I probably did something differently is my guess, but I can't figure out what.  Please help.

ed@ASUS-Ultra:~/Desktop$ ls -al /usr/lib/mozilla//plugins/
total 6900
drwxr-xr-x 2 ed   users    4096 2008-03-02 17:46 .
drwxr-xr-x 4 root root     4096 2008-02-21 20:58 ..
-rwxr-xr-x 1 ed   users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 ed   users      60 2008-03-02 17:46 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
ed@ASUS-Ultra:~/Desktop$ ls -al /usr/lib/firefox/plugins/
total 12
drwxr-xr-x 2 ed   users 4096 2008-03-02 17:46 .
drwxr-xr-x 4 root root  4096 2008-03-01 07:06 ..
lrwxrwxrwx 1 ed   users   60 2008-03-02 17:46 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
ed@ASUS-Ultra:~/Desktop$ uname -a
Linux ASUS-Ultra 2.6.24-11-generic #1 SMP Fri Feb 29 21:26:31 UTC 2008 x86_64 GNU/Linux


System is ASUS P5NE-SLI, Intel core2 Quad 6600, 2GB memory.

Thanks,

ed

---

### Post by blondieoubre on 2008-03-02
> **Kilz said:**
> Drag the GetFlash script file to the desktop. Open a terminal. Type in , ot copy and paste the following 2 commands.

```
cd ~/Desktop
./GetFlash | tee ~/Desktop/flashlog.txt
```



 This script is used to setup Flash and nspluginwrapper 
 for use in 64bit Firefox or other mozilla based browsers 

 Please select the version of the Ubuntu you are installing to. 
 Install options are : 

 1. Dapper Drake v6.06 or Edgy Eft 6.10 
 2. Feisty Fawn v 7.04 
 3. Gutsy Gibbon 

Install option (1-3)? : Gutsy Gibbon 
Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting nspluginwrapper for regex 'nspluginwrapper*'
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 160kB disk space will be freed.
(Reading database ... 88051 files and directories currently installed.)

Removing flashplugin-nonfree ...

Reading package lists...
Building dependency tree...
Reading state information...
Reading package lists...
Building dependency tree...
Reading state information...
Reading package lists...
Building dependency tree...
Reading state information...
Reading package lists...
Building dependency tree...
Reading state information...
Reading package lists...
Building dependency tree...
Reading state information...
Reading package lists...
Building dependency tree...
Reading state information...
Reading package lists...
Building dependency tree...
Reading state information...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 88046 files and directories currently installed.)
Unpacking flashplugin-nonfree (from flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.999.0.2+really0ubuntu12) ...
(Reading database ... 88052 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.999.0.2+really0ubuntu12 (using flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Unpacking replacement flashplugin-nonfree ...
Selecting previously deselected package nspluginwrapper.
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.6_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.999.0.2+really0ubuntu12) ...




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.




 Everything has been installed 
 Once you read this you can close this terminal 
 window. If you have a browser running you 
 will need to restart it.

---

### Post by CloudFX on 2008-03-02
> **Kilz said:**
> Please ell me what version of ubuntu you are running. 

Drag the GetFlash script file to the desktop. Open a terminal. Type in , ot copy and paste the following 2 commands.

```

 This script is used to setup Flash and nspluginwrapper 
 for use in 64bit Firefox or other mozilla based browsers 

 Please select the version of the Ubuntu you are installing to. 
 Install options are : 

 1. Dapper Drake v6.06 or Edgy Eft 6.10 
 2. Feisty Fawn v 7.04 
 3. Gutsy Gibbon 

Install option (1-3)? : Gutsy Gibbon 
Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting nspluginwrapper for regex 'nspluginwrapper*'
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nspluginwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 377kB disk space will be freed.
(Reading database ... 96584 files and directories currently installed.)

Removing nspluginwrapper ...

dpkg - warning: while removing nspluginwrapper, directory `/usr/lib/nspluginwrapper/plugins' not empty so not removed.

dpkg - warning: while removing nspluginwrapper, directory `/usr/lib/nspluginwrapper' not empty so not removed.

Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 160kB disk space will be freed.
(Reading database ... 96561 files and directories currently installed.)

Removing flashplugin-nonfree ...

Reading package lists...
Building dependency tree...
Reading state information...
Package libflash-mozplugin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package libflash0c2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting libswfdec0.4-dbg for regex 'libswfdec*'
Note, selecting libswfdec0.4-dev for regex 'libswfdec*'
Note, selecting libswfdec0.5-dev for regex 'libswfdec*'
Note, selecting libswfdec-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3 for regex 'libswfdec*'
Note, selecting libswfdec0.4 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1-dbg for regex 'libswfdec*'
Reading package lists...
Building dependency tree...
Reading state information...
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 96556 files and directories currently installed.)
Unpacking flashplugin-nonfree (from flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.999.0.2+really0ubuntu12) ...
(Reading database ... 96562 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.999.0.2+really0ubuntu12 (using flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Unpacking replacement flashplugin-nonfree ...
Selecting previously deselected package nspluginwrapper.
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.6_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.999.0.2+really0ubuntu12) ...
Setting up nspluginwrapper (0.9.91.6-1ubuntu1) ...




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.




 Everything has been installed 
 Once you read this you can close this terminal 
 window. If you have a browser running you 
 will need to restart it. 
```

---

### Post by Kilz on 2008-03-02
> **CloudFX said:**
> [CODE]
 This script is used to setup Flash and nspluginwrapper 
 for use in 64bit Firefox or other mozilla based browsers 

 Please select the version of the Ubuntu you are installing to. 
 Install options are : 

 1. Dapper Drake v6.06 or Edgy Eft 6.10 
 2. Feisty Fawn v 7.04 
 3. Gutsy Gibbon 

Install option (1-3)? : Gutsy Gibbon 
Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting nspluginwrapper for regex 'nspluginwrapper*'
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nspluginwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 377kB disk space will be freed.
(Reading database ... 96584 files and directories currently installed.)

Removing nspluginwrapper ...

dpkg - warning: while removing nspluginwrapper, directory `/usr/lib/nspluginwrapper/plugins' not empty so not removed.

dpkg - warning: while removing nspluginwrapper, directory `/usr/lib/nspluginwrapper' not empty so not removed.


You still do not have flash in firefox? Does firefox tell you there is a missing plugin?

---

### Post by ThunderRd on 2008-03-02
> **Kilz said:**
> It looks like you have files from a previous install still in place.

Thanks for answering, Kilz.  Ok then, would these be the correct lines to uninstall?

sudo apt-get remove nspluginwrapper
sudo rm -rfd /usr/lib/nspluginwrapper

Is there anything else I need to do before installing again?

---

### Post by CloudFX on 2008-03-02
> **Kilz said:**
> You still do not have flash in firefox? Does firefox tell you there is a missing plugin?

Yes. When I go to a site such as Youtube, it tells me to install it. I've tried the three procedures offered, to no success.

---

### Post by Kilz on 2008-03-02
> **CloudFX said:**
> Yes. When I go to a site such as Youtube, it tells me to install it. I've tried the three procedures offered, to no success.

3 procedures?

What is the results of ```
ls -al /usr/lib/nspluginwrapper/plugins
```

---

### Post by ThunderRd on 2008-03-03
> **Kilz said:**
> It looks like you have files from a previous install still in place.

OK, I uninstalled the wrapper in synaptic, then I deleted the flash plugin from /usr/lib/mozilla/plugins.  I also searched for the *wrapper.so [(I don't have the name handy) that sometimes ocurs in different places.  It didn't exist anymore.

Then I installed again using the oldflash script.

It installed OK, and I have video, but still no audio.  Here are the outputs:
```
   thunderrd@Q-6600:~$ ls -al /usr/lib/mozilla//plugins/
total 6900
drwxr-xr-x 2 thunderrd users    4096 2008-03-03 23:51 .
drwxr-xr-x 4 root      root     4096 2008-02-04 20:02 ..
-rwxr-xr-x 1 thunderrd users 7040036 2007-06-20 07:31 libflashplayer.so
lrwxrwxrwx 1 thunderrd users      38 2008-03-01 23:10 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 thunderrd users      36 2008-01-17 23:42 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 thunderrd users      37 2008-01-17 23:42 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 thunderrd users      34 2008-01-17 23:42 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 thunderrd users      35 2008-01-17 23:42 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 thunderrd users      36 2008-01-17 23:42 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 thunderrd users      37 2008-01-17 23:42 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 thunderrd users      42 2008-01-17 23:42 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 thunderrd users      43 2008-01-17 23:42 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 thunderrd users      60 2008-03-03 23:51 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
thunderrd@Q-6600:~$ ls -al /usr/lib/firefox/plugins/
total 24
drwxr-xr-x 2 root root  4096 2008-03-03 23:51 .
drwxr-xr-x 5 root root  4096 2008-02-16 14:49 ..
lrwxrwxrwx 1 root root    54 2008-03-01 23:10 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji_mozilla_firefox.so
lrwxrwxrwx 1 root root    36 2008-01-17 23:42 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2008-01-17 23:42 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2008-01-17 23:42 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2008-01-17 23:42 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2008-01-17 23:42 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2008-01-17 23:42 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2008-01-17 23:42 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2008-01-17 23:42 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2008-02-07 11:45 libunixprintplugin.so
lrwxrwxrwx 1 root root    60 2008-03-03 23:51 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 root root    37 2008-02-04 22:24 npwrapper.so -> /usr/lib/mozilla/plugins/npwrapper.so
lrwxrwxrwx 1 root root     2 2008-02-04 22:26 so -> so
thunderrd@Q-6600:~$ uname -a
Linux Q-6600 2.6.20-16-generic #2 SMP Tue Feb 12 02:11:24 UTC 2008 x86_64 GNU/Linux
```

---

### Post by Cyssou on 2008-03-03
Hi Kilz,

Thank you so much for that job.
I'm a recent ubuntu 64 user, and before you I cant' achieve the installation of flashplayer.
Now it's working perfectly.

Thank you

---

### Post by CloudFX on 2008-03-03
I managed to get it working on my own. Thansk for your help.

---

### Post by Kilz on 2008-03-03
> **ThunderRd said:**
> OK, I uninstalled the wrapper in synaptic, then I deleted the flash plugin from /usr/lib/mozilla/plugins.  I also searched for the *wrapper.so [(I don't have the name handy) that sometimes ocurs in different places.  It didn't exist anymore.

Then I installed again using the oldflash script.



Do you have audio from the totem plugin?

---

### Post by ThunderRd on 2008-03-03
> **Kilz said:**
> Do you have audio from the totem plugin?

Yes.  Totem, Amarok, Rhythmbox, etc all work, as do the system sounds.

---

### Post by Kilz on 2008-03-03
> **ThunderRd said:**
> Yes.  Totem, Amarok, Rhythmbox, etc all work, as do the system sounds.

I know you said the players work, but does the totem plugin in firefox play sounds when the media is in a webpage. Do you hear sounds with java applets?

---

### Post by ThunderRd on 2008-03-04
Yes, I have sound in java applelts; but I don't think it is through a Totem plugin-it's a Blackdown Java plugin for the 64-bit Firefox.  I've never installed a Totem plugin.

---

### Post by Kilz on 2008-03-04
> **ThunderRd said:**
> Yes, I have sound in java applelts; but I don't think it is through a Totem plugin-it's a Blackdown Java plugin for the 64-bit Firefox.  I've never installed a Totem plugin.

There are 2 more things we can try

Try this command, make sure to change <username> to your username.
```
chown -R <username>:users /home/<username>/.macromedia
```
and this one
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

---

### Post by marcobbi on 2008-03-04
This script is very cool.
What about multiples clicks on flash windows with compiz + emerald on gusty? Anyone fix it? 

thank you

---

### Post by bekirserifoglu on 2008-03-04
thank you so much. works like charm. couldn't find the thank u button though. :)

---

### Post by Kilz on 2008-03-04
> **bekirserifoglu said:**
> thank you so much. works like charm. couldn't find the thank u button though. :)

Clicking on that one in the first post, or any post of mine would be ok with me :D

---

### Post by ThunderRd on 2008-03-05
> **Kilz said:**
> There are 2 more things we can try

Try this command, make sure to change <username> to your username.
```
chown -R <username>:users /home/<username>/.macromedia
```
and this one
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

 Hmm.  Well, the commands completed, but there's no change.  The first one required root permission, BTW.


EDIT: samba problem unrelated; was bad firewall rule, never mind

---

### Post by Jeratt on 2008-03-05
> **marcobbi said:**
> This script is very cool.
What about multiples clicks on flash windows with compiz + emerald on gusty? Anyone fix it? 

thank you

Yes, this thing annoys me so much, but I love compiz so much more; ugg. ](*,)

---

### Post by fatsheep on 2008-03-05
I'm having trouble viewing videos on cnn.com now: [http://www.cnn.com/2008/POLITICS/03/05/march.4.contests/index.html?iref=topnews#cnnSTCVideo](http://www.cnn.com/2008/POLITICS/03/05/march.4.contests/index.html?iref=topnews#cnnSTCVideo).  It works temporarily but then the video suddenly cuts off a minute or so into the clip... :confused: Any ideas?

[ABC videos](http://abcnews.go.com/video/playerIndex?id=4403624%20and%20tune%20into%20ABC's) won't play for me at all...

---

### Post by grossaffe on 2008-03-07
installation didn't get flash working.  requested information below.

ls -al /usr/lib/mozilla/plugins/
```
total 6900
drwxr-xr-x 2 christian users    4096 2008-03-07 09:44 .
drwxr-xr-x 3 root      root     4096 2007-10-15 19:27 ..
-rwxr-xr-x 1 christian users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 christian users      36 2008-03-04 21:16 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 christian users      37 2008-03-04 21:16 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 christian users      34 2008-03-04 21:16 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 christian users      35 2008-03-04 21:16 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 christian users      36 2008-03-04 21:16 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 christian users      37 2008-03-04 21:16 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 christian users      42 2008-03-04 21:16 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 christian users      43 2008-03-04 21:16 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 christian users      60 2008-03-07 09:44 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

ls -al /usr/lib/firefox/plugins/
```
total 20
drwxr-xr-x 2 christian users  4096 2007-10-15 19:27 .
drwxr-xr-x 5 root      root   4096 2007-10-15 19:32 ..
lrwxrwxrwx 1 christian users    36 2008-03-04 21:16 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 christian users    37 2008-03-04 21:16 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 christian users    34 2008-03-04 21:16 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 christian users    35 2008-03-04 21:16 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 christian users    36 2008-03-04 21:16 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 christian users    37 2008-03-04 21:16 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 christian users    42 2008-03-04 21:16 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 christian users    43 2008-03-04 21:16 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 christian users 11456 2007-10-08 11:34 libunixprintplugin.so

```

uname -a
```
Linux christian-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

```

---

### Post by Kilz on 2008-03-07
> **fatsheep said:**
> I'm having trouble viewing videos on cnn.com now: [http://www.cnn.com/2008/POLITICS/03/05/march.4.contests/index.html?iref=topnews#cnnSTCVideo](http://www.cnn.com/2008/POLITICS/03/05/march.4.contests/index.html?iref=topnews#cnnSTCVideo).  It works temporarily but then the video suddenly cuts off a minute or so into the clip... :confused: Any ideas?

[ABC videos](http://abcnews.go.com/video/playerIndex?id=4403624%20and%20tune%20into%20ABC's) won't play for me at all...
The cnn video plays fine for me, ABC has never worked, even in ff32.

> **grossaffe said:**
> installation didn't get flash working.  requested information below.



Were there any error during the install? Please run the install again by draging the GetFlash file to the desktop then starting it with ```
~/Desktop/GetFlash
```. Then copy the entire install to a file and attach it here.

---

### Post by grossaffe on 2008-03-07
> **Kilz said:**
> Were there any error during the install? Please run the install again by draging the GetFlash file to the desktop then starting it with ```
~/Desktop/GetFlash
```. Then copy the entire install to a file and attach it here.

upon the second installation, i noticed these errors:
```
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```

and what was it you wanted me to attach?  the terminal results in the form of a text document?

---

### Post by Kilz on 2008-03-07
> **grossaffe said:**
> upon the second installation, i noticed these errors:
```
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```

and what was it you wanted me to attach?  the terminal results in the form of a text document?
From The file

```
 nspluginwrapper depends on ia32-libs (>= 1.6); however:
  Package ia32-libs is not installed.
```
 
You need to install ia32-libs

---

### Post by samwyse on 2008-03-07
How about uninstall instructions for this?

---

### Post by Kilz on 2008-03-07
> **samwyse said:**
> How about uninstall instructions for this?
The script installs packages. Simply remove nspluginwrapper and flashplugin-nonfree.

But looking at your post history, if it didnt work its most likely the files left in from all the failed attempts to get flash work in the past.

---

### Post by pElf28p on 2008-03-08
OK, I am a newb to Linux. I consider it a huge success that I actually got it running on my computer without crashing the whole thing. With that in mind, my next endeavor is trying to get flash to work. I have tried to run nspluginwrapper...getflash ..in a terminal as described in the steps at the first post in this topic. However, Flash will not work. I have read the readme file's troubleshooting steps and ran the terminals that were described; here are the results. 

Name of File Downloaded: nspluginwrapper install ...getflash
Ubuntu Version 7.10
-----------------------------------
XXX@XXX-laptop:~$ ls -al /usr/lib/mozilla/plugins

total 6900

drwxr-xr-x 2 XXX  users    4096 2008-03-08 08:31 .

drwxr-xr-x 3 root root     4096 2007-10-15 19:27 ..

-rwxr-xr-x 1 XXX  users 7040036 2007-06-19 20:31 libflashplayer.so

lrwxrwxrwx 1 XXX  users      36 2008-02-17 13:33 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so

lrwxrwxrwx 1 XXX  users      37 2008-02-17 13:33 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt

lrwxrwxrwx 1 XXX  users      34 2008-02-17 13:33 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so

lrwxrwxrwx 1 XXX  users      35 2008-02-17 13:33 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt

lrwxrwxrwx 1 XXX  users      36 2008-02-17 13:33 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so

lrwxrwxrwx 1 XXX  users      37 2008-02-17 13:33 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt

lrwxrwxrwx 1 XXX  users      42 2008-02-17 13:33 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so

lrwxrwxrwx 1 XXX  users      43 2008-02-17 13:33 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt

lrwxrwxrwx 1 XXX  users      60 2008-03-08 08:31 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

XXX@XXX-laptop:~$ ls -al /usr/lib/firefox/plugins

total 20

drwxr-xr-x 2 XXX  users  4096 2007-10-15 19:27 .

drwxr-xr-x 5 root root   4096 2007-10-15 19:32 ..

lrwxrwxrwx 1 XXX  users    36 2008-02-17 13:32 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so

lrwxrwxrwx 1 XXX  users    37 2008-02-17 13:32 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt

lrwxrwxrwx 1 XXX  users    34 2008-02-17 13:32 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so

lrwxrwxrwx 1 XXX  users    35 2008-02-17 13:32 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt

lrwxrwxrwx 1 XXX  users    36 2008-02-17 13:32 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so

lrwxrwxrwx 1 XXX  users    37 2008-02-17 13:32 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt

lrwxrwxrwx 1 XXX  users    42 2008-02-17 13:32 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so

lrwxrwxrwx 1 XXX  users    43 2008-02-17 13:32 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt

-rw-r--r-- 1 XXX  users 11456 2007-10-08 11:34 libunixprintplugin.so

XXX@XXX-laptop:~$ locate libflashplayer.so

/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

/usr/lib/mozilla/plugins/libflashplayer.so

/usr/lib/flashplugin-nonfree/libflashplayer.so
 
-----------------------------------------------------------------------
Also, when I originally ran the initial terminal to install the getflash file, I noticed a lot of output (in the terminal) that said things that do not seem to be right:

E: Couldn't find package nspluginwrapper* 
Couldn't find package libflash-mozplugin 
E: Couldn't find package libflash0c2 
E: Couldn't find package gnash
E: Couldn't find package mozilla-plugin-gnash
E: Couldn't find package swfdec-mozilla 
E: Couldn't find package libswfdec* 
E: Couldn't find package ia32-libs 
Errors were encountered while processing: 
 nspluginwrapper 
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory 
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so 


I have no clue what all of this means. I really like Ubuntu but I miss flash. Can anybody help!?!?
Thanks in advance!
-J

---

### Post by Kilz on 2008-03-08
> **pElf28p said:**
> OK, I am a newb to Linux. I consider it a huge success that I actually got it running on my computer without crashing the whole thing. With that in mind, my next endeavor is trying to get flash to work. I have tried to run nspluginwrapper...getflash ..in a terminal as described in the steps at the first post in this topic. However, Flash will not work. I have read the readme file's troubleshooting steps and ran the terminals that were described; here are the results. 


I have no clue what all of this means. I really like Ubuntu but I miss flash. Can anybody help!?!?
Thanks in advance!
-J

You dont have ia32-libs installed.
 what are the results of
```
uname -a
```

---

### Post by clearsky on 2008-03-08
Thanks  a lot for the instructions. :)Everything works as expected so far.

---

### Post by pElf28p on 2008-03-08
Here is the output from uname -a

Linux XXX-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
-J

---

### Post by oxxxid on 2008-03-08
Wow, thanks a LOT for writing this script! Flash is working relatively fine. The only issue I'm having is concerning buttons, which are working only once (I have to click somewhere else outside Firefox or   make my dock appear to make the button work again). Sometimes it's a little annoying, but at least I can watch videos and stuff

---

### Post by Kilz on 2008-03-08
> **pElf28p said:**
> Here is the output from uname -a

Linux XXX-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
-J
Download and install the new script uploaded today.

> **oxxxid said:**
> Wow, thanks a LOT for writing this script! Flash is working relatively fine. The only issue I'm having is concerning buttons, which are working only once (I have to click somewhere else outside Firefox or   make my dock appear to make the button work again). Sometimes it's a little annoying, but at least I can watch videos and stuff

Download and install the new script uploaded today the problem will go away.

---

### Post by cxk929 on 2008-03-09
Hi--thanks for all the work....I have been trying to install flash for quite a while now and I haven't been successful yet.  I had tried using the script before to no avail, now when I try to run it in terminal, after I choose "Gutsy Gibbon" the terminal window closes and doesn't appear to do anything.  

Also, in another attempt to use flash I have tried to install 32 bit firefox.  It appears under applications->internet and appears to begin to start up but ends up closing after a few seconds.  Any suggestions? Thanks!

---

### Post by wolffkrieger on 2008-03-09
Hi Kilz,

Well I tried following some of the replies of this post... my flash was working until today... don't know what happened maybe an update messed things up... so I tried the script for r48... didn't work :(... tried r115 didn't work... uninstalled nspluginwrapper from synaptic... installed it again in terminal.. didn't work...

I read a post where you recommended to remove nspluginwrapper and also remove *flash.so from /usr/lib64/firefox/plugins/... did so... actually for:
[INDENT]/usr/lib64/firefox/plugins/[/INDENT]
[INDENT]/usr/lib64/mozilla/plugins/[/INDENT]
[INDENT]/usr/lib/firefox/plugins/[/INDENT]
[INDENT]/usr/lib/mozilla/plugins/[/INDENT]
and also I had run the remove script... anyways the thing is that everytime I had run this install script after inputting my ubuntu version terminal closed... so I imagined everything that should happen happened... but after running the **ls -al /usr/lib/mozilla/plugins/** and **ls -al /usr/lib/firefox/plugins/** seems like no change... (also physically checked... :).... but alas nothing... :(... )

**ls -al /usr/lib/mozilla/plugins/**
```
wolffkrieger@ubukrieger64:/$ ls -al /usr/lib/mozilla/plugins/
total 8
drwxr-xr-x 2 wolffkrieger users 4096 2008-03-09 01:16 .
drwxr-xr-x 3 root         root  4096 2007-10-15 17:27 ..
lrwxrwxrwx 1 wolffkrieger users   39 2008-01-04 18:06 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 wolffkrieger users   36 2007-12-16 14:58 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 wolffkrieger users   37 2007-12-16 14:58 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 wolffkrieger users   34 2007-12-16 14:58 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 wolffkrieger users   35 2007-12-16 14:58 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 wolffkrieger users   36 2007-12-16 14:58 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 wolffkrieger users   37 2007-12-16 14:58 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 wolffkrieger users   42 2007-12-16 14:58 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 wolffkrieger users   43 2007-12-16 14:58 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt

```

**ls -al /usr/lib/firefox/plugins/**
```
wolffkrieger@ubukrieger64:/$ ls -al /usr/lib/firefox/plugins/
total 20
drwxr-xr-x 2 wolffkrieger users  4096 2008-03-09 01:08 .
drwxr-xr-x 5 root         root   4096 2008-02-08 06:03 ..
lrwxrwxrwx 1 wolffkrieger users    39 2008-01-04 18:06 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 wolffkrieger users    36 2007-12-16 14:58 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 wolffkrieger users    37 2007-12-16 14:58 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 wolffkrieger users    34 2007-12-16 14:58 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 wolffkrieger users    35 2007-12-16 14:58 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 wolffkrieger users    36 2007-12-16 14:58 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 wolffkrieger users    37 2007-12-16 14:58 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 wolffkrieger users    42 2007-12-16 14:58 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 wolffkrieger users    43 2007-12-16 14:58 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 wolffkrieger users 11456 2008-02-07 05:07 libunixprintplugin.so

```

**uname -a**
```
Linux ubukrieger64 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

```

Thanks in advance Kilz and great work!!!

---

### Post by Kilz on 2008-03-09
> **cxk929 said:**
> Hi--thanks for all the work....I have been trying to install flash for quite a while now and I haven't been successful yet.  I had tried using the script before to no avail, now when I try to run it in terminal, after I choose "Gutsy Gibbon" the terminal window closes and doesn't appear to do anything.  

Also, in another attempt to use flash I have tried to install 32 bit firefox.  It appears under applications->internet and appears to begin to start up but ends up closing after a few seconds.  Any suggestions? Thanks!

It was a typo. please get the new version uploaded today.

> **wolffkrieger said:**
> Hi Kilz,

Well I tried following some of the replies of this post... my flash was working until today... don't know what happened maybe an update messed things up... so I tried the script for r48... didn't work :(... tried r115 didn't work... uninstalled nspluginwrapper from synaptic... installed it again in terminal.. didn't work...

I read a post where you recommended to remove nspluginwrapper and also remove *flash.so from /usr/lib64/firefox/plugins/... did so... actually for:
[INDENT]/usr/lib64/firefox/plugins/[/INDENT]
[INDENT]/usr/lib64/mozilla/plugins/[/INDENT]
[INDENT]/usr/lib/firefox/plugins/[/INDENT]
[INDENT]/usr/lib/mozilla/plugins/[/INDENT]
and also I had run the remove script... anyways the thing is that everytime I had run this install script after inputting my ubuntu version terminal closed... so I imagined everything that should happen happened... but after running the **ls -al /usr/lib/mozilla/plugins/** and **ls -al /usr/lib/firefox/plugins/** seems like no change... (also physically checked... :).... but alas nothing... :(... )

Thanks in advance Kilz and great work!!!

I uploaded a new script this morning , try it. But you also helped in one way. I never intended the RemoveScript to be used like you used it. It is for those that want to not run the script for whatever reason. When you run it you remove clues as to what worked and what didnt.  To me your system looks like the script was never ran.

---

### Post by pElf28p on 2008-03-09
Kilz, forgive my ignorance, but when you say to download the newly uplaoded script, do you mean the one that says 
"Click here for the script that installs the previous r48 plugin (recommended)" at the beginning of this post? Also, you had mentioned that I do not have  ia32-libs installed. Do I need to download this before the 'new' script?  Thanks for your help so far. 
-J

---

### Post by wolffkrieger on 2008-03-09
> **pElf28p said:**
> Kilz, forgive my ignorance, but when you say to download the newly uplaoded script, do you mean the one that says 
"Click here for the script that installs the previous r48 plugin (recommended)" at the beginning of this post?

I believe that's the one. Last night I downloaded it and the file was: **oldflash-0.1.5.tar.gz**.
This morning the file's name is: **oldflash-0.1.5-1.tar.gz**.

So I would imagine it's new.... :lolflag:

---

### Post by wolffkrieger on 2008-03-09
Thanks Kilz!

You rock! :guitar: It works beautifully. :)... sound and everything... thanks again...

---

### Post by pElf28p on 2008-03-09
Where can I download ia32-libs? I did a search and tried to download it but I think I downloaded the wrong version because when I attempt to extract the file I get an error message. Any help is appreciated!
-Joe

---

### Post by Thilips on 2008-03-09
Worked great! It took me a year to find something that worked in 1 minute. GREAT work!!!

---

### Post by sluger1138 on 2008-03-09
> **pElf28p said:**
> Where can I download ia32-libs? I did a search and tried to download it but I think I downloaded the wrong version because when I attempt to extract the file I get an error message. Any help is appreciated!
-Joe

Hello,
I do believe you will find the  ia32 Files in synaptic.Hope this is of help too you.

---

### Post by Kilz on 2008-03-09
> **pElf28p said:**
> Kilz, forgive my ignorance, but when you say to download the newly uplaoded script, do you mean the one that says 
"Click here for the script that installs the previous r48 plugin (recommended)" at the beginning of this post? Also, you had mentioned that I do not have  ia32-libs installed. Do I need to download this before the 'new' script?  Thanks for your help so far. 
-J

Just download and run the newest script.

---

### Post by oxxxid on 2008-03-09
Thank you for the new script, kilz, it's working perfectly!

---

### Post by grossaffe on 2008-03-10
i'm not the only one who can't seem to find a working repository with ia32-libs, am I?

---

### Post by mario.kostelac on 2008-03-10
have a problem here...
flash just doesn't work.. i tried to reinstall a million times but nothing happend... sometimes ff doesn't recognize that need flash and instead of animations there are white backgrounds.

now both swiftweasel and ff doesn't recognite that flash is installed...
here is the code 
```

 This script is used to setup Flash and nspluginwrapper 
 for use in 64bit Firefox or other mozilla based browsers 

 Please select the version of the Ubuntu you are installing to. 
 Install options are : 

 1. Dapper Drake v6.06 or Edgy Eft 6.10 
 2. Feisty Fawn v 7.04 
 3. Gutsy Gibbon 

Install option (1-3)? : Gutsy Gibbon 
Reading package lists...
Building dependency tree...
Reading state information...
Package nspluginwrapper is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package nspluginwrapper is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package libflash-mozplugin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package libflash0c2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package mozilla-plugin-gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting libswfdec0.4-dbg for regex 'libswfdec*'
Note, selecting libswfdec0.4-dev for regex 'libswfdec*'
Note, selecting libswfdec0.5-dev for regex 'libswfdec*'
Note, selecting libswfdec-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3 for regex 'libswfdec*'
Note, selecting libswfdec0.4 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1-dbg for regex 'libswfdec*'
Reading package lists...
Building dependency tree...
Reading state information...
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
Selecting previously deselected package nspluginwrapper.
(Reading database ... 108009 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.6_amd64.deb) ...
Setting up nspluginwrapper (0.9.91.6-1ubuntu1) ...

 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.


 Everything has been installed 
 Once you read this you can close this terminal 
 window. If you have a browser running you 
 will need to restart it. 

ls -al /usr/lib/mozilla//plugins/
mario@mario-desktop:~/Desktop$ ls -al /usr/lib/mozilla//plugins/
total 12
drwxr-xr-x 2 mario users 4096 2008-03-10 19:36 .
drwxr-xr-x 3 root  root  4096 2008-03-10 19:36 ..
lrwxrwxrwx 1 mario users   60 2008-03-10 19:36 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

mario@mario-desktop:~/Desktop$ ls -al /usr/lib/firefox/plugins/
total 20
drwxr-xr-x 2 mario users  4096 2008-03-10 19:26 .
drwxr-xr-x 5 root  root   4096 2008-03-10 19:26 ..
-rw-r--r-- 1 mario users 11456 2008-02-07 12:07 libunixprintplugin.so

mario@mario-desktop:~/Desktop$ uname -a
Linux mario-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
mario@mario-desktop:~/Desktop$ 


```

pls help

---

### Post by erginemr on 2008-03-10
> **mario.kostelac said:**
> have a problem here...
flash just doesn't work.. i tried to reinstall a million times but nothing happend... sometimes ff doesn't recognize that need flash and instead of animations there are white backgrounds.

now both swiftweasel and ff doesn't recognite that flash is installed...
here is the code 
...
pls help

Please have a look at:
[http://ubuntuforums.org/showthread.php?t=714794&highlight=flash&page=2](http://ubuntuforums.org/showthread.php?t=714794&highlight=flash&page=2)

and try the links I gave in post #11.

---

### Post by mario.kostelac on 2008-03-10
thank you...
i solved the problem before you posted by removing everything related to flash and firefox :)

---

### Post by cxk929 on 2008-03-11
Kilz,
The script worked like a charm after I fixed the unmet dependencies (which is explained on the first page of this post.)

I don't know if this is related, but now when I use file browser, it will turn grey and crash after about 20 seconds regardless of what I am doing with it.  Do you think I might have installed it incorrectly?

Thanks!

---

### Post by pElf28p on 2008-03-11
**Well flash is still not working. I attempted to install nspluginwrapper- from 3/8/08- and here is the output I get:**
mkdir: cannot create directory `/tmp/ffplug': File exists

 This script is used to setup Flash and nspluginwrapper 
 for use in 64bit Firefox or other mozilla based browsers 

 Please select the version of the Ubuntu you are installing to. 
 Install options are : 

 1. Dapper Drake v6.06 or Edgy Eft 6.10 
 2. Feisty Fawn v 7.04 
 3. Gutsy Gibbon 

Install option (1-3)? :3
 Gutsy Gibbon 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nspluginwrapper for regex 'nspluginwrapper*'
E: Couldn't find package nspluginwrapper*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 160kB disk space will be freed.
(Reading database ... 88060 files and directories currently installed.)
Removing flashplugin-nonfree ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libflash-mozplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libflash0c2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libswfdec*
mkdir: cannot create directory `/tmp/nsplugwrapper': File exists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
--19:41:03--  [http://home.comcast.net/~ubuntume/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb](http://home.comcast.net/~ubuntume/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb)
           => `flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 88055 files and directories currently installed.)
Unpacking flashplugin-nonfree (from flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.999.0.2+really0ubuntu12) ...
--19:41:04--  [http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6-2_amd64.deb](http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6-2_amd64.deb)
           => `nspluginwrapper_0.9.91.6-2_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

(Reading database ... 88061 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.999.0.2+really0ubuntu12 (using flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Unpacking replacement flashplugin-nonfree ...
Selecting previously deselected package nspluginwrapper.
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.6-2_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.999.0.2+really0ubuntu12) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.
-------------------------------------------
**I noticed all of the error messages in the terminal output so I attempted to install ia32-libs but when I try to extract it I get the message: **
Error: Dependancy is not satisfiable: lib32gcc1

---------------------------
**Here are the results from troubleshoot guide in the readme file:**

Here are the results of ls -al /usr/lib/mozilla/plugins

joe@joe-laptop:~$ ls -al /usr/lib/mozilla/plugins
total 6900
drwxr-xr-x 2 joe  users    4096 2008-03-11 19:41 .
drwxr-xr-x 3 root root     4096 2007-10-15 19:27 ..
-rwxr-xr-x 1 joe  users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 joe  users      36 2008-02-17 13:33 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 joe  users      37 2008-02-17 13:33 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 joe  users      34 2008-02-17 13:33 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 joe  users      35 2008-02-17 13:33 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 joe  users      36 2008-02-17 13:33 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 joe  users      37 2008-02-17 13:33 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 joe  users      42 2008-02-17 13:33 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 joe  users      43 2008-02-17 13:33 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 joe  users      60 2008-03-11 19:41 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
joe@joe-laptop:~$ 

-------------------------------------
Here are the results from ls -al /usr/lib/firefox/plugins

joe@joe-laptop:~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 joe  users  4096 2007-10-15 19:27 .
drwxr-xr-x 5 root root   4096 2007-10-15 19:32 ..
lrwxrwxrwx 1 joe  users    36 2008-02-17 13:32 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 joe  users    37 2008-02-17 13:32 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 joe  users    34 2008-02-17 13:32 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 joe  users    35 2008-02-17 13:32 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 joe  users    36 2008-02-17 13:32 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 joe  users    37 2008-02-17 13:32 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 joe  users    42 2008-02-17 13:32 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 joe  users    43 2008-02-17 13:32 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 joe  users 11456 2007-10-08 11:34 libunixprintplugin.so
joe@joe-laptop:~$ 
----------------------------------
Here are the results from uname -a

joe@joe-laptop:~$ uname -a
Linux joe-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
joe@joe-laptop:~$

[B]Any help would be appreciated as I am quite confused. Thank you.
-J[/B]

---

### Post by Kilz on 2008-03-12
The error is common this last week or so. Its listed on the first post and I have edited that post to make it a little more clear, adding the exact error. [take a look here.]("http://ubuntuforums.org/showpost.php?p=4417385&postcount=914")

---

### Post by feminaexlux on 2008-03-12
The old flash script Works for Hardy Alpha 6 (using the Gutsy option) after moving the files from /usr/lib/mozilla/plugins to my Firefox 3 Beta 3 folder :)

Thanks!

---

### Post by martin saint martin on 2008-03-13
thank you so much!  you made the flash9 install so easy that i cried tears of joy!  :)

---

### Post by pElf28p on 2008-03-14
Kilz,
I tried the link you provided and followed the steps. Still no luck. ia32-libs does not show in synaptic. Any other ideas/suggestion? Thanks for all the help so far.
-Joe

---

### Post by bradyBunch on 2008-03-14
I too have issues with the ia32-lib install. I tried different repository servers but keep getting the same error from synaptic manager. When I select mark for installation, a window pops up which states;

The following packages have unresolved dependencies.

ia32-libs:
 Depends: lib32gcc1  but it is not installable
 Depends: libc6-i386 (>=2.3.6-2) but it is not installable
 Depends: lib32z1  but it is not installable
 Depends: lib32stdc++6  but it is not installable
 Depends: lib32asound2  but it is not installable
 Depends: lib32ncurses5  but it is not installable

---

### Post by Kilz on 2008-03-14
> **pElf28p said:**
> Kilz,
I tried the link you provided and followed the steps. Still no luck. ia32-libs does not show in synaptic. Any other ideas/suggestion? Thanks for all the help so far.
-Joe

Nope, the problem isnt the script, or the packages that I made. Its that the ia32-libs package and its dependent packages are not being seen in the repository by apt (the package manager). All those packages are in the official Ubuntu repositories. They  are common packages that 64bit Ubuntu needs. The only one who can fix them are official Ubuntu package maintainers. The issue should be reported on launchpad as a bug by someone experiencing the issue. The repositories are mirrors, the one you and others are using is bad.
Using the method in the Common Issues section, please tell me what mirror you are using.

---

### Post by bradyBunch on 2008-03-14
Thanks Kilz,

I followed the directions in this post;

[http://ubuntuforums.org/showpost.php?p=4417385&postcount=914](http://ubuntuforums.org/showpost.php?p=4417385&postcount=914)

From the Select Best Server result, I used ubuntu.media.mit.edu

I also tried mirror.csclub.uwaterloo.ca with no luck.

---

### Post by Kilz on 2008-03-14
> **bradyBunch said:**
> Thanks Kilz,

I followed the directions in this post;

[http://ubuntuforums.org/showpost.php?p=4417385&postcount=914](http://ubuntuforums.org/showpost.php?p=4417385&postcount=914)

From the Select Best Server result, I used ubuntu.media.mit.edu

I also tried mirror.csclub.uwaterloo.ca with no luck.

Can you try the main server?

---

### Post by bradyBunch on 2008-03-15
I tired the main server and still no luck. In /etc/apt/sources.list is

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted multiverse universe

I also found a reported bug that seems to address this problem

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/162681](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/162681)

Supposedly there is no problem if you have universe section enabled. From the line above I believe I do but I am still getting the original error.

---

### Post by robb0100 on 2008-03-15
My problem is not related to ia32-libs - this seems to be installed correctly. The only error from the script is:
Note, selecting libswfdec0.4-dbg for regex 'libswfdec*'
Note, selecting libswfdec0.4-dev for regex 'libswfdec*'
Note, selecting libswfdec0.5-dev for regex 'libswfdec*'
Note, selecting libswfdec-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3 for regex 'libswfdec*'
Note, selecting libswfdec0.4 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1-dbg for regex 'libswfdec*'
E: Couldn't find package libswfdec*

Suggests that I should install one or more of the above. ??

From the following it looks as though the script installed ok:

rbrown@rbrown-linux64-desktop:~$ ls -al /usr/lib/mozilla//plugins/
total 6900
drwxr-xr-x 2 rbrown users    4096 2008-03-15 23:05 .
drwxr-xr-x 3 root   root     4096 2007-04-15 21:58 ..
-rwxr-xr-x 1 rbrown users 7040036 2007-06-20 10:31 libflashplayer.so
lrwxrwxrwx 1 rbrown users      38 2007-11-25 15:39 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 rbrown users      39 2007-11-20 21:39 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 rbrown users      36 2007-11-20 20:16 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 rbrown users      37 2007-11-20 20:16 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 rbrown users      34 2007-11-20 20:16 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 rbrown users      35 2007-11-20 20:16 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 rbrown users      36 2007-11-20 20:16 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 rbrown users      37 2007-11-20 20:16 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 rbrown users      42 2007-11-20 20:16 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 rbrown users      43 2007-11-20 20:16 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 rbrown users      60 2008-03-15 23:05 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
rbrown@rbrown-linux64-desktop:~$ ls -al /usr/lib/firefox/plugins/
total 24
drwxr-xr-x 2 rbrown users  4096 2008-03-15 23:05 .
drwxr-xr-x 5 root   root   4096 2008-02-10 19:26 ..
lrwxrwxrwx 1 rbrown users    39 2007-11-20 21:39 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 rbrown users    36 2007-11-20 20:16 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 rbrown users    37 2007-11-20 20:16 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 rbrown users    34 2007-11-20 20:16 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 rbrown users    35 2007-11-20 20:16 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 rbrown users    36 2007-11-20 20:16 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 rbrown users    37 2007-11-20 20:16 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 rbrown users    42 2007-11-20 20:16 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 rbrown users    43 2007-11-20 20:16 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 rbrown users 11456 2008-02-07 22:07 libunixprintplugin.so
lrwxrwxrwx 1 rbrown users    60 2008-03-15 23:05 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
rbrown@rbrown-linux64-desktop:~$ uname -a
Linux rbrown-linux64-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
rbrown@rbrown-linux64-desktop:~$ 
rbrown@rbrown-linux64-desktop:~$ 

The sites that don't work give messages that suggest the GCJ Web Browser Plugin (IcedTea) should be installed.
Any clues?

Thanks for the very helpful info on this thread.

---

### Post by Kilz on 2008-03-15
> **robb0100 said:**
> My problem is not related to ia32-libs - this seems to be installed correctly. The only error from the script is:
Note, selecting libswfdec0.4-dbg for regex 'libswfdec*'
Note, selecting libswfdec0.4-dev for regex 'libswfdec*'
Note, selecting libswfdec0.5-dev for regex 'libswfdec*'
Note, selecting libswfdec-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3 for regex 'libswfdec*'
Note, selecting libswfdec0.4 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1-dbg for regex 'libswfdec*'
E: Couldn't find package libswfdec*

Suggests that I should install one or more of the above. ??
The script attempts to remove all the flash packages that could be installed as they conflict with what the script installles. At one time it was the #1 reason why the script didnt work, what you see is a list of things it tried to remove but didnt find.


> **robb0100 said:**
> 
The sites that don't work give messages that suggest the GCJ Web Browser Plugin (IcedTea) should be installed.
Any clues?

Thanks for the very helpful info on this thread.
icedtea is java not flash. Your being told to install a java plugin. The script only installs a flash plugin.

---

### Post by Kilz on 2008-03-15
> **bradyBunch said:**
> I tired the main server and still no luck. In /etc/apt/sources.list is

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted multiverse universe

I also found a reported bug that seems to address this problem

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/162681](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/162681)

Supposedly there is no problem if you have universe section enabled. From the line above I believe I do but I am still getting the original error.

What that report tells us is the reporter had a similar problem. Someone said make sure the universe is enabled, someone looked in the main repository and found the package. Since the original reporter didnt post again, it was marked incomplete and expired. Perhaps there is an error in your /etc/apt/sources.list, can you attach it to a post?

---

### Post by dptxp on 2008-03-16
Tried, I tried. If there were any errors I did not see it.
Flash does not work in my 64-bit Ubuntu.

Installed the Java plugins from add/remove.
No joy.

---

### Post by Kilz on 2008-03-16
> **dptxp said:**
> Tried, I tried. If there were any errors I did not see it.
Flash does not work in my 64-bit Ubuntu.

Installed the Java plugins from add/remove.
No joy.

Please drag the script on the desktop, open a terminal, navigate to the script. Then start the script with ./GetFlash. Look for errors if it doesnt work, if you cant see the error, copy it to a txt file and attach it. 

This script will not install Java. It never has, it never will.

---

### Post by dptxp on 2008-03-18
Thanks Kilz. It works now, tested at Adobe site too. Adobe says- 'installed'.

I did not use the instructions of this post, I simply followed your page-1 instructions again.

It seems that I had tried to install Flash earlier and failed.

---

### Post by fattysfinest on 2008-03-18
Thank You Kilz!!!
Worked flawlessly, it took maybe a minute from start to finish!
Amd 64,3800x2 with gutsy. Thanks again, it was a pleasure!
Brian

---

### Post by Kivech on 2008-03-18
Any chance on an inclusion of Hardy into your script?

Kivech

---

### Post by muadnu on 2008-03-20
The script works for me, but flash does not work reliably, sometimes it's shown and sometimes not. For some websites, it's never shown, for some other it's intermittent.

It gets fixed sometimes if I rerun the script. I'm guessing the problem is that something's left from previous attempts, but I cannot find anything. Anyone knows a full list of everything that should be uninstalled/removed?

---

### Post by mario.kostelac on 2008-03-21
Same problem again. Flash works and after some period just stop to work. The old story - flash is not shown, there is only html backrounds insted of flash...
Have I to post the info again? it's the same as my last info?

Tnx

---

### Post by bradyBunch on 2008-03-21
> **Kilz said:**
> What that report tells us is the reporter had a similar problem. Someone said make sure the universe is enabled, someone looked in the main repository and found the package. Since the original reporter didnt post again, it was marked incomplete and expired. Perhaps there is an error in your /etc/apt/sources.list, can you attach it to a post?

Kilz,

Sorry for the delay, I hate when works get in the way! 

Here is the list of my sources.list file;

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by Kilz on 2008-03-21
> **bradyBunch said:**
> Kilz,

Sorry for the delay, I hate when works get in the way! 

Here is the list of my sources.list file;



All your sources are commented out. None are without a # in front of them.

---

### Post by bradyBunch on 2008-03-21
> **Kilz said:**
> All your sources are commented out. None are without a # in front of them.

I went into Synaptic and enabled 'source code' under the 'Ubuntu Software' tab and also enabled Important and recommended security updates under the 'Updates tab'. This added the following lines to the bottom of /etc/apt/sources.list;

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

Ran Kilz's script and all is well. Flash is working.

Thank you Kilz. I do not remember deselecting those options but it's fixed now. I had 199 updates to do as well.

---

### Post by Kilz on 2008-03-21
> **Kivech said:**
> Any chance on an inclusion of Hardy into your script?

Kivech

Hardy may not need it. Hopefully the flash packages for Hardy will be fixed. If your running Hardy now and caht get flash running by 
```
sudo apt-get install flashplugin-nonfree
```
File a bug report on launchpad. Part of running Development versions is filing bug reports.

> **muadnu said:**
> The script works for me, but flash does not work reliably, sometimes it's shown and sometimes not. For some websites, it's never shown, for some other it's intermittent.

It gets fixed sometimes if I rerun the script. I'm guessing the problem is that something's left from previous attempts, but I cannot find anything. Anyone knows a full list of everything that should be uninstalled/removed?
There is no list, but if you give me a listing of the usr/lib/mozilla/plugins and /usr/lib/firefox/plugins and ~/.mozilla/plugins folders I will take a look.

---

### Post by mario.kostelac on 2008-03-22
Anybody for my problem above?

EDIT: reinstalled and it works.. duno why it crashed but... it works now :)

---

### Post by muadnu on 2008-03-23
> 
There is no list, but if you give me a listing of the usr/lib/mozilla/plugins and /usr/lib/firefox/plugins and ~/.mozilla/plugins folders I will take a look.

Here are the contents of these folders. I've tried removing everything which I think could be related, but no luck... At this moment almost no webpage with flash works...

```
dani@nemo:~$ ls /usr/lib/mozilla/plugins/
libflashplayer.so                mplayerplug-in-dvx.so
libjavaplugin_oji.so             mplayerplug-in-dvx.xpt
libjavaplugin.so                 mplayerplug-in-qt.so
libtotem-basic-plugin.so         mplayerplug-in-qt.xpt
libtotem-basic-plugin.xpt        mplayerplug-in-rm.so
libtotem-gmp-plugin.so           mplayerplug-in-rm.xpt
libtotem-gmp-plugin.xpt          mplayerplug-in.so
libtotem-mully-plugin.so         mplayerplug-in-wmp.so
libtotem-mully-plugin.xpt        mplayerplug-in-wmp.xpt
libtotem-narrowspace-plugin.so   mplayerplug-in.xpt
libtotem-narrowspace-plugin.xpt  npwrapper.libflashplayer.so
mozplugger.so

```
```

dani@nemo:~$ ls /usr/lib/firefox/plugins/
libjavaplugin.so                 mplayerplug-in-dvx.so
libtotem-basic-plugin.so         mplayerplug-in-dvx.xpt
libtotem-basic-plugin.xpt        mplayerplug-in-qt.so
libtotem-gmp-plugin.so           mplayerplug-in-qt.xpt
libtotem-gmp-plugin.xpt          mplayerplug-in-rm.so
libtotem-mully-plugin.so         mplayerplug-in-rm.xpt
libtotem-mully-plugin.xpt        mplayerplug-in.so
libtotem-narrowspace-plugin.so   mplayerplug-in-wmp.so
libtotem-narrowspace-plugin.xpt  mplayerplug-in-wmp.xpt
libunixprintplugin.so            mplayerplug-in.xpt
mozplugger.so                    npwrapper.libflashplayer.so

```
```
dani@nemo:~$ ls .mozilla/plugins
npcxoffice-dc7fc55b-1574-4eed-9d3d-2ed7ac5e4ace.linux64.NPSWF32.5664.so
npcxoffice-dc7fc55b-1574-4eed-9d3d-2ed7ac5e4ace.linux.NPSWF32.5664.so

```

Thanks!

---

### Post by Kilz on 2008-03-23
> **muadnu said:**
> Here are the contents of these folders. I've tried removing everything which I think could be related, but no luck... At this moment almost no webpage with flash works...


```
dani@nemo:~$ ls .mozilla/plugins
npcxoffice-dc7fc55b-1574-4eed-9d3d-2ed7ac5e4ace.linux64.NPSWF32.5664.so
npcxoffice-dc7fc55b-1574-4eed-9d3d-2ed7ac5e4ace.linux.NPSWF32.5664.so

```

Thanks!

These appear to be flash plugins. Copy them someplace else and restart the browser to check.

---

### Post by muadnu on 2008-03-23
> **Kilz said:**
> These appear to be flash plugins. Copy them someplace else and restart the browser to check.

I tried it, and at the beginning it seemed to be going better, I could watch a video in youtube. But then in any other webpage, flash either doesn't appear or disappears after a few seconds.

---

### Post by muadnu on 2008-03-23
> **muadnu said:**
> I tried it, and at the beginning it seemed to be going better, I could watch a video in youtube. But then in any other webpage, flash either doesn't appear or disappears after a few seconds.

I tried now purging my firefox installation and removing every trace I found of it, then running the script again. Same thing, no flash...

By the way, the script runs fine, but at some point it says it cannot find a package:

```
Note, selecting libswfdec0.4-dbg for regex 'libswfdec*'
Note, selecting libswfdec0.4-dev for regex 'libswfdec*'
Note, selecting libswfdec0.5-dev for regex 'libswfdec*'
Note, selecting libswfdec-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3 for regex 'libswfdec*'
Note, selecting libswfdec0.4 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1-dbg for regex 'libswfdec*'
E: Couldn't find package libswfdec*

```

---

### Post by Kilz on 2008-03-23
> **muadnu said:**
> I tried now purging my firefox installation and removing every trace I found of it, then running the script again. Same thing, no flash...

By the way, the script runs fine, but at some point it says it cannot find a package:

```
Note, selecting libswfdec0.4-dbg for regex 'libswfdec*'
Note, selecting libswfdec0.4-dev for regex 'libswfdec*'
Note, selecting libswfdec0.5-dev for regex 'libswfdec*'
Note, selecting libswfdec-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3 for regex 'libswfdec*'
Note, selecting libswfdec0.4 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1 for regex 'libswfdec*'
Note, selecting libswfdec0.5-1-dbg for regex 'libswfdec*'
E: Couldn't find package libswfdec*

```

That is a list of flash packages it tries to remove that would conflict with the flash it installes.

---

### Post by Mchl923 on 2008-03-24
I followed the instructions, but still no sign of flash...  at all.

---

### Post by mtrompeta on 2008-03-25
Kilz, thanks so much for this post and utility.  This worked like a charm:KS!!!

---

### Post by radamo on 2008-03-25
I am very new to Linux and hope this isn't a stupid question... I searched around and cannot seem to find how to (if at all posssible) get flash working for Hardy Heron.  I am running on the latest Beta x64 version and have looked and only found this thread and it seems to only support up to 7.10.  Is there a way to make this work for 8.04?  

Thanks for any help....

Rich

---

### Post by Kilz on 2008-03-25
> **radamo said:**
> I am very new to Linux and hope this isn't a stupid question... I searched around and cannot seem to find how to (if at all posssible) get flash working for Hardy Heron.  I am running on the latest Beta x64 version and have looked and only found this thread and it seems to only support up to 7.10.  Is there a way to make this work for 8.04?  

Thanks for any help....

Rich
```

sudo apt-get install flashplugin-nonfree
``` if flash doesn't work after restarting your browser, file a bug report on launchpad.

---

### Post by radamo on 2008-03-25
> **Kilz said:**
> ```

sudo apt-get install flashplugin-nonfree
``` if flash doesn't work after restarting your browser, file a bug report on launchpad.

Here is the result of running the code above:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 77 not upgraded.

I guess I will file a bug report.  Thanks,
RA

---

### Post by radamo on 2008-03-25
Here is my flashlog.txt if anyone has any ideas... Thanks,
RA

---

### Post by kushykush on 2008-03-25
The prescription prescribed in the first post (download tarball Flash) and run in terminal, did not work for me.  The terminal will close so swiftly (without leaving any message), that I could not tell if Flash was installed.  When I restarted Firefox, Flash had NOT installed.  After a couple other tries I left a bug report and stopped.

However, when I restarted this morning Flash had been installed.  I do not know how.  Now everything is playing, and the AMD-64 version works well.

This is unrelated but does anyone know what happened to creating new folders in Firefox 3.0?  It is not allowing me to create new folders for bookmarking.  Earlier there was no tab toolbar either and I could not see my tabs.  Now I can see the tabs but still no folder creation in bookmarks.

---

### Post by Mchl923 on 2008-03-25
I followed instructions, still no flash.  Any help?

---

### Post by Kilz on 2008-03-25
> **Mchl923 said:**
> I followed instructions, still no flash.  Any help?

How many other methods of installing flash have you tried? Have you read the Common problems section?

---

### Post by Mchl923 on 2008-03-25
read common problems,  its not that flash doesn't work, its that i don't even see it installed in firefox.

---

### Post by Kilz on 2008-03-25
> **Mchl923 said:**
> read common problems,  its not that flash doesn't work, its that i don't even see it installed in firefox.

Click on Help, then About Firefox. Near the bottom of the box that opens is a line starting with Mozilla/5.0 . Copy the whole thing and paste it to a reply.

---

### Post by cacycleworks on 2008-03-25
> **Kilz said:**
> Click on Help, then About Firefox. Near the bottom of the box that opens is a line starting with Mozilla/5.0 . Copy the whole thing and paste it to a reply.

FWIW, I'm running Gutsy and flash isn't working for me... so I did sudo apt-get install flashplugin-nonfree and it said: flashplugin-nonfree is already the newest version. So I remove it then re-run the install. It totally looked like it was behaving, it downloaded the tar.gz from Macromedia and everything.

Here's that about box...
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.12) Gecko/20080207 Ubuntu/7.10 (gutsy) Firefox/2.0.0.12

Interestingly enough, I think it might be more of a "big picture" problem. I installed Kubuntu on this computer and I think that was a mistake. I should have installed ubuntu server then apt-get install kubuntu-desktop afterwards. The most recent handful of updates have almost crippled my computer. And today I really needed the flash plug-in to visit a vendor's site. :(  I smell a reinstall coming on...

Any ideas about installing something like 32bit iceweasel to get my flash working? I used your script before and really liked that. I don't care for flash but when I'd need it, I'd launch up iceweasel. :)

:) Chris

---

### Post by Mchl923 on 2008-03-25
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.12) Gecko/20080207 Ubuntu/7.10 (gutsy) Firefox/2.0.0.12

---

### Post by Kilz on 2008-03-26
> **Mchl923 said:**
> Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.12) Gecko/20080207 Ubuntu/7.10 (gutsy) Firefox/2.0.0.12
and 
> **cacycleworks said:**
> FWIW, I'm running Gutsy and flash isn't working for me... so I did sudo apt-get install flashplugin-nonfree and it said: flashplugin-nonfree is already the newest version. So I remove it then re-run the install. It totally looked like it was behaving, it downloaded the tar.gz from Macromedia and everything.



Drag the script to the desktop, open a terminal and type in 
```
cd ~/Desktop
./GetFlash
```
Look over the install, if you see any issues from the Common Issues section follow the instructions for them, if not paste it into a text file and attach it to a post here along with the required information for reporting a problem.

---

### Post by nxmedia on 2008-03-26
Hi, I'm quite new to Linux so bear with me...

I have Xubuntu Linux, and an AMD 64-bit machine.

I follow these instructions, but double clicking the "GetFlash" file does nothing, as does right-click-execute. There's also no "open in terminal" option for the GetFlash file. Is there something I am doing wrong, or do I need to download another program first before doing this?

Thanks,
~Dan Badger

---

### Post by Kilz on 2008-03-26
> **nxmedia said:**
> Hi, I'm quite new to Linux so bear with me...

I have Xubuntu Linux, and an AMD 64-bit machine.

I follow these instructions, but double clicking the "GetFlash" file does nothing, as does right-click-execute. There's also no "open in terminal" option for the GetFlash file. Is there something I am doing wrong, or do I need to download another program first before doing this?

Thanks,
~Dan Badger

Drag the script to the desktop, open a terminal and type in 
```
cd ~/Desktop
./GetFlash
```

---

### Post by Mchl923 on 2008-03-26
thanks for all the help Kilz.

---

### Post by radamo on 2008-03-26
Ok... using the information posted in the "Common Issues" section I got flash working rather easily... Shame I didn't see that before posting all  of my questions... 
Thanks for the helpful posts in this thread.
RA

---

### Post by muadnu on 2008-03-26
> **muadnu said:**
> I tried now purging my firefox installation and removing every trace I found of it, then running the script again. Same thing, no flash...


I finally got it to work. I had to erase the relevant files in /usr/lib/mozilla/plugins, /usr/lib/firefox/plugins, /usr/lib/nspluginwrapper/plugins, and /usr/lib/iceweasel/plugins. I reinstalled after that and got flash...

---

### Post by Udibuntu on 2008-03-27
Hi Guys,

I'm sorry, but this doesn't work here...I erased all other files, but this plugin works half of the times, and at times doesn't work at all, see my [Southpark dissapointment.]("http://ubuntuforums.org/showthread.php?t=735850").

I know you all hoped to end all Flash Ubuntu 64 bit issues, but here I am after doing all that I can...

This is the only issue that made me turn to windoze - my Southpark deprivation...

Please help,

Udi

---

### Post by Aaronb2245 on 2008-03-27
Thank you! This has been driving me nuts! Some flash would work and others sites would not now all is good in my neighborhood!


Thanks Alot!
Aaron

---

### Post by Kilz on 2008-03-28
> **Udibuntu said:**
> Hi Guys,

I'm sorry, but this doesn't work here...I erased all other files, but this plugin works half of the times, and at times doesn't work at all, see my [Southpark dissapointment.]("http://ubuntuforums.org/showthread.php?t=735850").

I know you all hoped to end all Flash Ubuntu 64 bit issues, but here I am after doing all that I can...

This is the only issue that made me turn to windoze - my Southpark deprivation...

Please help,

Udi

Please read the Common Issues section for what to include in a request for help.

---

### Post by Udibuntu on 2008-03-28
Problem persists with [SouthparkStudio]("http://www.southparkstudios.com/")s "full episode" viewer. Video clips are viewed OK.

Here is the output:

udi@udi-laptop:~$ ls -al /usr/lib/mozilla/plugins
total 8384
drwxr-xr-x 2 udi  users    4096 2008-03-29 00:10 .
drwxr-xr-x 3 root root     4096 2007-04-15 14:58 ..
-rwxr-xr-x 1 udi  users 7040036 2007-06-20 03:31 libflashplayer.so
lrwxrwxrwx 1 udi  users      36 2008-03-19 21:59 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 udi  users      37 2008-03-19 21:59 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 udi  users      34 2008-03-19 21:59 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 udi  users      35 2008-03-19 21:59 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 udi  users      36 2008-03-19 21:59 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 udi  users      37 2008-03-19 21:59 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 udi  users      42 2008-03-19 21:59 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 udi  users      43 2008-03-19 21:59 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 udi  users  118744 2008-03-12 00:08 libvlcplugin.so
-rw-r--r-- 1 udi  users  269216 2007-01-26 02:17 mplayerplug-in-dvx.so
-rw-r--r-- 1 udi  users     981 2007-01-26 02:17 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 udi  users  269408 2007-01-26 02:17 mplayerplug-in-qt.so
-rw-r--r-- 1 udi  users     981 2007-01-26 02:17 mplayerplug-in-qt.xpt
-rw-r--r-- 1 udi  users  269472 2007-01-26 02:17 mplayerplug-in-rm.so
-rw-r--r-- 1 udi  users     981 2007-01-26 02:17 mplayerplug-in-rm.xpt
-rw-r--r-- 1 udi  users  270648 2007-01-26 02:17 mplayerplug-in.so
-rw-r--r-- 1 udi  users  269760 2007-01-26 02:17 mplayerplug-in-wmp.so
-rw-r--r-- 1 udi  users     981 2007-01-26 02:17 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 udi  users     981 2007-01-26 02:17 mplayerplug-in.xpt
lrwxrwxrwx 1 udi  users      60 2008-03-29 00:10 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
udi@udi-laptop:~$ 

and:

udi@udi-laptop:~$ ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 root root  4096 2008-03-29 00:10 .
drwxr-xr-x 5 root root  4096 2008-03-27 18:45 ..
lrwxrwxrwx 1 root root    36 2008-03-19 21:59 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2008-03-19 21:59 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2008-03-19 21:59 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2008-03-19 21:59 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2008-03-19 21:59 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2008-03-19 21:59 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2008-03-19 21:59 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2008-03-19 21:59 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11072 2008-03-25 17:57 libunixprintplugin.so
lrwxrwxrwx 1 root root    37 2008-03-26 11:32 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so
lrwxrwxrwx 1 root root    42 2008-03-19 22:23 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2008-03-19 22:23 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2008-03-19 22:23 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2008-03-19 22:23 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2008-03-19 22:23 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2008-03-19 22:23 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2008-03-19 22:23 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2008-03-19 22:23 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root    60 2008-03-29 00:10 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
udi@udi-laptop:~$ 

I appreciate your effort in helping me.

Udi

---

### Post by Kilz on 2008-03-28
> **Udibuntu said:**
> Problem persists with [SouthparkStudio]("http://www.southparkstudios.com/")s "full episode" viewer. Video clips are viewed OK.

Here is the output:

I appreciate your effort in helping me.

Udi

ok, a few things

open a terminal and type in 
```
sudo chown -R udi:users /usr/lib/firefox/plugins
```

Next, if that doesnt work. 
Drag the script to the desktop, open a terminal and type in 
```
cd ~/Desktop
./GetFlash
```
Look over the install, if you see any issues from the Common Issues section follow the instructions for them, if not copy and paste it into a text file and attach it to a post here .

Lastly, the attachedscreenshot shows the full version player, so we know the r48 plugin works.

---

### Post by Udibuntu on 2008-03-28
Kilz,

I was beginning to think this issue had nothing to do with this plugin or any other.

I disabled all extensions in my FF64bit and, lo and behold, the episode ran smoothly.

By elimination I enabled them one by one until the episode went blank again, and found the perp: Adblock.

Apparently I originally had something wrong with my Flash plugin setup, that's why when I first disabled Adblock I couldn't run the Flash in SouthPark site; When I re-installed the plugin I must have done it right, so when I disabled Adblock a second time I was able to see the vid.

I don't know what's the reason to this freak bug, and frankly I'm too tired to find out at the moment.

I thank you Kilz for doing your best to help. I was looking for the dime under the lamplight, as we say.

I hope I never have to switch to XP again....

Yours with respect and very best regards,

Udi

---

### Post by Sir Rodness on 2008-03-31
Hi,
I'm new to ubuntu. Just started getting tired of dealing with the MS BS and needed a change. I was using version 7.10 and have stayed away from the 64bit versions for a while cause of the issues with flash in firefox ( I like my flash sites). I'm now using 8.04 64bit and very happy cause all my hardware works now and I'm just in love with the GUI and all the toys. Anyway to my point of posting here. Again the reason I stayed away from 64bit is cause I couldn't get flash to work right in 64bit firefox. Well after visiting a few websites on what other's have done from very simple to rather lengthy approaches I was able to come up with a very simple combination that worked for me and I hope it works for you too.

1. Download the lastest version of adobe flash from the adobe website and unpack it.
2. copy libflashplayer.so from your download to your /usr/lib/mozilla/plugins/ directory. 
3. open your terminal and type nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
4. restart firefox if needed. 

Cheers.

---

### Post by Kilz on 2008-04-01
> **Sir Rodness said:**
> Hi,
I'm new to ubuntu. Just started getting tired of dealing with the MS BS and needed a change. I was using version 7.10 and have stayed away from the 64bit versions for a while cause of the issues with flash in firefox ( I like my flash sites). I'm now using 8.04 64bit and very happy cause all my hardware works now and I'm just in love with the GUI and all the toys. Anyway to my point of posting here. Again the reason I stayed away from 64bit is cause I couldn't get flash to work right in 64bit firefox. Well after visiting a few websites on what other's have done from very simple to rather lengthy approaches I was able to come up with a very simple combination that worked for me and I hope it works for you too.

1. Download the lastest version of adobe flash from the adobe website and unpack it.
2. copy libflashplayer.so from your download to your /usr/lib/mozilla/plugins/ directory. 
3. open your terminal and type nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
4. restart firefox if needed. 

Cheers.

Instead of all that you could have downloaded the script, double clicked on it, chosen "run in terminal". Chosen Gutsy from the list of choices as there is no Hardy yet. wait 30 seconds and restarted your browser.

---

### Post by chih on 2008-04-01
This worked for me!  I'm on AMD 64 Gutsy.
After days and days of searching for a solution and settling for Crossover which crashed my browser all the time, this finally worked. Thank you SO much.

---

### Post by Metaleks on 2008-04-05
Just adding a big THANK YOU for this thread.  It has solved the flash issue for me.  It was working before, but sometimes it would turn into a big block and stop working.  Following the original post's script fixed that problem.

Again, a big thank you ^_^

---

### Post by pElf28p on 2008-04-05
> **pElf28p said:**
> Kilz,
I tried the link you provided and followed the steps. Still no luck. ia32-libs does not show in synaptic. Any other ideas/suggestion? Thanks for all the help so far.
-Joe
[B]
A while back I posted the response above based on the following instructions:[/B]

"Well it seems to be solved now!
Thank you Kilz!
I found a website where someone was having the exact same problem with ia32-libs and ubuntu 7.10 x64:[https://answers.launchpad.net/ubuntu...question/15484](https://answers.launchpad.net/ubuntu...question/15484)
The info I got interested in was:
"Most probably the mirror you are using is not up to date. Try again in half an hour or so and it should be ok."
So I found another site which explained a little about the package manger and what happens when you press the "status" button in the manager GUI.
I removed all "Installed (.. config)" packages then (here comes the solution) I went to "Settings->Repositories" (in synaptic packet manager) and in the popup I clicked the dropdown with label "Download from" and clicked "other". There is an option to choose "best server" which I did.. it took awhile but it finally chose one.
After performing a reload of all the packages (using this new mirror) I found ia32-lib and simply installed it 
Then I ran Kilz script and now I am looking at youtube flash videos 
So the whole problem seems to have been a bad repository mirror.
Thanks Kilz and hope this can help some others 
Im out / Soul4"

**Kilz, you had instructed me to file an error report because Ialibs was still not showing in synaptic. Forgive my ignorance, I do not know how to do this as I am still learning about Linux. Would you point me in the direction of learning how to do this? Thanks!**

---

### Post by Kilz on 2008-04-05
> **pElf28p said:**
> [B] to "Settings->Repositories" (in synaptic packet manager) and in the popup I clicked the dropdown with label "Download from" and clicked "other". There is an option to choose "best server" which I did.. it took awhile but it finally chose one.
After performing a reload of all the packages (using this new mirror) I found ia32-lib and simply installed it [/B]


You followed those instructions?

---

### Post by MountainX on 2008-04-05
> **Kilz said:**
> 

 Originally Posted by radamo
I am very new to Linux and hope this isn't a stupid question... I searched around and cannot seem to find how to (if at all posssible) get flash working for Hardy Heron.
```

sudo apt-get install flashplugin-nonfree
``` if flash doesn't work after restarting your browser, file a bug report on launchpad.

I would appreciate it if anyone would explain more about what has changed for Hardy with Firefox 3. **Is the nspluginwrapper no longer needed in 64 bit Firefox 3?**

I understand Adobe will ***not*** be offering Flash in 64 bit for Linux, so how is it possible that  a Hardy 64 bit user can install Flash, javascript and all that other stuff so easily? 

See this post:
[http://ubuntuforums.org/showpost.php?p=4654792&postcount=17](http://ubuntuforums.org/showpost.php?p=4654792&postcount=17)

It sounds like Hardy 64 bit users are doing stuff I could never do when I was running 64 bit Ubuntu. Anyone care to explain it to me? Thanks.

---

### Post by daradib on 2008-04-05
> **MountainX said:**
> I would appreciate it if anyone would explain more about what has changed for Hardy with Firefox 3. **Is the nspluginwrapper no longer needed in 64 bit Firefox 3?**

I understand Adobe will ***not*** be offering Flash in 64 bit for Linux, so how is it possible that  a Hardy 64 bit user can install Flash, javascript and all that other stuff so easily? 

See this post:
[http://ubuntuforums.org/showpost.php?p=4654792&postcount=17](http://ubuntuforums.org/showpost.php?p=4654792&postcount=17)

It sounds like Hardy 64 bit users are doing stuff I could never do when I was running 64 bit Ubuntu. Anyone care to explain it to me? Thanks.

nspluginwrapper is still being used and necessary for 64-bit users.

BTW, if you install the package flashplugin-nonfree in Ubuntu 64-bit 7.10 or 8.04, nspluginwrapper is automagically setup.

---

### Post by MountainX on 2008-04-05
> **daradib said:**
> nspluginwrapper is still being used and necessary for 64-bit users.

BTW, if you install the package flashplugin-nonfree in Ubuntu 64-bit 7.10 or 8.04, nspluginwrapper is automagically setup.

The guy at the other link said, "i just opened firefox, went to a page that needed flash, it asked me if i wanted to install, i did, and bam, worked."

Is it really that simple to install Flash (and other plugins) under Hardy 64 bit now?

---

### Post by Kilz on 2008-04-05
> **MountainX said:**
> The guy at the other link said, "i just opened firefox, went to a page that needed flash, it asked me if i wanted to install, i did, and bam, worked."

Is it really that simple to install Flash (and other plugins) under Hardy 64 bit now?

It should be , yes. But let me remind you that Hardy is still under development. Unless you know how to rescue a broken system, don't install it.

---

### Post by pElf28p on 2008-04-05
> **Kilz said:**
> You followed those instructions?

Yes I did. Was that wrong?

---

### Post by Kilz on 2008-04-05
> **pElf28p said:**
> Yes I did. Was that wrong?

No it wasnt. But if you are having issues getting ia32-libs there is little I can do. Its a file in the official Ubuntu repositories. It isnt something I created. I cant fix issues with it, I have no way to do anything with the official repositories. Please give me the name of the mirror you are using now.

---

### Post by lsans on 2008-04-05
Thank you very much for this helpful script. My inability to fix this has been a real hindrance to using my cool little flash based camcorder or to work with some other stuff I've wanted to experiment with. This forum ismore impressive every time I visit it!

---

### Post by mntamimi on 2008-04-06
Thanks a ton for this! For anyone interested (I have to believe I wasn't the only one) this completely and super easily fixed my inability to get or see the myspace music player. It's great to have that back. Thanks again!

---

### Post by geordie on 2008-04-06
Thank you! Thank you! Thank you! I have just recently switched to Gutsy 64bit and love it the only issue I haven't been able to resolve has been choppy flash video. Now all I have to worry about is what to do with all the extra RAM and processor capability I have from killing Vista! This thread has been a lifesaver!

Geordie
HP Pavillion DV9774CA, Centrino Dual Core 2.0ghz, 3GB RAM, 2x160 SATA, Nvidia 8600, Gutsy 64bit, XP Performance Dual Boot.

---

### Post by bucc5062 on 2008-04-06
I just upgraded to 8.04.  It comes with the Beta version of Firefox.  the upgrade broke my flash player.  Last time I was able to follow some of these scripts and get it to work.  However, I have tried your script and still no joy.

One key issue is that my system does not have a ~/usr/local/firefox/pugins32 folder to move too.  I could build one (and may do so), but do not have much confidence that it will work.

I have been using Linux/Ubuntu now for 6 months.  I love it, I don't have a desire to return to Windows.  I do have a desire to watch videos again and am not happy that Hardy rboke my flash plugin.

So, is there a script, process, magic incantation that I can apply that will get adobe flash player 9 to work in Firefox 3.0 Beta?

What gets me is that it looks like things install, just no plugin action.  FF keeps telling me I need the plugin.

Help?

ls results:

total 12
drwxr-xr-x 2 genuser users 4096 2008-04-06 20:30 .
drwxr-xr-x 4 root   root  4096 2008-04-05 11:24 ..
lrwxrwxrwx 1 root   root    37 2008-04-06 20:30 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 genuser users   60 2008-04-06 20:26 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 genuser users   31 2008-01-16 21:56 xineplugin.so -> ../../xine-plugin/xineplugin.so

drwxr-xr-x 2 genuser users 4096 2008-04-06 20:30 .
drwxr-xr-x 4 root   root  4096 2008-04-05 11:27 ..
lrwxrwxrwx 1 root   root    37 2008-04-06 20:30 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 genuser users   60 2008-04-06 20:26 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 genuser users   31 2008-01-16 21:56 xineplugin.so -> ../../xine-plugin/xineplugin.so

---

### Post by Kilz on 2008-04-07
> **bucc5062 said:**
> I just upgraded to 8.04.  It comes with the Beta version of Firefox.  the upgrade broke my flash player.  Last time I was able to follow some of these scripts and get it to work.  However, I have tried your script and still no joy.

One key issue is that my system does not have a ~/usr/local/firefox/pugins32 folder to move too.  I could build one (and may do so), but do not have much confidence that it will work.

I have been using Linux/Ubuntu now for 6 months.  I love it, I don't have a desire to return to Windows.  I do have a desire to watch videos again and am not happy that Hardy rboke my flash plugin.

So, is there a script, process, magic incantation that I can apply that will get adobe flash player 9 to work in Firefox 3.0 Beta?

What gets me is that it looks like things install, just no plugin action.  FF keeps telling me I need the plugin.

Help?

ls results:

total 12
drwxr-xr-x 2 genuser users 4096 2008-04-06 20:30 .
drwxr-xr-x 4 root   root  4096 2008-04-05 11:24 ..
lrwxrwxrwx 1 root   root    37 2008-04-06 20:30 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 genuser users   60 2008-04-06 20:26 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 genuser users   31 2008-01-16 21:56 xineplugin.so -> ../../xine-plugin/xineplugin.so

drwxr-xr-x 2 genuser users 4096 2008-04-06 20:30 .
drwxr-xr-x 4 root   root  4096 2008-04-05 11:27 ..
lrwxrwxrwx 1 root   root    37 2008-04-06 20:30 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 genuser users   60 2008-04-06 20:26 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 genuser users   31 2008-01-16 21:56 xineplugin.so -> ../../xine-plugin/xineplugin.so

This script is not setup to work with Hardy Heron. If ```
sudo apt-get-install flashplugin-nonfree
``` does not install flash. Make a post on the Hardy Heron section of the forum and (most important) file a bug report on launchpad.

---

### Post by danielcaraj on 2008-04-09
Tank You very Much!!!!!!!!! this solved my problem with flash.  Muchas Gracias!!!!!

---

### Post by GeekGirl1 on 2008-04-09
Thank you also. There is now a bug report in Launchpad. I added my comments: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/214735](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/214735)

---

### Post by domero on 2008-04-10
I can't thank you enough for doing this. It's really helped me out. :KS

---

### Post by crossdelena on 2008-04-10
Thanks a lot this script  (used the recommended one!!) worked perfectly fine for Gutsy....

Cross

---

### Post by izak on 2008-04-10
Apperently I don´t have permission to click the thank you button, so I&#314;l do it the old fasioned way: THANK YOU! Everythin works

---

### Post by theodorekon on 2008-04-11
It seems to solve the problem with the flash 9 player on 64bit systems but do you also have a script for uninstalling it??

---

### Post by Kilz on 2008-04-11
> **theodorekon said:**
> It seems to solve the problem with the flash 9 player on 64bit systems but do you also have a script for uninstalling it??

You might want to read the first post.

---

### Post by boyofford on 2008-04-12
couldn't make it any easier, nice job!

---

### Post by mario.kostelac on 2008-04-12
so... old problem.. but now i spectated the crashing :D.. i was watchinh some youtube clips.. and once flash has just disappeared.. After that, i have not flash... Now i installed again and it works but... i don't want to reinstall every few days

---

### Post by Kilz on 2008-04-12
> **mario.kostelac said:**
> so... old problem.. but now i spectated the crashing :D.. i was watchinh some youtube clips.. and once flash has just disappeared.. After that, i have not flash... Now i installed again and it works but... i don't want to reinstall every few days

type ```
about:plugins
``` into the address bar and hit enter. Find the Flash section, copy it and paste it here please.

---

### Post by bluepowder7 on 2008-04-12
hey, thanks for the script!  as you know, i was asking about the options of using this wrapper or installing a 32-bit version of firefox.  i ended up using your script here, and boy it was fast and easy! a quick check on youtube shows that it works perfectly well.  thanks!

---

### Post by nbhat on 2008-04-13
Thanks for the script I had a32 lib problem. Followed instructions for a32 lib and got flas player installed fully.

---

### Post by mario.kostelac on 2008-04-13
@Kilz, your welcome -> [http://img362.imageshack.us/my.php?image=screenshotup2.png](http://img362.imageshack.us/my.php?image=screenshotup2.png)

---

### Post by Kilz on 2008-04-13
> **mario.kostelac said:**
> @Kilz, your welcome -> [http://img362.imageshack.us/my.php?image=screenshotup2.png](http://img362.imageshack.us/my.php?image=screenshotup2.png)

Thanks, that works.
> **mario.kostelac said:**
> so... old problem.. but now i spectated the crashing :D.. i was watchinh some youtube clips.. and once flash has just disappeared.. After that, i have not flash... Now i installed again and it works but... i don't want to reinstall every few days

In this earllier post, are you saying that you had a crash and flash stopped working?

---

### Post by mario.kostelac on 2008-04-13
Yeah... right that.. Sry for my bad English... But, just to know, only flash crashed (I saw when flash disappeared).

---

### Post by joetaxpayer on 2008-04-13
My sound doesn't work in flash or at apple.com/trailers.  All other system sounds and playback devices work.  I tried the sound solutions in the first post.  Thanks in advance for help.

```

simplej@knubbins:~$ ls -al /usr/lib/mozilla/plugins/
total 6900
drwxr-xr-x 2 simplej users    4096 2008-04-13 17:13 .
drwxr-xr-x 3 root    root     4096 2007-10-15 18:27 ..
-rwxr-xr-x 1 simplej users 7040036 2007-06-19 19:31 libflashplayer.so
lrwxrwxrwx 1 simplej users      38 2008-04-10 10:02 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 simplej users      36 2008-04-03 05:19 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 simplej users      37 2008-04-03 05:19 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 simplej users      34 2008-04-03 05:19 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 simplej users      35 2008-04-03 05:19 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 simplej users      36 2008-04-03 05:19 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 simplej users      37 2008-04-03 05:19 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 simplej users      42 2008-04-03 05:19 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 simplej users      43 2008-04-03 05:19 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 simplej users      60 2008-04-13 17:13 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
simplej@knubbins:~$ ls -al /usr/lib/firefox/plugins/
total 24
drwxr-xr-x 2 simplej users  4096 2008-04-13 17:13 .
drwxr-xr-x 5 root    root   4096 2008-04-03 21:35 ..
lrwxrwxrwx 1 simplej users    36 2008-04-03 05:19 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 simplej users    37 2008-04-03 05:19 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 simplej users    34 2008-04-03 05:19 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 simplej users    35 2008-04-03 05:19 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 simplej users    36 2008-04-03 05:19 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 simplej users    37 2008-04-03 05:19 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 simplej users    42 2008-04-03 05:19 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 simplej users    43 2008-04-03 05:19 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 simplej users 11456 2008-03-25 10:19 libunixprintplugin.so
lrwxrwxrwx 1 simplej users    60 2008-04-13 17:13 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
simplej@knubbins:~$ uname -a
Linux knubbins 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

```

---

### Post by Kilz on 2008-04-13
> **joetaxpayer said:**
> My sound doesn't work in flash or at apple.com/trailers.  All other system sounds and playback devices work.  I tried the sound solutions in the first post.  Thanks in advance for help.


So you see flash video, but no sound? How are you viewing the quicktime trailers, flash cant see them and I dont think I see a plugin for them?

---

### Post by joetaxpayer on 2008-04-13
I dunno, totem?  I guess I really don't understand the question (sry not much experience here).  What I do know is that I can visit youtube and other flash sites, and I get animations, but no sound.  I also tried going to apple trailers, since you mentioned it in a previous post, and the same thing happens there.  I am primarily using swiftweasel 64, but I get the same results in firefox 64.

---

### Post by joetaxpayer on 2008-04-13
Check that...I looked in my download actions, and it says I'm using quicktime plugin 7.2.0

EDIT:
about: plugins says qt video and audio is being handled by totem 2.20.2

---

### Post by joetaxpayer on 2008-04-13
I think I found the problem.  I unpacked some files into lib32 to try to get skype running, and it overwrote some symbolic links in the directory.  

```
simplej@knubbins:~$ ldconfig
/sbin/ldconfig.real: /lib32/libXss.so.1 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtOpenGL.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtDesigner.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtNetwork.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtAssistantClient.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtDBus.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtCore.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libdbus-1.so.3 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtGui.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtXml.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtTest.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtDesignerComponents.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtSvg.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtScript.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libsigc-2.0.so.0 is not a symbolic link

```

So obviously this has nothing to do with your script. :lolflag:

I will start a new thread.

---

### Post by radamo on 2008-04-16
Firefox 3 crashed hard on me and I had to create a new profile.  Flash, Java etc. all have to be reinstalled.  I can't get Flash working now...

I am running the latest Hardy beta code and all updates.  I have followed the instructions to purge flash and still no luck.  I also ran the script ((within oldflash-0.1.5-1.tar.gz) provided by Kilz and nothing yet.

Here is the output of the three commands requested:
radamo@lintest:~$ ls -al /usr/lib/mozilla/plugins
total 6900
drwxr-xr-x 2 radamo users    4096 2008-04-16 20:47 .
drwxr-xr-x 4 root   root     4096 2008-03-19 17:27 ..
-rwxr-xr-x 1 radamo users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 radamo users      60 2008-04-16 20:47 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
radamo@lintest:~$ ls -al /usr/lib/firefox/plugins
total 12
drwxr-xr-x 2 radamo users 4096 2008-04-16 20:47 .
drwxr-xr-x 4 root   root  4096 2008-04-06 09:50 ..
lrwxrwxrwx 1 radamo users   60 2008-04-16 20:47 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
radamo@lintest:~$ uname -a
Linux lintest 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

Thanks for any help....
RA

---

### Post by Kilz on 2008-04-17
The script is not compatible with Hardy. Please read the first post on how to install flash to Hardy.

---

### Post by radamo on 2008-04-17
> **Kilz said:**
> The script is not compatible with Hardy. Please read the first post on how to install flash to Hardy.

I thought I had tried that... I may have gotten confused last night... Thanks for the note, I will retry when back at home.  I really do appreciate you taking the time to help.  These kind of threads really help us newcomers to Ubuntu...  I will post back after I get a chance to try again.
RA

---

### Post by radamo on 2008-04-18
Thanks again Kilz... I removed all instances of the plugin reran the Hardy script and it worked like a charm... 
RA

---

### Post by Estesark on 2008-04-18
This plugin & method worked fine for me until today - now most websites containing Flash cause Firefox to hang. I have to force quit Firefox and reload it.

I'm sure I haven't updated Firefox or the plugin in the last day, and I've tried completely removing and reinstalling both, but to no avail. Any ideas, anyone?

Let me know if you need any additional information.

---

### Post by KevinCLovesU on 2008-04-19
Will you develop a script for Hardy when Hardy goes final?

---

### Post by Kilz on 2008-04-19
> **KevinCLovesU said:**
> Will you develop a script for Hardy when Hardy goes final?

You might want to read the first post in this thread again. In case it isnt clear, there are instructions on how to use a simple command to accomplish it. As long as thats all it takes, I don't think it will be necessary. But I thought the same thing about Gutsy.

---

### Post by guj4_n3b3sk4 on 2008-04-20
I have performed tutorial from the 1st page on 64-bit 7.10 Ubuntu, and it works just fine (although I've forgotten to close browser while instaling it).

Thank You.

---

### Post by frcr on 2008-04-21
Great job with this script, it reallyu helps.

But i've got a problem: sometimes my FF just stops playing flash - replaces animation with grey square and i have to restart it to have animation back.

Does anyone have same problem? Or... am i just stupid? :D

Thanks in advance.

---

### Post by MosMusy on 2008-04-21
I don't have a "getflash" file at least I can't find it. And also I can't find anything that says "extract here" only "extract", And can you please be a little more detailed on your instructios (e.g. do I have to open it with archive manager? where the "get flash" folder is?)

---

### Post by MosMusy on 2008-04-21
Disregard my last post,now I did everything you said and it still doesn't work!!! I have tried every possible way to install the stupid flash plugin and it still tells me the plug in is missing. Then when I go to install the plug-in in Firefox, it tells me I already have it! What should I do!

---

### Post by dptxp on 2008-04-21
Kilz, Flash worked in iceweasel in 64-bit sidux NYX without nspluginwrapper. I have not installed any 32 bit libraries so far.
Wonder how ?

---

### Post by Kilz on 2008-04-22
> **dptxp said:**
> Kilz, Flash worked in iceweasel in 64-bit sidux NYX without nspluginwrapper. I have not installed any 32 bit libraries so far.
Wonder how ?

Perhaps you installed a 32bit version of the browser, or the wrapper without knowing it. Secondly, perhaps you didn't install Macromedia flash, but one of the open source versions.

---

### Post by Kilz on 2008-04-22
> **MosMusy said:**
> Disregard my last post,now I did everything you said and it still doesn't work!!! I have tried every possible way to install the stupid flash plugin and it still tells me the plug in is missing. Then when I go to install the plug-in in Firefox, it tells me I already have it! What should I do!

Drag the script to the desktop, open a terminal and type in

```
cd ~/Desktop
./GetFlash
```

If flash works, your set, if not do the following, dont close the terminal. Look over the install, if you see any issues from the Common Issues section follow the instructions for them, if not copy and paste it into a text file and attach it to a post here . Also list what version of Ubuntu you are running and what version of your browser.

---

### Post by NDJeff on 2008-04-23
The script didn't work for me as written (AMD64, Hardy), I removed the - before install like so:

```
 sudo apt-get install flashplugin-nonfree
```

And it installed fine.

---

### Post by Kilz on 2008-04-23
> **NDJeff said:**
> The script didn't work for me as written (AMD64, Hardy), I removed the - before install like so:

```
 sudo apt-get install flashplugin-nonfree
```

And it installed fine.

The script is not designed to work with Hardy, you basically followed the instructions later on in the howto for Hardy.

---

### Post by Israphel on 2008-04-24
NDJeff wanted to say that is "apt-get install" and not "apt-get-install", fix that.

---

### Post by the_dude_abides on 2008-05-01
I've got Flash working in 64 bit Hardy with Firefox 3.0b5.  Thanks very much to this script in figuring it out.

Plugins are not in the same directory, i.e. /usr/lib/mozilla/plugins or /usr/lib/firefox/plugins.  By default when I upgraded from Gutsy to Hardy (using the update manager) it upgraded to the new fireforx and the plugins directory is now /usr/lib/firefox3.0b5

I modified the Gutsy section of the GetFlash script as below and ran it, restarted my browser and flash worked fine. (As a note I made sure to remove all flash plugin installations from everywhere before running it)

```

#make wrapped plugin
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/

```

to:

```

#make wrapped plugin
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0b5/plugins/

```

I only added the last two lines and I'm pretty sure the last line on its own is sufficient - but this worked for me.  

Hope this helps.

---

### Post by Kilz on 2008-05-01
> **the_dude_abides said:**
> I've got Flash working in 64 bit Hardy with Firefox 3.0b5.  Thanks very much to this script in figuring it out.

Plugins are not in the same directory, i.e. /usr/lib/mozilla/plugins or /usr/lib/firefox/plugins.  By default when I upgraded from Gutsy to Hardy (using the update manager) it upgraded to the new fireforx and the plugins directory is now /usr/lib/firefox3.0b5

I modified the Gutsy section of the GetFlash script as below and ran it, restarted my browser and flash worked fine. (As a note I made sure to remove all flash plugin installations from everywhere before running it)

```

#make wrapped plugin
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/

```

to:

```

#make wrapped plugin
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0b5/plugins/

```

I only added the last two lines and I'm pretty sure the last line on its own is sufficient - but this worked for me.  

Hope this helps.

Thanks, incorporated.

---

### Post by tim shores on 2008-05-09
that was great, worked on hardy amd64/firefox 3.0b5, thanks a lot

---

### Post by ondrejlipar on 2008-05-15
> **the_dude_abides said:**
> I've got Flash working in 64 bit Hardy with Firefox 3.0b5.  Thanks very much to this script in figuring it out.

Plugins are not in the same directory, i.e. /usr/lib/mozilla/plugins or /usr/lib/firefox/plugins.  By default when I upgraded from Gutsy to Hardy (using the update manager) it upgraded to the new fireforx and the plugins directory is now /usr/lib/firefox3.0b5

I modified the Gutsy section of the GetFlash script as below and ran it, restarted my browser and flash worked fine. (As a note I made sure to remove all flash plugin installations from everywhere before running it)

```

#make wrapped plugin
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/

```

to:

```

#make wrapped plugin
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0b5/plugins/

```

I only added the last two lines and I'm pretty sure the last line on its own is sufficient - but this worked for me.  

Hope this helps.

finally something that worked for me and my FF3b5 on Hardy 64. But I still can't hear any sound when it comes to flash :/

---

### Post by Kilz on 2008-05-15
[SIZE="5"][COLOR="Red"]**This post has been replaced in the new 64bit section. [Please post in the new post.]("http://ubuntuforums.org/showthread.php?t=772490") This post will no longer be supported.**[/COLOR][/SIZE]

---

