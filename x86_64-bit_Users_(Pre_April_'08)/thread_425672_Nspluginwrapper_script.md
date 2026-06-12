---
title: "Nspluginwrapper script"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kilz on 2007-04-27
[COLOR="Red"]*********This is an old post on the script. [Please visit THIS POST]("http://ubuntuforums.org/showthread.php?t=476924") for the latest version and information*********[/COLOR]


This script is for Feisty, Edgy, and Dapper, (maybe even Breezy if anyone is still running it) Do not use it on Gutsy. Gutsy has its own nspluginwrapper package in the repositories.

I have learned that nspluginwrapper is now stable, at least in Feisty. It works with the 32bit Macromedia Flash plugin that most users need. I dont think the 64bit browser is to the point that I can stop making the Firefox32 script. There are other plugins (java) that dont work for all versions. This install script should make it easier for those running Feisty to install it and Flash.
I placed it at the bottom of my Firefox 32 page for now. [Click here if you want to download it.]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.6.tar.gz")
The script also works with the 64bit builds of [Swiftweasel]("http://sourceforge.net/projects/swiftweasel/"), an optimized build of Firefox.

If you have any errors [please download this version of the script]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.6-ts.tar.gz"). It is the same script, but it will not clean up after itself. This will make troubleshooting easier. Please also read the included README file for instructions on what information to report in your post.

---

### Post by AlexDe on 2007-04-27
Worked like a charm, thanks :)

---

### Post by ronocdh on 2007-04-30
Just wondering if this will be kept current and include the 1.43 version of ndiswrapper. Also, I've read elsewhere that this version of ndiswrapper improves 64-bit support, but I don't see that anywhere on [their site]("http://ndiswrapper.sourceforge.net/joomla/?title=Special:Recentchanges&feed=atom"). Was this yet more 64-bit FUD, or is there something to the claim?

---

### Post by Tyrdium on 2007-04-30
Worked perfectly on my C2D Macbook Pro running Feisty. Thank you!

---

### Post by Kilz on 2007-04-30
> **ronocdh said:**
> Just wondering if this will be kept current and include the 1.43 version of ndiswrapper. Also, I've read elsewhere that this version of ndiswrapper improves 64-bit support, but I don't see that anywhere on [their site]("http://ndiswrapper.sourceforge.net/joomla/?title=Special:Recentchanges&feed=atom"). Was this yet more 64-bit FUD, or is there something to the claim?

This is a script for installing the nspluginwrapper that allows 32bit flash to work on the 64bit Firefox in the amd64 version of Ubuntu. ndiswrapper is for a 32bit driver for  networking cards, I havent even tried a script for it. But I might in the future.

---

### Post by triplep on 2007-05-01
Kliz, 

Works great!

You might want to add a 'pkill firefox' at the end. If they are using FF2, they will get the session restored when the start FF again.

---

### Post by lucky2 on 2007-05-01
P4D 2.6ghz feisty 64bit , 6200 , sblive , 40/60gig ata 100/133 , asrock 4core dual vsta mobo. Works like a charm, cheers.

---

### Post by Richhard on 2007-05-01
> **Kilz said:**
> I have learned that nspluginwrapper is now stable, at least in Feisty. I dont think the 64bit browser is to the point that I can stop making the Firefox32 script. There are other plugins (java) that dont work for all versions. This install script should make it easier for those running Feisty.
I placed it at the bottom of my Firefox 32 page for now. [Click here if you want to download it.]("http://home.comcast.net/~next/nsplugin-wrapper-install-0-1.tar.gz")

:KS  I would like to thank you very much: this is an absolut excellent solution and I had to search
longtime to find it!!

I am a dummy beginner with Ubuntu 7.04 AMD64 and your solution works excellent.

---

### Post by Kingedgar on 2007-05-01
Perfect, I had tried using nspluginwrapper once before with little result. This worked and I am well on my way with 64bit firefox.

---

### Post by NullHead on 2007-05-01
What is nspluginwrapper and what does it do? I know of and use ndiswrapper... but are they the same?

---

### Post by Kilz on 2007-05-01
> **NullHead said:**
> What is nspluginwrapper and what does it do? I know of and use ndiswrapper... but are they the same?

No they are not the same

ndiswrapper = a wrapper that allows 32bit network/wireless cards to be used on the 64bit version of Ubuntu.

nspluginwrapper = a wrapper that allows the 32bit Macromedia flash plugin to be used on the 64bit browser. If you only need the flash plugin and no others this might be an option for you. If you need a java plugin it is better imho to install the 32bit firefox.

---

### Post by jamesford on 2007-05-01
didnt try it myself but gave the link to a friend who never got around to installing flash cos she thought the method was too complicated. now shes got flash working so great job :)

---

### Post by NullHead on 2007-05-01
oh I got it now thanks Kilz once again. I allready have java flash and all of the good stuff with a 32bit firefox so no need hear.

---

### Post by boredom on 2007-05-02
Works great, I was getting 

> *** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for ./libflashplayer.so


when I did it manually.  Only way I got flash to work is with your script, thanks.

Boredom

---

### Post by Angelbeast on 2007-05-03
Okay i still don't understand how to install these type of files...just how do i get this up and running?

---

### Post by Kilz on 2007-05-03
> **Angelbeast said:**
> Okay i still don't understand how to install these type of files...just how do i get this up and running?

Download script, double click on it, select run in terminal.

---

### Post by rai4shu2 on 2007-05-03
```
sudo ln -s ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -s ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/
```

This doesn't really seem like a good idea, in particular if you have multi-user environment. Is this code even necessary?

---

### Post by Kilz on 2007-05-03
> **rai4shu2 said:**
> ```
sudo ln -s ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -s ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/
```

This doesn't really seem like a good idea, in particular if you have multi-user environment. Is this code even necessary?

No, it may not be a good idea in that situation. Im going to have to look into how to modify the script for that situation. Probably just copy the file into place.

---

### Post by wildlifer on 2007-05-03
Works great! Thanks Kilz!

---

### Post by Angelbeast on 2007-05-03
> **Kilz said:**
> Download script, double click on it, select run in terminal.

Thanks ...okay i got the plugin wrapper installed...but how do i install flash itself? sorry for the newbie stuff...

---

### Post by Kilz on 2007-05-03
> **Angelbeast said:**
> Thanks ...okay i got the plugin wrapper installed...but how do i install flash itself? sorry for the newbie stuff...

Its already done. All you need to do after installing is restart the browser.

---

### Post by Angelbeast on 2007-05-03
> **Kilz said:**
> Its already done. All you need to do after installing is restart the browser.

ooooooo...thank you so much ... the lst step to Ubuntu enjoyment is now completed...mwahahaha  *LOL*

---

### Post by Kilz on 2007-05-03
> **Angelbeast said:**
> ooooooo...thank you so much ... the lst step to Ubuntu enjoyment is now completed...mwahahaha  *LOL*

Your welcome. As I see it the purpose of an install script is to install everything needed. Then set it up. It would have been hard to set up the wrapper without the plugin.  :D

---

### Post by Angelbeast on 2007-05-04
> **Kilz said:**
> Your welcome. As I see it the purpose of an install script is to install everything needed. Then set it up. It would have been hard to set up the wrapper without the plugin.  :D

being such a newbie is so frustrating *LOL* ... 

hey have you heard of anyone have it so that the flash content becomes not visible and they have to restart the browser periodically to get it back?

---

### Post by Kilz on 2007-05-04
> **Angelbeast said:**
> being such a newbie is so frustrating *LOL* ... 

hey have you heard of anyone have it so that the flash content becomes not visible and they have to restart the browser periodically to get it back?

Nope, never heard of that happening.

---

### Post by ritesh on 2007-05-04
thanks thanks .....thanks to the power INFINITY....................this thing worked like MAGIC................I was using Red hat linux v4 (enterprise edition) on my dell precision workstation 390(64 bit) and was never able to install the flashplayer.........but your post and Ubuntu 7.04 did the magic......

Thanks once again...............

---

### Post by r_rehashed on 2007-05-04
Wow! Great script!

Wish getting the Sun Java 6 plugin to work was so easy.

Thanks a lot

---

### Post by Kilz on 2007-05-04
> **r_rehashed said:**
> Wow! Great script!

Wish getting the Sun Java 6 plugin to work was so easy.

Thanks a lot

The java plugin is not supported by nspluginwrapper. I wish it would work also.

---

### Post by Meatetarian on 2007-05-08
This script has absolutely made my day!  I've been looking for a simple solution that would allow me to keep my 64-bit browser since last week.

Thanks a ton!

---

### Post by Kilz on 2007-05-10
> **Meatetarian said:**
> This script has absolutely made my day!  I've been looking for a simple solution that would allow me to keep my 64-bit browser since last week.

Thanks a ton!

Your welcome, this script is all about making things easy. :D

---

### Post by Angelbeast on 2007-05-12
Hey one more quick question...I wanted to give Konqueror a try...Now i hve everything already set up with Firefox...do i have todo everything all over again for Konqueror or will it even work for it?

---

### Post by Kilz on 2007-05-12
I am not sure, I am a true gnome fan. My first distro was SuSE , but I only used kde for a few days before switching to gnome. When I went looking for a replacement because of problems with suse 10.1, I looked for a gnome based distro.
But it may work. You can try copying in the wrapped plugin to the knoqueror plugin folder(whereever that is) to see. This command should work, but you are going to have to edit the path to the konqueror plugin folder. Then restart konqureror after you copy it in.
```
sudo cp -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /location/of/konqueror/plugins
```

---

### Post by kuja on 2007-05-12
> **Angelbeast said:**
> Hey one more quick question...I wanted to give Konqueror a try...Now i hve everything already set up with Firefox...do i have todo everything all over again for Konqueror or will it even work for it?

In Feisty yes, in previous version of (K)Ubuntu, no.

---

### Post by nss0000 on 2007-05-13
BigKILZ:

Running Dapperx54:

That fancy **fishwrapper** script does NOT work for me. I ran it -- bunches of crap come down. I get/unpack FLASH. Run the installer. Nadanothingnix except an error message that sez it's a x32 app not x64. Shame-on-me. 

Humm ............x64Dapper still not ready for usrland, eh ... 

nss
*****

---

### Post by Kilz on 2007-05-13
> **nss0000 said:**
> BigKILZ:

