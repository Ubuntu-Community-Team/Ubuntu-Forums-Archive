---
title: "[SOLVED] lightscribe drive help"
date: 2007-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by madking on 2007-09-03
Hi,
    I am fairly new to ubuntu and thought you might want to know that before i begin. I switched to ubuntu a little while ago, and forgot to check how to use the dvd drive, and which one it is. Well i contacted HP and they said it was this:
> DVD+-R/RW optical drive - 16X speed, Super Multi dual format, double layer, LightScribe - With pre-attached front bezel (Pavilion)

When i insert a dvd i get a "xine Error - Kaffeine Player" saying
> No plugin found to handle this resource (dvd:///dev/hda)
Details:
04:01:36 PM: xine: couldn't find demux for >dvd:///dev/hda<
04:01:36 PM: xine: found input plugin : DVD Navigator

I am thoroghly perplexed :confused:, if any one could help that would be great. :) :)

---

### Post by John.Michael.Kane on 2007-09-03
> **madking said:**
> Hi,
    I am fairly new to ubuntu and thought you might want to know that before i begin. I switched to ubuntu a little while ago, and forgot to check how to use the dvd drive, and which one it is. Well i contacted HP and they said it was this:


When i insert a dvd i get a "xine Error - Kaffeine Player" saying


I am thoroghly perplexed :confused:, if any one could help that would be great. :) :)

Looks like you don't have the codec's installed to handle dvd playback.

This should get you going. 

First make sure you have all the repo's uncommented.

If your on kde open konsole, and type the below command.
```
kdesu kwrite /etc/apt/sources.list
```
If your on gnome open terminal, and type the below command.
```
gksudo gedit /etc/apt/sources.list
```
Next remove this symbol # from in front of lines starting with deb http and deb-src. Then save the file, and exit.

Next run the below command.
```
sudo aptitude update && sudo aptitude upgrade
```


Now to move to installing the codecs.

First run the following command.
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```
After which run this command.
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```
Last step run this following command.
```
sudo aptitude update && sudo aptitude install kaffeine libxine1-kde w64codecs libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ibxine-extracodecs
```

As for the lightscribe features of the drive. This should get you going.
[LIGHTSCRIBE SYSTEM SOFTWARE]("http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372")
[lightscribe?]("http://ubuntuforums.org/showthread.php?t=434981")
[No such file or directory - Lightscribe and others]("http://ubuntuforums.org/showthread.php?t=511987")
[Lightscribe Direct Disk Labeling Software]("http://ubuntuforums.org/showthread.php?t=106197&highlight=Lightscribe")
[[SOLVED] Lightscribe in Ubuntu 64 not detecting hardware]("http://ubuntuforums.org/showthread.php?t=517592&highlight=Lightscribe")
[LightScribe disc labelers for GNU/Linux]("http://www.linux.com/feature/118705")

---

### Post by madking on 2007-09-08
it didn't fix it! :mad:  I still get a message box titled "xine Error - Kaffeine Player" that says:
> No plugin found to handle this resource (dvd:///dev/hda)
01:14:45 PM: xine: couldn't find demux for >dvd:///dev/hda<
01:14:44 PM: xine: found input plugin : DVD Navigator

I had really hoped the solution you gave would work , but it didn't.
Any other ideas?

---

### Post by madking on 2007-12-19
Ok, i had fixed this a little bit ago, by installing vlc. I use that for dvds now. anyway.. how do i mark this as solved?...

---

### Post by John.Michael.Kane on 2007-12-19
> **madking said:**
> Ok, i had fixed this a little bit ago, by installing vlc. I use that for dvds now. anyway.. how do i mark this as solved?...

To mark the thread solved go to thread tools -> mark as solved. Another option is if you edit the OP there should be a option that says "mark as resolved."

Please don't hesitate to post should you have any other issues.

---

