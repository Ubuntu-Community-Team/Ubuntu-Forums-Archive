---
title: "Advantages and Disadvantages of 64bit. (Plus install Guides)"
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by John.Michael.Kane on 2008-04-24
The information contained herein is written to help users contemplating moving too 64-bit make informed choices. The information is not being presented to make 64-bit the best way to go.

Much has changed since the first release of Ubuntu for 64-bit, a starting point for users reading this would be one of the threads below, however. You should understand there are no conclusive answers. 

Every thread or post on this particular subject should be seen for what it is, and that is an opinion on what to use and nothing more. Since every end user requirement, and experience is different.

After looking over any of the threads below, you will still have to come to your own conclusions on the subject, and this can only be accomplished though testing 64-bit on your hardware.

The one theory that you may notice from the below threads. (it is time users have a forward way of thinking, and understand that 64-bit is the way to go, and by using a 64-bit OS this will help with its progress, in that more applications / plug-ins will be developed for it, if used by more people.) however, This is only a theory.

[is it a good idea to install 64 bit Ubuntu? ]("http://ubuntuforums.org/showthread.php?t=236717&highlight=java")
[386 vs AMD64]("http://ubuntuforums.org/showthread.php?t=223746&highlight=java")
[So what is the main advantage of 64-bit?]("http://ubuntuforums.org/showthread.php?t=350978&highlight=java")
[Is there much difference between 32bit and 64?]("http://ubuntuforums.org/showthread.php?t=239883&highlight=java")
[32 bit vs. 64 bit - which to install?]("http://ubuntuforums.org/showthread.php?t=272414&highlight=java")

Web articles:
[64-bit: More than just the RAM]("http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1")

[Desktop Linux performance comparison:32 bit vs 64 bit]("http://bingouv.blogspot.com/2008/08/desktop-linux-performance-comparison32.html")

(Note: Some of these threads are extremely long, and are not definitive, should you still have questions please feel free to post a detailed thread in the x86 64-bit Users section of the forum presenting your concerns, and questions.)

---------------------------------------------
Normally I would include some pros / cons, however. I think there are many variables involved when figuring out all possible pros and cons. So this is where the user will have to do their own testing.

I have included some some questions that were asked over time regarding 64-bit, which I have included below. 

1) Does more bits mean better performance? 

Answer: Depends. What is the machine used for. How was the program in question coded. The one thing that is said most often (Do not expect some of your applications to run any faster than they do on your 32-bit systems.) Examples: your web browser will still be limited by your Internet connection speed, and your word processing program speed will still be tied to how fast you can type, etc. 

2) Should I upgrade now, or sit on the fence? 

Answer: Again, it depends. In some cases users are advised not to, if their systems are working as they need, however. The end user will always have to decide for themselves based on current, and possible future needs.

3) My workstation is used primarily for office productivity software, e-mail, etc?

Answer: You will probably not need the scalability of 64-bit any time soon, however. If your system has 4-8 GB of ram or more you might want to look into installing a 64-bit OS so you can make use of that memory. Even having 4-8 GB might still not necessitate a move to 64-bit, as you can also make use of a PAE enable Kernel on a 32-bit install, if you want the ability to address more ram.

Some other possible reasons to research a move to 64-bit.

1) All your hardware, and software needs are supported.

2) You need to run memory-intensive applications such as graphics, CAD, video editing, or other programs that will benefit from the larger memory allocation offered by 64-bit systems.

Some possible reasons for not moving to 64-bit.

1) Everything you use under 32-bit works without issue, and you find having to put a bit more work into making some items function is not a path you want to travel.

2) You have programs that you use that are outside of the Ubuntu repositories, that are available as 32-bit only, and you do not feel like compiling them, or just cannot seem to make work under 64-bit.

3) You have hardware / peripherals that are not yet supported for some odd reason under 64-bit. 

Side Note: To make full use of 64-bit you will need native 64-bit applications, and this is where the problem starts for some users. Some programs a user might make use of may not provide native 64-bit applications  (Note there is now a 64-bit version of flash, Java, and there appears to be a 64-bit version of Skype.)

After reading through the above. you find making the move worth a try, please proceed to the below sections.
---------------------------------------------
[B]Beginning the move testing, and research to see if 64-bit is the path for you. The tactic suggested is running a dual-boot configuration of 32-bit, and 64-bit. As this will allow you to research, and test your hardware, and software configuration, While maintaining a fall back if 64-bit is not for you, it is also suggested that testing is done for thirty or more days to find out if running 64-bit fits your needs. 

