---
title: "Opera is not working"
date: 2008-05-07
forum: x86 64-bit Users
---

### Post by kabel_kabel on 2008-05-07
I installed the opera_9.50b2-20080422.2-shared-qt_amd64.deb file but is not working. I go to Applications --> Internet --> Opera nothing happens, is not loading. Does somebody knows what is going on? 

I know that is beta release but this is ridiculous. One thing after another. I have Firefox 64-bit 3.0b5 and the font antialiasing works perfect but i have some problems with flash. I decided to install Firebox 32-bit 2.0.0.14 and the problems with flash and java are gone, but now the font antialiasing is horrible. I have tried to tweak this antialiasing thing, no luck at all. So, finally i thought that i'll give a try with Opera 64-bit beta and Opera cannot even start, no error messages, plain nothing.

Thank you all
Kabel

---

### Post by kabel_kabel on 2008-05-07
This is the output

kabel@kabel-pc:~$ opera
exec: 222: /home/kabel/bin/opera: Argument list too long
kabel@kabel-pc:~$

and this output is after 5 min waiting, before that i had just a blinking cursor

---

### Post by kabel_kabel on 2008-05-07
Dear All,

I tried with stable Opera, and guess what, the same answer: Stable Opera is not working either.

Another question - since i have both Firefoxes 32-bit and 64-bit, does anybody knows if there is a chance "flash always on top" to be solved? Is pretty annoying when you go to nba.com, bestbuy.com, circuitcity.com … (it is a long list) and flash covers the menus of the web page.

Thank you all,
Kabel

---

### Post by kabel_kabel on 2008-05-09
Thank you guys helping me to solve this problem.

Kabel

---

### Post by isecore on 2008-05-09
You should demand a refund.

---

### Post by darco on 2008-05-09
Let's see, I have 2 pending threads over 2 days old with NO responses...sometimes its just luck that a knowledgeable person reads your threads and responds.
Anyways you can try to post the thread at the Opera forum ;)
good luck

darco

---

### Post by Sef on 2008-05-10
> Thank you guys helping me to solve this problem.

How did you solve your problem?

---

### Post by | MM | on 2008-05-10
> **kabel_kabel said:**
> This is the output

kabel@kabel-pc:~$ opera
exec: 222: /home/kabel/bin/opera: Argument list too long
kabel@kabel-pc:~$

and this output is after 5 min waiting, before that i had just a blinking cursor

How did you install the package?  dpkg or using the gtk installer?  if you apt-get remove opera, then dpkg -i /dir/of/package/opera_9.50b2-20080422.2-shared-qt_amd64.deb are there any erro messages?


> **kabel_kabel said:**
> Another question - since i have both Firefoxes 32-bit and 64-bit, does anybody knows if there is a chance "flash always on top" to be solved? Is pretty annoying when you go to nba.com, bestbuy.com, circuitcity.com &#8230; (it is a long list) and flash covers the menus of the web page.

Meh, for that you'll just have to wait for Adobe... that could be a while.

---

### Post by kabel_kabel on 2008-05-12
Dear all,

Thank you for your response.

> How did you solve your problem?
I did not solve it. I have decided that i will use Ubuntu again when Adobe fixes "flash always on top" bug. In the mean time i will use Vista x64 Ultimate.

> How did you install the package? dpkg or using the gtk installer? if you apt-get remove opera, then dpkg -i /dir/of/package/opera_9.50b2-20080422.2-shared-qt_amd64.deb are there any error messages?
First i have installed 32-bit Opera with --force-all, no errors but i couldn't start it; then i tried to remove it with dpkg -p command and ended up removing the folders and everything manually; then i thought lets try with 64-bit and nothing again, i cannot start it. I removed it manually because automatic feature is not working (folders were still present) and finally i tried with the last version of stable opera from their web site - same thing - nothing loads up. When i tried to load from the terminal after five minutes of waiting i got that error message "exec: 222: /home/kabel/bin/opera: Argument list too long".

So, thank you again, i have decided not to use Ubuntu until Adobe fixes their problem. I did not know that Opera is not open source software, so fixing the problem associated with Opera is not going to change the situation. I can live without Opera, but i cannot live with bad font antialiasing and "flash always on top".

Kabel

---

