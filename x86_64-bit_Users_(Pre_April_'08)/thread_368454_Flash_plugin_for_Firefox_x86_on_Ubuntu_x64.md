---
title: "Flash plugin for Firefox x86 on Ubuntu x64"
date: 2007-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by M$LOL on 2007-02-23
I downloaded the firefox32 deb for Ubuntu 64 and installed it, after running the install script, and it works perfectly, apart from whenever I try to install the Adobe Flash Player plugin it says 'Installation failed' and gives me the manual installation option. I don't mind installing it manually, but shouldn't it work automatically?

---

### Post by Kilz on 2007-02-23
> **M$LOL said:**
> I downloaded the firefox32 deb for Ubuntu 64 and installed it, after running the install script, and it works perfectly, apart from whenever I try to install the Adobe Flash Player plugin it says 'Installation failed' and gives me the manual installation option. I don't mind installing it manually, but shouldn't it work automatically?

Did you get the deb file from my howto?

---

### Post by M$LOL on 2007-02-23
Yes, and as you said, I ran the install script first.

---

### Post by Kilz on 2007-02-23
> **M$LOL said:**
> Yes, and as you said, I ran the install script first.

Thats because the script is real old. I havent updated it in months as everyone was installing Edgy and the script was originally written for Dapper. The script tried to install Flash 7, wich is no longer avilable.

I have updated the script to instal Flash 9. [Here is a link to the Updated script.]("http://home.comcast.net/~next/base-plugins-browsers-0-7.tar.gz")

---

### Post by M$LOL on 2007-02-23
Thanks. Should I uninstall the original install script first, and if so, how?

---

### Post by Kilz on 2007-02-23
> **M$LOL said:**
> Thanks. Should I uninstall the original install script first, and if so, how?

No need to, it should rewrite over what needs to be changed.

---

### Post by M$LOL on 2007-02-26
OK, when I open Firefox and go to Youtube.com, it says that the plugin needs to be installed. I try to install it and it says "Installation Failed". Isn't the script supposed to install it for me?

---

### Post by Kilz on 2007-02-26
> **M$LOL said:**
> OK, when I open Firefox and go to Youtube.com, it says that the plugin needs to be installed. I try to install it and it says "Installation Failed". Isn't the script supposed to install it for me?

Yes, and it installs a 32bit browser. Are you sure you are running the 32bit browser (also make sure there is no 64bit browser open when you start it)? if you are running firefox32, open a terminal and run this command

```
ls -al /usr/lib32/firefox32/plugins
```

Then paste the results in a post here

---

### Post by M$LOL on 2007-02-27
Well, I used the Firefox32 link in Applications -> Internet. There's also a link that says 'Firefox'. I previously installed McAfee SiteAdvisor and Adblock Plus on the x64 firefox, and they show up in the Firefox I'm running now (what I think is the 32 bit one). Here's the output you asked for:
```

total 1368
drwxr-xr-x 2 ciaran ciaran   4096 2007-02-23 21:58 .
drwxr-xr-x 4 ciaran ciaran   4096 2007-02-22 16:01 ..
lrwxrwxrwx 1 root   root       62 2007-02-22 16:15 libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so
-rw-r--r-- 1 ciaran ciaran  92448 2006-09-19 14:39 libnpp.so
-rwxr-xr-x 1 ciaran ciaran  19496 2006-09-10 03:41 libnullplugin.so
-rw-r--r-- 1 root   root   244412 2007-02-23 22:03 mplayerplug-in-gmp.so
-rw-r--r-- 1 root   root      981 2007-02-23 22:03 mplayerplug-in-gmp.xpt
-rw-r--r-- 1 root   root   244540 2007-02-23 22:03 mplayerplug-in-qt.so
-rw-r--r-- 1 root   root      981 2007-02-23 22:03 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root   root   244572 2007-02-23 22:03 mplayerplug-in-rm.so
-rw-r--r-- 1 root   root      981 2007-02-23 22:03 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root   root   245660 2007-02-23 22:03 mplayerplug-in.so
-rw-r--r-- 1 root   root   244860 2007-02-23 22:03 mplayerplug-in-wmp.so
-rw-r--r-- 1 root   root      981 2007-02-23 22:03 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root   root      981 2007-02-23 22:03 mplayerplug-in.xpt

```
Thanks for your help :)

---

