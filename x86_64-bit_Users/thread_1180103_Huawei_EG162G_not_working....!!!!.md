---
title: "Huawei EG162G not working....!!!!"
date: 2009-06-06
forum: x86 64-bit Users
---

### Post by shahdharmit on 2009-06-06
Hello all..

I'm new to Ubuntu. I use Ubuntu 9.04. I've this Huawei EG162G USB modem. I'm in India and use Idea Net Setter. It worked perfectly well in Fedora 10 and the previous 32-bit release of Ubuntu without any extra configurations. I just used to plug it and Network Manager would detect it and I would surf.

But in Jaunty I can't surf. NM detects it, I get connected and get an IP addresss assigned as well but then I can't surf. I use Firefox. My box is fully updated as well. Firefox just keeps loading and loading till long with no site opening up. Kindly help me out. Thanks in advance.

---

### Post by shahdharmit on 2009-06-06
Hello all..

I'm new to Ubuntu. I use Ubuntu 9.04. I've this Huawei EG162G USB modem. I'm in India and use Idea Net Setter. It worked perfectly well in Fedora 10 and the previous 32-bit release of Ubuntu without any extra configurations. I just used to plug it and Network Manager would detect it and I would surf.

But in Jaunty I can't surf. NM detects it, I get connected and get an IP addresss assigned as well but then I can't surf. I use Firefox. My box is fully updated as well. Firefox just keeps loading and loading till long with no site opening up.

I downloaded KPPP as mentioned in one of the posts on this forum but it didn't even get installed. Kindly help me out. Thanks in advance.

---

### Post by cariboo on 2009-06-06
You may want to uninstall network-manager-gnome and install gnome-network-admin and give it a try. Once you have uninstalled network-manager you will only get a small bar graph in the notification area. To setup the network connection go to System-->Administration-->Network.

---

### Post by GeorgeVita on 2009-06-06
Hi **shahdharmit**,

as you are connected, right click Network Manager icon and then see through "Connection Information" if the **/dev/ttyUSB0** is used and if you have **valid DNS** numbers.
For your tests disable Wireless (if any) and disconnect from Ethernet (just to avoid other conflicts).

Regards,
George

---

### Post by shahdharmit on 2009-06-11
I installed gnome-network-admin but i can't find its applet anywhere. How do I use it?

And as far as checking dns n stuffs is concerned, it's showing me everything perfectly. So i don't think it's a DNS number issue.

---

### Post by phantom@atom-desk on 2009-06-12
[http://technolark.blogspot.com/2009/05/idea-netsetter-on-ubuntu-jaunty.html](http://technolark.blogspot.com/2009/05/idea-netsetter-on-ubuntu-jaunty.html)

Somebody got it working.
Tell me if you get it to work. I am planning to buy one

Regards

---

### Post by Raaj on 2009-06-28
> **phantom@atom-desk said:**
> [http://technolark.blogspot.com/2009/05/idea-netsetter-on-ubuntu-jaunty.html](http://technolark.blogspot.com/2009/05/idea-netsetter-on-ubuntu-jaunty.html)

Somebody got it working.
Tell me if you get it to work. I am planning to buy one

Regards

yeah, that's my blog .. I got it working. i've given enough details out there, lemme know if u got some problem ..

---

