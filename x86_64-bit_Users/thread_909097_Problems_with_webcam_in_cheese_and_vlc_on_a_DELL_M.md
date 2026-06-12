---
title: "Problems with webcam in cheese and vlc on a DELL M1530"
date: 2008-09-03
forum: x86 64-bit Users
---

### Post by mngcld on 2008-09-03
Hi everybody!
I have a dell m1530 with UBUNTU 8.04 HARDY and I am having some problems with the webcam. It works fine with skype, but when I try to use it with other applications I have some problems.

CHEESE:
If I start it from terminal it works to shoot photos, but if I try to make a video it records the first one, but then the webcam goes off. Besides, if I try to play the video I get these errors
```
(realplay.bin:7672): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so: wrong ELF class: ELFCLASS64

ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```
the first line is repeated twice, the last line is repeated a lot of times. The video plays indeed, but the colors are really greenish and the audio is very weak.

VLC:
If I make a ls /dev/video* I can see only /dev/video0, but if I try to open it in vlc the webcam light blinks for a second but then goes out. I see no image at all. The error I get it this one:

```
[00000304] v4l demuxer error: cannot get channel infos (Invalid argument)

```

Thank you very much for your help in advance!

---

### Post by IntuitiveNipple on 2008-09-03
There are a lot of issues with Cheese being reported of late. The primary issue is that it doesn't support all the video formats that various cameras output. In your case it sounds more like some kind of gstreamer interaction though, since you can get video successfully after a clean start.

The real-player error:
```

(realplay.bin:7672): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so: wrong ELF class: ELFCLASS64

```
is caused by the fact you're using a 32-bit CPU architecture application on 64-bit and this library (libgio.so) isn't available in the system's 32-bit compatibility library directory. You could try using getlibs to find and install that library:
```

getlibs -l libgio.so

```

Give us some more information about the camera device so we can work from specifics. Please report the results of these commands:
```

lsusb

udevinfo --query=all --name=/dev/video0 --attribute-walk 

```

Also, from a clean start and not having tried to run any other camera applications, open a terminal and run vlc. When the GUI comes up do the usual steps to try and use the camera. vlc will write a lot of debugging messages to the terminal. Copy and paste those into a reply here so we can see where it has the problem.
```

vlc

```

---

### Post by mngcld on 2008-09-04
Hi IntuitiveNipple, thank you very much for your ready reply!

The webcam is an integrated one (fixed above the screen) with the resolution of 2 mega pixels. I tried to find some information on the dell website but that is all I found:
	
Integrated 2.0 MP camera

I hope the information below will be more useful.
This is the output of lsusb and I think that the camera is on the Omnivision line:

```
cataldo@cataldo-laptop:~$ lsusb
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 413c:3016 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
```

This is what I get with udevinfo:

```
cataldo@cataldo-laptop:~$ udevinfo --query=all --name=/dev/video0 --attribute-walk

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1a.7/usb3/3-1/3-1:1.0/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{dev}=="81:0"
    ATTR{name}=="Laptop Integrated Webcam"

  looking at parent device '/devices/pci0000:00/0000:00:1a.7/usb3/3-1/3-1:1.0/video4linux':
    KERNELS=="video4linux"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1a.7/usb3/3-1/3-1:1.0':
    KERNELS=="3-1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="uvcvideo"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="0e"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{modalias}=="usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00"
    ATTRS{interface}=="Laptop Integrated Webcam"
    ATTRS{iad_bFirstInterface}=="00"
    ATTRS{iad_bInterfaceCount}=="02"
    ATTRS{iad_bFunctionClass}=="0e"
    ATTRS{iad_bFunctionSubClass}=="03"
    ATTRS{iad_bFunctionProtocol}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:1a.7/usb3/3-1':
    KERNELS=="3-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:257"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="27"
    ATTRS{idVendor}=="05a9"
    ATTRS{idProduct}=="2640"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="ef"
    ATTRS{bDeviceSubClass}=="02"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="OmniVision Technologies, Inc. -2640-07.07.20.3"
    ATTRS{product}=="Laptop Integrated Webcam"

  looking at parent device '/devices/pci0000:00/0000:00:1a.7/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:256"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="46"
    ATTRS{idVendor}=="0000"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="4"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.24-19-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1a.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1a.7':
    KERNELS=="0000:00:1a.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x283a"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{subsystem_device}=="0x022e"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="22"
    ATTRS{local_cpus}=="00"
    ATTRS{modalias}=="pci:v00008086d0000283Asv00001028sd0000022Ebc0Csc03i20"
    ATTRS{numa_node}=="-1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

This is a file named "log" that I found in ~/.gnome2/cheese

```

