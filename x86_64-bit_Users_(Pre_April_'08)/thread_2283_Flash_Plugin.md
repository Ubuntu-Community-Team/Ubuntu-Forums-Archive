---
title: "Flash Plugin"
date: 2004-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cygnia on 2004-10-26
I can hear the groaning out there...yes I'm stuck on this last stumbling block. After reading another thread here about installing java and using the info provided to finally succeed, I went and grabbed a beer from the fridge in celebration. =D> 

But now I'm hungry for more. I've been RTFMing this for some time, although for the last six months since getting my AMD64 system SuSE has been holding my hand and doing it for me, so I didn't have to worry. I even tried to just download the latest Firefox and install in /usr/local but it wouldn't start.

So is there any way to get the flash plugin working in the Firefox that comes with Ubuntu? Any help would be great. Thanks.

-- 
Bryce

---

### Post by amoser on 2004-10-26
Umm, first download the tar/bzip file, unpack it.  Second open a root terminal, and cd into the directory it unpacked (install_flash_player_7_linux).  Execute flashplayer-installer (./flashplayer-installer). Press enter untill you see(exit all browser that you are running) <Please enter the installation path of the Mozilla, Netscape,or Opera browser (i.e., /usr/lib/mozilla):>.  Then type in /usr/lib/mozilla-firefox, hit enter.

Your done, so crack open one for me and one for you.

~Alan

---

### Post by Cygnia on 2004-10-26
amoser: thanks for responding, but I get the following error when I try to run the installer:

cygnia@cygniapolis:~/install_flash_player_7_linux $ sudo ./flashplayer-installer
 ERROR: Your architecture, \'x86_64\', is not supported by the
       Macromedia Flash Player installer.

In addition, I've tried to simply copy the two relevent files into the plugin directory, but then Firefox won't start at all. So that's why I'm stumped.

---

### Post by amoser on 2004-10-26
I do not bring good news, from what I have read, Macromedia has not ported the flash player over to AMD 64.  So sorry, I tried to help.  Yeah, I am not luckey enough to own a 64 bit proccessor, so sorry

---

### Post by burque on 2004-10-27
This probably requires multiverse in your sources.list, but I'm not sure. I use apt-get from the command line, not Synaptic. The package

flashplugin-nonfree

installed without a hitch for me when I did

sudo apt-get install flashplugin-nonfree

Here's the contents of my /etc/apt/sources.list:
*********************************************************************************

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

---

### Post by jdong on 2004-10-27
That doesn't work. There's no 64bit flash, and Firefox is 64-bit with the AMD64 version. Therefore, you need the 32-bit plugin _AND_ a 32-bit firefox, which seems to be an unsupported setup in Ubuntu.

Gentoo people had similar issues; PETITION FOR 64-BIT  FLASH!!!

---

### Post by Cygnia on 2004-10-27
jdong: Great idea. I entered that phrase into Google Lucky and I reached the following site:

[http://www.linuxappeal.net](http://www.linuxappeal.net)

I've already sent the Macromedia Flash petition off. Let's hope they respond soon.

-- 
Bryce

---

### Post by paxmundi on 2005-05-11
Hi. I just opened a topic in the Flash General Discussion Forum area called 64 bit flash plugin for linux (because there is no easy way to petition Macromedia). Please do go there and add your two cents to that topic if you feel you want a plugin.

---

### Post by tvilliers on 2005-06-08
The URL:
[http://www.macromedia.com/cfusion/webforums/forum/messageview.cfm?catid=194&threadid=1001545](http://www.macromedia.com/cfusion/webforums/forum/messageview.cfm?catid=194&threadid=1001545)

---

### Post by davea0511 on 2005-06-23
If you want your feedback heard by macromedia personnel you'll have to post it here:

[http://www.macromedia.com/cfusion/mmform/index.cfm?name=wishform](http://www.macromedia.com/cfusion/mmform/index.cfm?name=wishform)

---

### Post by Wim Sjøholm on 2005-07-27
They *still* haven't included it??

---

