---
title: "K8N Diamond fail start X"
date: 2005-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by sunche_locus on 2005-04-11
I use MSI K8n Diamon moterhbroad.
Use the nv driver , xorg display normally.
When I use nvidia-1-7174 then it show Device Error!!
I think it maybe I place only one GT6200 vedio card on K8N Diamond.
Please help!

[COLOR=Red]xorg.conf==>[/COLOR]
...
Section "Device"
	Identifier	"Nvidia GT6200"
	Driver		"nv"
        #Option          "SWCursor" "true"
        #Option          "NoRenderExtension" "true"
	VideoRam	128000
EndSection


[COLOR=Red]Xorg.0.log==>[/COLOR]
X Window System Version 6.8.2 (Ubuntu (static) 6.8.2-10 20050405154247 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 x86_64 [ELF]
Current Operating System: Linux ubuntu 2.6.11-1-amd64-k8 #1 Fri Feb 11 14:45:56 UTC 2005 x86_64
Build Date: 05 April 2005
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
OS Kernel: Linux version 2.6.11-1-amd64-k8 (buildd@yellow) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Feb 11 14:45:56 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 11 20:37:00 2005
(==) Using config file: "/etc/X11/xorg.conf"

(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
        i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, 915GM
(II) FBDEV: driver for framebuffer: fbdev, afb
(II) v4l driver for Video4Linux
(II) Primary Device is: PCI 05:00:0
[COLOR=Red](EE) No devices detected.[/COLOR]

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at [http://wiki.X.Org](http://wiki.X.Org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

