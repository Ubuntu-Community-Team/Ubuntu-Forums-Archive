---
title: "HOWTO: Install Skype on 64-bit Ubuntu"
date: 2007-05-03
forum: x86 64-bit Users
---

### Post by Cappy on 2007-05-03
[https://developer.skype.com/LinuxSkype](https://developer.skype.com/LinuxSkype)
The skype EULA: [http://www.skype.com/company/legal/eula/index.html](http://www.skype.com/company/legal/eula/index.html)

**Copy and paste the block of code into your terminal to use. The terminal can be found at *Applications-->Accessories-->Terminal***

[SIZE="4"][CENTER]**Medibuntu's Repositories:**[/CENTER][/SIZE]
Medibuntu offers skype, which can be added to your repositories here: [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
You can then install skype by using your Synaptic Package Manager to search for "skype" or ```
sudo apt-get install skype
```

[SIZE="5"]
[CENTER]**Install:**[/CENTER][/SIZE]

**Install directly from the website:**
> 
sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64); sudo dpkg -i skype-install.deb


[SIZE="5"]
[CENTER]**Older Ubuntu Install:**[/CENTER][/SIZE]

> 
sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N frozenfox.freehostia.com/cappy/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64); sudo dpkg -i skype-install.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p libqtcore4 libqtgui4 bluez-alsa


If it fails to run please run "skype" in the terminal and post the output with your question.

---

### Post by wildlifer on 2007-05-04
Works perfectly! Thanks a lot!

---

### Post by Garyu on 2007-05-06
Works great, but no desktop/panel/menu icon/starter... You should add that to make the guide complete. :)

---

### Post by jespdj on 2007-05-06
Note, if you have a webcam, it's not going to work in Skype on Linux; the Linux version of Skype does not support video.

---

### Post by Cappy on 2007-05-07
I'm not sure how to add a menu icon from the command line. I was using skype 1.3 so my old link launches the new one.

---

### Post by SebbeJohan on 2007-05-08
Thanks a lot Cappy! works like a charm!

---

### Post by Garyu on 2007-05-08
> **Cappy said:**
> I'm not sure how to add a menu icon from the command line. I was using skype 1.3 so my old link launches the new one.

gedit ~/Desktop/Skype.desktop

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Exec=skype
Name=Skype
Icon=/usr/share/pixmaps/skype.png
```

Save the file, and voila you have a desktop icon. You can drag-and-drop it to add it to the panel. I'm not sure how to add it to the menu though, other than right-clicking and choose to edit the menu, but that wouldn't be command-line copy-and-paste...

---

### Post by fede on 2007-05-10
Hello,

First, thanks for the guide. 

Second: ia32-libs doesn't seem to be in the repos (universe, multiverse & medibuntu enabled here).

```

fede@fs-desktop:~$ sudo apt-get install ia32-libs libsigc++-2.0-0c2a
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ia32-libs
fede@fs-desktop:~$

```

Is it in backports? Or elsewhere?

Thanks!

---

### Post by Cappy on 2007-05-10
ia32-libs is in universe

or you can just download it from packages
```

wget http://mirrors.kernel.org/ubuntu/pool/main/i/ia32-libs/ia32-libs_1.5ubuntu9_amd64.deb
sudo dpkg -i ia32-libs_1.5ubuntu9_amd64.deb

```

---

### Post by fede on 2007-05-11
Sorry, I didn't realize you were posting in the amd64 section.

I have a 32 bit processor (using generic kernel). I was trying to follow your instructions for i386; and the error I posted was using feisty 32 bit version. I have double (and triple) checked: I've got universe enabled and there is no ia32-libs package; the link you give is for amd64 as the package name implies, I suppose... Do you know if I need it or something else to make skype 1.4 work on a 32 bit i386 feisty?

Thanks!

---

### Post by Cappy on 2007-05-11
Oops, no, the ia32-libs is only for amd64 compatibility with i386. I didn't know i386 didn't have this library though. I'll take it off the i386 guide. Skype should be working for you now.

---

### Post by fede on 2007-05-11
Thanks! It works perfectly.

---

### Post by Cappy on 2007-05-19
Updated for some unmet dependencies if you didn't have Skype 1.3 installed.

---

### Post by Cappy on 2007-05-23
Updated for the new skype alpha 1.4.0.64.

[http://share.skype.com/sites/garage/2007/05/skype_for_linux_14_alpha_updat.html](http://share.skype.com/sites/garage/2007/05/skype_for_linux_14_alpha_updat.html)

In comparison with previous build this new release 1.4.0.64 has numerous new features implemented:
feature: Create Account.
feature: Call ordinary phones dialpad.
feature: Graphic emoticons.
feature: X11 public API transport.
feature: DBUS public API transport.
feature: Public API manager dialog in Options.
feature: Mark All Viewed in new events list.
feature: New dialpad and other graphics.
feature: Technical Call Info tooltip.
feature: Birthday reminders.
cleanup: Add hover effect to Myself, Services and Events Area text buttons.
cleanup: Add hover effect to Transfer text buttons.
cleanup: Display (Alpha) or (Beta) tag in header and about box.
cleanup: File Transfer cleanups.
cleanup: Improved contact card look

In addition to long list of new features we have addressed many issues:
bugfix: Changes to line input (mood messages etc), behaves much more nicely now.
bugfix: Crash when opening profile via right-click menu whilst in a call.
bugfix: Delete chats a lot more cleanly.
bugfix: Don&#8217;t duplicate users&#8217; languages.
bugfix: Don&#8217;t show e-mail address after reloading if it wasn&#8217;t stored.
bugfix: Double click pstn contact starts call regardless of chat/call setting.
bugfix: Escaping issue with contact notifications.
bugfix: Event notifications now reset between logins.
bugfix: Expanded contact now has mouseover tooltip on their name.
bugfix: Chat bookmark changes from history are now reflected in chat window.
bugfix: Fix & escaping in Chats menus.
bugfix: Fix for non-workable EULA in Qt 4.3.x.
bugfix: Fix for non-working buttons in Options Dialog in Qt 4.3.x.
bugfix: Fix jumpy drawing on appearing Edit Profile window.
bugfix: Explicitly telling a chat to open should open it, even if minimised.
bugfix: If you close a minimised chat window, you could no longer open the chat.
bugfix: Incorrect match code in Events model lead to unpredictable events.
bugfix: No more &#8216;Broken Call&#8217; windows.
bugfix: Only (try to) save e-mail addresses and languages when necessary.
bugfix: Opening a blank chat would immediately place it into Recent Chats.
bugfix: Repopulate profile widget editor upon reloading.
bugfix: Search Contacts dialogue corruption.
bugfix: Typing into the chat userlist no longer causes unexpected behaviour on the main contact list.
bugfix: Use plain text body in chat (fixes communication issues with latest Windows Skype versions).
bugfix: View Account Page button now links to account page.

---

### Post by heracles on 2007-05-23
installed it as per excellent script. But like most Linux operations that I do there is no evidence where it is e.g. not in menu or on desktop

---

### Post by rsambuca on 2007-05-23
Great job Cappy.  I hope you feel bad, though.  You are making me very lazy;)

Maybe I should install Gentoo or something to make up for it.

---

### Post by fede on 2007-05-23
Thanks again. There is a typo in the last line of code: I think you forgot to update the version number in the rm -rf command... very minor thing, though!

---

### Post by aikishugyo on 2007-05-23
Thanks for posting the how-to. I followed all the steps (several times, including pasting, to make sure) but get an error when trying skype. Here is my installed 1.4 alpha as per the how-to using sudo.

gernot@hasu:~$ ls -l /usr/bin/skype
-rwxr-xr-x 1 gernot gernot 17545124 2007-05-21 22:41 /usr/bin/skype

When I run it from the command line I get:

gernot@hasu:~$ skype
skype: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

But the library is evidently there:

gernot@hasu:~$ ls -l /usr/lib32/libdbus*
lrwxrwxrwx 1 root root     29 2007-05-24 08:30 /usr/lib32/libdbus-1.so.2 -> /usr/lib32/libdbus-1.so.3.2.0
-rw-r--r-- 1 root root 203808 2007-05-24 08:29 /usr/lib32/libdbus-1.so.3
-rw-r--r-- 1 root root 203808 2007-05-24 08:29 /usr/lib32/libdbus-1.so.3.2.0

What can be wrong here? I suspect permissions, but the lib permissions are identical to those of my other libs in the same directory.

Any hints (including application of cluestick) appreciated.

---

### Post by Cappy on 2007-05-23
I'm not sure on this, your file permissions are exactly the same as on my system!
I have a few suggestions that may (or may not) help.
Try linking again:
```

sudo ln -s /usr/lib32/libdbus-1.so.3 /usr/lib32/libdbus-1.so.2

```

if that doesn't work try this:
```
sudo ln -s /usr/lib32/libdbus-1.so.3 /usr/lib/libdbus-1.so.2
```

Sorry, I can't help you more than this =(

---

### Post by Cappy on 2007-05-23
> **fede said:**
> Thanks again. There is a typo in the last line of code: I think you forgot to update the version number in the rm -rf command... very minor thing, though!

Thanks, I changed it ^^

---

### Post by aikishugyo on 2007-05-24
> **Cappy said:**
> I'm not sure on this, your file permissions are exactly the same as on my system!
I have a few suggestions that may (or may not) help.

/ snipped all the good attempts /

Sorry, I can't help you more than this =(

Sorry mate, all attempts gave identical error :-( Too bad. Will try to install SkePE 1.3 and see what happens.

---

### Post by ivago on 2007-05-24
thx for pointing out  to make the symbolic link,  didn't had todo that with the first alpha from a few weeks ago so this thread fixed the libdbus error during initially  replacing and starting the skype binary.

All by all better than 1.3 but still no video and sms support wich probably won't be fixed in 2007 :(

---

### Post by robert114 on 2007-05-24
Thanx thumbs up mate!

---

### Post by Cappy on 2007-05-24
Added a menu icon on the end of the install.

---

### Post by Zhukov on 2007-05-28
Man, you just saved my day! :D

Whenever you come to Portugal just say something and I'll buy you a drink! :D

8-)

---

### Post by hiazle on 2007-05-28
THANK YOU SOO MUCH!!
Worked like a charm. One question though. Is it this version or am I missing something? I can not start skype minimized to tray. I've checked high and low, but can not find the option in "Preferences"

---

### Post by Cappy on 2007-05-29
> **hiazle said:**
> THANK YOU SOO MUCH!!
Worked like a charm. One question though. Is it this version or am I missing something? I can not start skype minimized to tray. I've checked high and low, but can not find the option in "Preferences"

Unfortunately, no. I checked the configuration file and there is no kind of option to enable this. Skype 1.4 is still missing some options. Hopefully they will have this added by next month. 
Looking through the configuration file I found an option to automatically answer incoming calls! It can't be enabled in the program options so I'm not sure if it will work or not but I'll be able to try it tomorrow.

Thank you for all the kind remarks! =)

---

### Post by hiazle on 2007-05-29
> **Cappy said:**
> Unfortunately, no. I checked the configuration file and there is no kind of option to enable this. 

Has anyone tried to add the option from a configuration file of a prior version. I don't have my prior version of skype installed, but I figured if we check what the option was, we could manually add it to the new config file. Makes sense?

---

### Post by Cappy on 2007-05-29
It's <StartMinimized>1</StartMinimized> in .Skype/shared.xml but it doesn't work in the new skype.

---

### Post by hiazle on 2007-05-29
> **Cappy said:**
> It's <StartMinimized>1</StartMinimized> in .Skype/shared.xml but it doesn't work in the new skype.

Oh, ok.. thanx for trying. Looking forward to another update from skype.

---

### Post by nbayiha on 2007-06-02
Hi Cappy thanks a lot for this thread , i got skype install like a charm.
but i have a question 
what for this step 
```
sudo mv /usr/bin/skype /usr/bin/skype1.3
```
if someone is installing skype for the first time ?:p

anyway thanks a lot for the thread.
Make my life a little bit easier.:-D

---

### Post by Cappy on 2007-06-02
Well skype 1.3 and skype 1.4 can coexist peacefully so I decided to leave skype 1.3 alone in case someone wants to use Skype 1.3 at some point (like me!). 

There isn't any reason for the line if you are installing skype for the first time. Mainly the reason is that I can't mantain separate blocks of code. I would have to have different blocks of code for 32-bit x 64-bit, fresh install, upgrading from 1.3, upgrading from previous 1.4 alpha. It would be a mess!

---

### Post by nbayiha on 2007-06-02
Thanks for the fast answer dude . And actually snth is bothering me  cause i can't find skype icon. i have to look  everywhere even in pixmap there is nothing. 
i have tried even this 
```
gedit ~/Desktop/Skype.desktop

Code:

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Exec=skype
Name=Skype
Icon=/usr/share/pixmaps/skype.png

Save the file, and voila you have a desktop icon. You can drag-and-drop it to add it to the panel. I'm not sure how to add it to the menu though, other than right-clicking and choose to edit the menu, but that wouldn't be command-line copy-and-paste...
``` 
but nothing till now.

---

### Post by Cappy on 2007-06-02
It is at the bottom of my script (It puts it in Applications-->Internet):
```

wget http://boundlesssupremacy.com/Cappy/skypealphaguide/skype.png
wget http://boundlesssupremacy.com/Cappy/skypealphaguide/skypealpha.desktop
sudo mv skype.png /usr/share/icons/
sudo mv skypealpha.desktop /usr/share/applications/
killall gnome-panel

```
- It saves the skype icon to  /usr/share/icons/
If that doesn't work .. try this:
```

rm ~/.local/share/applications/skypealpha.desktop
rm ~/.local/share/applications/skype.desktop
killall gnome-panel

```

---

### Post by nbayiha on 2007-06-02
it was actually in Application internet.

Thanks Dude !!!!!!!!!!!!!!!!!!!!!!!!!!!!! :-D

---

### Post by Sladi on 2007-06-06
Hi! 
I tried the script and nothing happens when I try to start Skype in Appfinder, the menu or in terminal. There are a nice icon and a menu entry in Network installed though. 
I use Xubuntu Feisty 64bit. 
The script said this: 
```
*****Welcome to My-Skype-Installer*****
====--- You will be asked for your root password during installation. ---===
====--- Installation can take some time depending on you internet speed. ---===
[1] continue and install for 64 bit Ubuntu 7.04
[2] Continue and install for 32 bit Ubuntu 7.04
[3] Stop/Exit
Enter your menu choice [1-3]: 1
Please enter your password and wait as My-Skype-Installer downloads some needed files
--20:28:48--  http://www.skype.com/go/getskype-linux-alpha-generic
           => `getskype-linux-alpha-generic'
Resolving www.skype.com... 198.173.5.35
Connecting to www.skype.com|198.173.5.35|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://download.skype.com/linux/skype-alpha-1.4.0.64-generic.tar.bz2 [following]
--20:28:49--  http://download.skype.com/linux/skype-alpha-1.4.0.64-generic.tar.bz2
           => `skype-alpha-1.4.0.64-generic.tar.bz2'
Resolving download.skype.com... 198.63.211.251, 209.0.200.3, 209.0.200.2, ...
Connecting to download.skype.com|198.63.211.251|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11,430,696 (11M) [application/octet-stream]

100%[====================================>] 11,430,696    21.71K/s    ETA 00:00

20:34:15 (34.27 KB/s) - `skype-alpha-1.4.0.64-generic.tar.bz2' saved [11430696/11430696]

mv: `skype-alpha-1.4.0.64-generic.tar.bz2' and `/home/sladi/Desktop/skype-alpha-1.4.0.64-generic.tar.bz2' are the same file
Password:
--20:34:25--  http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb
           => `libqt4-gui_4.2.3-0ubuntu3_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,962,990 (4.7M) [text/plain]

100%[====================================>] 4,962,990     38.11K/s    ETA 00:00

20:36:53 (35.21 KB/s) - `libqt4-gui_4.2.3-0ubuntu3_i386.deb' saved [4962990/4962990]

--20:36:53--  http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb
           => `libqt4-core_4.2.3-0ubuntu3_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,205,696 (1.1M) [text/plain]

100%[====================================>] 1,205,696     42.78K/s    ETA 00:00

20:37:40 (25.86 KB/s) - `libqt4-core_4.2.3-0ubuntu3_i386.deb' saved [1205696/1205696]

--20:37:40--  http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb
           => `libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.7, 204.152.191.39
Connecting to mirrors.kernel.org|204.152.191.7|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34,224 (33K) [text/plain]

100%[====================================>] 34,224        30.05K/s             

20:37:46 (30.03 KB/s) - `libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb' saved [34224/34224]

--20:37:47--  http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb
           => `libdbus-1-3_1.0.2-1ubuntu3_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 269,248 (263K) [text/plain]

100%[====================================>] 269,248       65.24K/s    ETA 00:00

20:37:57 (65.14 KB/s) - `libdbus-1-3_1.0.2-1ubuntu3_i386.deb' saved [269248/269248]

--20:38:04--  http://allyouneedisblog.freehostia.com/skype_icon.png
           => `skype_icon.png'
Resolving allyouneedisblog.freehostia.com... 64.72.119.253
Connecting to allyouneedisblog.freehostia.com|64.72.119.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 64,782 (63K) [image/png]

100%[====================================>] 64,782        42.25K/s             

20:38:10 (42.21 KB/s) - `skype_icon.png' saved [64782/64782]

--20:38:10--  http://allyouneedisblog.freehostia.com/Skype-1.4.0.desktop
           => `Skype-1.4.0.desktop'
Resolving allyouneedisblog.freehostia.com... 64.72.119.253
Connecting to allyouneedisblog.freehostia.com|64.72.119.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 172 [text/plain]

100%[====================================>] 172           --.--K/s             

20:38:11 (13.67 MB/s) - `Skype-1.4.0.desktop' saved [172/172]

gnome-panel: no process killed
./My-Skype-Installer.sh: line 98: /usr/bin/skype: No such file or directory
./My-Skype-Installer.sh: line 59: skype-1.4.0.64/: No such file or directory

```
When I type skype in the terminal this happens: 
```
bash: /usr/bin/skype: No such file or directory

```


edit:
The manual install seems to work, I can use Skype.

---

### Post by fakie_flip on 2007-06-06
It works, but I get these errors.

```
chris@ubuntu:~/.32bitLibs$ LD_LIBRARY_PATH=/home/chris/.32bitLibs skype
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
```

---

### Post by Cappy on 2007-06-06
I have no idea what the phoneline control in the mixer is for. I have it on my Audigy 4 also. It doesn't effect skype though.

---

### Post by Cappy on 2007-06-07
If anyone is interested, you can fix the "errors" that look like:
```

ldconfig: /usr/lib32/libsigc-2.0.so.0 is not a symbolic link

ldconfig: /usr/lib32/libdbus-1.so.3 is not a symbolic link

```
by deleting the file it is complaining about and then creating a soft link with that name to the longer named library that is left.

Here is an example:
```

**/usr/lib32$** ls -la libdbus*
lrwxrwxrwx 1 root root     25 2007-06-06 22:41 libdbus-1.so.2 -> /usr/lib32/libdbus-1.so.3
-rw-r--r-- 1 root root 203808 2007-06-06 22:41 libdbus-1.so.3
-rw-r--r-- 1 root root 203808 2007-06-06 22:41 libdbus-1.so.3.2.0
**/usr/lib32$** sudo rm libdbus-1.so.3
**/usr/lib32$** sudo ln -s libdbus-1.so.3.2.0 libdbus-1.so.3
**/usr/lib32$** ls -la libdbus*
lrwxrwxrwx 1 root root     25 2007-06-06 22:41 libdbus-1.so.2 -> /usr/lib32/libdbus-1.so.3
lrwxrwxrwx 1 root root     18 2007-06-07 15:33 libdbus-1.so.3 -> libdbus-1.so.3.2.0
-rw-r--r-- 1 root root 203808 2007-06-06 22:41 libdbus-1.so.3.2.0

```

ln -s <target> <newlinkname> makes a soft link. It can be used for directories also.

In short, you can it with a
```

cd /usr/lib32
sudo rm libdbus-1.so.3
sudo ln -s libdbus-1.so.3.2.0 libdbus-1.so.3
sudo rm libsigc-2.0.so.0
sudo ln -s libsigc-2.0.so.0.0.0 libsigc-2.0.so.0

```

If this problem happens on a 32-bit machine it would be in the "/usr/lib" directory instead.

---

### Post by macubo on 2007-06-07
I have something similar, always related to ALSA, and I posted something [here]("http://ubuntuforums.org/showpost.php?p=2799137&postcount=18")

---

### Post by Cappy on 2007-06-07
That looks like it may just be a bug in the Skype alpha. You may want to use Skype 1.3 instead

Try this before you do:
```

 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old

```
(reboot)

If that doesn't help at all you can change it back with:
```

 mv -f ~/.asoundrc.old .asoundrc
 mv -f ~/.asoundrc.asoundconf.old ~/.asoundrc.asoundconf

