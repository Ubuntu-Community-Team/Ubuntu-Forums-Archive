---
title: "Bootchart reporting slow times in x86_64"
date: 2009-11-11
forum: x86 64-bit Users
---

### Post by Naraltd on 2009-11-11
First let me say if this doesn't belong here, I apologize.  I wasn't really sure where to put it.

I just recently upgraded to the 9.10 64 bit version of ubuntu.  

Prior to that I was running 8.10 32 bit mode and was getting 17 seconds boot time on bootchart.  (I have an SSD drive).

But now on the same drive bootchart is appearing to be in the 1 minute range.

Now I'm not saying the boot is slow, in fact it appears to be blazing fast, but I'm not sure why bootchart is reporting it as slow as it is.

I have attached a bootchart png so you guys, who know way more than me, can take a look.

Thanks!

---

### Post by blueridgedog on 2009-11-11
Did you do a clean install with a fresh format of /?

---

### Post by jocko on 2009-11-11
> **Naraltd said:**
> First let me say if this doesn't belong here, I apologize.  I wasn't really sure where to put it.

I just recently upgraded to the 9.10 64 bit version of ubuntu.  

Prior to that I was running 8.10 32 bit mode and was getting 17 seconds boot time on bootchart.  (I have an SSD drive).

But now on the same drive bootchart is appearing to be in the 1 minute range.

Now I'm not saying the boot is slow, in fact it appears to be blazing fast, but I'm not sure why bootchart is reporting it as slow as it is.

I have attached a bootchart png so you guys, who know way more than me, can take a look.

Thanks!
That's just because bootchart waits 45 seconds after the login screen to record the desktop loading process.
If you don't like it that way, you can change it:
```
sudo nano /etc/init/bootchart.conf
```
Find this section:
```
pre-stop script
    # Sleep for an extra 45s to allow enough time to chart the desktop
    # login
    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 45
end script
```
Make it look like this:
```
#pre-stop script
    # Sleep for an extra 45s to allow enough time to chart the desktop
    # login
#    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 45
#end script
```

---

### Post by Naraltd on 2009-11-12
> **blueridgedog said:**
> Did you do a clean install with a fresh format of /?

Yeah it was a clean install.  I copied my old install over to a USB HD because it was 32 bit.

I wanted to run 64 bit VBox guests so needed to fresh install.

---

### Post by Naraltd on 2009-11-12
> **jocko said:**
> That's just because bootchart waits 45 seconds after the login screen to record the desktop loading process.
If you don't like it that way, you can change it:
```
sudo nano /etc/init/bootchart.conf
```
Find this section:
```
pre-stop script
    # Sleep for an extra 45s to allow enough time to chart the desktop
    # login
    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 45
end script
```
Make it look like this:
```
#pre-stop script
    # Sleep for an extra 45s to allow enough time to chart the desktop
    # login
#    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 45
#end script
```

Ahh I assume that is new then.  My desktop doesn't take 45 seconds to load, and honestly I'm not sure it did when I had it on a HDD.  Not sure why they would put that arbitrary value in there.

Thanks for the help. 

New bootchart attached.  12 seconds, and not any real tuning other than turning off the splash.

---

### Post by Naraltd on 2009-11-12
Guess I didn't actually get the attachment.

Here it is.

---

### Post by philinux on 2009-11-12
I prefer the new method of seeing how long the total process is from grub to useable desktop. The timings I'm getting are spot on to when the desktop is actually useable.

---

### Post by Naraltd on 2009-11-13
> **philinux said:**
> I prefer the new method of seeing how long the total process is from grub to useable desktop. The timings I'm getting are spot on to when the desktop is actually useable.

I can see that being valuable, I just feel the 45 seconds is WAY off.  

I'm pretty sure for my setup it is closer to 10-15 seconds.  

But knowing where that is at in the script, I can edit it to a more meaningful value.

---

