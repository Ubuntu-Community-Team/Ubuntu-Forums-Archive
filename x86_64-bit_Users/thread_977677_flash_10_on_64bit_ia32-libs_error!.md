---
title: "flash 10 on 64bit ia32-libs error!"
date: 2008-11-10
forum: x86 64-bit Users
---

### Post by yayh on 2008-11-10
Dear All,

i am trying to install flash 10 on 8.10 ubuntu 64bit but i am geting error cannot install ia32-libs to run 32bit softwares on ubuntun 64bit

```
yousef@Linux-desktop:~/Desktop$ sudo sh ./flash10_en.sh
Closing Firefox
Downloading and instaling Getlibs for required libraries
--2008-11-10 21:32:55--  http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
Resolving www.boundlesssupremacy.com... 209.123.149.151
Connecting to www.boundlesssupremacy.com|209.123.149.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6498 (6.3K) [text/plain]
Saving to: `getlibs-all.deb'

100%[======================================>] 6,498       21.5K/s   in 0.3s    

2008-11-10 21:32:57 (21.5 KB/s) - `getlibs-all.deb' saved [6498/6498]

(Reading database ... 99348 files and directories currently installed.)
Preparing to replace getlibs 2.06 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (2.06) ...
Removing previous installs of flash:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package nspluginwrapper is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Installing ia32-libs and nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32asound2 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32ncurses5 but it is not going to be installed
             Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 (>= 2.3.6-2) but it is not going to be installed
             Recommends: lib32nss-mdns but it is not going to be installed
  nspluginwrapper: Depends: lib32gcc1 (>= 1:4.1.1-21+ia32.libs.1.19) but it is not going to be installed
                   Depends: libc6-i386 (>= 2.1) but it is not going to be installed
E: Broken packages
Getting libs
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
  ia32-libs: Depends: lib32asound2 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32ncurses5 but it is not going to be installed
             Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 (>= 2.3.6-2) but it is not going to be installed
             Recommends: lib32nss-mdns but it is not going to be installed
E: Broken packages
The following i386 packages will be installed: libcurl3
Continue [Y/n]? y
libcurl3 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
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
  ia32-libs: Depends: lib32asound2 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32ncurses5 but it is not going to be installed
             Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 (>= 2.3.6-2) but it is not going to be installed
             Recommends: lib32nss-mdns but it is not going to be installed
E: Broken packages
The following i386 packages will be installed: libnss3-1d
Continue [Y/n]? y
libnss3-1d was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
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
  ia32-libs: Depends: lib32asound2 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32ncurses5 but it is not going to be installed
             Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 (>= 2.3.6-2) but it is not going to be installed
             Recommends: lib32nss-mdns but it is not going to be installed
E: Broken packages
The following i386 packages will be installed: libnspr4-0d
Continue [Y/n]? y
libnspr4-0d was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
Installing Flash Player 10
--2008-11-10 21:33:08--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
Resolving fpdownload.macromedia.com... 92.122.2.70
Connecting to fpdownload.macromedia.com|92.122.2.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3958745 (3.8M) [application/x-gzip]
Saving to: `install_flash_player_10_linux.tar.gz.3'

100%[======================================>] 3,958,745    239K/s   in 17s     

2008-11-10 21:33:25 (222 KB/s) - `install_flash_player_10_linux.tar.gz.3' saved [3958745/3958745]

install_flash_player_10_linux/
install_flash_player_10_linux/flashplayer-installer
install_flash_player_10_linux/libflashplayer.so
sudo: nspluginwrapper: command not found
Linking the libraries so that firefox can see them.
Done :-)
You may re-start Firefox now
yousef@Linux-desktop:~/Desktop$ 

```

---

### Post by cariboo on 2008-11-10
You can install flash from the repositories, The Adobe server seems pretty slow lately, so just wait for it to finish. I always install the ubuntu-restricted-extras meta packge, this installs all the codecs I need to play most types of audio/video files. You can install the ubuntu-restricted-extras using System-->Administration-->Synaptic package Manager.

Jim

---

### Post by Sef on 2008-11-11
Also check out this [tutorial]("http://ubuntuforums.org/showthread.php?t=772490") on installing flash on 64-bit.

---

### Post by yayh on 2008-11-12
thanks to all
i have follow the tutorial for flash 10 on 64bit, but i am getting the error above.

and installing ubuntu-restricted-extras  did not help also getting alots of error.

---

### Post by caver1 on 2008-11-12
Try this. Worked for me.
[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)
caver1

---

### Post by Kilz on 2008-11-12
> **caver1 said:**
> Try this. Worked for me.
[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)
caver1

That link has a command that automatically downloads, and then without any further action from the user, installs a script right after download. This has a great possibility for abuse and should not be done. New users may not see that is what that command does.
One thing that could happen is the script can be changed at any time to include malicious commands or install malicious software. Since the user cant see what the script is going to do before installing it they have no idea what its going to do.

---

### Post by yayh on 2008-11-14
thanks all,

but still the same error maybe this script works only on 8.04 64bit not on 8.10 64bit

---

### Post by caver1 on 2008-11-14
> **Kilz said:**
> That link has a command that automatically downloads, and then without any further action from the user, installs a script right after download. This has a great possibility for abuse and should not be done. New users may not see that is what that command does.
One thing that could happen is the script can be changed at any time to include malicious commands or install malicious software. Since the user cant see what the script is going to do before installing it they have no idea what its going to do.

