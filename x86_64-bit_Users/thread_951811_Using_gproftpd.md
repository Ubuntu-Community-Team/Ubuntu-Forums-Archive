---
title: "Using gproftpd"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by etdsbastar on 2008-10-18
Hello friends,

I am having some queries regarding setting up an ftp server for personal/commercial use:

1. How to use gproftpd provided with ubuntu.
2. Is there requires a special permission from someone to set up a ftp server.
3. Is it totally legal to use ftp server on the internet.
4. Is it compulsory to have static IP address for using and setting up an ftp server.
5. How can I setup an personal/commercial ftp server in ubuntu using gproftpd.

Thanks in advance

Regards.

---

### Post by cariboo on 2008-10-18
> 1. How to use gproftpd provided with ubuntu.

You have to run gproftd as root, to do this press Alt-F2 and enter:

```
gksu gproftpd
```

Enter your password when asked. The just fill in the blanks.

> 2. Is there requires a special permission from someone to set up a ftp server.

Not as far as I know. Check your local lwas

> 3. Is it totally legal to use ftp server on the internet.

Millions of people do, but check your local laws.

> 4. Is it compulsory to have static IP address for using and setting up an ftp server.

It is recommended that you have a static ip, but you can use services like noip.com and dydns.com, they are both free.

> 5. How can I setup an personal/commercial ftp server in ubuntu using gproftpd.

Install proftpd, gproftd is just a graphical configuration file editor for proftpd. Proftpd is in the repositories and you can use Synaptic Package Manger to install it.

Jim

---

### Post by Dufangoer on 2008-10-19
&#12288;&#12288;A man really loved a woman, but he was just too shy to propose to her. Now&#12288;he was up in his years and neither of them had ever been married. Of course,&#12288;they dated about once a week for the past six years, but he was so timid he&#12288;just never got around to suggesting marriage much less living together. &#12288;&#12288;But one day, he became determined to ask her the question. So he calls her on the phone, "June." &#12288;"Yes, this is June." &#12288;&#12288;"Will you marry me?" &#12288;&#12288;"Of course I will! Who's this?"cheap wow power leveling --------------------------------**buy [eq2 plat](http://www.epaxx.com),  [eq2 gold](http://www.epaxx.com), [everquest platinum](http://www.epaxx.com), [rs gold](http://www.favgames.com/rs-gold/), [silkroad gold](http://www.favgames.com/silkroad-gold/),**

---

### Post by etdsbastar on 2008-10-19
Thanks Jim,

Let me try the solutions provided by you first...

---

### Post by etdsbastar on 2008-10-19
Hey,

Its becoming impossible for me. Please give me another solution ...

---

### Post by etdsbastar on 2008-10-23
> **cariboo907 said:**
> You have to run gproftd as root, to do this press Alt-F2 and enter:

```
gksu gproftpd
```Enter your password when asked. The just fill in the blanks.



Not as far as I know. Check your local lwas



Millions of people do, but check your local laws.



It is recommended that you have a static ip, but you can use services like noip.com and dydns.com, they are both free.



Install proftpd, gproftd is just a graphical configuration file editor for proftpd. Proftpd is in the repositories and you can use Synaptic Package Manger to install it.

Jim

Jim,. I tried everything ...
Give me a clear and quick solution please...

---

### Post by Nepherte on 2008-10-23
Try this: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by cariboo on 2008-10-23
If you install proftpd, you should be able to access it using the default configuration. The really is no need for a gui as the configuration file in /etc/proftpd is pretty well commented and can be edited with a normal text editor.

Press Alt-F2 and type:

```
gksu gedit /etc/proftpd/proftpd.conf
```

I have never used gproftpd as the one time I looked at it, It didn't show any of the comments, which is kind of useless when you are trying to set the program up.

Jim

---

