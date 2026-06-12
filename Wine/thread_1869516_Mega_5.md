---
title: "Mega 5"
date: 2011-10-25
forum: Wine
---

### Post by Biomante on 2011-10-25
Hi there

I need some help with a program I am trying to run in ubuntu via Wine (MEGA 5). I manged to install it, but when I try to launch it from the terminal it doesn't works, and I get this message:

fixme:resource:GetGuiResources (0xe4,0): stub

Thanks for any help.

---

### Post by raja.genupula on 2011-10-26
> **Biomante said:**
> Hi there

I need some help with a program I am trying to run in ubuntu via Wine (MEGA 5). I manged to install it, but when I try to launch it from the terminal it doesn't works, and I get this message:

fixme:resource:GetGuiResources (0xe4,0): stub

Thanks for any help.

whats wine version you have ?

---

### Post by Biomante on 2011-10-26
Wine 1.2

---

### Post by raja.genupula on 2011-10-27
Hi man

upgrade your version of wine to 1.3 for better functionality .

all the best.

---

### Post by Biomante on 2011-10-27
No use. When I install MEGA 5, wine 1.3 gets uninstalled and wine 1.2 is installed.
Can anyone give some information about this error report? :

fixme:resource:GetGuiResources (0xe4,0): stub

Thanks

---

### Post by Biomante on 2011-10-29
Bump

---

### Post by Peter3000 on 2011-12-03
Hi Biomante

Di you find a solution? I'm having the same bug. 

First I get : /bin/cp: cannot stat `/usr/local/bin/MEGA/Private/Help/Roboex32.dll': No such file or directory
 
then it tries to execute MEGA and goes into the:

 GetGuiResources (0xe4,0): stub

I downloaded Roboex32.dll, and created the destination but it still says: /bin/cp: cannot stat `/usr/local/bin/MEGA/Private/Help/Roboex32.dll': No such file or directory

Please let me know if you have a solution!

---

### Post by Biomante on 2011-12-03
Sorry, no solution yet. I have not received any answer from the MEGA team, and their forums have been down for months now. Unfortunately now I am forced to run MEGA in Windows ...  ](*,)

---

### Post by deatom on 2012-02-06
Hi there,
I just ran into the very same problem.
Setting a lower Windows version enviroment for MEGA5 helped for me.

You can do that running winecfg. Set the Windows version to Windows ME.

---

### Post by Biomante on 2012-02-06
Thanks deatom!!

It seems to be working. :)

---

### Post by oscaredd on 2012-02-07
I had the same problem running the program, and was able to solve it in the same way!!!

Thanks!

---

### Post by bidax on 2012-03-26
Thanks! Worked like a charm.

---

### Post by Biomante on 2012-05-13
More problems, I upgraded to precise and now MEGA is not working again...
I tried reinstalling it, but I get this message (file attached).


Any ideas?

---

### Post by Biomante on 2012-05-18
Bump

---

