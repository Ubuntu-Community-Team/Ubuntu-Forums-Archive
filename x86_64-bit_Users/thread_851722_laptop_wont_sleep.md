---
title: "laptop wont sleep"
date: 2008-07-06
forum: x86 64-bit Users
---

### Post by royer10r on 2008-07-06
laptop wont suspend or hibernate without locking up
dell inspiron 1526

help
bryan

---

### Post by soxs on 2008-07-07
what ubuntu version / architecture do you use?
And is this all of a sudden or did the laptop refuse to sleep since you first installed?
GPU specs required.

---

### Post by royer10r on 2008-07-07
HH 8.04.1
AMD turion 64 x2 tl-60
has never suspended or hibernated
everything else is good though

---

### Post by soxs on 2008-07-08
Did you enable S3 and S1 states in your bios?

---

### Post by royer10r on 2008-07-08
there are no mention of these in the bios
though i have tried several distros an got the same results
so it must be my hardware

????
bryan

---

### Post by soxs on 2008-07-08
> **royer10r said:**
> there are no mention of these in the bios
though i have tried several distros an got the same results
so it must be my hardware

????
bryan

the fact you allready tried different distros and none of them worked, is rather bad. In that case I can't help you. I just "unpacked" my first laptop and I am going to try everything within the next week.

Btw. which driver did you install for you ati graphics card. This may be the cause for crashes when hibernating.

Everything else exceeds my knowledge and requires some more skilled guy to get his/her hand on this thread/your problem.

---

### Post by royer10r on 2008-07-08
it offered the graphics driver automaticly and only gave me one choice "ati accelerated graphics driver"....i just tried to suspend and then hibernate my desktop with 32bit ubuntu HH and got almost the same results....didnt work but hung in a different spot....am i doing something wrong...a dont know what it could be.....

????

---

### Post by kevmitch on 2008-07-09
Ok, let's try a low level sleep 
```
echo -n mem > /sys/power/state
```
This will tell the laptop to sleep right now without running a lot of the pre sleep scripts in /etc/acpi/suspend.d.

Usually those scripts are there to prevent problems when sleeping, but it's possible they could be causing them if you don't have your /etc/defaults/acpi-support file configured correctly for your hardware.

---

### Post by royer10r on 2008-09-10
it wont let me ...no permision

---

### Post by drjonze on 2008-09-10
Same problem here. I have never been able to get my machine to sleep. I don't really mind, I can live without it but I also have issues with lock-ups when the screen saver comes on. I can't have a screen saver, I just have it set to blank the screen. I think it might be issues with my graphics card, I have an nVida card (GeoForce 6100). Woe is me. I bought the machine before I'd even heard of Ubuntu. It took me a long time to get my display right and even longer when I started using my LCD TV as my monitor. 

Specs:

HH 8.4.1 (64)
Acer Aspire 9300  AMD 64 Turion

---

### Post by RavanH on 2008-09-30
> **royer10r said:**
> laptop wont suspend or hibernate without locking up
dell inspiron 1526

help
bryan

Suspend/hibernate is reported to work on the latest ATI drivers following the 2nd method instructions on [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29)

Not sure if this goes only for 32bit or for 64bit too, because I have not tested the hibernation yet...

In any case, it is interesting news from ATI driver dev ;)

---

### Post by royer10r on 2008-10-20
thanks RavanH,
that helped a little. i have recently updated to 8.10 in hopes that the new kernel would allow this to happen. but the results were the same. then i installed the new driver using the instructions you gave me and it made it a lot further. it still unfortunately froze but it made it to the screen that says restoring. i have only tryed it once though and hopefully it may be a beta thing. o well ill keep trying.

thanks,
bryan

---

### Post by RavanH on 2008-10-30
> **royer10r said:**
> thanks RavanH,
that helped a little. i have recently updated to 8.10 in hopes that the new kernel would allow this to happen. but the results were the same. then i installed the new driver using the instructions you gave me and it made it a lot further. it still unfortunately froze but it made it to the screen that says restoring. i have only tryed it once though and hopefully it may be a beta thing. o well ill keep trying.

thanks,
bryan

Did you mean you updated to Catalyst 8.10 or Ubuntu 8.10 (or both) ? 

A quote from the install instructions mentions some settings in /etc/default/acpi-support

> For ATI X1400, to get the laptop to wake up from suspend, I had to change the following in /etc/default/acpi-support:
```
SAVE_VBE_STATE=false

POST_VIDEO=false 

ENABLE_LAPTOP_MODE=false
```


Have you tested with these or other settings in the /etc/default/acpi-support config file yet? If so, what did you find, if anything at all? 

Wouldn't it be great if we got even closer to getting this Suspend to Disk (Hibernate) thing to work? Suspend to Ram (Sleep) seems to work on my system except for Wifi connection problems after Resume. Have you got Sleep working?

Thanks for sharing any info :)

---

### Post by cleopete on 2008-10-30
When I first installed the 32 bit Hardy (kernel 16, I think) suspend worked just fine.  It wasn't till later when I did a fresh install of Hardy 64 (kernel 19) that it all went to hell and didn't come back with Intrepid 64 beta.  It's Release Day and suspend is still hosed.

A blogger from the Intrepid site predicted this would stay a problem with Nvidia and ATI.  I don't know, but she sure helped fix my on-again/off-again Atheros troubles.

I have assumed some sort of kernel building project would be in order, but I haven't had time to learn how to do that...yet.

---

### Post by Bark on 2009-04-30
> **kevmitch said:**
> Ok, let's try a low level sleep 
```
echo -n mem > /sys/power/state
```
This will tell the laptop to sleep right now without running a lot of the pre sleep scripts in /etc/acpi/suspend.d.

Usually those scripts are there to prevent problems when sleeping, but it's possible they could be causing them if you don't have your /etc/defaults/acpi-support file configured correctly for your hardware.

I have the same problem as the original questioner and I tried this method. The same problem occurs, the computer goes to sleep and won't wake up again, so I have to remove the battery in order to get it to work again.

---

### Post by Bark on 2009-04-30
> **royer10r said:**
> it wont let me ...no permision

You probably need to add "sudo" before the command.

---

### Post by sjatkins on 2009-05-20
Just installed kubuntu 9 on MBP from around Jan 2008 era.  I don't see anything obvious in system settings to set thee machine to sleep on laptop close.  It doesn't by default which seems rather dumb for a laptop.  Found power management suspend options.  But setting suspend to disk or suspend to memory both do not sleep the laptop on lid close.  So what is the trick.  Or is this MIA yet again?

---

