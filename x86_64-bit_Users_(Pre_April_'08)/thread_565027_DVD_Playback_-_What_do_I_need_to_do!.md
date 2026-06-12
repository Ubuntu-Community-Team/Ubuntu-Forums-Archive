---
title: "DVD Playback - What do I need to do!"
date: 2007-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by cdfccf on 2007-10-01
Please help me!
What do I need to do in order to play retail DVDs 
I recently installed Ubuntu Feisty Fawn on my HP  AMD 64 base d computer.
I have spent the better part of 5 hours scouring anything that I could find on the subject, but
to no avail.
I am considering doing a fresh install and starting over!

any help would be appreciated.

---

### Post by John.Michael.Kane on 2007-10-01
> **cdfccf said:**
> Please help me!
What do I need to do in order to play retail DVDs 
I recently installed Ubuntu Feisty Fawn on my HP  AMD 64 base d computer.
I have spent the better part of 5 hours scouring anything that I could find on the subject, but
to no avail.
I am considering doing a fresh install and starting over!

any help would be appreciated.

For users running feisty 7.04 needing codec's.

Run these commands
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

Followed by.
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

You can now install your codecs. See below. run :
```
sudo aptitude update && sudo aptitude install libdvdcss2 w64codecs acidrip brasero gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse banshee totem-xine
```

Above info found in the sticky thread below.
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

Edit the above command gives you mplayer for playing dvds, and totem-xine. you can remove totem if mplayer fits the bill acidrip does just what it says it rips.

---

### Post by stmiller on 2007-10-01
Try using google to search the forum, like this:

[http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+play+DVDs&btnG=Search](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+play+DVDs&btnG=Search)

---

### Post by HousieMousie2 on 2007-11-18
> **stmiller said:**
> Try using google to search the forum, like this:

[http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+play+DVDs&btnG=Search](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+play+DVDs&btnG=Search)

Thank you, very useful information!  I had never seen Google used that way, and having spent many hours trying to sort out 'Kubuntu' programs/desired activities, I imagine I will use that extensively.

Thank you!

---

