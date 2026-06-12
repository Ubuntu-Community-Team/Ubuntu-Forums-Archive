---
title: "ARRL TQSL and WINE"
date: 2015-05-29
forum: Wine
---

### Post by tm-hart on 2015-05-29
TQSL and WINE on Ubuntu

After registering on the  ARRL's Logbook of the World, I needed the TQSL utility to process records.  
Unfortunately, the ARRL does not offer a Linux version of TQSL, a program that signs and uploads data.  My solution was to use WINE to install and run the latest Windows version of TQSL (currently v. 2.0.3) on 64-bit Ubuntu (currently ver. 15.04).   To date, I have successfully uploaded over 48,000 records without a problem.

The Synaptic Package Manager provided the following WINE components: 
wine1:1.7, winetricks, wine-gecko 2.34, wine-gecko 2.21, wine mono 4.5.4, wine mono 0.0.8, wine 1.7, wine 1.7-dev, wine 1.4-amd64, wine 1.7-amd64, wine-gecko 2.21 i386 and wine-gecko 2.34i386.

After using “wine control” to install Windows TQSL, an icon appeared on my desktop.  Click the icon to start the program and open its menu:  

- Log Operations
	Sign a file
	Sign and upload a file
	Create ADIF file
	Log into LoTW
- Station Location
	Create
	Edit
	Delete
	Display
- Callsign Certificates.
	Load
	Save
	Renew
	Display

Windows TQSL works on Ubuntu under WINE; this has saved me from finding and compiling the source code to run a Linux version of the program.

---

