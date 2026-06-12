---
title: "WakeUp Suspend with PS2 Keyboard How ?"
date: 2008-11-24
forum: x86 64-bit Users
---

### Post by Rodney9 on 2008-11-24
Hello,
How do I set my ps2 keyboards 'Wake Up' key to wakeup/resume from suspend.

The 'Sleep' key does work.
I can not find anything in Keyboard Shortcuts for wake up though.

I have searched this forum and can find references to usb, so I did try -

$ cat /proc/acpi/wakeup
Device S-state Status Sysfs node
P0P2 S4 disabled pci:0000:00:01.0
P0P3 S4 disabled
P0P1 S4 disabled pci:0000:00:1e.0
UAR1 S4 disabled pnp:00:0c
PS2K S4 disabled pnp:00:0e
EUSB S4 disabled pci:0000:00:1d.7
USBE S4 disabled pci:0000:00:1a.7
P0P5 S4 disabled
P0P6 S4 disabled
P0P7 S4 disabled
P0P8 S4 disabled pci:0000:00:1c.4
P0P9 S4 disabled pci:0000:00:1c.5
GBEC S4 disabled
USB0 S4 disabled pci:0000:00:1d.0
USB1 S4 disabled pci:0000:00:1d.1
USB2 S4 disabled pci:0000:00:1d.2
USB3 S4 disabled
USB4 S4 disabled pci:0000:00:1a.0
USB5 S4 disabled pci:0000:00:1a.1
USB6 S4 disabled pci:0000:00:1a.2
P0P4 S4 disabled pci:0000:00:1c.0

and -

$ echo PS2K > /proc/acpi/wakeup
bash: /proc/acpi/wakeup: Permission denied

beyond this I'm stumped, any clues ?

---

### Post by inobe on 2008-11-24
i am not sure i understand, are you locked out ?


did you sudo that last command ...

---

### Post by Rodney9 on 2008-11-24
> **inobe said:**
> i am not sure i understand, are you locked out ?


did you sudo that last command ...

Yes 
> ***sudo*** echo PS2K > /proc/acpi/wakeup
bash: /proc/acpi/wakeup: Permission denied

---

### Post by Rodney9 on 2008-11-24
Would a usb keyboard work ?

---

### Post by null_pointer_us on 2008-11-24
> **Rodney9 said:**
> Hello,
How do I set my ps2 keyboards 'Wake Up' key to wakeup/resume from suspend.

The 'Sleep' key does work.
I can not find anything in Keyboard Shortcuts for wake up though.

I've always set the wakeup key in the computer BIOS. Mine's set to the key with the power logo on it, but I could enable a BIOS option to wake up on any keypress. This feature varies widely, based on the system board. Some system boards use jumpers (instead) to enable keyboard/mouse wakeup.

---

### Post by Rodney9 on 2008-11-24
> sudo su
echo PS2K > /proc/acpi/wakeu

I have re-booted and used System/Preferences/Keyboard Shortcuts and still the 'Sleep' key will not work as it did *before* I used the code above.

> cat /proc/acpi/wakeup shows PS2K disabled, I do not understand ?

I have checked the bios in my brand new Asus P5Q Pro m/b, it  has power on by keyboard in the bios, but no wake execpt "PCIE devices to generate a wake event", I don't know what this means.


Now The 'Wakeup' and 'Sleep' keys *both* don't work, how do I get them to ?

Rodney.

---

### Post by null_pointer_us on 2008-11-24
> **Rodney9 said:**
> 

I have checked the bios in my brand new Asus P5Q Pro m/b, it  has power on by keyboard in the bios, but no wake execpt "PCIE devices to generate a wake event", I don't know what this means.


Now The 'Wakeup' and 'Sleep' keys *both* don't work, how do I get them to ?

Go into the BIOS and enable the Power On By Keyboard option. This will let the keyboard turn on or wake up the computer. I'm not sure what you need to do to get the sleep key working again, but, from what I can tell, the sleep key is an operating system problem whereas the wakeup key is a BIOS problem.

---

### Post by Rodney9 on 2008-11-24
> **null_pointer_us said:**
> Go into the BIOS and enable the Power On By Keyboard option. This will let the keyboard turn on or wake up the computer. I'm not sure what you need to do to get the sleep key working again, but, from what I can tell, the sleep key is an operating system problem whereas the wakeup key is a BIOS problem.

