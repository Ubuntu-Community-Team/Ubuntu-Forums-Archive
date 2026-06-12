---
title: "firefox stopped working"
date: 2005-05-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by lgl on 2005-05-18
Hi ,

     I have been using firefox on my system but two days ago it stopped working. Evolution has stopped working also. My system shares the adsl connection through an xp box.

It was fine before this time and all I have done is install java into the /opt folder. I can ping my other machine fine. Any ideas about how to fix this.

Thanks Leon

---

### Post by Bitchcassidy on 2005-05-18
[QUOTE=lgl]Hi ,

     I have been using firefox on my system but two days ago it stopped working. Evolution has stopped working also. My system shares the adsl connection through an xp box.

It was fine before this time and all I have done is install java into the /opt folder. I can ping my other machine fine. Any ideas about how to fix this.

Thanks Leon[/QUOTE]
 Hum ...
If you launch firefox or evolution from a terminal, what is your output ?

---

### Post by lgl on 2005-05-18
I will do that when I get home from work and post it if I can't fix it myself.

Just to say I am amzed at the speed of the response.

---

### Post by lgl on 2005-05-18
no output whatsoever just comes back to the prompt.

Also i am getting destination host unbreachable now when I ping

---

### Post by lgl on 2005-05-23
ok I have got it back to being able to ping the Windows machine. I have gone back to the windows machine and set it up again for sharing its Internet connection. I still cannot connect to the Internet from my ubuntu box. I am now pulling my hair because from my blinkered position it should be working.

Could anyone give me some suggestions as to where to look next.

set up is

AMD64 3200 
1 gb ram
Asus k8vdeluxe motherboard

/etc/network/interfaces
auto eth0
iface eth0 inet static
address 192.168.0.2
mask 255.255.255.0
gateway 192.168.0.1 
up route add -host 192.168.0.1 eth0 

Windows box has static address 192.168.0.1 and the sharing process has been done. 

What should Firefox settings be?
How do I check Windows? (I think the problem may be here actually) ](*,)  ](*,)  ](*,)

---

### Post by shady on 2005-05-23
you need help with your nunnery computer

---

### Post by lgl on 2005-05-23
I just want some pointers as to what could be wrong. Someone elses previous experience maybe.

---

### Post by Bitchcassidy on 2005-05-23
What is your network architecture ?
Kind of modem ? do you have a switch or a router? how do you share your connection (which equipment)?

I guess it would be easier to configure linux as a web gateway than wind$, with an ip forwarding if you have two network cards on it ...

---

### Post by lgl on 2005-05-24
[QUOTE=Bitchcassidy]What is your network architecture ?
Kind of modem ? do you have a switch or a router? how do you share your connection (which equipment)?

I guess it would be easier to configure linux as a web gateway than wind$, with an ip forwarding if you have two network cards on it ...[/QUOTE]

It is a two computer peer to peer.
Sagem fast 400/800 (I tnihk that is what it is called I am at work at the moment)
The windows machine should just share the connection. It was working up until about a week ago.

All I can think that I have done since then is 
           two or three updates
           installed Java into /opt
           run dpkg -xorg configure (think that is the right command reconfigure x)
           

I could possibly share it the other way around but I haven't looked at adding the drivers for my adsl modem yet I thought I could do that as a future project as it was working. I have also re-installed Windows (surprise) as it was locking a lot. I have re-run the sharing process and I think I should be in the same position as I was before but obviously I am not. Any thoughts would be appreciated.

---

### Post by vextorspace on 2005-05-24
The java plugin is the cause.  delete it from /usr/lib/mozilla-firefox/plugins/ directory and firefox will start again.  I have not found a java plugin that works.  Or a flash plugin.  I noticed some libc6 errors last time I tried.  I wonder if it has to do with the libraries in lib not being executable.  (I seem to recall it being a permission denied error).

-Doug

[QUOTE=lgl]Hi ,

     I have been using firefox on my system but two days ago it stopped working. Evolution has stopped working also. My system shares the adsl connection through an xp box.

It was fine before this time and all I have done is install java into the /opt folder. I can ping my other machine fine. Any ideas about how to fix this.

Thanks Leon[/QUOTE]

---

### Post by lgl on 2005-05-27
I had a look there was nothing in that directory.

---

