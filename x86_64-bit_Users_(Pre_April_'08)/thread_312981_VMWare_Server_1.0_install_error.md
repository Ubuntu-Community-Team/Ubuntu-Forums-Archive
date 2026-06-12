---
title: "VMWare Server 1.0 install error"
date: 2006-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by neptune on 2006-12-05
Hi,

I get an error during the installation of VMWare Server 1.0.1:

**Unable to get the last modification timestamp of the destination file /etc/vmware/ssl/rui.key**

Before doing the install, I obtained the following packages:
libx11-6 libx11-dev libxtst6 xlibs-dev xinetd wget linux-headers-2.6.17-10-generic build-essential gcc binutils-doc cpp-doc make manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc gcc-4.0-doc libc6-dev libgcc1

What am I doing wrong? 

Thanks!

---

### Post by hainesr on 2006-12-05
> **neptune said:**
> 
**Unable to get the last modification timestamp of the destination file /etc/vmware/ssl/rui.key**

Does /etc/vmware/ssl/rui.key exist on your machine? Maybe it wasn't written properly or you don't have the right permissions - you are doing this as root aren't you?

Also if you're using 64bit make sure you've installed the 32bit libs (ia32-libs package IIRC - there may be others too)...

I had great success (twice) installing vmware server (once Dapper, once Edgy) with this howto: [How To Install VMware Server On Ubuntu 6.06 LTS (Dapper Drake)]("http://www.howtoforge.com/ubuntu_vmware_server"). If you're using Edgy, don't worry that it says Dapper - it works perfectly!

Cheers,
Rob

---

### Post by neptune on 2006-12-05
Thats the same HowTo I'm following but still get that error.

Yes, I'm running amd64 version of Edgy and installing as root. But I didn't know about the ia32-libs package. Installing it right now. 

Hopefully this fixes the problem.

Thanks!

---

### Post by neptune on 2006-12-05
Hey, no more error! :)

However, now its asking for a serial number. I never got one when downloading VMWare Server.

Is there a special way to obtain it?

<EDIT>
Nevermind, got it.
</EDIT>

---

### Post by hainesr on 2006-12-05
Interestingly, when I tried to input my serial numbers I had to do so by hand - copy and paste into the terminal just would not work! It was copied in OK, but the VMware setup script kept saying that the serial number was blank! Very odd...

Rob

---

### Post by neptune on 2006-12-05
Wow thats strange. I was able to paste it into a putty window and it worked fine.

---

### Post by neptune on 2006-12-05
Another issue now, this time with the Management Interface.

I followed instructions from the above-linked HowTo and installed the VMWare Server Management Interface (vmware-server-mui). Everything went well, without incident. 

I completed the install by running **chown www-data:www-data /var/run/vmware/httpd**.

But trying to access the interface webpage at [https://localhost:8333/](https://localhost:8333/) doesn't work - I keep getting a "page not found" error. 

My apache2 is working fine because I get the default page at [http://localhost/](http://localhost/)

Please help... I'm almost there.

Thanks!

---

### Post by hainesr on 2006-12-06
> **neptune said:**
> Another issue now, this time with the Management Interface.

I followed instructions from the above-linked HowTo and installed the VMWare Server Management Interface (vmware-server-mui). Everything went well, without incident.

I have to say that I think this managment interface bit of the howto is a red herring. I've never used it - never even installed it! Try ignoring that section and going straight down to the bit about the vmware console - it does all I need. The management interface doesn't even allow you to create virtual machines. To get the console up and running just type 'vmware' into your terminal (assuming you installed into your path)...

> **neptune said:**
> But trying to access the interface webpage at [https://localhost:8333/](https://localhost:8333/) doesn't work - I keep getting a "page not found" error.

My apache2 is working fine because I get the default page at [http://localhost/](http://localhost/)

Did you restart apache? Do you get an [https://localhost/](https://localhost/) default page?

Cheers,
Rob

---

### Post by neptune on 2006-12-06
I've got the client console working just fine, however there are some options on the management interface that I'd like to be able to view and edit.

Has **anybody** got it working??


Regarding apache, yes I restarted the server; in fact, I even restarted the computer but still nothing on SSL. Basic [http://localhost](http://localhost) works fine, but https does not.

---

### Post by hainesr on 2006-12-06
I've not even installed this stuff so obviously I can't offer help through my own experiences directly, but I have setup apache and added new websites into it, which is what I guess is happening here.

Have a good look at this file [FONT="Fixedsys"]/etc/apache2/README[/FONT]

To enable ssl you need to load the ssl module into apache (which isn't done by default): ```
sudo a2enmod ssl
```

Then restart apache and you *should* be able to see something at [https://localhost](https://localhost)

Now the vmware mui *might* work, but if not you probably need to make sure that apache is including some extra config provided by the vmware install. Not having installed it myself, I don't know what! Have you added anything to your base apache config to pull in any vmware specific config files? Or maybe vmware has put something into [FONT="Fixedsys"]/etc/apache2/sites-available[/FONT] which you can enable with: ```
sudo a2ensite <vmware-stuff>
``` Then restart apache, of course...

Hope some of this helps!

As an aside - what is it that you need from the web-based interface that the console doesn't provide? Maybe I should install this stuff myself!

Cheers,
Rob

---

### Post by neptune on 2006-12-06
I ran the first command and received:
[B]Module ssl installed; run /etc/init.d/apache2 force-reload to enable.
[/B]
Fine. So I did **/etc/init.d/apache2 force-reload** as well and the webserver was restarted.

However, still nothing on [https://localhost](https://localhost)

Looks like I have to hit the books (well, readme files) on this one.


We use VMWare ESX at the office and I want to try and get something similar to play with at home since our 'lab' environment is pretty much non-existent. Thats the main reason.
I also just want to poke and prod and explore - its my nature. :)

---

### Post by hainesr on 2006-12-06
I've just had another look at the howto. Does vmware install its own copy of apache? It does some configuration of apache that I wouldn't want it doing to my system wide version! If it does install its own copy maybe you need to look for another httpd to run? Or maybe there's a clash between two running httpds?

I'm scratching around in the dark now. :-(

Rob

---

### Post by tzulberti on 2006-12-06
> **hainesr said:**
> Also if you're using 64bit make sure you've installed the 32bit libs (ia32-libs package IIRC - there may be others too)...

Cheers,
Rob

I was just having this problem, thanks for the solution...

---

### Post by hhabashy on 2007-11-11
I thank you guys for you great notes....I have been trying to install vmware server 1.0.4 for 3 days, and nothing.  I decide to change my search to older versions....and OMG that is all I have to say.  I was on going to give up and go back windows.

---

### Post by hhabashy on 2007-11-11
i am sorry...in all the rejoycing i forgot to mention.  I had the same problem that neptune had with the SSL Server.  Hainesr's suggestion to install the 32 bit libs worked worked worked.  Just to be clear on my setup
Core 2 duo with 8 gigs of mem...Ubuntu Desk 7.10 64 bit....vmware server 1.0.4.

---

