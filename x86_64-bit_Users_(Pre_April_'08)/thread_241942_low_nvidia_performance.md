---
title: "low nvidia performance"
date: 2006-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by scatyb on 2006-08-23
So I got the latest kernel update, reinstalled the nvidia drivers and all is well.  Except all gl apps are SOOO SLOW.  I ran glxgears and with the nvidia settings moved to performance, I could barely squeek out 100fps.  i thought I found a thread about this a while ago, but I cant find it again.  Sorry for asking again.


Nvidia fx5200
AMD64 3.2ghz
1.5gigs DDR333
80gig ata100

thanks.

---

### Post by scatyb on 2006-08-23
Also, after reboot, i'm stuck at 640x480. It won't let me go higher. And I forgot to mention, the driver version is 8762-amd64.  I believe that's the latest.

Thanks for your help.

---

### Post by John.Michael.Kane on 2006-08-23
What kernel are you using?

Did you compile it yourself?

---

### Post by scatyb on 2006-08-23
Well, it's the latest dapper, with the correct update, not 10.3.  i didn't compile it myself, I downloaded the 64bit iso from the website(this one).  

thanks.

---

### Post by John.Michael.Kane on 2006-08-23
So what guide did you use install your drivers?

---

### Post by scatyb on 2006-08-23
I used tselliot's? guide method #1.  seemed to work.  I stopped X then restarted it and all seemed well.  But I fully rebooted a little later and that's when I got locked at 640x480.

---

### Post by John.Michael.Kane on 2006-08-23
Can you try running ```
**sudo dpkg-reconfigure xserver-xorg**
```

---

### Post by scatyb on 2006-08-23
Well I can go home and try it after work, looks like it will though.  The question remains however, why am I getting such slow performance when alot of others on this forum are getting like 12k fps?  baffling.

---

### Post by John.Michael.Kane on 2006-08-23
scatyb i'm not sure why your having bad performance. i know i'm running a fairly lowend geforce 6100igp, and all seems ok. i too used tselliot guide. 

Also when you can post your sudo gedit /etc/X11/xorg.conf .

---

### Post by scatyb on 2006-08-23
I can get one posted in a few hours.  Work isn't over just yet.

I suppose I should get remote desktop setup eh?

---

