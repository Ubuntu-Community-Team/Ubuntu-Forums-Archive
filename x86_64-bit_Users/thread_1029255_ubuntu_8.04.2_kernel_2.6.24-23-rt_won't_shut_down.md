---
title: "ubuntu 8.04.2 kernel 2.6.24-23-rt won't shut down"
date: 2009-01-03
forum: x86 64-bit Users
---

### Post by act on 2009-01-03
Hello ubuntu ("ubuntu studio" installed) 8.04.2 kernel 2.6.24-23-rt won't shut down.

The PC goes through the motions but in the very end the Ubuntu logo still stays on the monitor and PC just "hangs". It never turns itself off.

I have this problem on two recent computer.
When I start whith the generic 2.6.24-23 kernel everything goes well.

I have try several things but nothing work for me.

sudo shutdown -h now

sudo shutdown -P now

sudo shutdown now

First LogOff and then ShutDown from the login screen

"sudo /etc/init.d/networking stop" to see if it's a network problem

sudo gedit /etc/init.d/alsa-utils
scroll down to where you see stop)
insert this at the top right after the stop) :
ifconfig eth0 down

sudo gedit menu.lst
find the first kernel line that isn't commented out (after the ## ## End Default Options ##):
kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash
add the following to the end:
<space> acpi=force where <space> means just press the space bar.
Your line should then look like this:
kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash acpi=force

First open the /etc/modules file as root in the text editor by entering in the terminal:
Code:
gksudo gedit /etc/modules
Then add this as the last line of the file:
Code:
apm power_off=1

Can anyone help me
Thanks

---

