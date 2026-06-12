---
title: "compiling source code YPOPS"
date: 2007-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by kyrhash on 2007-06-26
Ok i want to use a program called YPOPS to get access to my yahoo mail account within mozilla thunderbird.  The site says that it must be compiled from source, so i downloaded a file which is called ypops_0.8.6.2_linux_x86.tar.bz2 to my desktop.  From there i am at a loss on what to do.  I am almost completely new to linux so go slowly plz.

[YPOPS!]("http://ypopsemail.com/index.php")

---

### Post by david_2001 on 2007-06-26
Before you jump into compiling, does your yahoo mail account not allow you to set up POP & Forwarding?  Mine does, which means I can access it from Thunderbird without any additional software.

EDIT: That package you downloaded seems to contain a binary file, so no compilation will be necessary.

---

### Post by kyrhash on 2007-06-26
nope i don't think mine does, do you pay for yours or is it free?

and what do you mean a binary file which one is it?  How do i run it?  Sorry for all the  questions but like i said i am a noob at this.

---

### Post by kyrhash on 2007-06-26
maybe i just don't know what im doing, how is your thunderbird account cofigured and what options did you do online in yahoo mail.

---

### Post by david_2001 on 2007-06-26
> **kyrhash said:**
> nope i don't think mine does, do you pay for yours or is it free?

and what do you mean a binary file which one is it?  How do i run it?  Sorry for all the  questions but like i said i am a noob at this.
My yahoo mail account is free.  Bearing in mind that the ypops you have downloaded could be a trojan or spyware - apparently there are a number of bogus versions of yahoopops and I have no idea how to tell the real version from a fake - if you really want to run the binary then open the file you downloaded with archive manager (right click on the file and select Open with "Archive Manager"), click the extract icon in the archive manager toolbar and pick an extract location then navigate to that location with Nautilus and double-click on ypops.

---

### Post by tskariah on 2007-06-28
You could download the debian package for ypop from here: [YPOPS! for Ubuntu (i386.deb)]("http://www.geocities.com/t_skariah/ypops/")

based on YPOPS! version 0.8.8.

---

### Post by Mgiacchetti on 2008-06-27
that package is crap it will not work on my system.. i have changed the ports to 5110 and 5025 and still get "cannot connect to local host: connection refused"

i opened the system monitor and noticed that ypops isnt even running.  after sudo /etc/init.d/ypops start    i get the same exact thing.  i do sudo /etc/init.d/ypops restart i get "not running"    [ok]  so i figure its ok now since it said so and check my system monitor... guess what..  nothing.


just for fun to see if it would throw an error i did this:   

```
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ sudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops start
 * Starting ypops daemon: ypops                                          [ OK ] 
michael@AMD-64:/$ gksudo /etc/init.d/ypops restart
 * Restarting ypops daemon: ypops                                                
not running                                                             [ OK ]
michael@AMD-64:/$ gksudo /etc/init.d/ypops stop
 * Stopping ypops daemon: ypops                                                  
not running                                                             [ OK ]
michael@AMD-64:/$ gksudo /etc/init.d/ypops force-reload
 * Restarting ypops daemon: ypops                                                
not running                                                             [ OK ]
michael@AMD-64:/$ gksudo /etc/init.d/ypops force-reload
 * Restarting ypops daemon: ypops                                               
not running                                                             [ OK ]
michael@AMD-64:/$ gksudo /etc/init.d/ypops force-reload
 * Restarting ypops daemon: ypops                                                
not running                                                             [ OK ]
michael@AMD-64:/$ gksudo /etc/init.d/ypops force-reload
 * Restarting ypops daemon: ypops                                                
not running                                                             [ OK ]
michael@AMD-64:/$ gksudo /etc/init.d/ypops stop
 * Stopping ypops daemon: ypops                                                 
not running                                                             [ OK ]
michael@AMD-64:/$ gksudo /etc/init.d/ypops restart
 * Restarting ypops daemon: ypops                                                
not running                                                             [ OK ]

michael@AMD-64:/$ sudo apt-get remove ypops --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ypops*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 474kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 153784 files and directories currently installed.)
Removing ypops ...
Purging configuration files for ypops ...
 Removing any system startup links for /etc/init.d/ypops ...
   /etc/rc0.d/K01ypops
   /etc/rc1.d/K01ypops
   /etc/rc2.d/S99ypops
   /etc/rc3.d/S99ypops
   /etc/rc4.d/S99ypops
   /etc/rc5.d/S99ypops
   /etc/rc6.d/K01ypops

```

--edit--
BTW  after doing all that... it still didnt check my mail or show up in system monitor   i think your package is broke tskariah

---

### Post by tskariah on 2008-07-22
could you please check the log files ? or post it here ? 

thanks.

---