Running Dapperx54:

That fancy **fishwrapper** script does NOT work for me. I ran it -- bunches of crap come down. I get/unpack FLASH. Run the installer. Nadanothingnix except an error message that sez it's a x32 app not x64. Shame-on-me. 

Humm ............x64Dapper still not ready for usrland, eh ... 

nss
*****

The script was tested on 64bit Dapper, its what I run. Please run the script, and copy and paste the contents of the terminal, including any errors to a post here.

---

### Post by MelancholyStoo on 2007-05-13
Hey Kilz, just used the script.
I have to say thanks for making my life SO much easier!  I had no idea that flash 9 didn't work on the 64 version until i tried to install it.  You have saved me so much time and effort, keep up the good work!

Thanks again,

Stoo.

---

### Post by nepenthes on 2007-05-14
Thanks for the script, it worked great on my system!

However I have a feeling (also with my former Edgy - nspluginwrapper config) that Flash seems to work 100%, but actually it does work only for 99,5%. It sometimes, in very complex flash applications, does ignore mouse clicks, mouse-over seems to work but the click goes unnoticed.
Example is [http://www.spiegel.de/multimediauebersicht/](http://www.spiegel.de/multimediauebersicht/) when you click on the magnifying glass and try to watch some of the videos. Some start, others ignore the click, sometimes I can not even scroll down the list. Same goes for some sesamestreet games and other flash stuff.
I don't have those problems in my firefox32 setup on the same computer.

Still these are minor problems, generally happy.

Cheers, Nepenthes

---

### Post by danbert on 2007-05-15
This is kinda beyond the scope of these forums but...  I dualboot Ubuntu with Windows XP x64, and I run Minefield (Firefox 3.0.0a) because it's the only 64bit Firefox for Windows.  Is there a similar hack to get flash running in 64 bit Firefox for Windows?  (Once again, I find that Linux can do more than Windows, and get it done easier)

---

### Post by Limon47 on 2007-05-15
Hello!, Kilz. This is my 1st post and very new to Linux (Ubuntu). I would like to thank you for the script. It worked great in my system (laptop). Thanks a lot.

---

### Post by Mr. Brownstone on 2007-05-16
This script did not work for me off the bat. Here is what I needed to do to get it to run on my 64-bit laptop running the latest Feisty (changed lines are in red):```
#!/bin/bash

#make working directory
sudo mkdir /tmp/nsplugwrapper

#move to working directory
cd /tmp/nsplugwrapper

#install needed packages
[color=#ff0000]#sudo apt-get -y install ia32-libs ia32-libs-gtk linux32 lib32asound2 alien[/color]
[color=#008800]#I ran apt-get outside of this script to make sure everything needed
#was already installed before running the other commands[/color]

#Dowload rpm's
sudo wget -c http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.4-1.x86_64.rpm
sudo wget -c http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm

#Create deb files
sudo alien nspluginwrapper-0.9.91.4-1.x86_64.rpm
sudo alien nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm

#Install deb files
sudo dpkg -i *.deb

#Get Flash and place it
sudo wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
sudo tar -xzvf install_flash_player_9_linux.tar.gz
sudo [color=#ff0000]cp[/color] -f /tmp/nsplugwrapper/install_flash_player_9_linux/libflashplayer.so /usr/lib/[color=#ff0000]firefox[/color]/plugins/
sudo [color=#ff0000]cp[/color] -f /tmp/nsplugwrapper/install_flash_player_9_linux/flashplayer.xpt /usr/lib/[color=#ff0000]firefox[/color]/plugins/
[color=#008800]#Needed plugin in /usr/lib/firefox/ rather than /usr/lib/mozilla/
#Perhaps this is Firefox2 specific? Also changed mv to cp in case something went wrong[/color]

#make wrapped plugin
nspluginwrapper -i /usr/lib/[color=#ff0000]firefox[/color]/plugins/libflashplayer.so
[color=#ff0000]#sudo ln -s ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
#sudo ln -s ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/[/color]
[color=#008800]#Neither of the above two lines were needed. nspluginwrapper installed the
#wrapped plugin into ~/.mozilla/plugins/ automatically. If another user wants the
#flash plugin they should run the nspluginwrapper line from their own shell[/color]

#Clean up files
[color=#ff0000]#sudo rm -fdr /tmp/nsplugwrapper[/color]
[color=#008800]#Leave this folder intact in case something goes wrong[/color]
```Thanks for the script!

---

### Post by Kilz on 2007-05-16
> **Mr. Brownstone said:**
> This script did not work for me off the bat. Here is what I needed to do to get it to run on my 64-bit laptop running the latest Feisty (changed lines are in red):Thanks for the script!

You basically made the script into a howto. There already is a howto, that some people for some reason cant make work.

```
#install needed packages
#sudo apt-get -y install ia32-libs ia32-libs-gtk linux32 lib32asound2 alien
#I ran apt-get outside of this script to make sure everything needed
#was already installed before running the other commands

```
Why? The script uses apt-get, and everything is available in the repos.

```
#Needed plugin in /usr/lib/firefox/ rather than /usr/lib/mozilla/
#Perhaps this is Firefox2 specific? Also changed mv to cp in case something went wrong
```

According to the N[spluginwrapper documentation]("http://gwenole.beauchesne.info/projects/nspluginwrapper/#documentation") the reason why you want to use //usr/lib/mozilla/plugins is to make them avilable system wide. By moving them to the firefox directory, only that install can use it. 
Since the plugins are not needed in the place they were untared why not move them? There have been no problems with this script, why expect problems now?

```
#Neither of the above two lines were needed. nspluginwrapper installed the
#wrapped plugin into ~/.mozilla/plugins/ automatically. If another user wants the
#flash plugin they should run the nspluginwrapper line from their own shell
```

Why would a user want to run a script to setup the wrapper, then open a shell and ttype in commands. The reason a script is created or used is so that all you need do is click on it and everything is done for you.

```
#Leave this folder intact in case something goes wrong
```
But you are not the first person to run this script, nothing has gone wrong yet. I always clean up install files at the end. Its just me, I dont like leaving useless, unused files all over the place. Its one of those things I hated about windows.

---

### Post by Enverex on 2007-05-16
Didn't work for me, the last chunk is...

```
install_flash_player_9_linux/
install_flash_player_9_linux/Readme.txt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
install_flash_player_9_linux/flashplayer.xpt
mv: cannot stat `/home/enverex/.mozilla/plugins/npwrapper.libflashplayer.so': No such file or directory
ln: target `/usr/lib/mozilla-firefox/plugins/' is not a directory: No such file or directory




The plugin wrapper has been installed
You will need to restart Firefox for the changes to take effect
```

---

### Post by Kilz on 2007-05-16
> **Enverex said:**
> Didn't work for me, the last chunk is...

```
install_flash_player_9_linux/
install_flash_player_9_linux/Readme.txt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
install_flash_player_9_linux/flashplayer.xpt
mv: cannot stat `/home/enverex/.mozilla/plugins/npwrapper.libflashplayer.so': No such file or directory
ln: target `/usr/lib/mozilla-firefox/plugins/' is not a directory: No such file or directory




The plugin wrapper has been installed
You will need to restart Firefox for the changes to take effect
```

What version of Ubuntu are you running? Are you running Ubuntu/Kubuntu/xubuntu?

---

### Post by Enverex on 2007-05-16
It didn't work when I tried it before on Feisty and now I've updated to Gutsy which is where that error was posted from. It's stock Ubuntu.

---

### Post by eduardoska on 2007-05-18
This was Awesome!! Worked amazing! Thank you!!

---

### Post by barryoneal on 2007-05-18
This worked great for me, thanks.

b.

---

### Post by Mr. Brownstone on 2007-05-18
> **Kilz said:**
> But you are not the first person to run this script, nothing has gone wrong yetIt went wrong. I fixed it. What's the big deal? Hopefully others will learn from my mistake.

---

### Post by chrisv on 2007-05-19
Thanks Kilz, it worked for me but i had to do some tinkering. I will explain my story just in case somebody else is in a similar situation or Kilz may wish to change the script to handle my situation. 


OK, this is my story: 
Several months ago, when i was still running edgy, i used the old scriptless nspluggingwrapper method (i.e., by hand copying and moving files etc.) and it worked for me. I was very happy but eventually I upgraded to feisty and sure enough the darned thing stopped working. 

So i went back to the forums and found out about Kilz and his helpful script. But that did not work either. 

So i went into my mozilla/plugins and mozilla-firefox/plugins directories and decided to just delete everything that has the word 'flash' in it to give the script a fresh start. I also went into synaptic and removed all gnash packages and libraries. 

Then I ran Kilz's script  again. And it worked !!!

This may seem obvious to you guys but i am a newbie so it was quite a revelation. 

Thanks again Killz. Once again my Ubuntu does everything i need it to do!

---

### Post by pentax on 2007-05-20
I've been trying the instructions, but without any success. I'm using Kubuntu feisty. Here is the output from the terminal
----------------------------------------------------------------------------------------------------------------------

19:01:46 (61.08 KB/s) - `nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm' saved [51010/51010]

sudo: alien: command not found
sudo: alien: command not found
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
--19:01:49--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.42.70
Connecting to fpdownload.macromedia.com|72.246.42.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,609,703 (2.5M) [application/x-gzip]

100%[====================================>] 2,609,703     95.27K/s    ETA 00:00

19:02:19 (86.17 KB/s) - `install_flash_player_9_linux.tar.gz' saved [2609703/2609703]

install_flash_player_9_linux/
install_flash_player_9_linux/Readme.txt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
install_flash_player_9_linux/flashplayer.xpt
mv: target `/usr/lib/mozilla/plugins/' is not a directory: No such file or directory
mv: target `/usr/lib/mozilla/plugins/' is not a directory: No such file or directory
./nspw install: line 30: nspluginwrapper: command not found
mv: target `/usr/lib/mozilla/plugins/' is not a directory: No such file or directory
ln: creating symbolic link `/usr/lib/mozilla-firefox/plugins/npwrapper.libflashplayer.so' to `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': File exists

The plugin wrapper has been installed
You will need to restart Firefox for the changes to take effect
-------------------------------------------------------------------------------------------------------
So I restart FireFox and nada, no flash :(

---

### Post by NullHead on 2007-05-20
It looks like you don't have alien. Aline is a rpm to deb converter ... so try this in your terminal and run the script again```
sudo apt-get install alien
```

---

### Post by pentax on 2007-05-21
> **NullHead said:**
> It looks like you don't have alien. Aline is a rpm to deb converter ... so try this in your terminal and run the script again```
sudo apt-get install alien
```

Hey that worked:D thanks

---

### Post by brazzmonkey on 2007-05-23
thanks, works fine with konqueror too.

---

### Post by jusmurph on 2007-05-24
It worked for me, however a day later i have lost sound from flash (notably youtube)

Worked beautifully yesterday...

---

### Post by Battie on 2007-05-24
Thank you so much for this!  Gnash was a nice idea, but I couldn't stand the choppy scrolling and the way it seemed to rasterize everything.  I'm so glad to have real Flash again!

---

### Post by IgnorantGuru on 2007-05-24
If I use this, will I be using the Windows version of flashplayer? (*shudder*)  Or the linux 32 bit version wrapped in 64bit?

Also, if anyone has an opinion - I'm currently running 32bit Kubuntu but would like to give 64 a try.  I assume I can have both 32bit and 64bit Firefox installed simultaneously (in case I want to use Java)?

And will any other common apps require 32 bit?  For example, awhile back I tried SUSE64, but after installing 32 bit firefox, I then had to use 32bit MPlayer and thus 32bit avidemux (due to shared dependencies), so it was a bit of a mess.  Thoughts?  Thanks for any help.

---

### Post by Aidy on 2007-05-24
> **jusmurph said:**
> It worked for me, however a day later i have lost sound from flash (notably youtube)

Worked beautifully yesterday...

Are you using alsa 1.0.14 (latest)?
I believe there's a known issue with it and Flash.

I've got a bodge for it:

wget [http://dev.gentooexperimental.org/~peper/distfiles/emul-linux-x86-soundlibs-2.5.tar.bz2](http://dev.gentooexperimental.org/~peper/distfiles/emul-linux-x86-soundlibs-2.5.tar.bz2)

Extract, and move the resulting emul/linux/x86/usr/lib to /usr/lib32

Finally, run ldconfig /usr/lib32

IgnorantGuru - The script posted by the OP sets up/installs the linux 32 bit version, and wraps it.

---

### Post by jusmurph on 2007-05-25
> **Aidy said:**
> Are you using alsa 1.0.14 (latest)?
I believe there's a known issue with it and Flash.

I've got a bodge for it:

wget [http://dev.gentooexperimental.org/~peper/distfiles/emul-linux-x86-soundlibs-2.5.tar.bz2](http://dev.gentooexperimental.org/~peper/distfiles/emul-linux-x86-soundlibs-2.5.tar.bz2)

Extract, and move the resulting emul/linux/x86/usr/lib to /usr/lib32

Finally, run ldconfig /usr/lib32


Thanks.

<--- Noob

The download and extract is easy, i can even move it. However, the " run ldconfig /usr/lib32". Can you elaborate on that a bit more please? What exactly do i need to do there?

---

### Post by Aidy on 2007-05-25
just do:

sudo ldconfig /usr/lib32

I should mention that the error I was getting prior to performing these steps was:

```
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
```

when attempting to run Firefox with audio'd Flash.

---

### Post by jusmurph on 2007-05-25
I never got an error message, just no sound.

I then checked the mp3's and they worked fine.

---

### Post by Aidy on 2007-05-25
> **jusmurph said:**
> I never got an error message, just no sound.


You'd need to launch it from a console window to get the errors, or peruse the x error messages log.

---

### Post by jusmurph on 2007-05-25
All of which i would need further explaination of prior...

Could you please explain a bit more.

---

### Post by Aidy on 2007-05-25
Just type "firefox" from a console window.

---

### Post by jusmurph on 2007-05-25
O'm going to assume console window = terminal window?

---

### Post by NullHead on 2007-05-25
Yes you are correct.

---

### Post by jusmurph on 2007-05-25
got it, thanks!

---

### Post by jusmurph on 2007-05-25
Ok, i just restarted my system and now Flash has no sound again :(.

I went through the steps again and its not willing to work ..?

---

### Post by Kilz on 2007-05-25
[Try this package.]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb")

---

### Post by Enverex on 2007-05-25
No thoughts about the failure on my machne Kilz?

---

### Post by Kilz on 2007-05-25
> **Enverex said:**
> No thoughts about the failure on my machne Kilz?

I have done some testing, and for the life of me I dont know why it didnt work when you originally tested it. But that was an older version. For the most part its working for most people.
The script is so simple, it installs alien, converts the rpm's, installs the deb's, runs the wrapper app, copies the results to the right place. There just isnt a lot of places for it to mess up that I can see.
If you comment out the last line, or delete it
```
sudo rm -fdr /tmp/nsplugwrapper
```
Run the script, then tell me whats in the /tmp/nsplugwrapper directory, maybe we can figure it out.

---

### Post by jusmurph on 2007-05-25
> **Kilz said:**
> [Try this package.]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb")

Still nothing :(

---

### Post by Kilz on 2007-05-25
> **jusmurph said:**
> Still nothing :(

open a terminal, type in firefox, visit site with flash, copy errors in terminal into post here.

---

### Post by jusmurph on 2007-05-26
> **Kilz said:**
> open a terminal, type in firefox, visit site with flash, copy errors in terminal into post here.

I opened the terminal (Applications / Accesories / Terminal)
Typed in firefox
In firefox i navigated to you tube
The video played fine, i just get no sound.
Terminal did not report anything...

(did i do something wrong?)

So i unplugged it from my audidgy2 sound card and plugged into the onboard sound and (under System / Prefrences / themes) set it to auto detect and it worked. So know i got to investigate this hard ware and what all those preferences mean / do.

Thanks for the script though!:D

---

### Post by Pillage Idiot on 2007-05-27
Beautiful, beautiful thing.
Just run this on my amd64 and now have flash, with sound and all.

Now if I can just get my TV out working I will be a happy camper.

---

### Post by Cappy on 2007-05-31
Thanks! I've been using Opera all this time but a game needed firefox and this script did the job in 10 seconds! Thanks a lot =)

---

### Post by EatenByGrues on 2007-05-31
The plugin seems to work pretty well but I'm getting that mouse click thing too. For instance if I go to youtube and click on a video, it starts and plays fine. But if I pause it then try to unpause it won't recognize the click. I have to click out of flash (anywhere on the screen really) and then it accepts it again.

---

### Post by eduardoska on 2007-05-31
> **Aidy said:**
> just do:

sudo ldconfig /usr/lib32

I should mention that the error I was getting prior to performing these steps was:

```
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
```

when attempting to run Firefox with audio'd Flash.

I have the same problem no sound in firefox flash. Used this guide but suddenly one day... no sound in flash! 
after tried this my ouptut of firefox is this:
```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave

```

I had the same problem of ```
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
```

anyone can help??:(

---

### Post by russtifer on 2007-06-02
Thank you so much for this.  I am new to linux and not having flash working was pissing me off a little.  I am continually surprised by the level of support I am getting here.  That I think is the biggest advantage that Linux has.  Thanks again.

---

### Post by EatenByGrues on 2007-06-02
I figured out the issue with the 'clicking'. It's apparently an issue with Beryl, because as soon as I switch my window manager back to Metacity I no longer have the issue.

---

### Post by eks on 2007-06-03
Hallo!

When I first downloaded and ran the script it worked great right out of the box. No problem whatsoever.

But now I was configuring another user for my wife, so she can have her own desktop (mine is always huge mess of icons). I ran the script, it gave no errors and seemed to work, right as before. But it still shows nothing when I run the browser, as if it was not installed. about:plugins doesn't show flash there. And I've realized that mine /home/eks/.mozila/firefox/pluginreg.dat has the following lines at the end:

```

/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so:$
:$
1180807389000:1:3:$
Shockwave Flash 9.0 r31:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

```

While not on hers. I edited the file, but it seems it's generated AFTER you start Firefox (as some kind of log?).

**I supose the plugin is installed for all users, but how to configure a Firefox from another user to use it?**


eks

---

### Post by Kilz on 2007-06-03
> **eks said:**
> Hallo!

When I first downloaded and ran the script it worked great right out of the box. No problem whatsoever.

But now I was configuring another user for my wife, so she can have her own desktop (mine is always huge mess of icons). I ran the script, it gave no errors and seemed to work, right as before. But it still shows nothing when I run the browser, as if it was not installed. about:plugins doesn't show flash there. And I've realized that mine /home/eks/.mozila/firefox/pluginreg.dat has the following lines at the end:

```

/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so:$
:$
1180807389000:1:3:$
Shockwave Flash 9.0 r31:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

```

While not on hers. I edited the file, but it seems it's generated AFTER you start Firefox (as some kind of log?).

**I supose the plugin is installed for all users, but how to configure a Firefox from another user to use it?**


eks

Odds are its a ownership thing try this but edit the user name to your user name. The :users at the end should make it accessible to all users.
```
sudo chown -R YouUseName:users /usr/lib/mozilla/plugins
```

---

### Post by eks on 2007-06-04
> **Kilz said:**
> Odds are its a ownership thing try this but edit the user name to your user name. 
Thanks a lot!!!! :D

The command didn't worked, but it was indeed the ownership of the files. I ended up changing it with a root/nautilus to group:users to all files. (Have yet to read about permissions and ownerships on Linux...:) )


eks

---

### Post by macubo on 2007-06-06
HP Nx6125, turion ml40, ubuntu feisty 64bit, firefox 2.0.0.4, works great! thank you

PS: the terminal quits a little too fast just after downloading flash form adobe. This prevented me from seeing the final output messages. bye

---

### Post by tL0z on 2007-06-06
I've installed the plugin but I can't watch videos on the browser. Can it be a missing codec?

---

### Post by Kilz on 2007-06-06
> **tL0z said:**
> I've installed the plugin but I can't watch videos on the browser. Can it be a missing codec?

Exactly what did you install, and how did you install it?

---

### Post by tL0z on 2007-06-06
I only installed the Nspluginwrapper script, now, and a codec when I tried to open a xvid file, some time ago. Nothing else.

---

### Post by Kilz on 2007-06-06
> **tL0z said:**
> I only installed the Nspluginwrapper script, now, and a codec when I tried to open a xvid file, some time ago. Nothing else.

Exactly what are you trying to open or watch, please provide a link.

---

### Post by tL0z on 2007-06-06
A [WWE video]("http://www.wwe.com/shows/ecw/shows1/ecwonscifi/videos/"). But btw, I tried to watch an Youtube video and it worked.

---

### Post by Kilz on 2007-06-06
> **tL0z said:**
> A [WWE video]("http://www.wwe.com/shows/ecw/shows1/ecwonscifi/videos/"). But btw, I tried to watch an Youtube video and it worked.

The reason that site will not show for you is that it does not use flash. Flash is what you installed with nsplugin wrapper.
You will want to install a streaming media player and plugin. I know mplayer works for that site because mine works. The packages you need are
mplayer
and 
mozilla-mplayer
Then restart the browser.

---

### Post by tL0z on 2007-06-06
I've installed mozilla-mplayer (I had mplayer installed by default with Ubuntu) and it still doesn't work. It appears like this:

[IMG]http://img2.freeimagehosting.net/uploads/79ee7671b9.jpg[/IMG]

---

### Post by jusmurph on 2007-06-06
Is flash ever going to just work in Firefox 64?

---

### Post by Kilz on 2007-06-06
> **jusmurph said:**
> Is flash ever going to just work in Firefox 64?

Yes, just as soon as Adobe releases a 64bit flash plugin for linux.

---

### Post by sanketmedhi on 2007-06-06
> **tL0z said:**
> I've installed mozilla-mplayer (I had mplayer installed by default with Ubuntu) and it still doesn't work. It appears like this:

[IMG]http://img2.freeimagehosting.net/uploads/79ee7671b9.jpg[/IMG]

Try VLC Player instead. VLC has its own set of codecs and does not depend on the xine plugins. Install these packages and all corresponding dependencies...
wxvlc
mozilla-player-vlc

You can also use Totem with its mozilla plugin.
totem-xine
totem-mozilla

Install this package to be able to play all types of videos (except wmv9)...
gstreamer0.8-plugins

---

### Post by tL0z on 2007-06-07
Well, I've clicked with the right mouse button on the video and I clicked on "Open with Media Player". Then, it asked to download some codecs which I accepted.

However, the video plays very slowly and the sound and image aren't synchronised.

I've also download the packages sanketmedhi pointed.

---

### Post by fakie_flip on 2007-06-10
totem-mozilla with totem-xine did not work for me :( i cant play the warsow movement videos here.
[http://www.warsow.net/](http://www.warsow.net/)
has anyone else had trouble or know how to fix the problem?

---

### Post by Kilz on 2007-06-10
> **fakie_flip said:**
> totem-mozilla with totem-xine did not work for me :( i cant play the warsow movement videos here.
[http://www.warsow.net/](http://www.warsow.net/)
has anyone else had trouble or know how to fix the problem?

Firefox 32 and mplayer plugin from my script plays it. Link in my signature.
But to help you in the future. Posting different problems on the 10th sub page is not a good way to get help. Find a post on topic or make one.

---

### Post by Kobalt on 2007-06-10
Kilz, your script is as beautiful as it is simple & efficient, thank you ! :)
By the way (and out of curiosity) : do you know if in it's great kindness Adobe has a time frame for 64bit linux flash plugin ?

---

### Post by Kilz on 2007-06-10
> **Kobalt said:**
> Kilz, your script is as beautiful as it is simple & efficient, thank you ! :)
By the way (and out of curiosity) : do you know if in it's great kindness Adobe has a time frame for 64bit linux flash plugin ?

No they give the ever popular, We will release it as soon as it is finished, answer to that question.

---

### Post by Kobalt on 2007-06-10
Classical answer indeed...

---

### Post by darknightuk on 2007-06-10
any1 got embedded divx through mplayer sucessfully, buffers the clip 100% even thought i have specified otherwise then doesnt play it, i've got it playin on another box with dapper so it's not the clip, any ideas?

---

### Post by BobCFC on 2007-06-11
> **Kilz said:**
> Yes, just as soon as Adobe releases a 64bit flash plugin for linux.


It's the whole open source argument in a nutshell.  We all work together and build a 64bit browser on a 64bit OS and they cant port a plugin ...  yet they expect their format to be the standard for the web.


Thanks Kilz for the script, as soon as I uninstalled gnash it worked like a charm.  It's another reason why Ubuntu is the greatest.

Thanks also to [Gwenole Beauchesne]("http://gwenole.beauchesne.info/projects/nspluginwrapper/") who wrote the actual nspluginwrapper which makes the magic work.  Now I can watch the Google Tech Talks!   :mrgreen:


PS There isn't a 64bit flash for Windows either.

---

### Post by Kobalt on 2007-06-11
> **BobCFC said:**
> PS There isn't a 64bit flash for Windows either.
That kind of cheers me up :)

---

### Post by darknightuk on 2007-06-11
> **BobCFC said:**
> PS There isn't a 64bit flash for Windows either.
but what do think the chances are that this will not take long to appear and when it does it will install 1st time and work!

---

### Post by fakie_flip on 2007-06-11
The nspluginwrapper lets you use 32 bit flash in 64 bit Firefox, but what about Java. I thought I avoided the problem of installing a 32 bit Firefox, but is there no other way of getting Java working?

---

### Post by Kilz on 2007-06-11
> **fakie_flip said:**
> The nspluginwrapper lets you use 32 bit flash in 64 bit Firefox, but what about Java. I thought I avoided the problem of installing a 32 bit Firefox, but is there no other way of getting Java working?

There is no safe way of running java. Someone is bound to recommend the java-gcj-compat-plugin. But this warning from the Ubuntu wiki [Java page]("https://help.ubuntu.com/community/Java") is something everyone needs to see before choosing to do that.


Starting with Ubuntu 6.10 (EdgyEft), you can install the experimental java-gcj-compat-plugin from the universe archive. It is available on all architectures. **Note however, that the plugin currently [COLOR="Red"]runs with no security manager.[/COLOR] **This means that applets you load can do anything a java application that you download and run can do. **Be **very** careful which applets you run.**

So if someone writes an applet that loads rootkits on your computer, reformat your drive, ect. java-gcj-compat-plugin will happily let it.

---

### Post by fakie_flip on 2007-06-11
No thanks. Part of the reasons of having Linux is not to have those security problems that Windows has of malicious software.

---

### Post by fimbulvetr on 2007-06-11
p.s. this script only works on firefox for the user who installed it

If you want it to work for all users on the system, 

<code>
sudo chmod 775 /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
</code>

should do it

---

### Post by emink on 2007-06-12
Excellent work, Kilz.

This script takes care of required new modules/apps that need to be installed, their dependencies. Moreover, it's just a matter of click and click...viola.

I myself tried to figure out all these, but when I found this script is already made, it made my youtube experience  just easier. Great work, Kilz.

I highly recommend this.

- Emin

---

### Post by jusmurph on 2007-06-12
Kilz,

How do we completely remove the effects of this script and your " Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64" Swiftfox script.

I'm just trying to debug my sound issues.

---

### Post by Kilz on 2007-06-12
> **jusmurph said:**
> Kilz,

How do we completely remove the effects of this script and your " Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64" Swiftfox script.

I'm just trying to debug my sound issues.

I dont have a Swiftfox script. Swiftfox is a non free version of Firefox that cant be distributed. 
But the info you want is, firefox32 is a deb. It can be removed in synaptic/apt/adept. This script only places plugins in /usr/lib/mozilla/plugins

But exactly what sound issue do you think the browsers are affecting?

---

### Post by jusmurph on 2007-06-12
Swiftweasel i meant.

I had the problem eduardoska had [earlier in the thread]("http://ubuntuforums.org/showpost.php?p=2756453&postcount=76").

Although i fixed it now, though previously Linux was getting the default soundcard wrong. I assume it was the script for no other reason that it first began in flash videos first and then moved slowly out wards onto all videos.

I doubt it is the script but it was a place to start. For anyone else that loses sound in flash video...

The fix was ([found here]("https://bugs.launchpad.net/ubuntu/+bug/57141")):

$ sudo asoundconf list
(This Lists the Names of available sound cards, Eg:
Intel
CA0106

In the example the first one is integrated on the motherboard, and the second one (an audigy) is the one I use. To set the default sound card to the audigy for example)

$ sudo asoundconf set-default-card CA0106

---

### Post by jonlink on 2007-06-14
Thanks so much for this!  I am in the middle of a massive data recovery project for my parents, and I am switching them over to ubuntu, this made my life a bit easier (now to try and recover all those files ...ugh).

---

### Post by bigtom2 on 2007-06-15
I Tryed It It Worked Great On Fire Fox 2 64 Bit I Have Been Looking For A File Like
This For A Week Thanks So Much Bigtom2.

---

### Post by Alex&amp;Linux on 2007-06-15
Well done, Kilz.
Your contribution to this fourm is much appreciated!

(By the way, it worked)

---

### Post by thaibox on 2007-06-15
wow, after a couple of frustrating days, your solution worked perfectly.  Thank you very much.

---

### Post by Alex&amp;Linux on 2007-06-15
> **jonlink said:**
> Thanks so much for this!  I am in the middle of a massive data recovery project for my parents, and I am switching them over to ubuntu, this made my life a bit easier (now to try and recover all those files ...ugh).

Heh!
Funny, I just finished doing the same for my parents, and thus far it is quite enjoyed.
I found it very interesting to note that while a windows OS was confusing to them, this seems to make sense. mmmm...

---

### Post by ecs_pf5 on 2007-06-16
As they say in many a Chinese forum, "Many thanks and respect to the landlord" :)

Worked a dream here, couple of clicks and done. Thank you very much!

---

### Post by pearlie on 2007-06-16
Thanks much - worked beautifully right out of the box.  \\:D/

---

### Post by Luk0r on 2007-06-17
Script works great, thanks.

I am having one problem though.  It seems that whenever I restart/log out of the computer, it messes up flash and it stops working.  I seem to remember this happening on my last installation of 64bit Ubuntu too (when I did this process manually).  Any ideas?

---

### Post by Kilz on 2007-06-17
> **Luk0r said:**
> Script works great, thanks.

I am having one problem though.  It seems that whenever I restart/log out of the computer, it messes up flash and it stops working.  I seem to remember this happening on my last installation of 64bit Ubuntu too (when I did this process manually).  Any ideas?

Please enter this command, copy/pate the output back here

ls -al /usr/lib/mozilla-firefox/plugins/

Also 

ls -al /usr/lib/mozilla/plugins/

---

### Post by Luk0r on 2007-06-17
> luke@luke-desktop:~$ ls -al /usr/lib/mozilla-firefox/plugins/
total 20
drwxr-xr-x 2 root root  4096 2007-06-17 04:04 .
drwxr-xr-x 5 root root  4096 2007-06-17 02:43 ..
-rw-r--r-- 1 root root 11072 2007-06-01 17:18 libunixprintplugin.so
lrwxrwxrwx 1 root root    42 2007-06-17 02:56 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2007-06-17 02:56 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2007-06-17 02:56 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2007-06-17 02:56 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2007-06-17 02:56 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2007-06-17 02:56 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2007-06-17 02:56 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2007-06-17 02:56 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root    52 2007-06-17 04:04 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

luke@luke-desktop:~$ ls -al /usr/lib/mozilla/plugins/
total 8344
drwxr-xr-x 2 root root     4096 2007-06-17 18:32 .
drwxr-xr-x 3 root root     4096 2007-04-15 12:58 ..
-r--r--r-- 1  500 users     856 2006-12-15 21:51 flashplayer.xpt
-rwxr-xr-x 1  500 users 7040080 2006-12-15 21:51 libflashplayer.so
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
-rwxrwxr-x 1 luke luke    69696 2007-06-17 18:33 npwrapper.libflashplayer.so
lrwxrwxrwx 1 root root       61 2007-06-17 18:32 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so

It all appears to be there, it's probably a problem on the nspluginwrapper side of things, as some sites appear to work and others don't.

---

### Post by Kilz on 2007-06-17
> **Luk0r said:**
> It all appears to be there, it's probably a problem on the nspluginwrapper side of things, as some sites appear to work and others don't.

It looks to all be in order. Next time it messes up , open a tab and type in ```
about:plugins 
```
make sure the the filename in the flash section says npwrapper.libflashplayer.so

---

### Post by toecutter on 2007-06-20
Awesome, totally awesome :) works like a charm, sound on YouTube and everything! Thanks very much :D

---

### Post by sambehera on 2007-06-20
worked really well :D

only problem was it took me about 30 minutes  to figure out how to run a shell script in kde through the gui...

i did eventually manage by running > kdesu konqueror but that didnt work when i restarted in firefox... 

eventually had to run it through konsole... which worked .... but im still aching to know how to make shell scripts run in terminal in kde (gui)... [this is much easier on gnome]

---

### Post by Kilz on 2007-06-20
> **sambehera said:**
> worked really well :D

only problem was it took me about 30 minutes  to figure out how to run a shell script in kde through the gui...

i did eventually manage by running  but that didnt work when i restarted in firefox... 

eventually had to run it through konsole... which worked .... but im still aching to know how to make shell scripts run in terminal in kde... [this is much easier on gnome]

doesnt ./scriptname work?

---

### Post by kuja on 2007-06-20
Well, if you want to do it from Konqueror, I suppose one way you could do it would be select it then press "Ctrl+E", I doubt you'll find that in Kubuntu's Konqueror menus. I swear they have it crippled ... Anyhow, Ctrl + E = execute command, if the menu is there in Kubuntu's Konqueror it'll be "Tools -> Execute Shell Command ..."

---

### Post by anv on 2007-06-23
it worked here too. Yes In Firefox and also in Epiphany and Galeon browser.

---

### Post by tribaal on 2007-06-24
Worked like a charm on my new laptop :)

Thanks a lot :)

- trib'

---

### Post by pholvey on 2007-06-27
You, Sir, are a genius.  Thanks for your help!

P.

---

### Post by remij on 2007-06-29
Oh my :D Thank you so much :D Flash is worky-worky :D

---

### Post by sci-fi guy on 2007-07-01
Perfection

---

### Post by OrangeMediumGreen on 2007-07-06
@Kilz: Great work, thank you! =D>

Do you mind if your script is refered in the "ubuntuusers.de - wiki"?

greetings

---

### Post by Badgerz on 2007-07-08
worked 100% first time. cheers.

---

### Post by Kilz on 2007-07-10
> **OrangeMediumGreen said:**
> @Kilz: Great work, thank you! =D>

Do you mind if your script is refered in the "ubuntuusers.de - wiki"?

greetings

Feel free to post it anyplace that helps other users.  :D

---

### Post by davy cielen on 2007-07-11
Thx, your script worked perfect. 

Flash running at a AMD64 ubuntu with xgl in about 10 sec.

great work :popcorn:

---

### Post by reubano on 2007-07-12
Script isn't working for me. Alien fails to convert the rpm files. I get the following error


```
Use of uninitialized value in die at /usr/share/perl5/Alien/Package/Deb.pm line 487, <GETPERMS> line 14.
Package build failed. Here's the log:
        find nspluginwrapper-0.9.91.4 -type d -exec chmod 755 {} ;
find: nspluginwrapper-0.9.91.4: No such file or directory
        rm -rf nspluginwrapper-0.9.91.4
```

Ubuntu 6.10 - the Edgy Eft
Amd64

---

### Post by Kilz on 2007-07-12
> **reubano said:**
> Script isn't working for me. Alien fails to convert the rpm files. I get the following error


```
Use of uninitialized value in die at /usr/share/perl5/Alien/Package/Deb.pm line 487, <GETPERMS> line 14.
Package build failed. Here's the log:
        find nspluginwrapper-0.9.91.4 -type d -exec chmod 755 {} ;
find: nspluginwrapper-0.9.91.4: No such file or directory
        rm -rf nspluginwrapper-0.9.91.4
```

Ubuntu 6.10 - the Edgy Eft
Amd64

It looks like it isnt seeing the rpm to convert. I'm wondering if the file is downloaded. Download the attached script, it will not clean up after itself. Run it and see if the same error happens. If so look in /tmp/nsplugwrapper to see if the nspluginwrapper-0.9.91.4 file exists.

---

### Post by royg on 2007-07-15
Dude this was an awesome piece of script!! resolved many a headaches !! ;) thanks so much.

cheers


> **Kilz said:**
> I have learned that nspluginwrapper is now stable, at least in Feisty. It works with the 32bit Macromedia Flash plugin that most users need. I dont think the 64bit browser is to the point that I can stop making the Firefox32 script. There are other plugins (java) that dont work for all versions. This install script should make it easier for those running Feisty to install it and Flash.
I placed it at the bottom of my Firefox 32 page for now. [Click here if you want to download it.]("http://home.comcast.net/~ubuntume/nsplugin-wrapper-install-0-1.1.tar.gz")
The script also works with the 64bit builds of [Swiftweasel]("http://sourceforge.net/projects/swiftweasel/"), an optimized build of Firefox.

If you have any errors [please download this file]("http://ubuntuforums.org/attachment.php?attachmentid=37967&stc=1&d=1184233724"). It is the same script, but it will not clean up after itself. This will make troubleshooting easier.

---

### Post by maclif58 on 2007-07-16
many thanks. used you instructions and it worked.
maybe when I'll grow up I'll also understand what was going on.
maccabi

---

### Post by jairp on 2007-07-16
For Nubes, (just like me.lol)

Well, I was having this problem with installing Flash player (youtube) in amd64 bit version of fiesty ubuntu.

Now, EVeryhting is working. Thanks to this post. 

So, just download the script. And, run it. And, wait.

You might have to shut down firefox and restart couple of times to see the flash player in action. Or, also type the following in Terminal:

pkill firefox. and start firefox. GO to youtube.com and click on some videos to see if it is working!

hurrayyyyyyyyY!

---

### Post by Rock_Lee_NuX on 2007-07-18
AAAAAAAAAAAAAAAAAAAAAA!!!!!
YEEEEEEEEEEEEEEEAAAAAAAAAAAAAAAAAAAAAHHHH!!!


@Kilz
Soooooooooo siiiiiiiiiiiiiiiiimpleeeee!!! THANK YOU! THANK YOU! THANK YOU! THANK YOU! THANK YOU! 

Amazing work! I can waaaaaaaaaaaatch youtube again LOL :P

Just download and run the script.
Everything is automatic.
Downloads all the necessary files and voila...
Start Firefox 64bit version and you can browse youtube :D

(if you are on pstn might take a while)

:popcorn::popcorn::popcorn: on the house :guitar:

---

### Post by dn* on 2007-07-18
I'm having some trouble with this latest version of the wrapper. I was using a version from a about a month ago, and apart from the fact that after about half an hour of a firefox session flash would simply stop working, it worked ok. Then I updated with the latest script and things were fine for a day, but now I'm not getting any flash at all, and when firefox is generating pages it is freezing.

Running firefox from the terminal shows that around the time of the temporary freezes, this is coming up:

```
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection

```

any help appreciated.

---

### Post by zaffod on 2007-07-20
Thanks. This worked perfectly for me, except that it hasn't applied to all users on the system. 
Do I have to run the script again for each user?

---

### Post by Kilz on 2007-07-21
> **zaffod said:**
> Thanks. This worked perfectly for me, except that it hasn't applied to all users on the system. 
Do I have to run the script again for each user?

You shouldnt have to. Whats probably happened is that the plugin wrapper is owned by the person its running for. You will have to chown it, and make the group its in "users". An example command is 
sudo chown username:users /usr/lib/mozilla/plugins/flashplayer.xpt
and 
sudo chown username:users /usr/lib/mozilla/plugins/libflashplayer.so

You could also just do the plugin directory
sudo chown -R username:users /usr/lib/mozilla/plugins

You will have to edit the command to make username your username you login with.

---

### Post by zaffod on 2007-07-23
Hmmm. Thanks for your suggestion. 

I did:
chown -R karl.users /usr/lib/firefox/plugins/
chown -R karl.users /usr/lib/firefox/plugins/
chown -R karl.users /usr/lib/mozilla/plugins/

Incidentally, I still have the 32bit version of firefox installed and that loads flash fine now. But the 64bit version still doesn't load flash from other user accounts.... strange. 

Another question I have, will the Nspluginwrapper script changes be undone if I update firefox?

---

### Post by Kilz on 2007-07-23
> **zaffod said:**
> Hmmm. Thanks for your suggestion. 

I did:
chown -R karl.users /usr/lib/firefox/plugins/
chown -R karl.users /usr/lib/firefox/plugins/
chown -R karl.users /usr/lib/mozilla/plugins/

Incidentally, I still have the 32bit version of firefox installed and that loads flash fine now. But the 64bit version still doesn't load flash from other user accounts.... strange. 

Another question I have, will the Nspluginwrapper script changes be undone if I update firefox?

Did you use those exact commands, if so you used a "." where a ":" is used between karl and users, and you did not use sudo.

---

### Post by Myzrael on 2007-07-23
I ran the script but it still isn't working. Using a 64bit FireFox ofcourse and still no flash at all. Same after restarting my PC etc....no idea why it didn't work.

edit that's just me being dumb not using sudo first.............say nothing :P WIll probably work in a few minutes now.

---

### Post by Myzrael on 2007-07-23
Works perfectly. Now I only need to fix some sound issues on my Ubuntu and some other small stuff. Aweseome! Thanks

---

### Post by vinced on 2007-07-24
Kilz,
Great Script. Flash is working great. 
Many Thanks,
Vinced

---

### Post by Das Goat on 2007-07-24
Oh, man, Kilz!

You continue to stun me with your vast skill. After months of trying different stuff, your script "just works".

i want to cry I am so pleased.

---

### Post by AegisTalons on 2007-07-25
When I run the script, it works great. But when I restart/log out, Firefox does not have any flash support anymore. No YouTube or GoogleVideo. Any Ideas?

---

### Post by 7Aaron7 on 2007-07-25
ME TOO!!!
#-o

---

### Post by 7Aaron7 on 2007-07-25
> **Kilz said:**
> Thats because the plugins and everything is probably owned by root. You are going to have to chown the /usr/lib32/firefox32/plugins directory to the users group.

Well.........I tried what you said.  BUT, there was no such file in root.  There was a usr/lib**64**/firefox**64**/plugins., but no 32!!.  remember firefox/flash works fine as root,  but not as another user. 

So, I chown the firefox64 files to a new user group that includes everybody.  didn't work.

The strange this is, before I ran your script on the non user screen, I use to get "need to download flash player" messages on the web page.  Now after running the script , having flash work one time, when I go to a web page, I don't get the "need to download flash player" message any more.  That part of the web page is just blank.

---

### Post by trouble1313 on 2007-07-25
Just a suggestion for those having issues...Clean up after old attempts at getting things working. I had libraries kicking around that I had to delete before the script worked. Once I cleaned out the old junk, it worked fine (seemed to be an issue creating links if the file already existed).

Have to say, this worked darned sweet. Thanks for the script!

-Trouble

---

### Post by Kilz on 2007-07-25
> **7Aaron7 said:**
> Well.........I tried what you said.  BUT, there was no such file in root.  There was a usr/lib**64**/firefox**64**/plugins., but no 32!!.  remember firefox/flash works fine as root,  but not as another user. 

So, I chown the firefox64 files to a new user group that includes everybody.  didn't work.

The strange this is, before I ran your script on the non user screen, I use to get "need to download flash player" messages on the web page.  Now after running the script , having flash work one time, when I go to a web page, I don't get the "need to download flash player" message any more.  That part of the web page is just blank.

Please click on Help, then about Mozilla Firefox. At the bottom of the little window that opens is a section starting with Mozilla/5.0. Please copy that section into a post.

---

### Post by AegisTalons on 2007-07-25
Update: When I reboot my computer and run Firefox, I do have Flash support, but the wierdest thing is happening. If I go to [http://www.pandora.com]("http://www.pandora.com"), for example, I see the player. But I cannot do multiple clicks within the Flash player, I have to click outside of the player and then click where I want. 

So I want to scroll down my stations a little bit at a time, and then click on a station that I like, I would have to click outside of the flash player between each click inside the player. Has anyone else experienced this before? Any fixes?

---

### Post by michael37 on 2007-07-25
Flash works for me like a charm.  Go 64-bit.

---

### Post by zaffod on 2007-07-26
Does updating firefox break the changes this script makes?
ie. will flash still work after an update? Update Manager says there are updates...

---

### Post by Kobalt on 2007-07-26
Yes, you can upgrade Firefox safely. It won't affect nspluginwrapper and flash.

---

### Post by 7Aaron7 on 2007-07-26
thanks for looking, here's the info requested

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)

---

### Post by Kilz on 2007-07-26
> **7Aaron7 said:**
> thanks for looking, here's the info requested

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)

The reason I am asking this.
You have both the [32bit firefox installed]("http://ubuntuforums.org/showpost.php?p=3079976&postcount=991"), and you are attempting to use nspluginwrapper . They conflict, I have not been able to get nspluginwrapper to co exist with the 32bit flash plugin. 
What you are saying is that you get a blank space where flash is present. This is the exact problem I experience when running both. 
What way would you like flash to work, we can then concentrate on it. Do you want nspluginwrapper to work, or firefox32?

---

### Post by 7Aaron7 on 2007-07-27
Kilz, wow, I am honored that I you responded to me.  seriously!! you've done a lot to help me move away from windows (this is my first try at Ubuntu/Linux).  Your script worked great on the root firefox to enable flash player.

Ummm I guess that I would prefer to run firefox 64 + nspluginwrapper than the firefox 32.  I'm assuming that the firefox 64 will run faster.

thanks again in advance for the help.

:guitar: ( I actually do play guitar)

---

### Post by Kilz on 2007-07-27
> **7Aaron7 said:**
> Kilz, wow, I am honored that I you responded to me.  seriously!! you've done a lot to help me move away from windows (this is my first try at Ubuntu/Linux).  Your script worked great on the root firefox to enable flash player.

Ummm I guess that I would prefer to run firefox 64 + nspluginwrapper than the firefox 32.  I'm assuming that the firefox 64 will run faster.

thanks again in advance for the help.

:guitar: ( I actually do play guitar)

Not really, it may be slightly faster, but you may not be able to tell. The code in Firefox is 32bit code, its not optimized for the 64bit processor. The 64bit one in Ubuntu is compiled to make it work better. You will also have problems installing a safe version of java (one doesnt exist).
But lets get started. Please run this command and paste the results into a reply
```
ls -al /usr/lib/mozilla/plugins
```
also
```
ls -al /usr/lib/firefox/plugins
```

---

### Post by 7Aaron7 on 2007-07-28
Dear Kilz,
here's the output. (shelly is my wife, one of the users)

Shelly@foyer:~$ ls -al /usr/lib/mozilla/plugins
total 8344
drwxr-xr-x 2 root  root     4096 2007-06-26 13:17 .
drwxr-xr-x 3 root  root     4096 2007-05-25 00:58 ..
-r--r--r-- 1   500 users     856 2006-12-15 23:51 flashplayer.xpt
-rwxr-xr-x 1   500 users 7040080 2006-12-15 23:51 libflashplayer.so
lrwxrwxrwx 1 root  root       38 2007-05-27 01:33 libjavaplugin_oji.so -> /etc/a
lternatives/libjavaplugin_oji.so
-rw-r--r-- 1 root  root   269216 2007-01-26 02:17 mplayerplug-in-dvx.so
-rw-r--r-- 1 root  root      981 2007-01-26 02:17 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root  root   269408 2007-01-26 02:17 mplayerplug-in-qt.so
-rw-r--r-- 1 root  root      981 2007-01-26 02:17 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root  root   269472 2007-01-26 02:17 mplayerplug-in-rm.so
-rw-r--r-- 1 root  root      981 2007-01-26 02:17 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root  root   270648 2007-01-26 02:17 mplayerplug-in.so
-rw-r--r-- 1 root  root   269760 2007-01-26 02:17 mplayerplug-in-wmp.so
-rw-r--r-- 1 root  root      981 2007-01-26 02:17 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root  root      981 2007-01-26 02:17 mplayerplug-in.xpt
-rwx------ 1 aaron admin   69696 2007-06-26 13:17 npwrapper.libflashplayer.so
lrwxrwxrwx 1 root  root       61 2007-06-26 13:15 npwrapper.so -> ../../../../us
r/lib/nspluginwrapper/x86_64/linux/npwrapper.so
Shelly@foyer:~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 root root       4096 2007-06-26 13:19 .
drwxr-xr-x 5 root all users  4096 2007-06-10 13:06 ..
lrwxrwxrwx 1 root root         54 2007-05-27 01:33 libjavaplugin_oji.so -> /etc/
alternatives/libjavaplugin_oji_mozilla_firefox.so
-rw-r--r-- 1 root root      11072 2007-06-01 19:18 libunixprintplugin.so
lrwxrwxrwx 1 root root         42 2007-05-25 00:58 mplayerplug-in-qt.so -> ../..
/mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root         43 2007-05-25 00:58 mplayerplug-in-qt.xpt -> ../.
./mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root         42 2007-05-25 00:58 mplayerplug-in-rm.so -> ../..
/mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root         43 2007-05-25 00:58 mplayerplug-in-rm.xpt -> ../.                                                              ./mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root         39 2007-05-25 00:58 mplayerplug-in.so -> ../../mo                                                              zilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root         43 2007-05-25 00:58 mplayerplug-in-wmp.so -> ../.                                                              ./mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root         44 2007-05-25 00:58 mplayerplug-in-wmp.xpt -> ../                                                              ../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root         40 2007-05-25 00:58 mplayerplug-in.xpt -> ../../m                                                              ozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root         52 2007-06-26 13:19 npwrapper.libflashplayer.so -                                                              > /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so



thanks a zillion!!

---

### Post by Kilz on 2007-07-28
> **7Aaron7 said:**
> Dear Kilz,
here's the output. (shelly is my wife, one of the users)

Shelly@foyer:~$ ls -al /usr/lib/mozilla/plugins
total 8344
drwxr-xr-x 2 root  root     4096 2007-06-26 13:17 .
drwxr-xr-x 3 root  root     4096 2007-05-25 00:58 ..
-r--r--r-- 1   500 users     856 2006-12-15 23:51 flashplayer.xpt
-rwxr-xr-x 1   500 users 7040080 2006-12-15 23:51 libflashplayer.so
lrwxrwxrwx 1 root  root       38 2007-05-27 01:33 libjavaplugin_oji.so -> /etc/a
lternatives/libjavaplugin_oji.so
-rw-r--r-- 1 root  root   269216 2007-01-26 02:17 mplayerplug-in-dvx.so
-rw-r--r-- 1 root  root      981 2007-01-26 02:17 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root  root   269408 2007-01-26 02:17 mplayerplug-in-qt.so
-rw-r--r-- 1 root  root      981 2007-01-26 02:17 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root  root   269472 2007-01-26 02:17 mplayerplug-in-rm.so
-rw-r--r-- 1 root  root      981 2007-01-26 02:17 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root  root   270648 2007-01-26 02:17 mplayerplug-in.so
-rw-r--r-- 1 root  root   269760 2007-01-26 02:17 mplayerplug-in-wmp.so
-rw-r--r-- 1 root  root      981 2007-01-26 02:17 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root  root      981 2007-01-26 02:17 mplayerplug-in.xpt
-rwx------ 1 aaron admin   69696 2007-06-26 13:17 npwrapper.libflashplayer.so
lrwxrwxrwx 1 root  root       61 2007-06-26 13:15 npwrapper.so -> ../../../../us
r/lib/nspluginwrapper/x86_64/linux/npwrapper.so
Shelly@foyer:~$ ls -al /usr/lib/firefox/plugins
total 20
drwxr-xr-x 2 root root       4096 2007-06-26 13:19 .
drwxr-xr-x 5 root all users  4096 2007-06-10 13:06 ..
lrwxrwxrwx 1 root root         54 2007-05-27 01:33 libjavaplugin_oji.so -> /etc/
alternatives/libjavaplugin_oji_mozilla_firefox.so
-rw-r--r-- 1 root root      11072 2007-06-01 19:18 libunixprintplugin.so
lrwxrwxrwx 1 root root         42 2007-05-25 00:58 mplayerplug-in-qt.so -> ../..
/mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root         43 2007-05-25 00:58 mplayerplug-in-qt.xpt -> ../.
./mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root         42 2007-05-25 00:58 mplayerplug-in-rm.so -> ../..
/mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root         43 2007-05-25 00:58 mplayerplug-in-rm.xpt -> ../.                                                              ./mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root         39 2007-05-25 00:58 mplayerplug-in.so -> ../../mo                                                              zilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root         43 2007-05-25 00:58 mplayerplug-in-wmp.so -> ../.                                                              ./mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root         44 2007-05-25 00:58 mplayerplug-in-wmp.xpt -> ../                                                              ../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root         40 2007-05-25 00:58 mplayerplug-in.xpt -> ../../m                                                              ozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root         52 2007-06-26 13:19 npwrapper.libflashplayer.so -                                                              > /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so



thanks a zillion!!

Try this command in a terminal
```
sudo chown -R aaron:users /usr/lib/mozilla/plugins
```
restart the browser and see if flash works.

---

### Post by 7Aaron7 on 2007-07-29
thanks again!
well, we're halfway there.

I executed the command under Shelly, hit enter, and it seemed to "take".
opened up firefox, no go on the flash.

I did the same on aaron (root).  this time, linux asked for my password, after I entered the password, and flash now works on root user aaron.

So now, on to straightening out Shelly.

Thanks !!

---

### Post by 7Aaron7 on 2007-07-29
BTW, I forgot to mention that under Shelly, it did not ask for a password.

---

### Post by mogu on 2007-07-29
Thanks for the script! It worked great!

---

### Post by Kilz on 2007-07-29
> **7Aaron7 said:**
> BTW, I forgot to mention that under Shelly, it did not ask for a password.

You will not be able to do sudo under shelly. But if she is part of the "users" group everything should work for her.

---

### Post by 7Aaron7 on 2007-07-30
well.........
Shelly is still getting a blank space where flash should be. Want to try the other way?
thanks!

---

### Post by Kilz on 2007-07-30
> **7Aaron7 said:**
> well.........
Shelly is still getting a blank space where flash should be. Want to try the other way?
thanks!

Lets see the ```
ls -al /usr/lib/mozilla/plugins
``` results now please. Also is there anything in her ~/.mozilla/plugins folder if it exists.

---

### Post by 7Aaron7 on 2007-07-31
I don't know how to search for this: ~/.mozilla/plugins

here's the output of the command:

Shelly@foyer:~$ ls -al /usr/lib/mozilla/plugins
total 8344
drwxr-xr-x 2 aaron users    4096 2007-06-26 13:17 .
drwxr-xr-x 3 root  root     4096 2007-05-25 00:58 ..
-r--r--r-- 1 aaron users     856 2006-12-15 23:51 flashplayer.xpt
-rwxr-xr-x 1 aaron users 7040080 2006-12-15 23:51 libflashplayer.so
lrwxrwxrwx 1 aaron users      38 2007-05-27 01:33 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
-rw-r--r-- 1 aaron users  269216 2007-01-26 02:17 mplayerplug-in-dvx.so
-rw-r--r-- 1 aaron users     981 2007-01-26 02:17 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 aaron users  269408 2007-01-26 02:17 mplayerplug-in-qt.so
-rw-r--r-- 1 aaron users     981 2007-01-26 02:17 mplayerplug-in-qt.xpt
-rw-r--r-- 1 aaron users  269472 2007-01-26 02:17 mplayerplug-in-rm.so
-rw-r--r-- 1 aaron users     981 2007-01-26 02:17 mplayerplug-in-rm.xpt
-rw-r--r-- 1 aaron users  270648 2007-01-26 02:17 mplayerplug-in.so
-rw-r--r-- 1 aaron users  269760 2007-01-26 02:17 mplayerplug-in-wmp.so
-rw-r--r-- 1 aaron users     981 2007-01-26 02:17 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 aaron users     981 2007-01-26 02:17 mplayerplug-in.xpt
-rwx------ 1 aaron users   69696 2007-06-26 13:17 npwrapper.libflashplayer.so
lrwxrwxrwx 1 aaron users      61 2007-06-26 13:15 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so
Shelly@foyer:~$


Thanks,
Aaron

---

### Post by Kilz on 2007-07-31
> **7Aaron7 said:**
> I don't know how to search for this: ~/.mozilla/plugins

here's the output of the command:

Shelly@foyer:~$ ls -al /usr/lib/mozilla/plugins
total 8344
drwxr-xr-x 2 aaron users    4096 2007-06-26 13:17 .
drwxr-xr-x 3 root  root     4096 2007-05-25 00:58 ..
-r--r--r-- 1 aaron users     856 2006-12-15 23:51 flashplayer.xpt
-rwxr-xr-x 1 aaron users 7040080 2006-12-15 23:51 libflashplayer.so
lrwxrwxrwx 1 aaron users      38 2007-05-27 01:33 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
-rw-r--r-- 1 aaron users  269216 2007-01-26 02:17 mplayerplug-in-dvx.so
-rw-r--r-- 1 aaron users     981 2007-01-26 02:17 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 aaron users  269408 2007-01-26 02:17 mplayerplug-in-qt.so
-rw-r--r-- 1 aaron users     981 2007-01-26 02:17 mplayerplug-in-qt.xpt
-rw-r--r-- 1 aaron users  269472 2007-01-26 02:17 mplayerplug-in-rm.so
-rw-r--r-- 1 aaron users     981 2007-01-26 02:17 mplayerplug-in-rm.xpt
-rw-r--r-- 1 aaron users  270648 2007-01-26 02:17 mplayerplug-in.so
-rw-r--r-- 1 aaron users  269760 2007-01-26 02:17 mplayerplug-in-wmp.so
-rw-r--r-- 1 aaron users     981 2007-01-26 02:17 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 aaron users     981 2007-01-26 02:17 mplayerplug-in.xpt
-rwx------ 1 aaron users   69696 2007-06-26 13:17 npwrapper.libflashplayer.so
lrwxrwxrwx 1 aaron users      61 2007-06-26 13:15 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so
Shelly@foyer:~$


Thanks,
Aaron

open nautilus, click GO then Location and paste ~/.mozilla/plugins in the address space, hit enter.
One other command that may help
```
sudo chmod 755 /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
```

---

### Post by 7Aaron7 on 2007-07-31
:lolflag:):P=D> \\:D/

well like I said, you de man!!

the search yielded no files, but then I ran the command, and now all is well.

thanks a zillion again.

You know, as much as I appreciate all you did for me, I don't like being dependent on someone else.  can you recommend some books or sites for me to become more self sufficient with linux?

Aaron
:guitar:

---

### Post by Kilz on 2007-07-31
> **7Aaron7 said:**
> :lolflag:):P=D> \\:D/

well like I said, you de man!!

the search yielded no files, but then I ran the command, and now all is well.

thanks a zillion again.

You know, as much as I appreciate all you did for me, I don't like being dependent on someone else.  can you recommend some books or sites for me to become more self sufficient with linux?

Aaron
:guitar:

I use [this site all the time]("http://www.ss64.com/bash/") for information on commands. It tops my linux bookmarks.

---

### Post by Footer on 2007-07-31
Greetings,

Big trouble in river city ... Awhile back, I used the instructions in this thread (alternative 2):
```

     [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)

```
to get flash working in my 64bit Firefox.  I had to run this command every time I restarted Firefox in order to keep flash working:
```

    nspluginwrapper -v -a -i

```
which was annoying but workable.

I came along this thread for installing the nspluginwrapper with the script, gave it a whirl and now no flash, and a broken Firefox!  Launched from command line, I get this:
```

footer@kubuntu64:~/.kde/share/config$ firefox
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:25636): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
*** NSPlugin Viewer  *** ERROR: NPP_Destroy() get args: Message argument mismatch
*** NSPlugin Wrapper *** ERROR: NPP_New() invoke: Message type invalid
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Message type invalid

```
at which point, Firefox freezes and has to be killed from the command line.  Any idea how I can fix it or what went wrong ... ?

Thanks!

---

### Post by Kilz on 2007-07-31
> **Footer said:**
> Greetings,

Big trouble in river city ... Awhile back, I used the instructions in this thread (alternative 2):
```

     [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)

```
to get flash working in my 64bit Firefox.  I had to run this command every time I restarted Firefox in order to keep flash working:
```

    nspluginwrapper -v -a -i

```
which was annoying but workable.

I came along this thread for installing the nspluginwrapper with the script, gave it a whirl and now no flash, and a broken Firefox!  Launched from command line, I get this:
```

footer@kubuntu64:~/.kde/share/config$ firefox
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:25636): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
*** NSPlugin Viewer  *** ERROR: NPP_Destroy() get args: Message argument mismatch
*** NSPlugin Wrapper *** ERROR: NPP_New() invoke: Message type invalid
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Message type invalid

