---
title: "Sun Java 64 bit"
date: 2009-02-08
forum: x86 64-bit Users
---

### Post by Sprocket_dk on 2009-02-08
1. Remove already installed Java. (search java plugin in System>Administration>Synaptic)

2. Download latest version; [HTML]http://java.sun.com/javase/downloads/index.jsp[/HTML] (current version "jre-6u12-linux-x64.bin" will be used in this guide)

Click download at "Java SE Runtime Environment (JRE)" > choose platform "Linux x64" > mark "i agree ....." click continue > download file " jre-6u12-linux-x64.bin"

3. Move downloaded java to jvm dir;
```
sudo mv jre-6u12-linux-x64.bin /usr/lib/jvm/
```
(make sure that the terminalen is in the same dir as jre-6u12-linux-x64.bin)

4. Change to dir;
```
cd /usr/lib/jvm/
```

5. Grant permissions;
```
sudo chmod a+x jre-6u12-linux-x64.bin
```

6. Install java;
```
sudo ./jre-6u12-linux-x64.bin
```
(press space until asked; Do you agree to the above license terms? [yes or no], answer yes)

7. Delete java installation file;
```
sudo rm /usr/lib/jvm/jre-6u12-linux-x64.bin
```

8. Make link to firefox 3 java plugin;
```
sudo ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib64/firefox-addons/plugins/
```

8. Make link to Epiphany java plugin;
```
sudo ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib64/epiphany-gecko/2.24/plugins
```


Close your browser and start it up again. You should now be able to use 64 bit java.

---

### Post by Sprocket_dk on 2009-02-18
Edit. New link to firefox java plugin.
```
sudo ln -s /usr/java/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib64/firefox-addons/plugins/
```

---

### Post by marcelkoopman on 2009-02-18
Thanks for this.

Maybe its also good to add this to .bashrc?
> export JAVA_HOME=/usr/java/jre1.6.0_12/

---

### Post by albandy on 2009-02-18
Some advices:

install the java virtual machine in /usr/lib/jvm, is the folder assigned for java virtual machines.

in /etc/alternatives are the links to java javac .... use it.

as you can see, JAVA_HOME is not defined, this is because JAVA_HOME should be defined for each java software, some work with jre 1.5 other with jre 1.6 or 1.4 so if you define it as a system variable (bashrc) some programs can crash.

---

### Post by Sprocket_dk on 2009-02-18
@albandy

Thanks for the advice. I've corrected the guide.

---

### Post by jespdj on 2009-02-21
Thanks Sprocket_dk! That was easy and it works also on 64-bit Hardy! :)

---

### Post by trekguy on 2009-02-21
> **albandy said:**
> Some advices:

install the java virtual machine in /usr/lib/jvm, is the folder assigned for java virtual machines.

in /etc/alternatives are the links to java javac .... use it.

as you can see, JAVA_HOME is not defined, this is because JAVA_HOME should be defined for each java software, some work with jre 1.5 other with jre 1.6 or 1.4 so if you define it as a system variable (bashrc) some programs can crash.

I followed some directions which has resulted in my Java being located in  /usr/java/jre1.6.0_12.

I have no /usr/lib/jvm folder.  Is it simple enough to create a folder, and move it?  Or do I need to start from scratch?  Everything Java seems to work fine except Frostwire... which cannot seem to find the correct path to Java... could that be because of the current location?

---

### Post by trekguy on 2009-02-22
I have reinstalled Java into /usr/lib/jvm/jrel.6.0_12.  

It is also in /usr/java/jre1.6.0_12.

Is it a problem to have it two locations??

