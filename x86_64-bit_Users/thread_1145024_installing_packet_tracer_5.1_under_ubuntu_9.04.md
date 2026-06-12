---
title: "installing packet tracer 5.1 under ubuntu 9.04"
date: 2009-05-01
forum: x86 64-bit Users
---

### Post by alfa16vjtd on 2009-05-01
Hi I'm trying to install packet tracer 5.1 under ubuntu but I've troubles starting packet tracer after installation.
 
Here is what I did
 
I first untarred the archive
Then I installed the packet using sudo ./install
Then the installere asked two questions
 
1) the folder I should install it in I used /usr/local/packettracer
2) I he should create a link, here i accepted the default and the installer placed a link
    under /usr/local/bin

When I trie to open packettracer with the command packettracer the program however doesn't open but i get the notion packet tracer 5.1 starting.
 
Thx in advance
Kevin

---

### Post by alfa16vjtd on 2009-05-06
I didn't find how to manage the install in ubuntu but I managed to install packettracer under wine and it works fine that way

---

### Post by knichel on 2009-06-11
You have to download the generic linux installer for PT5.1 from Cisco site and some 32 bit libs and it installs  fine .

---

### Post by Cortux on 2009-08-10
> **knichel said:**
> You have to download the generic linux installer for PT5.1 from Cisco site and some 32 bit libs and it installs  fine .

I am having the same issue above, would you be so kind as to advise or post link on where I could download this from and how to install.

Thanks

---

### Post by Cortux on 2009-08-10
/usr/local/bin# ls
furiusisomount  packettracer

Packet tracer is highlighted in red and furiusisomount is in green. Furiusisomount works and packettracer does not initiate when typing in the terminal. 

Does this mean there is an error with the installation, how could i resolve this.

Someone please help.

---

### Post by knichel on 2009-08-10
You need to obtain the Generic Linux install version of Packet Tracer from the NetAcad website.  Click on the link to Packet tracer and look for the Generic version.

---

### Post by Cortux on 2009-08-10
Could you please post the link for me, I cant find it.

---

### Post by knichel on 2009-08-10
If you are a member of the Cisco NetworkAcademy just log in to your account and the link is on the left side of the page.  You cannot get to the software unless you are a member.  That means you have to have taken or teach a class for Cisco.

[http://www.cisco.com/web/learning/netacad/index.html](http://www.cisco.com/web/learning/netacad/index.html)

---

### Post by Cortux on 2009-08-10
> **knichel said:**
> If you are a member of the Cisco NetworkAcademy just log in to your account and the link is on the left side of the page.  You cannot get to the software unless you are a member.  That means you have to have taken or teach a class for Cisco.

[http://www.cisco.com/web/learning/netacad/index.html](http://www.cisco.com/web/learning/netacad/index.html)


Ok, I have taken the cbt nuggets, I dont know if that qualifies me.

BUT, I just managed to get it working. The terminal did not want to work, instead I wen into Home, Packet tracer, bin, then packet tracer again, and just mapped it as a menu app and it works great, thank you very much to all that helped. Knichel mainly.

I just have one more issue regarding the packet tracer, Theres no sound like the ones in windows when you open up cli and build networks. Can I get this working and how.

---

### Post by knichel on 2009-08-10
You can change the sound settings along with other settings in "Options->Settings"...

---

### Post by Cortux on 2009-08-10
> **knichel said:**
> You can change the sound settings along with other settings in "Options->Settings"...

Sound is ticked as active.

Is there any other resolve, maybe to do with the os

---

### Post by knichel on 2009-08-10
Well, other than making sure your sound card is working with linux and the volume is up... no, sorry.

---

### Post by Cortux on 2009-08-11
> **knichel said:**
> Well, other than making sure your sound card is working with linux and the volume is up... no, sorry.
 
Well, at least its working, thats sufficient. The sound doesnt really make much difference. 
 
Thanks Knichel.

---

### Post by knichel on 2009-08-11
To be quite honest, the sound is the first thing I turn off when I install it anyway.  IT gets kind of annoying.

---

### Post by Cortux on 2009-08-12
Your probably right, 
 
Thanks again for the assistance.

---

