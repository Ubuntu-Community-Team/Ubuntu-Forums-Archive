---
title: "HP a1130n"
date: 2005-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by gzenitsky on 2005-11-16
Dear Ubuntu friends,
I'm looking for some assistance in getting Ubuntu (or any flavor of Linux for that matter!) to run on my HP a1130n. I've made several attempts to get Linux installed, trying several different distros including Ubuntu and Kubuntu 5.10 x86_64 packages. The HP utilizes an AMD Athlon 64 mounted on a MSI mobo with the ATI chipset including ATI's X200 integrated gfx. I'll apologize for the lack of detail but most of my attempts have hung on what appears to be an issue with USB. I've tried all the boot modifiers including "no detection", noapci, nolapci, etc. I have yet to get through a boot sequence successfully except for one time with FC4 and I can't even duplicate that success. If you have any success with this box or a similar machine, please give me a holler. I would much prefer Linux over the pre-installed XP Media Edition. Do I need to explain that? :razz:

---

### Post by victor_c26 on 2005-11-23
I have the a1130n and have the same issue that you have with the USB ports. With other linuz distros, I just connect my optical mouse to the PS/2 port with the adapter that was included with it.

But does Ubuntu actually run on your a1130n? Mine always gives me an error message saying it can't boot up Ubuntu because "The graphics chip wasn't configured correctly".

---

### Post by gmz on 2005-11-23
Victor,
I have had both Ubuntu 5.10 and Kubuntu 5.10 running on the HP. As I mentioned in a previous message, I had to disable Legacy USB Support in the HP bios but I am able to run any and all USB devices including my USB trackball. 

I'm going to make some assumptions about your graphic situation so if I mention something you already know or have tried, please don't take offense. I'm assuming by "can't boot up" that you mean the boot sequence ends at the command line prompt for your login instead of starting the X server and launching either KDM or GDM. You'll have to login using your credentials setup during the install and run the xserver configuration utility with the following commands:
             sudo dpkg-reconfigure xserver-xorg
You'll be prompted for your password and then the utility will run. The first screen will ask for an autodetection of your video hardware. It doesn't matter what you chose, yes or no. The next screen will present you with the graphic drivers available in your installation. Chose vesa near the bottom of the list. The remainder of the setup screens can be answered with the defaults. The monitor detection screens will normally pickup the right monitor assuming you have a fairly well known panel or CRT. Once you complete the last screen the utility will quit to the command prompt and here you can simply type startx and your system should launch your display manager and boot into your desktop.

Once your inside Ubuntu, launch Synaptic or Kubuntu's package manager Adept. Here you can search for and load the ATI drivers. The name of the drivers escapes me but I believe it's something like xorg-flgrx. I apologize for not having the exact driver name. Load this driver through the package manager or from the command line if you prefer using apt-get and once it's loaded, do a Ctl-Alt-F1 and then Ctl-C to get back to a command prompt. Run the dpkg-reconfigure process I detailed above and this time at the video hardware screen chose the flg driver (it won't say anything about ati), finish out the reconfigure utility and startx again. You should be at whatever screen resolution you chose during reconfigure running under the new driver.

If you've already know how to do this or if this is not the answer to your problem, again I apologize for wasting your time. Let me know if this works. I'll be glad to help you troubleshoot any further problems. 

By the way, I have been using the x86 packages only at this point. I'll start goofing with the x86_64 packages this weekend. 

Sincerely,

Greg Zenitsky
Lee's Summit, MO

---

### Post by thenoobest1 on 2005-12-05
this worked for me, thanks... the driver name is  'xorg-driver-fglrx-dev'

---