### Post by Kilz on 2007-02-27
> **M$LOL said:**
> Well, I used the Firefox32 link in Applications -> Internet. There's also a link that says 'Firefox'. I previously installed McAfee SiteAdvisor and Adblock Plus on the x64 firefox, and they show up in the Firefox I'm running now (what I think is the 32 bit one). Here's the output you asked for:
```

total 1368
drwxr-xr-x 2 ciaran ciaran   4096 2007-02-23 21:58 .
drwxr-xr-x 4 ciaran ciaran   4096 2007-02-22 16:01 ..
lrwxrwxrwx 1 root   root       62 2007-02-22 16:15 libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so
-rw-r--r-- 1 ciaran ciaran  92448 2006-09-19 14:39 libnpp.so
-rwxr-xr-x 1 ciaran ciaran  19496 2006-09-10 03:41 libnullplugin.so
-rw-r--r-- 1 root   root   244412 2007-02-23 22:03 mplayerplug-in-gmp.so
-rw-r--r-- 1 root   root      981 2007-02-23 22:03 mplayerplug-in-gmp.xpt
-rw-r--r-- 1 root   root   244540 2007-02-23 22:03 mplayerplug-in-qt.so
-rw-r--r-- 1 root   root      981 2007-02-23 22:03 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root   root   244572 2007-02-23 22:03 mplayerplug-in-rm.so
-rw-r--r-- 1 root   root      981 2007-02-23 22:03 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root   root   245660 2007-02-23 22:03 mplayerplug-in.so
-rw-r--r-- 1 root   root   244860 2007-02-23 22:03 mplayerplug-in-wmp.so
-rw-r--r-- 1 root   root      981 2007-02-23 22:03 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root   root      981 2007-02-23 22:03 mplayerplug-in.xpt

```
Thanks for your help :)

For some reason the flash plugin didnt install. [You can simply download the plugin]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") Then use these commands.
```
cd ~/Desktop
tar -xzvf install_flash_player_9_linux.tar.gz
sudo mv -f ~/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib32/firefox32/plugins
sudo mv -f ~/Desktop/install_flash_player_9_linux/flashplayer.xpt /usr/lib32/firefox32/plugins
```

---

### Post by M$LOL on 2007-02-28
Thanks, that worked perfectly. Now that that's sorted, maybe you can help me with my other problem. Every once in a while, FF will take ages to load, and finally come up with a "Cannot find server". This has happened ever since I got my PC connected to the net, and I have IPv6 disabled. FF will normally be really fast, and then suddenly take ages to load before giving me that error. If I disable and then reenable the network adapter it will fix it, for a while, as will logging out and back in again. I have fiddled with the network adapter's settings unsuccessfully and at the moment it's set to DHCP with the nameserver my router's IP address.

My network has two PCs, this one and a Windows one connected wirelessly to a router which is also a DSL modem, which provides my net connection.

Thank you for taking the time to help me. :)

---

### Post by firekat on 2007-02-28
I am pretty much of a newbie with all of this but I loaded Flash, in a flash.  I am running Swiftfox amd 64.  Prior to installation of the deb package from the swiftfox website I ran "sudo apt-get ia32-libs-gtk".  I clicked on the swiftfox deb, it showed that all dependencies were complied with and loaded the program.  After a number of clicks on the program it installed and started running (after a few false firefox starts and a reboot).

I have seen a lot written about installing Flash being a problem.  This morning on a lark while browsing on the web and on a site requiring Flash I clicked on the green puzzle piece icon and faster than two shakes of a lamb's tail Flash was installed.  I just went to youtube and tested it on a video and it works!

Please let me know if this works for anyone else.  I'd like to know if a newbie like me can help anyone!

---

### Post by Kilz on 2007-02-28
> **firekat said:**
> I am pretty much of a newbie with all of this but I loaded Flash, in a flash.  I am running Swiftfox amd 64.  Prior to installation of the deb package from the swiftfox website I ran "sudo apt-get ia32-libs-gtk".  I clicked on the swiftfox deb, it showed that all dependencies were complied with and loaded the program.  After a number of clicks on the program it installed and started running (after a few false firefox starts and a reboot).

I have seen a lot written about installing Flash being a problem.  This morning on a lark while browsing on the web and on a site requiring Flash I clicked on the green puzzle piece icon and faster than two shakes of a lamb's tail Flash was installed.  I just went to youtube and tested it on a video and it works!

Please let me know if this works for anyone else.  I'd like to know if a newbie like me can help anyone!

The problem is that Swiftfox isnt free as in freedom. Its basically a compile of the Firefox code. The person who built it then took away your freedom to redistribute it to your friends. Something you can do with both the program (Firefox) and source code the compiled binary is made from.
I understand the need to run some non free things once in awhile. Like video card drivers and such to get functionality. But to give up freedom for no need when Firefox works just as well makes no sense to me and a lot of people who would perfer to use Free software if there is a choice. Because by using this non-free software we send the wrong idea back to the builder, that this taking away or freedom is ok. To many people have worked to hard and long to give us freedom for me to do that. It just isnt worth it.
To those that say there is a difference I direct you to [APC Benchmarks]("http://www.apcstart.com/node/3097"), that found a whopping .12th of a second speed difference.

