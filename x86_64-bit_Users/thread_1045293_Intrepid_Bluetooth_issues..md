---
title: "Intrepid Bluetooth issues."
date: 2009-01-20
forum: x86 64-bit Users
---

### Post by mckeja on 2009-01-20
I am not sure if this is just an amd64 problem, or if it is an Intrepid issue, but I had a lot of difficulty with my Bluetooth keyboard and mouse. I believe, however, that I have finally gotten things to work and figured I should post my process for others who might be having the same troubles.

The first thing I discovered was that in normal USB mode, my keyboard and mouse worked just fine. However, pulling out the dongle and replacing it just before logging in after every reboot is annoying. :)  Once logged in, using my keyboard/mouse in USB mode, I was able to do some research.

First, I installed the package "bluez-compat".  Then I plugged in my corded USB keyboard. I don't have a mouse other than my bluetooth one, so I opened a terminal first, then ran:
sudo /etc/init.d/bluetooth restart

Once that finished, my bluetooth mouse and keyboard were again in bluetooth mode and no longer functioning. I pressed the discovery buttons on both my keyboard and mouse, then using my normal USB keyboard, typed the following into the terminal window:
sudo hidd --search

Both the mouse and keyboard were detected and functioning at this point. After restarting the system, my Bluetooth keyboard/mouse were no longer functioning, so I did some more research.

The next step I had to take was to open the Bluetooth preferences, either by going into "System/Preferences/Bluetooth" or right-clicking the bluetooth icon and choosing "Preferences." Once the window opened, I had nothing in 'known devices' and no options were selected under 'visibility setting.'  

It is necessary to select "Always Visible" as the option for visibility settings, or you will always have to manually connect your bluetooth keyboard and mouse.  Next, I needed to click the big plus icon (Add Device) and start the Bluetooth Device Wizard.  Once the Device Search screen appeared, I pushed the 'discovery' button on my keyboard. It soon appeared in the window, and I selected it and clicked forward. It then prompted me to input a pin code on my keyboard. Once I did so, it finished and my keyboard was listed in known devices.  The mouse was a little more difficult because I had to use keyboard commands such as tab and the arrow keys to select my mouse from the list and finish the wizard.

By trial and error I learned that both steps, selecting 'always visible' and adding the devices to the 'known devices' list, are necessary to keep your keyboard and mouse functioning after reboot.

I hope this helps others who may be having issues with Bluetooth devices in Intrepid.

---

### Post by Bloemetjesgordijn on 2009-01-23
thx

I have had the same issue. Thx for writing it down.

However one of my desktops (I have something like "user-Desktop-1" and "user-Desktop-0") in the BlueTooth menu crashes once in a while.

Cheerz

Bloemetjesgordijn

---

