---
title: "Firefox 3 it's locking my system"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by WenSes on 2008-06-21
I'm using ubuntu 8.04 and firefox 3 (final). For some reason firefox, from time to time locks everything. Not even my mouse respond. Nothing... it completly freezes.

It's weird, because since with ubuntu 7.10 and betas/rc's from firefox I never got a result like this...

Any Ideas what to do?

EDIT: I happened me with opera too!!!... So it seems the problem it's ubuntu and not firefox... Gosh this sucks big time... It seems I'll have to chance distro for this... no explination and mayor problem...

---

### Post by pixel :-) on 2008-06-22
check the CPU/memory usage.Is it when you load a page?Are you doing something else at the same time?Do you use swap?Check system monitor.How ancient is your computer?:lolflag:

It could be a bug,are you doing something special you can think of?It's the same page?The page have flash?

---

### Post by JerichoKru on 2008-06-22
I think it may be an issue on Mozilla's end.

It does the same thing with my Fedora 9 install...so, Its not just an Ubuntu issue

---

### Post by pixel :-) on 2008-06-22
I have no problems.It could be a specific add on that misbehaving.**Run firefox in a terminal**, and hope for error mesages when this happens.And again, **check CPU/memory usage**.It could be a memory leek... well we need more info.

"It does the same thing with my Fedora 9 install...so, Its not just an Ubuntu issue "
Well, since linux distributions are copying each other madly,this is not surprising.

---

### Post by WeeWoh on 2008-06-22
Its probably a bug at mozilla's end. Try disabling all the addons and see what happens. Is it just a few particular pages or is it all round? If it is visit them using a different web browser and/or a different distro.

---

### Post by WenSes on 2008-06-22
My PC it's an athlon 64 +3200, 1 Gb ram, 160 HB, but 60 to Ubuntu and 100 to Windows and a radeon 9550 ATI video card. My actual version of Ubuntu it's 8.04, which I installed from zero (formatted pc before install). 

I can't use the terminal for diagnosis, since my PC halts completly... I can't move mouse, can't use keyboard... in fact I can't even turn off my PC normally (have to use the reset botton). 

I don't think it's a matter of Ram or CPU, since FF wasn't working hard at the moment of the problem. In fact, twice were problem that occurred only when I was opening my gmail, having at max, only two other tabs (no flash pages, only blogs).

For more data I can tel you, I downloaded swiftweasel, which I prefered over FF to use... but swiftweasel had the same issue and was occurring even often than FF.

On other hand, I didn't had this problems in Ubuntu 7.10. 

So... I'm confussed.

Now I'm using opera and running fine. In fact, usin ie4linux runs internet explorer 6 without problems.

Any ideas? I want my FF back!

---

### Post by pixel :-) on 2008-06-22
revert to firefox's last beta.It's 99% the same.

---

### Post by Sukarn on 2008-06-23
I was having similar issues when my swap had suddenly stopped being automounted for some reason. My computer used to grind to a halt when I opened one or two softwares. After rebooting a couple of times I checked "free -m" and saw that swap was being shows as 0, which made me realize that swap wasn't being automounted. I tried fixing that and that fixed the issue for me.

---

