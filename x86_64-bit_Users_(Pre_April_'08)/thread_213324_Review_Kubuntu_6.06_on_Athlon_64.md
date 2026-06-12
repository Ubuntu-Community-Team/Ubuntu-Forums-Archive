---
title: "Review: Kubuntu 6.06 on Athlon 64"
date: 2006-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by michux on 2006-07-11
I wrote a review of [Kubuntu 6.06 on Athlon 64](http://en.jakilinux.org/linux/ubuntu/kubuntu-606-on-athlon-64/). It covers installation and basic configuration including:
- getting the restricted formats support (including MOV, WMV, RealAudio)
- installing the 32-bit apps (Opera, Skype...)
- getting the Firefox plugins (Flash, Java)
- installing NVIDIA 3d drivers
- enabling DVD playback
- adding fine iPod support

Most of the information I gathered is easily accessible via Ubuntu forums and Wiki, but I still spent a few long hours configuring my new Kubuntu amd64 box. That's why I thought an article like that could be helpful.

Feel free to enter your comments and suggestions.

---

### Post by JoWilly on 2006-07-11
This is an excellent review / howto.

There should be a sticky at the top of this section and an entry in the ubuntu wiki (or maybe a link in an existing wiki entry).

---

### Post by Lil_Eagle on 2006-07-11
Indeed, very well done.  I'm also interested in the server aspects of the machine.  You mention:
> But it will also acts as a Apache web server with PHP and SVN support, parallely running a postfix mail server,which is the reason why it should be as reliable and multitasking-capable as possible.
I currently have another machine running DSL with Monkey Web Server, because it's an old machine.  It sucks up power, and I would rather combine the functions with Kubuntu running the 64-bit kernel.  I have no trouble setting up apache as it's almost point and click, but the mail server is another issue.  It would be my primary desktop as well as the server.

If you could add the details of the server side of the setup, I think many people would be interested.  It's far less expensive to have your own server than to hire out.  More importantly, if it goes down, you can fix it yourself and not have to rely on someone else to do it.

---

### Post by Kilz on 2006-07-11
A few things
I do believe the Macromedia flash is version 7, not 6. The wiki howto on installing 32bit Firefox needs some updating. It still links to firefox 1.5 not 1.5.0.4.

---

### Post by llanitedave on 2006-07-11
Great review!  It answered some questions I've been dealing with on my system.  I can't wait to try some of your fixes!

---

### Post by michux on 2006-07-12
> **Lil_Eagle said:**
> If you could add the details of the server side of the setup, I think many people would be interested.  It's far less expensive to have your own server than to hire out.  More importantly, if it goes down, you can fix it yourself and not have to rely on someone else to do it.

I'm going to prepare an article on Subversion setup running on Apache2 with secure authentication and roles. 

Concerning the Postfix setup, it's a very simple script used just for sending Wordpress activation e-mails for people registering on the vortal. Not a lot to describe here.

---

### Post by The Keeper on 2006-07-12
These days only working flash and w32codecs (without any hacks or dirty tricks) seems to be about only thing preventing the jump to 64-bit, everything else needed for day-to-day work works right away.

---

### Post by Lil_Eagle on 2006-07-12
> These days only working flash and w32codecs (without any hacks or dirty tricks) seems to be about only thing preventing the jump to 64-bit, 
While there isn't a 64-bit flash yet (blame adobe) you can install firefox32 with and flash (java and mplayer as well) by simply downloading and running the wonderful script that kilz made.  You can find it [here]("http://www.ubuntuforums.org/showthread.php?p=1174435")
I do believe that is mentioned in the howto.

---

### Post by michux on 2006-07-12
> **Lil_Eagle said:**
> While there isn't a 64-bit flash yet (blame adobe) you can install firefox32 with and flash (java and mplayer as well) by simply downloading and running the wonderful script that kilz made.  You can find it [here]("http://www.ubuntuforums.org/showthread.php?p=1174435")
I do believe that is mentioned in the howto.


Thanks. I added the link to my article.

---

### Post by michux on 2006-07-14
By the way, if you this it's worth it, you can [digg this article](http://digg.com/linux_unix/Kubuntu_6.06_on_Athlon_64). Then more people will get aware of the fact that Kubuntu can run nicely on amd64.

---

