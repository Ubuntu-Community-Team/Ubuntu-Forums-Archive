---
title: "Bluetooth keyboard in grub?"
date: 2006-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Eckstona on 2006-12-05
I have a logitech MX5000 desktop that runs on bluetooth. Every time I wish to boot into Winbloze with grub, I have to track down and plug in a PS/2 keyboard. Is there anyway I can get my bluetooth keyboard to work with grub?

---

### Post by Eckstona on 2006-12-12
Arrgh! Bump.

---

### Post by woolyghost on 2007-12-14
I have the same problem with the Logitek Dinovo keyboard. Any help would be great.

---

### Post by Law506 on 2007-12-14
Same problem here.  Had both XP and Ubuntu setup to run my Logitech MX1000 mouse and MX5000 keyboard set... but sadly could not go from one O/S to the other without a USB.  I am currently back to my old USB mouse and keyboard.  So yeah, if anyone knows anything that would be awesome.

---

### Post by John Jason Jordan on 2007-12-14
> **Law506 said:**
> Same problem here.  Had both XP and Ubuntu setup to run my Logitech MX1000 mouse and MX5000 keyboard set... but sadly could not go from one O/S to the other without a USB.  I am currently back to my old USB mouse and keyboard.  So yeah, if anyone knows anything that would be awesome.
I don't have a bluetooth keyboard and I don't have Windows, but I do have a Logitech V270 bluetooth mouse that is working flawlessly in Gutsy x86_64. I used Blueman to pair it up. When I reboot it just starts working as soon as the login window comes up. Blueman is not in the repositories but you can download it.

---

### Post by mediamind on 2007-12-16
I also have this problem--I'm using an apple bluetooth keyboard and logitech v270 mouse. My system (Dell Optiplex gx270) is set up for dual boot (gutsy and xp) but I still need my clunky ps2 keyboard for the grub menu.

Any suggestions are welcome!

---

### Post by John Jason Jordan on 2007-12-16
> **mediamind said:**
> I also have this problem--I'm using an apple bluetooth keyboard and logitech v270 mouse. My system (Dell Optiplex gx270) is set up for dual boot (gutsy and xp) but I still need my clunky ps2 keyboard for the grub menu.
You didn't say if the mouse is working. Is it? If so, how did you get it working?

One additional thought: I doubt if you will be able to use the bluetooth keyboard with the grub menu. Bluetooth on my system doesn't start until just before the login screen. You can edit the grub menu after booting, of course. It's just that if I'm right you can't edit it on the fly during the boot process unless you add a USB or PS2 keyboard.

---

### Post by mediamind on 2007-12-16
Yes, both the logitech mouse and the apple keyboard are working well. I'm able to use them to sign in at the login menu. 

I did two things to get them working:

1. I added the following code to the end of my /etc/bluetooth/hcid.conf file: 
sudo gedit /etc/bluetooth/hcid.conf

}
device 00:11:22:33:44:55 {
name “Apple Wireless Keyboard”;
auth enable;
encrypt enable;
}

device AA:BB:CC:DD:EE {
name “Bluetooth Travel Mouse”;
}


2. I played around with the HIDD settings: 
sudo gedit /etc/default/bluetooth 

and eventually settled on this configuration:

HIDD_ENABLED=1
HIDD_OPTIONS=" -i AA:BB:CC:DD:EE:FF --connect 00:11:22:33:44:55 --server"

