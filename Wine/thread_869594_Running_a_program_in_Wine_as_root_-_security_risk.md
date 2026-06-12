---
title: "Running a program in Wine as root - security risk?"
date: 2008-07-25
forum: Wine
---

### Post by King Crimson on 2008-07-25
Hi,

I'm running Kubuntu 8.04.1 with Wine 1.1.1. My problem is somehow non-standard and unusual, therefore I hope some guru might read this and suggest some nice solution...

After reading the Wine FAQ I realize that I shouldn't be running Wine as root or with sudo, since that gives the Windows application full control and access to the system, but in my special case I somehow see no other choice... unless any of you have a better suggestion!

I badly need a program for UDP logging from my dreambox satellite receiver (that is also running linux). I know I could simply run **netcat -u -l -p port_number**. But even though it works, the output is totally unformatted and looks like garbage. So since I couldn't find an alternative native linux application for that end, I turned to 3CSysLog, which is a free w32 program from 3com. In Windows, this runs just fine - it has a nice GUI and formats the output in a very nice and readable manner.

The only disadvantage of this program is that it has a fixed listening port (514). In Linux, any program that wants to have access to ports below 1024 needs root privileges to do so - if I try to run this program as normal user in Wine I get an error: binding to port 514 prohibited.

Therefore, I tried to run the program with: **sudo wine "/home/marek/.wine/dosdevices/c:/Program Files/syslog/3CSyslog.EXE"**. But that didn't work either - the system complained that "./wine is owned by another user" (I can't remember the exact wording, but it was something very similar).

I therefore saw no other choice than to issue the command **sudo chown -R root:root ~/.wine**. After that, finally, the program runs flawlessly after invoking it with **sudo wine "/home/marek/.wine/dosdevices/c:/Program Files/syslog/3CSyslog.EXE"**.

Of course, there's a big disadvantage of that "pathetic hack": now all programs need to be run in Wine as root. Therefore, three questions:

1.) Do you guys see any other (better) solution to the above problem?
2.) If not, do you know any other native Linux application for UDP logging, preferably with a GUI?
3.) If not, is the above solution really a huge security risk providing that I know exactly which programs I'm running and that I won't be running any viruses/malware etc.?

I'd be much obliged for an answer...

King Crimson

---

### Post by kdorf on 2008-07-25
tcpdump doesn't have a GUI, but will format your packets. You can configure it to capture only certain ports if you like. (`man tcpdump` for more info)

(yes, it also does UDP packets)

---

### Post by King Crimson on 2008-07-25
Thx for the tip, tcpdump actually looks quite promising - the packets are formatted correctly. After reading the manual and playing around a bit I came up with the following line:

**sudo tcpdump -i eth1  udp port 514 -v**

The -v option is necessary since otherwise "Msg: CCcam" messages are not displayed, and they are the only ones I care about. This gives for example the following output:

```
07:47:57.005915 IP (tos 0x0, ttl 64, id 2633, offset 0, flags [DF], proto UDP (17), length 128) 192.168.1.4.2208 > x64-desktop.local.syslog: SYSLOG, length: 100
        Facility daemon (3), Severity debug (7)
        Msg: CCcam: client XXX ecm request for handler 0xf640 [|syslog]
07:48:02.077297 IP (tos 0x0, ttl 64, id 2634, offset 0, flags [DF], proto UDP (17), length 90) 192.168.1.4.2208 > x64-desktop.local.syslog: SYSLOG, length: 62
        Facility daemon (3), Severity debug (7)
        Msg: CCcam: local ecm -> card /dev/sci0 0x100(0xXXX) si[|syslog]
07:48:02.499137 IP (tos 0x0, ttl 64, id 2635, offset 0, flags [DF], proto UDP (17), length 69) 192.168.1.4.2208 > x64-desktop.local.syslog: SYSLOG, length: 41
        Facility daemon (3), Severity debug (7)
        Msg: CCcam: local ecm <- card /dev/sci0 ok
07:48:02.501641 IP (tos 0x0, ttl 64, id 2636, offset 0, flags [DF], proto UDP (17), length 127) 192.168.1.4.2208 > x64-desktop.local.syslog: SYSLOG, length: 99
        Facility daemon (3), Severity debug (7)
        Msg: CCcam: client XXX ecm request for handler 0x64 0x[|syslog]

```

Now, to make this perfect - is there any way to filter out the first and second line so that only messages beginning with "Msg: CCcam:" are displayed and the whole rest is ignored? I found nothing about that in the manual...

KC

---

### Post by kdorf on 2008-07-25
You can pipe the output through grep. Something like this should do the trick:

```
sudo tcpdump -i eth1 udp port 514 -v | grep "Msg: CCcam"
```

Any line that does not contain the magic phrase "Msg: CCcam" will not be displayed. Note that the middle character is a vertical bar (pipe).

---

### Post by King Crimson on 2008-07-25
Thank you very much, that really did the trick. :-)

KC

---

