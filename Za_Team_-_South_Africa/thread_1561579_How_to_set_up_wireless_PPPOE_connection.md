---
title: "How to set up wireless PPPOE connection?"
date: 2010-08-26
forum: Za Team - South Africa
---

### Post by Jaaks on 2010-08-26
Ok here goes another one.
On my work pc I am connected wirelessly to a telkom (yes I know they suck) ADSL Router.

I have used up half the data for this month installing Ubuntu and trying to get my home pc working.

How do I setup another connection using my axxess ISP login and password so I can use my own data easily and swop between the two.
Windows:
Just have a shortcut on my desktop to a pppoe connection and can connect and disconnect as I like.

Would like something similar but have no idea how to do it.
Yes I am a total Ubuntu moron but trying to get it going so I can spread the joys to friends and family too.
Thanks in advance.

---

### Post by stefanor on 2010-08-26
> **Jaaks said:**
> How do I setup another connection using my axxess ISP login and password so I can use my own data easily and swop between the two.

[https://help.ubuntu.com/10.04/internet/C/connecting.html](https://help.ubuntu.com/10.04/internet/C/connecting.html)

---

### Post by Jaaks on 2010-08-27
Sorry Stefanor bur I read that stuff twice and nowhere does it say anything about putting in your ISP user name and password for wireless connection.
Yes I can connect to the router and get Internet but I want to use my own ISP so that I do not use the works data.
This is very easy in windows, just ensure router has bridge mode enabled and setup a PPPOE connection with your ISP details and voila a shortcut is on the desktop.
How do I do this in Ubuntu????

---

### Post by stefanor on 2010-08-27
Look at the section on DSL connections:

[LIST]
[*]Right click on network manager (the network connection icon)
[*]Edit connections
[*]DSL
[*]Add
[*]You should be able to work out the rest
[/LIST]

---

### Post by dineshs on 2010-08-30
Are you using 10.04?I think DSL tab method will not work for wireless pppoe
what does ```
iwconfig
``` say?If your wireless device is wlan0 try this
In a terminal type```
sudo pppoeconf wlan0
```and follow instructions
Now backup /etc/network/interfaces using```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
Now edit the same file using```
gksudo gedit /etc/network/interfaces
```
so that it contains only these two lines
```
auto lo
iface lo inet loopback

```
Restart machine
Run```
sudo pon dsl-provider
``` and wait for sometime
Does it work?

---

### Post by Jaaks on 2010-08-30
So these changes seem quite permanent and a lot of coding?
(Well one can code it all back again.)
Once I have done this and can use my own ISP how do I get back to using the normal connection too?
Why all the coding?? Can someone that is alot more clued up than me no twrite an app or get a program which can do this simply?
Enable the swop between the two connections?
So fo rnow I am just back to windows because Ubuntu cannot do what I need. :-(

---

### Post by kleinric on 2011-03-24
Howzit,

Do you need to dial up for both of them? Thats actually quite easy:

In a terminal, setup your first connection:
```
sudo pppoeconf
```This will create a file called /etc/ppp/peers/dsl-provider
Rename this file to your connection name, eg... 
```
sudo mv /etc/ppp/peers/dsl-provider /etc/ppp/peers/telkom
```Then setup your second connection:
```
sudo pppoeconf
```This, again, will create a file called /etc/ppp/peers/dsl-provider
Rename this file to your other connection name, eg...
```
sudo mv /etc/ppp/peers/dsl-provider /etc/ppp/peers/axxess
```Then to connect to telkom:
```
sudo pon telkom
```To connect to axxess
```
sudo pon axxess
```To disconnect:
```
sudo poff -a
```To check whats going on while you're waiting to connect:
```
sudo plog
```I'm not sure how to do it with the command line, but if you go System | Administration | Users & Groups, then select your username and click "Advanced Settings" then check the "Connect to the internet using a modem" under the "User Privileges" tab. Log out and in again and you'll be able to run all the commands without sudo.

I use a telkom billion wireless router at home - we have a telkom account and another prepaid one for when we're capped. I run "pon telkom" to connect until we're capped, then I use "pon prepaid" 

This system works absolutely perfectly for us. No extra configuration is required on the wireless network - it just need to be connected, which works fine through network manager for me.

---

### Post by kleinric on 2011-03-24
ps... once you've set it all up you only need to remember 3 commands:
Connect
```
pon filename
```
Disconnect
```
poff -a
```
Status:
```
plog
```

Turns out this is actually quicker than using a gui

---

