---
title: "ugh Internet disconnects when idle"
date: 2008-07-05
forum: x86 64-bit Users
---

### Post by jriley60 on 2008-07-05
so i've looked and looked and looked still no help i'm finally asking. i have 8.04 64 bit connected to a netgear router and every time i go idle i lose internet connection and have to restart. i've checked the bios and everything seems fine. router settings have nothing i can change so it must be somewhere in ubuntu. it's like my nic goes to sleep and won't wake up or something. please help as i hate having to restart constantly

---

### Post by nikgare on 2008-07-05
Do you really lose internet connect, or just the connection to you router?

---

### Post by prshah on 2008-07-05
> **jriley60 said:**
> so i've looked and looked and looked still no help i'm finally asking. i have 8.04 64 bit connected to a netgear router and every time i go idle i lose internet connection and have to restart. i've checked the bios and everything seems fine. router settings have nothing i can change so it must be somewhere in ubuntu. it's like my nic goes to sleep and won't wake up or something. please help as i hate having to restart constantly

Wireless power management

Try using the following commands to turn off power management for your wireless:```

sudo iwconfig eth9 txpower fixed
sudo iwconfig eth9 power off
sudo iwconfig eth9 commit
```

The third command may give an error as "feature not supported" that can be ignored.

Either one of the first two commands should work and will take effect immediately, _until_ your next reboot. 

So give the commands, then surf for an hour or two to check if it is effective. If it is effective, you can add the commands to your "/etc/rc.local" to take effect on every reboot.

Note that in the rc.local file, the last line should not be disturbed (ie, "exit 0")

---

### Post by jriley60 on 2008-07-07
??? i don't know if it worked or not



Error for wireless request "Set Tx Power" (8B27) :
    GET failed on device eth9 ; No such device.
joshua@joshua-desktop:~$ sudo iwconfig eth9 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth9 ; No such device.
joshua@joshua-desktop:~$ sudo iwconfig eth9 commit
Error for wireless request "Commit changes" (8B00) :
    SET failed on device eth9 ; No such device.
joshua@joshua-desktop:~$ sudo iwconfig eth0 txpower fixed
Error for wireless request "Set Tx Power" (8B27) :
    GET failed on device eth0 ; Operation not supported.
joshua@joshua-desktop:~$ sudo iwconfig eth0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth0 ; Operation not supported.
joshua@joshua-desktop:~$ sudo iwconfig eth0 commit
Error for wireless request "Commit changes" (8B00) :
    SET failed on device eth0 ; Operation not supported.

---

### Post by chetan.89 on 2008-07-08
Try this out. Worked in my case :). I had a similar problem as yours.

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Hope it helps you.
Good luck !
Chetan.

---

### Post by Yellow Pasque on 2008-07-09
eth9? Your interface is probably named wlan0. Use this to be sure:
```
cat /etc/network/interfaces
```

---

### Post by jriley60 on 2008-07-12
cat /etc/network/interfaces returns
auto lo
iface lo inet loopback

---

### Post by prshah on 2008-07-12
> **jriley60 said:**
> ??? i don't know if it worked or not

Error for wireless request "Set Tx Power" (8B27) :
    GET failed on device eth9 ; No such device.
joshua@joshua-desktop:~$ sudo iwconfig eth0 txpower fixed
Error for wireless request "Set Tx Power" (8B27) :
    GET failed on device eth0 ; Operation not supported.



You have to replace eth9 with the actual name of the interface. Use ```
iwconfig
``` to find your device, or paste the output here for advice.

---

### Post by jriley60 on 2008-07-23
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by jriley60 on 2008-07-23
i think theres a mix up i'm not using wireless....i just have my cord run through the wireless router....i still keep having to restart to use the internet if i go idle....it says it's sleeping, but i don't know how to wake it:mad:

---

### Post by jriley60 on 2008-07-31
ttt

---

### Post by lavinog on 2008-07-31
Have you tried switching the cable to make sure it isn't a bad cable.
When it does disconnect: what happens if you disconnect the cable for 5 secs then plug back in (this can be done on the router or computer side)? Does it restore the connection?

What model network card do you have?
can you post the output of
```

sudo lshw -class network

```

---

