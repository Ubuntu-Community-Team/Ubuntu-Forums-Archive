---
title: "Playing DVD's"
date: 2007-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by OldDog11 on 2007-05-11
I would like to install libdvdcss2 but I cannot find it in the Synaptic package Manager.

I have all four repositories checked.

Is libdvdcss2 available in the 64 bit version of Feisty Fawn?

---

### Post by John.Michael.Kane on 2007-05-11
At the bottom of this thread [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607) were these commands

**[COLOR="DarkRed"]For users running feisty 7.04 needing codec's.[/COLOR]**

Run these commands
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

Followed by.
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

Finally, run :
```
sudo aptitude update
```

You can now install your codecs. See below.

```
sudo aptitude install totem-xine libdvdcss2 w64codecs acidrip brasero  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse banshee libxine-extracodecs

```

---

### Post by OldDog11 on 2007-05-11
Thanks for your help.

I have installed everthing you suggest but I still cannot play DVD's

In xine, the xine engine failed to start. No plugin was found

Totem says I do not have appropriate plugins

Any suggestions what I do now or what plugins I should install?

---

### Post by John.Michael.Kane on 2007-05-11
> **OldDog11 said:**
> Thanks for your help.

I have installed everthing you suggest but I still cannot play DVD's

In xine, the xine engine failed to start. No plugin was found

Totem says I do not have appropriate plugins

Any suggestions what I do now or what plugins I should install?

Try ```
sudo aptitude install totem-xine
```

It should now read your dvd's.

---

### Post by OldDog11 on 2007-05-11
Many thanks for your help - I can now watch my DVD's.

That's terrific support from the Ubuntu community.

---

### Post by OldDog11 on 2007-05-11
just one more thing

I found this line on one of your help threads.

Do I need this or have I already entered it and what does it do?

sudo /usr/share/doc/libdvdread3/install-css.sh

thanks

---

### Post by John.Michael.Kane on 2007-05-11
> **OldDog11 said:**
> just one more thing

I found this line on one of your help threads.

Do I need this or have I already entered it and what does it do?

sudo /usr/share/doc/libdvdread3/install-css.sh

thanks

That command compiles, and installs the css file using a script. It's not really needed anymore, however. the method for using it still works.

---

### Post by Mr_bleu on 2007-06-11
I've tried following the directions above and get the following error message.
The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (Error reading NAV packet)
Any help is appreciated.

---

### Post by capecove on 2007-06-11
Hello Mr_bleu... Did you check this forum out? 

[http://ubuntuforums.org/showthread.php?t=470508](http://ubuntuforums.org/showthread.php?t=470508)

Hope this helps...

---

### Post by crjackson on 2007-06-12
> **SD-Plissken said:**
> At the bottom of this thread [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607) were these commands

**[COLOR="DarkRed"]For users running feisty 7.04 needing codec's.[/COLOR]**

Run these commands
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

Followed by.
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

Finally, run :
```
sudo aptitude update
```

You can now install your codecs. See below.

```
sudo aptitude install totem-xine libdvdcss2 w64codecs acidrip brasero  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse banshee libxine-extracodecs

```


Thanks - this post fixed my inability to play DVD movies:D

---

