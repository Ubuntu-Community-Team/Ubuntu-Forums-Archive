---
title: "Rdesktop slow printing (Fixed)"
date: 2007-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by eoinmadden on 2007-06-20
I connect to Windows 2003 terminal server using rdesktop from my Ubuntu machine. I have an OKI B4350 attached the the Ubuntu box.

Printing a windows test page (or any document) was taking over 60 seconds from the terminal server the using Ubuntu client. But I could do it in about 5 seconds if I connected to the terminal server if I used a windows client.

I don't use Tsclient to connect from the Ubuntu client. I use a little one line script which calls rdesktop.

Today I discovered that if I **specify the driver** in my script I can get the printing time down to 5 seconds!!!
So my script used to read...

rdesktop -u Eoin -n Dublin  -r printer:B4350 192.168.50.10 

Now I changed it to:

rdesktop -u Eoin -n Dublin  -r printer:B4350="OKI B4350(PCL)" -r lptport:LPT1=/dev/lp0 192.168.50.10 

and hey presto! Faster printing! 
Note the driver name is the name of the driver windows server uses, not what the ubuntu client uses.

---