Being that the author does give you a way to view the script before you run it there is no problem. 
It was the only way I could get Flash to work on my system. And you can see the script first if you want.
cavewr1

---

### Post by Yellow Pasque on 2008-11-14
It looks like you don't have all the standard repos installed. Go to System -> Administration -> Software Sources and make sure at least main, universe, and multiverse are enabled.

Also, install Flash from the repo if possible.

---

### Post by caver1 on 2008-11-14
> **Temüjin said:**
> It looks like you don't have all the standard repos installed. Go to System -> Administration -> Software Sources and make sure at least main, universe, and multiverse are enabled.

Also, install Flash from the repo if possible.



Not sure to who you were replying. 
I do have all the repos installed. My Flash worked fine until just a few days ago. Then it quit.
There are several answers out there to this problem and all of them work but not for everyone.
This tells me there are several different problems giving similar problems.
caver1

---

### Post by Yellow Pasque on 2008-11-14
My post was directed at the OP.

---

### Post by Kilz on 2008-11-14
> **caver1 said:**
> Being that the author does give you a way to view the script before you run it there is no problem. 
It was the only way I could get Flash to work on my system. And you can see the script first if you want.
cavewr1

Wellll, that is a matter of opinion. 

It also sets a dangerous example, disregarding even imho common sense safety measures. That you had luck and got up working is nice. But at any time the link could change, the link could point to another file. The links from the command and the hyperlink on the page could be made to be 99.9% alike and so pass a quick look, at any time. Come on, there are tons of ways of making it deceptive. 
That is , if they see the link. You know that light text that isnt underlined near the bottom. Of course the command is in big bold letters before it.
But even if nothing happens here. If this site is safe, its just pure luck that it is. It could just as easily be unsafe. Should we toss out doing things with a little safety? Not in my opinion. We also have to realize that others who may not experienced users may also read these posts in the future. 
Basic safety of reading and understanding what a shell script does before running it is a good idea. That is unless you would like to see your hard drive wiped.

---

### Post by caver1 on 2008-11-14
> **Kilz said:**
> Wellll, that is a matter of opinion. 

It also sets a dangerous example, disregarding even imho common sense safety measures. That you had luck and got up working is nice. But at any time the link could change, the link could point to another file. The links from the command and the hyperlink on the page could be made to be 99.9% alike and so pass a quick look, at any time. Come on, there are tons of ways of making it deceptive. 
That is , if they see the link. You know that light text that isnt underlined near the bottom. Of course the command is in big bold letters before it.
But even if nothing happens here. If this site is safe, its just pure luck that it is. It could just as easily be unsafe. Should we toss out doing things with a little safety? Not in my opinion. We also have to realize that others who may not experienced users may also read these posts in the future. 
Basic safety of reading and understanding what a shell script does before running it is a good idea. That is unless you would like to see your hard drive wiped.




All you have to do is look at the script in your text editor before you use it. If you decide that it can do little or no harm then save it and run it,  If you can't look at a script and figure out if it's good or not it doesn't  matter where the script came from. I have tried  the other "fixes" that are also safe and they didn't work. I could post them but I didn't because they didn't work. This one did and is safe so I posted it. And you can look at it before you run it if you know what you are doing.
caver1

---

### Post by alexcuervo on 2008-11-17
> **Kilz said:**
> Wellll, that is a matter of opinion. 

It also sets a dangerous example, disregarding even imho common sense safety measures. That you had luck and got up working is nice. But at any time the link could change, the link could point to another file. The links from the command and the hyperlink on the page could be made to be 99.9% alike and so pass a quick look, at any time. Come on, there are tons of ways of making it deceptive. 
That is , if they see the link. You know that light text that isnt underlined near the bottom. Of course the command is in big bold letters before it.
But even if nothing happens here. If this site is safe, its just pure luck that it is. It could just as easily be unsafe. Should we toss out doing things with a little safety? Not in my opinion. We also have to realize that others who may not experienced users may also read these posts in the future. 
Basic safety of reading and understanding what a shell script does before running it is a good idea. That is unless you would like to see your hard drive wiped.

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

### Post by Kilz on 2008-11-18
> **alexcuervo said:**
> @ Klitz, I wonder what makes your scripts more trustworthy? This is also a 3rd party website. YOUR scripts can also change at any time. And some of YOUR scripts are even hosted on a home computer, for instance this one: [http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz](http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz) at your post at [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)) 

The source code for the script at ([http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)) has always been available for everyones review and CONSTRUCTIVE criticism.

Besides, it is not true that the command "wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh) && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh" will "Automatically Install" as you put it. The user still needs to give his authorization before is executed. I see no difference in this and you telling your users in your posts to:

 You have a command on the site and it is posted elsewhere. This command downloads and as soon as the download is done, the script installs. This is unsafe. Please feel free to find that on any script I have created or offered, good luck, because it doesn't exist.
Downloading and installing should not be done from any 3rd party site unless the user has a chance to go over the script, to at least look at it.
Pointing out my scripts may not be safe only reinforces my suggestion for everyone read the script **[COLOR="Red"]any[/COLOR]** they install. That should be easier on one of mine as they don't automatically start. It is a huge safety problem when that happens.

---

### Post by steveneddy on 2008-11-19
How about installing the 64 bit alpha version of Flash?

I did this tonight and it works better on my laptop than trying to get the 32 bit version to work correctly.

---

