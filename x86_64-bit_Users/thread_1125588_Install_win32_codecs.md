---
title: "Install win32 codecs?"
date: 2009-04-14
forum: x86 64-bit Users
---

### Post by kamitsukai on 2009-04-14
Can someone point me in the direction of a tutorial to install win32 codecs on amd64 and get smplayer and vlc to use them?

---

### Post by billt1 on 2009-04-14
[http://www.medibuntu.org/](http://www.medibuntu.org/)

I think

---

### Post by kamitsukai on 2009-04-14
> **billt1 said:**
> [http://www.medibuntu.org/](http://www.medibuntu.org/)

I think

Thanks but that's only part of the problem solved, Still got to get it to install on 64 bit architecture;)

---

### Post by wolfen69 on 2009-04-14
why not install the win64 codecs?

---

### Post by Clancy_s on 2009-04-14
> **kamitsukai said:**
> Can someone point me in the direction of a tutorial to install win32 codecs on amd64 and get smplayer and vlc to use them?

It does depend on version and 32 /64 bit to a degree, fortunately there's a comprehensive how to that covers everything up to intrepid.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

If you're using jaunty I suggest you ask in a jaunty support thread.

---

### Post by Yellow Pasque on 2009-04-15
I think you can easily install them with getlibs
1. Download/Install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
2. Download the w32codecs .deb off of the medibuntu site: [http://packages.medibuntu.org/](http://packages.medibuntu.org/)
3. Install that .deb with:
```
getlibs -i <path_to_deb_you_downloaded>
```

.. but you'll need a 32-bit media player to actually use the codecs. I didn't see an easy way of achieving that with a quick google, but I'll admit that I didn't spend too much time looking. Hopefully, you figure it out.

---

### Post by kamitsukai on 2009-04-15
> **wolfen69 said:**
> why not install the win64 codecs?

I have but it appears that the win64 codec's dont include support for wmv audio?

---

### Post by kamitsukai on 2009-04-15
This is getting ridiculous why has no one thought of sorting this problem? I know it's not anyone's fault here but you would of thought by now that enough people would have moaned to get wmv audio to work on 64 bit ubuntu natively? I really need a thorough howto as I'm not capable enough on ubunttu to really do this without:mad:

---

### Post by stchman on 2009-04-15
> **kamitsukai said:**
> Can someone point me in the direction of a tutorial to install win32 codecs on amd64 and get smplayer and vlc to use them?

I run 64 bit Hardy and I can play nearly every type of media file out there.

Use this command:

```
sudo apt-get -y install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

If you need to get encrypted DVD playback follow my tutorial.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

You will be a media playing machine after this.

---

### Post by kamitsukai on 2009-04-15
> **stchman said:**
> I run 64 bit Hardy and I can play nearly every type of media file out there.

Use this command:

```
sudo apt-get -y install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

If you need to get encrypted DVD playback follow my tutorial.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

You will be a media playing machine after this.

Already done that yet still no audio in some wmv files

---

### Post by kamitsukai on 2009-04-15
OK after allot more research it appears that the reason audio is working on some and not others is because the newer wmv codec hasnt been fully reverse engineered to provide open source codec's...

**Link to Sabayon Linux Forum Post About the Problem -> **[http://forum.sabayonlinux.org/viewtopic.php?f=59&t=10319&sid=940e213b03b46a894358b59653b14a26](http://forum.sabayonlinux.org/viewtopic.php?f=59&t=10319&sid=940e213b03b46a894358b59653b14a26)

---

### Post by stchman on 2009-04-16
> **kamitsukai said:**
> OK after allot more research it appears that the reason audio is working on some and not others is because the newer wmv codec hasnt been fully reverse engineered to provide open source codec's...

**Link to Sabayon Linux Forum Post About the Problem -> **[http://forum.sabayonlinux.org/viewtopic.php?f=59&t=10319&sid=940e213b03b46a894358b59653b14a26](http://forum.sabayonlinux.org/viewtopic.php?f=59&t=10319&sid=940e213b03b46a894358b59653b14a26)

Windows can have their proprietary stuff.

---

### Post by stmiller on 2009-04-17
Try to play it back with the latest VLC. Or avoid crappy wma formats. :)

---

### Post by kamitsukai on 2009-04-17
> **stmiller said:**
> Try to play it back with the latest VLC. Or avoid crappy wma formats. :)

It won't work in any video player on 64 bit ubuntu as even VLC uses the system codecs for the newer wmv audio

---

