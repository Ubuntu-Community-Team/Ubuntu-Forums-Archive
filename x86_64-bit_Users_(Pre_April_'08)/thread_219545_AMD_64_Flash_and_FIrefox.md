---
title: "AMD 64 Flash and FIrefox"
date: 2006-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by shankhar on 2006-07-20
I tried to install Macromedia Flash player by following the instructions given in Abode site but unable to install the flash player. :( . Please give me instructions how to install flash player in Ubuntu in Firefox1.0

Before that please give me instructions to upgrade to Firefox 1.5x.

i'm sorry i had wrongly posted in Dapper Drake column i'm not using Dapper Drake, i'm using Ubuntu 5.10 in AMD 64 bit processor

Thanx in advance

---

### Post by Kilz on 2006-07-20
> **shankhar said:**
> I tried to install Macromedia Flash player by following the instructions given in Abode site but unable to install the flash player. :( . Please give me instructions how to install flash player in Ubuntu in Firefox1.0

Before that please give me instructions to upgrade to Firefox 1.5x.

i'm sorry i had wrongly posted in Dapper Drake column i'm not using Dapper Drake, i'm using Ubuntu 5.10 in AMD 64 bit processor

Thanx in advance
[I have a howto that gives step by step instructions for 32bit firefox and most plugins.]("http://www.ubuntuforums.org/showthread.php?p=1174435")

---

### Post by mayamaniac on 2006-07-20
flash wont work in AMD64, at least not yet. This is one of the main reason why I uninstalled Dapper 64bit on my AMD64 machine. I'm now running Dapper 32bit and haven't noticed any performance difference.

---

### Post by Kilz on 2006-07-20
> **mayamaniac said:**
> flash wont work in AMD64, at least not yet. This is one of the main reason why I uninstalled Dapper 64bit on my AMD64 machine. I'm now running Dapper 32bit and haven't noticed any performance difference.
Wrong, flash and other plugins just need 32bit firefox installed. Read my howto. I also have automated setup scripts on the page. There are few reasons to switch to a 32bit os, all it takes is following a howto most of the time.

---

### Post by jamesrw on 2006-07-24
dunno what it is but im getting flash just fine under 64bit breezy :)

---

### Post by Kilz on 2006-07-24
> **jamesrw said:**
> dunno what it is but im getting flash just fine under 64bit breezy :)

You should try 64bit Dapper. :D

---

### Post by jamesrw on 2006-07-26
whoops ya i meant dapper... its been a while

---

### Post by hajk on 2006-07-26
Actually, Macromedia Flash can be installed under AMD64 together with 32-bit Opera 9 (provided that you install the "Other/Static DEB" package from the Opera download site). This works because this software doesn't use system libraries, and because AMD64 processors have a 32-bit compatibility mode.

---

### Post by shankhar on 2006-07-26
Hello Kilz,
  
    i had tried your howto but i failed to make it.
    
    Actually there is Mozilla Firefox 1.0.7 already installed anyway i tried out your howto but i dono why its not coming.....:-k

---

### Post by shankhar on 2006-07-26
Hello Kilz,
  
    i had tried your howto but i failed to make it.
    
    Actually there is Mozilla Firefox 1.0.7 already installed anyway i tried out your howto but i dono why its not coming.....:-k

---

### Post by Kilz on 2006-07-26
> **shankhar said:**
> Hello Kilz,
  
    i had tried your howto but i failed to make it.
    
    Actually there is Mozilla Firefox 1.0.7 already installed anyway i tried out your howto but i dono why its not coming.....:-k

1.0.7 is incredibly old, I would be concerned about security. If you have trouble with the howto, download and run one of the automated setup scripts on the howto page.

---

### Post by shankhar on 2006-07-28
Hello Kilz,

    how can i upgrade to Firefox 1.5., please provide me help yar and also to install...
where can i find the installed folder of firefox1.0 in my system

:confused:

---

### Post by shankhar on 2006-07-28
Sorry Kilz

I'm a new user to Linux, but i luv linux.:D

---

### Post by adusty on 2006-07-28
I find this thread:
[http://www.ubuntuforums.org/showthread.php?t=160318](http://www.ubuntuforums.org/showthread.php?t=160318)
where they explain how to use nspluginwrapper, but the procedure does not work for me, someone can tell his experience?

Using nspluginwrapper should be better because you do not need to install a 32bit browser to use the plugin.

Thanks,
Alex

---

### Post by Kilz on 2006-07-28
> **adusty said:**
> I find this thread:
[http://www.ubuntuforums.org/showthread.php?t=160318](http://www.ubuntuforums.org/showthread.php?t=160318)
where they explain how to use nspluginwrapper, but the procedure does not work for me, someone can tell his experience?

Using nspluginwrapper should be better because you do not need to install a 32bit browser to use the plugin.

Thanks,
Alex

While its possible, nspluginwrapper is real hard to get working, the user more or less has to create each of the plugin themselves and manually move them into place. Its is getting mixed results at this point. From the creators own site "Bear in mind this is BETA software. The following plugins work reasonably well".
The 64bit work around sticky recommends to install 32bit firefox and 32bit plugins over this method at the present time because there is a better chance at success. But its up to you

---

### Post by DooX on 2006-07-28
Ok,your script is working Kilz thanx for effort creating it,but i dont like the way this problem solved.If we are using 64-bit proccessor we want 64-bit software.This is something that I would except from Microsoft...

---

### Post by Kilz on 2006-07-28
> **DooX said:**
> Ok,your script is working Kilz thanx for effort creating it,but i dont like the way this problem solved.If we are using 64-bit proccessor we want 64-bit software.This is something that I would except from Microsoft...

The problem is that Marcomedia/Adobe have yet to even release flash 8 for 32bit Linux, and no version for 64bit. Same with Sun Java plugin and acrobat. They are all proprietary formats that open source has no control over. If you are disappointed, please let them know with a post/email to their corporate offices.
I am a user just like you who is tired of things not working in any form. I made the howto's/scripts so we at least have some functionality.

---

### Post by shankhar on 2006-07-29
Hello Kilz,
    I had installed Firefox 1.5.0.4 by using your script and also Flash is working correctly, its great:D , but i intalled your script with java and mplayer after i installed firefox with flah after that, firefox and flash is working fine but when i browse a java site i.e applets and all firefox is getting crashed plz give me a solution.

And another issue i suppose firefox is intalled in my desktop, why i'm telling is a folder is ther in desktop named firefox and it is locked, i'm not sure where firefox is installed.

But its working fine great:D ......but wn i browse java enabled site firefox is getting crashed.....:-(

---

### Post by Kilz on 2006-07-29
> **shankhar said:**
> Hello Kilz,
    I had installed Firefox 1.5.0.4 by using your script and also Flash is working correctly, its great:D , but i intalled your script with java and mplayer after i installed firefox with flah after that, firefox and flash is working fine but when i browse a java site i.e applets and all firefox is getting crashed plz give me a solution.

And another issue i suppose firefox is intalled in my desktop, why i'm telling is a folder is ther in desktop named firefox and it is locked, i'm not sure where firefox is installed.

But its working fine great:D ......but wn i browse java enabled site firefox is getting crashed.....:-(

It sounds like something went wrong. Did the sript error out? Because there shouldnt be anything left on your desktop. Also did you aply the fix in the java section of the howto?

---

### Post by DooX on 2006-07-29
Hmm during the instalation of java,it asked do I want to enable something that is enabled by default but its not ok from security reason to be enable,so i said NO like it suggested.But now when i try to execute some java script i get ```
Plugin: 'Java' [ Loaded ]
Plugin: 'Java' [ inaccessible from javascript ]
Plugin: 'Flash' [ Probing ]
Plugin: 'Flash' [ Couldn't access javascript ]
```

I tryed to install script again,only java,but didnt helped,because didnt asked me again that question.Have any idea how to unnistal everything that your script placed in my Linux,or maybe some other solution?Thanx

---

### Post by Kilz on 2006-07-29
> **DooX said:**
> Hmm during the instalation of java,it asked do I want to enable something that is enabled by default but its not ok from security reason to be enable,so i said NO like it suggested.But now when i try to execute some java script i get ```
Plugin: 'Java' [ Loaded ]
Plugin: 'Java' [ inaccessible from javascript ]
Plugin: 'Flash' [ Probing ]
Plugin: 'Flash' [ Couldn't access javascript ]
```

I tryed to install script again,only java,but didnt helped,because didnt asked me again that question.Have any idea how to unnistal everything that your script placed in my Linux,or maybe some other solution?Thanx

 What page are you accessing? [You might also want to read this page before removing the java plugin.]("http://www.irt.org/script/4000.htm")

---

### Post by shankhar on 2006-08-02
> **Kilz said:**
> It sounds like something went wrong. Did the sript error out? Because there shouldnt be anything left on your desktop. Also did you aply the fix in the java section of the howto?

Hello Kilz,

Firefox crashed more times and finally it crashed fully:( , when i click the launcher it is not opening and so i removed firefox and i'm trying to install newly by again downloading your script, have you changed your script, why i'm asking is in the script folder ther is no folders such as exe, launch, libpangohack, prango.
OK anyway i'm installing again, i'll let you know what happens.;)

---

### Post by Kilz on 2006-08-02
> **shankhar said:**
> Hello Kilz,

Firefox crashed more times and finally it crashed fully:( , when i click the launcher it is not opening and so i removed firefox and i'm trying to install newly by again downloading your script, have you changed your script, why i'm asking is in the script folder ther is no folders such as exe, launch, libpangohack, prango.
OK anyway i'm installing again, i'll let you know what happens.;)

Yes I uploaded a new version a few days ago. I learned how to make a firefox32 .deb file. Then upgraded all the scripts to use that file. This improvement makes it easier to remove/upgrade firefox32 as its now a package. All the script dose now is install packages.

---

### Post by shankhar on 2006-08-02
> **Kilz said:**
> Yes I uploaded a new version a few days ago. I learned how to make a firefox32 .deb file. Then upgraded all the scripts to use that file. This improvement makes it easier to remove/upgrade firefox32 as its now a package. All the script dose now is install packages.

Oh, its greeat Kilz, the installation is going on.

I am installing Firefox32-flash-java-mplayer, before that i totally removed Firefox, 

I 'll tell you what happens. OK

---

### Post by shankhar on 2006-08-02
Hello Kliz,

  After i reinstalled Firefox its not opening. i duno why

This is what happenned

> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
--16:53:34--  [http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz](http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz)
           => `firefox32-1.5.0.5_amd64.tar.gz'
Resolving home.comcast.net... 204.127.198.24
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,525,767 (8.1M) [application/x-tar]

60% [================================================>                                 ] 5,117,600      6.07K/s    ETA 09:00

17:07:19 (6.19 KB/s) - Connection closed at byte 5117600. Retrying.

--17:07:20--  [http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz](http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz)
  (try: 2) => `firefox32-1.5.0.5_amd64.tar.gz'
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 206 Partial content
Length: 8,525,767 (8.1M), 3,408,167 (3.2M) remaining [application/x-tar]

63% [+++++++++++++++++++++++++++++++++++++++++++++++++==>                              ] 5,444,080      4.46K/s    ETA 09:19

17:08:20 (5.38 KB/s) - Connection closed at byte 5444080. Retrying.

--17:08:22--  [http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz](http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz)
  (try: 3) => `firefox32-1.5.0.5_amd64.tar.gz'
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 206 Partial content
Length: 8,525,767 (8.1M), 3,081,687 (2.9M) remaining [application/x-tar]

71% [++++++++++++++++++++++++++++++++++++++++++++++++++++=====>                        ] 6,083,056      4.50K/s    ETA 08:01

17:10:28 (4.97 KB/s) - Connection closed at byte 6083056. Retrying.

--17:10:31--  [http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz](http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz)
  (try: 4) => `firefox32-1.5.0.5_amd64.tar.gz'
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 206 Partial content
Length: 8,525,767 (8.1M), 2,442,711 (2.3M) remaining [application/x-tar]

78% [++++++++++++++++++++++++++++++++++++++++++++++++++++++++++=====>                  ] 6,713,840      7.68K/s    ETA 05:16

17:12:21 (5.64 KB/s) - Connection closed at byte 6713840. Retrying.

--17:12:25--  [http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz](http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz)
  (try: 5) => `firefox32-1.5.0.5_amd64.tar.gz'
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 206 Partial content
Length: 8,525,767 (8.1M), 1,811,927 (1.7M) remaining [application/x-tar]

80% [++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++=>                ] 6,905,152      2.93K/s    ETA 08:22

17:13:26 (3.26 KB/s) - Connection closed at byte 6905152. Retrying.

--17:13:31--  [http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz](http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz)
  (try: 6) => `firefox32-1.5.0.5_amd64.tar.gz'
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 206 Partial content
Length: 8,525,767 (8.1M), 1,620,615 (1.5M) remaining [application/x-tar]

100%[++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++===============>] 8,525,767      5.29K/s    ETA 00:00

17:17:51 (6.09 KB/s) - `firefox32-1.5.0.5_amd64.tar.gz' saved [8525767/8525767]

firefox32/launcher/Firefox32.desktop
firefox32/firefox32-1.5.0.5_amd64.deb
firefox32/Readme
Selecting previously deselected package firefox32.
(Reading database ... 86029 files and directories currently installed.)
Unpacking firefox32 (from .../firefox32-1.5.0.5_amd64.deb) ...
dpkg: error processing /home/nrsp/Desktop/ffinstall/firefox32/firefox32-1.5.0.5_amd64.deb (--install):
 trying to overwrite `/usr/lib32/libpangohack.so.0.0', which is also in package ia32-libs-gtk
Errors were encountered while processing:
 /home/nrsp/Desktop/ffinstall/firefox32/firefox32-1.5.0.5_amd64.deb
--17:17:57--  [http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb)
           => `flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16,492 (16K) [text/plain]

100%[=================================================================================>] 16,492        12.93K/s

17:18:14 (12.91 KB/s) - `flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb' saved [16492/16492]

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 86029 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 7.0.63.3ubuntu3 (using flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...
send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed with error code 1

cp: cannot stat `/usr/lib/flashplugin-nonfree/*': No such file or directory
--17:29:48--  [http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/j/j2se1.4-i586/j2re1.4_1.4.2.02-1ubuntu3_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/j/j2se1.4-i586/j2re1.4_1.4.2.02-1ubuntu3_i386.deb)
           => `j2re1.4_1.4.2.02-1ubuntu3_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 22,509,784 (21M) [text/plain]

100%[=================================================================================>] 22,509,784     7.44K/s    ETA 00:00

18:15:25 (8.09 KB/s) - `j2re1.4_1.4.2.02-1ubuntu3_i386.deb' saved [22509784/22509784]

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 86029 files and directories currently installed.)
Preparing to replace j2re1.4 1.4.2.02-1ubuntu3 (using j2re1.4_1.4.2.02-1ubuntu3_i386.deb) ...
Unpacking replacement j2re1.4 ...
Setting up j2re1.4 (1.4.2.02-1ubuntu3) ...

ln: `/usr/local/firefox32/plugins//libjavaplugin_oji.so': File exists
--18:16:27--  [http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/m/mplayerplug-in/mozilla-mplayer_3.17-1ubuntu1_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/m/mplayerplug-in/mozilla-mplayer_3.17-1ubuntu1_i386.deb)
           => `mozilla-mplayer_3.17-1ubuntu1_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 431,334 (421K) [text/plain]

100%[=================================================================================>] 431,334        6.76K/s    ETA 00:00

18:17:48 (6.58 KB/s) - `mozilla-mplayer_3.17-1ubuntu1_i386.deb' saved [431334/431334]

You may get a 'sudo: Unable to get working directory' error when the script cleans up after itself. Please disregard it.
sudo: cannot get working directory



give me a solution kilz:(

---

### Post by dasyar613 on 2006-08-02
Hey Shankhar, getting to be a little on the DEMANDING side aren't you. You may be getting to be a lttle frustrated, but the people on this forum are NOT your personal free software consultants. As for the people that keep complaining about Firefox and Flash, you have emailed them to complain of the lack of 64 bit support, right? As for the post about expectations as it pertains to Microsoft, you would have a leg to stand on if Ubuntu were the authors of Firefox and Flash.

---

### Post by Kilz on 2006-08-02
> **shankhar said:**
> Hello Kliz,

  After i reinstalled Firefox its not opening. i duno why

This is what happenned



give me a solution kilz:(

It looks like there were errors in the firefox instalation. [Download this file.]("http://home.comcast.net/~deletebox/firefox32-1.5.0.6_amd64.deb)

Next lets delete whats there so it installs clean.
```
sudo dpkg -r firefox32
sudo rm -r /usr/lib32/libpangohack.so.0
sudo rm -r /usr/lib32/libpangohack.so.0.0
sudo rm -r /etc/pango32/pangorc
sudo rm -r /usr/local/bin/firefox32
```

Then double click on the firefox32.deb file you downloaded and let gdebi install it.

---

### Post by shankhar on 2006-08-04
> **Kilz said:**
> It looks like there were errors in the firefox instalation. Download this file.[http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz]("http://home.comcast.net/~deletebox/firefox32-1.5.0.5_amd64.tar.gz")
Extract it.

Next lets delete whats there so it installs clean.
```
sudo dpkg -r firefox32
sudo rm -r /usr/lib32/libpangohack.so.0
sudo rm -r /usr/lib32/libpangohack.so.0.0
sudo rm -r /etc/pango32/pangorc
sudo rm -r /usr/local/bin/firefox32
```

Then double click on the firefox32.deb file you downloaded and let gdebi install it.

Hello Kilz,
Sorry yar i think i'm disturbing u...:sad: 

Again....

I opened the firefox32.deb file by default it is opening by Archive Manager, then i tried to open using gdeb, then it opened, i clicked install it asked password i gave it, then no changes had been seen it returns back to the last state.

There is no application like gdebi in the Application List and also in the Synaptics Package Manager also...

---

### Post by Kilz on 2006-08-04
> **shankhar said:**
> Hello Kilz,
Sorry yar i think i'm disturbing u...:sad: 

Again....

I opened the firefox32.deb file by default it is opening by Archive Manager, then i tried to open using gdeb, then it opened, i clicked install it asked password i gave it, then no changes had been seen it returns back to the last state.

There is no application like gdebi in the Application List and also in the Synaptics Package Manager also...

I never said you are disturbing me. 
The file you are downloading is a tar.gz. You have to extract it. Inside the files you extract is a deb file. I have to do it this way because the web space I get for free from my isp doesnt allow .deb files for some strange reason. I updated last night. [There is a new firefox file to download.]("http://home.comcast.net/~deletebox/firefox32-1.5.0.6_amd64.tar.gz"). Since you cant find gdebi, extract the file to your desktop, move the .deb file in it to your desktop. Open a terminal type in
```
sudo dpkg -i firefox32-1.5.0.6_amd64.tar.gz
```Drag the launcher in the extracted files to your desktop. Use it to launch the firefox.

---

### Post by x64Jimbo on 2006-08-04
kilz,
i really like the work you've been doing. Bravo!
You may want to have an option to install the Windows version of firefox thru wine. I've been using Firefox this way for a while now with no problems. This even allows viewing of websites that require Flash 8+.
Again, great work!

---

### Post by Kilz on 2006-08-04
> **x64Jimbo said:**
> kilz,
i really like the work you've been doing. Bravo!
You may want to have an option to install the Windows version of firefox thru wine. I've been using Firefox this way for a while now with no problems. This even allows viewing of websites that require Flash 8+.
Again, great work!
Thanks. Im trying to help as many people as I can and make the 64bit population grow. I use firefox under wine to watch the ABC tv shows online. To bad its gone for the summer.
I have to think about it making an install script. I was going to package swiftfox, as an alternative. But the creator is making me think twice. Hes posted what I concider a threat on their forum to stop work on it if I distribute it.

---

### Post by shankhar on 2006-08-07
> **Kilz said:**
> I never said you are disturbing me. 
The file you are downloading is a tar.gz. You have to extract it. Inside the files you extract is a deb file. I have to do it this way because the web space I get for free from my isp doesnt allow .deb files for some strange reason. I updated last night. [There is a new firefox file to download.]("http://home.comcast.net/~deletebox/firefox32-1.5.0.6_amd64.tar.gz"). Since you cant find gdebi, extract the file to your desktop, move the .deb file in it to your desktop. Open a terminal type in
```
sudo dpkg -i firefox32-1.5.0.6_amd64.tar.gz
```Drag the launcher in the extracted files to your desktop. Use it to launch the firefox.

Thank you Kilz

i tried that but again

nrsp@AMD1SacredInfocom:~/Desktop$ sudo dpkg -i firefox32-1.5.0.6_amd64.tar.gz
Password:
dpkg-deb: `firefox32-1.5.0.6_amd64.tar.gz' is not a debian format archive
dpkg: error processing firefox32-1.5.0.6_amd64.tar.gz (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 firefox32-1.5.0.6_amd64.tar.gz

i think u had mistakenly entered the filename firefox32-1.5.0.6_amd64.tar.gz instead of firefox32-1.5.0.6_amd64.deb

but anyway i tried the debian file the following is happened

nrsp@AMD1SacredInfocom:~/Desktop$ sudo dpkg -i firefox32-1.5.0.6_amd64.deb
(Reading database ... 98643 files and directories currently installed.)
Unpacking firefox32 (from firefox32-1.5.0.6_amd64.deb) ...
dpkg: error processing firefox32-1.5.0.6_amd64.deb (--install):
 trying to overwrite `/usr/lib32/libpangohack.so.0.0', which is also in package ia32-libs-gtk
Errors were encountered while processing:
 firefox32-1.5.0.6_amd64.deb

---

### Post by fieldstone on 2006-08-07
I've got Flash working (pretty much - sometimes it freezes/crashes) in Firefox, Firefox32, and Swiftfox. But no sound in any of them. I've tried all the hacks for this I've found online (symbolic links and changing firefox's dsp) and it doesn't seem to help.

When I run Firefox and try to play a flash file, I get the following message:

ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

I'm pretty sure this is my sound problem, but I'm stumped as to how to fix it. Has anyone run into this before?

---

### Post by Dragonstar on 2006-08-08
> **fieldstone said:**
> I've got Flash working (pretty much - sometimes it freezes/crashes) in Firefox, Firefox32, and Swiftfox. But no sound in any of them. I've tried all the hacks for this I've found online (symbolic links and changing firefox's dsp) and it doesn't seem to help.

When I run Firefox and try to play a flash file, I get the following message:

ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

I'm pretty sure this is my sound problem, but I'm stumped as to how to fix it. Has anyone run into this before?

I have the same situation except that I have sound, but it's out of sync. When I run "aoss firefox" (I have alsa-oss installed) and try to play a flash file, I still have sound out of sync and I get the same error.

---

### Post by Kilz on 2006-08-08
> **shankhar said:**
> Thank you Kilz

i tried that but again

nrsp@AMD1SacredInfocom:~/Desktop$ sudo dpkg -i firefox32-1.5.0.6_amd64.tar.gz
Password:
dpkg-deb: `firefox32-1.5.0.6_amd64.tar.gz' is not a debian format archive
dpkg: error processing firefox32-1.5.0.6_amd64.tar.gz (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 firefox32-1.5.0.6_amd64.tar.gz

i think u had mistakenly entered the filename firefox32-1.5.0.6_amd64.tar.gz instead of firefox32-1.5.0.6_amd64.deb

but anyway i tried the debian file the following is happened

nrsp@AMD1SacredInfocom:~/Desktop$ sudo dpkg -i firefox32-1.5.0.6_amd64.deb
(Reading database ... 98643 files and directories currently installed.)
Unpacking firefox32 (from firefox32-1.5.0.6_amd64.deb) ...
dpkg: error processing firefox32-1.5.0.6_amd64.deb (--install):
 trying to overwrite `/usr/lib32/libpangohack.so.0.0', which is also in package ia32-libs-gtk
Errors were encountered while processing:
 firefox32-1.5.0.6_amd64.deb

Please follow the [instructions in this post.]("http://www.ubuntuforums.org/showpost.php?p=1329697&postcount=27")

---

### Post by Kilz on 2006-08-08
> **fieldstone said:**
> I've got Flash working (pretty much - sometimes it freezes/crashes) in Firefox, Firefox32, and Swiftfox. But no sound in any of them. I've tried all the hacks for this I've found online (symbolic links and changing firefox's dsp) and it doesn't seem to help.

When I run Firefox and try to play a flash file, I get the following message:

ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

I'm pretty sure this is my sound problem, but I'm stumped as to how to fix it. Has anyone run into this before?

Is this happeneing with every version of Firefox. The 64bit, 32bit, and Swiftfox?

---

### Post by shankhar on 2006-08-11
Hello Kilz,
   That u told to follow is not worked out since it is not working on my system [That Debian Package], since i'm an new bie i dont know why it is, i think it may require some other packages to be installed.

And so i removed manually the installed contents of firefox32 in the firefox32 folder. i'm unable to remove firefox32 folder but removed the contents sucessfully. 

After that i followed your howto till Flash and also the Launcher now i got Firefox1.5.0.6 installed sucessfully with Flash. I'm happy:) 

But i don't know whether it will crash again or not. And i don't know why its happening.

Its really a great work done by you.

Now i'm happy.

Thank you very much Kilz.:D

---

### Post by Kilz on 2006-08-11
I know I tested the debain package on a virtual machine. But all the .deb file dose is install Firefox. The install scripts should set everything up if you agree to the licenses. You may also have to have the [universe repositories enabled]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")
Im glad the manual howto worked for you. :D

---

### Post by fieldstone on 2006-08-11
> **Kilz said:**
> Is this happeneing with every version of Firefox. The 64bit, 32bit, and Swiftfox?

Yes it is. I've even tried a clean reinstall of Ubuntu (still AMD64), and I've still got this problem.

---

### Post by Kilz on 2006-08-11
> **fieldstone said:**
> Yes it is. I've even tried a clean reinstall of Ubuntu (still AMD64), and I've still got this problem.

Is there a libaoss.so file in /usr/lib or /usr/lib32 ?

---

### Post by fieldstone on 2006-08-11
> **Kilz said:**
> Is there a libaoss.so file in /usr/lib or /usr/lib32 ?

In /usr/lib, there is. In /usr/lib32, there isn't.

---

### Post by fieldstone on 2006-08-11
> **Kilz said:**
> Is there a libaoss.so file in /usr/lib or /usr/lib32 ?

Actually, I only get the error if I try to run 'aoss /opt/swiftfox/swiftfox', and i get a similar one (with esd files instead) if I run 'esddsp /opt/swiftfox/swiftfox'. Otherwise, there's no error, but still no sound.

Stuff I've already tried:

ln -s /tmp/.esd-1000/ /tmp/.esd/
ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

Changing FIREFOX_DSP (in /etc/firefox/firefoxrc) to "aoss", "esd", "auto", or "arts", all with no success.

I've also tried creating a firefoxrc file in /opt/swiftfox and changing the DSP in there, but it also didn't seem to do anything. Does swiftfox (or firefox32, for that matter) refer to /etc/firefox/firefoxrc, or does it need its own file in its own directory?

I'm willing to try the chroot method if it's more reliable, whether it's more work or not... and I'm also willing to try reinstalling firefox32 using your script (haven't done that since reformatting). What do you suggest?

---

### Post by Kilz on 2006-08-11
> **fieldstone said:**
> Actually, I only get the error if I try to run 'aoss /opt/swiftfox/swiftfox', and i get a similar one (with esd files instead) if I run 'esddsp /opt/swiftfox/swiftfox'. Otherwise, there's no error, but still no sound.

Stuff I've already tried:

ln -s /tmp/.esd-1000/ /tmp/.esd/
ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

Changing FIREFOX_DSP (in /etc/firefox/firefoxrc) to "aoss", "esd", "auto", or "arts", all with no success.

I've also tried creating a firefoxrc file in /opt/swiftfox and changing the DSP in there, but it also didn't seem to do anything. Does swiftfox (or firefox32, for that matter) refer to /etc/firefox/firefoxrc, or does it need its own file in its own directory?

I'm willing to try the chroot method if it's more reliable, whether it's more work or not... and I'm also willing to try reinstalling firefox32 using your script (haven't done that since reformatting). What do you suggest?
First off Firefox in /usr/lib/firefox, the one that is installed with the amd64 version of Ubuntu wont even play flash. It is 64bit, flash is 32 bit. So messing with /etc/firefox wont do much good. You must have been looking at instructions for the i386 version.
Swiftfox disables things to make it faster, I dont know for sure if this is your problem, but I dont recommend it in any case as it is nonfree software.
I do recommend running this [Firefox32 install scrip]("http://home.comcast.net/~deletebox/Firefox32-flash-java-mplayer-3.tar.gz")t.  It only takes 2 commands you can find in the readme file when you extract the archive. Just agree to any questions it asks. Make sure the [univers repositories are enabled]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") and firefox is off when you do it.

---

### Post by fieldstone on 2006-08-11
> **Kilz said:**
> First off Firefox in /usr/lib/firefox, the one that is installed with the amd64 version of Ubuntu wont even play flash. It is 64bit, flash is 32 bit. So messing with /etc/firefox wont do much good. You must have been looking at instructions for the i386 version.
Swiftfox disables things to make it faster, I dont know for sure if this is your problem, but I dont recommend it in any case as it is nonfree software.
I do recommend running this [Firefox32 install scrip]("http://home.comcast.net/~deletebox/Firefox32-flash-java-mplayer-3.tar.gz")t.  It only takes 2 commands you can find in the readme file when you extract the archive. Just agree to any questions it asks. Make sure the [univers repositories are enabled]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") and firefox is off when you do it.

I'm at work right now, so I won't be able to do this until I get home. Firefox64 is now giving me a segmentation fault, so I need Firefox32 anyway.

Before I reinstalled Ubuntu, Firefox32 also had no sound in Flash, but I'll try this anyway and let you know if it works. If I need to switch FIREFOX_DSP for Firefox32, which file do I edit?

---

### Post by fieldstone on 2006-08-11
> **Kilz said:**
> First off Firefox in /usr/lib/firefox, the one that is installed with the amd64 version of Ubuntu wont even play flash. It is 64bit, flash is 32 bit. So messing with /etc/firefox wont do much good. You must have been looking at instructions for the i386 version.
Swiftfox disables things to make it faster, I dont know for sure if this is your problem, but I dont recommend it in any case as it is nonfree software.
I do recommend running this [Firefox32 install scrip]("http://home.comcast.net/~deletebox/Firefox32-flash-java-mplayer-3.tar.gz")t.  It only takes 2 commands you can find in the readme file when you extract the archive. Just agree to any questions it asks. Make sure the [univers repositories are enabled]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") and firefox is off when you do it.

About 64-bit Firefox:

The Flash plugin is supposed to work if it's installed using either Crossover Office or nspluginwrapper. I tried it both ways, but still no sound - not in Swiftfox, Firefox, or Firefox32, at least before I reinstalled Ubuntu. And things don't look much better after the reinstall either.

---

### Post by Kilz on 2006-08-11
> **fieldstone said:**
> About 64-bit Firefox:

The Flash plugin is supposed to work if it's installed using either Crossover Office or nspluginwrapper. I tried it both ways, but still no sound - not in Swiftfox, Firefox, or Firefox32, at least before I reinstalled Ubuntu. And things don't look much better after the reinstall either.

Crossoveroffice is wine. You would have to have installed the windows version of firefox for it to have worked with crossover office. The nspluginwrapper is difficult to get working for some people. Try this way, dont install anything else first. Sometimes installing mutiple things causes more problems.

---

### Post by fieldstone on 2006-08-11
> **Kilz said:**
> Crossoveroffice is wine. You would have to have installed the windows version of firefox for it to have worked with crossover office. The nspluginwrapper is difficult to get working for some people. Try this way, dont install anything else first. Sometimes installing mutiple things causes more problems.

I think you're missing what I'm saying here. I already DID get Flash working through both Crossover Office - yes, it DOES work in Linux Firefox, that's the whole point - and through nspluginwrapper. Neither of them had any sound.

Also - I installed (the 32-bit version of) Opera on my system, and had the exact same issue; flash worked but there was no sound.

All of this makes me think there's some underlying problem that's affecting all these browsers. And just installing Firefox32 isn't going to correct it. (But I'll still try it, just on the off chance it works. It didn't before, though.)

---

### Post by Kilz on 2006-08-11
> **fieldstone said:**
> I think you're missing what I'm saying here. I already DID get Flash working through both Crossover Office - yes, it DOES work in Linux Firefox, that's the whole point - and through nspluginwrapper. Neither of them had any sound.

Also - I installed (the 32-bit version of) Opera on my system, and had the exact same issue; flash worked but there was no sound.

All of this makes me think there's some underlying problem that's affecting all these browsers. And just installing Firefox32 isn't going to correct it. (But I'll still try it, just on the off chance it works. It didn't before, though.)

Yes I understand that you tried a lot of things to get sound working with flash. But I wonder if in all the trying that you did something that stoped it from working with the rest. My plan is to get one install, and work on that. Not try 10 different things that may cause problems with the others.
But there is one piece of info I can ask now. Do you have sound in other things?

---

### Post by fieldstone on 2006-08-11
> **Kilz said:**
> Yes I understand that you tried a lot of things to get sound working with flash. But I wonder if in all the trying that you did something that stoped it from working with the rest. My plan is to get one install, and work on that. Not try 10 different things that may cause problems with the others.
But there is one piece of info I can ask now. Do you have sound in other things?

Yep, that I do. Sound works in everything else, but I can't seem to get my headphones to work... probably that's a separate issue (I assume). If you have any insight on how to get headphones to work on nforce chipsets - especially without installing a new version of ALSA - I'm all ears :)

---

### Post by fieldstone on 2006-08-11
> **Kilz said:**
> Yes I understand that you tried a lot of things to get sound working with flash. But I wonder if in all the trying that you did something that stoped it from working with the rest. My plan is to get one install, and work on that. Not try 10 different things that may cause problems with the others.
But there is one piece of info I can ask now. Do you have sound in other things?

Firefox32 is installed, and still no sound in Flash. What should I try now?

---

### Post by Kilz on 2006-08-11
> **fieldstone said:**
> Firefox32 is installed, and still no sound in Flash. What should I try now?

First try and reboot, for some strange reason I had to last time. Then try this
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

---

### Post by fieldstone on 2006-08-11
> **Kilz said:**
> First try and reboot, for some strange reason I had to last time. Then try this
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

Already did that. It was one of the first things I tried.

---

### Post by Kilz on 2006-08-11
> **fieldstone said:**
> Already did that. It was one of the first things I tried.

In your home folder is a .macromedia folder, you may have to click edit, properties, and show hidden and backup files. Then close and reopen the home folder to see it. Who owns it and what group ? you or root? Right click on it, choose properties, click on permissions tab to find out.

---

### Post by fieldstone on 2006-08-12
> **Kilz said:**
> In your home folder is a .macromedia folder, you may have to click edit, properties, and show hidden and backup files. Then close and reopen the home folder to see it. Who owns it and what group ? you or root? Right click on it, choose properties, click on permissions tab to find out.

I'm the owner; I checked and followed your directions in the howto, just in case it might help. But still no sound.

---

### Post by Kilz on 2006-08-12
> **fieldstone said:**
> I'm the owner; I checked and followed your directions in the howto, just in case it might help. But still no sound.

So you also made sure you havs alsa-oss installed, dose the mplayer plugin have sound?

---

### Post by fieldstone on 2006-08-12
> **Kilz said:**
> So you also made sure you havs alsa-oss installed, dose the mplayer plugin have sound?

Yes... alsa-oss was installed by default, and i do have sound in the mplayer plugin.

---

### Post by Kilz on 2006-08-12
> **fieldstone said:**
> Yes... alsa-oss was installed by default, and i do have sound in the mplayer plugin.

WWhat happenes with ```
aoss firefox32
```

---

### Post by fieldstone on 2006-08-12
> **Kilz said:**
> WWhat happenes with ```
aoss firefox32
```

Still no sound. I know there should be, but there isn't :?

---

### Post by Kilz on 2006-08-12
> **fieldstone said:**
> Still no sound. I know there should be, but there isn't :?

No errors?

---

### Post by fieldstone on 2006-08-12
> **Kilz said:**
> No errors?

I do get a bunch of errors about libpangohack...

---

### Post by Kilz on 2006-08-12
> **fieldstone said:**
> I do get a bunch of errors about libpangohack...

thats normal, it cant load some graphics. But you dont get
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

---

### Post by fieldstone on 2006-08-12
> **Kilz said:**
> thats normal, it cant load some graphics. But you dont get
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

Nope, I don't get that message.

---

### Post by Kilz on 2006-08-12
> **fieldstone said:**
> Nope, I don't get that message.

Please make sure the lib32asound2 package is installed since we are running 32bit firefox.
```
sudo apt-get install lib32asound2
```

---

### Post by fieldstone on 2006-08-12
> **Kilz said:**
> Please make sure the lib32asound2 package is installed since we are running 32bit firefox.
```
sudo apt-get install lib32asound2
```

Yes, it's already installed.

---

### Post by Kilz on 2006-08-12
> **fieldstone said:**
> Yes, it's already installed.

Please go to /usr/local/firefox32 and make sure the flashplayer.xpt and libflashplayer.so are owned by you.

After looking for a solution I noticed that you have a post saying your audio jack for headphones isnt working. What audio drivers are you using?

---

### Post by fieldstone on 2006-08-12
> **Kilz said:**
> Please go to /usr/local/firefox32 and make sure the flashplayer.xpt and libflashplayer.so are owned by you.

After looking for a solution I noticed that you have a post saying your audio jack for headphones isnt working. What audio drivers are you using?

yes, they're owned by me, but still no sound.

i'm using whichever audio drivers were built into ubuntu... alsa, not sure of the details. how can i find out more?

---

### Post by Kilz on 2006-08-12
> **fieldstone said:**
> yes, they're owned by me, but still no sound.

i'm using whichever audio drivers were built into ubuntu... alsa, not sure of the details. how can i find out more?

Sound drivers are not something I know a lot about. But nvidia dose make nforce linux drivers for 64bit linux. I read in a pervious post of yours thats what you have. [You may want to look into installing them]("http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html"). This may kill 2 birds with one stone.

---

### Post by fieldstone on 2006-08-12
> **Kilz said:**
> Sound drivers are not something I know a lot about. But nvidia dose make nforce linux drivers for 64bit linux. I read in a pervious post of yours thats what you have. [You may want to look into installing them]("http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html"). This may kill 2 birds with one stone.

I tried installing those, and spent a lot of time tweaking config files, with no luck. I can live without headphone support, though, if I have to.

---

### Post by Kilz on 2006-08-12
> **fieldstone said:**
> I tried installing those, and spent a lot of time tweaking config files, with no luck. I can live without headphone support, though, if I have to.

I have a feeling the drivers are also causing the flash problem since we have just went over all of the known problems in my experence.

---

### Post by fieldstone on 2006-08-12
> **Kilz said:**
> I have a feeling the drivers are also causing the flash problem since we have just went over all of the known problems in my experence.

the nforce drivers aren't installed right now. i'm just using standard alsa.

---

### Post by Kilz on 2006-08-12
> **fieldstone said:**
> the nforce drivers aren't installed right now. i'm just using standard alsa.

Flash uses oss, the alsa-oss package is installed becuase you checked it.[ I did find a page]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=i820&chip=i820&module=intel8x0") that had some debian settings. Since Ubuntu is debian based you might want to look at it.

---

### Post by fieldstone on 2006-08-12
> **Kilz said:**
> Flash uses oss, the alsa-oss package is installed becuase you checked it.[ I did find a page]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=i820&chip=i820&module=intel8x0") that had some debian settings. Since Ubuntu is debian based you might want to look at it.

Yeah, that's the exact stuff I already tried, without success.

---

### Post by fieldstone on 2006-09-17
There was one additional step that was necessary for me, and I'm posting it here for anyone else that might be having Flash sound problems like I was.

After trying all the other fixes, I found that extracting the files from the i386 version of the "alsa-oss" deb file, and copying them to /usr/lib32/, solved my problem. Now I've got perfect sound in 32-bit firefox.

Hope that helps anyone else who's having the same problem I was.

---

### Post by Kilz on 2006-09-17
> **fieldstone said:**
> There was one additional step that was necessary for me, and I'm posting it here for anyone else that might be having Flash sound problems like I was.

After trying all the other fixes, I found that extracting the files from the i386 version of the "alsa-oss" deb file, and copying them to /usr/lib32/, solved my problem. Now I've got perfect sound in 32-bit firefox.

Hope that helps anyone else who's having the same problem I was.

Thank you, Ill be adding this fix to the script in the near future. :D

---

### Post by mrw on 2006-09-17
I used nspluginwrapper for AMD 64 for installing the 32 bit flash plubin in Firefox (64) and it works fine.

---

### Post by Kilz on 2006-09-17
> **mrw said:**
> I used nspluginwrapper for AMD 64 for installing the 32 bit flash plubin in Firefox (64) and it works fine.

As I posted on another thread, the wrapper is nice. But its still highly experemental. It can cause your browser to crash. Some people who use it block all flash, then enable just what they need to avoid this. Also as I understand it, it doesnt work for all plugins.
Im hoping it matures into something usefull. If so I plan on writing a script for it.

---

