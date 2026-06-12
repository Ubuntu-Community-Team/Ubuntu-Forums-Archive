---
title: "Firefox 32-bit on Ubuntu AMD64"
date: 2009-06-30
forum: x86 64-bit Users
---

### Post by xtjacob on 2009-06-30
I am trying to install Firefox 32-bit on Ubuntu 9.04 AMD64 and when ever I tried to start it i get this error:
```
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 679 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```
What am I doing wrong?

---

### Post by dtoronto on 2009-06-30
did you install it using the tarball or or off of the repositories?
It sounds like you may have used a .tar file, I would recommend installing it by adding the mozilla launchpad daily sources to your repositories and then doing a

```
$sudo apt-get install firefox-3.5
```

here's a quick guide on how to get it rolling

[http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html)

---

### Post by xtjacob on 2009-06-30
What I needed to do was install a 32-bit version of firefox so that i can use java. So I followed these instructions from here: [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#Installing%2032-bit%20Edition%20of%20Firefox](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#Installing%2032-bit%20Edition%20of%20Firefox)

---

### Post by Bert_421 on 2009-06-30
I have tried to install ff 3.5 as tar and the suggested site followed instructions as call out. (play with the synaptic manager no luck even tried deleting ff 3.01 in the manager said it removed it but when I click on the icon guess what ff 3.01 started up Go figure) Still no ff 3.5 same old 3.01 I think. I have been playing with Linux for about 2 months now, and I have to say I don't get the attraction of Linux (Ubuntu). It's not a learn curve it is a *_**PLANETARY ORBIT**_*.  
 

 I really like the look and feel and visual effect that Ubuntu (linux) has to offer, but the time spent getting it to work is ridiculous. Is like if you want to do something using linux you will have to go to the forum to see how it done. 

 

  I sure don't remember Windows being this difficult (learn curve)

---

### Post by jespdj on 2009-07-01
> **Bert_421 said:**
> I sure don't remember Windows being this difficult (learn curve)
Trying to compile Firefox yourself on Windows is at least as difficult as trying to compile it yourself on Linux.

---

### Post by Bert_421 on 2009-07-01
I loaded ff3.5 under 1 min including the download of the 8mg file, in both Windows XP and Windows 7.
and a day later still no ff3.5 on linux (Ubuntu)
 
I am just venting!!:confused::twisted: I spent at least 1.5 hours trying to install it yesterday. i can't beleave it takes so long to install the program.

---

### Post by xtjacob on 2009-07-01
I'm sorry guys but you're getting off topic. I don't need to know how to install firefox 3.5 I need to know how to install the 32-bit version of firefox on a 64-bit version of ubuntu so that I can use java. Can some help me with that?

---

### Post by jocko on 2009-07-02
> **xtjacob said:**
> I'm sorry guys but you're getting off topic. I don't need to know how to install firefox 3.5 I need to know how to install the 32-bit version of firefox on a 64-bit version of ubuntu so that I can use java. Can some help me with that?
Why make things more complicated than they are? Just install the package sun-java6-plugin to get java in 64 bit firefox. Or is there any particular reason you need 32 bit java?

---

### Post by Jimmyfj on 2009-07-02
> **xtjacob said:**
> I'm sorry guys but you're getting off topic. I don't need to know how to install firefox 3.5 I need to know how to install the 32-bit version of firefox on a 64-bit version of ubuntu so that I can use java. Can some help me with that?

Really - There's nothing to it. Go to your System>Administration>Synaptic

Once Synaptic is on your screen you click "Search" - And in the text-field you type "firefox 3.5" and click OK. After a few seconds you'll get the result. Amongst those results are Firefox 3.5 - Click on it and mark it for installation. Click Apply in top of your screen and wait for the install to finish.

Close Synaptic, and go to your Programs>Internet menu. Here you'll find a menu-point named Shiretoko which IS Firefox 3.5 Beta pulled from the repo. There will still be some waiting time before the final release hits the repos, and by that time you'll get it as an update.

EDIT:

On my Ubuntu 64 bit install I have the following packages installed for java:

**ia32-sun-java5, ia32-sun-java6, Sun-java5-bin, Sun-java5-jre, Sun-java6-bin, Sun-java6-jre and Sun-java6-plugin** 

Install those and you have no need for any FF 32 bit as **all** the Java works just fine.

---

### Post by xtjacob on 2009-07-02
I have all of those packages installed and java doesn't work. I look it up on google and everywhere it says you have to have 32-bit firefox with a 32-bit java plugin.

---

### Post by Jimmyfj on 2009-07-02
> **xtjacob said:**
> I have all of those packages installed and java doesn't work. I look it up on google and everywhere it says you have to have 32-bit firefox with a 32-bit java plugin.

That's strange. 'cause I don't need any 32 bit FF to make java work sweet 'n nicely in my 64 bit FF 3.0.1.1 or FF 3.5 Beta - Both flash and Java works fine. I'll bet you have the iceteajava installed, if you do try uninstalling it from Programs>Add/Remove>Internet. My Java don't work as expected with icedteajava installed.

---

### Post by xtjacob on 2009-07-02
Had icetea installed, so I removed it. Still doesn't work.

---

### Post by xtjacob on 2009-07-02
Oh feel kinda dumb, forgot to enable it in firefox! :lolflag:

---

