---
title: "[SOLVED] ffmpeg install"
date: 2008-06-15
forum: x86 64-bit Users
---

### Post by baileyone82 on 2008-06-15
Hello,

I can't seem to install ffmpeg for some reason.

```

bailey9@JBOD-Desktop:~$ which ffmpeg
bailey9@JBOD-Desktop:~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
          Depends: libswscale1d (>= 0.cvs20070307) but it is not going to be installed
E: Broken packages
bailey9@JBOD-Desktop:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
bailey9@JBOD-Desktop:~$ 

```

The problem seems to be libc6 needs to be upgraded to version 2.7, and I have 2.6, which apt-get says is the latest?

Thanks for the help,
Chris.

---

### Post by Moop on 2008-06-15
I installed ffmpeg from the medibuntu repository with no problems. 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by robertchahine on 2008-06-15
i have installed ffmpeg from the medibuntu repos too via liveCd

---

### Post by baileyone82 on 2008-06-15
I have Medibuntu added to my universe list. So I believe that I am attempting to install ffmpeg from Medibuntu. Still getting the version compatability errors.

---

### Post by robertchahine on 2008-06-15
> **baileyone82 said:**
> I have Medibuntu added to my universe list. So I believe that I am attempting to install ffmpeg from Medibuntu. Still getting the version compatability errors.
look at this thread 

[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

they need to install ffmpeg to make the convertit software works.
look at the how-to and see how they install ffmpeg

---

### Post by baileyone82 on 2008-06-15
Thanks for the tip, however, the first instruction is to install "ffmpeg2theora", which is dependent on "libswscale1d", which is dependent on "libc6", which gets me right back to the same problem I listed above.

---

### Post by jocko on 2008-06-16
> **baileyone82 said:**
> Hello,

I can't seem to install ffmpeg for some reason.

```
[COLOR=Red]ffmpeg: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed[/COLOR]

libc6 in hardy is 2.7-10, but in gutsy it is 2.6.1.
It looks like you use gutsy with the hardy medibuntu repo?
That's a bad idea as some of the packages in the hardy medibuntu repo have dependencies that are newer than what's available for gutsy.
Depending on which method you used to get the medibuntu repo, there are different ways to solve it:

1. If you used the easy way from [this page]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f"), try this:
[CODE]sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo rm /etc/apt/sources.list.d/medibuntu.list.save
```
Then add the correct repo with these commands (from the [same page]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f")):
```
sudo wget http://www.medibuntu.org/sources.list.d/[COLOR=Red]gutsy[/COLOR].list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

2. If you added the medibuntu repo by any other method:
```
gksudo gedit /etc/apt/sources.list
```
Find the medibuntu line and make sure it reads:
```
deb http://packages.medibuntu.org/ [COLOR=Red]gutsy[/COLOR] free non-free
```

---

### Post by stchman on 2008-06-16
> **baileyone82 said:**
> Hello,

I can't seem to install ffmpeg for some reason.

```

bailey9@JBOD-Desktop:~$ which ffmpeg
bailey9@JBOD-Desktop:~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
          Depends: libswscale1d (>= 0.cvs20070307) but it is not going to be installed
E: Broken packages
bailey9@JBOD-Desktop:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
bailey9@JBOD-Desktop:~$ 

```

The problem seems to be libc6 needs to be upgraded to version 2.7, and I have 2.6, which apt-get says is the latest?

Thanks for the help,
Chris.

You can get ffmpeg by installing one of the gstreamer packages.

```
sudo apt-get -y install gstreamer0.10-ffmpeg
```

Worked for me.

---

