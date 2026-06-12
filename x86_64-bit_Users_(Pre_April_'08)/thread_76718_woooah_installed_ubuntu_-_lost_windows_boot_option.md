---
title: "woooah installed ubuntu - lost windows boot option"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkrage on 2005-10-15
hi new to linux - currently im using knoppix live cd to access my pc.

the story ... 

i was given a copy of ubuntu by a freind who said its easy to set up - (problem one)
my set up is like this 

hda1 is windows xp (ntfs)
hdb2 is windows storage (ntfs)
hdc3 is ubuntu logical and swop partitioned 

real problem 1 is i have lost the ability to boot windows it goes straight to ubuntu with no option - so i need to know how do i get the boot option back.

real problem 2 is when ubuntu does boot up it goes thru the checks but cant access the system clock 
after some more checks it gets stuck at a subsystem check/load cant remember excactly but its just before ubuntu is ment to load up.

any help with this would be most appreciated 

hdc1 is setup as 200gig logical and 500meg swop.

hmmmm thinknig about it i do really need help.

cant lose my windows disks and cant keep using knoppix to access my pc - please help 

thx in advance

---

### Post by audax321 on 2005-10-15
Are you sure grub isn't just using a hidden menu? It might say Loading Grub.. or something when it boots and then you have like three seconds to hit escape and enter the menu.  Also, go into knoppix and access the root partition of the Ubuntu drive and open the file /boot/grub/menu.lst and post its contents as well as the contents of /etc/fstab.  Also which version of Ubuntu was given to you... i386 or 64-bit?

And make sure you look at these files in hdc and NOT the ones from the Knoppix LiveCD's filesystem.

---

### Post by Leopard on 2005-10-18
I had the exact same problem, when I upgraded from the preview of 5.10 to the release version.  My Windows XP entry dissapeared from the grub menu.

I ended up editing the file '/boot/grub/menu.lst' and adding this section in:

title		Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1
boot

after this line:
## ## End Default Options ##

It seems to work, I'm about to retest it now... ;)

---

### Post by bonzodog on 2005-10-19
1. Open /boot/grub/menu.lst in a gedit with the sudo command so you have permission to change it.

2 Near the top of the menu, you will see a line mentioning about hiding the menu. You will notice that this is commented IN by default, and the comment line above says so. comment this line out by adding a # before it so you get;
#hiddenmenu

3. Just below that, you will notice a comment line for the time the menu is to stay around before going to the default boot option. This is set to 3...yes 3 seconds!
Change it something reasonable like 30 or 60 seconds. remember this time is in seconds always, so if you want more than a minute, specify it in seconds.

4 In the same area, there is a setting for making the menu multicoloured, so it looks nice. These colour lines are commented out..uncomment them, and you will have a coloured boot menu that hangs around for a few minutes.

5. Add the windows option to the bottom of the file as mentioned above. While you are there, you will notice it lists about 6 boot options to load the kernels in various modes. You only need the top 2. Comment out the rest, DON'T DELETE THEM. leave the memtest option in as well.

6 save the file. When you re-boot, you should get a multi coloured blue and white menu, that lists the 3 options for ubuntu, plus your windows boot.

Hope this helps.

---

### Post by zupermanz on 2005-10-19
To make things easy try to install grubconf (for amd64)
you will find it here : [http://packages.debian.org/unstable/admin/grubconf](http://packages.debian.org/unstable/admin/grubconf)
then change time to 10 sec or whatever you like just make sure that there is a windows option....

---

