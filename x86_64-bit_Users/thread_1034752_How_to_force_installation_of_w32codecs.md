---
title: "How to force installation of w32codecs?"
date: 2009-01-09
forum: x86 64-bit Users
---

### Post by kallikles2003 on 2009-01-09
Has anyone been able to install the 32 bit codecs on a 64 bit system?

The installation instructions for the non-free codecs on the Medibuntu site mention that it is possible to force install the w32codecs on a 64 system and then use the 32 bits version of mplayer. I downloaded the .deb file for w32codecs, but I cannot figure out how to force that installation. Should I just unpack the file and copy manually the library files to /usr/lib/w32/codecs ? Is there a better method?

Any help appreciated 
 

S.

---

### Post by jocko on 2009-01-09
> **kallikles2003 said:**
> Has anyone been able to install the 32 bit codecs on a 64 bit system?

The installation instructions for the non-free codecs on the Medibuntu site mention that it is possible to force install the w32codecs on a 64 system and then use the 32 bits version of mplayer. I downloaded the .deb file for w32codecs, but I cannot figure out how to force that installation. Should I just unpack the file and copy manually the library files to /usr/lib/w32/codecs ? Is there a better method?

Any help appreciated 
 

S.
Why would you want to use the 32 bit codecs? The medibuntu repo have a "w64codecs" package, which contain the 64 bit versions of the same codecs...

---

### Post by Yellow Pasque on 2009-01-09
Use w64codecs unless you need to run a 32-bit program that uses the codecs. In that case, you would probably have to open up the w32codecs .deb with Archive manager and extract the contents of data.tar.gz/./usr/lib/ to /usr/lib32/

Using dpkg -i force-archictecture would NOT be a good idea in this case because the directory structure of w32codecs is intended for 32-bit systems, and it will conflict with w64codecs if you have that installed.

---

### Post by kallikles2003 on 2009-01-09
The w64codecs package does NOT contain the same codecs as the w32codecs package. There are only a few included (2 indeed), versus tens of codecs in the 32 bit package. In particular, the w64codecs package does not contain the codec needed to play WMA lossless audio format. If you look at the description of the package in the doc file it installs, the lack is clear.
Hence my need to install the 32 bits codec (plus a 32 bit version of a player, like mplayer, to use them).

S.

---

### Post by Kilz on 2009-01-09
> **kallikles2003 said:**
> The w64codecs package does NOT contain the same codecs as the w32codecs package. There are only a few included (2 indeed), versus tens of codecs in the 32 bit package. In particular, the w64codecs package does not contain the codec needed to play WMA lossless audio format. If you look at the description of the package in the doc file it installs, the lack is clear.
Hence my need to install the 32 bits codec (plus a 32 bit version of a player, like mplayer, to use them).

S.

What formats can you not play?

---

### Post by Ellaine on 2009-01-09
Go here & follow instructions. One codec must be eliminated because it won't work in 64bit.

[http://www.stchman.com:P](http://www.stchman.com:P)

---

### Post by bongtothesoo on 2009-01-22
i am in a similar situation.. have you figured out how to install w32codecs in ubuntu 64 bit?

---

### Post by Kilz on 2009-01-22
> **bongtothesoo said:**
> i am in a similar situation.. have you figured out how to install w32codecs in ubuntu 64 bit?

Are you sure you really need them. Mplayer and vlc play most everything without them. What format are you having problems with?

---

### Post by Yellow Pasque on 2009-01-23
> **bongtothesoo said:**
> i am in a similar situation.. have you figured out how to install w32codecs in ubuntu 64 bit?

open up the w32codecs .deb with Archive manager and extract the contents of data.tar.gz/./usr/lib/ to /usr/lib32/

---

### Post by stchman on 2009-01-23
Yes, use this to get your system up and running all the popular CODECs.  The only one I cannot run is the real media stuff but they are pretty rare.

32 bit
```
sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

64 bit
```
sudo apt-get -y install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

---

