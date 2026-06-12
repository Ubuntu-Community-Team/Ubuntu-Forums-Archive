---
title: "Voice chat for ubuntu x64"
date: 2009-04-29
forum: x86 64-bit Users
---

### Post by Canaryguy on 2009-04-29
Hi, 

I've been looking for a voice chat that is open source but so far I haven't be successful making one to work. I looking for one that works under ubuntu x64 and that can be installed in a Windows system too because I want to talk to another person that uses Windows.
Ekiga doesn't seem to work on my laptop. I've tried others I've seen in the forums like Kopete, Gizmo, GYachi.

Can anybody recommend me something?

Thanks

---

### Post by Big_astur on 2009-04-30
Can't u use Skype?

I tried it and works fine here. Linux version is a bit "old" comparing to windows one where they can do more things but for the rest it works fine. 

BTW it's also for video chat.

---

### Post by Sef on 2009-04-30
> Can't u use Skype?Skype is not open source.  it is proprietary.

> Ekiga doesn't seem to work on my laptop. 

What problems do you get with Ekiga?

---

### Post by Big_astur on 2009-04-30
> **Sef said:**
> Skype is not open source.  it is proprietary.
Sorry :D

---

### Post by jespdj on 2009-04-30
> **Sef said:**
> Skype is not open source.  it is proprietary.
But ofcourse that doesn't mean you cannot use it.... :rolleyes: The OP should choose for himself whether he wants to use proprietary software or not.

The easiest way to install Skype on 64-bit Ubuntu is by installing it from the [Medibuntu](http://www.medibuntu.org[/url) repository.

---

### Post by Canaryguy on 2009-04-30
Hi, again:

I was going to write the message I got from Ekiga, something like "Could not register SIP: X" but for my surprise I have just executed it and now it works. I installed the program yesterday and tried to make the Echo Test but I got the "not register SIP..." I guess it was just a matter of waiting until the registration I made was confirmed or something.

I'm sorry for wasting your time.

Bye.

---

### Post by Canaryguy on 2009-04-30
Here I am again, 

well, it seems that sometimes when I enter in Ekiga I get the message "Could not resgister SIP....".
I found a solution that worked for me. This was my answer in another post where they had also the same problem:

I'm using Ubuntu 9.04 x64 on a laptop and I had the same problem with Ekiga 3.2.0. I got the message "Could not register SIP:...."
What I did and worked was to open Ekiga and then Edit>Configuration Assistant
When asked for your user name and password enter them as you received them in your e-mail address when you registered in Ekiga.
In the Windows Ekiga Call Out Account I checked the "I do not want to sign up......" at the bottom.
In "Connection Type" you choose your best option. I chose DSL/Cable 512...
In the "Audio Devices" I chose HDA/INTEL (PTLIB/ALSA) in the three boxes. And I think it was this option that made my Ekiga to work fine. Maybe you have to try different audio settings until you see that the Echo Test icon turns green and you can make a call.

It seems I have to repeat the process every time I open Ekiga.

Bye.

---

### Post by coskierken on 2009-05-03
I just don't know why you don't use Skype in U64?  I got it to work fine.  I use it all the time.  Here is a link and it works.  It installs all that is needed to work under 64bit Ubuntu.  

[http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)

thanks to cappy!!!!!

---

### Post by TheBuzzSaw on 2009-09-10
It's about bloody time they released a 64-bit binary!

---

