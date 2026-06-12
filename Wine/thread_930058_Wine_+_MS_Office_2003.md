---
title: "Wine + MS Office 2003"
date: 2008-09-25
forum: Wine
---

### Post by PParent03 on 2008-09-25
Hi,

I'm beginner with Ubuntu and I have to use Microsoft Office 2003. I have installed Wine and after I have installed Microsoft Office 2003 Pro but, the installation stop at the step "Registering user". I&#8217;ve tried to restart the installation but no success. If somebody can help me with this issue, I would really appreciated. 

Thanks in advance


EDIT: Finally, I've resolved my problem. I had to change this line in system.reg 
&#8220;RegisteredOwner&#8221;=&#8221;Change preferred owner in ~/.wine/system.reg&#8221;

---

### Post by ooobuntooo on 2008-09-26
Try PlayonLinux or Crossover Office instead of wine.
They should get MS Office to work.

---

### Post by jualin on 2008-09-26
> **PParent03 said:**
> Hi,

I'm beginner with Ubuntu and I have to use Microsoft Office 2003. I have installed Wine and after I have installed Microsoft Office 2003 Pro but, the installation stop at the step "Registering user". I’ve tried to restart the installation but no success. If somebody can help me with this issue, I would really appreciated. 

Thanks in advance


EDIT: Finally, I've resolved my problem. I had to change this line in system.reg 
“RegisteredOwner”=”Change preferred owner in ~/.wine/system.reg”

I am getting the same issue, how did you change that line? When I open the system.reg file I see that line in several places all over the file. Did you change the line in all of them or only an specific one? Also what did you change it to?
Thank you in advance!

---

