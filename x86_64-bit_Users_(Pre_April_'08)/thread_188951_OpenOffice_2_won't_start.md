---
title: "OpenOffice 2 won't start"
date: 2006-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by sanketmedhi on 2006-06-04
Hello fellas,

I am facing a big problem with OpenOffice 2 here. I just upgraded to Dapper 6.06 LTS and I cannot get OpenOffice working at all! Here is the jargon it generates when I run the *openoffice* command at the command line...

[http://pastebin.com/758342]("http://pastebin.com/758342")

I have tried reinstalling OpenOffice and libgail several times with no luck. Please help! :( 

I am using AMD64 2800, Nvidia 5200+, 512 RAM.

---

### Post by Jiilik on 2006-06-04
Try installing the package ia32-libs-gtk

---

### Post by andabo on 2006-06-05
Same problem here. I created a bug report. Look at:

[https://launchpad.net/distros/ubuntu/+bug/48503]("https://launchpad.net/distros/ubuntu/+bug/48503")

---

### Post by cosine7 on 2006-06-05
I am having the same issue...
AMD64 3200 Dapper 6.06 x386 version....

---

### Post by andabo on 2006-06-05
I've found the solution:

To disable the lines, that appear, when minimizing a window, I checked the reduced_resources flag in gconf and enabled the "System/Preferences/Assistive Technology Support". This seems not to work with openoffice. So I disabled the second option again, and now it works without a problem...

---

### Post by sanketmedhi on 2006-06-05
Umm...would you mind telling us where to find the reduced_resources flag in gconf? :-k

---

### Post by sanketmedhi on 2006-06-06
The problem solved on its own. You can try uninstalling all Openoffice packages in Synaptic and then selecting Openoffice.org2 package which installs the whole suite. It worked for me. Give it a try.

---

### Post by cosine7 on 2006-06-06
Yeah, odd, i did some other stuff, rebooted a cpl of times and it started working...

---