```
at which point, Firefox freezes and has to be killed from the command line.  Any idea how I can fix it or what went wrong ... ?

Thanks!

Not off the top of my head, perhaps there is a conflict in the plugins. Please give me the results of these 3 commands.
```
ls -al /usr/lib/mozilla/plugins
```
```
ls -al /usr/lib/firefox/plugins
```
```
ls -al ~/.mozilla/plugins
```
Secondly, did you remove the nspluginwrapper packages you installed before running my script?

---

### Post by Footer on 2007-07-31
Thanks for the prompt response Kilz!

Here you go:

```

footer@kubuntu64:~$ ls -al /usr/lib/mozilla/plugins
total 7000
drwxr-xr-x 2 footer users    4096 2007-07-31 19:59 .
drwxr-xr-x 3 root    root     4096 2007-02-04 06:12 ..
-r-xr-xr-x 1 footer users   19726 2006-12-15 15:51 flashplayer-installer
-r--r--r-- 1 footer users     856 2007-06-19 19:31 flashplayer.xpt
-rwxr-xr-x 1 footer users 7040036 2007-06-19 19:31 libflashplayer.so
-rwxr-xr-x 1 footer users   69696 2007-07-31 20:04 npwrapper.libflashplayer.so
lrwxrwxrwx 1 root    root       61 2007-07-31 19:59 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so
footer@kubuntu64:~$ ls -al /usr/lib/firefox/plugins
total 96
drwxr-xr-x 2 footer users  4096 2007-07-21 11:09 .
drwxr-xr-x 5 root    root   4096 2007-07-21 11:09 ..
-rw-r--r-- 1 footer users 11072 2007-07-18 07:28 libunixprintplugin.so
-rwx------ 1 footer users 69696 2007-02-04 06:17 npwrapper.libflashplayer.so
footer@kubuntu64:~$ ls -al ~/.mozilla/plugins
total 0
drwxr-xr-x 2 footer footer 6 2007-07-31 18:58 .
drwx------ 4 footer footer 47 2007-01-28 13:03 ..
footer@kubuntu64:~$                                               