```
(reboot)

I doubt this will fix the gnome-power problem but it may fix those ALSA errors.

---

### Post by macubo on 2007-06-07
thank you for your reply.
I noticed that the gnome.power problem is strictly related to the killall gnome-panel command issued by that script.

The problem with ALSA seem to be a minor issue because sound works quite well locally (i.e. I can hear the voice mail test and the ring bell upon calls), but still haven't tried to phone actually.

PS: have you been able to change your avatar in 1.4 alpha?

[I]Little edit: I don't have any ~/.asoundrc* at all
Have tried the voice call test and seemed to work properly. It is using the integrated mic out-of-the-box[/I]

---

### Post by henriquemaia on 2007-06-15
I followed this howto to install the latest beta and it works great, even on amd64. Thanks a lot.

---

### Post by jasnix on 2007-06-15
I ran into problems installing this using your script Cappy.  It appears they have changed some things in the latest beta release.

I followed your guide and then I just added the following to make it work.

```
wget http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb
sudo dpkg -x libqt4-core_4.2.3-0ubuntu3_i386.deb libqt
sudo dpkg -x libqt4-gui_4.2.3-0ubuntu3_i386.deb libqt
sudo cp libqt/usr/lib/* /usr/lib32/

```
After that I started skype with no problems.

Hope this helps someone.

-Jason

---

### Post by Cappy on 2007-06-15
Edit: I now see there is a new beta. There is a .deb for Feisty Fawn too! I'll update my guide as soon as I get a chance.

---

### Post by Cappy on 2007-06-15
jasnix, thank you! Those lines work well.
This guide is now updated for Skype Beta =)

---

### Post by odiseo77 on 2007-06-16
Hi people, first, thanks to Cappy for the howto; after installing all the necessary libs as instructed, I managed to install skype succesfully. I was so happy that I even made a specific amd64 .deb package and uploaded it to rapidshare (I don't have a server of my own or a website atm). I'm willing to post the link here, but I'm not sure if it's allowed by the forum rules :confused: So, if a mod (or someone else) can give me some advice regarding this doubt, I'll post the link for everyone to download it :)

Greetings.

---

### Post by Cappy on 2007-06-16
"Can I redistribute Skype for Linux?
Yes, you can. For the fine print, read the EULA. In short, please link back to Skype servers for the actual file download (automatic downloading is OK), notify [email]distribution@skype.net[/email] about your intentions, and make the Skype EULA terms clear to your users.
[http://www.skype.com/company/legal/eula/index.html](http://www.skype.com/company/legal/eula/index.html)"

Basically, it says you have to download the binary off their site, but you can redistribute an amd64 script like mine. Is it possible to put my script in an AMD64 deb? That may be the only way.
Edit: Or maybe a AMD64 package with just the libraries in the package and a script to automatically download and install skype.

---

### Post by odiseo77 on 2007-06-16
Hi Cappy. Thanks for clarify this for me (I'm not very familiar with licenses and stuff). Well, I read [http://www.skype.com/company/legal/promote/distributionterms.html](http://www.skype.com/company/legal/promote/distributionterms.html) and it seems I have to contact them first, so I'll e-mail to [email]distribution@skype.net[/email] as stated there, explaining under which mean and circumstances I'm willing to distribute skype (in an autoinstaller .deb package, in this case) and wait for their answer; but, for the terms and conditions of this license it doesn't seem I can do this, so, I had to do what you suggested (a .deb package that automatically download all the necessary libs and the actual package from the skype site (something that would require a bit more of work from me, scripting and such)).

Thanks again for your answer :)

---

### Post by galileon on 2007-06-18
works for me, thanks!

---

### Post by D!mon on 2007-06-20
Thanks a lot, worked like a charm for me. Btw, where are groups in this beta???

---

### Post by munden on 2007-06-28
Thanks for the instructions.  It would have taken me forever to figure that out.  Now I have Skype 1.4.0.74 *mostly* working.  Skype chat is OK and I can receive audio but I cannot send audio.  I have had this AMD64 machine for only two days so I am still finding everything on it.  The mic works - I can echo to the speakers - but nothing gets to Skype.  

Can I buy a clue?

---

### Post by Cappy on 2007-06-28
Try this:
[http://ubuntuforums.org/showthread.php?p=2306168](http://ubuntuforums.org/showthread.php?p=2306168)

---

### Post by fakie_flip on 2007-06-29
Help please. These are the errors I am getting.

```
mike@mike-ubuntu:~$ DISPLAY=:0 skype
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so
```

---

### Post by munden on 2007-06-29
Thank you Cappy.  I hadn't found the "capture control" panel.  Everything works fine now. :D

---

### Post by fakie_flip on 2007-06-29
bump! can someone please help? I even tried getting the newest stable alsa-driver, alsa-utils, alsa-libs and compiling them all. Skype worked fine in 32 bit. What's the problem now? If I can't get this solved, I may go back to 32 bit because I use voice chat a lot to communicate with people.

---

### Post by Gigcsjcx on 2007-07-08
Nice work!:)

---

### Post by sfarber on 2007-07-14
Hello.
I have followed all the instructions in that Thread.
It is working fine. The only problem is that the mic doesn't work.
Does anyone have this problem?

Shay.

---

### Post by b9kline on 2007-07-18
I get a "Call Failed: problem with audio playback" 
any ideas?

---

### Post by Cappy on 2007-07-18
b9kline:
Look at the bottom of the skype Window, it looks like a gear. Click on it and and click "Options".
Goto "Sound Devices". I had to change mine from "Default Device" to "(hw:Audigy2,0)" on each of the drop down boxes. You can press the "Make a Test Sound" and if your Sound Out Dropdown is correct it will play a sound.
If you have a "less capable" sound card you may need to close anything else playing sound (mainly games since they can be OSS).

sfarber:
See: [http://ubuntuforums.org/showthread.php?t=385739](http://ubuntuforums.org/showthread.php?t=385739)

---

### Post by craigsn on 2007-07-18
Hello Cappy, I have Feisty 64 on my machine, with Skype 1.3 installed and working. I tried to find the instructions, if they are here, to upgrade my skype to 1.4. I apologize in advance if they are and I missed them, but can you help me out with the directions to do that? Also, what version do I download, the Feisty version, or something else?

Thanks

---

### Post by Cappy on 2007-07-18
You just follow the directions on the first post for "AMD64 (64-bit) install". [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)
It will "upgrade" your skype. You don't need to download anything yourself.

If you ```
sudo mv /usr/bin/skype /usr/bin/skype-1.3
```
(before you run the code on the first post)
You can run Skype 1.3 after you install the new one with the command "skype-1.3" which I would recommend in case you ever need to use it again.

---

### Post by craigsn on 2007-07-19
Great Cappy, it seems to be working for me. Thanks for the help.

Craig

---

### Post by Alpinist on 2007-07-19
Thanks for the script cappy.  Got it working on Kubuntu Feisty no problems.  Nice to have skype as I couldn't get the mike to work in TeamSpeak with aoss.

---

### Post by vinced on 2007-07-26
Cappy, 
Thanks for the install directions for  Skype and the microphone instructions. They work great.
vinced

---

### Post by suoko on 2007-07-27
The package with static libraries works on dapper.
I don't understand why ubuntu devs don't create packages which just install the complete app under /opt like mainactor uses to do.
I guess this method should be used for firefox, SL, google earth and all those packages which is always better to update.
This method allows you to have latest versions without the need of updating all libs.

---

### Post by Cappy on 2007-07-28
Thanks, I didn't know the static would work with Dapper. I've updated the first post with a dapper install. Something in it may be wrong since I can't check it though.

---

### Post by rajeev1204 on 2007-07-28
I would like to add one more thank you feather to that cappy of yours .;)



Thanks a lot man. 




regards

rajeev

---

### Post by Niedra on 2007-07-28
Followed whole guide until
```
sudo cp libqt/usr/lib/* /usr/lib32/
```
but it shows some error
```
sudo cp libqt/usr/lib/* /usr/lib32/
cp: omitting directory `libqt/usr/lib/qt4'
```
Could anybody help me ?

---

### Post by Cappy on 2007-07-28
Should be ```
sudo cp -R libqt/usr/lib/* /usr/lib32/
``` Thanks, I updated the first post.

---

### Post by nickdngr on 2007-07-29
after initally having followed the instructions on this page: [http://ubuntuforums.org/showthread.php?t=260519](http://ubuntuforums.org/showthread.php?t=260519) (an older thread) and being unsuccessful in installing skype -- but it did install an apps/internet menu location, i clicked the link and followed the directions on the first page of this thread. 

when i click on skype in the apps/internet i get nothing. when i type skype in the terminal i  get this:

skype: error while loading shared libraries: libsigc-2.0.so.0: cannot open shared object file: No such file or directory

it seems to work for everyone else, so what did i do wrong?

--edit--

after continued reading and searching, i had the getlibs tab open and overlooked it (i thought i'd already read it). thanks a lot! completely solved my problem. the only issue i had was i had to run the line as sudo getlibs /usr/bin/skype for it to take. much thanks cappy!

---

### Post by rsambuca on 2007-07-29
Hey Cappy, thanks again!  I have been building a 64bit pure debian OS based on the sid (unstable) branch.  I tried your how-to and it worked perfectly for the debian build as well (I just used the debian sources for the packages).

---

### Post by Bokonon on 2007-07-30
Thanks for the how-to.  1.4 allows me to use sound (internal mic) on my m1210 and the people I talk with say it is fine.

I still can't use the external mic connection, but this is worlds apart from having no sound at all.

---

### Post by saru411 on 2007-07-31
worked perfectly with my 7.04 kubuntu build, on asus p5w dh e6600 64 bit

---

### Post by rsambuca on 2007-08-01
Just a heads-up to everyone that a new update to the 1.4beta just came out.  The best thing for me was that you can now start it minimzed!

---

### Post by Cappy on 2007-08-01
Thanks, I've updated the guide. Changed the version numbers [in the script] to *'s so hopefully it won't break next time they decide to give us a new update.

Edit: Oops I made a typo in the dpkg line

[http://share.skype.com/sites/linux/2007/08/skype_for_linux_14_beta_update.html](http://share.skype.com/sites/linux/2007/08/skype_for_linux_14_beta_update.html)
Key updates include (but not limited to):

* Improved display of anitmated Emoticons
* Audio fixes - relative for mic volume and dmix controls
* Better support for USB audio devices
* SuSE and Mandriva packages!

---

### Post by craigsn on 2007-08-01
Cappy, now that things are moving along on the Skype beta, you might include a section in your initial install how to for people who are upgrading. Unless I am wrong, you do not need to do everything in your script. I'm using amd64, so for me, do I need to do the following lines.
>  (marked with *)
* sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2
cd ~
mkdir skypebetainstall
cd skypebetainstall
wget [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
* wget [http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb)
* wget [http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb)
* wget [http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb)
* wget [http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb)
* dpkg -x libqt4-core_4.2.3-0ubuntu3_i386.deb libqt
* dpkg -x libqt4-gui_4.2.3-0ubuntu3_i386.deb libqt
* dpkg -x libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb libqt
* dpkg -x libdbus-1-3_1.0.2-1ubuntu3_i386.deb libqt
* sudo cp -R libqt/usr/lib/* /usr/lib32/
* sudo ln -s /usr/lib32/libdbus-1.so.3 /usr/lib32/libdbus-1.so.2
* sudo ldconfig /usr/lib32
sudo dpkg -i --force-architecture skype-*.deb
rm -rf ~/skypebetainstall


I followed your script and everything is working fine, but was just wondering if it was all needed.

Thanks for keeping everything current. I certainly appreciate your effort here.

Craig

---

### Post by Cappy on 2007-08-01
No, you don't need any of those lines that are STARed for upgrading. I put an upgrade section on the first post, thanks for the suggestion. 

It had been suggested before but that was back when there wasn't a .deb and it would have been a pain to maintain.

---

### Post by Barney on 2007-08-02
Hi Cappy,

Thanks for all your work on Skype.

My problem:  Dapper installed on Dell Dimension 3000/Intel(R) Celeron(R) CPU 2.40GHz with a USB Phone (Simply Phone/Yealink 1025, supplied from Skype)

Skype 1.3 was working well, except that it froze everything for 5-60 seconds when initially trying to call out, and would then function normally.  Therefore, my attempt at upgrading with your directions on page 1 for Dapper/386.

Install per directions went fine - no errors.  Skype was started with the previous icon left in the panel to ver. 1.4.0.94.  Skype/Options/Sound Devices initially had Default device selected and the initial call-out heard the ringing out in the speakers; call was terminated, and both VOIP USB Phone/(plughw:default,0) and VOIP USB Phone/(hw:default,0) were tried as sound devices, but no sound was detected thru the USB phone on test calls.

Volume control functions (USB Phone selected) showed the Capture driven to the bottom of the scale, and after raising the level, they were driven down again when calls were attempted.  Selecting the Alsa mixer function showed a "red" dot above the USB phone Capture function, but no red-out on the bottom of the scale.

This appears to be a sound problem, as the installation went okay, but I just can't call out using the USB phone.

Suggestions?

Thanks,
Barney

---

### Post by Cappy on 2007-08-02
I'm not sure, I would try asking on the linux skype forums:
[http://forum.skype.com/index.php?showforum=18](http://forum.skype.com/index.php?showforum=18)

---

### Post by Barney on 2007-08-04
Skype Download page shows:

Software requirements

    * Qt 4.2.1+
    * D-Bus 1.0.0
    * libsigc++ 2.0.2
    * libasound2 1.0.12

Dapper is missing all of these.  Is it possible to add these?  &, from where could one get them?

---

### Post by Cappy on 2007-08-04
Use the first post on the first page where it says "Dapper".

---

### Post by Barney on 2007-08-04
Cappy,

I tried the Dapper install (again) from page one of this thread, but again I had no sound on 1.4.  Fortunately, 1.3 had been moved (mv) and I just located it and reverted to 1.3.

As I'm working on my Mom's computer and I'll be leaving tomorrow, I'll leave it on 1.3, until I return in September to give it another try.  Mom is 84 years old and the only one in town with Ubuntu, or any form of linux for that matter.  She loves it: "It just doesn't break!"

Barney

---

### Post by Cappy on 2007-08-04
My apologies, I didn't remember you had posted about the USB phone before. Leaving Skype 1.3 active is the best choice. 1.4 is still incomplete and is actually lacking more functionality than 1.3 (well other than the freezing problem everyone had). The newest version of skype says it added some more USB functionality but I guess it doesn't help with your skype phone. Skype 1.4 is more of a rewrite so that they can abandon some kind of licensing problem they have with 1.3.

Good luck to you.

---

### Post by halfmanhalfbug on 2007-08-06
Hi Cappy. I installed skype 1.4 beta on an HP L2000 (equivalent to Compaq dv2000 I think).It works fine. Thanks for the excellent script. Do the packages downloaded by wget need to be updated by hand? 
And one note about the sound in general in Feisty: it's very quiet even when cranked to 95% (and all other controls such as PC speaker and line-in at 100%). Has anyone else noticed this?
Thanks again,
hmhb

---

### Post by Cappy on 2007-08-06
> **halfmanhalfbug said:**
> Do the packages downloaded by wget need to be updated by hand? 


Only when you upgrade to Gutsy in the future should you need to re-run a skype "install" that will give you the new 32-bit libraries.

> **halfmanhalfbug said:**
>  
And one note about the sound in general in Feisty: it's very quiet even when cranked to 95% (and all other controls such as PC speaker and line-in at 100%). Has anyone else noticed this?
Thanks again,
hmhb

Have you enabled all of your sound controls? If you haven't, click on the speaker icon in the top right corner, Goto Edit-->Preferences and check all the boxes there. See if any of your controls are turned down half way.

It's also possible there is something on either the switches or options tab that could be changed (depends on the sound card).

---

### Post by RavanH on 2007-08-08
Hi,

I had installed Skype following your instructions and it has been running fine for a while. Now for some reason Skype stopped working and I re-installed the latest beta following your instructions again. Only now I get an error when starting Skype from terminal:
```
skype: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
```
But libasound2 is installed according to Synaptic... Any ideas how this came about or rather: how this can be solved?

EDIT: I found one symlink libasound.so.2 in /usr/lib on my system that points to /usr/lib/libasound.so.2.0.0 with root ownership...

---

### Post by Cappy on 2007-08-08
Try
```

sudo apt-get install lib32asound2

```

or

```

sudo apt-get --reinstall install lib32asound2

```

---

### Post by RavanH on 2007-08-08
> **Cappy said:**
> ```

sudo apt-get --reinstall install lib32asound2

```

Thanks Cappy for your quick reply. I tried the above one (because also lib32asound2 was reported as being installed already) but then command skype resulted in ```
skype: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
``` so I reinstalled lib32stdc++ but after that I got ```
skype: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
``` so then I reinstalled lib32z1...

Again, skype returned a new error: ```
skype: error while loading shared libraries: libgthread-2.0.so.0: cannot open shared object file: No such file or directory
``` but now I'm not sure which library I have to (re)install. I found lib32gcc1 installed (but cannot reinstall) and lib32g2c0 and lib32gcj7 not installed... Any of these or am I looking in the wrong place?

A bizarre chain of events. What in the world could have caused these packages to get broken?

---

### Post by Cappy on 2007-08-08
I don't know why your packages are breaking =(
It seems your 32-bit libs have been removed but dpkg still thinks they are installed.

Try
```

sudo apt-get --reinstall install ia32-libs ia32-libs-gtk ia32-libs-sdl

```
since those libraries are from there.


You can also try getlibs and see if it can fix (any/all) of the problems.
It's
```

sudo getlibs /usr/bin/skype
```
in case you forgot

---

### Post by rsambuca on 2007-08-08
Skype released a hotfix update to version 1.4.0.99 today.

---

### Post by Cappy on 2007-08-08
Thanks for the info.
I just checked the new skype and it requires no new dependencies.

---

### Post by RavanH on 2007-08-08
> **Cappy said:**
> You can also try getlibs and see if it can fix (any/all) of the problems.
It's
```

sudo getlibs /usr/bin/skype
```
in case you forgot

Ooops, I forgot indeed :roll:

Here's the output: ```
$ sudo getlibs /usr/bin/skype
Matched library libglib-2.0.so.0 to /feisty/libs/libglib2.0-0
Matched library libgthread-2.0.so.0 to /feisty/libs/libglib2.0-0
The following i386 libraries will be installed:
/feisty/libs/libglib2.0-0
Continue? (y/n) y
Downloading.Installing libraries ...
ravan@ravan-laptop:~$ sudo getlibs /usr/bin/skype
This application isn't missing any dependencies
ravan@ravan-laptop:~$ skype
```

:guitar:

Thanks!

---

### Post by maxrisc on 2007-08-17
Works perfectly on Tribe4 Gutsy 64bit 

Bless you brother :)

---

### Post by rsambuca on 2007-08-17
Now if only skype gets their servers fixed...

---

### Post by penguis on 2007-08-22
Now that I'm not behind my college's firewall, ran through these instructions and the install went like a charm.

BUT...

When running Skype through the gui, nothing happens. Doesn't even show up in System Monitor. When I try to run it in terminal, I get this:

symbol lookup error: /usr/lib/libQtGui.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

Any advice? I'm thinking of running the dls from the beginning of the instructions, only removing with apt-get instead of installing. 

That aside, thanks a mil, Cappy. She's lookin' great!

EDIT: Removed and re-installed all the libraries mentioned at the beginning, Now Skype runs as happy as a clam. On the downside, I killed wine. Bah. Back to the forums!

---

### Post by murgan on 2007-08-26
> **Cappy said:**
> Special Thanks To: Kilz, jasnix

[https://developer.skype.com/LinuxSkype](https://developer.skype.com/LinuxSkype)
August 1, 2007: Skype 1.4.0.94 released.
The skype EULA: [http://www.skype.com/company/legal/eula/index.html](http://www.skype.com/company/legal/eula/index.html)

If you get bad sound quality while using skype beta have your other skype user upgrade their skype also (Windows has v3.2, Mac has v2.6).
After installing Skype 1.4 beta you can run it from your (_Applications-->Internet_) Menu at the top left of your screen.

**Feisty (7.04) and Edgy (6.10) install:**

32-bit AND 64-bit upgrade from a previous Skype 1.4 Beta/Alpha:
```

wget http://www.skype.com/go/getskype-linux-ubuntu
sudo dpkg -i --force-architecture skype-*.deb

```

AMD64 (64-bit) install:
```

sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2
cd ~
mkdir skypebetainstall
cd skypebetainstall
wget http://www.skype.com/go/getskype-linux-ubuntu
wget http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb
dpkg -x libqt4-core_4.2.3-0ubuntu3_i386.deb libqt
dpkg -x libqt4-gui_4.2.3-0ubuntu3_i386.deb libqt
dpkg -x libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb libqt
dpkg -x libdbus-1-3_1.0.2-1ubuntu3_i386.deb libqt
sudo cp -R libqt/usr/lib/* /usr/lib32/
sudo ln -s /usr/lib32/libdbus-1.so.3 /usr/lib32/libdbus-1.so.2
sudo ldconfig /usr/lib32
sudo dpkg -i --force-all skype-*.deb
rm -rf ~/skypebetainstall

```

i386 (32-bit) install:
```

sudo apt-get install libsigc++-2.0-0c2a libdbus-1-3 libqt4-core libqt4-gui
cd ~
mkdir skypebetainstall
cd skypebetainstall
wget http://www.skype.com/go/getskype-linux-ubuntu
sudo dpkg -i skype-*.deb
sudo ln -s /usr/lib/libdbus-1.so.3 /usr/lib/libdbus-1.so.2
sudo rm -rf ~/skypebetainstall

```

**Dapper (Ubuntu 6.04) install:**

Dapper AMD64 (64-bit):
```

sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2
wget http://www.skype.com/go/getskype-linux-static
tar -xvjf skype_static*.tar.bz2
cd skype_static*
sudo mv skype /usr/bin/
sudo mkdir /usr/share/skype
sudo mv sounds /usr/share/skype/
sudo mv icons /usr/share/skype/
sudo mv skype.desktop /usr/share/applications/
cd ..
wget http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.16-3_i386.deb
sudo dpkg -x libsigc++-2.0-0c2a_2.0.16-3_i386.deb libsigc
wget http://security.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-2_0.60-6ubuntu8.1_i386.deb
sudo dpkg -x libdbus-1-2_0.60-6ubuntu8.1_i386.deb libsigc
sudo cp -R libsigc/usr/lib/* /usr/lib32/
sudo ldconfig /usr/lib32
sudo rm -rf skype_static*
sudo rm -rf libsigc

```

Dapper i386 (32-bit):
```

sudo apt-get install libsigc++-2.0-0c2a libdbus-1-2
wget http://www.skype.com/go/getskype-linux-static
tar -xvjf skype_static*.tar.bz2
cd skype_static*
sudo mv skype /usr/bin/
sudo mkdir /usr/share/skype
sudo mv sounds /usr/share/skype/
sudo mv icons /usr/share/skype/
sudo mv skype.desktop /usr/share/applications/
cd ..
sudo rm -rf skype_static*

```

Use "skype" to run skype 1.4 beta.

Works very well. Thanks. Also icon is on the desktop. The only missing item is webcam, which I think skype will resolve the problem soon.:)

---

### Post by DMcCann87 on 2007-09-03
Thank you so much for the guide!  After finishing up, it loaded up like it was always on there. :guitar:

---

### Post by Soarer on 2007-09-16
I'd like to add my thanks too Cappy. Worked like a charm.Thanks for posting this great guide.

---

### Post by paulororke on 2007-09-18
Great notes.  I'd tried for ages to get this working and finally - the RIGHT way....

---

### Post by scrapmetal on 2007-09-19
Thanks, used cut and paste method on first page, no luck, probably me.
Used craigsn on pg 8 with * lines deleted, worked PERFECT.
Thanks for a great resource, that even a newbie can succeed.

An apple does not FALL to the ground, it avoids floating pointlessly around in space.

---

### Post by henriquemaia on 2007-09-20
Works great in Gutsy. Thanks a lot.

---

### Post by fr33d1v3r on 2007-09-26
Thanx Cappy! I am really grateful, it works just fine!

---

### Post by rsambuca on 2007-10-04
Just a heads up to everyone that Skype 1.4 has now gone gold.  They have given it the codename [The Panacea]("http://share.skype.com/sites/garage/2007/10/skype_for_linux_14_gold_panacea.html")

---

### Post by techpr on 2007-10-04
> **rsambuca said:**
> Just a heads up to everyone that Skype 1.4 has now gone gold.  They have given it the codename [The Panacea]("http://share.skype.com/sites/garage/2007/10/skype_for_linux_14_gold_panacea.html")

just Installed 1.4.0.118, works fine...thanks!

---

### Post by HilliBilly on 2007-10-05
cappy, you wrote:

wget [http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb)
wget [http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb)
wget [http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb)
wget [http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb)

i have two questions:

a) i do have (in gutsy) a libsigc++-2.0 (version 2.0.17-2ubuntu2 according to synaptic) and a libdbus-1-3 (version 1.1.1.-3ubuntu2 according to synaptic) installed already, what does this mean?

b) synaptics offers me libqt4-core in newer version (4.3.2.-0ubuntu2) and also a newer version of libqt4-gui (4.3.2.-0ubuntu2), why are you using the older versions?

---

### Post by tzulberti on 2007-10-06
Thanks, this worked for me...

---

### Post by Cappy on 2007-10-07
> **HilliBilly said:**
> 
i have two questions:

a) i do have (in gutsy) a libsigc++-2.0 (version 2.0.17-2ubuntu2 according to synaptic) and a libdbus-1-3 (version 1.1.1.-3ubuntu2 according to synaptic) installed already, what does this mean?

b) synaptics offers me libqt4-core in newer version (4.3.2.-0ubuntu2) and also a newer version of libqt4-gui (4.3.2.-0ubuntu2), why are you using the older versions?

a) You need the 32-bit version of that library - if you are using the 64-bit version then you can only install the 64-bit version of libsigc. If you are using 32-bit you don't need this guide - you can just double click on the skype .deb file and it will install and run everything.

b) Because that is the correct library version for Feisty 64-bit. If you want the version of the libraries that Gutsy uses I suggest using getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by be4truth on 2007-10-07
I installed Skype 1.4 stable on Gutsy beta full updated 64 bit and it works with the Feisty amd64 instructions. Thx a lot!

---

### Post by HilliBilly on 2007-10-07
hi cappy,

thanks for the explanation! i installed getlibs (i really like the concept of your script!) .

now skype is running but freezes after making the first call. i am asking myself if i have done something wrong during installation (i.e. mixing 32~64bit stuff in a stupid way) or this is a 'normal' skype problem (which i have to solve somewhere eles). i did this:

:~/skype_1.4.0.118**$ sudo dpkg -i --force-architecture skype*.deb**
[sudo] password for hjs:
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package skype.
(Reading database ... 115193 files and directories currently installed.)
Unpacking skype (from skype-debian_1.4.0.118-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

my fault :), i forgot to install libqt4-core and libqt4-gui, what i did now via synaptic. then again:

:~/skype_1.4.0.118$ **sudo dpkg -i --force-architecture skype*.deb**
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 115416 files and directories currently installed.)
Preparing to replace skype 1.4.0.118-1 (using skype-debian_1.4.0.118-1_i386.deb) ...
Unpacking replacement skype ...
Setting up skype (1.4.0.118-1) ...

:~/skype_1.4.0.118$ **skype**
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory

:~/skype_1.4.0.118$ **getlibs /usr/bin/skype**
Matched library libQtCore.so.4 to /gutsy/libs/libqt4-core
Matched library libQtDBus.so.4 to /gutsy/libs/libqt4-core
Matched library libQtGui.so.4 to /gutsy/libs/libqt4-gui
Matched library libQtNetwork.so.4 to /gutsy/libs/libqt4-core
Matched library libsigc-2.0.so.0 to /gutsy/libs/libsigc++-2.0-0c2a
The following i386 libraries will be installed:
/gutsy/libs/libqt4-core
/gutsy/libs/libqt4-gui
/gutsy/libs/libsigc++-2.0-0c2a
Continue? (y/n) y
Downloading... Installing libraries ...
New depedencies have been detected:
libdbus-1.so.3
Matched library libdbus-1.so.3 to /gutsy/libs/libdbus-1-3
The following i386 libraries will be installed:
/gutsy/libs/libdbus-1-3
Continue? (y/n) y
Downloading. Installing libraries ...

:~/skype_1.4.0.118$ **skype**
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : legacy
Killed

or maybe ... someone else could help me?

---

### Post by Cappy on 2007-10-07
Top google search shows that your error occurs for 32-bit programs when you need to re-install your video card drivers.
[http://ubuntuforums.org/showthread.php?p=3466965](http://ubuntuforums.org/showthread.php?p=3466965)

---

### Post by HilliBilly on 2007-10-07
sorry, do not really understand your answer resp. the thread you mentioned, maybe i am still too much of a newbie.

do you mean i have to re-install my video card driver for my ATI Technologies Inc RV570 [Radeon X1950 Pro] to be able to use skype? i saw that update-manager wants to install a newer version anyway ... and doing this update, would this solve my video card driver problem (i.e. is updating equal to re-installing in this case)?

---

### Post by JJNova on 2007-10-08
I just wanted to say thank you for this. I was messing around with trying to make 32 libs work, and was having one hell of a time.

Thank you very much.

---

### Post by ddave01 on 2007-10-08
Cappy
Many thanks for showing the way in Skype install to AMD 64 bit
ddave01

---

### Post by exz on 2007-10-11
worked great, thanks

---

### Post by saru411 on 2007-10-14
hello cappy

my girl friend decided she wanted to install skype on my system but does not know anything about linux/ubuntu. she went to the skype website and dl the linux skype there. she then clicked yes she says. i have no idea what she did and im a little annoyed she touched my system but thats not important here. i have since tried installing your 64 bit skype from this thread and have run into a problem. well, im not sure that its a problem because i have not tried skype yet. the problem is that there werte errors while installing. i've included the install output here. please tell me how to continue. one thing that might have caused the issue is that i copy and paste you entire script in one copy/paste. should i have done it line by line? 

> saru@Lain:~$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs-gtk is already the newest version.
ia32-libs-sdl is already the newest version.
lib32asound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
saru@Lain:~$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs-gtk is already the newest version.
ia32-libs-sdl is already the newest version.
lib32asound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
saru@Lain:~$ cd ~
saru@Lain:~$ mkdir skypebetainstall
saru@Lain:~$ cd skypebetainstall
saru@Lain:~/skypebetainstall$ wget [http://www.skype.com/go/getskype-linux-ubuntu--14:11:40--](http://www.skype.com/go/getskype-linux-ubuntu--14:11:40--)  [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
           => `getskype-linux-ubuntu'
Resolving [www.skype.com](www.skype.com)... 204.9.163.136
Connecting to www.skype.com|204.9.163.136|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://download.skype.com/linux/skype-debian_1.4.0.118-1_i386.deb](http://download.skype.com/linux/skype-debian_1.4.0.118-1_i386.deb) [following]
--14:11:40--  [http://download.skype.com/linux/skype-debian_1.4.0.118-1_i386.deb](http://download.skype.com/linux/skype-debian_1.4.0.118-1_i386.deb)
           => `skype-debian_1.4.0.118-1_i386.deb'
Resolving download.skype.com... 198.173.5.10, 198.173.5.11, 209.0.200.3, ...
Connecting to download.skype.com|198.173.5.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13,384,906 (13M) [application/octet-stream]

100%[====================================>] 13,384,906   411.54K/s    ETA 00:00

14:12:10 (441.19 KB/s) - `skype-debian_1.4.0.118-1_i386.deb' saved [13384906/13384906]

saru@Lain:~/skypebetainstall$ wget [http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb)
--14:12:10--  [http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb)
           => `libqt4-core_4.2.3-0ubuntu3_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.7, 204.152.191.39
Connecting to mirrors.kernel.org|204.152.191.7|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,205,696 (1.1M) [text/plain]

100%[====================================>] 1,205,696    366.39K/s    ETA 00:00

14:12:13 (365.48 KB/s) - `libqt4-core_4.2.3-0ubuntu3_i386.deb' saved [1205696/1205696]

saru@Lain:~/skypebetainstall$ wget [http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb)
--14:12:13--  [http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb)
           => `libqt4-gui_4.2.3-0ubuntu3_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,962,990 (4.7M) [text/plain]

100%[====================================>] 4,962,990    377.86K/s    ETA 00:00

14:12:28 (338.46 KB/s) - `libqt4-gui_4.2.3-0ubuntu3_i386.deb' saved [4962990/4962990]

saru@Lain:~/skypebetainstall$ wget [http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb)
--14:12:28--  [http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb)
           => `libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.7, 204.152.191.39
Connecting to mirrors.kernel.org|204.152.191.7|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34,224 (33K) [text/plain]

100%[====================================>] 34,224       110.09K/s             

14:12:28 (110.07 KB/s) - `libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb' saved [34224/34224]

saru@Lain:~/skypebetainstall$ wget [http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb)
--14:12:28--  [http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb)
           => `libdbus-1-3_1.0.2-1ubuntu3_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 269,248 (263K) [text/plain]

100%[====================================>] 269,248      293.33K/s             

14:12:29 (292.71 KB/s) - `libdbus-1-3_1.0.2-1ubuntu3_i386.deb' saved [269248/269248]

saru@Lain:~/skypebetainstall$ dpkg -x libqt4-core_4.2.3-0ubuntu3_i386.deb libqt
saru@Lain:~/skypebetainstall$ dpkg -x libqt4-gui_4.2.3-0ubuntu3_i386.deb libqt
saru@Lain:~/skypebetainstall$ dpkg -x libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb libqt
saru@Lain:~/skypebetainstall$ dpkg -x libdbus-1-3_1.0.2-1ubuntu3_i386.deb libqt
saru@Lain:~/skypebetainstall$ sudo cp -R libqt/usr/lib/* /usr/lib32/
saru@Lain:~/skypebetainstall$ sudo ln -s /usr/lib32/libdbus-1.so.3 /usr/lib32/libdbus-1.so.2
saru@Lain:~/skypebetainstall$ sudo ldconfig /usr/lib32
saru@Lain:~/skypebetainstall$ sudo dpkg -i --force-all skype-*.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package skype.
(Reading database ... 114267 files and directories currently installed.)
Unpacking skype (from skype-debian_1.4.0.118-1_i386.deb) ...
dpkg: skype: dependency problems, but configuring anyway as you request:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
Setting up skype (1.4.0.118-1) ...

Configuration file `/etc/dbus-1/system.d/skype.conf', does not exist on system.
Installing new config file as you request.
saru@Lain:~/skypebetainstall$ rm -rf ~/skypebetainstall
saru@Lain:~/skypebetainstall$ 


thanks for your time and help

---

### Post by Soarer on 2007-10-14
OK. Two problems so far.

1. You are installing 32 bit Skype - is that what you wanted to do?
2. Paste the commands one at a time.

Your girlfriend is doing things 'the windows way'. I often think that creates a lot of support problems down the line.

---

### Post by saru411 on 2007-10-14
skype is only 32 bit, so yes im installing the 32 bit skype. i'm well aware my girlfriend is doing things the incorrect way. i got into a fight over this telling her not to install things on my computer. i will try installing by going line by line now and return with the result. and if it is to be installed line by line why doesnt it say so in the instructions or broken down into line by line quotes?

---

### Post by saru411 on 2007-10-14
> saru@Lain:~/skypebetainstall$ sudo dpkg -i --force-all skype-*.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 114381 files and directories currently installed.)
Preparing to replace skype 1.4.0.118-1 (using skype-debian_1.4.0.118-1_i386.deb) ...
Unpacking replacement skype ...
dpkg: skype: dependency problems, but configuring anyway as you request:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
Setting up skype (1.4.0.118-1) ...


again i got the same error while installing line by line. so this script was ment to be copied and pasted as a whole. installing line by line isnt an issue. now does any one know how to get my system back to preskyped so i can try installing this script or do you know how to get libqt4-core and libqt4-gui?

---

### Post by Cappy on 2007-10-14
Those errors you are getting are normal (you don't need those dependencies it is warning you about - ignore them). You can copy and paste the whole chunk of code into the terminal. There isn't any need to copy line by line.

Also, your girlfriend couldn't mess anything up with a 32-bit debian file anyway. It won't work for a 64-bit system.

Your skype should work when you run "skype" in the terminal.

---

### Post by Soarer on 2007-10-14
Those libraries are both available in the (Gutsy) repos.

The problem with cutting & pasting a series of commands is that you don't see the errors as they happen so you can stop and think about what went wrong before carrying on. The commands worked for me on 64bit Gutsy and I have functioning Skype, but maybe I am not trusting enough - I did them one at a time and monitored the output as it went along.

---

### Post by RoboRutt on 2007-10-14
Heya All, 

Just thought I would pop my $0.02 worth in ... Did the first method (top of thread) but got some library/ dependency issues.  I am using Fiesty on a Q6600, and found this worked:

First: Original code posted by Cappy

```

wget http://www.skype.com/go/getskype-linux-ubuntu
sudo dpkg -i --force-architecture skype-*.deb

```

Then, you get  the error :

dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

So just follow up with the code:

```

sudo apt-get install -f

```

This seems to work for me, done it on two Fiesty machines now... Happy to get comment/critique from those more geek than me.

Cheers, 
:)RR

---

### Post by Surge on 2007-10-14
Sorry, I don't have the patience to read through the full thread, but I had an ultra-simple approach to running sky in just a few seconds.

1. Install all 32bit libraries from repository
2. Download latest Skype 1.4 static package
3. Extract the package to /opt
4. sudo ln -sf /opt/skype_static-1.4.0.118 skype
5. Put small script into /opt/bin (which is on _my_ path (set through /etc/environment)), I call it skype
```
#!/bin/bash
linux32 /opt/skype/skype
```
6. sudo chmod +x /opt/bin/skype
Add link to /opt/bin/skype in any place/way you want.

Others might prefer /usr/local or other places, for me /opt sits on a separate partition and can be used by both 64 and 32 bit linux installs.

---

### Post by Cappy on 2007-10-14
> **Soarer said:**
> Those libraries are both available in the (Gutsy) repos.

The problem with cutting & pasting a series of commands is that you don't see the errors as they happen so you can stop and think about what went wrong before carrying on. The commands worked for me on 64bit Gutsy and I have functioning Skype, but maybe I am not trusting enough - I did them one at a time and monitored the output as it went along.

You ignore the error about the missing libraries because it is actually warning about missing the 64-bit version of those libraries even though the correct 32-bit are installed. It doesn't matter that you get dependency errors when force installing a 32-bit deb.

---

### Post by saru411 on 2007-10-15
> **Cappy said:**
> You ignore the error about the missing libraries because it is actually warning about missing the 64-bit version of those libraries even though the correct 32-bit are installed. It doesn't matter that you get dependency errors when force installing a 32-bit deb.

the error is what i was worried about. if its normal then i have no issues. maybe you could add a small note about the errors being normal under the 64 bit terminal script you have. i know it would have saved me all of these posts. i ran skype last night and it works fine. thanks for the help and my girlfriend is off the hook =)

---

### Post by YoG%*@ on 2007-10-17
thanks a lot for this howto!

the AMD64 bit installation instructions worked perfectly and the install was painless and i had no troubles at all getting skype to work. 

mux

---

### Post by Cappy on 2007-10-20
> **Cappy said:**
> Special Thanks To: Kilz, jasnix

[https://developer.skype.com/LinuxSkype](https://developer.skype.com/LinuxSkype)
August 1, 2007: Skype 1.4.0.94 released.
The skype EULA: [http://www.skype.com/company/legal/eula/index.html](http://www.skype.com/company/legal/eula/index.html)

If you get bad sound quality while using skype beta have your other skype user upgrade their skype also (Windows has v3.2, Mac has v2.6).
After installing Skype 1.4 beta you can run it from your (_Applications-->Internet_) Menu at the top left of your screen.

**Feisty (7.04) and Edgy (6.10) install:**

32-bit AND 64-bit upgrade from a previous Skype 1.4 Beta/Alpha:
```

wget http://www.skype.com/go/getskype-linux-ubuntu
sudo dpkg -i --force-architecture skype-*.deb

```

**AMD64 (64-bit) install:**
```

sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2
cd ~
mkdir skypebetainstall
cd skypebetainstall
wget http://www.skype.com/go/getskype-linux-ubuntu
wget http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb
dpkg -x libqt4-core_4.2.3-0ubuntu3_i386.deb libqt
dpkg -x libqt4-gui_4.2.3-0ubuntu3_i386.deb libqt
dpkg -x libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb libqt
dpkg -x libdbus-1-3_1.0.2-1ubuntu3_i386.deb libqt
sudo cp -R libqt/usr/lib/* /usr/lib32/
sudo ln -s /usr/lib32/libdbus-1.so.3 /usr/lib32/libdbus-1.so.2
sudo ldconfig /usr/lib32
sudo dpkg -i --force-all skype-*.deb
rm -rf ~/skypebetainstall

```

**32-bit install (If you don't know what you have use this):**

[http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)



**Dapper (Ubuntu 6.04) install:**

Dapper AMD64 (64-bit):
```

sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2
wget http://www.skype.com/go/getskype-linux-static
tar -xvjf skype_static*.tar.bz2
cd skype_static*
sudo mv skype /usr/bin/
sudo mkdir /usr/share/skype
sudo mv sounds /usr/share/skype/
sudo mv icons /usr/share/skype/
sudo mv skype.desktop /usr/share/applications/
cd ..
wget http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.16-3_i386.deb
sudo dpkg -x libsigc++-2.0-0c2a_2.0.16-3_i386.deb libsigc
wget http://security.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-2_0.60-6ubuntu8.1_i386.deb
sudo dpkg -x libdbus-1-2_0.60-6ubuntu8.1_i386.deb libsigc
sudo cp -R libsigc/usr/lib/* /usr/lib32/
sudo ldconfig /usr/lib32
sudo rm -rf skype_static*
sudo rm -rf libsigc

```

Dapper i386 (32-bit):
```

sudo apt-get install libsigc++-2.0-0c2a libdbus-1-2
wget http://www.skype.com/go/getskype-linux-static
tar -xvjf skype_static*.tar.bz2
cd skype_static*
sudo mv skype /usr/bin/
sudo mkdir /usr/share/skype
sudo mv sounds /usr/share/skype/
sudo mv icons /usr/share/skype/
sudo mv skype.desktop /usr/share/applications/
cd ..
sudo rm -rf skype_static*

```

Use "skype" to run skype 1.4 beta.

I am changing the post above to use my script getlibs instead. Otherwise Gutsy and Edgy users will end up with Feisty libraries.

---

### Post by steefjeqv on 2007-10-20
Thanks Cappy,

Works great on my new Gutsy 64 bit install.

Greetings,
Steven

---

### Post by nikitavfx on 2007-10-24
One more vote for the static version. Much simpler install. On a Mac Pro, Skype was freezing with the debian version of Skype (grabbed all the libs with getlibs).

Here's how it worked for me:

[http://macprolinux.blogspot.com/2007/10/skype-on-64-bit-gutsy.html](http://macprolinux.blogspot.com/2007/10/skype-on-64-bit-gutsy.html)

---

### Post by spellico on 2007-10-29
thanks so much for this! wish all the how to were this clear. couldn't install the newer version and the 1.3 kept freezing in dapper. It worked perfectly!!!

---

### Post by jonah1980 on 2007-10-29
hi i used getlibs to install skype and it worked great, it runs ok etc but my microphone doesn't pick up any sound whatever i try... can anyone help?

---

### Post by Portent on 2007-10-29
Worked great for 64-bit install. I originally had an error, then went back to check all the commands.  I was missing a few letters of one of the http addresses.  It looked like this:

[http://www.boundlesssupremacy.com/Ca...tlibs-all.deb](http://www.boundlesssupremacy.com/Ca...tlibs-all.deb)

but was supposed to be this:

[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)

Who knows, I'm probably the only one to do that.  In any case, skype is up and working great.

---

### Post by Cappy on 2007-10-29
> **Portent said:**
> Worked great for 64-bit install. I originally had an error, then went back to check all the commands.  I was missing a few letters of one of the http addresses.  It looked like this:

[http://www.boundlesssupremacy.com/Ca...tlibs-all.deb](http://www.boundlesssupremacy.com/Ca...tlibs-all.deb)

but was supposed to be this:

[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)

Who knows, I'm probably the only one to do that.  In any case, skype is up and working great.

Thanks, I didn't notice that - I'll find a way to fix it.

Edit: Fixed, thanks.

---

### Post by enetic on 2007-10-30
> **Garyu said:**
> Works great, but no desktop/panel/menu icon/starter... You should add that to make the guide complete. :)

if you rightclick on a panel and choose "add to panel" you can add "application launcher" its the best way...

---

### Post by tarekeldeeb on 2007-10-30
THANKS :popcorn:

I tried many HowTOs .. this works perfectly ..

I have Ubuntu 7.10 / AMD64

---

### Post by lamnk on 2007-11-03
> **Surge said:**
> Sorry, I don't have the patience to read through the full thread, but I had an ultra-simple approach to running sky in just a few seconds.

1. Install all 32bit libraries from repository
2. Download latest Skype 1.4 static package
3. Extract the package to /opt
4. sudo ln -sf /opt/skype_static-1.4.0.118 skype
5. Put small script into /opt/bin (which is on _my_ path (set through /etc/environment)), I call it skype
```
#!/bin/bash
linux32 /opt/skype/skype
```
6. sudo chmod +x /opt/bin/skype
Add link to /opt/bin/skype in any place/way you want.

Others might prefer /usr/local or other places, for me /opt sits on a separate partition and can be used by both 64 and 32 bit linux installs.
Work perfectly ! Thanks

---

### Post by ZERO_SHIFT on 2007-11-03
Thanks for the how-to!

---

### Post by ZERO_SHIFT on 2007-11-03
I wonder though will Skype have 64bit versions soon? How come 64bit OSX leopard has support?

---

### Post by mauris on 2007-11-05
wow. you are genius. I was straggling with the installation for some now. THANKS A LOT.  :guitar:

---

### Post by Kittyhawk on 2007-11-06
Thanks Cappy it does work properly :)

---

### Post by Simpele on 2007-11-07
How about Skype 2 beta?

I'm getting > skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

---

### Post by Cappy on 2007-11-07
Skype with video! zomg!
run
> cd; sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs /usr/bin/skype

I'll add a 2.0 guide to the tutorial in a few minutes.

Edit: Added to the front post.

---

### Post by Dripbagulhos on 2007-11-07
> **Cappy said:**
> Skype with video! zomg!
run


I'll add a 2.0 guide to the tutorial in a few minutes.

Edit: Added to the front post.

Hi! I followed the tutorial (Gutsy AMD64 + Skype Beta). It worked fine. Skype is now on gnome menu, it works fine for audio, but it shows the message "No devices found" (see attachment). My webcam works with camorama...

Any clue? :-)

Thanks!

---

### Post by tighem on 2007-11-07
Skype for me is not working with a standard mic and not at all with bluetooth. On BT it's complaining about the following:

ALSA lib ../../../src/pcm/pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_bluetooth.so

---

### Post by Cappy on 2007-11-07
> **Dripbagulhos said:**
> Hi! I followed the tutorial (Gutsy AMD64 + Skype Beta). It worked fine. Skype is now on gnome menu, it works fine for audio, but it shows the message "No devices found" (see attachment). My webcam works with camorama...

Any clue? :-)

Thanks!

Same issue - I'll let you know when I find a solution.

---

### Post by Cappy on 2007-11-07
> **tighem said:**
> Skype for me is not working with a standard mic and not at all with bluetooth. On BT it's complaining about the following:

ALSA lib ../../../src/pcm/pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_bluetooth.so

Mic issues are beyond the scope of this tutorial. You'll need to find out what sound card you have and search on the forums for it to find a solution to enable the mic (usually painless). You may want to check here first: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

As for bluetooth you should try
```
sudo apt-get install bluez-utils
```

---

### Post by Dripbagulhos on 2007-11-08
Hi Cappy and friends!

I don't know if I am in the right direction, but i coded:

```
$ dmesg | grep skype
[ 2702.663602] ioctl32(skype:10278): Unknown cmd fd(13) cmd(80685600){t:'V';sz:104} arg(f423e064) on /dev/video0
[ 2702.663612] ioctl32(skype:10278): Unknown cmd fd(13) cmd(803c7601){t:'v';sz:60} arg(f423e0cc) on /dev/video0
```

And, sure, the device exists:

```
$ ls /dev/vid*
/dev/video0
```

My guess: poor implementation of video on skype. I don't know why they don't open their code!! If their programers have no time (and I not talking about capacity!!) to mantain the Linux version in the same level of windows, just let the people who is capable, do it! Am I so wrong?

:-)

---

### Post by Cappy on 2007-11-08
> **Dripbagulhos said:**
> Hi Cappy and friends!

I don't know if I am in the right direction, but i coded:

```
$ dmesg | grep skype
[ 2702.663602] ioctl32(skype:10278): Unknown cmd fd(13) cmd(80685600){t:'V';sz:104} arg(f423e064) on /dev/video0
[ 2702.663612] ioctl32(skype:10278): Unknown cmd fd(13) cmd(803c7601){t:'v';sz:60} arg(f423e0cc) on /dev/video0
```

And, sure, the device exists:

```
$ ls /dev/vid*
/dev/video0
```

My guess: poor implementation of video on skype. I don't know why they don't open their code!! If their programers have no time (and I not talking about capacity!!) to mantain the Linux version in the same level of windows, just let the people who is capable, do it! Am I so wrong?

:-)

I've been trying to get it to work with a skype dev. It seems to be a kernel module (gspca) that was compiled incorrectly in Ubuntu's 64-bit kernel. It is a 64-bit only problem.

Unfortunately, I don't know anything about the kernel so I'm having problems getting the module to run correctly after compiling from the author's source page.

Remember that it *is* still beta .. I'm sure this is going to be one of the first things they find a solution to.

---

### Post by kiepmad on 2007-11-08
How I installed skype 2.0 beta!
N.B.: I had skype 1.4 and 32bit libraries installed before.

Download skype from official page, the ubuntu feisty package.
```
http://www.skype.com/intl/en/download/skype/linux/beta/choose/
```

open terminal
```

cd /location/of/skype
sudo dpkg --force-architecture -i skype-debian_2.0.0.13-1_i386.deb

```

After installation, I used
```
ldd /usr/bin/skype
``` 
to find missing libraries

I found that the libXss.so.1 was missing.

What I made:
```
getlibs -32 libXss.so.1
```

That was it, it's working, but does not my recognize my webcam. ;)

---

### Post by kr0n1x on 2007-11-08
the link of skype in the first post isn't correct.
it download the 1.4 version instead of newer beta ...(or i did some error doing the command in terminal?)

---

### Post by Cappy on 2007-11-08
> **kr0n1x said:**
> the link of skype in the first post isn't correct.
it download the 1.4 version instead of newer beta ...(or i did some error doing the command in terminal?)

The links are correct. There is a code section to install 1.4 and then there is a code section to install 2.0

---

### Post by Cuppa-Chino on 2007-11-08
> **kiepmad said:**
> 
I found that the libXss.so.1 was missing.

What I made:
```
getlibs -32 libXss.so.1
```


maybe I am daft but that does nothing on mine...

```
desktop:/usr/lib32$ getlibs -32 libXss.so.1
Usage: getlibs /path/to/binary

```

**and then you reinstall getlibs and you are done!**  [as described here]("http://ubuntuforums.org/showpost.php?p=2849759&postcount=1")

---

### Post by Cappy on 2007-11-08
If you run the script on the first post it should upgrade getlibs to the newest version.

Also, if you decide not to use the first post I would use
```
sudo getlibs /usr/bin/skype
```
so that it would solve any other missing dependencies.

---

### Post by Dripbagulhos on 2007-11-08
> **Cappy said:**
> I've been trying to get it to work with a skype dev. It seems to be a kernel module (gspca) that was compiled incorrectly in Ubuntu's 64-bit kernel. It is a 64-bit only problem.

Unfortunately, I don't know anything about the kernel so I'm having problems getting the module to run correctly after compiling from the author's source page.

Remember that it *is* still beta .. I'm sure this is going to be one of the first things they find a solution to.

So, let's wait for the fix! :-)

Thank you for the patience and good will!

---

### Post by saw24 on 2007-11-09
> **Dripbagulhos said:**
> ```
$ dmesg | grep skype
[ 2702.663602] ioctl32(skype:10278): Unknown cmd fd(13) cmd(80685600){t:'V';sz:104} arg(f423e064) on /dev/video0
[ 2702.663612] ioctl32(skype:10278): Unknown cmd fd(13) cmd(803c7601){t:'v';sz:60} arg(f423e0cc) on /dev/video0
```

And, sure, the device exists:

```
$ ls /dev/vid*
/dev/video0
```

Same here. But: Cam works with Ekiga.

---

### Post by Dripbagulhos on 2007-11-09
Yes! I've forgotten to mention it. My cam works with camorama and Ekiga.

---

### Post by kstan_79 on 2007-11-09
No luck for my ubuntu gutsy 64bit, I'd installthe skype successfully, I can start the skype as well.

after login then the skype not responding, when I click option it freeze too.
In console I can't see any error message. However I saw the network utilization high, and it keep sending www[sync] package.

I install skype with getlibs.

---

### Post by kr0n1x on 2007-11-09
Anyway i can look my Windows Xp friends with cam...i can look their cam...
but they can't look me...my cam isn't found in skype.
in other software like amsn, ekiga, mplayer, vlc..the webcam works well

edit: in gutsy 64 bit

---

### Post by HellBoyz77 on 2007-11-09
Same here, the cam (stk11xx) is recognized in camorama and ekiga but not in skype.

Gutsy 64bit, nvidia proprietary driver, compiz fusion enabled.

This is the log:

Nov  9 19:18:44 HBuntuMobile kernel: [ 5088.346523] ioctl32(skype:26462): Unknown cmd fd(34) cmd(80685600){t:'V';sz:104} arg(f437c064) on /dev/video0
Nov  9 19:18:44 HBuntuMobile kernel: [ 5088.346538] ioctl32(skype:26462): Unknown cmd fd(34) cmd(803c7601){t:'v';sz:60} arg(f437c0cc) on /dev/video0
Nov  9 19:19:09 HBuntuMobile kernel: [ 5112.821501] ioctl32(skype:26462): Unknown cmd fd(34) cmd(80685600){t:'V';sz:104} arg(f437c064) on /dev/video0
Nov  9 19:19:09 HBuntuMobile kernel: [ 5112.821515] ioctl32(skype:26462): Unknown cmd fd(34) cmd(803c7601){t:'v';sz:60} arg(f437c0cc) on /dev/video0
Nov  9 19:19:31 HBuntuMobile kernel: [ 5135.070493] ioctl32(skype:483): Unknown cmd fd(13) cmd(80685600){t:'V';sz:104} arg(f4307064) on /dev/video0
Nov  9 19:19:31 HBuntuMobile kernel: [ 5135.070794] ioctl32(skype:483): Unknown cmd fd(13) cmd(803c7601){t:'v';sz:60} arg(f43070cc) on /dev/video0

---

### Post by Dripbagulhos on 2007-11-09
> **kstan_79 said:**
> No luck for my ubuntu gutsy 64bit, I'd installthe skype successfully, I can start the skype as well.

after login then the skype not responding, when I click option it freeze too.
In console I can't see any error message. However I saw the network utilization high, and it keep sending www[sync] package.

I install skype with getlibs.

Although we all have this issue with Gutsy AMD64 and webcam on skype, I had no other problem with this beta. Today I have made some calls to regular phones, cel phones and my skype friends. The sound is clear, no lags, etc. I have put it on my "Sessions" to auto start with every login, and no problems either: it is starting quickly and always conecting to skype server.

I think I will try these beta on the other machine (i386) witch has the same version of Ubuntu (7.10) but is 32 bits. I suppose that on that machi it should work...

Thanks for everyone's reports!

---

### Post by hellmet on 2007-11-09
> **Dripbagulhos said:**
> Hi! I followed the tutorial (Gutsy AMD64 + Skype Beta). It worked fine. Skype is now on gnome menu, it works fine for audio, but it shows the message "No devices found" (see attachment). My webcam works with camorama...

Any clue? :-)

Thanks!
Same problem..

Thanks a ton for the tutorial though.. This will mean no more windows for voice..

---

### Post by Emblem Parade on 2007-11-10
Amazing work, Cappy. getlibs is an excellent idiot-proof tool.

I just wonder if you or anyone else knows how to uninstall Skype if it's installed this way (using skype-install.deb)? It doesn't, of course, appear as an apt package.

Also, if someone discovers a way to get webcams working with Skype 2.0 Beta on AMD64, be sure to let us starving users know!

---

### Post by Cappy on 2007-11-10
To remove skype you ```
sudo dpkg -r skype
```

---

### Post by snkmad on 2007-11-10
Skype installed with no problems here on Gutsy amd64.
But when i go to Options, under Soud Devices , and make a test call, i cant hear me.
I know my mic is working, but how do i configure it for skype?

---

### Post by Mr. Knuffke on 2007-11-10
Same problem that others have spoken to on this thread.  Skype Beta 2.0 in Gutsy on a 64 bit AMD.  Audio is fine.  Webcam is not found.  Webcam works in everything else that I have ever used it with.

---

### Post by snkmad on 2007-11-10
Actually everythings working fine.
My mic problem? It was just disabled on gnome-volume-manager...

---

### Post by Dripbagulhos on 2007-11-10
Hi guys!

More news about the beta. In the machine running Ubuntu 64, I can make calls an see video with no problem. In the machine running Ubuntu 32, if I don't start my webcam (if I don't send video, only receive) that works as fine as Ubuntu 64, but if I start sending my video, after about two minutes skype crashes.

So, it is not only the 64 bits version that has problems. The 32 bits also have problems!!

---

### Post by mabovo on 2007-11-15
Trying to install it got this:

felipe@felipe-desktop:~$ sudo getlibs /usr/bin/skype
Unknown distro, using Debian Unstable (sid) settings
/usr/bin/getlibs: 123: shopt: not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Fatal Error: /emul/ia32-linux does not exist
Your distro may not have been detected properly
Detected as: x86_64 debian unstable
No LSB modules are available.
Distributor ID: Ubuntu Description: Ubuntu hardy (development branch) Release: 8.04 Codename: hardy
felipe@felipe-desktop:~$

Although I have 1.4 running perfect, how can I put this version with webcam to work ?

---

### Post by mabovo on 2007-11-15
felipe@felipe-desktop:~$ sudo apt-get install ia32-linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-linux
felipe@felipe-desktop:~$ getlibs -32 libXss.so.1
Unknown distro, using Debian Unstable (sid) settings
/usr/bin/getlibs: 123: shopt: not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Fatal Error: /emul/ia32-linux does not exist
Your distro may not have been detected properly
Detected as: x86_64 debian unstable
No LSB modules are available.
Distributor ID: Ubuntu Description: Ubuntu hardy (development branch) Release: 8.04 Codename: hardy
felipe@felipe-desktop:~$ sudo getlibs /usr/bin/skype
Unknown distro, using Debian Unstable (sid) settings
/usr/bin/getlibs: 123: shopt: not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Fatal Error: /emul/ia32-linux does not exist
Your distro may not have been detected properly
Detected as: x86_64 debian unstable
No LSB modules are available.
Distributor ID: Ubuntu Description: Ubuntu hardy (development branch) Release: 8.04 Codename: hardy
felipe@felipe-desktop:~$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
Note, selecting ia32-libs instead of ia32-libs-gtk
ia32-libs is already the newest version.
Note, selecting ia32-libs instead of ia32-libs-sdl
ia32-libs is already the newest version.
lib32asound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
felipe@felipe-desktop:~$ wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
--12:21:10--  [http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
           => `getlibs-all.deb'
Resolving boundlesssupremacy.com... 209.123.149.151
Connecting to boundlesssupremacy.com|209.123.149.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,412 (5.3K) [text/plain]
Server file no newer than local file `getlibs-all.deb' -- not retrieving.

felipe@felipe-desktop:~$ sudo dpkg -i getlibs-all.deb
(Reading database ... 112489 files and directories currently installed.)
Preparing to replace getlibs 1.06 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (1.06) ...
felipe@felipe-desktop:~$ sudo getlibs /usr/bin/skype
Unknown distro, using Debian Unstable (sid) settings
/usr/bin/getlibs: 123: shopt: not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Fatal Error: /emul/ia32-linux does not exist
Your distro may not have been detected properly
Detected as: x86_64 debian unstable
No LSB modules are available.
Distributor ID: Ubuntu Description: Ubuntu hardy (development branch) Release: 8.04 Codename: hardy
felipe@felipe-desktop:~$ getlibs -32 libXss.so.1
Unknown distro, using Debian Unstable (sid) settings
/usr/bin/getlibs: 123: shopt: not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Fatal Error: /emul/ia32-linux does not exist
Your distro may not have been detected properly
Detected as: x86_64 debian unstable
No LSB modules are available.
Distributor ID: Ubuntu Description: Ubuntu hardy (development branch) Release: 8.04 Codename: hardy
felipe@felipe-desktop:~$ 

And nothing yet.

---

### Post by Cappy on 2007-11-15
I've updated the script. Try again.

---

### Post by mabovo on 2007-11-15
I think that now is ok.

(Reading database ... 112985 files and directories currently installed.)
Preparing to replace getlibs 1.06 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (1.07) ...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: regarding skype-install.deb containing skype:
 skype-static conflicts with skype
  skype (version 2.0.0.13-1) is to be installed.
dpkg: warning - ignoring conflict, may proceed anyway !
(Reading database ... 112985 files and directories currently installed.)
Preparing to replace skype 2.0.0.13-1 (using skype-install.deb) ...
Unpacking replacement skype ...
Replaced by files in installed package skype-static ...
Setting up skype (2.0.0.13-1) ...
This application isn't missing any dependencies
felipe@felipe-desktop:~$ 


Just one doubt:

Skype 1.4.0.118 is running on my system. What's the trick to make 2.0.0.13 work ?

---

### Post by Cappy on 2007-11-15
> **mabovo said:**
> 
Skype 1.4.0.118 is running on my system. What's the trick to make 2.0.0.13 work [with a webcam]?

There isn't a solution yet

---

### Post by mabovo on 2007-11-15
Should I remove 1.4 ?

When I type skype on terminal it loads 1.4 :confused:

---

### Post by mabovo on 2007-11-15
My webcam is Logitech Quickcam pro 5000 and it's running very well without lucview stuff.

Skype name: marcos.bovolon

Should have a thread like this on hardy development when devs release a new kernel version, don't you think that ?

---

### Post by Cappy on 2007-11-15
It looks like this line is the problem:
skype-static conflicts with skype

```
sudo apt-get remove skype-static
```
or
```
sudo dpkg -r skype-static
```
may remove that.

I'm not sure where you installed that from. 

If you moved the files manually in to the /usr/bin folder you will need to manually delete them.

```
whereis skype
``` can help you figure out where the 1.4 binary is, if all else fails.

---

### Post by mabovo on 2007-11-15
felipe@felipe-desktop:~$ whereis skype
skype: /usr/bin/skype /usr/share/skype /usr/share/man/man1/skype.1.gz
felipe@felipe-desktop:~$

I didn't move any file.

---

### Post by mabovo on 2007-11-15
felipe@felipe-desktop:~$ dmesg | grep skype
felipe@felipe-desktop:~$ sudo apt-get remove skype-static
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  skype-common dbus-x11
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  skype-static
0 upgraded, 0 newly installed, 1 to remove and 69 not upgraded.
Need to get 0B of archives.
After unpacking 18.8MB disk space will be freed.
Do you want to continue [Y/n]?

Of course don't.

The 69 not upgraded refers to Xorg 1.4 that I prefer to wait until Hardy alpha 1

---

### Post by Axx83 on 2007-11-19
Hello, it works very well on mine too BUT, how do I uninstall skype 2 beta installed with this script ? That's either useful when skype 64 bit comes out and for those whu used skype installed through automatix (bad bad thing that automatix).

Please answer me !

---

### Post by Cappy on 2007-11-19
To remove skype installed from the script on the first post you use 
```
sudo dpkg -r skype
```

but if you run the script on the first post when a new skype comes out it will replace your old skype anyway. In other words, you don't need to remove your old skype to upgrade if you installed it from the first post of this tutorial or from a .deb file manually.

---

### Post by Axx83 on 2007-11-19
yes the script upgrades too, but if a 64bit version comes out you probably want to install from scratch, and btw I had skype installed with Automatix and I think it's cleaner that I uninstall both then install just skype beta with your script.

---

### Post by darqfiber on 2007-11-19
After running this script and installing skype 2.0 beta (thanks for that!) 

Now my VMWare Workstation won't run any 64bit Virtual Machines as it complains that it's not a 64 bit processor.

I am working on it but I think that some libraries were overwritten in /usr/lib with 32 bit versions and that's why it thinks its no longer a 64bit machine :) -- I am leaning towards to qt libs but so far my efforts have been fruitless. 

I'll take any suggestions, best guesses or advice that anyone is willing to offer - surely there must be some way for VMWare Workstation and Skype 2.0 beta to peacefully co-exist?

Thanks

DF

---

### Post by crjackson on 2007-11-19
> **darqfiber said:**
> After running this script and installing skype 2.0 beta (thanks for that!) 

Now my VMWare Workstation won't run any 64bit Virtual Machines as it complains that it's not a 64 bit processor.

I am working on it but I think that some libraries were overwritten in /usr/lib with 32 bit versions and that's why it thinks its no longer a 64bit machine :) -- I am leaning towards to qt libs but so far my efforts have been fruitless. 

I'll take any suggestions, best guesses or advice that anyone is willing to offer - surely there must be some way for VMWare Workstation and Skype 2.0 beta to peacefully co-exist?

Thanks

DF

I had a couple of things die on me.  I just reinstalled the app from synaptic and it all works fine now.  I can only guess reinstalling pulled in the proper libs and corrected the problem.

---

### Post by Cappy on 2007-11-19
See if ```
sudo apt-get install libqt4-core libqt4-gui libsigc++-2.0-0c2a libdbus-1-3
```
fixes the problem.

If that doesn't fix the problem I would try reinstalling the program.

Let me know if/how you fix it so if there is a problem I can fix it. Also I should point out that getlibs doesn't meddle with the 64-bit libraries at all. I can't think of any way that installing the 32-bit libs should break anything.

---

### Post by darqfiber on 2007-11-20
[http://vegdave.wordpress.com/2007/03/22/notes-on-installing-skype-on-ubuntuamd64/](http://vegdave.wordpress.com/2007/03/22/notes-on-installing-skype-on-ubuntuamd64/)

The comments in this blog entry seem to indicate the same or similiar problem - I am no closer to a solution alas. I may have to re-install the OS.

DF

---

### Post by HilliBilly on 2007-11-20
hi, 

my skype always freezes when i am trying to do a second phonecall. 

had this problem some time ago and didn't find a solution. today removed my old installation of skype and reinstalled 64-bit skype 2.0 with cappy's howto in first post. but it stills freezes! starting skype from terminal shows no error messages.

i am on 64-bit gutsy (2.6.22-14-generic). during installation i accepted to install a i386 library (marked it red), was this correct? 


me@centurion1:~$ **whereis skype**
skype: /usr/bin/skype /usr/share/skype

me@centurion1:~$ **sudo dpkg -r skype**
(Reading database ... 153820 files and directories currently installed.)
Removing skype ...

me@centurion1:~$ **cd; sudo apt-get install ia32-libs lib32asound2; cd ~/Desktop; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -N -O skype-install.deb [http://www.skype.com/go/getskype-linux-beta-ubuntu;](http://www.skype.com/go/getskype-linux-beta-ubuntu;) sudo dpkg -i getlibs-all.deb; sudo dpkg -i --force-all skype-install.deb; sudo getlibs /usr/bin/skype; cd ~**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manual installed.
lib32asound2 is already the newest version.
lib32asound2 set to manual installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.22-12 libglitz-glx1 linux-headers-2.6.22-12-generic
  libglitz1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
--17:47:24--  [http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
           => `getlibs-all.deb'
Resolving boundlesssupremacy.com... 209.123.149.151
Connecting to boundlesssupremacy.com|209.123.149.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,402 (5.3K) [text/plain]

100%[====================================>] 5,402         --.--K/s             

17:47:24 (39.37 KB/s) - `getlibs-all.deb' saved [5402/5402]

--17:47:24--  [http://www.skype.com/go/getskype-linux-beta-ubuntu](http://www.skype.com/go/getskype-linux-beta-ubuntu)
           => `skype-install.deb'
Resolving [www.skype.com](www.skype.com)... 204.9.163.136
Connecting to www.skype.com|204.9.163.136|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://download.skype.com/linux/skype-debian_2.0.0.13-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.13-1_i386.deb) [following]
--17:47:25--  [http://download.skype.com/linux/skype-debian_2.0.0.13-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.13-1_i386.deb)
           => `skype-install.deb'
Resolving download.skype.com... 209.0.200.3, 130.117.72.89, 209.0.200.2
Connecting to download.skype.com|209.0.200.3|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14,933,294 (14M) [application/octet-stream]

100%[====================================>] 14,933,294   167.77K/s    ETA 00:00

17:48:35 (209.20 KB/s) - `skype-install.deb' saved [14933294/14933294]

(Reading database ... 153708 files and directories currently installed.)
Preparing to replace getlibs 1.06 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (1.07) ...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package skype.
(Reading database ... 153708 files and directories currently installed.)
Unpacking skype (from skype-install.deb) ...
Setting up skype (2.0.0.13-1) ...
Matched library libXss.so.1 to /gutsy/libs/libxss1
[COLOR="Red"]The following i386 libraries will be installed:
/gutsy/libs/libxss1
Continue? (y/n) y[/COLOR]
Downloading. Installing libraries ...
me@centurion1:~$

---

### Post by Cappy on 2007-11-20
All of that is correct. 

You may want to stop skype and run
```
rm -rf ~/.Skype
```
in case you have some bad skype settings that are causing the freezing.

Also, I would try ```
sudo apt-get install --reinstall ia32-libs lib32asound2
``` since it was set to manual install and there might be some 32-bit libraries that you don't have.

I've heard that for some users the solution to skype freezing was to use the static binary install. There is a post of code on how to install 1.4 static on the first post labeled as "Dapper LTS (Ubuntu 6.04) install:".

---

### Post by rsambuca on 2007-12-05
Just an FYI.  An update to the latest Skype beta has been released. [ Details of bugfixes and download link can be found here]("http://share.skype.com/sites/garage/2007/12/skype_20_beta_for_linux_update.html").

---

### Post by crjackson on 2007-12-06
Will the current install code posted on page one install the latest deb or does it have to be modified?

---

### Post by Cappy on 2007-12-06
The 2.0 code on the front page will install the newest one. 

I have outgoing video working too. I'll try to write a good tutorial for it tomorrow.

---

### Post by crjackson on 2007-12-06
> **Cappy said:**
> The 2.0 code on the front page will install the newest one. 

I have outgoing video working too. I'll try to write a good tutorial for it tomorrow.

Cool, thanks...

On a system where the previous beta was installed using your page 1 info, can I just run the thing over again to upgrade to the latest version?

---

### Post by Cappy on 2007-12-06
Yes, it says this on the front page
**64-bit install (or upgrade) skype 2.0 (with video):**

---

### Post by tekhawk on 2007-12-08
anyone want to point me to a good higher res cheap linux friendly webcam now lol

i think i have a cheap logitech messenger camera right now low low res looks bad on skype i just had it to test video on linux now i need a real one

or a way to make the xbox 360 camera work on linux LOL

---

### Post by aikishugyo on 2007-12-10
Cheap? How much is that? less than US$100? I'd say go with any of the 2007-model Quickcams from Logitech. The Pro 5000 or Pro 9000 work well and are nicely portable.

---

### Post by Duffy on 2007-12-13
I get this message every time I try to start Skype after following the install for 32 bit Skype beta on a 64 bit system:

Aborted (core dumped)

---

### Post by Cappy on 2007-12-13
> **Duffy said:**
> I get this message every time I try to start Skype after following the install for 32 bit Skype beta on a 64 bit system:

Aborted (core dumped)

Try removing your local ~/.Skype files
```
rm -rf ~/.Skype
```

If that doesn't work you will probably want to use the statically linked version of Skype.

---

### Post by aikishugyo on 2007-12-17
Not that this is anything new, but I've noticed---I'm on *Hardy* now BTW---that sometimes libraries are renewed or deleted during upgrades and* SkyPE* bombs out (the exact library that is no longer found is seen if you type  *skyp*e a the command line prompt and watch the output).

In that case, I check to see whether the required library is in /usr/lib32. I also check if Cappy's *getlibs-all* package can deduce that it needs it. If not, then I have to fetch it myself, using a search to find out where to download the library package from for Ubuntu distributions on 1386 systems. I then use *dpkg -i --force-all* to install the *deb* pacakge.

Next, I check in /usr/lib where the new lib was installed (this is now incorrectly installed in the 64-bit lib dir) and whart links were created. I then duplicate these in the /usr/lib32 dir, and reinstall the 64-bit packages.

Thereafter, *SkyPE* once again works....

---

### Post by Cappy on 2007-12-17
Updates are deleting libraries that getlibs installed for skype in /usr/lib32? Is it a specific update such as an update to ia32-libs?

Does ```
sudo getlibs /usr/bin/skype
``` not work in this situation?

Did you try ```
sudo getlibs -32 missinglibrary.so.number
```
?

---

### Post by mips on 2007-12-18
```
wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
```

Why can you not use a trusted source for this ?

I for one am very wary of installing things from non-trusted sources.

---

### Post by Cappy on 2007-12-18
> **mips said:**
> ```
wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
```

Why can you not use a trusted source for this ?

I for one am very wary of installing things from non-trusted sources.

What would you suggest? The script is currently on my own (shared) website, hosted by Site5.

---

### Post by averyh on 2007-12-18
Fixed the first problem i posted.  I am now getting...

avery@avery-desktop:~$ skype
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory
avery@avery-desktop:~$

I saw some previous post about some shared libraries.  Was going to start seeing if I could get a library through some commands, but with being so new to this, I didn't want to mess anything up.  Any ideas.

Thanks,
Avery

---

### Post by Cappy on 2007-12-19
> **averyh said:**
> Fixed the first problem i posted.  I am now getting...

avery@avery-desktop:~$ skype
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory
avery@avery-desktop:~$

I saw some previous post about some shared libraries.  Was going to start seeing if I could get a library through some commands, but with being so new to this, I didn't want to mess anything up.  Any ideas.

Thanks,
Avery

You need to run one of the scripts on the first post.
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)
You probably want the section labeled "64-bit install (or upgrade) skype 2.0 (with video):"

If it still isn't working you should post the output of ```
sudo getlibs /usr/bin/skype
```

---

### Post by Locutux on 2007-12-19
I installed it, and it works perfectly fine. The only problem is that it shows no icon. :S

---

### Post by superid on 2007-12-23
> **Cappy said:**
> The 2.0 code on the front page will install the newest one. 

I have outgoing video working too. I'll try to write a good tutorial for it tomorrow.

Hi,
Are you saying there's a solution to the "No devices found" issue?
I'm running Ubuntu 64-bit and am having the same problem, I'd greatly appreciate a solution.

Thanks in advance,
 Leo

---

### Post by kr0n1x on 2007-12-23
> **superid said:**
> Hi,
Are you saying there's a solution to the "No devices found" issue?
I'm running Ubuntu 64-bit and am having the same problem, I'd greatly appreciate a solution.

Thanks in advance,
 Leo

same situation

---

### Post by Cappy on 2007-12-23
> **superid said:**
> Hi,
Are you saying there's a solution to the "No devices found" issue?
I'm running Ubuntu 64-bit and am having the same problem, I'd greatly appreciate a solution.

Thanks in advance,
 Leo

the link you are looking for is on the front page
[http://ubuntuforums.org/showthread.php?t=634393](http://ubuntuforums.org/showthread.php?t=634393)

---

### Post by superid on 2007-12-23
Cappy, you're a legend.
Haven't tried the procedure yet, but I'm pretty confident I'll get it working with the newly provided info.

Huge thanks for both threads, happy holidays!

---

### Post by mandragor on 2007-12-28
Great howto - It worked perfectly! 

This should be a part of the ubuntu wiki, much easier to follow the one (albeit long) command in
this thread than the 7-step guide over at:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

My only critique, or rather suggestion to improve it, is to make getlibs install needed libraries
without asking (perhaps with a --force parameter) so no user-interaction is needed..

Keep up the good work Cappy, this is life-saver! :)

---

### Post by Cappy on 2007-12-29
> **mandragor said:**
> Great howto - It worked perfectly! 

This should be a part of the ubuntu wiki, much easier to follow the one (albeit long) command in
this thread than the 7-step guide over at:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

My only critique, or rather suggestion to improve it, is to make getlibs install needed libraries
without asking (perhaps with a --force parameter) so no user-interaction is needed..

Keep up the good work Cappy, this is life-saver! :)

Thanks, I've already implemented this in the new getlibs as --yes or -yes option as --force will be used for something else. It's not the main download yet since there is some stuff I need to do such as documentation.

---

### Post by MidasTouchBR on 2008-01-05
Hi guys

I'm kinda new here, but I hope I can be helpful. I've just rebuilt the Skype 2.0.0.27-1 beta package with the 32-bit libraries that are not available for installation on Ubuntu 7.10 amd64 (the ones that you are getting through **getlibs** I guess) and changed the dependencies for not being necessary the "dpgk -i --force-architecture" method.

I tested it in a HP Pavilion 2225 Notebook with Ubuntu 7.10 Gutsy AMD64. Everything worked fine, including the webcam.

It still depends on lib32asound2, ia32-libs, libc6-i386, lib32stdc++6, lib32gcc1, which you can get by

**sudo apt-get install lib32asound2 ia32-libs libc6-i386 lib32stdc++6 lib32gcc1**

Since this is the first time that I do this, I would be thankful if somebody could try the package and send me report:[EMAIL="guilherme.augustus@gmail.com"][COLOR="Blue"] guilherme.augustus@gmail.com[/COLOR][/EMAIL]

Here you can download it:

[[COLOR="Blue"]skype-ubuntu_2.0.0.27-1_gutsy-amd64.deb[/COLOR]]("http://w14.easy-share.com/14069021.html")

If you already have the library packages mentioned above, or installed them as explained,  just do a **dpkg -i skype-ubuntu_2.0.0.27-1_gutsy-amd64.deb** inside the directory that you saved the file.

See ya!!!

---

### Post by prince_niceguy on 2008-01-15
thanks man.... worked like breeze..

---

### Post by fcorourke on 2008-01-16
Hi I ran the script and did not see any errors . It even suggested I run "wget --help" -- which gives the command line options. BUT when I type skype into command line it says  "command not found". Oh it was Skype 2.0. What do I need to try?  I am a newbie -- but would really like to stick with 64 bit -- although my brother asked WHY I even installed 64 bit. I just thought it had to be better with a 64 bit machine, although old AMD 3800. Thanks in advance.

      Fred

---

### Post by Cappy on 2008-01-16
Sounds like skype didn't install for some reason. Are you running 6.06 Dapper?

Try copying and pasting this in to the terminal again:
> sudo apt-get install ia32-libs lib32asound2; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-beta-ubuntu;](http://www.skype.com/go/getskype-linux-beta-ubuntu;) sudo dpkg -i getlibs-all.deb; sudo dpkg -i --force-all skype-install.deb; sudo getlibs /usr/bin/skype; cd ~

If that still gives the  "wget --help" error try
> 
wget boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget [http://www.skype.com/go/getskype-linux-beta-ubuntu;](http://www.skype.com/go/getskype-linux-beta-ubuntu;) sudo dpkg -i getlibs-all.deb; sudo dpkg -i --force-all skype-debian_2.0.0.27-1_i386.deb; sudo getlibs /usr/bin/skype;


Let me know how it goes please!

P.S. You should probably post ALL output

---

### Post by Sepher0 on 2008-01-19
> sepher@Skynet:~$ skype
skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory
sepher@Skynet:~$ 
sepher@Skynet:~$ getlibs -32 libXss.so.1
/usr/bin/getlibs: line 106: getopt: command not found
sepher@Skynet:~$ sudo getlibs -32 libXss.so.1
[sudo] password for sepher:
/usr/bin/getlibs: line 106: getopt: command not found
sepher@Skynet:~$ sudo getlibs -32 libXss.so.1
/usr/bin/getlibs: line 106: getopt: command not found
sepher@Skynet:~$ /usr/lib32$ getlibs -32 libXss.so.1
bash: /usr/lib32$: No such file or directory
sepher@Skynet:~$ sudo getlibs /usr/bin/skype
/usr/bin/getlibs: line 106: getopt: command not found
sepher@Skynet:~$ skype
skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory
sepher@Skynet:~$ sudo getlibs /usr/bin/skype
/usr/bin/getlibs: line 106: getopt: command not found
sepher@Skynet:~$ getlibs /usr/bin/skype
/usr/bin/getlibs: line 106: getopt: command not found
sepher@Skynet:~$ sudo getlibs -32 missinglibrary.so.number
/usr/bin/getlibs: line 106: getopt: command not found

I tried a few things in the thread but I keep getting the same error, 
what is "/usr/bin/getlibs: line 106: getopt: command not found"

on ubuntu 7.10

---

### Post by Cappy on 2008-01-19
getopt is in util-linux, an essential package

Try
```
sudo apt-get install util-linux ia32-libs
```
or
```
sudo apt-get install --reinstall util-linux
```

---

### Post by Sepher0 on 2008-01-19
I would of tried that,  but I Just went with a fresh reinstall of 7.10,  it worked after reinstalling ubuntu :)


which was good for me any way cause now I can dual boot xp. (I had messed it up the first time)

THANKS!

---

### Post by sepia-shots on 2008-01-20
Top work. Worked for me. I added the icon in by right clicking and using the add launcher option.

Many thanks, excellent post.

---

### Post by umatix on 2008-01-25
HELLO !

Been trying since forever to inatall skype on edgy.

Can't seem to find appropriate help.

Seems I have dependancy issues I can't fix.

I have tried all three solutions in your post and no luck. the last two end the same way.

Here is the output from the last example:


-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i getlibs-all.deb; sudo dpkg -i --force-all skype-install.deb; sudo getlibs /usr/bin/skype; cd ~
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
--03:26:43--  [http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
           => `getlibs-all.deb'
Resolving boundlesssupremacy.com... 209.123.149.151
Connecting to boundlesssupremacy.com|209.123.149.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6,436 (6.3K) [text/plain]
Server file no newer than local file `getlibs-all.deb' -- not retrieving.

--03:26:43--  [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
           => `skype-install.deb'
Resolving [www.skype.com](www.skype.com)... 204.9.163.136
Connecting to www.skype.com|204.9.163.136|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://download.skype.com/linux/skype-debian_1.4.0.118-1_i386.deb](http://download.skype.com/linux/skype-debian_1.4.0.118-1_i386.deb) [following]
--03:26:44--  [http://download.skype.com/linux/skype-debian_1.4.0.118-1_i386.deb](http://download.skype.com/linux/skype-debian_1.4.0.118-1_i386.deb)
           => `skype-install.deb'
Resolving download.skype.com... 130.117.72.42, 130.117.72.43
Connecting to download.skype.com|130.117.72.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13,384,906 (13M) [application/octet-stream]

100%[=============================================================================>] 13,384,906   941.22K/s    ETA 00:00

03:27:00 (797.59 KB/s) - `skype-install.deb' saved [13384906/13384906]

(Reading database ... 111149 files and directories currently installed.)
Preparing to replace getlibs 2.02 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (2.02) ...
dpkg - warning: downgrading skype from 2.0.0.27-1 to 1.4.0.118-1.
(Reading database ... 111149 files and directories currently installed.)
Preparing to replace skype 2.0.0.27-1 (using skype-install.deb) ...
Unpacking replacement skype ...
dpkg: skype: dependency problems, but configuring anyway as you request:
 skype depends on libasound2 (>> 1.0.12); however:
  Version of libasound2 on system is 1.0.11-7ubuntu3.
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
Setting up skype (1.4.0.118-1) ...
/usr/bin/getlibs: line 574: unexpected EOF while looking for matching `''
/usr/bin/getlibs: line 594: syntax error: unexpected end of file
iman@iman-laptop:~$ 

Would apriciate any assistance as i really need it on my laptop and can't upgrade to feisty as its impossible to mount peripherals including CDROM and external HD

Thanks

---

### Post by Cappy on 2008-01-26
You need to enable your extra repositories so you can install ia32-libs.
Here is a link on how to do this in Edgy:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

Make sure you ```
sudo apt-get update
```

As for the syntax error, I did find a syntax error in my code. I left out a " ' " that I could not find until I checked it out with emacs.

Next, try installing this getlibs:
[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-2.03-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-2.03-all.deb)

and run
```
sudo getlibs /usr/bin/skype
```

and let me know how it goes.

Getlibs depends on your repositories being correct so if ia32-libs won't install getlibs may not work either.

---

### Post by D!mon on 2008-01-30
I'm running Ubuntu Gutsy amd64. I've never had problems with  installing with skype on my computer, but I just realized that I can't change my Skype Picture and neither can see anyone's Picture :( My Co-worker who uses the same version of Skype (2.0.0.27) with Ubuntu Gutsy i386 doesn't have any problems with the Skype Picture. 
Does anyone know how to fix this? Should I install some additional libraries?

---

### Post by damoisture on 2008-01-31
Just installed it on my 7.10 x86-64 install. Works like charm, even got a menu entry under Apps>Internet. Thank you so much for the tutorial!

---

### Post by sunseeker888 on 2008-02-01
Hi guys

I an absolute beginner on Linux. Which version of skype shall I download for uduntu. I have 64 bit Ubuntu 7.10 installed? I keep getting wrong architecture i386, from package insatller after installing ubuntu Feisty Fawn (7.04). Please help:confused:

---

### Post by Cappy on 2008-02-01
Look on the first post and install **64-bit install (or upgrade) skype 2.0 (with video):**

All instructions are on the first post.

---

### Post by sunseeker888 on 2008-02-01
Thanks for your reply, I nstalled skype, but it's  a weird version. There ain't any options for  sms or to  see my account for skype out?

Is that correct? On linux :confused:skype version no sms or account lookup details possible? Sorry for  the dumb questions, i know bollox about Linux.

---

### Post by sunseeker888 on 2008-02-01
Hi Cappy



That was the link and command below, I used from your post. Shame I need skype to send sms all day as it's much faster using a keyboard. hope i do not have to go back to windows.




wget boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget [http://www.skype.com/go/getskype-linux-beta-ubuntu;](http://www.skype.com/go/getskype-linux-beta-ubuntu;) sudo dpkg -i getlibs-all.deb; sudo dpkg -i --force-all skype-debian_2.0.0.27-1_i386.deb; sudo getlibs /usr/bin/skype;

---

### Post by zirtik on 2008-02-02
> cd; sudo apt-get install ia32-libs lib32asound2; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-beta-ubuntu;](http://www.skype.com/go/getskype-linux-beta-ubuntu;) sudo dpkg -i getlibs-all.deb; sudo dpkg -i --force-all skype-install.deb; sudo getlibs /usr/bin/skype; cd ~


Thank you, I tried to install Skype 2.0 and it worked great including the webcam support on Hardy with an AMD64! The only thing I did was to install getlibs before copying your commands and pasting them on the terminal. 

For details on getlibs please see this thread:

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Corvair on 2008-02-03
Hello Cappy
Nice work you are doing.
I am using Gutsy 7.10 on a new 64 bit install with an Intel processor.
I have tried installing Skype 2.0 as per your first post without success.  When I try downloading I am told sorry wrong architecture. So I tried all the command lines and this is what I get.
What am I doing wrong?




0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
claude@claude-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
claude@claude-desktop:~$ wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
--19:37:02--  [http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
           => `getlibs-all.deb'
Resolving boundlesssupremacy.com... 209.123.149.151
Connecting to boundlesssupremacy.com|209.123.149.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6,458 (6.3K) [text/plain]
Server file no newer than local file `getlibs-all.deb' -- not retrieving.

claude@claude-desktop:~$ wget -O skype-install.deb
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
claude@claude-desktop:~$ sudo dpkg -i getlibs-all.deb
(Reading database ... 112237 files and directories currently installed.)
Preparing to replace getlibs 2.04 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (2.04) ...
claude@claude-desktop:~$ sudo dpkg -i --force-all skype-install.deb
dpkg: error processing skype-install.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-install.deb
claude@claude-desktop:~$ sudo getlibs /usr/bin/skype
The file "/usr/bin/skype" does not exist
Usage: getlibs /path/to/binary
       getlibs -l i386librarytoinstall.so
       getlibs -p i386packagename
       getlibs -w www.website.com/i386package.deb
       getlibs -i /home/root/i386package.deb
       See 'man getlibs' for more commands
claude@claude-desktop:~$ cd ~
claude@claude-desktop:~$

---

### Post by Cappy on 2008-02-03
You didn't copy it correctly. Just copy the whole block of code into the terminal.

---

### Post by Corvair on 2008-02-03
As you can see I am not a programmer annalist

I enterred the block and this time it has instakked and in the right place.

Thanks a million.

---

### Post by Meneldir on 2008-02-04
Thanks! Worked perfectly...

---

### Post by mwpmwjcp on 2008-02-05
Thanks man, this rules, you've let me see my 15 month old daughter 1300 miles away!

---

### Post by MinceMedallion on 2008-02-06
Thanks - the install for Ubuntu 7.10 x64 worked perfectly. Skype appears in Gnome menu. Fixed a big headache!

---

### Post by kirenpillay on 2008-02-07
Thanks! Worked first time!:)

---

### Post by Timokl on 2008-02-17
Thanks! Everything worked for me now!

Timo

---

### Post by buntu_hugenewbie11 on 2008-02-18
So I installed 2.0 on Gutsy 64 following the directions.
Unfortunately the sound is unstable from my end when I call other users or use the echo server. I have tried all sorts of configurations via Alsa mixer but none worked. Instead I was thinking of uninstalling 2.0 and using Cappy's directions to install 1.4.
My question is: How do I go about uninstalling 2.0 correctly so that I can install 1.4?

---

### Post by Cappy on 2008-02-18
```
sudo dpkg -r skype
```

and then use the Skype 1.4 script.

---

### Post by hp_dv2k_guy on 2008-02-18
I have a strange problem
I have skype running now but it doesnt sign-in or anything

however when i use 'sudo skype' it runs perfectly :confused:

---

### Post by Cappy on 2008-02-18
Copy and paste this into the terminal
```
sudo chown  $USER:$USER -R ~/.Skype
```

If that doesn't work run skype in the terminal and post the output.

---

### Post by hp_dv2k_guy on 2008-02-19
you had the right idea
there were some files that were not in my ownership, not the directory itsef but some files in a subdirectory

THANKS

---

### Post by tonywhelan on 2008-02-21
Thank you for this script. I used it recently to install Skype 2 Beta on my AMD64 and it ran perfectly.

Built a new Gutsy install tonight and tried installing the same way (pasted commands into terminal) and it fails repeatedly.

Says:
Failed to download file [http://security.ubuntu.com/ubuntupool/main/q/qt4-x11/libqt4-core_4.3.2-0ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntupool/main/q/qt4-x11/libqt4-core_4.3.2-0ubuntu3.2_i386.deb)
The mirrors do not have the requested file or there is no internet connection
Failed to download file [http://security.ubuntu.com/ubuntupool/main/q/qt4-x11/libqt4-gui_4.3.2-0ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntupool/main/q/qt4-x11/libqt4-gui_4.3.2-0ubuntu3.2_i386.deb)
The mirrors do not have the requested file or there is no internet connection
No packages to install

I notice it says "ubuntupool" whereas the actual web path should be "ubuntu/pool" but I can't see where that error comes from.

I can live without Skype right now, but thought the problem may be bigger than just me so best to mention it.

cheers

---

### Post by Cappy on 2008-02-21
> **tonywhelan said:**
> Thank you for this script. I used it recently to install Skype 2 Beta on my AMD64 and it ran perfectly.

Built a new Gutsy install tonight and tried installing the same way (pasted commands into terminal) and it fails repeatedly.


Your /etc/apt/sources.list probably has something like ```
http://security.ubuntu.com/ubuntu
``` instead of ```
http://security.ubuntu.com/ubuntu/
``` (slash on the end) in it.

You can fix that manually with ```
gksudo gedit /etc/apt/sources.list
```

Edit: and then apt-update

---

### Post by tonywhelan on 2008-02-21
> **Cappy said:**
> Your /etc/apt/sources.list probably has something like ```
http://security.ubuntu.com/ubuntu
``` instead of ```
http://security.ubuntu.com/ubuntu/
``` (slash on the end) in it.

You can fix that manually with ```
gksudo gedit /etc/apt/sources.list
```

Edit: and then apt-update

Yes, that was it, thanks very much.

Tony

---

### Post by muadnu on 2008-02-23
I upgraded to the beta version, and my integrated webcam on a Dell Vostro 1400 works perfectly. But every time I try a call, using a usb phone, the microphone works for a second or two and then stops recording. If I make the test call, I hear myself talking for the first few seconds and then nothing. The same thing happened a while ago when the beta version just came out, now I tried it again it to see if it could have been solved but nothing... I'm not sure if this has happened to anyone else.

---

### Post by Cappy on 2008-02-23
The skype forums is a better place for that kind of question:
[http://forum.skype.com/index.php?showforum=18](http://forum.skype.com/index.php?showforum=18)

The first thing I would try though would be going to Options --> Sound Devices --> Uncheck "Allow Skype to automatically adjust my mixer levels". It sounds like Skype may be muting the microphone.

---

### Post by muadnu on 2008-02-23
That did it, it was quite easy :oops:

---

### Post by marduuk on 2008-02-23
marduuk@Marduuk:~$ skype
skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory


this is what i get when running skype through term
and nothing happens when i use the icon to launch skype

---

### Post by Cappy on 2008-02-23
Run the code on the front post.

If you already did (and have getlibs) then use
```
sudo getlibs /usr/bin/skype
```

---

### Post by Celeb on 2008-02-28
Hi, the installation worked, but i dont have mic, i can hear the sound but i can't send it.


Thanks a lot

Joaquin Diaz Trepat

---

### Post by arch0njw on 2008-03-03
Marvellous!!!  This is great!  Thank you so very much!

---

### Post by aev on 2008-03-09
The skype install from the first post works great.

---

### Post by incubus on 2008-03-10
Since this is an all-or-nothing operation (and it's important to know where things went wrong), wouldn't it be better to use && instead of ; between commands?

By the way, it worked flawlessly, thank you!

incubus

---

### Post by Emblem Parade on 2008-03-14
Dear Cappy,

Skype 2 is out of beta! Great news. ...And this means you can update your guide, because the links you mention for the old Skype 1.x branch now all point to Skype 2 instead.

---

### Post by crjackson on 2008-03-14
Time to upgrad then.  I'll be doing this over the weekend...

---

### Post by crjackson on 2008-03-16
Does anyone know how to get it to work with my older creative webcam?

```
Bus 002 Device 003: ID 05a9:a511 OmniVision Technologies, Inc. OV511+ WebCam

```

aMSN - Camstream - Ekiga all recognize and display video fine.  Problem is I want to use Skype instead.  Any Ideas?

---

### Post by edu77pose on 2008-03-24
:guitar:

Thanks for that, all the steps worked without a hiccup.

Can't wait till they just make a deb file for 64bit.

---

### Post by craig.taverner on 2008-03-25
The installation worked well on hardy heron beta, and getlibs claimed no libs were missing, but skype had no sound and the console produced:
[COLOR="Blue"]ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave[/COLOR]
Repeated many times. I then noticed from the skype install log that there were missing dependencies, libqt4, and so I installed them with apt-get (which also provided libaudio2). Restarting skype gave the same error. What could I be missing?

---

### Post by vasilis34 on 2008-03-25
I get the same error 

ALSA lib ../../../src/pcm/pcm_dmix.c:874snd_pcm_dmix_open ) unable to open slave

when there is another sound application, for example amarok, opened. When I close any other sound app, skype has sound. I don't know if this is a bug concerning the new pulseaudio system in hardy or anything else but I 'd like to hear if anyone has any idea on how to solve this problem.

---

### Post by Seinfeld on 2008-03-26
Cappy.. Thanks very very much.. I would like to add a very important note guys....

Cappy's algorithm works flawlessly but BE SURE to download the Static OSS (1.4) NOT the (2.0) as the latter will give an error libXss.o.1 not found. The algorithm uses the *  so it will just grab your downloaded version whatever it is, so just be sure. Also if you are trying to install Skype from Automatix2, it is directed to 1.4.deb by default which is recently removed by Skype that is why it does not work and cannot find the download. We all look forward that Skype releases 64 bit version soon..
:KS
Thanks and Thanks a million Cappy.. Works great

---

### Post by rsambuca on 2008-03-28
FYI - [Skype released a hotfix for 2.0]("http://share.skype.com/sites/garage/2008/03/skype_20_for_linux_hotfix.html") today.  From the release, it looks like they fixed a bug or two.

---

### Post by Predtech on 2008-03-29
I gotta tell you THANKS, from the bottom of my dark heart, lol. I love Linux as opposed to Winblows, and i am overjoyed that i can now use Skype on my 64bit version of Ubuntu 7.10

---

### Post by Mr_Ada on 2008-03-29
I get "
skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory"

after I have done the above 64 bit procedure and try running skype onthe  command line.

Also I tried to do the gedit thing and got this error:

gedit: symbol lookup error: gedit: undefined symbol: g_once_init_enter_impl

I am guessing I am serious honked up.  How do I check things for consistency?

Chris

---

### Post by Cappy on 2008-03-29
You ran
> sudo apt-get install ia32-libs lib32asound2; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i getlibs-all.deb; sudo dpkg -i --force-all skype-install.deb; sudo getlibs /usr/bin/skype
?

Let me see the output of
```
sudo getlibs /usr/bin/skype
```


As for the gedit error .. your libraries are messed up somehow, possibly from an upgrade. Give me the output from:
```
sudo updatedb; locate libglib | grep -v '/usr/share/' | grep -v '/var/'
```
This will take a few minutes.

---

### Post by zorkerz on 2008-03-29
I have hardy. Should I change anything from the gutsy instructions?

One of the commands we enter is 'wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb' What is boundlessupremacy.com? Are we going to the site because they have packages that are not in the ubuntu repos?

Sorry if you have covered this already. I did not check every single post on this thread. Does ubuntuforums have a search feature for a single thread?

---

### Post by sayantandas on 2008-03-29
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
ALSA lib pcm_dmix.c:874: (snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874: (snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874: (snd_pcm_dmix_open) unable to open slave

[LEFT]this what i get when i start skype in terminal
[/LEFT]

---

### Post by Cappy on 2008-03-29
> **zorkerz said:**
> I have hardy. Should I change anything from the gutsy instructions?
You have to use the static install at the bottom because Hardy 64-bit cannot use the 32-bit libraries required by skype due to a Hardy bug. I just updated the static install to work with Hardy. I haven't updated it in a long time so there might be something that has changed.

> **zorkerz said:**
> 
One of the commands we enter is 'wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb' What is boundlessupremacy.com? Are we going to the site because they have packages that are not in the ubuntu repos?
It's my domain with my package.

> **zorkerz said:**
> Sorry if you have covered this already. I did not check every single post on this thread. Does ubuntuforums have a search feature for a single thread?

In the top right, below the page numbers there is a "Search this thread"

> **sayantandas said:**
> Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
ALSA lib pcm_dmix.c:874: (snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874: (snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874: (snd_pcm_dmix_open) unable to open slave

[LEFT]this what i get when i start skype in terminal
[/LEFT]

Your sound settings are not correct. You'll probably want to start a new thread and list wha distro you are using, your sound card, etc.
Edit: You may also want to try the different options available to you in Skype under sound devices.

---

### Post by MasterSushi on 2008-03-30
I am using Gutsy 64 bit and this worked perfectly. Thank you very much.

---

### Post by Paulo Wageck on 2008-03-30
worked like a charm

10x!!!!!!!!

:popcorn:

---

### Post by Equiflux on 2008-03-30
I'm having trouble uninstalling the 32-bit deb/package. When I installed it I just forced dpkg, I didn't use getlib. When I try to run "sudo apt-get remove skype" it tells me the "skype" package can not be found.

---

### Post by Cappy on 2008-03-30
> **Equiflux said:**
> I'm having trouble uninstalling the 32-bit deb/package. When I installed it I just forced dpkg, I didn't use getlib. When I try to run "sudo apt-get remove skype" it tells me the "skype" package can not be found.

```
sudo dpkg -r skype
```

---

### Post by lduperval on 2008-03-30
Another happy customer! I installed and tested the Webcam and both work very well.

Next up, doing an actual real call with video.

Let me add that I tried to get theat webcam thing working but Skype is the only one it worked with.

Thanks for this post!

L

---

### Post by kieranpete on 2008-04-01
great how to works well

---

### Post by colinsanter on 2008-04-01
I am using an Acer Aspire 5050 with an AMD64 Turion processor. The code worked perfectly. Many Thanks.=D>

---

### Post by kimme on 2008-04-02
This worked perfectly for me, but jittering sound when I call Skypes Test Center to check how my call is sounding.

---

### Post by MasterSushi on 2008-04-02
This works perfectly for me in Ubuntu 7.10 64 bit.

Thank you very much for being a huge help to the Ubuntu community.

---

### Post by 8086 on 2008-04-03
Here's [an updated How-To for Ubuntu 8.04]("http://folk.ntnu.no/kopseng/blogg/?p=175").

Think the info in the first post is a bit out-dated. All things work perfectly for me on my Acer 6292 including webcam.

---

### Post by Cappy on 2008-04-03
> **8086 said:**
> 
Think the info in the first post is a bit out-dated.

It is, in fact, not.

Some additional notes:

The Hardy install provided (at the bottom) uses the static installation to avoid the recent ia32-libs in Hardy conflict with qt4 32-bit/64-bit.

Also, see my getlibs script to see why manually installing 32-bit libs is a thing of the past.

---

### Post by 8086 on 2008-04-03
Oohh. Didn't see that. Just read the top thing about 7.04/7.10... and jumped to the next posting. Thanks for letting me know of your getlib script - seems nice.

---

### Post by dark_phantom on 2008-04-05
I'm not sure if this has been covered or not.  But I had to do an extra step for Hardy to get the icons to show in AWN and in Applications/Internet.  

This is what I did:
```
sudo cp /usr/share/skype/icons/SkypeBlue_48x48.png /usr/share/pixmaps/skype.png
sudo cp /usr/share/pixmaps/skype.png /usr/share/icons/skype.png
```

After this I was able to see the icons.

---

### Post by Little Elf on 2008-04-07
Thanks so much for the great description!!! I had tried installing it for hours (without my shell as I'm too unsure about what to do myself), but after following the instructions in this thread it worked perfectly! :)

---

### Post by cherry316316 on 2008-04-08
thanks alot

just a side question ,  have u tried installing acrobat on 64 bit hardy ? for me its giving some conflicts of library , when i am using gusty instructions.

---

### Post by mr fuzzy on 2008-04-08
Do you ever get tired of the praise and appreciation Cappy?

Thanks heaps, I've been trying to get Skype working for hours before finding this post. Things like this make Ubuntu so nice to use.

Thanks again

---

### Post by aidave on 2008-04-08
Thanks for this.  On the last line:

```

sudo getlibs /usr/bin/skype

```

It said "getlibs command not found".  I went to try to install it but can't find it...

"boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb "
Connection refused

---

### Post by LarsSikstrom on 2008-04-08
Cappy,

I want to add my thanks for your concise and to the point advice. I have just installed Hardy Heron on my home assembled AMD 64 computer and spent a great deal of time and effort to find a way to use Skype on it. And then I found what you had written and followed the instructions. Miraculously the installation proceeded overcoming various problems by itself. And Skype appears as it should and I am quite confident it will work when I try it on my contacts to morrow.

I only hope others in my situation will find their way to your posting and benefit as I have.

Again many thanks

Lars Sikstrom

---

### Post by Cappy on 2008-04-08
> **aidave said:**
> Thanks for this.  On the last line:

```

sudo getlibs /usr/bin/skype

```

It said "getlibs command not found".  I went to try to install it but can't find it...

"boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb "
Connection refused

Server may have been down for the moment when you tried; Try again

> **mr fuzzy said:**
> Do you ever get tired of the praise and appreciation Cappy?


No.

Guide Note:
I've edited the Hardy Heron install. It will now use the top (non-static) install and include instructions on how to fix the problems with gtk. I don't like my static install procedure that much.

---

### Post by kushykush on 2008-04-08
I get the same error "getlibs command not found.

---

### Post by mkarnicki on 2008-04-12
**64-bit HARDY USERS**: If you do not see any buttons/pictures use this fix:

([http://ubuntuforums.org/showpost.php?p=4660832&postcount=7](http://ubuntuforums.org/showpost.php?p=4660832&postcount=7))

Cappy, what exactly does this script do? Cose I wanted to execute it and I got:

ln: creating symbolic link `/usr/l32/lib32': File exists
sed: can't read /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.8: No such file or directory

What can I do about it? /I don't see avatars on skype, Hardy 8.04, HP tx1320us

---

### Post by Cappy on 2008-04-12
That script is for when you cannot see all images, not just avatars. I'll clarify on the guide. The only way to get avatars on 64-bit at the moment is to use the static install.

If you notice problems you can reverse it too:
> sudo sed -i -e 's/usr\/l32/usr\/lib/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders

---

### Post by joetaxpayer on 2008-04-13
[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb) seems to be down.

---

### Post by observative on 2008-04-13
It was down earlier today when I tried too.

---

### Post by Cappy on 2008-04-14
That's actually my old install.

As for the link being down ... the forums were abbreviating the link. I fixed the problem.

---

### Post by observative on 2008-04-14
That would explain why it said beta. I will remove that from my previous post. The link works now, thanks again :)

---

### Post by CybrSpy on 2008-04-14
Strange that I'm getting this error:

skype
skype: symbol lookup error: /usr/lib32/libQtNetwork.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

This is from a fresh hardy install on my laptop just this morning, it works fine on my desktop - but I installed it 2 days earlier.  

getlibs says everything is fine.

Anyone have any ideas?

cheers

---

### Post by oooh on 2008-04-14
Worked perfect with video support using:

64-bit install (or upgrade) skype 2.0 (with video):

On Sony Vaio FZ21M

Thanks master !

---

### Post by guj4_n3b3sk4 on 2008-04-20
I have installed Skype by manual from 1st page for 7.10 Ubuntu 64-bit. Skype appears in my Applications, but when I click on it, nothing happens. I go to terminal, type Skype, press enter and I get this:

```
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory

```

How to fix the problem and start Skype?

---

### Post by Cappy on 2008-04-20
Then copy and paste just this into the terminal:
```
sudo apt-get install ia32-libs lib32asound2; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs /usr/bin/skype
```

Copy and paste any errors you get from running those lines if skype still doesn't work.

---

### Post by guj4_n3b3sk4 on 2008-04-20
After **sudo apt-get install ia32-libs lib32asound2** I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
lib32asound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

After **wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb** I get this:

```
--13:05:19--  http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
           => `getlibs-all.deb'
Resolving boundlesssupremacy.com... 209.123.149.151
Connecting to boundlesssupremacy.com|209.123.149.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6,498 (6.3K) [text/plain]
Server file no newer than local file `getlibs-all.deb' -- not retrieving.
```

After **sudo dpkg -i getlibs-all.deb** I get this:

```
(Reading database ... 100517 files and directories currently installed.)
Preparing to replace getlibs 2.06 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (2.06) ...

```

And after **sudo getlibs /usr/bin/skype** I get this:

```
libQtDBus.so.4: libqt4-core
libQtGui.so.4: libqt4-gui
libQtNetwork.so.4: libqt4-core
libQtCore.so.4: libqt4-core
The following i386 packages will be installed:
libqt4-core
libqt4-gui
Continue [Y/n]? y
libqt4-core was not found in your repositories
Make sure you have all repositories enabled and updated
libqt4-gui was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

```

That libtqt4-core and gui is missing me, seems like. What next?

---

### Post by guj4_n3b3sk4 on 2008-04-20
I have resolved problem. Seems that problem was folowing: I went to synaptic and checked if those libs were installed. And they were. I did folowing: marked lib, went to preferences, force version, and downgrade it from 3.2 (ubuntu) to version (dunno exactly which one, I think 3 only, but dunno) for Gutsy (in brackets you'll see (gutsy)).

I have downgrade it, and after that last command from my previous post was done correctly, and Skype started successfully.

---

### Post by Cappy on 2008-04-20
Glad you resolved it. 

The problem was in your repositories so I would recommend you goto System-->Administration-->Software Sources

and check all of the check boxes except "Source code".

Then change to the **Updates** tab and check all of the boxes under "Ubuntu updates".

Then click close and click the "reload" button when a popup comes up.

This will help prevent future problems (not just relating to getlibs).

---

### Post by guj4_n3b3sk4 on 2008-04-20
Done that, thank you for the advice. Anyway, how often do I need to do updates? Should I install any update I've been noticed of, or?

---

### Post by idoisler on 2008-04-21
dosn't work for me...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32bz2-1.0
E: Package ia32-libs has no installation candidate
--08:03:35--  [http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
           => `getlibs-all.deb'
Resolving boundlesssupremacy.com... 209.123.149.151
Connecting to boundlesssupremacy.com|209.123.149.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6,498 (6.3K) [text/plain]
Server file no newer than local file `getlibs-all.deb' -- not retrieving.

--08:03:36--  [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
           => `skype-install.deb'
Resolving [www.skype.com](www.skype.com)... 204.9.163.136
Connecting to www.skype.com|204.9.163.136|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://download.skype.com/linux/skype-debian_2.0.0.68-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.68-1_i386.deb) [following]
--08:03:37--  [http://download.skype.com/linux/skype-debian_2.0.0.68-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.68-1_i386.deb)
           => `skype-install.deb'
Resolving download.skype.com... 204.9.165.83, 212.72.53.130, 204.9.165.82
Connecting to download.skype.com|204.9.165.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15,481,312 (15M) [application/octet-stream]

100%[====================================>] 15,481,312   347.47K/s    ETA 00:00

08:04:29 (332.42 KB/s) - `skype-install.deb' saved [15481312/15481312]

(Reading database ... 88237 files and directories currently installed.)
Preparing to replace getlibs 2.06 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (2.06) ...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 88237 files and directories currently installed.)
Preparing to replace skype 2.0.0.68-1 (using skype-install.deb) ...
Unpacking replacement skype ...
dpkg: skype: dependency problems, but configuring anyway as you request:
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
Setting up skype (2.0.0.68-1) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32bz2-1.0
E: Package ia32-libs has no installation candidate
This application isn't missing any dependencies






any ideas ?/?

---

### Post by Cappy on 2008-04-22
Do the same thing that was two posts up. [http://ubuntuforums.org/showthread.php?t=432295&page=30#297](http://ubuntuforums.org/showthread.php?t=432295&page=30#297)

---

### Post by pete35887 on 2008-04-24
thanks man!

---

### Post by wincent on 2008-04-27
Thank you very much, worked from the first attempt... Hardy heron is awesome :razz:

---

### Post by Emblem Parade on 2008-04-27
Dear Cappy and everyone else:

Skype 2, 32- and 64-bit, is now available on the [Medibuntu]("http://www.medibuntu.org/") repositories. This guide should probably be updated to include this information, and perhaps retired. :)

(For those worried about external repos, know that Medibuntu is as close as it gets to official, and is very well maintained. Also includes Google Earth, Acrobat Reader, and, of course, the unencrypted DVD codecs.)

---

### Post by Concrete on 2008-04-28
Thank you for this... It really works great, and im happy :)

---

### Post by cherry316316 on 2008-04-28
I have a problem with skype linux.
when I use skype video , after few seconds
or probably after a minute, my video gets stuck 
to some old frame. (both I and the other party can see it stuck and dancing in the same old frame )



Then I have to stop broadcasting 
my video and start it again. and this happen again and again
which is annoying.

interestingly, the video of other party never got stuck.

the only solution i have to this problem at present is
to restart my computer and goto windows and use skype there.
skype video works fine in window. But, I don't want to go in win
so any body have any solution to this problem ???

---

### Post by cherry316316 on 2008-04-28
> **Emblem Parade said:**
> Dear Cappy and everyone else:

Skype 2, 32- and 64-bit, is now available on the [Medibuntu]("http://www.medibuntu.org/") repositories. This guide should probably be updated to include this information, and perhaps retired. :)

(For those worried about external repos, know that Medibuntu is as close as it gets to official, and is very well maintained. Also includes Google Earth, Acrobat Reader, and, of course, the unencrypted DVD codecs.)


question: 
I found this archive [http://ubuntuforums.org/archive/index.php/t-522525.html](http://ubuntuforums.org/archive/index.php/t-522525.html)
which was very good in explaining, what is skype-static

Now, i was looking for QT GUI toolkit , as mention in that link.
but when i do search in synaptic, i get too many options, which are very close to each other. Does any one knows which one is best.

Thanks

---

### Post by sofasurfer on 2008-04-28
Athlon x2 64 processor.
64 bit Hardy Ubuntu.

I installed skype by sudo apt-get install skype. The echo test returned no audio.
I then found this thread. I uninstalled skype by sudo apt-get remove skype. I then installed skype by using command found at the top of this thread...

sudo apt-get install ia32-libs lib32asound2; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i --force-all skype-install.deb; 

Echo test still returns no audio.

How to I fix this?

Thanks...

---

### Post by mouse4d on 2008-04-28
**sofasurfer** +1 Have the same problem
it tells me "Problem with Audio Playback" where it should be "Calling"(or smthg like that)

if i run it from terminal:

mouse@vizuina:~$ skype
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

thanks in advance :)

---

### Post by harak on 2008-04-28
> **mouse4d said:**
> **sofasurfer** +1 Have the same problem
it tells me "Problem with Audio Playback" where it should be "Calling"(or smthg like that)

if i run it from terminal:

mouse@vizuina:~$ skype
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

thanks in advance :)

mouse4d, I have the same problem as well. But what i noticed is that this error appeared if another program was acessing the speaker. For example of i am playing a video on google/ playing some music locally, skype gives me the above errors. But if change the website or close the player...skype works without any problem.

---

### Post by sofasurfer on 2008-04-29
I get NO error messages. I just have no audio.

---

### Post by mouse4d on 2008-04-29
> **harak said:**
> mouse4d, I have the same problem as well. But what i noticed is that this error appeared if another program was acessing the speaker. For example of i am playing a video on google/ playing some music locally, skype gives me the above errors. But if change the website or close the player...skype works without any problem.

wow thanks... you were right! :popcorn:
but  i don't really like how mic works in Linux, i mean i had openSUSE, now Ubuntu, and even with Mic Boost (+20 bB) i have sometimes to shout i order to be heared(in windows worked just fine, so it's not the mic or other hardware issues). well, i guess i'll have just to get used with it. :D

---

### Post by hazica on 2008-04-29
Thanks mate. Everything went smooth.

---

### Post by NiGhtPiSH on 2008-05-02
Is it me only having the problem with the avatars? I just can't select one and load it. Do you think it's a problem because my Ubuntu is installed via Wubi?

---

### Post by fofftorrent on 2008-05-02
other option is to install via medibuntu for BOTH i386 and amd64:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo aptitude install update
sudo aptitude install medibuntu-keyring 
sudo aptitude install update
sudo aptitude install skype

works like a charm with no hocus pocus:guitar:

---

### Post by edu77pose on 2008-05-04
:guitar:

The 64bit tip worked smoothly on an intel core 2 duo.

Ubuntu rocks!

---

### Post by juve_abhi on 2008-05-06
thanks a ton

---

### Post by gattopi on 2008-05-10
I have this Error  Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
 ANy Ideas?

Thanks

---

### Post by xellas84 on 2008-05-14
> **fofftorrent said:**
> other option is to install via medibuntu for BOTH i386 and amd64:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo aptitude install update
sudo aptitude install medibuntu-keyring 
sudo aptitude install update
sudo aptitude install skype

works like a charm with no hocus pocus:guitar:

Newbie here, tried copy pasting all those commands in (one at a time)

This didn't work for some reason... the first line seemed to work, but every one of those filenames failed.  Couldn't find update, medibuntu-keyring, or skype when I tried aptitude install.

---

### Post by Cappy on 2008-05-14
> **gattopi said:**
> I have this Error  Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
 ANy Ideas?

Thanks

```
sudo apt-get install bluez-audio
```

and install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

and use
```
sudo getlibs /usr/bin/skype
```

If you are trying to get your bluetooth to work with skype look here too: [http://ubuntuforums.org/showthread.php?p=4910397](http://ubuntuforums.org/showthread.php?p=4910397)

---

### Post by fofftorrent on 2008-05-18
xellas84, can u list what was shown in the terminal?

you did preface commands with sudo, right?

---

### Post by Cappy on 2008-05-18
> **fofftorrent said:**
> xellas84, can u list what was shown in the terminal?

you did preface commands with sudo, right?

Your commands are incorrect

---

### Post by fofftorrent on 2008-05-19
what's wrong with them? seems to work for me...

---

### Post by Luuka on 2008-06-05
Hey guys, after lurking for a while, I decided to join in the forums, seeing as many of my problems [such as not having flash on kubuntu] have been solved by following the directions here.

In any case, my problem now is such. I have installed skype on this machine using the skype_static file, and it has worked. I know how to put sound on it, so that's all good. However, the cam that I use seems to be one of those "fiddle to get it working." I installed the file as required by following this link "https://wiki.ubuntu.com/SkypeWebCams." The cam I have is Creative Live! Cam Notebook Pro [0400].

This is the only text that tells me what to do. 
"With Skype 2.0.0.68 and ATI fglrx driver. You should setup ov51x-jpeg-1.5.7 and "sudo modprobe ov51x-jpeg forceblock=1" or "sudo gedit /etc/modprobe.d/options" add there "options ov51x-jpeg forceblock=1". ov51x-jpeg-1.5.7 can be found here: [WWW] http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz"

I installed it, use the sudo gedit, added that option, but still nothing! I am at a wit's end!](*,) Nothing I do is working and I'm ready to throw the damn computer out the window! Is there anything I can do or some other link I can follow so that I can do this? I'm very new to ubuntu and never had to work with a camera, but now I do. Any help or suggestions would be highly appreciated.

---

### Post by mhenriday on 2008-06-06
> **sofasurfer said:**
> I get NO error messages. I just have no audio. **sofasurfer**, I can't help wondering if you don't suffer from precisely the same problem I do on my **Athlon 64 X2 5000+** machine, which has the added disadvantage of running a **Creative Sound Blaster X-Fi** audio card - take a look at the screendump attached hereto, which shows the results of my attempt to ring the **Skype** test-calling centre. What audio card are you using, by the way ? Heroic work has been done by **NullHead**, **Temüjin**, *et al* on another [_thread_]("http://ubuntuforums.org/showthread.php?t=571656") to enable us to get audio to work with this card ; I, for example, only became able to listen to ***YouTube*** videos directly from the net a couple of days ago. But as I'm running 64-bit **Hardy**, and therefore installed the 64-bit **OSS4** deb package, I suspect that forcing the **Skype** i386 deb architecture has resulted in a package which fails to work on my setup. Am I going to have to wait until **Skype** vouchsafes us a native 64-bit package to be able to use the service, or is it something else entirely which is causing the difficulties ? Grateful for any suggestions !...

Henri

---

### Post by hihihi on 2008-06-08
> **Luuka said:**
> Hey guys, after lurking for a while, I decided to join in the forums, seeing as many of my problems [such as not having flash on kubuntu] have been solved by following the directions here.

In any case, my problem now is such. I have installed skype on this machine using the skype_static file, and it has worked. I know how to put sound on it, so that's all good. However, the cam that I use seems to be one of those "fiddle to get it working." I installed the file as required by following this link "https://wiki.ubuntu.com/SkypeWebCams." The cam I have is Creative Live! Cam Notebook Pro [0400].

This is the only text that tells me what to do. 
"With Skype 2.0.0.68 and ATI fglrx driver. You should setup ov51x-jpeg-1.5.7 and "sudo modprobe ov51x-jpeg forceblock=1" or "sudo gedit /etc/modprobe.d/options" add there "options ov51x-jpeg forceblock=1". ov51x-jpeg-1.5.7 can be found here: [WWW] http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz"

I installed it, use the sudo gedit, added that option, but still nothing! I am at a wit's end!](*,) Nothing I do is working and I'm ready to throw the damn computer out the window! Is there anything I can do or some other link I can follow so that I can do this? I'm very new to ubuntu and never had to work with a camera, but now I do. Any help or suggestions would be highly appreciated.



hello Luuka,

please do not through the computer out of the window.
tell us: 
what computer are u using?
what ubuntu version? 
and try out the following:
=first get cam to work before trying it in skype.
->u can make the first test by typing in terminal:
$ gstreamer-properties 
there, under video-tab, try to see if u managed to get your camera to work and if it works correctly.
than tell us if it works.
good luck

---

### Post by Luuka on 2008-06-08
You know, it's so funny, but aggravation seems to be my energy feed when it comes to things like this. I have reinstalled Ubuntu 8.04 onto the Shuttle PC I ordered from newegg, which came with Foresight Linux preinstalled. Now, that wasn't too terrible of a starting OS, but I had a hell of a time trying to install things using sudo conary command, that it wasn't worth my time. My personal computer has 8.04 and I'm quite happy with it.

The funny thing is, I actually got the camera working now. Of course, I had to jump through hellfire and like, 10 different websites before I finally figured it out, and tada! The only thing I regret now is not keeping track of those sites, but I can most certainly fetch them again for anyone who might have trouble with it. Thank you for taking the time to read my post though! :KS

---

### Post by Cappy on 2008-06-08
> **Luuka said:**
> 
The funny thing is, I actually got the camera working now. Of course, I had to jump through hellfire and like, 10 different websites before I finally figured it out, and tada! The only thing I regret now is not keeping track of those sites, but I can most certainly fetch them again for anyone who might have trouble with it. Thank you for taking the time to read my post though! :KS

You should make a tutorial in a new thread for others who come across your problem =)

---

### Post by dedyisn on 2008-06-10
I'm using Skype 2.0
but there is no sound. It Say that my there is a problem with my audio output.
But on the other application, there is no sound devices  problem.
my Media player like rhytmbox and amarok running well.

Anyone can help how to get my skype can get a sound ?
sorry for my bad english

---

### Post by fonsi2099 on 2008-06-12
It works fine for me, cappy many thanks.


:guitar:
On my Hardy, AMD 64bit

---

### Post by mhenriday on 2008-06-13
I should mention that for 64-bit users who, for whatever reason, do not find it appropriate to force the architecture of i386 deb packages, can install what seems to be a 64-bit version of **Skype** (??) direct from Synaptic, if they add the [_Medibuntu repositories_]("https://help.ubuntu.com/community/Medibuntu") to their 3rd party list. Alas, doing so didn't help me with my audio problems in **Skype**, but those with a less refractory audio card than **Creative**'s **Soundblaster X-Fi** might like to give it a whirl....

Henri

---

### Post by mark.kristos on 2008-06-14
I get this output when trying to run your script:

mark@ubuntu-laptop:~$ sudo apt-get install ia32-libs lib32asound2; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i --force-all skype-install.deb; 
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manually installed.
lib32asound2 is already the newest version.
lib32asound2 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--06:53:09--  [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
           => `skype-install.deb'
Resolving [www.skype.com](www.skype.com)... failed: Name or service not known.
dpkg-deb: unexpected end of file in version number in skype-install.deb
dpkg: error processing skype-install.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 skype-install.deb
mark@ubuntu-laptop:~$

---

### Post by mark.kristos on 2008-06-14
> **mhenriday said:**
> I should mention that for 64-bit users who, for whatever reason, do not find it appropriate to force the architecture of i386 deb packages, can install what seems to be a 64-bit version of **Skype** (??) direct from Synaptic, if they add the [_Medibuntu repositories_]("https://help.ubuntu.com/community/Medibuntu") to their 3rd party list. Alas, doing so didn't help me with my audio problems in **Skype**, but those with a less refractory audio card than **Creative**'s **Soundblaster X-Fi** might like to give it a whirl....

Henri

Installed great following instruction on the link given. Heres what a successful install should look like:

mark@ubuntu-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for mark: 
--07:10:36--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to [www.medibuntu.org|87.98.242.10|:80](www.medibuntu.org|87.98.242.10|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

07:10:52 (37.63 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

mark@ubuntu-laptop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Get:3 [http://archive.canonical.com](http://archive.canonical.com) hardy Release [6998B]                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]               
Get:5 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages [14B]                
Get:6 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources [666B]                
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6022B]
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [5590B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [22.9kB]        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [3457B]   
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [13.0kB]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                              
Get:14 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages [5721B]               
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]             
Get:16 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages [7726B]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [209kB]        
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6022B]  
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [70.1kB]        
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [906B]    
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [40.4kB]   
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [7036B]     
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [7696B]  
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [1433B]   
Fetched 532kB in 12s (42.7kB/s)                                                
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]? y
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 1s (3432B/s)                            
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 126914 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [5590B]                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Fetched 190B in 6s (28B/s)                                                     
Reading package lists... Done
mark@ubuntu-laptop:~$ sudo synaptic

Then, open synaptic and search for skype, mark skype package for install. Click apply. Boom, boom, bang it even installs the launcher icon in the applications menu.

I made a test call successfully.

Thumbs Up, this is straight.

---

### Post by mhenriday on 2008-06-14
Glad to see that the **Medibuntu** link worked for you, **mark.kristos** ! Just out of curiosity, may I ask what sort of audio card you are running ?...

Henri

---

### Post by mark.kristos on 2008-06-15
> **mhenriday said:**
> Glad to see that the **Medibuntu** link worked for you, **mark.kristos** ! Just out of curiosity, may I ask what sort of audio card you are running ?...

Henri

Intel Corporation 82801H ( see screenshot )

---

### Post by victorgreen on 2008-06-15
Thanks so much, this worked brilliantly, Ive installed skype before on 64bit hardy, but it involved a ton more steps and creating a lot of my own folders in /bin. This way was faster, simpler, easier and all around better.

---

### Post by chadid on 2008-06-16
Thanks alot it worked superb for me

---

### Post by mhenriday on 2008-06-16
Glad you chaps - **victorgreen** and **chadid** found the [_Medibuntu link_]("https://help.ubuntu.com/community/Medibuntu") useful ! I'd be especially interested in hearing if anyone with a **Creative Soundblaster X-Fi** audio card has succeeded in getting the sound to work in **Skype** using this method (or any other, for that matter !)...

Henri

---

### Post by Cappy on 2008-06-16
> **mhenriday said:**
> Glad you chaps - **victorgreen** and **chadid** found the [_Medibuntu link_]("https://help.ubuntu.com/community/Medibuntu") useful ! I'd be especially interested in hearing if anyone with a **Creative Soundblaster X-Fi** audio card has succeeded in getting the sound to work in **Skype** using this method (or any other, for that matter !)...

Henri

The normal skype offered at Medibuntu is the same as the one from the official site.

Do try closing all programs that could be using sound (even browsers if they have flash going) and then starting skype. That may help.

If that fails then you may want to play with the skype settings where you can change your input/output.

Also, **victorgreen** and **chadid** didn't say they used medibuntu. However, I've added medibuntu to the Hardy guide because of the skype-static-oss package (referred to below).

P.S. I just remembered that medibuntu has a skype-static-oss package. Your X-Fi drivers use OSS so skype-static-oss may work better. It should be as easy as following the medibuntu repository instructions and using ```
sudo apt-get install skype-static-oss
```
(or synaptic)

Let me know what ends up working.

---

### Post by mhenriday on 2008-06-17
> **Cappy said:**
> ... However, I've added medibuntu to the Hardy guide because of the skype-static-oss package (referred to below).

P.S. I just remembered that medibuntu has a skype-static-oss package. Your X-Fi drivers use OSS so skype-static-oss may work better. It should be as easy as following the medibuntu repository instructions and using ```
sudo apt-get install skype-static-oss
```
(or synaptic)

Let me know what ends up working.

Thanks for your reply, **Cappy** ! In addition to the «skype-common» package, one of the remaining **Skype**-related **2.0.0.68-repackmedibuntu3** packages must be installed in order to get **Skype** to work. In my situation, the «skype-static-oss» package is the obvious choice, and the one in fact I have installed. Alas, I still can't get the sound in **Skype** to work. However, I can send chat messages with the service, so the cloud is not entirely without a silver lining. Grateful, in any event, for further suggestions !... 

Henri

---

### Post by mhenriday on 2008-06-23
For those interested, I can note that updates for the relevant **Medibuntu** packages (to version **2.0.0.72-0medibuntu1**) for **Skype** were released yesterday, but alas, I still can't get any sound in **Skype** with my **Creative Soundblaster X-Fi** card. I suppose we'll have to wait until **Creative** releases a driver that really functions for 64-bit **Linux**, and that doesn't force us to jump through all manner of hoops to get even the simplest (two front speakers) sound to work....

Henri

---

### Post by macabro22 on 2008-06-23
> **mhenriday said:**
> For those interested, I can note that updates for the relevant **Medibuntu** packages (to version **2.0.0.72-0medibuntu1**) for **Skype** were released yesterday, but alas, I still can't get any sound in **Skype** with my **Creative Soundblaster X-Fi** card. I suppose we'll have to wait until **Creative** releases a driver that really functions for 64-bit **Linux**, and that doesn't force us to jump through all manner of hoops to get even the simplest (two front speakers) sound to work....

Henri

Will that upgrade make it work with pulseaudio? My skype works only if all other media players are off

---

### Post by RonakG on 2008-06-24
Hi,

I didn't come across the link, and did a lots of things to install skype on Hardy 64-bit. But no luck.

Now when I try to do it from Synaptic, after following the steps, I get this error.

skype:
  Depends: ia32-libs (>=1.6) but 1.5ubuntu9 is to be installed
 Depends: lib32asound2 but it is not going to be installed

How do I resolve this now?

---

### Post by Cappy on 2008-06-24
> **RonakG said:**
> Hi,

I didn't come across the link, and did a lots of things to install skype on Hardy 64-bit. But no luck.

Now when I try to do it from Synaptic, after following the steps, I get this error.

skype:
  Depends: ia32-libs (>=1.6) but 1.5ubuntu9 is to be installed
 Depends: lib32asound2 but it is not going to be installed

How do I resolve this now?

ia32-libs 1.5ubuntu9 is in Feisty. Either you are using Ubuntu Feisty or your repositories are messed up and you should change mirrors and reload them. Synaptic Package Manager --> Settings --> Repositories
If it is the latter you would be best off making a new thread and posting your /etc/apt/sources.list with it

```
lsb_release -c
```
will tell you if you are running Hardy or not.

If you are running Feisty, there are Feisty specific instructions on the first post.

---

### Post by 8086 on 2008-06-27
Try running skype with padsp prepended (like this: "padsp skype") if you have trouble with the combination of skype and pulseaudio.

---

### Post by macabro22 on 2008-06-27
> **8086 said:**
> Try running skype with padsp prepended (like this: "padsp skype") if you have trouble with the combination of skype and pulseaudio.

Then I lose audio in everything else - not good.

---

### Post by Machiavelli on 2008-06-28
Works like a charm, thank you!

---

### Post by kev000 on 2008-06-28
I'm still not getting sound.

I've tried the medibuntu skype install.  I've tried starting with padsp.  I'm still not getting sound consistently :(.

The error in the terminal is still:

```
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

```

I sometimes get sound when I restart, but no too long after the sound will die again.

Please help!!

nVidia nforce 590 chipset if it matters.

---

### Post by macabro22 on 2008-06-30
> **kev000 said:**
> I'm still not getting sound.

I've tried the medibuntu skype install.  I've tried starting with padsp.  I'm still not getting sound consistently :(.

The error in the terminal is still:

```
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

```

I sometimes get sound when I restart, but no too long after the sound will die again.

Please help!!

nVidia nforce 590 chipset if it matters.

Make sure every other application which uses audio is shut down then proceed to configuring pulseaudio as the sound device in system==>preferences==>audio (or something like that).

If that doesn´t work I advise looking for realtime help on #alsa at irc.freenode.net.

People over there helped me diagnose my problems with an audio diagnostics script provided in the official ALSA forums.]

Good luck

---

### Post by nubdora on 2008-06-30
Works perfectly. Thanks, chief.

---

### Post by ATSC on 2008-07-13
Many thanks Cappy, I owe you a drink or two! :)

---

### Post by sirwhiteout on 2008-07-13
Is there a way to improve the sound quality from the mic? The software processing of skype-static-oss makes it all noisy and full of echo.

---

### Post by macabro22 on 2008-07-14
> **sirwhiteout said:**
> Is there a way to improve the sound quality from the mic? The software processing of skype-static-oss makes it all noisy and full of echo.

The OSS-static version produces a lotta *static*, eh?

hehe =]

Why don't you use the regular 2.0 beta version?

---

### Post by ray_niblock on 2008-07-30
Cappy.  Top banana.......works perfectly on my Athlon64 3500+.

Thanks.  Ray

---

### Post by mngcld on 2008-07-31
> **mouse4d said:**
> **sofasurfer** +1 Have the same problem
it tells me "Problem with Audio Playback" where it should be "Calling"(or smthg like that)

if i run it from terminal:

mouse@vizuina:~$ skype
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

thanks in advance :)

i hav a dell xps m1530. to avoid this mess one has to disable the bluetooh applet trough system>preferences>session and check the bluetooth applet off. thanks a lot!!!!

---

### Post by jcway212 on 2008-07-31
just did this....worked perfect!!! Thanks!!! :)

---

### Post by the_X_files on 2008-08-15
I used the method in the first post to install skype 2.0.0.72 on Ubuntu Hardy 64, everything works fine except the avatarts. I can't see no one's avatar. Any suggestions?

---

### Post by macabro22 on 2008-08-15
> **the_X_files said:**
> I used the method in the first post to install skype 2.0.0.72 on Ubuntu Hardy 64, everything works fine except the avatarts. I can't see no one's avatar. Any suggestions?

I don't get avatars in skype linux as well. I suppose its not implemented yet in this version.

Notice it is still a beta version.

---

### Post by the_X_files on 2008-08-15
> **macabro22 said:**
> I don't get avatars in skype linux as well. I suppose its not implemented yet in this version.

Notice it is still a beta version.

I found a solution to this problem.
[http://ubuntuforums.org/showthread.php?t=661863](http://ubuntuforums.org/showthread.php?t=661863)

It's so cool to see other people's avatars :)

---

### Post by suomalainen on 2008-08-24
Thank you! It works now!!!!!

---

### Post by MGdesigner on 2008-08-27
The method helps me a lot! Thank you!:popcorn:

---

### Post by macabro22 on 2008-08-27
> **the_X_files said:**
> I found a solution to this problem.
[http://ubuntuforums.org/showthread.php?t=661863](http://ubuntuforums.org/showthread.php?t=661863)

It's so cool to see other people's avatars :)

I guess avatars aren´t implemented in Skype 2.0.0.43 though it is in skype-oss-static.

---

### Post by orrorin on 2008-08-28
I've a fresh install of hardy-64 and skype. When I test my audio connection using skype's test/echo service, I can hear the audio alright from my speakers. However, my mic doesn't seem to work.

So, then I installed 'skype-oss-static' but still have the same problem. My mic works fine with Windows/Vista. [I tried padsp skype and also did a reboot.]

My audio settings in System->Preference->Sound for 'Audio Conferencing' are currently set to Autodetect and OSS for sound playback and capture respectively.

---

### Post by ahmed_d on 2008-09-12
thanx

---

### Post by Pavle on 2008-09-19
Hi all, I read a few pages in the thread but my problem still *sounds* unique:
I followed Cappy's inital instructions and installed skype from site (thx man). The install ran fine except for an error about libqt4-core and libqt4-gui not being installed (even though it is installed but then it might be the x64 version).

Anyway I tried to launch it and it ran fine but at first I had no sound at all. After rebooting I got the startup sound and when I go to Options > Sound device the "make test sound" test works.
So far so good.

However when I try to make a test call it just says "Call failed". Before rebooting it used to say "Call Failed: Problem with Audio Playback" but now it's just Call failed (and the sound test works)... I tried changing the Sound Out and Ringing devices from default to whatever but no change.

I have an Nvidia CK804 integrated soundcard and quite ignorant about pulseaudio and all those sound servers so it might be a simple problem..

Any help would be more than welcome!
Thanks for this thread!

---

### Post by craigsn on 2008-09-25
Cappy, have you tried this on Intrepid. I installed Alpha 5 and skype worked fine, > 
craig@Greezy:~$ skype
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)


Any ideas or suggestions
Thanks
Craig

---

### Post by kushykush on 2008-09-25
I followed the instructions on that link.  Did not work. All I want is to install Skype under Intrepid 64, and amazingly there is nothing out there for something which should not be that complicated.

---

### Post by Cappy on 2008-09-25
Apparently, getlibs isn't working properly on Intrepid for unknown reasons. I'll look into it this weekend.

---

### Post by niket on 2008-09-27
> **Cappy said:**
> Special Thanks To: jasnix

[https://developer.skype.com/LinuxSkype](https://developer.skype.com/LinuxSkype)
The skype EULA: [http://www.skype.com/company/legal/eula/index.html](http://www.skype.com/company/legal/eula/index.html)

**Copy and paste the block of code into your terminal to use. The terminal can be found at *Applications-->Accessories-->Terminal***
[SIZE="5"]
[CENTER]**Hardy LTS (8.04) install:**[/CENTER][/SIZE]

**Install directly from the website:**


**Medibuntu's Repositories:**
Medibuntu offers skype, which can be added to your repositories here: [Medibuntu]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f")
You can then install skype by using your Synaptic Package Manager to search for "skype" or ```
sudo apt-get install skype
```

For users with sound problems due to PulseAudio, Medibuntu also offers the package "skype-static-oss". Once installed, skype can be run through pulse audio with "padsp skype".

[SIZE="5"]
[CENTER]**Gutsy (7.10), Feisty (7.04), and Edgy (6.10) installs:**[/CENTER][/SIZE]


**64-bit install (or upgrade) skype 2.0 (with video):**


**64-bit webcam problems**:
See here [http://ubuntuforums.org/showthread.php?t=634393](http://ubuntuforums.org/showthread.php?t=634393) for instructions on how to get your webcam to work if it doesn't.


After installing Skype you can run it from your (_Applications-->Internet_) Menu at the top left of your screen.


[SIZE="5"][CENTER]**Dapper LTS (Ubuntu 6.04) install:**[/CENTER][/SIZE]

(This section may be outdated)

**AMD64 (64-bit) static :**
```

sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2
wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
wget http://www.skype.com/go/getskype-linux-static
tar -xvjf skype_static*.tar.bz2
cd skype_static*
sudo mv skype /usr/bin/
sudo mkdir /usr/share/skype
sudo mv sounds /usr/share/skype/
sudo mv icons /usr/share/skype/
sudo cp /usr/share/skype/icons/SkypeBlue_48x48.png /usr/share/icons/skype.png
sudo cp /usr/share/icons/skype.png /usr/share/pixmaps/skype.png
sudo mv skype.desktop /usr/share/applications/
cd ..
sudo rm -rf skype_static*
sudo getlibs /usr/bin/skype

```

**i386 (32-bit) static :**
```

sudo apt-get install libsigc++-2.0-0c2a libdbus-1-2
wget http://www.skype.com/go/getskype-linux-static
tar -xvjf skype_static*.tar.bz2
cd skype_static*
sudo mv skype /usr/bin/
sudo mkdir /usr/share/skype
sudo mv sounds /usr/share/skype/
sudo mv icons /usr/share/skype/
sudo mv skype.desktop /usr/share/applications/
cd ..
sudo rm -rf skype_static*

```

If it fails to run please run "skype" in the terminal and post the output with your question.




Thanks a lot!!! It works great!!
\\:D/\\:D/\\:D/\\:D/=D>=D>=D>

---

### Post by frunns on 2008-10-01
Neat guide, but as getlibs doesn't work too well on Intrepid, any suggestions on how to get libQtGui.so.4? Fell in love instantly with Intrepid, so I'd rather not go back just for Skype.

---

### Post by Cappy on 2008-10-01
> **kushykush said:**
> I followed the instructions on that link.  Did not work. All I want is to install Skype under Intrepid 64, and amazingly there is nothing out there for something which should not be that complicated.

> **frunns said:**
> Neat guide, but as getlibs doesn't work too well on Intrepid, any suggestions on how to get libQtGui.so.4? Fell in love instantly with Intrepid, so I'd rather not go back just for Skype.

Use
```
getlibs -p libqtgui4
```

They changed the name of the package in Intrepid.

---

### Post by frunns on 2008-10-01
> **Cappy said:**
> Use
```
getlibs -p libqtgui4
```

They changed the name of the package in Intrepid.

Yeah, that worked. Skype still complains about not finding the file though. ><

Edit: Nvm, new file, works fine after installing that too. :)

---

### Post by Soarer on 2008-10-02
I am clearly doing something wrong. I pasted the command at the start of this thread for Intrepid: 

```
sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb http://www.skype.com/go/getskype-linux-ubuntu; sudo dpkg -i --force-all skype-install.deb; sudo getlibs -p libqtgui4; sudo getlibs /usr/bin/skype 
```

And got the following:

```
dpkg: skype: dependency problems, but configuring anyway as you request:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
Setting up skype (2.0.0.72-1) ...
sudo: getlibs: command not found
sudo: getlibs: command not found
mike@nexus:~$ skype
skype: error while loading shared libraries: libQtXml.so.4: cannot open shared object file: No such file or directory
```

Also got ```
getlibs: command not found
``` when trying the code in the previous couple of posts.

Any clue as to what I am doing wrong, please?

---

### Post by Gedemins on 2008-10-02
exactly the same problem here.

---

### Post by Cappy on 2008-10-02
I added ```
sudo dpkg -i getlibs-all.deb
```

to the Hardy section instead of the Intrepid section on accident. Fixed.

---

### Post by Soarer on 2008-10-02
Tried the new version (thanks Cappy) but I get:

```
~$ skype
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)
```

The error happens when I try to use the call test service.

---

### Post by samperlmutar on 2008-10-02
> **Soarer said:**
> Tried the new version (thanks Cappy) but I get:

```
~$ skype
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)
```

The error happens when I try to use the call test service.

when i type "skype" into the terminal i get the same error. anybody? when i click the skype icon, i see the splash screen, then program, then it quits. every time.

---

### Post by Gedemins on 2008-10-02
it's because of pulseaudio. 

> **iamjfarrell said:**
> This workaround worked for me! 

**Temporary workaround:** in the /usr/share/alsa/alsa.conf comment out the line that says:
"/usr/share/alsa/pulse.conf"

but skype then starts with no sounds (and thogh doesn't crash)
on my previous installation of ubuntu i did one of the tutorials with pulseaudio that made skype sound work. only i don't remember which it was (because only that one worked form me then)

---

### Post by craigsn on 2008-10-02
> **Cappy said:**
> Use
```
getlibs -p libqtgui4
```

They changed the name of the package in Intrepid.

I tried that, and when I invoke skype from the command line I get the following:
> 
craig@Greezy:~$ skype
Segmentation fault (core dumped)


Any suggestions.
Thanks

---

### Post by aktiwers on 2008-10-02
Thanks!

Edit: Oh it did not work..  I get this error in Intrepid (8.10) :
> 
aktiwers@HAL2:~$ skype
skype: error while loading shared libraries: libQtCore.so.4: cannot open shared object file: No such file or directory
aktiwers@HAL2:~$ 


---

### Post by frunns on 2008-10-03
> **aktiwers said:**
> Thanks!

Edit: Oh it did not work..  I get this error in Intrepid (8.10) :

Look just a few posts up.

---

### Post by frunns on 2008-10-03
> **Soarer said:**
> Tried the new version (thanks Cappy) but I get:

```
~$ skype
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)
```

The error happens when I try to use the call test service.

Use the alternate skype version Cappy mentions. Skype-static-oss or something like that...

---

### Post by ephro on 2008-10-03
> **frunns said:**
> Use the alternate skype version Cappy mentions. Skype-static-oss or something like that...

This bug comment should fix your problems:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6)


Ephro

---

### Post by samperlmutar on 2008-10-03
> **ephro said:**
> This bug comment should fix your problems:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6)


Ephro

thank you so much....skype works perfectly now. 

the sound quality was terrible on the oss version for me, but with the regular package it's great.

---

### Post by neil6412 on 2008-10-05
Hello,

Have seemingly successfully installed Skype - the icon appears under Applications / Internet / menu - however when I click on aforementioned icon, nothing happens.  Any suggestions welcome.

Thanks
Neil

" neil@neil-laptop:~$ sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i --force-all skype-install.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p libqtgui4; sudo getlibs /usr/bin/skype
[sudo] password for neil: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
ia32-libs is already the newest version.
lib32asound2 is already the newest version.
libasound2-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2008-10-05 08:09:29--  [http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
Resolving boundlesssupremacy.com... 209.123.149.151
Connecting to boundlesssupremacy.com|209.123.149.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6498 (6.3K) [text/plain]
Saving to: `getlibs-all.deb'

100%[======================================>] 6,498       --.-K/s   in 0.1s    

2008-10-05 08:09:30 (51.3 KB/s) - `getlibs-all.deb' saved [6498/6498]

--2008-10-05 08:09:30--  [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
Resolving [www.skype.com](www.skype.com)... 204.9.163.136
Connecting to [www.skype.com|204.9.163.136|:80](www.skype.com|204.9.163.136|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb) [following]
--2008-10-05 08:09:30--  [http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb)
Resolving download.skype.com... 194.192.199.202, 78.141.176.34, 78.141.176.35
Connecting to download.skype.com|194.192.199.202|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15504764 (15M) [application/octet-stream]
Saving to: `skype-install.deb'

100%[======================================>] 15,504,764   140K/s   in 1m 44s  

2008-10-05 08:11:15 (145 KB/s) - `skype-install.deb' saved [15504764/15504764]

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 155280 files and directories currently installed.)
Preparing to replace skype 2.0.0.72-1 (using skype-install.deb) ...
Unpacking replacement skype ...
dpkg: skype: dependency problems, but configuring anyway as you request:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
Setting up skype (2.0.0.72-1) ...
(Reading database ... 155280 files and directories currently installed.)
Preparing to replace getlibs 2.06 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (2.06) ...
The following i386 packages will be installed: libqtgui4
Continue [Y/n]? Y
Downloading ...
Installing libraries ...
This application isn't missing any dependencies "

---

### Post by Odisej on 2008-10-05
I am using Intrepid (64) but cannot get skype to work using instructions at the beginning of this thread. Like previous poster noticed Skype does not start if clicked (but does appear in the menu). If started from terminal I get the following error:

> Fatal: Cannot mix incompatible Qt libraries
Aborted (core dumped)

---

### Post by Cappy on 2008-10-05
> **Odisej said:**
> I am using Intrepid (64) but cannot get skype to work using instructions at the beginning of this thread. Like previous poster noticed Skype does not start if clicked (but does appear in the menu). If started from terminal I get the following error:

Try
```
sudo getlibs -p libqtcore4 libqtgui4
```

I'm guessing the ia32-libs included an older version than the one in libqtgui4.

---

### Post by sunny_nwho on 2008-10-05
even i have the same error with the QT4 Libraries. I use ubuntu 8.10 beta. Any help would be great

---

### Post by samperlmutar on 2008-10-06
okay. skype works great, no problems whatsoever.

but now the ubuntu update manager is trying to update the skype-common package, but keeps showing an error and doesn't update.

---

### Post by briancb on 2008-10-06
I had Skype working perfectly on a previously upgraded Heron to Intrepid via Upgrade Manager. 

I had to do a clean install because of Nvidia driver problems and now Skype won't work. 

Maybe the best way would be to clean install Hardy install static-skype get it working and then do a Upgrade via Upgrade Manager.

I solved all my problems by downloading 64bit 8.04 (not 8.04.1) merging my Home folder from previous install, installing skype-static and using upgrade manager from then on.

Got all updates and Skype is still working perfectly.

---

### Post by sifar786 on 2008-10-06
> **Cappy said:**
> Special Thanks To: jasnix

[https://developer.skype.com/LinuxSkype](https://developer.skype.com/LinuxSkype)
The skype EULA: [http://www.skype.com/company/legal/eula/index.html](http://www.skype.com/company/legal/eula/index.html)

If you get the error

there is a fix available here: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6) (link from [ephro]("http://ubuntuforums.org/member.php?u=227171"))

**Copy and paste the block of code into your terminal to use. The terminal can be found at *Applications-->Accessories-->Terminal***
[SIZE="5"]
[CENTER]**Intrepid (8.10) install:**[/CENTER][/SIZE]



[SIZE="5"]
[CENTER]**Hardy LTS (8.04) install:**[/CENTER][/SIZE]

**Install directly from the website:**


**Medibuntu's Repositories:**
Medibuntu offers skype, which can be added to your repositories here: [Medibuntu]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f")
You can then install skype by using your Synaptic Package Manager to search for "skype" or ```
sudo apt-get install skype
```

For users with sound problems due to PulseAudio, Medibuntu also offers the package "skype-static-oss". Once installed, skype can be run through pulse audio with "padsp skype".

[SIZE="5"]
[CENTER]**Gutsy (7.10), Feisty (7.04), and Edgy (6.10) installs:**[/CENTER][/SIZE]


**64-bit install (or upgrade) skype 2.0 (with video):**


**64-bit webcam problems**:
See here [http://ubuntuforums.org/showthread.php?t=634393](http://ubuntuforums.org/showthread.php?t=634393) for instructions on how to get your webcam to work if it doesn't.


After installing Skype you can run it from your (_Applications-->Internet_) Menu at the top left of your screen.


[SIZE="5"][CENTER]**Dapper LTS (Ubuntu 6.04) install:**[/CENTER][/SIZE]

(This section may be outdated)

**AMD64 (64-bit) static :**
```

sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2
wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
wget http://www.skype.com/go/getskype-linux-static
tar -xvjf skype_static*.tar.bz2
cd skype_static*
sudo mv skype /usr/bin/
sudo mkdir /usr/share/skype
sudo mv sounds /usr/share/skype/
sudo mv icons /usr/share/skype/
sudo cp /usr/share/skype/icons/SkypeBlue_48x48.png /usr/share/icons/skype.png
sudo cp /usr/share/icons/skype.png /usr/share/pixmaps/skype.png
sudo mv skype.desktop /usr/share/applications/
cd ..
sudo rm -rf skype_static*
sudo getlibs /usr/bin/skype

```

**i386 (32-bit) static :**
```

sudo apt-get install libsigc++-2.0-0c2a libdbus-1-2
wget http://www.skype.com/go/getskype-linux-static
tar -xvjf skype_static*.tar.bz2
cd skype_static*
sudo mv skype /usr/bin/
sudo mkdir /usr/share/skype
sudo mv sounds /usr/share/skype/
sudo mv icons /usr/share/skype/
sudo mv skype.desktop /usr/share/applications/
cd ..
sudo rm -rf skype_static*

```

If it fails to run please run "skype" in the terminal and post the output with your question.
I am using ubuntu 8.04.1 desktop 32 bit version. i installed skype as you suggested but it does not run. when i ran it through terminal, i got this error msg:

skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory

Please advice.

regards,

---

### Post by Cappy on 2008-10-06
The instructions were for 64-bit. 32-bit users only need to download and click on the skype deb from their site.

You can easily install the missing libraries using
```
sudo apt-get install libqt4-gui libqt4-core
```

---

### Post by lamborghiniwang on 2008-10-07
I am having difficulty to input Chinese in Skype 2.0.0.72. I have scim-bridge installed and it works in all other applications(firefox, konqueror, pidgin), but in Skype Ctrl-Space doesn't do anything.
I tried both the static version and the dynamic-link version from medibuntu on my Hardy 64-bit, and both have the same problem.
Could anyne give me some advice?

---

### Post by buntu_hugenewbie11 on 2008-10-07
I installed skype using the method from page 1 of this thread.
Now I would like to install using the medibuntu repository as it seems like it will be easier to update.
How do I safely uninstall the skype I installed from page 1 of this thread?

---

### Post by rasmus91 on 2008-10-07
I'd also like to know that, cos my installation doesn't work at all... :(

It says: > FATAL: cannot mix incompatible Qt libraries

---

### Post by dzrtmn on 2008-10-11
Hi,

I followed the suggestion for installing skype in Hardy Heron. The first two commands worked OK, but the last one gave the following results:

[INDENT]sudo dpkg -i --force-all skype-install.deb 
dpkg - warning, overriding problem because --force enabled: 
 package architecture (i386) does not match system (amd64) 
Selecting previously deselected package skype. 
(Reading database ... 108320 files and directories currently installed.) 
Unpacking skype (from skype-install.deb) ... 
dpkg: skype: dependency problems, but configuring anyway as you request: 
 skype depends on libqt4-core (>= 4.2.1); however: 
  Package libqt4-core is not installed. 
 skype depends on libqt4-gui (>= 4.2.1); however: 
  Package libqt4-gui is not installed. 
Setting up skype (2.0.0.72-1) ... [/INDENT]

What is the impact of libqt4-core and libqt4-gui not being installed?

Thanks...

---

### Post by johnystevenson on 2008-10-18
hi there would like to thank cappy and all who contributed to this how to.  I don't have skype completely configured correctly (sound issues), but am delighted thus far with my progress.

cheers
johny

---

### Post by emecas on 2008-10-18
:) 
Thanks Cappy
Skype is working!!!

---

### Post by Milleman on 2008-10-19
I'm posting this, as I used it myself to install Skype 2.0 with video on 64-bit Ubuntu:

> cd; sudo apt-get install ia32-libs lib32asound2; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-beta-ubuntu;](http://www.skype.com/go/getskype-linux-beta-ubuntu;) sudo dpkg -i getlibs-all.deb; sudo dpkg -i --force-all skype-install.deb; sudo getlibs /usr/bin/skype; cd ~

(Above copied from [http://ubuntuforums.org/showthread.php?t=432295]("http://ubuntuforums.org/showthread.php?t=432295"))

See here [http://ubuntuforums.org/showthread.php?t=634393]("http://ubuntuforums.org/showthread.php?t=634393") for instructions on how to get your webcam to work.

/Mill

---

### Post by parakeets11 on 2008-10-20
I just installed Ubuntu 8.10 and I tried installing skype.  It installed, but I can't make calls, it says that there is a problem with audio capture.  Anyone else have this problem?

---

### Post by johnystevenson on 2008-10-20
i think there is a lot of people with this problem....including me:)

---

### Post by macabro22 on 2008-10-20
> **parakeets11 said:**
> I just installed Ubuntu 8.10 and I tried installing skype.  It installed, but I can't make calls, it says that there is a problem with audio capture.  Anyone else have this problem?

This problem happens when there are applications accessing your sound card. Skype needs to be the only application accessing the audio device in order for that problem to be solved. For now at least.

---

### Post by parakeets11 on 2008-10-21
Thing is, it works in KDE right from install.  Now, I don't like KDE but if I want my Skype, I have to suffer it.  But I somehow managed (this was a couple months ago) to get Skype in AMD 64 GNOME on my laptop, Running Ubuntu Hardy 8.04.  It _sometimes_works if you install the skype-oss package, but the sound is fugly.  Untill then, ill deal with KDE.  But the new KDE lags for me and I don't know why :S.

---

### Post by macabro22 on 2008-10-21
> **parakeets11 said:**
> Thing is, it works in KDE right from install.  Now, I don't like KDE but if I want my Skype, I have to suffer it.  But I somehow managed (this was a couple months ago) to get Skype in AMD 64 GNOME on my laptop, Running Ubuntu Hardy 8.04.  It _sometimes_works if you install the skype-oss package, but the sound is fugly.  Untill then, ill deal with KDE.  But the new KDE lags for me and I don't know why :S.

Skype works fine here under the condition no other application is accessing the audio device simultaneously. I am using gnome.

---

### Post by parakeets11 on 2008-10-22
I know but it does this for me right from start-up.  I have no other applications running but it will still not work.

---

### Post by Vadi on 2008-10-27
Not sure if this was known... [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)

(its still a 32bit binary, just in a nice 64bit .deb)

---

### Post by thenasko on 2008-10-28
I am using Intrepid and skype seems to be broken. I get the following messages.
```

nasko@serre:~$ ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm_dmix.c:947:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib ../../../src/pcm/pcm_dsnoop.c:532:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm_dmix.c:947:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib ../../../src/pcm/pcm_dsnoop.c:532:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm_dmix.c:947:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib ../../../src/pcm/pcm_dsnoop.c:532:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream

```

I verified bluez-alsa is installed and getlibs says all dependencies are installed.

---

### Post by mkarnicki on 2008-10-31
Just wanted to report that after upgrading to hardy 8.10 and adding the medibuntu repository, a simple
$sudo apt-get install skype
worked for me :) yay. Using HP tx1320us (AMD64). I can even see the pictures of the users, without any additional effort ^_^

---

### Post by macabro22 on 2008-10-31
> I can even see the pictures of the users, without any additional effort ^_^

You can?

Whats the skype version? I wonder why I can't

---

### Post by Cappy on 2008-10-31
> **macabro22 said:**
> You can?

Whats the skype version? I wonder why I can't

The medibuntu 64-bit package is skype static, which lets you see contact pictures but some people also suffer from low quality sound.

---

### Post by speedothebrief on 2008-10-31
Nice Work!

---

### Post by davidw89 on 2008-10-31
THIS IS BROKEN
Can't make any calls
There's an error: Problem with audio codec!

What do i do?
Ubuntu 8.10 x64

---

### Post by fferreira on 2008-10-31
% sudo apt-get install skype

% skype 
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so

%


It used to work under Hardy 64bits. On Intrepid 64 bits it is broke...

Cheers

---

### Post by Cappy on 2008-11-01
Try ```
sudo getlibs -p bluez-alsa
``` and see if that helps.

---

### Post by Temmink on 2008-11-01
Same issue here, 'sudo getlibs -p bluez-alsa' did not help, any other ideas?

---

### Post by mkarnicki on 2008-11-01
> **Cappy said:**
> The medibuntu 64-bit package is skype static, which lets you see contact pictures but some people also suffer from low quality sound.

Correct. I must explain myself - I didn't know the Medibuntu repos had the old version 1.6. So I visited skype.com/download and got the static version, and followed few simple instructions in the README provided. Good luck!

**@Temmink** Have you tried:
$ sudo apt-get build-dep skype

---

### Post by fferreira on 2008-11-01
> **Cappy said:**
> Try ```
sudo getlibs -p bluez-alsa
``` and see if that helps.

Didn't work, other error message though. 
```
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
```


Starting to consider going back to Hardy...

Cheers

---

### Post by ubun_two on 2008-11-02
Same problem for me.  I can't get Skype to work under 64bit Intrepid.

I manged to get sound output to work by going to preference and changing the sound options from default to other things (I went from the top to bottom of the list and one of them worked), but it's still useless because microphone doesn't work.

/usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so file is clearly missing.  I got these files from Hardy installation and copied over to this location, and I got the exact same error fferreira got.

---

### Post by oceallaighm on 2008-11-02
After 5 months, I took the plunge and moved from Vista Home Premium to Ubuntu 8.10 Intrepid Ibex x86_64 AMD.

For Skype I followed the instructions and it installed as it should. The program runs so I can't complain, its a start.

It wasn't working so in Options, Sound Devices, I changed all of the items to HDA ATI SB (hw:SB,0), with this I got the test sound to work. I then made a test call, note it appears to work, as there is a longer gap on the call duration before I get the Skype persons voice, than I had got previously but I don't hear my own voice.

I can't get the sound recorder to work in order to test the microphone as it crashes immediately.

In sound, open volume control, HDA ATI SB (Alsa Mixer) is shown. 

I am going to attach 2 screen shots of the sound device settings in Skype and of the sound preferences in the Control Centre.

Is this an Alsa v's Pulseaudio thing?

Many thanks.

---

### Post by ubun_two on 2008-11-02
> **oceallaighm said:**
> 
Is this an Alsa v's Pulseaudio thing?



I don't know.  I tried removing pulse audio, but Skype still didn't work for me.  I got the sound output, but I can't talk into it.

Here is the bug entry of problem in question:

[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/285412]("https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/285412")

---

### Post by gerula on 2008-11-03
Thanks, Cappy! It worked for me (Ubuntu 8.10 64 bit)

---

### Post by oceallaighm on 2008-11-03
> **oceallaighm said:**
> 

I can't get the sound recorder to work in order to test the microphone as it crashes immediately.

In sound, open volume control, HDA ATI SB (Alsa Mixer) is shown. 

Is this an Alsa v's Pulseaudio thing?

Many thanks.

I installed Audicity, I can get neither it nor the sound recorder to work. They are not recognising the microphone as an input device. Skype isn't the problem, it just happens to be the only application that I use at the moment that requires sound input. Note sound out put works, I can listen to music.

How do I go about checking out the sound system in Ubuntu 8.10?

---

### Post by Foggy on 2008-11-03
Further to the previous two comments/queries I have installed Skype, on a fresh install of 8.10, copy and paste as described, I can hear the test sound beautifully on Skype but can not hear my microphone. On Volume control, I have opened "Playback Capture feedback" but on "Recording Line in" the Microphone icon will not stay un-muted. Can someone please explain how to or what preferences should be visible.
My thanks in advance.
BJ

---

### Post by aktiwers on 2008-11-03
Installed skype fine using Mediubuntu repos.

---

### Post by oceallaighm on 2008-11-03
> **Foggy said:**
> Further to the previous two comments/queries I have installed Skype, on a fresh install of 8.10, copy and paste as described, I can hear the test sound beautifully on Skype but can not hear my microphone. On Volume control, I have opened "Playback Capture feedback" but on "Recording Line in" the Microphone icon will not stay un-muted. Can someone please explain how to or what preferences should be visible.
My thanks in advance.
BJ

As they say a picture says a thousand words. I am attaching 3 screen shots of what I get for output devices when I double click on the sound icon. 

One clearly shows that volume control is off or muted, changing this does not make a difference, as when you go back in, it is still shown as off or muted. So how do I turn it on or un-mute it, if that is a stupid question?

The reason for the 3 screen shots is that I would like to know which input option does Skype use? 

Please also refer to the screen shots on the earlier posting, as nobody has said if these settings were correct or not?

Many thanks.

**EXTRA INFORMATION:-**

There appears to be several threads going on at present in other areas of this forum. It would appear that the problem is not just in Ubuntu 8.10 or just in the 64bit version, nor just on specific hardware. The problem appears to be possibly a bug with the alsa mixer or alsa lib files. 

Please find the links below, that I have found so far.

[http://ubuntuforums.org/showthread.php?t=956565](http://ubuntuforums.org/showthread.php?t=956565)

[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/290121](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/290121)

[http://weblogs.inf.udp.cl/nboettcher/31/10/2008/configurar-microfono-en-ubuntu-intrepid-ibex-en-equipo-dell-xps-m1330-m1530/](http://weblogs.inf.udp.cl/nboettcher/31/10/2008/configurar-microfono-en-ubuntu-intrepid-ibex-en-equipo-dell-xps-m1330-m1530/)

Regards

---

### Post by iason86 on 2008-11-06
worked perfectly thanks a lot:)

---

### Post by ubun_two on 2008-11-06
> **iason86 said:**
> worked perfectly thanks a lot:)

So what did you do exactly?  I still can't get mic in on Skype working.

---

### Post by toddh on 2008-11-06
After installing 8.10 I did not have audio playback or my mic working.  So I've accomplished both with the following steps:

added the third party software sources:
system>administration>software sources

 sudo apt-get install skype
 sudo getlibs -p bluez-alsa

selected usb source for mic (system>preferences>sound preferences):
sound capture: ak5370 usb

configured Skype Options (ctrl+o) to use same source:
sound devices: sound in ak5370

sound and playback are both working for me now.

---

### Post by comorbid on 2008-11-07
Just made my test call, everything seems to be working just fine.

---

### Post by Stormx on 2008-11-07
Not working after medibuntu install.

ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so

Help?

---

### Post by Frugoo Scape on 2008-11-09
Thanks so much. It works perfect.

---

### Post by fferreira on 2008-11-10
> **Stormx said:**
> Not working after medibuntu install.

ALSA lib ../../../src/pcm/pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so

Help?

Sound capture working fine... Skype not:

 skype
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)



any clue???

---

### Post by talkin on 2008-11-13
Everything works fine, but I don't see any avatars and I can't set mine.
Any solutions?

---

### Post by scourge on 2008-11-21
> **fferreira said:**
> Sound capture working fine... Skype not:

 skype
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)



any clue???

Had this same problem. It was solved by installing the skype-static-oss package from the Medibuntu repos.

---

### Post by dchurch24 on 2008-11-24
> **jespdj said:**
> Note, if you have a webcam, it's not going to work in Skype on Linux; the Linux version of Skype does not support video.

Has this changed now?

I just read this:

"64-bit users may need to upgrade their gspca or uvc drivers if their webcam is not being detected by Skype. "

on Skype's website, it seems to imply that webcams are now supported?

---

### Post by lamborghiniwang on 2008-11-26
Has anyone been able to using SCIM in Skype running in a 64-bit Ubuntu? SCIM works in every applications on my 64-bit Hardy except Skype.

---

### Post by blizzard30 on 2008-11-26
Works lovely.It even show in shortcuts.Latest version is 2.0?

---

### Post by fferreira on 2008-11-29
> **scourge said:**
> Had this same problem. It was solved by installing the skype-static-oss package from the Medibuntu repos.

It finally worked!!!!!

---

### Post by ken78724 on 2008-11-29
thanks Crappy! I asked about this in my intro to the 64 bit social group this afternoon. Kenneth

---

### Post by Washington Irving on 2008-12-03
So just to clarify, Skype can be installed on 64-bit Intrepid with full functionality. Webcam and sound both working fine?

---

### Post by macabro22 on 2008-12-03
> **Washington Irving said:**
> So just to clarify, Skype can be installed on 64-bit Intrepid with full functionality. Webcam and sound both working fine?

Almost. Webcam plays fine. Audio does too but only on the left speaker and never when another app is accessing the sound card. That is, unless you disable pulseaudio.

---

### Post by efeurich on 2008-12-06
Muchos gracias !!

---

### Post by Lupusceleri on 2008-12-10
Great guide, worked like a charm.. :)

---

### Post by JunCTionS on 2008-12-12
thanks :)

---

### Post by mhenriday on 2008-12-22
After following the procedure outlined in **Nullhead**'s [***[COLOR="Blue"]_Creative 1.00 driver guide_[/COLOR]***]("http://ubuntuforums.org/showthread.php?t=870001") thread, I finally managed to get my **Creative Soundblaster X-Fi** to work with my 64-bit **Intrepid** setup. I then decided to return to my eternal (?) **Skype** problem on **Ubuntu** and proceeded to install the **2.0.0.72-0medibuntu4** version via **Medibuntu** and **Synaptic**. Alas, when I attempted to ring others via **Skype**, I received a notice to the effect that there is a problem with Audio Playback (see the first screenclip below). I then attempted to remedy the problem by configuring my sound devices («Options» &#8594; «Sound Devices»). With the configuration shown in the second screenclip below, I discovered that I was now able to ring up the **Skype Test Call** and hear what the young lady had to say, but not my own voice. None of the other settings available to me worked as well. In the midst of these trials, a friend, who had noticed that I was registered as being online, rang me up, but alas, we were unable to converse - I could hear him perfectly well, but he couldn't hear me. My headset and microphone work quite well in the **Skype 4.0 beta** on **Windows**, so that particular piece of hardware is unlikely to be the problem. Any suggestions as to how to proceed ?...

Henri

---

### Post by MikeDK on 2008-12-22
Hi first of, do you have your whole system set up with pulseaudio, alsa or oss?

If you have pulseaudio set up, under System=>Preferences=>Sound, you should try setting your with something (plughw:x-fi,0) in your Sound in device or in my case, HDA Nvidia(plughw:NVidia,0) maybe that'll do the trick, just maybe, dont know how it is with those X-Fi cards.

Kind Regards MikeDK

Good Luck

feel free to send me a message on skype, on how it went? if im not answering right away ill get back to you asap.

---

### Post by weatherguyto on 2008-12-23
Hi Cappy,

Will this procedure below work for Ubuntu 8.10 64bit also?
Is there any new updates to this procedure since this update?
Would you mind sending me an email at:weatherguyto@gmail.com
on an updated procedure to install skype on 64bit Ubuntu.

Thanks so much,
weatherguyto


sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2
wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
wget [http://www.skype.com/go/getskype-linux-static](http://www.skype.com/go/getskype-linux-static)
tar -xvjf skype_static*.tar.bz2
cd skype_static*
sudo mv skype /usr/bin/
sudo mkdir /usr/share/skype
sudo mv sounds /usr/share/skype/
sudo mv icons /usr/share/skype/
sudo cp /usr/share/skype/icons/SkypeBlue_48x48.png /usr/share/icons/skype.png
sudo cp /usr/share/icons/skype.png /usr/share/pixmaps/skype.png
sudo mv skype.desktop /usr/share/applications/
cd ..
sudo rm -rf skype_static*
sudo getlibs /usr/bin/skype

---

### Post by mhenriday on 2008-12-23
*Dav*, **MikeDK**, and thanks for your speedy response ! I'm running **ALSA**, but even if I install the repository **Pulseaudio** files in addition, I still can't hear my own voice when I ring up **Skype Test Call**. As I mentioned in my earlier posting, I do, however, hear the operator's voice loud and clear. I haven't yet tried uninstalling the **ALSA** files and running solely on **Pulseaudio** - it took me more than a year to get adequate sound from the **Soundblaster** card, which has made me somewhat more diffident with regard to bold experiments than was my wont....

Henri

---

### Post by sbuhlig on 2008-12-23
Works great!

Thanks

---

### Post by RunLengthLimited on 2009-01-04
$ sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64;](http://www.skype.com/go/getskype-linux-ubuntu-amd64;) sudo dpkg -i skype-install.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p libqtcore4 libqtgui4 bluez-alsa 
[sudo] password for [user]: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
lib32asound2 is already the newest version.
libasound2-plugins is already the newest version.
The following packages were automatically installed and are no longer required:
  libswt-gnome-gtk-3.4-jni libswt-cairo-gtk-3.4-jni libswt-mozilla-gtk-3.4-jni
  tcl8.5 lib32v4l-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2009-01-04 16:32:45--  [http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
Resolving boundlesssupremacy.com... 209.123.149.151
Connecting to boundlesssupremacy.com|209.123.149.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6498 (6.3K) [text/plain]
Server file no newer than local file `getlibs-all.deb' -- not retrieving.

--2009-01-04 16:32:46--  [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)
Resolving [www.skype.com](www.skype.com)... 204.9.163.162
Connecting to [www.skype.com|204.9.163.162|:80](www.skype.com|204.9.163.162|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://download.skype.com/linux/skype_ubuntu-2.0.0.72-1_amd64.deb](http://download.skype.com/linux/skype_ubuntu-2.0.0.72-1_amd64.deb) [following]
--2009-01-04 16:32:46--  [http://download.skype.com/linux/skype_ubuntu-2.0.0.72-1_amd64.deb](http://download.skype.com/linux/skype_ubuntu-2.0.0.72-1_amd64.deb)
Resolving download.skype.com... 204.9.165.83, 212.72.53.130, 204.9.165.82
Connecting to download.skype.com|204.9.165.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15506542 (15M) [application/octet-stream]
Saving to: `skype-install.deb'

100%[======================================>] 15,506,542   149K/s   in 1m 57s  

2009-01-04 16:34:43 (130 KB/s) - `skype-install.deb' saved [15506542/15506542]

Selecting previously deselected package skype.
(Reading database ... 143738 files and directories currently installed.)
Unpacking skype (from skype-install.deb) ...
Setting up skype (2.0.0.72-1) ...
(Reading database ... 143873 files and directories currently installed.)
Preparing to replace getlibs 2.06 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (2.06) ...
The following i386 packages will be installed: libqtcore4 libqtgui4 bluez-alsa
Continue [Y/n]? y
Downloading ...
Installing libraries ...

$ uname -a
Linux megablast 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

$ skype
Aborted

???

---

### Post by ScottNZ on 2009-01-11
Thanks Cappy!

This Intrepid instructions worked without a hitch. Video works, and after manually selecting the audio devices, sound works as well.

Nice and simple.

Scott

---

### Post by smorgado on 2009-01-16
I followed Cappy´s  direction but I get this message when I log in skype 

ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Error de entrada/salida(5)

---

### Post by smorgado on 2009-01-16
I forgot to say it was in 8.10 intrepid

---

### Post by J&amp;R on 2009-01-17
and now i can remove ia32-libs from my computer ,thank you

---

### Post by andresmh on 2009-01-20
It failed to install for me on Jaunty 64-bit. THis is what I got: 

```
ubuntu@ubuntu:~$ sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb http://www.skype.com/go/getskype-linux-ubuntu-amd64; sudo dpkg -i skype-install.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p libqtcore4 libqtgui4 bluez-alsa 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0 lib32asound2
E: Package ia32-libs has no installation candidate
--2009-01-20 13:49:11--  http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
Resolving boundlesssupremacy.com... 174.132.151.2
Connecting to boundlesssupremacy.com|174.132.151.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6498 (6.3K) [text/plain]
Server file no newer than local file `getlibs-all.deb' -- not retrieving.

--2009-01-20 13:49:16--  http://www.skype.com/go/getskype-linux-ubuntu-amd64
Resolving www.skype.com... failed: Name or service not known.
wget: unable to resolve host address `www.skype.com'
dpkg-deb: unexpected end of file in version number in skype-install.deb
dpkg: error processing skype-install.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 skype-install.deb
(Reading database ... 103462 files and directories currently installed.)
Preparing to replace getlibs 2.06 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (2.06) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0 lib32asound2
E: Package ia32-libs has no installation candidate
The following i386 packages will be installed: libqtcore4 libqtgui4 bluez-alsa
Continue [Y/n]? 
Downloading ...
Installing libraries ...
ubuntu@ubuntu:~$ skype
bash: skype: command not found
ubuntu@ubuntu:~$ sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb http://www.skype.com/go/getskype-linux-ubuntu-amd64; sudo dpkg -i skype-install.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p libqtcore4 libqtgui4 bluez-alsa 

```

---

### Post by Vadi on 2009-01-20
Try [https://help.ubuntu.com/community/Skype#AMD64](https://help.ubuntu.com/community/Skype#AMD64) ?

---

### Post by Cappy on 2009-01-20
> **andresmh said:**
> It failed to install for me on Jaunty 64-bit. THis is what I got: 


Enable the Universe Repos.

---

### Post by eyeJ on 2009-01-22
Thank you!

---

### Post by nickolasemp on 2009-02-07
Worked perfectly in 8.04 amd64..! I am so happy!

---

### Post by bakulkrishana on 2009-02-07
Please make sure that you have selected 'pluse' for all three options.
[LIST]
[*]Sound In
[*]Sound Out
[*]Ringer
[/LIST]

and have the fix installed described in post 1.

Thanks,
Bakul

---

### Post by arsen13 on 2009-02-27
I'm getting the same error as smorgado does, can someone help me?
> ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)

the problem is with soundinput as i can hear the others well, nothing from the list of soundinput works.

Thanks

---

### Post by shashtheash95 on 2009-03-02
Thanks a lot for the instructions!!!
Worked excellently!!!!

Thanks Again!!

---

### Post by drtre on 2009-03-05
Maybe it's just me but I can test my webcam in the options/video devices but still no option is available for video calls.

---

### Post by 3Miro on 2009-03-06
> **drtre said:**
> Maybe it's just me but I can test my webcam in the options/video devices but still no option is available for video calls.

I think you should first call the person and then let them see you. On the call window there should be an option to share your camera. The only issue that I have is that it does not work for conference calls.

---

### Post by drtre on 2009-03-06
> **3Miro said:**
> I think you should first call the person and then let them see you. On the call window there should be an option to share your camera. The only issue that I have is that it does not work for conference calls.

While dialling I don't c any video option. U mean the call must be received by the other one then the option appears?

---

### Post by 3Miro on 2009-03-06
> **drtre said:**
> While dialling I don't c any video option. U mean the call must be received by the other one then the option appears?

Yes, they have to receive the call and at the bottom of the call window you will see an option to share the video. It is right on the line with hag up, start chat and other options. If you can successfully test the video in skype this should work.

---

### Post by drtre on 2009-03-06
> **3Miro said:**
> Yes, they have to receive the call and at the bottom of the call window you will see an option to share the video. It is right on the line with hag up, start chat and other options. If you can successfully test the video in skype this should work.

Thank you man. And how come you can't use it in conference?

---

### Post by superalanliu on 2009-03-22
thanks man! works great!

---

### Post by skarosg3 on 2009-04-07
Great work man! thanks

---

### Post by Darkade on 2009-04-12
How is it that this package is not listed in the skype download site?

[http://www.skype.com/download/](http://www.skype.com/download/)

I mean it's great to have it up and running but why isn't the 64bit pacakge listed in the "official" list?

---

### Post by emotional1 on 2009-04-19
I am having difficulty with Skype on 8.10 64bit.  I found this work around but don't know how to copy the file into the directory I created, not sure what 
the command to copy/paste  I am using HP tx1220 64-bit thanks in advance

Another workaround that works for me:
1. Create /etc/ld.so.conf.d/alsa32.conf with the following contents:
/usr/lib32/alsa-lib

2. Create /etc/ld.so.conf.d/alsa64.conf with the following contents:
/usr/lib/alsa-lib

3. sudo ldconfig

4. Open /usr/share/alsa/pulse.conf in the editor and remove the "/usr/lib/alsa-lib/" prefix from the libasound_module_conf_pulse.so file.

---

### Post by kartook on 2009-05-08
Good joo it works fine for me "):guitar:

---

### Post by xbalanque on 2009-05-21
hm ... used to work on 8.10, but not working on 9.04. Sound freezes often ... sometimes the whole skype freezes.

When running from the command line I get errors like:

ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

I did run the sudo getlibs -p bluez-alsa.

Any ideas anyone ?

thanks!

---

### Post by Pug505GR on 2009-05-24
I've been running Skype with no real problems under 8.04, with the exception of using the internal mike on my Presario laptop. At the time when I installed it, it was accepted that the internal mike of these machines couldnt be used under linux.

Have there been any advances on this? I've just moved up to 9.04 64 bit and seem to have the audio playback working through the internal speakers, but not the microphone.

Also my Skype usb headset doesn't seem to be working either, although dmesg does recognise it. It doesnt seem to rate a mention on any audio options.

Thanks

Matt

---

### Post by merlinus on 2009-05-24
I just installed 64-bit Skype, and my USB headset works fine.  You might check the Options in the software whilst online.

---

### Post by patrick.fehr on 2009-05-27
Here( Jaunty Jackalope (9.4) on a 64Bit architecture) it works beautiful with this 2 liner:

wget [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)
sudo dpkg -i skype_ubuntu-2.0.0.72-1_amd64.deb



best regards
Patrick

---

### Post by Goddard on 2009-06-03
Works great thanks.

---

### Post by jimzhang on 2009-06-21
> **patrick.fehr said:**
> Here( Jaunty Jackalope (9.4) on a 64Bit architecture) it works beautiful with this 2 liner:

wget [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)
sudo dpkg -i skype_ubuntu-2.0.0.72-1_amd64.deb



best regards
Patrick

(Reading database ... 110171 files and directories currently installed.)
Unpacking skype (from skype_ubuntu-2.0.0.72-1_amd64.deb) ...
dpkg: error processing skype_ubuntu-2.0.0.72-1_amd64.deb (--install):
 trying to overwrite `/etc/dbus-1/system.d/skype.conf', which is also in package skype-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 skype_ubuntu-2.0.0.72-1_amd64.deb


I tried with no luck... need help, thanks

---

### Post by Deicider on 2009-06-29
mic doesnt work in skype or in anything else in linux :S

---

### Post by macabro22 on 2009-06-29
> **Deicider said:**
> mic doesnt work in skype or in anything else in linux :S

Thats one unnecessary extrapolation of a particular case. Try harder.

---

### Post by gnu-buntu on 2009-07-04
Hello,

I apologize for the length of this posting, but I've worked on the problem for a long time and am very confused and frustrated.  I use skype all the time on windows, and I have used it via linux running on vmware.  Also, I know enough about linux to be very dangerous -- to my system.  I am trying to drop windows, but in order to do that, I really need skype, which I can't seem to get working.  

Unfortunately, it seems that I've entered configuration hell, as I don't have a very good grasp of ubuntu package management.  (The current advice is that I should stick with apt(-get) and synaptic for package managers.)

My current system: 
HP dv6770se laptop, AMD Turion 64-bitX2, 2.1 GHz, 3 GB RAM, 250 GB hard drive
Kubuntu Jaunty 9.04

I would prefer to run 64-bit skype, but I'll use whatever I can get -- that works.

The issues seem related to 64-bit vs. 32-bit and various bits pertaining to medibuntu, pulse, alsa and libasound, whatever they are.  
I've already installed, uninstalled and reinstalled various skype-related packages.  
Most recently I followed this approach, as it's simple, it comes straight from skype, and it promises to be 64-bit:
   Originally Posted by patrick.fehr View Post
   Here( Jaunty Jackalope (9.4) on a 64Bit architecture) it works beautiful with this 2 liner:
   Quote:
   wget [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)
   sudo dpkg -i skype_ubuntu-2.0.0.72-1_amd64.deb

...but I get this error repeated multiple times:
   ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

Now someone wrote this...
   (Post 1) Another workaround that works for me:
   1. Create /etc/ld.so.conf.d/alsa32.conf with the following contents:
   /usr/lib32/alsa-lib
   2. Create /etc/ld.so.conf.d/alsa64.conf with the following contents:
   /usr/lib/alsa-lib
   3. sudo ldconfig
   4. Open /usr/share/alsa/pulse.conf in the editor and remove the 
      "/usr/lib/alsa-lib/" prefix from the libasound_module_conf_pulse.so
      file

I did all those things except #4, since I don't seem to have a /usr/share/alsa/pulse.conf file.  (Why not?)  I do have relevant files:
   /usr/lib32/alsa-lib/libasound_module_conf_pulse.so 
   /usr/lib/alsa-lib/libasound_module_conf_pulse.so

And someone else wrote...
   Re: HOWTO: Install Skype on 64-bit Ubuntu
   Please make sure that you have selected 'pulse' for all three 
   options.
      * Sound In
      * Sound Out
      * Ringer
   and have the fix installed described in post 1.

How and where do I select those 'pulse' options???

I'm happy to tear everything out (especially the 32-bit stuff) and start over, but first I'd really appreciate some clear, sage advice.  Please!

Thanks,
~Peter

---

### Post by Tigerkermit on 2009-07-09
Hi, I do have the same problem with the 64 bit Ubuntu and Skype.
Mic is working very silent only. Already tried to adjust but does not work.
Video is not working at all. When I start the Video, Skype close and stop.
Sound works well.
I have Vista on the same HW installed. With Vista there is no problem !

Any hint is welcome !

---

### Post by Seinfeld on 2009-07-09
Hi Tigerkermit,

As I understand. your sound works fine and only your mic does not work..Let me know if you cannot follow any step of the following and I will guide you again...
1. Open your volume control (Go to the sound icon and Open Volume Control)
2. Go the "option" tab and point your "input source" to be "Front Mic" if your mic is hooked to the front audio on you case or just "Mic" if otherwise.
3. Click "Preferences" and make sure that "Capture" is checked and its volume slider is at a reasonable range (This will appear in "Recording tab too"). Also make sure that the Input source is checked too of course..
4. Open Skype test call.. Make sure that your preferences in Skype points to your correct sound card in Sound In and Sound Out options on Skype preferences.
5. As for the video.. your camera MUST be seen by Skype in Video Devices option.. Is it ?? if so, Test it.. If not, then its driver has to be installed.. If you are using Hardy or later, it should see most of devices... Let me know..

Good Luck

---

### Post by macabro22 on 2009-07-09
Hi, I found this a while ago (can't remember where) and it fixed my problem with low mic capture volume. Try it out:

> I was able to quickly fix it by modifying my /etc/asound.conf. The idea
was to use ALSA's softvol dB-gain plugin to do a software mic boost and
pipe that to a new pulseaudio device "pulseboost" that can be used by
Skype etc.

After adding those lines below and rebooting, you should see a new
slider called "+50dB Mic Capture Volume" in gnome-volume-control's
Recording tab (if you don't see it, go to Preferences and check it).
Raise it to maximum (+50dB), or a bit below that in case the maximum
value clips your voice or captures too much noise in the environment.

In my case, Skype was able to list a new device named "pulseboost" in
its Options configuration dialog's SoundDevices tab. If you choose this
device for SoundIn, Skype can benefit from the +50dB softvol mic boost
in gnome-volume-control. I also chose it for my Skype's
soundout/ringing, but I think that's not required.

Is there a side-effect to this? Well, I guess that with this setup you
can only use the mic at one application at any time, because it directly
accesses the mic's hw:0,0, but at least you have a huge mic boost in
that application.

### my /etc/asound.conf:
pcm.pulseboost {
    type asym
    playback.pcm {
        type pulse
    }
    #software gain upto 50dB for digital microphone
    capture.pcm {
        type softvol
        slave.pcm "hw:0,0"
        #slave.pcm "pulse0"
        control {
            name "+50dB Mic Capture Volume"
            card 0
        }
        max_dB 50.0
    }
}
ctl.pulseboost {
  type pulse
}

I also added the line 'load-module module-alsa-source device=pulseboost'
to my /etc/pulse/default.pa, and renamed my ~/.asoundrc to avoid any
conflicts with my previous alsa configuration, but I think that's
unnecessary.

That would probably work with Hardy, Gutsy, Jaunty etc as well.

---

### Post by gnu-buntu on 2009-07-09
> **Seinfeld said:**
> Hi Tigerkermit,

As I understand. your sound works fine and only your mic does not work..Let me know if you cannot follow any step of the following and I will guide you again...
1. Open your volume control (Go to the sound icon and Open Volume Control)
2. Go the "option" tab and point your "input source" to be "Front Mic" if your mic is hooked to the front audio on you case or just "Mic" if otherwise.
3. Click "Preferences" and make sure that "Capture" is checked and its volume slider is at a reasonable range (This will appear in "Recording tab too"). Also make sure that the Input source is checked too of course..
4. Open Skype test call.. Make sure that your preferences in Skype points to your correct sound card in Sound In and Sound Out options on Skype preferences.
5. As for the video.. your camera MUST be seen by Skype in Video Devices option.. Is it ?? if so, Test it.. If not, then its driver has to be installed.. If you are using Hardy or later, it should see most of devices... Let me know..

Good Luck

Hi,

When I run Skype from the command line, I see this error:
> ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
... (repeated multiple times)

When I call numbers, it rings, connects, etc., but there is no sound output, and I can't tell about input.

My skype gui window is rather simple, and no volume control or sound icon are apparent.  However, it does have a "main menu" button, which can bring up an "Options" window with selections like General, Sound Devices, Video Devices, etc.

When I turned on "display technical call info" and made some test calls, it looked pretty happy, showing nothing unusual.

Sound Device (Sound In, Out, Ringing) options are:
       Default device
       - HDA NVidia (hw:NVidia:0)
       - HDA NVidia (plughw:NVidia:0)
       - HDA NVidia (hw:NVidia:1)
       - HDA NVidia (plughw:NVidia:1)
       - hdmi
       - headset
It's on "Default" for now.  I tried some NVidia combinations, but nothing worked.  When I chose "headset", it indicated "problems with audio" in the popup call box.

FWIW, When I test video, it displays a good, live image.

Skype works fine on this hardware under Vista.

So maybe sound isn't getting into and out of skype.  I'm using a simple headset, and there's no BlueTooth.  
I don't know anything about pulse audio or ALSA, so I'd appreciate any help to get skype working.  

Thanks,
~Peter

HP dv6770se laptop, AMD Turion 64-bitX2, 64-bit Kubuntu Jaunty 9.04

---

### Post by Tigerkermit on 2009-07-11
> **Seinfeld said:**
> Hi Tigerkermit,

As I understand. your sound works fine and only your mic does not work..Let me know if you cannot follow any step of the following and I will guide you again...
1. Open your volume control (Go to the sound icon and Open Volume Control)
2. Go the "option" tab and point your "input source" to be "Front Mic" if your mic is hooked to the front audio on you case or just "Mic" if otherwise.
3. Click "Preferences" and make sure that "Capture" is checked and its volume slider is at a reasonable range (This will appear in "Recording tab too"). Also make sure that the Input source is checked too of course..
4. Open Skype test call.. Make sure that your preferences in Skype points to your correct sound card in Sound In and Sound Out options on Skype preferences.
5. As for the video.. your camera MUST be seen by Skype in Video Devices option.. Is it ?? if so, Test it.. If not, then its driver has to be installed.. If you are using Hardy or later, it should see most of devices... Let me know..

Good Luck

Hello Seinfeld,
thanks for your help, however it doesn't work.
If I am using the voice recorder coming with Ubuntu, the mic works well. Just wtih Skype there is no sound when I use the test call. I chenged at Skype Options eveything to 'Pulse' but it will not work.
As for the Video, I also believe it is a driver problem. As I said if I use the test at skype, Skype is going to close immediataly. 

grr.

---

### Post by macabro22 on 2009-07-12
Did you just ignore what I just posted? Try it out.

---

### Post by Tigerkermit on 2009-07-13
Hello Macabro22,
sorry but I am not so familiar with Linux and yours looking bit tricky to me.
However I looked for the asound.conf but could not find.
I have at /usr/share/odc/libasound2-plugins/examples a file asound.conf_jack
I guess this is just an example but is not used ?
Do I need to generate the config file ?
Sorry but which location you mean with ### my /etc/
Is this my home directory ?
Sorry for so many questions.

---

### Post by gnu-buntu on 2009-07-14
> **gnu-buntu said:**
> Hi,
...
it rings, connects, etc., but there is no sound output, and I can't tell about input.
...
So maybe sound isn't getting into and out of skype.  I'm using a simple headset, and there's no BlueTooth.  
I don't know anything about pulse audio or ALSA, so I'd appreciate any help to get skype working.  
...
HP dv6770se laptop, AMD Turion 64-bitX2, 64-bit Kubuntu Jaunty 9.04

Hi All,

Problem solved, but it was mostly due to dumb luck and persistence, with a smattering of intuition.  Here's how it happened, in case it's useful to some other KDE and Linux multi-media noob...

The short answer is that I ran Kmix ('alsamixer -V  all' works, too) and increased the gain on "PCM" and "Digital".  For unknown reasons, both settings were at the bottom, 0.

If I run skype from the command line, it works, but the 'ALSA lib pcm_bluetooth.c:1569audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)' messages still show up. However, it doesn't seem to matter, so I'll ignore it for now.

BTW, the name of the package from skype, "skype_ubuntu-2.0.0.72-1_amd64.deb" is perhaps a bit misleading: It does run on AMD x86_64, but the actual binary is 32-bit. It appears to satisfy the package naming convention, so maybe I just drew the wrong conclusion from the name.

Now here's the long version of the story; please feel free to skip it:

Since the error mentioned ALSA, I stumbled onto this page after a Google search:
   - [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
There is a link under "New ALSA Users", "Help to debug":
   - [http://www.alsa-project.org/main/index.php/Help_To_Debug](http://www.alsa-project.org/main/index.php/Help_To_Debug)
Down at the bottom, under "Driver specific pages", there is a link for the Intel
HDA driver:
   - [http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA](http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA)
Down at the bottom... "For Users, Troubleshooting, Mixer configuration," it recommends "try fiddling with the mixer settings on alsamixer"

So I ran 'alsamixer -V all', in order to control both playback and capture.

I noticed that both the PCM and the Digital slides were at 0, so I ran them up into the red, and skype started working.  Evidently they control volume at some point in the skype audio pipeline...

Cheers,
~Peter

---

### Post by macabro22 on 2009-07-15
> **Tigerkermit said:**
> Hello Macabro22,
sorry but I am not so familiar with Linux and yours looking bit tricky to me.
However I looked for the asound.conf but could not find.
I have at /usr/share/odc/libasound2-plugins/examples a file asound.conf_jack
I guess this is just an example but is not used ?
Do I need to generate the config file ?
Sorry but which location you mean with ### my /etc/
Is this my home directory ?
Sorry for so many questions.

No problem man. In a terminal window(Applications>accessories>terminal) just do ```
sudo gedit /etc/asound.conf
```

Copy and paste that piece of code, , restart gnome, raise the volume bars.

It works like a charm.

Good luck

---

### Post by larsman1 on 2009-07-16
I downloaded Skype 2.0 directly from the Skype website.  The default 9.04 Ubuntu installer works fine without any terminal typing.  I'm sending some screenshots - easier than typing - of how I set up my webcam for sound and video.
    The Options pulldown is on the llittle blue "S" cloud on the bottom left after you log in.

---

### Post by gnu-buntu on 2009-07-17
> **larsman1 said:**
> I downloaded Skype 2.0 directly from the Skype website.  The default 9.04 Ubuntu installer works fine without any terminal typing.  I'm sending some screenshots - easier than typing - of how I set up my webcam for sound and video.
    The Options pulldown is on the llittle blue "S" cloud on the bottom left after you log in.

Thanks very much, Larsman.  Yes, those images are pretty much what I see now, too, with the Medibuntu package that I finally got working.

Maybe you or others can help me with some related questions:

[LIST]
[*]Is your Skype 2.0 32-bit or 64-bit? 
> file /usr/bin/skype.real
/usr/bin/skype.real: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.4.1, stripped
(You might have a skype binary, in which case
> file $(which skype)
will yield the answer.)
[*]How did you download the package?  I couldn't get synaptic to accept 3rd-party repository entries like:
http://www.skype.com/go/getskype-linux-ubuntu-amd64 free non-free
http://download.skype.com/linux/repos/debian/ free non-free
http://download.skype.com free non-free
I don't really understand what the entry ought to be, so I appreciate any help you can give.
[/LIST]
Thanks again!
~Peter

---

### Post by dannymichel on 2009-07-18
im getting 'Cannot mix incompatible Qt libraries'
karmic

---

### Post by Tigerkermit on 2009-07-19
> **macabro22 said:**
> No problem man. In a terminal window(Applications>accessories>terminal) just do ```
sudo gedit /etc/asound.conf
```Copy and paste that piece of code, , restart gnome, raise the volume bars.

It works like a charm.

Good luck

Many thanks Macabro22. With your code it works well now.
Microphone is working nice. :P
My remaining problem is still the Video. Wenn I push the test buttom, Skype close ! :confused:

I am using a simple Logitech Webcam. In Skype there is only shown:
Camera (/dev/video0)

Does anyone have an idea ?

Thanks

---

### Post by carlodrengen on 2009-08-06
[SIZE=5]the 
[CENTER]**Intrepid (8.10) install:**[/CENTER]
[/SIZE]

     Quote:
                    sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64); sudo dpkg -i skype-install.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p libqtcore4 libqtgui4 bluez-alsa                                 
[SIZE=5]work like a charm
:P
[/SIZE]

---

### Post by carlodrengen on 2009-08-06
i use 64 bit and it work fine!

---

### Post by gnu-buntu on 2009-08-06
> **carlodrengen said:**
> 
     Quote:
                    sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64); sudo dpkg -i skype-install.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p libqtcore4 libqtgui4 bluez-alsa                                 [SIZE=5]
:P
[/SIZE]
[SIZE=1]getlibs-all.deb doesn't seem to be at the boundless... link anymore.  

This works [/SIZE][SIZE=1]*as of toda*y,[/SIZE][SIZE=1] with another source for the file:
[/SIZE][INDENT][SIZE=1] sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; [/SIZE]
[SIZE=1] wget -N frozenfox.freehostia.com/cappy/getlibs-all.deb; [/SIZE]
[SIZE=1] wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64;](http://www.skype.com/go/getskype-linux-ubuntu-amd64;) [/SIZE]
[SIZE=1] sudo dpkg -i skype-install.deb; [/SIZE]
[SIZE=1] sudo dpkg -i getlibs-all.deb; [/SIZE]
[SIZE=1] sudo getlibs -p libqtcore4 libqtgui4 bluez-alsa;[/SIZE][/INDENT]

---

### Post by ArcticTern on 2009-08-08
> **Cappy said:**
> 

sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64); sudo dpkg -i skype-install.deb                      

This line of code pasted into a terminal installed Skype 2.0 perfectly, no further action required, video and everything! I am running Hardy on an amd64 laptop.  Thank You.

---

### Post by tudor117 on 2009-08-14
Okay so I tried pretty much everything.
Then I got skype to work.
After an update of ia32-libs, skype started giving underuns and i tried EVERYTHING to get it to work again. But it won't.
It's grainy on both my part and whoever I am talking to. Its also very interupted. It's impossible to use.

it says ```
 ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

RtApiAlsa: underrun detected.

```but a whole lot more underruns its goes through the whole list.
I have tried using pulse realtime and non realtime as well as many different fragments and nice levels.
Sometimes it even says it gets disconnected and forces me to kill pulseaudio.
I am totally confused.

An other thing is that I have ALSA and Pulse from Luke's PPA. Hope that doesn't affect much.
Ubuntu Jaunty 9.04 AMD64
4GB RAM
Dual core processor

---

### Post by chris1950 on 2009-08-15
Followed directions by cut and past first one was fine the second (GPG Key) 
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Produced the following error --E: Couldn't find package medibuntu-keyring

Any ideas why?

---

### Post by chris1950 on 2009-08-15
Finally got it installed, I can't sign in - server connection failed.

---

### Post by theZoid on 2009-08-18
I installed Skype on Ubuntu 9.04 x64 via Synaptic with Medibuntu repo enabled, video et al works out of the box.  FWIW.

---

### Post by cybrsaylr on 2009-08-19
theZoid,
How do you enable the Medibuntu repos?

---

### Post by cybrsaylr on 2009-08-19
Nevermind.
I followed the directions of Cappy in post #1 of this thread.
I enabled the Medibuntu repos, then put the code in terminal and Skype installed like a charm. Then played around and configured it and made a test call and so far it appears to work pretty well.

---

### Post by theZoid on 2009-08-19
> **cybrsaylr said:**
> theZoid,
How do you enable the Medibuntu repos?

I see you fixed it...there's a multimedia section in my blog, link in my sig...you might want to check that to see if you've covered everything else...I set that up because my saved links kept changing :)

---

### Post by craigsn on 2009-08-21
Hi, I just installed the alpha 4 of karmic over my Jaunty install, and when I try to run Skype I get the following message 
> 
craig@juzzy:~$ skype
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)


What are my steps in fixing this? 

Thanks for the help.
Craig

---

### Post by AIQ on 2009-08-22
I got the same errors, but the workaround [here]("http://aaronblohowiak.com/2009/08/07/skype-in-ubuntu-karmic-core-dump/") seems to fix the problem by using the [skype-static-oss]("http://packages.medibuntu.org/intrepid/skype-static-oss.html") package instead.

---

### Post by mess110 on 2009-08-22
> **cybrsaylr said:**
> theZoid,
How do you enable the Medibuntu repos?

this guide could be of a little help
```
https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories
```

and if you don't feel like reading just type this in a terminal
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

after that, to install skype just type (again in a terminal)
```
sudo apt-get install skype
```

ps: (works for 64 bit as well)

---

### Post by dannymichel on 2009-08-22
Skype 64bit Ubuntu: [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)

---

### Post by craigsn on 2009-08-23
AIQ, thank for the pointer. That worked for me. And the bonus is that my webcam is now working. Not sound yet, but one step at a time.

---

### Post by ken78724 on 2009-08-24
thanks dannymichel, your guidance [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64) looks looks like a short cut for us to overcome "no audioplay back"; no login & no chat the latter two of which were working before I tried an OSS4 install given us in another lead.

Hmmmmm, looks like you use U 9.04 Jaunty but the URL given only supplies skype download for 8.04 and 8.10. Is there a special work around? 

Anyone please advise

---

### Post by dannymichel on 2009-08-24
y isnt everyone just downloading the '.deb'?

---

### Post by gnu-buntu on 2009-08-25
> **AIQ said:**
> ...the workaround [here]("http://aaronblohowiak.com/2009/08/07/skype-in-ubuntu-karmic-core-dump/") seems to fix the problem by using the [skype-static-oss]("http://packages.medibuntu.org/intrepid/skype-static-oss.html") package instead.

Many thanks (also) for the pointer.  It got things working for me -- at last.

Prior to that, I had spent many, many hours tweaking, tampering and twidling things in an attempt to get Skype working reliably.  I have *never* had so much trouble getting something working under Linux. 

I'm happy now (and keeping my fingers crossed).

---

### Post by ken78724 on 2009-09-04
Hi, I just verified I have the latest install using post by I believe Medi110. Will reboot to see if I have audio, login capability and chat which I lost following an effort to do an OSS4 install that bombed. 

Still open to advice. Thanks.

---

### Post by ken78724 on 2009-09-04
Hi All: after the last posting I rebooted; I still have no sys sign in sound and unsure what ".deb" download dannymichel referred to in the post a week ago and do not see gnu-buntu's specifics re skype-static-oss when going to that karmic website guidance. 

all in all, is it more level headed for a challenged 70 yr old to uninstall and reinstall or is it possible I'd lose other installs related to ubuntu studio for AMD 64 bit I have been working toward over many months. 

help would be well received. truly would like to do a webinar and youtube posts

thanks. Ken:)

---

### Post by gnu-buntu on 2009-09-04
> **ken78724 said:**
> Hi All: after the last posting I rebooted; I still have no sys sign in sound and unsure what ".deb" download dannymichel referred to in the post a week ago and do not see gnu-buntu's specifics re skype-static-oss when going to that karmic website guidance. 

all in all, is it more level headed for a challenged 70 yr old to uninstall and reinstall or is it possible I'd lose other installs related to ubuntu studio for AMD 64 bit I have been working toward over many months. 

help would be well received. truly would like to do a webinar and youtube posts

thanks. Ken:)
 
Simply installing the skype-static-oss package is probably safe.  It caused me no problems, but I can't make promises about it.  It uses the standard /dev/dsp driver as the sound device and doesn't mess with alsa, pulse, etc., AFAIK.
You can get the package by enabling "multiverse" in your package manager repository Software Sources list and then searching for "skype" with the package manager.   The package should have the string "medibuntu" somewhere in its version identifiers.  All you need do is install the one package -- and have a little luck.  Good luck!
Please let us know how it goes or if you have further questions.
Cheers,
~Peter

---

### Post by williamson389 on 2009-09-04
Hey,
i installed skype from this post quite a while ago, with no problems.  I did not realize however that running skype utilizes 100% of my cpu.  After checking thoroughly i know it is skype and i feel that it might be using too much resources. ;)

I was thinking that since the original install was back in april, if a new install would be a goo idea, thinking that this was a custom build for 64-bit and maybe its been worked on. 

I do not know where to start the uninstall, since its not in the repositories.  
 If anyone could give a start with that it would be much appreciated.

Thanks

---

### Post by gnu-buntu on 2009-09-04
> **williamson389 said:**
> Hey,
i installed skype from this post quite a while ago, with no problems.  I did not realize however that running skype utilizes 100% of my cpu.  After checking thoroughly i know it is skype and i feel that it might be using too much resources. ;)

I was thinking that since the original install was back in april, if a new install would be a good idea, thinking that this was a custom build for 64-bit and maybe its been worked on. 

I do not know where to start the uninstall, since its not in the repositories.  
 If anyone could give a start with that it would be much appreciated.

Thanks

100% surely means something is wrong. 

I myself use the skype-static-oss package, and it consumes 0-2% cpu when I don't have a connection and 11-14% with a conversation going (low/mid-range HP laptop, 1.5 years old, AMD Turion64X2).

The skype version I have is 2.0.0.72.

Please see my earlier reply (today) about how to install medibuntu skype, as medibuntu offers several variants of 64-bit skype: "regular" and two static flavors.  I use the Synaptic package manager, and with any luck you can get it to upgrade everything for you.  It can also remove obsolete or unused packages.  (Of course the various *apt* family tools will do the job, too.)  A while back, I installed and uninstalled skype every which way until the static-oss package finally worked -- but Synaptic did all the *un*installation.

Cheers,
~Peter

---

### Post by gnu-buntu on 2009-09-04
I use skype-static-oss.  The sound devices are /dev/dsp.  I noticed that an unrelated application I use leaves the pulseaudio process running even after the app terminates.  What's more, after that, skype doesn't work any more, reporting an "audio problem."  I killed the pulseaudio process and skype started working again.  That gives me a workaround, but does anyone have insight into this problem and maybe how to fix it?

Thanks,
~Peter

---

### Post by dannymichel on 2009-09-04
am i missing something? does this install like a newer version of skype unavailable by just using the .deb package i linked to?
whats the differece in using this method rather than just installing with the .deb that i linked?

---

### Post by williamson389 on 2009-09-06
Thanks alot Gnu-buntu, worked great.   Feel kinda stupid that i forgot about synptic, but thats what forums are for i guess.
Thanks alot

---

### Post by ken78724 on 2009-09-08
Responding to my own question you can install OSS4 aka: &#8220;oss-linux-4.1-1052_amd64.deb&#8221; aka: OSS4 click on: 
[http://www.4front-tech.com/release/oss-linux-4.1-1052_amd64.deb](http://www.4front-tech.com/release/oss-linux-4.1-1052_amd64.deb)

have not rebooted but I believe this'll work.

---

### Post by VOLKOV9 on 2009-09-21
I'm having trouble with displaying video in Skype: <http://ubuntuforums.org/showthread.php?p=7987358>.  I can't find anyone else that's had quite the same problem.  Any ideas?

Thanks in advance.

---

### Post by mn_voyageur on 2009-09-23
Okay, I am trying amd64 Jaunty. Skype mic is not working.

Pulse Audio mic input is showing when I speak, or whistle.  Volume Meter (Recording)

Default input is my Phillips 9000 camera/mic.  (USB Device 0x471:0x329 - USB Audio.)

Everything worked fine before switching to 64 bit OS.

Tried a lot of things, but can't figure out why this won't work.

MN

I returned to 2.0.0.72.  I did not pay attention to the Skype web site, where it clearly says that the version is a Beta.

MN

---

### Post by Arup on 2009-09-25
With the older x32 version in the repos, I talk for hours to my friends in US and my wife in Philippines, cam and sound on, no issues so I don't see the point of messing around with the beta unless it can give me that stability. The lure of pure x64 is there but even then, need for it to work day in day out issueless.

---

### Post by graa on 2009-10-25
Agh I've tried each one of the codes to install skype, i get an error each time, i'm copying everything from my terminal. Please somebody help...
Also, when i try to install the .deb, i get this error message: > /tmp/skype-ubuntu-intrepid_2.1.0.47-1_amd64-2.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

> hamlet@ubuntu:~$ sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64;](http://www.skype.com/go/getskype-linux-ubuntu-amd64;) sudo dpkg -i skype-install.deb 
[sudo] password for hamlet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
--2009-10-25 13:53:03--  [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)
Resolving [www.skype.com](www.skype.com)... 204.9.163.162
Connecting to [www.skype.com|204.9.163.162|:80](www.skype.com|204.9.163.162|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.skype.com/download/](http://www.skype.com/download/) [following]
--2009-10-25 13:53:03--  [http://www.skype.com/download/](http://www.skype.com/download/)
Reusing existing connection to [www.skype.com:80](www.skype.com:80).
HTTP request sent, awaiting response... 302 Found
Location: [http://www.skype.com/go/download](http://www.skype.com/go/download) [following]
--2009-10-25 13:53:03--  [http://www.skype.com/go/download](http://www.skype.com/go/download)
Reusing existing connection to [www.skype.com:80](www.skype.com:80).
HTTP request sent, awaiting response... 302 Found
Location: [http://www.skype.com/intl/en/download/skype/windows/](http://www.skype.com/intl/en/download/skype/windows/) [following]
--2009-10-25 13:53:04--  [http://www.skype.com/intl/en/download/skype/windows/](http://www.skype.com/intl/en/download/skype/windows/)
Reusing existing connection to [www.skype.com:80](www.skype.com:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `skype-install.deb'

    [  <=>                                  ] 15,475      48.5K/s   in 0.3s    

2009-10-25 13:53:04 (48.5 KB/s) - `skype-install.deb' saved [15475]

dpkg-deb: `skype-install.deb' is not a debian format archive
dpkg: error processing skype-install.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 skype-install.deb
hamlet@ubuntu:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype
hamlet@ubuntu:~$ sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N frozenfox.freehostia.com/cappy/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64;](http://www.skype.com/go/getskype-linux-ubuntu-amd64;) sudo dpkg -i skype-install.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p libqtcore4 libqtgui4 bluez-alsa 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
--2009-10-25 13:54:35--  [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb)
Resolving frozenfox.freehostia.com... 66.40.52.59
Connecting to frozenfox.freehostia.com|66.40.52.59|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6498 (6.3K) [application/x-debian-package]
Saving to: `getlibs-all.deb'

100%[======================================>] 6,498       33.1K/s   in 0.2s    

2009-10-25 13:54:37 (33.1 KB/s) - `getlibs-all.deb' saved [6498/6498]

--2009-10-25 13:54:37--  [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)
Resolving [www.skype.com](www.skype.com)... 204.9.163.162
Connecting to [www.skype.com|204.9.163.162|:80](www.skype.com|204.9.163.162|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.skype.com/download/](http://www.skype.com/download/) [following]
--2009-10-25 13:54:37--  [http://www.skype.com/download/](http://www.skype.com/download/)
Reusing existing connection to [www.skype.com:80](www.skype.com:80).
HTTP request sent, awaiting response... 302 Found
Location: [http://www.skype.com/go/download](http://www.skype.com/go/download) [following]
--2009-10-25 13:54:37--  [http://www.skype.com/go/download](http://www.skype.com/go/download)
Reusing existing connection to [www.skype.com:80](www.skype.com:80).
HTTP request sent, awaiting response... 302 Found
Location: [http://www.skype.com/intl/en/download/skype/windows/](http://www.skype.com/intl/en/download/skype/windows/) [following]
--2009-10-25 13:54:37--  [http://www.skype.com/intl/en/download/skype/windows/](http://www.skype.com/intl/en/download/skype/windows/)
Reusing existing connection to [www.skype.com:80](www.skype.com:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `skype-install.deb'

    [  <=>                                  ] 15,475      48.3K/s   in 0.3s    

2009-10-25 13:54:38 (48.3 KB/s) - `skype-install.deb' saved [15475]

dpkg-deb: `skype-install.deb' is not a debian format archive
dpkg: error processing skype-install.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 skype-install.deb
Selecting previously deselected package getlibs.
(Reading database ... 151223 files and directories currently installed.)
Unpacking getlibs (from getlibs-all.deb) ...
Setting up getlibs (2.06) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bluez-alsa is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
  linux-backports-modules-2.6.27-9-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libqt4-dbus libqt4-designer libqt4-network libqt4-qt3support libqt4-script
  libqt4-sql libqt4-sql-mysql libqt4-xml qt4-qtconfig
Suggested packages:
  libqt4-dev
The following NEW packages will be installed
  libqt4-dbus libqt4-designer libqt4-network libqt4-qt3support libqt4-script
  libqt4-sql libqt4-sql-mysql libqt4-xml libqtcore4 libqtgui4 qt4-qtconfig
0 upgraded, 11 newly installed, 0 to remove and 129 not upgraded.
Need to get 11.2MB of archives.
After this operation, 29.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libqtcore4 4.4.3-0ubuntu1.3 [2085kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libqt4-xml 4.4.3-0ubuntu1.3 [112kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libqt4-dbus 4.4.3-0ubuntu1.3 [216kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libqt4-script 4.4.3-0ubuntu1.3 [420kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libqtgui4 4.4.3-0ubuntu1.3 [4286kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libqt4-designer 4.4.3-0ubuntu1.3 [2073kB]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libqt4-network 4.4.3-0ubuntu1.3 [437kB]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libqt4-sql 4.4.3-0ubuntu1.3 [109kB]
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libqt4-qt3support 4.4.3-0ubuntu1.3 [1366kB]
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libqt4-sql-mysql 4.4.3-0ubuntu1.3 [33.7kB]
Get: 11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main qt4-qtconfig 4.4.3-0ubuntu1.3 [109kB]
Fetched 11.2MB in 15s (715kB/s)                                                
Selecting previously deselected package libqtcore4.
(Reading database ... 151224 files and directories currently installed.)
Unpacking libqtcore4 (from .../libqtcore4_4.4.3-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4.4.3-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4.4.3-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package libqt4-script.
Unpacking libqt4-script (from .../libqt4-script_4.4.3-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4.4.3-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package libqt4-designer.
Unpacking libqt4-designer (from .../libqt4-designer_4.4.3-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package libqt4-network.
Unpacking libqt4-network (from .../libqt4-network_4.4.3-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package libqt4-sql.
Unpacking libqt4-sql (from .../libqt4-sql_4.4.3-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package libqt4-qt3support.
Unpacking libqt4-qt3support (from .../libqt4-qt3support_4.4.3-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package libqt4-sql-mysql.
Unpacking libqt4-sql-mysql (from .../libqt4-sql-mysql_4.4.3-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package qt4-qtconfig.
Unpacking qt4-qtconfig (from .../qt4-qtconfig_4.4.3-0ubuntu1.3_i386.deb) ...
Processing triggers for man-db ...
Setting up libqtcore4 (4.4.3-0ubuntu1.3) ...

Setting up libqt4-xml (4.4.3-0ubuntu1.3) ...

Setting up libqt4-dbus (4.4.3-0ubuntu1.3) ...

Setting up libqt4-script (4.4.3-0ubuntu1.3) ...

Setting up libqtgui4 (4.4.3-0ubuntu1.3) ...

Setting up libqt4-designer (4.4.3-0ubuntu1.3) ...

Setting up libqt4-network (4.4.3-0ubuntu1.3) ...

Setting up libqt4-sql (4.4.3-0ubuntu1.3) ...

Setting up libqt4-qt3support (4.4.3-0ubuntu1.3) ...

Setting up libqt4-sql-mysql (4.4.3-0ubuntu1.3) ...
Setting up qt4-qtconfig (4.4.3-0ubuntu1.3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


---

### Post by tudor117 on 2009-10-25
You guys do realize that there's a new version of skype for download on skype's website.
It works flawlessly with pulseaudio, and even with the pulseaudio-module-jack. That means you can use jack and jack rack for cool effects.
[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)
Just get the [Ubuntu 8.10+ 64-bit]("http://www.skype.com/go/getskype-linux-beta-ubuntu-64").

---

### Post by mn_voyageur on 2009-10-25
I stopped after loading 2.0.0.72.

I will try the download and see how it works.

MN

RETREAT! - I am glad that skype-ubuntu-intrepid_2.1.0.47-1_amd64 is working for you.  However, it would not work for me.

I know this, because I save everything that I download and it is the identical file.  

Once again, I am sincerely grateful that this version works for you, but many of us had numerous problems.

MN

---

### Post by tudor117 on 2009-10-25
That's very weird because before it was like 50/50. It worked ok for some time with medibuntu then a lib32 package got updated and I couldn't getting skype to work again. I even tried the new pulseaudio. Like anysound played was cracked every 10th of a second.
It was impossible to use. 
Then I tried the static OSS build. It worked okay but I couldn't watch youtube videos which is what I do a lot with skype or even listen to music. Nor could I use jack with it.

So what happens when you use the new beta that doesn't work?

---

### Post by mn_voyageur on 2009-10-25
I don't remember what did not work.  I do remember that my kids were getting upset that they could not see me while I was away from home.

I loaded 2.0.0.72 and everything was fine.  I decided to leave well enough alone.  

Skype still likes to hijack my computer.  Skype.real is constantly hogging the processor.  And requires me to KILL it.  I have yet to determine why, but I plan to run a VPN tunnel and then identify teleconferencing software that will allow us to bypass Skype.

I'll use Skype to talk with my parents and such, but calling the house will be via VPN soon.

MN

---

### Post by irohaphoto on 2009-10-26
When I installed Ubuntu 8.04 on another PC and downloaded skype there was no video...
is this true? or maybe that PC with ubuntu couldn't detect a driver?

---

### Post by briancb on 2009-10-26
I have the beta skype installed on Karmic I have 2 issues;

1. not that important but skype loads automatically on fresh boot that would be ok but the video is scrambled. I have to close skype down every time and  start again after that the video's fine.

2. This is important the sound that others hear from my mic is distorted with a constant hum. This is the same whether I use a headphone mic. or the one in my webcam.

I hate to say it but when I use skype I have to load Windows 7.:(

---

