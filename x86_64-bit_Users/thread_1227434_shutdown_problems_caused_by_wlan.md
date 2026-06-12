---
title: "shutdown problems caused by wlan"
date: 2009-07-30
forum: x86 64-bit Users
---

### Post by Erik Bekkering on 2009-07-30
I'm using a Sony Vaio VGN-FZ21E wich I upgraded to 4 Gb mem. After installing Ubunbu Jaunty 64 bit I've encountered the shutdown problem a lot of users already reported.
As soon as I shutdown, or reboot, the screen finally goes black, but a cursor is blinking in the leftmost corner. The system will not power-off.
When I switch the wifi card (an Intel wich uses iwl3945) of with the switch on from of the notebook, to OFF, before I shutdown,  everything works OK.
So the problem is defenitely in the wlan interface. I've tried to implement a line containing "ifconfig wlan down" but this didn't work.
A "modprobe -r iwl3945" caused my system to hang.
Is there anyone who found a solution for this problem?
thanks, Erik

---

### Post by Erik Bekkering on 2009-08-02
> **Erik Bekkering said:**
> I'm using a Sony Vaio VGN-FZ21E wich I upgraded to 4 Gb mem. After installing Ubunbu Jaunty 64 bit I've encountered the shutdown problem a lot of users already reported.
As soon as I shutdown, or reboot, the screen finally goes black, but a cursor is blinking in the leftmost corner. The system will not power-off.
When I switch the wifi card (an Intel wich uses iwl3945) of with the switch on from of the notebook, to OFF, before I shutdown,  everything works OK.
So the problem is defenitely in the wlan interface. I've tried to implement a line containing "ifconfig wlan down" but this didn't work.
A "modprobe -r iwl3945" caused my system to hang.
Is there anyone who found a solution for this problem?
thanks, Erik

You can forget this thread. I've found a solution bij implementing "ifconfig wlan0 down" in the /etc/K50alsa-utils script. This line shutdowns the wlan interface and solves the problem

Erik

---

