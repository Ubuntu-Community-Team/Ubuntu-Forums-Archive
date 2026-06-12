---
title: "need to change baud rate permenantly"
date: 2005-07-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by daniel49 on 2005-07-28
pretty much am getting my ubuntu set up, but have noticed the modem seemed very slow. I have been able to connect using system admin/networking/activate
it is not autodetected but was able to point it to /dev/ttyUSB0 and that worked.

indeed it was setup at 9600 baud. found out for sure by stty -a </dev/ttyUSB0 
tried gnome ppp dialer ( which has an option to set baud), but it couldn't find modem. 
so tried stty -F /dev/ttyUSB0 115200 
 to change baud rate and that was successful! 

 unfortunately doesn't seem to be saving it on a reboot.anyone know why that is? 
And how I can make the change permenant?

---

### Post by dmn_clown on 2005-07-28
I've always had better luck with kppp as far as modem configuration and such goes.  Unfortunately dialup speed would make the installation of kdelibs time intensive.

However, you should be able to change the modem's default speed in the /etc/ppp/peers/provider configuration file.

```
sudo nano -w /etc/ppp/peers/provider
``` 

57600  under the speed heading should connect you at a quicker speed than 9600, you can try to go faster but you risk your modem defaulting back to a much slower speed when it cannot connect at the requested speed.  Experiment and find a speed that works for your setup.

---

### Post by daniel49 on 2005-07-28
[QUOTE=dmn_clown]I've always had better luck with kppp as far as modem configuration and such goes.  Unfortunately dialup speed would make the installation of kdelibs time intensive.

However, you should be able to change the modem's default speed in the /etc/ppp/peers/provider configuration file.

```
sudo nano -w /etc/ppp/peers/provider
``` 

57600  under the speed heading should connect you at a quicker speed than 9600, you can try to go faster but you risk your modem defaulting back to a much slower speed when it cannot connect at the requested speed.  Experiment and find a speed that works for your setup.[/QUOTE]
 no that file in provider is already set at 38000+ doesn't seem to be related to anything that happens on my connection.

Again I just go to system/administration/networking and activate it from there is the only way thats worked so far.

like I said though i can set it temp to 115000+ temporarily till I reboot, so I downloaded the kpp dialer and libraries as you suggested.
true it was easy to set up but for some reason it dials,connects,and then terminates with an error message of 1? dunno why I used kpp in fedora 3 and it worked great for me.

---

### Post by daniel49 on 2005-07-29
ok, have a solution finally. came back to post it for those that may follow with same problem.


Apparently udev hasn't been started at all when this module (usbserial)is loaded.  what you can do is defer setting the baud until the very end of the boot process.  there is a file called /etc/init.d/bootmisc.sh , which runs at the very end. You can   move  the stty statement into /etc/init.d/bootmisc.sh.
so in essence what i did was

sudo gedit /etc/init.d/bootmisc.sh

and added 

stty -F /dev/ttyUSB0 115200 

at the very end of the sh file just before it exits.
so in essence it changes my baud rate from 9600 to 15200 on each boot.
is working much better and faster now.

Thank you bersl for your help!

---