Here's a few links that were useful in helping me figure this out:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)
[http://ubuntuforums.org/showthread.php?t=87919&highlight=bluetooth+mouse&page=8](http://ubuntuforums.org/showthread.php?t=87919&highlight=bluetooth+mouse&page=8)
[http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673)

As an aside, once I got the mouse working, I had to turn down the motion acceleration and sensitivity in system preferences--the mouse was just too fast. 

A related question: Right now gutsy is the default in my grub menu which means I only need to dig out my ps2 keyboard to switch to xp during bootup. Besides using my wired keyboard or making xp the default in the grub menu, is there any other way to switch between gutsy and xp?

---

### Post by John Jason Jordan on 2007-12-16
> **mediamind said:**
> A related question: Right now gutsy is the default in my grub menu which means I only need to dig out my ps2 keyboard to switch to xp during bootup. Besides using my wired keyboard or making xp the default in the grub menu, is there any other way to switch between gutsy and xp?
Great added information for those wanting to get bluetooth working. In my case I have a Logitech V270 travel mouse, but by using Blueman I didn't need to do any of the stuff you did - Blueman is a GUI bluetooth applet that handles all the pairing up and stuff. It saw the mouse, paired it up, and it has worked flawlessly ever since (except, as you noted, nothing bluetooth works until the login screen). 

I also have a pair of Sony DR-BT50 audiophile bluetooth headphones. Again, Blueman paired them up perfectly. However, I could not get sound out of them until I read another thread where I learned that I need a .asoundrc file in my home folder. I didn't have one, but I copied and pasted from others' suggestions into Text Editor and saved the file as ~/.asoundrc (just search the forums for asoundrc to find the text). The .asoundrc file has the same sort of script language as your hcid.conf file.

Regarding XP and Linux, I don't know of any solution for your specific problem. But I can suggest that you consider running XP inside of Linux. That way you only boot to Linux. In order to run XP you launch it like a program once Linux is running. I did this with Virtualbox, which works perfectly and is easy to configure. Windows launches in about 25 seconds and thereafter runs just as fast as if it were running alone. However, if you are short on memory, this may not be the best solution. It may also not be a good solution if you spend more time in Windows than in Linux. (Although you could reverse the process and run Linux as a guest OS from within XP.)

I note that on my computer bluetooth can be turned on and off in the BIOS. Thus, I don't know why it needs Linux booted before it works. It should be accessed directly by the BIOS, so the keyboard should work the same as a wired keyboard. Having said that, one of the big things about bluetooth is security. You wouldn't want someone sitting at another desk to be able to use a bluetooth keyboard to access your computer. Thus, bluetooth devices always need a secure file containing the device's address. As far as I know Windows and MacOS have the same problem - the bluetooth devices don't work until the OS has booted. Maybe what is needed is for motherboard manufacturers to come up with BIOSs that have the ability to store device addresses.

---

### Post by mediamind on 2007-12-17
Thanks for the heads up re Blueman and Virtualbox. I installed Blueman tonight--I rather like the GUI.

And I'm going to give Virtualbox a try as well. Ideally I'd still like to be able to switch between gutsy and xp in the grub menu using my bluetooth keyboard though your point about bluetooth security makes a lot of sense.

One last thought: There must be a way to reboot from gutsy into xp without making xp the permanent default in grub. In other words, I'd like to keep gutsy as the default choice in grub but still be able to restart from gutsy into xp when needed. Ideally there could be a "restart in xp" option/button in the log off screen.

---

### Post by John Jason Jordan on 2007-12-17
> **mediamind said:**
> Thanks for the heads up re Blueman and Virtualbox. I installed Blueman tonight--I rather like the GUI.

And I'm going to give Virtualbox a try as well. Ideally I'd still like to be able to switch between gutsy and xp in the grub menu using my bluetooth keyboard though your point about bluetooth security makes a lot of sense.

One last thought: There must be a way to reboot from gutsy into xp without making xp the permanent default in grub. In other words, I'd like to keep gutsy as the default choice in grub but still be able to restart from gutsy into xp when needed. Ideally there could be a "restart in xp" option/button in the log off screen.
This is easy to do. From the command line:

sudo gedit /boot/grub/menu.lst

The menu.lst file is what grub reads in order to show your boot options. At the end you will find an "automagic" section containing the boot options. 

The first thing you need to do is a Save As under a different filename in order to make a backup of your existing menu.lst file. Then reopen menu.lst with gedit and go to the automagic section. The first (default) item in the boot menu will be the first entry in the "automagic" section. So just take the Ubuntu lines and copy and paste them ahead of the Windows lines. Save the file and reboot. That should do it.

If by chance this mucks things up, remember you can edit the boot menu list entries on the fly during boot. When grub first comes up hit Esc to stop the boot process and allow you to edit the boot options. Follow the instructions, e.g., "e" to edit one of the boot options, go to the line you want to edit, hit "e" again to edit the line, then hit "b" to boot with your changes. Whatever edits you make on the fly will not be saved to the menu.lst file so, if you had a problem and your on the fly edits worked, after you finish booting open Gedit and make the changes to the menu.lst file so they will be permanent.

As for the "restart in XP" option on the shutdown menu, that is not a possibility. As far as I know it is hard coded and there is no way to change the options. That having been said, you might be able to hack something up that would do it. Linux has awesome abilities to customize options. My problem is that I am not a programmer and I don't understand everything about how Linux and Ubuntu work.

---

### Post by mediamind on 2007-12-17
Thanks much for the instructions on changing the grub boot order. I did this for my original install but it's good to have a quick refresher.

> As for the "restart in XP" option on the shutdown menu, that is not a possibility. As far as I know it is hard coded and there is no way to change the options. That having been said, you might be able to hack something up that would do it. Linux has awesome abilities to customize options. My problem is that I am not a programmer and I don't understand everything about how Linux and Ubuntu work.

Yes, I'm clearly not a programmer either though I am going to keep searching for a hack for this--I'm determined to get rid of my ps2 keyboard once and for all. 

Thanks again for your help.

---

### Post by woolyghost on 2007-12-18
I thank you all for your ideas but I think you are all missing something.

I to have the same problems with this setup: I Dual Boot Win XP, Vista & Gusty Gibbon. I have the Logitech deNovo Media Desktop (Bluetooth MX Lazer Mouse, Bluetooth Keyboard & Media Pad.) All works fine from login onwards but not in Grub & my BIOS.

That is not the whole story though. I can enter BIOS and operate the Grub menu with the bluetooth keyboard when restarting from Win XP or Vista, it is only when I restart after using Ubuntu that it dose not work. This proves that it is not a bluetooth driver problem and that it is actualy possible to use this setup before ubuntu (or any other OS) boots.

I have read somewhere that the Logitech bluetooth dongle can operate in two different modes (HIDD & Bluetooth.) When in HIDD mode it acts just like a normal USB keyboard (Human Interface Device.) Once the operating system takes over the mode is set to Bluetooth and the devices get paired.

I also read that Logitech do not make linux drivers and will not give out info to help us. This means that currently no one knows exactly how to switch between modes properly.

My asumption is that the proper drivers installed under windows must be switching off bluetooth and enabling HIDD as windows shuts down thus letting me use the keyboard on next boot. This is only a guess but sounds very likely to me. In Linux this must not be happening and so we are stuck in Bluetooth mode.

I hope this helps somebody out there, and more so I hope it points someone  with more knoledge than me in the right direction to find a proper soloution for all of us.

PS.
There is about a 30 second delay in my Grub before it loads the default OS. This is enough time to press the little red buttons on the back of the keyboard and on the dongle which in my case will reactivate the keyboard so that I can select another OS.

Its not ideal but it seems to works and means that I can put away the old wired keyboard for good.

---

### Post by bernardfrancois on 2008-01-13
> **woolyghost said:**
> 
There is about a 30 second delay in my Grub before it loads the default OS. This is enough time to press the little red buttons on the back of the keyboard and on the dongle which in my case will reactivate the keyboard so that I can select another OS.

Its not ideal but it seems to works and means that I can put away the old wired keyboard for good.

The same works for me. Pressing the button on the back of the keyboard seems to be enough for me (I don't need to press the button on the bluetooth stick).

An alternative solution would be to put grub on an usb stick, and set windows as the first boot option. Like that, you would just have to make sure the stick is inserted when you want to boot to windows (if you set the boot priority of usb higher than that of the hard drive).

I tried to create a usb stick with grub on it using the following howto:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive).

It failed, when I boot from it I just get a black screen.

---

### Post by Shlomir on 2008-02-14
Im in the same boat as many of you and would really love a hack for this!

Right now I am typing away with my Logitech MX5000 Bluetooth keyboard, but when I reboot my dualbooted with machine grub looses the Bluetooth connection and I need a bloomin PS2 keyboard to ghetto-style boot into XP or Gutsy..

When I reboot and press the bluetooth button, it says 'trying to connect', and doesn'[t connect in Grub where it defaults to Ubuntu, and then eventually mnakes it's connection to Ubuntu...

But like many other i would like to chuck out my PS2/UBB wired deviced AND have dual-boot with Grub AND have my Bluetooth kB/mouse work as well!!

COME ON UBUNTU AND LINUX DIE-HARDS PROVE IT CAN BE DONE!  I CAN'T DO IT COZ I'M A LAMERZ H4X0RS BUT I KNOW THE 7EETS CAN DO IT!

OH, AND THANKS IF YOU DO! :guitar:

---

