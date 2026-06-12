---
title: "Flash 9 on AMD 64 system"
date: 2007-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by andy_b on 2007-06-02
Hello, I run Dapper Drake with the architecture for AMD 64.  I have a 32 bit version of Opera that I use when I want to use Flash.  My problem is, my version of flash is out dated and I can't seem to get flash 9 working.  I've tried hacking it like I did to flash 7 but that didn't seem to work.  Any suggestions on how to get Flash 9 working for Opera?

---

### Post by Case_f on 2007-06-02
[http://ubuntuforums.org/showthread.php?t=413040](http://ubuntuforums.org/showthread.php?t=413040)

---

### Post by Ubivetz on 2007-06-02
```

$ wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
$ tar -xzf install_flash_player_9_linux.tar.gz
$ cp sudo cp libflashplayer.so /usr/lib/opera/plugins
$ sudo cp flashplayer.xpt /usr/lib/opera/plugins

```

---

### Post by henri915 on 2007-06-02
> **Ubivetz said:**
> ```

$ wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
$ tar -xzf install_flash_player_9_linux.tar.gz
$ cp sudo cp libflashplayer.so /usr/lib/opera/plugins
$ sudo cp flashplayer.xpt /usr/lib/opera/plugins

```

Does the same thing work for Firefox, omitting "Opera" and inserting "firefox"?

---

### Post by JAPrufrock on 2007-06-02
In 32 bit firefox libflashplayer.so should be copied or symbolic linked to >  /usr/lib32/firefox32/plugins/

---

### Post by andy_b on 2007-06-03
Thank you everyone.  That was easier than I thought.

---

### Post by andy_b on 2007-06-03
Ah dag nabbit!  Alot of the flash vids show up as blank screens with audio only, any idea's what the problem could be?

---

