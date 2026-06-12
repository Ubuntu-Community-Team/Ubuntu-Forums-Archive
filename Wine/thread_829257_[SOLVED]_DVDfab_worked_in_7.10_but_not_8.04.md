---
title: "[SOLVED] DVDfab worked in 7.10 but not 8.04"
date: 2008-06-14
forum: Wine
---

### Post by transporter_ii on 2008-06-14
I'm running crossover office "crossover-standard_6.2.0-1_i386"

On Ubuntu 7.10, DVDfab worked perfect. The same version of DVDfab, with the same version of crossover office, installed on a fresh install of 8.04, gets to the part to enter a registration code or try a free trial, and then just never starts up no matter which one you try and do.

On the bright side, DVDshrink didn't work on 7.10 without some jumping through hoops, and it seems to work in 8.04.

I've looked through log files and I can find no errors...but I'm not exactly sure which file this would go to.

I'm open for any suggestion...


Thanks,

---

### Post by transporter_ii on 2008-06-14
Still not sure the exact issue, but Ubuntu 8.04 breaks Crossover Office and WINE. Just a week ago, I installed IE 6.0 on 7.10 and it worked fine. It also fails to start under 8.04, just like DVD fab.

Apparently, there are some fixes, but they did not work for me. I still have support available for Crossover Office, and I have opened a ticket.

Here it is:

-=-=-=-=-=

This is a problem with multiple apps, but IE60 is a good example.

Approx. a week ago, I installed IE 6.0 on Ubuntu 7.10 and it worked fine. Some hard drive issues and I upgraded to a clean install of Ubuntu 8.04. Now hardly anything works under crossover office. Internet Explorer 6.0 installs fine, but never starts up. DVDfab worked fine under 7.10 but fails to start on 8.04.

I tried the fix for the DOS mem issue and it did not work. When I run command: cat /proc/sys/vm/mmap_min_addr
It returns "0" (My understanding that a system with issues would return non-zero value).

Also a related question, as long as I still have support.

If IE 6.0 or DVDfab failing to start causes an error message, where would it be logged? I have spent well over an hour looking for a log with some helpful information and I can't fine anything.

-=-=-=-=-=-

I will post any helpful information they give me.

Transporter_ii

---

### Post by transporter_ii on 2008-06-24
Here is the IE 6 fix:

From the crossover office link for known issues "CXOffice62_Ubuntu804dosmem," it gives this command:

    sudo sysctl -w vm.mmap_min_addr=0


And it states this will fix it until a reboot. It then goes on to give a permanent fix (sudo gedit /etc/sysctl.conf and change 65536 to 0).

Well, I tried the temporary fix just to see if it would work...and even did a suggested test I found, just to make sure it returned a value of "0." However, IE 6 still refused to even start, much less run.

After opening a ticket, I went ahead and did the permanent fix, and after a reboot, IE 6 just started working.

---

### Post by transporter_ii on 2008-06-24
A reply from Crossover Office support regarding DVDfab:

Our developers tested this several times yesterday and were always able to get DVDfab to install and run with CrossOver 7.0.  Can you tell us more about the system with Ubuntu 8.04 that DVDfab is not functioning on?  Has it been updated recently?

---

### Post by transporter_ii on 2008-06-24
My reply to Crossover Office support:

Thanks for looking at it. My installs went almost like this on two different systems: Install 8.04, did some updates, installed Crossover Office, installed the few Windows programs that I have used in the past...only to find three out of four of them didn't work. And as far as updates, I update my systems almost every time I see an update available (the majority of the time).

After the last time we corresponded, I mentioned that DVDfab 4 mysteriously went to work on one of my systems.

Well, after that, I uninstalled Crossover Office and re-installed it on both systems, and everything went right to work on both systems.

In my opinion, that had to have been something that got updated in Ubuntu.

Regardless, I'm really happy to have the few Windows programs I use going again.

As a side note, I noticed that DVDfab.com specifically says that DVDfab will run under WINE. Personally, I think it should be considered for adding to the supported list, because it is certainly one of the better programs in its area.

---

