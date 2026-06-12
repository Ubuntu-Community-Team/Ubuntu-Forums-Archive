---
title: "Server downing ethernet card for no reason"
date: 2008-10-26
forum: x86 64-bit Users
---

### Post by jaie on 2008-10-26
For some unknown reason, one of the network cards on my server seems to drop off every few weeks. Here are the logs:

Oct 26 08:07:21 servervpn -- MARK --
Oct 26 08:27:21 servervpn -- MARK --
Oct 26 08:47:21 servervpn -- MARK --
Oct 26 08:57:07 servervpn kernel: [321610.270827] r8168: eth1: link down
Oct 26 08:57:09 servervpn kernel: [321612.243075] r8168: eth1: link up
Oct 26 08:57:37 servervpn kernel: [321640.737254] r8168: eth1: link down
Oct 26 09:27:22 servervpn -- MARK --
Oct 26 09:47:22 servervpn -- MARK --
Oct 26 10:07:22 servervpn -- MARK --

This occurred on Sunday, when nobody was at the office and caused great havoc on Monday morning. Does anybody have any idea as to why this may happen or what steps I can take to try and find out?

The machine has two ethernet cards and eth0 seems to be fine.

---

### Post by ABCC on 2008-10-27
Is that an internal or external network card? It could be that your ISP and/or a system on the other end of the wire resets the connection from their end once in a while? 

From the log it looks like the link came back straight away, what sort of mayhem resulted from this?

ABCC

---

### Post by Yellow Pasque on 2008-10-27
One thing to check - make sure there are no power-saving options for the LAN card in the BIOS if you need a constant connection.

---

### Post by jaie on 2008-10-27
> **ABCC said:**
> Is that an internal or external network card? It could be that your ISP and/or a system on the other end of the wire resets the connection from their end once in a while? 

From the log it looks like the link came back straight away, what sort of mayhem resulted from this?

ABCC

eth1 is the external network card. I can not confirm that the external device is to blame (Linksys Router connected to Cisco BDSL Modem), but I don't believe that the other end is to blame because restarting the server fixed the problem.

Because this computer is acting as the vpn connection, it caused havoc when people tried to vpn in and couldn't. Its setup for both OpenVPN and Poptop, DNS, Mailserver, Fileserver, Squid Proxy as well as some other things.

Unless I'm reading the logs wrong it appears to me that the link did come back straight away the first time, but a few minutes later it went down and did not come back up.

---

### Post by jaie on 2008-10-29
I had the same problem occur again today. This after a reboot the card didn't come up and I had to reboot it again. It seems as if it is getting more frequent. Here is the log i have cat /var/log/messages | grep eth

Oct 29 23:22:11 servervpn kernel: [229856.314982] r8168: eth1: link up
Oct 29 23:22:42 servervpn kernel: [229886.982291] r8168: eth1: link down
Oct 29 23:22:44 servervpn kernel: [229888.700325] r8168: eth1: link up
Oct 29 23:24:18 servervpn kernel: [229982.542604] r8168: eth1: link down
Oct 29 23:24:20 servervpn kernel: [229984.105781] r8168: eth1: link up
Oct 29 23:40:16 servervpn kernel: [230934.975458] r8168: eth1: link down
Oct 29 23:40:18 servervpn kernel: [230936.544527] r8168: eth1: link up
Oct 30 03:53:17 servervpn kernel: [246019.113075] r8168: eth1: link down
Oct 30 03:53:18 servervpn kernel: [246020.682550] r8168: eth1: link up
Oct 30 04:06:08 servervpn kernel: [246785.337901] r8168: eth1: link down
Oct 30 04:06:10 servervpn kernel: [246786.896035] r8168: eth1: link up
Oct 30 04:16:33 servervpn kernel: [247406.210297] r8168: eth1: link down
Oct 30 04:16:34 servervpn kernel: [247407.855086] r8168: eth1: link up
Oct 30 04:17:04 servervpn kernel: [247437.368353] r8168: eth1: link down
Oct 30 04:17:06 servervpn kernel: [247439.073425] r8168: eth1: link up
Oct 30 04:20:14 servervpn kernel: [247626.091596] r8168: eth1: link down
Oct 30 04:20:16 servervpn kernel: [247627.675247] r8168: eth1: link up
Oct 30 10:45:29 servervpn kernel: [270594.118709] r8168: eth1: link down