Detected webcam: Laptop Integrated Webcam
device: /dev/video0
video/x-raw-yuv 352 x 288 num_framerates 1
30/1 
video/x-raw-yuv 320 x 240 num_framerates 1
30/1 
video/x-raw-yuv 176 x 144 num_framerates 1
30/1 
video/x-raw-yuv 160 x 120 num_framerates 1
30/1 
video/x-raw-yuv 640 x 480 num_framerates 1
10/1 
v4l2src name=video_source device=/dev/video0 ! video/x-raw-yuv,width=640,height=480,framerate=10/1 ! identity


```

If I start vlc from terminal and then choose Open Capture Device from the File menu that is what I obtain:
```

cataldo@cataldo-laptop:~$ vlc
VLC media player 0.8.6e Janus
[00000304] v4l demuxer error: cannot get channel infos (Invalid argument)

```

which is what I sent in the previous post, I do not get more. Maybe I did not understand what you meant me to do.. I have no idea what this demuxer is.

Finally, I think I managed to install the missing library the way you suggested and there is no more the reaplayer error:

```

cataldo@cataldo-laptop:~$ sudo getlibs -l libgio.so
libgio.so: libgnomeui-0
The following i386 packages will be installed:
libgnomeui-0
Continue [Y/n]? Y
Downloading ...
Installing libraries ...
cataldo@cataldo-laptop:~$ 

```

After the library update and after restarting the computer, I tried to run cheese from terminal and this time the error is a different one: if I try to record a video I can see myself on the screen, but after a while the window becomes grey (it is what happens when a window does not respond, with any application on my ubuntu, I do not know if it is the same on other ubuntus). After this I can see a .ogg file in the ../media directory but not in the cheese window. If I try to play it with any player it gives an error such as "stream contains no data". Besides cheese does not work any more even to take photos, unless I restart it. The video output is violet-blueish after the first video-shooting, also if I try to play an .avi file with a movie player (I used vlc).



```

cataldo@cataldo-laptop:~$ cheese

(gnome-video-thumbnailer:29373): GStreamer-CRITICAL **: gst_event_new_new_segment_full: assertion `start != -1' failed

(gnome-video-thumbnailer:29373): GStreamer-CRITICAL **: gst_event_new_new_segment_full: assertion `start != -1' failed
gnome-video-thumbnailer couldn't process file: 'file:///home/cataldo/.gnome2/cheese/media/0002.ogg'
Reason: Took too much time to process.

** (cheese:29318): WARNING **: could not load /home/cataldo/.gnome2/cheese/media/0002.ogg (video/x-theora+ogg)



```

Thank you in advance for your help, I hope that this information can be useful.

---

### Post by IntuitiveNipple on 2008-09-05
All that info is just what we need. I can see the camera is a UVC (USB Video Class) device and is using the uvcvideo driver.

It looks as if it might not be entirely UVC compliant, or that the driver is being confused by it in some way. That's something that can be investigated.

The thing to do is install [luvcview from Michel Xhaard's site](http://mxhaard.free.fr/download.html) and see if it can handle the camera without a problem. If it can then the problems are being caused on the application side (scroll almost to the end of the page for the link to the download).

Here's the instruction for downloading, extracting, building and running it:
```

cd ~
wget http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz
tar -xzf luvcview-20070512.tar.gz
cd luvcview-20070512
make

```
Now run it. Set the device path if it isn't video0:
```

./luvcview -f yuv /dev/video0 

```
With that you can try adjusting settings such as brightness, contrast, saturation, and gain in the GUI. It will report what it is doing in the console:
```

luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
max 127, min 0, step 1, default 63 ,current 64 
Control name:Brightness set to value:64
max 127, min 0, step 1, default 63 ,current 65 
Control name:Brightness set to value:65
max 127, min 0, step 1, default 63 ,current 66 
Control name:Brightness set to value:66
max 127, min 0, step 1, default 63 ,current 67 
Control name:Brightness set to value:67
Set Gain up error
ioctl querycontrol error 22
Control name:Contrast set to value:78
max 127, min 0, step 1, default 52 ,current 79 

