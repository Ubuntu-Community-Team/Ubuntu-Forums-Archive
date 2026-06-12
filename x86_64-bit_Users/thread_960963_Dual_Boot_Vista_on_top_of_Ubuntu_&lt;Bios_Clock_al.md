---
title: "Dual Boot: Vista on top of Ubuntu &lt;Bios Clock always Changing&gt;"
date: 2008-10-27
forum: x86 64-bit Users
---

### Post by wasistloss on 2008-10-27
I have had a nice Ubuntu installation going for a couple months now, and with getting an SSD I have been installing Vista 64-bit over and over (too many dangerous file downloads).  (I welcome the day of DirectX independence).

My computer was made March 07.

I used EasyBCD to write to the Vista inconsiderate boot loader to allow Grub.

Everytime I boot into Ubuntu 8.04, when I return to Vista.... the clock from the CMOS/bios level is knocked forward 4 hours.

Don't see any posting about this.....

Should I just replace my CMOS battery?

---

### Post by felker2 on 2008-10-28
This is probably caused by the setting that Ubuntu sets GMT in your CMOS clock and Vista sets the local time in your CMOS clock.

Solution: set both OSes to the same method, so both GMT or both localtime.

---

### Post by wasistloss on 2008-10-28
So I verified that Ubuntu time setting is using America/New_York, which does not state explicitly GMT, but seems to be EST.  Vista 64bit is using GMT EST as well, and once again come back to Vista and the clock is pushed forward 4 hours.  I also tried using the server time updating in Ubuntu with same results (also set to America/New_york).

You said one or the other may be using local time, but I did not actually see this as an option in Ubuntu.  There is no other option in Vista but GMT.

So I"m thinking this may not be the solution.

Thank you,
Vasses Louse

---

### Post by felker2 on 2008-10-29
What does your /etc/default/rcS say about UTC? Here's my setting:

```
sander@ubuntu810:~$ cat /etc/default/rcS | grep UTC
UTC=no
sander@ubuntu810:~$
```

If you have "UTC=yes", your CMOS clock is set to UTC/GMT, which is the explanation for your time problem. See [http://ubuntuguide.org/wiki/Dapper#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29](http://ubuntuguide.org/wiki/Dapper#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29)

---

### Post by wasistloss on 2008-10-29
Ok so problem solved by entering value UTC=no.

So this is because Microsoft doesn't use UTC?

Also that link you posted on dapper I found the UTC/GMT link which was dead. So I just turned to no and problem solved.

Thank you,
Vasses

---

### Post by felker2 on 2008-10-30
> **wasistloss said:**
> Ok so problem solved by entering value UTC=no.

Thank you,
Vasses

You're welcome. You can press the "Thanks"-medal in my post ... ;-)

Sander

---

### Post by novafluxx on 2009-04-06
Thanks! Just did a search and found this! Exactly the answer I needed!

---

