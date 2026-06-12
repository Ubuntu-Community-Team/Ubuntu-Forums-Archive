---
title: "New Ubuntu 7.04 machine needs help"
date: 2007-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kxpress on 2007-09-02
:cool:I have a 64-bit machine (Thinkpad T61 Intel Centrino T7300 2.0 GHz, 2 GB DDR2 Ram PC5700, 15.4' screen 1680x1055 WXGS+, Nvidia Quadros M140 128MB, 120 GB SATA, CD R/W/DVD-ROM, Intel PRO 3945 Wireles Card) with "three" OSes WinXP Pro 32-bit, Ubuntu 7.04 32-bit, and Unbuntu 7.04 64-bit.

Reagarding Ubuntu environment for both 32-bit and 64-bit, my machine is still configured with "vesa" graphic 1024x768 screen; CD R: functional, W: not verified; sound : not verified; wireless: functional.
My intention is used this machine to do some design simulation works, I think 64-bit version will give me a boost in performance.

The first hurdle is installing the Nvidia chip's driver to utilize the maximum screen performance of the 1680x1050 screen and NVidia Quadros M140. My screen looks "awkward " with the default "vesa" screen configuration. I've read some HOW TO posts, but I am not sure which one is easiest and most sufficient... I've tried to use the Envy script to install new Nvidia driver without success

On Envy's terminal console after extracting packages, it asked to insert the Ubuntu 7.04 release CD in the the drive 'CDROM', the press"enter" ...
I did so, but it stucked there forever ... Anyone experienced the same sympton ? I also tried to use the command text version i.e. 
Code: sudo envy -t
The process stayed at one step forver...

SATA Controller Mode must be in "Compatibility" instead of  "AHCI" for CD/DVD ROM to be functional. Am I loosing some disk performance here ?

I am new to Linux, so I would not dare to follow the instructions on the Nvidia website or other post with 27 or so commands.

My experience installation for both 32-bit or 64-bit Ubuntu is very simple not much different, however I noticed for 64-bit Ubuntu the wireless card works consistently while in 32-bit Uncuntu the wireless works off and on ...

In my machine, the 64-bit Ubuntu's boot time is certainly much faster than Ubuntu 32-bit's. Can I say performance can be recognized here ???? After everything is setlled down, I plan to erase 32-bit partition to regain my disk space for future usage.

I know this is Linux, it is free, I can't expect a simple click as I paid for Window. But if anyone  has succesful installed this type of Graphic Card, please help to lead me step --by-step in making through this process. I am not a software-oriented guy, especcially in Linux..... 

Thank in advance.:)

---

### Post by gtdaqua on 2007-09-03
Install the following from Synaptic Package manager.

Or got to the "System" menu and find "Resrticted Drivers...". This should be under "Administration" - I am not sure but should be easy to locate under "System" menu. 

Once you click Restricted Drivers, you should see nvidia listed and from there you can install it. 

OR search for the following in the Synaptic Package Manager:
nvidia-kernel-common (enough for display)
nvidia-glx-new  (required for google earth )

Install both the components.

Then restart the PC so that the NVIDIA chipset is loaded.

---

### Post by gtdaqua on 2007-09-03
See [this]("http://www.psychocats.net/ubuntu/nvidia") link too:

---

### Post by Jouke74 on 2007-09-03
First make sure you have a internet connection working ok (as you stated should be working).
Then under Synaptic you can set your repositories to include all universes (restricted is required).
Then do what the guy above me told you. You wont be needing the CD anymore.

If your sound is configured correctly you should hear it at log-in. If not please first check (right click) the Alsa mixer (sound icon in the right corner) and move around with the sliders and check boxes while playing some WAV music file with Totem.

If you are going to do simulation work, you are going to need to get used to the command line anyway, I guess? You will see a big performance boost under 64 bit. The command line works boils down to one thing: Type a command, and read the result. If the output states what it has done and everything is ok, then start with the next command. If it says error anywhere stop, and read why.... It is also good to know what the command is doing before hand. Easiest way to learn: Google.

Why the 32 bit and 64 bit version of Ubuntu installed? 64 bit will be fine. One big hurdle, your wireless internet is working and the rest should not be a major problem. 

Good luck.

---

### Post by Kxpress on 2007-09-03
I only found one driver in my machine:
"Intel(R) PRO/Wireless 3495 Network Connection driver for Linux"

I already followed other instructions, get in to the Synaptic Manager selected to install two files: "Nvidia-glx-new" and "Nvidia-kernel-common", rebooted the machine but  there is no Nvidia Driver listed under Restricted Driver window???

Any idea ?

Thanks

Notes: I used Ubuntu Alternate CD 7.04 for installation and selected "Vesa" as defaulted graphic mode. The reason I have both 32-bit and 64-bit versions due to reading some conflict stories about 64-bit vs 32-bit versions. It turned out it is not much difference in installation, both are easy to install with same minor heck-ups... I planned to erase the 32-bit when everything was settled. I used Unix for awhile, Linux is similar but I am just precautious .... or as someone said just a "lazy" new user .... expecting too much for free. Noop, your help is greatly appreciated, my "phylosohpy" is why re-spinning the wheels ? Cheers.

---

