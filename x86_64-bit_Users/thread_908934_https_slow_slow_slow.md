---
title: "https slow slow slow"
date: 2008-09-03
forum: x86 64-bit Users
---

### Post by xanapia on 2008-09-03
[COLOR="SeaGreen"]When I connect to a site via https I seem to login alright but after that things are real slow.  
I am using hardy 8.0.4.1 in AMD 64 bit mode, using and AMD Athlon 64 X2 3800+ with 4g of ddr-2 400 memory and everything is on a 260g sata II disk with about 200 g available.  

My Vista Ultimate crapped out so I switched to Ubuntu and there are a few non show stopers I have yet to figure out.

I would appreciate any help or suggestions.

Steve   [/COLOR]  [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by tuxxy on 2008-09-03
Can you give an example to try?

What browser are you using and have you tried a repalcement to see if it could be the problem?

---

### Post by xanapia on 2008-09-03
my main problem is when i go to my banking site.  I use Firefox 3.0.1 and have tried safari and something else.

The bill pay site is [https://ftc.usersonlnet.com/asp/USERS/Common/Login/NetLogin.asp](https://ftc.usersonlnet.com/asp/USERS/Common/Login/NetLogin.asp). but obviously i cant give my info to get in.if i find another one i will update the post

---

### Post by stoian on 2008-11-07
same here, folks. i use firefox 3 from repositories. my banking site is slow at home (ubuntu/firefox) but is fast at work (xp/ie).

what gives?

---

### Post by Kryspy on 2008-11-08
Happens here as well.

Kryspy

---

### Post by cariboo on 2008-11-08
I have one web site that I go to on occasion that just does not work using Firefox in Linux. I have to revert to Vista+IE7 to access the site. I have made my problems known, but I really doubt anything will be done about it. The site btw is bell.ca

Jim

---

### Post by Kryspy on 2008-11-09
This is my main problematic site:

[https://www.txn.banking.pcfinancial.ca/a/authentication/preSignOn.ams](https://www.txn.banking.pcfinancial.ca/a/authentication/preSignOn.ams)

I get the same result using Opera as well.

Kryspy

---

### Post by stephanecharette on 2008-11-10
> **Kryspy said:**
> This is my main problematic site:

[https://www.txn.banking.pcfinancial.ca/a/authentication/preSignOn.ams](https://www.txn.banking.pcfinancial.ca/a/authentication/preSignOn.ams)

I get the same result using Opera as well.

Kryspy

These are known issues, both for Bell and PC Financial.  They have a device on their network which is not correctly dealing with the tcp scaling window size.  The solution and explanation is here:

[http://ubuntuforums.org/showthread.php?t=959637&page=4](http://ubuntuforums.org/showthread.php?t=959637&page=4)

Stéphane Charette

---

### Post by Kryspy on 2008-11-11
Thanks alot.  That fixed it.   I thought it was a LINUX problem. Shame on me for blaming the Penguin :(

Kryspy

---

