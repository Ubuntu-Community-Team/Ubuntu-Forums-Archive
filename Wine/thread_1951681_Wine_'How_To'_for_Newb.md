---
title: "Wine 'How To' for Newb"
date: 2012-04-02
forum: Wine
---

### Post by Curtis6767 on 2012-04-02
I'm running 12.04 LTS Beta 2 inside the Wubi

I have not downloaded Wine, nor can I find it on my computer. But I do plan to, probably after the final 12.04 release.

I have been to Winehq, read just about everything there, then went to the Wine Wiki and read just about everything there. And yet, I cannot find a detailed How To for wine.

Maybe I just missed it. Maybe it's all there, but I didn't find it.

If you can point me to a site that just has a simple Wine 'How to', please do.

What I'd like to know seems to me to be very basic yet somehow overlooked at Winehq or the Wiki.

First, I'd just like to know how to actually down load Wine. It is in the software center, but there is apparently some confusion about how to actually download it. To use the PPA, or not. And also some confusion about which version. There is a Wine 1.5, but it is not yet in the software center.

Okay, so I download it. Where is it? Is it in 'usr' ? How do I execute it? Then what? If I want to use it, how do I load it? If I put a Windows based CD in my CD drive, does Wine detect this and open and start installing the Windows program?

If I have to do something with config, then why isn't that mentioned anywhere at Winehq or their wiki?

Thanks

---

### Post by kalkems on 2012-04-03
Hi!
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

This explains using a ppa even though it's a bit out of date. The ppa of course will always give you the latest wine version which might be bad in some production situations.
I have never experienced a cd auto starting a win install through wine. I have always right clicked in nautalis and pointed the exe file to wine install.
As for a wiki. I have always searched the net for answers.
/ernie

---

### Post by forrestcupp on 2012-04-03
> **Curtis6767 said:**
> 
Okay, so I download it. Where is it? Is it in 'usr' ? How do I execute it? Then what? If I want to use it, how do I load it? If I put a Windows based CD in my CD drive, does Wine detect this and open and start installing the Windows program?

If I have to do something with config, then why isn't that mentioned anywhere at Winehq or their wiki?

Thanks

Wine doesn't make your computer run like Windows and automatically run autodetected CDs. With Wine, you can run some Windows exe files, but not every Windows program out there will run.

I wouldn't bother with the PPA. 12.04 comes with the latest stable release that just came out. 1.5 is a brand new beta, and if you already have 1.4 installed, it's probably not worth it.

To install something with Wine, you need to open up the file browser, Nautilus, and find the setup file. When you find setup.exe or whatever it is, right-click on it and choose Properties. In the "Open With" tab, find and choose "Wine Windows Program Loader". After you do that, any exe file will automatically be opened with Wine. If it still doesn't open, you'll need to go to the "Permissions" tab in the file's Properties and check the box that says "Allow executing file as a program". You'll never have to set the "Open With" property again, but you might need to set the execute property with other files.

After you install something with Wine, it should show up in a dash search. Sometimes if you aren't able to install something from a CD, it will work if you copy the entire contents of the CD to your hard drive and run it from there.

Like I said, not every Windows program works well with Wine. Go over to WineHQ and search their app database for the program you want to run. If the program is in the list, it will give you a rating for how well it works, and also people's experiences with workarounds to get things to work.

Also, you might want to look through the [Before asking for help](http://ubuntuforums.org/showthread.php?t=885111) sticky in this sub forum.

---

### Post by lovinglinux on 2012-04-03
Keep in mind you can install Wine and most software you will ever need using the one click install of the Software Center. That is the first thing to try.

You just use a PPA when you cannot find the software in the Software Center or if you need a version that is not available in the repositories.

In addition to forrestcupp's comments, I would recommend using PlayOnLinux. You can find it in the Software Center as well. This tools makes easier to install and configure applications using Wine.

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by Curtis6767 on 2012-04-03
> **kalkems said:**
> Hi!
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

This explains using a ppa even though it's a bit out of date. The ppa of course will always give you the latest wine version which might be bad in some production situations.
I have never experienced a cd auto starting a win install through wine. I have always right clicked in nautalis and pointed the exe file to wine install.
As for a wiki. I have always searched the net for answers.
/ernie

Thanks, I've looked at that and I'm not sure I need to add the PPA since Wine is available through the Software Center.

> **forrestcupp said:**
> Wine doesn't make your computer run like  Windows and automatically run autodetected CDs. With Wine, you can run  some Windows exe files, but not every Windows program out there will  run.

I wouldn't bother with the PPA. 12.04 comes with the latest stable  release that just came out. 1.5 is a brand new beta, and if you already  have 1.4 installed, it's probably not worth it.

To install something with Wine, you need to open up the file browser,  Nautilus, and find the setup file. When you find setup.exe or whatever  it is, right-click on it and choose Properties. In the "Open With" tab,  find and choose "Wine Windows Program Loader". After you do that, any  exe file will automatically be opened with Wine. If it still doesn't  open, you'll need to go to the "Permissions" tab in the file's  Properties and check the box that says "Allow executing file as a  program". You'll never have to set the "Open With" property again, but  you might need to set the execute property with other files.

After you install something with Wine, it should show up in a dash  search. Sometimes if you aren't able to install something from a CD, it  will work if you copy the entire contents of the CD to your hard drive  and run it from there.

Like I said, not every Windows program works well with Wine. Go over to  WineHQ and search their app database for the program you want to run. If  the program is in the list, it will give you a rating for how well it  works, and also people's experiences with workarounds to get things to  work.

Also, you might want to look through the [Before asking for help]("http://ubuntuforums.org/showthread.php?t=885111") sticky in this sub forum.

Thanks for this information. And I did read the "Before asking for help" sticky.  But I'm a newb and I can't find Applications-> Add/Remove. I assume that I would go into the Update Manager, Settings, then Other Software. At that point I have two options at the bottom of the window, those being Add, which then wants the repository information, or Add Volume, which then asks to change the repository information.


BTW, I have searched for Wine on my system and if it is loaded by default, I can't find it. If I go to Dash and search for Wine there, when I go to Wine it does not show that it is installed. I've gone into 'usr' but do not see Wine in that file, either.

Thanks

---

### Post by forrestcupp on 2012-04-03
> **lovinglinux said:**
> 
In addition to forrestcupp's comments, I would recommend using PlayOnLinux. You can find it in the Software Center as well. This tools makes easier to install and configure applications using Wine.

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)I actually don't recommend that if you can easily install something from Wine. PlayOnLinux makes things very easy to install, but it makes it a pain to deal with after you install them. For instance, installing Microsoft Office with Wine automatically creates a .desktop file so it can be searched for in Dash and show up in menus. It also makes it very easy to associate files with Word, Excel, etc. But if you install it with PlayOnLinux, you have to manually perform a bunch of dirty hacks to get those things to work. PlayOnLinux is great if you're having trouble with Wine, but going pure Wine is preferred if you can do it.

