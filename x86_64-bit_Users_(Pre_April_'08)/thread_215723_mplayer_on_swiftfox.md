---
title: "mplayer on swiftfox"
date: 2006-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by killkoy on 2006-07-14
I am having trouble getting mplayer working on swiftfox.
I went to the swiftfox/plugins directoryand typed this command
```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in* .
```
but when I go to [this]("http://www.apple.com/trailers/independent/conversationswithotherwomen/trailer/") website i get the click here to download plugin message.
Any help would be much apreciated

Thanks, killkoy

---

### Post by Kilz on 2006-07-14
> **killkoy said:**
> I am having trouble getting mplayer working on swiftfox.
I went to the swiftfox/plugins directoryand typed this command
```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in* .
```
but when I go to [this]("http://www.apple.com/trailers/independent/conversationswithotherwomen/trailer/") website i get the click here to download plugin message.
Any help would be much apreciated

Thanks, killkoy

If you go to the swiftfox/plugins directory, do you see the mplayerplug-in's?

---

### Post by killkoy on 2006-07-14
yes i do

---

### Post by Kilz on 2006-07-14
> **killkoy said:**
> yes i do

If you type ```
about:plugins
``` into the address bar, and click go. Are the plugins listed in the page?

---

### Post by killkoy on 2006-07-14
yes, I get Google VLC, QuickTime Plug-in 6.0, RealPlayer 9, Windows Media Player Plugin and mplayerplug-in 3.17

---

### Post by Kilz on 2006-07-14
> **killkoy said:**
> yes, I get Google VLC, QuickTime Plug-in 6.0, RealPlayer 9, Windows Media Player Plugin and mplayerplug-in 3.17
Ok last question. Do you have mplayer installed? Also have you closed all open browser windows and restarted Swiftfox (I bet you have but I have to ask anyway)?

---

### Post by killkoy on 2006-07-14
> **Kilz said:**
> Ok last question. Do you have mplayer installed? Also have you closed all open browser windows and restarted Swiftfox (I bet you have but I have to ask anyway)?

Your right I have done both of those:p

---

### Post by Kilz on 2006-07-14
> **killkoy said:**
> Your right I have done both of those:p

Ok, One more question, where did you get the plugin? Did you download it or get it with Synaptic?

---

### Post by killkoy on 2006-07-14
> **Kilz said:**
> Ok, One more question, where did you get the plugin? Did you download it or get it with Synaptic?

I used ```
sudo aptitude install mplayer mozilla-mplayer mplayer-amd64
```

---

### Post by Kilz on 2006-07-14
> **killkoy said:**
> I used ```
sudo aptitude install mplayer mozilla-mplayer mplayer-amd64
```

Ok the reason why the plugin isnt working is because Swiftfox is 32bit. Even the versions for the amd64 processor are 32bit. This is why the flash and java plugins work. But the mplayer and plugins in apt/synaptic for people running the amd64 version are 64bit. Here is a link to the [32bit mplayer plugins]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fm%2Fmplayerplug-in%2Fmozilla-mplayer_3.17-1ubuntu1_i386.deb&md5sum=29571e50f3631bcb6c1f1e447a93ebf4&arch=i386&type=main") you can open the .deb file with yor archive program if you install
```
sudo apt-get dpkg-dev
```
You might also have to install the [32bit mplayer and codecs]("http://www.ubuntuforums.org/showthread.php?t=188974")

---

### Post by killkoy on 2006-07-15
Thanks, it works fine now

---

### Post by Kilz on 2006-07-15
> **killkoy said:**
> Thanks, it works fine now

:D

---

### Post by fabertawe on 2006-07-19
[snip]
> **Kilz said:**
> Here is a link to the [32bit mplayer plugins]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fm%2Fmplayerplug-in%2Fmozilla-mplayer_3.17-1ubuntu1_i386.deb&md5sum=29571e50f3631bcb6c1f1e447a93ebf4&arch=i386&type=main") you can open the .deb file with yor archive program if you install
```
sudo apt-get dpkg-dev
```
You might also have to install the [32bit mplayer and codecs]("http://www.ubuntuforums.org/showthread.php?t=188974")

Kilz you're a lifesaver =D> ...wish I'd seen that link a couple of weeks ago!

I am getting one problem though... following the link at the top of the thread to view the trailer I can download and view the clip but viewing it in the firefox page it loads and then gives the following error:
'Error: mplayer execv: No such file or directory'

I uninstalled mplayer before installing the 32bit version from the link. Should I have installed over the original mplayer?

Thanks ... Paul

---

### Post by Kilz on 2006-07-19
> **fabertawe said:**
> [snip]


Kilz you're a lifesaver =D> ...wish I'd seen that link a couple of weeks ago!

I am getting one problem though... following the link at the top of the thread to view the trailer I can download and view the clip but viewing it in the firefox page it loads and then gives the following error:
'Error: mplayer execv: No such file or directory'

I uninstalled mplayer before installing the 32bit version from the link. Should I have installed over the original mplayer?

Thanks ... Paul

The mplayer32 installs to a dirrefent directory to my knowlage.  I have both installed. You may also be ablle to install them both.

---

### Post by fabertawe on 2006-07-19
> **Kilz said:**
> The mplayer32 installs to a dirrefent directory to my knowlage.  I have both installed. You may also be ablle to install them both.

I'd forced 'mplayer-fonts' in to get rid of the nag at startup but then synaptic was sulking because of a broken package! So installed mplayer and re-linked gmplayer to mplayer32 and now that video plays in Swiftfox :-D 

Cheers ... Paul

---

