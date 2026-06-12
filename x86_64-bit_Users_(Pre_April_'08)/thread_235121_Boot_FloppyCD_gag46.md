---
title: "Boot Floppy/CD gag46"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cariboo1938 on 2006-08-12
Setting up Boot Floppy

I follow the instructions on Herman's very detailed "GAG page";
Start menu: 'Choose an option' : Install {4}
2nd menu: 'Choose your keyboard': qwerty {1}
3rd menu: 'Choose your language': English {8}
4th menu:  Choose  "Setup GAG"  Key {S}
New Menu: Choose "Add a new OS"
New menu shows 
Key      Partition    Type
B          83h Linux	Ext2
..
G	83h Linux	Ext2
H  
It seems that H is the swap Partition. and the second hard drive, where Windows is installed, is not recognized.  
If I select any of these B-G and follow the instructions to "Save on Floppy" {F}
I get, when restarting with the floppy inserted, the GAG menu showing Linux OS. When I try to start it, I get the error message: [COLOR="Red"]"Sector boot not found or invalid"[/COLOR]. That's it. I have to take the floppy out and reset the computer.
What went wrong?](*,)

---

### Post by Cariboo1938 on 2007-03-10
The problem was that I didn't have neither Grub nor any other MBR set up.
[HERE]("http://users.bigpond.net.au/hermanzone/") a person finds how to do it.
Excellent work from Herman!
Thanks
Case closed:)

---

