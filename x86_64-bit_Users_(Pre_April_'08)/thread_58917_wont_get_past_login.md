---
title: "wont get past login"
date: 2005-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by marshall_symons on 2005-08-22
i put together a computer a month or so back. now i have two. the new one is the amd64[marshall82]and the old is a p3[marshall77].

i was using the synaptic thing on marshall77 and i pushed smart update. at this point it says it needs like a 1000 packages, it goes on for a while and has some errors and cant finish doing its upgrading, i take little notice and continue using it for web browsing etc for a few days.

 today i got a second monitor so i could use both at the same time. i on acciedntly unpluged marshall77  while it was running while i was installing the new computer, when it came back on it wont let me get past the login screen unless i got to the terminal style login. then it works,but is like all terminal style and dosent show the desk top stuff.  

is there a way i can transfer stuff off  marshall77 to marshall82 so i can reinstall a clean install on marshall77?

 i have a router. they are both online thru it. 

i really dont know much about computers. i have aim. maybe some one can hit me up and let me know? sn:marshallsymons


on a side note does anyone have myspace? check me and my girl out myspace.com/marshallsymons

---

### Post by DancingSun on 2005-08-22
Some rough directions:
[list=1]
[*]Take the hard disk drive out of marshall77 and put in in marshall82, (assuming you have the old IDE HDD interface) connect it as a slave drive if you are connecting to the IDE controller1, otherwise connect it to the secondary IDE controller.
[*]Boot into Ubuntu in marshall82, mount the secondary HDD (marshall77's HDD).
[*]Copy the files from marshal77's HDD to marshall82's HDD.
[*]Unmount the secondary HDD.
[*]Shutdown marshall82, and move marshall77's HDD back to marshall77.
[/list] 

While I could answer questions that you may have about connecting the HDD, I'm new to Linux so I wouldn't know how to mount the HDD on top of my head, but I remember looking up some posts about mounting secondary HDDs in these forums, you could try the same.

---

### Post by marshall_symons on 2005-08-22
[QUOTE=DancingSun]Some rough directions:
[list=1]
[*]Take the hard disk drive out of marshall77 and put in in marshall82, (assuming you have the old IDE HDD interface) connect it as a slave drive if you are connecting to the IDE controller1, otherwise connect it to the secondary IDE controller.
[*]Boot into Ubuntu in marshall82, mount the secondary HDD (marshall77's HDD).
[*]Copy the files from marshal77's HDD to marshall82's HDD.
[*]Unmount the secondary HDD.
[*]Shutdown marshall82, and move marshall77's HDD back to marshall77.
[/list] 

While I could answer questions that you may have about connecting the HDD, I'm new to Linux so I wouldn't know how to mount the HDD on top of my head, but I remember looking up some posts about mounting secondary HDDs in these forums, you could try the same.[/QUOTE]


thank you so much.

---

