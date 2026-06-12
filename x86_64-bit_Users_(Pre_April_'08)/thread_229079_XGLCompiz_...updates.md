---
title: "XGL/Compiz ...updates?"
date: 2006-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by aceracer24 on 2006-08-03
I have racked my brain trying to find update and correct info as to the install of XGL and compiz. I have found MANY threads, some state specificlaly amd64 but are outdated and otehr do not state what arch they will work for. I would REALLY appreciate it if someone would either update the HowTo's to reflect current status of a working XGL/Compiz amd64/nvidia install. I've already trashed one Ubuntu install do to old info.

---

### Post by x64Jimbo on 2006-08-04
XGL is still highly experimental, and you have to understand the risks involved if you're going to try it out. That said, I too am hoping for a) more stability in the product soon and b) good support for amd64 and KDE. In the meantime I'm content to wait patiently. Good things take time.

---

### Post by Vlatko on 2006-08-04
i'm a newbie and i installed it with this guide few hours ago. so far i have no problems.
[http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D](http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D)

---

### Post by mattlach on 2006-08-12
> **Vlatko said:**
> i'm a newbie and i installed it with this guide few hours ago. so far i have no problems.
[http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D](http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D)

Hmm  I just took a look at this, and many of the files fail dependancy checks due to libpango...

```

# sudo apt-get install xserver-xgl compiz-gnome cgwd gcompizthemer gcompizthemer-themes
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  cgwd: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
        Conflicts: gcompizthemer
  compiz-gnome: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
                Depends: compiz (= 0.0.13-0quinn29) but it is not going to be installed
  gcompizthemer: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
E: Broken packages

```

Any ideas?

---

### Post by John.Michael.Kane on 2006-08-12
This may help those who want XGL/Compiz under 64bit. [COLOR="Red"]**Note howto: was tested under Gnome/nvidia only**[/COLOR]

[[COLOR="Blue"]**XGL/Compiz For 64Bit User's**[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=235013")

---

### Post by IanW on 2006-08-13
Anyone got a good howto for Ubuntu64/AMD64/ATI?

---

### Post by xopher on 2006-08-13
You should check out [compiz.net]("http://www.compiz.net"), there's a lot of how to's, most likely something that fits your setup too.

---

### Post by aceracer24 on 2006-09-11
I got it running awhile ago, but most of the how to's now are seriously outdated. Especially when it conserns the newest compiz thats out. I'd make one myself but, I don't always have the time to offer support for those that it may not work for. Not to mention I am NO expert. All I would be able to do is offer what worked for me. Sometimes thats not enough since I can't always explain why it works :)

---

