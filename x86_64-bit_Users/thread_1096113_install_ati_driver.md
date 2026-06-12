---
title: "install ati driver"
date: 2009-03-14
forum: x86 64-bit Users
---

### Post by SupraMan on 2009-03-14
ok so i am a total noob to ubuntu and even the forums (took me a while to learn how to post one). well to sum it up i am runing ubuntu 64 bit on a dell dimension 9100 with 5 gig ram (only using 3.4) and an ati radeon x600.
i recently tried to install wow through wine but the vide is all messed up and runs very laggy. looked it up and found that it could be that i dont have the new driver for my video card. downloaded it , ati-driver-installer-9.2-x86.x86_64.run, but no matter where i look on google i cant find a step by step instruction on how to install it that works. so to sum it up thats what i need, a step by step on how to install this.

---

### Post by cariboo on 2009-03-14
The driver is pretty easy to install:

[list=1]
[*] Press Ctrl-Alt-F1 to get to the console
[*] at the  prompt type:
```
sudo /etc/init.d/gdm stop
```
this will stop the Gnome Desktop Manager.
[*] Assuming you have the driver file sitting on your desktop cd to the desktop:
```
cd ~/Desktop
```
[*] Make the file executeable:
```
chmod +x ./ati-driver-installer-9.2-x86.x86_64.run
```
[*] Install the driver:
```
sudo ./ati-driver-installer-9.2-x86.x86_64.run
```
I have have an nvidia card, but I assume the install process is the same, answer **yes** to all the question, and wait for it to finish compiling.
[*] Restart X:
```
sudo /etc/init.d/gdm start
```
Restarting GDM should take you back to your desktop.
[/list]

Jim

---

### Post by Yellow Pasque on 2009-03-14
Follow this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by SupraMan on 2009-03-15
cariboo907 i tried your way but when i try to cd into desktop it gives me this message "-bash: cd: /home/hayabusa/desktop: no such file or directory" and i've tried cd before it goes into home with no prob but it wont go into hayabusa idk y

---

### Post by lvleph on 2009-03-15
I would suggest envyng. It does everything for you and makes sure you don't screw up. Somehow I always seem to mess it up. 

EDIT: Is your user name hayabusa, or is this a separate user? If it is your user the when you get into terminal type pwd, to see where it is putting you.

---

### Post by Yellow Pasque on 2009-03-15
> **SupraMan said:**
> /home/hayabusa/**[SIZE="5"]d[/SIZE]**esktop: no such file or directory

LiNUx iS CaSe SenSITivE

---

### Post by racerraul on 2009-03-16
Installation instruction are on AMD\ATI website...
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat92-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat92-inst.pdf)

Besure that you do not have any restricted drivers loaded in jockey (Hardware Drivers) or in the /usr/share/ati folder.  If the folder does not exist then you do not have proprietary drivers installed.

Good luck... after spending quite a bit of time trying to get all the features I wanted working with the ATI card I was using, I was not satisfied and bought an nvidia card...

Life is good now :)

---

### Post by SupraMan on 2009-03-16
i tried system>administrator>hardware drivers and i couldnt even run the special effects on the desktop now when i hit play on wow it doesnt even run. and no i did not put anything with uper case. i can cd into /home 
and can even hit dir and it will show hayabusa but when i try to hit cd /hayabusa it tells me that it doesnt exist

---

### Post by SupraMan on 2009-03-16
im seriously getting frustrated w ubuntu. now im totaly restricted to what i can even do on it. im on the way into architecture but cant run any cad software on wine. cant play any games so far. its becoming pretty complicated. and so im left listening to music and just using some pages on the internet. i mean i LOVE what the ppl behind linux r doing but maybe idk enough about pc yet to really be able to use this

---

### Post by SupraMan on 2009-03-16
oh now im also running in low graphics mode because of "god knows what i did lol" any idea how to fix that?

---

### Post by stchman on 2009-03-16
Just enable the ATI driver in System--->Administration--->Hardware Drivers.

---

### Post by jocko on 2009-03-17
> **SupraMan said:**
> i tried system>administrator>hardware drivers and i couldnt even run the special effects on the desktop now when i hit play on wow it doesnt even run. and no i did not put anything with uper case. i can cd into /home 
and can even hit dir and it will show hayabusa but when i try to hit [COLOR=Red]cd /hayabusa[/COLOR] it tells me that it doesnt exist
That's right. You have no /hayabusa directory. A "/" before the directory name implies the root of the file system.
So:```

cd /home
cd hayabusa
```
would work.

But as pointed out earlier:
Linux is case sensitive. In your previous post you typed:
"**/home/hayabusa/[COLOR=Red]d[/COLOR]esktop**"
That directory does NOT exist, but:
"**/home/hayabusa/[COLOR=Blue]D[/COLOR]esktop**" does.

---

