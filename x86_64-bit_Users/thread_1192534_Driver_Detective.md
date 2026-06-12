---
title: "Driver Detective ???"
date: 2009-06-20
forum: x86 64-bit Users
---

### Post by Spaceman7o on 2009-06-20
Audio driver wont work or something .. i get video but not sound my vista works fine its just this i need help ive did the lspci code and this is what comes up i use an Advent pc if that helps?.

 00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LF-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

---

### Post by jerrrys on 2009-06-20
if this is a new install you need to download:

flash
gstreamer
restricted extras

all can be found in Synaptic Package Manager

---

### Post by Spaceman7o on 2009-06-20
Dude ive did this but cant fiond flash and when gstreamer is found is comes up restricted extras anyway what now after i install that?

---

### Post by jerrrys on 2009-06-20
there is more than one way to download flash

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=c8L&num=30&newwindow=1&ei=L-s8Sp3mLqC-NJLwrKUO&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=adobe+flash+ubuntu&spell=1](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=c8L&num=30&newwindow=1&ei=L-s8Sp3mLqC-NJLwrKUO&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=adobe+flash+ubuntu&spell=1)

---

### Post by Spaceman7o on 2009-06-20
Dude isnt flash for videos because if it is its the audio i need help with?

---

### Post by jerrrys on 2009-06-20
put it this way...this is how i got 804 to work for me...i also installed this

[http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback)

and on one last note. i found VLC media player to be a better choice for me than the default player.

thats all i got to offer you.   good luck

---

### Post by Spaceman7o on 2009-06-20
ok thankyou but it dosent seem to be working oh well thanks for your time.

---

### Post by philinux on 2009-06-20
Go into system>prefs>sound.

Try changing the settings to pulse sound server, instead of autodetect, and check with the test button.

---

### Post by Spaceman7o on 2009-06-20
nope didnt work with any of them :(

---

### Post by Spaceman7o on 2009-06-20
its working and here was my solution Here's the upshot:

2. Configure libao applications to use PulseAudio:
Code:

$ echo "default_driver=pulse" >~/.libao

3. Perform the following steps to remove obsolete configuration files, ensure "libflashsupport" is not installed & you have the all the necessary packages up-to-date:
Code:

$ rm -r ~/.pulse ~/.asoundrc*
$ sudo apt-get update && sudo apt-get dist-upgrade
$ sudo apt-get remove libflashsupport
$ sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio

NOTE: Choose Yes to allow unsigned packages to be installed.

4. Go to System/Preferences/Sound. Set all "Sound playback" options to "Autodetect", and set "Sound capture" to "ALSA".

5. Reboot for changes to take effect!

---

