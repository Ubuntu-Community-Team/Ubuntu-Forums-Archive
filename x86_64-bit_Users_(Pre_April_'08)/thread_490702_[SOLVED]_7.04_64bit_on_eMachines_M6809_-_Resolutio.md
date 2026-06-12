---
title: "[SOLVED] 7.04 64bit on eMachines M6809 - Resolution Problem"
date: 2007-07-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-07-02
Having ubuntu on my desktops has sparked me to install the same on my laptos.  I installed on my personal lappy 1st, because my wife doesen't let me change hers unless I can promiss it won't jack anything up in the process.  What are gonna do?

Laptop: eMachines M6809 - AMD64 3200+, 1.25GB RAM, 7200 RPM HD 60GB, Broadcom Wireless, WinXP Partition 40GB, ATI Mobile Radeon 9600.

[B]Installs perfectly but 1'st major proble is the 1024x768 resolution.  The native screen resolution for this system is 1280x800.  The option is there after installing the proprietarity ATI drivers from the ATI website, but the screen is garbled and corrupt to the point of not being able to recognize anything.  Installing the restricted drivers from the ubuntu provided option gives exactly the same result.

Using only the default driver won't let me have anything but 1024x768, which is of no use at all to me.[/B]

I removed ubuntu from the system for now.  I'm hoping someone here will have it correctly installed/configured on one of these laptops and can provide me with instructions on how to do the same.

The next problem if I get past the video issue is making the wireless work...


Any information is appreciated even if it's just to tell me I'm SOL on this computer.

Heck, I've been trying for 2 weeks to get a wireless connection on one of my desktops to no avail...

---

### Post by crjackson on 2007-07-03
Wow, no one has any ideas at all?

---

### Post by crjackson on 2007-07-06
Not even an idea?

---

### Post by bongey on 2007-09-08
Hello, I have been running linux on a 6809 for about 3 years gentoo, suse, fedora, and ubuntu.  Here is the problems. The 9600 is a AGP card, but there is a little problem with  the kernel/graphics driver, it incorrectly detects the video ram as 128 mb.  Try it lspci -v . The kernel started giving issues on my machine around a 2.6.18. My suggestion if you want all the cool stuff like xgl and beryl , downgrade to edgy i386. I have struggled with the ati drivers and the open source ones for more than a year, they just don't work right in the latest kernels. I have looked into trying to hake the kernel to fix the issue but for now I don't have the time. I am using the ati drivers version 8.29.6 . The x64 on ubuntu will give you floating point errors when trying to run with direct rendering.  If you don't care about direct rendering the latest work. 
For you question try editing the Device section of the xorg.conf file this is what mine looks like. 

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx" 
        Option "Mode1" "1200x800"#this tells you LCD monitor . 
        Option "Mode2" "1200x800"# this has to be the same on older ati drivers .
                                                            #older drivers mess up the where the pointer should be at when going from screen to screen .
        Option "DesktopSetup" "horizontal" #don't add unless you have a dual screen setup.
        Option      "VideoOverlay" "on"
        Option      "BusType" "PCI"
        Option      "OpenGLOverlay" "off"
EndSection
 
If you have any other questions send me line.

---

### Post by crjackson on 2007-09-08
Actually, I should have marked this thread solved, but since no one replied to the thread I forgot.

The latest drivers work perfectly for me and with all my resolutions available.  I have no video issues at all.

I just follow the manual install procedure and all is well...  Thanks for the reply.

---

### Post by bongey on 2007-09-09
Do you have direct rendering working? The latest drivers didn't work with my 6809 with direct rendering.

---

### Post by bongey on 2007-09-09
If you have the same machine as me , the only thing I can think of is my hardware is faulty, or the amount of ram I have. I have it maxed out a 2GB , 100GB hd, 4000+ processor(latest bios).  I have been rough on it though, so I wouldn't be surprised if that were that were the case. If you have 7.04 working with direct rendering , what version of the driver , the one just released in august? I want to run the 64-bit version in AGP mode. Can you post your xorg.conf file? With the latest drivers everything seems to go alright but if dri works , I get nothing but a blank screen. Looking into the  Xorg.0.log shows no warnings or errors, just a blank screen. If I ssh into the machine xorg is taxed out a 98% cpu and doesn't let it go, only way to get out of it is a hard reboot.  I am going to run a memtest real quick to see if I can see anything there.

---

### Post by crjackson on 2007-09-09
It actually doesn't sound like we have the same machine.  My machine has 256MB on board ram, and 1GB Kingston in the only memory slot.  How ever did yo come up with 2GB?

I have a Hitachi 7200 RPM HD upgrade.  The drivers are the latest posted on the ATI download page.

I installed the drivers manually using this[COLOR="Red"]**_[ Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.39.4_Driver_Manually")_**[/COLOR]

---

### Post by bongey on 2007-09-09
If you have a 6809 you have the same machine as me. The machine is capable of 2 GB. There is a module under the keyboard for upgrading to 2GB. I replaced the HD and the CPU. Your machine has the same motherboard and such. It might be that have 2GB of ram installed that is giving me issues.

---

### Post by crjackson on 2007-09-09
> **bongey said:**
> If you have a 6809 you have the same machine as me. The machine is capable of 2 GB. There is a module under the keyboard for upgrading to 2GB. I replaced the HD and the CPU. Your machine has the same motherboard and such. It might be that have 2GB of ram installed that is giving me issues.

[FONT="Comic Sans MS"][SIZE="3"]Okay, so you are saying that there is a second memory slot, other than the one I can access by removing the bottom plate?

I'd love to replace the CPU but I'm not big on dissecting laptops.  I've literally built hundreds of desktops but the laptop is a more delicate animal.
[/SIZE][/FONT]

---

### Post by bongey on 2007-09-09
Yep about right under the left control key. Trust me the 2nd one  is pain to replace the memory module. There is no onboard memory, just another dim slot. The cpu is really easy to swap out, if you ever want to do it I could give you instructions. In the mean time I am trying to see if I can find one on ebay. You never said if you had direct rendering working . If you do then my machine hardware is acting up. Thanks

GL-Demo/redbook$ glxinfo |grep rend
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: MOBILITY RADEON 9600 Generic

---

### Post by crjackson on 2007-09-10
> **bongey said:**
> Yep about right under the left control key. Trust me the 2nd one  is pain to replace the memory module. There is no onboard memory, just another dim slot. The cpu is really easy to swap out, if you ever want to do it I could give you instructions. In the mean time I am trying to see if I can find one on ebay. You never said if you had direct rendering working . If you do then my machine hardware is acting up. Thanks

GL-Demo/redbook$ glxinfo |grep rend
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: MOBILITY RADEON 9600 Generic

Yes, I'd be interested in upgrading the cup.  I just don't way to PRY my case apart and mess up the lappy.  

As far as I can tell I do have direct rendering working on mine.  Looking at your glxinfo line above it appears that you do too, so what isn't working on yours?

---

### Post by bongey on 2007-09-10
I can't get it to work in ubuntu 7.04 i386 or x64. I am using edgy right now which is alright. The cpu upgrade requires removing the keyboard, then a plate under the keyboard then the cooling system, really it isn't that bad. The only catch is the there is a screw for a ground wire for the screen that is threaded into a screw holding down the laptop heat sink.

---

