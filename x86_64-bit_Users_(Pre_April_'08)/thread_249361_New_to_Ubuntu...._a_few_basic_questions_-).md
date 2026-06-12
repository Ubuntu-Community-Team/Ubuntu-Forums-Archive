---
title: "New to Ubuntu.... a few basic questions :-)"
date: 2006-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by banko on 2006-09-02
Hello All,

This was my first install of Ubuntu, and as such I have a few questions; However, first I would like to make some comments to the developers...

   !!! Simply Amazing !!!

I purchased this HP Pavilion dv8000 one month ago, and have tried far far too many distributions with it.  90% of them couldn't even get the thing to boot.  The ones that could messed up on almost every driver configuration you could imagine.  Ubuntu simply works!

I popped in the CD booted up and clicked the install icon that was placed on the Desktop, and I shit you not 12 minutes later I was ready to boot into my new system.  

Unfortunately there were two minor problems. 

Ubuntu did not ask me for my Network Information during the installation, and as a result I received one error that it could not retreive the updates.  However that was a quick change, then I uncommented some lines in the /etc/apt/sources.list then did an apt-get update and voila everything was "working".

I used quotes because for some reason i was getting a warning in the taskbar about my wireless card not working, but this was a lie it works perfectly, so I just removed the item from the task bar.

Later I did a reinstall for fun, this time i setup the Network before running the install and the first problem of course never occured, and ran perfectly.  That stupid warning was still there.

Anyway long and short of it, Ubuntu simply worked where no one else did, and all of you developers deserve a serious pat on the back. I do however, recommend including a network setup in the installation.

Now back to me :mrgreen: 

I now have a bare system (this in itself is awesome, since most distro's can't even give you that anymore!), and I need to setup a development enviroment for this laptop.  For the next year I will be learning assembly, linux, and perl, and hopefully be going through piles of Linux source code for the purposes of completely learning the ins and outs of the linux system.

This leads me to my first question.... What is a good programming suit (set of tools) for developing using these three languages.  

Secondly, and I'm sure you receive this question lots considering how many people are making the switch from windows to linux.  How do i install the codecs and players needed to watch my DVD's and other movie and music files.  I followed a few posts online, but there seems to be a problem since I run on a 64 bit system.

From what I have seen so far, to install programs in Ubuntu, all I really need to do is type sudo apt-get install [package], and I can add sources to the sources.list file if needed.  Am I missing anything here? I would like to review a manual, if one exists.  Please indicate if it does and where.

I would also like to get pointed towards any documentation, you guys feel important for new linux users.  That said I already have a couple books on bash.  And lastly, is there any so called Ubuntu Groups or Communities for beginners, and people that would like to contribute in the near future?  I did take some programming classes a few years ago, and I develop websites for a living, and would like very much to get involved, I just need to get a grasp on Linux first.


Thanks in advance,

Banko

---

### Post by Kilz on 2006-09-02
> **banko said:**
> Hello All,

This was my first install of Ubuntu, and as such I have a few questions; However, first I would like to make some comments to the developers...

   !!! Simply Amazing !!!

I purchased this HP Pavilion dv8000 one month ago, and have tried far far too many distributions with it.  90% of them couldn't even get the thing to boot.  The ones that could messed up on almost every driver configuration you could imagine.  Ubuntu simply works!

I popped in the CD booted up and clicked the install icon that was placed on the Desktop, and I shit you not 12 minutes later I was ready to boot into my new system.  

Unfortunately there were two minor problems. 

Ubuntu did not ask me for my Network Information during the installation, and as a result I received one error that it could not retreive the updates.  However that was a quick change, then I uncommented some lines in the /etc/apt/sources.list then did an apt-get update and voila everything was "working".

I used quotes because for some reason i was getting a warning in the taskbar about my wireless card not working, but this was a lie it works perfectly, so I just removed the item from the task bar.

Later I did a reinstall for fun, this time i setup the Network before running the install and the first problem of course never occured, and ran perfectly.  That stupid warning was still there.

Anyway long and short of it, Ubuntu simply worked where no one else did, and all of you developers deserve a serious pat on the back. I do however, recommend including a network setup in the installation.

Now back to me :mrgreen: 

I now have a bare system (this in itself is awesome, since most distro's can't even give you that anymore!), and I need to setup a development enviroment for this laptop.  For the next year I will be learning assembly, linux, and perl, and hopefully be going through piles of Linux source code for the purposes of completely learning the ins and outs of the linux system.

This leads me to my first question.... What is a good programming suit (set of tools) for developing using these three languages.  

Secondly, and I'm sure you receive this question lots considering how many people are making the switch from windows to linux.  How do i install the codecs and players needed to watch my DVD's and other movie and music files.  I followed a few posts online, but there seems to be a problem since I run on a 64 bit system.

From what I have seen so far, to install programs in Ubuntu, all I really need to do is type sudo apt-get install [package], and I can add sources to the sources.list file if needed.  Am I missing anything here? I would like to review a manual, if one exists.  Please indicate if it does and where.

I would also like to get pointed towards any documentation, you guys feel important for new linux users.  That said I already have a couple books on bash.  And lastly, is there any so called Ubuntu Groups or Communities for beginners, and people that would like to contribute in the near future?  I did take some programming classes a few years ago, and I develop websites for a living, and would like very much to get involved, I just need to get a grasp on Linux first.


Thanks in advance,

Banko


For the dvd's
```
sudo apt-get install libdvdread3 debhelper build-essential fakeroot totem-xine
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

---

### Post by Das Goat on 2006-09-02
Hi! I'm trilled that i could find some one using this model laptop with Ubuntu. I hope you have a few answers for me. I down loaded the ISO and burned it, and when I check it in windows it seems ok, but I can not boot from the CD. It wants to work, but when it it gets to a section just after loading something called "3674" I get a message that Int 1 through 6 could not load, waiting 5 minutes. After 5 minutes, it tries again, but stil can not do it, no mater how long i wait. Any ideas? I really want to start using Ubuntu.

---

### Post by banko on 2006-09-03
GasGoat - 

Do to my large amounts of experimenting with programs and following instructions from other forums, I ended up reinstalling Ubuntu about 7 times yesterday. This was not "needed" of course, but i find a 12 minute install a hell of a lot easier then 30 minute clean up trying to fix all the bad advice :mad: 

Three times I encountered the same error that you received, however all three times I just rebooted with "control alt delete" and the second time it would boot up properly, and perform the install.

I will however give you a few things to think about before you go through with the install of the 64 bit version.

1.  I have yet to find anyone who can fix the network warning for the wireless card.  Strange thing is if you install the 32 bit version everything runs smooth as pie for the wireless program.  This is a rather small issue as the connection does work, its just a little slow, do to the constant warning and rechecking of the app.

2.  Codecs Codecs Codecs using the 64 bit version, pretty much forces you into creating a 32 bit chroot environment, for firefox, realplayer, w32codecs, the list just goes on.  The biggest and obvious is FLASH, it is simply impossible to get FLASH working on a 64bit firefox.

However I will note that i have seen many persons caim that the VLC Player will player EVERYTHING under the sun in the 64bit version INCLUDING FLASH!!!  I performed the install, and it has yet to play anything for me.  Which is rather strange as I used this program on windows and the aclaims are quite true that there was nothing this thing wouldn't play (other than real player)  I never had to worry about codecs or right issues, it simply worked.  There for I am going to look further into this.  I'm pretty sure it just doesnt like the preinstalled players that came with Ubuntu, and as soon as i figure out how to install a completely bare Ubuntu system without any of the apps I expect this to solve 99% of my problems.

A side note i did get the regular movie player playing DVD's.  If you plan on using the getting started guide for Ubuntu, expect 25% of the stuff to simply not work, as the downloads simply don't exist for our version, dispite the instructions to download them, and yes i enabled the galaxy and other repositories.

My last install that I purformed yesterday was the 32bit version and it solved every issue i had.  I just followed the community documentation (stay clear of easyUbuntu and automatrix for this laptop), this is truely 64 bit issue.

Other happy news: "imwheel" absolute greatest package ever made for mouses!!!  Why do i say that? I have a Logitech MX Laser mouse (bluetooth) that has 7 buttons, plus verticle scrolls, plus horizontal scrolls.  This application allows me full control over my mouse buttons, click accuracy, speed, and combo short-cuts (pressing two buttons at same time)

My only problem is I am way to stubborn.  I have absolutely everything running perfectly the way i wanted, and i am about to get rid of it all and try the 64bit version again.  I refuse to use a 32bit chroot so I wont be able to have flash, but all other video and music issues i expect to be solved by using the VLC as my default player.

I will keep you updated as to the results.  The good news is i talk way too much so you will get a step by step procedure for anything you need help with that i accomplish.  If you by chance find a program that will allow us to use the remote control that comes with our laptop let me know.

This question is for everyone! How do i perform a fresh installation of the 64bit version, and have it not install any of the games or Sound and video programs?

For some reason i can not just perform a regular install and then do a sudo apt-get remove on the movie or cd player

---

### Post by Kilz on 2006-09-03
> **banko said:**
> 
2.  Codecs Codecs Codecs using the 64 bit version, pretty much forces you into creating a 32 bit chroot environment, for firefox, realplayer, w32codecs, the list just goes on.  The biggest and obvious is FLASH, it is simply impossible to get FLASH working on a 64bit firefox.


You must have missed the link in my signature and the link in the work around sticky to my Firefox howto/script. My advice is checking that sticky if you are having application issues.

---

### Post by banko on 2006-09-12
GAS GOAT,

The problem (alleast for me) is, for some reason if i pop the install CD in and reboot the computer i get the same error and the CD fails to boot the laptop.  However if you perform a full shutdown then boot with the CD all is well.

I have no clue as to why that would effect it, but on my system that is definately the case.

Please let me know if this helped.

---