---

### Post by firekat on 2007-02-28
Sorry, I did not mean to insult you.  I am not totally aware of all the different licensing of the myriad of different free software.

It was my assumption that if it worked in swiftfox it would work in firefox since they are similar and all my firefox settings (what few there were) was picked up.

I tried firefox and it did not come up with puzzle pieces.

I guess from now on I will be loath to offer assistance lest I step on anyone's toes.  After all I am a newbie, what do I know?


Sorry.

---

### Post by Kilz on 2007-02-28
> **firekat said:**
> Sorry, I did not mean to insult you.  I am not totally aware of all the different licensing of the myriad of different free software.

It was my assumption that if it worked in swiftfox it would work in firefox since they are similar and all my firefox settings (what few there were) was picked up.

I tried firefox and it did not come up with puzzle pieces.

I guess from now on I will be loath to offer assistance lest I step on anyone's toes.  After all I am a newbie, what do I know?


Sorry.

Please dont take what I said as being negative towards you. It wasnt ment that way. Part of what the forums are for is information in all forms. Since Ubuntu is a FOSS (Free and Open Source Software) project. Sometimes it is necessary to share opinions on what is free and what isnt. Ubuntu's [Philosophy is very important]("http://www.ubuntu.com/ubuntu/philosophy"), as is its stance on _free _as in _freedom_ software (same page).
Sometimes new users dont think about the free as in freedom, all they consider is the free as in cost. But the two are linked. 
We should all do our part to uphold the freedom of software, its in our own best interest. Thats why when someone perverts (the creator of Swiftfox) free software some of us take offense. That they have tricked new users is even more offensive.
The offense isnt towards you, the new user, but the person who has taken some freedom from the community. Not just one person , but the whole community. We are all the worst for it.
Please also continue to post and help, thats part of Ubuntu. :)

---

### Post by M$LOL on 2007-03-01
In general, I always try to stay with software that is free in both ways and also opensource. Software made by companies always has terms and conditions attached, and that's not a good thing for the rest of us.

Any advice about my problem? It's starting to become more and more frequent, and is making it near impossible to use the net.

---

### Post by Kilz on 2007-03-01
> **M$LOL said:**
> In general, I always try to stay with software that is free in both ways and also opensource. Software made by companies always has terms and conditions attached, and that's not a good thing for the rest of us.

Any advice about my problem? It's starting to become more and more frequent, and is making it near impossible to use the net.

The only thing I can think of is you may want to try disabling ipv6. I did and it speeded up my firefox, the hourglass seemed to show all the time before. 

for ubuntu

1. gksudo gedit /etc/modprobe.d/aliases
2.Comment out this line: alias net-pf-10 ipv6
3.Save the file
4.gksudo gedit /etc/modprobe.d/blacklist
5.Add this line: blacklist ipv6
6.Save the file and restart your computer

for kubuntu

1.kdesu kate /etc/modprobe.d/aliases
2.Comment out this line: alias net-pf-10 ipv6
3.Save the file
4.kdesu kate /etc/modprobe.d/blacklist
5.Add this line: blacklist ipv6
6.Save the file and restart your computer

You must reboot for changes to take effect. 

If that doesnt help, its a network setting or connection issue. Im not all than knowlageable in that department. So rather than say the wrong thing and make it worse, I suggest posting in the network secrion of the forum or make a new post on it in this section.

---

### Post by M$LOL on 2007-03-01
Well, that seems to have worked, even though I had already done it in Firefox :confused: , thanks so much for your help, you've solved both of my problems in one thread.:grin:

---

### Post by diafanos on 2007-03-19
I run the script, everything went fine, except from flash installation.
Even though the two files (libflashplayer.so and flashplayer.xpt) are in the plugin directory, still no flash!!!

Please any suggestions? I'm really disappointed...


Edit
-------
Ok, I got it. There is a .mozilla directory in $HOME. I went there and delete all previous (from firefox 64) plugins.

---

### Post by Kilz on 2007-03-19
> **diafanos said:**
> I run the script, everything went fine, except from flash installation.
Even though the two files (libflashplayer.so and flashplayer.xpt) are in the plugin directory, still no flash!!!

Please any suggestions? I'm really disappointed...

Disappointed? Why?

After answering, open a terminal and type in 
```
ls -al /usr/lib32/firefox32/plugins

```
 
Then paste in the results after your answer.

---

### Post by diafanos on 2007-03-20
It's ok Kilz, you didn't notice, but I had edited my post. I wasn't aware of the $HOME\.mozilla directory. There was a flash plugin from previous browser (firefox 64). I deleted and problem is solved.

> Disappointed?
No longer! Thanks!

---

