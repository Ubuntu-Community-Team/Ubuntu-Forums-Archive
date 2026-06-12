---
title: "How Can I DELETE a FOLDER?"
date: 2007-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mr_bleu on 2007-06-09
I cannot delete the jre1.6.0_01 folder I've downloaded to desktop to get my java working.  Java and flash are working fine.  The folder is locked. I am the administrator/root.  I have not set the root password this time I've installed.   I've tried rm -rf .  They aren't working.
djr@djr-laptop:~/Desktop$ sudo chroot jre1.6.0_01
chroot: cannot run command `/bin/bash': No such file or directory
djr@djr-laptop:~/Desktop$ chroot jre1.6.0_01
chroot: cannot change root directory to jre1.6.0_01: Operation not permitted
djr@djr-laptop:~/Desktop$ rm -rf ./jre1.6.0_01
rm: cannot remove `./jre1.6.0_01/LICENSE': Permission denied
rm: cannot remove `./jre1.6.0_01/COPYRIGHT': Permission denied
djr@djr-laptop:~/Desktop$ 

Any help is appreciated.  Thanks.

---

### Post by taurus on 2007-06-09
```
cd ~/Desktop
sudo rm -rf jre1.6.0_01
```

---

### Post by NeoLithium on 2007-06-09
Use 'sudo' at the beginning of the rm command :)

---

### Post by Mr_bleu on 2007-06-09
I've tried that, it's not working for me.  The folder's LOCKED.  When I right click on it and view permissions, it doesn't show me a thing.

---

### Post by NeoLithium on 2007-06-09
djr@djr-laptop:~/Desktop$ rm -rf ./jre1.6.0_01
Was the line you posted, it should be :
```

sudo rm -rf jre1.6.0_01

```

---

### Post by Mr_bleu on 2007-06-09
djr@djr-laptop:~$ cd ~/Desktop
djr@djr-laptop:~/Desktop$ sudo rm -rf /jre1.6.0_01
Password:
djr@djr-laptop:~/Desktop$ 


No errors, folder's still there locked.

---

### Post by NeoLithium on 2007-06-09
don't use the / in front of jre1.60_01 ; might work that way.

---

### Post by sel on 2007-06-09
Click on your desktop and press 'F5'?

---

### Post by Mr_bleu on 2007-06-09
> **NeoLithium said:**
> don't use the / in front of jre1.60_01 ; might work that way.

That did it, THANKS!!!:popcorn::popcorn::popcorn::popcorn:

I couldn't find how in the forums or googling it.  I went to computerhope and saw the / option.

---

### Post by NeoLithium on 2007-06-09
No problemo :)

---

