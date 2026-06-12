---
title: "Wine not launching"
date: 2018-06-03
forum: Wine
---

### Post by miambilistore on 2018-06-03
I had installed Wine and when I try to launch it, nothing happens. Even the wine WIndows manager doesn't show.

This is what I get when I try to install anything or do anything at all in the terminal:

```
Err:9 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu bionic Release           
  404  Not Found [IP: 91.189.95.83 80]
Ign:10 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease               
Get:11 http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu bionic/main amd64 Packages [596 B]
Err:13 https://dl.winehq.org/wine-builds/ubuntu bionic Release                 
  404  Not Found [IP: 151.101.172.69 443]
Get:14 http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu bionic/main i386 Packages [600 B]
Get:15 http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu bionic/main Translation-en [168 B]
Reading package lists... Done                       
E: The repository 'http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Kindly assist!

---

### Post by kc1di on 2018-06-03
What the error message show it that it's trying to connect to a server, what program are you trying to install?
If it were me at that point I would install playonlinux ```
sudo apt install playonlinux
``` once installed it will be found in the games section of the menu.
Play on linux is a nice front end for wine and allows you to install and run programs much easier. It also allows you to install many different versions of wine which may help with running some programs. 
You can read about it [here :]("https://www.playonlinux.com/en/") 

It installs program in their own virtual files and thus avoids problems with other programs you may have installed. 

Wine can be hard to get set up on it's own.  And not all windows programs will run well under it. 
you should check the [wine apps list found here]("https://appdb.winehq.org") to see if your program has been successfully done under wine.
Anything on the list that does not have at least a gold or silver will not run well under wine. 
good luck.

---

### Post by PaulW2U on 2018-06-03
@miambilistore, the two PPAs that are showing errors have not been updated for the bionic release. I'm not sure why you are using them anyway as the latest version of WINE, i.e. 3.01, is in the Ubuntu repositories so can be installed without the use of any PPA. If you remove them your errors will go away when you next update.

In the Software & Updates application go to the "Other Software" tab and uncheck the respective entries or highlight them and click "Remove".

---

### Post by miambilistore on 2018-06-03
Hi. I have installed as instructed on the Wine version. I'm uninstalling Wine. Please tell me the other method to install it.

I have an xz file downloaded.

---

### Post by miambilistore on 2018-06-03
Hi. playonlinux is already installed and is not helping me as wine has issues and is telling me something about wine having issues.

---

### Post by PaulW2U on 2018-06-04
> **miambilistore said:**
> Hi. I have installed as instructed on the Wine version. I'm uninstalling Wine. Please tell me the other method to install it.

I have an xz file downloaded.
From what you have posted it is unclear how you first installed WINE. It is always best to install software from the Ubuntu repositories. To install WINE, the terminal command is:
```
sudo apt install wine
```
There should be no need to go to the winehq.com for installation instructions or to download files to install manually. Installing from the official repositories will ensure that you have software that works with your version of Ubuntu. I've never used playonlinux but may be the issues that you are seeing are due to installing incompatible versions of playonlinux and WINE from different sources?
> **miambilistore said:**
> Hi. playonlinux is already installed and is not helping me as wine has issues and is telling me something about wine having issues.
I'm assuming that you took kc1di's advice and installed playonlinux from the Ubuntu repositories. Let us know when you have done the same with WINE. If you find that something is not working then please give full details of what happens when you start the program including the full text of any error messages then may be someone can help you further.

---

### Post by kc1di on 2018-06-06
install wine in playonlinux by selecting the tool tab and manage wine versions you can install wine upto version 3.9 at this time. 
to install wine from the ubuntu repository install from terminal with this command ```
sudo apt install wine-stable
```

good luck.

---

### Post by MikeCyber on 2018-06-08
don't scare newbies. synaptic is easier to use.

---

### Post by mlnease on 2018-06-11
Hello,

I'm having this same problem.  I first installed from Synaptic; it appeared and appears installed.  But it doesn't appear in my xfce4-panel Application Menu or on any other menu on the system.

I reinstalled from Synaptic with the same result (also of course updated, restarted etc.).

When I ran ```
sudo apt install wine-stable
``` I received ```
wine-stable is already the newest version (3.0-1ubuntu1).
```

.wine with its usual subdirectories is present at /home/mn/.wine.  Is that where is should've gone?

Thanks in advance for any help.

---

### Post by PaulW2U on 2018-06-12
> **mlnease said:**
> I first installed from Synaptic; it appeared and appears installed.  But it doesn't appear in my xfce4-panel Application Menu or on any other menu on the system.
I'm not a WINE user myself but does the thread [Whats happening with wine?]("https://ubuntuforums.org/showthread.php?t=2391933") and the bug report [Xdg .desktop, .directory and mimetype files missing in the package]("https://bugs.launchpad.net/ubuntu/+source/wine-development/+bug/1576326") help at all?

@miambilistore, if you return to this thread does this help explain what you are seeing?

---

### Post by mlnease on 2018-06-12
> **PaulW2U said:**
> I'm not a WINE user myself but does the thread [Whats happening with wine?]("https://ubuntuforums.org/showthread.php?t=2391933") and the bug report [Xdg .desktop, .directory and mimetype files missing in the package]("https://bugs.launchpad.net/ubuntu/+source/wine-development/+bug/1576326") help at all?

@miambilistore, if you return to this thread does this help explain what you are seeing?

Thanks for this, PaulW2U.  It certainly looked (maybe still looks) promising; but I've been all over the pages and links and meself haven't got there yet.  I'll report here if I figure it out.

Meanwhile...you mention you don't use WINE; I have a couple old .exe's that I don't know how to run without (shudder) installing Windows on another partition.  Any suggestions?

Thanks again and in advance.

---

