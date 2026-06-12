---
title: "Cisco VPN Client Install"
date: 2008-11-18
forum: x86 64-bit Users
---

### Post by nkingcade on 2008-11-18
I am attempting to install the Cisco VPN client on a box. I get the following messages:

Making module
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/neal/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/neal/Desktop/vpnclient/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/neal/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Can someone tell me what the problem is here. Thanks.

Neal

---

### Post by soxs on 2008-11-18
+1 I would like to know that aswell...

though there is cisco compatible opensource client called cvpn, though I don't know how to set it up with the data I got from my university... *g*

---

### Post by russlar on 2008-12-12
go to this site: [http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/](http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/)

follow the instructions exactly, including the comments section at the bottom of the page.

---

### Post by soxs on 2008-12-13
> **russlar said:**
> go to this site: [http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/](http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/)

follow the instructions exactly, including the comments section at the bottom of the page.
Does neither work for my hardy x86_64 nor intrepid x86_64 install work, on 2 different maschines... stuck at compile stage.

---

### Post by soxs on 2009-02-05
Got so, far I get another error. This Flag error can be fixed, by opening the makefile aka [Make] and replacing CFLAGS with EXTRA_CFLAGS

---

### Post by soxs on 2009-02-05
The exact error:
```
[...]
/home/bernhard/Desktop/vpnclient/interceptor.c: In Funktion »recv_ip_packet_handler«:
/home/bernhard/Desktop/vpnclient/interceptor.c:646: Warnung: Zuweisung erzeugt Ganzzahl von Zeiger ohne Typkonvertierung
/home/bernhard/Desktop/vpnclient/interceptor.c:667: Warnung: Übergabe des Arguments 2 von »CniNewFragment« erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/home/bernhard/Desktop/vpnclient/interceptor.c: In Funktion »do_cni_send«:
/home/bernhard/Desktop/vpnclient/interceptor.c:785: Fehler: Ungültige Operanden für binäres - (haben »sk_buff_data_t« und »unsigned char *«)
make[2]: *** [/home/bernhard/Desktop/vpnclient/interceptor.o] Fehler 1
make[1]: *** [_module_/home/bernhard/Desktop/vpnclient] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.27-11-generic'
make: *** [default] Fehler 2
Failed to make module "cisco_ipsec.ko".
```

This patch, intially created for 2.6.24, doesn't seeeem to work anymore: 

wget [http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff](http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff)

[http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/](http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/)

---

### Post by OrkanSpec on 2009-02-06
Hi,

Have you tried vpnc? It had some problems a few years ago, but starting with Ubuntu 8.04 it works perfectly for me.

Connection configuration is stored in /etc/vpnc/*.conf files. There should be an example in that folder.

---

### Post by soxs on 2009-02-06
This would require me to move my cisco config to acvpn config, but I don't know about what fields I actualy have to set?

I will check this out when I am back at university on monday morning.

---

### Post by radamo on 2009-02-06
I am relatively new to linux and install vpnc and the networkmanager-vpnc from synaptic last night.  It was really easy to set up and configure.  I imported my pcf and then used a cisco vpn password decrypter easily found with google. You just have use your text editor on your pcf file to get the decrypted password for your group.  

Connected right away and gives a solid connection. 
RA

---

