---
title: "newbie problems with WinTV-NOVA-TD dual tuner stick"
date: 2007-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by johnwillyums on 2007-12-07
Hello All

I'm a complete newbie who has (perhaps foolishly) opted for a dual boot with Vista 64x and Gutsy 64x times on my new pc.
Needless to say I'm having difficulties in both and am gradually working through a list of issues in both operating systems.
I'm getting there and I'm loving Ubuntu and would hope to eventually leave Vista behind altogether.
My current issue is that I have a WinTV-NOVA-TD dual tuner usb tv stick which I can't seem to get working in Ubuntu,it works through Media Center in Vista.
For anyone interested I received loads of help from a guy called wieman01 on a thread called:
 
HOWTO: Kaffeine & (Hauppauge) WinTV-Nova-T Stick [Feisty Fawn]

This is in Hardware and Laptops in Main Support Categories in Ubuntu Forums.

After an amazing amount of effort on his part he eventually suggested I post my problem in this forum as he felt he had gone as far as he could and did not have 64x knowledge to call on.

I tried to follow his instructions around kaffeine but got nowhere and I've installed anything I can see in the repositories that seems to be about tv eg mythtv frontend/backend, miro, zapping tv viewer and many more.

All this has been to no avail. I can't seem to do anything with mythtv and I just can't find my device.
If I look in device manager I find an entry for a NovaT 500Stick, which is not what I have exactly.

I'm at a loss and resent having to go back to Vista for tv.

Does anyone out there have one of these? If so how do I get it working.
As I've said, wieman01 got me to try a lot of different things so anyone wishing to help would do well to have a look at his thread.

Thanks for listening, John

ps my pc is as follows: Q6600 cpu, Asus P5N E-SLI, 4GB ram, nVidia 8600GT, 500GB HDD

---

### Post by johnwillyums on 2007-12-16
Hi. I take it from the deafening silence that, either it can't be done or noone knows how to do it.

Least I got some viewers. I posted a similar query on Hauppauge's own forum several weeks ago and got  4 views and no response

Oh well. It's not as important as my printer (Canon i9950) so I'll make a fresh post about that.

John

---

### Post by wieman01 on 2007-12-19
Hi John, 

Is installing the 32-bit version of Ubuntu an option perhaps? Thing is that you might not take full advantage of 64-bit anyway, so why not revert to 32-bit... just a thought.

---

### Post by johnwillyums on 2007-12-23
Hello again wieman.

Sorry I took so long to reply but I've been away.

You mention doing a 32bit install. I'm reluctant to do that and I cannot see why it would make a difference as many of my apps are running as 32bit on my 64bit Ubuntu.

I posted on Hauppauge's forum and was directed here:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-TD-Stick](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-TD-Stick)

This informs me that I need:

dvb-usb-dib0700-1.10.fw firmware file

I have downloaded this to my desktop but cannot move it into  /lib/firmware 

If I try I get a -" you do not have permission to write to this folder"- error notice.

Hopefully this is some simple newbie ignorance and I just need to be told how to do it.

Today I got some updates and one of them was for mythtv.

This did not install and I was asked to verify if MySQL-server was running by entering:

sudo dpkg-reconfigure mythtv-database

I've tried this but when I get to the question about "localhost" I do not know what to put. If I press enter I just end up back at terminal.

So presumably I do not have a MySQL server or local host. How do I find one?

Also, is mythtv relevant to my problem with the tv tuner? I thought I was trying to use it with Kaffeine.

All the best to you and thanks for the continuing support, John williams

---

### Post by wieman01 on 2007-12-23
32-bit might make a difference because the firmware might support 32-bit only. Believe me, 64-bit can be a problem when it comes to hardware support for devices such as wireless adapters (ndiswrapper) and possibly TV cards. Don't want to spread FUD, but 64-bit can be a hassle. Therefore I was suggesting to try out 32-bit. 

Why don't you try in dual mode or by booting from Live CD?

---

### Post by Col-1023 on 2007-12-23
If you don't have permission to move a file into a particular folder, or write to a folder, then there is an applet (can't remember the name) which you can get from synaptic which will put an option in the right click menue so when you right click on a folder, you can open it as root user.

An alternative is to llogin as root and then move the firmware file to the right directory, and then log-out as root, (since it's unsafe to be root user for long periods.

I haven't got into tv-tuners with linux yet, but from what I understand kaffeine and mythtv are 2 completely different programs, and kaffeine doesn't need mythtv to recognise the tv-card.  Once it finds the card, it should be able to find the channels, play or record tv.

Hope this helps.

---

### Post by johnwillyums on 2007-12-24
Hello. Thanks for that. I managed to get the firmware file into /lib/firmware  but it doesn't seem to have made a great deal of difference.
When I open Kaffeine I get a message saying "cannot bind info socket".
If I ok this I get a box with various choices including DVB.
If I click that I get a screen up and everything looks promising but if I try to configure DVB I get the "cannot bind info socket" message again and can't get any further.
Does anyone have any ideas where I go from here?

Thanks to you all and seasons greetings, John Williams

---

