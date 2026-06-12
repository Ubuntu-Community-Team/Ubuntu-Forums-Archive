---
title: "Segmentation Fault"
date: 2008-11-18
forum: x86 64-bit Users
---

### Post by nkingcade on 2008-11-18
What is a "segmentation fault"? I get the following response when starting the Cisco VPN client:

neal@nealvinho:~$ sudo vpnclient connect VDH_VPN
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Segmentation fault


Thanks in advance.

Neal

---

### Post by felker2 on 2008-11-19
A software crash. See [http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault):

"A segmentation fault occurs when a program attempts to access a memory location that it is not allowed to access, or attempts to access a memory location in a way that is not allowed (for example, attempting to write to a read-only location, or to overwrite part of the operating system)."

---

### Post by dcstar on 2008-11-19
> **nkingcade said:**
> What is a "segmentation fault"? I get the following response when starting the Cisco VPN client:

neal@nealvinho:~$ sudo vpnclient connect VDH_VPN
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Segmentation fault


Thanks in advance.

Neal

Last time I compiled the Cisco client, I had to apply the special 64-bit patches, did you do this?

---

### Post by nkingcade on 2008-11-19
I applied the "offset" patch and the [B]vpnclient-linux-2.6.22.diff. Rebooted the machine. started the service and the client. Any ideas on a fix. 
[/B]

---

### Post by burghman on 2008-12-10
Installed the latest vpn client on Intrepid according to [Oleg's post #42]("http://www.blog.arun-prabha.com/2008/05/01/cisco-vpn-installation-issue-with-ubuntu-804-hardy-heron/"). Supposedly the 2.6.24 vpnclient patch is not required with this version.  I installed the cisco_skbuff_offset.patch, changed CFLAGS to EXTRA_CFLAGS in the Makefile and ran vpn_install.

Despite the clean build, there is a segmentation fault when trying to connect.  Has anyone made any progress with this problem?  Any ideas on how to troubleshoot it?

/vpnclient$ sudo vpnclient connect Scottsdale
Cisco Systems VPN Client Version 4.8.02 (0030)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Segmentation fault

---

### Post by GordonPMartin on 2009-01-19
I am experiencing the exact same problem.  Has anyone found a fix yet?

I am using Cisco VPN client ver. 4.8.02.0030 on Ubuntu 8.10 64 bit.
I have modified the makefile for the EXTRA_CFLAGS and run the patch cisco_skbuff_offset.patch.

It seemed to install just fine with no errors. The vpnclient_init start
seemed to work just fine as well. But when I try to connect the client with "sudo vpnclient connect MyProfile" I get the Segmentation fault.


Thanks for any help,

Gordon

---

### Post by GordonPMartin on 2009-01-19
It looks like my segmentation fault was being caused by a value in my .pcf profile file.  I no longer get the error if I remove the enc_GroupPwd value.

Now when I run it I get asked for my group password.  But then it says "Initializing the VPN connection" before timing out with the error "The VPN sub-system is busy or has failed."

If I retry, the client just tells me that "The application was unable to communicate with the VPN sub-system".

My troubleshooting continues!

---

### Post by smillerlsu on 2009-02-21
I'm seeing this on multiple systems now... I compile / run exactly as burghman and GordonPMartin and get the same results. I have compiled this on a PhenomX3 with 8.10 and now an AthlonX2 with Jaunty Alpha4... 

On a side note, What is really frustrating me is I can connect with VPNC, but for some reason can't get X11 forwarding to work successfully (xclock doesn't launch on my machine, even though ForwardX11 is enabled and I have done the setenv DISPLAY xxx.xxx.xxx.xxx:0 on the remote server).

I wish I even knew what to check!

---

### Post by steffx on 2009-05-12
Hi,
maybe you can try this set of patches:

[http://forum.tuxx-home.at/viewtopic.php?uid=3352&f=15&t=767&start=0](http://forum.tuxx-home.at/viewtopic.php?uid=3352&f=15&t=767&start=0)

cheers,
s

---