> **Curtis6767 said:**
> Thanks, I've looked at that and I'm not sure I need to add the PPA since Wine is available through the Software Center.



Thanks for this information. And I did read the "Before asking for help" sticky.  But I'm a newb and I can't find Applications-> Add/Remove. I assume that I would go into the Update Manager, Settings, then Other Software. At that point I have two options at the bottom of the window, those being Add, which then wants the repository information, or Add Volume, which then asks to change the repository information.
That's because that sticky is very old and it desperately needs to be updated. It's no longer called "Add/Remove". Now you need to be looking for the Software Center to install apps. Alternatively, to install Wine, you could open a terminal and type:
```
sudo apt-get install wine
```
Just note that Wine is not a graphical application. Winecfg is graphical, but Wine itself is not. You just have to either run the commands from the terminal, or associate .exe files with Wine, like I mentioned earlier, and double click the .exe file to run it with Wine.

---

### Post by lovinglinux on 2012-04-03
> **forrestcupp said:**
> I actually don't recommend that if you can easily install something from Wine. PlayOnLinux makes things very easy to install, but it makes it a pain to deal with after you install them. For instance, installing Microsoft Office with Wine automatically creates a .desktop file so it can be searched for in Dash and show up in menus. It also makes it very easy to associate files with Word, Excel, etc. But if you install it with PlayOnLinux, you have to manually perform a bunch of dirty hacks to get those things to work. PlayOnLinux is great if you're having trouble with Wine, but going pure Wine is preferred if you can do it.

Oh, I see. I never experienced that, because I only use PlayOnLinux to install a couple of games and portable executables. I never tried to install a complex application like Microsoft Office. Thanks for the warning.

What I like about PlayOnLinux is that I can easily create different Wine prefixes, now called "virtual drives", and also use different versions of Wine.

---

### Post by Curtis6767 on 2012-04-03
Went back over to psycho cats, and re-read their[ Wine tutorial]("http://www.psychocats.net/ubuntu/wine"), which is now starting to make sense. 

There are also a couple of videos out there that run through the install process for both Wine and a Windows .exe. They're for older versions of Ubuntu but this does give some idea of how the process works.

---

### Post by forrestcupp on 2012-04-04
> **lovinglinux said:**
> 
What I like about PlayOnLinux is that I can easily create different Wine prefixes, now called "virtual drives", and also use different versions of Wine.

It really is good for that. Another thing I like about PlayOnLinux is that it can download and manage a lot of different versions of Wine for those apps that don't work well with newer versions. If they would just work out the issues with creating .desktop files and file association, it would definitely be the best way.

---

### Post by Curtis6767 on 2012-04-04
Just thought I'd list some of the sites I've visited where I've been gathering information about Wine:

Wine Reviews:[ A guide to Wine on Ubuntu for Beginners]("http://www.wine-reviews.net/wine-reviews/tips-n-tricks/a-guide-to-wine-on-ubuntu-for-beginners.html")

Addictive Tips: [Install and Use Wine in Ubuntu Linux]("http://www.addictivetips.com/ubuntu-linux-tips/install-and-use-wine-in-ubuntu-linux/")

PsychoCats: [Using Wine on Ubuntu]("http://psychocats.net/ubuntu/wine")

Youtube: [How to Install Wine in Ubuntu 11.04]("https://www.youtube.com/watch?v=aSQt9qXduqU&feature=related")

Youtube: [How to Install Windows Emulator (Wine) on Ubuntu]("https://www.youtube.com/watch?v=6CnoBTXBTqo")

Youtube:[ Run Windows Applications on Ubuntu using Wine]("https://www.youtube.com/watch?v=RLRLWEfdFqY")

Youtube: [How to Install a Program in Wine]("https://www.youtube.com/watch?v=HFSA-UyyZnM&feature=related")

Youtube: [Install .exe on Ubuntu]("https://www.youtube.com/watch?v=KUo5StZDtUE&feature=related")

That  should do it for now. I'm sure I'll have to go through this stuff at  least once more, but I at least have an idea about the installation and  use of Wine.

---

