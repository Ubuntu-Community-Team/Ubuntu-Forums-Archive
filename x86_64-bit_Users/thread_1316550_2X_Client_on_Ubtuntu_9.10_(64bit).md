---
title: "2X Client on Ubtuntu 9.10 (64bit)"
date: 2009-11-06
forum: x86 64-bit Users
---

### Post by dgoosens on 2009-11-06
dear fellow ubunteros,

I hope someone has a solution to my little issue.

I have to connect to a Windows server in order to run some Windows Apps.
Our company uses the 2X virtualization for this.

This worked great on Ubuntu 9.04 by using the 2XClient I found here:
[http://www.2x.com/applicationserver/as_manual/2XApplicationServer-Installi-3.html](http://www.2x.com/applicationserver/as_manual/2XApplicationServer-Installi-3.html)

I just upgraded to Karmic... and the 2XClient won't work anymore...
I "installed" the application as I did on Jaunty but when I launch the program I get:
```

#:/opt/2X/Client/bin/2XClient
bash: /usr/local/bin/2XClient: No such file or directory

```
This is strange, as the file does exist...

I tried running as user and root and also tried to "chmod +x" it but it won't work...

Any ideas/suggestions ?


ps: Apart from this issue, Karmic Koala Rules !

---

### Post by Barafu Albino Cheetah on 2009-11-06
Bash can't start your application --> the problem is with file, not some libraries. Check sure, that 
1) app is really there. 
2) that file is not a symlink to non-existing file. 
3) that file has executable paermissions.

---

### Post by dgoosens on 2009-11-06
thanks for you reply...
as I mentionned in my initial post... I checked all of the points you mention...

However, I don't know why and/or how, but I just tried to install it again... and suddenly it works...

I am guessing there was some kind of dependency missing, maybe java...

but thanks,

---

### Post by Barafu Albino Cheetah on 2009-11-06
Any sort of dependency missing would produce another errors. I guess it was symlink missing.

---

