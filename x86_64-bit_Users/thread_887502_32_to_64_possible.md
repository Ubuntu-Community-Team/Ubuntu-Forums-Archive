---
title: "32 to 64 possible ?"
date: 2008-08-12
forum: x86 64-bit Users
---

### Post by huxterby on 2008-08-12
Hello everybody.

I just installed Ubuntu Hardy Heron for a friend (the 32 bit version) then I found out their system was 64 bit.

Is a reinstall necessary, or is there a special Ubuntu way to upgrade?

Thanks in advance.

Huxterby

---

### Post by PCessna on 2008-08-12
> **huxterby said:**
> Hello everybody.

I just installed Ubuntu Hardy Heron for a friend (the 32 bit version) then I found out their system was 64 bit.

Is a reinstall necessary, or is there a special Ubuntu way to upgrade?

Thanks in advance.

Huxterby

Reinstall. Have a good day.

---

### Post by huxterby on 2008-08-12
Thank you very much for the quick reply Pcessna.

Have a nice day yourself.

Huxterby

---

### Post by sandysandy on 2008-08-12
just go ahead and use the 32 bit.:)

unless of course there is a compelling reason to go for 64 bit.

regards

---

### Post by brujoand on 2008-08-12
> just go ahead and use the 32 bit.

So your saying there is nothing to gain by using an OS optimised for your system?
like adressing more then 3,5(or so) Gb ram which you could with the 64-bit system.. 
Do you really think the 64-bit version of ubuntu is that bad? 
 - thats a qustion, not retorical :)

---

### Post by hufferd on 2008-08-12
I posted kind of about this very same thing yesterday.  Just my 2 cents on the issue.

 [The link is here]("http://ubuntuforums.org/showthread.php?t=886875")

I really had more issues with trying to run a 64 bit OS then I care to think about so I went back to the 32 bit ver and things seem  to be working much better.  In my opinion there is not enough support for the 64-bit OS out there yet...

---

### Post by Kilz on 2008-08-12
> **hufferd said:**
> I posted kind of about this very same thing yesterday.  Just my 2 cents on the issue.

 [The link is here]("http://ubuntuforums.org/showthread.php?t=886875")

I really had more issues with trying to run a 64 bit OS then I care to think about so I went back to the 32 bit ver and things seem  to be working much better.  In my opinion there is not enough support for the 64-bit OS out there yet...

There is plenty of support. Also please list what issues you had with specific package and application names.

---

### Post by brujoand on 2008-08-12
Yeah I'm interested in your issues aswell, since my friend runs the 64-bit ubuntu on his macbook and he is loving it.. Kilz, maybe you can tells us what he would be missing out on by not using the 64-bit?

Anders

---

### Post by sandysandy on 2008-08-12
> **GrimmVarg said:**
> So your saying there is nothing to gain by using an OS optimised for your system?
like adressing more then 3,5(or so) Gb ram which you could with the 64-bit system.. 
Do you really think the 64-bit version of ubuntu is that bad? 
 - thats a qustion, not retorical :)


since he has already installed 32 bit, it may be wiser to use it before going to trouble of downloading , burning and reinstalling fresh.


i have used both 32 bit and 64 bit ubuntu. 

now depending on what ur using it for, difference will be felt.

for routine tasks the speed of 64 bit may not be that discernible.

regards

---

### Post by dominiquec on 2008-08-12
Using 64-bit Ubuntu 8.04 on a Quad Core, and happily so.  But first few weeks were a bit of a pain: no Flash on Firefox, Skype won't work.  Resolved these issues via the forum, thank goodness.  

What I'm saying is: be prepared for minor glitches at first.

---

### Post by tuxxy on 2008-08-12
The only minor glitch you may expect is the 32 but flash web plugin, however it runs fine for me and everythin else runs excellent on 64bit.

---

### Post by hufferd on 2008-08-12
> **dominiquec said:**
> Using 64-bit Ubuntu 8.04 on a Quad Core, and happily so.  But first few weeks were a bit of a pain: no Flash on Firefox, Skype won't work.  Resolved these issues via the forum, thank goodness.  

What I'm saying is: be prepared for minor glitches at first.


don't mind glitches but -- ANY time you have to "force" install something that can't be good. There is a reason they call it "Force" its not to be :)

---

### Post by Kilz on 2008-08-12
> **hufferd said:**
> don't mind glitches but -- ANY time you have to "force" install something that can't be good. There is a reason they call it "Force" its not to be :)