Still no joy with FrostWire.  :(

---

### Post by Sprocket_dk on 2009-02-22
> **trekguy said:**
> I have reinstalled Java into /usr/lib/jvm/jrel.6.0_12.  

It is also in /usr/java/jre1.6.0_12.

Is it a problem to have it two locations??

Still no joy with FrostWire.  :(

No it's no problem. Just link it to your browser and make sure it's the only java plugin installed.

---

### Post by novafluxx on 2009-02-22
I also edited my /etc/environment file which controls the path, and added /usr/lib/jvm and /usr/lib/jvm/bin

---

### Post by ck_tomato on 2009-03-04
> **Sprocket_dk said:**
> 
1. Remove already installed Java. (search java plugin in System>Administration>Synaptic)

Searching "java plugin" returns a number of packages (around 80). Are all of them to be removed?

---

### Post by Sprocket_dk on 2009-03-04
Only those which intefere with your browser and are not used elsewhere.

If dought, then post your about: plugins from your browser.

(type about: plugins in your browsers adress minus the space)

---

### Post by ck_tomato on 2009-03-04
Here is the about: plugins from my browser.
Thank you very much.



Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.

Adobe Reader 8.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
IcedTea Web Browser Plugin

    File name: IcedTeaPlugin.so
    The IcedTea Web Browser Plugin executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
Totem Web Browser Plugin 2.24.3

    File name: libtotem-basic-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	application/annodex type 	anx 	Yes
audio/annodex 	audio/annodex type 	axa 	Yes
video/annodex 	video/annodex type 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wmv 	Yes
video/x-ms-wm 	Windows Media video 	wmv 	Yes
video/x-ms-wmp 	Windows Media video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/x-ms-wmp 	Windows Media video 	wmp 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes

---

### Post by Krause on 2009-03-05
Is the sun java thats in the intrepid (or jaunty if your using the alpha) repositories not the true 64bit sun java?

I just remember it working in firefox on jaunty when I installed the Sun JDK6/JRE6 and the sun-java-plugin package. (the later package is only in the jaunty repos)

---

### Post by Sprocket_dk on 2009-03-11
@ck_tomato

You'll have to remove IcedTeaPlugin to use sun java. Search icedtea in synaptic and mark for removal. Then follow the guide and install sun java.

---

### Post by Sprocket_dk on 2009-03-11
@Krause

> **Krause said:**
> Is the sun java thats in the intrepid (or jaunty if your using the alpha) repositories not the true 64bit sun java?

I just remember it working in firefox on jaunty when I installed the Sun JDK6/JRE6 and the sun-java-plugin package. (the later package is only in the jaunty repos)

Sun jave 64 bit isn't in the respositories (last time I checked). Some homebanking sites require the new 64 bit java release in order to work.

I would'nt be able to tell if it is in the jaunty respositories.

---

### Post by marcelkoopman on 2009-03-11
Its in the jaunty repository. Running jaunty now and the plugin works great.
Just need to install sun-java6-plugin.

So maybe wait a month or upgrade now to jaunty?

---

### Post by zika on 2009-03-11
it should not be so complicated and should not be written in so many places. please take a look at [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59) that was tested and re-tested. it works ... ;) thanks presence1960 for testing it ... ! it works with the same setting with FF2.* FF3.0.*, FF3.1*, FF3.2*, Epiphany, Swiftweasel, KDE, ...

---

### Post by Sprocket_dk on 2009-03-12
@zika

Great work zika and you're right. This thread should be deleted.

---

### Post by ck_tomato on 2009-03-12
@Sprocket_dk

Thank you so much.

---

### Post by SuperSonic4 on 2009-03-12
Many thanks for the guide and thanks for using the terminal commands, it makes it easier to follow in kubuntu too

---

### Post by blakjack on 2009-03-13
Hi

I follow the guide but i can't make applets run with the new plugin, and in the page [http://browserspy.dk/java.php](http://browserspy.dk/java.php) detect the new version of the plugin but the applet appers in gray.

I put an attachment of my screenshot.

And i do this.
I download the jdk 6 update 12, and i put in /opt/java/jdk1.6.0*
I made the link from  /opt/java/jdk1.6.0_12/jre/lib/amd64/libnpjp2.so to ~/.mozilla/plugins/ and /usr/lib/mozilla/plugins/ restart firefox and i have installed swiftweasel3 too, and in both programs in about:plugins apperce this.
**********************************************************************
libnpjp2.so

    File name: libnpjp2.so

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_12 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_12 	Java

I did the update-alternatives stuff and i try to move jdk folder to /usr/lib/jvm/ and the same i get JAVA_HOME variable in my .bashrc link to jdk folder i try the same but deleting this variable and i got the same problem, i try to check with out compiz and the same problem too.

But if i run firefox in a terminal with $ sudo firefox the applets appears but if is an animation and compiz is enabled firefox crash, with out compiz works fine.

My question is why i most run firefox with sudo to watch the applets?
I need do something else ? 
I check my permissions folder and the permissions are this drwxr-xr-x with root as owner.

Ok i hope to help me out with this problem.

Sorry for my bad english i'm still learning :D

---

### Post by blakjack on 2009-03-13
I miss somethig, Im using hardy 64, I have Vaio Core 2 Duo and Nvidia GeForce 8400M GT card with nvidia drivers 180.29

My kernel 2.6.24-24-generic

Best Regards

---

### Post by Sprocket_dk on 2009-03-14
@blakjack

Give us your entire about:plugins from your browser and I'll run it through.

---

### Post by jespdj on 2009-03-14
> **blakjack said:**
> I follow the guide but i can't make applets run with the new plugin, and in the page [http://browserspy.dk/java.php](http://browserspy.dk/java.php) detect the new version of the plugin but the applet appers in gray.
Try switching off Compiz (desktop effects) and see if that helps. Some combinations of Java / graphics card and driver / Compiz don't work well...

---

### Post by blakjack on 2009-03-15
Hi Sprocket_dk, this are my plugins on firefox 3 64

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
libnpjp2.so

    File name: libnpjp2.so

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_12 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_12 	Java 		Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	- 	ogg 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	- 	anx 	Yes
audio/annodex 	- 	axa 	Yes
video/annodex 	- 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	unknown 		Yes
application/vlc 	unknown 		Yes
video/x-google-vlc-plugin 	unknown 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Microsoft ASX playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
DivX Browser Plug-In

    File name: mplayerplug-in-dvx.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes
QuickTime Plug-in 7.4.5

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plug-in

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
application/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in 3.55

    File name: mplayerplug-in.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
video/3gpp 	MPEG 4 Video 	mp4,3gp 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
audio/x-ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
audio/flac 	FLAC Audio 	flac 	Yes
audio/x-flac 	FLAC Audio 	flac 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/x-flv 	Flash Video 	flv 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes

hope you can help me.

---

### Post by blakjack on 2009-03-15
Hi jespdj, i try to turn off compiz and java applets appears in gray too, only works if run 
> sudo firefox
But i don't know why i must run firefox with sudo in order to applets works.

Thanks.

---

### Post by jespdj on 2009-03-15
It only works when you run Firefox as root (with sudo)? Aha, so it is a permissions problem. That's really strange. How *exactly* did you install Java? Do the directories and files that have to do with Java have the right permissions, so that you can read them when logged in as a normal user?

It's hard to find out what's wrong exactly, there are many different possibilities for which directories or files don't have the right permissions. I'd start looking at your **~/.mozilla** directory, and check if everything has the right permissions there.

---

### Post by Yellow Pasque on 2009-03-15
Good work on the guide, sprocket. It should really be stickied until the release of Jaunty.

blakjack, can you post the output of:
```
groups
```

---

### Post by JimmyA on 2009-03-15
I can't get my JAva to work with Firefox either.
I'm running Kubuntu.

I installed Java 6 with Synaptic but I can't add Java to Firefox.
I alreadly tried number 8 but no success. 

Hope you guys can help me:)

