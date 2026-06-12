---
title: "compatibility problems?"
date: 2006-05-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Symo on 2006-05-19
I've just gone and bought a computer and am trying to run Ubuntu as the only OS on it. I've now since discovered there can be problems with compatibility and I'm wondering if this could be the case with my computer components.

The processor is an AMD64 3400+. My chipset is northbridge: nVidia GeForce 6100 and southbridge: nVidia nForce 410 MCP.
For graphics I've got NV44 graphics DX9.0 VGA and Pixel Shader 3.0.
For audio it's Realtek ALC850 7.1 channel AC'97 audio codec.

Why I think there might be incompatibility problems is because I can't get X up and running on anything but the Vesa driver. (Have followed instructions for installing nVidia drivers but with no success.) Also have problems with multimedia.

If I do have components that are incompatible does that mean having to give up on Ubuntu and Linux?!

---

### Post by Jason_25 on 2006-05-19
Don't give up.  I'll be building someone a system like that running linux and a few other oses for someone soon.

What do you mean you have followed the instructions for the nvidia driver with no success?  That's very unspecific.  I can almost guarantee we can get your display right.  The 6100 is on Nvidia's compatibility list for 87.56.

---

### Post by Symo on 2006-05-19
Thanks for the reply.

I followed the instructions (method 1) on this page: [http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")
 
When I tried it the screen just went black - I couldn't even do CTRL+ALT+BACKSPACE. 

I also tried installing another nvidia driver (well, I don't know if it was another driver but it was listed separately in synaptic and was meant to provide support for GeForce chipsets). When I did that I got back to the command line at least. There was also a message which said "NVIDIA kernel module is version 1.0.7174 but this X module is version 1.0.7667".

About compatibility again.. so the GeForce 6100 is compatible, but what about the nForce 410? Am I just gonna be running on one lung?!

---

### Post by Jason_25 on 2006-05-19
Your motherboard should be fairly well supported. 

At what point did the screen go black?  Did you install the old 76.67 driver?  That may not support your card and probably could lock up your system.  Also, when it locked up, did you check your Xorg.0.log for any clues?

---

### Post by Symo on 2006-05-19
I tried to recreate what I did before by enabling the driver (version 7667) with sudo nvidia-glx-config enable and rebooting. The screen went black after the initial boot up sequence and just before the login page should have come up. I had to restart the computer and go into the BIOS to boot in recovery mode and then reconfigure X. I'm afraid that I don't know what command to use to check the Xorg.0.log file.
 I then went and uninstalled version 7667 and installed version 7174 legacy driver. Enabled the driver with sudo nvidia-glx-config enable and pressed CTRL+ALT+BACKSPACE. This time I got to the black screen with $ prompt. The message was something like "Failed to open NVIDIA kernel" or "Failed to intialise NVIDIA kernel".

 So 7174 seemed better in that it didn't create a lock up but it still didn't get X up and running.:-k 

By the way, I appreciate you helping me out here. This seems to be a nice community with helpful people.:)

---

### Post by Jason_25 on 2006-05-19
I take it your on Breezy if your still using those old drivers.  You probably need the newest 87.56.  You'll need to manually install and compile the driver on breezy.  When you say you had to restart the computer it was totally locked up?  Could you SSH into it?  Could you switch to a virtual console?  You'll need to do one of the two to check the logfile to see what's wrong.

---

### Post by Symo on 2006-05-20
I'm afraid I'm quite new to ubuntu and to Linux so I don't know all the terms yet or how to do many things.
Where can I find the 87.56 driver and how do I install it and compile the driver? (Or should I maybe just wait until Dapper comes out and then upgrade?)
How do I SHH or switch to a virtual console? And what do I type to check the logfile?

---

### Post by Jason_25 on 2006-05-20
It's the manual method in the link you posted earlier.  It basically entails removing your restricted modules, installing build-essential and your kernel headers, then running the installer from nvidia's website.  Then finally changing  your xorg file to match the driver.

You can upgrade to dapper now if you like.  To SSH you'll need to install openssh-server .  To switch to a virtual console, type ctrl-alt-[F1-F8].  There are  several ways to check the log.  It's located in /var/log with all the others.

---

### Post by Symo on 2006-05-22
Thanks Jason_25! That seemed to do the trick. It was an 87.56 I needed.

(This Ubuntu trip is gonna be a steep learning curve, I can tell...)

---