```

And no, I did not remove the nspluginwrapper packages prior to running your script.

:confused:

---

### Post by Kilz on 2007-07-31
> **Footer said:**
> Thanks for the prompt response Kilz!

Here you go:

```

footer@kubuntu64:~$ ls -al /usr/lib/mozilla/plugins
total 7000
drwxr-xr-x 2 footer users    4096 2007-07-31 19:59 .
drwxr-xr-x 3 root    root     4096 2007-02-04 06:12 ..
-r-xr-xr-x 1 footer users   19726 2006-12-15 15:51 flashplayer-installer
-r--r--r-- 1 footer users     856 2007-06-19 19:31 flashplayer.xpt
-rwxr-xr-x 1 footer users 7040036 2007-06-19 19:31 libflashplayer.so
-rwxr-xr-x 1 footer users   69696 2007-07-31 20:04 npwrapper.libflashplayer.so
lrwxrwxrwx 1 root    root       61 2007-07-31 19:59 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so
footer@kubuntu64:~$ ls -al /usr/lib/firefox/plugins
total 96
drwxr-xr-x 2 footer users  4096 2007-07-21 11:09 .
drwxr-xr-x 5 root    root   4096 2007-07-21 11:09 ..
-rw-r--r-- 1 footer users 11072 2007-07-18 07:28 libunixprintplugin.so
-rwx------ 1 footer users 69696 2007-02-04 06:17 npwrapper.libflashplayer.so
footer@kubuntu64:~$ ls -al ~/.mozilla/plugins
total 0
drwxr-xr-x 2 footer footer 6 2007-07-31 18:58 .
drwx------ 4 footer footer 47 2007-01-28 13:03 ..
footer@kubuntu64:~$                                               

