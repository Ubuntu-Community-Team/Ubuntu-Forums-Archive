---
title: "a few more questions..."
date: 2006-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by iamdigitalman on 2006-05-30
hello again. I finally got breezy running after I fixed the date. now I have a few more questions:

-my USB white Pro mouse keep jumping around the screen. I am having such a hard time controling it, i went back to my old ADB mouse. I tried adjusing the sensitivity in the mouse control panel, but that isnt working. any help here? I would like to use it, as it's more precise.

-I cant seem to right click. both the USB and ADB mice are single button. Under mac OS 9, I used contextual menus and the control key.

-I cant play flash movies, under the web browser or anything. I got the version of flash player for PPC, but the installer runs, then exits. what is wrong?

-I cant seem to access the IDE zip drive. I insert a disk, and under the file browser, I click the icon for the zip drive (it detects the drive fine), but I get an error dialog saying the givin UDI is not a mountable device.

-the same goes for floppy disks in my USB floppy dirve. I can format them fine, but even if they are formatted ext2, they will not mount.

-same for my iPod. I have it connected over firewire, but it wont mout, even under gtkpod. there isnt even a icon for it under the computer folder.

-my DSL modem has a USB port to connect it to the computer, and you can connect to the net over the USB port. there was a driver for Windows and Mac OS 9, but I cant find one for linux. I am using the RJ-45, but there is another computer that usually connects to that, so I would like to keep it free.

thanks. -digital ;)

---

### Post by zhoux on 2006-05-30
ok i can't solve all of the problems, but i may help you w/ the mouse problems.

It seems your jumpy mouse is the cause of wrong resolution. So you need to edit the xorg.conf file:

back up the xorg.conf file first, it is located in /etc/X11/xorg.conf

Then sudo gedit /etc/X11/xorg.conf

Then scroll down toward the bottom/middle part, there is a section labeled "Inputdevice", Identifer = "configured mouse".

Add:

Option   "Resolution"     "100"
with quotes, and 100 is up to you to decide.

Also to fix the single button mouse problem, i THINK you should change the protocol to something like "ExplorerPS/2" 

The protocol is located in the same section as the resolution.
I'm not sure if this is the right way to fix the single click mouse problem, because i don't use mac, but it is worth a try.

Hopefully that helps.

---

### Post by linear on 2006-05-31
Can't help with the rest, but use F12 for right-click.
 
Oh, and AFAIK, there is no Flash player for Linux-PPC.

---

### Post by iamdigitalman on 2006-05-31
[QUOTE=linear]Can't help with the rest, but use F12 for right-click.
 
Oh, and AFAIK, there is no Flash player for Linux-PPC.[/QUOTE]

THANK YOU THANK YOU THANK YOU!!

F12 forks excelent. a bit quirky, as I am used to pressing control, but whatever. I sould probibly get a 2 button mouse, but this works fine for now.

and as for the mouse quirkyness, it appears to have disspaeared for some reason, but if it comes back, I will try the fix in the first reply.

and now to a new question: any way to get the clock in the panel to display metric time? yes, I am one of the rare folks who uses metric time.

thanks. -digital ;)

---

### Post by Uta on 2006-05-31
I find it interesting that you installed a Flash plugin for PPC? Really, we've all been waiting for one. Here is a petition to get Macromedia/Adobe to do their job.
[http://www.petitiononline.com/fla4lppc/petition.html](http://www.petitiononline.com/fla4lppc/petition.html)

---

### Post by Uta on 2006-05-31
I find it interesting that you installed a Flash plugin for PPC? Really, we've all been waiting for one. Request it from Adobe/Macromedia
[http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform](http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform)

---

### Post by iamdigitalman on 2006-05-31
I had a flash pluging for PPC back when I used Mac OS 9. it used Flash 7, so the sites that use version 8, which seem to be more and more each day wouldnt work.

so, why hasnt Adobe put one out for Linux on PPC? they have one for linux on i686. have they never heard of Ubuntu PPc or Debain PPc or LinuxPPC?

or, they could just release the source of the x86 version, and let us grep heads figure out the rest.

-digital ;)

---

### Post by Uta on 2006-05-31
[http://www.petitiononline.com/fla4lppc/](http://www.petitiononline.com/fla4lppc/)
A place to register the unfairness of it all--

---

### Post by linear on 2006-05-31
[quote=iamdigitalman]any way to get the clock in the panel to display metric time?[/quote]
Right-click (now that you can do it) on the clock; choose preferences.

---

### Post by iamdigitalman on 2006-05-31
ok, my options are 12 hour, 24 hour, Unix Time, and INternet Time (WTF are these last two?! ) no metric time listed.

thanks. -digital ;)

---

### Post by linear on 2006-05-31
Sorry, didn't realize at first what you were asking for.

---

### Post by iamdigitalman on 2006-06-01
[QUOTE=linear]Sorry, didn't realize at first what you were asking for.[/QUOTE]

no problem.

so as an update, here are the issues I am having:

-cant play flash movies
-cant access IDE zip drive
-can format, but not access USB floppy drive
-cant mount or talk to my iPod. note I searched the forums, but everybody is either using a shuffle model, or is using a USB cable. I am using a 6 pin firewire cable hooked to my built in firewire bus.
-cant get DSL modem to connect over USB.
-cant get panel clock to disply metric time.

see the starter post for full details.

thanks. -digital ;)

---

### Post by iamdigitalman on 2006-06-02
ok, screw the USB port on the 2wire modem. just got a new one (has been en route for days now), and it doesnt have one. but it does have 4 RJ-45's and built in wifi. guess I'll use the old USB cable to work this cheap old webcam I have.

everything else it still a mystery.

-digital ;)

---

