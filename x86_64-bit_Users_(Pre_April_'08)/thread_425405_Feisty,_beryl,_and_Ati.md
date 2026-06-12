---
title: "Feisty, beryl, and Ati"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryboto on 2007-04-27
So, I really wanted to start folding using the linux SMP client.  I've got an Opteron running at 2.8ghz, and I've been getting a high PPD using ubuntu in VMware.  I've successfully installed ubuntu feisty 7.04, and I haven't really had any video related issues.  I wanted to try beryl, as a classmate of mine uses it on his nvidia based laptop.  Well, I'm having issues.  I'm using the fglrx driver, and beryl works, but strangely.  First, the manager doesn't start on login even though it's added to the sessions menu.  

The second problem is the issue that I've only read of nvidia users having, if I use the Emerald window decorator, the window title bars are invisible.  it's not that I can't drag the windows by them, I can, I just can't see them.  

Lastly, beryl seems to be functioning in a limited fashion.  Wobble effects work, but nothing else will apply.  Minimize effects can be set in the settings manager, but nothing changes after I set them.  The cube wont work either.  I can't get the "Rain" extra to work.  Blur doesn't seem to make a difference on or off.  I'm not sure what the deal is. 

If i set the window decorator to Heliodor, i can see the title bars, but I can't use the visually pleasing emerald themes.  Should I be using a different driver?  Here's the video device line from the xorg.conf file.  ```
Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Acer MFM DVI"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

Any help would be appreciated, and just for the record, I've used linux before, but I'm still quite new, so dumbing it down for me would also be appreciated.

---

### Post by ryboto on 2007-04-27
i forgot to mention that my video card is an x1950pro.

---

### Post by ryboto on 2007-04-28
just giving this a bump so it doesn't get lost and forgotten..

---

### Post by Zoltarp on 2007-05-01
Hey there, I am by no means an expert but I was having a similar problem. I have an Nvidia Quadro card in mine though. What I found out was that I was using the wrong utility to use Beryl's effects. I was using "desktop effects" under System\Preferences this I believe is Ubunto's desktop effects. I enabled the window wobble and cube thing and would loose the top of my windows, like you said. I found that opening a terminal window and typing " beryl-manager" brings up a tool bar, click on "Select window manager" and select Beryl. Hope that helps.

---

### Post by ryboto on 2007-05-07
So, now I'm getting new errors when I tried some LD command.  I tried running beryl-manager from a terminal, and it said it couldn't load beryl-xgl, and it would repeat that indefinitely until I ended the manager.  I installed beryl-xgl from a thread on the forums here, and now I get an error along the lines of "cannot find libXcomposite.so : cannot find object" and then if I go the the beryl-manager in the task bar, and right click it, window decorator options are greyed out, and I'm stuck with the metacity.  I can use Compiz, but i only get the wobble effect, and I can't use emerald themes.  Also, if I try to run emerald, I get 

"emerald: Could not acquire decoration manager selection on screen 0 display ":1.0"

So...I'm not sure what to do to get it working.  On top of that, ubuntu froze up twice in a row, once while my SMP folding client was beginning to start, and then just a moment ago when I was playing with beryl.

---

### Post by JKoder on 2007-05-09
> **ryboto said:**
> So, I really wanted to start folding using the linux SMP client.  I've got an Opteron running at 2.8ghz, and I've been getting a high PPD using ubuntu in VMware.  I've successfully installed ubuntu feisty 7.04, and I haven't really had any video related issues.  I wanted to try beryl, as a classmate of mine uses it on his nvidia based laptop.  Well, I'm having issues.  I'm using the fglrx driver, and beryl works, but strangely.  First, the manager doesn't start on login even though it's added to the sessions menu.  

The second problem is the issue that I've only read of nvidia users having, if I use the Emerald window decorator, the window title bars are invisible.  it's not that I can't drag the windows by them, I can, I just can't see them.  

Lastly, beryl seems to be functioning in a limited fashion.  Wobble effects work, but nothing else will apply.  Minimize effects can be set in the settings manager, but nothing changes after I set them.  The cube wont work either.  I can't get the "Rain" extra to work.  Blur doesn't seem to make a difference on or off.  I'm not sure what the deal is. 

If i set the window decorator to Heliodor, i can see the title bars, but I can't use the visually pleasing emerald themes.  Should I be using a different driver?  Here's the video device line from the xorg.conf file.  ```
Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Acer MFM DVI"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

Any help would be appreciated, and just for the record, I've used linux before, but I'm still quite new, so dumbing it down for me would also be appreciated.
So about your Emerald Window borders.
I also use Ubuntu 7.04 x64, beryl with an ATI Radeon Xpress 1100 video card
Everything is working PERFECTLY **BUT** to have Window borders with emerald you need.

1. Get the attachment and unzip it. It the beryl-xgl file from an older beryl binary.
This seems to be missing from Ubuntu 7.04 repository. 
Now, put this file in /usr/bin folder and reload emerald.
WOALA it work's
Let me know if this works for you to !

Thanks

---

### Post by ryboto on 2007-05-09
I had already added that to the usr/bin directory.  I'm going to try uninstalling beryl and emerald, and then reinstalling them.  Complete removal, then a new install.

---

### Post by ryboto on 2007-05-09
So, this is the error I get when I start beryl manager from a command line,

```
beryl-xgl: error while loading shared libraries: libXcomposit.so.1: cannot open shared object file: No such file or directory
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compis.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :1.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
inotify_add_watch: No such file or directory
```

For the record, libXcomposite is installed.  I've reinstalled it since I first got the error to see if it would fix it, still, nothing.

---

### Post by ryboto on 2007-05-09
I should also note that compiz works, i get the screen wobble, but thats it.  I can't use beryl, and I can't use emerald.

---

### Post by config on 2007-05-11
As I understand, you gotta choose between compiz and beryl. You can't have both working...

---

### Post by ryboto on 2007-05-11
> **config said:**
> As I understand, you gotta choose between compiz and beryl. You can't have both working...

I know...I was just stating, that Compiz is working with the heliodor window decorator.  I would rather be using beryl, but it doesn't want to work.

---

### Post by config on 2007-05-13
The same problem :). I'd love to use beryl but it is more buggy. Compiz is rather stable. Gotta wait?