```

And no, I did not remove the nspluginwrapper packages prior to running your script.

:confused:

You have an old wrapped flash plugin in /usr/lib/firefox/plugins. Lets move it someplace for now.
```
sudo mv /usr/lib/firefox/plugins/npwrapper.libflashplayer.so ~/Desktop 
```
Then try firefox.

---

### Post by Neuge on 2007-08-01
First I'll say, I haven't read all 18 pages of this thread so if this problem has been addressed please say so.

I have a Dell Latitude D630 laptop with an Intel 4965agn wireless card.  Running feisty, to get the wireless driver working with iwlwifi, I had to update to the latest gutsy kernel by temporarily adding the gutsy repositories to the packages list.  Unfortunately this poses two problems (maybe interconnected) when running the nspluginwrapper script.

First, all the ia32* packages and their dependencies in feisty are incompatible with the gutsy kernel.  Second, the update to the gutsy kernel breaks the sound drivers (which work in feisty), something I haven't been able to fix yet.  Obviously some of the 32-bit package dependencies also depend on the sound driver.  But I can't install flash and don't know if it's one problem, the other, or a coupling of both.

If it matters, I also have an Inspiron 640m with the latest feisty kernel for which this script worked perfectly.  Well, not the script but Kilz' own tutorial on the nspluginwrapper install before he made this script.

---

### Post by Kilz on 2007-08-01
> **Neuge said:**
> First I'll say, I haven't read all 18 pages of this thread so if this problem has been addressed please say so.

I have a Dell Latitude D630 laptop with an Intel 4965agn wireless card.  Running feisty, to get the wireless driver working with iwlwifi, I had to update to the latest gutsy kernel by temporarily adding the gutsy repositories to the packages list.  Unfortunately this poses two problems (maybe interconnected) when running the nspluginwrapper script.

First, all the ia32* packages and their dependencies in feisty are incompatible with the gutsy kernel.  Second, the update to the gutsy kernel breaks the sound drivers (which work in feisty), something I haven't been able to fix yet.  Obviously some of the 32-bit package dependencies also depend on the sound driver.  But I can't install flash and don't know if it's one problem, the other, or a coupling of both.

If it matters, I also have an Inspiron 640m with the latest feisty kernel for which this script worked perfectly.  Well, not the script but Kilz' own tutorial on the nspluginwrapper install before he made this script.

Did you run the script and see errors, or is it just sound that is an issue? I have to believe that if you are running some form of hybrid of Fiesty/Gutsy you are going to have lots of issues. This may be one, because there is a nspluginwrapper package in the Gutsy repositories. This script will not work on Gutsy. You may have better luck trying to install that Gutsy nspluginwrapper package.

---

### Post by Neuge on 2007-08-01
> **Kilz said:**
> Did you run the script and see errors, or is it just sound that is an issue? I have to believe that if you are running some form of hybrid of Fiesty/Gutsy you are going to have lots of issues. This may be one, because there is a nspluginwrapper package in the Gutsy repositories. This script will not work on Gutsy. You may have better luck trying to install that Gutsy nspluginwrapper package.Before the errors, there's no way my lappy has installed or is seeing the nspluginwrapper in the gutsy repositories.  I added the gutsy sources temporarily to install the gutsy kernel only (absolutely nothing else was installed), then promptly removed them and restarted.  It was this process that killed the sound drivers (2.6.22-8 kernel if it matters).

As for the errors in the script install.  When the script is first run from the terminal, it obviously runs apt-get to install several ia32* packages.  When I run the script it says something of the sort "nspluginwrapper depends on ia*** but it will not be installed", but it then goes on to try to install the rest of the packages in the script.  It fails for all the ia* package dependencies.  If I add the gutsy repositories back to the sources list only to update the few ia32* package dependencies and try to install them, I get the exact same error.

I probably won't have my lappy back until late this afternoon (uni installing Office on it for me, slowly) so I won't be able to test fixes immediately.

---

### Post by Footer on 2007-08-01
> **Kilz said:**
> You have an old wrapped flash plugin in /usr/lib/firefox/plugins. Lets move it someplace for now.
```
sudo mv /usr/lib/firefox/plugins/npwrapper.libflashplayer.so ~/Desktop 
```
Then try firefox.

WHOOHOO!!!  That did the trick Kilz!  Working perfectly now!  Thanks much for the support and the script.  I'm a happy camper again!!!

:guitar:

---

### Post by Kilz on 2007-08-01
> **Neuge said:**
> Before the errors, there's no way my lappy has installed or is seeing the nspluginwrapper in the gutsy repositories.  I added the gutsy sources temporarily to install the gutsy kernel only (absolutely nothing else was installed), then promptly removed them and restarted.  It was this process that killed the sound drivers (2.6.22-8 kernel if it matters).

As for the errors in the script install.  When the script is first run from the terminal, it obviously runs apt-get to install several ia32* packages.  When I run the script it says something of the sort "nspluginwrapper depends on ia*** but it will not be installed", but it then goes on to try to install the rest of the packages in the script.  It fails for all the ia* package dependencies.  If I add the gutsy repositories back to the sources list only to update the few ia32* package dependencies and try to install them, I get the exact same error.

I probably won't have my lappy back until late this afternoon (uni installing Office on it for me, slowly) so I won't be able to test fixes immediately.

If you cant get nspluginwrapper working, there is always the possibility of installing a 32bit firefox, or variant and 32bit flash. Since browsing inst a number crunching activity, there really is no performance loss a human could tell.

> **Footer said:**
> WHOOHOO!!!  That did the trick Kilz!  Working perfectly now!  Thanks much for the support and the script.  I'm a happy camper again!!!

:guitar: 
Cool, now that we know the file is the bad one we can delete it. If its owned by root this command will do the trick.
sudo rm ~/Desktop/npwrapper.libflashplayer.so

---

### Post by buzz_ on 2007-08-05
For German users:
**[Firefox: Flash unter Ubuntu 7.04 64bit installieren]("http://blitzlight.com/linuxbuzz/?p=4")!**

Worked fine for me!

---

### Post by PILGU on 2007-09-29
thanks Kilz. at last I've got Flash player running in Firefox on my amd64 Feisty fawn. It is Guys like you that help us cling thighter onto UBUNTU.:)

---

