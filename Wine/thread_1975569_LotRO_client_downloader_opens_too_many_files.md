---
title: "LotRO client downloader opens too many files"
date: 2012-05-07
forum: Wine
---

### Post by brainwash on 2012-05-07
I'm trying to download the LotRO client using the offical client downloader. The program does work, but it will crash after some time leaving this error message:
```
...
fixme:ntdll:server_ioctl_file Unsupported ioctl 900c4 (device=9 access=0 func=31 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 900c4 (device=9 access=0 func=31 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 900c4 (device=9 access=0 func=31 method=0)
**err:winediag:FILE_CreateFile Too many open files, ulimit -n probably needs to be increased**
```

Some more details:
```
brainwash@local:~$ uname -a
Linux local 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i386 GNU/Linux
brainwash@local:~$ wine --version
wine-1.5.3
brainwash@local:~$ ulimit
unlimited
```

So I'm pretty confused about this error message.

---

### Post by xtremesupremacy3 on 2012-05-20
Hey there,

There is a better way of running Lotro on Ubuntu and it works perfectly I must say.
(The following was posted on Lotro Lorebook and I used it to get it to work)

1) Instead of downloading that awful installer from the main site, download the following installer (even if your in the EU): [http://www.fileplanet.com/213014/210000/fileinfo/The-Lord-of-the-Rings-Online-Client-%28Free-Game%29]("http://www.fileplanet.com/213014/210000/fileinfo/The-Lord-of-the-Rings-Online-Client-%28Free-Game%29")

2)For the required wine libraries, use the following, eventhough the latest Wine includes Winetricks its better using this: 
```
wget http://www.kegel.com/wine/winetricks
chmod +x winetricks 
./winetricks d3dx9_36
```

3) Install the following using winetricks:
```
./winetricks vcrun2008
```

4) Download and use PyLotro (For me the repo version no longer existed, so I downloaded the source version which is easy don't worry):
[http://www.lotrolinux.com/download.php]("http://www.lotrolinux.com/download.php")

5) When you start PyLotro, there is a good chance it cannot find the game, to fix this, click Tools > Options then click the '...' next to Game Directory and find your Lotro directory (usually found in ~/.wine/drive_c/Program Files/Turbine/The Lord of the Rings Online)

6) To update the game to the latest version, click Tools, then Patch and Start. Please note you can get weird errors regarding space of some kind, just ignore that, as long as it does something all is well. Once it says **Finished** it's done.

7) Play the game, have fun!

---

### Post by brainwash on 2012-05-20
Thanks for your detailed reply. :)

After some crashes the official client downloader finished the donwload. I did not care much about looking for the cause of this behavior. Installing and running the client was not a problem. 

On a side note, I prefer to launch the game via command line:

[http://ubuntuforums.org/showpost.php?p=11935405&postcount=96](http://ubuntuforums.org/showpost.php?p=11935405&postcount=96)

---