---

### Post by zika on 2009-03-15
> **JimmyA said:**
> I can't get my JAva to work with Firefox either.
I'm running Kubuntu.
I installed Java 6 with Synaptic but I can't add Java to Firefox.
I alreadly tried number 8 but no success. 
Hope you guys can help me:)
```

cd ~
cd .mozilla
mkdir plugins
cd plugins
ln -s /usr/lib/jvm/java-6-sun-1.6.0.12/jre/lib/amd64/libnpjp2.so libnpjp2.so

```
I assume You have 64-bit and the location above is from Jaunty. if You do not, just do```
locate libnpjp2.so
``` and change the location given above for the one You've got. I hope it will work. :)

---

### Post by JimmyA on 2009-03-15
> **zika said:**
> ```

cd ~
cd .mozilla
mkdir plugins
cd plugins
ln -s /usr/lib/jvm/java-6-sun-1.6.0.12/jre/lib/amd64/libnpjp2.so libnpjp2.so

```
I assume You have 64-bit and the location above is from Jaunty. if You do not, just do```
locate libnpjp2.so
``` and change the location given above for the one You've got. I hope it will work. :)
Thank you but it's still not working :(

---

### Post by blakjack on 2009-03-15
> **jespdj said:**
> It only works when you run Firefox as root (with sudo)? Aha, so it is a permissions problem. That's really strange. How *exactly* did you install Java? Do the directories and files that have to do with Java have the right permissions, so that you can read them when logged in as a normal user?

It's hard to find out what's wrong exactly, there are many different possibilities for which directories or files don't have the right permissions. I'd start looking at your **~/.mozilla** directory, and check if everything has the right permissions there.

Ok, i downloaded the jdk-6u12-linux-x64.bin and the owner is me and the permissions are -rwxr-xr-x (owner RWX grups RX others RX), i copied to /opt/java/ then i run this.

> sudo ./jdk-6u12-linux-x64.bin

i check the permissions folder of the jdk and are this drwxr-xr-x with root owner.