--- REBOOT BECAUSE eth1 DOESN'T COME BACK UP

Oct 30 11:19:23 servervpn kernel: [   40.568379] eth0: DGE-530T Gigabit Ethernet Adapter
Oct 30 11:19:23 servervpn kernel: [   43.240887] eth0: network connection up using port A
Oct 30 11:21:03 servervpn kernel: [  204.140719] device eth0 entered promiscuous mode
Oct 30 11:31:14 servervpn kernel: [  811.128899] device eth0 left promiscuous mode

--- REBOOT BECAUSE eth1 DIDN"T COME UP ON STARTUP

Oct 30 11:32:43 servervpn kernel: [   32.951145] eth0: DGE-530T Gigabit Ethernet Adapter
Oct 30 11:32:43 servervpn kernel: [   33.217969] eth1: RTL8168B/8111B at 0xffffc200100a4000, 00:19:db:88:62:b4, IRQ 201
Oct 30 11:32:43 servervpn kernel: [   33.380757] r8168: eth1: link down
Oct 30 11:32:43 servervpn kernel: [   34.772850] r8168: eth1: link up
Oct 30 11:32:43 servervpn kernel: [   36.025740] eth0: network connection up using port A
Oct 30 11:31:57 servervpn kernel: [   69.771012] r8168: eth1: link down
Oct 30 11:31:59 servervpn kernel: [   71.409620] r8168: eth1: link up
Oct 30 11:32:39 servervpn kernel: [  111.158379] device eth0 entered promiscuous mode

---

