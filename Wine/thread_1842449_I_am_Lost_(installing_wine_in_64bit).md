---
title: "I am Lost (installing wine in 64bit)"
date: 2011-09-11
forum: Wine
---

### Post by Imrans23 on 2011-09-11
Hey guys, I just installed Linux 11.04 64bit in my computer and I'm completely lost :P
I want to get Wine1.3 and I tried just about everything.
By everything i mean I went into software sources, added the ppa that the wine website had told me to add. I updated and then I used the code to install wine. And then I got the following message
> 
The following packages have unmet dependencies:
 wine1.3 : Depends: ia32-libs (>= 1.6) but it is not going to be installed
           Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
           Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed
           Depends: lib32nss-mdns (>= 0.10-3) but it is not going to be installe
And then I thought that it might have something to do with me using a 64bit or something (I'm not really good with computers :P) So I downloaded what is supposedly the ia32libs from here
[https://launchpad.net/ubuntu/natty/+source/ia32-libs](https://launchpad.net/ubuntu/natty/+source/ia32-libs)
I downloaded the one which is 841 MB. So then I extracted it, and it extracted to my homefolder and there is still no difference...

---

### Post by Lighthorse01 on 2011-09-11
Go to the Software Center and type wine in the search bar
select Microsoft Windows Compatibility Layer (meta package)
install that. it will install what you need.

---

### Post by Imrans23 on 2011-09-12
I searched in the software center but I only found 
"Wine Windows Compatibility layer" for wine 1.2 
"Wine Windows Compatibility layer (Beta Release)" for wine 1.3
And Trying to install them I got the same error
> 
The following packages have unmet dependencies:

wine1.3: PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.16.0~ubuntu7 is to be installed
         Depends: ia32-libs (>= 1.6) but 20090808ubuntu9 is to be installed
         Depends: libc6-i386 (>= 2.6-1) but 2.12.1-0ubuntu16 is to be installed

Is this problem arising because I don't have the ia32-libs? If so, is there a tutorial as to how I do it?

---

### Post by uRock on 2011-09-12
Moved to *Wine* sub-forum.

---

### Post by jacksaff on 2011-09-13
Try installing the other packages first - eg. sudo apt-get install ia32-libs
and so on. apt should give you some feedback if they won't install. 

If you get those packages installed and wine still  won't install, it might be because of the ubuntu numbering system (see the different numbers for ia32-libs for example). In that case the dependencies are already installed and you might have some luck forcing the apt-get install with tthe 'fix' option: apt-get -f install wine

---

### Post by Imrans23 on 2011-09-13
Hmm.
Ok, so here is what I did 
"sudo apt-get install ia32-libs"
result:
> 
The following packages have unmet dependencies:
 ia32-libs : Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32asound2 but it is not going to be installed
             Depends: lib32bz2-1.0 but it is not going to be installed
             Depends: lib32ncurses5 but it is not going to be installed
             Depends: lib32v4l-0 but it is not going to be installed
             PreDepends: libc6-i386 (>= 2.9-18) but it is not going to be installed

And when I attempted to download these dependencies, all I got was
"E: Unable to load package"

So, I tried the other dependencies
"sudo apt-get install lib32asound2"
Result
> 
lib32asound2 : Depends: libasound2 (= 1.0.23-2.1ubuntu2)
                Depends: libc6-i386 (>= 2.9-18) but it is not going to be installed

And also,
"sudo apt-get install libc6-i386"
result
> 
libc6-i386 : Depends: libc6 (= 2.12.1-0ubuntu16) but 2.13-0ubuntu13 is to be installed
E: Broken packages


---

### Post by cwwilson721 on 2011-09-13
Since you added the wine ppa, it's EASY

To make sure you don't have issues, do this:
[LIST]
[*]In terminal, enter sudo apt-get update
[*]Enter sudo apt-get upgrade (These 2 commands get everything up to speed)
[*]Enter sudo apt-get install wine (This installs wine 1.2 and it's dependencies, just in case)
[*]Enter sudo apt-get install wine1.3 (Installs wine 1.3)
[*]Enter winecfg (This sets up your '.wine' folder and other stuff...)
[/LIST]
I added the regular wine install just to be sure there is no boo-boo for ia32libs, just in case.

Good luck

---

### Post by Imrans23 on 2011-09-13
Still not working.. :S I did both the upgrade and the update. They were both successful, but neither 1.2 or 1.3 would install. Just to be sure that we're on the same page, I added this into my software sources
ppa:ubuntu-wine/ppa

---

### Post by dino99 on 2011-09-13
what are you doing ? (I downloaded the one which is 841 MB. ) ;)

all you need is to run synaptic (because ubuntu is for humans :))

sudo synaptic

then select ia32libs to remove/purge (right click), and select wine1.3 to install

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by Imrans23 on 2011-09-16
Hmm, the instructions in the above post didn't work either, when I tried ticking ia32libs, it would just say that I have unmet dependencies and would cancel out on me.. Anyway, I did finally find a way to install it.
I just followed this link : [http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)
Anyway, now I'm stuck once again :P
If I try to install a 64bit application, it will tell me that it is not supported in the wine prefix.  The following is an example of what happened when I tried to install iTunes 64bit
> 
imran@imran-desktop:~$ cd ~/Desktop/
imran@imran-desktop:~/Desktop$ wine "iTunes64Setup.exe"
err:process:create_process starting 64-bit process L"Z:\\home\\imran\\Desktop\\iTunes64Setup.exe" not supported in 32-bit wineprefix
wine: Bad EXE format for Z:\home\imran\Desktop\iTunes64Setup.exe

Later on I found this website, [http://wiki.winehq.org/Wine64](http://wiki.winehq.org/Wine64)
I am not exactly sure what's written in this page...
Firstly, how do I run a shell script?
Secondly, how do I configure something?

---

