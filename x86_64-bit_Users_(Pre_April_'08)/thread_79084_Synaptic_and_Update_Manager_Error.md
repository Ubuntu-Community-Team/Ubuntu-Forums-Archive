---
title: "Synaptic and Update Manager Error"
date: 2005-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by derrick81787 on 2005-10-19
Help! Every time I click on the Synaptic Package Manager or the Update Manager they don't load. Synaptic will prompt me for my password, and then flash up on the screen for a split second before closing. Update Manager does the same thing but doesn't prompt for any password. I've tried accessing Synaptic from the Terminal, but whenever I do, the same thing happens as before except I get this error :

"(synaptic:8324): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:8324): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Segmentation fault"

I'm kind of new to Ubuntu and Linux in general, and I have no idea what that means. I'm running Ubuntu Breezy Badger 5.10 AMD 64 Version. Can anyone help? It would be greatly appreciated.

---

### Post by grj on 2005-10-19
Open a terminal window and type:

sudo apt-get update

if that works type 

sudo apt-get dist-upgrade -s   --this will simulate a dist upgrade

see if there are any packages for synaptic for you to upgrade

note their names

sudo apt-get install package names from above

try synaptic again

---

