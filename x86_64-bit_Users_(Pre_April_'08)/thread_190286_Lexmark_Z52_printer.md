---
title: "Lexmark Z52 printer"
date: 2006-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by TWFJR on 2006-06-06
Just upgraded to DapperDrake6.06, running 64bit AMD processor. Printer worked before upgrade.  Printer is configured using "High Quality Image (Gutenprint) (en) (Suggested)."  Z52 Properties:  Driver:  Lexmark; Z52; and, driver listed above.   Configuration says that the printer is "ready."  It is also listed as default.  What happens when trying to print test page or any other page is that the printer gives up blank paper.  Any suggestions as to what needs to be done?

---

### Post by Don Wood on 2006-08-14
I can second this request.  I am running dapper with the 686 kernel on amd-64.  When I use the included driver for the Lexmark Z52 all I get is a blank page for each job I send to the printer.  Any ideas?

---

### Post by Game_Ender on 2006-09-12
I am using the standard 32bit Ubuntu and I have the same blank page problem.

---

### Post by Game_Ender on 2006-09-12
I have posted a bug about this on launchpad [here]("https://launchpad.net/distros/ubuntu/+source/gutenprint/+bug/60073"). Please go there an confirm/comment on the bug some we can hopefully get this issue resolved.

---

### Post by Kilz on 2006-09-12
I don't think its a bug. I think you just have the unlucky experience to own a lexmark. They are notorious for the worst printer support for Linux of any company. I replaced a z32 that did the same thing with a hp after spending days on it.

---

### Post by osaeris on 2006-09-12
Kilz, 

I was upgrading my friends house from a mess of windows boxes to all ubuntu (bar one gaming laptop). I avoided a potentially frustrating time with their Lexmark z32 after reading previous forums. I ditched the lexmark and got them an Epson C62. It's braw. I plugged it in, added it in the print dialogue, set up CUPS then forgot about it.

Sometimes you just have to buy something. 

PS My 64 bit dapper is working nicely. 

Steve

---

### Post by Kilz on 2006-09-12
> **osaeris said:**
> Kilz, 

I was upgrading my friends house from a mess of windows boxes to all ubuntu (bar one gaming laptop). I avoided a potentially frustrating time with their Lexmark z32 after reading previous forums. I ditched the lexmark and got them an Epson C62. It's braw. I plugged it in, added it in the print dialogue, set up CUPS then forgot about it.

Sometimes you just have to buy something. 

PS My 64 bit dapper is working nicely. 

Steve

Thats what I did, sometimes its easier to replace something than bang your head into a wall ](*,)  With Lexmark its a lot of banging. My brother had a lexmark to when I installed Ubuntu for him (stoped the "my windows is messed up" calls dead). He went and got a epson 3800 when the lexmark didnt work.

---

### Post by Game_Ender on 2006-09-12
I understand, I know Lexmark has bad Linux support, but if the z52 won't work with the driver it should tell me that, not let me setup the printer. I would assume a developer at least tested on one z52 to confirm it worked before adding to the list of printers the driver works with.

So in short:  If it lets me "install" the printer it should work, if they are known not to work then I shouldn't be able to install it.

---

