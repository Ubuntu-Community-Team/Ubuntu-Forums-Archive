---
title: "ibook G4 running Dagger"
date: 2006-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by wytygr on 2006-04-21
I installed Dagger on the ibook G4, and everything works great except for an external monitor. I have searched and found some sample configs that should work but they do not. IT has the ATI 9550 and will not work on my external display. Any ideas? Thanks

---

### Post by hentaidan on 2006-04-21
Its Dapper :)

My external LCD display works fine (iBook G4, Radeon 9550), but you have to reboot with the screen attached else it wont be detected.

All I did was edit xorg.conf (see [http://yet-to.be/wordpress/2006/03/18/ibook-g4-radeon-9550-mirroring-on-ubuntu/](http://yet-to.be/wordpress/2006/03/18/ibook-g4-radeon-9550-mirroring-on-ubuntu/) )

Dan

---

### Post by wytygr on 2006-04-23
I tried that but it still does not work. I am using a CRT monitor with the ibbok supplied adapter for an external monitor. It just breaks X and will not start. I have to cp my old configu back to get it to work. I want to be able to use it like I was an osx, where the main desktop is my external monitor and the LCD on the ibbok itself is the extra space.That is the only thing keeping me from fully switching over to linux on the ibook. I run Centos on my main desktop and miss having linux on the ibook. Screw intel, I have no desire to use one of those laptops. Also, I need to be able or would like to playback DVD's. If I could do this, I would switch ove rin a heartbeat.

Thanks!

---

### Post by hentaidan on 2006-04-23
[QUOTE=wytygr]It just breaks X and will not start.[/QUOTE]

Do you get any error messages?

---

### Post by wytygr on 2006-04-23
No, it complains a little about the keyboard, but other than that, the logs don't say much. Unfortunately, I am back on OSX until I can figure out why it is doing what it is. Especially since the ibook can only do 1024x768.:(

---

### Post by wytygr on 2006-04-25
Here is the error that I am getting:

Parse error on line 73 of section Device in file /etc/X11/xorg.conf
        The Option keyword requires 1 or 2 quoted strings to follow it.
Parse error on line 73 of section Device in file /etc/X11/xorg.conf
        "“true”" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor

---

### Post by Audiophiliac on 2006-04-26
Just when I thought I've seen a perfect Ibook G4 install posted, comes a few more problems. Does this mean aside form no dvd and external monitor, lan, modem, and wifi works?

I just installed Tiger and loving it. I am wondering why we go through so much pain to get Linux working on an otherwise perfect machine.

---

### Post by hentaidan on 2006-04-26
[QUOTE=wytygr]Here is the error that I am getting:

Parse error on line 73 of section Device in file /etc/X11/xorg.conf
        The Option keyword requires 1 or 2 quoted strings to follow it.
Parse error on line 73 of section Device in file /etc/X11/xorg.conf
        "“true”" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor[/QUOTE]

Can you post your xorg.conf? Looks like your missing a keyword somewhere.

---

### Post by hentaidan on 2006-04-26
[QUOTE=Audiophiliac]Just when I thought I've seen a perfect Ibook G4 install posted, comes a few more problems. Does this mean aside form no dvd and external monitor, lan, modem, and wifi works?[/QUOTE]
I have DVD, mirror/clone monitor, ethernet working fine. Modem I cant test, and wireless would work if my network wasnt WPA.

[QUOTE=Audiophiliac]I just installed Tiger and loving it. I am wondering why we go through so much pain to get Linux working on an otherwise perfect machine.[/QUOTE]
I hate Tiger, and cant wait to get it off my iBook :twisted: IMHO its not perfect, far from it. But if you think Tiger is perfect why are you going "through so much pain to get Linux working"?

---

### Post by Audiophiliac on 2006-04-26
I've stopped. I cannot evaluate an os when most things don't work. That is why I browse the forums to see if anyone has made everything work with the least amount of pain. The way i see it, there is a long way to go. But I will visit from time to time.

---

### Post by jdp on 2006-04-26
[QUOTE=hentaidan]I hate Tiger, and cant wait to get it off my iBook :twisted: IMHO its not perfect, far from it. But if you think Tiger is perfect why are you going "through so much pain to get Linux working"?[/QUOTE]

I think the perfect might have been meant for the machine, not the OS.

---

### Post by seatea on 2006-04-27
hentaidan,

Your comment about  dvd playback got my attention. After weeks of failed attempts at getting dvd to run on my PM G4 400, ATI 128 Rage Pro graphics card, I was able to get xine to play dvds, but only with XShm. Using Xv causes problems with the colors on my  screen and does not play video. My playback with XShm is not good and I have pretty much given up on dvd playback for now. Maybe your  ibook has a different  graphics  card, but I would be interested in how you  were able to get dvd playback on your sytem.

---

### Post by prometoys on 2006-04-28
Hi,

with this config my X work dual headed with extended desktop:

[http://www.prometoys.net/downloads/xorg.conf.dual](http://www.prometoys.net/downloads/xorg.conf.dual)

Make a backup of your xorg.conf and rename my conf in (suprise) xorg.conf

You must plugin the external display and restart X.

If you have questions, write me a mail (me@prometoys.net), I didn't read forums much.

---

### Post by prometoys on 2006-04-28
audiophillac:

this works not: modem, tv out, 3d (there are rumours, it should work know, but I didn't configure it yet)

this works, but should be improved: wlan, external display (add/remove without logout), suspend (usb-touchpad sometimes missed to wake up)

everything else works perfect

---

### Post by Audiophiliac on 2006-04-28
Thanks for the replies. I will just have to wait until a single install cd will make everything work.

---

### Post by hentaidan on 2006-04-28
[QUOTE=seatea]but I would be interested in how you  were able to get dvd playback on your sytem.[/QUOTE]

Using an iBook G4, Radeon 9550, Ubuntu Dapper and VLC. I dont remember doing anything special, AFAIK, it should work out of the box.

---

### Post by seatea on 2006-04-28
Thanks for the  information. I guess the Radeon card drivers offer more functionality with Ubuntu at this point.

---

### Post by blue_chili on 2006-09-14
Have a look at my xorg.conf, although my external monitor is different to yours it may work. I commented out the refresh rates for my external monitor but left in the ones for the ibook LCD (I've got an iBook G4 12" 800MHZ). Note that for my external monitor I just put in the one mode of 1280x1024. You may need to change or add in others.

[http://www.ubuntuforums.org/showpost.php?p=1497267&postcount=279](http://www.ubuntuforums.org/showpost.php?p=1497267&postcount=279)

---

