---
title: "Dual Monitor setup in xorg.conf"
date: 2009-04-28
forum: x86 64-bit Users
---

### Post by mreude on 2009-04-28
Ok, guys here it is. I assume that it doesn't matter what monitor/lcd screens I am using but I will give them anyway.

LG L194WT 17" Flatron Widescreen
LG 32" 720P HDTV

I just need to know what modifications I need to make to my xorg.conf file so that it recognizes both the monitor and tv when they are plugged in. I tried to use the nvidia x server settings, but every time I try to "Save to X Configuration File" I get the same message, "Failed to parse existing X config file '/etc/X11/xorg.conf'!" Even if I try use the "sudo nvidia-settings" in a terminal I get the same message.

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	BUSID	"05:00:0"
EndSection
```

Here is what I'm using:
Ubuntu 9.04 Jaunty
NVidia GeForce 7600 GT x 2 (Both monitor and tv are plugged into the same card)
NVIDIA Driver 180.44

---

### Post by mreude on 2009-04-28
Ok, a little more information about

```
sudo nvidia-settings
```

When I click "Save to X Configuration File" I get this message:
```
mreude@mikes-pc:/etc/X11$ sudo nvidia-settings 

PARSE ERROR:  Parse error on line 9 of section Module in file /etc/X11/xorg.conf.
"Disable" is not a valid keyword in this section.

Segmentation fault
```

Again, any constructive input is welcome.

---

### Post by doas777 on 2009-04-28
well, your headed the right direction with nvidia-settings, but the existing xorg is probably conflicting. 
try running:```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to "reset" your xorg. you will have to reenable the nvidia driver, and reboot.

then go back to nvidia settings, configure, and attempt to save your xconfig again. hopefully the parser error will be gone.

good luck

---

### Post by mreude on 2009-04-28
> **doas777 said:**
> well, your headed the right direction with nvidia-settings, but the existing xorg is probably conflicting. 
try running:```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to "reset" your xorg. you will have to reenable the nvidia driver, and reboot.

then go back to nvidia settings, configure, and attempt to save your xconfig again. hopefully the parser error will be gone.

good luck

Great! That helped out alot. But now wants to write the following xorg.conf file.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L194WT"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

[COLOR="Red"]Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
    BusID          "5:00:0"
EndSection[/COLOR]

[COLOR="YellowGreen"]Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:5:0:0"
EndSection[/COLOR]

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

My questions are as follows:
   Are the [COLOR="Red"]red[/COLOR] and [COLOR="YellowGreen"]green[/COLOR] sections duplicates?
   And is there anything in the new code that can or should be omitted?

---

### Post by mreude on 2009-04-28
Ok, nevermind about the duplicate code. if I uncheck the "Merge with existing file." box it removes that code. Time for reboot I'm crossing my fingers.

Thanks Again.

---

### Post by mreude on 2009-04-28
Alright, I now have two screens set up. One is an LCD Monitor and the other is an LCD HDTV. Now, here is the problem. The TV is set up as the main display and the Monitor as the secondary. I don't see any way of changing this in the NVIDIA-settings program. Is there something I'm missing?

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG TV"
    HorizSync       31.0 - 60.0
    VertRefresh     56.0 - 63.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG L194WT"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:5:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:5:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

So far I have tried to switch the port the two are plugged in to, but to no avail.

Also, I noticed that in the code it states '"TwinView" "0"' and I was going for "Separate X Screen" Will this make any difference or is this what it is supposed to be set to?

---

### Post by mreude on 2009-04-29
Well, I'm not exactly sure what I did to change it. But I now have the monitor as the primary and the tv as the secondary.

I replaced:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  **"Screen0"** 0 0
    Screen      1  **"Screen1"** RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection
```

with

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  **"Screen1"** 0 0
    Screen      1  **"Screen0"** RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection
```

Then I rebooted and had the monitor as the primary. After that I loaded "sudo nvidia-settings" and overwrote the modified xorg.conf file and rebooted. This kept the monitor as the primary so far.

I'm not sure if this is the best way to do this, but it worked for me.

Now I'm having an issue that many are having with loading programs on the secondary monitor. Firefox and a select few programs will load on the secondary monitor, but everything else loads to the primary.

Also, is there no way to move applications from one screen to another? Any input would be appreciated.

---

### Post by doas777 on 2009-04-29
I just found out last night, while upgrading a mediabox to jaunty, that for the first time, Nvidia Twinview worked perfectly for me. Twinview treats the desktop as one double wide pane,  but will maximize windows to only one physical screen (you need to reboot before the maximize works right). you can move windows back and forth between screens.

there are a pair of caveats however. your monitors must be set to the same resolution, or else the smaller monitor (resolution) will pan, and fullscreen will draw partially offscreen.
the only other issue, is that it mangled the scalling of my desktop, and doubled it on the width (ok), and on the height (not ok),and since one monitor is a 19" and the other a 32" SD TV, the seperation between the two is jarring. I just set it to a solid color and changed the theme to look nice.

if twinview isn;t right for you, i've been using seperate X screens on my mediabox for a few years now (it was my second major linux troubleshooting experience), and havent had any problems (since watching anime is all i use it for), just launching a viewer on the TV desktop and dragging files into it from the monitor (you can't drag windows, but you can files). it may not be as nice for serious work though.

have fun.
franklin

oh yeah, you can find twinview in nvidia-settings under "X Server display configuration", and press the button "Configuration", and select TwinView. also on that page, you should be able to set a screen as primary. you may have to click the advanced button to see those controls.

---

### Post by captaindobbe on 2009-06-16
Hi, not sure if you solved your problem or not... I had the same problem today, solved this way... It might not be very "clean" though... 
Like you, I was able to setup my display as I wanted but each time i wanted to save the config, I had the same error message... 
i created a drag and drop sudo in order to be able to edit the xorg.conf file:
**"Drag & Drop sudo**

 This is a trick from the [this thread]("http://www.ubuntuforums.org/showthread.php?t=24008") on the [Ubuntu Forums]("https://help.ubuntu.com/community/UbuntuForums"). 
Create a [launcher]("https://help.ubuntu.com/community/HowToAddaLauncher") with the following command: 
gksudo "gnome-open %u"(When you drag and drop any file on this launcher (it's useful to put it on the desktop or on a panel), it will be opened as root with its own associated application. This is helpful especially when you're editing config files owned by root, since they will be opened as read only by default with gedit, etc. ")

then when I save the xorg.inf file, i clicked on "show preview" ... just copied the text in the preview, opened my worg.inf file with the sudo launcher ( to open it as root ), pasted the text, saved the file...

tada... 

worked...

> **mreude said:**
> Ok, guys here it is. I assume that it doesn't matter what monitor/lcd screens I am using but I will give them anyway.

LG L194WT 17" Flatron Widescreen
LG 32" 720P HDTV

I just need to know what modifications I need to make to my xorg.conf file so that it recognizes both the monitor and tv when they are plugged in. I tried to use the nvidia x server settings, but every time I try to "Save to X Configuration File" I get the same message, "Failed to parse existing X config file '/etc/X11/xorg.conf'!" Even if I try use the "sudo nvidia-settings" in a terminal I get the same message.

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    BUSID    "05:00:0"
EndSection
```Here is what I'm using:
Ubuntu 9.04 Jaunty
NVidia GeForce 7600 GT x 2 (Both monitor and tv are plugged into the same card)
NVIDIA Driver 180.44

---

