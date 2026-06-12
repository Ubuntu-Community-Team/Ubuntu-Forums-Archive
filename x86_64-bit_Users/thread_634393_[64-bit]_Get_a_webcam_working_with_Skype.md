---
title: "[64-bit] Get a webcam working with Skype"
date: 2007-12-07
forum: x86 64-bit Users
---

### Post by Cappy on 2007-12-07
This HowTo is for 64-bit users who need to get a webcam working with a 32-bit application.

Based on [http://forum.skype.com/index.php?s=&showtopic=101297&view=findpost&p=463468](http://forum.skype.com/index.php?s=&showtopic=101297&view=findpost&p=463468)

[SIZE="4"]**Find what driver your webcam uses:**[/SIZE]
First, check to see what webcam driver you are using. You can do this by plugging in your webcam and going to the System Log (System-->Administration-->System Log). Look in syslog and now plug-in your webcam. You should see some bold lines appear that include either "gspca", "uvcvideo", or "pwc". This is your webcam driver. Alternatively, you can find the same information by plugging your webcam in and using ```
dmesg
```

[SIZE="4"]**Before you begin:**[/SIZE]
Make sure you have the build-essential package as it is required
```
sudo apt-get install build-essential
```

[SIZE="4"]**If you use the GSPCA driver:**[/SIZE]
Driver homepage: [http://mxhaard.free.fr](http://mxhaard.free.fr)

Run
```

myrelease=`uname -r`
olddriver=`locate -r "/$myrelease/.*gspca\.ko$"`
sudo mv $olddriver "/home/$USER/gspca.old"

```

Now, if ```
uname -r
```
says you have a kernel of 2.6.11 or higher download [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)
else download [http://mxhaard.free.fr/spca50x/Download/spca5xx-v4l1goodbye.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-v4l1goodbye.tar.gz)

Extract the file, change to the directory in the console (remember if it is on the Desktop change to the Desktop first) and run
```

sudo modprobe -r gspca; sudo make clean; sudo make; sudo make install

```

If all went well then unplug your webcam and run
```

sudo modprobe gspca

```
and replug the webcam in. It should be done! If your webcam is still not working you should try rebooting.

[SIZE="4"]**If you use the UVCVIDEO driver:**[/SIZE]
Driver homepage: [http://linux-uvc.berlios.de](http://linux-uvc.berlios.de)

Install subversion:
```
sudo apt-get install subversion build-essential
```

Run
```

myrelease=`uname -r`
olddriver=`locate -r "/$myrelease/.*usbvideo\.ko$"`
sudo mv $olddriver "/home/$USER/usbvideo.old"

```

Now, let's download the source:
```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
```

If that completed successfully we can now
```

cd trunk
modprobe -r uvcvideo; sudo make; sudo make install

```

If all went well then unplug your webcam and run
```

sudo modprobe uvcvideo

```
and replug the webcam in. It should be done! If your webcam is still not working you should try rebooting.

---

### Post by mdoube on 2007-12-09
```
svn checkout http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/
```

is the command required to access the svn repository

---

### Post by mdoube on 2007-12-09
```
sudo modprobe -r usbvideo; sudo modprobe usbvideo
```
should read
```
sudo modprobe -r uvcvideo; sudo modprobe uvcvideo
```
Should it not?

---

### Post by Cappy on 2007-12-09
> **mdoube said:**
> ```
sudo modprobe -r usbvideo; sudo modprobe usbvideo
```
should read
```
sudo modprobe -r uvcvideo; sudo modprobe uvcvideo
```
Should it not?

I haven't compiled the uvcvideo myself.  I think you suggestion is correct and the command should be ```
modprobe -r uvcvideo snd_usb_audio
```. This makes me wonder though: does uvcvideo.ko need to be removed also?

> **mdoube said:**
> ```
svn checkout http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/
```

is the command required to access the svn repository

Both links say that they are revision 149.

---

### Post by defenestratos on 2007-12-13
In skype my quickcam for skype was not recognized before I did the stuff above. Now it is recognized but the test yields only black. I am a noob when it comes to drivers and things so any help would be great!
The driver is SPCAxxx

---

### Post by Cappy on 2007-12-13
This happened to me also. I'm not sure what fixed it.

The fix was probably
```
sudo chmod 777 /dev/video0
```
(or whatever your /dev/video device number is!)
and then rebooting.

Another thing I tried wasI moving the
/lib/modules/YourKernelNumber/kernel/drivers/usb/media/gspca.ko
to the original directory that we deleted the original ubuntu module from.
That directory can be found with ```
locate gspcav1
``` if you forgot the location.

However, I deleted that file in an attempt to figure out what fixed the problem and it didn't break the webcam input so I don't think that was the problem.

---

### Post by defenestratos on 2007-12-13
> **Cappy said:**
> This happened to me also. I'm not sure what fixed it.

The fix was probably
```
sudo chmod 777 /dev/video0
```
(or whatever your /dev/video device number is!)
and then rebooting.

Another thing I tried wasI moving the
/lib/modules/YourKernelNumber/kernel/drivers/usb/media/gspca.ko
to the original directory that we deleted the original ubuntu module from.
That directory can be found with ```
locate gspcav1
``` if you forgot the location.

However, I deleted that file in an attempt to figure out what fixed the problem and it didn't break the webcam input so I don't think that was the problem.


Thanks but still no go. I moved the file and sudo chmoded the video0 file but it is still black.
I just checked and Camorama works now, albeit with poor pic quality and when I toggle image size it crashes.

---

### Post by debolitopo on 2007-12-13
Hi everybody,

I did install skype 2.0 and  made it work with my webcam under Ubuntu 7.10

the only problem is that every time I restart I need first to type (as posted by mdoube) :

Code:
sudo modprobe -r uvcvideo; sudo modprobe uvcvideo

otherwise skype does not recognize my webcam.

Any possibility to make this automatic?
Thanks

---

### Post by Cappy on 2007-12-13
According to the wiki [http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC)
you can create a file /etc/modprobe.d/uvcvideo with
```

install uvcvideo /sbin/modprobe snd_usb_audio; /sbin/modprobe --ignore-install uvcvideo
```

---

### Post by Simpele on 2007-12-16
I don't seem to be using a driver. When I reconnect my webcam (Logitech Quickcam Express), I get this in my log:

[ 3162.320413] usb 4-2: USB disconnect, address 3
[ 3164.488286] usb 4-2: new full speed USB device using uhci_hcd and address 4
[ 3164.655250] usb 4-2: configuration #1 chosen from 1 choice
[ 3164.658183] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[ 3164.658190] quickcam: Kernel:2.6.22-14-generic bus:4 class:FF subclass:FF vendor:046D product:0870
[ 3164.667107] quickcam: Sensor HDCS-1020 detected
[ 3164.669126] quickcam: Registered device: /dev/video0

What should I do to make it work with Skype? It is recognized by Kopete.

---

### Post by Cappy on 2007-12-16
> **Simpele said:**
> I don't seem to be using a driver. When I reconnect my webcam (Logitech Quickcam Express), I get this in my log:

[ 3162.320413] usb 4-2: USB disconnect, address 3
[ 3164.488286] usb 4-2: new full speed USB device using uhci_hcd and address 4
[ 3164.655250] usb 4-2: configuration #1 chosen from 1 choice
[ 3164.658183] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[ 3164.658190] quickcam: Kernel:2.6.22-14-generic bus:4 class:FF subclass:FF vendor:046D product:0870
[ 3164.667107] quickcam: Sensor HDCS-1020 detected
[ 3164.669126] quickcam: Registered device: /dev/video0

What should I do to make it work with Skype? It is recognized by Kopete.

That's the quickcam driver: [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)
There are installation instructions on the page.

You should delete/move your precompiled driver first (like the other drivers) before you do the make all.
```
locate -r quickcam.ko$
```

---

### Post by kr0n1x on 2007-12-27
please update gspca url :D is old now...

here's the new one: [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)

---

### Post by WenSes on 2008-01-02
Hi everybody!:

I got a problem similar to Simpele's one, when I check my syslog, it says something like this:

Jan  2 20:07:37 WenSes kernel: [ 2320.144245] usb 4-2: new full speed USB device using uhci_hcd and address 3
Jan  2 20:07:37 WenSes NetworkManager: <debug> [1199315257.557236] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8f6_noserial'). 
Jan  2 20:07:37 WenSes kernel: [ 2320.344084] usb 4-2: configuration #1 chosen from 1 choice
Jan  2 20:07:37 WenSes NetworkManager: <debug> [1199315257.599388] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8f6_noserial_if0'). 
Jan  2 20:07:37 WenSes NetworkManager: <debug> [1199315257.664923] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8f6_noserial_if2'). 
Jan  2 20:07:37 WenSes NetworkManager: <debug> [1199315257.700276] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8f6_noserial_if1'). 
Jan  2 20:07:37 WenSes NetworkManager: <debug> [1199315257.716803] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8f6_noserial_if1_alsa_capture_0'). 
Jan  2 20:07:37 WenSes NetworkManager: <debug> [1199315257.730794] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8f6_noserial_if1_oss_pcm_0'). 
Jan  2 20:07:37 WenSes NetworkManager: <debug> [1199315257.744815] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8f6_noserial_if1_oss_pcm_0_0'). 
Jan  2 20:07:37 WenSes NetworkManager: <debug> [1199315257.761937] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8f6_noserial_if1_alsa_control__1'). 
Jan  2 20:07:37 WenSes NetworkManager: <debug> [1199315257.776256] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8f6_noserial_if1_oss_mixer__1'). 
Jan  2 20:07:37 WenSes NetworkManager: <debug> [1199315257.807732] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8f6_noserial_usbraw'). 

My cam it's not detected at all, I'm getting desperate. It's a Logitech QuickCam Messenger.., what can I do? 

I got into a page that claims to have the drivers, but Im really a noob and I cant follow the instructions without getting into problems... 

Somebody can help me please!!

---

### Post by ELMIT on 2008-01-12
same here

---

### Post by sanandrikos on 2008-01-22
same for me..

---

### Post by hantabaru on 2008-02-01
A couple of things.

1. Probably easily fixed but the webcam image is upside down. Am I missing something?

2. The fix for getting the module to load automatically is for suse and didn't work. Is there a file of modules to load at start up I can just add the uvcvideo module to.

Cheers

---

### Post by shane2peru on 2008-02-12
> **Cappy said:**
> 

[SIZE="4"]**If you use the GSPCA driver:**[/SIZE]
Driver homepage: [http://mxhaard.free.fr](http://mxhaard.free.fr)


Now, if ```
uname -r
```
says you have a kernel of 2.6.11 or higher download [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)
else download [http://mxhaard.free.fr/spca50x/Download/spca5xx-v4l1goodbye.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-v4l1goodbye.tar.gz)



You can get this file here:  [http://www.slackware.com/~alien/slackbuilds/gspcav1/build/](http://www.slackware.com/~alien/slackbuilds/gspcav1/build/)  since it is no longer on the above mentioned site.  I did this and believe it will work for me.  At least it gives me the option in Skype now!  Before it was some generic setting that didn't work.  Thanks for this simple how to!  When I reboot, I'm sure it will work like a charm, if not, I'm another step closer.

Shane

---

### Post by Cappy on 2008-02-12
All of the links still work and are up to date.

---

### Post by shane2peru on 2008-02-13
> **Cappy said:**
> All of the links still work and are up to date.

Really??  They didn't work for me for some reason.  How odd, well, I guess this can just be one more source then. :)

Shane

PS:  OH, by the way it works!!!  Thanks Cappy for this wonderful trick!

---

### Post by alienhunt on 2008-02-13
I am using gspcav on Ubuntu 7.10, kernel 2.6.22.14-generic, x86_64, Skype Beta 2.0.

First time I installed the drivers it was immediately recognized in Skype (even though there is no option to start viewing the webcam in Skype.. but that's besides the point). After 5 minutes it stopped working. These are the only logs I have than I can show you guys.. maybe someone will know..

From Messages Tab:
```
Feb 13 15:49:54 home kernel: [18661.227429] Linux video capture interface: v2.00
Feb 13 15:49:54 home kernel: [18661.241547] usbcore: registered new interface driver gspca
Feb 13 15:49:54 home kernel: [18661.242901] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: gspca driver 01.00.20 registered
Feb 13 15:50:01 home kernel: [18668.445853] usb 1-1: new full speed USB device using uhci_hcd and address 4
Feb 13 15:50:01 home kernel: [18668.589449] usb 1-1: configuration #1 chosen from 1 choice
Feb 13 15:50:01 home kernel: [18668.594144] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
Feb 13 15:50:01 home kernel: [18668.594182] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_probe:4275] Camera type JPEG 
Feb 13 15:50:02 home kernel: [18669.641654] /home/alienhunt/Desktop/gspcav1-20071224/Vimicro/zc3xx.h: [zc3xx_config:669] Find Sensor HV7131R(c)
Feb 13 15:50:02 home kernel: [18669.655738] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_getcapability:1249] maxw 640 maxh 480 minw 160 minh 120
Feb 13 15:50:22 home kernel: [18689.044826] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
Feb 13 15:50:22 home kernel: [18689.045651] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
Feb 13 15:50:37 home kernel: [18704.839250] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
Feb 13 15:50:37 home kernel: [18704.840388] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
Feb 13 15:50:40 home kernel: [18707.908542] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
Feb 13 15:50:40 home kernel: [18707.908598] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
Feb 13 15:51:13 home kernel: [18740.102400] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
Feb 13 15:51:13 home kernel: [18740.102456] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
Feb 13 15:51:16 home kernel: [18743.568041] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
Feb 13 15:51:16 home kernel: [18743.568098] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
Feb 13 15:52:27 home kernel: [18814.623603] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca50x_isoc_irq:1146] Non-zero status (-18) in isoc completion handler.
Feb 13 15:59:33 home kernel: [19236.409463] usb 1-1: USB disconnect, address 4
```

From Syslog
```
Feb 13 15:50:22 home kernel: [18689.044826] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
Feb 13 15:50:22 home kernel: [18689.045651] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
Feb 13 15:50:37 home kernel: [18704.839250] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
Feb 13 15:50:37 home kernel: [18704.840388] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
Feb 13 15:50:40 home kernel: [18707.908542] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
Feb 13 15:50:40 home kernel: [18707.908598] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
Feb 13 15:51:13 home kernel: [18740.102400] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
Feb 13 15:51:13 home kernel: [18740.102456] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
Feb 13 15:51:16 home kernel: [18743.568041] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
Feb 13 15:51:16 home kernel: [18743.568098] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
Feb 13 15:52:27 home kernel: [18814.623603] /home/alienhunt/Desktop/gspcav1-20071224/gspca_core.c: [spca50x_isoc_irq:1146] Non-zero status (-18) in isoc completion handler.
Feb 13 15:59:33 home kernel: [19236.409463] usb 1-1: USB disconnect, address 4
```

---

### Post by linq on 2008-03-18
This tutorial worked flawlessly on my Gutsy 64 bit. Thank You very much.

---

### Post by adi_8079 on 2008-03-21
Works perfect with my Logitech Communicate STX.
Thanks!

---

### Post by comedian999 on 2008-03-29
I'm having what, I'm sure, is a newb problem, but I'll be damned if I can solve it: when I try to run the make, I'm getting the following error:

```
rob@overmind:~/Extractions/Extractions 3/gspcav1-20071224$ sudo modprobe -r gspca; sudo make clean; sudo make; sudo make install
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        *.symvers *.err
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/rob/Extractions/Extractions 3/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `3/gspcav1-20071224'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1
rob@overmind:~/Extractions/Extractions 3/gspcav1-20071224$ 
```

To save my soul, I can't figure out what gspca.ko file is missing, or what permissions issue I might be bumping into since I'm running sudo. Could someone who knows stuff point me in the right direction?

Thanks!

---

### Post by comedian999 on 2008-03-29
Aaaand, I solved my own problem. One of the folders in the path from which I was trying to run the compile from had a space in it, and it was screwing up the make script. I removed the space, reran the original tutorial, and it worked like a charm, as written.

Thanks for the great tutorial!

---

### Post by celles on 2008-04-08
Hello!

I've successfully installed Skype, and the sound seems to work but my video does not.  Skype can SEE the webcam and even correctly identifies it (QuickCam Pro 4000), but the video is black.  I've identified the driver as pwc, but there seems to be zero advice on either this or the Skype forum for dealing with this driver.

This is what I see in the sys log after I try to preview the cam in Skype:

Apr  8 19:19:21 sean-desktop kernel: [  511.534457] compat_ioctl32: v4l2 ioctl VIDIOC_S_PARM, dir=rw (0xc0cc5616)
Apr  8 19:19:21 sean-desktop kernel: [  511.534469] ioctl32(skype:6697): Unknown cmd fd(26) cmd(c0cc5616){t:'V';sz:204} arg(f618ee10) on /dev/video0

I'm a complete Linux noob, so be gentle!

---

### Post by tyk on 2008-04-18
worked perfectly :))))
thanks.

