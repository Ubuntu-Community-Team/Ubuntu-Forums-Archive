---
title: "Installing Ubuntu i386 on AMD64"
date: 2005-10-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by sebdah on 2005-10-10
Question 1:
Is it possible to install Ubuntu Breezy for i386 on a AMD64 processor?

Question 2:
If I install Breezy (for 64-bit) is it possible to compile and run i386 applications?

---

### Post by greenfrog on 2005-10-10
In answer to Question 1, yes you can install 32 bit Ubuntu on an AMD64

Question 2, I can not help you with.

---

### Post by Drain on 2005-10-10
[QUOTE=sebdah]Question 2:
If I install Breezy (for 64-bit) is it possible to compile and run i386 applications?[/QUOTE]

It's my understanding that it is possible to do so, but it's a little (okay, maybe a lot) tricky. What you need to learn about is creating a 32-bit chroot, and details about how to do that in Hoary are here: [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575) . I'm pretty certain that it should work with Breezy as well (there will probably be a place or two where you'd have to switch the word "Hoary" for "Breezy" in the install process). 

That forum thread will either get you started or put you in a world of hurt. ;-) Good luck!

---

### Post by brt on 2005-10-10
Ubuntu i386 on AMD64 really works as good as on the 64bit Ubuntu. I tried both and cannot find any disadvantages of the i386 variant. 

the only reason why i am using the 64bit Ubuntu now, is because i think why should i use a 32bit system when having 64bit hardware and a 64bit OS availiable.

when i switched to 64bit i kept my old 32bit system which i am using as chroot now for running 32bit appications (just as described in the 32bit chroot howto, but i didnt need to setup the software in the chroot as its already there)

if you are lazy and don't want to care about running 32bit applications in a chroot, even its not too hard, then its a wise choice to stay with Ubuntu i386.

---

### Post by funkenstein on 2005-10-11
Here's a question for you:
Do you want to get on with your life and work on your 64 bit machine, or do you have lots of free time to mess about?

I *REALLY* want to mess about with 64bit OS's, but after doing that for a while, I find that my MSc thesis is going down the drain as I spend more time tinkering than working. If its for "fun", go for the 64bit headache. If it's for work, go for 32bit Hoary and wait at least till there's a stable ubuntuguide for Breezy.

my £0.02 (approx. $0.0349186) :p

---

