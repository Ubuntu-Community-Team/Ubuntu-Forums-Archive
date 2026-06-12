---
title: "Transcode?"
date: 2005-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by gratefulfrog on 2005-04-15
Has anyone managed to install a working trancode on an AMD64 platform? 

Synaptic tells me that it is uninstallable, and I cannot manage to build it from source, either. Even under a 32bit chroot...

Any ideas?

---

### Post by blahrus on 2005-04-15
[QUOTE=gratefulfrog]Has anyone managed to install a working trancode on an AMD64 platform? 

Synaptic tells me that it is uninstallable, and I cannot manage to build it from source, either. Even under a 32bit chroot...

Any ideas?[/QUOTE]
 i have not even had luck building from source, I assome thats why there is no working binary

---

### Post by FluffyElmo on 2005-04-16
I've installed and used AVIDemux, transcode, FFMPEG and other encoding packages from the following repository:

```
deb http://cyberspace.ucla.edu/marillat/ unstable main
```

I haven't really used transcode (AVIDemux mostly), but it installs and runs without errors. In addition to universe and multiverse, I also have ```
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
``` in my sources list if you have problems try adding that as well.

Good Luck, hope it works for you as well...

---

### Post by gratefulfrog on 2005-04-28
[QUOTE=FluffyElmo]Good Luck, hope it works for you as well...[/QUOTE]

Thanks! that's a great help!
 :grin:

---

### Post by Drain on 2005-05-16
When I tried to apt-get install transcode, I got the following error message:

 ```
The following packages have unmet dependencies:
  transcode: Depends: libavcodeccvs (>= 2:20050427-0.0) but it is not going to be installed
             Depends: libavifile-0.7c102 (>= 1:0.7.43.20050224-1) but it is not going to be installed
             Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
             Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
             Depends: libvorbisfile3 (>= 1.1.0) but 1.0.1-1 is to be installed