### Post by 080729jk on 2008-10-30
&#21271;&#20140;&#39640;&#20048;&#36974;&#38451;&#26377;&#38480;&#20844;&#21496; &#65292;[**&#22826;&#38451;&#20254;**](http://www.korack.cn/cp_qt_diaosan.htm)&#26159;&#20197;&#29983;&#20135;&#24191;&#21578;&#20254;&#20026;&#20027;&#65292;&#22810;&#20803;&#21270;&#32463;&#33829;&#30340;&#22823;&#22411;&#21046;&#20254;&#20225;&#19994;&#65292;&#20225;&#19994;&#20135;&#21697;&#28041;&#21450;&#24191;&#21578;&#20254;&#12289;&#36974;&#38451;&#31735;&#12289;&#20419;&#38144;&#23637;&#21488;&#21450;&#25143;&#22806;&#20241;&#38386;&#29992;&#21697;&#12290;&#20027;&#23548;&#20135;&#21697; &#8220; &#39640;&#20048; &#8221; &#29260;&#24191;&#21578;&#36974;&#38451;&#20254;&#65292;[**&#22826;&#38451;&#20254;**](http://www.korack.cn/cp_qt_diaosan.htm)&#36830;&#32493;&#21313;&#24180;&#34987;&#20013;&#22269;&#28040;&#36153;&#32773;&#22522;&#37329;&#20250;&#35780;&#20026;&#8220;&#28040;&#36153;&#32773;&#20449;&#36182;&#30340;&#30693;&#21517;&#21697;&#29260;&#8221;&#65292;&#24182;&#34987;&#21271;&#20140;&#24066;&#36136;&#37327;&#25216;&#26415;&#30417;&#30563;&#23616;&#25480;&#20104;&#8220;&#25216;&#26415;&#30417;&#30563; 12365 &#29702;&#20107;&#21333;&#20301;&#8221;&#65292; AAA &#32423;&#20449;&#29992;&#31561;&#32423;&#20225;&#19994;&#65307; &#25317;&#26377;&#22269;&#23478;&#27880;&#20876;&#30340;&#39640;&#20048;&#29260;&#21830;&#26631;&#12290;     &#39640;&#20048;&#20135;&#21697;&#30340;&#36136;&#37327;&#21644;&#25216;&#26415;&#24037;&#33402;&#22312;&#20840;&#22269;&#21046;&#20254;&#34892;&#19994;&#20013;&#22788;&#20110;&#39046;&#20808;&#22320;&#20301;&#65292;[**&#24191;&#21578;&#20254;**](http://www.korack.cn/cp_ggs.htm)&#22312;&#22269;&#20869;&#22806;&#24066;&#22330;&#20139;&#26377;&#24456;&#39640;&#30340;&#22768;&#35465;&#12290; &#32463;&#36807;&#21313;&#22810;&#24180;&#30340;&#36805;&#36895;&#21457;&#23637;&#65292;&#39640;&#20048;&#30340;&#21592;&#24037;&#24050;&#22686;&#33267; 200&#22810;&#20154;&#65292;&#29616;&#24050;&#25104;&#20026;&#22269;&#20869;&#24191;&#21578;&#20254;&#30340;&#26368;&#22823;&#20379;&#24212;&#21830; &#65292;[**&#24191;&#21578;&#20254;**](http://www.korack.cn/cp_ggs.htm)&#22312;&#36896;&#22411;&#35774;&#35745;&#12289;&#25216;&#26415;&#24037;&#33402;&#12289;&#38754;&#26009;&#12289;&#21253;&#35013;&#31561;&#26041;&#38754;&#37117;&#26377;&#20102;&#36739;&#22823;&#30340;&#21019;&#26032;&#21644;&#31361;&#30772;&#65292;&#24050;&#32463;&#36798;&#21040;&#22269;&#38469;&#20808;&#36827;&#27700;&#24179; &#12290;   ** **[**&#24191;&#21578;&#20254;**](http://www.korack.cn/cp_ggs.htm) &#22312;&#22269;&#20869;&#39640;&#20048;&#25317;&#26377;&#24378;&#22823;&#30340;&#23458;&#25143;&#32676;&#20307;&#65292;&#21516;&#22269;&#20869;&#22806;&#35768;&#22810;&#30693;&#21517;&#22823;&#20225;&#19994;&#37117;&#26377;&#38271;&#26399;&#30340;&#21512;&#20316;&#65292;&#22914;&#65306;&#21487;&#21475;&#21487;&#20048;&#65292;&#30334;&#20107;&#21487;&#20048;&#12289;&#20234;&#21033;&#12289;&#38592;&#24034;&#12289;&#40614;&#24403;&#21171;&#12289;&#26397;&#26085;&#21860;&#37202;&#12289;&#21644;&#38706;&#38634;&#31561;&#65307;&#39640;&#20048;&#29260;&#24191;&#21578;&#36974;&#38451;&#20254;&#22312; &#22269;&#20869;&#24066;&#22330;&#21344;&#26377;&#29575;&#36830;&#32493; 10 &#24180;&#20445;&#25345; 50 &#65285;&#24038;&#21491;&#12290;&#12288;&#12288;&#20844;&#21496;&#20197; &#8220; &#20248;&#36136;&#38136;&#21697;&#29260;&#65292;&#35802;&#20449;&#25602;&#22825;&#19979; &#8221; &#20026;&#32463;&#33829;&#23447;&#26088;&#65292;&#31215;&#26497;&#21019;&#26032;&#65292;&#25552;&#39640;&#21697;&#29260;&#65292;&#22686;&#24378;&#20248;&#21183;&#65292;&#25512;&#21160;&#20102;&#22269;&#20869;&#24191;&#21578;&#20254;&#24037;&#33402;&#21644;&#24191;&#21578;&#20254;&#25991;&#21270;&#30340;&#21457;&#23637;&#12290;&#30446;&#21069;&#65292;&#20844;&#21496;&#22312;&#21697;&#29260;&#12289;&#36136;&#37327;&#12289;&#25216;&#26415;&#12289;&#24066;&#22330;&#12289;&#35268;&#27169;&#21644;&#25928;&#30410;&#31561;&#26041;&#38754;&#25317;&#26377;&#20102;&#30456;&#24403;&#31283;&#23450;&#30340;&#23454;&#21147;&#20248;&#21183;&#65292;&#25104;&#20026;&#25105;&#22269;&#24191;&#21578;&#20254;&#21046;&#20316;&#34892;&#19994;&#30340;&#40857;&#22836;&#20225;&#19994;&#21644;&#20248;&#31168;&#20195;&#34920;&#12290;

---

### Post by jaie on 2008-11-17
The network card was changed and the eth-up eth-down trouble went away. Touch wood the machine seems to be running without any trouble now.

---