Note: These iso's are for Intel users with EM64T processors eg: Pentium D / Pentium Dual-Core / Celeron D/ Core2 series including Duo, Quad, and Xeon processors, as well as certain Pentium4's, and AMD 64 users[/B]

1)Choosing your version, and install method: Desktop live / install CD: This can be used to test 64bit Ubuntu, and to make sure your hardware works. This same disc can be used to install Ubuntu. For those wanting to do direct to disc installs use the Alternate install CD.

[Currently supported and eol versions:]("https://wiki.ubuntu.com/Releases") 

[Ubuntu 9.10 download]("http://releases.ubuntu.com/karmic/") 

---------------------------------------------
**Setting up video driver, and desktop effects:**
Note: Almost all Intel video cards should be fully functional by default.

[**Nvidia:**]("http://www.psychocats.net/ubuntu/nvidia") 

[**Ubuntu_ATI Linux driver Installation Guide**]("http://wiki.cchtml.com/index.php/Ubuntu") 

[**Desktop effects**]("http://www.psychocats.net/ubuntu/desktopeffects") 
---------------------------------------------
**Setting up wine: Note Wine now has a 64-bit deb available for 8.04-9.04. To install it use the method below.**
[Wine_Setup]("http://www.winehq.org/download/deb")
---------------------------------------------
**Setting up other 32-bit applications:**
[Getlibs: Automatically solves dependencies for binaries on 64bit, and 32bit systems]("http://ubuntuforums.org/showthread.php?t=474790&highlight=skype") 
---------------------------------------------
**Flash plug-in installation:** 

Flash installation Under 8.04-9.10 can be accomplished using using synaptic, or the command below. All dependencies should be installed automatically. 
```
sudo aptitude install flashplugin-nonfree
``` 

Regarding the native alpha 64-bit flash: This can be manually installed using the below information. Note: This done at your own risk, also make sure you un-install any previous version of flash player you might have installed.
Step one: go to [Adobe Labs Downloads Flash Player 10 for 64-bit Linux]("http://labs.adobe.com/downloads/flashplayer10.html")

Step two: cd to where the file was saved after the download is finished, and untar and uncompressed the tarball using the below command. 
```
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

Step three: Create a plugins directory inside ~/.mozilla using the below command.
```
mkdir ~/.mozilla/plugins
```

Step four: Copy the libflashplayer.so  file into this directory:
```
mv libflashplayer.so ~/.mozilla/plugins
```

Note: The third step, making a plug-ins directory, is only required if the directory doesn't exist yet. As my installation of Ubuntu 9.04 was clean I did not have to un-install the old Flash player, and I did have to create the plug-ins directory.
-----------------------
**Installing Java see below:**

Option one: The sun-java6-plugin in the Ubuntu repository, which is installable via synaptic, software centre or the below command.
```
sudo aptitude install sun-java6-plugin
``` 

Option two: The below guide, if you want to have the latest version.

The 64bit Java browser plug-in: Note this is the method that worked for me, and it was done on a clean install, with no previous plug-ins installed YMMV.
[64bit Java as the default runtime]("http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/")
-----------------------
Skype can be installed after adding the medibuntu repo, or using the 64-bit deb from the skype web site.

-----------------------
**Media playback repositories, and Codec install 9.04:**
[SIZE="1"]**A note about Codec install Multimedia / DVD playback. It is your responsibility to make sure that the software being installed can be legally used in your country, and for your intended purpose:**[/SIZE]

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \--output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

For previous releases use the link below.
[Ubuntu_Community_Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Setting up the basic codec install:

```
sudo aptitude install libavifile-0.7c2 gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg x264 libdvdcss2
``` 

Users who feel they need, W64 can install it using the below command. 
```
sudo aptitude install w64codecs
``` 
-----------------------

Installing a movie player:

Choosing a movie player can be a daunting task, as some feel one player is better than others. Below are some of the common ones used, and the way they can be installed, and how to set them up if needed. 

1) Totem-xine: This player usually only requires the end user to install it, and it's dependencies. Under most cases it requires no further set-up after installing is needed. To install use the command below. 
```
sudo aptitude install totem-xine libxine1-ffmpeg
``` 

Note: if you plan to use totem-xine first remove totem-gstreamer, as it seems to cause conflicts when testing.
To remove totem-gstreamer use the below command.
```
sudo aptitude remove totem-gstreamer
```

2) Mplayer: This is one of the players users swear by, However. It does require a bit of set-up on the users part after installing, Which will be explained. To install use the command below.
```
sudo aptitude install mplayer
``` 

After installing mplayer you may be required to set the default video. To do so open mplayer by typing the command below 
```
gmplayer
``` 

Next: 
1) Right click on the mplayer, and select preferences .
2) Under video tick enable direct rendering, and you might not need double buffering you will have to test this on your particular hardware.
Should you have playback issues you can try, and change available drivers from xv to x11.

Also, depending on the video / dvd being played you may have to adjust for subtitle playback.

3) VLC: This is another player that users seem to hold in high regards for playing movies, and from my testing it would appear this is another player that should only requires the user to install it, However. Depending on the video / dvd being played you may have to adjust for subtitle playback. To install use the command below.
```
sudo aptitude install vlc
``` 

Side note for Gnome, and window manager users: Vlc now makes use of qtlibs, it does not install any KDE based items though.

-----------------------
**Setting up browser video playback plugin's.:**

Installing mozilla-mplayer package: Note: there is a bit of set-up involve with it. 
```
sudo aptitude install mozilla-mplayer
``` 

Plug-in set-up. 
1) Try playing the video. 
2) As the video is attempting to play right click on the box that will have the video. 
3) Select configure. 
4) Where it says video output change to x11. (note this might not be needed) 
5) Adjust the cache to 2092 or more if you like. 
6) Change percent of media to cache to 50. 
7) You should now have browser playback. 

Setting up mozilla-plugin-vlc:

```
sudo aptitude install mozilla-plugin-vlc
``` 

Testing indicates that mozilla-plugin-vlc only requires the users to install it, and no further setup was needed.

Side note: Make sure to remove totem-mozilla if you plan to use one of the above player-plugins.
-----------------------
Below is a screen-shot of 9.10 showing all three programs used for testing, including Java, and flash fully working using the methods described above.
[[IMG]http://img265.imageshack.us/img265/2406/snapshotz.th.png[/IMG]](http://img265.imageshack.us/i/snapshotz.png/)
-----------------------
**Other info that may be of some interest.**

Mounting Linux partitions etc: [**Mounting extra hard drives**]("http://www.psychocats.net/ubuntu/mountlinux") 

Setting up wifi: [**WiFiHowTo**]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") 

Finding out if a particular application installed is 32, or 64-bit can be done by passing the file command if you know the path of the program. To find the binary path, you can pass the which command from your terminal.

```
xxxx@desktop:~$ which mplayer output the below info.

