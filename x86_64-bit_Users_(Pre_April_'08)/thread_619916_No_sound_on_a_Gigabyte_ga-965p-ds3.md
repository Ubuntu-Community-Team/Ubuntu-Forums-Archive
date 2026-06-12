---
title: "No sound on a Gigabyte ga-965p-ds3"
date: 2007-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by wootwoot123 on 2007-11-22
This is my first time installing the amd64 build and I have no sound with this release. I have sound in windows and with other builds of ubuntu but anything that makes sound gives me nothing. Any suggestions on what to check?

---

### Post by Toffeeapple on 2007-11-22
Are you using Gutsy 7.10... I have the same board and the onboard sound works without any tinkering on 7.10.. I'm assuming you are talking about the onboard sound.. is it turned on in BIOS?

Right click on the speaker icon top right of your desktop and experiment from there.. also System/Preferences/Sound.. whats going on in there?

..and not wanting to sound too condescending or anything but are your speakers plugged into the correct sockets on the back? are they turned on?

what program are you trying to get sound out off? something within the settings there maybe....

: )

---

### Post by wootwoot123 on 2007-11-22
Nothing is wrong with the speakers, they were working just fine in XP before installing gutsy. I had no startup sound and going under the sound properties and running the test I hear no sound. I checked the kernel config and the intel HDA 888 was not checked off. From what I understand the audio chipset is the 888 on this board so I am unsure why it was turned off. Anyways I turned it on and compiled a new kernel but still nothing.

---