---

### Post by jacuz on 2008-04-23
Helped nicely, thank you!

---

### Post by pommattski on 2008-04-26
Hi, 
I have a webcam that worked 'out of the box' with Feisty (32-bit) for the last year - regularly using it with Skype.
I thought I should at least give 64bit Hardy a go but it was frustrating to find that it didin't 'just-work'.

Then I found your post...
I can confirm that the "GSPCA driver:" of your section worked on my new Hardy 64bit install - no problems.
Cappy: THANKS:)
Matt.

---

### Post by chrisblue on 2008-04-27
> **celles said:**
> Hello!

I've successfully installed Skype, and the sound seems to work but my video does not.  Skype can SEE the webcam and even correctly identifies it (QuickCam Pro 4000), but the video is black.  I've identified the driver as pwc, but there seems to be zero advice on either this or the Skype forum for dealing with this driver.

This is what I see in the sys log after I try to preview the cam in Skype:

Apr  8 19:19:21 sean-desktop kernel: [  511.534457] compat_ioctl32: v4l2 ioctl VIDIOC_S_PARM, dir=rw (0xc0cc5616)
Apr  8 19:19:21 sean-desktop kernel: [  511.534469] ioctl32(skype:6697): Unknown cmd fd(26) cmd(c0cc5616){t:'V';sz:204} arg(f618ee10) on /dev/video0

