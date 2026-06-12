---
title: "Xorg Video Problem - LCD Laptop with HDMI External Monitor"
date: 2009-04-14
forum: x86 64-bit Users
---

### Post by djringjr on 2009-04-14
Hello everyone!

I've searched and tried all the usual methods but when I attach my HDMI LCD external monitor to my keyboard, the resolution changes to a very low resolution.  I had stupidly tried to set the monitor to the only (at that time) wide screen resolution, and since then, I've had problems.

I finally did manage with the new updates to get wide screen on my laptop, and everything is well if I disconnect the HDMI cable to the external monitor.

Here is what xrandr says:

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI-1 disconnected (normal left inverted right x axis y axis)

Somewhere - not Xorg.conf - there must be stored the bad resolution with the HDMI because xrandr knows that the HDMI monitor is disconnected.

I'll try to post what it says when I connect the HDMI monitor, but I think there might be problems - like when I use System/Preferences/Display - I cannot use the "OK" button because it's off the screen!

Here is this post - more in a moment.

Thanks

David

---

### Post by djringjr on 2009-04-14
OK, I logged out - and by the way I'm running Ubunty 64 Jaunty on this laptop and the BIG resolution came back on both the LCD notebook monitor, and also the external LCD monitor connected by HDMI cable.

Here is what xrandr returns:

Screen 0: minimum 320 x 200, current 720 x 400, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 720x400+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0 +
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0* 
   640x400        85.1  
   640x350        85.1  
HDMI-1 connected 720x400+0+0 (normal left inverted right x axis y axis) 370mm x 222mm
   1280x768       59.9 +
   1280x720       75.0     60.0  
   1024x768       75.0     72.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1* 

I've tried sudo dpkg-reconfigure xserver-org command, but I still get this low resolution - and the resolution is so low that I cannot see the OK button in System/Preferences/Display to change the display on the LCD Notebook.

Help!

Thanks,

David

---

### Post by djringjr on 2009-04-15
Does anyone know if this is a setting (or configuration file) problem, or is it a bug?

I'd like to report this as a bug if it is for the upcoming release of Jaunty.


Thanks,

David

---

### Post by Thelasko on 2009-04-15
What kind of video card is it?

---

### Post by djringjr on 2009-04-15
GPU/VPU:  Intel Integrated Graphics Media Accelerator 4500MHD
	  Video Interface:  	HDMI, VGA

More specifications here:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4492099&CatId=3444]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4492099&CatId=3444")

---

### Post by Thelasko on 2009-04-15
I'm not an expert on the 4500 series, but I know a bit about the older 3100 chip sets.  The 3100 series will only allow a [maximum virtual resolution of 2048x2048.]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#the_Virtual_screen")  That means that both of your screen resolutions must fit into a box that size.

That may be the source of your problem.

---

### Post by djringjr on 2009-04-17
One thing I forgot to say - "out of the box" before I tried to change the resoolution of the laptop screen (it was annoying and not wide), I had 1024x768 resolution on both the external HDMI monitor and the laptop.  The external monitor has a circuit that stretches the video to make it appear full screen so it wasn't annoying.

There is a bug in Jaunty about wide screen video - and it has been reported.  I don't know if this is a bug or just my lack of knowledge in finding the answer.

Regards to all,

David

---

