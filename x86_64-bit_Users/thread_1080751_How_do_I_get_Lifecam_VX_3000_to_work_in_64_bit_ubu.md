---
title: "How do I get Lifecam VX 3000 to work in 64 bit ubuntu 8.10 intrepid"
date: 2009-02-25
forum: x86 64-bit Users
---

### Post by kotoro on 2009-02-25
My webcam model is Microsoft Lifecam VX 3000;

I have tried adapting to instructions by the following:
[http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)
and following the instructions here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280657](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280657)

to install these

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)

and I installed both of these, as well as attempting to use the gspca source that came preloaded with  Ubuntu intrepid 8.10 64 bit. I don't know what I've done wrong, but none of it worked at all, and I now fear that I've got drivers fighting with each other for dominance. I need guidance to clear out all the driver sets and install the best one for my case, or to just work forward from here in such a way as to get the damn thing working.


--edit to clarify a bit I DID get the source files to compile into *.ko  files, but beyond that I'm not sure whether I did the right things. A lot of linux help seems to be written with the assumption that we know what to do once we get to a certain point. I can assure you that I am used to hardware, and I'm pretty accustomed to windows, but I have very little experience with linux, so I have absolutely no idea what I'm doing.

---

### Post by kotoro on 2009-03-12
Still no progress, I'm sure theres a simple solution, but I'm just too noobish to figure it out.

---

### Post by athaki on 2009-03-13
It's a microsoft product.  Ergo, you won't get it to work. I had the exact same camera and just gave it to my mom.  If you're feeling adventrous, here's a link. [http://ubuntuforums.org/showthread.php?t=381188]("http://ubuntuforums.org/showthread.php?t=381188")

---

### Post by rosewood on 2009-03-13
> **athaki said:**
> It's a microsoft product.  Ergo, you won't get it to work.

Well actually I have a MS LifeCam VX-1000 which did work with Hardy. It seemed to already have a suitable driver as I didn't have to do anything. Unfortunately it does not seem to work with Intrepid though.

---

### Post by jesterthejedi on 2009-03-22
Working after 6 months of waiting and searching forums. My cam is the dreaded Microsoft VX-1000.

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file (top of page little text link called bz2)
extract archive (you can extract with nautilus)
in terminal "cd /Desktop/gspca" + <TAB> or exact name <ENTER>
in terminal type "make" no quotes takes about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

I am so happy that I should pinch myself. I bought this webcam in June for my birthday and it was always a pain in the butt to solve. Success at last!

---

### Post by sansor on 2009-03-23
Works... I couldn't get it working in Skype, though...

---

