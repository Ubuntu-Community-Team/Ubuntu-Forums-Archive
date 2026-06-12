---
title: "Can't install kubuntu-desktop"
date: 2006-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by JAPrufrock on 2006-12-17
Just got a new box with an AMD64 sempron, and installed Ubuntu Dapper on it.  However, I can't seem to install the kubuntu-desktop. I've tried both synaptic and apt-get with different sources.list./s. All the common repositories are there. Anyone know which repository contains the kubuntu-desktop package?

sorry, device manager lists the cpu as an Athlon64/Opteron

---

### Post by Travisty on 2006-12-17
The kubuntu-desktop should be available with out messing with your sources. 

I attached the original sources with the extra repos uncommented. Backup your current list and replace it with this. Do and apt-get update, then sudo apt-get install kubuntu-desktop.

---

### Post by JAPrufrock on 2006-12-17
Thanks for the sources.list - I will use it.  I found out what was wrong- my sources.list was automatically generated using a server in Costa Rican as a mirror (probably the University of Costa Rica), and for some reason a lot of the URLs weren't functional, including the binary-amd64 ones. So in the deb urls in sources.list I changed the references from "cr" (Costa Rica) to "us" (United States) and I was able to get Synaptic to load the kubuntu-desktop. However, I will get rid of my sources.list now, because I still get 15-20 error messages when I update, and I'll use the one that you attached to your message.  Thanks!

---

### Post by Travisty on 2006-12-17
You're welcome. Glad to help!

---

