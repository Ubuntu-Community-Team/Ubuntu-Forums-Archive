---
title: "Need pointers"
date: 2009-11-10
forum: x86 64-bit Users
---

### Post by ganeshmallyap on 2009-11-10
Hi all,

I have installed Ubuntu Karmic AMD64 on my home desktop. It is working wonderfully and I am very happy with its overall performance.  Now I wanted to find out the answers for the following questions related to this computer system.

1.  How many 32 bits applications/processes are running currently.  And what are their process ids.
2.  How many 32 bits applications are installed currently in my system.
3.  What is the executable file name OR process ID of the application running in active window.
4.  What is the version of the Flash installed in my computer.
5.  I had installed proprietary version of Sun Virtualbox (3.0.x) downloaded from vendor's website.  When I run 32bit OS from this application, it works just fine.  But while running a 64 bit OS, it throws an error message something like - 'This software needs x86_64 type platform. But available is i686 type".  How do I fix this?
6.  What is the best solution for converting videos from one format to another without loss of quality?  I tried HandBrake & Mobile Media converter in my past system installation on Jaunty 32 bits.  But I was not happier with the results.  The output quality was quite poor. In my new system, I am unable to install both of these softwares.  Anyway, I am looking for a better solution.
7.  I have installed WINE software.  But I am not able to run few tiny Win32 applications through WINE.  Is there a way we can run Win32 applications through WINE in AMD64?

Thanks a ton in advance.

Ganesh

---

### Post by bford16 on 2009-11-10
I can answer some of these questions, but not all.

1. I don't know how to identify 32-bit processes, but I'm sure there is a way.
2. Same answer for #2.  But most of your installed apps will be 64-bit.  The Flash plugin is 32-bit by default.  Some video drivers require 32-bit software as well.
3. You can find the executable name of a program by adding the launcher to the panel, then right-clicking on the panel icon and selecting 'Properties.'  To find the process ID, open a terminal window, and run the 'ps aux | grep [process name]' command. In the example below, I have looked up the current process information for firefox.  The second line of the result includes the 'grep' process, because I have used 'grep firefox' to filter the results of the 'ps aux' command.  The vertical line between 'ps aux' and 'grep firefox' is called a 'pipe.' You can find the pipe symbol on the backslash key.  The pipe is used to send the result of one command to another command.```
ps aux | grep firefox
barry     1945  4.2 10.7 542544 81636 ?        Sl   06:24   1:39 /usr/lib/firefox-3.5.4/firefox --sm-config-prefix /firefox-twt1P9/ --sm-client-id 1088e85addb28cda85125781154878214000000018170036 --screen 0
barry    18310  0.0  0.1   7336   884 pts/0    R+   07:03   0:00 grep --color=auto firefox

```4. You can find the version of Flash by right clicking on any Flash object in the browser window, and choosing Properties.
5. I think Virtualbox only supports 32-bit guest Operating Systems.
6. Don't know about this. You might be better off trying to find a player for the current format.  Almost every type of video can be played on a GNU/Linux system.
7. Wine is a limited framework for running Windows software natively on Linux.  Some software works perfectly, some works halfway, many programs will not run at all.  Visit WineHQ for more details.  32-bit applications will run on WINE on a 64-bit OS.

---

### Post by ganeshmallyap on 2009-11-10
Thank you so much bford16.  Couple of my doubts got closed with your reply.

---

### Post by sanderj on 2009-11-11
> **bford16 said:**
> 

1. I don't know how to identify 32-bit processes, but I'm sure there is a way.


From the top of my head:

You can use 'file <executable>' to see it's 32/64-bitness. From the process / top / ps -af (-ax ?) overview, you can distill the executables, and thus determine the bitness.

So 'file /usr/lib/firefox-3.5.4/firefox' and 'file `which grep`' should give the 32- or 64-bitness. I think you can write a nice one-liner to automagically parse the process list and give the bitness of each process.

Again: this is from the top of my head, so details can differ.

---

### Post by timgood on 2009-11-11
VirtualBox can be used to run 64 bit operating systems, and has been able to for a while.

---

### Post by pbrane on 2009-11-11
Adobe flash comes in 64-bit too. ([http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")) I have been using it for about a year now with no problems. Another way to find out what flash version you are running is to go to **about : plugins** in Firefox. (Don't put spaces before or after the colon, I had to do this to keep from creating a smileyface) This way you not only get the version installed but also confirm that it is installed in a way that Firefox can use it.

---

### Post by ganeshmallyap on 2009-11-14
Thank you all for your time, attention and valuable replies.  Each of my questions were answered now.  Further 64 bit OS on Virtualbox started working after I enabled the checkbox by name "Enable PAE/NX" under Settings->System->processor tab of virtualbox client. Thanks again.

---

### Post by keplerspeed on 2009-11-14
[http://xkcd.com/138/](http://xkcd.com/138/)

---

### Post by Emanuele_Z on 2009-11-14
> **keplerspeed said:**
> [http://xkcd.com/138/](http://xkcd.com/138/)
32bit pointers... :-)

---

