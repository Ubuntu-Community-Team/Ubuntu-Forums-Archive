---
title: "Wine: The following packages have unmet dependencies"
date: 2012-12-06
forum: Wine
---

### Post by mrc1503 on 2012-12-06
Hello,
     I am very new to ubuntu and Linux in general... I am an IT student and have only taken an introductory class on UNIX/Linux, but I really liked it so I decided to install it as my OS.  The problem is that I need to install wine (for using MS programs for school) and have run into problems doing installing via the terminal, I receive the following message:
                                  The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.18-0ubuntu1) but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: ttf-droid
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
   Any help would be appreciated.
Thanks,
Matt

---

### Post by verzx on 2012-12-06
Use the Update Manager and use the command below. :)

```
sudo apt-get install update
```

---

### Post by Tumshukuru H. Mhalila on 2012-12-06
first use the command below to update

```
sudo apt-get install update
```
then write: 
```
sudo apt-get install PlayOnLinux 
```
the command above is the best for MS program it will be installed with wine Enjoy!!:P

---

### Post by philinux on 2012-12-06
Moved to Wine forum.

The command above is wrong. It should be.

```
sudo apt-get update
```

---

### Post by mrc1503 on 2012-12-06
These are the commands, in order, that I used in the command line terminal.
 sudo add-apt-repository ppa:ubuntu-wine/ppa
 sudo apt-get update
 sudo apt-get install wine1.5


That's when I received the unmet dependencies error... I tried installing PlayOnLinux as suggested, this is the message I got: E: Unable to locate package PlayOnLinux. A little frustrating but I am enjoying the learning experience. I'll keep hammering away at it, but any more suggestions would be appreciated.
Thanks,
Matt

---

### Post by snowpine on 2012-12-06
Welcome to the forums!

Why don't you use the stable, trusted, and tested Wine 1.4 from the Ubuntu repositories? It can be installed with 1 mouse click in the Ubuntu Software Center and is guaranteed not to have unmet dependencies. :)

---

### Post by mrc1503 on 2012-12-06
I tried that and the software center gave me the following message: 
The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed
I'm sure I'm missing something really simple that would not be missed by a more experienced user.

---

### Post by snowpine on 2012-12-06
> **mrc1503 said:**
> I tried that and the software center gave me the following message: 
The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed
I'm sure I'm missing something really simple that would not be missed by a more experienced user.

Did you remember to remove the ubuntu-wine PPA that you added earlier from your your software sources?

---

### Post by mrc1503 on 2012-12-06
I removed everything that I had downloaded from the terminal and have searched for anything that I could think of. I still received the same error as before in the software center... Do I need to change any of the add ons below, or include some?

---

### Post by Tweak42 on 2012-12-06
I've lately seen a few users report unmet dependencies / broken packages problems trying to install wine.  I'm just speculating but there possibly could be a problem with 12.10 and mutiarch with respects to wine.

What version of Ubuntu are you using and what arch (i386 or amd64)?

If you don't mind the trouble reinstalling, try out 12.04 LTS (i386) release to see if wine installs correctly.  Personally I haven't upgraded to 12.10 since the clean test installs using release images locked up at boot or during setup.

---

### Post by mrc1503 on 2012-12-06
I'm using a12.10 amd64... that may be the case as you suggested.  I have dual boot on the computer, but I wanted a way to be free from the Windows OS and use wine for the classes that I absolutely needed to use a MS program.  I suppose I may have to wait until a patch comes through for 12.10...

---

### Post by mrc1503 on 2012-12-07
I downloaded all of the missing packages, but a error code still came up regarding the version of ubuntu I am using the error is:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not installable

I am assuming wine doesn't yet support ubuntu 12.10...
I installed virtualbox instead, does anyone have any good links or instructions for installing windows 7 through virtualbox?

---

### Post by Tweak42 on 2012-12-08
> **mrc1503 said:**
> I downloaded all of the missing packages, but a error code still came up regarding the version of ubuntu I am using the error is:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not installable

I am assuming wine doesn't yet support ubuntu 12.10...
I installed virtualbox instead, does anyone have any good links or instructions for installing windows 7 through virtualbox?

Wine should work in ubuntu 12.10, it just sounds like there are issues with the 64 bit side for some reason.

Vbox has an easy step-by-step install creation wizard and Win7 is on the list.  Hit up google and youtube there are plenty of windows 7 in virtualbox guides out there.  Don't forget to install the vbox guest additions after you get installed or you'll be missing some features.

---

### Post by Akshata172003 on 2012-12-09
I have the same issue as [mrc1503]("http://ubuntuforums.org/member.php?u=1763105") .  hope to find a solution

---

### Post by orb9220 on 2012-12-10
Yep same here 64bit and No Wine So thought to Whine Here :-) !
Hope for a fix soon.
.

---

