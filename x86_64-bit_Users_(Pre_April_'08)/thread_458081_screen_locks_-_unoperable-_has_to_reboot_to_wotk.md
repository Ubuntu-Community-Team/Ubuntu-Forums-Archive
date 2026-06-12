---
title: "screen locks - unoperable- has to reboot to wotk"
date: 2007-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by rodolfoarce on 2007-05-29
Hello guys:

I'm using Ubuntu Feisty (7.04) Server, with ubuntu-desktop installed

It worked just fine whith the server install, but when i added ubuntu-desktop the system crashes every day or so.. The only way to make work again is by rebooting

When trying to  switch to console (Ctrl + Alt + F1) the screen changes but the system remains crashed.. no servers (httpd,bind,samba) work

The system is completely updated and upgraded  (apt-get upgrade)

I've seen a lot of errors of this sort in othe system envoiroments (pc,ppc,etc) so i'm guessing that is not just a x86_64 issue

---

### Post by incubus on 2007-05-29
rodolfo,

After rebooting to get the system to work again, can you get the log files?  They are in /var/log/
In particular, I would take a look at dmesg, kern.log, syslog, and perhaps Xorg.0.log since it seems that it crashes when you're using X.

Any graphics card?

incubus

---

### Post by rodolfoarce on 2007-05-29
I don't see anything suspicios in any of the logs..

I forgot to mention that this machine had a double boot with winxp and centos before.. and has been working perfectly for quite some time with the other Operating Systems

---

### Post by incubus on 2007-05-29
Strange...

You mentioned that you can switch to the other terminals via ctrl+alt+f1, right?  Can you actually log in there?  Or are you getting a blank screen?

incubus

---

### Post by rodolfoarce on 2007-05-30
nop, I cannot switch to another terminal.. Ctrl + Alt + F(n) DOES NOT work.. i mean, it actually changes what you see on the screen but it doesn't affect the system itself

I switch to the first terminal and the screen changes it colors, but i type the login and password and type shutdown or reboot and doesn't work.. i press the reboot combination and it doesn't work either

my entire system is render unoperable.. no services work.. nor the ssh-server.. absolutley nothing works

---

