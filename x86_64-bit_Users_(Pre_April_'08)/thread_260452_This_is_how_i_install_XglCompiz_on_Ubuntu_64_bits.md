---
title: "This is how i install Xgl/Compiz on Ubuntu 64 bits"
date: 2006-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by city-17 on 2006-09-18
I recently got Xgl/Compiz running on Dapper 64 bits, i hope this works to others with similar configuration (a clean install of Dapper Drake 64 bits, Nvidia card and Gnome).

I own a Nvidia GeForce6800 and i installed the propietary driver version 8762 using Synaptic, just searched for the packages named 'nvidia-glx' and 'linux-restricted-modules-2.6.15-26-amd64-generic' and marked them for installation. 

Note: 2.6.15-26-amd64-generic is what i get with the command uname -r.

When the installation finished i typed the following
```
sudo nvidia-glx-config enable
```
After restarting my machine i added the option RenderAccel to the xorg configuration with sudo gedit /etc/X11/xorg.conf
```
Section "Device"
	Identifier	"NVIDIA Corporation NV41.1 [GeForce 6800]"
	Driver		"nvidia"
        Option "RenderAccel" "true"
        .
        .
        .
```
Then i added this repositories at the end with sudo gedit /etc/apt/sources.list
```
## These repositories provides the latest Xgl/Compiz stuff built for AMD64
deb http://ubuntu.systemadministrator.org dapper eyecandy
deb-src http://ubuntu.systemadministrator.org dapper eyecandy
```
After that i typed
```
wget http://ubuntu.systemadministrator.org/2F306651.gpg -O- | sudo apt-key add -
sudo apt-get update

```
I installed the following packages with aptitude: 'xserver-xgl', 'compiz',
'compiz-gnome' and 'csm'. Aptitude took care of all dependencies.

Next, i created this script to start xgl (sudo gedit /usr/bin/startxgl.sh)
```

#!/bin/sh 
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session
```
Then i made the script executable with the following command
```
sudo chmod +x /usr/bin/startxgl.sh
```
And then added the script to sessions (sudo gedit /usr/share/xsessions/xgl.desktop)
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```
Finally i looged in the new Xgl session and typed at console 
```
compiz-start
```

These are the guides i have used so far:
[https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")
[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz]("https://help.ubuntu.com/community/CompositeManager/InstallingCompiz")
[http://www.wiredfool.com/2005/06/15/widescreenLcdsAndUbuntuLinux]("http://www.wiredfool.com/2005/06/15/widescreenLcdsAndUbuntuLinux")

---

### Post by jamesford on 2006-09-19
thanks for posting this. been trying multpiple howtos without any success so nice that someone is posting their working method

bookmarked, will try it out later

---

### Post by Jon &quot;Yogi&quot; on 2006-09-19
Followed your how-to, and things seem to be ok until I log in to the XGL session.  I get sent back to the login screen.  Have any ideas what could be going on?

---

### Post by gurgle on 2006-09-19
check this out:

[http://www.tectonic.co.za/view.php?id=1153](http://www.tectonic.co.za/view.php?id=1153)

---

### Post by fabertawe on 2006-09-20
What exactly do Xgl and Compiz do?! I've seen so many posts about them but no real info and been wanting to ask this for ages. Anyone have a good link with screenshots or some good info?

Cheers ... Paul

---

### Post by jamesford on 2006-09-20
search youtube.com for compiz
pics wont do it justice

---

### Post by city-17 on 2006-09-20
> **Jon "Yogi" said:**
> Followed your how-to, and things seem to be ok until I log in to the XGL session.  I get sent back to the login screen.  Have any ideas what could be going on?

Sorry, i forgot to mention that you have to make the script executable, but i have already updated that in the howto.

---

### Post by hannav85 on 2006-09-21
Hi,

Regarding this bit:

> **city-17 said:**
> 
I installed the following packages with aptitude: 'xserver-xgl', 'compiz',
'compiz-gnome' and 'csm'. Aptitude took care of all dependencies.
[/URL]

I followed this (with very little knowledge of aptitude) and firstly the terminal started listing a load of kde programmes it was downloading (im running gnome), why is this and is that correct?! (i went to search and put in xserver-xgl and then double clicked on it and pressed g for download). And secondly aptitude didnt list a programme called "csm." Where exactly do i find that??

Hope someone can help me...

Thanks in advance,

Hanna

---

### Post by hannav85 on 2006-09-21
> **city-17 said:**
> Sorry, i forgot to mention that you have to make the script executable, but i have already updated that in the howto.

Hi, i followed both your guide and the one on the wiki pages listed at the bottom. However, im now getting the same problem as Jon "Yogi." Every time i change the session to xgl the screen goes the ubuntu colour and then remains for about ten seconds before sending me back to the login page :confused: 

Any ideas? Making the file executable obviously hasnt helped for me :sad: 

Thanks, Hanna

---

### Post by gurgle on 2006-09-21
does this give you restart and shutdown buttons?

also, cant you just use compiz-manager instead of creating a whole new session?

---

### Post by Jon &quot;Yogi&quot; on 2006-09-21
So far, I have been able to get to the ubuntu color like Hanna, and get kicked to the login screen. That is fully functional. Gurgle, I have tried using compiz-manager in user-space from a different howto, but that didn't work either. 

Reinstalled dapper last night instead since I had some extra time.  Dist-upgraded and will retry the howto this afternoon.

Just incase anyone needs /wants to know, I have an evga geforce 6800.

Jon


I just went through the howto again, using automatix to install the nvidia drivers, and everythings works great so far.  My guess as to why is didn't work the first time was residual config files floating around from other howtos that didn't work.  The fresh install (or at least having a default install) seems to be the ticket. Thanks everyone for helping out! :D

---

### Post by hannav85 on 2006-09-21
Jon, Could you explain exactly how you used automatix to install the nvidia drivers? Did you basically follow this how to after installing nvidia drivers from automatix? Is it the nvidia-glx? Sorry im quite new to linux and have been trying to get this xgl-compiz thing to work for a long time now with many a x server crash! :( 

Cheers,

Hanna

---

### Post by Jon &quot;Yogi&quot; on 2006-09-21
> **hannav85 said:**
> Jon, Could you explain exactly how you used automatix to install the nvidia drivers? Did you basically follow this how to after installing nvidia drivers from automatix? Is it the nvidia-glx? Sorry im quite new to linux and have been trying to get this xgl-compiz thing to work for a long time now with many a x server crash! :( 

Cheers,

Hanna

I just used [automatix]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_Ubuntu_6.06_Dapper_Drake") (just install it like it says on the automatix site, then have it install the nvidia driver). After the driver is installed, I restarted to make sure it was working right (you should see a nvidia splash screen for a breif second before the logon screen. If not, you can always try to open the nvidia settings (in gnome) from Applications>System Tools>Nividia Settings). Once I knew that it was working fine, I followed the howto from installing "xserver-xgl" onward.

If you have any problems, just let us know. ;)

Jon

---

### Post by Yolan on 2006-09-21
I'm having trouble getting XGL working on my AMD64. I've everything installed and configured (from what I can tell) properly. The problem is that when I go to run Xgl, I get the following error:

[0] couldn't create glitz drawable for window.

Any ideas?

---

### Post by city-17 on 2006-09-21
> **hannav85 said:**
> Hi,

I followed this (with very little knowledge of aptitude) and firstly the terminal started listing a load of kde programmes it was downloading (im running gnome), why is this and is that correct?! (i went to search and put in xserver-xgl and then double clicked on it and pressed g for download). And secondly aptitude didnt list a programme called "csm." Where exactly do i find that??

Hope someone can help me...

Thanks in advance,

Hanna

Do you mean that you had trouble after doing this?
```
sudo aptitude install xserver-xgl
```

---

### Post by gurgle on 2006-09-21
Will this work if i install the drivers using teh Envy tool? Also, are the Gnome restart and shutdown buttons missing using this method?

---

### Post by city-17 on 2006-09-21
> **gurgle said:**
> does this give you restart and shutdown buttons?

also, cant you just use compiz-manager instead of creating a whole new session?

It's true that this method breaks those buttons but only in the Xgl session (the default session remains intact), you have to logout from the Xgl session and shutdown or restart from the login screen

The advantage of having a Xgl session is that right now Xgl/compiz is at development and may crash with some 3d games or applications that use opengl, and this way you always have your default session intact. I see another advantage in case that the installation fails because when using the session  method you just won't be able to log into the Xgl session but when using the other method the X server will break and you have to undo things from a text mode shell.

---

### Post by city-17 on 2006-09-22
> **gurgle said:**
> Will this work if i install the drivers using teh Envy tool? Also, are the Gnome restart and shutdown buttons missing using this method?

I haven't tried the Envy script by myself but as long as it gets you the Nvidia propietary driver 8762 or 8774 installed you shouln't have trouble.

---

### Post by thread on 2006-09-22
Does the gconf plugin for compiz work on AMD64 yet? I don't seem to have ANY of the compiz plugins at the moment, though.

I can't install compiz-plugins because it depends on csm, which I assume isn't available because I'm AMD64? How does one run xgl on AMD64 without a csm package (and thus compiz-plugins) ?

---

### Post by gurgle on 2006-09-22
thanks for the replies City 17.

the envy script gets rid of some packages, maybe i shouldnt use that. 

also, what about compiz-manager, the replacement for compiz-start written by Quinn? That would be helpful I think. 

thanks!

---

### Post by gurgle on 2006-09-22
> **thread said:**
> Does the gconf plugin for compiz work on AMD64 yet? I don't seem to have ANY of the compiz plugins at the moment, though.

I can't install compiz-plugins because it depends on csm, which I assume isn't available because I'm AMD64? How does one run xgl on AMD64 without a csm package (and thus compiz-plugins) ?

i think RAOF's repo has csm, am i right?

---

### Post by city-17 on 2006-09-22
Hi, i hope this solves some doubts:

Csm is available with the repos mentioned in my post, Csm is the new compiz-manager (i think) and means compiz settings manager, this package allows you to configure the compiz plugins. I have attached a picture of it. With this package you have to type at console compiz-start in order to start compiz.

If you follow my directions, then Aptitude will automatically install the packages that are dependencies, like this one: compiz-plugins 0.37-0ubuntu1, wich already contains the new water plugin.

---

### Post by gurgle on 2006-09-22
city: why are we using compiz-start instead of compiz-manager?

---

### Post by city-17 on 2006-09-22
> **gurgle said:**
> city: why are we using compiz-start instead of compiz-manager?

Because we are using the session method to install Xgl.

---

### Post by kislo_metal on 2006-09-22
had some problem with all borders when compiz-manager started...and else i can`t use the cgwd thems/:confused: 
Had any ideas?

---

### Post by gurgle on 2006-09-23
i am getting the issue that the XGL session will not start.

i sign in to the session OK, but then after about 10 seconds i get kicked back to teh sign in screen. :(

---

### Post by patslap on 2006-09-24
I experience the same session login problem as several other people: I select XGL as new session whilst in the login screen, enter username and password, then screen displays ubuntu-brown background (and nothing else) for about 10 seconds before returning to the login screen.



Anyone had any success fixing this? :confused:

---

### Post by bernardfrancois on 2006-09-24
I tried following the guide, but at the following point I get stuck:

```

$ sudo apt-get install xserver-xgl compiz compiz-gnome csm
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
compiz is already the newest version.
compiz-gnome is already the newest version.
E: Couldn't find package csm
$ 

```

---

### Post by brent09 on 2006-09-24
edit: former difficulty solved
Now I've got the same problem as others where i try to login in Xgl and it takes me back to the login screen.

I've reinstalled ubuntu and installed my nvidia drivers with automatix as was suggested earlier and it has not solved anything.

---

### Post by patslap on 2006-09-24
Has anyone got compiz running on 64-bit? Seems everyone is experiencing the same problem at login.

---

### Post by gurgle on 2006-09-24
anyone got a working tutorial for compiz on ubuntu x64?

---

### Post by Jon &quot;Yogi&quot; on 2006-09-25
My session is broken again...

It almost seems to me that there is a problem involving CSM...:-k

Would look at it, but must finish this paper by the morning...](*,) I'll try to look into it later this week, if no one else beats me to it.

---

### Post by hannav85 on 2006-09-25
I have followed this how to word for word and im still getting thrown back to the login screen after about 10 seconds when trying to login into the xgl session.

I noticed that when i was using aptitude to download the programmes it said "some files were not downloaded sucessfully" for example this was one of the lines:

 [http://debian-amd64.alioth.debian.org](http://debian-amd64.alioth.debian.org) sid/contrib sources [ERROR]

any ideas?!?!

any help will be very much appreciated ](*,) 

Hanna

---

### Post by brent09 on 2006-09-25
COMPIZ WORKS!

I followed a different guide, but had to kinda... squeeze bits of this guide into it.

First, I followed: [http://www.ubuntuforums.org/showthread.php?t=148860&highlight=compiz.real%3A+composite+extension](http://www.ubuntuforums.org/showthread.php?t=148860&highlight=compiz.real%3A+composite+extension)

But, at the end of step one, where you install compiz with apt-get things weren't working (couldn't find cgwd)
So in addition to what I had already done in that thread, I came back to this thread and added the repos and keys mentioned.  Then I installed compiz-core compiz compiz-gnome and csm with aptitude.

```
sudo aptitude install compiz-core compiz compiz-gnome csm
```

Then I went back to the first thread and continued from Step 2.

Works for me. Except I have no window borders (unsure if that's a glitch, or it if should look this way)

---

### Post by hannav85 on 2006-09-25
Im downgrading to 32 bit :( I'm too much of a newbie to feel comfortable with 64 bit ubuntu! 

Just one question though...in order for xgl/compiz to work on a 64 bit processor do i need to have 64 bit ubuntu?

Cheers, Hanna

---

### Post by Relain on 2006-09-25
So i did exactly what you said and yeah it didn't really work either, i start an XGL / compiz session and get stuck at the brown screen. I suppose that means that gnome isn't really starting up properly. 

Anyone got any ideas? I've had it working on a 32bit processor before and i've tried a whole bunch of different ways to make it go on my 64bit machine. 

Hmm.

---

### Post by Jon &quot;Yogi&quot; on 2006-09-25
Hanna, No you don't have to have 64bit Ubuntu to run compiz, you will just use 32bit software instead. I would advise though that downgrading is not necessarily the way to go. Remember that compiz is still developing, and in time will get better and easier to install and use. Going to 32bit may not guarantee that compiz will work either. 

Either way, I hope you the best with Ubuntu!

Jon

---

### Post by hannav85 on 2006-09-26
Jon, I dont expect to get compiz to work at all ;) ive just given up with 64 bit in general, it has nothing to do with the compiz thing not working. there are so many things i couldnt get working! now im back on 32 bit things seem nice and easy again :) I will maybe come back in the future when other programmes are easier to set up on 64

cheers for your help :)

