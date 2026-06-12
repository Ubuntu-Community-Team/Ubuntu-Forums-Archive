---
title: "Create link between ttyUSBx and comx in Ubuntu 17.04"
date: 2017-04-29
forum: Wine
---

### Post by 2468_calvin on 2017-04-29
I just upgraded to Ubuntu Unity 17.04 and cannot create symbolic links to run Windows programs under Wine. These symbolic links match up the ttyUSB on Linux to the com on Windows.   I have done this using Ubuntu 14.04 without a problem.  I cannot get these to work under 17.04. 

*** Linux uses ttyUSBx to identify a USB port while Windows uses comx to identify the same thing, i.e. Windows COM1 is the same as Linux ttyUSB0. Under wine, you need to establish a link between ttyUSBx and comx ***

Code: ( You must use capital letters for USB and small letters for com as shown below. ) 

ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

Make a link for any additional number on com ports you may use in the future:

ln -s /dev/ttyUSB1 ~/.wine/dosdevices/com2
ln -s /dev/ttyUSB2 ~/.wine/dosdevices/com3
ln -s /dev/ttyUSB3 ~/.wine/dosdevices/com4

Then in the Windows program that you run under wine, the comx port you select will connect to the Linux ttyUSBx port.  

I have tried using sudo in front of the command lines and that does not work.  

TIA
Calvin

---

### Post by Xian on 2017-04-30
> **2468_calvin said:**
> 
Make a link for any additional number on com ports you may use in the future:

ln -s /dev/ttyUSB1 ~/.wine/dosdevices/com2
ln -s /dev/ttyUSB2 ~/.wine/dosdevices/com3
ln -s /dev/ttyUSB3 ~/.wine/dosdevices/com4

Then in the Windows program that you run under wine, the comx port you select will connect to the Linux ttyUSBx port.  

I have tried using sudo in front of the command lines and that does not work.  


Can you please post the exact command you issued in the terminal and the output?

---

### Post by 2468_calvin on 2017-04-30
Here is coding and output. 


csd@csd--D830-160GB:~$ ln -s /dev/ttyUSB4 ~/.wine/dosdevices/com5
csd@csd--D830-160GB:~$


There was nothing on the terminal in the output line. I verified that a new link was created in the /.wine/dosdevices/ directory.

---