```

---

### Post by Crafty Kisses on 2008-09-05
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)



To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by mngcld on 2008-09-05
Thank you again for your help!

I installed luvcview after installing the libraries in the README file that comes with the archive. Unfortunately it does not work very well: the video that I can see on the screen and that is recorded (so luvcview CAN record a video!) is not fluid and every 1-2 seconds there is a small infinitesimal stop. I think this is due to the fact that the framerate continues to go up and down (also below 10 fps, you can read the fps on the top of the window). The conditions under which I tried to use the camera are normal: the light was sufficient and with skype I have no such problems under these conditions. 
I read that shutting off autoexposure can improve this but I cannot use that command, it produces an error.
I tried also to understand which are the supported recording formats launching luvcview with the -L flag, and then tried commands such as these:

```
luvcview -f jpg -s 640x480 -i 30
```

to force format, resolution and framerate, but apparently the video is not yet fluid. I hoped that I could also tilt and pan the camera (I think that I was able to do that in windows when I first started the computer, so the camera should be able to do it) but it gives an error. If I want to know the available controls of the camera I see:

```

cataldo@cataldo-laptop:~$ luvcview -l
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Available controls of device 'Camera 1' (Type 1=Integer 2=Boolean 3=Menu 4=Button)
V4L2_CID_BASE         (predefined controls):
 index:9963776    name:Brightness                       type:1 min:0     max:200   step:1     def:90    now:119 
 index:9963777    name:Contrast                         type:1 min:5     max:50    step:1     def:30    now:37 
 index:9963778    name:Saturation                       type:1 min:0     max:100   step:1     def:64    now:63 
 index:9963779    name:Hue                              type:1 min:0     max:255   step:1     def:0     now:0 
 index:9963792    name:Gamma                            type:1 min:1     max:4     step:1     def:2     now:2 
V4L2_CID_PRIVATE_BASE (driver specific controls):
 index:134217728  name:Backlight Compensation           type:1 min:0     max:3     step:1     def:3     now:3 
 index:134217729  name:Power Line Frequency             type:3 min:0     max:2     step:1     def:2     now:1 
  Menu items:
  index:0 name:Disabled
  index:1 name:50 Hz
  index:2 name:60 Hz
 index:134217730  name:Sharpness                        type:1 min:0     max:31    step:1     def:1     now:1 
 Clean Up done Quit 
```

Thank you also for your help, Codename. I installed Ekiga that is not so stable, anyway. I can see myself on the screen, but I am not sure it will work during a call, since there were some problems while doing the video set up with the configuration druid. As soon as I find somebody to call I will let you know what happens.

Thank you again! I hope to get this video problem fixed..

---

### Post by Crafty Kisses on 2008-09-05
Glad you could see yourself that means the cam is obviously detected which is good. :)

---

### Post by IntuitiveNipple on 2008-09-05
> **mngcld said:**
> Unfortunately it does not work very well: the video that I can see on the screen and that is recorded (so luvcview CAN record a video!) is not fluid and every 1-2 seconds there is a small infinitesimal stop.
This looks like something you should report to Laurent Pinchart, the maintainer of uvcvideo, since these are the kinds of things he wants to solve.

Post a report with the lsub and luvcview information you've shown here to the [uvcvideo project on BerliOS](http://developer.berlios.de/bugs/?group_id=5681), and possibly subscribe to the developers mailing-list there and post an email referencing the bug report and this thread.

Let me know the bug report # and URL so I can subscribe to it.

---

### Post by freackout on 2009-07-13
> **mngcld said:**
> Hi everybody!
I have a dell m1530 with UBUNTU 8.04 HARDY and I am having some problems with the webcam. It works fine with skype, but when I try to use it with other applications I have some problems.

CHEESE:
If I start it from terminal it works to shoot photos, but if I try to make a video it records the first one, but then the webcam goes off. Besides, if I try to play the video I get these errors
```
(realplay.bin:7672): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so: wrong ELF class: ELFCLASS64

ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```
the first line is repeated twice, the last line is repeated a lot of times. The video plays indeed, but the colors are really greenish and the audio is very weak.

VLC:
If I make a ls /dev/video* I can see only /dev/video0, but if I try to open it in vlc the webcam light blinks for a second but then goes out. I see no image at all. The error I get it this one:

```
[00000304] v4l demuxer error: cannot get channel infos (Invalid argument)

```

Thank you very much for your help in advance!
try guvcview it wont hog the cpu, has more settings and can choose formats/ cameras/ res plus loads more. another link for codecs & demuxers
(demuxer is ffmpeg related i think) is [http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html](http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html)

---

### Post by jespdj on 2009-07-14
Note that you are responding to a 10-month old thread. I doubt that the OP is still waiting for an answer.

Cheese, Skype and other programs that use the webcam never gave me any problems on my Dell XPS M1530 - not with Ubuntu 8.04, 8.10 and 9.04 (all 64-bit).

---

