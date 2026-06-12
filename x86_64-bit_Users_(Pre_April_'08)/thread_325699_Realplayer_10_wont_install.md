---
title: "Realplayer 10 wont install"
date: 2006-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by vikrant_me on 2006-12-26
I downloaded the realplayer10.bin frm real networks as mentioned in this post:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29)


    *  Download Realplayer's Official Linux Version 

Then add execute permissions to the installer and execute it.

chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

when i try to execute it says:

vicky@vicky-desktop:~/Desktop$ ./RealPlayer10GOLD.bin 
bash: ./RealPlayer10GOLD.bin: No such file or directory
vicky@vicky-desktop:~/Desktop$ 

even when i can see the file there!

---

### Post by uniko on 2006-12-26
You could try copying the file to another folder and try launching installer from there. I remember having similar problems long ago and I think moving files from desktop to elsewhere helped.

---

### Post by vikrant_me on 2006-12-26
tried it...din work...

---

### Post by rajeev1204 on 2006-12-28
hi

move it to home folder




regards

rajeev

---

### Post by pynux on 2006-12-28
install realplayer :

```

$ sudo apt-get install linux32 ia32-libs  ia32-libs-gtk lib32asound2 lib32stdc++6
$ wget http://software-dl.real.com/26609df6fe4765c0c717/helix/20061125/player_all-realplay_gtk_current-20061125-linux-2.2-libc6-gcc32-i586@rhel4/realplay-10.1.0.2554-linux-2.2-libc6-gcc32-i586.bin
$ chmod +x realplay-10.1.0.2554-linux-2.2-libc6-gcc32-i586.bin
$ sudo ./realplay-10.1.0.2554-linux-2.2-libc6-gcc32-i586.bin
(install in /usr/lib32/RealPlayer )

$ sudo mkdir /usr/lib/plugin-web32
$ cp /usr/lib32/RealPlayer/mozilla/* /usr/lib/plugin-web32/


```

---

### Post by Pointman on 2007-01-04
I am having the exact same problem..  I moved it from desktop to my home folder still the same result I can even rename the file, but when i tried to execute it it gives me the same error..  I am going to try the last suggestion, but being a linux newbie i'm not sure exactly what i am accomplishing by doing this..  

It looks as if I am installing 32 bit support for my 64bit kernel??  dunno I will try it and post my results

---

### Post by Pointman on 2007-01-04
These are my results..  not too encouraging


jason@JasonUbuntu:~$ wget [http://software-dl.real.com/26609df6fe4765c0c717/helix/20061125/player_all-realplay_gtk_current-20061125-linux-2.2-libc6-gcc32-i586@rhel4/realplay-10.1.0.2554-linux-2.2-libc6-gcc32-i586.bin](http://software-dl.real.com/26609df6fe4765c0c717/helix/20061125/player_all-realplay_gtk_current-20061125-linux-2.2-libc6-gcc32-i586@rhel4/realplay-10.1.0.2554-linux-2.2-libc6-gcc32-i586.bin)
--17:24:24--  [http://software-dl.real.com/26609df6fe4765c0c717/helix/20061125/player_all-realplay_gtk_current-20061125-linux-2.2-libc6-gcc32-i586@rhel4/realplay-10.1.0.2554-linux-2.2-libc6-gcc32-i586.bin](http://software-dl.real.com/26609df6fe4765c0c717/helix/20061125/player_all-realplay_gtk_current-20061125-linux-2.2-libc6-gcc32-i586@rhel4/realplay-10.1.0.2554-linux-2.2-libc6-gcc32-i586.bin)
           => `realplay-10.1.0.2554-linux-2.2-libc6-gcc32-i586.bin'
Resolving software-dl.real.com... 66.203.123.22
Connecting to software-dl.real.com|66.203.123.22|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:24:35 ERROR 404: Not Found.

---

### Post by Pointman on 2007-01-04
Good news after running the first command

$ sudo apt-get install linux32 ia32-libs  ia32-libs-gtk lib32asound2 lib32stdc++6

I can now execute the program..  now lets see if i can figure out how to use it. rofl

---

### Post by Aphorism on 2007-01-06
If you push the libtotem* plugins out of your /usr/lib/firefox/plugins directory and install mozilla-mplayer plugin you can listen and play most RealPlayer content like the BBC, etc.  No need for Realplayer for much anymore.

---

### Post by pennyminstrel on 2007-10-28
Just wanted to say thanks to the guys that helped. I was having just the same problems, copied the file to my home folder and it worked like magic! It asked for confirmation of a few commands I wasn´ t sure of but i just confirmed them all and it worked! And presumably it might work in other similar situations, so I´ve learnt something too. Thanks again

---

