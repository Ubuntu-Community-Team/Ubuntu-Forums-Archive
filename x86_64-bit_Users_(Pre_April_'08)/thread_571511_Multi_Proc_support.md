---
title: "Multi Proc support?"
date: 2007-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by ncreek on 2007-10-09
I have installed Feisty _64 several times. I am new to Ubuntu and Linux so I have been experimenting and end up botching the install. All in the name of learning. The one thing I can't locate is whether x86 Feisty will support my Athlon X2 4400. I think that I would be happier installing the straight 32b version over having to "doctor" the 32/64b installs that I am getting now. Just want to know if the dual CPU's will be supported?

---

### Post by John.Michael.Kane on 2007-10-09
> **ncreek said:**
> I have installed Feisty _64 several times. I am new to Ubuntu and Linux so I have been experimenting and end up botching the install. All in the name of learning. The one thing I can't locate is whether x86 Feisty will support my Athlon X2 4400. I think that I would be happier installing the straight 32b version over having to "doctor" the 32/64b installs that I am getting now. Just want to know if the dual CPU's will be supported?

First yes Ubuntu 32bit, and 64bit support dual core processors, As well as quad cores, and more.

Second what exactly is the issue you are having?

---

### Post by Kilz on 2007-10-09
> **ncreek said:**
> I have installed Feisty _64 several times. I am new to Ubuntu and Linux so I have been experimenting and end up botching the install. All in the name of learning. The one thing I can't locate is whether x86 Feisty will support my Athlon X2 4400. I think that I would be happier installing the straight 32b version over having to "doctor" the 32/64b installs that I am getting now. Just want to know if the dual CPU's will be supported?

Why would you want to run a 4 core processor with an operating system that cuts the performance? It would be like having a corvette and putting a yugo engine in it. Why would you post this as your first question? I could see if you were having some issue and had tried to resolve it. But on the first post?

---

### Post by ncreek on 2007-10-09
I appreciate the feedback. I initially was running dapper x86 on an Athlon XP. When I put together this new unit with the Athlon X2 4400. since it was a 64b and dual core decided to go Feisty_64. Well I have gotten most items to run under the 64b sys, but frankly it seems there are more crippled 64/32 apps running under Feisty. I now this may not set well with a bunch of folks but my feeling is that I would rather run a stable 32b dual core than a somewhat unstable 64/32b dual core.sys. i seem to run into quite a few apps that don't run well because of unsupported libs and such. LOVE LOVE LOVE Ubuntu. Maybe just need to run something a little less bleeding edge.

---

### Post by Kilz on 2007-10-09
> **ncreek said:**
> I appreciate the feedback. I initially was running dapper x86 on an Athlon XP. When I put together this new unit with the Athlon X2 4400. since it was a 64b and dual core decided to go Feisty_64. Well I have gotten most items to run under the 64b sys, but frankly it seems there are more crippled 64/32 apps running under Feisty. I now this may not set well with a bunch of folks but my feeling is that I would rather run a stable 32b dual core than a somewhat unstable 64/32b dual core.sys. i seem to run into quite a few apps that don't run well because of unsupported libs and such. LOVE LOVE LOVE Ubuntu. Maybe just need to run something a little less bleeding edge.

While that may have been true of Dapper running some 32bit applications (Open office was 32 bit in dapper). There are no 32bit applications in feisty except those you add. What applications are you having problems with? Did you add them yourself? If so how did you add them?

---

### Post by John.Michael.Kane on 2007-10-09
@ncreek Let the members here try to help you get the issues your having under 64bit sorted out before jumping ship,

Also IMHO moving back to 32bit should be a last resort used only after exhausting all options.

---

### Post by ncreek on 2007-10-09
Ok guys here goes. This is the kind of nonsence I don't need or want. Granted I love Ubuntu - lots of great features but stuff like this drives me nuts. The scenario:

After posting this afternoon I decided to take my Feisty I386 build out for a ride. Popped it in and went for a boot. Problem have a Geforce FX5500 that needs a restricted. The old Athlon X2 went into a nose diive and had to boot out. No matter whether I booted from the CD in straight start mode or safe graphics the Geforce would crash. Opted to go with the built in VIA graphics S3. By the time I had switched the inputs and the BIOS I somehow had corrupted xorg.conf. I looked at the xorg.log and found that for some reason the OS would now longer boot except in 640x480. It had ruled out all other modes. Edited and reedited xorg.conf to no avail. only 640x480. Reinstalled all the drivers including restricted. Alas I am writing this from Windows. This is too much. Love the OS but 64 seems to have too many bugs yet.

My System:

MSI k9vgm-v
athlon x2 -4400
2 g G-Skil DDR2 -800 Memory
>1Tb Seagate HDD (4)

---

### Post by Kilz on 2007-10-10
> **ncreek said:**
> Ok guys here goes. This is the kind of nonsence I don't need or want. Granted I love Ubuntu - lots of great features but stuff like this drives me nuts. The scenario:

**After posting this afternoon I decided to take my Feisty I386 build out for a ride.** Popped it in and went for a boot. Problem have a Geforce FX5500 that needs a restricted. The old Athlon X2 went into a nose diive and had to boot out. No matter whether I booted from the CD in straight start mode or safe graphics the Geforce would crash. Opted to go with the built in VIA graphics S3. By the time I had switched the inputs and the BIOS I somehow had corrupted xorg.conf. I looked at the xorg.log and found that for some reason the OS would now longer boot except in 640x480. It had ruled out all other modes. Edited and reedited xorg.conf to no avail. only 640x480. Reinstalled all the drivers including restricted. Alas I am writing this from Windows. This is too much. Love the OS but 64 seems to have too many bugs yet.

My System:

MSI k9vgm-v
athlon x2 -4400
2 g G-Skil DDR2 -800 Memory
>1Tb Seagate HDD (4)

You, by your own admitting, are running the 32bit version of Ubuntu(see bold text above). You had a video driver problem. Something that is common regardless of what version of Ubuntu you are running . 
The versions of Ubuntu are
i386 = 32bit
AMD64 = 64bit
It doesn't matter what your processor is. When we ask what bit you are running, we are referring to the operating system, not your hardware. You have installed a 32bit operating system. One that doesn't make use of the full performance of your hardware. Can you answer a couple questions?
1. Have you ever installed the AMD64 (64bit) version of Ubuntu.
2. What applications if any gave you issues while running the AMD64 (64bit) version of Ubuntu.

Next. You have little or no experience. If you do not ask for help, but instead give up. You will be trapped in the virus laden, malware infested, slow, expensive, blue screen of death operating system from Microsoft.
Linux is a good operating system. But it does require some setup and learning. Just as you had to learn when you started using Windows long ago. I am writing this from an Athlon x2 4600. There are no problems. But just as you would need to install drivers if you used a version of windows bought at a store (not a restore disk the computer manufacturer created with them) you will need to install video drivers.

---

### Post by Jouke74 on 2007-10-10
It sounds like most of your problems come from:

- Video drivers and setting up your video card. For the Nvidia Gforce there should be decent support, for the VIA I am not really sure. In principle the standard basic Mesa driver should be supported with both your graphics options. Did you check the CD for corruption of files (I know is a straw). Monitor, if only 640x480 is seen, the monitor section of your Xorg.conf probably needs adjustment. I read that you tried these things already... What is the ouput of "Dmesg"? I assume you tried a reconfiguration of the X-server already?

- It seems unclear what you call 64 bit and 32 bit from previous posts. The 64 bit version is indeed the AMD64 iso and 32 bit i386. If you mix these up with your operating system and programs / drivers, e.g. trying to install 64 bit video drivers on a 32 bit system you will have a real hard time to get it running, if at all. This also might explain the library errors. 

The same reason for these errors might be the fact that you are trying to run 32 bit apps on a 64 bits platform. In that case did you install the 32 bits libraries for 64 bit systems?

sudo apt-get install ia32-libs*

---

### Post by John.Michael.Kane on 2007-10-10
> **ncreek said:**
> Ok guys here goes. This is the kind of nonsence I don't need or want. Granted I love Ubuntu - lots of great features but stuff like this drives me nuts. The scenario:

After posting this afternoon I decided to take my Feisty I386 build out for a ride. Popped it in and went for a boot. Problem have a Geforce FX5500 that needs a restricted. The old Athlon X2 went into a nose diive and had to boot out. No matter whether I booted from the CD in straight start mode or safe graphics the Geforce would crash. Opted to go with the built in VIA graphics S3. By the time I had switched the inputs and the BIOS I somehow had corrupted xorg.conf. I looked at the xorg.log and found that for some reason the OS would now longer boot except in 640x480. It had ruled out all other modes. Edited and reedited xorg.conf to no avail. only 640x480. Reinstalled all the drivers including restricted. Alas I am writing this from Windows. This is too much. Love the OS but 64 seems to have too many bugs yet.

My System:

MSI k9vgm-v
athlon x2 -4400
2 g G-Skil DDR2 -800 Memory
>1Tb Seagate HDD (4)
I'm not going to try and change your mind, As said many time before no matter how much info is made available 'In the end you the user will have to make the choice of what is right for you,and you needs.'

That said. Here is what you can try either under 64bit or 32 bit. After plugging back in your geforce card etc.

1) Reboot with the Ubuntu cd in the drive.
2) At the boot/install menu (make sure to press F6 first).  
3)Add the command below to the boot line
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

