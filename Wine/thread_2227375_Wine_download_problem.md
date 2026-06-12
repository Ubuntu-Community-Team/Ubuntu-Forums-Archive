---
title: "Wine download problem"
date: 2014-06-01
forum: Wine
---

### Post by gordon99 on 2014-06-01
I am trying to download WINE in Ubuntu 14.04. I have now got as far as 'configuringttf-mscorefonts-installer. The page shows 'End user license agreement for microsoft software' and seems to be stuck with the second clause of the license incomplete. However, if I try to end the download I get a message to say, in effect, that the download is still happening. Has anyone got a clue as to how long I should wait before abandoning the installation of WINE?

---

### Post by bapoumba on 2014-06-01
*Thread moved to **Wine**.*
have you tried hitting <tab> to highlight <OK> ?

---

### Post by gordon99 on 2014-06-01
Many thanks bapoumba. Having done as you suggested the download continued. However, it now seems to be stuck with 'my name @ laptop name $' immediatly after " Processing triggers forlibc-bin (2.19-0ubuntu6)." Is it needing a new command line from me?

---

### Post by bapoumba on 2014-06-01
Should not, it is still installing/configuring packages. Please let it finish and post any error your might get.

---

### Post by gordon99 on 2014-06-01
No movement - no error messages I'm afraid. I did try putting in my passsword and received the reply "command not found". The last line is still 'gordon@Gordon-HP:~$

---

### Post by bapoumba on 2014-06-01
> **gordon99 said:**
> No movement - no error messages I'm afraid. I did try putting in my passsword and received the reply "command not found". The last line is still 'gordon@Gordon-HP:~$

Is there anything above that ? there should be. If you have not closed the window, please paste them here.
Please alos post the output to :
```
apt-cache policy wine
```

---

### Post by gordon99 on 2014-06-01
Have now quit. No message to say install was still in process. Will make another attempt soon.
Thanks for your help. Will probably be back for more assistance.

---

### Post by bapoumba on 2014-06-01
The command I posted will tell you if it is installed or not. Here is my output, wine is not installed :
```
bapoumba@SonyBlue:~$ apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1:1.6.2-0ubuntu4
  Version table:
     1:1.6.2-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
```

---

### Post by gordon99 on 2014-06-02
Hello again bapoumba,
When I tried to reinstall Wine the program terminated quickly. On reading some of the new download, however, prior to the re-install terminating, I got the impression that the program was  seeing Wine as already installed. I therefore started to look further and in Dash I found a Configuring Wine icon and a Winetricks icon. Unless I hear or find to the contrary I will assume for the present the Wine has, indeed, fully installed. As I explained  earlier, the last line of the original download, which was where I left it when I decided to try another install, was 'gordon@Gordon-HP:~$'. I would have expected the last line to read " Finished" or something similar.
The penultimate line read 'Processing triggers for libc-bin (2.19-0ubuntu6). Unless I hear from you, or someone as knowledgeable, that Wine is definitely not properly installed, I will start another thread for assistance in configuring Wine. The Configuring Wine launcher opens up a screen with a number of tabs for configuration entries.  Thanks once again.

---

### Post by bapoumba on 2014-06-02
Well, I'm not that wine savvy.. May be someone else will know about this error.

---

