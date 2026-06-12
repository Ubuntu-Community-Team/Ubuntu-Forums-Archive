---
title: "My Dapper Drake is slow----please help me"
date: 2006-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by gopi on 2006-06-27
Hello everyone
i am using the HP Compaq nx6125 model laptop, i used the Ubuntu 5.10 64bit, and now i installed the 6.06 one which is 64bit. The Daper Drake is very slow what should i do. It logs in very slow, starts the applications very slow. Please help me....with some tips or installation arguments or customization techniques. 

thanx.

---

### Post by heldal on 2006-06-27
[QUOTE=gopi]Hello everyone
i am using the HP Compaq nx6125 model laptop, i used the Ubuntu 5.10 64bit, and now i installed the 6.06 one which is 64bit. The Daper Drake is very slow what should i do. It logs in very slow, starts the applications very slow. Please help me....with some tips or installation arguments or customization techniques. 
[/QUOTE]

Do applications run slow too, or is it just startup that is slow. Many people have been bitten by IDE performance problems lately, caused by the HAL-daemon (hald) constantly polling optical drives, blocking any IDE harddrive on the same channel. In this case::

[LIST]
[*]does it make a difference to the performance if you put a data CD (mountable) in the drive?
[*]Try stop the relevant service (sudo /etc/init.d/dbus stop) and check if that makes a difference. 
[/LIST]

Further information on this problems can be found in other threads:

[http://ubuntuforums.org/showthread.php?t=188901](http://ubuntuforums.org/showthread.php?t=188901)

[http://ubuntuforums.org/showthread.php?t=200125](http://ubuntuforums.org/showthread.php?t=200125)

... not sure if this applies to your box.

---

### Post by andram on 2006-06-29
please try also to use the "noapic nolapic" bootparameters if you did not yet.
See also:
[http://www.ubuntuforums.org/showthread.php?t=182136]("http://www.ubuntuforums.org/showthread.php?t=182136")

---

