---
title: "Unable to launch SDRUno under WINE &amp; have it remain open to use RSP1A Rx"
date: 2020-10-01
forum: Wine
---

### Post by ccor58 on 2020-10-01
I am running ubuntu Studio 20.04LTS with wine / winetricks installed and installed SDRUno under wine. 32 GB RAM and 64 bit cpu. When I launch SDRUno from the created desktop link it can take up to 3-5 minutes for the windows to all open, which they do, then immediately they all close. It does not stay open. There is no specific log file for wine to use the tail -f command to see what is occurring and why it shuts down immediately. I am using an RSP1A USB SDR receiver and when I do an lsusb listing it shows up as detected but has no mfr's detail just the address block  ( Bus 001 Device 010: ID 1df7:3000  ). There is an initial splashscreen that says the program does not detect the RSP1A device yet it is showing in the lsusb listing as an active device. None of the other native linux SDR programs work with the RSP1A ie Cubic SDR, Limesuite, CuteSDR etc as they do not detect the device either. SDRUno installs the windows device driver under wine but appears not to use it as designed.

Any help or tips are appreciated. 

SDRUno and SDR Spectrum Analyzer s/w programs appear to install properly under wine but meither will stay open running normally; they launch all the associated windows mormally then immediately close all simultaneously.

thanx , 73 & Gud DX

---

### Post by CelticWarrior on 2020-10-01
[https://www.sdrplay.com/docs/SDRunoUnderLinuxGuide.pdf](https://www.sdrplay.com/docs/SDRunoUnderLinuxGuide.pdf)

---

### Post by ccor58 on 2020-10-01
followed guide as provided on the link and changed xenial spec to focal for 20.04LTS I experienced a few class errors during the installs but now can launchMain EXTIO window and it stays opened. Click play and there is static and ac hum evident but no indication what it is from. subsequently launch SDR Uno with EXT IO started and it does as it did before waits to open all windows for control and waterfall monitoring and as soon as the last one opens they all close; except the EXT IO main window. still indicates no device while lsusb shows one.

---