### Post by diehardhoosier84 on 2012-12-10
So after days of head banging code and fixes I finally came to the conclusion that its 12.10. I /unistalled 12.10, installed 12.04.1 LTS. Everything was smooth. Ran my 

```
sudo apt-get update
```and everything checked out ok. I should also point out (because i saw some people say they did NOT have an option to choose x64 or x32 OS versions) i am running x64. Wubi will give you the choice from the WEBSITE pre install. Now, after running updates, I downloaded and updated all Drivers. So from this point I have a fresh 12.04.1 LTS x64 install with all updates and drivers. The exact same place i was when i could not get wine to install last time. I then 

```
 sudo apt-get install wine
```and Boom. Good 2 go. Not sure if 12.10 is just still new and wine hasnt updated but it works perfect on my machine now. I'm even able to run World of Warcraft from my Win7 folder directly using these steps:

```

For the purpose you want, you actually do not  need to copy the files over. you can run WOW from within the windows  partition. What you really have to do is the following to have  everything working as it should:
  
[LIST=1]
[*]Install the PPA for WINE. You HAVE TO install the PPA which is much better. More info here: [How to update Wine to the latest version?]("http://askubuntu.com/questions/100947/how-to-update-wine-to-the-latest-version")
[*]Install using winetricks (After having installed Wine) all  DirectX 9 components. Since the release of Wine 1.4, you can just  install the DirectX that comes with any Windows CD/DVD (eg: The DirectX  10 that comes with Skyrim). That should be enough to get DirectX  working.
[*]Install the latest drivers for Intel, Nvidia or Ati. All of which you can find/install with this PPA: [How do I install the latest Nvidia drivers via the Additional Drivers tool?]("http://askubuntu.com/questions/104527/how-do-i-install-the-latest-nvidia-drivers-via-the-additional-drivers-tool")
[*]Follow this link with any additional relevant information about WoW: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=25610](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25610)
[*]Create a desktop shortcut/launcher as mentioned in this question to have a working one click icon: [How can I edit/create new launcher items in Unity by hand?]("http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand/128284#128284") (Easy way here: [http://askubuntu.com/a/128284/7035](http://askubuntu.com/a/128284/7035) )
[*]Edit the Desktop shortcut and in the command line type: wine "DIR" -opengl where DIR is the complete location of your Wow.exe file. For example in my case wine "/media/fun/games/World of Warcraft/Wow.exe" -opengl".  The OpenGL is to give you more available graphics options. You can also  remove it but for most video cards it is better to have it there to  make the game run smoother.
[/LIST]
  If you still want to copy the Wow folder, you can put it on your  Ubuntu home folder and do the same steps mentioned before. Just wanted  to point out that you can run the game from the same Windows partition,  does saving you space and time.
 
```
found here [http://askubuntu.com/questions/139331/how-do-i-copy-program-files-from-windows-partition-to-my-ubuntu-partition](http://askubuntu.com/questions/139331/how-do-i-copy-program-files-from-windows-partition-to-my-ubuntu-partition)




Wow runs better now than it did in my Win7 partition with Wine and its literally a click away. Easy enough.



Sorry if this is crazy to keep up with, Im in a hurry to leave work but wanted to share this in hopes it would help someone as well. Ill check back in a little while to fix errors/spelling ect.  If you have a question on my process feel free to PM me.

---

### Post by BrianL on 2012-12-13
Yes, I have the same problem as the OP. Same operating system. Same Wubi install.
Same errors. 

Any other suggestions besides what the last posts suggests?

First ever foray into Linux. Really like it and have been tweaking for a few days to
get it where I liked it more. Wanted to use Wine to run Photoshop and starting getting
all the unmet dependencies.Will keep googling for a fix. Any help appreciated. Just remember I'm really green at this, but learning.

---

### Post by dino99 on 2012-12-13
To those still using wine1.4, you'd better to try the latest 1.5.19 (the "unstable" version works better than the "stable" with recent hardware/games/... and think to glance at :

- winehq site to know how to get it
- winetricks site for additional needs (first find your app feedback into the winehq/appbase)

[http://wiki.winehq.org/FrontPage](http://wiki.winehq.org/FrontPage)

---

### Post by BrianL on 2012-12-13
Ok, have found a solution that worked for me. I have a wubi install of ubunti 12.10 on windows 7 pro 64bit. After following the advise in this link, wine 1.5 installed.

[http://ubuntuforums.org/showthread.php?p=12402510#post12402510](http://ubuntuforums.org/showthread.php?p=12402510#post12402510)

and I'm so new to linux I didn't know how to navigate and accept the graphical
user interface inside a terminal window that you get when you try to install so
I'll add a link to that too incase anyone is as green as me to linux.;)

[http://askubuntu.com/questions/16225/how-can-i-accept-microsoft-eula-agreement-for-ttf-mscorefonts-installer](http://askubuntu.com/questions/16225/how-can-i-accept-microsoft-eula-agreement-for-ttf-mscorefonts-installer)

---

