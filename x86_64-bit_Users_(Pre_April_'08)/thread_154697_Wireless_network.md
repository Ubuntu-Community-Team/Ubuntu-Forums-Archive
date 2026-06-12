---
title: "Wireless network"
date: 2006-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by FrustratedGuy on 2006-04-03
Hello, everyone,

I am using a computer with Windows XP and Kubuntu Linux AMD64. I am having some trouble getting online. When I try to set it up, it appears that the only way to access the settings is to log in as root, which is annoying but not the issue.

The issue is that whenever I try to activate my WiFi interface, it blinks active for a second and goes inactive again.

I am using a Linksys Wireless G-PCI Adapter, connecting to a router of same make. I'm thinking I have some setup wrong; can you help me out?

I am including snapshots of my setup; however, I am obscuring my IP Address and similar info for privacy's sake.

Also note that on the "Default Gateway", I enter the same default gateway as on my Windows system, but no matter what it goes back to a blank box when I Apply and close it.

[http://img406.imageshack.us/img406/5353/picint8fr.jpg](http://img406.imageshack.us/img406/5353/picint8fr.jpg)

[http://img218.imageshack.us/img218/7199/picgate6kc.jpg](http://img218.imageshack.us/img218/7199/picgate6kc.jpg)

[http://img435.imageshack.us/img435/2043/picdomain1pg.jpg](http://img435.imageshack.us/img435/2043/picdomain1pg.jpg)

---

### Post by Schmung on 2006-04-03
I'm certain I just replied to this...

Arhgg, there was loads of text as well.

Oh well, long and short of it - I had the same issue. I have yet to fix the problem.
I think (could well be wrong) you're better off using the normal build as the 64 bit one dislikes ndiswrapper and thats what you're going to need to get that card working. Assuming of course that its a  WMP54GS - which I'm fairly certain it is.

Anyway, the problem I have and the one you will probably come up again is that the installer has autodected the card as a broadcom jobby adn given it eth0, meaning that when you try installing ndiswrapper it won't be able to assign wlan0 and you'll be in the same situation as me.  

Hopefully someone can shed some light on either of our situations. Should I fix my issue, I'll let you know how. Will keep an eye on this topic as well.

---

### Post by FrustratedGuy on 2006-04-03
Sounds good. :) But I don't want to go through the headache of installation again. It was hard before, and will be again. Besides, I have a AMD 64 Processor - shouldn't I use the build designed for it?

Actually, if there's a tutorial for setting up wireless networks I'd appreciate a link. Google hasn't been very helpful.

---

### Post by Schmung on 2006-04-03
Don't have anything to hand right now and I'm about to shoot off as well.
Have a look through the Wiki, theres a wireless troubleshooting guide, an installation guide and a few bits about ndiswrapper.

The problem with the 64 bit build is that it has issues with some bits of 32 bit software, particularly ndiswrapper, which you;re going to need if you want to use that card.

ndiswrapper lets you use the windows drivers for the cards in Linux.

I'll check the forums in work tomorrow morn and if no-ones posted the liks by then I'll go digging for them.

---

### Post by FrustratedGuy on 2006-04-03
I got the ndiswrapper, but I have no clue how to install it. I am familiar with DOS but use of the Konsole eludes me...

---

### Post by FrustratedGuy on 2006-04-03
A bit of an update: I found out I need to install binutils (whatever that means) to install other stuff. So I got an instruction web page, copied the contents into a txt file, burned it with the binutils install, and... it didn't work.

In the below pic, the instructions are at left. At right, my Konsole - I hit Ctrl-C in the middle of it when I goofed, but the commands were followed to the letter. The result was not pretty.

[http://img92.imageshack.us/img92/1521/frustration34lr.jpg](http://img92.imageshack.us/img92/1521/frustration34lr.jpg)

---

