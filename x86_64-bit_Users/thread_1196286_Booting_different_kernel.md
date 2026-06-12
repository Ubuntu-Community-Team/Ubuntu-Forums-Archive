---
title: "Booting different kernel?"
date: 2009-06-24
forum: x86 64-bit Users
---

### Post by Dreen on 2009-06-24
Hello,

My current problem is the following:
My usual computer has amd 64 bit and so it runs Xubuntu-amd64. I went home for holiday but my laptop died recently so to take my files with me I took the hdd from the usual computer. A lack of foresight on my part, all computers in my home are intel, 32 bit. I can access the files from Ubuntu LiveCD (which, in fact, I am using right now) but I cant boot the system due to wrong kernel. I would really like to boot the system, if only for all the apps I already have there. Can I just put a different kernel on the linux partition on the hdd via the LiveCD and boot it? How would I go about doing so? Cheers.

---

### Post by sebastianabate on 2009-06-25
You cannot install the 32bit kernel and boot your computer, because every executable and library installed are 64bits, and cannot be used in a 32bit enviroment. You must backup every configuration (/etc, /home/user, /var/lib/every_service_you_have_installed) and reinstall your system.

PD: Sorry for my english, I'm from Argentina.

---

### Post by Dreen on 2009-06-25
Thanks sebastianabate, I guess this is an only option.

---

