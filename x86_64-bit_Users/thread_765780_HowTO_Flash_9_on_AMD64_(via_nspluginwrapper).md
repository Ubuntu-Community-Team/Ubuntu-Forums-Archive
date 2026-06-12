---
title: "HowTO Flash 9 on AMD64 (via nspluginwrapper)"
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by ajmorris on 2008-04-24
**This is from Kilz's original post, all thanks go to him. Just helping out with forum stickies from the forum upgrade. (feel free to have Kilz repost it.)**


**[SIZE=4][COLOR=Sienna]Nspluginwrapper Install Script for Dapper-Gutsy(Updated 3/8/08 )[/COLOR][/SIZE]**
This script will install the nspluginwrapper, and Flash for your 64bit browser for the **amd64 version of Ubuntu** Dapper, Edgy and Feisty, and Gutsy. It will not work on the i386 or 32bit version. 
It will not install other plugins. There are other plugins, java being one, that nspluginwrapper can not work with. The script has been updated on 8/21/07. It no longer uses alien on Feisty, and it will clean out previous installs. I have also made a script that installs the old flash plugin that seems to work better than the new one. 
[Click here for the script that installs the previous r48 plugin]("http://home.comcast.net/%7Eubuntume/oldflash-0.1.5-1.tar.gz") **[COLOR=DarkRed](recommended)[/COLOR]** 
or
[Click here if you want to download the script for r115 Flash plugin.]("http://home.comcast.net/%7Eubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz") **([COLOR=Red]THIS FLASH IS FULL OF BUGS - INSTALL AT YOUR OWN RISK[/COLOR])**

If the script works for you please consider clicking this thank you icon.  [[IMG]http://i9.photobucket.com/albums/a74/tghc/thanks.png[/IMG] ]("http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=4589989") 

Due to the problems with Flash and Gutsy the script has been modified to install flash and set it up for gutsy using the nspluginwrapper package in the Gutsy repo's.

The script also works with the 64bit builds of [Swiftweasel]("http://sourceforge.net/projects/swiftweasel/"), an optimized build of Firefox.

**[SIZE=4][COLOR=Sienna]Instructions[/COLOR][/SIZE]**
1. Download the script.
2. Right click on the tar.gz and select "Extract Here"
3. Close **all **browsers.
4. Inside the folder that extracts is a "GetFlash" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done.  :grin:

SD-Plissken has pointed out that users of the Fluxbox desktop may need to open a terminal and launch the script by navigating to it and using this command to launch the script.
     Code:
     sudo ./GetFlash 
**[SIZE=4][COLOR=Red]How to get help (Please Read Before Making a Post)[/COLOR][/SIZE]**
If you have any problems and need help Please read the included README file for instructions on what information to report in your post. **[COLOR=Red]Do not repeatedly install the script or try other methods until you have read the sections below and *made a post*.[/COLOR]**

**[SIZE=4][COLOR=Sienna]Common Issues[/COLOR][/SIZE]**
[SIZE=3]**Sound**[/SIZE]
First download and double click on [this package]("http://home.comcast.net/%7Edeletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") to install it.
Gutsy - People using Gutsy that have sound problems [should read this thread.]("http://ubuntuforums.org/showthread.php?t=655825")

[SIZE=3]**Sessions**[/SIZE]
Please make sure to start a new browser session if you run into any issues.

[SIZE=3]**Other Flash Plugins. **[/SIZE]
If after installing the script you cant see flash. Make sure that all attempts at installing other flash plugins (Gnash, swfdec, etc) have been uninstalled and the files they created have been removed. The remains of past failed attempts are the #1 cause of flash not working. This is because the files conflict with the flash plugin.

[SIZE=3]**Firefox 3 Beta's **[/SIZE]
This script sets up flash for the 2.0 series of firefox, Firefox 3 beta will also work, but you will need to link the plugins. [This post gives info on the Beta 3.]("http://ubuntuforums.org/showthread.php?t=695674") You may need to edit the commands if your Firefox beta folder is in another place. Forum member kurtpete offers some additional help [in this post.]("http://ubuntuforums.org/showpost.php?p=4359542&postcount=826")

[SIZE=3]**What to Include in your Post **[/SIZE]
When asking for help, please include the results of the following commands.
     Code:
     ls -al /usr/lib/mozilla//plugins/
ls -al /usr/lib/firefox/plugins/
uname -a 
[SIZE=3]**Unmet Dependencies ia32-libs**[/SIZE]
Users with any of the following errors during install are [directed to this post.]("http://ubuntuforums.org/showpost.php?p=4417385&postcount=914")
The ******* in rthe following error is a wildcard that represents any package name.
     Code:
     The following packages have unmet dependencies:
********: Depends: ******** but it is not going to be installed 
or
     Code:
     nspluginwrapper depends on ia32-libs; however:
Package ia32-libs is not installed. 
[SIZE=3]**Remove Script**[/SIZE]
[This link]("http://home.comcast.net/%7Eubuntume/RemoveScript.tar.gz") will download the removal script. Extract the file, then double click on the RemoveScript file and select run in terminal. This script is unnecessary if you are having issues getting the script to work. Its only use is to completely remove the applications from the script. This is counterproductive when people cant get the script to work because it removes clues as to what worked and what didnt.

[SIZE=3]**Hardy Heron**[/SIZE]
This script is not setup to work with Hardy Heron. If      Code:
     sudo apt-get install flashplugin-nonfree 
 does not install flash. Make a post on the Hardy Heron section of the forum and (**most important**)[ file a bug report on launchpad.]("https://launchpad.net/ubuntu") Part of running a Beta is reporting the bugs so they can be fixed.

---

### Post by GumbyX on 2008-04-25
This script will now work in 8.04!! :) Just tired it and it works wonderfully. Thanks again for getting this scrip up. Saved me a lot of trouble.

