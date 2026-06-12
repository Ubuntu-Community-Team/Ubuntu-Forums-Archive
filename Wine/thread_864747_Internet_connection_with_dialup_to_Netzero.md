---
title: "Internet connection with dialup to Netzero"
date: 2008-07-19
forum: Wine
---

### Post by bobterri73 on 2008-07-19
I am setting up a second computer in my house.  My son-in-law put Ubuntu 7.10 on it for my operating system.  Now I want to connect to the internet with it.  My first computer, using Windows XP, connects with my ISP Netzero through a dial-up connection.  Netzero has said they do not support Linux operating systems.

How can I connect to my ISP, or is there another dialup ISP that will support my Ubuntu operating system?

I attempted to set up the Netzero software under the WINE application, but I could not get WINE to recognize it.  I am using WINE version 0.9.57.

I did connect to the Netzero home page by using the terminal program and entering the local Netzero number, but the connection was so slow that I could not do anything once I was there.

Thanks for your help.

---

### Post by Vorian Grey on 2008-07-20
If you can connect through the terminal (presumably using wvdial) then you don't need the Netzero dialer. The reason it probably ran so slow is it wasn't configured correctly. For example the Baud in your wvdial conf file (found in /etc/wvdial,conf) should be 11500. 

I don't use Netzero but I do have dialup and I use Gnome-ppp to connect. It's in the repos and it's easy to set up and use. 

BTW, my ISP told me that they didn't support Linux either but I get online just fine.

---

### Post by bobterri73 on 2008-07-28
Thanks for your input and quick response.  Sorry it took me so long to reply.  I did adjust the baud rate as you suggested and was able to get online, but the Netzero site keeps telling me to load the latest version of their software.  That will not help because I am not using their software to connect.  I tried to install and run their software in Wine 0.9.57 but nothing seemed to happen.

One interesting thing I found: If I jump to my email provider (Juno) just after connecting to Netzero then I do not get any error messages from Netzero, but if I try to go to any other site from there, or to any other site directly from Netzero, the error messages from Netzero pup up and do not let me connect to anything else.

Any help would be appreciated.

Thanks again.

Bob

---

### Post by zieglerj on 2008-08-01
the problem is with netzero's server. Boycott them if you can but I can't for the moment. Nearest I can tell there has to be a way to fool them into thinking you're using their dial-up prog. I think it would have something to do with the dns settings ... but I'm not sure. Any help would be greatly appriciated. :)

---