4) Proceed to install Ubuntu as you normally would.


Also should you every have issues with your xorg.conf.You have a couple of options.

Option one manual edit:
1) press Ctrl-Alt-F2
Next enter the below command.
```
sudo nano /etc/X11/xorg.conf 
```
The above command allowed you to edit the conf to use vesa.

Option two xorg reset:
1) press Ctrl-Alt-F2
Next enter the below command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ncreek on 2007-10-10
Ok let me set things straight. 1) I am currently running an AMD_64 Feisty on the system. 2) When I said that I took Feisty i386 out for a drive I meant a distro boot. The problems that I encounter are numerous and seem to revolve around libs. I know that 32b apps can run on this 64, but just as there are workarounds for things , i.e. no 64b Flash in 64b Firefox (which I installed), this seems to be the normal way of getting many of the mundane installs completed in AMD_64. As for the restricted drivers issue with the Nvidia (I installed and manually reconf. xorg.conf, because the res. issue and pci address was incorrect after install. I know I should have written a bug report. I will when I boot back into Ubuntu (using the other junk sys right now:(..). But less I digress.. yesterday I booted the Feisty i386 distro to try out some items. With the Nvidia running the system crashed (POWERNOW -k8 constantly restting bits. Shut down computer. Again rebooted now chosing safe graphics mode on distro. Same result. Shut down -reboot reset bios to internal Via and recable monitor. Now the distro would not accept the Via-- what gives. I thought a distro always ignored any underlying installed system and ONLY used the CD files. So after all was said and done I ended up with a botched EXISTING AMD_64 install. The X11 system has some serious issues. I sudo nano xorg.conf to death. Reinstalled all the X11 libs. xorg.log says everything installed ok but the NVidia is now incapable of all but 640x480. This seems to be somewhat the normal in the 64b install. My feelings is that there is a mixing of 32 and 64 libs that cause these problems. i love the speed of the 64b system, but hate the constant struggle I am encountering to keep it healthy, just like this X11 gambit going on now. The short time I ran the old Dapper i386 I don't seem to remember all these issues. That was the reason for originally posting asking about the dual cpu support in i386. At least I have the dual cpu working.I could go on about other issues I have encountered, for the most part I read posts and docs to the extreme before posting. i most always get the answer by reading. That still eats up a lot of time. I have no idea why the trashing of my AMD_64 install by running Feisty i386 distro. But this is the problems!!!!!

---

### Post by John.Michael.Kane on 2007-10-10
@ncreek you might have better luck doing a clean install or running Gutsy. 

Personally I have the feeling your issue is not so much Os related, As the system crashed using 32bitubuntu. 

IMHO it seems more hardware related looking at all the issues you are having, It seems time to strip the rig down, and rebuild it. checking every piece of hardware to make sure none are faulty.

That said you will have to run whatever architecture, As well as distro that offers what you need, and works with your hardware.

---

### Post by ncreek on 2007-10-10
thanks for the reply. I am in W2k at the moment and I am looking at the hardware connections and you may be onto something. I don't see my Nvidia card in the view by conn. but I see the onbrd VIA S3, shich is disabled. Also the display is really corrupted. So maybe the issue is that I am having an ongoing conflict between the geforce 5500 and the S3. I am perplexed, but will ferret deeper before I throw in the AMD_64 towel. Thanks again.

---