No forcing is a option of apt-get. If it was bad it would not be included as an option. In this case you are telling apt-get to disregard the control file in the deb that says the package was designed to run on a i386 computer. Since we know i386 packages run on AMD64 there is no reason not to try this.

---

### Post by Mad_Max_1412 on 2008-08-13
Guys,

I am thinking of upgrading my AMD CPU to a 4800+ 64-bit one.

Since my hard drive isn't partitioned, and I don't really have any room on another disk to copy my user files (Video files mostly) to, what will I need to do to upgrade (or fresh install) the 64 bit version of Ubuntu?

Is there a way to partition my hard drive without destroying the existing data and then install the 64 bit to the new partition and delete any old 32-bit Ubuntu directories?  ie My 500GB hard drive probably has 100GB free space.  Partition part of (or all) of this 100GB for the install location for 64-bit Ubuntu.  Then when it re-boots, it uses this partition.  This leaves me with a 400GB partition with my user file directory, plus all the directories that come with Ubuntu (32 bit) that I should be able to delete.

Also, I read somewhere that there should be a separate partition for the swap file.  Is this true, and if so, how big should it be?

I was thinking of re-installing the 32 bit version since I've been mucking about trying to get my videomate TV card working (ie configuration edits based on Forum suggestions) plus installing apps like Kaffiene to work with it.  I figured there's probably some rubbish left around.  But I'm just about to recover a more powerful processor from my Windows machine so I might as well go the whole hog and install the 64 bit version.

Thanks

---

### Post by Kilz on 2008-08-13
> **Mad_Max_1412 said:**
> Guys,

I am thinking of upgrading my AMD CPU to a 4800+ 64-bit one.

Since my hard drive isn't partitioned, and I don't really have any room on another disk to copy my user files (Video files mostly) to, what will I need to do to upgrade (or fresh install) the 64 bit version of Ubuntu?

Is there a way to partition my hard drive without destroying the existing data and then install the 64 bit to the new partition and delete any old 32-bit Ubuntu directories?  ie My 500GB hard drive probably has 100GB free space.  Partition part of (or all) of this 100GB for the install location for 64-bit Ubuntu.  Then when it re-boots, it uses this partition.  This leaves me with a 400GB partition with my user file directory, plus all the directories that come with Ubuntu (32 bit) that I should be able to delete.

Also, I read somewhere that there should be a separate partition for the swap file.  Is this true, and if so, how big should it be?

I was thinking of re-installing the 32 bit version since I've been mucking about trying to get my videomate TV card working (ie configuration edits based on Forum suggestions) plus installing apps like Kaffiene to work with it.  I figured there's probably some rubbish left around.  But I'm just about to recover a more powerful processor from my Windows machine so I might as well go the whole hog and install the 64 bit version.

Thanks

Yes, the installer will offer to partition the disk during setup. You can have both the 32bit and 64bit version installed on the same disk. Then you can then move over to it at your own pace. You can even mount the 32bit install to a folder in the 64bit install to help move over any files. Then when you are done, delete the 32bit partition to reclaim space. But as with any install problems sometimes do pop up, make sure to back up anything you cant afford to loose.

---

### Post by elmoosecapitan on 2008-08-13
If you are simply concerned about changing from 32-bit to 64-bit, you need to do a fresh install. You can keep your partitions, but you will have to reinstall from scratch. 64-bits are more efficient, however, because how young 64-bit archs are, not all programs, i.e., flash-10, are available just yet. Give it time.


cheers

---

### Post by Kilz on 2008-08-13
> **elmoosecapitan said:**
> If you are simply concerned about changing from 32-bit to 64-bit, you need to do a fresh install. You can keep your partitions, but you will have to reinstall from scratch. 64-bits are more efficient, however, because how young 64-bit archs are, not all programs, i.e., flash-10, are available just yet. Give it time.


cheers

Flash 10 runs on 64bit with nspluginwrapper.

---

### Post by Mad_Max_1412 on 2008-08-13
> **Kilz said:**
> Yes, the installer will offer to partition the disk during setup.

Should the swap file be a separate partition, or was what I heard/read about this a load of rubbish?  If it does need a separate partition, does the installer take that into account?

---

### Post by Kilz on 2008-08-14
> **Mad_Max_1412 said:**
> Should the swap file be a separate partition, or was what I heard/read about this a load of rubbish?  If it does need a separate partition, does the installer take that into account?

You should be able to use the same swap partition for both.

---

