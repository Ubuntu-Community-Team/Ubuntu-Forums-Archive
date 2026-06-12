---
title: "gstreamer and dvd playback"
date: 2007-08-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by mandyfester on 2007-08-18
Hello 

I am using feisty 64 bit and I cannot get gstreamer 0.10 to play dvds. 

I would like this to work so that I can use Elisa multimedia system which uses gstreamer as its base multimedia player.

Has anyone had any success? If so any help is much appreciated.

Thanks

Mandy

---

### Post by John.Michael.Kane on 2007-08-18
> **mandyfester said:**
> Hello 

I am using feisty 64 bit and I cannot get gstreamer 0.10 to play dvds. 

I would like this to work so that I can use Elisa multimedia system which uses gstreamer as its base multimedia player.

Has anyone had any success? If so any help is much appreciated.

Thanks

Mandy

To play dvd's with menu support you need to use libdvdcss2, and the totem-xine back end along with these files libxine-extracodecs, and libdvdnav4 

To get those above files do the following.
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

Followed by.
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

Finally, run 
sudo aptitude update

You can now install your codecs. See below.
```
sudo aptitude install totem-xine libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs libdvdnav4 
```

Or if you want to play them without menu support (gstreamer0.10) support:

```
sudo aptitude install libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by mandyfester on 2007-08-18
Thanks. I am able to watch DVDs with totem xine but I still get the message in Elisa. "no player installed" whenever I try and view a DVD. I thought it was a gstreamer configuration issue since it uses gstreamer to view and play its media files but it may just be an error in Elisa, I am using version 0.3.1.

---

