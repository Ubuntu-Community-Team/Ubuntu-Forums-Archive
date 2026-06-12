---
title: "Com Port issue"
date: 2008-10-02
forum: Wine
---

### Post by Shiloh Hawkesworth on 2008-10-02
When I open the program it appears to open fine, but it is not seeing the com port to receive the data.

The devise is visible:

[130821.850749] usb 5-1: FTDI USB Serial Device converter now attached to ttyUSB0


When I run the program in the terminal this is what I get:

fixme:ole:OleLoadPictureEx (0xaaf064,77884,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fae8), partially implemented.
fixme:ole:OleLoadPictureEx (0xaba69c,902,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f7a8), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x15d6d8)->(0x172f70, 0, (nil)), hacked stub.
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub
err:comm:get_baud_rate tcgetattr error 'Input/output error'
err:comm:set_baud_rate tcgetattr error 'Input/output error'
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub
err:comm:get_baud_rate tcgetattr error 'Input/output error'
err:comm:set_baud_rate tcgetattr error 'Input/output error'
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub
fixme:comm:GetCommProperties (0x88 0x32f4d0 )
fixme:wininet:InternetGetConnectedState always returning LAN connection.



I have created a symbolic link using:
ln -s /dev/ttyUSB0 com1
and
ln -s /dev/usb/ttyUSB0 ~/.wine/dosdevices/com1

because I was not sure which one was right.


Here is a little about the product:
The programs function is as follows:
Monitor the status of your Herpstat product online.
Receive Scheduled Emails or VTEXT messages with status information.
Receive Emergency Email and VTEXT alerts.
Update the Herpstat’s firmware when code changes have been made.

The general idea is that you have 4 thermostats hooked up to a cage. And if you connect the thermostat to the computer you can monitor the temps etc. I would REALLY like to be able to do that with Ubuntu. I have not been able to get the program to work under Wine.
The adapter is a single USB to serial using a FTDI chip. (FT232R)

Here is a link to the website (although you probably need the thermostat to do much). The file is called "Herpstat Uploader Software"
[http://spyderrobotics.com/downloads/index.html](http://spyderrobotics.com/downloads/index.html)

I would be extremely grateful of any help. 
I am really "green" on the terminal, so please bear with me.

---

### Post by Chondro_Biak on 2008-10-04
*Bump*

---

