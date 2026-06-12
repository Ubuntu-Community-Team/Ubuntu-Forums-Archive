---
title: "Last 5 problems with my Acer Aspire Laptop ..pls help"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by tarekeldeeb on 2007-11-04
Hello all ..:popcorn:

I'd like to join the celebration of the new Gutsy ..

I have installed it on my Acer Aspire 5050/5051 laptop 2 weeks ago .. and I almost switched from windows .. this is the first edition that is really a competitor to Billy ..

I managed to do many things successfully guided by many threads in this forum:
- Install the driver needed for my ATI card
- Install the Wifi Driver (broadcom 43xx)
- Wine
- VMware workstation (having windows XP for special SW)
- Bluetooth works perfect
- Firefox32 with flash 9 with sound 
- Conduit for syncing my data
- All needed codecs
- All eye-candy stuff (compiz and so ..)

I'm very happy for my status .. but I have 5 last problems which i wish to solve

1- I boot without the loading screen (I modified a file to use: nosplash) .. I wish to have the splash working again
2- No screensaver .. after timeout , the screen just fades for 1 sec and returns back .. when I select screensaver preview in full screen it works .. but it does not show ofter the 1-min timeout
3- I still have no drivers for the 5-in-1 ENE card reader !
4- I still have no driver for the built-in Orbicam webcam, when i type lsusb it gives : Bus 003 Device 002: ID 0c45:6260 Microdia 
5- Laptop does not hibernate nor suspend to Ram (sleep) .. i read many threads .. but did not find useful info or successful stories !

Can any1 help me with these 5 ?

Thanks in advance,
Tarek:)

---

### Post by jointstereotype on 2007-11-04
> 3- I still have no drivers for the 5-in-1 ENE card reader !
4- I still have no driver for the built-in Orbicam webcam, when i type lsusb it gives : Bus 003 Device 002: ID 0c45:6260 Microdia

I also have an Acer laptop, and FYI the ENE drivers included with Gutsy are buggy at the moment. I've found that 256mb SD cards, for example, work fine, but 2gb ones do not. I've been told the drivers will improve with time, perhaps in another Ubuntu release or two.

As for the Orbicam, I have yet to come across a post where someone got it working. So...sorry I couldn't be more helpful. LOL If you do figure out the secret, please post it! ;)

---

### Post by trjepp on 2007-11-05
I have the same laptop, and have made much of the same progress that you have, but i would like to add one more problem to your list. 

6.Battery meter always shows that i am connected to ac power. When the battery actually does run out, the computer simply shuts off, corrupting all manor of important files

also, i'd love to know how you got the bluetooth working.

---

### Post by azwar on 2007-11-05
I've just installed a fresh gutsy 32 bits on my acer 5052 (AMD turion 64x2 = 2.2 GHz, 1 Gb RAM, Ati Xpress 1100, 80 gb HDD), Atheros Ar5007eg...

My problems are : 

1. wifi still not work even after i've installed with ndiswrapper

2. long time to boot up (take up near to 5-7  minutes). I never faces this problems with Feasty Fawn. i also configure the startup process to make it fast (gnome-session-properties) but still no changes. 

3. ATi driver show error on 'composite extension" when try to enable desktop effect. i've enable all restricted repositories, installed the driver but still no changes. when i use feisty on my desktop (p4 2.4 GHz, 1.25 Gb RAM, ATi radeon 9250) its fine. Is there any different how the driver works both on laptop and my desktop.

please help me lah...

---

### Post by tarekeldeeb on 2007-11-05
> **trjepp said:**
> I have the same laptop, and have made much of the same progress that you have, but i would like to add one more problem to your list. 

6.Battery meter always shows that i am connected to ac power. When the battery actually does run out, the computer simply shuts off, corrupting all manor of important files

also, i'd love to know how you got the bluetooth working.

I really dont have the battery meter problem ..

The BT issue .. what is your status ? .. when u turn the BT on, do u get the Bluetooth Applet/manager icon beside the clock ? if not try to install <using synaptic> a package: Bluez-Gnome

If yes .. goto preferences make your laptop discoverable .. make pairing/bonding with ur mobile device .. then whenever you want to copy files .. just right-click the BT icon >> Browse Devices >> wait till ur device appears >> connect

You can then browse your files .. copy from/to it ..:lolflag:

---

### Post by brawa on 2007-11-08
For either making your boot time faster if you have splash enabled, or keeping boot fast while re-enabling splash, try this:

[http://geekybits.blogspot.com/2007/11/fix-for-no-splash-in-ubuntu-710.html](http://geekybits.blogspot.com/2007/11/fix-for-no-splash-in-ubuntu-710.html)

I had the following problems with my acer aspire that this fixed:
1) Black boot screen, slow boot.
2) Changed to nosplash--fast but no spash
3) This fixed it! Read the directions somewhere else on these forums, but couldn't remember where so a quick search brought this blog link. Sorry I can't give proper credit to whoever posted the thread I read :(

---

### Post by xdudor on 2007-11-11
> **trjepp said:**
> 

6.Battery meter always shows that i am connected to ac power. When the battery actually does run out, the computer simply shuts off, corrupting all manor of important files



yeah that is what i feel, after a long journey of seeking the solution i simply conclusing that the battery was not supported by ubuntu any idea??:(

---

### Post by Tig3rzhark on 2007-11-13
I heard that your bluetooth works fine for gutsy.  I have trouble trying to get bluetooth to work for my Acer Aspire 5100.  Could you tell me how can I get my laptop to recognize my Nokia 2865i and my headset?

---

### Post by tarekeldeeb on 2007-11-13
> **Tig3rzhark said:**
> I heard that your bluetooth works fine for gutsy.  I have trouble trying to get bluetooth to work for my Acer Aspire 5100.  Could you tell me how can I get my laptop to recognize my Nokia 2865i and my headset?

- let your laptop be findable
- search from your phone, your laptop is found
- request pairing from phone .. write ur password
- request is sent to laptop .. rewrite the password

now: whenever u want to connect to ur phone, right-click on the BT icon beside the clock,then "Browse Devices" .. your phone will be listed >> connect !

---

### Post by absolut1983 on 2007-12-10
Hi, folks.

   I bought an Acer Aspire 5051 a couple of weeks ago and, with a little help from the forum users, I managed to get a decent boot, Compiz enabled and working perfectly and the sound.

  Unfortunately I haven't found any complete info about the Bluetooth or the wifi.

   Switching the BT on, I get no reaction at all from the system. Same with the wifi, cause Gutsy just doesn't recognize the device.

   I'm also having some minor problems with the headphone jack and the built in mic, but this is far less important than the BT and the wifi.

   Did anyone manage to solve those issues?

   Thanks in advance.

---