The power key does work, I had already enabled it in the bios. But not the sleep or wakeup keys, no keys will suspend or wakeup .   

Which is the best ps2 multimedia keyboard for Linux ?

ps: I checked the bios manual and looked at the m/b and the default jumper setting is for keyboard wakeup any key, of course none work for me.

---

### Post by stmiller on 2008-11-25
Some keyboards with third party buttons for wake/sleep actually require software in Windows to do those functions. It is going to be a stretch to get those special keys working in Linux to do power functions...


Wake from sleep with PS2 is a function in the BIOS as stated above. Enable 'S3' suspend, and wake from PS2 in the BIOS and that is pretty much it.

---

### Post by Rodney9 on 2008-11-26
> **stmiller said:**
> Some keyboards with third party buttons for wake/sleep actually require software in Windows to do those functions. It is going to be a stretch to get those special keys working in Linux to do power functions...


Wake from sleep with PS2 is a function in the BIOS as stated above. Enable 'S3' suspend, and wake from PS2 in the BIOS and that is pretty much it.

The sleep button did work until I did  - 
sudo echo PS2K > /proc/acpi/wakeup

I have enabled S3 and the default jumper setting is for keyboard wakeup any key, the keyboard still will not wake up the pc.

I am buying a usb "Logitech Illuminated Keyboard" tomorrow, hopefully it will wake up the pc from suspend.

Rodney.

---

### Post by Rodney9 on 2008-11-26
No luck, new keyboard, and still can not wake up from suspend with the keyboard, that is 3 (three) I have tried so far.

---

### Post by null_pointer_us on 2008-11-27
> No luck, new keyboard, and still can not wake up from suspend with the keyboard, that is 3 (three) I have tried so far.

Then the problem doesn't appear to be the keyboard. Any PS/2 keyboard ought to wake up the computer if you have the BIOS configured to wake up by any key. I would look into a BIOS update, even if the board is brand new. (But, if the only updated BIOS is a beta, I would contact Asus support for advice before trying it.)

Does the power button on your computer case wake the computer? This should work regardless of keyboard/mouse compatibility issues.

-----------------------------------

If the case's power button does not work, some possible causes/fixes are:

[LIST]
[*]The open source video drivers may not handle sleeping with your specific model of video card. Try installing the proprietary drivers through System -> Administration -> Hardware Drivers.
[*]Some motherboards have a variety of issues (e.g. booting, rebooting, powering down, sleeping, waking, etc.) when all four DIMM slots are populated, especially by high density DIMM modules. Try updating the BIOS first. If that doesn't help, try removing 4 GB of memory from your system.
[*]Some power supplies do not supply the proper amount/type of power to the system in sleep mode, depending upon how much power your components (CPU, RAM, GPU, HDDs, etc.) are using. Unplug unnecessary components. This definitely includes USB devices, such as flash drives, game controllers, multimedia devices, etc.
[*]Some power supplies and motherboards have sleep mode incompatibilities, and will not work properly no matter what you do. Try using Google to search for standby/sleep problems with your specific model of motherboard and power supply.
[*]Some system boards have issues with sleep mode and overclocking: you can do one or the other, but not both. My previous system board had this problem, but my current board sleeps/wakes fine with an E8400 at 450 fsb. Try resetting everything to stock.
[/LIST]
-----------------------------------

However, if you can use the case's power button to wake the computer, then it's clear that the sleep/wake process itself works fine, and the problem is simply limited to the way the BIOS and OS interact with your keyboard and mouse.

Try to wake the computer by double-left-clicking with the mouse. Perhaps this will tell us something about your system, either way. Note that the mouse light should stay on during sleep and wakeup, because the system has to keep the mouse "on" to detect the clicking.

-----------------------------------

Finally, here's some threads where people with Asus P5Q Pro boards got it working:

[LIST]
[*][http://forums.techpowerup.com/showthread.php?t=14664](http://forums.techpowerup.com/showthread.php?t=14664)
[*][http://www.tomshardware.com/forum/253748-30-wouldn-wake-sleep](http://www.tomshardware.com/forum/253748-30-wouldn-wake-sleep)
[/LIST]
The first thread is tiny, but it confirms that someone got his PS/2 keyboard to wake the computer with your model of system board. However, the second thread has a lot of info. Unfortunately, you have to wade through the unhelpful posts.

If all else fails, Asus support should be able to help you fix this issue.

---

