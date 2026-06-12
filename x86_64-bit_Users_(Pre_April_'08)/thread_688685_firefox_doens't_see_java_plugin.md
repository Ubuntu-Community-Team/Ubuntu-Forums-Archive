---
title: "firefox doens't see java plugin"
date: 2008-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tectuktitlay on 2008-02-05
Hi,

I'm running a standard Gutsy install on a AMD 64 Athlon and I can't seem to install java in firefox. I've both tried gcj and blackdown plugins. After installing java object in a web page still show the "missing plugin"-picture. My about: plugins page looks like this:

```

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Totem Web Browser Plugin 2.20.0

    File name: libtotem-basic-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	ogg 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogg 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NSV video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	WMV video 	wms 	Yes
application/asx 	Playlist 	asx 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes

```

It doesn't seem to be there. I've got blackdown installed now, but with gcj I had exactly the same problem.

What can I do?

In desperation,

Tec

---

### Post by y-lee on 2008-02-05
Ok I had a very similar problem only none of my plugins were showing up in FF. I had compiled the newest version of FF myself in Dapper Keeping the old version. To solve this problem what I had to do was put a link in my mozilla profile plugin directory to the actual plugin. Look in this directory and see if you have a link to the java plugin in question.


```
/home/username/.mozilla/plugins
```

If not find the plugin and put a link to it in that directory.

Any questions just ask and if you already have a link there to the Java plugin post back and let us know. tho honestly if this is not it I'm not sure :confused:

---

### Post by Tectuktitlay on 2008-02-05
Y-Lee,

It works! Thanx! Do I have to do this for every user?

Gr, Tec

---

### Post by y-lee on 2008-02-05
> **Tectuktitlay said:**
> Y-Lee,

It works! Thanx! Do I have to do this for every user?

Gr, Tec

I had to. I was new to ubuntu then and wasn't sure why i had the problem. I figured it out myself tho.  I think if I had of known what i know now maybe I could have avoided the problem, but then again maybe not :lolflag:

---

### Post by Tectuktitlay on 2008-02-05
All right. So how would one go about avoiding this problem?
I'm pretty new, you see.

Gr, Tec

---

### Post by y-lee on 2008-02-05
I think my problem had to do with the way i compiled firefox, i used advice on a debian forum. I don't know about your problem. are ya using the firefox that comes with Ubuntu or another? Actually since i fixed mine I haven't give it much thought, tho the next time i install Ubuntu I plan on using "official" information as much as possible. lol

Honestly I'm just glad i didn't have to explain in detail how to find your plugin or how to create a link. So you are certainly not a total Noob.

---

### Post by Tectuktitlay on 2008-02-05
> So you are certainly not a total Noob.

Thanx. I'm using ubufox in Gutsy. I'lll update my profile.

Unfortunately I can't open the applet it's all about: SSL-tunnel-agent.

I have to work on a windows PC at my work via Remote Desktop. I thought maybe I can do this from Ubuntu as well as from Windows. The applet works perfectly on an 32-bit Ubuntu-machine and I found out I can use rdesktop to log into the PC. I't really weird and cool to see a little Windows-XP-desktop in one of your Ubuntu-windows!

Unfortunately I can't do this at home, clearly. When I open the page Blackdown comes along way in starting up the agent, but it fails at some point. Is there an offical java-plugin for 64-bit Linux?

Gr, Tec

---

### Post by FooAtari on 2008-02-05
I'm having the same problem

I upgraded from Kubuntu 7.10 (32-bit) to Ubuntu 7.10 (64-bit)

Now flash and java doesnt work, even though I installed them from synaptic.  Can you give more details I put links in the plugin directory? (sorry)

Thanks

Edit

Actually I think the plugins are there.  Too late too look at this just now, ill look tomorrow :)

---

### Post by y-lee on 2008-02-05
> Is there an offical java-plugin for 64-bit Linux?

I don't know  I not a 64 bit user. Actually gotta go now RW things to do. Google it and look around, or search here.

Ah FooAtari no need to be sorry but I don't have time now. Hopefully someone will help if not, I'll be back on today or tomorrow. :)

```
man ln
```

will tell ya about links, to get out of man hit q

---

### Post by Tectuktitlay on 2008-02-05
y-lee, got it! Thanx for you help.

fooatari, just look in  /usr/lib/mozilla/plugins/
There should be a file like libjavaplugin_oji.so, but it could be named a bit different.
In my case it was called like that. Name should include java and plugin and end with .so .
Then do this:
ln -s  /usr/lib/mozilla/plugins/libjavaplugin_oji.so ~/.mozilla/plugins/
killall firefox-bin

That should be it.

Gr, Maarten

---

### Post by FooAtari on 2008-02-06
Thanks, I'll try that tonight.