---

### Post by FedeXX on 2006-09-26
> **gurgle said:**
> i am getting the issue that the XGL session will not start.

i sign in to the session OK, but then after about 10 seconds i get kicked back to teh sign in screen. :(
Same problem here... I can't believe there isn't a fix for this...

---

### Post by kislo_metal on 2006-09-26
I had this problem too!!
it`s look like compiz-manager can`t init window decorator.

---

### Post by gurgle on 2006-09-27
there has to be a way to get this fixed. anyone? <img>

---

### Post by Jon &quot;Yogi&quot; on 2006-10-03
Ok. I removed compiz and all the related packages, then reinstalled them. I can get into the XGL session fine now, but when I run compiz-start, everything goes white. When I alt-tab, things get a little gray, and I can see a white wobbly selection in the middle of the screen. When I rotate the cube, I can see the cube spin, but everything is still white. Makes for some cool effects, but sure isn't productive. 

My guess is there is a compatability issue with the packages, as csm looks to be a step behind the others. Just a guess.

I'll let you know if I figure anything out. 

Jon

---

### Post by dimis on 2006-10-04
Just a thought: What happens if all of you people downgrade to the previous kernel (or an even earlier) version? Do you still have trouble logging into XGL?

---

### Post by kesman on 2006-10-19
> **brent09 said:**
> COMPIZ WORKS!

I followed a different guide, but had to kinda... squeeze bits of this guide into it.

First, I followed: [http://www.ubuntuforums.org/showthread.php?t=148860&highlight=compiz.real%3A+composite+extension](http://www.ubuntuforums.org/showthread.php?t=148860&highlight=compiz.real%3A+composite+extension)

But, at the end of step one, where you install compiz with apt-get things weren't working (couldn't find cgwd)
So in addition to what I had already done in that thread, I came back to this thread and added the repos and keys mentioned.  Then I installed compiz-core compiz compiz-gnome and csm with aptitude.

```
sudo aptitude install compiz-core compiz compiz-gnome csm
```

Then I went back to the first thread and continued from Step 2.

**[COLOR="Red"]Works for me. Except I have no window borders (unsure if that's a glitch, or it if should look this way)[/COLOR]**

Same problem here!
Thanks for this thread, I finally got compiz up and running on my laptop, amd64 & Ati Mobility Radeon x700. Yet I still would like some more, as in window borders :P
I also installed compiz-manager from these repos:

```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
```
and instead of using compiz-start in Xgl session, I used it, and it prints out:

```
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
compiz: No GLXFBConfig for depth 32
compiz: No GLXFBConfig for depth 32
compiz: No GLXFBConfig for depth 32
```

I tried to search for a clear solution, with no luck...

---

### Post by Stormbringer on 2006-10-19
> Iim still getting thrown back to the login screen after about 10 seconds when trying to login into the xgl session.

For me the problem turned out to be a missing library that isn't mentioned in the first post and somehow isn't a dependency. After investigating Xorg.0.log. I installed the required "libglitz-glx1" and the Xgl session started up.

However, I now have the problem that the Xgl-server crashes upon starting "compiz-start" or "compiz-manager" ... I see the screen changing and a second later it crashes away kicking me back to the login screen. Same happens if I try to start anything else that is related to OpenGL i.e. "glxgears" or some OpenGL screensaver.

Error message involved (only logged in .xsession-errors)

```

X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  4079
  Current serial number in output stream:  4079

```

Running Nvidia 96.26 AMD64 on a TwinView Setup, RenderAccel and AllowGLXWithComposite is enabled, and "Composite" is enabled in the "Extension" section as well.

No matter how I tweak the settings in xorg.conf the Xgl Server crashes upon the launch of compiz or some OpenGL application.

Any solution to this problem?

**EDIT** Crashing problem solved
The nvidia driver wasn't compiled correctly - direct rendering wasn't available. Reinstalled xserver-org-dev along with all of it's dependencies and now it works just fine.

---

### Post by beamo on 2006-10-23
Finally got it to work!

I've been trying to get this to work on AMD64 for a long time. Here is what I did:

I read brent09's post on page 4 (that was the real key) and visited the thread he mentions ([http://www.ubuntuforums.org/showthread.php?t=148860&highlight=compiz.real%3A+composite+extension](http://www.ubuntuforums.org/showthread.php?t=148860&highlight=compiz.real%3A+composite+extension))
I followed that thread from step two until the end and I followed it exactly. 

For step one I did this:

(note that my kernel is version 2.6.15-23-amd64-generic as I did all this after a fresh install. Not sure that the kernel version really matters so long as it's amd64-generic, but this is what finally worked for me. I did replace my sources list with the one from the unnoficial guide before proceeding. Beyond that I did nothing. Like I said, fresh install.)

From this thread's original post: 
> ...install the propietary driver version 8762 using Synaptic, just search for the packages named 'nvidia-glx'...

Note: 2.6.15-26-amd64-generic is what i get with the command uname -r. 

When the installation finished i typed the following
```

sudo nvidia-glx-config enable

```
After restarting my machine i added the option RenderAccel to the xorg configuration with sudo gedit /etc/X11/xorg.conf
```

Section "Device" Identifier "NVIDIA Corporation NV41.1 [GeForce 6800]" Driver "nvidia" Option "RenderAccel" "true" . . .

```
Then i added this repositories at the end with sudo gedit /etc/apt/sources.list
```

## These repositories provides the latest Xgl/Compiz stuff built for AMD64 deb http://ubuntu.systemadministrator.org dapper eyecandy deb-src http://ubuntu.systemadministrator.org dapper eyecandy

```
After that i typed
```

wget http://ubuntu.systemadministrator.org/2F306651.gpg -O- | sudo apt-key add - sudo apt-get update

```
 

Then I entered this command into the terminal"
```
sudo apt-get install compiz xserver-xgl csm libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd
```

That is the end of step one, now go to step two on the other thread.

I really hope this works for somebody because I had fits getting this thing to work.

---

### Post by total wormage on 2007-02-24
is it me or is [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) down or moved?

i'm getting this:

```
Resolving ubuntu.systemadministrator.org... failed: Name or service not known.
```


:p

---

### Post by JAPrufrock on 2007-02-24
I managed to get Compiz running on 64 bit dapper with a GeForce FX5200 video card.  It was a while ago so I can't remember all the details.  Nevertheless, here are some notes I took which may help. 
Sorry I can't list all the steps I took.  Some steps may be missing, but this is all I remember, or took notes on.  I used the how-tos already mentioned in this thread, which will probably fill in the missing steps.

First of all, it's important to add some repositories: Before starting, I added the following repositories to my sources.list.  If I remember correctly, the systmadministrator.org url didn't work, but it wasn't important anyway:

##################################################
## These repositories provides the latest Xgl/Compiz stuff built for AMD64
deb [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
deb-src [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main-amd64
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
###################################################


COMPIZ
XGL
Files needed for xgl:
	xserver-xgl (I installed with synaptic)

Problem:  Couldn't get XGL to install, because on the session login I was told that I was missing the file &#8220;/usr/share/X11/rgb.txt
But I found this:

"You'll find that /usr/lib/X11/rgb.txt exists - the Xgl package was just (mistakenly) built without the option to point it there. If you symlink /usr/share/X11/rgb.txt to /usr/lib/X11/rgb.txt, it then works, and emacs loads once more! Yay!"

So I entered the following command:  sudo ln /usr/lib/X11/rgb.txt /usr/share/X11

This got rid of that error message, but I got another:  &#8220;Gtk-WARNING**: cannot open display

So I went into /etc/gdm/gdm.conf and changed 2 lines to:
 			#0=Standard
			  1=Standard   (note: it use to be 0=Standard and #1=Standard; later I changed it back-see below.)
So hooray, XGL worked

[U]Now for Compiz
[/U]
Files Needed for Compiz 13 (I installed them with apt-get, after adding to my sources.list):
	compiz
	compiz-core
	csm
	libglitz1
	libglitz-glx1
	cgwd
	others??
The installation was lacking a file, which the how-tos did not mention:  libglitz-glx1
Note: libglitz1 _was_ intalled with compiz.

Important:  Go to the gdm.conf file.
Leave or change the /etc/gdm/gdm.conf file to:    #1=Standard
				                                          0=Standard
And add the following lines at the end of the /etc/gdm/gdm.conf file:
> [servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true	

So the Xgl server becomes the Standard server!!

Start Compiz with the the terminal command, compiz-start


change the smiley to "colon p"

---

