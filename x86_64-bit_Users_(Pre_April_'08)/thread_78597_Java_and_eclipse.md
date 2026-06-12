---
title: "Java and eclipse?"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by sulobanks on 2005-10-18
I noticed eclipse packages when I installed 5.10.  I thought that would be a really cool idea.  But it wasn't.  Installed eclipse and synaptic listed several dependencies, which I accepted.  When everything was installed, I tried to run eclipse and got errors.  Basically, had /usr/local/lib/eclipse/plugins instead of just /usr/lib... Tried a symlink. Then on the next launch, it told me it couldn't install plugins.  At no time have I seen a splash screen or a window of any sort opening. I only get a log file generated with this error information.

I guess my first question is has anyone gotten the ubuntu eclipse package to work? If so, how?

---

### Post by bronson on 2005-10-18
I did get Eclipse to work.  I only had to do one strange thing:

"sudo chmod a+w /usr/local/lib/eclipse"

Of course, that's a bad idea unless you're the only person that ever uses your machine.

Small problem: now I get an error when I choose "Help Contents" from the Help menu: "The file /usr/share/eclipse/debian/help.htm cannot be found. Please check the location and try again."

It would appear that Eclipse on Ubuntu just isn't in very good shape.

---

### Post by sulobanks on 2005-10-18
I'll have to go look up that howto that helped me get it working in hoary.  IBM java and someone's homemade compilation of eclipse for ppc.  It'll do until ubuntu gets this figured out. Surely they'll get it right in the first couple waves of updates?

---

### Post by astroboysoup on 2005-10-18
I finally got Eclipse working on my iBook g3 500 dual usb after a week of tinkering with it.

I had to install the IBM SDK and manually download the latest version of Eclipse for the ppc.

The main problems that I came across were permission problems. I only figured out after studying the error log files carefully and realised that the program was trying to access the plugins but couldn't.

a simple sudo infront the load command got it up and running just fine. I haven't done much testing but i have compiled and ran a few programs and it works fine.

Hit me up if you need any help.

---

### Post by cow_racer on 2005-10-23
[QUOTE=astroboysoup]I finally got Eclipse working on my iBook g3 500 dual usb after a week of tinkering with it.

I had to install the IBM SDK and manually download the latest version of Eclipse for the ppc.

The main problems that I came across were permission problems. I only figured out after studying the error log files carefully and realised that the program was trying to access the plugins but couldn't.

a simple sudo infront the load command got it up and running just fine. I haven't done much testing but i have compiled and ran a few programs and it works fine.

Hit me up if you need any help.[/QUOTE]


Is Eclipse usable under a 500 Mhz g3?

---