And i check my folder **~.mozilla/** and the owner is me and the permissions are drwx------

Thanks

---

### Post by blakjack on 2009-03-15
> **Temüjin said:**
> Good work on the guide, sprocket. It should really be stickied until the release of Jaunty.

blakjack, can you post the output of:
```
groups
```

Hi, my output of groups are:

> blakjack adm dialout fax cdrom floppy tape audio dip video plugdev scanner nvram fuse lpadmin admin pulse-access pulse-rt sambashare clamav mysql gnunet

Thanks

---

### Post by ztirffritz on 2009-03-19
I followed the instructions in this thread, but when I try to test my installation here, it still shows an older version:

[http://java.com/en/download/installed.jsp?detect=jre&try=1](http://java.com/en/download/installed.jsp?detect=jre&try=1)

"Your Java version is 1.6.0_0"

Anyone know how to fix this?

---

### Post by ztirffritz on 2009-03-19
I figured out my problem, I had IcedTea installed.  I'd forgotted that I installed it.  looking at about:plugins in Firefox reminded me.

---

### Post by blakjack on 2009-03-23
I made it, my java plugin works now just fine.
I just uninstall al programs that i have installed referencing java, like sun jdk 5, eclipse 3.2 , tomcat and other java libs, then i restarted the x system and the plugins works again. I don't know what exactly of al dependencies were the problem but works now.

This are the list of the programs that i removed.
ant
ant-optional
eclipse
eclipse-efj
eclipse-jdt
eclipse-pde
eclipse-platform
eclipse-rcp
eclipse-sdk
gcj-4.2-base
gij-4.2
java-common
junit
junit4
libbackport-util-concurrent-java
libbcel-java
libcommons-beanutils-java
libcommons-codec-java
libcommons-collections-java
libcommons-collections3-java
libcommons-dbcp-java
libcommons-digester-java
libcommons-el-java
libcommons-launcher-java
libcommons-logging-java
libcommons-modeler-java
libcommons-pool-java
libdom4j-java
libgcj-common
libgcj8-1
libgcj8-1-awt
libjaxen-java
libjaxme-java
libjaxp1.3-java
libjdom1-java
libjsch-java
liblog4j1.2-java
liblucene-java
libmx4j-java
libqt3-java
libregexp-java
libsaxonb-java
libservlet2.3-java
libservlet2.4-java
libswt3.2-gtk-java
libtomcat5.5-java
libxerces2-java
libxom-java
libxpp2-java
libxpp3-java
sun-java5-bin
sun-java5-demo
sun-java5-fonts
sun-java5-jdk
sun-java5-jre
libpigment0.3-8 
libxul-common 
odbcinst1debian1 
libqt3-jni 
unixodbc 
libxul0d
libmozjs0d 
libswt3.2-gtk-jni 
liblucene-java-doc


Thanks!!

---

### Post by Arup on 2009-03-23
Java latest works beautifully with Opera 9.64:D

---

### Post by acidblue on 2009-04-03
AAAAhhhhggg! 
I am so frustrated with 64bit Linux/java
I followed the giude and got java working in Firefox.
But nothing else works!
Frostwire won't start, and I can't complie java programs, no javac. when i do in bash 'Java -version '
i get "java not installed"
I tried several re-boots to no avail, i even edited my .bashrc file,
as long as /etc/enviroment 

I'm using 8.10.
Everything was fine using IcedTea, but i didn't have javac for compliling.
So i decided to uninstall it and install using this guide.
Now things are worse and still no javac.
I need help, please!

---

### Post by zika on 2009-04-04
this way You've installed only plugin. You might try simply:
```
sudo apt-get install sun-java6-bin
sudo apt-get install sun-java6-jdk
sudo apt-get install sun-java6-jre
```or register installed java through ```
sudo update-alternatives --install "/usr/bin/java" "java" "/where_is_Your_java_installed/java" 1
```with first option easier ...

---

### Post by acidblue on 2009-04-04
> **zika said:**
> this way You've installed only plugin. You might try simply:
```
sudo apt-get install sun-java6-bin
sudo apt-get install sun-java6-jdk
sudo apt-get install sun-java6-jre
```or register installed java through ```
sudo update-alternatives --install "/usr/bin/java" "java" "/where_is_Your_java_installed/java" 1
```with first option easier ...

Thanks for the reply, thats what i ended up doing.
Well the first part anyway,and all is well.
Firefox runs fine, as does eclipse and so on.

---

### Post by presence1960 on 2009-04-16
> **zika said:**
> it should not be so complicated and should not be written in so many places. please take a look at [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59) that was tested and re-tested. it works ... ;) thanks presence1960 for testing it ... ! it works with the same setting with FF2.* FF3.0.*, FF3.1*, FF3.2*, Epiphany, Swiftweasel, KDE, ...

it works very well and your instructions are very easy to follow. Thanks for showing me another way to install 64bit java. I have shared your instructions a number of times in the forums and always give you credit and thanks zika!

---

