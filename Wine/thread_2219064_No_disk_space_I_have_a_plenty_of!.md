---
title: "No disk space? I have a plenty of!"
date: 2014-04-22
forum: Wine
---

### Post by yan4 on 2014-04-22
Hi,

Today I tried to install an VST audio application but it was aborted with the message that there was not enough disk space.

I ran the command [COLOR=#000000][FONT=courier]df -h ~ [/FONT][/COLOR]on terminal and double checked with GParted, and both ensured me that I have 54GB of free disk space and the application to be installed is just 200MB.

What may be happening???

Thanks!

---

### Post by papibe on 2014-04-22
Hi yan4.

Could you post the result of that command?

Also, could you post the result of this one?
```
df -i
```
Regards.

---

### Post by Sandgoose on 2014-04-25
I have seen some setups incorrectly calculate free space, try plug in a small usb stick tell wine that it is "drive d:" via winecfg, rerun your setup and tell it to install on d: if it works you can always move it and update the reg files afterwards, worth a shot?

guess you could aways install on on usb drive on a windows box export the reg files and see if it will install/run that way ?

---

