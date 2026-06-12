---
title: "Install 64 bit Flash Player Plugin For Firefox In Ubuntu Linux [HowTo]"
date: 2009-05-02
forum: x86 64-bit Users
---

### Post by sneerwell on 2009-05-02
check out this here :KS
** [Install 64 bit Flash Player Plugin For Firefox In Ubuntu Linux [HowTo]]("http://sneerwell.blogspot.com/2009/05/install-64-bit-flash-player-plugin-for.html") **

---

### Post by misfitpierce on 2009-05-02
or you can just let Ubuntu take care of it by installing Ubuntu Restrcited Extras package under Add/Remove under Applications and search for it... auto installs java and flash and all... so I mean thats prob easiest route.

---

### Post by Arup on 2009-05-02
The restricted package or the synaptic package will install the x32 version of Flash 10 with nspluginwrapper, the x64 version of Flash 10 is far superior to this method and way easier to install.

---

### Post by misfitpierce on 2009-05-02
I mean the 32 bit one runs fine though except on HD content... Does it really make a huge performance difference though?

---

### Post by misfitpierce on 2009-05-02
Nevermind I suppose both ways will work just fine but it seems to be a bit snappier with the actual 64-Bit version installed so thankyou both for the link... was exceptionally easy to install. Just needed to remove flashplugin-nonfree 32-Bit and install this by the command in terminal... So thanks again as the 64-Bit version seems to be a bit snappier... Very happy. :)

---

### Post by Arup on 2009-05-02
Check phoronix website, they benchmarked x32 flash and x64,the x64 makes a huge difference, the fps is higher than flash in Win.

---

### Post by sneerwell on 2009-05-02
ok i will check there site!!!!

---

### Post by cprofitt on 2009-05-02
How is the stability of the 'alpha' Flash release?

---

### Post by misfitpierce on 2009-05-03
Is the one from the link the alpha one? If it is... then it works perfectly fine.

---

### Post by Arup on 2009-05-03
> **cprofitt said:**
> How is the stability of the 'alpha' Flash release?

If your video drivers are configured right, excellent, I can watch full screen youtube with Opera with minimal CPU spikes.

---

### Post by dcstar on 2009-05-03
> **sneerwell said:**
> check out this here :KS
** [Install 64 bit Flash Player Plugin For Firefox In Ubuntu Linux [HowTo]]("http://sneerwell.blogspot.com/2009/05/install-64-bit-flash-player-plugin-for.html") **

And they have a later version available (just make sure you delete the other download first):

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz) ([http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html))

And I would also do this so the plugin is available to all users, not just the one who ran the script:

```
sudo mv ~/.mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins
```

---

