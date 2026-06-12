---
title: "VMWARE Issues"
date: 2006-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by csalsb on 2006-12-17
I just installed VMware 5.5.2 and I also tried 5.5.3 as well.  The program installs with no issues, and it tells me that It has installed and can be run by executing the /usr/bin/vmware command.  I do this over and over again and I get the same problem:
[B]
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.[/B]

I have ran the configuration over and over again and get the same problem.  Any help on this issue would be greatly appreciated.

csalsb

---

### Post by melancholeric on 2006-12-17
sudo mv /etc/vmware/not_configured /etc/vmware/not_configured_backup

---

### Post by psycho78 on 2006-12-17
Try this:  sudo vi /usr/bin/vmware

and put in 
LD_PRELOAD=/usr/lib/libdbus-1.so.3
export LD_PRELOAD

right after #!/bin/sh
and give it another try....this helped me out! :)

---

### Post by csalsb on 2006-12-17
ok I tried both of those ideas and neither worked.  So I tried to reinstall from scratch and then I noticed the following error at the beginning:

/usr/bin/ldd: line 171: /lib/ld-linux.so.2: No such file or directory
ldd: /lib/ld-linux.so.2 exited with unknown exit code (127)
Making sure services for VMware Workstation are stopped.

 it then runs thorugh the entire configuration and then says installed sucessfully.  NOt sure what to make of this, but I have to believe that the above error is causing my grief.

thanks for the help so far, and hopefully we can get this rolling.

csalsb

---

### Post by csalsb on 2006-12-17
alright fixed it.  You need to install the 32 bit emulaton libraries in order for VMware to install correctly and run.  You need to have the Ia32-libs and the Ia32-libs-gtk installed in order to get vmware upand running.

csalsb

---

### Post by csalsb on 2006-12-17
Sorry forgot to change the topic to solved

---

