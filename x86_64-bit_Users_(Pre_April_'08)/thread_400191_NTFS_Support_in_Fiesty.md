---
title: "NTFS Support in Fiesty"
date: 2007-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by sammyd253 on 2007-04-03
Not sure if I heard this anywhere but is NTFS support going to be in Fiesty?  I think it'd be really nice to have my Windows NTFS partitions mounted in Ubuntu so that I could swap files between partitions.

---

### Post by Martje_001 on 2007-04-03
Files on a NTFS-filesystem can only be _read_ by Linux. So I don't think it's going to be a feature in Feisty

---

### Post by sammyd253 on 2007-04-03
That's what I thought.  I know that only being able to read from NTFS has been a limitation for awhile now.  Wasn't sure if they attempted to fix this.  Thanks though!

Anyone else hear anything?

---

### Post by djrobthaman on 2007-04-03
Hmm... I wouldn't say that Linux cannot write to NTFS.  I'm using edgy and have read/write set up for NTFS and it works flawlessly... for me anyway.  I have heard that it's still not 100% stable so that would probably rule it out from being actually being packaged with feisty.

If you want to find out how to set it up, you can go here:

[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g")

---

### Post by sammyd253 on 2007-04-03
Seems good, but has anyone tested the 64-bit method?  Seems to be a little problematic...?

---

### Post by eentonig on 2007-04-03
reading ntfs is on by default in Feisty. At least, I didn't have to install anything else to access my NTFS drive.

Writing is not available by default, but some progress is being made on that part. alltough still very much in alpha/beta state for the moment I think.

---

### Post by Toadmund on 2007-04-03
I'm 64bit, I was able to transfer over music and movie files from windows no problem.
The NTFS required no installation on my part (apart from feisty install itself)

---

### Post by djrobthaman on 2007-04-03
@sammyd

I'mk running the 64-bit version of edgy.  I don't remember which method I used, so I suppose it must have been that one and I've had no problems so far.

---

### Post by sammyd253 on 2007-04-03
Well If I can read from NTFS partitions by default in Fiesty, then I won't even bother writing to these partitions.  I would just want access so that I could load my mp3 collection off of my current NTFS partition.

---

### Post by Biochem on 2007-04-03
I Installed Feisty 64 bit last weekend and I can read and write on my ntfs partition.
All I had to do is install ntfs-3g from the repo. I was glad to see that I didn't have to install 3rd party repos for that anymore. Than I changed my all ntfs entry in /etc/fstab to ntfs-3g. *Et voila* full ntfs support:)

---

### Post by tj.milligan on 2007-04-03
To enable ntfs read/write support in Feisty you'll want ntfs-3g. Rather than having to toil[1] away, editing config files and such, you can simply install [via synaptic or apt-get] **ntfs-config**, a GUI for ntfs-3g. Then run Applications > System Tools > NTFS Configuration Tool and you're done! BTW, this seems to be Feisty-only, as it isn't found in the Edgy repo.

[1] I use this word lightly; It's not necessarily difficult to edit /etc/fstab, and CLI is certainly faster in experienced hands than GUI. It's my opinion that the GUI is best option for the average/casual user.

---

### Post by sammyd253 on 2007-04-04
> **tj.milligan said:**
> [1] I use this word lightly; It's not necessarily difficult to edit /etc/fstab, and CLI is certainly faster in experienced hands than GUI. It's my opinion that the GUI is best option for the average/casual user.


I agree with you here.  I am fairly comfortable with editing files from the CLI,  as I've done it before.  Besides, even though I may struggle a bit, I like to learn.  I feel like I'm getting a better experience when I'm doing it from the CLI.  Thanks for your tips though, the NTFS-3g package is one that I plan to get once I do install Ubuntu.

---

