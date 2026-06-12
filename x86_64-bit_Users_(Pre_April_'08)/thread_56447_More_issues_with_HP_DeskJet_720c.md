---
title: "More issues with HP DeskJet 720c"
date: 2005-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by manfo on 2005-08-12
Ok, let's start it over :-)

Since I still couldn't get CUPS to print with my HP DeskJet 720c, I tried to look for something else. According to [this nice tutorial](http://xlife.zuavra.net/columns/20030315/), I simply tried to do a ```
echo -e "This text should appear on the printer\f" > /dev/lp0
```

(I assume the device is right--parallel port), but this won't work either.

Permissions on /dev/lp0 are set to 660 (which, I think, is ok), but I keep getting these:

```

manfo@ubuntu:~$ echo -e "This text should appear on the printer\f" > /dev/lp0
bash: /dev/lp0: Permission denied
manfo@ubuntu:~$ sudo echo -e "This text should appear on the printer\f" > /dev/lp0
Password:
bash: /dev/lp0: Permission denied
manfo@ubuntu:~$

```

Ok. Then I tried to chmod /dev/lp0 to 777. This is what I got:

```

manfo@ubuntu:~$ sudo chmod 777 /dev/lp0
Password:
manfo@ubuntu:~$ echo -e "This text should appear on the printer\f" > /dev/lp0
manfo@ubuntu:~$ sudo echo -e "This text should appear on the printer\f" > /dev/lp0
manfo@ubuntu:~$

```

That is, I don't get the "Permission denied" error anymore, but the printer just sits there and gets nothing done...

What next? :-)

Bye
.m

---

### Post by DancingSun on 2005-08-12
You probably need to do this in the root terminal.  Open up Applications -> System Tools -> Root Terminal, then enter that echo command.

---

### Post by manfo on 2005-08-12
[QUOTE=DancingSun]You probably need to do this in the root terminal.  Open up Applications -> System Tools -> Root Terminal, then enter that echo command.[/QUOTE]

Ok, I did it, but nothing happens :-(
(I start thinking that this is a *printer* problem... I'll try it on a Windows box.)

Thanks anyway! :-)
.m

---

