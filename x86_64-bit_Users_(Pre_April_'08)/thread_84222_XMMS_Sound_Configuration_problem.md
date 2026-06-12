---
title: "XMMS Sound Configuration problem"
date: 2005-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cihan on 2005-10-30
when i try to play any mp3 or wma there is a error code:
Your sound card is configured properly.you have the correct output plugin selected etc..
but at the second or third trying then it works.
what can i do?

---

### Post by bootleg on 2005-10-30
Did you change the output plugin?

I have a german Ubuntu, but in English I guess it has to be options -> preferences -> Audio i/o plugins, I use the Alsa Output plugin

I generally use the alsa plugin in Ubuntu.

---

### Post by Cihan on 2005-10-30
I changed the output plugin.I using the alsa now.

it worked.

thanks

---

### Post by keisashankara on 2005-11-12
Incase anyone has similiar trouble. I could not get Alsa to work with Breezy but was working with hoary. 

I tried sudo dpkg-reconfigure alsa-base but to no success. 

Then looking at my ASUS mainboard model a7v I noticed that the 4th and 5th pci bus was shared. (the card was in the 5th bus)

I moved the sound card to PCI bus slot 3 and it worked (this is more probally a pci detection problem then a sound problem, all in all it just frustrates). 

Also the card did not appear in a lspci until it was moved to the third bus. 

Yet it still worked in the 5th position under hoary

---

