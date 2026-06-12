---
title: "Trying to connect to Office network-Win 2003"
date: 2008-09-23
forum: x86 64-bit Users
---

### Post by trestamanos on 2008-09-23
there is probably more than one way to do this......

option 1

I am running Ubuntu 8.04 and through Virtualbox, I am running windows where i could map the drives to get access to the office server folders?  Permission nor access is not an issue.  The problem is I don't think it can be done for the detaisl tab tells me that Share folders (none) and remote display is disabled-this is a free version of virtualbox.

--------

OPtion 2

I would love to have access thorough Ubuntu bypassing Windows but i don't know enough and I am not sure it can be done?

Can anyone help?

Thanks in advance.

tres

---

### Post by cariboo on 2008-09-24
I'm not really sure what you are trying to do, but if you are trying to access windows shares on a server, in windows just go to my network places and the shares should show up automagically. The same with Ubuntu, go Places-->Network and double click on the Windows network icon. the network shares should show up. the only thing you may have to change is the workgroup and that can be done in Network Manager.

One other thing to check is to make sure you have networking set to nat in Virtualbox.

Jim

---

### Post by trestamanos on 2008-09-24
Cariboo,

thank you for your reply.  i was afraid of not explaining myself better.....which probably explains for the lack of feedback.  :lolflag::lolflag:

i didnt even know that "Network" was under places.  I will definitely mess with it.  I saw network tools under Administration.....

RE Windows.....i've mapped many drives (by NO MEANS i am an expert net admin).and i thought i knew how.

Im not using a domain.  Our network workgroup-on Windows- is called 211MANASOTA.  I changed that field by right clicking on the computer icon, then Computer name tag, etc.
Still doesnt show under net admin
Could it be an issue cause of running win through virtual box?  thnx again.

tres

---

