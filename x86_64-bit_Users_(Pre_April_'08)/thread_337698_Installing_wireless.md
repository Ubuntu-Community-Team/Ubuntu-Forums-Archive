---
title: "Installing wireless"
date: 2007-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Doug11 on 2007-01-13
I just upgraded to amd64...both machine and edgy. I have done tons of reading today and have made it about this far,,,
doug@home:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!

Is there a different driver I have to use for the 64 bit. I tried a couple diferent how-tos but as far as I saw,,they all used the bcmwl5.inf and the bcmwl5.sys files. Is this correct. Am I heading in the right direction but wrong road?

---

### Post by John Jason Jordan on 2007-01-13
> **Doug11 said:**
> I just upgraded to amd64...both machine and edgy. I have done tons of reading today and have made it about this far,,,
doug@home:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!

Is there a different driver I have to use for the 64 bit. I tried a couple diferent how-tos but as far as I saw,,they all used the bcmwl5.inf and the bcmwl5.sys files. Is this correct. Am I heading in the right direction but wrong road?
Since you used the bcmwl5 driver, I am assuming you have a Broadcom chip. Is that correct? If so, there are different Broadcom chips. Which one do you have?

I should add that a default installation of Ubuntu Dapper or Edgy (64-bit) will detect the Broadcom chip and try to install the new open source driver for it, so you don't need ndiswrapper. If it is not working with the open source driver and you decide to use ndiswrapper instead, you must blacklist the open source driver or it will try to load. This will prevent ndiswrapper from working.

---

### Post by Doug11 on 2007-01-13
Yes. I do have the broadcom chip.  That sort of makes sense now because the light for my wireless was coming on right from the start meaning the radio was picked up where as before with the 32-bit edgy,,,i would have to install the ndiswrappper and driver manually. What I have noticed in this version of edgy is that under system>Admin>windows wireless drivers,,,you can just pick a windows .inf file and it will install it for you. I used it and now have this,,,

doug@home:~$ ndiswrapper -l
Installed drivers:
netbc564                driver installed 

But every time i reboot,,I have to go into networking and enable this device,,,but yet it still does not work. Any other suggestions?

---

### Post by Doug11 on 2007-01-13
> **John Jason Jordan said:**
> Since you used the bcmwl5 driver, I am assuming you have a Broadcom chip. Is that correct? If so, there are different Broadcom chips. Which one do you have?

I should add that a default installation of Ubuntu Dapper or Edgy (64-bit) will detect the Broadcom chip and try to install the new open source driver for it, so you don't need ndiswrapper. If it is not working with the open source driver and you decide to use ndiswrapper instead, you must blacklist the open source driver or it will try to load. This will prevent ndiswrapper from working.

I shold also say that I have not blacklisted anything yet,,if so,,what shold i comment out and where?

---

### Post by John Jason Jordan on 2007-01-13
> **Doug11 said:**
> I shold also say that I have not blacklisted anything yet,,if so,,what shold i comment out and where?
A quick search of the forums disclosed this, posted by sjnovick here:

[http://ubuntuforums.org/showthread.php?t=332397&highlight=blacklist+broadcom:](http://ubuntuforums.org/showthread.php?t=332397&highlight=blacklist+broadcom:)

1. Remove the driver from loaded modules
# rmmod bcm43xx
2. Blacklist bcm43xx so that it doesn't get loaded upon reboot. See the file /etc/modprobe.d/blacklist. Add the entry

blacklist bcm43xx

3. Now, load ndiswrapper:
# modprobe ndiswrapper
# depmod -a

4. You should be able to eth1 in your network manager. If you prefer the manual route:
# iwconfig eth1 [you may need to put info here like essid]
# ifconfig eth1 up
# dhclient eth1

Here's another forum thread:

[http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306)

---

### Post by amd-64 on 2007-01-13
Before step 4, you should restart networking, to make sure the wireless card is not controlled by the bcm43xx module. I usually run 
```
sudo /etc/init.d/networking restart

```

---

### Post by Doug11 on 2007-01-14
I tried all that in that howto,,but now when I go to enable and configure my wireless in Networking,,,it has disappeared. Just wired and modem connection there now.

doug@home:~$ iwconfig eth1
eth1      No such device

---

### Post by Doug11 on 2007-01-14
Well, after much more reading and more probs not getting wine to work or vmware to run properly and my wireless,,I"m gonna just sick back and go with the 32-bit distros for a while longer until the 64 gets a few more of the bugs worked out. I havent experimented with Dapper yet so I'm gonna play with that for a while. Thanks to those who have tried to help.

---

### Post by woopud on 2007-01-14
> **Doug11 said:**
> Well, after much more reading and more probs not getting wine to work or vmware to run properly and my wireless,,I"m gonna just sick back and go with the 32-bit distros for a while longer until the 64 gets a few more of the bugs worked out. I havent experimented with Dapper yet so I'm gonna play with that for a while. Thanks to those who have tried to help.

I run Edgy  64bit on my AMD HP laptop with the Broadcom wireless with no problems.  Don't use this Ndiswrapper crap, i tried that for weeks with no luck and a lot of frustration just use fwcutter using the following link, worked for me in ten minutes !

Bert

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by Doug11 on 2007-01-15
This is quoted from the Howto you sent..


[It seems that if you get the following string back: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) that this guide is VERY unlikly to work for you although it does sometimes, dont ask me why, but basically every "no" vote and "this didnt work for me" post comes from a BCM4318 user....]

I have the rev 02 Broadcom card and funny enough,,,it worked for me,,,don't know why,,,but it is. Thanks for the tips.

---

### Post by amd-64 on 2007-04-03
For those who did not manage to make this driver to work, I just found out one good tip. 

If you have installed the wireless driver too many times or from more than one source, there is no guarantee which one ndiswrapper is using particularly if they have the same name. 

I have a 64bit machine, but while trying to get the wireless working, I may have installed 32 bit driver and/or other versions of the driver.  It did not help to uninstall the driver using 
```

sudo modprobe -e bcmwl5
```

I needed to remove the old installations from /etc/ndiswrapper before installing the 64-bit driver using 
```

cd /etc/ndiswrapper
sudo /bin/rm -r  *olddrivers*
sudo modprobe -i bcmwl5 
```
which then worked right away.


By the way ndiswrapper works much better for now and has at least twice the range as bcm43xx. This is a bug in bcm43xx which will be fixed eventually.

---