I'm a complete Linux noob, so be gentle!

Same webcam, same problem. My syslog for the same event is

Apr 27 21:11:23 ubuntu-dogbox kernel: [18017.334925] compat_ioctl32: v4l2 ioctl VIDIOC_S_PARM, dir=rw (0xc0cc5616)
Apr 27 21:11:23 ubuntu-dogbox kernel: [18017.335191] ioctl32(skype:10117): Unknown cmd fd(13) cmd(c0cc5616){t:'V';sz:204} arg(f5657e10) on /dev/video0

any noob help appreciated.

---

### Post by squaregoldfish on 2008-06-10
Works flawlessly in Gutsy with Quickcam Messenger.

Thanks,
Steve.

---

### Post by black drongo on 2008-07-09
hi
i cant follow this guide 
on plugging the usb webcam, iget this in syslog
> kernel: [  596.647986] usb 2-3: new full speed USB device using ohci_hcd and address 5
kernel: [  596.753901] usb 2-3: configuration #1 chosen from 1 choice
NetworkManager: <debug> [1215646231.456782] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_17a1_118_noserial').  NetworkManager: <debug> [1215646231.572141] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_17a1_118_noserial_if0'). 

lsusb returns

> Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 17a1:0118  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 0000:0000 

what may be the problem?
pls advice.