---

### Post by robb0100 on 2008-03-17
> **Tectuktitlay said:**
> y-lee, got it! Thanx for you help.

Then do this:
ln -s  /usr/lib/mozilla/plugins/libjavaplugin_oji.so ~/.mozilla/plugins/
killall firefox-bin

That should be it.

Gr, Maarten

My 7.10 install with FF required something just a little bit different:
ln -s  /usr/lib/mozilla/plugins/libjavaplugin_oji.so ~/.mozilla/firefox/plugins/plugins

For some reason there were 2 levels of plugins folders and the .so file needed to be in the lower one.

Maybe this will help others.

Another big thanks to Maarten and y-lee - I have been sweating this one for a while.

Do Ubuntu developers know about this fix?

---

### Post by MarshyTheKid on 2008-04-04
I'm having problems getting Java to work again on FireFox. I went from using the 32 bit version, to using the 64 bit, since my 32 no longer liked java or flash. I got flash to work, but now its Java

```
$ sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so ~/.mozilla/plugins
```

Says that its not a directory.

```
$ sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so ~/.mozilla/firefox/plugins
```

Thats accepted fine but when I go to a page that has java on it, it still says I need to install it.

Any help?

---

### Post by prostar on 2008-04-04
Jave 1.4 is getting "a little old".  I have sun jre 1.6 installed for most programs, and I have the "icedtea" 1.7 mozilla plugin installed for the web.  Just look in synaptic for "mozilla plugin" and see what your choices are.  I don't think the "blackdown" works too well.  The only downfall I"ve found is you can't click twice in an applet.  You have to scroll your mouse off the applet then back on to be able to click again.  If anyone knows how to fix that, I'd be golden.

---

### Post by MarshyTheKid on 2008-04-04
I love it when a plan comes together.

I already had icedtea installed. When I would try to search for a plugin with FF, it would tell me to instal GCJ, but when I tried to it told me that icedtea-java7-plugin was installed.

```
sudo aptitude install gcjwebplugin icedtea-java7-plugin
```
That fixed it!

---

### Post by DarkW0lf on 2008-04-05
I have Sun JRE 1.6 installed and cannot find a java plugin in my mozilla/firefox directory so I can't link it to my home directory. Checked the java directory and still cannot find a plugin to link.

Where do I get the plugin ?

Someone asked about flash, I installed Gnash and it's related plugins and I haven't had any problems except when a site needs ver 9 ( gnash only supports up to 8 )

---

### Post by prostar on 2008-04-05
The post just above yours should fix it up (#15).  Or search synaptic for "mozilla plugin" and you should find the icedtea 1.7.  Assuming you are both on x64, do you have the click problem I described?  I'd really like to get rid of that...

---

### Post by MarshyTheKid on 2008-04-07
I'm so pissed. 
My university requires java and flash to be able to log in for wireless(If they supported Linux, which they don't so I get **** service). My java was working for some sites kinda crapily, and it doesn't work at all for the log in.
Curse me for installing 64 bit. Any help with solving this java problem?

---

### Post by Kilz on 2008-04-07
> **MarshyTheKid said:**
> I'm so pissed. 
My university requires java and flash to be able to log in for wireless(If they supported Linux, which they don't so I get **** service). My java was working for some sites kinda crapily, and it doesn't work at all for the log in.
Curse me for installing 64 bit. Any help with solving this java problem?

If icedtea does not work for you , then install the [32bit browser/flash/java setup]("http://ubuntuforums.org/showthread.php?t=202537"). Icedtea is not Sun java, there is no 64bit Sun Java plugin.

---

### Post by MarshyTheKid on 2008-04-08
> **Kilz said:**
> If icedtea does not work for you , then install the [32bit browser/flash/java setup]("http://ubuntuforums.org/showthread.php?t=202537"). Icedtea is not Sun java, there is no 64bit Sun Java plugin.
I recently was using that until one day it randomly stopped working. I did no updates, no installs, no changes.

---

### Post by DarkW0lf on 2008-04-13
What is up with gcj, gij and icedtea ?

I am trying to figure out which is which for an AMD 64 machine and still get the plugin.

---

### Post by Kilz on 2008-04-13
> **DarkW0lf said:**
> What is up with gcj, gij and icedtea ?

I am trying to figure out which is which for an AMD 64 machine and still get the plugin.

gcj and icedtea are more or less the same thing. Installing icedtea should give you a 64bit java plugin. But it isnt Sun Java, it isn't perfect and will not work with every site.

---

### Post by DarkW0lf on 2008-04-19
I asked because gcj/gij web plugin doesn't seem to be working. Installed 1.4.2 version and applets won't load.

I was wondering if icedtea plugin would work.

Even sun java doesn't always work so I am not too worried about that.

---