E: Broken packages
```

Any suggestions as to what I can do to resolve those?

---

### Post by gratefulfrog on 2005-05-16
since then, I've learned that transcode can be replaced by the far superior 'ffmpeg'. However, the version on the Ubuntu repository is obsolete and defective on a 64bit platform. 

the best solution is to download from cvs and build it oneself. You can find more info at my HowToDvd page: [http://gratefulfrog.net/HowToDvd.html](http://gratefulfrog.net/HowToDvd.html) 

Good luck!

---

### Post by FluffyElmo on 2005-05-16
I think transcode uses ffmpeg for much of it's encoding but adds further transformations and codecs of it's own? That said, if ffmpeg alone will do what you want then don't go through the trouble of installing transcode.

The problem installing transcode is that the Marillat repositories track Debian Unstable, not Ubuntu. They were in sync for a while after Hoary released (when I installed) but have since moved on. 

Your best option is probably to build from source (though I wasn't able to get transcode and ffmpeg both built from source at the same time). Your other option would be to add a debian-unstable repository temporarily ([http://amd64.debian.net/README.mirrors.html](http://amd64.debian.net/README.mirrors.html)), grab just the few packages you need and then remove it. 

Since libc is one of the dependencies though, there may be too many changes needed to go this route. I haven't tried this, and maybe someone who knows more can comment on just how unwise it is :-)

---

### Post by Drain on 2005-05-16
Thanks for the suggestions. I might go the apt-get route with the debian unstable repository, but at first glance, that looks like it's going to be more trouble than building a few packages from scratch. I'll keep you posted (unless I hose the install! :-) )

---

### Post by FluffyElmo on 2005-05-16
Keep us updated whichever way you go. I've thought of updating my transcode/ffmpeg occasionally either way but haven't taken the time yet to try it. A couple of thoughts that occurred to me after posting:

Maybe the Breezy repositories have what you need? A full upgrade to Breezy is not recommended but if it had the packages you need it may be a better choice going forward. I can't seem to find a list of Breezy packages...but there must be one.

You should also investigate how to roll-back changes using apt-get in case it doesn't work ;-)  I remember a post on going from hoary back to warty which covered this but can't seem to find it at the moment.

---

### Post by Drain on 2005-05-16
[QUOTE=FluffyElmo]Keep us updated whichever way you go. I've thought of updating my transcode/ffmpeg occasionally either way but haven't taken the time yet to try it. A couple of thoughts that occurred to me after posting:

Maybe the Breezy repositories have what you need? A full upgrade to Breezy is not recommended but if it had the packages you need it may be a better choice going forward. I can't seem to find a list of Breezy packages...but there must be one.

You should also investigate how to roll-back changes using apt-get in case it doesn't work ;-)  I remember a post on going from hoary back to warty which covered this but can't seem to find it at the moment.[/QUOTE]
 I've thought about that too - I'd love to contribute to the development of Ubuntu, as it has on the whole, been very kind to me. :-) 

So I've figured out that I'd switch out the "hoary" in my /etc/apt/sources.list and change it to "breezy" . The next step would then be "apt-get update" then "apt-get dist-upgrade" ... Wish I could find a concise howto on this. 

Again, I'll keep y'all posted if that works.

---

### Post by FluffyElmo on 2005-05-16
I don't think I'd do that just yet. Maybe in a couple of months when Breezy has settled down a little. For now, I'd just try changing *hoary* to *breezy*, then an *apt-get update*, then *apt-get install transcode*. If it works then change *breezy* back to *hoary* and do another *apt-get update*. 

That way you'd only have upgraded the packages you needed for transcode. If it doesn't work, then you'll probably have to try the same thing with the debian-unstable repos. Now that I think about it, I may try it myself in the next couple of days...let me know how things go.

---

### Post by Drain on 2005-05-16
Well, after downloading 260 MB for 400-something packages, Breezy Badger seems to be running fairly smoothly. I had a little hiccup when I restarted and had to apt-get the nvidia drivers, but after that, *apt-get install transcode* worked great. 

I then went back to [www.ubuntuguide.org](www.ubuntuguide.org), followed the instructions to grab dvd::rip, and it doesn't appear to spot any of the dependencies.  :-P So either I rebuild dvd::rip from source so it notices that transcode and a few other assorted utilities, or I should give up on that particular idea and use avidemux or gtranscode for the same purpose. Or I could (heaven forbid! ;-) ) learn to use the CLI. 

Thanks for your suggestions.

---

### Post by FluffyElmo on 2005-05-17
Hmm, I may have to give Breezy a try. I switched to Hoary very early, and my system has been stable for far too long  ;-) 

I have DVD::Rip and AVIDemux installed, I got them from *deb [http://cyberspace.ucla.edu/marillat/](http://cyberspace.ucla.edu/marillat/) unstable main*.

Glad you got things working...

---

### Post by Hep on 2005-08-23
> **FluffyElmo]Hmm, I may have to give Breezy a try. I switched to Hoary very early, and my system has been stable for far too long   said:**
> http://cyberspace.ucla.edu/marillat/[/url] unstable main*.

Glad you got things working...


Not working for me ...

---

### Post by FluffyElmo on 2005-08-23
Here is the procedure I used to install transcode and ffmpeg on a fresh Hoary install about a month ago. As best as I remember it anyways. Please, read the cautionary tales at the end as well, since there are no guaranties and you should know what you're actually doing.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.hoary
sudo gedit /etc/apt/sources.list
```
Wherever you see 'hoary' change it to 'breezy' and then save the file.
```
sudo apt-get update
sudo apt-get install transcode ffmpeg initrd-tools
```
Read the required changes *carefully*. In particular if you see anything X related (Xorg, xserver-common, etc), you should stop and try something else. 
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.breezy
sudo cp /etc/apt/sources.list.hoary /etc/apt/sources.list
sudo apt-get update
```

CAUTION #1: You are installing development packages from Breezy into your system. This may cause problems, as of this writing a full dist-upgrade to Breezy will most likely leave your system non-functional. Be very careful to upgrade only what you need. In particular, X is messed up. So be aware of what you are installing.

CAUTION #2: initrd-tools is required because you must update libc to install transcode. If libc and initrd-tools are not the same, next time you upgrade your kernel your system won't boot. I found this out the hard way a few weeks after installing transcode the first time. I haven't had any further problems, but be aware that there *can* be issues down the road that aren't apparent right away.

That said, this has worked very well for me and it was a lot easier than building transcode from source. Never did manage to get transcode to build from source :(

Good Luck!

---

### Post by Corbelius on 2005-08-24
Any suggestions? wait for the breezy stable ;)

---

