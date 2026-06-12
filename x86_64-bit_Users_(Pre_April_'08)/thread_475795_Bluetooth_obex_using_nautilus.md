---
title: "Bluetooth obex using nautilus"
date: 2007-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by alek66 on 2007-06-16
Has anyone figure out how to configure this properly?
I want to browse the files on my phone and pda... I see many people have done this, but they dont post any good explanation how.
[IMG]http://img375.imageshack.us/img375/6449/obex1kb7.png[/IMG]
I want to be able to do this... 
[IMG]http://img375.imageshack.us/img375/4279/obex2ex8.png[/IMG]

Images where taken from [here]("http://weblog.topopardo.com/?p=1483")

---

### Post by setterm on 2007-06-17
G'day,

after some reading and searching, the best way to get what you want - because it worked brilliantly for me, is to run "sudo apt-get install **gnome-vfs-obexftp**". This will install the obex protocol into the vfs layer that nautilus will be able to run on top of. It will scan for any available bluetooth devices, rather quickly, and display them with the display name instead of the device id. Then from there, by clicking on the icon, you can view the device like a local filesystem. I don't know yet about writing to the device or deleting files, but you can view them and copy them just as easily as in konqueror with **bluetooth:/**. Just press ctrl+l then type in **obex:///** and enter.

if you have any drama's, email me. [email]Matthew.setter@gmail.com[/email]

have a great one,

Setts

---

### Post by dom on 2008-03-23
good thread,

works for me, ubuntu 7.10

now successfully browsing obex://[device-id] in nautilus

also, "Browse Device" in the "Bluetooth Applet 0.14" works.

cheers

---

### Post by Windsurfer619 on 2008-06-26
This does NOT work for me. I get a "Operation not supported by backend" in Hardy Heron. Can anyone explain how I can get this to work? Thanks!

---

