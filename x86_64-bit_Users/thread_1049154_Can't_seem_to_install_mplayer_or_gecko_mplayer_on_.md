---
title: "Can't seem to install mplayer or gecko mplayer on system"
date: 2009-01-24
forum: x86 64-bit Users
---

### Post by FireFighter on 2009-01-24
Hi all. Have just installed Ubuntu8.04 64bit on my computer. I have successfully gotten all the media going following this post:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I have run into one diffuculty though. I can't get the mplayer or gecko player to install so that I can stream windows video and audio through Firefox. When I follow the post where it comes to that using terminal, I get the following reply:

**********@**********-desktop:~$ sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
[sudo] password for pappendick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kaffeine-mozilla is not installed, so not removed
Package mozilla-helix-player is not installed, so not removed
Package mozilla-mplayer is not installed, so not removed
Package mozilla-plugin-vlc is not installed, so not removed
Package totem-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32ncurses5 nspluginwrapper libxine1-x ia32-libs libxcb-xv0
  linux-headers-2.6.24-19 libxine1-plugins libc6-i386 lib32gcc1 lib32asound2
  libxine1-console libxine1-misc-plugins libxvmc1
  linux-headers-2.6.24-19-generic lib32z1 lib32stdc++6 libxcb-shape0
  libxcb-shm0 libxine1-bin libxine1-ffmpeg libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xine-plugin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 238kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122054 files and directories currently installed.)
Removing xine-plugin ...
**********@**********-desktop:~$ sudo apt-get install gnome-mplayer gecko-mediaplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-mplayer: Depends: mplayer (>= 1.0) or
                          mplayer-nogui (>= 1.0) but it is not going to be installed
E: Broken packages

Tried to go the mplayer route and got the same error. Really want to be able to stream windows audio and video. I was successful in installing the vlc plugin for Firefox and it works but I can't go to full screen on the video once it starts (no option to). So I just uninstalled it and have come here for help.

Help.

Thanks.

---

### Post by jocko on 2009-01-24
Make sure you have all the repos activated.
Go to System --> Administration --> Software Sources.
In the first tab (software for ubuntu) make sure the top four repos (main, universe, restricted and multiverse) are active. In the third tab (updates), make sure at least the top two are active.
Then:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mplayer [COLOR=Blue]#and whatever else packages you want[/COLOR]
```

---

### Post by FireFighter on 2009-01-25
Thanks jocko for the prompt reply. 

You were on the correct trail. I have found out what my problem was. At the beginning of the sticky about multimedia on my first post, it talked about setting up Medibutu repository. I overlooked that the command was for intrepid and not hardy. Changed it over to hardy where intrepid was mentioned (just like the post warned), and all went well. Sometimes it is the little things that are overlooked that cause all the trouble! Feel kind of embarassed actutally, but, oh well.

Thank you again.

---

