---
title: "Are there any 'tricks' for graphics problems with specific apps?"
date: 2018-10-29
forum: Wine
---

### Post by treii28 on 2018-10-29
I'm trying to run a small development app for a rather specific voice-recognition embedded device (Veeer EasyVR) and it has a helper program to help you program the chip on the device. When run in windows, certain functions such as the program and test buttons will pop up a small widget box with the status such as "speak command now" for the test feature. Upon a successful test (in regular windows) it will then flash cyan color as the background under the voice-trigger it recognized so you can know it worked properly.

I was able to get the software itself installed and working under wine complete with connecting to the device over the com port. But whenever I click the 'program' or 'test', the little pop-over box that comes up is blank with transparency right around the outer border. (this doesn't bother me so much as I already know what the dialogues say). Then if doing a test, after a successful test, there is no colored flash under the voice command that was detected. This is something that I need to make sure the commands are triggering properly.

Before I give up on using it in wine, are there any tricks that might get the graphics working properly or any known issues with rendering some types of pop-overs and text background colors that I might find fixes for?  I'd really prefer to do my development in linux if I could as my machine runs a lot faster than it does in bloated Windows 10 home.

I don't know if it's pertinent, but the graphics card is a Radeon 6750m.  I have tried installing/running the program in both wine64 and with the arch set to wine32 with a separate ~/.wine32 prefix. Same results in both.

SW

---

### Post by treii28 on 2018-10-30
as an aside, I got the program to work in a windows 7 virtual box with access to /dev/ttyUSB0 as com1. but I would still be curious about any suggestions for using wine.

I was able to learn from the developers of the helper program that it was built with Windows Template Library v9.1

---

