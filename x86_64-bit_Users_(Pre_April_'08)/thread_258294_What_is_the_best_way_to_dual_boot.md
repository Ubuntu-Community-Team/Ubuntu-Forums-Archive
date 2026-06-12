---
title: "What is the best way to dual boot"
date: 2006-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by j0eb0b on 2006-09-15
Due to my sound travails I fell back the XP to get everything working.  When i installed Windows I left an unformated 150G partition on my drive.  I want to reinstall Dapper 64 into this space and continue to learn Ubuntu.  Is there a How To that tells how to install Ubuntu onto an established XP system?

---

### Post by kuja on 2006-09-15
It should be as straightforward to do as to install Ubuntu normally. Just have it use that blank partition and you should be set. It should detect the windows xp install out-of-the-box, but post back if it gives you any trouble.

---

### Post by j0eb0b on 2006-09-16
Well I am back on Dapper 64 again and hope i haven't shot myself in the foot.

Apparently when I installed XP and created two drive letters I apparently only formatted the C: drive.  When i went to install Dapper i accepted the default which I thought would place Dapper on D: but instead broke my C: drive into two 75G partitions.  The install proceeded normally.  When Windows came back up he complained some because he had lost half his real estate but continued and then gave me a message that he had installed a new device, which I assume is the 75G partition containing Dapper.  So, I have both XP and Dapper on the C: and D: which I formatted once I realized it wasn't has 155 G.  I have unexplainably lost 15G of my 320 G drive.

The machine dual boots to both operating systems and the only issue I have seen is Dapper froze once when I left the keyboard and the screen saver came up.  Is there anything inherently wrong with my current setup?  How can I find out what happened to the lost 15G of disk.  While I am unlikely to need it in this lifetime, I am curious what happened to it.

When the machine posts, Dapper is the default OS which is OK.  How can I increase the time to select which operating system to boot which is now
very short.

Thanks,
Joe

---

### Post by Kilz on 2006-09-16
> **j0eb0b said:**
> Well I am back on Dapper 64 again and hope i haven't shot myself in the foot.

Apparently when I installed XP and created two drive letters I apparently only formatted the C: drive.  When i went to install Dapper i accepted the default which I thought would place Dapper on D: but instead broke my C: drive into two 75G partitions.  The install proceeded normally.  When Windows came back up he complained some because he had lost half his real estate but continued and then gave me a message that he had installed a new device, which I assume is the 75G partition containing Dapper.  So, I have both XP and Dapper on the C: and D: which I formatted once I realized it wasn't has 155 G.  I have unexplainably lost 15G of my 320 G drive.

The machine dual boots to both operating systems and the only issue I have seen is Dapper froze once when I left the keyboard and the screen saver came up.  Is there anything inherently wrong with my current setup?  How can I find out what happened to the lost 15G of disk.  While I am unlikely to need it in this lifetime, I am curious what happened to it.

When the machine posts, Dapper is the default OS which is OK.  How can I increase the time to select which operating system to boot which is now
very short.

Thanks,
Joe

You can install gparted with synaptic. It will give you the partition intformation. You will be able to see if there is any unused areas. You probably wont be able to change things for the linux partitions anyway because it will lock any in use.
IMHO I think the 15G is probably made up of swap partition and the file alocation tables that are created when you format any disk. You never get to use 200g of a 200g drive. More like 170G.
But the tool would be good to partition up the unused other drive .

---

### Post by hajk on 2006-09-16
And edit /boot/grub/menu.lst to change the timeout to 20 (seconds), say, or whatever. No need to reinstall grub, BTW.

---

### Post by j0eb0b on 2006-09-16
Kilz

Thanks for the advice.  I just ran you Foxfire script and got the follwing error at the end during the java install.  What did I do wrong?

15:18:51 (89.39 KB/s) - `j2re1.4_1.4.2.02-1ubuntu3_i386.deb' saved [22509784/22509784]

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package j2re1.4.
(Reading database ... 70188 files and directories currently installed.)
Unpacking j2re1.4 (from j2re1.4_1.4.2.02-1ubuntu3_i386.deb) ...
Setting up j2re1.4 (1.4.2.02-1ubuntu3) ...

You may get a 'sudo: Unable to get working directory' error when the script cleans up after itself. Please disregard it.
j0eb0b@j0eb0b-desktop:~/Desktop/ffinstall$

---

### Post by Kilz on 2006-09-16
> **j0eb0b said:**
> Kilz

Thanks for the advice.  I just ran you Foxfire script and got the follwing error at the end during the java install.  What did I do wrong?

15:18:51 (89.39 KB/s) - `j2re1.4_1.4.2.02-1ubuntu3_i386.deb' saved [22509784/22509784]

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package j2re1.4.
(Reading database ... 70188 files and directories currently installed.)
Unpacking j2re1.4 (from j2re1.4_1.4.2.02-1ubuntu3_i386.deb) ...
Setting up j2re1.4 (1.4.2.02-1ubuntu3) ...

[b]You may get a 'sudo: Unable to get working directory' error when the script cleans up after itself. Please disregard it.[/]
j0eb0b@j0eb0b-desktop:~/Desktop/ffinstall$

If your refering to the bolded areas in your comments, its a warning that "if" you get a error stating "sudo: Unable to get working directory" to disregard it. 
You see the script clean up after itself because it would leave a folder root creates on your desktop. That folder is hard to get rid of for new people, so it deletes it. A side effect is sometimes the script warns it cant read from the folder it just deleted. Nothing to worry about. :D

---

### Post by j0eb0b on 2006-09-16
I wasn't referring to the text at the end of the message, I was referring to this:

dpkg - warning, overriding problem because --force enabled:
package architecture (i386) does not match system (amd64)
Selecting previously deselected package j2re1.4.
(Reading database ... 70188 files and directories currently installed.)
Unpacking j2re1.4 (from j2re1.4_1.4.2.02-1ubuntu3_i386.deb) ...
Setting up j2re1.4 (1.4.2.02-1ubuntu3) ...

I guess this is not a error.

After running the script, I tried to test by going to Google - Videos and picking one at random.  Vorfire comes back with a "plugin missing" error and claims none can be found.  If you go to manual install nothing happens.

What else do I need to do?  i have gone into repostitories and enabled everything.

---

