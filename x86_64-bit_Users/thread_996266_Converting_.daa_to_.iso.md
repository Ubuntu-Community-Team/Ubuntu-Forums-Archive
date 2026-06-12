---
title: "Converting .daa to .iso"
date: 2008-11-28
forum: x86 64-bit Users
---

### Post by Dotkito on 2008-11-28
Alright, I have tried all sorts of commands in Terminal, I am going to copy and paste what I have.

```
robert@robert-itails:~$ ./poweriso convert Windows Xp Pro Sp3 3264 Vista Style.daa -o image.iso -ot iso

PowerISO   Copyright(C) 2004-2007 PowerISO Computing, Inc
            Type poweriso -? for help

Unrecognized parameter: Xp
robert@robert-itails:~$ -?
bash: -?: command not found
robert@robert-itails:~$  -?
bash: -?: command not found
robert@robert-itails:~$ ./poweriso convert Windows_Xp_Pro_Sp3_3264_Vista_Style.daa -o Windows_XP_Pro.iso -ot iso

PowerISO   Copyright(C) 2004-2007 PowerISO Computing, Inc
            Type poweriso -? for help

Windows_Xp_Pro_Sp3_3264_Vista_Style.daa: No such file or directory
robert@robert-itails:~$ ./poweriso convert /home/robert/desktop/Windows Xp Pro Sp3 3264 Vista Stlye.daa -o Windows XP Pro SP3.iso -ot iso

PowerISO   Copyright(C) 2004-2007 PowerISO Computing, Inc
            Type poweriso -? for help

Unrecognized parameter: Xp
robert@robert-itails:~$ ./poweriso convert /home/robert/desktop/windows_xp_sp3_3264_vista_style.daa -o Windows_XP_Pro_SP3.iso -ot iso

PowerISO   Copyright(C) 2004-2007 PowerISO Computing, Inc
            Type poweriso -? for help

/home/robert/desktop/windows_xp_sp3_3264_vista_style.daa: No such file or directory
robert@robert-itails:~$ ./poweriso convert /home/robert/desktop/windows_xp_sp3_3264_vista_style.daa -o /home/robert/desktop/Windows_XP_SP3.iso -ot iso

PowerISO   Copyright(C) 2004-2007 PowerISO Computing, Inc
            Type poweriso -? for help

/home/robert/desktop/windows_xp_sp3_3264_vista_style.daa: No such file or directory
robert@robert-itails:~$ ./poweriso convert /home/robert/Desktop/Windows_Xp_Sp3_3264_Vista_Style.daa -o /home/robert/Desktop/Windows_Xp_Sp3_3264_Vista_Style.iso -ot iso

PowerISO   Copyright(C) 2004-2007 PowerISO Computing, Inc
            Type poweriso -? for help

/home/robert/Desktop/Windows_Xp_Sp3_3264_Vista_Style.daa: No such file or directory
robert@robert-itails:~$ 

```

Any way I can convert this? I am using PowerISO and it doesn't seem to find directories.

---

### Post by stinger30au on 2008-11-28
install acetoneiso from getdeb

[http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by Dotkito on 2008-11-28
Omg, thanks so much, I couldn't remember if it was getdeb or debwarehouse. lol

again, thanks

---

### Post by archman on 2009-03-03
nonsense installing software for that...use daa2iso from [http://aluigi.altervista.org/mytoolz.htm](http://aluigi.altervista.org/mytoolz.htm)

go to src dir, make, and run! ./daa2iso xyz.daa xyz.iso

---

### Post by rexo on 2009-04-03
You shouldn't use "spaces" in you file names. Rename it to something like Windows_Xp_Pro_...daa. If you want to use spaces, then type "\" before each one:

./poweriso convert Windows\ Xp\ Pro\ Sp3\ 3264\ Vista\ Style.daa -o image.iso -ot iso

---

