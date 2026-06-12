---
title: "My experience with Ubuntu 8.10 x64 - Encouraging!"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by zelthian on 2008-12-02
I have been a Linux fan for a while, but until the network manager changes in 8.10, and the popularity of the netbook, I have been dragging my feet to convert. I did, recently, after successfully running World of Warcraft under Wine. I was thrilled, and I decided to switch full time.

Then I realized Linux was only using 2.7gb of my 8gb of RAM.

No problem, just use 64-bit, right? Sure. Issues abound, but I had some time, and I have figured out a way to get all the things I need working in Ubuntu 8.10 x64 that I need, including:

[LIST]
[*]Basic Java Support
[*]Basic Flash Support (for youtube)
[*]XM Radio Online
[*]Skype
[*]World of Warcraft under Wine
[/LIST]

Getting the last two to work at the same time was the biggest challenge. To that end, I wanted to share with everyone what I did in case it may help someone in the future.

**[COLOR="Red"]DISCLAIMER:[/COLOR]** No, I will not help you with your particular setup. I am not an expert. Everything I did here I found out how to do by searching the Internet. Google and the Ubuntu Forums are wonderful things.

My setup:

EVGA 780i motherboard
2.4ghz quad-core proc
8 gig ram
nVidia 9800 GTX vid card
(sound and NIC are onboard the mb)


**STEP 1** – Install Ubuntu 8.10 x64

Nothing fancy here. Do a normal install to your liking. I put my /home directory on a separate drive because, well, I had one.


**STEP 2** – Install updates

Use the Update Manager to install all available updates. Do not skip this step. Do it now. Don't forget to restart.


**Step 3** – Install latest nVidia video driver

The driver from the Hardware Drivers tool is never the latest. For the best Warcraft on Wine experience, go to nvidia.com and get and install the latest 64bit Linux driver. Follow the instructions on the site. [COLOR="Red"]When the install asks, “Install NVIDIA's 32-bit compatibility OpenGL libraries?” choose “Yes”![/COLOR]

**NOTE:** To drop out of X, type:

```
sudo /etc/init.d/gdm stop
```

Do an ALT-F1 to get to a login prompt. Login and do the install. When done, reboot.


**STEP 4** – Basic media, including Flash and Java

I do this the easy way, through the Medibuntu repositories. I discovered this through ubuntumini.com when I was researching for my Dell Mini 9. I encourage you to visit the site, but to get all the basic codecs and whatnot for x64, here are the commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install libdvdcss2 libdvdread3 w64codecs ubuntu-restricted-extras
```

This will get you Java and Flash. If you had Firefox open during the install, close and re-open it before testing.


**STEP 5** – XM Radio Online

This gets a bit more complicated, but just a bit. Credit for the process goes to this link:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Here is the boiled-down procedure:

```
sudo apt-get install mplayer mozilla-mplayer
gksudo gedit /etc/mplayerplug-in.conf
```

Delete the current contents of the file and paste the following into the file and save:

```
download=1
cachesize=1024
cache-percent=25
keep-download=0
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=1
black-background=1
rtsp-use-http=0
rtsp-use-tcp=0
```

Restart the browser if necessary, and your XM Radio Online player should work.


**STEP 6** – Skype

This one is super easy to install, as you have the medibuntu repositories already set up. Just type:

```
sudo apt-get install skype
```

Login and change your outbound and ring to “pulse”. Your sound-in settings will differ from mine, but I ended up using "HDA NVidia (hw:NVidia,0)".


**Step 7** – Wine and Warcraft

First we set up Wine. I took the information from this site, which I suggest you visit:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Here are the steps I followed:

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

sudo apt-get update
sudo apt-get install wine
sudo apt-get alsa-oss
```

Wine is a 32-bit application. On my system, running warcraft with ALSA results in crappy sound on both the x32 and x64 versions of Ubuntu. So, I configure Wine to use OSS, but then I can't run Skype at the same time. By using aoss, I can route Wine w/OSS through ALSA, which solves the problem and still gives me good sound. However, when you install aoss, you get the 64-bit version, which doesn't work with Wine.

Enter getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Go there, click the link and install getlibs. Then, run this:

```
getlibs -l /usr/bin/aoss
```

getlibs will prompt you to install the i386 version of alsa-oss. Type Y to install it.

Now for the fun parts:

```
winecfg
```

Set Audio to “OSS” and de-select “ALSA”. Check the box for Driver Emulation at the bottom. Click “Apply” then “OK”.

I then copied my World of Warcraft directory into ~/.wine/drive_c/Program Files. Check the link at the beginning of this section for more option to get Warcraft on your box.

Edit the config.wtf file (in the warcraft wtf folder) and add this to the bottom of the file:
```

SET gxApi "opengl"
```

Also, follow thi guide's recommendation to add an entry to the registry:

> Open a terminal window, type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

   1. Find this key HKEY_CURRENT_USER\Software\Wine\
   2. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
   3. Right-click on the wine folder and select [NEW] then [KEY]
   4. Replace the text New Key #1 with OpenGL
   5. Right-click in the right hand pane and select [NEW] then [String Value]
   6. Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
   7. Then double click anywhere on the line, a dialog box will open.
8.In the value field type GL_ARB_vertex_buffer_object

Now all you should have to do is run warcraft with wine with aoss:

```
aoss wine "C:\Program Files\World of Warcraft\WoW.exe"
```

Don't run the launcher, as I don't think the launcher runs WoW.exe with aoss. Only run the launcher when you need to patch, then after the patch run WoW.exe with aoss.

**FINAL THOUGHTS**

I think x64 isn't as bad as some people make it out to be. Granted, I had to do a lot of searching, but all in all it's not terribly worse than x32. Take the plunge!

---

### Post by stchman on 2008-12-03
I use 64 bit Hardy exclusively and I can do everything I want.

---

### Post by loomsen on 2008-12-03
> **stchman said:**
> I use 64 bit Hardy exclusively and I can do everything I want.

#2, tho on Intrepid

> This will get you Java and Flash. 

That's where I stopped reading.

---