---

### Post by Patsoe on 2008-04-25
> **GumbyX said:**
> This script will now work in 8.04!! :) Just tired it and it works wonderfully. Thanks again for getting this scrip up. Saved me a lot of trouble.

I don't think you need it on Hardy? I encountered a flash-page in Firefox and it just prompted me to install a flash plugin. Even gave three options (one of them being adobe's).

---

### Post by hackle577 on 2008-04-25
I did what you described Patsoe, and installed Adobe's version (not Gnash or Swfdec). It worked for a while but now it isn't working at all, I don't get video or audio.

I also have flashplugin-nonfree installed. Would that create a conflict?

---

### Post by Patsoe on 2008-04-25
hackle577: I don't get it - as far as I can see flashplugin-nonfree *is* the Adobe plugin? [http://packages.ubuntu.com/hardy/flashplugin-nonfree](http://packages.ubuntu.com/hardy/flashplugin-nonfree)

I chose swfdec, which didn't give any trouble so far.

---

### Post by fogcat on 2008-04-25
I used the script:  positive results.

No problems at all in this regard...cannot speak for others.

Machine:    Intel E6550
            GA-P35-DS3L/S3L  MB
            2 GB DDR2 800Mhz
            Nvidia 8600GT

fogcat

---

### Post by hackle577 on 2008-04-25
Acutally, Patsoe, you are correct. I was confused lol

My Flash is now working though, just seemed to cut out randomly. I think I'll have to investigate this further...

---

### Post by thekat on 2008-04-25
Flash is working great..

```

sudo apt-get install flashplugin-nonfree

```

---

### Post by teslarage on 2008-04-26
Works great for me using the above command since Hardy Alpha 6.

---

### Post by sirzepp on 2008-04-27
Just upgraded to Hardy 8.04 LTS.

flash is not working

The apt-get flashplugin-nonfree does not work

I've made a comment on the on-going bug report that seems to apply.

---

### Post by vishalrao on 2008-04-28
Yes, like Patsoe above, I too did it the easy way...

To get Flash on Hardy amd64, I just visited a Flash-enabled page in Firefox where it asked to install the plugin and I clicked that (might have also clicked allow popup/install), I believe Ubuntu's FF plugin takes care of installing your choice of Adobe Flash or one of the other Free versions via the apt machinery... works fine for me.

---

### Post by LaRoza on 2008-04-28
Closed. See active sticky.

---

