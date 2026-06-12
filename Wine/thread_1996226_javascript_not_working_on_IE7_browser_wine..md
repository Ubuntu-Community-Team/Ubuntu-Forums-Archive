---
title: "javascript not working on IE7 browser wine."
date: 2012-06-04
forum: Wine
---

### Post by saru1683 on 2012-06-04
Hi,

I am new to wine and I have installed wine 1.4  in Ubuntu 12.04 LTS. 
Using Winetricks I have installed IE7.

my problem is with javascript on IE7 browser not working.
I have also checked that javascript is already enabled by default.

my simple html file code with javascript is
```
<html><head><script type="text/javascript">alert("test javascript");</script></head><body><noscript>javascript enabled </noscript><p>&nbsp;&nbsp;&nbsp;</p></body></html>
```.

you can see this is Simple javascript but not working with IE7 wine.

---

### Post by lisati on 2012-06-04
*Thread moved to **Wine**.*

---

### Post by cogadh on 2012-06-05
My only suggestion would be don't use Internet Explorer, it doesn't actually work in Wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=25](http://appdb.winehq.org/objectManager.php?sClass=application&iId=25)

Is there are reason you need IE and can't simply use the native browser?

---

### Post by saru1683 on 2012-06-05
Thanks Cogadh,

I have develop website as per client requirement using fully javascript and jQuery. He is using Window XP and he checks website's functionality in IE7 Browser thats why I need IE7 just for testing purpose. If is thare any way to work in wine than well and good other wise I have to install Window XP.

Thanks, 
Sanjay

---

### Post by cogadh on 2012-06-06
For testing website code functionality against IE, I strongly recommend against trying to do it through Wine. Not only is it nearly impossible to get IE to work properly in Wine, even if it did run, you can't trust that it will actually function the same way it works on Windows, due to the incompleteness of Wine. You'd be better off installing XP in a virtual machine or dual-booting (personally, I prefer the VM, much less hassle).

---

### Post by saru1683 on 2012-06-07
Thax for your reply Cogadh,

I will go for installing XP in dual-booting.

Thanks,
Sanjay

---

### Post by na5h on 2012-06-07
Actually, it is possible to test websites in IE9, 8 and 7 on Linux. Microsoft has created some customized Windows VHDs for this purpose:

[http://www.webupd8.org/2011/09/test-websites-in-internet-explorer-9-8.html](http://www.webupd8.org/2011/09/test-websites-in-internet-explorer-9-8.html)

The disk space required is RIDICULOUSLY large though!

---

### Post by saru1683 on 2012-06-08
VHDs is batter way compare to wine but space is big problem, and  just for testing purpose I  dont want to use it.

Thanks for helping me.

---

### Post by dgatwood on 2012-07-02
And the Windows licenses on those disk images expire about three weeks from now, according to the download page.  It doesn't make much sense to spend a day downloading something that's just going to stop working in a few weeks.

---

### Post by badjem79 on 2012-11-09
I solved this problem by reading the winehq page related to ie7

> 
winetricks -q msxml3 ie7 
sleep 30 # allow WINE to finish writing to disk 
wine iexplore 'www.example.com'


The solution is to install msxml3 aside ie7, then javascrit starts to work, I'm so happy :KS i did register in the forum to share the workaround!

Cheers!

PS F##k the thousands GB VHDs...

---