---

### Post by strumluff on 2007-05-13
Well config Beryl works just fine for a lot of people including myself and I run it on a desktop with an nvidia card, and a laptop with an unsupported ATI card. It's totally stable on the desktop but there are a couple of annoying bugs with Beryl on the laptop but nothing that doesn't involve a quick workaround. I'd recommend you try out Beryl first and see for yourself, it's very simple to install on an nvidia card however a little trickier to install with most ATI cards. Ofcourse this depends on how computer literate you are.

It's still got a long way to go though so if you try it and its not behaving get rid of it for now and use Compiz it's still pretty. :)

---

### Post by ryboto on 2007-05-13
I don't think people are following my posts...I DO have beryl installed.  But whenever I start an XGL session, and switch to beryl as the window manager, it just crashes back to the default window manager.  I posted the errors is gives in the terminal.  Instead, I use the beryl-manager to select Compiz, because it works.

---

### Post by config on 2007-05-14
> **strumluff said:**
> Well config Beryl works just fine for a lot of people including myself and I run it on a desktop with an nvidia card, and a laptop with an unsupported ATI card. It's totally stable on the desktop but there are a couple of annoying bugs with Beryl on the laptop but nothing that doesn't involve a quick workaround. I'd recommend you try out Beryl first and see for yourself, it's very simple to install on an nvidia card however a little trickier to install with most ATI cards. Ofcourse this depends on how computer literate you are.

It's still got a long way to go though so if you try it and its not behaving get rid of it for now and use Compiz it's still pretty. :)
On my ATI x1950 pro + amd64 it works crappy (I have the least compatible configuration)... That's just my experience. Had to jump with tambourine around my computer for a long time to make it work and after that I had bugs anyway...
> **ryboto said:**
> I don't think people are following my posts...I DO have beryl installed.  But whenever I start an XGL session, and switch to beryl as the window manager, it just crashes back to the default window manager.  I posted the errors is gives in the terminal.  Instead, I use the beryl-manager to select Compiz, because it works.
> **config said:**
> As I understand, you gotta choose between compiz and beryl. You can't have both working...
Try to uninstall Compiz - that was the hint of my post.
By the way, what version of beryl do you have? I have more or less the same configuration as you do but could start beryl only using non-official version from "Treviños SVN-repository" ([have a look here]("http://forum.beryl-project.org/viewtopic.php?f=36&t=4046"))

---

### Post by ryboto on 2007-05-15
I looked at the website for the repository, but I'm still new, and not sure how to add it so that I can get beryl...care to show me what to do?

---

### Post by ryboto on 2007-05-15
I was able to add the repository.  I uninstalled beryl, reinstalled, and now when I load the xgl session, all I get is a screen full of artifacts.  Well, more like a lot of horizontal lines, and everything is completely garbled.  Hard to explain.  So...really not sure what to do at this point.

---

### Post by ronocdh on 2007-05-15
> **ryboto said:**
> I was able to add the repository.  I uninstalled beryl, reinstalled, and now when I load the xgl session, all I get is a screen full of artifacts.  Well, more like a lot of horizontal lines, and everything is completely garbled.  Hard to explain.  So...really not sure what to do at this point.
I used [this guide]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m") on my X1600 to get things going. Sorry if it's redundant, but I wanted to make sure you'd tried one with a high success rate. =)

---

### Post by ryboto on 2007-05-15
i guess a restart fixed the garbled screen, but beryl is still not working.  Whats even more odd is that even after adding those repositories, I can still only install version 0.2.1, not th 0.3 that's listed...GRRRRR

---

### Post by RAOF on 2007-05-15
0.3 doesn't, and almost certainly won't, exist (the packages that say "0.3" will be SVN snapshots that are no longer actively developed).  As far as I'm aware, essentially all Beryl development has been transferred to CompComm/OpenCompisiting.

---

### Post by ryboto on 2007-05-15
> **ronocdh said:**
> I used [this guide]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m") on my X1600 to get things going. Sorry if it's redundant, but I wanted to make sure you'd tried one with a high success rate. =)

yea, I used that too.  Still, no dice.  Compiz works nicely, but beryl just quits with the errors I've posted.  No one knows what those errors mean?? I've signed up for the beryl forums..but can't post there just yet.

---

### Post by config on 2007-05-16
Did you try starting beryl with "beryl-xgl --use-copy"?
I told you that beryl is buggy for such configuration...

Where did you sign in? What forums? The one on beryl-project.com is not working now...

Those errors that you've posted before say that there is the conflict in your system between beryl and compiz...

---

### Post by ryboto on 2007-05-16
> **config said:**
> Did you try starting beryl with "beryl-xgl --use-copy"?
I told you that beryl is buggy for such configuration...

Where did you sign in? What forums? The one on beryl-project.com is not working now...

I know, I signed up for the new forum.  Still, no responses.  As for starting beryl with beryl-xgl --use-copy, it immiediately gives me the LibXcomposite error.  So, until I can fix that, it's not working.

---

