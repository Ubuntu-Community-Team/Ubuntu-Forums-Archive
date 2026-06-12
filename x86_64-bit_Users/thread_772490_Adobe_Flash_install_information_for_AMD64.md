---
title: "Adobe Flash install information for AMD64"
date: 2008-04-28
forum: x86 64-bit Users
---

### Post by Kilz on 2008-04-28
Hi
Take a look below. There are options for everything.

**[SIZE="4"][COLOR="Sienna"]64bit Adobe Flash Alpha and Java Beta[/COLOR][/SIZE]**
Adobe has released a 64bit Adobe Flash 10 plugin. The 64bit Sun java plugin is in beta testing. At this time its possible to run a 64bit browser and plugins for most users.
We need to keep some things in mind before even starting this..
1. Its an Alpha and Beta - as such expect there to be problems and bugs. Expect to have to file bug reports and wait for some time until the code is fixed.
2. Your own tolerance for solving bugs and having things not work . There will be little help and you will be blazing a trail into new things. If you cant stand for something not to work right, and your plugins work now,..... you may want to leave this alone.  There will probably be no work arounds.

 If you experience any bugs make 100% sure to [file a bug report with Adobe for flash.]("http://bugs.adobe.com/flashplayer/")or [Sun for Java]("http://forums.java.net/jive/index.jspa") IMHO if you try this, filling out bug reports is what you should do as a good FOSS user. Its how you help and the software gets better. Dont wait for someone else to do it.

Here is a link to [the release notes ]("http://labs.adobe.com/downloads/flashplayer10.html")which has a download link. [URL="http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install"]Here are the install instructions for Flash. 
[/URL] 
Here are the install scripts 
[64bit Flash Alpha]("http://home.comcast.net/~ubuntume/Get64bitFlash-0.1.tar.gz")*
[ 64bit Sun Java beta]("http://home.comcast.net/~ubuntume/Get64bitJava-0.1.2.tar.gz").*
1. Download either script.
2. Right click on the tar.gz and select "Extract Here"
3. Close **all **browsers.
4. Inside the folder that extracts is a "Get64bitFlash" or "Get64bitJave" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done.  :D

***** There are reports of some things missing on flash sites with the new 64bit plugin *****

[COLOR="Sienna"][SIZE="4"]**Jaunty Jackalope**[/SIZE][/COLOR]
Jaunty is still in development. This is not the place to look for or discuss issues with it yet as the 64bit section of the forums is for release versions.
Important links
1. [The place to file bug reports]("https://launchpad.net/ubuntu/+filebug"). ( do it now, yes **you**, dont wait for someone else to do it)
2. [The development sectio]("http://ubuntuforums.org/forumdisplay.php?f=352")n of the forum. ( the place to look for fast fixes after reporting the bug.

[COLOR="Sienna"][SIZE="4"]**Intrepid Ibex**[/SIZE][/COLOR]
If the following doesnt work
```
sudo apt-get install nspluginwrapper flashplugin-nonfree
```
[COLOR="Red"]**[SIZE="3"]File a [BUG REPORT NOW[/SIZE]**[/COLOR]]("https://launchpad.net/ubuntu/+filebug") Dont wait for someone else to do it.
 Dont :
1. Dont Run any scripts
2. Dont try alternate flash installs.
Both of which can leave files that conflict with the flash plugin.

File a bug report so the developers who dont read the forums can fix the issue.
Then read the How to get help section below for help.

[COLOR="Sienna"][SIZE="4"]**Hardy Heron**[/SIZE][/COLOR]

[SIZE="2"]**Flash 10 script**[/SIZE]
There is now a script to install Flash 10 to Hardy Heron. This script works on Hardy only to my knowledge. [Download file]("http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz")
**[SIZE="2"][COLOR="Sienna"]Instructions[/COLOR][/SIZE]**
1. Download the script.
2. Right click on the tar.gz and select "Extract Here"
3. Close **all **browsers.
4. Inside the folder that extracts is a "GetFlash10" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done.  :D
8. If you select anything but Hardy Heron the script will not install anything.

If flash still does not work 
**[COLOR="Red"]DO Not[/COLOR]** install other scripts below. Run all the commands above again. Other scripts will only make things worse. 
**[COLOR="Red"]DO Not[/COLOR]** try other methods, these may leave files in place that will cause problems. 
Read the How to get help section below before making any posts.


[SIZE="2"]**Flash 9 manual**[/SIZE]
If you upgraded from Gutsy you may need to clean out the previous install. Please do the following one at a time.
```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
```
If you did a clean install the above step is not needed, but cant hurt. If any of the commands say the package/file cant be found dont worry. We want to make sure they are gone, they may not be on your system.
To install flash to Hardy
1. Open a terminal
2. Type
```
sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0.3/plugins/
```

If this helped please consider clicking the thank you icon like this.  [IMG]http://i9.photobucket.com/albums/a74/tghc/thanks.png[/IMG] at the bottom of the post.

Flash should work on Hardy without any scripts or work arounds other than the commands above.
If flash still does not work 
**[COLOR="Red"]DO Not[/COLOR]** install the scripts below. Run all the commands above again. The script will only make things worse. 
**[COLOR="Red"]DO Not[/COLOR]** try other methods, these may leave files in place that will cause problems. 
Read the How to get help section below before making any posts.

[COLOR="Sienna"][SIZE="4"]**Flash 10**[/SIZE][/COLOR]
Adobe has released Flash 10. The plugin is of better quality than Flash 9. I will add this manual install section for those that would like to do it themselves. I would only use the instructions on Hardy, though Gutsy might work.
[Click Here]("http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb") to download [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790")
[Click Here]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz") to get Flash 10
Save the files to your desktop, if you save files to a different location, drag them to your desktop.

First
1. Open a terminal and execute the following commands for removal of old plugins. Some may error out saying they cant find a file, that's ok. We just want to make sure they are removed if they exist.
```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo apt-get purge flashplugin-nonfree
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

Next we install new stuff.

```
cd ~/Desktop
sudo apt-get -y install nspluginwrapper
sudo dpkg -i getlibs-all.deb
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d
```
We install the flash plugin
```
tar -xzvf install_flash_player_10_linux.tar.gz install_flash_player_10_linux
sudo mv -f ~/Desktop/install_flash_player_10_linux/libflashplayer.so /usr/lib/firefox-addons/plugins/
```
We wrap it and link it.
```
sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo ln -s /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
```
Then restart your browser.
If flash does not work 
**[COLOR="Red"]DO Not[/COLOR]** install other scripts. Run all the commands above again. Other scripts will only make things worse. 
**[COLOR="Red"]DO Not[/COLOR]** try other methods, these may leave files in place that will cause problems. 
Read the How to get help section below before making any posts.

**[SIZE="4"][COLOR="Sienna"]Dapper-Gutsy only (Install Script)[/COLOR][/SIZE]**
This script will install the nspluginwrapper, and Flash for your 64bit browser for the **amd64 version of Ubuntu** Dapper, Edgy and Feisty, and Gutsy. It will not work on the i386 or 32bit version. 
It will not install other plugins. There are other plugins, java being one, that nspluginwrapper can not work with. The script has been updated on 8/21/07. It no longer uses alien on Feisty, and it will clean out previous installs. I have also made a script that installs the old flash plugin that seems to work better than the new one. 
[Click here for the script that installs the previous r48 plugin]("http://home.comcast.net/~ubuntume/oldflash-0.1.5-1.tar.gz") **[COLOR="DarkRed"](recommended Dapper-Feisty)[/COLOR]** 
[Click here if you want to download the script for r124 Flash plugin.]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.7.tar.gz")**[COLOR="DarkRed"](recommended for Gutsy)[/COLOR]** 

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
**[SIZE="3"][COLOR="Red"][B]All**[/COLOR] posts asking for help [COLOR="Red"]**must**[/COLOR] have a link to a bug report you filed about the problem on Launchpad.[/SIZE][/B]
First look through the Common Issues section to see if your problem is a common one with a fix. Then read the last 2 pages of this post to see if the issue is being addressed already by someone else.
Second [**file a bug report on Launchpad** ]("https://launchpad.net/ubuntu/+filebug")to let the developers know of the problem. Simply posting problems to the forums does not let the developers know about bugs. Few developers if any read the forums. If they do not know about issues they may never get fixed and the problem may even be in the next Ubuntu version. Add the url of the bug report to your post. 
When you make a post, make in in this thread. Please do not make a separate post. Include the results of the following.
Hardy-Intrepid
```
ls -al /usr/lib/mozilla/plugins/
ls -al /usr/lib/firefox-addons/plugins
```
Dapper-Gutsy
```
ls -al /usr/lib/mozilla/plugins/
ls -al /usr/lib/firefox/plugins
```
Make sure to add the URL of the bug report.
If flash installs but there are other issues running it please read the Common Issues section below.
**[COLOR="Red"]Hardy users should not install the automated script or try other methods.[/COLOR]**
**[COLOR="Red"]Dapper-Gutsy users should not repeatedly install the script or try other methods.[/COLOR]**


**[SIZE="4"][COLOR="Sienna"]Common Issues[/COLOR][/SIZE]**
[SIZE="3"]**Sound**[/SIZE]
First download and double click on [this package]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") to install it.
Gutsy-Hardy - People using Gutsy or Hardy that have sound problems [should read this thread.]("http://ubuntuforums.org/showthread.php?t=655825")

[SIZE="3"]**Grey Box**[/SIZE]
The grey box is not related to 64bit. It happens in all versions of Ubuntu as [this post in a 32bit section proves.]("http://ubuntuforums.org/showthread.php?t=590242") I recommend trying the Flash 10 beta to see if your issues have been addressed by Adobe. Flash is not open source, Adobe is the only one who can fix some errors. Please report your issues to them.
This issue is most likely made worse in 64bit because the plugin is wrapped, there is no known fix for that. The problem most often happens with multiple flash enabled sites open in multiple tabs or windows. 
The simple solution is to only open one at a time.
It has been suggested that creating a config file may help
```
sudo mkdir /etc/adobe
sudo gedit /etc/adobe/mms.cfg
```
Add the line
WindowlessDisable = 1
Then save the file.

Another solution was posted by [jdong here.]("http://ubuntuforums.org/showpost.php?p=6197678&postcount=46"). > **jdong said:**
> Another hint I was given by our resident Mozilla guru, disable Windowsless mode in Flash.

Make an /etc/adobe/mmm.cfg file with the contents
```

WindowlessDisable=true

```


[SIZE="3"]**Sessions**[/SIZE]
Please make sure to start a new browser session if you run into any issues.

[SIZE="3"]**Other Flash Plugins. **[/SIZE]
If after installing the script you cant see flash. Make sure that all attempts at installing other flash plugins (Gnash, swfdec, etc)  have been uninstalled and the files they created have been removed. The remains of past failed attempts are the #1 cause of flash not working. This is because the files conflict with the flash plugin.

[SIZE="3"]**Firefox 3 Beta's **[/SIZE]
This script sets up flash for the 2.0 series of firefox, Firefox 3 beta will also work, but you will need to link the plugins. [This post gives info on the Beta 3.]("http://ubuntuforums.org/showthread.php?t=695674") You may need to edit the commands if your Firefox beta folder is in another place. Forum member kurtpete offers some additional help [in this post.]("http://ubuntuforums.org/showpost.php?p=4359542&postcount=826")


[SIZE="3"]**Unmet Dependencies ia32-libs**[/SIZE]
Users with any of the following errors during install are [directed to this post.]("http://ubuntuforums.org/showpost.php?p=4417385&postcount=914")
The ******* in rthe following error is a wildcard that represents any package name.
```
The following packages have unmet dependencies:
********: Depends: ******** but it is not going to be installed
```
or
[CODE]nspluginwrapper depends on ia32-libs; however:
Package ia32-libs is not installed.
[SIZE="3"]**Flash 10 beta RC3**[/SIZE]
I received a pm about the rc3 of the Flash 10 beta that may help some people.
[QUOTE=bpl07][Flash 10 RC]("http://labs.adobe.com/downloads/flashplayer10.html") was released today.
To get it running on AMD64, I had to use getlibs to install 32-bit libraries of libcurl3, libnss3-1d, and libnspr4-0d.  I'm using nspluginwrapper 1.1.0, but as you pointed out it could probably work for some with the current ubuntu release (0.9.91).[/QUOTE]


[SIZE="3"]**Remove Script**[/SIZE]
[This link]("http://home.comcast.net/~ubuntume/RemoveScript.tar.gz") will download the removal script. Extract the file, then double click on the RemoveScript file and select run in terminal. This script is unnecessary if you are having issues getting the script to work. Its only use is to completely remove the applications from the script. This is counterproductive when people cant get the script to work because it removes clues as to what worked and what didnt.

[COLOR="Sienna"][SIZE="4"]**32bit Firefox, Flash and Java**[/SIZE][/COLOR]
While I do not think its necessary or even a good idea. [The 32bit Firefox, Flash, and Java script]("http://ubuntuforums.org/showthread.php?t=202537") is still available and supported. This would be IMHO a last resort before you go to all the trouble of removing the 64bit version of Ubuntu. It will install the same browser and plugins the 32bit version uses.

[COLOR="Sienna"][SIZE="4"]**Mozilla Downloads**[/SIZE][/COLOR]
This thread is about installing the flash plugin to the Firefox browser installed from the Ubuntu repositories. If at some point in the past you downloaded Firefox from Mozilla and manually installed it. Please understand that you have installed a 32bit version. Flash with the wrapper is not going to work, neither is the information here going to help you. If you want a 32bit Firefox. [Use the script and packages HERE. ]("http://ubuntuforums.org/showthread.php?t=202537")

If any of this info is helpful to you please consider clicking the thank you icon It looks like this.  [[IMG]http://i9.photobucket.com/albums/a74/tghc/thanks2.png[/IMG]]("http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=6018515&securitytoken=1225058685-044fe9fd8d2ae0ec403c56cc116bb82ee31a3956") You can click on this one if you dont see another.

* All scripts should be opened, inspected, and read. You should understand what they do.

---

### Post by doorknob60 on 2008-04-28
Yay, first post in the updated thread :D Anyways, I think this should actually be included in the Ubuntu repositores (the AMD64 ones), because many AMD64 users won't think to look here for flash. There's problably a good reason that it's *not* included, but it would be nice. Got another idea, if it can't get into main or universe or multiverse or any of those, maybe in Medibuntu?

---

### Post by Kilz on 2008-04-28
> **doorknob60 said:**
> Yay, first post in the updated thread :D Anyways, I think this should actually be included in the Ubuntu repositores (the AMD64 ones), because many AMD64 users won't think to look here for flash. There's problably a good reason that it's *not* included, but it would be nice. Got another idea, if it can't get into main or universe or multiverse or any of those, maybe in Medibuntu?

Yes, sometimes the latest and greatest isn't so great. Sometimes stability is important. Hardy should install flash in the repo's (its in the howto), but then so did Gutsy when it came out.

---

### Post by jatiesch on 2008-04-28
hi i installed hardy yesterdat & installed flashplugin-nonfree version 9.0.124.ubuntu2 using synaptic pkg manager...however i am still not able to play flash videos in firefox 3 beta 5...
:confused:

---

### Post by Kilz on 2008-04-28
> **jatiesch said:**
> hi i installed hardy yesterdat & installed flashplugin-nonfree version 9.0.124.ubuntu2 using synaptic pkg manager...however i am still not able to play flash videos in firefox 3 beta 5...
:confused:

when you type ```
about:plugins
``` into the address bar abnd hit enter, do you see a Shockwave flash section?

---

### Post by jatiesch on 2008-04-29
hi thanks for ur responce n sry for late replay...
i get this on *about: plugin* so flash plugin is installed i think...

[I]Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes[/I]

but i have added few screenshots..
javascript is enabled..
cant understand the problem....

---

### Post by dptxp on 2008-04-29
I used
> apt-get install flashplugin-nonfree
in sidux 64 bit, and my flash worked in iceweasel.
I do not remember installing nspluginwrapper.

---

### Post by jatiesch on 2008-04-29
that is i think the same thing...i.e. installing flashplugin-nonfree through synaptic...
then why's the error??

---

### Post by Kilz on 2008-04-29
> **jatiesch said:**
> that is i think the same thing...i.e. installing flashplugin-nonfree through synaptic...
then why's the error??

Did you do a clean install of Hardy, or did you do an upgrade from Gutsy?

---

### Post by jatiesch on 2008-04-29
yup it was a clean installation...no upgrade(my gusty setup was a bit screwed up so did a new hardy installation)

---

### Post by Kilz on 2008-04-29
> **jatiesch said:**
> yup it was a clean installation...no upgrade(my gusty setup was a bit screwed up so did a new hardy installation)

Try running the new hardy setup script. It uses the files in the repos, but it cleans out files left over in failed install attempts.

---

### Post by jatiesch on 2008-04-29
i think i failed to help u understand my problem here..thr were no failed installation attempts...installation was perfect 
or do u mean to repair firefox or whole system again(that would be too much)..??

---

### Post by Kilz on 2008-04-29
> **jatiesch said:**
> i think i failed to help u understand my problem here..thr were no failed installation attempts...installation was perfect 
or do u mean to repair firefox or whole system again(that would be too much)..??

O, there was a perfect install, so everything is working 100% and you dont need any help with flash? 
To me, any install that isnt working is a failed install. The script will remove all the files, even those that may get left behind when uninstalling with synaptic.

---

### Post by |moon| on 2008-04-30
I ran the latest script and this is off of a fresh install with out me fiddling with any settings besides settings with my soundcard.  This isn't an upgrade, I changed from vista to ubuntu and formatted the drive that housed the previous operating system.  Suggestions? Err, and flash isn't working :)

---

### Post by Kilz on 2008-04-30
> **|moon| said:**
> I ran the latest script and this is off of a fresh install with out me fiddling with any settings besides settings with my soundcard.  This isn't an upgrade, I changed from vista to ubuntu and formatted the drive that housed the previous operating system.  Suggestions? Err, and flash isn't working :)

what errors do you get? What other methods of installing flash have you tried. Did you read the entire first post?

---

### Post by |moon| on 2008-04-30
I did read the entire first post, although I've been up for quite a bit now so I might've missed something.

The first install I tried was flashnon-free (I think is the file format) and after I installed that flash video's would come up instead of saying I needed to install the plugin but would not play, every time I would click on a link it would just cycle me back to the first frame so I removed the flashnon-free part and used the script (which would've removed all installed packages) and it went back to nothing at all not even the first scenes opening up, later on the evening I downloaded a flash plugin through mozilla and the flash videos will come up now but not with any sound.  I'm not getting any error messages, it just isn't working when I go to click on a video. *and on a side note I have been up for a really long time and am going to bed, I'll have to check the post later in the afternoon when I wake up, sorry :p*

---

### Post by Kilz on 2008-04-30
> **|moon| said:**
> I did read the entire first post, although I've been up for quite a bit now so I might've missed something.

The first install I tried was flashnon-free (I think is the file format) and after I installed that flash video's would come up instead of saying I needed to install the plugin but would not play, every time I would click on a link it would just cycle me back to the first frame so I removed the flashnon-free part and used the script (which would've removed all installed packages) and it went back to nothing at all not even the first scenes opening up, later on the evening I downloaded a flash plugin through mozilla and the flash videos will come up now but not with any sound.  I'm not getting any error messages, it just isn't working when I go to click on a video. *and on a side note I have been up for a really long time and am going to bed, I'll have to check the post later in the afternoon when I wake up, sorry :p*

Ok, what I am getting from you is you have no sound. This section from the first post may help you


**[SIZE="4"][COLOR="Sienna"]Common Issues[/COLOR][/SIZE]**
[SIZE="3"]**Sound**[/SIZE]
Gutsy-Hardy - People using Gutsy or Hardy that have sound problems [should read this thread.]("http://ubuntuforums.org/showthread.php?t=655825")

---

### Post by |moon| on 2008-04-30
woo! thanks.  Working fine now

---

### Post by jeromio on 2008-04-30
I had flash working in 7.04 with both ff2 and ff3 beta 3. I had originally installed flash using this script - no problems. For the beta install, that was a bit ganked, but I just copied the relevant folders over the the ff3 beta side and that worked.

With Hardy, I now have ff3 beta 5. The adept update process just seemed to grab the latest ff3 beta and removed the old beta and the ff2. 

Flash doesn't work. I re-ran the script - nada.

---

### Post by Thingymebob on 2008-05-01
> **jeromio said:**
> I had flash working in 7.04 with both ff2 and ff3 beta 3. I had originally installed flash using this script - no problems. For the beta install, that was a bit ganked, but I just copied the relevant folders over the the ff3 beta side and that worked.

With Hardy, I now have ff3 beta 5. The adept update process just seemed to grab the latest ff3 beta and removed the old beta and the ff2. 

Flash doesn't work. I re-ran the script - nada.

exactly the same here

---

### Post by Kilz on 2008-05-01
Did either of you upgrade from another version, or was it a clean install? Have you tried other methods, did you read the entire first post?

---

### Post by Thingymebob on 2008-05-01
Sorry, Missed the bit about linking plugins for FF3 beta. All working now. Thanks By the way this was a Dist upgrade from Gutsy

---

### Post by jeromio on 2008-05-01
In the README, it asks for the following:
> jeromio@blirp:/home/downloads/nspluginwrapper install$ ls -al /usr/lib/mozilla/plugins
total 7952
drwxr-xr-x 2 root users    4096 2008-04-30 22:15 .
drwxr-xr-x 4 root root     4096 2008-04-28 21:21 ..
-rwxr-xr-x 1  501 users 8115888 2008-03-24 22:02 libflashplayer.so
lrwxrwxrwx 1 root users      60 2008-04-30 22:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
and
> jeromio@blirp:/home/downloads/nspluginwrapper install$ ls -al /usr/lib/firefox/plugins
total 12
drwxr-xr-x 2 root users 4096 2008-04-30 22:15 .
drwxr-xr-x 4 root root  4096 2008-04-28 21:21 ..
lrwxrwxrwx 1 root users   27 2008-01-13 10:59 npica.so -> /usr/lib/ICAClient/npica.so
lrwxrwxrwx 1 root users   60 2008-04-30 22:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
Which made me think about how I got the ff3b3 flash working. The new ff3b5 has a link to firefox-addons/plugins. But that's empty. SO, I rm'd that and made a link to firefox/plugins. Nothing happened to flash, so I am going to restart ff now.....

---

### Post by jeromio on 2008-05-01
Okay, that worked. SO, the script works in the /usr/lib/mozilla and /usr/lib/firefox folders. This leaves FF3 out since it has an ff3 folder and a ff-addons folder for plugins. Just find all the plugins folders and make sure that they link to /usr/lib/firefox/plugins.

---

### Post by nihilion on 2008-05-01
Hi, I have Kubuntu64/Hardy. I haven't been able to get this script to work at all. 

First I got this:
> mkdir: cannot create directory `/tmp/ffplug': File exists

So then I deleted that File and tried again. Then I got this...

> GetFlash: 11: function: not found

So then I tried installing the regular flash non-free using apt-get at the terminal. It installed and it sort of worked, but then not properly. I mean, I was able to watch youtube videos, but there seemed to be some problem with layers. See the images below:

<see images below>

I then gave up and decided to write a post. I did those command lines you said to do. the results are below:

> nihilion@Seltzertron5500:~$ ls -al /usr/lib/mozilla//plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-05-01 17:02 .
drwxr-xr-x 4 root root 4096 2008-04-30 21:50 ..

and...

> nihilion@Seltzertron5500:~$ ls -al /usr/lib/firefox/plugins/
total 20
drwxr-xr-x 2 root root  4096 2008-05-01 17:02 .
drwxr-xr-x 5 root root  4096 2008-04-29 23:50 ..
-rw-r--r-- 1 root root 11456 2008-04-18 14:54 libunixprintplugin.so


Any ideas?

Thanks for your time.

Nick

---

### Post by bmitchell062003 on 2008-05-01
I tried to install flash following the post. And it is still not working. Any other advice. Sorry if this gets on anyones nervous, Im new.

---

### Post by Kilz on 2008-05-01
I have rewritten the howto post to stop the common error of people running the script, and when that doesn't work, reading and following the directions.

---

### Post by joycey on 2008-05-02
I have installed the flash-nonfree package and it is working, however not all videos are playing.  For instance, I can play videos from YouTube without a problem, but the flash videos at [www.ted.com](www.ted.com) and [www.thedailyshow.com](www.thedailyshow.com) both fail to play.  I suspect this might be a codec issue, in particular I suspect the videos are in mp4 format and that the 32-bit library for this is missing.

Is anyone else experiencing a similar problem or have a solution?

---

### Post by Yellow Pasque on 2008-05-02
joycey, thedailyshow.com is using Flash, not mp4. If you have other sites working (like YouTube), then please do as the sticky recommends and file a bug report on Launchpad or search for existing bugs. It would also be helpful if you launched firefox from the terminal and captured any error messages it outputs when you try to go to a site like thedailyshow.com

---

### Post by joycey on 2008-05-02
Yes, but the "flv" files encompass a variety of encodings, including MPEG-4, which is where I suspect the problem is.  The fact some videos work and others don't is what causes me to suspect a codec problem.

---

### Post by joycey on 2008-05-02
I seem to have resolved the problem.  Installing lib32nss-mdns allows the videos to play.  I can't begin to hypothesize why though.  It is a recommended package for ia32-libs, but not required.

---

### Post by Throne777 on 2008-05-02
I upgraded from Gutsy. I've tried everything recommended in this thread. I've moved the plugins and whatnot. Running FF3.0b5. Flash is just displayed as a grey box for where it should be; the sound plays though.
Any help would be much appreciated :)

---

### Post by Yellow Pasque on 2008-05-02
> **Throne777 said:**
> I upgraded from Gutsy. I've tried everything recommended in this thread. I've moved the plugins and whatnot. Running FF3.0b5. Flash is just displayed as a grey box for where it should be; the sound plays though.
Any help would be much appreciated :)
That sounds like a bug with npviewer.bin Try and run firefox from the terminal and capture any error messages it outputs.

---

### Post by ostsjoe on 2008-05-03
I'm gettin npviewer errors as well after the 8.04 upgrade. It was acting funny before the upgrade, but now it barely works as well. Basically it will start playing a utube video or other flash app, and just stops after about 10 seconds and the window turns grey. Heres the output:

```
(npviewer.bin:23161): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(npviewer.bin:23161): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:23161): Gdk-WARNING **: GdkWindow 0x3c0023d unexpectedly destroyed

(npviewer.bin:23161): Gdk-WARNING **: GdkWindow 0x3c0023c unexpectedly destroyed

(npviewer.bin:23161): Gdk-WARNING **: GdkWindow 0x3c0023b unexpectedly destroyed

(npviewer.bin:23161): Gdk-WARNING **: GdkWindow 0x3c00238 unexpectedly destroyed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 2938 error_code 182 request_code 157 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection reset by peer
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasProperty() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasMethod() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invoke() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_New() invoke: Connection closed
```

I did already try removing and reinstalling flashplugin-nonfree, but it didn't make a difference. I also symlinked up the plugin folders, no change.

---

### Post by NagasakiJones on 2008-05-03
Hi, I've installed "flashplugin-nonfree" but I get no sound. I've been at this all day yesterday trying to fix this. I tried most every proposed fix in the forums but to no avail. I've tried so many things (except installing gnash or swfdec) my memory's a haze.

After installing flashplugin-nonfree with no fix, I followed Common Issues - Sound and installed the ia32-also-oss package, still no fix. Then I followed the thread recommended and tried installing "lib32cap1_1.10-14build1_amd64.deb" but when I do I get a "Failed to install", it says "trying to overwrite '/lib32/libcap.so.1.10', which is also in package ia32-libs". And I already have "libflashsupport(svn20080217)".

I have an AMD64, fresh install on new partition of Hardy, using the default Firefox 3.05b. I have installed all the multimedia codecs and they work no problem, including downloaded flvs. Also what I think may be significant is that I'm using an M-Audio Revolution 5.1 sound card via the digital out/sPDIF. In the Sound Preferences I have "IEC1724 IEC958" selected for all possible options that offer it, as all other options do not play sound. Default Mixer Tracks device is set to "M Audio Revolution-5.1 (Alsa Mixer)" but I've also tried "playback:ALSA PCM on front:0 (IEC1724) via DMA (Pulse Audio Mixer)". 

I'll be extremely grateful for anyone who can help me out here! If any other information's needed, just tell me what to provide. And I'm a newbie here so you can assume I don't know too much - because I don't.

---

### Post by chex313 on 2008-05-03
Upgraded from Gusty to Hardy. Only had Beta 3
installed...so there was nothing to link to as far as Firefox 2 per directions. Here is what I get.

```
dad@dad-desktop:~$ ls -al /usr/lib/mozilla//plugins/
total 6900
drwxr-xr-x 2 dad  users    4096 2008-04-25 22:59 .
drwxr-xr-x 4 root root     4096 2008-04-25 22:56 ..
-rwxr-xr-x 1 dad  users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 dad  users      60 2008-03-11 17:06 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
dad@dad-desktop:~$ ls -al /usr/lib/firefox/plugins/
total 24
drwxr-xr-x 2 dad  users  4096 2008-05-03 16:25 .
drwxr-xr-x 5 root root   4096 2008-05-03 16:25 ..
-rw-r--r-- 1 root root  11456 2008-04-18 14:54 libunixprintplugin.so
lrwxrwxrwx 1 dad  users    60 2008-03-11 17:06 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
dad@dad-desktop:~$ uname -a
```

Can someone give direction on what to do next. Thanks

---

### Post by Kilz on 2008-05-03
> **chex313 said:**
> Upgraded from Gusty to Hardy. Only had Beta 3
installed...so there was nothing to link to as far as Firefox 2 per directions. Here is what I get.

```
dad@dad-desktop:~$ ls -al /usr/lib/mozilla//plugins/
total 6900
drwxr-xr-x 2 dad  users    4096 2008-04-25 22:59 .
drwxr-xr-x 4 root root     4096 2008-04-25 22:56 ..
-rwxr-xr-x 1 dad  users 7040036 2007-06-19 20:31 libflashplayer.so
lrwxrwxrwx 1 dad  users      60 2008-03-11 17:06 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
dad@dad-desktop:~$ ls -al /usr/lib/firefox/plugins/
total 24
drwxr-xr-x 2 dad  users  4096 2008-05-03 16:25 .
drwxr-xr-x 5 root root   4096 2008-05-03 16:25 ..
-rw-r--r-- 1 root root  11456 2008-04-18 14:54 libunixprintplugin.so
lrwxrwxrwx 1 dad  users    60 2008-03-11 17:06 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
dad@dad-desktop:~$ uname -a
```

Can someone give direction on what to do next. Thanks

Read the directions for Hardy and follow them.

---

### Post by chex313 on 2008-05-03
> Read the directions for Hardy and follow them.

So I guess your saying report it as a bug:)

Thought I might have missed something.

---

### Post by Yellow Pasque on 2008-05-03
> So I guess your saying report it as a bug

Yeah, that's what he's saying. Could we troubleshoot your problem here? Probably, but it would take a lot longer and get lost in a sea of posts a lot quicker than if you take the bug up with the developers. It's 2008 and flashplugin-nonfree has been available since the release of Gutsy. It really should be working with a simple 'apt-get install' by now and the best way to ensure this is alerting the developers to the problems.

Personally, I've decided to invest my time in supporting users who want to use OSS4 with Ubuntu, because there are no developers working on that.

As for Kilz, the release of Ubuntu 8.04 has brought a flood of new Hardy64 users to this forum and Kilz does not have time to troubleshoot each individual problem, though I'm sure he would like to.

---

### Post by Kilz on 2008-05-03
> **Temüjin said:**
> Yeah, that's what he's saying. Could we troubleshoot your problem here? Probably, but it would take a lot longer and get lost in a sea of posts a lot quicker than if you take the bug up with the developers. It's 2008 and flashplugin-nonfree has been available since the release of Gutsy. It really should be working with a simple 'apt-get install' by now and the best way to ensure this is alerting the developers to the problems.

Personally, I've decided to invest my time in supporting users who want to use OSS4 with Ubuntu, because there are no developers working on that.

As for Kilz, the release of Ubuntu 8.04 has brought a flood of new Hardy64 users to this forum and Kilz does not have time to troubleshoot each individual problem, though I'm sure he would like to.

Quoted for the pure truth of it.

Flash should install and work on Hardy. We should need no work arounds or scripts. Perhaps with a few dozen bug reports we may actually see if fixed.

---

### Post by Yellow Pasque on 2008-05-03
> **joycey said:**
> I seem to have resolved the problem.  Installing lib32nss-mdns allows the videos to play.  I can't begin to hypothesize why though.  It is a recommended package for ia32-libs, but not required.
Excellent. It appears this package might be needed to view certain Flash content.

Kilz, could you add this package to the Hardy section of your original post?

---

### Post by fatsheep on 2008-05-04
I just upgraded to Hardy Heron and I'm glad to see that 64-bit users can finally install flash easily from the repositories. Today is a good day for Linux. :guitar: :popcorn:

---

### Post by ericartman on 2008-05-04
Thank you for making 64 useable to me. After removing all the variants, gnash and non-free from synaptic among others, I just used the first apt-get noted in line 2 of your post and all went well. This was the only roadblock for me and 64 bit useage thanks for opening up the door.

Cart

---

### Post by chex313 on 2008-05-04
One more question then.

Would a work around be installing 32 bit firefox?

---

### Post by Kilz on 2008-05-04
> **chex313 said:**
> One more question then.

Would a work around be installing 32 bit firefox?

no, this thread is  about making flash work with your 64bit browser.
But [32bit firefox is still avilable]("http://ubuntuforums.org/showthread.php?t=202537") if you need the Sun java plugin.

---

### Post by chex313 on 2008-05-04
Got it working!

I had a 32bit version of firefox from Gutsy...removed it

Also removed Firefox 2xx.

Rebooted.

The reboot alone probably got it working. (This rig runs 24/7 for a DC project).

I get so used to not rebooting for anything...it was the last thing that occurred to me.
EDIT: Worked without a reboot on my second Hardy Rig.
Thanks for the help(and sorry for the noob questions.:))

---

### Post by drs305 on 2008-05-05
Kilz,

I have your script working fine with FF3.05b using your first post Line 2 command above. I can't get swiftweasel to work - should it?

Hardy dist-upgrade, AMD64.

Added:
Just checked the about : plugins and swiftweasel still shows:
Shockwave Flash

    File name: /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

in addition to the one in /usr/lib/swfdec-mozilla/libswfdecmozilla.so

Is this conflicting and how would I remove it if that is the culprit?

---

### Post by Kilz on 2008-05-05
> **drs305 said:**
> Kilz,

I have your script working fine with FF3.05b using your first post Line 2 command above. I can't get swiftweasel to work - should it?

Hardy dist-upgrade, AMD64.

What version of swiftweasel do you have installed? The 64bit version or Swiftweasel32?

---

### Post by drs305 on 2008-05-05
Thanks. I found that I still had the npwrapper link in /usr/lib/nspluginwrapper. I guess I thought it was deleted somewhere along the way. Anyway, I renamed it and I guess that deleted the conflict. So now I'll delete it and should be good to use swiftweasel 64 once again (2.0.0.14).

nspluginwrapper doesn't show installed in synaptic. Can I just delete the entire /usr/lib/nspluginwrapper folder now that I have Hardy running properly? I have FF3b, Swiftweasel64 2.0.0.14 (preference) and FF32 (for company java page) on my machine.

---

### Post by Plasma_NZ on 2008-05-05
Ok, my flash works on all sites except the likes of [www.evilchilli.com](www.evilchilli.com) etc... but im sometimes getting intermittent freeze's in firefox on some flash-videos etc... it grays out the entire firefox and doesnt come right till i goto terminal and kill the nsplugin proccess... any idea's whats causing it.?

---

### Post by Kilz on 2008-05-05
> **drs305 said:**
> Thanks. I found that I still had the npwrapper link in /usr/lib/nspluginwrapper. I guess I thought it was deleted somewhere along the way. Anyway, I renamed it and I guess that deleted the conflict. So now I'll delete it and should be good to use swiftweasel 64 once again (2.0.0.14).

nspluginwrapper doesn't show installed in synaptic. Can I just delete the entire /usr/lib/nspluginwrapper folder now that I have Hardy running properly? I have FF3b, Swiftweasel64 2.0.0.14 (preference) and FF32 (for company java page) on my machine.

Just because you cant find it doenst mean it isnt installed. Nspluginwrapper is needed to run flash on your 64bit browser, I wouldnt delete it.

> **Plasma_NZ said:**
> Ok, my flash works on all sites except the likes of [www.evilchilli.com](www.evilchilli.com) etc... but im sometimes getting intermittent freeze's in firefox on some flash-videos etc... it grays out the entire firefox and doesnt come right till i goto terminal and kill the nsplugin proccess... any idea's whats causing it.?

Off the top of my head, nope.

---

### Post by Shii on 2008-05-06
I followed the instructions in the OP and nothing happened. Firefox is acting like Flash is not installed.

Clarification: It pops up an "install plugin" box then tells me it's already installed and exits.

---

### Post by Yellow Pasque on 2008-05-06
Shii, more information, please (you didn't follow all of the instrustions in the OP). What versions of Ubuntu and Firefox are you running? What output do you get when you start FF from a terminal and go to a site with Flash content? 
Output from these commands?:
```
ls -al /usr/lib/mozilla//plugins/
ls -al /usr/lib/firefox/plugins/
uname -a
```

---

### Post by Shii on 2008-05-06
Oh... I didn't think that mattered because there's nothing exciting there.

> avery@daxyne:~$ ls -al /usr/lib/mozilla//plugins/
total 12
drwxr-xr-x 2 avery users 4096 2008-05-05 23:44 .
drwxr-xr-x 4 root  root  4096 2008-05-05 18:46 ..
lrwxrwxrwx 1 root  root    37 2008-05-05 23:25 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 avery avery   42 2008-05-05 23:44 libflashplayer.so -> /usr/lib/firefox/plugins/libflashplayer.so
lrwxrwxrwx 1 root  root    39 2008-04-12 15:54 nphelix.so -> /opt/real/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 root  root    40 2008-04-12 15:54 nphelix.xpt -> /opt/real/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 avery users   60 2008-04-11 13:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
avery@daxyne:~$ ls -al /usr/lib/firefox/plugins/
total 6912
drwxr-xr-x 2 avery users    4096 2008-05-05 23:25 .
drwxr-xr-x 5 root  root     4096 2008-05-05 18:48 ..
lrwxrwxrwx 1 root  root       37 2008-05-05 23:25 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
-rwxr-xr-x 1 avery users 7040036 2007-06-19 19:31 libflashplayer.so
-rw-r--r-- 1 root  root    11456 2008-04-18 13:54 libunixprintplugin.so
lrwxrwxrwx 1 root  root       39 2008-04-12 15:54 nphelix.so -> /opt/real/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 root  root       40 2008-04-12 15:54 nphelix.xpt -> /opt/real/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 avery users      60 2008-04-11 13:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
avery@daxyne:~$ uname -a
Linux daxyne 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
avery@daxyne:~$ 

It doesn't make any difference whether I move files out of that directory, Firefox still acts like there's no Flash. RealPlayer works though.

---

### Post by Kilz on 2008-05-06
> **Shii said:**
> Oh... I didn't think that mattered because there's nothing exciting there.


It doesn't make any difference whether I move files out of that directory, Firefox still acts like there's no Flash. RealPlayer works though.

It appears you have multiple flash installs that are conflicting

lrwxrwxrwx 1 root root 37 2008-05-05 23:25 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin

Also the flash plugin itself is not from the script because it is in the wrong place. I dont think the wrapper can wrap a symlink. I recommend removing all the flash files and rerunning the script.

---

### Post by Shii on 2008-05-06
I removed everything with "flash" in it and reinstalled nspluginwrapper and flashplugin-nonfree. It works now.

---

### Post by Kilz on 2008-05-06
to slow

---

### Post by ger_macaco on 2008-05-06
> **ostsjoe said:**
> I'm gettin npviewer errors as well after the 8.04 upgrade. It was acting funny before the upgrade, but now it barely works as well. Basically it will start playing a utube video or other flash app, and just stops after about 10 seconds and the window turns grey. Heres the output:

```
(npviewer.bin:23161): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(npviewer.bin:23161): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:23161): Gdk-WARNING **: GdkWindow 0x3c0023d unexpectedly destroyed

(npviewer.bin:23161): Gdk-WARNING **: GdkWindow 0x3c0023c unexpectedly destroyed

(npviewer.bin:23161): Gdk-WARNING **: GdkWindow 0x3c0023b unexpectedly destroyed

(npviewer.bin:23161): Gdk-WARNING **: GdkWindow 0x3c00238 unexpectedly destroyed

(npviewer.bin:23161): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 2938 error_code 182 request_code 157 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection reset by peer
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasProperty() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::HasMethod() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invoke() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_New() invoke: Connection closed
```

I did already try removing and reinstalling flashplugin-nonfree, but it didn't make a difference. I also symlinked up the plugin folders, no change.

> **Throne777 said:**
> I upgraded from Gutsy. I've tried everything recommended in this thread. I've moved the plugins and whatnot. Running FF3.0b5. Flash is just displayed as a grey box for where it should be; the sound plays though.
Any help would be much appreciated :)

Same here, some Flash is rendered as a grey box where the content should be. Generally, these are embedded Flash from some other site, but I'm not sure if it has something to do.

I'm running FF2 on Kubuntu Hardy Heron amd64.

Any ideas? Is it a bug (and someone working on it in launchpad)?

---

### Post by Kevbert on 2008-05-06
Works well with BBC news and Sky Sports videos and Gutsy.  Thanks.

---

### Post by Kilz on 2008-05-06
> **ger_macaco said:**
> Same here, some Flash is rendered as a grey box where the content should be. Generally, these are embedded Flash from some other site, but I'm not sure if it has something to do.

I'm running FF2 on Kubuntu Hardy Heron amd64.

Any ideas? Is it a bug (and someone working on it in launchpad)?

How did you install firefox 2? The odds are that no one will be working on a bug for firefox 2 for hardy. It is in the universe. Bugs are only fixed for critical and security issues.
Since you replied "same here", does that mean you upgraded from Gutsy? Can you list in order all the things you have done, or installed to try and get this to work? What you are describing sounds like conflicting flash plugins.

---

### Post by nihilion on 2008-05-06
I've tried absolutely everything in this post. Nothing works. At best, it just slows down my browsers to a crawl.

---

### Post by nihilion on 2008-05-06
Does this make any sense to anyone???



Setting up ia32-libs (2.2ubuntu10) ...

Setting up nspluginwrapper (0.9.91.5-2ubuntu2) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up lib32nss-mdns (0.10-3ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kilz on 2008-05-06
> **nihilion said:**
> Does this make any sense to anyone???



Setting up ia32-libs (2.2ubuntu10) ...

Setting up nspluginwrapper (0.9.91.5-2ubuntu2) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
**debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable**
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up lib32nss-mdns (0.10-3ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
The bolded part mean you have another package manager open trying to install something. Repeatedly trying to install the same thing over and over again will not magically make it work.
```

sudo apt-get -f
```
May stop that error.
Then reread the Hardy section of the post and follow what it says.

---

### Post by ger_macaco on 2008-05-06
> **Kilz said:**
> How did you install firefox 2? The odds are that no one will be working on a bug for firefox 2 for hardy. It is in the universe. Bugs are only fixed for critical and security issues.

Maybe it's not a bug regarding FF2, but flash plugin itself.

> **Kilz said:**
> Since you replied "same here", does that mean you upgraded from Gutsy? Can you list in order all the things you have done, or installed to try and get this to work? What you are describing sounds like conflicting flash plugins.

Yes, upgraded from Gutsy. Then installed FF2 through adept manager. Afterwards, I did try to reinstall nspluginwrapper and flash plugin several times, without getting any better.

---

### Post by Kilz on 2008-05-06
> **ger_macaco said:**
> Maybe it's not a bug regarding FF2, but flash plugin itself.



Yes, upgraded from Gutsy. Then installed FF2 through adept manager. Afterwards, I did try to reinstall nspluginwrapper and flash plugin several times, without getting any better.

Did you clear out the install from Gutsy?

---

### Post by ger_macaco on 2008-05-06
> **Kilz said:**
> Did you clear out the install from Gutsy?

I think I did. However, I'm not quite sure. How can I check? Why should that have something to do with this issue?

---

### Post by Kilz on 2008-05-07
> **ger_macaco said:**
> I think I did. However, I'm not quite sure. How can I check? Why should that have something to do with this issue?

The first post in this thread gives instructions, the reason its important is because of changes in the packages. You need to remove all the old files.

---

### Post by ger_macaco on 2008-05-07
> **Kilz said:**
> The first post in this thread gives instructions, the reason its important is because of changes in the packages. You need to remove all the old files.

Many thanks! that did it..

---

### Post by Swarms on 2008-05-08
What would it require to do a full cleanup of flashmess? I have juggled between the three options, and now nothing works and I consider it is old files interfering.

---

### Post by Kilz on 2008-05-08
> **Swarms said:**
> What would it require to do a full cleanup of flashmess? I have juggled between the three options, and now nothing works and I consider it is old files interfering.

That could be complicated depending on where the files were installed. The files could be anyplace from 
/usr/lib/mozilla/plugins
/usr/lib/firefox-addons/plugins
/usr/lib/firefox/plugins
./mozilla/plugins
and the 
/usr/lib/nspluginwrapper 
folder should be removed entirely. Then any files you placed in other locations based on the howto's you may have followed. 
Secondly the files in those folders may not be clearly labeled as flash files, but still be flash plugins. This is a major problem some people get into when they dont keep track of what they have installed.

---

### Post by s_spiff on 2008-05-09
Tried the howto for Hardy Heron, but still no flash :(
the results of the commands you asked us to include are as follows :
> 
alok@spiffed:~$ ls -al /usr/lib/mozilla//plugins/
total 1488
drwxr-xr-x 2 root root   4096 2008-05-09 08:47 .
drwxr-xr-x 4 root root   4096 2008-04-22 23:41 ..
lrwxrwxrwx 1 root root     37 2008-05-09 08:47[COLOR=YellowGreen] flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin[/COLOR]
-rw-r--r-- 1 root root 290880 2008-03-18 07:48 mplayerplug-in-dvx.so
-rw-r--r-- 1 root root   1067 2008-03-18 07:48 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root root 290880 2008-03-18 07:48 mplayerplug-in-qt.so
-rw-r--r-- 1 root root   1067 2008-03-18 07:48 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root 290880 2008-03-18 07:48 mplayerplug-in-rm.so
-rw-r--r-- 1 root root   1067 2008-03-18 07:48 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root 290872 2008-03-18 07:48 mplayerplug-in.so
-rw-r--r-- 1 root root 290880 2008-03-18 07:48 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root   1067 2008-03-18 07:48 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root   1067 2008-03-18 07:48 mplayerplug-in.xpt
alok@spiffed:~$ ls -al /usr/lib/firefox/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-05-09 08:47 .
drwxr-xr-x 4 root root 4096 2008-05-03 20:24 ..
lrwxrwxrwx 1 root root   37 2008-05-09 08:47 [COLOR=YellowGreen]flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin[/COLOR]
lrwxrwxrwx 1 root root   43 2008-05-04 01:15 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root   44 2008-05-04 01:15 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 root root   42 2008-05-04 01:15 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root   43 2008-05-04 01:15 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root   42 2008-05-04 01:15 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root   43 2008-05-04 01:15 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root   39 2008-05-04 01:15 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root   43 2008-05-04 01:15 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root   44 2008-05-04 01:15 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root   40 2008-05-04 01:15 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
alok@spiffed:~$ uname -a
Linux spiffed 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux

Now what am i supposed to do?

EDIt : got it, I should have restarted firefox. Please add that to your howto for noobs like me :D

---

### Post by Ronin324 on 2008-05-09
Kilz the latest procedure for installing flash fixed the npviewer.bin from crashing out for me when trying to look at flash pages. Well Done

---

### Post by jhulf on 2008-05-10
> **joycey said:**
> I seem to have resolved the problem.  Installing lib32nss-mdns allows the videos to play.

This solved the problem for me too. I had no troubles with 64bit Gutsy playing Flash - Clips, then after an upgrade (via Synaptic) to 64bit Hardy, some Flashs worked (Youtube), others did'nt ([www.tagesschau.de](www.tagesschau.de)).

**lib32nss-mdns** did the trick :biggrin:. Thanks.

---

### Post by Throne777 on 2008-05-12
Ran Firefox in the terminal and got the following:

```

/home/throne777/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/throne777/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/throne777/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/plugins/libflashplayer.so [/usr/lib/firefox-addons/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x622900: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x622900: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x622900: NP_GetValue
GCJ PLUGIN: thread 0x622900: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x622900: NP_GetValue return
GCJ PLUGIN: thread 0x622900: NP_GetValue
GCJ PLUGIN: thread 0x622900: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622900: NP_GetValue return

```

Thanks for any help.

---

### Post by Kilz on 2008-05-12
> **Throne777 said:**
> Ran Firefox in the terminal and got the following:

Thanks for any help.

If you are still having the grey box after doing the Hardy instructions in the first post, give me the results of
```
ls -al /usr/lib/mozilla/plugins
```
and 
```
ls -al /usr/lib/firefox-addons/plugins
```
and
```
ls -al /usr/lib/firefox/plugins
```

---

### Post by Sef on 2008-05-13
Deleted.  Wrong thread; [right thread]("http://ubuntuforums.org/showthread.php?p=4953981#post4953981").

---

### Post by Throne777 on 2008-05-14
> **Kilz said:**
> If you are still having the grey box after doing the Hardy instructions in the first post, give me the results of
```
ls -al /usr/lib/mozilla/plugins
```
and 
```
ls -al /usr/lib/firefox-addons/plugins
```
and
```
ls -al /usr/lib/firefox/plugins
```

```

throne777@throne777-desktop:~$ ls -al /usr/lib/mozilla/plugins
total 8
drwxr-xr-x 2 root root 4096 2008-05-02 18:19 .
drwxr-xr-x 4 root root 4096 2008-05-02 18:19 ..
lrwxrwxrwx 1 root root   26 2008-05-02 18:19 gxineplugin.so -> ../../gxine/gxineplugin.so
throne777@throne777-desktop:~$ ls -al /usr/lib/firefox-addons/plugins
total 6900
drwxr-xr-x 2 root      root     4096 2008-05-02 17:06 .
drwxr-xr-x 5 root      root     4096 2008-04-24 22:02 ..
lrwxrwxrwx 1 root      root       37 2008-04-24 23:20 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rwxr-xr-x 1 throne777 users 7040036 2007-06-20 01:31 libflashplayer.so
lrwxrwxrwx 1 throne777 users      60 2008-01-31 21:32 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
throne777@throne777-desktop:~$ ls -al /usr/lib/firefox/plugins
total 12
drwxr-xr-x 2 throne777 users 4096 2008-04-24 23:20 .
drwxr-xr-x 4 root      root  4096 2008-04-24 22:02 ..
lrwxrwxrwx 1 root      root    37 2008-04-24 23:20 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 throne777 users   60 2008-01-31 21:32 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

In case it's necessary;

The following was in red highlight:
```

 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

```

The following was in aqua highlight:
```

gxineplugin.so 
```

The following was in neon green highlight:
```

/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

And yeah, I did what the first post told me to do.
Thanks for any help.

---

### Post by Kilz on 2008-05-14
> **Throne777 said:**
> ```

throne777@throne777-desktop:~$ ls -al /usr/lib/mozilla/plugins
total 8
drwxr-xr-x 2 root root 4096 2008-05-02 18:19 .
drwxr-xr-x 4 root root 4096 2008-05-02 18:19 ..
lrwxrwxrwx 1 root root   26 2008-05-02 18:19 gxineplugin.so -> ../../gxine/gxineplugin.so
throne777@throne777-desktop:~$ ls -al /usr/lib/firefox-addons/plugins
total 6900
drwxr-xr-x 2 root      root     4096 2008-05-02 17:06 .
drwxr-xr-x 5 root      root     4096 2008-04-24 22:02 ..
lrwxrwxrwx 1 root      root       37 2008-04-24 23:20 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rwxr-xr-x 1 throne777 users 7040036 2007-06-20 01:31 libflashplayer.so
lrwxrwxrwx 1 throne777 users      60 2008-01-31 21:32 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
throne777@throne777-desktop:~$ ls -al /usr/lib/firefox/plugins
total 12
drwxr-xr-x 2 throne777 users 4096 2008-04-24 23:20 .
drwxr-xr-x 4 root      root  4096 2008-04-24 22:02 ..
lrwxrwxrwx 1 root      root    37 2008-04-24 23:20 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 throne777 users   60 2008-01-31 21:32 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

In case it's necessary;

The following was in red highlight:
```

 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

```

The following was in aqua highlight:
```

gxineplugin.so 
```

The following was in neon green highlight:
```

/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

And yeah, I did what the first post told me to do.
Thanks for any help.

Did you at any time run the install script insted of the Hardy instructions?

---

### Post by Throne777 on 2008-05-15
> **Kilz said:**
> Did you at any time run the install script insted of the Hardy instructions?

I ran the install script on 7.10 before Hardy had been released.

---

### Post by Plasma_NZ on 2008-05-15
> **Plasma_NZ said:**
> Ok, my flash works on all sites except the likes of [www.evilchilli.com](www.evilchilli.com) etc... but im sometimes getting intermittent freeze's in firefox on some flash-videos etc... it grays out the entire firefox and doesnt come right till i goto terminal and kill the nsplugin proccess... any idea's whats causing it.?

Has anyone come across this problem??? Will also mention i run compiz..:confused:

---

### Post by Kilz on 2008-05-15
> **Throne777 said:**
> I ran the install script on 7.10 before Hardy had been released.

```
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
```
Should solve the problem after a restart of the browser. If it doesn't, follow the hardy instructions on the first (both sets of commands).

---

### Post by Plasma_NZ on 2008-05-16
Ok... my flash is utterly useless, tried the clean install etc... Anything that uses flash works for like 10 seconds then - firefox gray's out - and the only way to kill it is via terminal ...

Im running Hardy-Heron 64bit - Running Compiz aswell... it's at the point where ubuntu is pointless as i basically cant browse many sites as most people use flash these days...

What to do..

> physics@physics:~$ ls -al /usr/lib/mozilla//plugins/
total 12
drwxr-xr-x 2 physics users 4096 2008-05-16 17:28 .
drwxr-xr-x 4 root    root  4096 2008-02-22 14:58 ..
lrwxrwxrwx 1 root    root    37 2008-05-16 17:28 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 physics users   39 2008-04-22 15:33 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root    root    60 2008-05-16 17:28 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
physics@physics:~$ ls -al /usr/lib/firefox/plugins/
total 8
drwxr-xr-x 2 physics users 4096 2008-05-16 17:28 .
drwxr-xr-x 4 root    root  4096 2008-03-07 01:41 ..
lrwxrwxrwx 1 root    root    37 2008-05-16 17:28 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 physics users   39 2008-04-22 15:33 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
physics@physics:~$ 


---

### Post by Kilz on 2008-05-16
> **Plasma_NZ said:**
> Ok... my flash is utterly useless, tried the clean install etc... Anything that uses flash works for like 10 seconds then - firefox gray's out - and the only way to kill it is via terminal ...

Im running Hardy-Heron 64bit - Running Compiz aswell... it's at the point where ubuntu is pointless as i basically cant browse many sites as most people use flash these days...

What to do..

Your locations look as they should. But, How many different howto's and methods did you try to get flash working?

---

### Post by Plasma_NZ on 2008-05-16
I have only Done 2, First i was using the script for gusty 7.10 - then i tried your one on here... after purging current install ..

---

### Post by Kilz on 2008-05-16
> **Plasma_NZ said:**
> I have only Done 2, First i was using the script for gusty 7.10 - then i tried your one on here... after purging current install ..

What is the version of nspluginwrapper in synaptic?

---

### Post by Plasma_NZ on 2008-05-17
> **Kilz said:**
> What is the version of nspluginwrapper in synaptic?

0.9.91.5-2ubuntu2

---

### Post by pingpongboss on 2008-05-17
Wow, thank you for the crazy fast update to installing Flash 10 beta!!

appreciate it

---

### Post by Kilz on 2008-05-17
> **Plasma_NZ said:**
> 0.9.91.5-2ubuntu2

At this point everything looks like it should. You may want to file a bug report. You can also try the flash 10 beta to see if it will help. But there are no guarantees.

---

### Post by Plasma_NZ on 2008-05-17
> **Kilz said:**
> At this point everything looks like it should. You may want to file a bug report. You can also try the flash 10 beta to see if it will help. But there are no guarantees.

Yep - i tried beta10 - still the same issue... I always seem to have these kinda problems.. Will file a bug-report shortly.

---

### Post by Throne777 on 2008-05-18
> **Kilz said:**
> ```
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
```
Should solve the problem after a restart of the browser. If it doesn't, follow the hardy instructions on the first (both sets of commands).

Finally started working! Thanks a bunch :)

---

### Post by swimstarguy on 2008-05-18
I could not get this, or any other flash install, to work.

I can't seem to copy and paste what's in the terminal so I don't know exactly what to say but I keep getting messages like this:

"Package flashplugin-nonfree is not installed, so not removed"

"E: Couldn't find package libflash-mozplugin"

E: Couldn't find package libflash0c2

couldn't find package gnash

dpkg: error processing nspluginwrapper (--install):

"Errors were encountered while processing:
 nspluginwrapper
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: no such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so"

And then it says "The plugin and files should now be installed. But we need to se the ownership of the files to you. Please type in yoru login name and hit enter. The terminal will then close and everything will be setup."

I have no idea what I'm doing wrong. I've tried every stupid flashplayer walkthough I've found and so far nothing has worked. It's incredibly frustrating.

I know I'm supposed to delete or uninstall previous install attempts and I thought I did.

I just want freaking flashplayer. 
I'm a n00b and cannot figure this crap out on my own.

I have a Dell Inspiron 1521 with the AMD 64 processor. 
A friend installed Linux for me and I'm not sure if I have the 32 or 64 bit browser. I haven't heard back from him or anything from him in weeks. He went back to school and disappeared on me. 

HELP!

---

### Post by Kilz on 2008-05-19
> **swimstarguy said:**
> I could not get this, or any other flash install, to work.

I can't seem to copy and paste what's in the terminal so I don't know exactly what to say but I keep getting messages like this:

"Package flashplugin-nonfree is not installed, so not removed"

"E: Couldn't find package libflash-mozplugin"

E: Couldn't find package libflash0c2

couldn't find package gnash

dpkg: error processing nspluginwrapper (--install):

"Errors were encountered while processing:
 nspluginwrapper
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: no such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so"

And then it says "The plugin and files should now be installed. But we need to se the ownership of the files to you. Please type in yoru login name and hit enter. The terminal will then close and everything will be setup."

I have no idea what I'm doing wrong. I've tried every stupid flashplayer walkthough I've found and so far nothing has worked. It's incredibly frustrating.

I know I'm supposed to delete or uninstall previous install attempts and I thought I did.

I just want freaking flashplayer. 
I'm a n00b and cannot figure this crap out on my own.

I have a Dell Inspiron 1521 with the AMD 64 processor. 
A friend installed Linux for me and I'm not sure if I have the 32 or 64 bit browser. I haven't heard back from him or anything from him in weeks. He went back to school and disappeared on me. 

HELP!

What version of Ubuntu are you running?

---

### Post by Plasma_NZ on 2008-05-19
to find out if your running a 32bit or 64bit OS... open terminal and type

```
uname -a
```

u should get a result like so

> physics@physics:~$ uname -a
Linux physics 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
physics@physics:~$ 

That shows your using a 64bit system....

To find out which ubuntu your using, in the same terminal type

```
lsb_release -a
```

and you'll get something like this

> physics@physics:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy
physics@physics:~$ 


---

### Post by swimstarguy on 2008-05-19
Thank you Plazma_NZ.

I am using 64 bit version and I'm on 7.10, Gutsy Gibbon.


~Zar4

---

### Post by Kilz on 2008-05-19
> **swimstarguy said:**
> Thank you Plazma.

I am using 64 bit version and I'm on 7.10, Gutsy Gibbon.


~Zar4

Drag the install script to the desktop, close all browsers.
open a terminal, and type in
```
cd ~/Desktop
./GetFlash
```

Do not close the terminal after its done. Start the browser. Go here [http://www.mycokerewards.com](http://www.mycokerewards.com) and see if flash works. If it doesnt, highlight the entire install in the terminal. Right click and choose copy, then open up the text editor and paste the whole thing. Save it as a txt file and attach it to a post here.

---

### Post by Plasma_NZ on 2008-05-19
Ok.. have been running firefox from terminal to check what happens when it crash's.. its yet to crash, but despite that there's still some interesting stuff happening..

```
(npviewer.bin:22118): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:22118): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:22118): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:22477): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

```

---

### Post by swimstarguy on 2008-05-20
> **Kilz said:**
> Drag the install script to the desktop, close all browsers.
open a terminal, and type in
```
cd ~/Desktop
./GetFlash
```

Do not close the terminal after its done. Start the browser. Go here [http://www.mycokerewards.com](http://www.mycokerewards.com) and see if flash works. If it doesnt, highlight the entire install in the terminal. Right click and choose copy, then open up the text editor and paste the whole thing. Save it as a txt file and attach it to a post here.



I tried exactly that and I still cannot get flash to work.
I got this message:

```
david@Patton:~$ cd ~/Desktop
david@Patton:~/Desktop$ ./GetFlash
bash: ./GetFlash: No such file or directory
david@Patton:~/Desktop$ 
```

I have the file from the first post saved and extracted to my desktop. I've tried to run it several times and I have not gotten it to work. What am I missing?


~Zar4

---

### Post by Kilz on 2008-05-20
> **swimstarguy said:**
> I tried exactly that and I still cannot get flash to work.
I got this message:

```
david@Patton:~$ cd ~/Desktop
david@Patton:~/Desktop$ ./GetFlash
bash: ./GetFlash: No such file or directory
david@Patton:~/Desktop$ 
```

I have the file from the first post saved and extracted to my desktop. I've tried to run it several times and I have not gotten it to work. What am I missing?


~Zar4

You need to make sure that the script file, named GetFlash that is inside the folder that extracts is on the desktop.

---

### Post by Kilz on 2008-05-20
> **Plasma_NZ said:**
> Ok.. have been running firefox from terminal to check what happens when it crash's.. its yet to crash, but despite that there's still some interesting stuff happening..



It looks like you are running KDE and it is having problems with the gtk (gnome) controls. I dont see any flash errors.

---

### Post by Plasma_NZ on 2008-05-20
> **Kilz said:**
> It looks like you are running KDE and it is having problems with the gtk (gnome) controls. I dont see any flash errors.

Far as im aware im running gnome with no KDE ... - not entirely sure to be honest.. was a default standard install of hardy heron.. when it boot's a gome window manager loads.. etc..

---

### Post by Kilz on 2008-05-20
> **Plasma_NZ said:**
> Far as im aware im running gnome with no KDE ... - not entirely sure to be honest.. was a default standard install of hardy heron.. when it boot's a gome window manager loads.. etc..

Are you running a theme that is diffrent from the default one? The reason I thought you were running KDE is that its trying to load libartsc.so.0 [part of the kde sound system]("http://packages.ubuntu.com/hardy/libartsc0")

---

### Post by Plasma_NZ on 2008-05-20
> **Kilz said:**
> Are you running a theme that is diffrent from the default one? The reason I thought you were running KDE is that its trying to load libartsc.so.0 [part of the kde sound system]("http://packages.ubuntu.com/hardy/libartsc0")

Indeed i am..

As follows

Theme - Custom

Controls         - Clearlooksclassic
Windows Boarders - Industrial
Icons            - Nerdy Lines

---

### Post by Yellow Pasque on 2008-05-20
> **Plasma_NZ said:**
> Indeed i am..

As follows

Theme - Custom

Controls         - Clearlooksclassic
Windows Boarders - Industrial
Icons            - Nerdy Lines
Those are GNOME themes, and should not affect the sound.
Go to System -> Preferences -> Sound and make sure eveything is set to PulseAudio.
As Kilz said, I'm not sure what aRTS is doing on your system unless you have KDE packages installed. GNOME has traditionally used ESD (Enlightened Sound Daemon) as a sound server/mixer before the advent of PulseAudio.

---

### Post by Plasma_NZ on 2008-05-20
> **Temüjin said:**
> Those are GNOME themes, and should not affect the sound.
Go to System -> Preferences -> Sound and make sure eveything is set to PulseAudio.
As Kilz said, I'm not sure what aRTS is doing on your system unless you have KDE packages installed. GNOME has traditionally used ESD (Enlightened Sound Daemon) as a sound server/mixer before the advent of PulseAudio.

No offence but u obviously havent read my previous posts.. i have sound and flash works.. just every now and then it crash's firefox..

---

### Post by Yellow Pasque on 2008-05-20
Plasma, I have read your posts. The version of libflashsupport that comes with Hardy probably has arts support compiled in and is causing the errors below. You should see if the libraries are installed, and if not:
```
sudo apt-get install libartsc0
```

```
(npviewer.bin:22118): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
```

---

### Post by Plasma_NZ on 2008-05-21
> **Temüjin said:**
> Plasma, I have read your posts. The version of libflashsupport that comes with Hardy probably has arts support compiled in and is causing the errors below. You should see if the libraries are installed, and if not:
```
sudo apt-get install libartsc0
```

```
(npviewer.bin:22118): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
```

Already installed and the latest - the only thing i've installed to change themes is "gnome-art" from synaptic

---

### Post by kaiwondergoo on 2008-05-22
I could not get sound to work or the video to play more the a few seconds after following these steps. After spending a lot of time reading through the other posts I found one that suggested the following:

```
asoundconf set-pulseaudio
```

then **system->preferences->sound** and set everything to **PulseAudio Sound Server** and restart FireFox

It worked for me

--
kwg

8.04 64bit
FireFox 3.0b5

---

### Post by Plasma_NZ on 2008-05-22
my audio works fine... its not my problem, the problem is flash crashes randomly ...

---

### Post by Yellow Pasque on 2008-05-22
> **Plasma_NZ said:**
> my audio works fine... its not my problem, the problem is flash crashes randomly ...
Report it as a bug on Launchpad. This is beyond the scope of these forums.

---

### Post by Plasma_NZ on 2008-05-22
> **Temüjin said:**
> Report it as a bug on Launchpad. This is beyond the scope of these forums.

Already have :) [https://bugs.launchpad.net/ubuntu/+bug/231839](https://bugs.launchpad.net/ubuntu/+bug/231839)

---

### Post by Yellow Pasque on 2008-05-22
> **Plasma_NZ said:**
> Already have :) [https://bugs.launchpad.net/ubuntu/+bug/231839](https://bugs.launchpad.net/ubuntu/+bug/231839)
Good man.

EDIT: Your pizza vendor uses Flash to take online orders? Blasphemy!

---

### Post by Synkboy on 2008-05-23
I STILL cannot get Flash to work in Hardy, I am considering going back to XP, Gutsy was great, upgraded to Hardy and have had NOTHING but trouble!!!

I tried the two command lines for purge the old version and installing the new one, and I get so far in the terminal as to deciding y/n, and when I type Y+Enter I get "Abort", every time!!!

I am at my wits end here!

---

### Post by Kilz on 2008-05-23
> **Synkboy said:**
> I STILL cannot get Flash to work in Hardy, I am considering going back to XP, Gutsy was great, upgraded to Hardy and have had NOTHING but trouble!!!

I tried the two command lines for purge the old version and installing the new one, and I get so far in the terminal as to deciding y/n, and when I type Y+Enter I get "Abort", every time!!!

I am at my wits end here!

Please copy the contents of the terminal with that and paste it here.

---

### Post by pixel :-) on 2008-05-24
when the pluging craches, and your left with a white scare and you whant to avoid to restart firefox, 

*go in tools-->add-ons-->disableflash and then reenable it, reload the page.And it should be working again.I think it should be similar with other browsers.

*killing npviewer.bin doesn't work,it can actually block it for good.

---

### Post by limejuice on 2008-05-24
Hi,

I'm having trouble getting flash to work. What happens is the video starts to play, but then it just freezes. I can see the picture, but no sound. Sound does work on my system and I can play music and non-flash video. I did have to swithc the System->Preferences->Sound from PulseAudio to ALSA to fix a problem. I don't know if that matters for flash.

I did a clean install of hardy x64 bit desktop edition. I installed ubuntu-restricted pacakge which included flash. I haven't installed much else.  I tried to follow the directions at the top of this thread, but it didn't help. I rant he following commands:

sudo apt-get install flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0b5/plugins/

Here is info requested at top of the threads:

ls -al /usr/lib/mozilla//plugins/; 

lrwxrwxrwx 1 root root   37 2008-05-01 10:43 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

ls -al /usr/lib/firefox/plugins/; 
lrwxrwxrwx 1 root root   37 2008-05-01 10:43 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin

uname -a
Linux jasper 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux


That flashplugin-alternative.so looks suspicious? Could that be the problem?  Thanks for any help.  Other than this petulant flash plugin, everything else I've tried works beautifully under Ubuntu 8.04.

Limejuice

---

### Post by Kilz on 2008-05-24
> **limejuice said:**
> Hi,

I'm having trouble getting flash to work. What happens is the video starts to play, but then it just freezes. I can see the picture, but no sound. Sound does work on my system and I can play music and non-flash video. I did have to swithc the System->Preferences->Sound from PulseAudio to ALSA to fix a problem. I don't know if that matters for flash.

I did a clean install of hardy x64 bit desktop edition. I installed ubuntu-restricted pacakge which included flash. I haven't installed much else.  I tried to follow the directions at the top of this thread, but it didn't help. I rant he following commands:

sudo apt-get install flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0b5/plugins/

Here is info requested at top of the threads:

ls -al /usr/lib/mozilla//plugins/; 

lrwxrwxrwx 1 root root   37 2008-05-01 10:43 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

ls -al /usr/lib/firefox/plugins/; 
lrwxrwxrwx 1 root root   37 2008-05-01 10:43 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin

uname -a
Linux jasper 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux


That flashplugin-alternative.so looks suspicious? Could that be the problem?  Thanks for any help.  Other than this petulant flash plugin, everything else I've tried works beautifully under Ubuntu 8.04.

Limejuice

The plugin is installed. That you can see a part of the flash video proves it is installed. Please read the Hardy section in the first post for instructions on what to do if it still does not work for you.

---

### Post by Not Sure on 2008-05-24
Thanks Kilz,
I have 64-bit Ubuntu installed. I just executed the sudo commands and now my x86_64 Firefox has Flash.  It works fast too!  I have one question:  Is this 64-bit flash or is this 32-bit flash running on a 64-bit web browser?

                            :popcorn:

---

### Post by Yellow Pasque on 2008-05-25
> **Not Sure said:**
> Is this 64-bit flash or is this 32-bit flash running on a 64-bit web browser?
Unfortunately, there is no native 64-bit Flash. It works with the magic of a program called nspluginwrapper. If you want 64-bit Flash, I suggest taking the time to send Adobe feedback. Adobe has stated that they will consider a native 64-bit version of Flash with enough "customer demand". Whether this is true or an empty corporate promise, I don't know. I would like to believe it's true, so I made my demand known, like so: [http://ubuntuforums.org/showpost.php?p=5031885&postcount=6](http://ubuntuforums.org/showpost.php?p=5031885&postcount=6)

Historical side note: Back in the "old days", we had to compile the nspluginwrapper program ourselves and install Flash manually from the Adobe website (the original reason Kilz scripted the process). Then, nspluginwrapper became available in the repo (though that version was sometimes buggy). Finally, the flashplugin-nonfree package was released with Gutsy, but we still often needed a hack/workaround. 
The current Hardy install is really nice, but obviously still isn't perfect. We can make it even better by reporting bugs on Launchpad, especially bugs that occur after Flash is properly installed.

Other historical side note: We often had to walk two miles to school, in the snow (uphill both ways, with or without shoes).

---

### Post by Kilz on 2008-05-25
> **Temüjin said:**
> 
Other historical side note: We often had to walk two miles to school, in the snow (uphill both ways, with or without shoes).

Only 2 miles for you? I had to walk 4 miles. :D

---

### Post by Not Sure on 2008-05-25
Thanks Temujin,  I went to the Adobe website and posted my two cents worth. I hope Adobe realizes that for every person who posts "feedback", there are thousands who feel the same way but do not take the time to post anything.  I'm happy that I have Flash now on my 64-bit Hardy.  Time for Popcorn.          
                         :popcorn:

---

### Post by Yellow Pasque on 2008-05-26
Thank you for telling Adobe we need native 64-bit. It's been 4 years since the introduction of the AMD64 architecture/CPU's and that's a long time in the tech world. The hardware is ready and capable, but the industry has been slow to adopt. I understand that Microsoft wants to sell upgrades to users with 32-bit CPU's. However, there should be more pressure on system vendors to offer the 64-bit version as the standard.

I just checked their websites, and Dell and Gateway don't even offer the 64-bit version of Windows Vista/XP to home users **across their entire product lines**! (At least HP does).

---

### Post by DarthAndy on 2008-05-27
I was having problems with this after following the advice but tracked it down to a missing nspluginwrapper folder under /usr/lib. Couldn't find it anywhere. Reinstalled via synaptic and it now works a treat.

---

### Post by dr_nailz on 2008-05-28
Followed instructions for Hardy (including the 'cleaning up' section) up to:

```
$ sudo apt-get install flashplugin-nonfree
...
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
...
Download done.
Flash Plugin installed.
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The same thing happens if I run:
```
$ sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/firefox-addons/plugins/libflashplayer.so
```

I do not have any of the following installed: gnash, libflash, swfdec.

Installed lib32nss-mdns version: 0.10-3ubuntu2

Any ideas?

---

### Post by Kilz on 2008-05-28
> **dr_nailz said:**
> Followed instructions for Hardy (including the 'cleaning up' section) up to:

```
$ sudo apt-get install flashplugin-nonfree
...
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
...
Download done.
Flash Plugin installed.
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The same thing happens if I run:
```
$ sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/firefox-addons/plugins/libflashplayer.so
```

I do not have any of the following installed: gnash, libflash, swfdec.

Installed lib32nss-mdns version: 0.10-3ubuntu2

Any ideas?

it looks like nspluginwrapper isnt being installed. It should be because it is a required package.

---

### Post by Yellow Pasque on 2008-05-28
dr_nailz, make sure /usr/bin/nspluginwrapper is a symbolic link to /usr/lib/nspluginwrapper/x86_64/linux/npconfig

If not, create it with:
```
cd /usr/bin
sudo rm nspluginwrapper
sudo ln -s /usr/lib/nspluginwrapper/x86_64/linux/npconfig ./nspluginwrapper
```

```
dan@harvest:/usr/lib/nspluginwrapper/x86_64/linux$ ls
npconfig  npwrapper.so
dan@harvest:/usr/lib/nspluginwrapper/x86_64/linux$ cd /usr/bin
dan@harvest:/usr/bin$ ls -la nspluginwrapper 
lrwxrwxrwx 1 root root 44 2008-04-24 13:39 nspluginwrapper -> ../lib/nspluginwrapper/x86_64/linux/npconfig
```

---

### Post by balayyoub on 2008-05-28
thank you very much
it worked for a couple of minutes for me then it stopped again
I really to work this problem
Ubuntu 7.10 Firefox 2 64-bit

---

### Post by Guevara the Pirate on 2008-05-28
> **dr_nailz said:**
> Followed instructions for Hardy (including the 'cleaning up' section) up to:

```
$ sudo apt-get install flashplugin-nonfree
...
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
...
Download done.
Flash Plugin installed.
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The same thing happens if I run:
```
$ sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/firefox-addons/plugins/libflashplayer.so
```

I do not have any of the following installed: gnash, libflash, swfdec.

Installed lib32nss-mdns version: 0.10-3ubuntu2

Any ideas?
Hey dr_nailz,

I was having a similar error as you were. The only difference between your error and mine is that I wasn't getting this line: "*** NSPlugin Viewer *** preloader not found". I too was following the Hardy portion of the guide, including the uninstall/purge at the beginning to no avail. I think however I may have found a workaround on launchpad. 

According to this page: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/180854]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/180854") the Hardy version of ia32-libs, version 2.2, doesn't cooperate well with flash and ends up not letting it work. As a result, a lot of people there have rolled back to the gutsy version of ia32-libs, version 2.1. I did this as well. I've only had it installed for half an hour but so far youtube, and the mycokerewards page that kilz suggested earlier in the thread are working without a problem. I got the 2.1 package from here: 
[http://us.archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.1ubuntu3_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.1ubuntu3_amd64.deb"). 

Hope this helps. Good luck!

---

### Post by dr_nailz on 2008-05-29
> **Kilz said:**
> it looks like nspluginwrapper isnt being installed. It should be because it is a required package.

I should have mentioned that it is installed (hence why I can run the command).  Version: 0.9.91.5-2ubuntu2.  I've tried reinstalling it, and I haven't tried installing it using anything but apt-get and adept.

> **Temüjin said:**
> dr_nailz, make sure /usr/bin/nspluginwrapper is a symbolic link to /usr/lib/nspluginwrapper/x86_64/linux/npconfig

Thanks, it is:
```
$ ls -l /usr/bin/nspluginwrapper
lrwxrwxrwx 1 root root 44 2008-05-29 00:08 /usr/bin/nspluginwrapper -> ../lib/nspluginwrapper/x86_64/linux/npconfig
```

> **Guevara the Pirate said:**
> Hey dr_nailz,

I was having a similar error as you were. The only difference between your error and mine is that I wasn't getting this line: "*** NSPlugin Viewer *** preloader not found". I too was following the Hardy portion of the guide, including the uninstall/purge at the beginning to no avail. I think however I may have found a workaround on launchpad. 

According to this page: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/180854]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/180854") the Hardy version of ia32-libs, version 2.2, doesn't cooperate well with flash and ends up not letting it work. As a result, a lot of people there have rolled back to the gutsy version of ia32-libs, version 2.1. I did this as well. I've only had it installed for half an hour but so far youtube, and the mycokerewards page that kilz suggested earlier in the thread are working without a problem. I got the 2.1 package from here: 
[http://us.archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.1ubuntu3_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.1ubuntu3_amd64.deb"). 

Hope this helps. Good luck!

Thanks, I downgraded to 2.1ubuntu3 and followed the steps from the start, but I run into the same issue installing flashplugin-nonfree (or when running `nspluginwrapper -i` if I try it manually).

I saw another poster mention the **linux32** package, although they were running Debian.  Should I have this package installed?  It isn't, and if I try it wants to remove all kinds of core packages on me.

---

### Post by balayyoub on 2008-05-29
> **balayyoub said:**
> thank you very much
it worked for a couple of minutes for me then it stopped again
I really to work this problem
Ubuntu 7.10 Firefox 2 64-bit


I just downloaded the remove script and uninstalled the flash plugin because it caused me some problems like the Firefox takes for ever to open a page that contain flash media.
after this is not working and the java plugin I think I will leave Ubuntu and go for Fedora or OpenSolaris.

---

### Post by stephenb on 2008-05-29
balayyoub, I can understand your frustration. It really is pathetic that flash and java for 64 bit are a recurring problem. It's also a pain that upgrades send you backwards.

I had flash (not java) working in Feisty. But now in Hardy, after trying all recommendations, all I get is this:

Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

The only thing that works for me now is gnash. But this really hogs resources and for some things does not work.

It's my only choice for the moment.

---

### Post by Kilz on 2008-05-29
> **stephenb said:**
> balayyoub, I can understand your frustration. It really is pathetic that flash and java for 64 bit are a recurring problem. It's also a pain that upgrades send you backwards.

I had flash (not java) working in Feisty. But now in Hardy, after trying all recommendations, all I get is this:

Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

The only thing that works for me now is gnash. But this really hogs resources and for some things does not work.

It's my only choice for the moment.

Is nspluginwrapper installed?

---

### Post by dr_nailz on 2008-05-29
> **Kilz said:**
> Is nspluginwrapper installed?

It looks like this:
```
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
```
is output from nspluginwrapper.  Specifically, after a non-ok status is returned from *detect_plugin_viewer* in nspluginwrapper's *npw-config.c*.

So it should be installed (for stephenb, as for me).

I tried quickly to compile nspluginwrapper from source but ran into some compile errors (missing libs?) so gave up.  No doubt this will later come back to bite me =)

Now, I don't really know what I'm doing here, but:
```
$ locate npviewer
/usr/lib/nspluginwrapper/i386/linux/npviewer
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin
/usr/lib/nspluginwrapper/noarch/npviewer
```
should I be seeing an npviewer for x86_64 there?

---

### Post by Kilz on 2008-05-29
> **dr_nailz said:**
> It looks like this:
```
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
```
is output from nspluginwrapper.  Specifically, after a non-ok status is returned from *detect_plugin_viewer* in nspluginwrapper's *npw-config.c*.

So it should be installed (for stephenb, as for me).

I tried quickly to compile nspluginwrapper from source but ran into some compile errors (missing libs?) so gave up.  No doubt this will later come back to bite me =)

Now, I don't really know what I'm doing here, but:
```
$ locate npviewer
/usr/lib/nspluginwrapper/i386/linux/npviewer
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin
/usr/lib/nspluginwrapper/noarch/npviewer
```
should I be seeing an npviewer for x86_64 there?

No , there is no npviewer for x86_64 on my system, and it works perfectly.
Lets start from scratch, and use a different nspluginwrapper package.
```
sudo apt-get purge nspluginwrapper
sudo rm -rfd /usr/lib/nspluginwrapper
```
[Then download this package]("http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6_amd64.deb") and install it.
I notice that you are trying to wrap a plugin in /usr/lib/flashplugin-nonfree, that location does not exist on my install. Are you sure its there?
You might want to use these commands.
```
sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
```

---

### Post by stephenb on 2008-05-29
Thanks for the file Kilz. 

After installing the package and running nspluginwrapper, I got this message:

sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
nspluginwrapper: /usr/lib/firefox-addons/plugins/libflashplayer.so is not a valid NPAPI plugin

---

### Post by dr_nailz on 2008-05-29
> **Kilz said:**
> Lets start from scratch, and use a different nspluginwrapper package.
```
sudo apt-get purge nspluginwrapper
sudo rm -rfd /usr/lib/nspluginwrapper
```
[Then download this package]("http://home.comcast.net/~ubuntume/nspluginwrapper_0.9.91.6_amd64.deb") and install it.

The same result unfortunately, both when installing flashplugin-nonfree and when running nspluginwrapper manually.

> **Kilz said:**
> I notice that you are trying to wrap a plugin in /usr/lib/flashplugin-nonfree, that location does not exist on my install. Are you sure its there?

Yes it looks like flashplugin-nonfree puts it there:
```
$ ls -l /usr/lib/flashplugin-nonfree/
total 7940
-rw-r--r-- 1 root root 8115888 2008-05-30 08:34 libflashplayer.so
```

> **Kilz said:**
> You might want to use these commands.
```
sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
```

```
$ sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/firefox-addons/plugins/libflashplayer.so
```

> **stephenb said:**
> After installing the package and running nspluginwrapper, I got this message:

sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
nspluginwrapper: /usr/lib/firefox-addons/plugins/libflashplayer.so is not a valid NPAPI plugin

That's the message it gives when the file doesn't exist.  If you will be running nspluginwrapper manually, make sure you've extracted libflashplayer.so to the right place (it should exist at /usr/lib/firefox-addons/plugins/libflashplayer.so).

---

### Post by stephenb on 2008-05-29
OK, when I install the flashplugin with apt-get it puts libflashplayer.so here: /usr/lib/flashplugin-nonfree/libflashplayer.so

So I copied that here: /usr/lib/firefox-addons/plugins/libflashplayer.so

Then when I run nspluginwrapper, it goes back to the same error.

sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
nspluginwrapper: no appropriate viewer found for /usr/lib/firefox-addons/plugins/libflashplayer.so

---

### Post by Kilz on 2008-05-29
Since Flash and the nspluginwrapper are installed perhaps it is a bug that needs reporting.

[Here is a link to Launchpad so you both can report it.]("https://launchpad.net/ubuntu/+filebug")

---

### Post by stephenb on 2008-05-30
Yep, good idea. Here it is:

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/235946](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/235946)

Of course, this is not a new bug. People were getting it in Gutsy for some reason, and maybe even before that for all I know. I can't understand why it keeps cropping up after all this time.

---

### Post by ubuntu-freak on 2008-05-30
I came up with this method for installing Flash v10 beta today, after switching to Ubuntu 64-bit. Kilz, you may find this command-string useful, due to the changes introduced in Hardy. It worked like a charm for me and that's why I'm sharing this method with you and others. Even installing Flash 9 with "sudo apt-get..." afterwards (as a test) didn't cause any issues, it just replaced all the manually created files.

Install the Flash plugin manually by downloading the tar archive of [Adobe Flash v10 beta](http://labs.adobe.com/downloads/flashplayer10.html). Simply open the tar archive, then find the file named "libflashplayer.so and place it on your desktop. Next, execute this command in the terminal: (if you have already purged Flash, start copying the command from "sudo mkdir", or from "sudo cp")

**sudo apt-get purge flashplugin-nonfree && sudo mkdir  /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so && sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so && sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so**

You may now restart Firefox and use the plugin.
 
Nathan

---

### Post by pixel :-) on 2008-05-30
On my system, flash olmost never blocks(white scare).

However,if i use flashblock, it's something like90% of the time,it gets blocked when i decide to unblock it.

I did a system backup and ktorrent was running and boinc was running(option not to remove from memory) and i was streaming with amaroK.In other words my machine started to feel the load.

flash got blocked in firefox3

In general it seems,that if flash get prevented(cpu,slow connection) from loading fast enough it gets in zombie mode.

Do you think that this is whats going on?A lot of people are getting seemingly random blocks.

---

### Post by esc1 on 2008-06-01
The clean install instructions worked for me. Thanks. :)

---

### Post by northwestuntu on 2008-06-04
man this flash thing is getting frustrating :mad:

i installed via nspluginwrapper on a clean install of hardy.  the flash only works for a few videos and then it's just a blank spot.  i have to restart firefox for it to work again.

it seems like the problem got worse the more ubuntu updates i did.

do i need to reinstall flash or what?  

seems like i spend so much time trying to get the flash to work right.

---

### Post by sharkcohen on 2008-06-05
Wow, I can't believe how easy this was.  Ubuntu rocks, ubuntuforums.org rocks.  Thank you ubuntuforums.org!

---

### Post by edxmonkey on 2008-06-08
Sorry, posted in the wrong section...

---

### Post by Jenga-kun on 2008-06-08
Do I have to uninstall adobe flash before I do this cuz I didn't.

---

### Post by Kilz on 2008-06-08
> **Jenga-kun said:**
> Do I have to uninstall adobe flash before I do this cuz I didn't.

No that shouldn't be necessary unless you are installing the flash 10 beta.

---

### Post by Jenga-kun on 2008-06-08
> **Kilz said:**
> No that shouldn't be necessary unless you are installing the flash 10 beta.

Well I install the script and my flash doesn't work so my next step is to uninstall adobe flash, but I don't know how. Can somebody help? I don't know if this is necessary but my system monitor says that the status of npviewer.bin is zombie.

---

### Post by Kilz on 2008-06-09
> **Jenga-kun said:**
> Well I install the script and my flash doesn't work so my next step is to uninstall adobe flash, but I don't know how. Can somebody help? I don't know if this is necessary but my system monitor says that the status of npviewer.bin is zombie.

You can follow the first part of the hardy instructions. That should remove everything. But if you installed Flash manually by some other howto you are going to have to reverse the steps, or give me some information like a link to it so I can help you.

---

### Post by onering on 2008-06-10
Fresh install of Hardy 64bit running on AMD64X2-5000+.  Having issues installing flash per below.

Step#2) ***_sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/_***
After running this line, I get no response or confirmation that it ran (this may be normal, not sure)

Step#3) **_*sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0b5/plugins/*_**
After running this line, I get: ln: target `/usr/lib/firefox-3.0b5/plugins/' is not a directory: No such file or directory

---

### Post by Yellow Pasque on 2008-06-10
@onering: 
- ln returns nothing if successful, so yes, it is normal.
- firefox has been updated from beta status to release candidate since the guide was written. The command should now be: 
```
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/**firefox-3.0**/plugins/
```

---

### Post by onering on 2008-06-10
@Temüjin: Thanks, that was it!

---

### Post by onering on 2008-06-10
@Temujin: That was it, Thanks!

---

### Post by devosion on 2008-06-11
> **northwestuntu said:**
> man this flash thing is getting frustrating :mad:

i installed via nspluginwrapper on a clean install of hardy.  the flash only works for a few videos and then it's just a blank spot.  i have to restart firefox for it to work again.

it seems like the problem got worse the more ubuntu updates i did.

do i need to reinstall flash or what?  

seems like i spend so much time trying to get the flash to work right.

Im experiencing this problem alot as well, and it seems to be occuring more and more.

---

### Post by Alex Deez on 2008-06-16
I'm just tagging this topic so I can find it again.  The instructions in the first post worked perfectly for me.

---

### Post by limejuice on 2008-06-18
I had a problem with flash video freezing after 1-2 seconds of playing. 
It turns out this was due to my video card (integrated intel 3100) not liking the default VESA driver.

I'm new to Ubuntu, and I didn't know where to check the graphics card driver.  After some searching, I found you needed to run "display-config-gtk".

After I changed my video card to "Intel" and logged out/logged back in, everything works now.

---

### Post by Awkward on 2008-06-19
The code is not working for me. I have ff3 folder installed in my home folder which is called "mike", can someone edit the script so i can install this and get flash back? I don't much about Linux lol

---

### Post by kobutak on 2008-06-22
Thanks.  Worked just fine.

---

### Post by Pethegreat on 2008-06-22
I get an error when I run the command:
```
sudo apt-get install nspluginwrapper flashplugin-nonfree 
```

This is the error I get. 
```
sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lib32nss-mdns is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree nspluginwrapper
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 131kB of archives.
After this operation, 549kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/multiverse nspluginwrapper 0.9.91.5-2ubuntu2 [113kB]
Get:2 http://us.archive.ubuntu.com hardy/multiverse flashplugin-nonfree 9.0.124.0ubuntu2 [18.7kB]
Fetched 131kB in 1s (95.8kB/s)             
Preconfiguring packages ...
Selecting previously deselected package nspluginwrapper.
(Reading database ... 175054 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_0.9.91.5-2ubuntu2_amd64.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_amd64.deb) ...
Setting up nspluginwrapper (0.9.91.5-2ubuntu2) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
Error parsing proxy URL http://:8080/: Invalid host name.
download failed
The Flash plugin is NOT installed.

```
Is there a way to manually download and set up flash since it appears that apt-get does not want to play along.

---

### Post by Yellow Pasque on 2008-06-22
Pethegreat, it looks like a problem with your proxy settings. Go to System -> Preferences -> Network Proxy and select "Direct Connection to the Internet" unless you use a proxy.

---

### Post by Pethegreat on 2008-06-22
> **Temüjin said:**
> Pethegreat, it looks like a problem with your proxy settings. Go to System -> Preferences -> Network Proxy and select "Direct Connection to the Internet" unless you use a proxy.
Well that was the problem. I got flash working with sound now.

---

### Post by bluepowder7 on 2008-06-23
fresh install of hardy (less than 12 hours old!), and the 3 lines of terminal commands worked fine (though i used aptitude instead of apt-get).  one thing i noticed, though, is that the link that's created in line 2 and 3 of your commands is actually broken as far as Thunar is concerned.  flash (youtube) works fine in firefox, haven't tried it in opera, but do you have any idea why the link is shown as broken?

here's a screenshot:

[IMG]http://i106.photobucket.com/albums/m244/GregR7/screenshots/Thunar-brokenlink.jpg[/IMG]

---

### Post by b3n5p34km4n on 2008-06-26
flash won't work for me

i attached a txt file with the terminal results that the first post said i should include.

---

### Post by ear9mrn on 2008-06-27
Firefox 3.0 update.

You will need to do the following if you are running Firefox 3.0.

sudo mv /usr/lib/firefox-3.0/plugins /usr/lib/firefox-3.0/pluginsold
sudo ln -s  /usr/lib/mozilla/plugins /usr/lib/firefox-3.0/

---

### Post by b3n5p34km4n on 2008-06-27
> **ear9mrn said:**
> Firefox 3.0 update.

You will need to do the following if you are running Firefox 3.0.

sudo mv /usr/lib/firefox-3.0/plugins /usr/lib/firefox-3.0/pluginsold
sudo ln -s  /usr/lib/mozilla/plugins /usr/lib/firefox-3.0/

i tried that, and no result.

here's the new txt file

edit:  what if i went in synaptic and completely removed firefox and all the related files, then reinstalled, then followed the directions in the first post?

---

### Post by netsurfau on 2008-06-28
Went through & followed the instructions.
Result - no change at all.

Flash doesn't always freeze FF.  With some sites, the embedded flash starts & runs for a bit then, stops leaving a grey square in place of images.

I've attached the requested info as requested in the Readme

---

### Post by jimei on 2008-06-28
[Dunk SB]("http://www.gucci-sneaker.com/catalog_39.html")
[Air force one]("http://www.gucci-sneaker.com/catalog_42.html")

---

### Post by onering on 2008-06-29
Kilz,
Thanks for the nice post.  I'm new to Ubuntu and a little confused what to do for a clean new installation of Hardy 8.04 64bit.

From your first post:
> 
If you did a clean install this step is not needed.

Which step?  The one before or after this line?

> 
Flash should work on Hardy without any scripts or work arounds other than the commands above.


From this statement, for Hardy I gather that you need to run the following lines but I'm not sure.  In other posts I see that you don't need to run these for Hardy.
> 
sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins/



Could you clarify what to do for an absolute new clean install of Hardy.  Thanks.


*EDIT*  The reason I ask is because after flash is working fine for a few hours it then stops working.  All I then get is  gray box where the flash video should be playing.  Similar to the one here: [http://ubuntuforums.org/showthread.php?p=4936499]("http://ubuntuforums.org/showthread.php?p=4936499")

---

### Post by Kilz on 2008-06-29
> **onering said:**
> 
From this statement, for Hardy I gather that you need to run the following lines but I'm not sure. In other posts I see that you don't need to run these for Hardy.
How many howto's, and or posts have you followed trying to get flash to work?

> **onering said:**
> 
*EDIT*  The reason I ask is because after flash is working fine for a few hours it then stops working.  All I then get is  gray box where the flash video should be playing.  Similar to the one here: [http://ubuntuforums.org/showthread.php?p=4936499]("http://ubuntuforums.org/showthread.php?p=4936499")

This post is about installing flash on a 64bit system. If you have flash working for any length of time, its installed. Why it runs for some people for only a short period is unknown.

---

### Post by Yellow Pasque on 2008-06-29
> after flash is working fine for a few hours it then stops working. All I then get is gray box where the flash video should be playing
I wonder if it has something to do with memory allocation. If the code is poorly written (it's Adobe coding for Linux, so it wouldn't surprise me), it could have memory leaks. Try keeping an eye on RAM usage with:
```
free -m
```

---

### Post by onering on 2008-06-29
> **Kilz said:**
> How many howto's, and or posts have you followed trying to get flash to work?

This is the only howto that I've used.  In looking for an answer to the gray box issue I see many posts telling several different ways to install flash for 64 bit.  Perhaps they are outdated methods or just wrong but as Newbie it's hard to know.  I wasn't sure if I did something wrong and that's why I'm getting the gray box.  I guess I have it installed correctly and there is a bug somewhere that gives me the gray box.

Thanks.

---

### Post by Kilz on 2008-06-29
> **onering said:**
> This is the only howto that I've used.  In looking for an answer to the gray box issue I see many posts telling several different ways to install flash for 64 bit.  Perhaps they are outdated methods or just wrong but as Newbie it's hard to know.  I wasn't sure if I did something wrong and that's why I'm getting the gray box.  I guess I have it installed correctly and there is a bug somewhere that gives me the gray box.

Thanks.

The reason I asked is because files left in from old attempts can do wierd things. But it looks like the grey box is something that happens in all versions of Ubuntu [as this post from a 32bit section shows.]("http://ubuntuforums.org/showthread.php?t=590242")
I think the memory issue may be worth looking at as Temüjin suggested. Are you running multiple tabs?

---

### Post by onering on 2008-06-29
I do run multiple tabs.  The issue seems to be intermittent for my computer.  Flash was not working when I posted about 1.5 hrs ago.  Without any reboots or changes to the system Flash is now working again.  I did restart the browswer a few times though.  I'll pay more attention to things now to try and draw a correlation.  

Last night when this first happened I "reinstalled" the flash plugin per your method:
> sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins/ 

Immediately after doing this, Flash started to work again.  Not sure if that is what fixed it or if the act of waiting a while and restarting the browser fixed it.

Here is what I get when I do "free -m".  Flash is working now though.
```

~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5979       2734       3245          0       1769        471
-/+ buffers/cache:        493       5486
Swap:         9279          0       9279
```

---

### Post by Kilz on 2008-06-29
> **onering said:**
> I do run multiple tabs.  The issue seems to be intermittent for my computer.  Flash was not working when I posted about 1.5 hrs ago.  Without any reboots or changes to the system Flash is now working again.  I did restart the browswer a few times though.  I'll pay more attention to things now to try and draw a correlation.  

Last night when this first happened I "reinstalled" the flash plugin per your method:


Immediately after doing this, Flash started to work again.  Not sure if that is what fixed it or if the act of waiting a while and restarting the browser fixed it.

Here is what I get when I do "free -m".  Flash is working now though.
```

~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5979       2734       3245          0       1769        471
-/+ buffers/cache:        493       5486
Swap:         9279          0       9279
```

We need to know about memory when it stops working.  :)

---

### Post by netsurfau on 2008-06-29
> **netsurfau said:**
> Went through & followed the instructions.
Result - no change at all.

Flash doesn't always freeze FF.  With some sites, the embedded flash starts & runs for a bit then, stops leaving a grey square in place of images.

I've attached the requested info as requested in the Readme

-------------------------------------------------------------------

Um, was my post invisible or, just being ignored :confused:

I've given up on Hardy for the time being as I was having multiple issues
with video, display, flash etc.

I'm running a clean install of Gutsy and using FF 2.0.0.14.

I have tried everything I could think of to resolve this, including removing all flash related files and trying a clean re-install.

Yet the issue doesn't go away.  FF either locks up, needing a "Force Quit" to get back up or embedded flash appears as a grey box.

I would appreciate some help here.

---

### Post by Kilz on 2008-06-30
> **netsurfau said:**
> -------------------------------------------------------------------

Um, was my post invisible or, just being ignored :confused:

I've given up on Hardy for the time being as I was having multiple issues
with video, display, flash etc.

I'm running a clean install of Gutsy and using FF 2.0.0.14.

I have tried everything I could think of to resolve this, including removing all flash related files and trying a clean re-install.

Yet the issue doesn't go away.  FF either locks up, needing a "Force Quit" to get back up or embedded flash appears as a grey box.

I would appreciate some help here.

Not ignored. But as I have pointed out to a few people. Adobe owns Flash, it is not open source. This thread is about installing Flash. If flash runs but has issues you can try the beta 10. But if flash has errors or runs bad the way to get them solved is letting Adobe know the issue exists. This issue is not a 64bit problem, but is reported to happen to all versions of Ubuntu. Ubuntu cant solve it because the code isnt open and available.

---

### Post by onering on 2008-06-30
@Kilz/@Temüjin,

Ok, it's doing it again- gray box where the flash video should be.  Here is what I get from "free -m":
```

             total       used       free     shared    buffers     cached
Mem:          5979       2381       3598          0         28       1287
-/+ buffers/cache:       1065       4914
Swap:         9279          0       9279

```

I'll leave the computer in this state.  Is there anything else you want me to check?

---

### Post by Kilz on 2008-06-30
> **onering said:**
> @Kilz/@Temüjin,

Ok, it's doing it again- gray box where the flash video should be.  Here is what I get from "free -m":
```

             total       used       free     shared    buffers     cached
Mem:          5979       2381       3598          0         28       1287
-/+ buffers/cache:       1065       4914
Swap:         9279          0       9279

```

I'll leave the computer in this state.  Is there anything else you want me to check?

Thanks, how many tabs did you have open?

---

### Post by onering on 2008-06-30
I had two instances of Firefox running.  One with four tabs open and the other with two tabs open.  It is still in that state now, are there any other useful files or logs I can post?

*EDIT* A reboot fixed it.  Flash works again.

---

### Post by ericson578 on 2008-07-02
Just wanted to say thank you to Nathan (aka reassuringlyoffensive)!  I followed your instructions and they worked perfectly.  So far no problems with flash 10b and Firefox 3.

Here are my original symptoms:  Fresh install of Hardy 64, ran all of the recommended updates right away.  First flash page I hit in firefox 3 x64 asked me to install a missing plugin, I chose yes and selected adobe.  The non-free adobe plugin installed, but after a firefox restart I would still get the "install missing plugin" prompt, meaning flash was not being recognized as an installed plugin.

Here is a copy of Nathan's commands that I ran (I did them one at a time just in case one of them failed from different dir names or something, but turns out they all worked the first time)

[HTML]ericson@fliptrak-laptop:/usr/lib/firefox-addons/plugins$ sudo apt-get purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122306 files and directories currently installed.)
Removing flashplugin-nonfree ...
Purging configuration files for flashplugin-nonfree ...
ericson@fliptrak-laptop:/usr/lib/firefox-addons/plugins$ sudo mkdir /usr/lib/flashplugin-nonfree
ericson@fliptrak-laptop:/usr/lib/firefox-addons/plugins$ sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ 
ericson@fliptrak-laptop:/usr/lib/firefox-addons/plugins$ sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so
ericson@fliptrak-laptop:/usr/lib/firefox-addons/plugins$ sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /etc/alternatives/firefox-flashplugin
ericson@fliptrak-laptop:/usr/lib/firefox-addons/plugins$ sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so
ericson@fliptrak-laptop:/usr/lib/firefox-addons/plugins$ sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
 [/HTML]

---

### Post by risher1 on 2008-07-02
> **Kilz said:**
> Not ignored. But as I have pointed out to a few people. Adobe owns Flash, it is not open source. This thread is about installing Flash. If flash runs but has issues you can try the beta 10. But if flash has errors or runs bad the way to get them solved is letting Adobe know the issue exists. This issue is not a 64bit problem, but is reported to happen to all versions of Ubuntu. Ubuntu cant solve it because the code isnt open and available.
 
I found the solution somewhere in this thread, might work for you. I seems the installer file is not executable.  
code
sudo chmod +x flashplayer-installer
sudo (./) flashplayer-installer  (may not be necessary)

Good Luck

---

### Post by iamnotthemessiah on 2008-07-05
kilz any chance of a howto for using the new nspluginwrapper ? [http://gwenole.beauchesne.info//en/projects/nspluginwrapper](http://gwenole.beauchesne.info//en/projects/nspluginwrapper)

tried installing from source but no luck
tried aliening the rpms to deb and that worked and installed but wasnt able to get it to work with flash anyway

---

### Post by MonkeyWrench32 on 2008-07-06
It's available in the uPure64 repository:  [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)

---

### Post by Kilz on 2008-07-06
> **iamnotthemessiah said:**
> kilz any chance of a howto for using the new nspluginwrapper ? [http://gwenole.beauchesne.info//en/projects/nspluginwrapper](http://gwenole.beauchesne.info//en/projects/nspluginwrapper)

tried installing from source but no luck
tried aliening the rpms to deb and that worked and installed but wasnt able to get it to work with flash anyway

I would like to take it slow on the wrapper. I'm sure it will be packaged by Ubuntu once its been checked out. Those that install it from 3rd party repositories please [report all bugs to the developer.]("http://gwenole.beauchesne.info//en/projects/nspluginwrapper")

---

### Post by dalesd on 2008-07-06
I just got Flash working, 64-bit, Flash10 Beta.  Thanks.

---

### Post by BightningLug on 2008-07-08
I'm currently having issues with flash not being able to play correctly. I'm using Firefox 3 on Hardy 64bit (AMD64). I've followed direction on installing, uninstalling, removing, purging, etc. various things related to playing flash files, including the instructions in the current thread and [this one]("http://ubuntuforums.org/showthread.php?t=766683").

My problem is that flash doesn't play. I don't get a gray box, well, sometimes I do, but the video will play for about 1 to 2 seconds and stop. Also, the sound is not working.

My previous problem was that there was always a gray box with a play symbol inside it whenever there was a flash file embedded into a page.
[IMG]http://i171.photobucket.com/albums/u302/bin_recycled/flash_box.png[/IMG]
I followed the directions [here]("http://ubuntuforums.org/showthread.php?t=766683") which removed that gray box and everything seemed fine. I rebooted and flash played as it should and I had sound. Without doing anything, it started displaying the above annoyances... not playing and/or no sound.

I have tried to install Flash 10, but the installer refuses to run saying that my 64bit architecture is not supported.

I've read in this thread that others have gotten Flash 10 installed, but I don't see how. Is there something I'm missing? Something I'm not doing correctly? How exactly do I go about installing Flash 10 on my 64bit system? Or is there some other way to resolve my problems with flash not playing correctly?

---

### Post by steveneddy on 2008-07-08
WOW! I didn't go buy this guide. I just kinda figured it out for myself, but the new Flash 10 beta ROCKS!

Finally it looks like it's supposed to!

Whoever I'm supposed to thank...

THANK YOU!!

Regards, Steven Eddy

---

### Post by Kilz on 2008-07-08
> **BightningLug said:**
> 
I have tried to install Flash 10, but the installer refuses to run saying that my 64bit architecture is not supported.

I've read in this thread that others have gotten Flash 10 installed, but I don't see how. Is there something I'm missing? Something I'm not doing correctly? How exactly do I go about installing Flash 10 on my 64bit system? Or is there some other way to resolve my problems with flash not playing correctly?

Yes, Please read and follow the instructions on the first post of this thread for installing Flash 10.

---

### Post by Soarer on 2008-07-09
Small point. I did the actions suggested in the first post with Firefox closed, and when I opened FF again YouTube still didn't work.

After a reboot however it did! A bit Microsoft-esque I know, but worth a try. :)

Thanks very much to Kilz for providing the information on this thread.

---

### Post by empty_tank on 2008-07-14
adobe flash 10 beta works in my Dell laptop running hardy.

thanks

---

### Post by sha_man on 2008-07-14
Hello,

I've got the same 'grey box' (it's actually more white than grey). Videos from Youtube seem to work. It's more the embedded content which doesn't or does work, but only for 1-2 seconds before it gets blank.

It did that sometimes on Gutsy, but now it's really worse...

Any ideas?

---

### Post by Yellow Pasque on 2008-07-14
> **sha_man said:**
> Hello,

I've got the same 'grey box' (it's actually more white than grey). Videos from Youtube seem to work. It's more the embedded content which doesn't or does work, but only for 1-2 seconds before it gets blank.

It did that sometimes on Gutsy, but now it's really worse...

Any ideas?
Make sure you have the appropriate multimedia codes installed, as Flash can include other audio/video formats from my understanding.

Xine:
```
sudo apt-get install xine-plugin libxine1-all-plugins
```

VLC:
```
sudo apt-get install vlc mozilla-plugin-vlc libvlc0
```

If that doesn't work, try starting FireFox from the terminal and see if it outputs errors/warnings there.

---

### Post by painterh on 2008-07-15
Hi;  I have suddenly started having problems with flashplugin-non-free.  I had a terrible time getting it to work in the first place, and for the last several days I have been getting error messages concerning flashplugin.  It seems there must have been some libs that were updated in a recent update and now I can neither remove it or re-install it.  In either case, flash content is not viewable in Firefox.  The error msg. is as follows
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have included the information mentioned in the post for trouble shooting. 

harlund@harlund-desktop:~$ ls -al /usr/lib/mozilla//plugins/
total 1628
drwxr-xr-x 2 root root   4096 2008-07-15 16:59 .
drwxr-xr-x 4 root root   4096 2008-04-22 11:11 ..
-rw-r--r-- 1 root root  19456 2007-01-05 11:52 libflash-mozplugin.so
lrwxrwxrwx 1 root root     39 2008-06-06 07:14 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
-rw-r--r-- 1 root root 118392 2008-04-15 10:33 libvlcplugin.so
-rw-r--r-- 1 root root 290880 2008-05-13 03:31 mplayerplug-in-dvx.so
-rw-r--r-- 1 root root   1067 2008-05-13 03:31 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root root 290880 2008-05-13 03:31 mplayerplug-in-qt.so
-rw-r--r-- 1 root root   1067 2008-05-13 03:31 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root 290880 2008-05-13 03:31 mplayerplug-in-rm.so
-rw-r--r-- 1 root root   1067 2008-05-13 03:31 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root 290872 2008-05-13 03:31 mplayerplug-in.so
-rw-r--r-- 1 root root 290880 2008-05-13 03:31 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root   1067 2008-05-13 03:31 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root   1067 2008-05-13 03:31 mplayerplug-in.xpt
harlund@harlund-desktop:~$ ls -al /usr/lib/firefox/plugins/
total 7948
drwxr-xr-x 2 root root    4096 2008-07-15 17:22 .
drwxr-xr-x 4 root root    4096 2008-05-14 20:26 ..
-rw-r--r-- 1 root root 8115888 2008-07-15 17:22 libflashplayer.so
lrwxrwxrwx 1 root root      39 2008-06-06 07:14 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root      43 2008-05-13 05:58 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root      44 2008-05-13 05:58 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 root root      42 2008-05-13 05:58 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root      43 2008-05-13 05:58 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root      42 2008-05-13 05:58 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root      43 2008-05-13 05:58 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root      39 2008-05-13 05:58 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root      43 2008-05-13 05:58 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root      44 2008-05-13 05:58 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root      40 2008-05-13 05:58 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
harlund@harlund-desktop:~$ uname -a
Linux harlund-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux
harlund@harlund-desktop:~$ 

I hope someone has some idea how to fix this.

---

### Post by Kilz on 2008-07-15
It look like you have 2 flash plugins installed.

---

### Post by painterh on 2008-07-15
Thanks for the reply.  Any idea how I can uninstall both of them and then re-install?  I tried to remove --purge and that's when I got the message I posted above.

---

### Post by Sef on 2008-07-17
I upgraded the 32-bit FF to 2.15 and lost flash and java.  What can I do to get them running again?

---

### Post by Kilz on 2008-07-17
> **Sef said:**
> I upgraded the 32-bit FF to 2.15 and lost flash and java.  What can I do to get them running again?

How did you upgrade it?

---

### Post by Sef on 2008-07-17
> How did you upgrade it?

With the upgrade button in Firefox.

---

### Post by Kilz on 2008-07-17
> **Sef said:**
> With the upgrade button in Firefox.

There is a slight change to the starter script I add so it look in the 32bit plugin folder I created for the script. Download the attached file and add it to the firefox32 folder letting it overwrite the one there. When you restart the plugins should work.

---

### Post by painterh on 2008-07-17
Does anybody know what would cause this error message when I try to install flashplugin-nonfree?

I have tried removing and re-installing using synaptic (I have tried every combination of synaptic, apt-get, aptitude) and always get the this error;
dpkg: error processing flashplugin-nonfree (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Sef on 2008-07-17
I downloaded the script to my desktop, extracted the script, opened the terminal, changed to ~/Desktop, and then cd firefox, but then I get a message 'No Such File or Directory'.  (Same message applies to cd firefox.tar.gz.)

What do I need to do to get this to work?

---

### Post by JMillard81 on 2008-07-17
> **Sef said:**
> I downloaded the script to my desktop, extracted the script, opened the terminal, changed to ~/Desktop, and then cd firefox, but then I get a message 'No Such File or Directory'.  (Same message applies to cd firefox.tar.gz.)

What do I need to do to get this to work?

./firefox

---

### Post by Kilz on 2008-07-17
> **Sef said:**
> I downloaded the script to my desktop, extracted the script, opened the terminal, changed to ~/Desktop, and then cd firefox, but then I get a message 'No Such File or Directory'.  (Same message applies to cd firefox.tar.gz.)

What do I need to do to get this to work?

It is not an installation script, it is a replacement of the file in the firefox32 folder of the same name. Just copy the file into the /usr/local/firefox32 folder.

---

### Post by Sef on 2008-07-17
Replaced the run-mozilla.sh.  Now it does not come on.  Will run a bit on the bottom bar, but that is it.

---

### Post by enjoysunday on 2008-07-17
Hey guys&#65281;&#65281;:):)
I am a new LORD player. I am very interested of it even though I do not know it much I just started playing in the beginning of this month. I enjoy it a lot .:guitar:
And I really do not know which class is good for me and I really do not have a lot of time playing the game everyday . just about 2 hours after I finish my work. i am looking forward to ur advice and suggestions . thanks a lot :guitar:
By the way , I really like and trust   agamegold.com  [www.wow.4s.com](www.wow.4s.com) 
you can just have a try to go there and juge by yourself:lolflag:

---

### Post by gonxa62 on 2008-07-17
Muy bueno el post pude solucionar el problema de sonido de las peliculas flash en mi ubuntu 8.0 hardy heron,en AMD64, con el navegador mozilla firefox 3.0
mUCHAS gRACIAS DESDE ARGENTINA

---

### Post by Sef on 2008-07-17
> Muy bueno el post pude solucionar el problema de sonido de las peliculas flash en mi ubuntu 8.0 hardy heron,en AMD64, con el navegador mozilla firefox 3.0
mUCHAS gRACIAS DESDE ARGENTINA

Very good post I was able to solve the sound problem with the  flash movies in my ubuntu 8,0 hardy heron, AMD64, with the navigator mozilla firefox 3.0

Thank you from Argentina

---

### Post by Kilz on 2008-07-17
> **Sef said:**
> Replaced the run-mozilla.sh.  Now it does not come on.  Will run a bit on the bottom bar, but that is it.

In the firefox32 folder is a file named firefox. That was what I thought was in the tarball. Was the file you extracted named run-mozilla.sh?

---

### Post by Sef on 2008-07-17
> Was the file you extracted named run-mozilla.sh?

Yes.  I didn't see a folder named firefox.

Update: Wait.  There is a firefox folder.  

If you have the run-mozilla.sh, I will need a copy of that, get it from elsewhere, or install firefox.

---

### Post by Kilz on 2008-07-18
Sure, here it is.

---

### Post by ThunderRd on 2008-07-18
I'm going to do something highly unusual ;) and ask some questions ***before*** I do anything.

I have used your script in the past for feisty, so I am somewhat familiar with it.  I now have a clean install of 8.04.1, and I can install either 9 or 10.  In your OP you said that the Flash 10 beta is superior to 9, so I have downloaded the file. 

ia32libs is already installed, I run Folding@Home and it's required for that.

#1- Before I run the Flash 10 install commands for Hardy in the OP, should I install nspluginwrapper?  I don't see it in the listed commands here, so should I assume that these commands are for users of Flash 9 who wish to go to 10?

```
sudo apt-get purge flashplugin-nonfree
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
cd ~/Desktop
tar -xzvf flashplayer10_install_linux_070208.tar.gz install_flash_player_10_linux
sudo mv -f ~/Desktop/install_flash_player_10_linux/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo ln -s /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
```

#2- If this is to replace Flash 9 with 10, how about new installs?  Are there any other needed packages [other than ia32libs] to satisfy any dependencies?

#3- Is there any reason to install Flash 9 rather than 10?

---

### Post by Kilz on 2008-07-18
> **ThunderRd said:**
> I'm going to do something highly unusual ;) and ask some questions ***before*** I do anything.

I have used your script in the past for feisty, so I am somewhat familiar with it.  I now have a clean install of 8.04.1, and I can install either 9 or 10.  In your OP you said that the Flash 10 beta is superior to 9, so I have downloaded the file. 

ia32libs is already installed, I run Folding@Home and it's required for that.

#1- Before I run the Flash 10 install commands for Hardy in the OP, should I install nspluginwrapper?  I don't see it in the listed commands here, so should I assume that these commands are for users of Flash 9 who wish to go to 10?

```
sudo apt-get purge flashplugin-nonfree
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
cd ~/Desktop
tar -xzvf flashplayer10_install_linux_070208.tar.gz install_flash_player_10_linux
sudo mv -f ~/Desktop/install_flash_player_10_linux/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo ln -s /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
```

#2- If this is to replace Flash 9 with 10, how about new installs?  Are there any other needed packages [other than ia32libs] to satisfy any dependencies?

#3- Is there any reason to install Flash 9 rather than 10?

You are correct, it is highly unusual, :D but one of the best things to do. First, yes the instructions were written from the beliefe that someone would have flash 9 installed. So please install nspluginwrapper and lib32nss-mdns. If I were you, I would go strait to 10, there is no real reason not to and a lot of good reasons to.

---

### Post by ThunderRd on 2008-07-19
Thanks for the answers.  I'll give it a go tonight.

---

### Post by ntan01 on 2008-07-19
when I try to install flashplugin-nonfree I get the following error


Download done.
Flash Plugin installed.
invalid option -n
nspluginwrapper, configuration tool.  Version 1.0.0

   usage: nspluginwrapper [flags] [command [plugin(s)]]

   -h --help               print this message
   -v --verbose            flag: set verbose mode
   -a --auto               flag: set automatic mode for plugins discovery
   -l --list               list plugins currently installed
   -u --update             update plugin(s) currently installed
   -i --install [FILE(S)]  install plugin(s)
   -r --remove [FILE(S)]   remove plugin(s)

dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)



Is this a bug that I need to report or am I screwing something up?

-Nate

Running Ubuntu 8.04

---

### Post by painterh on 2008-07-19
This exactly what I have been fighting with for the last week.  Your error message is the same as mine.  I have tried everything, even installing the latest flashplugin-nonfree 10.  No difference.  something is definitely broken, and I think it is related to a recent update of nspluginwrapper or ia32-libs.  At any rate, you might want to follow with a report on Lauchpad.

---

### Post by Kilz on 2008-07-19
> **ntan01 said:**
> when I try to install flashplugin-nonfree I get the following error


Download done.
Flash Plugin installed.
invalid option -n
nspluginwrapper, configuration tool.  Version 1.0.0

   usage: nspluginwrapper [flags] [command [plugin(s)]]

   -h --help               print this message
   -v --verbose            flag: set verbose mode
   -a --auto               flag: set automatic mode for plugins discovery
   -l --list               list plugins currently installed
   -u --update             update plugin(s) currently installed
   -i --install [FILE(S)]  install plugin(s)
   -r --remove [FILE(S)]   remove plugin(s)

dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)



Is this a bug that I need to report or am I screwing something up?

-Nate

Running Ubuntu 8.04

Nspluginwrapper in [the Ubuntu repositories]("http://packages.ubuntu.com/hardy/nspluginwrapper") is at version 0.9.91.5. You might have a 3rd party repository enabled that is installing version 1.0.0. Since that package appears to be broken, I suggest you uninstall it, download the package from the Ubuntu repository, install it, then lock the version in Synaptic so you dont have it upgraded to a broken package.
Filing a bug report on Launchpad for the packages of a 3rd party repository will do no good. You should inform the repository owner.To find that out, before replaceing it, search for it in Synaptic, highlight it, then click Package, then propeerties. The Maintainer should give you an idea who it belongs to.

---

### Post by painterh on 2008-07-19
Sorry for asking a really stupid question, but I've downloaded the file (nspluginwrapper-0.9.91.5)
 from Ubuntu repo and don't know how to install. I am still learning directory structure and commands.

---

### Post by Kilz on 2008-07-19
> **painterh said:**
> Sorry for asking a really stupid question, but I've downloaded the file (nspluginwrapper-0.9.91.5)
 from Ubuntu repo and don't know how to install. I am still learning directory structure and commands.

first uninstall tghe other one, close synaptic and double click on the deb.

---

### Post by painterh on 2008-07-19
Thanks for the reply Kilz. I will look on the web site and see if they have a .deb for nspluginwrapper 0.9.91.5.  The one I downloaded was a tar.gz file

---

### Post by Kilz on 2008-07-19
> **painterh said:**
> Thanks for the reply Kilz. I will look on the web site and see if they have a .deb for nspluginwrapper 0.9.91.5.  The one I downloaded was a tar.gz file

Post 213 has a direct link to the nspluginwrapper page for the Ubuntu repository. You can download a deb from there.

---

### Post by robcar on 2008-07-19
Thanks; I had the same problem and your solution worked for me.
The repo with the broken nspluginwrapper package was **hardy-upure64**, so I disabled it, did an update and now flash works fine!
:)

I'll tell the package maintainer about that above.

thanks a lot! 

--
rob

---

### Post by painterh on 2008-07-20
Thanks alot, I got the .deb and it worked perfectly.  I really appreciate your help.

---

### Post by Sef on 2008-07-20
Thank you Kliz for that.  However, FF2 still does not start up.  Should I uninstall and reinstall it or is there something else to try?

---

### Post by Kilz on 2008-07-20
> **Sef said:**
> Thank you Kliz for that.  However, FF2 still does not start up.  Should I uninstall and reinstall it or is there something else to try?

Go to the howto and download the deb. :)

---

### Post by ntan01 on 2008-07-20
> **Kilz said:**
> Nspluginwrapper in [the Ubuntu repositories]("http://packages.ubuntu.com/hardy/nspluginwrapper") is at version 0.9.91.5. You might have a 3rd party repository enabled that is installing version 1.0.0. Since that package appears to be broken, I suggest you uninstall it, download the package from the Ubuntu repository, install it, then lock the version in Synaptic so you dont have it upgraded to a broken package.
Filing a bug report on Launchpad for the packages of a 3rd party repository will do no good. You should inform the repository owner.To find that out, before replaceing it, search for it in Synaptic, highlight it, then click Package, then propeerties. The Maintainer should give you an idea who it belongs to.

That fixed it. I've been fiddling around in soruce.list lately trying to get something else working. I'll contact the maintainer and let them know about the bug.

Thanks for your help.

-Nate

---

### Post by Sef on 2008-07-22
> Go to the howto and download the deb. 

Thank you.  It is working again.

---

### Post by dancmd on 2008-07-23
dan@cmd:~$ sudo apt-get purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dan@cmd:~$ sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
dan@cmd:~$ sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
dan@inspiron:~$ cd ~/Desktop
dan@inspiron:~/Desktop$ tar -xzvf flashplayer10_install_linux_070208.tar.gz install_flash_player_10_linux
install_flash_player_10_linux/
install_flash_player_10_linux/libflashplayer.so
install_flash_player_10_linux/flashplayer-installer
dan@cmd:~/Desktop$ sudo mv -f ~/Desktop/install_flash_player_10_linux/libflashplayer.so /usr/lib/firefox-addons/plugins/
dan@cmd:~/Desktop$ sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo: nspluginwrapper: command not found

-------------------------------------------
what's wrong?!

---

### Post by Kilz on 2008-07-23
> **dancmd said:**
> dan@cmd:~$ sudo apt-get purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dan@cmd:~$ sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
dan@cmd:~$ sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
dan@inspiron:~$ cd ~/Desktop
dan@inspiron:~/Desktop$ tar -xzvf flashplayer10_install_linux_070208.tar.gz install_flash_player_10_linux
install_flash_player_10_linux/
install_flash_player_10_linux/libflashplayer.so
install_flash_player_10_linux/flashplayer-installer
dan@cmd:~/Desktop$ sudo mv -f ~/Desktop/install_flash_player_10_linux/libflashplayer.so /usr/lib/firefox-addons/plugins/
dan@cmd:~/Desktop$ sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo: nspluginwrapper: command not found

-------------------------------------------
what's wrong?!

please provide the results of ```
uname -a
```

---

### Post by hobbes_ba on 2008-07-26
I have a annoying problem.

Every time I exited a flash full screen video using compiz the video (youtube) gets freeze. Only audio, at least for a time until the embedded video starts to actually play.

If I minimize the browser window and later restore it, goes away.

There is a workaround for this?

Firefox 3 + Intrepid Ibex Alpha 3 

(the very same thing happen with Hardy too)

Anyone?

---

### Post by bholliday72 on 2008-07-31
Hey thanks for the script for flash 9, it works perfectly now :)

---

### Post by onering on 2008-08-03
I removed Flash 9 and installed Flash 10 Beta as described in the first post.  Flash 10 works great on YouTube however when I go to other websites like [www.cnn.com](www.cnn.com) or [www.bestbuy.com](www.bestbuy.com) it tells me that a Flash player is not installed.  

Is there something wrong with the installation or is it that these websites don't recognize the Beta version?  If so, how can I trick them into seeing the Beta version?

---

### Post by Kilz on 2008-08-03
> **onering said:**
> I removed Flash 9 and installed Flash 10 Beta as described in the first post.  Flash 10 works great on YouTube however when I go to other websites like [www.cnn.com](www.cnn.com) or [www.bestbuy.com](www.bestbuy.com) it tells me that a Flash player is not installed.  

Is there something wrong with the installation or is it that these websites don't recognize the Beta version?  If so, how can I trick them into seeing the Beta version?

I do not know, if there are any issues with Beta 10 follow the instructions on the first post.

---

### Post by bholliday72 on 2008-08-04
Thanks, flash now works in FF3.0.1 but not in Opera 9.51.  I'll chalk it up to opera being broken. :lolflag:

---

### Post by JMonkeYJ on 2008-08-05
heh, this isn't going too well for me. i searched the thread but didn't see anyone else having the same problem:

after i run
sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns

i get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lib32nss-mdns

any ideas?

---

### Post by Yellow Pasque on 2008-08-05
> **JMonkeYJ said:**
> E: Couldn't find package lib32nss-mdns

Go to System -> Administration -> Software Sources and make sure you have all the repos enabled (or at least main, universe, and multiverse).

---

### Post by bawilson2 on 2008-08-06
> **onering said:**
> I removed Flash 9 and installed Flash 10 Beta as described in the first post.  Flash 10 works great on YouTube however when I go to other websites like [www.cnn.com](www.cnn.com) or [www.bestbuy.com](www.bestbuy.com) it tells me that a Flash player is not installed.  

Is there something wrong with the installation or is it that these websites don't recognize the Beta version?  If so, how can I trick them into seeing the Beta version?

It is the websites.  Many sites only check if the version is equal to 7, 8, or 9.  If you have the newer version 10 it will fail just as if you had a really old version.  Sites need to update their code before the players will work.  Should happen sometime as version 10 gains more steam.

---

### Post by JMonkeYJ on 2008-08-07
> **Temüjin said:**
> Go to System -> Administration -> Software Sources and make sure you have all the repos enabled (or at least main, universe, and multiverse).

they already are :confused:

---

### Post by Yellow Pasque on 2008-08-07
> **JMonkeYJ said:**
> they already are :confused:
You ARE running the 64-bit version of Ubuntu, right?
```
uname -a
```

---

### Post by JMonkeYJ on 2008-08-07
> **Temüjin said:**
> You ARE running the 64-bit version of Ubuntu, right?
```
uname -a
```

yeah:

Linux 2.6.22-15-generic #1 SMP Tue Jun 10 08:52:15 UTC 2008 x86_64 GNU/Linux

confounding, isn't it? i'm using ubuntu 7.10 if that makes a difference. maybe i should try upgrading to 8.04.

---

### Post by 4Bhere on 2008-08-09
Hi
Thankyou for the flash 9 install info.
I cant get videos to play on CNN after installing
Here is the outputs requested:
:~$ ls -al /usr/lib/mozilla//plugins/
total 12
drwxr-xr-x 2 root root 4096 2008-06-06 08:38 .
drwxr-xr-x 4 root root 4096 2008-03-30 22:31 ..
lrwxrwxrwx 1 root root   37 2008-04-05 14:56 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   34 2008-05-20 16:49 libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so
lrwxrwxrwx 1 root root   60 2008-06-06 08:38 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
:~$ ls -al /usr/lib/firefox/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-05-20 16:49 .
drwxr-xr-x 6 root root 4096 2008-03-30 22:34 ..
lrwxrwxrwx 1 root root   37 2008-04-05 14:56 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root   34 2008-05-20 16:49 libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so
:~$ ls -al /usr/lib/firefox-3.0.1/plugins/
total 12
drwxr-xr-x 2 root root 4096 2008-08-09 10:21 .
drwxr-xr-x 5 root root 4096 2008-03-30 22:34 ..
lrwxrwxrwx 1 root root   60 2008-08-09 10:21 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
:~$ uname -a
Linux 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux


Not sure if I did it correctly.  I also checked with "about-plugins" and shockwave flash is listed

Any guidance is appreciated ;);)](*,)](*,):neutral::-o

---

### Post by Yellow Pasque on 2008-08-09
4BHere: Flash can embed other media formats inside of it. Make sure you have the proper codecs installed and a plugin to go with it.
Personally, I prefer VLC.  Alternatives are totem, xine and mplayer.
```
sudo apt-get install mozilla-plugin-vlc
```

---

### Post by WillyLinux on 2008-08-09
> **Kilz said:**
> [COLOR="Sienna"][SIZE="4"]**Hardy Heron**[/SIZE][/COLOR]
To install flash to Hardy...
.

thanks!!!
worked great.

Ubuntu 8.04 64 bits 2.6.24-19-generic
Firefox 3.0
Script nspluginwrapper-install-0-1.8.6-2.tar.gz

---

### Post by Udibuntu on 2008-08-10
Hi Kilz, Guys

No Flash on FF3.0.1, Feisty 64amd.

I went through every walkthrough I saw to no avail...

pasted below are the details you need, I hope, to help...

Cheers you guys,

Udi

-------

udi@udi-laptop:~$ ls -al /usr/lib/mozilla//plugins/
total 1576
drwxr-xr-x 2 udi  users   4096 2008-08-10 10:00 .
drwxr-xr-x 3 root root    4096 2007-04-15 14:58 ..
lrwxrwxrwx 1 udi  users     36 2008-03-19 21:59 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 udi  users     37 2008-03-19 21:59 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 udi  users     34 2008-03-19 21:59 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 udi  users     35 2008-03-19 21:59 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 udi  users     36 2008-03-19 21:59 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 udi  users     37 2008-03-19 21:59 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 udi  users     42 2008-03-19 21:59 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 udi  users     43 2008-03-19 21:59 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 udi  users 118744 2008-03-12 00:08 libvlcplugin.so
-rw-r--r-- 1 udi  users 269216 2007-01-26 02:17 mplayerplug-in-dvx.so
-rw-r--r-- 1 udi  users    981 2007-01-26 02:17 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 udi  users 269408 2007-01-26 02:17 mplayerplug-in-qt.so
-rw-r--r-- 1 udi  users    981 2007-01-26 02:17 mplayerplug-in-qt.xpt
-rw-r--r-- 1 udi  users 269472 2007-01-26 02:17 mplayerplug-in-rm.so
-rw-r--r-- 1 udi  users    981 2007-01-26 02:17 mplayerplug-in-rm.xpt
-rw-r--r-- 1 udi  users 270648 2007-01-26 02:17 mplayerplug-in.so
-rw-r--r-- 1 udi  users 269760 2007-01-26 02:17 mplayerplug-in-wmp.so
-rw-r--r-- 1 udi  users    981 2007-01-26 02:17 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 udi  users    981 2007-01-26 02:17 mplayerplug-in.xpt
-rwxr-xr-x 1 udi  users  78152 2008-08-10 09:34 npwrapper.libflashplayer.so
udi@udi-laptop:~$ ls -al /usr/lib/firefox/plugins/
total 24
drwxr-xr-x 2 udi  users  4096 2008-08-10 09:47 .
drwxr-xr-x 5 root root   4096 2008-07-18 12:31 ..
lrwxrwxrwx 1 udi  users    36 2008-03-19 21:59 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 udi  users    37 2008-03-19 21:59 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 udi  users    34 2008-03-19 21:59 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 udi  users    35 2008-03-19 21:59 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 udi  users    36 2008-03-19 21:59 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 udi  users    37 2008-03-19 21:59 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 udi  users    42 2008-03-19 21:59 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 udi  users    43 2008-03-19 21:59 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root  11072 2008-07-15 19:55 libunixprintplugin.so
lrwxrwxrwx 1 udi  users    37 2008-03-26 11:32 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so
lrwxrwxrwx 1 udi  users    42 2008-03-19 22:23 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 udi  users    43 2008-03-19 22:23 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 udi  users    42 2008-03-19 22:23 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 udi  users    43 2008-03-19 22:23 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 udi  users    39 2008-03-19 22:23 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 udi  users    43 2008-03-19 22:23 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 udi  users    44 2008-03-19 22:23 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 udi  users    40 2008-03-19 22:23 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root     60 2008-08-10 09:34 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 root root     24 2008-08-10 09:47 plugins -> /usr/lib/firefox/plugins
udi@udi-laptop:~$ uname -a
Linux udi-laptop 2.6.20-17-generic #2 SMP Wed Jul 9 22:24:42 UTC 2008 x86_64 GNU/Linux
udi@udi-laptop:~$

---

### Post by Kilz on 2008-08-10
[QUOTE=Udibuntu;5558691]Hi Kilz, Guys

No Flash on FF3.0.1, Feisty 64amd.

I went through every walkthrough I saw to no avail...

pasted below are the details you need, I hope, to help...

Cheers you guys,

Udi

-------

The flash plugin is not installed. What happens if you try ```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Udibuntu on 2008-08-10
The flash plugin is not installed. What happens if you try ```
sudo apt-get install flashplugin-nonfree
```[/QUOTE]

What I get is this - 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libxul-common libglib-java libnspr4-0d libwavpack1 libgtk-jni libgtkglext1
  libxul0d libgstreamer0.8-0 libcdaudio1 libmozjs0d libcairo-java
  libsoundtouch1c2 libnss3-0d libswt3.2-gtk-jni libmms0
Use 'apt-get autoremove' to remove them.

And no Flash.

How do I enter the command for autoremove?

---

### Post by Kilz on 2008-08-10
> **Udibuntu said:**
> The flash plugin is not installed. What happens if you try ```
sudo apt-get install flashplugin-nonfree
```

What I get is this - 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libxul-common libglib-java libnspr4-0d libwavpack1 libgtk-jni libgtkglext1
  libxul0d libgstreamer0.8-0 libcdaudio1 libmozjs0d libcairo-java
  libsoundtouch1c2 libnss3-0d libswt3.2-gtk-jni libmms0
Use 'apt-get autoremove' to remove them.

And no Flash.

How do I enter the command for autoremove?[/QUOTE]

```
sudo apt-get autoremove
```

---

### Post by Udibuntu on 2008-08-11
Thanks Kilz for taking the time to walk me through this. If it wasn't for you I would have already given up on FF3..

Should I run the earlier code before autoremove or just open terminal and copy the autoremove command?

Also, what shoud I do after the autoremove is executed? re-run which commands?

Thanks again,

Udi

---

### Post by Udibuntu on 2008-08-11
Update:

No Flash.

Autoremoved some 35MB and re-ran the old flash plugin. process went OK but no Flash.

I think I have something wrong in either folder names or paths, or something.

I'd still appreciate your help.

Udi

---

### Post by Dwezzel on 2008-08-11
Same here...no more flash since Firefox was upgraded to 3.0.1.

Everything is in place like before...does the Firefox 3.0.1 upgrade broke something ??  

Trying to figure out what can be broke...

If someone else have this issue since upgrading Firefox to 3.0.1, maybe it can help narrowing the problem.

Dwe

---

### Post by Kilz on 2008-08-11
> **Dwezzel said:**
> Same here...no more flash since Firefox was upgraded to 3.0.1.

Everything is in place like before...does the Firefox 3.0.1 upgrade broke something ??  

Trying to figure out what can be broke...

If someone else have this issue since upgrading Firefox to 3.0.1, maybe it can help narrowing the problem.

Dwe

If you are running Hardy, follow the Hardy howto, including the top section to remove the old plugin and wrapper.

---

### Post by Dwezzel on 2008-08-11
Hi Kilz,

> If you are running Hardy, follow the Hardy howto, including the top section to remove the old plugin and wrapper.

I've tried that....no results.  Youtube is still not working ...

Dwe

---

### Post by Kilz on 2008-08-11
> **Dwezzel said:**
> Hi Kilz,



I've tried that....no results.  Youtube is still not working ...

Dwe

Are the flashplugin-nonfree and nspluginwrapper packages installed?

If those packages are installed (look in synaptic if unsure) what are the results of ```
ls -al /usr/lib/firefox-addons
```

---

### Post by Dwezzel on 2008-08-11
> Are the flashplugin-nonfree and nspluginwrapper packages installed?

Yes they are...I,ve verified with synaptic.

Here's the result of

 ```
ls -al /usr/lib/firefox-addons
```

```
 ls -al /usr/lib/firefox-addons/plugins/
total 12
drwxr-xr-x 2 root root 4096 2008-08-11 13:18 .
drwxr-xr-x 5 root root 4096 2008-04-22 14:09 ..
lrwxrwxrwx 1 root root   60 2008-08-11 13:18 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```


Dwe

---

### Post by Kilz on 2008-08-11
what is the result of ```
ls -al /usr/lib/flashplugin-nonfree
```

---

### Post by alexcuervo on 2008-08-11
The flash Beta 10 procedure does not work with the just released (Aug 11 2008 ) Flash version 10.0.0.569 on 64 bit systems

---

### Post by Dwezzel on 2008-08-12
Hi Kilz,

Here's what you requested....


```
ls -al /usr/lib/flashplugin-nonfree
total 8016
drwxr-xr-x   2 root root    4096 2008-08-11 13:17 .
drwxr-xr-x 178 root root   69632 2008-08-11 14:57 ..
-rw-r--r--   1 root root 8115888 2008-08-11 13:17 libflashplayer.so
```


Dwe

---

### Post by Dwezzel on 2008-08-12
Wow....

Just reboot the system...and flash seems running OK....I didn't do anything though...

hmmmm...intermittent stuff... ???   I'll keep you in touch...

Dwe

---

### Post by Udibuntu on 2008-08-12
Bump.

I still have trouble, even after rebooting..

Feisty 64bit with FF3 - no Flash.

Please help..

Udi

---

### Post by Kilz on 2008-08-12
> **Udibuntu said:**
> Bump.

I still have trouble, even after rebooting..

Feisty 64bit with FF3 - no Flash.

Please help..

Udi

Read posts #247 forward between me and Dwezzel. Please do as I suggested and provide all the information I asked him for

---

### Post by Udibuntu on 2008-08-13
> **Kilz said:**
> Read posts #247 forward between me and Dwezzel. Please do as I suggested and provide all the information I asked him for

```
udi@udi-laptop:~$ ls -al /usr/lib/firefox-addons
ls: /usr/lib/firefox-addons: No such file or directory
udi@udi-laptop:~$ ls -al /usr/lib/flashplugin-nonfree
total 6960
drwxr-xr-x   2 udi  udi     4096 2008-08-11 14:11 .
drwxr-xr-x 148 root root   65536 2008-08-11 14:11 ..
-rwxr-xr-x   1 udi  udi  7040036 2007-06-20 03:31 libflashplayer.so
udi@udi-laptop:~$ 
```

---

### Post by Kilz on 2008-08-13
> **Udibuntu said:**
> ```
udi@udi-laptop:~$ ls -al /usr/lib/firefox-addons
ls: /usr/lib/firefox-addons: No such file or directory
udi@udi-laptop:~$ ls -al /usr/lib/flashplugin-nonfree
total 6960
drwxr-xr-x   2 udi  udi     4096 2008-08-11 14:11 .
drwxr-xr-x 148 root root   65536 2008-08-11 14:11 ..
-rwxr-xr-x   1 udi  udi  7040036 2007-06-20 03:31 libflashplayer.so
udi@udi-laptop:~$ 
```

Please try to rerun the r48 script.

---

### Post by Udibuntu on 2008-08-13
> **Kilz said:**
> Please try to rerun the r48 script.

```
ls -al /usr/lib/flashplugin-nonfreeudi@udi-laptop:~$ ls -al /usr/lib/flashplugin-nonfree
total 6960
drwxr-xr-x   2 udi  udi     4096 2008-08-13 16:38 .
drwxr-xr-x 148 root root   65536 2008-08-13 16:38 ..
-rwxr-xr-x   1 udi  udi  7040036 2007-06-20 03:31 libflashplayer.so
udi@udi-laptop:~$ ls -al /usr/lib/firefox-addons
ls: /usr/lib/firefox-addons: No such file or directory **(((((can this be the reason?)))))**
udi@udi-laptop:~$ 
```

No Flash after browser restart.

---

### Post by Kilz on 2008-08-13
> **Udibuntu said:**
> ```
ls -al /usr/lib/flashplugin-nonfreeudi@udi-laptop:~$ ls -al /usr/lib/flashplugin-nonfree
total 6960
drwxr-xr-x   2 udi  udi     4096 2008-08-13 16:38 .
drwxr-xr-x 148 root root   65536 2008-08-13 16:38 ..
-rwxr-xr-x   1 udi  udi  7040036 2007-06-20 03:31 libflashplayer.so
udi@udi-laptop:~$ ls -al /usr/lib/firefox-addons
ls: /usr/lib/firefox-addons: No such file or directory **(((((can this be the reason?)))))**
udi@udi-laptop:~$ 
```

No Flash after browser restart.

No, thats not the reason, you are running Feisty, firefox-addons is only in Hardy.
What are the results of ```
ls -al /usr/lib/nspluginwrapper/plugins/
```

---

### Post by Yellow Pasque on 2008-08-13
> **Kilz said:**
> No, thats not the reason, you are running Feisty, firefox-addons is only in Hardy.

Shouldn't this directory be present if he's trying to run FF3?
Udibuntu, see if there's a firefox-3.... directory in /usr/lib/. The name of the directory kept changing with the version of FF3, so that's why the firefox-addons directory was created. Perhaps this is not the case with Feisty.

---

### Post by Kilz on 2008-08-13
> **Temüjin said:**
> Shouldn't this directory be present if he's trying to run FF3?
Udibuntu, see if there's a firefox-3.... directory in /usr/lib/. The name of the directory kept changing with the version of FF3, so that's why the firefox-addons directory was created. Perhaps this is not the case with Feisty.

What you asked got me thinking, Firefox 3.0 series isnt in the Feisty repositories. Gutsy is as far back as it goes. So we need to find out how and where Firefox 3.0.1 was installed by Udibuntu.

---

### Post by Udibuntu on 2008-08-14
First Kilz - 

```
udi@udi-laptop:~$ ls -al /usr/lib/nspluginwrapper/plugins/
total 92
drwxr-xr-x 2 udi users  4096 2008-08-13 16:38 .
drwxr-xr-x 6 udi udi    4096 2008-08-13 16:37 ..
-rwxr-xr-x 1 udi users 78152 2008-08-13 16:38 npwrapper.libflashplayer.so
udi@udi-laptop:~$ 
```

Temujin, thanks for trying to help. This is what I get, I hope I copied the command right.

```
udi@udi-laptop:~$ /usr/lib/firefox-3
bash: /usr/lib/firefox-3: No such file or directory
udi@udi-laptop:~$ 
```

I got FF3 from Mozilla, not from Feisty repo's, since they don't have it. I'm using FF3 at the moment, and though it is linked to app's menu and the bar icon I have placed, it is not listed in neither add/remove list nor in Synaptic.

I was guided by aysiu in this [thread]("http://ubuntuforums.org/showthread.php?t=879749").

---

### Post by Kilz on 2008-08-14
> **Udibuntu said:**
> First Kilz - 
[B]
I got FF3 from Mozilla[/B], not from Feisty repo's, since they don't have it. I'm using FF3 at the moment, and though it is linked to app's menu and the bar icon I have placed, **it is not listed in neither add/remove list nor in Synaptic.**

I was guided by aysiu in this [thread]("http://ubuntuforums.org/showthread.php?t=879749").

This is your problem. You manually installed Firefox 3 from Mozilla. Firefox from Mozilla isnt in the place that Ubuntu installs it, it also isnt coded to look for plugins where Ubuntu places them. You will have to manually have to install all plugins to its plugin folder for them to work.

```
sudo ln -s /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /path/to/FF3/plugins/
```
You are going to have to edit this command for it to work. You are going to have to replace /path/to/FF3 with the path to Firefox3.

---

### Post by Udibuntu on 2008-08-14
> **Kilz said:**
> This is your problem. You manually installed Firefox 3 from Mozilla. Firefox from Mozilla isnt in the place that Ubuntu installs it, it also isnt coded to look for plugins where Ubuntu places them. You will have to manually have to install all plugins to its plugin folder for them to work.

```
sudo ln -s /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /path/to/FF3/plugins/
```
You are going to have to edit this command for it to work. You are going to have to replace /path/to/FF3 with the path to Firefox3.


Thanks Kilz, I thought so.
Uhhmm..how do I know what this path to FF3 is? I don't know thw syntax for this process.

---

### Post by Kilz on 2008-08-14
> **Udibuntu said:**
> Thanks Kilz, I thought so.
Uhhmm..how do I know what this path to FF3 is? I don't know thw syntax for this process.

Since you manually installed it, I have no idea where you placed firefox 3 in the file system. That is the path.

---

### Post by Yellow Pasque on 2008-08-14
> **Udibuntu said:**
> Thanks Kilz, I thought so.
Uhhmm..how do I know what this path to FF3 is? I don't know thw syntax for this process.
open up the file browser (Nautilus) and search for firefox-

---

### Post by Udibuntu on 2008-08-15
> **Temüjin said:**
> open up the file browser (Nautilus) and search for firefox-

All references are pointing to FF2.

The only FF3 result is the tar file I installed from.

It's like FF3 is not installed on my system at all, just running, he he...:confused:

---

### Post by Plasma_NZ on 2008-08-16
ok.. strange issue..

Flash pages work fine, flash video's do not.

using the latest updates for firefox etc..

firefox 3.0.1 

Here's the following data related 

> ls -al /usr/lib/mozilla//plugins/
total 12
drwxr-xr-x 2 physics users 4096 2008-08-16 21:49 .
drwxr-xr-x 4 root    root  4096 2008-02-22 14:58 ..
lrwxrwxrwx 1 root    root    37 2008-08-16 21:49 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rwx------ 1 physics users    0 2008-08-16 21:46 libflashplayer.so
lrwxrwxrwx 1 physics users   60 2008-08-16 21:46 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

> ls -al /usr/lib/firefox/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-08-16 21:49 .
drwxr-xr-x 4 root root 4096 2008-08-16 21:49 ..
lrwxrwxrwx 1 root root   37 2008-08-16 21:49 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin

> uname -a
Linux physics 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

---

### Post by Udibuntu on 2008-08-17
Bump.

I've tried running FF3 from terminal, FF3 runs after that, no Flash.

But look at this output, can anybody decipher this?

> udi@udi-laptop:~$ firefox

(firefox-bin:15188): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox-bin:15188): Gtk-WARNING **: Error loading theme icon for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory

(firefox-bin:15188): Gtk-WARNING **: Error loading theme icon for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory
LoadPlugin: failed to initialize shared library /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so [/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libunixprintplugin.so [/usr/lib/firefox/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libvlcplugin.so [/usr/lib/mozilla/plugins/libvlcplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/libtotem-basic-plugin.so [/usr/lib/totem/libtotem-basic-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/libtotem-gmp-plugin.so [/usr/lib/totem/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/libtotem-mully-plugin.so [/usr/lib/totem/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/libtotem-narrowspace-plugin.so [/usr/lib/totem/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-qt.so [/usr/lib/mozilla/plugins/mplayerplug-in-qt.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-rm.so [/usr/lib/mozilla/plugins/mplayerplug-in-rm.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so [/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in.so [/usr/lib/mozilla/plugins/mplayerplug-in.so: wrong ELF class: ELFCLASS64]
udi@udi-laptop:~$ 

---

### Post by Kilz on 2008-08-17
> **Udibuntu said:**
> Bump.

I've tried running FF3 from terminal, FF3 runs after that, no Flash.

But look at this output, can anybody decipher this?

Please provide the command that you used to enable flash. 

You also , have errors from installing a 32bit firefox 3, gtk the totem plugin on a 64bit install. This thread is only about flash and how to install it.

---

### Post by Udibuntu on 2008-08-17
> **Kilz said:**
> Please provide the command that you used to enable flash. 

You also , have errors from installing a 32bit firefox 3, gtk the totem plugin on a 64bit install. This thread is only about flash and how to install it.

Thanks Kilz.

Flash is NOT enabled. If you see evidence of the contrary please let me know what to do to make it noticeable in my browser.

Please ignore other than Flash issues - I copied all the gobbledygook I saw in the terminal without any discretion on my part as I don't anderstand a word it says...

Cheers,

Udi

---

### Post by Kilz on 2008-08-17
> **Udibuntu said:**
> Thanks Kilz.

Flash is NOT enabled. If you see evidence of the contrary please let me know what to do to make it noticeable in my browser.

Please ignore other than Flash issues - I copied all the gobbledygook I saw in the terminal without any discretion on my part as I don't anderstand a word it says...

Cheers,

Udi

What command did you use after I gave you the information [in post 264]("http://ubuntuforums.org/showpost.php?p=5587028&postcount=264") to try and enable flash.

---

### Post by Udibuntu on 2008-08-18
> **Kilz said:**
> What command did you use after I gave you the information [in post 264]("http://ubuntuforums.org/showpost.php?p=5587028&postcount=264") to try and enable flash.

None.

I didn't even get to finding the right path to FF3 plugin folder.

I just ran *firefox * from the terminal.

Anyway, Flash does not work on my system.

Udi

---

### Post by Udibuntu on 2008-08-19
Bump.

Need help getting Flash to work on FF3 gotten from Mozilla, Feisty 64bit.

Previously installed r48 (as well as other plugins) don't work.

Removed, re-installed, nada.

The main clue is that FF3 doesnt find the plugin after install, as FF3 did not come from the repo's.

This means I need to link them myself. Problem is Nautilus can't find any files or folders related to FF3, exept the tar file I extracted and installed from...

Wierd stuff. Any help will be appreciated as I'm about to give up and remove FF3 (not an easy feat when I can't find any mark that it's installed...)

:frown:

---

### Post by Yellow Pasque on 2008-08-19
Udibu.. What does this return?:
```
which firefox
```

---

### Post by Kilz on 2008-08-19
> **Udibuntu said:**
> Bump.

Need help getting Flash to work on FF3 gotten from Mozilla, Feisty 64bit.

Previously installed r48 (as well as other plugins) don't work.

Removed, re-installed, nada.

The main clue is that FF3 doesnt find the plugin after install, as FF3 did not come from the repo's.

This means I need to link them myself. Problem is Nautilus can't find any files or folders related to FF3, exept the tar file I extracted and installed from...

Wierd stuff. Any help will be appreciated as I'm about to give up and remove FF3 (not an easy feat when I can't find any mark that it's installed...)

:frown:

We need the path to the place you placed firefox 3. I gave you a command in post 264 of this thread that requires that path. Without it I can not help you, odds are no one can. Since you manually installed Firefox 3 there is no way we can get its path except from you.

---

### Post by Udibuntu on 2008-08-19
> **Kilz said:**
> We need the path to the place you placed firefox 3. I gave you a command in post 264 of this thread that requires that path. Without it I can not help you, odds are no one can. Since you manually installed Firefox 3 there is no way we can get its path except from you.

Understood.

I tried to search nautilus for "firefox-", "firefox-3" and found nothing except the tar.bz file I downloaded from Mozilla.

Please provide me with idiot proof steps to find what we are looking for - commands I should copy and paste, walkthroughs etc.

I have no knowledge in either terminal use, unix or linux, but I can copy and paste like a champ :)

BTW, I ccan't uninstall FF3 becayse I can't find it anywhere in add/remove menu...

Thanks,

Udi

---

### Post by Yellow Pasque on 2008-08-19
[SIZE="4"]**Hello Udibuntu**[/SIZE]

I think you missed my post above since Kilz posted at the same time. Copy and paste this:
```
which firefox
```
This will give you the path to the default firefox binary (it looks to be FF3 from your previous posts)

---

### Post by oz_ollie on 2008-08-19
The updated Firefox 3.0.1 requires a different third line:
```
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0.1/plugins/

```

---

### Post by Yellow Pasque on 2008-08-19
> **oz_ollie said:**
> The updated Firefox 3.0.1 requires a different third line:
```
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0.1/plugins/

```

That link shouldn't be necessary, because /usr/lib/firefox-3.x.../plugins/ should just be a symlink to /usr/lib/firefox-addons/plugins/

It's kind of confusing, but that's the way mozilla devs seem to like it :lolflag:


EDIT: /me fires up Epiphany with webkit backend.

---

### Post by Udibuntu on 2008-08-20
> **Temüjin said:**
> [SIZE="4"]**Hello Udibuntu**[/SIZE]

I think you missed my post above since Kilz posted at the same time. Copy and paste this:
```
which firefox
```
This will give you the path to the default firefox binary (it looks to be FF3 from your previous posts)

Thanks Temujin, I did miss your post.

I get:

```
udi@udi-laptop:~$ which firefox
/usr/bin/firefox
```

AFAIK this is the default path, isn't it?

What should I do next?

---

### Post by Kilz on 2008-08-20
> **Udibuntu said:**
> 

AFAIK this is the default path, isn't it?

What should I do next?

Not really,  /usr/bin folder only contains the binbary, or a symlink to the binary. It isnt a path to the firefox3 folder. We need to find the firefox3 folder because thats where the plugins are.
This command will help us if its a symlink. 
```
ls -al /usr/local/bin/swift*
```

If on the other hand its a shell script to start firefox3 you will need attach it to a post here so we can look in it for the path.

---

### Post by Udibuntu on 2008-08-20
> **Kilz said:**
> Not really,  /usr/bin folder only contains the binbary, or a symlink to the binary. It isnt a path to the firefox3 folder. We need to find the firefox3 folder because thats where the plugins are.
This command will help us if its a symlink. 
```
ls -al /usr/local/bin/swift*
```

If on the other hand its a shell script to start firefox3 you will need attach it to a post here so we can look in it for the path.

```
udi@udi-laptop:~$ ls -al /usr/local/bin/swift*
ls: /usr/local/bin/swift*: No such file or directory
udi@udi-laptop:~$ 
```


> If on the other hand its a shell script to start firefox3 you will need attach it to a post here so we can look in it for the path

How do I find what you asked for in the "shell script" option?

Please guide me like you're guiding an old lady on how to land a fighter jet...

Thanks,

Udi

---

### Post by Kilz on 2008-08-20
> **Udibuntu said:**
> ```
udi@udi-laptop:~$ ls -al /usr/local/bin/swift*
ls: /usr/local/bin/swift*: No such file or directory
udi@udi-laptop:~$ 
```




How do I find what you asked for in the "shell script" option?

Please guide me like you're guiding an old lady on how to land a fighter jet...

Thanks,

Udi

Sorry, my error, try this command

```

ls -al /usr/bin/fire*
```

---

### Post by Udibuntu on 2008-08-21
> **Kilz said:**
> Sorry, my error, try this command

```

ls -al /usr/bin/fire*
```

```
udi@udi-laptop:~$ ls -al /usr/bin/fire*
lrwxrwxrwx 1 root root 20 2008-08-09 23:05 /usr/bin/firefox -> /opt/firefox/firefox
lrwxrwxrwx 1 root root 22 2008-08-19 21:17 /usr/bin/firefox.ubuntu -> ../lib/firefox/firefox
udi@udi-laptop:~$ 
```

The firefox.ubuntu reference is probably the install of FF2 I tried last night. It was completed but I can run only FF3...

I'm not giving up yet on FF3...

---

### Post by Kilz on 2008-08-21
> **Udibuntu said:**
> ```
udi@udi-laptop:~$ ls -al /usr/bin/fire*
lrwxrwxrwx 1 root root 20 2008-08-09 23:05 /usr/bin/firefox -> /opt/firefox/firefox
lrwxrwxrwx 1 root root 22 2008-08-19 21:17 /usr/bin/firefox.ubuntu -> ../lib/firefox/firefox
udi@udi-laptop:~$ 
```

The firefox.ubuntu reference is probably the install of FF2 I tried last night. It was completed but I can run only FF3...

I'm not giving up yet on FF3...

Good they are symlinks, what is the the results of 

```
ls -al /opt/firefox/plugins
```

---

### Post by Udibuntu on 2008-08-21
> **Kilz said:**
> Good they are symlinks, what is the the results of 

```
ls -al /opt/firefox/plugins
```


```
udi@udi-laptop:~$ ls -al /opt/firefox/plugins
lrwxrwxrwx 1 root root 24 2008-08-10 09:47 /opt/firefox/plugins -> /usr/lib/firefox/plugins
udi@udi-laptop:~$ 
```

---

### Post by Kilz on 2008-08-21
> **Udibuntu said:**
> ```
udi@udi-laptop:~$ ls -al /opt/firefox/plugins
lrwxrwxrwx 1 root root 24 2008-08-10 09:47 /opt/firefox/plugins -> /usr/lib/firefox/plugins
udi@udi-laptop:~$ 
```

That isnt the one where the plugins are, try 
```
ls -al /lib/firefox/plugins
```

if that doesnt bring up the list of plugins try

```
ls -al /usr/lib/mozilla/plugins
```


One other piece of info, you did say you downloaded the firefox3 from mozilla, right?

---

### Post by Udibuntu on 2008-08-21
> **Kilz said:**
> That isnt the one where the plugins are, try 
```
ls -al /lib/firefox/plugins
```

if that doesnt bring up the list of plugins try

```
ls -al /usr/lib/mozilla/plugins
```


One other piece of info, you did say you downloaded the firefox3 from mozilla, right?
```

udi@udi-laptop:~$ ls -al /lib/firefox/plugins
ls: /lib/firefox/plugins: No such file or directory
udi@udi-laptop:~$ ls -al /usr/lib/mozilla/plugins
total 1492
drwxr-xr-x 2 udi  users   4096 2008-08-19 21:02 .
drwxr-xr-x 3 root root    4096 2007-04-15 14:58 ..
lrwxrwxrwx 1 udi  users     36 2008-03-19 21:59 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 udi  users     37 2008-03-19 21:59 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 udi  users     34 2008-03-19 21:59 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 udi  users     35 2008-03-19 21:59 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 udi  users     36 2008-03-19 21:59 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 udi  users     37 2008-03-19 21:59 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 udi  users     42 2008-03-19 21:59 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 udi  users     43 2008-03-19 21:59 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 udi  users 118744 2008-03-12 00:08 libvlcplugin.so
-rw-r--r-- 1 udi  users 269216 2007-01-26 02:17 mplayerplug-in-dvx.so
-rw-r--r-- 1 udi  users    981 2007-01-26 02:17 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 udi  users 269408 2007-01-26 02:17 mplayerplug-in-qt.so
-rw-r--r-- 1 udi  users    981 2007-01-26 02:17 mplayerplug-in-qt.xpt
-rw-r--r-- 1 udi  users 269472 2007-01-26 02:17 mplayerplug-in-rm.so
-rw-r--r-- 1 udi  users    981 2007-01-26 02:17 mplayerplug-in-rm.xpt
-rw-r--r-- 1 udi  users 270648 2007-01-26 02:17 mplayerplug-in.so
-rw-r--r-- 1 udi  users 269760 2007-01-26 02:17 mplayerplug-in-wmp.so
-rw-r--r-- 1 udi  users    981 2007-01-26 02:17 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 udi  users    981 2007-01-26 02:17 mplayerplug-in.xpt
udi@udi-laptop:~$ 
```

Looks like the second shot was on target, right?

Yes, I downloaded it from Mozilla.

What next, Captain?

---

### Post by Kilz on 2008-08-21
[Click here,]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") download the file to your desktop. Open a terminal and enter in the following one at a time. Dont worry if the first two error saying they cant find a file, I just want to make sure they are deleted if they exist.

```
rm -r /usr/lib/firefox/plugins/npwrapper*
rm -r /usr/lib/mozilla/plugins/npwrapper*
cd ~/Desktop
tar -xzvf install_flash_player_9_linux.tar.gz install_flash_player_9_linux
sudo mv -f ~/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
```


Restart your browser.

---

### Post by thomman on 2008-08-21
I installed the script on a Hardy fresh install using scripts but flash want working. So I began reading through the post. And started doing what Kilz was saying one by one. The output is what follows maybe it will be of some help to others. 

First diagnostics:

**:~$ ls -al /usr/lib/mozilla//plugins/**

total 8
drwxr-xr-x 2 root root 4096 2008-04-11 22:25 .
drwxr-xr-x 4 root root 4096 2008-07-02 15:27 ..

**:~$ ls -al /usr/lib/firefox/plugins/**

total 8
drwxr-xr-x 2 root root 4096 2008-04-11 23:09 .
drwxr-xr-x 4 root root 4096 2008-08-21 08:46 ..
thomman@thomman:~$ uname -a
Linux thomman 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

**:~$ ls -al /usr/lib/firefox-addons/plugins**
total 12
drwxr-xr-x 2 root root 4096 2008-08-21 13:16 .
drwxr-xr-x 5 root root 4096 2008-07-02 15:25 ..
lrwxrwxrwx 1 root root   60 2008-08-21 13:16 [COLOR="Red"]npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
[/COLOR]

Seeing the red npwrapper I did the following as instructed.

**:~$ sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so**

I was asked to redo the two steps on page 1 if firefox again did not load flash. And since flash wouldn't work still I again redid the whole procedure on page 2 as instructed

I got an error for the following which I didnt get on my previous install

**:~$ sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins/**

ln: target `/usr/lib/firefox-3.0/plugins/' is not a directory: No such file or directory

I checked and found that the directory was firefox-3.0.1 and not firefox-3.0 so I applied the folowing in leiu and now the plugin works like a dream. Thanks Kilz!

**:~$ sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0.1/plugins/**

Hope this helps someone!

---

### Post by Udibuntu on 2008-08-23
> **Kilz said:**
> [Click here,]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") download the file to your desktop. Open a terminal and enter in the following one at a time. Dont worry if the first two error saying they cant find a file, I just want to make sure they are deleted if they exist.

```
rm -r /usr/lib/firefox/plugins/npwrapper*
rm -r /usr/lib/mozilla/plugins/npwrapper*
cd ~/Desktop
tar -xzvf install_flash_player_9_linux.tar.gz install_flash_player_9_linux
sudo mv -f ~/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
```


Restart your browser.

I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! 

Flash works, BTW :lolflag:

You are the greatest Kilz!!!!!

What did you do to make it work? what can I learn for future use?

THANK YOU!

Udi

---

### Post by Kilz on 2008-08-23
> **Udibuntu said:**
> I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! I LOVE YOU!!! 

Flash works, BTW :lolflag:

You are the greatest Kilz!!!!!

What did you do to make it work? what can I learn for future use?

THANK YOU!

Udi

Your welcome What you did was finish installing a 32bit application (firefox and flash) All the other plugins need to be 32bit also if you need them.

What you can learn is the commands

rm  - remove - never ever try and delete anything without a path to it, never use wildcards except to finish off words.

mv - move or copy - you can move files around.

sudo lets you do things like root.

You can also have [this great link]("http://www.ss64.com/bash/") that gives all the commands and little explanations.

---

### Post by miceagol on 2008-08-23
> **NagasakiJones said:**
> Hi, I've installed "flashplugin-nonfree" but I get no sound. I've been at this all day yesterday trying to fix this. I tried most every proposed fix in the forums but to no avail. I've tried so many things (except installing gnash or swfdec) my memory's a haze.

After installing flashplugin-nonfree with no fix, I followed Common Issues - Sound and installed the ia32-also-oss package, still no fix. Then I followed the thread recommended and tried installing "lib32cap1_1.10-14build1_amd64.deb" but when I do I get a "Failed to install", it says "trying to overwrite '/lib32/libcap.so.1.10', which is also in package ia32-libs". And I already have "libflashsupport(svn20080217)".

I have an AMD64, fresh install on new partition of Hardy, using the default Firefox 3.05b. I have installed all the multimedia codecs and they work no problem, including downloaded flvs. Also what I think may be significant is that I'm using an M-Audio Revolution 5.1 sound card via the digital out/sPDIF. In the Sound Preferences I have "IEC1724 IEC958" selected for all possible options that offer it, as all other options do not play sound. Default Mixer Tracks device is set to "M Audio Revolution-5.1 (Alsa Mixer)" but I've also tried "playback:ALSA PCM on front:0 (IEC1724) via DMA (Pulse Audio Mixer)". 

I'll be extremely grateful for anyone who can help me out here! If any other information's needed, just tell me what to provide. And I'm a newbie here so you can assume I don't know too much - because I don't.

I have the same problem as you. I get sound with everything but flash on an M-audio Revolution 5.1 using the digital output. How do I get Pulse Audio to use this output?

---

### Post by Udibuntu on 2008-08-23
> **Kilz said:**
> Your welcome What you did was finish installing a 32bit application (firefox and flash) All the other plugins need to be 32bit also if you need them.

What you can learn is the commands

rm  - remove - never ever try and delete anything without a path to it, never use wildcards except to finish off words.

mv - move or copy - you can move files around.

sudo lets you do things like root.

You can also have [this great link]("http://www.ss64.com/bash/") that gives all the commands and little explanations.

Uhm..does that mean my FF3 is 32bit?

---

### Post by Kilz on 2008-08-23
> **Udibuntu said:**
> Uhm..does that mean my FF3 is 32bit?

Yes, the firefox downloaded from Mozilla is 32bit. This made it easy to install flash, it works without a wrapper. If you want a 64bit installable version try [swiftweasel]("http://swiftweasel.tuxfamily.org/"). It is an optimized build of firefox.

---

### Post by Udibuntu on 2008-08-24
> **Kilz said:**
> Yes, the firefox downloaded from Mozilla is 32bit. This made it easy to install flash, it works without a wrapper. If you want a 64bit installable version try [swiftweasel]("http://swiftweasel.tuxfamily.org/"). It is an optimized build of firefox.

I wasn't aware of that. Had I known it was 32bit app I would have said something, sorry. 

I've tried to install SW in the past but it didn't go well, don't remember why.

I'll give it another shot (right after I solve a Google Earth crash problem).

Cheers Kilz, I appreciate your time and effort in helping me out here. I know you are a busy person and yet you answered all my questions and invested work in solving this issue.

You are a true model of the open source spirit, and helped me not to lose my faith in it...

Yours with respect,

Udi
Israel

---

### Post by Cope57 on 2008-08-24
[Using Adobe Flash and other 32-bit applications on 64-bit Linux]("http://www.linux.com/feature/142075")
"There is both Gnash and Swfdec as free solutions."
So for people who *need* Adobe's flash, this is the solution.

I use swfdec myself, and can view and play flash videos from youtube and games with sound having no issues.
For java, I use openjdk.

---

### Post by grossaffe on 2008-08-27
> **Cope57 said:**
> [Using Adobe Flash and other 32-bit applications on 64-bit Linux]("http://www.linux.com/feature/142075")
"There is both Gnash and Swfdec as free solutions."
So for people who *need* Adobe's flash, this is the solution.

I use swfdec myself, and can view and play flash videos from youtube and games with sound having no issues.
For java, I use openjdk.

What if I already have Swfdec installed and I need to replace it with Adobe?  the instructions in that link show you how to remove gnash, but not swfdec.

---

### Post by chadb88 on 2008-08-27
> **Kilz said:**
> [Click here,]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") download the file to your desktop. Open a terminal and enter in the following one at a time. Dont worry if the first two error saying they cant find a file, I just want to make sure they are deleted if they exist.

```
rm -r /usr/lib/firefox/plugins/npwrapper*
rm -r /usr/lib/mozilla/plugins/npwrapper*
cd ~/Desktop
tar -xzvf install_flash_player_9_linux.tar.gz install_flash_player_9_linux
sudo mv -f ~/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
```


Restart your browser.

I tried everything that was listed in the first post and in this one and I just get these error messages ```
chad@chad-desktop:~$ apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
chad@chad-desktop:~$ neo1
bash: neo1: command not found
chad@chad-desktop:~$ apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
chad@chad-desktop:~$ rm -r /usr/lib/firefox/plugins/npwrapper*
rm: cannot remove `/usr/lib/firefox/plugins/npwrapper*': No such file or directory
chad@chad-desktop:~$ rm -r /usr/lib/mozilla/plugins/npwrapper*
rm: cannot remove `/usr/lib/mozilla/plugins/npwrapper*': No such file or directory
chad@chad-desktop:~$ cd ~/Desktop
chad@chad-desktop:~/Desktop$ tar -xzvf install_flash_player_9_linux.tar.gz install_flash_player_9_linux
tar: install_flash_player_9_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: install_flash_player_9_linux: Not found in archive
tar: Error exit delayed from previous errors
chad@chad-desktop:~/Desktop$ mv -f ~/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
mv: cannot move `/home/chad/Desktop/install_flash_player_9_linux/libflashplayer.so' to `/usr/lib/firefox/plugins/': Not a directory

```

sorry, I just installed ubuntu for the first time today. very very very new to all this

---

### Post by Kilz on 2008-08-27
> **chadb88 said:**
> I tried everything that was listed in the first post and in this one and I just get these error messages ```
chad@chad-desktop:~$ apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
```
This command has sudo in front of it in the howto, you left it off.

> **chadb88 said:**
> ```
chad@chad-desktop:~$ cd ~/Desktop
chad@chad-desktop:~/Desktop$ tar -xzvf install_flash_player_9_linux.tar.gz install_flash_player_9_linux
tar: install_flash_player_9_linux.tar.gz: Cannot open: No such file or directory

```

sorry, I just installed ubuntu for the first time today. very very very new to all this

What version of Ubuntu did you install?

---

### Post by Kilz on 2008-08-27
> **grossaffe said:**
> What if I already have Swfdec installed and I need to replace it with Adobe?  the instructions in that link show you how to remove gnash, but not swfdec.

```
sudo apt-get purge swfdec-mozilla
```
This should do it, but I am not sure if any files would be left in the plugins folder.

Just in case anyone needs it, the following will remove gnash
```
sudo apt-get purge mozilla-plugin-gnash
```

Both Gnash and swfdec show promise, but they are not perfect and may not work on all sites. The adobe plugin is great for those who do not have concerns over the licensing.

---

### Post by grossaffe on 2008-08-27
> **Kilz said:**
> ```
sudo apt-get purge swfdec-mozilla
```
This should do it, but I am not sure if any files would be left in the plugins folder.

Just in case anyone needs it, the following will remove gnash
```
sudo apt-get purge mozilla-plugin-gnash
```

Both Gnash and swfdec show promise, but they are not perfect and may not work on all sites. The adobe plugin is great for those who do not have concerns over the licensing.

thanks.  and yeah, swfdec shows real promise, but being a student, there are some flash things (online homework) that swfdec just can't do yet.  In the future I'd like to be able to rid myself of adobe, but until then...

---

### Post by causeitsme on 2008-08-28
For anyone interested, I've been so frustrated with the lack of video for ages now, I had followed the instructions in the OP and and many of the recommendations by posters in this thread. I then did all kinds of things I found around the net. I was at the point that I was gonna do a fresh install and start over. (That would've meant a lot of work to get everything back up and running properly and what not)

I then decided to first try to uninstall firefox, so I went to Synaptic and checked Firefox 3 for complete removal. (I backed up my passwords and bookmarks first). Then reinstalled Firefox 3 and BAM! Everything works, some other things also started working that I didn't even know I were missing, such as little thumbnails on articles and such on some of the websites I visit. 

Anyway, sorry for being so long-winded, but, it worked for me.:guitar:

---

### Post by Harksaw on 2008-08-31
I followed the instructions in the first post and have flash working well, but some websites tell me I need 9.0.45 and about:plugins says I have 9.0 r31.

Is there any way to get the newer version?

---

### Post by Kilz on 2008-08-31
> **Harksaw said:**
> I followed the instructions in the first post and have flash working well, but some websites tell me I need 9.0.45 and about:plugins says I have 9.0 r31.

Is there any way to get the newer version?

Its the one in the repositories. There is no easy way to install it. You could download it from Adobe, execute the following.

```
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/*
```

Copy the new one to /usr/lib/firefox-addons/ then run

```
sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so

```
 Then restart the browser.

---

### Post by DarkGob on 2008-08-31
So, just upgraded from Gutsy to Hardy, upgraded from Firefox 2.something to 3.0.1 (downloaded from Mozilla and before the upgrade to Hardy), and I've gone from being able to view Flash to not being able to view Flash. I've done some fiddling per this thread but so far nothing. Details:

```
chris@chris-desktop:~$ ls -al /usr/lib/mozilla//plugins/
total 1452
drwxr-xr-x 2 chris users   4096 2008-08-31 21:33 .
drwxr-xr-x 4 root  root    4096 2008-08-31 13:55 ..
-rw-r--r-- 1 chris users 282704 2007-03-29 02:49 mplayerplug-in-dvx.so
-rwxr-xr-x 1 chris users   1021 2007-03-29 02:49 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 chris users 282704 2007-03-29 02:49 mplayerplug-in-qt.so
-rwxr-xr-x 1 chris users   1021 2007-03-29 02:49 mplayerplug-in-qt.xpt
-rw-r--r-- 1 chris users 282704 2007-03-29 02:49 mplayerplug-in-rm.so
-rwxr-xr-x 1 chris users   1021 2007-03-29 02:49 mplayerplug-in-rm.xpt
-rw-r--r-- 1 chris users 282704 2007-03-29 02:49 mplayerplug-in.so
-rw-r--r-- 1 chris users 282704 2007-03-29 02:49 mplayerplug-in-wmp.so
-rwxr-xr-x 1 chris users   1021 2007-03-29 02:49 mplayerplug-in-wmp.xpt
-rwxr-xr-x 1 chris users   1021 2007-03-29 02:49 mplayerplug-in.xpt
lrwxrwxrwx 1 chris users     49 2007-08-14 10:57 nphelix.so -> /home/chris/Desktop/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 chris users     50 2007-08-14 10:57 nphelix.xpt -> /home/chris/Desktop/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 chris users     60 2008-02-17 00:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

```
chris@chris-desktop:~$ ls -al /usr/lib/firefox/plugins/
total 16
drwxr-xr-x 3 chris users 4096 2008-08-31 21:33 .
drwxr-xr-x 4 root  root  4096 2008-08-31 13:57 ..
lrwxrwxrwx 1 chris users   49 2007-08-14 10:57 nphelix.so -> /home/chris/Desktop/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 chris users   50 2007-08-14 10:57 nphelix.xpt -> /home/chris/Desktop/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 chris users   60 2008-02-17 00:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
drwxr-xr-x 2 chris users 4096 2007-06-06 18:39 quarantine

```

**about:plugins**
[quote=]Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes[/quote]

Ideas?

---

### Post by Kilz on 2008-09-01
> **DarkGob said:**
> So, just upgraded from Gutsy to Hardy, upgraded from Firefox 2.something to 3.0.1 (downloaded from Mozilla and before the upgrade to Hardy), and I've gone from being able to view Flash to not being able to view Flash. I've done some fiddling per this thread but so far nothing. Details:



Ideas?


This says flash is installed.

```
about:plugins
Quote:
Shockwave Flash

File name: npwrapper.libflashplayer.so
Shockwave Flash 9.0 r124

MIME Type Description Suffixes Enabled
application/x-shockwave-flash Shockwave Flash swf Yes
application/futuresplash FutureSplash Player spl Yes 
```

Exactly what have you done to try and get flash working?

---

### Post by kjb34 on 2008-09-01
I just installed the 64 Hardy and tried to use the recommendation at the beginning of the thread nothing happened. But when I did the update voila Flash worked.

---

### Post by Kilz on 2008-09-01
> **kjb34 said:**
> I just installed the 64 Hardy and tried to use the recommendation at the beginning of the thread nothing happened. But when I did the update voila Flash worked.

Did you restart your browser after doing the commands?

---

### Post by kjb34 on 2008-09-01
Nah I didn't. :oops: That might be why it didn't work.

---

### Post by Harksaw on 2008-09-01
> **Kilz said:**
>  then run

```
sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so

```
 Then restart the browser.

Running this command, it tells me "/usr/lib/firefox-addons/plugins/libflashplayer.so is not a valid NPAPI plugin"



I downloaded the tar.gz file from [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) , the one that was labeled "Adobe Flash Player version 9.0.124.0 .tar.gz for Linux (x86)"  and extracted libflashplayer.so into the directory you said. . . Am I not downloading the right file?

---

### Post by Kilz on 2008-09-01
> **Harksaw said:**
> Running this command, it tells me "/usr/lib/firefox-addons/plugins/libflashplayer.so is not a valid NPAPI plugin"



I downloaded the tar.gz file from [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) , the one that was labeled "Adobe Flash Player version 9.0.124.0 .tar.gz for Linux (x86)"  and extracted libflashplayer.so into the directory you said. . . Am I not downloading the right file?

It is, make sure it exists.

---

### Post by DarkGob on 2008-09-01
> **Kilz said:**
> This says flash is installed.

Exactly what have you done to try and get flash working?

Well, I guess it was just the instructions from the original post (just the ones for Hardy). Restarted my browser. I think I had another Flash plugin that I got rid of but I can't remember what it was called.

Extra information, I suppose, is that I just get a gray box, instead of a "missing plugin" dialog. Should I try the Flash 10 Beta?

---

### Post by Kilz on 2008-09-01
> **DarkGob said:**
> Well, I guess it was just the instructions from the original post (just the ones for Hardy). Restarted my browser. I think I had another Flash plugin that I got rid of but I can't remember what it was called.

Extra information, I suppose, is that I just get a gray box, instead of a "missing plugin" dialog. Should I try the Flash 10 Beta?

Did you do the clean out commands as well as the install ones?

---

### Post by DarkGob on 2008-09-01
> **Kilz said:**
> Did you do the clean out commands as well as the install ones?

Yes, those as well.

---

### Post by Kilz on 2008-09-01
> **DarkGob said:**
> Yes, those as well.

I just went back and tok a look at your first post in an attempt to get more info. [In post 308 ]("http://ubuntuforums.org/showpost.php?p=5703245&postcount=308") you tell me that you upgraded from firefox 2 to 3.0.1 with a package from Mozilla. Please click on help, then About Firefox. Near the bottom of that window is a string that starts with Mozilla/5.0. Please copy and paste the whole thing into a reply.

---

### Post by DarkGob on 2008-09-01
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

---

### Post by Kilz on 2008-09-02
> **DarkGob said:**
> Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

Thats good, looks like the Upgrade replaced the 32bit version. What is in firefox addons? Also how many tabs do you have open?

```
ls -al /usr/lib/firefox-addons/plugins
```

---

### Post by DarkGob on 2008-09-02
```
chris@chris-desktop:~$ ls -al /usr/lib/firefox-addons/plugins
total 12
drwxr-xr-x 2 root root 4096 2008-08-31 21:22 .
drwxr-xr-x 5 root root 4096 2008-08-31 13:57 ..
lrwxrwxrwx 1 root root   60 2008-08-31 21:22 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

Flash is nonfunctional independent of the number of tabs I have open.

---

### Post by Kilz on 2008-09-02
> **DarkGob said:**
> ```
chris@chris-desktop:~$ ls -al /usr/lib/firefox-addons/plugins
total 12
drwxr-xr-x 2 root root 4096 2008-08-31 21:22 .
drwxr-xr-x 5 root root 4096 2008-08-31 13:57 ..
lrwxrwxrwx 1 root root   60 2008-08-31 21:22 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

Flash is nonfunctional independent of the number of tabs I have open.

The problem we are running into is this. The grey box you describe is most often the result of conflicting flash plugins. But by looking in the most common locations I dont see any other plugins.
Please make sure the /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so file exists. Can you also search for libflashplayer.so and see where it is located?

---

### Post by DarkGob on 2008-09-02
```
chris@chris-desktop:~$ ls -al /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
-rwxr-xr-x 1 chris users 70120 2008-02-17 00:15 /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```
So it does exist.

npwrapper.libflashplayer.so is located in /usr/lib/nspluginwrapper/plugins.

---

### Post by Kilz on 2008-09-02
> **DarkGob said:**
> ```
chris@chris-desktop:~$ ls -al /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
-rwxr-xr-x 1 chris users 70120 2008-02-17 00:15 /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```
So it does exist.

npwrapper.libflashplayer.so is located in /usr/lib/nspluginwrapper/plugins.

Great, now where exactly is libflashplayer.so, the file it wrapps located. Just to be clear, libflashplayer.so, not npwrapper.libflashplayer.so. Please do a search of the file system.

---

### Post by DarkGob on 2008-09-02
... #-o

For some reason, when I ran the line ```
sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns

``` it didn't actually install flashplugin-nonfree. I installed it and everything's working now.

:oops:

---

### Post by KTK on 2008-09-07
I had the same problem and stumbled across this looking for help.

Great post! Really informative; solved the problem and clarified the situation.

Thanks a lot.

---

### Post by Dr Noam on 2008-09-08
After many hours, asking advice, trawling through several pages of this long thread, and several attempts using the instructions in the first post I've succeeded! NO flash related stuff worked before at all, now it all seems fine. The difference was: _Removing gnash_ before following the instructions. Perhaps that could be added to the tips on the first page?
Thanks, Kilz :)

---

### Post by alexcuervo on 2008-09-08
For Ubuntu 64 bit users there is a 2 click installer for the latest Flash 10 RC at [http://www.queleimporta.com/how-to-install-flash-10-rc-on-ubuntu-64-bits-with-2-clicks/en/](http://www.queleimporta.com/how-to-install-flash-10-rc-on-ubuntu-64-bits-with-2-clicks/en/)

---

### Post by Kilz on 2008-09-08
> **Dr Noam said:**
> After many hours, asking advice, trawling through several pages of this long thread, and several attempts using the instructions in the first post I've succeeded! NO flash related stuff worked before at all, now it all seems fine. The difference was: _Removing gnash_ before following the instructions. Perhaps that could be added to the tips on the first page?
Thanks, Kilz :)
Thats a good idea, I just added the command.

> **alexcuervo said:**
> For Ubuntu 64 bit users there is a 2 click installer for the latest Flash 10 RC at 

I dont recommend installing scripts from someone new. That command they ask you to copy and paste in includes a download and a script. Scripts can install alll kinds of things, some of them no good.

---

### Post by swimstarguy on 2008-09-10
I can't get it to work.
I've tried a number of different ways but flashplayer still isn't quite working.
The player comes up blank. There's no grey box either so I'm not havng that problem.

I ran the code to clear out previous installs but that didn't work.
It worked before I upgraded to Hardy.

> david@Patton:~$ ls -al /usr/lib/mozilla//plugins/
total 7952
drwxr-xr-x 2 david users    4096 2008-09-07 14:14 .
drwxr-xr-x 4 root  root     4096 2008-09-04 01:56 ..
lrwxrwxrwx 1 root  root       37 2008-09-07 14:14 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rwxr-xr-x 1 david users 8115888 2008-03-24 21:02 libflashplayer.so
lrwxrwxrwx 1 david users      60 2008-09-03 22:03 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
david@Patton:~$ ls -al /usr/lib/firefox/plugins
total 12
drwxr-xr-x 2 david users 4096 2008-09-07 14:14 .
drwxr-xr-x 5 root  root  4096 2008-09-04 01:58 ..
lrwxrwxrwx 1 root  root    37 2008-09-07 14:14 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 david users   60 2008-09-03 22:03 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
david@Patton:~$ uname -a
Linux Patton 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
david@Patton:~$ 



~Zar4

---

### Post by Kilz on 2008-09-11
> **swimstarguy said:**
> I can't get it to work.
I've tried a number of different ways but flashplayer still isn't quite working.
The player comes up blank. There's no grey box either so I'm not havng that problem.

I ran the code to clear out previous installs but that didn't work.
It worked before I upgraded to Hardy.




~Zar4

The problem could be the fact that you have tried a number of ways. Each may have left files in place. First lets just clean out everything. Do the following commands one at a time. If some of them say a file or package doesnt exist its ok we want to make sure its gone if it does.

```
sudo rm /usr/lib/mozilla/plugins/flashplugin-alternative.so 
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm /usr/lib/firefox/plugins/flashplugin-alternative.so
sudo rm /usr/lib/firefox/npwrapper.libflashplayer.so
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
```

Then redo the install commands'

```
sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0.1/plugins/
```

---

### Post by Joh_ on 2008-09-13
I have to admit I haven't read through all pages (34 pages were a bit too many) so I have no idea if anybody else has experienced this, but I didn't find it on launchpad.

I'm running Hardy Heron, newly installed and followed the instructions for the very same. I *technically* can run flash, but it doesn't work quite well in practice. All movies on youtube for example freeze every 2 seconds. Skipping ahead a bit plays the movie for 2 seconds, then it freezes again. Regular flash movies (such as [badgerbadgerbadger.com](http://badgerbadgerbadger.com/)) works fine during the loading screen, but as soon as the actual "movie" is about to start they freeze too.

I tried changing to the flash 10 beta, hoping it would be fixed but it's the same thing there so I'm assuming it's some issue with nspluginwrapper rather than flash itself. Any ideas?

```
$ ls -lA /usr/lib/nspluginwrapper/plugins/
total 84
-rwxr-xr-x 1 root root 78248 2008-09-13 16:56 npwrapper.libflashplayer.so

$ ls -lA /usr/lib/firefox-addons/plugins/
total 9656
-rwxrwxr-x 1 johan johan 9864208 2008-08-08 06:59 libflashplayer.so
lrwxrwxrwx 1 root  root       60 2008-09-13 16:42 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

$ ls -lA /usr/lib/firefox-3.0.1/plugins
lrwxrwxrwx 1 root root 25 2008-09-08 18:38 /usr/lib/firefox-3.0.1/plugins -> ../firefox-addons/plugins
```

---

### Post by Kilz on 2008-09-13
> **Joh_ said:**
> I have to admit I haven't read through all pages (34 pages were a bit too many) so I have no idea if anybody else has experienced this, but I didn't find it on launchpad.

I'm running Hardy Heron, newly installed and followed the instructions for the very same. I *technically* can run flash, but it doesn't work quite well in practice. All movies on youtube for example freeze every 2 seconds. Skipping ahead a bit plays the movie for 2 seconds, then it freezes again. Regular flash movies (such as [badgerbadgerbadger.com](http://badgerbadgerbadger.com/)) works fine during the loading screen, but as soon as the actual "movie" is about to start they freeze too.

I tried changing to the flash 10 beta, hoping it would be fixed but it's the same thing there so I'm assuming it's some issue with nspluginwrapper rather than flash itself. Any ideas?

```
$ ls -lA /usr/lib/nspluginwrapper/plugins/
total 84
-rwxr-xr-x 1 root root 78248 2008-09-13 16:56 npwrapper.libflashplayer.so

$ ls -lA /usr/lib/firefox-addons/plugins/
total 9656
-rwxrwxr-x 1 johan johan 9864208 2008-08-08 06:59 libflashplayer.so
lrwxrwxrwx 1 root  root       60 2008-09-13 16:42 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

$ ls -lA /usr/lib/firefox-3.0.1/plugins
lrwxrwxrwx 1 root root 25 2008-09-08 18:38 /usr/lib/firefox-3.0.1/plugins -> ../firefox-addons/plugins
```

What is the url to the bug report you filed?

---

### Post by Joh_ on 2008-09-13
> **Kilz said:**
> What is the url to the bug report you filed?
I didn't file one yet since I was hoping someone else would've encountered the same thing I did and hopefully had a fix. Seems I'm out of luck. I'll file one tomorrow (it's 4 am atm and I'm heading for bed.) :P

---

### Post by dodtsair on 2008-09-14
Flash is not working, when I got to youtube then I see a grey box.

Commands I ran to try to get it to work, plus some informative commands

Lmpower@dodtsair:~$ uname -a
Linux dodtsair 2.6.24-19-xen #1 SMP Wed Aug 20 21:08:51 UTC 2008 x86_64 GNU/Linux

mpower@dodtsair:~$ ls usr/lib/mozilla/plugins/ /usr/lib/firefox/plugins/ /usr/lib/firefox/ /usr/lib/nspluginwrapper /usr/lib/firefox-addons/plugins/ /usr/lib/nspluginwrapper/plugins/ /usr/lib/firefox-addons/plugins/ /usr/lib/firefox-3.0.1/plugins/
ls: cannot access usr/lib/mozilla/plugins/: No such file or directory
ls: cannot access /usr/lib/firefox/plugins/: No such file or directory
ls: cannot access /usr/lib/nspluginwrapper: No such file or directory
ls: cannot access /usr/lib/nspluginwrapper/plugins/: No such file or directory
/usr/lib/firefox/:
extensions

/usr/lib/firefox-3.0.1/plugins/:

/usr/lib/firefox-addons/plugins/:

/usr/lib/firefox-addons/plugins/:

mpower@dodtsair:~$ sudo rm /usr/lib/mozilla/plugins/flashplugin-alternative.so 
rm: cannot remove `/usr/lib/mozilla/plugins/flashplugin-alternative.so': No such file or directory
mpower@dodtsair:~$ sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
rm: cannot remove `/usr/lib/mozilla/plugins/libflashplayer.so': No such file or directory
mpower@dodtsair:~$ sudo rm /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
rm: cannot remove `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': No such file or directory
mpower@dodtsair:~$ sudo rm /usr/lib/firefox/plugins/flashplugin-alternative.so
rm: cannot remove `/usr/lib/firefox/plugins/flashplugin-alternative.so': No such file or directory
mpower@dodtsair:~$ sudo rm /usr/lib/firefox/npwrapper.libflashplayer.so
rm: cannot remove `/usr/lib/firefox/npwrapper.libflashplayer.so': No such file or directory
mpower@dodtsair:~$ sudo apt-get -y purge nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32ncurses5 classpath-gtkpeer ia32-libs libnm-util0
  libboost-date-time1.34.1 classpath-common lib32gcc1 lib32asound2 dhcdbd
  libboost-thread1.34.1 libnl1 cacao libraptor1 lib32z1 libapt-pkg-perl
  liblist-moreutils-perl lib32stdc++6 classpath libconfig-file-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mpower@dodtsair:~$ sudo apt-get -y purge mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32ncurses5 classpath-gtkpeer ia32-libs libnm-util0
  libboost-date-time1.34.1 classpath-common lib32gcc1 lib32asound2 dhcdbd
  libboost-thread1.34.1 libnl1 cacao libraptor1 lib32z1 libapt-pkg-perl
  liblist-moreutils-perl lib32stdc++6 classpath libconfig-file-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mpower@dodtsair:~$ sudo apt-get -y purge swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32ncurses5 classpath-gtkpeer ia32-libs libnm-util0
  libboost-date-time1.34.1 classpath-common lib32gcc1 lib32asound2 dhcdbd
  libboost-thread1.34.1 libnl1 cacao libraptor1 lib32z1 libapt-pkg-perl
  liblist-moreutils-perl lib32stdc++6 classpath libconfig-file-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mpower@dodtsair:~$ sudo apt-get -y purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32ncurses5 classpath-gtkpeer ia32-libs libnm-util0
  libboost-date-time1.34.1 classpath-common lib32gcc1 lib32asound2 dhcdbd
  libboost-thread1.34.1 libnl1 cacao libraptor1 lib32z1 libapt-pkg-perl
  liblist-moreutils-perl lib32stdc++6 classpath libconfig-file-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mpower@dodtsair:~$ sudo rm -rfd /usr/lib/nspluginwrapper
mpower@dodtsair:~$ sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so

mpower@dodtsair:~$ sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
Reading package lists... Done
...
Flash Plugin installed.


**#Here is what is important**
**#/usr/lib/nspluginwrapper/plugins/: has no contents**

mpower@dodtsair:~$ ls usr/lib/mozilla/plugins/ /usr/lib/firefox/plugins/ /usr/lib/firefox/ /usr/lib/nspluginwrapper /usr/lib/firefox-addons/plugins/ /usr/lib/nspluginwrapper/plugins/ /usr/lib/firefox-addons/plugins/ /usr/lib/firefox-3.0.1/plugins/
ls: cannot access usr/lib/mozilla/plugins/: No such file or directory
/usr/lib/firefox/:
extensions  plugins

/usr/lib/firefox-3.0.1/plugins/:

/usr/lib/firefox-addons/plugins/:

/usr/lib/firefox-addons/plugins/:

/usr/lib/firefox/plugins/:
flashplugin-alternative.so

/usr/lib/nspluginwrapper:
i386  noarch  plugins  x86_64

/usr/lib/nspluginwrapper/plugins/:

#I do not see how these link commands can succeed considering there is no source to link from.

mpower@dodtsair:~$ sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
mpower@dodtsair:~$ sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0.1/plugins/


mpower@dodtsair:~$ ls usr/lib/mozilla/plugins/ /usr/lib/firefox/plugins/ /usr/lib/firefox/ /usr/lib/nspluginwrapper /usr/lib/firefox-addons/plugins/ /usr/lib/nspluginwrapper/plugins/ /usr/lib/firefox-addons/plugins/ /usr/lib/firefox-3.0.1/plugins/ -l
ls: cannot access usr/lib/mozilla/plugins/: No such file or directory
/usr/lib/firefox/:
total 0
drwxr-xr-x 2 root root 30 2008-08-25 22:21 extensions
drwxr-xr-x 2 root root 39 2008-09-13 21:13 plugins

/usr/lib/firefox-3.0.1/plugins/:
total 0
lrwxrwxrwx 1 root root 60 2008-09-13 21:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

/usr/lib/firefox-addons/plugins/:
total 0
lrwxrwxrwx 1 root root 60 2008-09-13 21:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

/usr/lib/firefox-addons/plugins/:
total 0
lrwxrwxrwx 1 root root 60 2008-09-13 21:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

/usr/lib/firefox/plugins/:
total 0
lrwxrwxrwx 1 root root 37 2008-09-13 21:13 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin

/usr/lib/nspluginwrapper:
total 0
drwxr-xr-x 3 root root 18 2008-09-13 21:12 i386
drwxr-xr-x 2 root root 37 2008-09-13 21:12 noarch
drwxr-xr-x 2 root root  6 2008-04-11 10:39 plugins
drwxr-xr-x 3 root root 18 2008-09-13 21:12 x86_64

/usr/lib/nspluginwrapper/plugins/:
total 0

#This leaves me with three broken links in /usr/lib/firefox-3.0.1/plugins/:
#/usr/lib/firefox-addons/plugins/:
# and in /usr/lib/firefox-addons/plugins/:

Was this the intended out come of your scripts or should I have some file named npwrapper.libflashplayer.so in /usr/lib/nspluginwrapper/plugins/?

Mike Power

---

### Post by dodtsair on 2008-09-14
Fixed at least for now
mpower@dodtsair:~/Desktop/install_flash_player_9_linux$ sudo ln -sf /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so /usr/lib/nspluginwrapper/plugins/

mpower@dodtsair:~/Desktop/install_flash_player_9_linux$ ls /usr/lib/nspluginwrapper/plugins/ -l
total 0
lrwxrwxrwx 1 root root 56 2008-09-13 21:35 npwrapper.libflashplayer.so -> /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

This gives me working flash from one Firefox run to another.

---

### Post by Fr@nKy on 2008-09-15
I have a question... How is Flash 10 RC working under 64-bit? I mean does the current Hardy version of nspluginwrapper works with it? If not... What is needed to work? 

This is probably the only reason I don't go 64-bit on the next install :(

---

### Post by Kilz on 2008-09-15
> **Fr@nKy said:**
>  I mean does the current Hardy version of nspluginwrapper works with it? 

Yes.

---

### Post by Nikos.Alexandris on 2008-09-16
> **dodtsair said:**
> Flash is not working, when I got to youtube then I see a grey box.

Commands I ran to try to get it to work, plus some informative commands

Lmpower@dodtsair:~$ uname -a
Linux dodtsair 2.6.24-19-xen #1 SMP Wed Aug 20 21:08:51 UTC 2008 x86_64 GNU/Linux

mpower@dodtsair:~$ ls usr/lib/mozilla/plugins/ /usr/lib/firefox/plugins/ /usr/lib/firefox/ /usr/lib/nspluginwrapper /usr/lib/firefox-addons/plugins/ /usr/lib/nspluginwrapper/plugins/ /usr/lib/firefox-addons/plugins/ /usr/lib/firefox-3.0.1/plugins/
ls: cannot access usr/lib/mozilla/plugins/: No such file or directory
ls: cannot access /usr/lib/firefox/plugins/: No such file or directory
ls: cannot access /usr/lib/nspluginwrapper: No such file or directory
ls: cannot access /usr/lib/nspluginwrapper/plugins/: No such file or directory
/usr/lib/firefox/:
extensions

/usr/lib/firefox-3.0.1/plugins/:

/usr/lib/firefox-addons/plugins/:

/usr/lib/firefox-addons/plugins/:

mpower@dodtsair:~$ sudo rm /usr/lib/mozilla/plugins/flashplugin-alternative.so 
rm: cannot remove `/usr/lib/mozilla/plugins/flashplugin-alternative.so': No such file or directory
mpower@dodtsair:~$ sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
rm: cannot remove `/usr/lib/mozilla/plugins/libflashplayer.so': No such file or directory
mpower@dodtsair:~$ sudo rm /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
rm: cannot remove `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': No such file or directory
mpower@dodtsair:~$ sudo rm /usr/lib/firefox/plugins/flashplugin-alternative.so
rm: cannot remove `/usr/lib/firefox/plugins/flashplugin-alternative.so': No such file or directory
mpower@dodtsair:~$ sudo rm /usr/lib/firefox/npwrapper.libflashplayer.so
rm: cannot remove `/usr/lib/firefox/npwrapper.libflashplayer.so': No such file or directory
mpower@dodtsair:~$ sudo apt-get -y purge nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32ncurses5 classpath-gtkpeer ia32-libs libnm-util0
  libboost-date-time1.34.1 classpath-common lib32gcc1 lib32asound2 dhcdbd
  libboost-thread1.34.1 libnl1 cacao libraptor1 lib32z1 libapt-pkg-perl
  liblist-moreutils-perl lib32stdc++6 classpath libconfig-file-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mpower@dodtsair:~$ sudo apt-get -y purge mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32ncurses5 classpath-gtkpeer ia32-libs libnm-util0
  libboost-date-time1.34.1 classpath-common lib32gcc1 lib32asound2 dhcdbd
  libboost-thread1.34.1 libnl1 cacao libraptor1 lib32z1 libapt-pkg-perl
  liblist-moreutils-perl lib32stdc++6 classpath libconfig-file-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mpower@dodtsair:~$ sudo apt-get -y purge swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32ncurses5 classpath-gtkpeer ia32-libs libnm-util0
  libboost-date-time1.34.1 classpath-common lib32gcc1 lib32asound2 dhcdbd
  libboost-thread1.34.1 libnl1 cacao libraptor1 lib32z1 libapt-pkg-perl
  liblist-moreutils-perl lib32stdc++6 classpath libconfig-file-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mpower@dodtsair:~$ sudo apt-get -y purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32ncurses5 classpath-gtkpeer ia32-libs libnm-util0
  libboost-date-time1.34.1 classpath-common lib32gcc1 lib32asound2 dhcdbd
  libboost-thread1.34.1 libnl1 cacao libraptor1 lib32z1 libapt-pkg-perl
  liblist-moreutils-perl lib32stdc++6 classpath libconfig-file-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mpower@dodtsair:~$ sudo rm -rfd /usr/lib/nspluginwrapper
mpower@dodtsair:~$ sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so

mpower@dodtsair:~$ sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
Reading package lists... Done
...
Flash Plugin installed.


**#Here is what is important**
**#/usr/lib/nspluginwrapper/plugins/: has no contents**

mpower@dodtsair:~$ ls usr/lib/mozilla/plugins/ /usr/lib/firefox/plugins/ /usr/lib/firefox/ /usr/lib/nspluginwrapper /usr/lib/firefox-addons/plugins/ /usr/lib/nspluginwrapper/plugins/ /usr/lib/firefox-addons/plugins/ /usr/lib/firefox-3.0.1/plugins/
ls: cannot access usr/lib/mozilla/plugins/: No such file or directory
/usr/lib/firefox/:
extensions  plugins

/usr/lib/firefox-3.0.1/plugins/:

/usr/lib/firefox-addons/plugins/:

/usr/lib/firefox-addons/plugins/:

/usr/lib/firefox/plugins/:
flashplugin-alternative.so

/usr/lib/nspluginwrapper:
i386  noarch  plugins  x86_64

/usr/lib/nspluginwrapper/plugins/:

#I do not see how these link commands can succeed considering there is no source to link from.

mpower@dodtsair:~$ sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
mpower@dodtsair:~$ sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0.1/plugins/


mpower@dodtsair:~$ ls usr/lib/mozilla/plugins/ /usr/lib/firefox/plugins/ /usr/lib/firefox/ /usr/lib/nspluginwrapper /usr/lib/firefox-addons/plugins/ /usr/lib/nspluginwrapper/plugins/ /usr/lib/firefox-addons/plugins/ /usr/lib/firefox-3.0.1/plugins/ -l
ls: cannot access usr/lib/mozilla/plugins/: No such file or directory
/usr/lib/firefox/:
total 0
drwxr-xr-x 2 root root 30 2008-08-25 22:21 extensions
drwxr-xr-x 2 root root 39 2008-09-13 21:13 plugins

/usr/lib/firefox-3.0.1/plugins/:
total 0
lrwxrwxrwx 1 root root 60 2008-09-13 21:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

/usr/lib/firefox-addons/plugins/:
total 0
lrwxrwxrwx 1 root root 60 2008-09-13 21:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

/usr/lib/firefox-addons/plugins/:
total 0
lrwxrwxrwx 1 root root 60 2008-09-13 21:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

/usr/lib/firefox/plugins/:
total 0
lrwxrwxrwx 1 root root 37 2008-09-13 21:13 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin

/usr/lib/nspluginwrapper:
total 0
drwxr-xr-x 3 root root 18 2008-09-13 21:12 i386
drwxr-xr-x 2 root root 37 2008-09-13 21:12 noarch
drwxr-xr-x 2 root root  6 2008-04-11 10:39 plugins
drwxr-xr-x 3 root root 18 2008-09-13 21:12 x86_64

/usr/lib/nspluginwrapper/plugins/:
total 0

#This leaves me with three broken links in /usr/lib/firefox-3.0.1/plugins/:
#/usr/lib/firefox-addons/plugins/:
# and in /usr/lib/firefox-addons/plugins/:

Was this the intended out come of your scripts or should I have some file named npwrapper.libflashplayer.so in /usr/lib/nspluginwrapper/plugins/?

Mike Power

The same for me on Linux vertical 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

Cheers, Nikos

---

### Post by Nikos.Alexandris on 2008-09-16
> **dodtsair said:**
> Fixed at least for now
mpower@dodtsair:~/Desktop/install_flash_player_9_linux$ sudo ln -sf /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so /usr/lib/nspluginwrapper/plugins/

mpower@dodtsair:~/Desktop/install_flash_player_9_linux$ ls /usr/lib/nspluginwrapper/plugins/ -l
total 0
lrwxrwxrwx 1 root root 56 2008-09-13 21:35 npwrapper.libflashplayer.so -> /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

This gives me working flash from one Firefox run to another.

This does not work (either) for me :-(

---

### Post by Kilz on 2008-09-16
> **Nikos.Alexandris said:**
> This does not work (either) for me :-(

If you are running Ubuntu, Kubutnu, or Xubuntu I suggest reading the first post specifically the How to get help section. If you are running some other linux distro you may want to go to its forums or documentation. The uname string you gave does not look like one from Ubuntu.

---

### Post by Nikos.Alexandris on 2008-09-16
> **Kilz said:**
> If you are running Ubuntu, Kubutnu, or Xubuntu I suggest reading the first post specifically the How to get help section. If you are running some other linux distro you may want to go to its forums or documentation. The uname string you gave does not look like one from Ubuntu.

Thank you for your reply Kilz. I' ve allready read the instructions and the "how to get help" section, not carefully though. I'll have a look.

Cheers, Nikos

FYI:
nik@vertical:~$ lsb_release -rd
Description:	Ubuntu 8.04.1
Release:	8.04

---

### Post by Nikos.Alexandris on 2008-09-16
I' ve been trying for a while to get flash working (with firefox) and I always face the same "...get latest Flash..." message in youtube for example. The strange thing is that flash works correctly with epiphany-browser (which I use currently!).

( Bug report in lauchnpad: [https://bugs.launchpad.net/ubuntu/+bug/270868](https://bugs.launchpad.net/ubuntu/+bug/270868) )

nik@vertical:~$ uname -a
Linux vertical 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux


nik@vertical:~$ lsb_release -rd
Description:	Ubuntu 8.04.1
Release:	8.04


nik@vertical:~$ ls -al /usr/lib/mozilla/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-09-16 13:19 .
drwxr-xr-x 4 root root 4096 2008-05-05 18:42 ..
lrwxrwxrwx 1 root root   37 2008-09-16 13:19 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   42 2008-06-17 19:34 nphelix.so -> /usr/local/realplayer11/mozilla/nphelix.so
lrwxrwxrwx 1 root root   43 2008-06-17 19:34 nphelix.xpt -> /usr/local/realplayer11/mozilla/nphelix.xpt


nik@vertical:~$ ls -al /usr/lib/firefox-addons/plugins
total 12
drwxr-xr-x 2 root root 4096 2008-09-16 13:22 .
drwxr-xr-x 5 root root 4096 2008-09-15 12:49 ..
lrwxrwxrwx 1 root root   42 2008-06-17 20:36 nphelix.so -> /usr/local/realplayer11/mozilla/nphelix.so
lrwxrwxrwx 1 root root   43 2008-06-17 20:36 nphelix.xpt -> /usr/local/realplayer11/mozilla/nphelix.xpt
lrwxrwxrwx 1 root root   60 2008-09-16 13:22 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so


nik@vertical:~$ ls -l /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 root root 56 2008-09-16 13:31 /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so -> /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so


nik@vertical:~$ ls /var/lib/flashplugin-nonfree/ -l
total 84
-rwxr-xr-x 1 nik nik 78248 2008-09-16 13:19 npwrapper.libflashplayer.so

...
Thank you, Nikos

---

### Post by Kilz on 2008-09-16
> **Nikos.Alexandris said:**
> I' ve been trying for a while to get flash working (with firefox) and I always face the same "...get latest Flash..." message in youtube for example. The strange thing is that flash works correctly with epiphany-browser (which I use currently!).

Details below:



You forgot the link to the bug report on launchpad.

---

### Post by Nikos.Alexandris on 2008-09-16
I think the following is also important!


nik@vertical:~$  ls -l /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 root root 56 2008-09-16 13:31 /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so -> /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

---

### Post by Nikos.Alexandris on 2008-09-16
OK, I've edited post #343

Thank your for time and efforts. Nikos

---

### Post by Kilz on 2008-09-16
> **Nikos.Alexandris said:**
> OK, I've edited post #343

Thank your for time and efforts. Nikos

Did you upgrade the install from a previous Ubuntu install or was it a clean install?

---

### Post by Nikos.Alexandris on 2008-09-16
> **Kilz said:**
> Did you upgrade the install from a previous Ubuntu install or was it a clean install?

Initially I've upgraded but then I performed a clean install.

---

### Post by Kilz on 2008-09-16
> **Nikos.Alexandris said:**
> Initially I've upgraded but then I performed a clean install.

On the bug report you stated that

"I tried in adittion once to install the official adobe package."

How did you install it and to what location.

---

### Post by Nikos.Alexandris on 2008-09-16
> **Kilz said:**
> On the bug report you stated that

"I tried in adittion once to install the official adobe package."

How did you install it and to what location.

Sorry for time-crunching :-)

I clicked on Get the latest Flash player. (link provided in youtube's website after not being able to see a video), then it goes to "http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash", then I downloaded the version "Adobe Flash Player version 9.0.124.0.tar.gz".

After that... (I copy paste from my history):

2613  cd /usr/local
 2614  ls
 2615  mkdir flash
 2616  sudo mkdir flash
 2617  cd flash/
 2618  sudo mv /home/nik/Incoming/install_flash_player_9_linux.tar.gz .
 2619  ls
 2620  tar xzvf install_flash_player_9_linux.tar.gz 
#need root permissions here, so...
 2621  sudo tar xzvf install_flash_player_9_linux.tar.gz 
 2622  ls
 2623  ls -l
 2624  cd install_flash_player_9_linux/
 2625  ls
 2626  ls -l
 2627  ./flashplayer-installer 
 2628  sudo ./flashplayer-installer 

#checked if it works but no success here either. So I removed it...

 2629  cd ..
 2630  sudo rm -rf flash/
 2631  exit

---

### Post by Kilz on 2008-09-16
First clean out the old installed files.

```
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
```

Then purge the installed packages. I have a feeling that you installed swfdec at one time because this file 

flashplugin-alternative.so 

is part of swfdec. It is a conflicting flash plugin.

```
sudo apt-get -y purge swfdec-mozilla
```

You might as well also purge the other possible conflicting plugins.

```
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge flashplugin-nonfree
```

Then try and reinstall flash.

```
sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0.1/plugins/
```

---

### Post by Nikos.Alexandris on 2008-09-16
Step-by-Step:
```
nik@vertical:~$ sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
[sudo] password for nik: 
nik@vertical:~$ sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
nik@vertical:~$ sudo rm -f /usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so

```

Removing as suggested
```
nik@vertical:~$ sudo apt-get -y purge swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

nik@vertical:~$ sudo apt-get -y purge swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

nik@vertical:~$ sudo apt-get -y purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 168kB disk space will be freed.
(Reading database ... 309040 files and directories currently installed.)
Removing flashplugin-nonfree ...
Purging configuration files for flashplugin-nonfree ...
```

Installing...
```
nik@vertical:~$ sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nspluginwrapper is already the newest version.
lib32nss-mdns is already the newest version.
Suggested packages:
  konqueror-nsplugins libflashsupport ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 309029 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--15:27:06--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 84.53.166.70
Connecting to fpdownload.macromedia.com|84.53.166.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  932.50 KB/s

[...]

 2950K .......... .......... ...                             100%    1.25 MB/s

15:27:08 (1.62 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.
Flash Plugin installed.
```

Checking...
```
nik@vertical:~$ ls -l /usr/lib/nspluginwrapper/plugins/
total 0
```

**Why is the /usr/lib/nspluginwrapper/plugins/ directory empty?** Following linking actions create "dead links". Searching for the desired file:
```

nik@vertical:/$ sudo updatedb

nik@vertical:/$ locate npwrapper.libflashplayer.so
/home/nik/.mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

```

All created links lead to /usr/lib/nspluginwrapper/
```
nik@vertical:/$ ls -l /home/nik/.mozilla/plugins
total 0
lrwxrwxrwx 1 root root 60 2008-09-16 13:30 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

nik@vertical:/$ ls -l /usr/lib/firefox/plugins/
total 8
lrwxrwxrwx 1 root root 37 2008-09-16 15:27 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root 64 2008-09-15 12:45 libjavaplugin_oji.so -> /usr/local/java/jre1.6.0_07/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root 42 2008-06-17 19:34 nphelix.so -> /usr/local/realplayer11/mozilla/nphelix.so
lrwxrwxrwx 1 root root 43 2008-06-17 19:34 nphelix.xpt -> /usr/local/realplayer11/mozilla/nphelix.xpt
lrwxrwxrwx 1 root root 60 2008-09-15 13:32 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

nik@vertical:/$ ls -l /usr/lib/iceweasel/plugins/
total 4
lrwxrwxrwx 1 root root 39 2008-09-16 15:27 flashplugin-alternative.so -> /etc/alternatives/iceweasel-flashplugin
lrwxrwxrwx 1 root root 60 2008-09-15 13:32 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

Only under /var/lib/flashplugin-nonfree/ is the file to be found!
```
nik@vertical:/$ ls -l /var/lib/flashplugin-nonfree/
total 84
-rwxr-xr-x 1 root root 78248 2008-09-16 15:27 npwrapper.libflashplayer.so

```

# Linking to /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
```
sudo ln -sf /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so /usr/lib/firefox-3.0.1/plugins/
```

Checking with firefox a youtube video fails again :-(

---

### Post by Kilz on 2008-09-16
While some of the information is useful, most isnt.
You are going to have to remove flashplugin-alternative.so in the folders you just added to this post that you didnt include before. What would be helpful is the results of 
```

ls -al /usr/lib/mozilla/plugins/
ls -al /usr/lib/firefox-addons/plugins

```
to see where the libflashplayer.so file is located. Just to be clear, we are not looking for npwrapper.libflashplayer.so but libflashplayer.so.

---

### Post by Nikos.Alexandris on 2008-09-16
Looking for libflashplayer.so
```
nik@vertical:~$ locate libflashplayer.so
/home/nik/.mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib32/ia32-flashplugin-nonfree/libflashplayer.so
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
```

and for flashplugin-alternative.so
```

nik@vertical:~$ locate flashplugin-alternative.so
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
/usr/lib32/firefox/plugins/ia32-flashplugin-alternative.so
/usr/lib32/iceape/plugins/ia32-flashplugin-alternative.so
/usr/lib32/iceweasel/plugins/ia32-flashplugin-alternative.so
/usr/lib32/midbrowser/plugins/ia32-flashplugin-alternative.so
/usr/lib32/mozilla/plugins/ia32-flashplugin-alternative.so
/usr/lib32/xulrunner/plugins/ia32-flashplugin-alternative.so
```

[COLOR="Red"]Should all (or at least from mozilla & firefox) *flashplugin-alternative.so's* be removed?[/COLOR]

More useful info:
```
nik@vertical:~$ ls -al /usr/lib/mozilla/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-09-16 15:27 .
drwxr-xr-x 4 root root 4096 2008-05-05 18:42 ..
lrwxrwxrwx 1 root root   37 2008-09-16 15:27 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   42 2008-06-17 19:34 nphelix.so -> /usr/local/realplayer11/mozilla/nphelix.so
lrwxrwxrwx 1 root root   43 2008-06-17 19:34 nphelix.xpt -> /usr/local/realplayer11/mozilla/nphelix.xpt

nik@vertical:~$ ls -al /usr/lib/firefox-addons/plugins
total 8
drwxr-xr-x 2 root root 4096 2008-09-16 15:36 .
drwxr-xr-x 5 root root 4096 2008-09-15 12:49 ..
lrwxrwxrwx 1 root root   42 2008-06-17 20:36 nphelix.so -> /usr/local/realplayer11/mozilla/nphelix.so
lrwxrwxrwx 1 root root   43 2008-06-17 20:36 nphelix.xpt -> /usr/local/realplayer11/mozilla/nphelix.xpt
lrwxrwxrwx 1 root root   56 2008-09-16 15:36 npwrapper.libflashplayer.so -> /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
```

---

### Post by Kilz on 2008-09-16
Try this first

```
sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0.1/plugins/
```
Then restart the browser.
It should create the wrapped plugin at /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so.

---

### Post by Nikos.Alexandris on 2008-09-16
So I did but it still doesn't work.

```
nik@vertical:~$ ls -la /usr/lib/nspluginwrapper/plugins/
total 92
drwxr-xr-x 2 root root  4096 2008-09-16 18:15 .
drwxr-xr-x 6 root root  4096 2008-09-16 18:11 ..
-rwxr-xr-x 1 root root 78248 2008-09-16 18:15 npwrapper.libflashplayer.so

nik@vertical:~$ ls -la /usr/lib/firefox-addons/plugins/
total 12
drwxr-xr-x 2 root root 4096 2008-09-16 18:16 .
drwxr-xr-x 5 root root 4096 2008-09-15 12:49 ..
lrwxrwxrwx 1 root root   42 2008-06-17 20:36 nphelix.so -> /usr/local/realplayer11/mozilla/nphelix.so
lrwxrwxrwx 1 root root   43 2008-06-17 20:36 nphelix.xpt -> /usr/local/realplayer11/mozilla/nphelix.xpt
lrwxrwxrwx 1 root root   60 2008-09-16 18:16 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

nik@vertical:~$ ls -la /usr/lib/firefox-3.0.1/plugins/
total 12
drwxr-xr-x 2 root root 4096 2008-09-16 18:16 .
drwxr-xr-x 5 root root 4096 2008-09-15 12:49 ..
lrwxrwxrwx 1 root root   42 2008-06-17 20:36 nphelix.so -> /usr/local/realplayer11/mozilla/nphelix.so
lrwxrwxrwx 1 root root   43 2008-06-17 20:36 nphelix.xpt -> /usr/local/realplayer11/mozilla/nphelix.xpt
lrwxrwxrwx 1 root root   60 2008-09-16 18:16 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

Why does it work with epiphany?

---

### Post by Kilz on 2008-09-16
> **Nikos.Alexandris said:**
> So I did but it still doesn't work.

Why does it work with epiphany?

No idea. Its possible that epiphany is 32bit or some other reason. It should work now. You have the wrapper in place. Please open firefox, then click Help and then About firefox. Near the bottom of the little info indow is a string that starts with Mozilla/5.0. Please copy the string to a reply here.

---

### Post by Nikos.Alexandris on 2008-09-16
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

---

### Post by nss0000 on 2008-09-16
Nice work Big-K your wrapper_script did it again for me. I just WWW upgraded from fav x64-DD_6.06_LTS to x64-HH_8.04.1 on my AMD5400+ kit. 

Download took about 40-min and install another 30. Completely without issue. EXCEPT: 
1) PAN got wiped clean
2) no FLASH

But again, even I can follow your wrapper_install_script. Worked the 1st time! Fishing vids from U-Tube  splash across my LCD again. Many thanks.

BTW: Referenced "icons" smaller than a a quarter ( $0.25) cannot be seen by OWGs.

---

### Post by Kilz on 2008-09-16
> **Nikos.Alexandris said:**
> Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

When you type ```
about:plugins
``` into the address bar do you see a Shockwave flasn section? If so please copy it into a reply here.

---

### Post by Nikos.Alexandris on 2008-09-16
Sure, shockwave flasn section is present (attached a screenshot).

---

### Post by LadFromWales85 on 2008-09-17
Anyone have any ideas how to install the Flash 10 RC on Intrepid.
I had it working with Hardy but since the upgrade I can't get nspluginwrapper to install the plugin.  I am missing a couple of 32bit libs.

```

/usr/lib/nspluginwrapper/i386/linux$ ldd npviewer.bin | grep "not found"
libxcb-render-util.so.0 => not found
libxcb-render.so.0 => not found

```

```

/usr/lib/nspluginwrapper/i386/linux$ ls -l /usr/lib32 | grep xcb
lrwxrwxrwx 1 root root      15 2008-09-17 13:35 libxcb.so.1 -> libxcb.so.1.0.0
-rw-r--r-- 1 root root   95676 2008-06-13 10:41 libxcb.so.1.0.0
lrwxrwxrwx 1 root root      20 2008-09-17 13:35 libxcb-xlib.so.0 -> libxcb-xlib.so.0.0.0
-rw-r--r-- 1 root root    5364 2008-06-13 10:41 libxcb-xlib.so.0.0.0

```

Any idea where 32bit versions of these libraries can be located?

Thanks

EDIT: got them by running getlibs against npviewer.  Plugin is now installed and showing in about:plugins, but getting constant grey boxes :(  Restarting Firefox doesn't get it working.  Flashless for now!

---

### Post by irvken on 2008-09-18
New install of HH - I get

```
E: Couldn't find package nspluginwrapper
```

Has it been removed?

sources.list is

```
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

Maybe I'm missing something

---

### Post by Nikos.Alexandris on 2008-09-18
> **Nikos.Alexandris said:**
> Sure, shockwave flasn section is present (attached a screenshot).

Just tried with Opera 960 (64-bit) following instructions/workaround for flash at [1]:
 (1) It's too fast and (2) flashplayer works.

Why isn't it working on FFX3?

[1] [https://help.ubuntu.com/community/OperaBrowser#head-8b233e94ad0c1adc2f768dd1dd7c403b6f8ddd75](https://help.ubuntu.com/community/OperaBrowser#head-8b233e94ad0c1adc2f768dd1dd7c403b6f8ddd75)

---

### Post by Kilz on 2008-09-18
> **Nikos.Alexandris said:**
> Just tried with Opera 960 (64-bit) following instructions/workaround for flash at [1]:
 (1) It's too fast and (2) flashplayer works.

Why isn't it working on FFX3?

[1] [https://help.ubuntu.com/community/OperaBrowser#head-8b233e94ad0c1adc2f768dd1dd7c403b6f8ddd75](https://help.ubuntu.com/community/OperaBrowser#head-8b233e94ad0c1adc2f768dd1dd7c403b6f8ddd75)

At this point I am running out of ideas as to why its not working. It is listed in the ```
about:plugins
``` and we have created a wrapped plugin that should work. To my knowledge all conflicting packages have been removed. Perhaps the bug report will offer some insight that will help you.

---

### Post by Kilz on 2008-09-18
> **irvken said:**
> New install of HH - I get

```
E: Couldn't find package nspluginwrapper
```

Has it been removed?

sources.list is

```
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

Maybe I'm missing something

What are the results of ```
uname -a
```

---

### Post by Nikos.Alexandris on 2008-09-18
> **Kilz said:**
> At this point I am running out of ideas as to why its not working. It is listed in the ```
about:plugins
``` and we have created a wrapped plugin that should work. To my knowledge all conflicting packages have been removed. Perhaps the bug report will offer some insight that will help you.

I appreciate your time Kilz and co.
Thank you a lot, Nikos

---

### Post by opteron180 on 2008-09-18
Hi,
I suggest this topic should be sub divided because I need to read all 37 pages to make sure I do not double post.

Version:
[PHP]Linux Kze-Linux 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux[/PHP]

I think some users asked about the grey box issue, I think this is a similar issue. When I go to [http://usa.asus.com/index.aspx](http://usa.asus.com/index.aspx), the menus are displayed behind the ad. Please see attached. THis often happens: menu displayed behind the box. Should I try Flash10?

Thanks

---

### Post by Kilz on 2008-09-18
> **opteron180 said:**
> Hi,
I suggest this topic should be sub divided because I need to read all 37 pages to make sure I do not double post.

Version:
[PHP]Linux Kze-Linux 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux[/PHP]

I think some users asked about the grey box issue, I think this is a similar issue. When I go to [http://usa.asus.com/index.aspx](http://usa.asus.com/index.aspx), the menus are displayed behind the ad. Please see attached. THis often happens: menu displayed behind the box. Should I try Flash10?

Thanks

Flash 10 is nice, and solves the menu problem. But the newest versions of the beta require a lot of extra 32bit libraries that are not listed in the howto. 
The grey box issue happens a lot on multiple tabs.
If you had read the "How to get help" section (large bold red letters) of the howto you will see I dont suggest people read 37 pages. Just the last 2.
But the help mainly deals with install problems. If you have flash working some times, its installed.

---

### Post by Nikos.Alexandris on 2008-09-19
The following is from a 64-bit Ubuntu installation with a working flashplayer for FFX3. Now isn't this strange?

```
$ ls -al /usr/lib/mozilla/plugins/
total 1492
drwxr-xr-x 2 sara users   4096 2008-09-14 00:18 .
drwxr-xr-x 4 root root    4096 2008-06-09 03:47 ..
lrwxrwxrwx 1 root root      37 2008-09-14 00:18 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rw-r--r-- 1 root root  290880 2008-05-13 12:31 mplayerplug-in-dvx.so
-rw-r--r-- 1 root root    1067 2008-05-13 12:31 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root root  290880 2008-05-13 12:31 mplayerplug-in-qt.so
-rw-r--r-- 1 root root    1067 2008-05-13 12:31 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root  290880 2008-05-13 12:31 mplayerplug-in-rm.so
-rw-r--r-- 1 root root    1067 2008-05-13 12:31 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root  290872 2008-05-13 12:31 mplayerplug-in.so
-rw-r--r-- 1 root root  290880 2008-05-13 12:31 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root    1067 2008-05-13 12:31 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root    1067 2008-05-13 12:31 mplayerplug-in.xpt
lrwxrwxrwx 1 sara users     60 2008-02-13 20:02 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

$ ls -al /usr/lib/firefox-addons/plugins
total 12
drwxr-xr-x 2 root root 4096 2008-09-14 00:18 .
drwxr-xr-x 5 root root 4096 2008-09-14 00:23 ..
lrwxrwxrwx 1 root root   60 2008-09-14 00:18 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

The following is empty!
```
ls -la /usr/lib/nspluginwrapper/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-04-11 19:39 .
drwxr-xr-x 6 root root 4096 2008-09-14 00:18 ..

```

And here is the link to the wrapped flashplayer!!
```
$ ls -la /etc/alternatives/mozilla-flashplugin 
lrwxrwxrwx 1 root root 56 2008-09-14 00:18 /etc/alternatives/mozilla-flashplugin -> /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so


$ ls -la /var/lib/flashplugin-nonfree/
total 92
drwxr-xr-x  2 root root  4096 2008-09-14 00:18 .
drwxr-xr-x 58 root root  4096 2008-09-14 00:53 ..
-rwxr-xr-x  1 root root 78248 2008-09-14 00:18 npwrapper.libflashplayer.so

```

And libflashplayer.so of course...
```
$ ls -la /usr/lib/flashplugin-nonfree/
total 8016
drwxr-xr-x   2 root root    4096 2008-09-14 00:18 .
drwxr-xr-x 188 root root   69632 2008-09-16 20:50 ..
-rw-r--r--   1 root root 8115888 2008-09-14 00:18 libflashplayer.so
```


More info:

Firefox > Help > About:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

The **about: plugins** page shows correctly the Shockwave Flash section.

I'll try that on my machine later and report back if it works(!?)

Greetings, Nikos

---

### Post by fido777 on 2008-09-19
Like Kilz says, if you're having problems like gray boxes with Flash 10, make sure you let adobe know on their **[[COLOR="Blue"]feedback form[/COLOR]]("http://www.adobe.com/cfusion/mmform/index.cfm?name=fp_beta_feedback")**.  We need to make our voices heard.

---

### Post by Kilz on 2008-09-19
> **Nikos.Alexandris said:**
> The following is from a 64-bit Ubuntu installation with a working flashplayer for FFX3. Now isn't this strange?




More info:

Firefox > Help > About:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

The **about: plugins** page shows correctly the Shockwave Flash section.

I'll try that on my machine later and report back if it works(!?)

Greetings, Nikos

I walked you through wrapping the flash plugin and placing it in the plugin folder. Your browser shows the plugin installed. What you are showing changes none of that.

---

### Post by Nikos.Alexandris on 2008-09-19
> **Kilz said:**
> I walked you through wrapping the flash plugin and placing it in the plugin folder. Your browser shows the plugin installed. What you are showing changes none of that.

Kilz,
I am convinced you showed the correct way to go about it. I am just wondering (in my last post) why it works with an "alternative" link (namely the flashplugin-alternative.so).

---

### Post by Kilz on 2008-09-19
> **Nikos.Alexandris said:**
> Kilz,
I am convinced you showed the correct way to go about it. I am just wondering (in my last post) why it works with an "alternative" link (namely the flashplugin-alternative.so).

Its a symlink, it is wrapping the file through the symlink. But it is still wrapping the file. The symlink will refer to the flashplugin.so. But when we did it, we cut the symlink out. It should work for sure since we cut a symlink, that would make it easier not harder. [The original setup]("http://ubuntuforums.org/showpost.php?p=5798995&postcount=343") you had the same symlinks , it didnt work then. but please try it if you think it will work this time. I just dont think it will change anything.

---

### Post by Nikos.Alexandris on 2008-09-19
> **Kilz said:**
> Its a symlink, it is wrapping the file through the symlink. But it is still wrapping the file. The symlink will refer to the flashplugin.so. But when we did it, we cut the symlink out. It should work for sure since we cut a symlink, that would make it easier not harder. [The original setup]("http://ubuntuforums.org/showpost.php?p=5798995&postcount=343") you had the same symlinks , it didnt work then. but please try it if you think it will work this time. I just dont think it will change anything.

Yes, it's clear to me that the correct flashplugin.so is used/wrapped. Anyway, being no expert I am trying all possible stuff, even if they are just a waste of time... simply cause I don't know that they are a waste of time :-)

Just for the records: this last "alternative" link is from another system not mine. Once again thank you for your patience and the clarifications.

Nikos

---

### Post by Nikos.Alexandris on 2008-09-20
> **fido777 said:**
> Like Kilz says, if you're having problems like gray boxes with Flash 10, make sure you let adobe know on their **[[COLOR="Blue"]feedback form[/COLOR]]("http://www.adobe.com/cfusion/mmform/index.cfm?name=fp_beta_feedback")**.  We need to make our voices heard.

I've filled the form and submitted it just a minute ago (concerning flash player 9 of course). Hopefully I'll get a meaningful reply.

Greetings, Nikos

---

### Post by mgbridges on 2008-09-20
I followed the instructions in the first post of this thread and everything semed to run OK, but after restarting Firefox I'm still getting the "You must download and install the latest version of the Adobe Flash Player to view this content.

I'm running Firefox 3 on Gutsy. Details of the troubleshooting commands output below:

```
martin@Vetinari:~$ ls -al /usr/lib/mozilla/plugins/
total 7952
drwxr-xr-x 2 martin users    4096 2008-09-20 19:00 .
drwxr-xr-x 4 root   root     4096 2008-06-18 22:11 ..
-rwxr-xr-x 1 martin users 8115888 2008-03-25 15:02 libflashplayer.so
lrwxrwxrwx 1 martin users      36 2008-06-10 20:52 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 martin users      37 2008-06-10 20:52 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 martin users      34 2008-06-10 20:52 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 martin users      35 2008-06-10 20:52 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 martin users      36 2008-06-10 20:52 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 martin users      37 2008-06-10 20:52 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 martin users      42 2008-06-10 20:52 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 martin users      43 2008-06-10 20:52 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 martin users      60 2008-09-20 19:00 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
martin@Vetinari:~$ ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 martin users  4096 2008-09-20 19:00 .
drwxr-xr-x 5 root   root   4096 2008-07-18 23:21 ..
lrwxrwxrwx 1 martin users    36 2008-06-10 20:52 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 martin users    37 2008-06-10 20:52 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 martin users    34 2008-06-10 20:52 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 martin users    35 2008-06-10 20:52 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 martin users    36 2008-06-10 20:52 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 martin users    37 2008-06-10 20:52 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 martin users    42 2008-06-10 20:52 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 martin users    43 2008-06-10 20:52 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 martin users 11456 2008-07-16 05:35 libunixprintplugin.so
lrwxrwxrwx 1 martin users    60 2008-09-20 19:00 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
martin@Vetinari:~$ uname -a
Linux Vetinari 2.6.22-15-generic #1 SMP Wed Aug 20 15:47:07 UTC 2008 x86_64 GNU/Linux
```

Launchpad bug number is 272928.

Anyone got any ideas about what might be causing the problem?

Cheers,

Martin

---

### Post by Kilz on 2008-09-20
> **mgbridges said:**
> I followed the instructions in the first post of this thread and everything semed to run OK, but after restarting Firefox I'm still getting the "You must download and install the latest version of the Adobe Flash Player to view this content.

I'm running Firefox 3 on Gutsy. Details of the troubleshooting commands output below:

```
martin@Vetinari:~$ ls -al /usr/lib/mozilla/plugins/
total 7952
drwxr-xr-x 2 martin users    4096 2008-09-20 19:00 .
drwxr-xr-x 4 root   root     4096 2008-06-18 22:11 ..
-rwxr-xr-x 1 martin users 8115888 2008-03-25 15:02 libflashplayer.so
lrwxrwxrwx 1 martin users      36 2008-06-10 20:52 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 martin users      37 2008-06-10 20:52 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 martin users      34 2008-06-10 20:52 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 martin users      35 2008-06-10 20:52 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 martin users      36 2008-06-10 20:52 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 martin users      37 2008-06-10 20:52 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 martin users      42 2008-06-10 20:52 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 martin users      43 2008-06-10 20:52 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 martin users      60 2008-09-20 19:00 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
martin@Vetinari:~$ ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 martin users  4096 2008-09-20 19:00 .
drwxr-xr-x 5 root   root   4096 2008-07-18 23:21 ..
lrwxrwxrwx 1 martin users    36 2008-06-10 20:52 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 martin users    37 2008-06-10 20:52 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 martin users    34 2008-06-10 20:52 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 martin users    35 2008-06-10 20:52 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 martin users    36 2008-06-10 20:52 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 martin users    37 2008-06-10 20:52 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 martin users    42 2008-06-10 20:52 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 martin users    43 2008-06-10 20:52 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 martin users 11456 2008-07-16 05:35 libunixprintplugin.so
lrwxrwxrwx 1 martin users    60 2008-09-20 19:00 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
martin@Vetinari:~$ uname -a
Linux Vetinari 2.6.22-15-generic #1 SMP Wed Aug 20 15:47:07 UTC 2008 x86_64 GNU/Linux
```

Anyone got any ideas about what might be causing the problem?

Cheers,

Martin

I cant seem to find the link to your bug report.

---

### Post by blissfulpenguin on 2008-09-20
:thank you::KS:KS:KS:KS:KS:KS

---

### Post by malrost on 2008-09-21
I'm running Hardy (w/ Firefox 3.0.1). It was an upgrade from Gutsy, so I followed the clean out steps first. Now I'm getting the following dependency error at apt-get install:

```
The following packages have unmet dependencies:
nspluginwrapper: 
Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu4 is to be installed
Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed

```

I then tried apt-get install for both libgtk2.0-0 and libpango1.0-0, but get "is already the newest version." for both. Thinking it might be a repository or mirror server issue, I used Software Sources, ran "select best server" and chose that mirror. 

I've had this issue for a few days now, and at this point I'm not sure how to troubleshoot any further.


Here's my info:

```
beb@beb-sonata3:~$ ls -al /usr/lib/mozilla//plugins/
total 28
drwxr-xr-x 2 root root  4096 2008-09-21 13:11 .
drwxr-xr-x 4 root root  4096 2008-08-20 19:27 ..
lrwxrwxrwx 1 root root    26 2008-08-20 19:31 gxineplugin.so -> ../../gxine/gxineplugin.so
-rw-r--r-- 1 root root 19456 2007-01-05 14:52 libflash-mozplugin.so
lrwxrwxrwx 1 root root    39 2007-11-10 23:25 nphelix.so -> /home/beb/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 root root    40 2007-11-10 23:25 nphelix.xpt -> /home/beb/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 root root    31 2007-11-10 13:20 xineplugin.so -> ../../xine-plugin/xineplugin.so
beb@beb-sonata3:~$ ls -al /usr/lib/firefox/plugins
total 8
drwxr-xr-x 2 root root 4096 2008-09-21 13:11 .
drwxr-xr-x 4 root root 4096 2008-08-20 19:27 ..
lrwxrwxrwx 1 root root   39 2007-11-10 23:25 nphelix.so -> /home/beb/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 root root   40 2007-11-10 23:25 nphelix.xpt -> /home/beb/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 root root   31 2007-11-10 13:20 xineplugin.so -> ../../xine-plugin/xineplugin.so
beb@beb-sonata3:~$ uname -a
Linux beb-sonata3 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

```

---

### Post by ahuman on 2008-09-21
I tried the steps on the first page, but wasn't able to make the Flash install work. However, this worked for me:

I installed Flash using the link for Gusty-Hardy (Ubuntu 7.10 and Ubuntu 8.04 versions) users here: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924).

I also downgraded to Firefox 2 first by going to System/Synaptic Package Manager and searching Firefox-3. I deleted anything from the results with a green square next to it (aka anything installed). Then, I went to Add/Remove programs, searched for Firefox-2 and installed it. 

Thanks!
:guitar:

---

### Post by mgbridges on 2008-09-21
> **Kilz said:**
> I cant seem to find the link to your bug report.

Original post edited to add bug tracking reference.

Martin

---

### Post by Kilz on 2008-09-21
> **mgbridges said:**
> Original post edited to add bug tracking reference.

Martin

Try

```
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins
```

If it fails can you tell me if /usr/lib/firefox-3.0/plugins exists?

---

### Post by mgbridges on 2008-09-22
> **Kilz said:**
> Try

```
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins
```


This fails:
```
ln: creating symbolic link `/usr/lib/firefox-3.0/plugins' to `/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so': No such file or directory
```

> **Kilz said:**
> 
If it fails can you tell me if /usr/lib/firefox-3.0/plugins exists?

It does not. See below:
```
martin@Vetinari:~$ ls -a /usr/lib/firefox-3.0/plugins
ls: /usr/lib/firefox-3.0/plugins: No such file or directory
```

/usr/lib/firefox/plugins exists. In it there is a link called npwrapper.libflashplayer.so which links to /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

Any ideas?

Martin

---

### Post by Kilz on 2008-09-22
Martin
Can you tell me how you installed firefox 3 to Gutsy? Also can you tell me what other methods you used to install flash to firefox 3?

---

### Post by mgbridges on 2008-09-22
> **Kilz said:**
> Martin
Can you tell me how you installed firefox 3 to Gutsy? Also can you tell me what other methods you used to install flash to firefox 3?

It's been a while since I installed Firefox 3, so I can't clearly remember. However, there is a *firefox-3.0.tar.bz2* package in my Downloads directory so I suspect I installed it from that.

For your info, there is also a *firefox* folder hierarchy in the Downloads directory but it looks like this pre-dates the Firefox 3 install.

I have previously tried installing Flash player using the Adobe installers, but I don't think I've tried that since moving to Firefox 3.

Martin

---

### Post by Kilz on 2008-09-22
> **mgbridges said:**
> It's been a while since I installed Firefox 3, so I can't clearly remember. However, there is a *firefox-3.0.tar.bz2* package in my Downloads directory so I suspect I installed it from that.

For your info, there is also a *firefox* folder hierarchy in the Downloads directory but it looks like this pre-dates the Firefox 3 install.

I have previously tried installing Flash player using the Adobe installers, but I don't think I've tried that since moving to Firefox 3.

Martin

The thing is, if you downloaded a package from mozilla, extracted is and placed it I need to know where. Since you did it, we cant get it from anyone else but you. Without that info it will be impossible to get flash running. If you have a launcher or link on a menu you can get the path from it.
Second, its possible that its a 32bit Firefox 3. Please click Help , then About Firefox, near the bottom of the little window that will open is a string that starts with Mozilla/5.0. Copy and paste that string to a reply. That way we can tell what bit the browser is, and that way we can see what needs to be done to install plugins.

---

### Post by mgbridges on 2008-09-23
> **Kilz said:**
> The thing is, if you downloaded a package from mozilla, extracted is and placed it I need to know where. Since you did it, we cant get it from anyone else but you. Without that info it will be impossible to get flash running. If you have a launcher or link on a menu you can get the path from it.

The menu bar launcher links to /home/martin/Documents/Downloads/firefox/firefox

> **Kilz said:**
> Second, its possible that its a 32bit Firefox 3. Please click Help , then About Firefox, near the bottom of the little window that will open is a string that starts with Mozilla/5.0. Copy and paste that string to a reply. That way we can tell what bit the browser is, and that way we can see what needs to be done to install plugins.

String is: Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-GB; rv:1.9) Gecko/2008052912 Firefox/3.0

Hope that helps.

Martin

---

### Post by Kilz on 2008-09-23
> **mgbridges said:**
> The menu bar launcher links to /home/martin/Documents/Downloads/firefox/firefox



String is: Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-GB; rv:1.9) Gecko/2008052912 Firefox/3.0

Hope that helps.

Martin

It sure does, You have Firefox installed to your home folder and its 32bit.
```

ln -s /usr/lib/mozilla/plugins/libflashplayer.so /home/martin/Documents/Downloads/firefox/plugins
```

Should have flash working after a restart of the browser.

---

### Post by bobby_fabulous on 2008-09-24
Thanks mate instructions worked like a charm :)

---

### Post by mgbridges on 2008-09-25
> **Kilz said:**
> It sure does, You have Firefox installed to your home folder and its 32bit.
```

ln -s /usr/lib/mozilla/plugins/libflashplayer.so /home/martin/Documents/Downloads/firefox/plugins
```

Should have flash working after a restart of the browser.

Brilliant - that has sorted it! Thanks for your help.

Martin

---

### Post by MaindotC on 2008-09-25
> **malrost said:**
> I'm running Hardy (w/ Firefox 3.0.1). It was an upgrade from Gutsy, so I followed the clean out steps first. Now I'm getting the following dependency error at apt-get install:

```
The following packages have unmet dependencies:
nspluginwrapper: 
Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu4 is to be installed
Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed

```

I then tried apt-get install for both libgtk2.0-0 and libpango1.0-0, but get "is already the newest version." for both. Thinking it might be a repository or mirror server issue, I used Software Sources, ran "select best server" and chose that mirror. 

I've had this issue for a few days now, and at this point I'm not sure how to troubleshoot any further.


Here's my info:

```
beb@beb-sonata3:~$ ls -al /usr/lib/mozilla//plugins/
total 28
drwxr-xr-x 2 root root  4096 2008-09-21 13:11 .
drwxr-xr-x 4 root root  4096 2008-08-20 19:27 ..
lrwxrwxrwx 1 root root    26 2008-08-20 19:31 gxineplugin.so -> ../../gxine/gxineplugin.so
-rw-r--r-- 1 root root 19456 2007-01-05 14:52 libflash-mozplugin.so
lrwxrwxrwx 1 root root    39 2007-11-10 23:25 nphelix.so -> /home/beb/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 root root    40 2007-11-10 23:25 nphelix.xpt -> /home/beb/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 root root    31 2007-11-10 13:20 xineplugin.so -> ../../xine-plugin/xineplugin.so
beb@beb-sonata3:~$ ls -al /usr/lib/firefox/plugins
total 8
drwxr-xr-x 2 root root 4096 2008-09-21 13:11 .
drwxr-xr-x 4 root root 4096 2008-08-20 19:27 ..
lrwxrwxrwx 1 root root   39 2007-11-10 23:25 nphelix.so -> /home/beb/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 root root   40 2007-11-10 23:25 nphelix.xpt -> /home/beb/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 root root   31 2007-11-10 13:20 xineplugin.so -> ../../xine-plugin/xineplugin.so
beb@beb-sonata3:~$ uname -a
Linux beb-sonata3 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

```

Try using aptitude instead of apt.  I've run into this similar problem before about unmet dependencies, and if you try and trace back the dependencies it turns into a loop (you need this, which needs this, which needs this, which needs the first item in the list...)  I used aptitude instead of apt and it auto-resolved it for me.

---

### Post by MaindotC on 2008-09-25
I'm getting this problem:
```

amd64@amd64-desktop:~/Desktop/install_flash_player_10_linux$ sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
*** NSPlugin Viewer  *** ERROR: libnss3.so: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/firefox-addons/plugins/libflashplayer.so
amd64@amd64-desktop:~/Desktop/install_flash_player_10_linux$ ls /usr/lib/firefox-addons/plugins/
libflashplayer.so
amd64@amd64-desktop:~/Desktop/install_flash_player_10_linux$ locate libnss3.so
/usr/lib/libnss3.so
/usr/lib/libnss3.so.1d
amd64@amd64-desktop:~/Desktop/install_flash_player_10_linux$

```

I'll google it but I wanted to get a post out in case you knew right away what the problem is.

---

### Post by Kilz on 2008-09-25
> **strAlan said:**
> I'm getting this problem:
```

amd64@amd64-desktop:~/Desktop/install_flash_player_10_linux$ sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
*** NSPlugin Viewer  *** ERROR: libnss3.so: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/firefox-addons/plugins/libflashplayer.so
amd64@amd64-desktop:~/Desktop/install_flash_player_10_linux$ ls /usr/lib/firefox-addons/plugins/
libflashplayer.so
amd64@amd64-desktop:~/Desktop/install_flash_player_10_linux$ locate libnss3.so
/usr/lib/libnss3.so
/usr/lib/libnss3.so.1d
amd64@amd64-desktop:~/Desktop/install_flash_player_10_linux$

```

I'll google it but I wanted to get a post out in case you knew right away what the problem is.

Sure I know whats happening. [As I explained to you in this post]("http://ubuntuforums.org/showpost.php?p=5852822&postcount=8"), that sent you down this path. I do not recommend installing the newer versions of Flash 10 beta because of all the 32bit libraries that need to be manually coppied into place. You **[COLOR="Red"]cant [/COLOR]**just simply force in libraries, never, ever, ever force in library packages as they will overwrite 64bit libraries your system may need.
[Getlibs may help]("http://ubuntuforums.org/showthread.php?t=474790"), but be ready for a lot of them and even then it may not completely fix the issue. If you want to help your fellow 64bit users you might want to post a list back here of all the libraries you needed to install. I will add it to the top post and credit you for the list.
Also, and this is just a reminder and a warning to anyone who reads this post thinking they will be the next to try this and I will hold their hand. It is stated clearly and plainly I will not troubleshoot issues with the flash 10 beta. Stick to what you have at the present if you are not comfortable with manual installs and troubleshooting.

---

### Post by MaindotC on 2008-09-25
Hi, Kilz.  I know you did explain the copying of all the libraries and I didn't mean to ignore that - I thought it was simply a matter of doing it.  You said I'd have to put these lib32's in and I thought it was simply a matter of apt-getting them, not manually placing them.  I did find a resolution on [Flash's help site](http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=72&catid=675&threadid=1387868&enterthread=y) that I've yet to test but I'll keep you updated.  I apologize if I created extra work for you.  Thanks!

---

### Post by Kilz on 2008-09-25
> **strAlan said:**
> Hi, Kilz.  I know you did explain the copying of all the libraries and I didn't mean to ignore that - I thought it was simply a matter of doing it.  You said I'd have to put these lib32's in and I thought it was simply a matter of apt-getting them, not manually placing them.  I did find a resolution on [Flash's help site](http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=72&catid=675&threadid=1387868&enterthread=y) that I've yet to test but I'll keep you updated.  I apologize if I created extra work for you.  Thanks!

Not really extra work, but it isnt an easy task and I want those that feel they must try this to know exactly what to expect.

---

### Post by MaindotC on 2008-09-25
Have you tried [this tutorial](http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/)?  A lot of people on Twitter claimed that it got everything working and I was wondering how, if at all, it differs from your instructions.

---

### Post by Nikos.Alexandris on 2008-09-25
> **strAlan said:**
> Have you tried [this tutorial](http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/)?  A lot of people on Twitter claimed that it got everything working and I was wondering how, if at all, it differs from your instructions.

Does not work for me.

---

### Post by MarshyTheKid on 2008-09-25
```
$ ls -al /usr/lib/mozilla//plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-09-25 18:18 .
drwxr-xr-x 4 root root 4096 2008-04-22 11:11 ..
lrwxrwxrwx 1 root root   37 2008-09-25 18:18 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

```

```
$ ls -al /usr/lib/firefox/plugins/
total 20
drwxr-xr-x 2 root root  4096 2008-09-25 18:18 .
drwxr-xr-x 5 root root  4096 2008-09-25 17:49 ..
lrwxrwxrwx 1 root root    37 2008-09-25 18:18 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
-rw-r--r-- 1 root root 11456 2008-09-24 04:39 libunixprintplugin.so

```

I think flash stopped working when I updated to 3.0.2
Any suggestions?

---

### Post by MarshyTheKid on 2008-09-25
> **MarshyTheKid said:**
> ```
$ ls -al /usr/lib/mozilla//plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-09-25 18:18 .
drwxr-xr-x 4 root root 4096 2008-04-22 11:11 ..
lrwxrwxrwx 1 root root   37 2008-09-25 18:18 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

```

```
$ ls -al /usr/lib/firefox/plugins/
total 20
drwxr-xr-x 2 root root  4096 2008-09-25 18:18 .
drwxr-xr-x 5 root root  4096 2008-09-25 17:49 ..
lrwxrwxrwx 1 root root    37 2008-09-25 18:18 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
-rw-r--r-- 1 root root 11456 2008-09-24 04:39 libunixprintplugin.so

```

I think flash stopped working when I updated to 3.0.2
Any suggestions?

I reinstalled 3.0.1
How do I get it to work with 3.0.2?

---

### Post by Kilz on 2008-09-25
> **MarshyTheKid said:**
> I reinstalled 3.0.1
How do I get it to work with 3.0.2?

Please reread the first post in this thread, specifically the "how to get help" section. Read the very first line.

---

### Post by MarshyTheKid on 2008-09-26
> **Kilz said:**
> Please reread the first post in this thread, specifically the "how to get help" section. Read the very first line.
Yea, I did. I looked under flash and saw this
> If after installing the script you cant see flash. Make sure that all attempts at installing other flash plugins (Gnash, swfdec, etc) have been uninstalled and the files they created have been removed. The remains of past failed attempts are the #1 cause of flash not working. This is because the files conflict with the flash plugin.
And I followed that.

---

### Post by Kilz on 2008-09-26
Since you seem to be having trouble finding the "How to get help" section of the fist post. I will copy it here for you.

**[SIZE="4"][COLOR="Red"]How to get help (Please Read Before Making a Post)[/COLOR][/SIZE]**
**[SIZE="3"][COLOR="Red"][B]All**[/COLOR] posts asking for help [COLOR="Red"]**must**[/COLOR] have a link to a bug report on Launchpad.[/SIZE][/B]
First look through the Common Issues section to see if your problem is a common one with a fix. Then read the last 2 pages of this post to see if the issue is being addressed already by someone else.
Second [**file a bug report on Launchpad** ]("https://launchpad.net/ubuntu/+filebug")to let the developers know of the problem. Simply posting problems to the forums does not let the developers know about bugs. Few developers if any read the forums. If they do not know about issues they may never get fixed and the problem may even be in the next Ubuntu version. Add the url of the bug report to your post. 
When you make a post, make in in this thread. Please do not make a separate post. Include the results of the following.
Hardy
```
ls -al /usr/lib/mozilla/plugins/
ls -al /usr/lib/firefox-addons/plugins
```
Dapper-Gutsy
```
ls -al /usr/lib/mozilla/plugins/
ls -al /usr/lib/firefox/plugins
```
Make sure to add the URL of the bug report.
If flash installs but there are other issues running it please read the Common Issues section below.
**[COLOR="Red"]Hardy users should not install the automated script or try other methods.[/COLOR]**
**[COLOR="Red"]Dapper-Gutsy users should not repeatedly install the script or try other methods.[/COLOR]**

---

### Post by Mjölner on 2008-10-04
thanks.

just had to replace the version number in the third line of code for the hardy install.

---

### Post by pejobe on 2008-10-05
Sitting here with a clean install of intrepid beta and wonder if I should follow this post to get flash working?
I like Kilz conservative approach and want to install as little as possible.
Please guide me.

~$ ls -al /usr/lib/mozilla/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-10-05 11:19 .
drwxr-xr-x 4 root root 4096 2008-10-01 22:11 ..
lrwxrwxrwx 1 root root   44 2008-10-05 11:19 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   42 2008-10-05 11:19 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   44 2008-10-05 11:19 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   50 2008-10-05 11:19 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so

~$ ls -al /usr/lib/firefox-addons/plugins
total 8
drwxr-xr-x 2 root root 4096 2008-09-25 12:19 .
drwxr-xr-x 5 root root 4096 2008-10-01 22:08 ..

---

### Post by Kilz on 2008-10-05
> **pejobe said:**
> Sitting here with a clean install of intrepid beta and wonder if I should follow this post to get flash working?
I like Kilz conservative approach and want to install as little as possible.
Please guide me.

~$ ls -al /usr/lib/mozilla/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-10-05 11:19 .
drwxr-xr-x 4 root root 4096 2008-10-01 22:11 ..
lrwxrwxrwx 1 root root   44 2008-10-05 11:19 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   42 2008-10-05 11:19 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   44 2008-10-05 11:19 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   50 2008-10-05 11:19 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so

~$ ls -al /usr/lib/firefox-addons/plugins
total 8
drwxr-xr-x 2 root root 4096 2008-09-25 12:19 .
drwxr-xr-x 5 root root 4096 2008-10-01 22:08 ..

You can try the hardy commands, But since I have not tried or even looked at Intrepid I cant promise it will work.. Please let me know if they work.

---

### Post by pejobe on 2008-10-05
> **Kilz said:**
> You can try the hardy commands, But since I have not tried or even looked at Intrepid I cant promise it will work.. Please let me know if they work.
Now:
~$ ls -al /usr/lib/mozilla/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-10-05 22:14 .
drwxr-xr-x 4 root root 4096 2008-10-01 22:11 ..
lrwxrwxrwx 1 root root   37 2008-10-05 22:14 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   44 2008-10-05 11:19 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   42 2008-10-05 11:19 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   44 2008-10-05 11:19 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   50 2008-10-05 11:19 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so


$ ls -al /usr/lib/firefox-addons/plugins
total 12
drwxr-xr-x 2 root root 4096 2008-10-05 22:15 .
drwxr-xr-x 5 root root 4096 2008-10-01 22:08 ..
lrwxrwxrwx 1 root root   60 2008-10-05 22:15 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

!OBS! npwrapper ...lipflashplayer.so are marked with red color on black background on the screen.

-After restart I got at once:
 Bug #205356:
This report is public
compiz.real crashed with signal 7

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/205356]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/205356")

After visiting myspace music for a few seconds the screen started to faint and eventually flash figures became white and I got:
Bug #141613:
This report is public
npviewer.bin crashed with SIGSEGV

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/141613]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/141613")

So, any suggestions?

---

### Post by Kilz on 2008-10-05
> **pejobe said:**
> 
So, any suggestions?

No, I havent even looked at Intrepid. 
I strongly suggest filing you own bug report. That ancient one you linked to will not help you or anyone else.

---

### Post by pejobe on 2008-10-06
> **Kilz said:**
> I strongly suggest filing you own bug report. That ancient one you linked to will not help you or anyone else.

Yes, in the list of known bugs that appeared I picked this one because it described the same features as mine. Ok, next time I will file my own bug report.

Yesterday before finishing for the day, I rerun your script with both the 'cleaning' code and the 3 install lines. And today I can not provoke the crashes...Any suggestions on sites that can try this out?
On youtube the movies play well but NO SOUND.
On myspace music I can not listen to the music and the music files do not play, instead is it a blank white spot or nothing just background rendering.

---

### Post by pejobe on 2008-10-06
> **pejobe said:**
> Yes, in the list of known bugs that appeared I picked this one because it described the same features as mine. Ok, next time I will file my own bug report.

Yesterday before finishing for the day, I rerun your script with both the 'cleaning' code and the 3 install lines. And today I can not provoke the crashes...Any suggestions on sites that can try this out?
On youtube the movies play well but NO SOUND.
On myspace music I can not listen to the music and the music files do not play, instead is it a blank white spot or nothing just background rendering.

EDIT: Just did an package update and now sound is working on YouTube.
Myspace Music is still bad. Flickering or nothing appears...

---

### Post by Kilz on 2008-10-06
You are running Intrepid Ibex, It is still under development. Things are being worked on. I had hoped that the commands for hardy would help you. They didnt. 
But,
1. I do not recommend anyone installing development versions unless they 
    A) File bug reports - The developments sole purpose isnt to give you an operating system to use. Its to catch the bugs so when you find a bug can report them and they can be fixed.
    B) Can troubleshot issues on their own - asking for help is going to be a game of chasing your tail.
2. Historically I have not given support for any version until it is released. I think its best to go back to that practice. This section is for releases, not development. Please understand that the reasons is so that the bugs go to the place where the developers will see them and possibly fix it.

---

### Post by CrazyG on 2008-10-09
Kilz,

I can't seem to find the "thanks" icon to click on (aging eyes, no doubt) so would just like to say a very sincere thanks to you for your Dapper and Hardy Flash howto's.  They have allowed me to indulge my addiction to YouTube videos.

:)

---

### Post by Kilz on 2008-10-09
I think I have overloaded the first post, if you cant find it on the first, anyone will do. :)

---

### Post by Ti133700N on 2008-10-18
After trying countless scripts / tutorials to make flash works on Ubuntu x64, this one worked flawlessly !

Thank you so much !

---

### Post by r4e on 2008-10-19
For others having problems with flashplugin-nonfree on Intrepid Ibex, I was able to get it working correctly:

I upgraded from Hardy -> Intrepid. So first I got rid of the old nspluginwrapper and flash plugins as instructed by Kilz:

```

sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so

```

Next I executed the following commands:

```

sudo su -
apt-get install nspluginwrapper flashplugin-nonfree lib32bz2-dev
cd /usr/lib/nspluginwrapper/i386/linux
ln -s /usr/lib32/libnss3.so libnss3.so
ln -s /usr/lib32/libplc4.so libplc4.so
ln -s /usr/lib32/libplds4.so libplds4.so
ln -s /usr/lib32/libsmime3.so libsmime3.so
ln -s /usr/lib32/libssl3.so libssl3.so
ln -s /usr/lib32/nss/libsoftokn3.so libsoftokn3.so
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
ls -al
exit

```

If you don't get any errors, it should have installed correctly. Reload Firefox and go to youtube.com to check.

If you got errors, check to make sure the symlinks are valid. If any of the library lines are red (from the ls -al command above), then you are missing the 32-bit libraries.

Giving credit where due, I adapted the solution to Ubuntu from here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=500710](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=500710)  So thanks Julien Valroff and other Debian users.

I'm filing this with my bug report:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/286204](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/286204)

r4e

---

### Post by sat_e_llite on 2008-10-20
Will this work with Flash 10, non beta? I'm using Hardy.

---

### Post by r4e on 2008-10-20
> **sat_e_llite said:**
> Will this work with Flash 10, non beta? I'm using Hardy.

It might, but you (or someone else) would have to test it, since I no longer have a 64-bit hardy machine. I seem to recall having the same error (*** NSPlugin Viewer *** ERROR: /usr/local/lib/libnss3.so: version `NSS_3.11' not found) when trying to install Flash 10 on Hardy prior to upgrading to Intrepid, so there's a good chance it'll work.

If you test it and it does work, please let us know.

Thanks,

r4e

---

### Post by MaindotC on 2008-10-21
Why upgrade to Flash 10?

---

### Post by Udibuntu on 2008-10-21
Hello Kilz old pal, sorry to trouble you yet again on a Flash issue, but...

I just installed Hardy 64bit with its native Firefox 3 - flash works only partially, some sites (e.g Southpark Studio's full episodes site) do not work at all - they either grey box me or do not show anything...

Here's the output info:

> udi@udi-laptop:~$ ls -al /usr/lib/mozilla/plugins/
total 9812
drwxr-xr-x 2 root root 4096 2008-10-21 22:26 .
drwxr-xr-x 4 root root 4096 2008-07-02 12:57 ..
lrwxrwxrwx 1 root root 37 2008-10-21 22:26 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rwxr-xr-x 1 root root 10017140 2008-10-21 19:28 libflashplayer.so
lrwxrwxrwx 1 root root 60 2008-10-21 19:28 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
udi@udi-laptop:~$ ls -al /usr/lib/firefox-addons/plugins
total 12
drwxr-xr-x 2 root root 4096 2008-10-21 22:28 .
drwxr-xr-x 5 root root 4096 2008-07-02 12:55 ..
lrwxrwxrwx 1 root root 60 2008-10-21 22:28 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
udi@udi-laptop:~$


I tried the "grey box workarounds", including Flash 10, to no avail.

Link to Launchpad - [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/246450](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/246450)

What did I miss?

Thanks a bunch,

Udi

---

### Post by davidw89 on 2008-10-23
I like your script..

Any chance of getting Flash Player 10 instead?

---

### Post by Kilz on 2008-10-23
> **davidw89 said:**
> I like your script..

Any chance of getting Flash Player 10 instead?

You asked for it, you got it. That is if you run Hardy Heron. Read the first post.

---

### Post by jeromio on 2008-10-24
> **Udibuntu said:**
> Hello Kilz old pal, sorry to trouble you yet again on a Flash issue, but...

I just installed Hardy 64bit with its native Firefox 3 - flash works only partially, some sites (e.g Southpark Studio's full episodes site) do not work at all - they either grey box me or do not show anything...

Here's the output info:



I tried the "grey box workarounds", including Flash 10, to no avail.

Link to Launchpad - [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/246450](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/246450)

What did I miss?

Thanks a bunch,

UdiYou missed the same thing I missed - I wish I knew what it was. I have been running Hardy x64 since it came out. FF3 and flash9 via this script. Then yesterday everything stopped working. Flash (npviewer) is generally unstable and dies frequently. Usually restarting FF fixes it, but not anymore. I think it is tied to the FF3.03 upgrade. No flash at all, just grey boxes. So I tried to do flash10, using the new GetFlash10 script. Nada. I can get a flash app to run for 2 seconds, then it'll die and no more flash. The npviewer process shows as defunct.

I tried re-running the script to no avail.

---

### Post by Kilz on 2008-10-25
> **jeromio said:**
> You missed the same thing I missed - I wish I knew what it was. I have been running Hardy x64 since it came out. FF3 and flash9 via this script. Then yesterday everything stopped working. Flash (npviewer) is generally unstable and dies frequently. Usually restarting FF fixes it, but not anymore. I think it is tied to the FF3.03 upgrade. No flash at all, just grey boxes. So I tried to do flash10, using the new GetFlash10 script. Nada. I can get a flash app to run for 2 seconds, then it'll die and no more flash. The npviewer process shows as defunct.

I tried re-running the script to no avail.

This howto deals with installingg flash. If flash runs for even a second, its installed. If this is a request for help installing flash please reread the first post.

---

### Post by r4e on 2008-10-25
> **strAlan said:**
> Why upgrade to Flash 10?

It seems to reduce the occurrence of the infamous grey box bug, at least for me anyway. I've only had one grey box incident since the upgrade.

---

### Post by raghunath22 on 2008-10-28
Hey Thanks for the script, Kilz. It works for most of the site but somehow, colbertnation still gives me the gray box :( Will have to look for a work-around myself ... (gets off lazy bum and looks for someone who'll write code :))

---

### Post by Kilz on 2008-10-29
> **raghunath22 said:**
> Hey Thanks for the script, Kilz. It works for most of the site but somehow, colbertnation still gives me the gray box :( Will have to look for a work-around myself ... (gets off lazy bum and looks for someone who'll write code :))

Did you try the flash 10 install?

---

### Post by aidave on 2008-10-30
Confirm installation fails on Ibex 8.10 final release, using apt-get instruction at top of thread (apt-get flashplugin-nonfree nspluginwrapper)

---

### Post by Kilz on 2008-10-30
Any chance on you reading the how to get help section and supplying the required info?

---

### Post by Arup on 2008-10-31
On Opera latest 9.62 x64, you have to download Flash 10 from Adobe site and then extract libflashplayer.so and put it in /usr/lib/opera/plugin folder manually.

---

### Post by davidw89 on 2008-10-31
In Ubuntu 8.10 x64, typing this in Terminal will install Adobe Flash Player and solve all the problem (previously this never worked in Hardy Heron and it looks like finally a fix)

> sudo apt-get install nspluginwrapper flashplugin-nonfree

---

### Post by russlar on 2008-10-31
> **aidave said:**
> Confirm installation fails on Ibex 8.10 final release, using apt-get instruction at top of thread (apt-get flashplugin-nonfree nspluginwrapper)

It looks like it's already installed (at least on Kubuntu), just not functional. I made it work by purging, then re-installing flashplugin-nonfree and nspluginwrapper

---

### Post by francis_ba on 2008-11-01
[IMG]http://tinyurl.com/rerunner/[/IMG]
love ubuntu

---

### Post by steveneddy on 2008-11-02
> **davidw89 said:**
> In Ubuntu 8.10 x64, typing this in Terminal will install Adobe Flash Player and solve all the problem (previously this never worked in Hardy Heron and it looks like finally a fix)

This is where i was this morning and I still get drop down menus popping under the main video on a web page in FF3.

Opera with Flash 10 renders correctly.

---

### Post by maxxum on 2008-11-02
^^ Having the same problem. Flash 10 is working fine in Opera but not in firefox. In the about:plugins page of firefox, I don't see the flash plugin as installed. When I go to a page with flash on it, it asks me to install the player. I have done it several times, removed it, installed using aptitude. Now it asks me to install it but when I say yes, it says the plugin is already installed.  
I restarted firefox after installation, even restarted the computer. Nothing helped. There is some file that needs to be copied somewhere...can someone tell me which/where? I am running 8.10 x64.

---

### Post by Kilz on 2008-11-02
> **maxxum said:**
> ^^ Having the same problem. Flash 10 is working fine in Opera but not in firefox. In the about:plugins page of firefox, I don't see the flash plugin as installed. When I go to a page with flash on it, it asks me to install the player. I have done it several times, removed it, installed using aptitude. Now it asks me to install it but when I say yes, it says the plugin is already installed.  
I restarted firefox after installation, even restarted the computer. Nothing helped. There is some file that needs to be copied somewhere...can someone tell me which/where? I am running 8.10 x64.

Please read the first post How To Get Help section for what you should have included in your post.

---

### Post by maxxum on 2008-11-03
sorry...and thanks.
```
maxubu64@maxubux64:~$ ls -al /usr/lib/mozilla/plugins/total 8
drwxr-xr-x 2 root root 4096 2008-11-03 12:06 .
drwxr-xr-x 4 root root 4096 2008-10-29 17:15 ..
lrwxrwxrwx 1 root root   37 2008-11-02 17:09 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   44 2008-11-01 21:47 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   42 2008-11-01 21:47 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   44 2008-11-01 21:47 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   50 2008-11-01 21:47 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so
```
```

maxubu64@maxubux64:~$ ls -al /usr/lib/firefox/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-11-02 17:09 .
drwxr-xr-x 4 root root 4096 2008-11-02 16:41 ..
lrwxrwxrwx 1 root root   37 2008-11-02 17:09 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin

```

---

### Post by Kilz on 2008-11-03
You are still missing the link to your bug report.

---

### Post by WijbrandSchaap on 2008-11-05
I just had Flash working and Firefox no longer freezing when opening new pages. So I was happy. Then this morning an update came in of my kernel. I now can no longer see my favourite Youtube-clips. I have purged an reinstalled flash, gnash and all the related plugins, but that didn't help. Anyone got the same problem? A solution would be great!

---

### Post by Kilz on 2008-11-05
> **WijbrandSchaap said:**
> I just had Flash working and Firefox no longer freezing when opening new pages. So I was happy. Then this morning an update came in of my kernel. I now can no longer see my favourite Youtube-clips. I have purged an reinstalled flash, gnash and all the related plugins, but that didn't help. Anyone got the same problem? A solution would be great!

Flash and gnash are conflicting plugins. You cant or shouldnt have both installed.

---

### Post by WijbrandSchaap on 2008-11-05
> **Kilz said:**
> Flash and gnash are conflicting plugins. You cant or shouldnt have both installed.
I Knew I was doing something stupid. Gnash is out the door and Flash rocks again... Thanks. I'm fine again. ):P

---

### Post by jmrasor on 2008-11-07
Same scenario as r4e's post #415: upgraded from Hardy to Intrepid.
Followed his method.
Worked perfectly.

Good job!

---

### Post by aidave on 2008-11-09
I tried:

sudo apt-get install --reinstall libflashplugin

Now its working...

---

### Post by galenparker on 2008-11-10
A re-installation worked for me in 64bit intrepid.

Using this command:

```

sudo apt-get install --reinstall nspluginwrapper flashplugin-nonfree

```

Galen

---

### Post by Arup on 2008-11-11
[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)

This is the only method that works for Opera, otherwise blank screen with the default isntall and only FF works for youtube.

---

### Post by Kilz on 2008-11-11
> **Arup said:**
> 
This is the only method that works for Opera, otherwise blank screen with the default isntall and only FF works for youtube.

Please do not post links to any howto that has that kind of command. The command in that howto downloads a script and automatically installs it without giving the person installing it a chance to look at the script. This is as unsafe a practice as cant be done as the script can be changed at any time.

---

### Post by Arup on 2008-11-11
> **Kilz said:**
> Please do not post links to any howto that has that kind of command. The command in that howto downloads a script and automatically installs it without giving the person installing it a chance to look at the script. This is as unsafe a practice as cant be done as the script can be changed at any time.

The site gives you option to download the script before executing it, and as of now, this is the only way to get Flash 10 working nicely in Opera, so far every other method has failed including the one from the repos, for a first time Ubuntu user, this script bad or good is heaven sent. Unless there is a better solution, the best I can advice is to download and check the script out before executing it.

---

### Post by Kilz on 2008-11-12
> **Arup said:**
> The site gives you option to download the script before executing it, and as of now, this is the only way to get Flash 10 working nicely in Opera, so far every other method has failed including the one from the repos, for a first time Ubuntu user, this script bad or good is heaven sent. Unless there is a better solution, the best I can advice is to download and check the script out before executing it.

Yes, downloading the script, then looking at it, then running it is the correct way. But that command automatically downloads, and then without any further action from the user, installs the script right after download. Sadly the offer to look at the script is lower than the command and they may see it after running the command.  New users may also think its safe since someone like you recommended it. The link to the script could also be fashioned in such a way to point to a different file.
This has a great possibility for abuse and should not be done. New users may not see that is what that command does.
One thing that could happen is the script can be changed at any time to include malicious commands or install malicious software. Since the user cant see what the script is going to do before installing it they have no idea what its going to do.
While this script may be safe, it leads to a false sense of security. The next time they see a command like this it may not be. The user will think its safe then. But trusting it they may delete the contents of their drive, install a rootkit or other bad things.
Helping other users is a good thing, and I command you for trying to help others. But imho we must also make sure that we help them understand what could go wrong and to be safe rather than sorry. So I would rather err on the side of caution, I hope you would as well.

---

### Post by Arup on 2008-11-12
Two things I wish dearly, one is Java and other is Flash, in today's world both are important, Flash is hugely popular like it or leave it and therefore working flash is a must. If only the repos can do the right job we won't be having this thread at all, sadly there is no other solution but this for Opera to work with flash, not all are interested in running FF, the default repos installation of Flash works fine with FF as does Java. So far for Opera, even Sun Java installation is providing no solution for Java pages.

---

### Post by Kilz on 2008-11-12
> **Arup said:**
> Two things I wish dearly, one is Java and other is Flash, in today's world both are important, Flash is hugely popular like it or leave it and therefore working flash is a must. If only the repos can do the right job we won't be having this thread at all, sadly there is no other solution but this for Opera to work with flash, not all are interested in running FF, the default repos installation of Flash works fine with FF as does Java. So far for Opera, even Sun Java installation is providing no solution for Java pages.

The solution is to keep reporting bugs on launchpad in the hopes it will be fixed. IMHO I think its possible that scripts sometimes hurt more than they help. The user who runs one has the problem fixed, but the bug is seldom reported. When its not reported, its not fixed. So others have the same problem because it wasn't fixed.

---

### Post by 081104jk on 2008-11-13
[**&#20445;&#27905;&#29992;&#21697;&#20844;&#21496;**](http://www.icleant.com/bjypgs.htm) ----&#25143;&#22806;[**&#20928;&#27700;&#22120;**](http://www.quanlai.net/cn/Index.Asp)&#30693;&#35782;     &#25143;&#22806;&#38543;&#22320;&#39278;&#29992;&#26410;&#32463;&#22788;&#29702;&#25110;&#27809;&#26377;&#34987;&#20928;&#21270;&#30340;&#27700;&#65292;&#23601;&#22909;&#20687;&#22312;&#29609;&#20420;&#32599;&#26031;&#36718;&#30424;&#36172;&#19968;&#26679;&#65292;&#24744;&#21487;&#33021;&#31532;&#19968;&#27425;&#12289;&#31532;&#20108;&#27425;&#12289;&#31532;&#19977;&#27425;&#8230;&#8230;&#37117;&#27809;&#26377;&#38382;&#39064;&#65292;&#20294;&#38543;&#26102;&#37117;&#26377;&#21487;&#33021;&#21463;&#21040;&#22823;&#32676;&#24494;&#29983;&#29289;&#30340;&#25915;&#20987;&#32780;&#20498;&#19979;&#65292;&#20063;&#35768;&#20960;&#20010;&#23567;&#26102;&#20869;&#24744;&#23601;&#21487;&#33021;&#30149;&#20498;&#12290;    [**&#20928;&#27700;&#22120;**](http://www.quanlai.net/cn/Index.Asp)&#30340;&#31181;&#31867;&#65306;     [**&#20928;&#27700;&#22120;**](http://www.quanlai.net/cn/Index.Asp)&#26681;&#25454;&#20928;&#27700;&#30340;&#21407;&#29702;&#21644;&#26041;&#27861;&#65292;&#20027;&#35201;&#21487;&#20197;&#21306;&#20998;&#20026;&#26426;&#26800;&#24335;[**&#20928;&#27700;&#22120;**](http://www.quanlai.net/cn/Index.Asp)&#21644;&#21270;&#23398;&#24335;&#20928;&#27700;&#33647;&#29255;&#12290;&#22312;&#26426;&#26800;&#24335;&#20928;&#27700;&#22120;&#20013;&#30001;&#20110;&#20351;&#29992;&#30340;&#36807;&#28388;&#20171;&#36136;&#30340;&#19981;&#21516;&#36824;&#21487;&#20197;&#20877;&#32454;&#20998;&#20026;&#38518;&#29943;&#12289;&#27963;&#24615;&#28845;&#21644;&#29627;&#29827;&#32420;&#32500;&#19977;&#31181;&#26426;&#26800;&#24335;&#36807;&#28388;&#22120;&#12290;&#32780;&#21270;&#23398;&#24335;&#20928;&#27700;&#29255;&#20063;&#22240;&#20026;&#20351;&#29992;&#30340;&#28040;&#27602;&#20803;&#32032;&#19981;&#21516;&#32780;&#20998;&#20026;&#38134;&#12289;&#30872;&#21644;&#27695;&#19977;&#31181;&#12290;&#20197;&#19979;&#31616;&#35201;&#35828;&#26126;&#23427;&#20204;&#30340;&#20928;&#27700;&#21407;&#29702;&#21644;&#29305;&#28857;&#12290;

---

### Post by HalNineThousand on 2008-11-13
I may have gotten confused along the way, but I've seen different discussions and issues and I may not have kept it all straight.

I've installed 64bit Intrepid as a fresh install on a system with a 4 core Phenom by AMD.  I had a few glitches, like getting the dual-head monitors to work, but that seemed to resolve itself as packages got upgraded.

I'm still stuck, though, with one issue: Flash on Konqueror.  It's working fine on Firefox, but it seems everything I've read about Flash has either been people working with Firefox or Opera or on Hardy or an earlier version.  I use Firefox and Konqeror for different reasons and things are much easier if I can use Java and Flash in both of them.  I've seen posts on dealing with this before Intrepid was finalized or on earlier versions, but I don't think I've seen one on dealing with it now that Intrepid has been officially released (in case that changes anything).

Has anyone gotten Flash working on Firefox AND Konqueror on 64bit Intrepid?  Did I miss a point in any earlier posts?  (There are, after all, about 45 pages of posts and while I tried to go through them, I may have missed something or gotten versions and browsers confused in some posts.)

Thanks for any help on this!

---

### Post by Arup on 2008-11-14
If you install from the repos either via Ubuntu restricted or stand alone, it works fine on Firefox, no issues at all, problem is with Opera and the workaround is to install the plugin first and then install Opera.

---

### Post by H4rold on 2008-11-17
For those who want the latest beta version (64 bit version) : 

Remove the current one that uses ndiswrapper.
Download the beta one from adobe
copy it in your mozilla plugin folder :

apt-get --purge remove nonfree-flashplugin nspluginwrapper
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)
tar xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so .mozilla/plugins/

---

### Post by chuckyp on 2008-11-17
You don't need to install nspluginwrapper its required by flashplugin-nonfree. And this works on Intrepid 64bit no problems.

---

### Post by alexcuervo on 2008-11-17
> **Kilz said:**
> Yes, downloading the script, then looking at it, then running it is the correct way. But that command automatically downloads, and then without any further action from the user, installs the script right after download. Sadly the offer to look at the script is lower than the command and they may see it after running the command.  New users may also think its safe since someone like you recommended it. The link to the script could also be fashioned in such a way to point to a different file.
This has a great possibility for abuse and should not be done. New users may not see that is what that command does.
One thing that could happen is the script can be changed at any time to include malicious commands or install malicious software. Since the user cant see what the script is going to do before installing it they have no idea what its going to do.
While this script may be safe, it leads to a false sense of security. The next time they see a command like this it may not be. The user will think its safe then. But trusting it they may delete the contents of their drive, install a rootkit or other bad things.
Helping other users is a good thing, and I command you for trying to help others. But imho we must also make sure that we help them understand what could go wrong and to be safe rather than sorry. So I would rather err on the side of caution, I hope you would as well.

@ Klitz, I wonder what makes your scripts more trustworthy? This is also a 3rd party website. YOUR scripts can also change at any time. And some of YOUR scripts are even hosted on a home computer, for instance this one: [http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz](http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz) at your post at [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)) 

The source code for the script at ([http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)) has always been available for everyones review and CONSTRUCTIVE criticism.

Besides, it is not true that the command "wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh) && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh" will "Automatically Install" as you put it. The user still needs to give his authorization before is executed. I see no difference in this and you telling your users in your posts to:

> 
**5. Select "Run in Terminal"**

1. Download the script.
2. Right click on the tar.gz and select "Extract Here"
3. Close all browsers.
4. Inside the folder that extracts is a "GetFlash10" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done.
8. If you select anything but Hardy Heron the script will not install anything.


---

### Post by xebian on 2008-11-17
Time to get rid of this sticky, or updated for the 64-bit flash.

---

### Post by Kilz on 2008-11-17
> **alexcuervo said:**
> @ Klitz, I wonder what makes your scripts more trustworthy? This is also a 3rd party website. YOUR scripts can also change at any time. And some of YOUR scripts are even hosted on a home computer, for instance this one: [http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz](http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz) at your post at [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)) 

The source code for the script at ([http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)) has always been available for everyones review and CONSTRUCTIVE criticism.

Besides, it is not true that the command will "Automatically Install" as you put it. The user still needs to give his authorization before is executed. I see no difference in this and you telling your users in your posts to:

I dont and never have had a command that automatically downloads and installs a script on any howto I have ever made. That is all I have pointed out as a problem. 
There is a series of steps. At any time the person can view the script and look at it because they have it downloaded. None of my scripts have commands that automatically download, start, and install them.
Doing so is a big NO NO.

> **xebian said:**
> Time to get rid of this sticky, or updated for the 64-bit flash.
I dont think the release by adobe of an Alpha version of 64bit flash is a reason to remove a sticky. But I have added the information to the first post.

---

### Post by vanadium101 on 2008-11-17
I thought i would give better instructions than H4rold did for installing the beta 64 bit version

```

sudo apt-get purge flashplugin-nonfree nspluginwrapper

wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz

tar xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz

sudo rm /usr/lib/firefox/plugins/libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so

sudo cp libflashplayer.so /usr/lib/firefox/plugins
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```

Checking in about:plugins should show the version to be 10.0 d20

---

### Post by Arup on 2008-11-17
If you have done apt-get --purge or a complete uninstallation from there is no need for a rm for the libflashplayer.so as it already has been removed.

In Alejandro's defence for a first time Ubuntu user, it can be quite daunting to untar and do the command prompt rm, cp etc., in that case, that script eases the process greatly and makes transition to Ubuntu from Windows a wee bit easier and less troublesome. In today's media dependant world, everyone needs working Flash and when that doesn't happen, frustration sets in and sometimes that makes them go back to their original OS. Of course like any scripts there are risks but then the creator wouldn't be so irresponsible to put it up a website. All he is trying to do is make it easy for novices to install Flash, maybe thats what Ubuntu devs should be doing but I guess their hands are full. The Adobe dev also lamented the fact that he had absolutely no help from Linux devs regarding the development of Flashx64 and thats another surprise.

---

### Post by vanadium101 on 2008-11-17
The reason I used rm for the libflashplayer.so was because the files didn't get purged from there properly and were still in the directories that the new one was to be copied to.

---

### Post by Arup on 2008-11-17
> **vanadium101 said:**
> The reason I used rm for the libflashplayer.so was because the files didn't get purged from there properly and were still in the directories that the new one was to be copied to.

If you use --purge or complete uninstall from Synaptic, it shouldn't be the case, both methods completely remove any traces of old Flash.

---

### Post by Yellow Pasque on 2008-11-17
I installed the 64-bit version. It works nicely in FF 3.04, but it segfaults in Swiftweasel 3.03. Hmm...

---

### Post by Arup on 2008-11-17
> **Temüjin said:**
> I installed the 64-bit version. It works nicely in FF 3.04, but it segfaults in Swiftweasel 3.03. Hmm...

Do you have nsplugin installed? If so, do a --purge remove.

---

### Post by vanadium101 on 2008-11-17
try putting libflashplayer.so in /usr/lib/Swiftweasel/plugins
first make sure that directory exists and then try 

```
sudo cp libflashplayer.so /usr/lib/Swiftweasel/plugins
```

it might not be the solution to other browsers but it does work nicely in firefox

---

### Post by HalNineThousand on 2008-11-17
I'll restate an important part of my original question, which has gone unanswered so far:

Is anyone using Flash in Konqueror successfully on 64bit Intrepid?

I notice everyone talks about Firefox, but for various reasons I would love to have Flash work in both browsers, but it seems like Konqueror is being totally ignored on this thread.  Why?

---

### Post by limejuice on 2008-11-17
I installed 64bit alpha according to vanadium101 instructions, and I've got videos.google.com and [www.youtube.com](www.youtube.com) working fine. Videos seem to be working much smoother than the 32bit version with nspluginwrapper, esp. when you go fullscreen.

But it's important to check about:plugins after you follow the steps to make sure you have version "10.0 d20" installed and no older versions, because I still had some links to nspluginwrapper which caused firefox to think the older flash 10 was still installed, even though nspluginwrapper had been purged. That caused flash apps to fail to load.

I had installed the32bit  flash10 beta and then the 32bit flash 10 final version, so maybe that's why I have extra links.  But purging nspluginwrapper and nonfree-flashplugin didn't remove those extra links.

After I removed those extra links and restarted firefox, everything worked.  As I mentioned, videos seem to be working very nice. I just checked espn and all the flash on that site seemed to be working also.  So far, it looks really nice!

Here are the extra links which weren't removed after following
vanadium101's steps in post #456.

/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

---

### Post by Arup on 2008-11-17
nsplugin wrapper has to be completely removed for x64 Flash to function as per Adobe recommendations.

---

### Post by jtgd on 2008-11-18
Has anyone gotten it to work with Konqueror? I am running Feisty amd64 and it just crashes.
 The instructions say not to use nsplugin, but I don't see how to make it work without that.

---

### Post by Arup on 2008-11-18
> **jtgd said:**
> Has anyone gotten it to work with Konqueror? I am running Feisty amd64 and it just crashes.
 The instructions say not to use nsplugin, but I don't see how to make it work without that.

Why not install Opera and give that a try? You can copy liflashplayer.so in /usr/lib/Opera/plugins

---

### Post by HalNineThousand on 2008-11-18
> **Arup said:**
> Why not install Opera and give that a try? You can copy liflashplayer.so in /usr/lib/Opera/plugins

I never buy that as a reason for not trying to get something to work.  We all use programs that work for us and our unique needs.  In my case, I have reasons for using Konqueror and reasons for using Firefox.  If the solution were to just use another program because the config works there, then I might as well switch to a Mac so it all "just works" or switch to Windows since that's what most software works on anyway without tweaking.

---

### Post by Arup on 2008-11-18
> **HalNineThousand said:**
> I never buy that as a reason for not trying to get something to work.  We all use programs that work for us and our unique needs.  In my case, I have reasons for using Konqueror and reasons for using Firefox.  If the solution were to just use another program because the config works there, then I might as well switch to a Mac so it all "just works" or switch to Windows since that's what most software works on anyway without tweaking.

It works in Ubuntu without tweak as well in case you selected the x32 version. For x64, even Windows has program and driver issues and the only issue in x64 was Flash and so far, its working with FF and Opera very reliably. I have never used Konqueror so have no idea about the plugin process, maybe a Kubuntu user here will explain it better. I thought Konqueror like Opera would pick the plugin up from /usr/lib/mozilla/plugins but I guess I was mistake. If you have FF installed, have you tried pointing to the usr/lib/mozilla/flashplugin in Konqueror plugin options? If you don't have option, create a folder called Flash, copy libflashplayer.so to it and then fire up Konqueror, select options plugin and point to it.

---

### Post by Soarer on 2008-11-18
Thanks to Kilz, Arup and vanadium101 I have followed these easy instructions and it worked first time. I didn't need the 'rm' commands but not harm was done by running them.

So far it seems to be a better plugin than the 32 bit one.

Thanks folks, I appreciate your efforts.

---

### Post by fatbuttlarry on 2008-11-18
64-bit worked worse on my K(Ubuntu) 8.04 64-bit than the 32-bit with nspluginwrapper.

Details at bottom of [this post]("http://ubuntuforums.org/showpost.php?p=6201563&postcount=7").

Although I use KDE, I do not use Konqueror for regular browsing, so I haven't put any effort into flash with that browser.

-Tres

---

### Post by Arup on 2008-11-18
My 14 year old newphew came yesterday and played online flash based game for hours without any hitches, then he watched various youtube clips probably for another hour or so and there was no slow downs whatsoever. Did you remove nsplugin before installing the x64 Flash?

---

### Post by HalNineThousand on 2008-11-18
> **Arup said:**
> It works in Ubuntu without tweak as well in case you selected the x32 version. For x64, even Windows has program and driver issues and the only issue in x64 was Flash and so far, its working with FF and Opera very reliably.

I definitely know about Windows driver issues!  One thing I love about Linux is that I don't have to search for drivers.  I remember when I first started with Linux, in the very late '90s, it wasn't easy to find drivers for most hardware on Linux but now I never have to hunt for anything -- it's all usually included in the distro when I install.

> **Arup said:**
> I have never used Konqueror so have no idea about the plugin process, maybe a Kubuntu user here will explain it better. I thought Konqueror like Opera would pick the plugin up from /usr/lib/mozilla/plugins but I guess I was mistake.

It's supposed to and it looked like, on first install, Konq at least picked up on it being a plugin because there was a blank white square where the Flash should be, but when I tried a purge than reinstall of Flash (since I figured it might be a config issue or something), then once that was done, it was like Konq didn't even know about Flash anymore.

> **Arup said:**
>  If you have FF installed, have you tried pointing to the usr/lib/mozilla/flashplugin in Konqueror plugin options? If you don't have option, create a folder called Flash, copy libflashplayer.so to it and then fire up Konqueror, select options plugin and point to it.

FF is installed.  Generally I use FF for web browsing and Konq for file handling (I don't like Dolphin!), but there are times I want Konq for some websites for various reasons, which is why I want Flash on Konq as well -- it just seems nobody has Flash working on Konq on 64bit yet.

---

### Post by Thelasko on 2008-11-18
The new 64-bit Flash plugin is the best I have ever used.  I see no difference between it and Flash on Windows.  Plus, it's very fast.

No bugs to report yet.

---

### Post by Toadmund on 2008-11-18
> **vanadium101 said:**
> I thought i would give better instructions than H4rold did for installing the beta 64 bit version

```

sudo apt-get purge flashplugin-nonfree nspluginwrapper

wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz

tar xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz

sudo rm /usr/lib/firefox/plugins/libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so

sudo cp libflashplayer.so /usr/lib/firefox/plugins
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```

Checking in about:plugins should show the version to be 10.0 d20

Now, to get it actually working, extract the ```
libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
```
cut or copy the ```
libflashplayer.so
```icon
Into ```
home/user/.mozilla/plugins
```
Create a plugins folder if one does not exist then put it in.

Close your browser, restart.

---

### Post by H4rold on 2008-11-18
> **Toadmund said:**
> Now, to get it actually working, extract the ```
libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
```
cut or copy the ```
libflashplayer.so
```icon
Into ```
home/user/.mozilla/plugins
```
Create a plugins folder if one does not exist then put it in.

Close your browser, restart.

vanadium101  post works also (even if the rm part is useless)

Your way of doing it is exactly the same than the one I posted before.

I prefer putting it in ~/.mozilla/plugins because it's a directory that belongs to user and not to the system. I do not like touching the system, I'd rather leave it to apt.

---

### Post by Arup on 2008-11-18
Problem with putting that plugin in ~/.mozzilla/plugins is that browser like Opera would look for the standard /usr/lib/share/mozilla/plugins folder, of course that can be changed but its an added hassle. Most other programs needing flash looks in the default /usr/lib/share/mozilla/plugins folders by default.

---

### Post by Toadmund on 2008-11-18
> **H4rold said:**
> 
Your way of doing it is exactly the same than the one I posted before.

Yes, I see that, it seems vanadiums 'improved' script did not do that, but yours has that command to do that.

I used vanadiums, but it was not complete until I pasted 'libflashplayer.so' into my .mozilla/plugins folder.

I figured by making that post I could help someone else who used vanadiums script without taking a bit from yours. Seems both are lacking completeness unless they are merged.


PS, so far this 64 bit version works really good, I don't have to keep refreshing a page, or restarting my browser to get the screen up from a gray box every three or so times, the video shows up every time, major hassle no longer. :)

---

### Post by m_l17 on 2008-11-18
I switched to the alpha and it's working better than before :)

I like to thank H4rold :popcorn: and vanadium101 :popcorn:

---

### Post by Thelasko on 2008-11-18
> **Toadmund said:**
> PS, so far this 64 bit version works really good, I don't have to keep refreshing a page, or restarting my browser to get the screen up from a gray box every three or so times, the video shows up every time, major hassle no longer. :)

It also appears to display in the correct order.  No more Flash over menu's problems.  Of course, I hear the latest nspluginwrapper fixed that in Intrepid.

---

### Post by Hark3n on 2008-11-18
I struggled with flash all evening and finally found this.

Had problems with the copy of the .so file until I went searching for the folder it tried copying to and found the correct location at /usr/lib/firefox-addons/plugins.

Now all is well in the land of flash.

Thanks,
E

---

### Post by clayX on 2008-11-18
i run apt-get remove, then apt-get install nspluginwrapper flashplugin-nonfree, it says flash installed, but it didn't.  it doesn't show up in the firefox plugins at all.  i just installed intrepid kubuntu 64 on Friday, and am pretty new, so i'm sure it's something simple?

---

### Post by deew on 2008-11-18
I just downloaded the 10.0.20.7 alpha from Adobe.  Got it here:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I went to my home folder, set to show hidden files, went into .mozilla, created a folder named plugins and put the libflashplayer.so file in it.

I restarted Firefox and so far I am amazed.  As I type this, i am playing a video from the Colbert site - a thing that i have never done on Ubuntu before.  Ever.  

That is an improvement.  (running Hardy)

---

### Post by xebian on 2008-11-18
> **HalNineThousand said:**
> 

FF is installed.  Generally I use FF for web browsing and Konq for file handling (I don't like Dolphin!), but there are times I want Konq for some websites for various reasons, which is why I want Flash on Konq as well -- it just seems nobody has Flash working on Konq on 64bit yet.

It does work on Konq but it's slow and needs reload(s) before it starts playing.  The panel showing 'what's being viewed now' is a problem.:(

---

### Post by xebian on 2008-11-18
> **clayX said:**
> i run apt-get remove, then apt-get install nspluginwrapper flashplugin-nonfree, it says flash installed, but it didn't.  it doesn't show up in the firefox plugins at all.  i just installed intrepid kubuntu 64 on Friday, and am pretty new, so i'm sure it's something simple?
:confused:
Not sure if you have been reading the previous posts, but you just get the new 64-bit release and you don't need any of the nspluginwrapper nor the flashplugin-nonfree.  Just follow the instructions as posted above.

---

### Post by clayX on 2008-11-18
> **xebian said:**
> :confused:
Not sure if you have been reading the previous posts, but you just get the new 64-bit release and you don't need any of the nspluginwrapper nor the flashplugin-nonfree.  Just follow the instructions as posted above.

i'm so lost.  there's a million different ways posted above. :lolflag:

---

### Post by em4r1z on 2008-11-18
I followed [**vanadium101**]("http://ubuntuforums.org/showthread.php?p=6200737#post6200737")'s instructions and Flash works like a charm, better than the 32-bit version, which refused to work unless I reloaded the web page almost every time I used it.

If you used Synaptic to install/remove flashplugin-nonfree you might also want to purge:
ia32-libs (2.2ubuntu18)
lib32asound2 (1.0.17a-0ubuntu4)
lib32gcc1 (1:4.3.2-1ubuntu11)
lib32ncurses5 (5.6+20071124-1ubuntu2)
lib32nss-mdns (0.10-3ubuntu2)
lib32stdc++6 (4.3.2-1ubuntu11)
lib32z1 (1:1.2.3.3.dfsg-12ubuntu1)
libc6-i386 (2.8~20080505-0ubuntu7)

And delete these files:
/usr/lib/firefrox/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

---

### Post by stroyer on 2008-11-19
Just installed the new 64bit   plug-in by creating a new folder under the hidden ./mozilla folder

It has fixed all of my flash issues thus far. Awesome

---

### Post by Kilz on 2008-11-19
> **em4r1z said:**
> I followed [**vanadium101**]("http://ubuntuforums.org/showthread.php?p=6200737#post6200737")'s instructions and Flash works like a charm, better than the 32-bit version, which refused to work unless I reloaded the web page almost every time I used it.

If you used Synaptic to install/remove flashplugin-nonfree you might also want to purge:
ia32-libs (2.2ubuntu18)
lib32asound2 (1.0.17a-0ubuntu4)
lib32gcc1 (1:4.3.2-1ubuntu11)
lib32ncurses5 (5.6+20071124-1ubuntu2)
lib32nss-mdns (0.10-3ubuntu2)
lib32stdc++6 (4.3.2-1ubuntu11)
lib32z1 (1:1.2.3.3.dfsg-12ubuntu1)
libc6-i386 (2.8~20080505-0ubuntu7)

And delete these files:
/usr/lib/firefrox/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

I wouldnt remove the first list if you have any other 32bit linux application or wine installed.

---

### Post by kepreon on 2008-11-19
I guess no one else shares my problems, but installing the alpha version with FF 3.04 (souped up with a lot of extensions, mind you) segfaulted the browser repeatedly.  I was able to get it up and running for a while and Flash worked fine, but then yesterday the plugin corrupted my bookmarks and history (and the back button wouldn't work) so I had to manually clear out the cache in my ~/.mozilla/firefox and remove the plugin before I could get it to work again.  Is anyone else having problems with segfaults or have any suggestions on how to debug it?

---

### Post by Thelasko on 2008-11-19
> **kepreon said:**
> I guess no one else shares my problems, but installing the alpha version with FF 3.04 (souped up with a lot of extensions, mind you) segfaulted the browser repeatedly.  I was able to get it up and running for a while and Flash worked fine, but then yesterday the plugin corrupted my bookmarks and history (and the back button wouldn't work) so I had to manually clear out the cache in my ~/.mozilla/firefox and remove the plugin before I could get it to work again.  Is anyone else having problems with segfaults or have any suggestions on how to debug it?

I reported a bug about the mouse freezing video when it was in full screen and saw [this one]("https://bugs.adobe.com/jira/browse/FP-1030").

However, I haven't experienced any crashes as a result of the new plugin.

---

### Post by Kilz on 2008-11-19
> **kepreon said:**
> I guess no one else shares my problems, but installing the alpha version with FF 3.04 (souped up with a lot of extensions, mind you) segfaulted the browser repeatedly.  I was able to get it up and running for a while and Flash worked fine, but then yesterday the plugin corrupted my bookmarks and history (and the back button wouldn't work) so I had to manually clear out the cache in my ~/.mozilla/firefox and remove the plugin before I could get it to work again.  Is anyone else having problems with segfaults or have any suggestions on how to debug it?

File A Bug Report.

Please also read the 64bit Adobe Flash Alpha section of the first post.

---

### Post by kepreon on 2008-11-19
Thanks.  It appears that my bug is the same as [https://bugs.adobe.com/jira/browse/FP-1017]("https://bugs.adobe.com/jira/browse/FP-1017") -- Gmail crashes the plugin.  Unfortunately, I need Gmail, so I can't use the alpha quite yet...

---

### Post by xebian on 2008-11-19
> **kepreon said:**
> I guess no one else shares my problems, but installing the alpha version with FF 3.04 (souped up with a lot of extensions, mind you) segfaulted the browser repeatedly.  I was able to get it up and running for a while and Flash worked fine, but then yesterday the plugin corrupted my bookmarks and history (and the back button wouldn't work) so I had to manually clear out the cache in my ~/.mozilla/firefox and remove the plugin before I could get it to work again.  Is anyone else having problems with segfaults or have any suggestions on how to debug it?

I doubt the plugin has anything to do with your issue.  My guess is you have an sql db corruption.  When you got rid of the .mozilla/firefox, FFox recreated a new fresh/empty one.

---

### Post by xebian on 2008-11-19
> **kepreon said:**
> Thanks.  It appears that my bug is the same as [https://bugs.adobe.com/jira/browse/FP-1017]("https://bugs.adobe.com/jira/browse/FP-1017") -- Gmail crashes the plugin.  Unfortunately, I need Gmail, so I can't use the alpha quite yet...

Gmail is working quite well here.  I do enjoy the French clubic site he says is crashing (not on mine).  Too bad they don't have an english version.

---

### Post by Kilz on 2008-11-19
> **kepreon said:**
> Thanks.  It appears that my bug is the same as [https://bugs.adobe.com/jira/browse/FP-1017]("https://bugs.adobe.com/jira/browse/FP-1017") -- Gmail crashes the plugin.  Unfortunately, I need Gmail, so I can't use the alpha quite yet...

Guessing its the same as one you found isnt filing a bug report. Its fast, its free, just do it.

---

### Post by Thelasko on 2008-11-19
> **Kilz said:**
> Guessing its the same as one you found isnt filing a bug report. Its fast, its free, just do it.

Once you register, you can also vote for bugs that effect you.

---

### Post by newbiebme on 2008-11-23
Hi, I'm still having flash problems I think. I read the thread on 64 bit systems and flash and this one ( I have a 64 bit). When I visit you tube for ex: the page loads but not the applet, when I click on the applet then it loads.
 One problem might be that I installed flash for AMD 64 bit users, but I don't know what AMD is. I think there is either that or intel right? I have intel.
 Next I don't know how to tell which flash player I havem gusty,adobe..... I already have icedtea and the open JDK installed.

Is there a way I can uninstall all flash and try again? Oh and I have firefox

---

### Post by PMahoney on 2008-11-23
Just confirming that the new flash works with Gmail on my box with FF 3.0.4 and Opera.

P

---

### Post by Kilz on 2008-11-23
> **newbiebme said:**
> Hi, I'm still having flash problems I think. I read the thread on 64 bit systems and flash and this one ( I have a 64 bit). When I visit you tube for ex: the page loads but not the applet, when I click on the applet then it loads.
 One problem might be that I installed flash for AMD 64 bit users, but I don't know what AMD is. I think there is either that or intel right? I have intel.
 Next I don't know how to tell which flash player I havem gusty,adobe..... I already have icedtea and the open JDK installed.

Is there a way I can uninstall all flash and try again? Oh and I have firefox

Follow the clean out instructions in the Hardy section of the first post. 
AMD or Intel, it doesn't matter much as  long as its 64bit (Intel calls it EMT64) and you installed the AMD64 version of Ubuntu. If you have 64bit hardware, but did not install the 64bit (AMD64) version you are in the wrong place. 
I would like you to open a terminal and type in the following.
```
uname -a
```
please paste the results to a reply here.

> **PMahoney said:**
> Just confirming that the new flash works with Gmail on my box with FF 3.0.4 and Opera.

P

Thats fine, but at 50 pages and growing lets keep the "its working" posts to a minimum. This way it will be easier to get people to actually read the info that gets added.

---

### Post by Xebec on 2008-11-23
The plugin have been installed successfully. It works very reliably - no crashes in three days of usage. However there is a big problem with this Alpha. It is much slower than vanilla 32 bit + nspluginwrapper. My OC'd to 3.3 Ghz Q6600 struggles with quite a few youtube videos, especially if they are in full screen mode. I hope Adobe will fix this issue ASAP.

---

### Post by jtgd on 2008-11-23
I just installed the newest stable Firefox (3.0.4) on Feisty.  It runs OK.  It is:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.0.4) Gecko/2008102920 Firefox/3.0.4

I unpacked it into a directory and in that directory's plugins I copied the new libflashplayer and it gives this error when I run it:

LoadPlugin: failed to initialize shared library /home/jay/Install/firefox-3.0.4/firefox/plugins/libflashplayer.so [/home/jay/Install/firefox-3.0.4/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]

Why won't a 64bit Firefox load a 64bit plugin???

(BTW this very same plugin does work with limited success in Konqueror so I know the plugin works)

---

### Post by Yellow Pasque on 2008-11-23
> **jtgd said:**
> Why won't a 64bit Firefox load a 64bit plugin???
You've got a 32-bit version of FF 3.04 there (it says i686).

---

### Post by jtgd on 2008-11-23
> **Temüjin said:**
> You've got a 32-bit version of FF 3.04 there (it says i686).
It says "i686 (x86_64)".  Isn't x86_64 64-bit?

And if it's not, where do I get the 64bit Firefox v3?

---

### Post by Xebec on 2008-11-24
> **jtgd said:**
> I just installed the newest stable Firefox (3.0.4) on Feisty.  It runs OK.  It is:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.0.4) Gecko/2008102920 Firefox/3.0.4

Jay, here is how it looks on my Intrepid:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.4) Gecko/2008111319 Ubuntu/8.10 (intrepid) Firefox/3.0.4

Note the absence of i686. It seems to me you've installed 32 bit version. Try 32 bit Flash plugin from Adobe: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)

---

### Post by jtgd on 2008-11-24
> **Xebec said:**
> Jay, here is how it looks on my Intrepid:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.4) Gecko/2008111319 Ubuntu/8.10 (intrepid) Firefox/3.0.4

Note the absence of i686. It seems to me you've installed 32 bit version. Try 32 bit Flash plugin from Adobe: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)

OK.  Thanks, but I already have 32-bit flash running.  I use Icecat when I need to do flash, though I prefer to use Konqueror for most everything else.  Ideally I'm hoping to get the 64-bit flash working on Konqueror eventually, but until then I thought I would try to get it working with Firefox as everyone else seems to be able to do, but I can't find a 64-bit Firefox 3 anywhere.  Is there such a beast?

---

### Post by Xebec on 2008-11-25
> **jtgd said:**
> Is there such a beast?Why? If you have 32 bit already running, there is no difference. Really. On the top of it 32 bit has quicker and more reliable Flash and working Java for years. 
I have to run my 64 bit not by my choice. If I had a choice, it would have been 32 bit version. For some (probably really irrational) reason Canonical guys decided otherwise. And now we are stuck in this thread - trying to have normal browsing capabilities as the rest of the world while keeping repositories in more or less vanilla state.

---

### Post by Izek on 2008-11-25
Too bad flash crashes a lot in hardy for me. Every time I navigate from a youtube movie to another page, BOOM, firefox crashes and it has to close.

---

### Post by jtgd on 2008-11-25
> **Xebec said:**
> Why? If you have 32 bit already running, there is no difference. Really. On the top of it 32 bit has quicker and more reliable Flash and working Java for years. 
This thread started with the release of the 64-bit version.  Everyone seems to think it is faster.  I have noticed that the 32-bit version cannot handle a full screen flash playback (becomes a slow frame rate and CPU maxes out) while the 64-bit version plays smoothly in full screen.

---

### Post by Thelasko on 2008-11-25
> **jtgd said:**
> This thread started with the release of the 64-bit version.  Everyone seems to think it is faster.  I have noticed that the 32-bit version cannot handle a full screen flash playback (becomes a slow frame rate and CPU maxes out) while the 64-bit version plays smoothly in full screen.

I still get dropped frames with the 64-bit version.  Although it is much better than with 32-bit.  In my opinion, Flash 9 handled full screen video much better than both versions of Flash 10.

I've made a bug report noting this.

---

### Post by mjmctaggart on 2008-11-27
I was having the same problem with FF3.0.4 on Hardy 8.04 AMD64: YouTube videos would start, play for ~2 seconds and then freeze up :(. Tried the various fixes listed on Page 1 of this thread, but all to no avail :confused:. So, using the Synaptic Package Manager, I uninstalled FF, following which, I ran the uninstall code under the "Flash 9 manual" section of this thread. After rebooting, I used Synaptic to reinstall FF 3.0.4 with the Adobe FlashPlayer Plugin and all seems to be fine :).

---

### Post by CinciBearFan on 2008-11-29
Help,

I'm new to linux, (just built a new machine, and made the full blown switch, no dual boot here) and finally got the 64 bit version of Flash installed. 

dad@Ced-Home:~$ uname -a
Linux Ced-Home 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

I'm running 8.10 and firefox 3.0.4


The problem I am having is that none of the applets autoload. This isn't the end of the world for a site like Youtube, where it's one extra click. But for those with a lot of flash, they load like shown in my attachment, just a bunch of "f"s on the page, requiring many many clicks.

See [http://www.americasarmy.com/](http://www.americasarmy.com/) as an example of  flash heavy site.

---

### Post by Izek on 2008-11-29
Are you sure you aren't using gnash's swf viewer or something not flashplugin-nonfree CinciBearFan?

---

### Post by CinciBearFan on 2008-11-29
> **Izek said:**
> Are you sure you aren't using gnash's swf viewer or something not flashplugin-nonfree CinciBearFan?

I thought I had uninstalled all of those. How can I confirm?
I did this:

```
sudo apt-get remove --purge mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree

```

and got this response:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
Package flashplugin-nonfree is not installed, so not removed

```


I followed this method of installing it in the first place: 
[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)


D

---

### Post by xebian on 2008-11-30
> **CinciBearFan said:**
> I thought I had uninstalled all of those. How can I confirm?
I did this:

```
sudo apt-get remove --purge mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree

```

and got this response:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
Package flashplugin-nonfree is not installed, so not removed

```


I followed this method of installing it in the first place: 
[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)


D

you can check if you have flash installed correctly by going to the Firefox menu > Tools > add-ons > and then the Plugins tab.  You should see 'Shockwave Flash 10.0 d20'

---

### Post by Sally on 2008-12-03
I'm having a recurring problem with Flash under Hardy. Apologies if this has been addressed; I read through part of this thread but it's 50+ pages long so may have missed a fix that covers my issue...

After following the instructions to install Flash 10 from script I still see the "grey box" in place of flash content when opening a new browser window. If I go to Plugins, disable/enable the Flash plugin *and* refresh the page, flash works. But I have to do this every time I open a new browser window.

Has this been reported before, and if so is there a fix? *Or* can anyone tell me if this has been addressed under Ibex?

Thanks!

---

### Post by vhozard on 2008-12-03
Since a couple of days there is a native 64 bit plugin of flash available!
It's still very beta, but I've tested it and it [COLOR="Red"]**works wonderful**[COLOR="Black"].[/COLOR][/COLOR]
Download link [COLOR="Red"]---> [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html") <---[/COLOR]

Greets Vhozard,

---

### Post by Tuliku on 2008-12-04
I just installed ubuntu 64 bit, and used synaptic to install some packages including the adobe flash plugin.
Works perfect !

For heavy flash testing try: [www.derbauer.de](www.derbauer.de)
My firefox + flashplugin had no issue's with it.

---

### Post by Sally on 2008-12-04
Thanks, Vhozard -- I installed the native plugin and it works perfectly!

Sally

---

### Post by efeurich on 2008-12-06
Awesome, worked like a charm.
Thanks!!!

---

### Post by FDF12389 on 2008-12-09
Thanks

---

### Post by osaeris on 2008-12-09
Genius again, thanks Kilz. Are you using the 64 bit alpha version of flash yourself yet ?

---

### Post by dBuster on 2008-12-09
Would it be recommended to remove the other Flash 9 install or do something different if we have already installed flash 9???

I believe I have flash 9 installed and then installed flash 10 and there are some websites such as nbc.com in which trying to watch tv shows online I get messages that I need to upgrade to the new version of flash.

---

### Post by Arup on 2008-12-09
Always advisable to totally remove older Flash before installing new Flash, also if you used x32 flash on x64 Intrepid, you need to remove nsplugin as well otherwise issues can arise.

---

### Post by Kilz on 2008-12-09
> **osaeris said:**
> Genius again, thanks Kilz. Are you using the 64 bit alpha version of flash yourself yet ?

Yes, its pretty good for an alpha. I also have no fear of troubleshooting if something blows up.

---

### Post by veeravalli on 2008-12-09
Wonderful-  Thanks!

---

### Post by Ehtetur on 2008-12-10
Hey, thanks to your script, I was able to get flash to work!! :twisted:

There was an extra step I had to do... Maybe it was because I first installed flash from the ubuntu pop-up... The one with the options to install flash, SWC <i think>, or gnash. (I chose flash)...

With FF304 on Hardy, after I ran the script, I had to create a symbolic link in the xulrunner-addons folder in order for flash to work. Once I did, it worked great.

> cd /usr/lib/xulrunner-addons/plugins/
sudo ln -s /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so .

---

### Post by The other One on 2008-12-14
Kilz, thanks for this post. I've been using your old ff32-3in1 script without any issues for so long that only now in FF 3.0.4 have I needed to look for a new flash solution. I referred to many of your posts or answers to other's posts when I 1st transitioned to Ubuntu, but never thanked you - so here it is.
You are seriously a saviour to a lot of us 64 bit users.

---

### Post by Kilz on 2008-12-14
> **The other One said:**
> Kilz, thanks for this post. I've been using your old ff32-3in1 script without any issues for so long that only now in FF 3.0.4 have I needed to look for a new flash solution. I referred to many of your posts or answers to other's posts when I 1st transitioned to Ubuntu, but never thanked you - so here it is.
You are seriously a saviour to a lot of us 64 bit users.

Your Welcome,
 I recently stopped supporting the 32bit Firefox script. It still works, but the versions of Firefox are getting old. I had planned on supporting it until 64bit sun java was released. But the 64bit open source java plugin is good. The new 64bit Alpha flash plugin was the straw.
 If what I did helped you and others run the 64bit version. It was time well spent. :D  Now if it was just as easy to kill all the fud 64bit would be more popular.

---

### Post by SeePU on 2008-12-16
What is the best way to (purge?) uninstall all the old Flash files (including nsplugin?)?  I believe I installed Flash 10 32-bit version (I thought it was 64-bit) since I used the repositories (used package installer).

I understand I am supposed to install x64 Flash 10 from the Adobe (Labs?) website?  It's a tar file?:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I understand steps to be:

1) Download:  64-bit plugin (tar file) from above website
2) Install the libflashplayer.so into /usr/lib64/mozilla/plugins and remove existing 32bit plugin.
3) Make sure you have alsa-plugins-pulseaudio.x86_64 and libcurl.x86_64 installed. *

I found #3 step at an Adobe Flash Player site.  

Please if anyone can confirm those instructions, that would be great.

So, what is the best way to uninstall the 32-bit Flash files?  Will standard uninstall commands get rid of everything?

---

### Post by Arup on 2008-12-16
Either use sudo apt-get --purge remove command or use total unistall from synaptic, make sure to remove nsplugin as well.

---

### Post by SeePU on 2008-12-16
I can't find 'libcurl.x86_64' AND/OR 'alsa-plugins-pulseaudio.x86_64'!!

I searched all the repositories.  Is there a 'How-To' for this?

I am just wondering why it has to be so hard.

---

### Post by Arup on 2008-12-16
Just remove all flash and nsplugin and unzip the flashx64, you will have a libflashplayer.so open up terminal and do a mv libflashplayer.so to /usr/lib/mozilla/plugins and then open up FF and type about plugins to see if its installed.

---

### Post by Yellow Pasque on 2008-12-18
Note that there is an updated version of the 64-bit Alpha version of Flashplayer released today (12/16/08).

---

### Post by Thelasko on 2008-12-18
> **Temüjin said:**
> Note that there is an updated version of the 64-bit Alpha version of Flashplayer released today (12/16/08).

Any ideas on what bugs were fixed?

---

### Post by Yellow Pasque on 2008-12-18
> **Thelasko said:**
> Any ideas on what bugs were fixed?
Unfortunately, there's no changelog on Adobe's site or in the release notes, just a few "known issues".

---

### Post by Arup on 2008-12-18
Few vulnerabilities were fixed.

---

### Post by Yellow Pasque on 2008-12-18
> **Arup said:**
> Few vulnerabilities were fixed.
Uhh, do you have a source on this or are you just speaking from peronal experience? Vulnerabilites? Do you mean security vulnerabilites or just functionality bugs?

---

### Post by Arup on 2008-12-18
> **Temüjin said:**
> Uhh, do you have a source on this or are you just speaking from peronal experience? Vulnerabilites? Do you mean security vulnerabilites or just functionality bugs?

[http://www.adobe.com/support/security/bulletins/apsb08-24.html](http://www.adobe.com/support/security/bulletins/apsb08-24.html)

---

### Post by Yellow Pasque on 2008-12-18
> **Arup said:**
> [http://www.adobe.com/support/security/bulletins/apsb08-24.html](http://www.adobe.com/support/security/bulletins/apsb08-24.html)
Well, that's a security advisory and it's not clear whether it applies to the 64-bit version. I was hoping you had a changelog. :\

---

### Post by SeePU on 2008-12-18
Since it doesn't mention the 64-bit version, I would assume it is referring to the 32-bit version of Flash.

Also, the 'about' or “check version” page shows I have ver. 10.0.21.1 installed.

Note:  I have Kubuntu 64-bit 8.10 installed with the Alpha Flash 64-bit version.

---

### Post by onering on 2008-12-19
I am using the Adobe "alpha" 64-bit flash player with Ubuntu 8.10.  I've been using it for a few days now and it has works great, no problems like I used to have with ndiswrapper/32 bit flash version.  

I thought I would post the steps I used to install it here, although they might be redundant to some of the previous posts, it may help someone new who just looks towards the bottom of the thread.

Here is how I installed it from a clean install of 8.10:

1) Download the 64-bit plugin for Linux here:
[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

2) Untarred and uncompressed the tarbal.  Created a plugins directory inside ~/.mozilla and copy the libflashplayer.so  file into this directory.  You can do both of these steps with the following commands in a terminal window:

```
tar zxvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
mkdir ~/.mozilla/plugins
mv libflashplayer.so ~/.mozilla/plugins
```

3)Restart Firefox and Flash should work.

4) I found these simple steps at this [link]("http://johnbokma.com/mexit/2008/11/25/64-bit-adobe-flash-ubuntu.html").

---

### Post by Arup on 2008-12-19
I have placed the libflashplayer.so /usr/lib/mozilla/plugins and it works fine with FF and Opera, wonder why Adobe is asking to create a new /.mozilla/plugins

---

### Post by w0ng on 2008-12-20
> **Temüjin said:**
> Note that there is an updated version of the 64-bit Alpha version of Flashplayer released today (12/16/08 ).
Ditto. Latest alpha works fine following updated instructions of [_H4rold's post_]("http://ubuntuforums.org/showpost.php?p=6196594&postcount=451"):
```
sudo apt-get --purge remove nspluginwrapper flashplugin-non-free
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
tar xvf libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
mkdir ~/.mozilla/plugins/
mv libflashplayer.so ~/.mozilla/plugins/
```

[quote=about:plugins]Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d21

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes[/quote]

---

### Post by Arup on 2008-12-21
Since FF is preinstalled in Ubuntu, why not move the libflahsplayer.so to /usr/lib/mozilla/plugins where other plugins are there as well instead of creating a ~/.mozilla/plugins

---

### Post by w0ng on 2008-12-21
> **Arup said:**
> Since FF is preinstalled in Ubuntu, why not move the libflahsplayer.so to /usr/lib/mozilla/plugins where other plugins are there as well instead of creating a ~/.mozilla/plugins

Where possible, I prefer to tinker around without requiring su access to make it work.

---

### Post by Arup on 2008-12-21
> **w0ng said:**
> Where possible, I prefer to tinker around without requiring su access to make it work.

Good point but it seems to be the default plugin folder and browsers like Opera look there for plugins as well so in this case, it would be a good idea to use that in case you need to use other programs that might need the plugins.

---

### Post by magawake on 2008-12-21
> **onering said:**
> I am using the Adobe "alpha" 64-bit flash player with Ubuntu 8.10.  I've been using it for a few days now and it has works great, no problems like I used to have with ndiswrapper/32 bit flash version.  

I thought I would post the steps I used to install it here, although they might be redundant to some of the previous posts, it may help someone new who just looks towards the bottom of the thread.

Here is how I installed it from a clean install of 8.10:

1) Download the 64-bit plugin for Linux here:
[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

2) Untarred and uncompressed the tarbal.  Created a plugins directory inside ~/.mozilla and copy the libflashplayer.so  file into this directory.  You can do both of these steps with the following commands in a terminal window:

```
tar zxvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
mkdir ~/.mozilla/plugins
mv libflashplayer.so ~/.mozilla/plugins
```

3)Restart Firefox and Flash should work.

4) I found these simple steps at this [link]("http://johnbokma.com/mexit/2008/11/25/64-bit-adobe-flash-ubuntu.html").

I have followed these instructions, but I keep getting this.

LoadPlugin: failed to initialize shared library /home/defult/.mozilla/plugins/libflashplayer.so [/home/default/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]


I am using Firefox 3.0.4  (X11; U; Linux i686 (x86_64); en-US; rv:1.9.04)

Any ideas?

TIA

---

### Post by Kilz on 2008-12-21
> **magawake said:**
> I have followed these instructions, but I keep getting this.

LoadPlugin: failed to initialize shared library /home/defult/.mozilla/plugins/libflashplayer.so [/home/default/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]


I am using Firefox 3.0.4  (X11; U; Linux i686 (x86_64); en-US; rv:1.9.04)

Any ideas?

TIA

Yes, you are running the 32bit version of Firefox. Please reread the "64bit Adobe Flash Alpha" section again. Please pay attention to the points and the final paragraph in that section.

---

### Post by magawake on 2008-12-21
> **Kilz said:**
> Yes, you are running the 32bit version of Firefox. Please reread the "64bit Adobe Flash Alpha" section again. Please pay attention to the points and the final paragraph in that section.

Linux ubuntu 2.6.22-16-generic #1 SMP Mon Nov 24 17:50:35 GMT 2008 x86_64 GNU/Linux

Let me reread then

---

### Post by Kilz on 2008-12-21
> **magawake said:**
> Linux ubuntu 2.6.22-16-generic #1 SMP Mon Nov 24 17:50:35 GMT 2008 x86_64 GNU/Linux

Let me reread then

Not Ubuntu, that is 64bit, your version of firefox is 32bit. > **magawake said:**
> 

I am using Firefox 3.0.4  (X11; U; Linux [COLOR="Red"]**i686**[/COLOR] ([COLOR="YellowGreen"]**x86_64**[/COLOR]); en-US; rv:1.9.04)


Red bold = The version of Firefox  
Green bold The version of the os

---

### Post by dspisak on 2008-12-22
Hello.  This is my first post to the forum.  I followed the instructions in this thread but I either do not have audio or Firefox crashes.

Here are the details.
ubuntu 8.10 amd64, kernel 2.6.27
Firefox 3.0.5 (canonical - 1.0) x86_64
Shockwave Flash 10.0 d21 (downloaded 12/20)

I first removed the 32-bit flash player by running:
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
sudo apt-get remove ia32-libs nspluginwrapper.

I then downloaded the 64-bit libflash tar file and extracted the libflashplayer.so file. I exited Firefox. I copied the .so file to the /home/.mozilla/plugins folder. I then restarted Firefox and tried these sites:
Excite/Stock watcher - quotes appear
KXPR FM streaming audio - status bar says data is transferring but no audio
YouTube - video is received, but no audio
CNN - attempts to view videos crashes firefox

I also copied the .so file to /usr/lib/mozilla/plugins with the same results.

MPlayer runs .wav, .wmv, .mpg, .mpeg, .mov, and .mp3 files so I know the audio card works.

Actually with Firefox 3.0.4 (I don't recall if it was 32 or 64-bit) everything worked great with flash 9 and 10 32-bit versions. I received an automatic update to 3.0.5 and my troubles began. Now I can't find a 32-bit version of 3.0.4 to reinstall.

Thank you for your help.

Dan

---

### Post by Yellow Pasque on 2008-12-22
dspisak,
- if you upgraded from Ubuntu 8.04, make sure the libflashsupport package isn't still installed
- try starting firefox from the terminal and going to Youtube and then CNN
- make sure the options in System -> Preferences -> Sound are set to PulseAudio (assuming you're using it)

> Now I can't find a 32-bit version of 3.0.4 to reinstall.
Firefox 3.05 fixes critical security issues. Don't run 3.04.

---

### Post by patman0623 on 2008-12-23
I'm currently running Flash through nspluginwrapper. I haven't had nearly as many issues as the crappy 64 bit version Flash released. But I can't seem to run the video from blogtv.com. It repeats every time. I get the following response from Terminal:
```
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue() 
```(x2)

Then upon navigating away, I get:
```
(npviewer.bin:2390): Gtk-CRITICAL **: gtk_style_detach: assertion 
`style->attach_count > 0' failed 
```(x6)
```
(npviewer.bin:2390): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
```

Not surprisingly, the browser crashes (gtk_widget_destroy not working, etc.)

Is this an nspluginwrapper issue or Flash issue? Is there any way I can fix this?

Thanks.

---

### Post by Kilz on 2008-12-23
> **patman0623 said:**
> 
Is this an nspluginwrapper issue or Flash issue? Is there any way I can fix this?

Thanks.

A quote from the first page.

I suggest rereading the 64bit Flash beta section again if you are asking this question. Paying attention to point 2.

Did you file a bug report with Adobe?

---

### Post by patman0623 on 2008-12-23
> **Kilz said:**
> I suggest rereading the 64bit Flash beta section again if you are asking this question. Paying attention to point 2.
Did you file a bug report with Adobe?I can't even tell who's bug it is (nspluginwrapper or adobe) to file the report, let alone figure out how to do so - and something makes me think adobe would be less than sympathetic to a vague bug report run on an 32 bit emulator. Nonetheless I will make an attempt, I guess.

Does your browser crash if you go to blogtv? If so, I guess I'll know which.

---

### Post by dspisak on 2008-12-23
> **Temüjin said:**
> dspisak,
- if you upgraded from Ubuntu 8.04, make sure the libflashsupport package isn't still installed
- try starting firefox from the terminal and going to Youtube and then CNN
- make sure the options in System -> Preferences -> Sound are set to PulseAudio (assuming you're using it)

Firefox 3.05 fixes critical security issues. Don't run 3.04.

libflashsupport...
8.10 is a clean install onto a new paritition.  libflashsupport is not installed.

start FF in Terminal...
No difference.  No youtube audio.  CNN video crashes FF.

PulseAudio...
I installed PulseAudio and set the Sound options to it.  No difference.  Same problems.  Sound/Test gives error messages.  Now ICAClient, used to log-on to work, does not work.  I un-installed Pulse Audio and reset the Sound options to AutoDetect.  Sound/Test now works fine, no errors.  ICAClient still in-operative.

I have been running 3.4.0 on my laptop for several weeks without problems.  The laptop runs 8.10, i386 version.

Thank you for your help, but I am very frustrated.  I have been to many websites and have followed their various suggestions.  None of them have worked.  I could probably remove 8.10 amd64 and install the i386 version, but why should I do that?  I already have xpPro on another partition and I do not have these problems.

FWIW, I filed a bug report at Adobe.

Here is an update.  I restarted the computer with xpPro and used it for several hours.  I then restarted with ubuntu and guess what... There is audio on KXPR-FM and on YouTube.  CNN videos still crash Firefox.  However, Citrix ICA Client no longer works on Firefox.  I'll keep on trying but any ideas are appreciated.

12/28 update:
Citrix Client is back up and running (curiously, it does not show on firefox/plugins).  Hooray!  Certain websites, CNN.com, Bose.com, Samsung.com still crash which I think is a 64-bit Flash related problem.  I also run 8.10-i386 on another partition and 32-bit Flash 10.0r15 does not crash these websites.

Thanks.

Dan

---

### Post by dBuster on 2008-12-28
> **w0ng said:**
> Ditto. Latest alpha works fine following updated instructions of [_H4rold's post_]("http://ubuntuforums.org/showpost.php?p=6196594&postcount=451"):
```
sudo apt-get --purge remove nspluginwrapper flashplugin-non-free
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
tar xvf libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
mkdir ~/.mozilla/plugins/
mv libflashplayer.so ~/.mozilla/plugins/
```

Thanks for this post!!!  This thread took me long enough to read through the 50plus pages but when I got to this one it was the charm!!  I no longer have firefox crashing when I go to a page with flash on it!  USAToday displays in the upper right corner properly now.  What a life saver!!!  Now time to go tackle why java is not working...  hmmf 

But thanks for this post!!!

---

### Post by Raffles10 on 2008-12-30
I haven't read the 50 pages of this topic, so if I'm teaching people to suck eggs please ignore this post completely.:wink:

I installed 'ubuntu-8.10-desktop-amd64.iso' for the first time yesterday and after installing ubuntu-restricted-extras, i found that flash, java, mp3, etc were all working perfectly, except DVD playback, I'll have to find libdvdcss2 for that.

so just doing:

```
sudo apt-get install ubuntu-restricted-extras
```

did it for me.:D

btw ubuntu-restricted-extras is version 25.

---

### Post by Kilz on 2008-12-30
> **Raffles10 said:**
> I haven't read the 50 pages of this topic, so if I'm teaching people to suck eggs please ignore this post completely.:wink:

I installed 'ubuntu-8.10-desktop-amd64.iso' for the first time yesterday and after installing ubuntu-restricted-extras, i found that flash, java, mp3, etc were all working perfectly, except DVD playback, I'll have to find libdvdcss2 for that.

so just doing:

```
sudo apt-get install ubuntu-restricted-extras
```

did it for me.:D

btw ubuntu-restricted-extras is version 25.

The problem is, it never stays working for long. Every once in awhile we get someone who thinks its solved for good.
The first time was in Gutsy. If it makes it 6 months Ill agree with you.
Another point is, you may have a 32bit flash and an open source java. Aalso the 64bit plugins are here, but I have no idea if they will make Jaunty. If not hopefully we will see 64bit flash in jaunty +1's repositories and have some stability.

---

### Post by Schulu on 2008-12-30
Hi!

I'm using Intrepid Ibex with the kubuntu-resticted-extras and your install script for flash worked like a charm. However your script for java didn't do its job correctly. It seems the kubuntu-restricted-extras added also the icedtea6-plugin which your script doesn't remove. So I added the following lines and then it worked:
```
## First we uninstall and remove all the existing java plugins
sudo apt-get -y purge icedtea6-plugin
```

Maybe you should add this to your script. 

Greetings from Germany
Toby

---

### Post by Kilz on 2009-01-02
> **Schulu said:**
> Hi!

I'm using Intrepid Ibex with the kubuntu-resticted-extras and your install script for flash worked like a charm. However your script for java didn't do its job correctly. It seems the kubuntu-restricted-extras added also the icedtea6-plugin which your script doesn't remove. So I added the following lines and then it worked:
```
## First we uninstall and remove all the existing java plugins
sudo apt-get -y purge icedtea6-plugin
```

Maybe you should add this to your script. 

Greetings from Germany
Toby

Thanks, I added it, and upgraded to the b03 java release.

---

### Post by ivan-frankfurt on 2009-01-03
I also put the .so file in /usr/lib/mozilla/plugins as there's 2 users on the computer.
The plugin works well with most flash content (including youTube) but Firefox dies when attempting to show the Flash content from this website

[http://marleyandmemovie.com/](http://marleyandmemovie.com/)

starting firefox from konsole does not show much information or a call stack, only a "Illegal instruction" error.

I would be interested to know if other people can see that website.
I have Kubuntu 8.10, latest updates, kernel is 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64

cheers
Ivan

---

### Post by Kilz on 2009-01-03
> **ivan-frankfurt said:**
> I also put the .so file in /usr/lib/mozilla/plugins as there's 2 users on the computer.
The plugin works well with most flash content (including youTube) but Firefox dies when attempting to show the Flash content from this website

[http://marleyandmemovie.com/](http://marleyandmemovie.com/)

starting firefox from konsole does not show much information or a call stack, only a "Illegal instruction" error.

I would be interested to know if other people can see that website.
I have Kubuntu 8.10, latest updates, kernel is 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64

cheers
Ivan

Please tell me exactly what plugin you attempted to install as well as a link to the bug report you filed on this issue.
Type ```
about:plugins
```, hit enter, copy the name of the flash plugin back here.

---

### Post by ivan-frankfurt on 2009-01-03
> **Kilz said:**
> Please tell me exactly what plugin you attempted to install as well as a link to the bug report you filed on this issue.
Type ```
about:plugins
```, hit enter, copy the name of the flash plugin back here.

Apologies, I was unclear.
I installed the 64 bit plugin from Macromedia, i.e. as root
cd /usr/lib/mozilla/
mkdir plugins
cd plugins/
tar xzvf /tmp/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d21

I'll log a bug tomorrow, checking out for tonight.

thanks and best regards

---

### Post by mad_prince on 2009-01-04
hello, my FF doesen't see libflashplugin.so I've copied it to all of three FireFox plugins path and nothing. I don't have flash players on the websites like youtube.com. What is more funny, Opera with its plugin path set on '/usr/lib/mozilla/plugins' sees and uses flashplugin without any problems.

In FF in about:plugins I don't have anything about flash. I've tried to install nonfree, but error 404 occured

---

### Post by Kilz on 2009-01-04
> **mad_prince said:**
> hello, my FF doesen't see libflashplugin.so I've copied it to all of three FireFox plugins path and nothing. I don't have flash players on the websites like youtube.com. What is more funny, Opera with its plugin path set on '/usr/lib/mozilla/plugins' sees and uses flashplugin without any problems.

In FF in about:plugins I don't have anything about flash. I've tried to install nonfree, but error 404 occured

If you are asking for help please read the How to get help section of the first post.

---

### Post by dBuster on 2009-01-04
I too am having flash issues and that Marleyandme website is a prime example.  It totally shuts down firefox, closes it and then when I reopen and restore the prior session I have to be quick to close that tab...

Per request here is my about:plugins flash info

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d21

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r15

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

---

### Post by Kilz on 2009-01-04
> **dBuster said:**
> I too am having flash issues and that Marleyandme website is a prime example.  It totally shuts down firefox, closes it and then when I reopen and restore the prior session I have to be quick to close that tab...

Per request here is my about:plugins flash info

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d21

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r15

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

Would you happen to have a link to the bug report you filled out at Adobe?

---

### Post by Arup on 2009-01-05
I see npwrapper and if I am not mistaken that means the x32 version of Flash is still left over and thats why the problem.

---

### Post by dBuster on 2009-01-05
> **Arup said:**
> I see npwrapper and if I am not mistaken that means the x32 version of Flash is still left over and thats why the problem.

I had removed manually the npwrapper and then ran the script and it was installed with the script...  I can remove it again if that is the recommendation... 

Taken from the getflash10 script...

```
#wrap the plugin
sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo ln -s /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

```

---

### Post by dBuster on 2009-01-05
> **Kilz said:**
> Would you happen to have a link to the bug report you filled out at Adobe?

Sorry I have not filled out a bug report myself but most certainly can if no one else has done so.  Or is it recommended that everyone that is having this issue file a report?

Thanks for all the assistance Kilz!  It is most appreciated!!!:popcorn:

---

### Post by Arup on 2009-01-05
> **dBuster said:**
> I had removed manually the npwrapper and then ran the script and it was installed with the script...  I can remove it again if that is the recommendation... 

Taken from the getflash10 script...

```
#wrap the plugin
sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo ln -s /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

```

No need for any script, just do a sudo apt-get --purge remove nsplugin and then do a sudo mv libflashplayer.so /usr/lib/mozila/plugins and you are all set, works like a charm on both Opera and FF and there is no issue with flash on any site here.

---

### Post by koe1974 on 2009-01-05
I just used both the GetFlash and GetJava on 8.10 with FF 3.0.5 and the flash worked wonderfully however there seems to be a problem with the GetJava script.

There is a line:
```
sudo mv jre1.6.0_12 /usr/lib/jvm/
```
But it does not result in a folder /usr/lib/jvm/jre1.6.0_12 being created. I have no idea why as the script was moving fast and I did not notice any errors.

As a result the script makes the following symlinks but they don't point to the correct place.

If you change the next two lines:

```
sudo ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib/firefox-addons/plugins/
```

to:

```
sudo ln -s /usr/lib/jvm/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/lib/jvm/lib/amd64/libnpjp2.so /usr/lib/firefox-addons/plugins/
```
Then everything works great and you have a 64bit java plugin for firefox!

Thanks for the scripts!

---

### Post by dBuster on 2009-01-06
> **koe1974 said:**
> I just used both the GetFlash and GetJava on 8.10 with FF 3.0.5 and the flash worked wonderfully however there seems to be a problem with the GetJava script.

There is a line:
```
sudo mv jre1.6.0_12 /usr/lib/jvm/
```
But it does not result in a folder /usr/lib/jvm/jre1.6.0_12 being created. I have no idea why as the script was moving fast and I did not notice any errors.

As a result the script makes the following symlinks but they don't point to the correct place.

If you change the next two lines:

```
sudo ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib/firefox-addons/plugins/
```

to:

```
sudo ln -s /usr/lib/jvm/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/lib/jvm/lib/amd64/libnpjp2.so /usr/lib/firefox-addons/plugins/
```
Then everything works great and you have a 64bit java plugin for firefox!

Thanks for the scripts!

The script created the folders it called for on my system.  If I were to follow your recommendation it would not be pointing to the correct location...

While looking for those folders I did notice I have a file by the name of .java-6-sun.jinfo and when I view that file everything in it is pointing to the java-6-sun-1.6.0.07 folder...  Which it also includes something referring to the plugins.  Not sure if this may be the cause of my not being able to use the jre1.6.0_12 or not.  But I thought to mention it...

---

### Post by Kilz on 2009-01-07
> **koe1974 said:**
> I just used both the GetFlash and GetJava on 8.10 with FF 3.0.5 and the flash worked wonderfully however there seems to be a problem with the GetJava script.

There is a line:
```
sudo mv jre1.6.0_12 /usr/lib/jvm/
```

Then everything works great and you have a 64bit java plugin for firefox!

Thanks for the scripts!

Thanks for telling me about the error you had. I was unable to duplicate it. But did change the install script slightly. Instead of using mv which can be used to rename things, I changed it to cp -r for a recursive copy.

---

### Post by crazyfuturamanoob on 2009-01-07
Official Adobe Flash Player for firefox tells me "unsupported architecture blablabla can't install".

Does this guide work on Ubuntu 8.10 amd64? All other installers refuse.

---

### Post by Kilz on 2009-01-07
> **crazyfuturamanoob said:**
> Official Adobe Flash Player for firefox tells me "unsupported architecture blablabla can't install".

Does this guide work on Ubuntu 8.10 amd64? All other installers refuse.

Are you sure you have a amd64 compatible chip and/or installed the 64bit os??

---

### Post by upsidedown010 on 2009-01-07
thank you good sir! thank you so much!

---

### Post by peregrine290 on 2009-01-12
Attempted to use [COLOR="SandyBrown"]Live CD[/COLOR] x86 64-bit Jaunty Jackalope, downloaded and burnt today 12 January 2009 from official site.  

1) Still stuck with a screen resolution of only 800x600.  Why only this ridiculous screen resolution?  Some earlier versions had sensible resolutions that were automatically detected -- that ceased, though, with Hardy Heron (also 800x600).  

2) Attempt to get Adobe Flash Player for AMD64 chip.  At console, as advised: >>sudo apt-get install nspluginwrapper flashplugin-nonfree<<; result -- "E: Couldn't find package nspluginwrapper."  

Any suggestions -- or should I just give up...?

---

### Post by Clancy_s on 2009-01-17
For the record, on a 64 bit install that's an update from 7.10 via 8.04.  I have been using 32 bit flash and java via the scripts provided by Kilz back when I first installed 7.10

About an hour ago I ran the 2 scripts provided to install 64 bit flash and java.  I've done a bit of browing around, everywhere I tested, including cnn and the marley site work OK for me, so the problems aren't universal.

(I had to temporarily disable noscript and adblock plus to get cnn, just allowing cnn didn't do it))

Thanks for providing the scripts. :)

(One odd thing - when I clicked on the 'thank you' button in the first post I got a message from the forums saying I did't have permission to access this page, even with noscript and adblock turned off.  It's the only thanks icon I see.  I used to see one, I didn't notice it had disappeared til now.)

---

### Post by InspiredIndividual on 2009-01-17
> **Kilz said:**
> (...) There are options for everything.

**[SIZE="4"][COLOR="Sienna"]64bit Adobe Flash Alpha and Java Beta[/COLOR][/SIZE]**
(...)
[COLOR="Sienna"][SIZE="4"]**Intrepid Ibex**[/SIZE][/COLOR]
(...)
[COLOR="Sienna"][SIZE="4"]**32bit Firefox, Flash and Java**[/SIZE][/COLOR]


I'm sorry for my misunderstanding, but I'm a bit confused now. I just did a fresh install of Intrepid Ibex 64-bit on my laptop, so I followed the instructions under 'Intrepid Ibex'. Everything went without a hitch, great. Does this mean I have 32-bit Flash installed now, as opposed to the 64bit if I had followed the instructions under '64bit Adobe Flash Alpha'? That seems strange, as it says under '32bit Firefox, Flash and Java' that this would be a last resort. Or are there different 64bit Flash plugins, an official one from Adobe and an unofficial one from the repositories?  
:confused:

---

### Post by Kilz on 2009-01-18
> **InspiredIndividual said:**
> I'm sorry for my misunderstanding, but I'm a bit confused now. I just did a fresh install of Intrepid Ibex 64-bit on my laptop, so I followed the instructions under 'Intrepid Ibex'. Everything went without a hitch, great. Does this mean I have 32-bit Flash installed now, as opposed to the 64bit if I had followed the instructions under '64bit Adobe Flash Alpha'? That seems strange, as it says under '32bit Firefox, Flash and Java' that this would be a last resort. Or are there different 64bit Flash plugins, an official one from Adobe and an unofficial one from the repositories?  
:confused:

1.The 64bit plugins are in Alpha and Beta testing. I dont recommend everyone use them right now.

2.'32bit Firefox, Flash and Java' refers to an older script of mine that installed everything 32bit, even the browser. 

3. The Intrepid instructions/script use packages from the Ubuntu repositories. By following them you are installing something the developers designed to work. 

4. As long as it works, dont second guess yourself. There is no performance or other thing you are missing out on.

---

### Post by InspiredIndividual on 2009-01-19
Thanks for the information. And thanks for the installation instructions! I had Java and Flash10 running perfectly with OpenJDK and flashplugin-nonfree from the repositories. Nevertheless, I decided to try the 64bit install scripts as well. Everything is running without a hitch.

---

### Post by digital-daniel on 2009-01-21
Hello,

I have Ubuntu 8.10 and have had a few problems opening certain websites: [www.fastweb.it](www.fastweb.it) and [www.samsung.com](www.samsung.com). With both of these sites the page stays white and fails to load. There is no error just a "Waiting for website" message. 

I think this may have something to do with Java and have posted elsewhere  but so far no luck. I'm using firefox3.0.5 and have the icetea plug in and I'm on a AMD64 system. 

Would the java plug in make a difference? If I do it and it doesn't work how would I uninstall? 

Daniel

PS I'm only on week 3 with linux so talk to me as if I'm stupid.;)

---

### Post by WijbrandSchaap on 2009-01-21
I had the same, but in most cases (YouTube etc) it helps if I restart FF. Strangely enough that does the trick every time. The only site which doesn't work that way is The Daily Show. Have to view that in Google Chrome (Crossover) or Opera. Don't think this helps, but hey, it's worth a try.
:-)
Wijbrand

---

### Post by ibuclaw on 2009-01-22
> **Kilz said:**
> 1.The 64bit plugins are in Alpha and Beta testing. I dont recommend everyone use them right now.

2.'32bit Firefox, Flash and Java' refers to an older script of mine that installed everything 32bit, even the browser. 

3. The Intrepid instructions/script use packages from the Ubuntu repositories. By following them you are installing something the developers designed to work. 

4. As long as it works, dont second guess yourself. There is no performance or other thing you are missing out on.

Yep, but that still doesn't stop people from making them ;)

I'm on hardy, and nswrapper has seemingly failed completely, so I pulled the tar from the adobe site, replaced the 'i[3456]86' glob match with 'x86_64' in the 'flashplayer-installer' script (run **chmod +w flashplyer-installer** to make it writeable) and put the 64bit pre-release flash plugin in the install folder instead of the 32bit one.

Then ran **./flashplayer-installer** (without sudo) and it installed it into my ~/.mozilla directory, flash has been working since :)

I would upload a gunzip of it, but I don't think binary blobs are allowed on this forum.

Regards
Iain

---

### Post by Kilz on 2009-01-22
> **tinivole said:**
> Yep, but that still doesn't stop people from making them ;)

I'm on hardy, and nswrapper has seemingly failed completely, so I pulled the tar from the adobe site, replaced the 'i[3456]86' glob match with 'x86_64' in the 'flashplayer-installer' script (run **chmod +w flashplyer-installer** to make it writeable) and put the 64bit pre-release flash plugin in the install folder instead of the 32bit one.

Then ran **./flashplayer-installer** (without sudo) and it installed it into my ~/.mozilla directory, flash has been working since :)

I would upload a gunzip of it, but I don't think binary blobs are allowed on this forum.

Regards
Iain

All to much work to me. I'd simply download the simple install script on the front page and use it instead of modifying the Adobe one. If you want speed use gksudo nautilus and delete the old plugin and copy the new one in place without a script.

---

### Post by xoros on 2009-01-22
> **tinivole said:**
>  **./flashplayer-installer** 

What is that actually doing?  Just placing the plugin into the mozilla plugins folder like Kilz is doing?

---

### Post by jallp82 on 2009-01-23
Ok so I am using Xubuntu 8.04 Hardy Heron.

I downloaded both files to install the alpha and beta, java and flash but when I double click on the files after I have extracted them they do nothing, nothing opens at all.

I'm completely new to any Linux what so ever. :( I apologize now if I'm just retarded and am doing something wrong.



[B][COLOR="Lime"]
I got it just searched on yahoo and found an easy way to do it just ignore my message :)[/COLOR][/B]

---

### Post by evencoil on 2009-01-23
Fresh install of Intrepid 8.10 64-bit. Installed nspluginwrapper and flashplugin-nonfree but had the grey box problem.

This worked seamlessly:

> 
It has been suggested that creating a config file may help
Code:

sudo mkdir /etc/adobe
sudo gedit /etc/adobe/mms.cfg

Add the line
WindowlessDisable = 1
Then save the file.

Thanks!

---

### Post by HalNineThousand on 2009-01-23
So nobody has it working on Konqueror on 64 bit yet?  No work-arounds from Ubuntu?

Frustrating!

---

### Post by xebian on 2009-01-23
> **HalNineThousand said:**
> So nobody has it working on Konqueror on 64 bit yet?  No work-arounds from Ubuntu?

Frustrating!

The 64-bit flash plugin works like a charm in konqueror.

---

### Post by HalNineThousand on 2009-01-24
> **xebian said:**
> The 64-bit flash plugin works like a charm in konqueror.

On Intrepid?  I've never seen it come close to working.  Is it new?  what packages did you install and did you have to do anything besides just install packages?

---

### Post by dcstar on 2009-01-24
Just a minor "gotcha" when using the script to install the Flash 10 on xxxxxGutsyxxxxx I meant Hardy! :

I had another repository that had a later version of nspluginwrapper, but I did not have the authentication key for this repository - so if I installed anything from it I just had to manually acknowledge this situation, but the script didn't like this and wouldn't install the nspluginwrapper package.

I got around it by temporally disabling this this repository and allowing the script to use the "standard" repositories, and then enabling it and allowing an upgrade.

---

### Post by Kilz on 2009-01-24
> **dcstar said:**
> Just a minor "gotcha" when using the script to install the Flash 10 on Gutsy:

I had another repository that had a later version of nspluginwrapper, but I did not have the authentication key for this repository - so if I installed anything from it I just had to manually acknowledge this situation, but the script didn't like this and wouldn't install the nspluginwrapper package.

I got around it by temporally disabling this this repository and allowing the script to use the "standard" repositories, and then enabling it and allowing an upgrade.

Thanks. That script is quite old. Not much life left in Gutsy, it will reach end of life around the release of Jaunty.

---

### Post by dcstar on 2009-01-25
> **Kilz said:**
> Thanks. That script is quite old. Not much life left in Gutsy, it will reach end of life around the release of Jaunty.

Ahem, isn't 8.04 a LTS release (desktop supported until April 2011, Jaunty will be gone long before 8.04 will):

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

"Reports of my demise are greatly exaggerated"......          :tongue:

---

### Post by Izek on 2009-01-25
> **dcstar said:**
> Ahem, isn't 8.04 a LTS release (desktop supported until April 2011):

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

"Reports of my demise are greatly exaggerated"......          :tongue:

You/he said Gutsy, not Hardy.

---

### Post by Kilz on 2009-01-25
> **Izek said:**
> You/he said Gutsy, not Hardy.

Yes, Gutsy is Ubuntu 7.10 not 8.04. I was surprised to even hear of someone running Gutsy at this late in its life. Most users should imho have moved or started the process of moving off Gutsy with only about 3 months left.
Also (this is especially mho) Gutsy, while a good release, was not a Great release. Only Edgy was worse, But I started with Breezy (only ran it a few days), so Im not sure of hoary or warty.
Hardy is at least as good, Intrepid is on par with Dapper and Feisty. I hope we dont get another dog after a Great release like I have noticed has happened in the past.
I probably wont be installing Jaunty for myself. My file server is running Hardy, my daughters school is running Hardy, and Intrepid will do for my Ubuntu install for a long time.

---

### Post by Hooya on 2009-01-25
I tried everything in this thread only to find flash never loading at all in firefox.  Eventually I just went to Adobe's site and found a link that seems to be nowhere else on the internet:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

At the bottom there's a .tar.gz file containing a prebuilt 64 bit version of libflashplayer.so.  Extract (in Hardy) to /usr/lib/firefox-addons/plugins and /usr/lib/mozilla/plugins directories.

Flash now works.  No wrapper, no complicated scripts or steps.

---

### Post by Kilz on 2009-01-25
> **Hooya said:**
> I tried everything in this thread only to find flash never loading at all in firefox.  Eventually I just went to Adobe's site and found a link that seems to be nowhere else on the internet:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

At the bottom there's a .tar.gz file containing a prebuilt 64 bit version of libflashplayer.so.  Extract (in Hardy) to /usr/lib/firefox-addons/plugins and /usr/lib/mozilla/plugins directories.

Flash now works.  No wrapper, no complicated scripts or steps.

I guess you didnt look at the top of the first post in this thread.

**[SIZE="4"][COLOR="Sienna"]64bit Adobe Flash Alpha and Java Beta[/COLOR][/SIZE]**

That section gives all the info needed, and an install script.

---

### Post by Hooya on 2009-01-25
It was actually the first thing I tried.  I don't know why it didn't work, but it didn't.  Manually download and putting the thing in there did work, however.

---

### Post by xoros on 2009-01-25
> **Hooya said:**
> I tried everything in this thread only to find flash never loading at all in firefox.  Eventually I just went to Adobe's site and found a link that seems to be nowhere else on the internet:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

At the bottom there's a .tar.gz file containing a prebuilt 64 bit version of libflashplayer.so.  Extract (in Hardy) to /usr/lib/firefox-addons/plugins and /usr/lib/mozilla/plugins directories.

Flash now works.  No wrapper, no complicated scripts or steps.

I made this post awhile ago which contained that link and some other good links: [http://ubuntuforums.org/showthread.php?p=6597556#1](http://ubuntuforums.org/showthread.php?p=6597556#1)

---

### Post by xebian on 2009-01-25
> **HalNineThousand said:**
> On Intrepid?  I've never seen it come close to working.  Is it new?  what packages did you install and did you have to do anything besides just install packages?

Install the 64-bit flash, make sure you have konqueror-nsplugins  installed, and then configure konqueror -> plugins.

---

### Post by dcstar on 2009-01-25
> **Izek said:**
> You/he said Gutsy, not Hardy.

Whoops, I was thinking of 8.04 but got the name wrong in the original post...... :redface:

---

### Post by Yashiro on 2009-01-26
If you're using the 64bit bit plug-in you absolutely **do not** want any other flash players or nsplugin plug-ins running.

The 64bit one still crashes alot too. Just be aware of that.

---

### Post by HalNineThousand on 2009-01-26
> **xebian said:**
> Install the 64-bit flash, make sure you have konqueror-nsplugins  installed, and then configure konqueror -> plugins.

I see no reference to 64 bits in the package.  Are you using, specifically, the package flashplugin-nonfree?  I have that package installed along with konqueror-nsplugins.  There's also nothing to do in Konqueror in config, under Plugins.  I can scan for plugins and it recognizes Flash, but it never works.

---

### Post by Kilz on 2009-01-26
> **HalNineThousand said:**
> I see no reference to 64 bits in the package.  Are you using, specifically, the package flashplugin-nonfree?  I have that package installed along with konqueror-nsplugins.  There's also nothing to do in Konqueror in config, under Plugins.  I can scan for plugins and it recognizes Flash, but it never works.

The 64bit plugin is not a Ubuntu package. You can read about it on the first post of this thread. You can either follow the links, download a tarball, and manually place the file or download the script and run it.

---

### Post by dBuster on 2009-01-28
Here is one for everyone...

Jaunty Jackalope 64bit Alpha 3 - Java 64, Flash 64

Morning updates today kicked the sound out of Firefox!  Any flash video or java applet with sound such as games have no sound.  Sound functions fine in Ubuntu however in Firefox, it is non-existent. 

Tried to re-install pulseaudio - no change
Tried to re-install the flash64 plugin - no change

At a loss but want the sound back, any ideas?

Everything was working fine until the updates.  Sound was splendid and movies were smooth.  Now there is no sound and videos are a little on the choppy side.  I understand that I am not running final releases of anything, however with this new laptop this is the only combination that would run.

---

### Post by Kilz on 2009-01-29
> **dBuster said:**
> Here is one for everyone...

Jaunty Jackalope 64bit Alpha 3 - Java 64, Flash 64

Morning updates today kicked the sound out of Firefox!  Any flash video or java applet with sound such as games have no sound.  Sound functions fine in Ubuntu however in Firefox, it is non-existent. 

Tried to re-install pulseaudio - no change
Tried to re-install the flash64 plugin - no change

At a loss but want the sound back, any ideas?

Everything was working fine until the updates.  Sound was splendid and movies were smooth.  Now there is no sound and videos are a little on the choppy side.  I understand that I am not running final releases of anything, however with this new laptop this is the only combination that would run.

This sticky, in fact the whole 64bit section is for release versions. Where everything is expected to work.
Jaunty is still under development. As such everything is not expected to work. There could be a number of reasons including different versions of some packages conflicting with the requirements of other packages.
The place to discuss and ask for help for such issues is in the [development section of the forum]("http://ubuntuforums.org/forumdisplay.php?f=352"). In fact it would be the first and only place to look. 
I would also [file bug reports]("https://launchpad.net/ubuntu/+filebug") on each and every issue so that the developers (who dont read the forums as is plainly written at the top of that section) can fix the issue. After all that is why a Alpha exists. Not to give you a new piece of software to play with, but to work the bugs out of the next version.

---

### Post by dBuster on 2009-01-29
> **Kilz said:**
> This sticky, in fact the whole 64bit section is for release versions. Where everything is expected to work.
Jaunty is still under development. As such everything is not expected to work. There could be a number of reasons including different versions of some packages conflicting with the requirements of other packages.
The place to discuss and ask for help for such issues is in the [development section of the forum]("http://ubuntuforums.org/forumdisplay.php?f=352"). In fact it would be the first and only place to look. 
I would also [file bug reports]("https://launchpad.net/ubuntu/+filebug") on each and every issue so that the developers (who dont read the forums as is plainly written at the top of that section) can fix the issue. After all that is why a Alpha exists. Not to give you a new piece of software to play with, but to work the bugs out of the next version.

No I am not using the Jaunty alpha because as you put "a new piece of software to play with," but rather it is the only version that would boot up on this new laptop since the old laptop took a dive and I am not going to use another distro other than Ubuntu!  

I was looking in this thread for feelers as to any sound issues that may have plagued the Intrepid or Hardy users that I might be able to give a try on Jaunty.  Some work and some do not.  The scripts in this thread for Java and Flash worked like a charm though.

And by the way I have a post in that thread as well...

---

### Post by Shii on 2009-01-31
Is there an issue that would cause YouTube to work but Google Video/Hulu to segfault? I can't seem to find any documentation of this.

edit: This is weird... the issue seems to have disappeared when I logged out and back in.

---

### Post by shane4stef on 2009-02-02
Once again my old friend killz has done it . The new 64bit Java and flash actually work like a charm. Killz scripts make everything painless to install as usual. Your a real credit to the Ubuntu community . I`m sure this wont be the last time I thank you for your excellent work.

---

### Post by johnjohn2 on 2009-02-04
Thanks dude,working perfectly

cheers
john

---

### Post by johnjohn2 on 2009-02-04
> **shane4stef said:**
> Once again my old friend killz has done it . The new 64bit Java and flash actually work like a charm. Killz scripts make everything painless to install as usual. Your a real credit to the Ubuntu community . I`m sure this wont be the last time I thank you for your excellent work.

Northamptonians are growing on here

---

### Post by johnjohn2 on 2009-02-04
> **Shii said:**
> Is there an issue that would cause YouTube to work but Google Video/Hulu to segfault? I can't seem to find any documentation of this.

edit: This is weird... the issue seems to have disappeared when I logged out and back in.

In a sense no

---

### Post by johnjohn2 on 2009-02-04
> **dBuster said:**
> No I am not using the Jaunty alpha because as you put "a new piece of software to play with," but rather it is the only version that would boot up on this new laptop since the old laptop took a dive and I am not going to use another distro other than Ubuntu!  

I was looking in this thread for feelers as to any sound issues that may have plagued the Intrepid or Hardy users that I might be able to give a try on Jaunty.  Some work and some do not.  The scripts in this thread for Java and Flash worked like a charm though.

And by the way I have a post in that thread as well...

What laptop make is it as i have had the same issues as you and only jaunty would work

---

### Post by dBuster on 2009-02-05
> **johnjohn2 said:**
> What laptop make is it as i have had the same issues as you and only jaunty would work

It is a Compaq CQ60-215dx that I have but I now have it working smoothly with the recent morning updates..

---

### Post by northwestuntu on 2009-02-06
thanks kilz!!!

---

### Post by mad_max0204 on 2009-02-14
I installed 64bit flash and it works great. There are even no problems with multiple youtube videos in firefox.

One thing thou happened. Since I installed 64bit flash (I know its beta) I have some problems.
When I start my computer and when I log into ubuntu I get the panel but desktop is empty and I cant left/right click on it.
Is there anyone with simmilar problem and how can I see what things are being loaded and were it gets an error.
When I restart x with alt+ctrl+backspace everything is fine.

---

### Post by mkarnicki on 2009-02-15
Where then heck did the "THANK YOU !!! " button go?

---

### Post by Pluscom on 2009-02-15
My Toshiba A215 (AMD64) runs very well on the 64 bit version of 8.10. except I could not get the flash player to install from Adobe (wrong architecture).  Being dumb as a rock I had not realised that gnash and flashplugin-nonfree can be installed using synaptic. :KS

---

### Post by pejobe on 2009-02-15
Flash cease to work after some time. I have filed a bug report at:

[http://bugs.launchpad.net/ubuntu/+bug/329942]("http://bugs.launchpad.net/ubuntu/+bug/329942")

Left is a grey box where the film was.

Output of :~$ ls -al /usr/lib/mozilla/plugins/
total 8
drwxr-xr-x 2 root root 4096 2009-02-15 19:26 .
drwxr-xr-x 4 root root 4096 2008-10-29 22:15 ..
lrwxrwxrwx 1 root root   37 2008-12-20 17:25 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   44 2008-11-15 09:36 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   42 2008-11-15 09:36 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   44 2008-11-15 09:36 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   50 2008-11-15 09:36 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   26 2009-01-14 08:59 nppdf.so -> /var/lib/acroread/nppdf.so
lrwxrwxrwx 1 root root   57 2008-11-23 09:56 npwrapper.libflashplayer.so -> /var/lib/flashplugin-nonfree//npwrapper.libflashplayer.so
lrwxrwxrwx 1 root root   37 2008-11-21 18:15 npwrapper.nppdf.so -> /var/lib/acroread//npwrapper.nppdf.so

output of:
~$ ls -al /usr/lib/firefox-addons/plugins
total 8
drwxr-xr-x 2 root root 4096 2009-02-15 18:03 .
drwxr-xr-x 5 root root 4096 2008-10-29 22:13 ..
lrwxrwxrwx 1 root root   43 2009-02-15 18:03 libnpjp2.so -> /opt/java/jre1.6.0_12/lib/amd64/libnpjp2.so

Recently upgraded to firefox 3.06 and I think the problem started after that.

---

### Post by TonyFordz on 2009-02-18
Hey thank you very much for the Flash help I been searching like crazy trying to find a working solution to the flash bug for 7.10 64-bit because for what ever reason 8.10 refused to install on my PC which is an AMD Quad Core 9550 CPU, and after trying 8 different post solutions on a few different sites this is the only one that worked.

Now I get to search for a working java solution lol because this one didn't do it for me...

---

### Post by muziqaz on 2009-02-23
thanks for how to's. I've been cursing adobe for not beeing able to get out 64bit flash.
now, on to sound problem solving :D

---

### Post by Yellow Pasque on 2009-02-25
An update to the native 64-bit Alpha Flash player was released recently (2/24/09)
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I'm not sure what's included in this update, but I suspect it's only critical/security fixes.

---

### Post by 3Miro on 2009-02-25
I has issues installing flash on my Kubuntu 8.10 KDE 4.2 It gave me an md5sum error. The solution for me was:

-install the flash-nonfree package and get the md5sum error
-go to adobe and download the tar-ball for flash from their web-page
-go to (cd /var/lib/dpkg/info/)
-edit the installation script (sudo pico flashplugin-nonfree.postinst) and put the correct md5sums for the tar-ball that I downloaded from Adobe.
-to get the correct md5sums, open a new terminal and go to the folder where the tar-ball from Adobe was installed. Use md5sum xxxx.tar, then extract it and do the same for libflashplayer.so.
-in the terminal: sudo dpkg-reconfigure flashplugin-nonfree

Interestingly enough, I got a system76 64-bit laptop with flash preinstalled, I don't know how they did it, but it works flawlessly. Both running from Firefox and Totem.

Previously (as of a month ago) I had no problem installing flash on my 64-bit ubuntu on my desktop (I made a complete reinstall and reconfiguration of my entire system since then). I used the repository.

Firefox crashes on my KDE desktop, but that may be a KDE vs Gnome issue.

The new repository ran flawlessly, I even have flash in Konqueror.

---

### Post by gfenton on 2009-02-25
First post but I truly hope it will help until Adobe pulls their finger out.

I have made a 64 bit .deb package containing the latest libflashplayer.so

No major achievement but just clicking install saves a lot of chasing your own tail.

The .deb is available at [http://linuximages.co.uk/flash10amd64.deb](http://linuximages.co.uk/flash10amd64.deb)

Feel free to extract it and verify that it is just a straight tweak of the adobe standard linux download with the following amendments:

* in DEBIAN/control: Architecture: amd64 as opposed to Architecture: x86
* in usr/lib/adobe-flashplugin/libflashplayer.so version has been changed to the version at [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)
* in md5sums usr/lib/adobe-flashplugin/libflashplayer.so changed to 1957a3414dfbfe5f7de000ae72da4cb6

dpkg -b . is then executed and the package renamed to the link above.

Hope this helps and if it cures even one person's flash headaches I'll be happy.

Regards all

---

### Post by dBuster on 2009-02-25
Just edited the GETFLASH script for the latest release, ran it and voila I have the latest plugin.  No other flash was installed in this laptop and thus only having the 64 bit flash and it is sweet!

Thanks!

---

### Post by JG6_oddball on 2009-03-06
sorry guys but i did not read all the posts here So i may be repeating A CURE that was already  found, after 2 infuriating hours i found it :)
[http://gaarai.com/2009/02/20/proper-adobe-flash-support-on-ubuntu-64-bit/](http://gaarai.com/2009/02/20/proper-adobe-flash-support-on-ubuntu-64-bit/)

"> Automated Install

I&#8217;ve created a script that will take care of the details of installing this solution for you. Simply run the following commands from Terminal (Applications > Accessories > Terminal):
wget [http://gaarai.com/install_adobe_flash_64.sh](http://gaarai.com/install_adobe_flash_64.sh)
chmod +x install_adobe_flash_64.sh
./install_adobe_flash_64.sh

Since this script uses the sudo command, you will be prompted for your password. I have to use sudo since I need to close Firefox, remove apt packages, remove existing Flash plugins in the /usr/lib directory, and copy the new plugin to /usr/lib/mozilla/plugins/.
Manual Install

If my script and its use of sudo makes you uncomfortable, this is the sequence of steps you need to install the plugin manually:

   1. Download the Adobe Flash 64-bit plugin (the following is all one line):
      wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)
   2. Extract the libflashplayer.so from the archive:
      tar xvfz libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
   3. Close Firefox
   4. Remove old Flash plugins. The follow commands are what my script uses to automate this process:

      sudo apt-get remove -y --purge -qq flashplugin-nonfree \
      gnash gnash-common mozilla-plugin-gnash \
      swfdec-mozilla libflashsupport nspluginwrapper
      sudo rm -f /usr/lib/mozilla/plugins/*flash*
      sudo rm -f ~/.mozilla/plugins/*flash*
      sudo rm -f /usr/lib/firefox/plugins/*flash*
      sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
      sudo rm -rf /usr/lib/nspluginwrapper

   5. Copy libflashplayer.so to /usr/bin/mozilla/plugins/:
      sudo mkdir -p /usr/bin/mozilla/plugins/
      sudo cp libflashplayer.so /usr/bin/mozilla/plugins

Now you&#8217;re ready to load Firefox again and test it out."



I did the automated and it worked like a charm (once i remembered to close synaptic)

p.s it still wont work in firefox....but does work perfectly in seamonkey

---

### Post by krisvdm on 2009-03-06
*Open a terminal, enter the command:*
sudo apt-get remove nspluginwrapper flashplugin-nonfree

 * Download 64 bit (AMD) flash version from Abode at the bottom of the link:  *
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)   
 * Save it from the download page. It is a .tar.gz*

  *Assuming your the saved tar is in your home directory, extract by entering the command:*
sudo tar xvf ~/libflashplayer-10.0.xxx.linux-x86_64.so.tar.gz 
*  The "**xxx**" denote the version number.*

  * "install" by entering:*
sudo mv libflashplayer.so /usr/lib/firefox-3.xxx/plugins/

---

### Post by JG6_oddball on 2009-03-07
thnx Kris

S!

---

### Post by Jim_in_Omaha on 2009-03-10
This also worked for me. I noticed a dramatic improvement in speed particularly with flash games like 'The Space Game' at Candystand. That thing would drag this to a near standstill and now when many ships are attacking the base it still keeps playing smoothly. Not that I like to play games or anything but it just is annoying to brag up Ubuntu and have Firefox be a dog with Flash.

Another problem I have is when playing videos and surfing with another opened Firefox it would kill the video. So far I have not had that happen yet with this 64-bit Flash....

> **krisvdm said:**
> *Open a terminal, enter the command:*
sudo apt-get remove nspluginwrapper flashplugin-nonfree

 * Download 64 bit (AMD) flash version from Abode at the bottom of the link:  *
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)   
 * Save it from the download page. It is a .tar.gz*

  *Assuming your the saved tar is in your home directory, extract by entering the command:*
sudo tar xvf ~/libflashplayer-10.0.xxx.linux-x86_64.so.tar.gz 
*  The "**xxx**" denote the version number.*

  * "install" by entering:*
sudo mv libflashplayer.so /usr/lib/firefox-3.xxx/plugins/

---

### Post by snl2587 on 2009-03-18
Thanks! [S]This new version seems to have fixed every problem I had with the nsplugin solution.[/S]

Seems this doesn't play nicely with pulseaudio. Any fixes?

---

### Post by davisch on 2009-03-22
The install worked well and it is an improvement but it still consistently crashes Firefox - and other browsers - if you are using an Nvidia video card.  The problem is documented on the Adobe Bug pages so perhaps the next release will address the problem.  We can always hope.

---

### Post by dBuster on 2009-03-23
I am running a nVidia card and this plugin and have not had one crash from flash what so ever.  I am also running the latest java 64bit plugin as well, likewise, no crash.

I am current with both the latest flash and java plugins.  I have no other flash or java plugins other than the 64bit versions that I used the scripts to install and upon updates to both I modified the scripts with the names of the new files and ran them to get updated.  

Sounds like it might be a conflict with possibly another plugin.  I know that was my case on my old hardy laptop...

---

### Post by tjeremiah on 2009-03-23
I hope this is fixed or is better with 9.04.

---

### Post by Yellow Pasque on 2009-03-23
> **tjeremiah said:**
> I hope this is fixed or is better with 9.04.
Don't hold your breath. Jaunty still uses the 32-bit Flash through nspluginwrapper. Also, the ATI and Nvidia proprietary drivers seem to crash or segfault more frequently than the open-source video drivers. These companies just aren't on the same page on Linux and I don't have high hopes that they're going to get there any time soon.

---

### Post by Vadi on 2009-03-24
Ymmv

---

### Post by dBuster on 2009-03-24
> **Temüjin said:**
> Don't hold your breath. Jaunty still uses the 32-bit Flash through nspluginwrapper. Also, the ATI and Nvidia proprietary drivers seem to crash or segfault more frequently than the open-source video drivers. These companies just aren't on the same page on Linux and I don't have high hopes that they're going to get there any time soon.

I do not know your configuration however, I am not running a nspluginwrapper...  I have full screen fluid flash with my nvidia card and I am running Jaunty as well...  Here are my plugins:

```

Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.26.0 plugin handles video and audio streams.

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233


QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.26.0 plugin handles video and audio streams.

Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

libnpjp2.so

    File name: libnpjp2.so

DivX Browser Plug-In

    File name: mplayerplug-in-dvx.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

QuickTime Plug-in 7.4.5

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets


Windows Media Player Plug-in

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets


mplayerplug-in 3.55

    File name: mplayerplug-in.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Picasa

    File name: npPicasa3.so
    Picasa plugin

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22


```

I stripped out the file types but those are the plugins I am running.  my nvidia driver is 180.37

---

### Post by davisch on 2009-03-25
The differences I see are that I have Totem 2.22.01 where you have 2.26.0 and that I have Nvidia driver ver 169.12 and you have 180.37.

Perhaps I have an older card and it is my problem,,,

Thank you for posting the information!!!

---

### Post by loomsen on 2009-03-25
Working fine here too.

> 
[color=red]docter[/opt][/color] lsb_release -ir;uname -rm;nvidia-settings -q all | grep -i driver; ls /opt/ | grep libflash
[i]
Distributor ID:	Ubuntu
Release:	9.04
2.6.28-11-generic x86_64
  Attribute 'NvidiaDriverVersion' (tiffy:0.0): 180.37 
libflashplayer-10.0.22.87.linux-x86_64.so.tar
[/i]
[color=red]docter[/opt] [/color]


Running Opera...

Package: opera
Version: 9.64.2480.gcc4.qt3

Didnt have any problems with the alpha so far.

---

### Post by mashedbear on 2009-03-28
> **krisvdm said:**
> *Open a terminal, enter the command:*
sudo apt-get remove nspluginwrapper flashplugin-nonfree

 * Download 64 bit (AMD) flash version from Abode at the bottom of the link:  *
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)   
 * Save it from the download page. It is a .tar.gz*

  *Assuming your the saved tar is in your home directory, extract by entering the command:*
sudo tar xvf ~/libflashplayer-10.0.xxx.linux-x86_64.so.tar.gz 
*  The "**xxx**" denote the version number.*

  * "install" by entering:*
sudo mv libflashplayer.so /usr/lib/firefox-3.xxx/plugins/


Thanks krisvdm - I followed your instructions and everything seems to work just fine. 

I downloaded the latest beta: * libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz. * 

I did change the tar options to include the z option - to tell tar that the file is compressed. Don't know if that was needed but the command was:
```
sudo tar xvzf ~/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
```

---

### Post by acebrain01 on 2009-03-28
Download the Get64bitFlash from first post and change the lines in text editor 
--from--

```

## Then we make a temp folder and download the new plugin
cd /tmp/pluginstall
sudo wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz

## Next we extract and place the plugin
sudo tar xvf libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
```


--to--


```
## Then we make a temp folder and download the new plugin
cd /tmp/pluginstall
sudo wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

## Next we extract and place the plugin
sudo tar xvf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
```


Save and run in terminal.

---

### Post by philinux on 2009-03-30
This sticky needs updating. 


Abbreviated version:-

Remove flash non free

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Unpack the usual .so file. It only needs to be put in ~/.mozilla/plugins

---

### Post by Insane_Homer on 2009-03-31
Hi there,

I installed x64 Java and Flash on my jaunty install today. I used the following 2 very helpful HOWTOs @ 64bitjungle.com (they are a bit slow to open initially)

1. [Sun Java]("http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/")

2. [Adobe Flash]("http://www.64bitjungle.com/ubuntu/adobe-flash-player-10-alpha-for-64-bit-linux-ubuntu-installation/")

The only thing I had that was different was that Firefox listed 3 flash plugins. I used synaptic to remove the old ones.

It's blinding faster than it was before.

---

### Post by coolman009 on 2009-04-01
How to know that my system is 32bit platform or a 64 bit platform???Is it related to the Processor or to the Operating system??I am having AMD 3800+ processor...is it 32 or 64???

---

### Post by snl2587 on 2009-04-01
I believe the command is, in the terminal: 
```
uname -m
```

If the response is "x86_64", you're running the 64-bit version of Ubuntu.

---

### Post by Jim_in_Omaha on 2009-04-05
> **Insane_Homer said:**
> Hi there,

I installed x64 Java and Flash on my jaunty install today. I used the following 2 very helpful HOWTOs @ 64bitjungle.com (they are a bit slow to open initially)

1. [Sun Java]("http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/")

2. [Adobe Flash]("http://www.64bitjungle.com/ubuntu/adobe-flash-player-10-alpha-for-64-bit-linux-ubuntu-installation/")

The only thing I had that was different was that Firefox listed 3 flash plugins. I used synaptic to remove the old ones.

It's blinding faster than it was before.

I had mine working from an earlier post in this thread. There was a update and it messed up the flash. (I'm making a mental note not to allow it to update Flash) I found a good test for my machine is to go to Weather.com and go into the active weather map. While it is loading the clouds I would drag the map around and it would freeze up for several seconds. When the the Flash64 is installed properly it will not freeze up at all and will slide around with the mouse while loading data perfectly smooth.

Also while watching videos on YT and viewing something on another Firefox browser, if I would go back one page it would once in a while stop the video in the you tube browser and show a grey panel where the video was. This update fixes that too if installed correctly. (this is my experience anyway....)

---

### Post by mmand on 2009-04-07
I don't know if this has been posted before or not (and I'm sorry for not looking through 65 pages of replies, I just don't have time right now), but here's my solution.

After struggling with all kinds of scripts, tricks, and tips about installing the 64 bit version, I decided to try (just for the hell of it) the 32 bit version.

I downloaded the .tar.gz from here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

After extracting it, I opened the folder and copied libflashplayer.so to ~/.mozilla/plugins/

After restarting Firefox, about:plugins showed me this right at the top:
```

**Shockwave Flash**
File name:  libflashplayer.so
Shockwave Flash 10.0 r22
MIME Type Description Suffixes Enabled
application/x-shockwave-flash Shockwave Flash swf Yes
application/futuresplash FutureSplash Player spl Yes
```I don't know WHY 32 bit version of flash works where 64 bit wouldn't, but I'm glad to finally have flash working after four hours of bullcrap. I hope this helps someone else.

By the way, I'm using 64 bit Intrepid Ibex with a ubuntuzilla installed version of Firefox 3.0.8. I'm going to go out on a limb and say that ubuntuzilla didn't install the 64 bit version of Firefox, but I'm not sure how to tell. Help -> About tells me:
```
Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.0.8) Gecko/2009032608 Firefox/3.0.8
```

I'm going to be waiting for Jaunty to attempt 64 bit flash again, since I'll be doing a clean install of it.

---

### Post by daveisfera on 2009-04-07
I just installed the 64-bit Flash 10 plugin for Firefox, and it seems to be working but I don't get any sound. Any ideas on how I can fix that?
Thanks,
Dave

---

### Post by Yellow Pasque on 2009-04-07
> **mmand said:**
> I'm going to go out on a limb and say that ubuntuzilla didn't install the 64 bit version of Firefox, but I'm not sure how to tell.
You are correct. You're running a 32-bit browser.
```
Mozilla/5.0 (X11; U; Linux **i686** (x86_64); en-US; rv:1.9.0.8) Gecko/2009032608 Firefox/3.0.8
```

---

### Post by mmand on 2009-04-07
> **Temüjin said:**
> You are correct. You're running a 32-bit browser.
```
Mozilla/5.0 (X11; U; Linux **i686** (x86_64); en-US; rv:1.9.0.8) Gecko/2009032608 Firefox/3.0.8
```

I guess if I would have bothered to read their home page (instead of just, you know, installing the 64 bit version of their software), I'd have known this...

[http://ubuntuzilla.wiki.sourceforge.net/#tochome27](http://ubuntuzilla.wiki.sourceforge.net/#tochome27)

Funny how this reading thing works isn't it?

Thanks for clearing it up for me though, I got confused by the **(x86_64)** part. I've seen some apps that have that in their about info as well, but are really 64 bit.

---

### Post by axelsvag on 2009-04-08
I have tried to follow all your advices with my Ubuntu 64 bit and installation of flash player 10. Everything seems to work in most applications but for example this " [http://www.mtv.com/videos/the-hills-season-5-ep-1-dont-cry-on-your-birthday/1608283/playlist.jhtml](http://www.mtv.com/videos/the-hills-season-5-ep-1-dont-cry-on-your-birthday/1608283/playlist.jhtml) " just works on my 32 bit ubuntu installation not my 64 bit ubuntu.

---

### Post by skidmarks on 2009-04-09
Is anybody else having this problem? 

I installed flash 10 a while back under Intrepid and everything was fine. I recently upgraded to Jaunty and now flash plays fine, except when I try to go fullscreen. It will switch brief to full and then immediately drop back out.

I don't even know where to start looking for this one... I've got an nvidia card...

thx

---

### Post by drkshrk on 2009-04-11
I've recently installed the native 64 bit version of Adobe Flash and everything works fine (sound and fullscreen). This is a pre-release version but is very stable and hasn't give me problems on Intrepid or Jaunty. 
The best part of this is that neither nspluginwrapper nor the 32bit libraries are needed anymore... so you'll have a true 64 bit flash plugin running on your system.

First download the 64 bit plugin from:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz")

Once downloaded, untar it and you'll have a file named **libflashplayer.so**. Copy this file to your **$home/.mozilla/plugins** or **/usr/lib/mozilla/plugins** directory and voila... you'll have flash plugin 10.0 r22 version ready to rock.

Or if you prefer a more deb-type installation mode... cp or mv **libflashplayer.so** to **/usr/lib/adobe-flashplugin** (don't forget the sudo command if needed)
 
Then download my attached file (postinst.tar.gz) untar it and run the script... it will create all the links to libflashplayer.so so that other browser can use the plugin as well... (the script is the same as the one inside the deb package from Adobe)

I believe the second method is more safe because once Adobe releases it's 64 bit plugin... the installer will only update the file in /usr/lib/adobe-flashplugin

good luck!!!

---

### Post by daveisfera on 2009-04-11
> **drkshrk said:**
> I've recently installed the native 64 bit version of Adobe Flash and everything works fine (sound and fullscreen). This is a pre-release version but is very stable and hasn't give me problems on Intrepid or Jaunty. 
The best part of this is that neither nspluginwrapper nor the 32bit libraries are needed anymore... so you'll have a true 64 bit flash plugin running on your system.

First download the 64 bit plugin from:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz")

Once downloaded, untar it and you'll have a file named **libflashplayer.so**. Copy this file to your **$home/.mozilla/plugins** or **/usr/lib/mozilla/plugins** directory and voila... you'll have flash plugin 10.0 r22 version ready to rock.

I did exactly this on my laptop with Jaunty and Flash works without a hitch, but on my DVR box with Mythbuntu 9.04 the video plays, but I don't get any sound. I can hear sound in all of my other apps, but I'm guessing that Flash isn't playing to the right device. Does anyone know how to tell flash to play sound through a specific device?

---

### Post by starcannon on 2009-04-11
Kilz,

Thanks for the scripts, worked perfectly here. I did take a little time and changed out the java download in your java download script, to the newest java version available. Fantastic, thanks again.

Rob aka starcannon

---

### Post by elite_op. on 2009-04-13
I'm pretty sure my question was answered about 30 pages back or so, but didn't bother to to read all of that. I think it should be a quick fix. Any ways I am running the 64 bit version of Ubuntu 8.10. When I download it then open it it show a error i386. This also happened when I tryed to download skype.

---

### Post by mtnwalker2b on 2009-04-14
Many thanks to the author of this sticky.  After  days  of pulling  hair and gnashing teeth  and trying  every conceivable option to no avail.  The little script  at the top of this post  worked beautifully  on  both my AMD 64's    The dual core  and the PhenomII quad core  both responded identically without a hitch.  using  Ultimate Edition 2.1  on both machines.
Thanks  again,  this is going to be a great day.
zoe

---

### Post by lavinog on 2009-04-15
> **elite_op. said:**
> I'm pretty sure my question was answered about 30 pages back or so, but didn't bother to to read all of that. I think it should be a quick fix. Any ways I am running the 64 bit version of Ubuntu 8.10. When I download it then open it it show a error i386. This also happened when I tryed to download skype.

what is the output of ```
uname -a
```

---

### Post by elite_op. on 2009-04-16
Problem solved uninstall 64 bit cause it sucks, and install 32 bit which rocks. Yeah just put on 32 bit everything works fine.:popcorn:

---

### Post by dBuster on 2009-04-17
Un-installing 64 bit and going what some might consider backwards to 32bit?!  I wont....  I have no problems with 64bit flash and even my Skype works like a charm.  

Here is a kicker, I am even using Jaunty!  Been since Alpha3 and now we are in Release candidate, could be happier with the 64 bit! 

As far as the flash, I just made sure I used the scripts in the forums for installing 64 bit flash and java when I first installed and did not install any other flavor of flash or java....  I do remember on my other laptop the headaches I had with other flavors of java and flash causing me many issues with 64 bit versions when I installed them...  Maybe a clean install to solve the issue???

my 2 cents...

---

### Post by Efros on 2009-04-24
```
Flash 10
Adobe has released Flash 10. The plugin is of better quality than Flash 9. I will add this manual install section for those that would like to do it themselves. I would only use the instructions on Hardy, though Gutsy might work.
Click Here to download Getlibs
Click Here to get Flash 10
Save the files to your desktop, if you save files to a different location, drag them to your desktop.

First
1. Open a terminal and execute the following commands for removal of old plugins. Some may error out saying they cant find a file, that's ok. We just want to make sure they are removed if they exist.
Code:

sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo apt-get purge flashplugin-nonfree
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

Next we install new stuff.

Code:

cd ~/Desktop
sudo apt-get -y install nspluginwrapper
sudo dpkg -i getlibs-all.deb
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

We install the flash plugin
Code:

tar -xzvf install_flash_player_10_linux.tar.gz install_flash_player_10_linux
sudo mv -f ~/Desktop/install_flash_player_10_linux/libflashplayer.so /usr/lib/firefox-addons/plugins/

We wrap it and link it.
Code:

sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo ln -s /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

Then restart your browser.
If flash does not work
DO Not install other scripts. Run all the commands above again. Other scripts will only make things worse.
DO Not try other methods, these may leave files in place that will cause problems.
Read the How to get help section below before making any posts.

```


I can confirm the above procedure worked for my Intrepid to Jaunty upgrade on two different machines. Now have flash working on both. many thanks

---

### Post by lesmcd on 2009-04-24
Here is a link to the best discription for getting the alpha AMD64 bit Adobe Flash Player to function in either Ubuntu 8.1 or 9.4.

[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html)

I send my most cincere thanks to the author.  This fixed my flash player problems in Firefox and Opera.

Les McDermott

---

### Post by Wandering Wombat on 2009-04-25
> **lesmcd said:**
> 
[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html)


Thanks for the link, worked for me, no probs

Cheers

---

### Post by Arup on 2009-04-26
> **lesmcd said:**
> Here is a link to the best discription for getting the alpha AMD64 bit Adobe Flash Player to function in either Ubuntu 8.1 or 9.4.

[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html)

I send my most cincere thanks to the author.  This fixed my flash player problems in Firefox and Opera.

Les McDermott

Indeed one of the good examples of flash 10x64 Alpha install I have come across, very important to link the libflashplayer.so to Firefox-Addons and xulrunner so that other non browser apps needing Flash can work.

---

### Post by stanca on 2009-04-26
For me it worked everytime too but I had to add the flashblock in firefox because it often crashed on sites with many flashes.
Now everything's OK.

---

### Post by nybronx on 2009-04-26
Let me tell you guys the flash works like a charm.....Thanks for the help:)

---

### Post by lilbill on 2009-04-26
Works great on Jaunty Xubuntu 64-bit...thanks!!

---

### Post by davisch on 2009-04-27
I can not get Flash 10 to work correctly on my system.  I think it is because I have an older Nvidia (FX5600) that requires me to run the "legacy" driver (173.xx).  The problem is documented on the Adobe bug site but no fix is available - [http://bugs.adobe.com/jira/browse/FP-1069](http://bugs.adobe.com/jira/browse/FP-1069)  I would guess that since it is a problem with legacy boards that it will not be fixed.  Guess I'll have to get a newer video card...

---

### Post by dcory on 2009-04-27
I installed the beta 64 bit flash on intrepid machine.  After an upgrade to Jaunty, it mostly works fine, but there a few video sites where it refuses to play. (very strangely, politico.com's videos load, but refuse to play; I can even scroll through them but can't watch them!) I suspect reinstalling flash would help.

This is the problem.  How do I *remove* the beta version of flash that I've installed?  Even better, how do I remove and reinstall it?

Thanks to anyone who can help!
Dcory

---

### Post by Storm Rider on 2009-04-27
> **Wandering Wombat said:**
> Thanks for the link, worked for me, no probs

Cheers

Nice find.  The sh file worked perfectly.

---

### Post by Thelasko on 2009-04-28
So if I install flashplayer-nonfree in Jaunty, will it install the 64-bit flash alpha or 32-bit flash with nspluginwrapper?

---

### Post by Arup on 2009-04-29
> **Thelasko said:**
> So if I install flashplayer-nonfree in Jaunty, will it install the 64-bit flash alpha or 32-bit flash with nspluginwrapper?

x32 with nspluginwrapper.

---

### Post by northwestuntu on 2009-04-30
> **Arup said:**
> x32 with nspluginwrapper.

how can get the 64bit on jaunty?

---

### Post by tjeremiah on 2009-04-30
I swear, why do so many "answer" in such a way assuming everyone understands the language of linux?

---

### Post by celem on 2009-04-30
I just used the solution at Romeo Adrian Cioaba's site (link below) and can attest that it worked quickly and painlessly to install the new native 64bit Flash Player 10 on Linux without using nspluginwrapper. I have, so far, only tested it with Youtube.com but that site worked perfectly.

See:
[http://tinyurl.com/57o22j](http://tinyurl.com/57o22j)

---

### Post by Thelasko on 2009-04-30
> **Arup said:**
> x32 with nspluginwrapper.

I don't understand the logic behind this.  The Alpha works fine.  It's not like Jaunty is a LTS release.  Getting more people to use it is the only way we will find bugs.

---

### Post by miegiel on 2009-04-30
I've got everything running and now it's 64bit it's running better then ever.

It's just that the movies are using my viop sound card instead of my music and vids sound card. I can't find where to change it and my sound card settings in *System > Preferences > Sound* are being ignored :roll: (by either FF or flash).

If anyone has an idea ...

---

### Post by Arup on 2009-05-01
> **miegiel said:**
> I've got everything running and now it's 64bit it's running better then ever.

It's just that the movies are using my viop sound card instead of my music and vids sound card. I can't find where to change it and my sound card settings in *System > Preferences > Sound* are being ignored :roll: (by either FF or flash).

If anyone has an idea ...

sudo apt-get install padevchooser

---

### Post by miegiel on 2009-05-01
> **Arup said:**
> sudo apt-get install padevchooser

According to *PulseAudio Device Chooser* the card I use for music and vids is already the default device.

I tried playing an ogg in firefox and it grabs the default soundcard, so i'm pretty sure it's flash who for some reason rather uses my voip soundcard.

atm I'm digging through all the *.conf files hoping to find some inspiration.

**Solved** with a trick I found in another thread.
```
:~$ asoundconf list
Names of available sound cards:
SB
HDMI
T71Universe
:~$ asoundconf set-default-card T71Universe
```

---

### Post by manca on 2009-05-07
I can confirm too that this x64 flash plugin works very good so far in jaunty.

---

### Post by jeffthegodofbiscuits on 2009-05-07
Has anyone else experienced their web browsers crashing when opening a page that contains flash elements such as ESPN.com. 

I only seem to experience the issue when, for example, I am on ESPN's front page and the cycling flash headlines transition. Then the entire browser will crash. This occurs with Firefox, Opera and Konqueror. 

I am able to view youtube videos without issue, though when going to full screen the video playback is choppy. 

I have experienced this issue with both the 32 bit version of flash from the repositories, as well as the 64 bit version from Adobe's site. 

I'm not sure what other information to provide. Overall the upgrade to 9.04 has been very solid, save the issue with Flash.

---

### Post by forger on 2009-05-08
Jaunty is not in development anymore, please update :)

---

### Post by mikeric on 2009-05-08
> **lesmcd said:**
> Here is a link to the best discription for getting the alpha AMD64 bit Adobe Flash Player to function in either Ubuntu 8.1 or 9.4.

[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html)

I send my most cincere thanks to the author.  This fixed my flash player problems in Firefox and Opera.

Les McDermott

Thanks, I used the script on that page and it worked for me no problem

---

### Post by CooksWithFire on 2009-05-11
I do nothing with this part, right?

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email]

I start with this in a terminal after the $, right?
sudo killall -9 firefox

Then what do I do at 
CD~
wget http...

---

### Post by bashphoenux on 2009-05-12
thank you verry much !!

---

### Post by martin_legion on 2009-05-12
Worked like a charm. Thanks a lot!

---

### Post by northwestuntu on 2009-05-16
so it seems kilz isn't coming back.

> Arch! the way to go.

Some of the great qualities.
1. Supper fast.
2. Its what you make it, not what others have chosen for you.
3. It lacks the constant influx of clueless newbies.
4. It doesnt have mods who think that its ok for new users to ask stupid questions over and over and over.
5. Once its installed you never have to install another version.

might as well take the sticky down since it won't be updated by him now.  how bout some new instructions on installing 64bit flash.

32 sucks!! ;)

---

### Post by dBuster on 2009-05-16
> **CooksWithFire said:**
> I do nothing with this part, right?

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email]

I start with this in a terminal after the $, right?
sudo killall -9 firefox

Then what do I do at 
CD~
wget http...

What you are reading appears to be a script.  You can copy and save that to a file and then make the file executable and then double click on it choosing to run it in a terminal.  It is not meant for you to type each line one by one...  ;)

Actually that page has a link to download the script file...  Look down on that page.

---

### Post by northwestuntu on 2009-05-16
i can't understand why ubuntu didn't include the 64 beta along with the 32? they included a beta version of firefox before.

---

### Post by miegiel on 2009-05-16
> **northwestuntu said:**
> i can't understand why ubuntu didn't include the 64 beta along with the 32? they included a beta version of firefox before.

AFAIK 64bit flash is still alpha.

---

### Post by northwestuntu on 2009-05-17
> **miegiel said:**
> AFAIK 64bit flash is still alpha.

that's true. i was thinking it was beta.

it is a lot more stable then using the 32 though in my experience.

---

### Post by Thelasko on 2009-05-18
> **miegiel said:**
> AFAIK 64bit flash is still alpha.

It's been out for quite a while.  It should be beta by now.

---

### Post by protargol on 2009-05-23
> **celem said:**
> I just used the solution at Romeo Adrian Cioaba's site (link below) and can attest that it worked quickly and painlessly to install the new native 64bit Flash Player 10 on Linux without using nspluginwrapper. I have, so far, only tested it with Youtube.com but that site worked perfectly.

See:
[http://tinyurl.com/57o22j](http://tinyurl.com/57o22j)

Thanks!  This worked beautifully.

---

### Post by Chame_Wizard on 2009-05-26
Have the newest flash version ,but sometimes it completly hangs.

---

### Post by sabmo on 2009-05-30
intel core 2 duo running ubuntu 9.04 x86_64

Take the alpha libflashplayer.so and put it directly into
my /usr/lib/firefox-addons/plugins  and it works perfectly so far.

one file, into one directory, if only everything could be this simple

---

### Post by shane2peru on 2009-06-06
Hey everyone.  This script isn't too dificult to hack. :)  Here is the updated script.  All I did was update the flash link to the latest.

```

#!/bin/bash

## First we make the working directory
sudo mkdir /tmp/pluginstall

#choose version of ubuntu
#Input code browser
function strinput {
 unset refstr
 echo -n "$1"
 read refstr
}

## Ask if they agree to file bug reports, sort of a reminder
echo
echo " This script is used to setup the Flash 10 Alpaha. "
echo " By entering yes below you acknowlage that you "
echo " are installing development software and you "
echo " will file bug reports with Adobe for every "
echo " problem you incounter."
echo
echo " Do you agree? yes or no : "


if [ "$installtype" = "" ]
then
 echo -n "(please type the whole word in lower case letters)"
 strinput
else
 refstr=$installtype
fi

if [ "$refstr" = "yes" ]
then
 echo "Flash installing."


## First we uninstall and remove all the existing flash packages

sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so

## Then we make a temp folder and download the new plugin
cd /tmp/pluginstall
sudo wget [COLOR="Red"]http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz[/COLOR]

## Next we extract and place the plugin
sudo tar xvf [COLOR="Red"]libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz[/COLOR]
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/


elif [ "$refstr" = "no" ]
then
 echo "I am sorry but you have to agree. "

else
 echo  " I am sorry but you have to agree. "
 echo
fi

```

I highlighted the pertinent parts that I changed.  I gave it a try and it works fine.  Updated my Flash to the release candidate.  You can just copy that above and paste it into a text editor, and save it as GetFlash64 in your home directory.  Then right click on it and make it executable via the properties tab select the check the execute box.  Or in a terminal type:
```

chmod +x GetFlash64

```

^^^  That must be executed in the same directory as your file or it won't work.  :)  Enjoy!

Shane

PS if someone will get me the correct link for the latest Java64 I will update that script and post it here too.  I hate the java website, it is always sooo confusing to me, and I don't know what is the proper file to get. :oops:

---

### Post by Pendaws on 2009-06-07
> **sabmo said:**
> intel core 2 duo running ubuntu 9.04 x86_64

Take the alpha libflashplayer.so and put it directly into
my /usr/lib/firefox-addons/plugins  and it works perfectly so far.

one file, into one directory, if only everything could be this simple

I tried this ut it wont allow me to drag it there or copy and paste? Please, what am I doing wrong?

---

### Post by Yellow Pasque on 2009-06-07
> **Pendaws said:**
> I tried this ut it wont allow me to drag it there or copy and paste? Please, what am I doing wrong?
You need root permissions to do that.
```
gksudo nautilus
```

---

### Post by Pendaws on 2009-06-07
Thank you Temujin, It is now added to my list of helpful texts. :)

---

### Post by Koltor on 2009-06-08
The information in the first post is outdated and causes Firefox to crash repeatedly. The currently working protocol can be found in the first post of this thread: [http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964) . It works perfectly on the first attempt with no further modification needed.

---

### Post by miegiel on 2009-06-08
> **Koltor said:**
> The information in the first post is outdated and causes Firefox to crash repeatedly. The currently working protocol can be found in the first post of this thread: [http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964) . It works perfectly on the first attempt with no further modification needed.

Kilz has been away since October 31st, 2008 and the OP is a year old.

---

### Post by shane2peru on 2009-06-08
> **miegiel said:**
> Kilz has been away since October 31st, 2008 and the OP is a year old.

I modified the OP script for the latest Flash.  You can get that here: [http://ubuntuforums.org/showpost.php?p=7412598&postcount=699](http://ubuntuforums.org/showpost.php?p=7412598&postcount=699)

Post #699.  Just copy and paste the script to a text editor, and make it executable, I explain it all there.  Course I understand post 699 doesn't get near as much exposure as post 1 does. :D

Shane

---

### Post by ryank76nz on 2009-06-23
The latest update to Firefox 3.0.11 has broken flash and I can't install 9 or 10 - have tried every how-to I can find and nothing works, including the post above.

Has anyone successfully installed flash on 64 bit on Firefox 3.0.11? If so, which method did you use?

---

### Post by Arup on 2009-06-23
Flash works fine here on FF3.0.11 Just untar the alpha 10 flash from Adobe and move it to /usr/lib/mozila/plugins If you install Opera, it also picks up the flash from there.

---

### Post by miegiel on 2009-06-23
> **ryank76nz said:**
> The latest update to Firefox 3.0.11 has broken flash and I can't install 9 or 10 - have tried every how-to I can find and nothing works, including the post above.

Has anyone successfully installed flash on 64 bit on Firefox 3.0.11? If so, which method did you use?

Are you trying to install the 64bit or 32bit versions of the flash player?

Anyway from the OP
> **Other Flash Plugins.**
If after installing the script you cant see flash. Make sure that all attempts at installing other flash plugins (Gnash, swfdec, etc) have been uninstalled and the files they created have been removed. The remains of past failed attempts are the #1 cause of flash not working. This is because the files conflict with the flash plugin.

Get the 64 bit (still beta) flash player here (download link is at the bottom of the page).
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by ryank76nz on 2009-06-23
The latest 64 bit, that's why I'm posting in this forum.

Thanks for the link, that worked and was what I couldn't find on the Adobe site.

---

### Post by finndo on 2009-06-24
[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

follow this instruction works in jaunty 9.04 x64, just remember to do an apt-get update and then an apt-get upgrade afterwards.

----------------------------------------------------
AMD Phenom II x4 955 Black Edition 3.2 GHz (not overclocked)
OCZ Black Edition DDR3 1333MHz at 8-8-8-24 (underclocked for stability issues)
ECS A790GXM-AD3 (V1.0A) Black Edition MB with AMD 790GX chipset and ATI Radeon&#8482; HD 3300
Thermal Take V9 Black Edition case
Kubuntu 9.04 x64

built May 23rd 2009
----------------------------------------------------

---

### Post by Hutto on 2009-06-24
This worked for me...

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz

---

### Post by hammergil on 2009-06-25
New to Ubuntu.  Ran the script from the first page for Hardy to get flash 10.  restarted computer and no flash.  here is the output of the commands requested from first page.  any help would be appreciated.  maybe i just need to link the files to the plugins, but i don't know how to do that

david@david-desktop:~$ ls -al /usr/lib/mozilla/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-04-11 11:55 .
drwxr-xr-x 4 root root 4096 2009-01-20 04:12 ..
david@david-desktop:~$ ls -al /usr/lib/firefox-addons/plugins
total 9924
drwxr-xr-x 2 root  root      4096 2009-06-25 08:05 .
drwxr-xr-x 5 root  root      4096 2009-01-20 04:10 ..
-rwxr-xr-x 1 david david 10131640 2009-02-02 20:06 libflashplayer.so
lrwxrwxrwx 1 root  root        60 2009-06-25 07:57 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

---

### Post by hammergil on 2009-06-25
don't know if this means anything, but the libflashplayer.so is in green text and npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so is in red text with grey background...

---

### Post by miegiel on 2009-06-25
> **hammergil said:**
> New to Ubuntu.  Ran the script from the first page for Hardy to get flash 10.  restarted computer and no flash.  here is the output of the commands requested from first page.  any help would be appreciated.  maybe i just need to link the files to the plugins, but i don't know how to do that

david@david-desktop:~$ ls -al /usr/lib/mozilla/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-04-11 11:55 .
drwxr-xr-x 4 root root 4096 2009-01-20 04:12 ..
david@david-desktop:~$ ls -al /usr/lib/firefox-addons/plugins
total 9924
drwxr-xr-x 2 root  root      4096 2009-06-25 08:05 .
drwxr-xr-x 5 root  root      4096 2009-01-20 04:10 ..
-rwxr-xr-x 1 david david 10131640 2009-02-02 20:06 libflashplayer.so
lrwxrwxrwx 1 root  root        60 2009-06-25 07:57 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

Try running the cleanup script again from the 1st post.

```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo apt-get purge flashplugin-nonfree
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

And then try installing the 64 bit beta flash player from Adobe (download link is at the bottom of the page, installation instructions should be in the .tar.gz file). [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by hammergil on 2009-06-25
by cleanup script you mean the remove script right?  or do i use your code you posted, or both?  Sorry, just want to be clear.  thanks

---

### Post by miegiel on 2009-06-25
> **hammergil said:**
> by cleanup script you mean the remove script right?  or do i use your code you posted, or both?  Sorry, just want to be clear.  thanks

I just copied it from the 1st post ;)

---

### Post by hammergil on 2009-06-25
that worked perfectly for me...kindof
For some reason the libflashplayer.so file was still there after the rm
so i used terminal and changed to the directory of the file and rm again and this time it did remove for some reason.  Then my next hurdle was getting the new libflashplayer.so file that i downloaded from adobe from the desktop to the plugin folder.  It wouldn't let me drag and drop it there because of permissions.  So I learned a new command "mv".  I changed the directory to my Desktop (cd Desktop) where the new file was and then typed "sudo mv libflashplayer.so /usr/lib/firefox-addons/plugins" and the file was moved.  Then i restarted browser and now I have flash player...thanks for the help...I am learning!

---

### Post by rwttaber on 2009-06-25
can i have help, ubuntu nub here, when i try to copy the flash player to the Mozilla plug-ins folder i get a message saying permission denied.

thx in advanced

---

### Post by miegiel on 2009-06-25
> **rwttaber said:**
> can i have help, ubuntu nub here, when i try to copy the flash player to the Mozilla plug-ins folder i get a message saying permission denied.

thx in advanced

Put sudo in front of the copy command.

---

### Post by rwttaber on 2009-06-25
I was using drag and drop, whats the copy command for the terminal?

---

### Post by miegiel on 2009-06-25
> **rwttaber said:**
> I was using drag and drop, whats the copy command for the terminal?

```
cp
```

you could also try 

```
sudo nautilus
```

then you can drag and drop as root

---

### Post by rwttaber on 2009-06-25
never mind, i figured it out

---

### Post by cjminton on 2009-06-26
Hey this is my first post but I just wanted to say that I found this post to be somewhat useless since it's outdated. 

Heres the easy way to install flash 10 for ubuntu 9.04 64 bit **and firefox**.

First uninstall the old 
```
sudo apt-get remove flashplugin-nonfree flashplugin-installer
```In with the new direct from Adobe
```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

```
Extracting/installing flash 10 into firefox
```
tar xvf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
```Enjoy.
DON'T FORGET TO COMPLETELY RESTART THE COMPUTER BEFORE USING FLASH!:)

Credits - [http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/)

---

### Post by michaelzap on 2009-06-26
I'm still having audio issues with the latest Flash 10 from Adobe on a fresh Jaunty installation. Specifically, if I play anything with audio in my web browser, no other audio application can play audio again until I close and restart Firefox. Similarly if I'm playing music (in Exaile), I can't also play any Flash audio (even if I stop playing the other application first).

Any resolution for this issue in Jaunty?

---

### Post by cjminton on 2009-06-26
> **michaelzap said:**
> I'm still having audio issues with the latest Flash 10 from Adobe on a fresh Jaunty installation. Specifically, if I play anything with audio in my web browser, no other audio application can play audio again until I close and restart Firefox. Similarly if I'm playing music (in Exaile), I can't also play any Flash audio (even if I stop playing the other application first).

Any resolution for this issue in Jaunty?

Try the post above yours. 

When I first installed flash I didn't fully restart ubuntu and the audio also wouldn't work, did you remember to restart ubuntu and not just firefox?

---

### Post by miegiel on 2009-06-26
> **michaelzap said:**
> I'm still having audio issues with the latest Flash 10 from Adobe on a fresh Jaunty installation. Specifically, if I play anything with audio in my web browser, no other audio application can play audio again until I close and restart Firefox. Similarly if I'm playing music (in Exaile), I can't also play any Flash audio (even if I stop playing the other application first).

Any resolution for this issue in Jaunty?

It sounds like :twisted: the flash player is directly hooking on to your sound "card" instead of hooking on to pulse. Maybe the "PulseAudio Device Chooser" (search Add/Remove Applications) can help you fix it.

---

### Post by ryank76nz on 2009-06-27
> **cjminton said:**
> Hey this is my first post but I just wanted to say that I found this post to be somewhat useless since it's outdated. 

Heres the easy way to install flash 10 for ubuntu 9.04 64 bit **and firefox**.

First uninstall the old 
```
sudo apt-get remove flashplugin-nonfree flashplugin-installer
```In with the new direct from Adobe
```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

```
Extracting/installing flash 10 into firefox
```
tar xvf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
```Enjoy.
DON'T FORGET TO COMPLETELY RESTART THE COMPUTER BEFORE USING FLASH!:)

Credits - [http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/)

I followed this and got absolutely nothing. Nothing appears where the flash should be when I load a page with Flash on it. 

????????? 

Should I try to go back to a previous version of Firefox that works? Or maybe avoid updates in future.

---

### Post by michaelzap on 2009-06-27
> **cjminton said:**
> Try the post above yours.
When I first installed flash I didn't fully restart ubuntu and the audio also wouldn't work, did you remember to restart ubuntu and not just firefox?
I already have that version of Flash installed, and I've restarted many times since I installed it a week or so ago.

I'm using Alsa in order to get 5.1 sound from my laptop; maybe that's part of the problem?

---

### Post by ryank76nz on 2009-06-28
> **Hutto said:**
> This worked for me...

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz

This works for youtube but closes Firefox on other sites including [www.stardoll.com](www.stardoll.com), [www.theonion.com](www.theonion.com)

ARGH add Wordpress media/image functions and this is getting really frustrating.

---

### Post by kami84gr on 2009-06-28
I would also like to confirm from my experience that the 64bit Adobe flash works like a charm works like a charm on default (and tweaked)  ubuntu 9.04, fedora 11, and Arch x86_64 installations, provided that you remove first any previous "wraped" 32bit plugins.

I've tested it with Firefox 3.0.11 , 3.5 beta 4 and with Opera 9.64 and 10 beta.

In all installations it worked WITHOUT rebooting the pc , just the browser.

It hasn't crashed so far on any of the sites im using it with and to be honest I think it is somewhat faster than the 32bit wrapped version, but that it is just personal estimation.

Best regards!

---

### Post by Arup on 2009-06-28
> **kami84gr said:**
> I would also like to confirm from my experience that the 64bit Adobe flash works like a charm works like a charm on default (and tweaked)  ubuntu 9.04, fedora 11, and Arch x86_64 installations, provided that you remove first any previous "wraped" 32bit plugins.

I've tested it with Firefox 3.0.11 , 3.5 beta 4 and with Opera 9.64 and 10 beta.

In all installations it worked WITHOUT rebooting the pc , just the browser.

It hasn't crashed so far on any of the sites im using it with and to be honest I think it is somewhat faster than the 32bit wrapped version, but that it is just personal estimation.

Best regards!

I agree, has worked flawlessly in FF and Opera and even Opera 10 beta and in both Phenom and Intel quad core PC.

---

### Post by cjminton on 2009-06-28
> **ryank76nz said:**
> I followed this and got absolutely nothing. Nothing appears where the flash should be when I load a page with Flash on it. 
 
????????? 
 
Should I try to go back to a previous version of Firefox that works? Or maybe avoid updates in future.
 
Previous version of firefox? Perhaps. I've only used w/e firefox comes with ubuntu 9.04

---

### Post by lavinog on 2009-06-29
> **ryank76nz said:**
> This works for youtube but closes Firefox on other sites including [www.stardoll.com](www.stardoll.com), [www.theonion.com](www.theonion.com)

ARGH add Wordpress media/image functions and this is getting really frustrating.

what version is listed in the plugins tab.

I had the same issue, but it turned out to be that I had two versions installed. (one in the /usr/lib folder and one in my home .mozilla/plugins)
The script that you quoted (Hutto's) is an older version. cjminton's post uses the later version, but doesn't remove old versions automatically

post the output of
```

find / -name '*flash*' 2>/dev/null

```

---

### Post by ryank76nz on 2009-06-29
The version is Shockwave Flash 10.0 d20

Here's the result: 

```
/etc/alternatives/xulrunner-addons-flashplugin
/etc/alternatives/xulrunner-flashplugin
/etc/alternatives/iceape-flashplugin
/etc/alternatives/iceweasel-flashplugin
/etc/alternatives/mozilla-flashplugin
/etc/alternatives/firefox-flashplugin
/etc/alternatives/midbrowser-flashplugin
/lib/modules/2.6.24-24-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/var/cache/apt/archives/flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_amd64.deb
/var/lib/dpkg/info/adobe-flashplugin.prerm
/var/lib/dpkg/info/adobe-flashplugin.list
/var/lib/dpkg/info/adobe-flashplugin.postinst
/var/lib/dpkg/info/adobe-flashplugin.md5sums
/var/lib/dpkg/alternatives/xulrunner-addons-flashplugin
/var/lib/dpkg/alternatives/xulrunner-flashplugin
/var/lib/dpkg/alternatives/iceape-flashplugin
/var/lib/dpkg/alternatives/iceweasel-flashplugin
/var/lib/dpkg/alternatives/mozilla-flashplugin
/var/lib/dpkg/alternatives/firefox-flashplugin
/var/lib/dpkg/alternatives/midbrowser-flashplugin
/usr/lib32/libflashsupport.so
/usr/share/icons/gnome/24x24/devices/media-flash.png
/usr/share/icons/gnome/24x24/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/22x22/devices/media-flash.png
/usr/share/icons/gnome/22x22/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/16x16/devices/media-flash.png
/usr/share/icons/gnome/16x16/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/32x32/devices/media-flash.png
/usr/share/icons/gnome/32x32/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/scalable/devices/media-flash.svg
/usr/share/icons/gnome/scalable/mimetypes/gnome-mime-application-x-shockwave-flash.svg
/usr/share/icons/Human/24x24/devices/media-flash-cf.png
/usr/share/icons/Human/24x24/devices/media-flash.png
/usr/share/icons/Human/24x24/devices/media-flash-ms.png
/usr/share/icons/Human/22x22/devices/media-flash-cf.png
/usr/share/icons/Human/22x22/devices/media-flash.png
/usr/share/icons/Human/16x16/devices/media-flash.png
/usr/share/icons/Human/48x48/devices/media-flash-cf.png
/usr/share/icons/Human/48x48/devices/media-flash.png
/usr/share/icons/Human/48x48/devices/media-flash-ms.png
/usr/share/icons/Human/scalable/devices/media-flash.svg
/usr/share/icons/Human/scalable/devices/media-flash-ms.svg
/usr/share/icons/Human/scalable/devices/media-flash-cf.svg
/usr/share/icons/HighContrastLargePrintInverse/48x48/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/man/man8/btcflash.8.gz
/usr/share/mime/application/x-shockwave-flash.xml
/usr/share/mime/application/x-flash-video.xml
/usr/share/doc/adobe-flashplugin
/usr/share/app-install/icons/flashblock.xpm
/usr/share/app-install/icons/flash.png
/usr/share/app-install/desktop/flashblock.desktop
/usr/share/app-install/desktop/flash10.desktop
/usr/share/app-install/desktop/flashplugin-nonfree.desktop
/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/flashwin.py
/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/lib/flashwin.py
/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/lib/flashwin.pyc
/usr/lib/openoffice/program/libflash680lx.so
/usr/lib/adobe-flashplugin
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/src/linux-headers-2.6.24-16/include/asm-sparc/jsflash.h
/usr/src/linux-headers-2.6.24-16/include/asm-cris/axisflashmap.h
/usr/src/linux-headers-2.6.24-16/include/asm-arm/nwflash.h
/usr/src/linux-headers-2.6.24-16/include/asm-arm/mach/flash.h
/usr/src/linux-headers-2.6.24-16/include/asm-mips/mach-excite/excite_nandflash.h
/usr/src/linux-headers-2.6.24-16/include/linux/spi/flash.h
/usr/src/linux-headers-2.6.24-16/include/linux/mtd/flashchip.h
/usr/src/linux-headers-2.6.24-24/include/asm-sparc/jsflash.h
/usr/src/linux-headers-2.6.24-24/include/asm-cris/axisflashmap.h
/usr/src/linux-headers-2.6.24-24/include/asm-arm/nwflash.h
/usr/src/linux-headers-2.6.24-24/include/asm-arm/mach/flash.h
/usr/src/linux-headers-2.6.24-24/include/asm-mips/mach-excite/excite_nandflash.h
/usr/src/linux-headers-2.6.24-24/include/linux/spi/flash.h
/usr/src/linux-headers-2.6.24-24/include/linux/mtd/flashchip.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/mtd/scb2/flash.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.24-24-generic/include/config/mtd/scb2/flash.h
/usr/src/linux-headers-2.6.24-24-generic/include/config/mtd/dataflash.h
/usr/bin/btcflash
/home/ryan/Documents/ebooks/flashant1pdf.pdf
/home/ryan/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz.1
/home/ryan/.macromedia/Flash_Player/#SharedObjects/GAJS3GKM/static.twitter.com/flash
/home/ryan/.macromedia/Flash_Player/#SharedObjects/GAJS3GKM/tvnz.co.nz/stylesheets/tvnz/entertainment/flash
/home/ryan/.macromedia/Flash_Player/#SharedObjects/GAJS3GKM/flash.quantserve.com
/home/ryan/.macromedia/Flash_Player/#SharedObjects/GAJS3GKM/cdn.stardoll.com/flash
/home/ryan/.macromedia/Flash_Player/#SharedObjects/GAJS3GKM/cdn-static.viddler.com/flash
/home/ryan/.macromedia/Flash_Player/macromedia.com/support/flashplayer
/home/ryan/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#flash.quantserve.com
/home/ryan/Packages/install_flash_player_10_linux.deb
/home/ryan/Packages/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
/home/ryan/flashagain
/home/ryan/flashinstructions
/home/ryan/flash3
/home/ryan/Pictures/libflashplayer.so
/home/ryan/Pictures/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
/home/ryan/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz

```

Thanks

---

### Post by lavinog on 2009-06-29
> **ryank76nz said:**
> The version is Shockwave Flash 10.0 d20

Here's the result: 


```
/etc/alternatives/xulrunner-addons-flashplugin
/etc/alternatives/xulrunner-flashplugin
/etc/alternatives/iceape-flashplugin
/etc/alternatives/iceweasel-flashplugin
/etc/alternatives/mozilla-flashplugin
/etc/alternatives/firefox-flashplugin
/etc/alternatives/midbrowser-flashplugin

```
I don't know why these are here. you may want to check that they are all pointing to the same location:
```
ls -l /etc/alternatives/*flashplugin
```



```

/usr/lib32/libflashsupport.so

```
Not sure what this is for, unless it was for the hardy package. Are you using hardy?
Someone else might know.


I suspect that one of these is conflicting with the others (I think you might have the hardy package installed alongside the manual install):
```

/usr/lib/adobe-flashplugin
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so

```

post the output of this:
```

find /usr/lib/ -name '*flashplugin*' -exec md5sum {} \; 2>/dev/null
find /usr/lib/ -name 'libflashplayer.so' -exec md5sum {} \; 2>/dev/null

```
All of the md5sums need to be the same. A difference could cause an issue.

---

### Post by ryank76nz on 2009-06-29
Hi, yes I'm using Hardy.

```
ryan@ryan-desktop:~$ find /usr/lib/ -name '*flashplugin*' -exec md5sum {} \; 2>/dev/null
ryan@ryan-desktop:~$ find /usr/lib/ -name 'libflashplayer.so' -exec md5sum {} \; 2>/dev/null
80e9c834aad24dc4f01e3e42c59c369e  /usr/lib/firefox-addons/plugins/libflashplayer.so
80e9c834aad24dc4f01e3e42c59c369e  /usr/lib/mozilla/plugins/libflashplayer.so
80e9c834aad24dc4f01e3e42c59c369e  /usr/lib/xulrunner-addons/plugins/libflashplayer.so

```

I checked these:

/etc/alternatives/xulrunner-addons-flashplugin - broken
/etc/alternatives/xulrunner-flashplugin - broken
/etc/alternatives/iceape-flashplugin - broken
/etc/alternatives/iceweasel-flashplugin - broken
/etc/alternatives/mozilla-flashplugin  - broken
/etc/alternatives/firefox-flashplugin - broken
/etc/alternatives/midbrowser-flashplugin - broken

hm.. all broken.

---

### Post by lavinog on 2009-06-29
Thats odd, it didn't show the other files.
how about manually trying:
```

md5sum /usr/lib/adobe-flashplugin
md5sum /usr/lib/midbrowser/plugins/flashplugin-alternative.so
md5sum /usr/lib/xulrunner/plugins/flashplugin-alternative.so
md5sum /usr/lib/iceweasel/plugins/flashplugin-alternative.so
md5sum /usr/lib/iceape/plugins/flashplugin-alternative.so

```

---

### Post by ryank76nz on 2009-06-30
```
ryan@ryan-desktop:~$ md5sum /usr/lib/adobe-flashplugin
md5sum: /usr/lib/adobe-flashplugin: Is a directory
ryan@ryan-desktop:~$ md5sum /usr/lib/midbrowser/plugins/flashplugin-alternative.so
md5sum: /usr/lib/midbrowser/plugins/flashplugin-alternative.so: No such file or directory
ryan@ryan-desktop:~$ md5sum /usr/lib/xulrunner/plugins/flashplugin-alternative.so
md5sum: /usr/lib/xulrunner/plugins/flashplugin-alternative.so: No such file or directory
ryan@ryan-desktop:~$ md5sum /usr/lib/iceweasel/plugins/flashplugin-alternative.so
md5sum: /usr/lib/iceweasel/plugins/flashplugin-alternative.so: No such file or directory
ryan@ryan-desktop:~$ md5sum /usr/lib/iceape/plugins/flashplugin-alternative.so
md5sum: /usr/lib/iceape/plugins/flashplugin-alternative.so: No such file or directory
ryan@ryan-desktop:~$ 


```


Is there a way to get rid of ALL the other ones and start again?

cheers

---

### Post by miegiel on 2009-06-30
> **ryank76nz said:**
> Is there a way to get rid of ALL the other ones and start again?

Try running the removal commands in the 1st post. I had the best results running the purge / remove (sudo apt-get purge .. / sudo rm ..) commands 1 by 1 instead of running the scripts.

---

### Post by ryank76nz on 2009-07-01
That was the first thing I tried.

Come on folks, it can't be that hard to purge this thing. Firefox 3.0.11, Flash 10.0 d20. Delete everything with 'flash' in the name? Purge firefox itself?

---

### Post by miegiel on 2009-07-01
> **ryank76nz said:**
> That was the first thing I tried.

Come on folks, it can't be that hard to purge this thing. Firefox 3.0.11, Flash 10.0 d20. Delete everything with 'flash' in the name? Purge firefox itself?

Because I <3 quoting myself :D

> **miegiel said:**
> Try running the cleanup script again from the 1st post.

```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo apt-get purge flashplugin-nonfree
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

And then try installing the 64 bit beta flash player from Adobe (download link is at the bottom of the page, installation instructions should be in the .tar.gz file). [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz seems newer than 10.0 d20 to me.

Deleting every file with "flash" in it is a bad idea. Deleting every file ending with "libflashplayer.so" is a lot safer. And get rid of the "nspluginwrapper" junk too.

**ps :** After a purge and delete command, run the command a 2nd time and make sure you get the right error. "rm: cannot remove `test': No such file or directory" for *rm ...* And "Package test is not installed, so not removed" for *apt-get purge ...*
(*"test"* was just a not existing file / package name I used to get the errors ;))

---

### Post by lavinog on 2009-07-01
> **ryank76nz said:**
> ```
ryan@ryan-desktop:~$ md5sum /usr/lib/adobe-flashplugin
md5sum: /usr/lib/adobe-flashplugin: Is a directory
ryan@ryan-desktop:~$ md5sum /usr/lib/midbrowser/plugins/flashplugin-alternative.so
md5sum: /usr/lib/midbrowser/plugins/flashplugin-alternative.so: No such file or directory
ryan@ryan-desktop:~$ md5sum /usr/lib/xulrunner/plugins/flashplugin-alternative.so
md5sum: /usr/lib/xulrunner/plugins/flashplugin-alternative.so: No such file or directory
ryan@ryan-desktop:~$ md5sum /usr/lib/iceweasel/plugins/flashplugin-alternative.so
md5sum: /usr/lib/iceweasel/plugins/flashplugin-alternative.so: No such file or directory
ryan@ryan-desktop:~$ md5sum /usr/lib/iceape/plugins/flashplugin-alternative.so
md5sum: /usr/lib/iceape/plugins/flashplugin-alternative.so: No such file or directory
ryan@ryan-desktop:~$ 


```


Is there a way to get rid of ALL the other ones and start again?

cheers
Now it is saying that these don't exist, but they existed earlier.
> 
Come on folks, it can't be that hard to purge this thing. Firefox 3.0.11, Flash 10.0 d20. Delete everything with 'flash' in the name? Purge firefox itself?
It shouldn't be.

---

### Post by don_xvi on 2009-07-01
Add me to those having a miserable time trying to get this to work.
After such a long time suffering with unstable Flash, today I decided to upgrade from 8.04->8.10->9.04 and Firefox 3.5.
In my miserable 8.04 days, I tried 3 or 4 times to start from scratch hoping to make Flash work, and work all the time, so I have numerous bits & pieces all over.  I don't really know that this is the cause of my current problem, though, as it doesn't seem like Firefox is looking ANYWHERE I have copied the new Flash plugin, and I've copied it into a lot of directories this evening.
It seems like if I can tell Firefox "LOOK IN THIS DIRECTORY FOR THE PLUGIN", maybe it would work.  This install of FF seems to have forgotten all of my installed plugins except for this guy:
```
    File name: /home/q2user/RealPlayer/mozilla/nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4434 built with gcc 3.4.6 on Oct 1 2008

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
```
I installed FF 3.5 first according to the directions on the FF site which would seem to have put it into my home directory, but that didn't work, so I then used ubuntuzilla to install it.  I'm finding it hard to figure out where the active files are, and how to control it.  I've got libflashplayer.so in just about every directory on the drive...
Any advice besides wiping the OS out and starting over ?  That seems like such a Windows solution...

---

### Post by Yashiro on 2009-07-01
About time the binary was updated to fix the crashes that are still present in this plugin.

---

### Post by techfanboy81 on 2009-07-03
Its great that you posted the flash installation guide.  I'm having trouble installing with AMD.

---

### Post by ryank76nz on 2009-07-03
> **miegiel said:**
> 
**ps :** After a purge and delete command, run the command a 2nd time and make sure you get the right error. "rm: cannot remove `test': No such file or directory" for *rm ...* And "E: Couldn't find package test" for *apt-get purge ...*
(*"test"* was just a not existing file / package name I used to get the errors ;))

So what do I do if I don't get those errors? which I don't. What does that mean?

---

### Post by miegiel on 2009-07-03
> **ryank76nz said:**
> So what do I do if I don't get those errors? which I don't. What does that mean?

For the *rm* commands: If you don't get an error that the file doesn't exist it still exists and you didn't delete it the 1st time you ran the command.

For the *apt-get purge* commands: I made a stupid mistake generating the error :D The apt-get out put should look like :
```

user@machine:~$sudo apt-get purge libclamav5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Package libclamav5 is not installed, so not removed**
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
(I used the the libclamav5 package just as an example)

---

### Post by ryank76nz on 2009-07-05
> **miegiel said:**
> For the *rm* commands: If you don't get an error that the file doesn't exist it still exists and you didn't delete it the 1st time you ran the command.


If it didn't delete with sudo rm, how do I delete it?

---

### Post by miegiel on 2009-07-05
> **ryank76nz said:**
> If it didn't delete with sudo rm, how do I delete it?

Try adding the *v* switch to the command. For example :
```
sudo rm -rfd**v** /usr/lib/nspluginwrapper
```
It makes *rm* give more info on what it's doing.

If you can't make sense of the output post it here (in full and including the command you used).

---

### Post by shane2peru on 2009-07-05
Firefox 3.5 and flash or plugins in general seems to be having an issue. This is true across the boards.  See this thread for a little more info: [http://ubuntuforums.org/showthread.php?t=1175961](http://ubuntuforums.org/showthread.php?t=1175961)
(Read the thread don't just go doing all the commands, it doesn't seem to help)

I have tried too, either downgrade back to the normal firefox 3 in the repos, or go with Seamonkey, or Iceweasel.  

Shane

---

### Post by Martin Marshalek on 2009-07-14
I just used the scripts on the first post in Jaunty and they seem to have worked but I'm not sure. How do I check if I have 64-bit Java and Flash. Also, I an official version ever comes out, how do I uninstall what was installed by the scripts?

---

### Post by dlmarti on 2009-07-16
Flash was working for days, no issues at all (Jaunty 64bit, fresh install).

Today I needed Java so I went did an install through the browser, yeah Java worked.

Now flash is horribly broken, everytime I go to a site with flash I get an illegal instruction exception.

I uninstall all of the java stuff, but I get the same error.

I uninstalled the flash stuff (including manually removing the libflash file) and did a normal install from the browser, I get the same error.

I ran the scripts posted in this thread, and manually installed the libflash file, I get the same error.

Does anyone have any idea what I can try now?

---

### Post by tigrezno on 2009-07-16
the Getlibs .deb package is not downloadable anymore with the script

Now i don't have any flash player support, what can i do?

flash 10 is not working for me

do i need latest java for it to work?

[edit] also, I can't reinstall flashplugin-nonfree, as Adobe is not distributing flash9 anymore and synaptic is not installing it properly.

this is the error:

Downloading...
--22:15:58--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.162.70
Connecting to fpdownload.macromedia.com|88.221.162.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:15:59 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.


So, this is really broken on hardy

---

### Post by Jazmac on 2009-07-17
I'm getting no love from Flash on my 64bit processor.  Which is weird because when I ran Ubuntu 9.04 live, one installed. But installation on the hard drive I'm getting no love.  I'm a noob with Ubuntu and none of what I've found so far, is working.  So I came here for help.

Tried a few things there and still no love.  What is this so uber difficult to do on Lunux?

-JazMac

---

### Post by ikt on 2009-07-19
> **Jazmac said:**
> What is this so uber difficult to do on Lunux?

As far as I can tell, you can still install the regular 32 bit flash plugin on ubuntu just by going to add/remove programs, or by installing flash-nonfree, this guide is specifically for 64 bit.

---

### Post by lavinog on 2009-07-19
> **Jazmac said:**
> 
What is this so uber difficult to do on Lunux?

A lot of it is because 64bit flash has yet to come out of alpha status. Adobe has control of this.

---

### Post by Jazmac on 2009-07-19
> **ikt said:**
> As far as I can tell, you can still install the regular 32 bit flash plugin on ubuntu just by going to add/remove programs, or by installing flash-nonfree, this guide is specifically for 64 bit.

I figured I'd try my new search pal **Bing** to find something and I did.   Google kept me mired in nonsense for hours.  Anyway, **Bing** found a link to a script and got Flash 64bit  working flawlessly.  Now I can watch a few youtubes and keep on my quest to understand Ubuntu.

Thanks for the assist.

-JazMac

---

### Post by lavinog on 2009-07-19
> **Jazmac said:**
> I figured I'd try my new search pal **Bing** to find something and I did.   Google kept me mired in nonsense for hours.  Anyway, **Bing** found a link to a script and got Flash 64bit  working flawlessly.  Now I can watch a few youtubes and keep on my quest to understand Ubuntu.

Thanks for the assist.

-JazMac

I would have to say that is pretty ironic.

---

### Post by Jazmac on 2009-07-20
> **lavinog said:**
> I would have to say that is pretty ironic.

The fix?

-JazMac

---

### Post by lavinog on 2009-07-20
> **Jazmac said:**
> The fix?

-JazMac

microsoft solving a linux problem ;)

---

### Post by markbuntu on 2009-07-24
Yesterday there was an intersting post about 64bit flash on the pulseaudio mailing list by Tanu Kaskinen. It appears that 64bit flash10 is coded to use dmix which is a very odd choice since dmix has been deprecated and replaced by pulseaudio in many distros. Anyway, you can get flash to play through pulseaudio by doing this

Edit your ~/.asoundrc and add these lines

pcm.!dmix {
    type pulse
}

This will redirect flash and anything else still using dmix to pulseaudio so you can control where it plays. I have 4 different sound devices so flash sound was a real pita for me before doing this fix. Pulseaudio will probably get updated soon to take care of this but you can do the above now, yourself.

---

### Post by psablo on 2009-07-24
First, thanks to Kilz for the script.

My question is why do I have to run this script every couple of weeks?

Flash failing seems tied to the Ubuntu updates.

---

### Post by miegiel on 2009-07-25
> **psablo said:**
> First, thanks to Kilz for the script.

My question is why do I have to run this script every couple of weeks?

Flash failing seems tied to the Ubuntu updates.

Ubuntu updates don't break my 64bit flash, maybe you didn't completely remove/uninstall the 32bit flash player and the updates reinsert some 32bit flash files.

---

### Post by pstickar on 2009-07-26
I successfully installed Flash10 on Hardy and I'm in gratitude to you for taking the time to write the howto.

In this computer Hardy was installed very long ago. So it is not "clean".

During the installation I had a couple of problems, though.
The script that is mentioned at the top of the howto did not work. Then I went to the bottom of the howto and found a remove script. Then I went to the middle of the howto and found a sequence of manual instructions that did work. I can imagine there might be other inexperienced users like me who might find very useful a "table of contents" at the beginning of the howto.

I tested the instalation with wechoosethemoon.org and everything worked, incredibly well, but if there is a more thorough test available, it would be nice to know.

After the installation I noticed that acroread was not there any more. I had to reinstall it.

Again, many many thanks for your hard work.

Best,
p.

---

### Post by Crath on 2009-07-27
Just posting to say Thank You for the Flash10 Installer.  Successful installation on 9.04!

---

### Post by judicator01 on 2009-07-29
Is there an easy way to remove Gnash, swfdec etc if they were installed manually? How do I check if I have these (or anything else that would mess with flash) installed?

---

### Post by miegiel on 2009-07-29
> **judicator01 said:**
> Is there an easy way to remove Gnash, swfdec etc if they were installed manually? How do I check if I have these (or anything else that would mess with flash) installed?

If you still have the installer you might be able to figure out where the install script copied the files.

---

### Post by psablo on 2009-07-29
> **miegiel said:**
> Ubuntu updates don't break my 64bit flash, maybe you didn't completely remove/uninstall the 32bit flash player and the updates reinsert some 32bit flash files.

Good suggestion, any idea how to remove the 32bit Flash?

I've only run Kilz's script to remove old Flash files and I imagine it doesn't cover old 32bit files, but I can't tell by reading the script:

sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so

thanks

---

### Post by DougieFresh4U on 2009-07-30
Trying to follow the install for flash and I keep getting the following error:
```
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```
this is my first time using 64 bit and I really want to get this working. How can I get rid of this problem package? I am no 'guru' so please provide any codes if possible.
Thanks

---

### Post by miegiel on 2009-07-30
> **DougieFresh4U said:**
> Trying to follow the install for flash and I keep getting the following error:
```
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```
this is my first time using 64 bit and I really want to get this working. How can I get rid of this problem package? I am no 'guru' so please provide any codes if possible.
Thanks

Just installed the 64bit flash player in karmic. Wiser through experience I didn't install the 32bit junk and didn't need to uninstall/purge/remove it :twisted: If you do need to uninstall/purge/remove the 32bit junk the scripts in the 1st post should provide you with the inspiration you need.

I don't know what you're trying with *dpkg*, but this is how I "installed" the 64bit flash player.

[LIST=1]
[*]Download the 64bit flash player [_here_]("http://labs.adobe.com/downloads/flashplayer10.html") (link at the botom of the page).
[*]Extract *libflashplayer.so* to "where ever"
[*]In a terminal run ```
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins
```
[*]Restart firefox
[/LIST]

---

### Post by dcstar on 2009-07-31
> **miegiel said:**
> 
..........

[LIST=1]
[*]Download the 64bit flash player [_here_]("http://labs.adobe.com/downloads/flashplayer10.html") (link at the botom of the page).
[*]Extract *libflashplayer.so* to "where ever"
[*]In a terminal run ```
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins
```
[*]Restart firefox
[/LIST]

And just a reminder to all of us using the 64-bit Alpha player that the version there right now was released **July 30th**, so those with an older version may want to update.

---

### Post by quee0849 on 2009-07-31
My flash stopped working yesterday. I've tried dcstar's instructions above but they didn't work for me. I'm running Jaunty 64 bit.  Any suggestions?

---

### Post by miegiel on 2009-07-31
> **quee0849 said:**
> My flash stopped working yesterday. I've tried dcstar's instructions above but they didn't work for me. I'm running Jaunty 64 bit.  Any suggestions?

If you're referring to the post above yours, that's only the install procedure. You might need to remove/purge/uninstall stuff to get it to work. Check the [_1st post_]("http://ubuntuforums.org/showthread.php?t=772490") of the thread or try what I posted in [_post #741_]("http://ubuntuforums.org/showpost.php?p=7545844&postcount=741")

---

### Post by davisch on 2009-07-31
Nuts!!  I was hoping this one would work for me but no such luck.  I have an older Nvidia (GeForce5400FX) card that requires the "legacy" driver (173.xx).  Looks like my only hope is to buy a newer card.  I can still view the YouTube videos but not Hulu or Huffington Post.  It looks like a lot of sites are starting to put Flash stuff on their index pages and it is sure making it difficult for folks running older systems.  Come to think of it - it is probably a pretty small population - older 64 bit systems with legacy Nvidia cards....  Thanks for posting the instructions - they did work well.

---

### Post by Rody on 2009-08-01
I just modifed a script i found on the forms to install the new version, it is not as clean as a .deb but it works great.

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email]

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

---

### Post by miegiel on 2009-08-01
> **Rody said:**
> I just modifed a script i found on the forms to install the new version, it is not as clean as a .deb but it works great.
 
Nice 1 **Rody**

---

### Post by suda on 2009-08-01
I've been reading through the responses, and I'm still not sure how to get the latest Adobe Flash to install. I don't speak the "language." I installed Adobe Flash 10.0.22.87 with Synaptic Manager for Jaunty 9.04. It worked great until recently. I went to Adobe's site to download the latest flash player--the specs said 10.0.32.18-1 worked with AMD Athion 64. I downloaded the package for Debian from Adobe's site, but it would only work with i386 architecture.

So how do I get a current Adobe flash for Jaunty? Or is there an open-source flash player that will stream movies from youtube and Hulu? Any help is appreciated. 

Thanks!

---

### Post by lavinog on 2009-08-02
> **suda said:**
> I've been reading through the responses, and I'm still not sure how to get the latest Adobe Flash to install. I don't speak the "language." I installed Adobe Flash 10.0.22.87 with Synaptic Manager for Jaunty 9.04. It worked great until recently. I went to Adobe's site to download the latest flash player--the specs said 10.0.32.18-1 worked with AMD Athion 64...*snip* 

The 64bit flash plugin is in alpha state still.  You won't find it on adobes download page until it is out of beta.
You can find it at the bottom of this page: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

You will need to uninstall the plugin that is installed with synaptic...it isn't compatible with the 64bit driver

---

### Post by miegiel on 2009-08-02
> **suda said:**
> I've been reading through the responses, and I'm still not sure how to get the latest Adobe Flash to install. I don't speak the "language." I installed Adobe Flash 10.0.22.87 with Synaptic Manager for Jaunty 9.04. It worked great until recently. I went to Adobe's site to download the latest flash player--the specs said 10.0.32.18-1 worked with AMD Athion 64. I downloaded the package for Debian from Adobe's site, but it would only work with i386 architecture.

So how do I get a current Adobe flash for Jaunty? Or is there an open-source flash player that will stream movies from youtube and Hulu? Any help is appreciated. 

Thanks!

Juts to explain the basics :

The "normal" flash, the one you install when firefox tells you you need to install the plugin when you visit a flash site for example, is 32bit and needs to be wrapped in a 32bit "emulator" to run on 64bit ubuntu (or any other 64bit OS for that matter). Obviously not an ideal solution, but it kind of works. The main annoyance is that the 32bit flashplayer runs less smooth wrapped in the emulator then it would on a 32bit OS. For example, youtube movies don't run smooth in fullscreen.

However, adobe also has a 64bit flashplayer for linux. It's still in the alpha stage (it's not even beta yet), but it works fine. The conspiracy theorist in me says adobe is keeping it labelled as alpha because they don't want to tick off microsoft, since there is no 64bit flashplayer for windows at all.

If you want to install the 64bit flashplayer you'll need to get rid of all the 32bit stuff, including the wrapper or the 64bit player won't work.

I suggest you give **Rody**'s script from a few posts back a shot . It should work till adobe renames *libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz* to the next version. But you can also do it by hand using the 1st post and the last couple of posts above here for inspiration.

---

### Post by linux4me on 2009-08-02
I successfully installed the Adobe flash plugin, but I'm wondering what the best way to be notified of updates will be?

I signed up for an Adobe Labs account and subscribed to their newsletter, but they don't make it clear whether a notice for us poor Linux users is going to be in there.

---

### Post by miegiel on 2009-08-02
> **linux4me said:**
> I successfully installed the Adobe flash plugin, but I'm wondering what the best way to be notified of updates will be?

[LIST=1]
[*]Visit [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) from time to time works best.
[*]Subscribe to this thread and hope someone posts here when there is an update.
[/LIST]

> I signed up for an Adobe Labs account and subscribed to their newsletter, but they don't make it clear whether a notice for us poor Linux users is going to be in there.

I'm doubtful they will, but then I'm no fan of adobe and I suspect they aren't a fan of linux either. :twisted:

---

### Post by lavinog on 2009-08-02
> **miegiel said:**
> 
I'm doubtful they will, but then I'm no fan of adobe and I suspect they aren't a fan of linux either. :twisted:

Hopefully firefox3.5's support for embedded videos will convince others to stop using flash for video...after that the only thing flash would be good for is malicious advertising.

---

### Post by linux4me on 2009-08-02
Thanks, miegiel, I'm subscribed here and I'll post if I see an update on the Adobe Labs site.

---

### Post by suda on 2009-08-02
My thanks to you Lavinog. Will try it!

s.

---

### Post by suda on 2009-08-02
Thank you, miegiel!

s.

---

### Post by suda on 2009-08-02
Success! Thank you all! 

P.S. Didn't install as 10.0.32.18.linux-x86_64--but as 10.0.2d...whatever..it works for now.

s.

---

### Post by psablo on 2009-08-04
> **Rody said:**
> 
echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 


Thanks Rody!
My only question is with the line " cd ~ "

Does that imply something of the sort:
sudo mkdir /tmp/pluginstall
cd /tmp/pluginstall
and then wget ...flashplayer... ?
or is "cd ~" some syntax I'm not familiar with?

---

### Post by miegiel on 2009-08-04
> **psablo said:**
> Thanks Rody!
My only question is with the line " cd ~ "

Does that imply something of the sort:
sudo mkdir /tmp/pluginstall
cd /tmp/pluginstall
and then wget ...flashplayer... ?
or is "cd ~" some syntax I'm not familiar with?

~ is a "shortcut" to anyone's home directory

---

### Post by psablo on 2009-08-04
I've been running both the Kilz and the Rody script, tweaking them as best I can, and I can never get Hulu.com to play flash video's, so I finally just gave in and  upgraded to Jaunty 9.04 and installed Firefox 3.5 and now Hulu works.

---

### Post by dbuell on 2009-08-05
> **psablo said:**
> I've been running both the Kilz and the Rody script, tweaking them as best I can, and I can never get Hulu.com to play flash video's, so I finally just gave in and upgraded to Jaunty 9.04 and installed Firefox 3.5 and now Hulu works.

I followed the Rody script. Of course it was no different from what I had done previously. I continued to get Segmentation Faults that would cause Firefox to crash whenever I visited certain Flash sites. Hulu was one of the many that would cause a Segmentation Fault.

I have been frustrated by Adobe Flash for quite some time. nsplugins worked for everything, but unfortunately took alot of CPU time and memory as well. I removed nsplugins and installed the latest(july 30th) 64-bit alpha. The adobe player tests and demos worked flawlessly, but the seg faults made nearly any other flash site unavailable while crashing firefox.

I was able to correct this only by running firefox with sudo. I am now able to watch videos on Hulu. However, Rhapsody online doesn't work and full-screen is definitely still choppy.

Is everyone else running in sudo or root, or is there something else I am missing?

Thanks

And did anybody catch today's XKCD comic?

[http://xkcd.com/619/](http://xkcd.com/619/)

**edit**

A restart corrected the sudo thing. Of course I didn't exactly want to restart. (I had a pretty long up-time)

Rhapsody still doesn't work and playback is choppy in fullscreen, but otherwise this works very well.

---

### Post by archeryguru2000 on 2009-08-05
Amazing!  I just wanted to give you a HUGE thanks for this post.  =D>  I just recently started having problems with my flash player.  I think it must've come up after upgrading to FF-3.0... FYI I'm using Ub-8.10, 64bit.  I never noticed any problems since I rarely watch any videos through my browser.  Your script worked flawlessly.

Thanks again,
~~archery~~

---

### Post by novafluxx on 2009-08-11
Will this post thats stickied, ever be updated? Native 64-bit Java has been around for a few releases now, and a few months.

Native 64-bit Adobe Flash, however, is still in "alpha" stage, with a refresh just a month or so ago!

---

### Post by Thelasko on 2009-08-13
> **psablo said:**
> I've been running both the Kilz and the Rody script, tweaking them as best I can, and I can never get Hulu.com to play flash video's, so I finally just gave in and  upgraded to Jaunty 9.04 and installed Firefox 3.5 and now Hulu works.

Are you sure Adblock Plus isn't the culprit?

---

### Post by forlau on 2009-08-14
The scripts from RODY worked fine.:)

---

### Post by northwestuntu on 2009-08-14
> **novafluxx said:**
> Will this post thats stickied, ever be updated? Native 64-bit Java has been around for a few releases now, and a few months.

Native 64-bit Adobe Flash, however, is still in "alpha" stage, with a refresh just a month or so ago!

yeah i don't understand why they leave this up?  do any mods ever looks in here or what?

---

### Post by danbar on 2009-08-15
Thanks, it solved my problem too.

---

### Post by miegiel on 2009-08-15
> **northwestuntu said:**
> [QUOTE=novafluxx;7771311]Will this post thats stickied, ever be updated? Native 64-bit Java has been around for a few releases now, and a few months.

Native 64-bit Adobe Flash, however, is still in "alpha" stage, with a refresh just a month or so ago!

yeah i don't understand why they leave this up?  do any mods ever looks in here or what?[/QUOTE]

I guess because it still helps a lot of people. Following the OP without thinking might not be a good idea, but it still explains what's up and what needs to be done. Regarding flash that is, no one has mentioned java here for a while. And if you read the last posts in the thread you'll see plenty posts referring to [_rody's script_]("http://ubuntuforums.org/showthread.php?p=7717588#post7717588") which is still up to date.

---

### Post by miegiel on 2009-08-17
For those of you running alpha's of karmic koala (the up comming ubuntu 9.10), [_**dinxter** made a .deb_]("http://ubuntuforums.org/showthread.php?p=7800146#post7800146") to install the 64bit alpha flash player.

---

### Post by lockaar on 2009-08-19
Hello everyone,

I am very new to Ubuntu, but am desperately trying to install this flash script. I am using 8.10 Hardy and yes, I have a 64 bit processor.

I tried downloading the script in the first post...no luck, I see that the file is added to the firefox-addons folder but there is an "X" in the top right corner of the file icon indicating the link to the file is broken (see attached screenshots)...I don't know why that would be since I ran the script without errors it seems.

I also tried copying the script instructions which are further down the first post...no luck, it is the last step where I extract the file and are trying to move the file to the "add-on" folder where it fails, it says the following even though I do have that file on my desktop:
 > ~/Desktop$ tar -xzvf install_flash_player_10_linux.tar.gz install_flash_player_10_linux
tar: install_flash_player_10_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: install_flash_player_10_linux: Not found in archive
tar: Error exit delayed from previous errors
Lastly I tried running the script RODY posted, but to no avail.

Please help! I feel utterly crippled by not having flash capabilities in my browser.

Thanks.

---

### Post by miegiel on 2009-08-19
> **lockaar said:**
> Hello everyone,

I am very new to Ubuntu, but am desperately trying to install this flash script. I am using 8.10 Hardy and yes, I have a 64 bit processor.

I tried downloading the script in the first post...no luck, I see that the file is added to the firefox-addons folder but there is an "X" in the top right corner of the file icon indicating the link to the file is broken (see attached screenshots)...I don't know why that would be since I ran the script without errors it seems.

I also tried copying the script instructions which are further down the first post...no luck, it is the last step where I extract the file and are trying to move the file to the "add-on" folder where it fails, it says the following even though I do have that file on my desktop:
 Lastly I tried running the script RODY posted, but to no avail.

Please help! I feel utterly crippled by not having flash capabilities in my browser.

Thanks.

It looks like you tried to install the 32bit flash player 1st, the wrapper file is what the 32bit player get wrapped in so it can run on a 64bit linux. But **rody**'s script should remove all 32bit flash stuff.

Check **rody**'s script for the next line
```
wget http://download.macromedia.com/pub/l...6_64.so.tar.gz
```
and change it to
```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```
The link got abbreviated because the script wasn't in a code box ;)

---

### Post by lockaar on 2009-08-19
Wow Miegiel...you are absolutely awesome! That worked, those are some sharp eyes you have.

I know learning the scripting and ins and outs of Linux will be an uphill battle for me, but I am beginning to see how narly this community is, so help is only a post away.

Thanks again, and if there is a Miegiel fan-club, I will proudly join.

Also thanks to Rody for the script!!

---

### Post by miegiel on 2009-08-19
you're welcome :)

---

### Post by lockaar on 2009-08-20
Is it normal for certain flash sites to crash a lot using the Adobe 64 bit flash drivers?

Earlier when I would go to ESPN's mainpage my Firefox browser would crash, every time, but not on other sites. Earlier today though ESPN was fine after they changed the homepage stories.

Also I have the same problem with Justin.tv, every time (even now) I direct my browser to the site, Firefox crashes to desktop.

Is there any solution to this or does it come along with the shaky Adobe drivers?

---

### Post by linux4me on 2009-08-21
> **lockaar said:**
> Is it normal for certain flash sites to crash a lot using the Adobe 64 bit flash drivers?

Earlier when I would go to ESPN's mainpage my Firefox browser would crash, every time, but not on other sites. Earlier today though ESPN was fine after they changed the homepage stories.

Also I have the same problem with Justin.tv, every time (even now) I direct my browser to the site, Firefox crashes to desktop.

Is there any solution to this or does it come along with the shaky Adobe drivers?

Is it normal? I would say no. I've tried both the sites you mentioned and neither one caused FF to crash for me, and the Flash displays just fine. You may have another problem.

---

### Post by tad1073 on 2009-08-21
I edited your script to include the latest version of flash which is libflashplayer-10.0.32.18.linux-x86_64.so.

---

### Post by lockaar on 2009-08-21
> **linux4me said:**
> Is it normal? I would say no. I've tried both the sites you mentioned and neither one caused FF to crash for me, and the Flash displays just fine. You may have another problem.

I did a little investigating and I found out that* it is* the flash plug-in that is causing my Firefox browser to crash when going to sites like Hulu, Justin.tv, etc. I disabled my Flash plug-in and then went to all the sites I've had problems with, each one loaded fine (without the flash items). No crashes. However once I enabled the Flash plug-in then refreshed the pages...BOOM bye bye firefox.

I can post the terminal log if needed, but is it possible the latest Flash verison is bugged?

---

### Post by psablo on 2009-08-22
> **Thelasko said:**
> Are you sure Adblock Plus isn't the culprit?

DUH ... thanks.
I always look for the most complicated solution first.

---

### Post by davisch on 2009-08-22
> **lockaar said:**
> I did a little investigating and I found out that* it is* the flash plug-in that is causing my Firefox browser to crash when going to sites like Hulu, Justin.tv, etc. I disabled my Flash plug-in and then went to all the sites I've had problems with, each one loaded fine (without the flash items). No crashes. However once I enabled the Flash plug-in then refreshed the pages...BOOM bye bye firefox.

I can post the terminal log if needed, but is it possible the latest Flash verison is bugged?

I suspect that you have an nvidia video card that requires the "legacy" driver (173.xx).  This bug was documented on the Adobe site last year but it doesn't look like they are going to fix it.  In fact I don't know who really creates the problem - nvidia or adobe - but it cause Firefox to execute and "illegal" instruction that crashes it back to the desktop.  I have been running with the "flash block" add on for Firefox for some time now.  Sites never crash unless I try to view the flash.  Funny that some sites work just fine - like Youtube - and others - like Huffington Post - seem to always fail.  I think our only solution is to buy a newer video card.

---

### Post by lockaar on 2009-08-22
> I suspect that you have an nvidia video card that requires the "legacy" driver (173.xx). This bug was documented on the Adobe site last year but it doesn't look like they are going to fix it. In fact I don't know who really creates the problem - nvidia or adobe - but it cause Firefox to execute and "illegal" instruction that crashes it back to the desktop. I have been running with the "flash block" add on for Firefox for some time now. Sites never crash unless I try to view the flash. Funny that some sites work just fine - like Youtube - and others - like Huffington Post - seem to always fail. I think our only solution is to buy a newer video card.Unfortunately I would need to also upgrade my Motherboard, processor, whole she-bang. Not exactly possible being a poor college student. My current vid card is an Nvidia 6600 AGP.

I can post my terminal log of the crash if that might help find a solution, I hate not being able to get onto most of my usual sites (ESPN, Hulu, Justin.tv).

EDIT: Here is what my terminal reads every time I go to to Hulu, Justin.tv, and sometimes ESPN.
```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Illegal instruction

```I have no idea what any of that means, but I know it is flash related.

EDIT #2: I uninstalled my current Nvidia glx drivers and downgraded them to the legacy drivers, however after a reboot I still get the same crashing with the exact same error as above. I have now upgraded back to the newest drivers since that doesn't appear to be the issue.

I'm totally lost as to what I can do to fix this.

Also if I should make this its own thread just tell me, kinda new around these parts and since my issue is 64-bit flash related I figured this was the place for it.

---

### Post by northwestuntu on 2009-08-23
> **Rody said:**
> I just modifed a script i found on the forms to install the new version, it is not as clean as a .deb but it works great.

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email]

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

thanks for that.  was able to update my old flash that had been a little buggy.  now playing videos a lot better :guitar:

---

### Post by GTASouthPark on 2009-08-28
Hello I really need some help.

I had the flash player working last week.  I had firefox 3 and then i used ubuntuzilla and now am running 3.5.2

also I have the adblock plus add-on installed

i have tried many different methods for installing the flash player again but none have seemed to work correctly.

I'm running ubuntu 9.04 64 bit. and have an ATI graphics card

can anybody help me?  give me a good script that will work? or give me some good tips.  I really want flash player.  thanks in advance :)

---

### Post by miegiel on 2009-08-28
> **GTASouthPark said:**
> Hello I really need some help.

I had the flash player working last week.  I had firefox 3 and then i used ubuntuzilla and now am running 3.5.2

also I have the adblock plus add-on installed

i have tried many different methods for installing the flash player again but none have seemed to work correctly.

I'm running ubuntu 9.04 64 bit. and have an ATI graphics card

can anybody help me?  give me a good script that will work? or give me some good tips.  I really want flash player.  thanks in advance :)

The script in [_this post_]("http://ubuntuforums.org/showthread.php?p=7717588#post7717588") is still up to date. Beware that you properly copy the *wget url* (it's abbreviated in the post).

---

### Post by GTASouthPark on 2009-08-28
> **miegiel said:**
> The script in [_this post_]("http://ubuntuforums.org/showthread.php?p=7717588#post7717588") is still up to date. Beware that you properly copy the *wget url* (it's abbreviated in the post).

I followed that script, and it still did not work.  There is nothing in my firefox plugins, and when I try youtube it says that I either have an old version of flash player or java is turned off.

---

### Post by miegiel on 2009-08-29
> **GTASouthPark said:**
> I followed that script, and it still did not work.  There is nothing in my firefox plugins, and when I try youtube it says that I either have an old version of flash player or java is turned off.

If you're sure it's not java, you can paste the commands from the script in a terminal one by one (adding the *v* option to the *rm* commands makes it tell a little more about what is being done). Or cut the script in two, so you have separate remove and install scripts. After removing, search for any *libflashplayer.so* files or leftovers of the *nspluginwrapper*. When you're sure all the old parts of flash and the wrapper are gone, try installing it again.

---

### Post by jondale on 2009-08-29
I have an interesting issue where firefox core dumps anytime I visit a site with flash.  However, if I run firefox with sudo it works perfectly on every website.

I'm using the 10.0.32.18 alpha version of flash on firefox 3.5.2.
I have made sure NO other versions or nsplugginwrapper exist on the system.
This is with a fresh install with no addons installed.

Anybody else seen this or have any ideas?

---

### Post by miegiel on 2009-08-30
> **jondale said:**
> I have an interesting issue where firefox core dumps anytime I visit a site with flash.  However, if I run firefox with sudo it works perfectly on every website.

I'm using the 10.0.32.18 alpha version of flash on firefox 3.5.2.
I have made sure NO other versions or nsplugginwrapper exist on the system.
This is with a fresh install with no addons installed.

Anybody else seen this or have any ideas?

[http://ubuntuforums.org/showthread.php?t=1178332](http://ubuntuforums.org/showthread.php?t=1178332) might provide some inspiration. It seems you should always *gksudo firefox* and never *sudo firefox*

---

### Post by jondale on 2009-08-30
I'm not really sure why but after doing a couple system updates and rebooting the issue resolved itself.  I can now use firefox+flash with no sudo/gksudo just fine.

---

### Post by Zer0Nin3r on 2009-08-31
> **Rody said:**
> I just modifed a script i found on the forms to install the new version, it is not as clean as a .deb but it works great.

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email]

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

Thank you for the script.  I was able to go to the [beta site from Adobe]("http://labs.adobe.com/downloads/flashplayer10.html") and use their latest link.

In the future how will this work around affect us when the offical version comes out and is in the repositories?  How will we make the transition to the stable version?

---

### Post by Guilden_NL on 2009-08-31
> **GTASouthPark said:**
> I followed that script, and it still did not work.  There is nothing in my firefox plugins, and when I try youtube it says that I either have an old version of flash player or java is turned off.

Same here after hand installing.  All the bits and pieces are in the right directories, but it's not working.  I used the same script and the previous version of Flash in 3.0, after moving up to 3.5.1 I lost Flash.

Disabled Adblock and NoScript just to make sure that I wasn't blocking a necessary script.

---

### Post by kneewax on 2009-09-03
OK, I've read and re-read the advice in this thread BUT nothing I seem to do will get Flash working on my x64 Jaunty & Firefox 3.5  Also evesrsince going to FF3.5 all my program opening defaults are so screwed up I can't even 'open containing folder' for downloads.

Please is there an easy way to get FF3.5 on x64 to use flash properly?  the script looked excellent but actually just doesn't work on my machine.

I even tried each step of the script manually.  To no avail.  I've tried a direct download of the beta version from Adobe - but no dice.

Anyone?

[EDIT: Flash wax working fine before I went to 3.5]

---

### Post by miegiel on 2009-09-03
> **kneewax said:**
> OK, I've read and re-read the advice in this thread BUT nothing I seem to do will get Flash working on my x64 Jaunty & Firefox 3.5  Also evesrsince going to FF3.5 all my program opening defaults are so screwed up I can't even 'open containing folder' for downloads.

Please is there an easy way to get FF3.5 on x64 to use flash properly?  the script looked excellent but actually just doesn't work on my machine.

I even tried each step of the script manually.  To no avail.  I've tried a direct download of the beta version from Adobe - but no dice.

Anyone?

[EDIT: Flash wax working fine before I went to 3.5]

It could be something went wrong while updating FF. Have you tried uninstalling it (or uninstalling both flash and FF), remove any leftovers including stuff in your home and reinstalling it?

Same goes for others with FF3.5 problems after updating it ;) Maybe there's a "FF3.5 poked me in the eye after updating it from FF3" thread.

---

### Post by GTASouthPark on 2009-09-04
I uninstalled firefox through synaptic.  then reinstalled firefox 3.0 through the repository, and it is still at version 3.5.2, and the flash player still doesn't work even doing the script again hmmm

---

### Post by kneewax on 2009-09-09
> **miegiel said:**
> It could be something went wrong while updating FF. Have you tried uninstalling it (or uninstalling both flash and FF), remove any leftovers including stuff in your home and reinstalling it?

Same goes for others with FF3.5 problems after updating it ;) Maybe there's a "FF3.5 poked me in the eye after updating it from FF3" thread.

Yeah I tried this - hoewever despite the *uninstall* FF remains at 3.5 and the same issues still there.

Interestingly Flash works in Epiphany so it is def. a FF 3.5 specific issue...

---

### Post by michael37 on 2009-09-09
[thread=1259102]Updated script version 0.2 for new version of Flash.[/thread]

I wish the author would update the original post...

---

### Post by dbuell on 2009-09-11
> **dbuell said:**
> I followed the Rody script. Of course it was no different from what I had done previously. I continued to get Segmentation Faults that would cause Firefox to crash whenever I visited certain Flash sites. Hulu was one of the many that would cause a Segmentation Fault.

I have been frustrated by Adobe Flash for quite some time. nsplugins worked for everything, but unfortunately took alot of CPU time and memory as well. I removed nsplugins and installed the latest(july 30th) 64-bit alpha. The adobe player tests and demos worked flawlessly, but the seg faults made nearly any other flash site unavailable while crashing firefox.

I was able to correct this only by running firefox with sudo. I am now able to watch videos on Hulu. However, Rhapsody online doesn't work and full-screen is definitely still choppy.

Is everyone else running in sudo or root, or is there something else I am missing?

Thanks

And did anybody catch today's XKCD comic?

[http://xkcd.com/619/](http://xkcd.com/619/)

**edit**

A restart corrected the sudo thing. Of course I didn't exactly want to restart. (I had a pretty long up-time)

Rhapsody still doesn't work and playback is choppy in fullscreen, but otherwise this works very well.


I should have clarified the statement regarding Rhapsody.

Rhapsody does allow the 25 free songs per month to play using the x86_64 flash 10 alpha release (7/30/09) but it appeared that I could not sign in.

However, what I did not realize was that it did sign me in, but still appeared as though I had not signed in. The "25 plays left" still appears, but it does not count down when I play songs after signing in. Hopefully this helps someone that let the interface fool them as it did me.

---

### Post by Anusiya on 2009-09-11
> **lockaar said:**
> I did a little investigating and I found out that* it is* the flash plug-in that is causing my Firefox browser to crash when going to sites like Hulu, Justin.tv, etc. I disabled my Flash plug-in and then went to all the sites I've had problems with, each one loaded fine (without the flash items). No crashes. However once I enabled the Flash plug-in then refreshed the pages...BOOM bye bye firefox.

I can post the terminal log if needed, but is it possible the latest Flash verison is bugged?

There is a fix for this. Please refer to [HTML]http://ubuntuforums.org/showthread.php?t=1263905[/HTML]

Thanks,
Anusiya

---

### Post by northwestuntu on 2009-09-12
> **michael37 said:**
> [thread=1259102]Updated script version 0.2 for new version of Flash.[/thread]

I wish the author would update the original post...

the author has moved on to arch linux.  so i don't think it will get updated.  you would think a mod would put some kind of updated info in the sticky since that's what stickys are for?

---

### Post by bapoumba on 2009-09-12
[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

Please refer to the above thread, I'm closing here and unstick.

---

