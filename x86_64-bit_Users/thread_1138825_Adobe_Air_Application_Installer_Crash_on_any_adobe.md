---
title: "Adobe Air Application Installer Crash on any adobe AIR programs"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by Tirish Anau on 2009-04-26
So I tried to install Tweet Deck, Twhirl, and Seemic Desktop and the Terminal says it has been crashing. This is what happened when i tried to install tweetdeck but the it seems to come out the same on any of the others as well.

tirish@Tirish:~$ sudo /opt/"Adobe AIR"/Versions/1.0/Resources/airappinstaller
[sudo] password for tirish: 
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
Application crashed with an unhandled SIGSEGV
Crashlog has been dumped in /tmp/airCrashLogs/0426_1638_D3UEoL
tirish@Tirish:~$ 

I'm not entirely sure what all this means and would welcome any help that anyone can offer.

Thanks again

---

### Post by Tirish Anau on 2009-04-26
Just to clarify my system is using Ubuntu Studio 9.04 installation and also did not work before that upgrade.

---

### Post by Tirish Anau on 2009-04-26
It's also 64-bit and yes I'm AMD Triple Core Phenom

---

### Post by Bytor on 2009-04-28
I have a similar error on Intrepid 32-bit

Trying as root it spits out 2 lines of error plus the 2 line notice of the SIGSEGV. Trying as a normal user just spits out the last 2 lines. Can't find anything about this on Adobe forums, hopefully an Ubuntu guru will know what's what.

[root@CoryWork] 10:24:27 [6]/tmp> "/usr/bin/Adobe AIR Application Installer"

(airappinstaller:9501): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(airappinstaller:9501): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Application crashed with an unhandled SIGSEGV
Crashlog has been dumped in /tmp/airCrashLogs/0428_1024_zmOWEt

---

### Post by theturtlemoves on 2009-05-02
I'm having the same problem on a fresh install of Jaunty 64-bit.

---

### Post by alienato on 2009-05-13
i've segmentation fault on a fresh jaunty 64bit

---

### Post by timgood on 2009-06-08
I've been trying to solve this problem for a few days now - I've done all the things other successful people have done but to no avail. I also get the message about Wrong ELF class and failure to load gio libraries when I start the Air Application Installer from the command line. Installer will launch, but segfaults when I attempt to install applications. Would very much like to get iplayer desktop working. Platform 64bit Jaunty.

---

### Post by timgood on 2009-06-08
OK here's an interesting thing. I installed 32 bit version of Jaunty on VirtualBox and then installed Flash and Adobe Air. Same problem - installation of iplayer desktop or tweetdeck segfaults. This may indicate that it is a processor problem? I'm running an AMD Quad Core - are you all running AMD as well?

---

### Post by hounddog32 on 2009-06-09
I get the same thing on a 32 bit install on my X3 720. Adobe Air is installed fine, but trying to install any application gives a segmentation fault immediately.

---

### Post by jdriskill on 2009-06-17
Hi,

I have this same problem when I run the installer:

/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
Application crashed with an unhandled SIGSEGV
Segmentation fault

The installer will run, but crashes with the segfault whenever I try to install an application.

Any new news on this?

Thanks,

Jeff

---

### Post by mnology on 2009-06-27
Raising my hand as another 32bit user(Linux Mint 7 actually) where I'm getting segfaults no matter what AIR app I'm trying to install. The window pops up(sometimes) and disappears immediately. Running airappinstaller from the command line only provides 'Segmentation Fault'.

strace doesn't show anything that sticks out except for last few lines about not being able to access memory. I doubt my 4GB's isn't enough.

Compiled 16GB/32GB bigmem kernel which didn't change anything, have since gone back to stock kernel(4GB bigmem).

Also AMD architecture.

---

### Post by afrodeity on 2009-06-27
Me too. On 64bit Hardy, the installer just hangs. Went through the tutorial provided, did everything I'm supposed to do, but it segs out, so no Adobe Air for me.

---

### Post by rssaddict on 2009-06-30
Same here. 32 bit Ubuntu 9.04, AMD architecture. Segfaults out on any AIR app install.

---

### Post by cfexrun on 2009-07-01
I've run into this as well. 9.04 32bit, AMD dual core laptop (CQ50). Again, AIR install seemed to go fine, but when trying to use the AIR Application Installer it segfaults.

So... uhhh... what the deuce?

---

### Post by timgood on 2009-07-02
I have a feeling that this might be Ubuntu specific (Mint is also based on Ubuntu) as I can see other distro's have succeeded. I don't know if we'll get an answer in the short term...

It may be a processor specific problem - seems like people running AMD processors are getting this problem in the main.

---

### Post by anabelle on 2009-07-12
Same thing here

AMD X4 2.6

Can't install any app :(

---

### Post by rowanparker on 2009-08-14
> **jdriskill said:**
> /usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
Application crashed with an unhandled SIGSEGV
Segmentation fault

I get exactly that too.

Also on AMD64 (Anthlon X2 2.1Ghz)

---

### Post by VK7HSE on 2009-08-17
I to am having this issue on my AMD x2 64 athlon (7750+) I've attempted on both x86_64 & i386 Air installs, but unable to install any air applications...

---

### Post by anabelle on 2009-08-17
It's happenning for me on a 64bit processor but running a 32bit system

---

### Post by VK7HSE on 2009-08-20
I've just had another attempt (Jaunty i386) 

dpkg -l | grep adobeair
adobeair1.0 1.5.2.8870 Adobe AIR

Reveals the following, but the information on the Adobe forums seems to have gone very quiet on this issue! So I'm no closer to a fix/answer :(
I have also installed the same version of air on my netbook (ubntu netbook remix 9.04 Intel mobile 900MHz CPU) and all is fine! so there is definitely an issue within the way the code is processed. So it's my opinion that until AdobeAir is updated (yet again!) applications will remain un-installable... :(

I suppose if it works on Windows that's all they appear to care about!

---

### Post by kaapstorm on 2009-08-21
Adobe provides some feedback here: [http://forums.adobe.com/thread/451632](http://forums.adobe.com/thread/451632)

The problem seems to be with Ubuntu + AMD CPUs. I have a Phenom X3. 

The only way I managed to install it was to install Ubuntu in a virtual machine, and then install Air on that. 

That worked. I use KVM for virtualisation. I haven't tried with VirtualBox or VMWare. I chose a single CPU, 32 bit (i686), and used Ubuntu Hardy i386 Server Edition, but I'm sure Jeos would work just as well.

---

### Post by Tomy on 2009-08-29
Has anyone solved this problem yet? I have a AMD Phenom X4 and am running Ubuntu 9.04 32bit. AIR apps will not install. I checked the Adobe forum but nothing seems to be happening over there.

---

### Post by sammyboy405 on 2009-10-19
Anyone Been Able to Get Adobe Air apps to Work on AMD Processors?

[http://forums.adobe.com/thread/451632?tstart=0](http://forums.adobe.com/thread/451632?tstart=0)

thats about the only active thread I can find on the issue over at adobe.

---

### Post by MrMerry on 2009-11-13
try 

rm -fr /etc/opt/Adobe/certificates/crypt/

After installing Adobe Air, and run the airappinstaller as root.

See [http://forums.fedoraforum.org/showthread.php?t=233539](http://forums.fedoraforum.org/showthread.php?t=233539)

where they seem to have solved the issue fully for Fedora 12 (i686 and x86_64)

---

