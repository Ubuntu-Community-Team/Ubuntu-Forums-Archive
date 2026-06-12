---
title: "Java applet makes puts Firefox in a loop  (Intrepid AMD64)"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by edantes on 2008-11-03
In the interest of full disclosure, I am running the following setup:

**Ubuntu 8.10 amd64 com Firefox 3.03,  IcedTea6-plugin, openjdk-6-jre**

The ONLY (congrats to the Ubuntu folk, great distro) problem with Intrepid AMD64 goes as follows.  *Banco do Brasil* online banking system uses an applet with a virtual keyboard for users to enter their passwords.  This applet starts and displays correctly with my setup, until I try send the entered password.  Firefox goes into a mad loop.

You don't need an account nor Portuguese skills to try it out.  Go to this address:

[https://www2.bancobrasil.com.br/aapf/login.jsp?aapf.IDH=sim](https://www2.bancobrasil.com.br/aapf/login.jsp?aapf.IDH=sim)

Enter a mock password by clicking on the numbers under "Teclado virtual" and press the "Entrar" button.  You are  officially in a loop, you might need to restart Firefox to get out of it.  The message in Firefox error log is
```

Error: Permission denied to get property XULElement.disabled
Source File: https://www2.bancobrasil.com.br/aapf/includes/js/aapf.js
Line: 421

```

Could this be a problem with the 64-bit plugin?

I also tried this page with Opera using sun-java6 jre, but the applet won't even start.

The reason I am bothering you with this is to get  opinions on where the bug report should go.  Mozilla? The Bank? OpenJDK?

Thanks in advance.

---

### Post by MindFlayer on 2008-11-03
Got the same problem here with another online bank. I'd say it's probably a firefox or openjdk issue.

---

### Post by Nintendo01 on 2008-11-03
I'd also say it's either firefox or java, but probably java. While playing an online game (RuneScape) when I hit the quit button ingame it's supposed to bring me back to the homepage, but it gives me a 404 page not found error and I still hear the (albeit glitchy due to a known icedtea java problem with RuneScape) music. I have to quit firefox completely to get java to shutdown and stop my intel dual core processor from running at 100%. Once, java didn't even shut down when firefox closed and I had to kill the java process in the system monitor, even end process didn't work, I had to kill it. It also gives me 404 errors sometimes when I try to log in to the website using the java powered login. When I do manage to login, java keeps running at about 20% processor until I close firefox, it used to close out as soon as I got logged in. Before I upgraded from hardy, I never had any of these problems.

---

### Post by 73ckn797 on 2008-11-09
I have never been able to get Java to work in Ubuntu 64 Hardy. From what I understand Intrepid Java will not work either. That is my only hold up to using the 64 Ubuntu. It is a Java issue. They do not have a 64 bit Java last I heard or looked into it.

---

### Post by echovolutionx on 2008-11-09
:confused::confused::confused:

---

### Post by jamesstansell on 2008-11-09
> **73ckn797 said:**
> I have never been able to get Java to work in Ubuntu 64 Hardy. From what I understand Intrepid Java will not work either. That is my only hold up to using the 64 Ubuntu. It is a Java issue. They do not have a 64 bit Java last I heard or looked into it.

It might be time to look into it again.  Intrepid has the icedtea6-plugin package which has been working for a number of people.

(Hardy had the icedtea-gcgwebplugin package which worked for a number of people but suffered from not having the java <--> javascript liveconnect functions.  Liveconnect is one of the main things that the intrepid package fixes.)

-james.

P.S.  Sun has created a 64-bit plugin but theirs is not released yet.  Check back in about 3-4 months for that implementation.

---

### Post by 73ckn797 on 2008-11-10
> **jamesstansell said:**
> It might be time to look into it again.  Intrepid has the icedtea6-plugin package which has been working for a number of people.

(Hardy had the icedtea-gcgwebplugin package which worked for a number of people but suffered from not having the java <--> javascript liveconnect functions.  Liveconnect is one of the main things that the intrepid package fixes.)

-james.

P.S.  Sun has created a 64-bit plugin but theirs is not released yet.  Check back in about 3-4 months for that implementation.


I will check the icedtea package again. I know it did not work for me in Hardy 64 bit.

I knew something was coming in 64 bit. At least my wait is several months closer than before!

---

### Post by 73ckn797 on 2008-11-10
> **jamesstansell said:**
> It might be time to look into it again.  Intrepid has the icedtea6-plugin package which has been working for a number of people.

Installed the icedtea6-plugin but does not work. I have need to uploads photos daily and the Aurigma Image Uploader does not work in a 64 bit Java.

---

### Post by Kralnor on 2009-02-16
Got the same problem here with Intrepid, although this is the 32-bit version. However, I have only encountered this with one specific applet, which used to work in previous versions of Ubuntu and also works under both 32bit WinXP and 64bit Vista.

Applets used for online banking seemingly work fine.

Sorry for bumping an old thread, but I have tried numerous re-installations of Java and several plugins. Still not getting it to work.

---

