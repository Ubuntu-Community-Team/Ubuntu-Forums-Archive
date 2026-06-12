---
title: "File Permissions On Storage Drive"
date: 2007-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Angelbeast on 2007-04-29
Hi. I have just recently installed Ubuntu 7.04. Well. along with all of the wireless problems i am having. I have a second hard drive that i use for storage. There are alot of file on this drive that                                           need to be abe to edit. Problem is.. All of the fles are read only now.  Can someone tell me just how to change allof the files on this drive so that i can edit them and can have the proper permissions?

---

### Post by kuja on 2007-04-29
in a terminal:

sudo chmod 640 -R /path/to/the/drive
sudo chown $USER:$USER -R /path/to/the/drive

This might do the trick.

---

### Post by discmaster on 2007-04-29
> in a terminal:

sudo chmod 640 -R /path/to/the/drive
sudo chown $USER:$USER -R /path/to/the/drive

This might do the trick

Could you clarify a wee bit further for a complete newbie? :-)

Sorry for the "elementary" questions, but how do I determine the /path to the drive?

---

### Post by discmaster on 2007-04-29
Ok, after "muddling" around, I did figure out how to enter that info. in the term. window. After all was completed, I am still unable to write to the drive.

---

### Post by kuja on 2007-04-30
Can you post the contents of your /etc/fstab file, oh, and you're sure you got the path right, right?

---

### Post by discmaster on 2007-04-30
Thanks for the offer to help, kuja. In the meantime, I was able to get things working. A friend helped me out with the /fstab file, we edited it & all turned out ok!

Thanks again, discmaster :-)

---

