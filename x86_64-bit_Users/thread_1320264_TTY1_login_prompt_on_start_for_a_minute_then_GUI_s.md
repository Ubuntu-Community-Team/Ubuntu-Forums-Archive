---
title: "TTY1 login prompt on start for a minute then GUI starts..."
date: 2009-11-09
forum: x86 64-bit Users
---

### Post by atleastitsnotcrack on 2009-11-09
I've recently upgraded to 9.10 and found this great new feature which adds a minute to the start up time.
Heres how I see it:
I get the Ubuntu splash briefly then back to this:

Starting up
Ubuntu 9.10 user-desktop tty1
user-desktop login:

If I leave it, it will start the GUI after a minute or so

If I login it will give details of memory usable and such of the system with various other details and the terminal prompt. after 10~20 seconds the GUI starts.

I searched around for a considerable time hoping to be able solve this with the guidance of other's experiences of similar behavior to no avail.

Any idea's?

---

### Post by Giblet5 on 2009-11-09
Incredibly slow or resource-starved PC?

Running from disk drives configured to run in PIO mode?

Synchronous file systems?

---

### Post by atleastitsnotcrack on 2009-11-09
Sorry,

PC is not resource starved 2600mhz dual core AMD 2gig ram blah blah blah

Hard drives are in DMA mode as per BIOS

Sorry this NOOB doesn't know what a synchronous file system is...But I can tell you the drive is paritioned into 3 drives, 40gig for linux file system, 100gig for windows the hungry pig, reminder 500gig for general storage.  

Didn't have this issue on 8.04~9.04.

GUI boots very fast much faster in 9.10 then it did in 8.04 but this login issue delays things.

How does one enable or find bootlogs for ubuntu? so I can find more information for help with this issue

---

### Post by atleastitsnotcrack on 2009-11-09
More Info:
After logging into TTY1 as per the details in the first message the following system information is presented by the terminal

CPU 2.79%
Memory 2%
Processes 194
HDD 32%

and that I can graph the information with the help of the website landscape.conical.com

Sorry I wish I tell you more.

---

### Post by atleastitsnotcrack on 2009-11-11
Ok after grub I see this screen:
[http://www.virtualpixel.de/wp-content/uploads/2009/10/usplash.jpg](http://www.virtualpixel.de/wp-content/uploads/2009/10/usplash.jpg)

Then tty1 comes up requesting login.

Then after what feels like forever like a pot beginning to boil this screen appears:
[http://digitizor.com/wp-content/uploads/2009/09/xsplash.png](http://digitizor.com/wp-content/uploads/2009/09/xsplash.png)

Is this a problem with usplash??

I found the logs they were right under my nose that is why they are so hard to find :)
Searching for tty1 within them returns not found
I can't find anything that could appear to cause this issue to my limited knowledge, I can post logs if need be.

Thanks for reading.

The links to images within are credited to their respective owners and merely being used for communicative purposes.

---

### Post by pbrane on 2009-11-11
Not that this is any help, but I **upgraded** from 9.04 to 9.10 as well and I too am experiencing longer boot times. 9.04 booted much quicker the 9.10 does. Not sure why, maybe a fresh install would solve it.

---

### Post by atleastitsnotcrack on 2009-11-11
BTW I'm using autologin I believe this has changed in karmic

My tty1.conf contains
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -8 38400 tty1

[http://www.shallowsky.com/blog/](http://www.shallowsky.com/blog/) says:

Create /usr/bin/loginscript if you haven't already, containing something like this:

#! /bin/sh
/bin/login -f yourusername

Then edit /etc/init/tty1.conf and look for the respawn line, and replace the line after it, exec /sbin/getty -8 38400 tty1, with this:

exec /sbin/getty -n -l /usr/bin/loginscript 38400 tty1


I'll give it a go if I don't return something bad has happened! :)

---

### Post by atleastitsnotcrack on 2009-11-11
still long boot time,

instead of TTY1 terminal text prompting for login I just get a blinking cursor that slowly line feeds - echo turned off maybe in one of those options???

I only get to see usplash for 4 seconds

---

