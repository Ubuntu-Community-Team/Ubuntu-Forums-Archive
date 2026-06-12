---
title: "how do I install skype on AMD 64 Ubuntu 9.04?"
date: 2009-05-09
forum: x86 64-bit Users
---

### Post by saskatchewan on 2009-05-09
How do I install Skype on a AMD 64 machine running Ubuntu 9.04?

I tried running the Ubuntu 7.04 to 8.04 downloads from the Skype website and the installer said "wrong architecture".  Then I tried the Skype Static.  It seems to run but I can't get an icon in the applications.

Help....

---

### Post by RedSingularity on 2009-05-09
Did you look in the package manager??  It should have your correct architecture in there.

---

### Post by saskatchewan on 2009-05-09
That was the first place that I looked but no success.

The next place is the following website:

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

and 

[http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

I was able to install Skype and even got an icon but, Skype does still not work.

It keeps giving an error about the sound device.

Any ideas on how I could rectify this?

---

### Post by RedSingularity on 2009-05-09
Oh ok so you got it installed and now you have a problem with sound?  What type of headset/speakers you using?  USB or Analog?

---

### Post by saskatchewan on 2009-05-09
Analog

---

### Post by saskatchewan on 2009-05-09
I have analog.

I tried removing skype (sudo apt-get remove skype) and doing a clean install.

When reinstalled Skype I got the following 

Error: Breaks exisiting package 'skype' conflict: skype ( )

What does this meand and do you have any suggestions as to how to fix it?

---

### Post by RedSingularity on 2009-05-09
sudo apt-get autoremove skype

try that

---

### Post by saskatchewan on 2009-05-09
and when I run it i still get "problem with audio playback"
I am doing several things right now so if you send a reply and I don't get back to you right away I am not ignoring you I just have a lot of things on the go and I am trying to get my computer to work.

---

### Post by RedSingularity on 2009-05-09
Did you install it via .deb package?

---

### Post by saskatchewan on 2009-05-09
yes, via a deb package

---

### Post by RedSingularity on 2009-05-09
If you want to remove it you have to do this:

sudo dpkg -r skype

---

### Post by saskatchewan on 2009-05-09
I removed it with the command you suggested and then reinstalled it with sudo apt-get install skype
But there is still the same audio system problem.
I gotta run for a bit so will chat about it later.

---

### Post by coskierken on 2009-05-09
This link worked for me thanks to cappy!  I am running skype on 9.04 64bit with alc888 sound chipset on MSI G45M motherboard.  

[http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)

---

### Post by jespdj on 2009-05-09
The easiest way to install Skype on 64-bit is via the [Medibuntu repository](http://www.medibuntu.org). Add the repository to your software sources (see website for instructions), and then install it with Synaptic or with:
```
sudo apt-get install skype
```

---

### Post by saskatchewan on 2009-05-09
I have tried the download and install for Skype but I still get the mesage "problem with audio playback" when I try to make a call

---

### Post by coskierken on 2009-05-09
Ok, you might have it install correctly.  Now go to options in the skype menu and check to see which sound device you are using.  Make sure it is set to go to the default or which ever one is for the sound card you want to use.  Also, check the System/Pref/sound is going to where it should.  Just keep trying the options until you get it to go where you want and what Skype wants.  This is an important step many forget and think they can't get it to work.  Keep us informed.

---

### Post by justken on 2009-05-11
This does seem like a sound setup issue - possibly pulse.  Following the post & tutorial from psyke83 at this link solved it for me:

[http://ubuntuforums.org/showthread.php?t=1150669&page=2](http://ubuntuforums.org/showthread.php?t=1150669&page=2)

---