/usr/bin/mplayer
```

After that you can run 
```
file /usr/bin/program name here
```

Examples: 
```
file /usr/bin/skype will output the below.
``` 
```
/usr/bin/skype: ELF **32-bit **LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.1, dynamically linked (uses shared libs), stripped
``` 

```
file /usr/bin/mencoder will output the below.
``` 
```
/usr/bin/mencoder: ELF **64-bit** LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
```

Other dvd, music tools, and other guides read below, to find one that fits your needs. 

1) [thoggen]("http://thoggen.net/") DVD backup utility based on GStreamer and Gtk+. 

2) [dvdrip]("http://www.exit1.org/dvdrip/") Perl front end for transcode.

3) [acidrip]("http://untrepid.com/acidrip/") Wraps MPlayer and MEncoder.

4) [K9copy]("http://k9copy.sourceforge.net/") DVD backup tool for KDE.

5) [CDBackup]("https://help.ubuntu.com/community/CDRipping") 

6) [Forum tutorials. Most are architecture independent]("http://ubuntuforums.org/forumdisplay.php?f=100&order=desc") 
-----------------------

In closing, I have a basic theory, and some threads that include other points of view.

I would suggest to anyone looking to move from one software architecture to another, to write down your complete software needs to accomplish the tasks you do on a daily basis, and if possible your future software needs, as well as a complete hardware research. This holds true for anyone moving from Windows to Linux etc.

Another thing to remember when choosing to stay with 32-bit or moving to 64-bit, is the Linux Kernel is constantly progressing, and the distribution you choose will forever be progressing as well, and issues that you might have had using one architecture may not be there in later versions of either software architecture. This is why trying both out over time can also help with decision making.

Also, as some major hardware and some software vendors move in the 64-bit direction, 64-bit computing will eventually make 32-bit OS's semi-obsolete, I use the term semi, as there will always be users of what some class as old hardware, Which for the most part is 32-bit based, and users who may always favor a 32-bit OS.

Users having issues after using any of the info on this page, are kindly asked to post their issues inside the respective threads, and should a new thread be required please include as much information and details possible regarding the issue. Also please include a copy of any error messages you have. Also let forum members know what guides you used, as this will allow them to better assist you with your problem.

The above covers the basics. This will also be the last update until the next Ubuntu version is released.

---