---

### Post by BanjoPants on 2009-02-07
Forgive me for my ignorance...

I identified the driver as gspca

When I follow the instructions I keep running into this error

maryanna@maryanna-desktop:~$ myrelease=`uname -r`
maryanna@maryanna-desktop:~$ olddriver=`locate -r "/$myrelease/.*gspca\.ko$"`
maryanna@maryanna-desktop:~$ sudo mv $olddriver "/home/$USER/gspca.old"
mv: missing destination file operand after `/home/maryanna/gspca.old'
Try `mv --help' for more information.


Thanks for your help...

---

### Post by gombadi on 2009-02-07
> 
maryanna@maryanna-desktop:~$ myrelease=`uname -r`
maryanna@maryanna-desktop:~$ olddriver=`locate -r "/$myrelease/.*gspca\.ko$"`
maryanna@maryanna-desktop:~$ sudo mv $olddriver "/home/$USER/gspca.old"
mv: missing destination file operand after `/home/maryanna/gspca.old'
Try `mv --help' for more information.


The mv command is complaining that it did not get enough information. My guess is the $olddriver variable is empty so the mv command will see -

```

mv  /home/maryanna/gspca.old

```

Type an echo $myrelease and echo $olddriver after each command to see what the variables contain.

---

### Post by msohn88 on 2009-03-05
GSPCA driver link does not have a drvier anymore. :(

NVM: page 2 has it!

min@min-laptop:~$ myrelease=`uname -r`
min@min-laptop:~$ olddriver=`locate -r "/$myrelease/.*gspca\.ko$"`
min@min-laptop:~$ sudo mv $olddriver "/home/$USER/gspca.old"
mv: missing destination file operand after `/home/min/gspca.old'
Try `mv --help' for more information.


What did I do wrong?

I just downloaded the driver for GSPCA on my desktop...

---

### Post by BanjoPants on 2009-04-26
I finally got it to work!  Thank you for all your help, but this thread got me to the solution.

[http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html](http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html)

---

