---
title: "Graphics Card Problems-can't log in."
date: 2009-10-17
forum: x86 64-bit Users
---

### Post by That_Guy_Smells on 2009-10-17
Hi Guys,
I really love what I have seen of Ubuntu, however I have recently come across a problem and now I cant even log in.
I have a Dell Studio XPS 435MT (Intel Core i7, 6GB Tri-Channel DDR3 RAM, 640GB HDD, ATI Radeon HD 4850-Slightly Overclocked using ATI's software) with Ubuntu 9.04 64-Bit and Windows Vista Home Premium dual-booted.
Ubuntu has been running fine until I decided I wanted to enable special effects.
I got the error "Desktop Effects could not be enabled". I googled and eventually decided it was my graphic drivers.
I tried installing the latest *nix drivers from ATI's site but they didn't install for some reason.
So I found a menu somewhere (I can't remember where it was) which had some "Propriety Drivers" (or something like that). The only selection there was an ATI one, so I clicked enable. It did some stuff for a while and eventually I got another error saying it wasn't enabled.
Next time I rebooted I got a load of static on my screen after seeing the Ubuntu progress bar.
This happens every time I try and boot up Ubuntu now and the only way to get rid of it is to pull the power cord out.
I have tried going into recovery mode and ran most of the options to no avail.
I have uploaded a video to YouTube showing the screen from switching on until the static appears ([http://www.youtube.com/watch?v=ko126IURCfs](http://www.youtube.com/watch?v=ko126IURCfs)).
If someone could help me please it would be greatly appreciated as I'm stuck with Vista for the time being.
Thanks in advance.
TGS

---

### Post by Yellow Pasque on 2009-10-17
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by That_Guy_Smells on 2009-10-17
Thanks alot, I'll give it a go now and post the results soon-I assume I use the root terminal in recovery mode?
I can't remember ever installing fglrx but I'll follow these steps anyway.
Cheers

---

### Post by That_Guy_Smells on 2009-10-17
Thanks [Temüjin]("http://ubuntuforums.org/member.php?u=327594")!
I ran the first three commands in the root terminal:
```

  sudo /usr/share/ati/fglrx-uninstall.sh  # (which didn't work)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 

```And I am replying from my Ubuntu system!!=D>
Thanks so much-marking the topic as solved

---

