---
title: "No FreeNX under uBuntu amd64 = No uBuntu"
date: 2006-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by countryboy on 2006-04-18
I gather that uBuntu Breezy AMD64 doesn't support FreeNX. Which is just wonderful as the organisation I work for wants to run 64-bit apps but also use FreeNX (or any remote session software with multiple sessions).

So it means putting the i386 (32-bit) version on a Dual-core Pentium EM64T machine and running only 32-bit apps or not being able to provide remote sessions to a 64-bit machine.

I think uBuntu is great but to my mind this is basic stuff that should work right out of the box ](*,)

---

### Post by Yagisan on 2006-04-19
last time I checked a) Ubuntu didn't have a FreeNX, and b) FreeNX didn't work right on 64bit.

With a bit of effort you can set up a 64bit kernel, with a mixed 64bit and 32bit userland, and try it like that. That does mean however you become the point of contact when it breaks, and it won't be easy to upgrade.

---

### Post by countryboy on 2006-04-19
Yeah I know uBuntu doesn't have a FreeNX, but it is the fact that you can run FReeNx on the i386 version but not the 64 bit version which irks me

---

### Post by Yagisan on 2006-04-22
[QUOTE=countryboy]Yeah I know uBuntu doesn't have a FreeNX, but it is the fact that you can run FReeNx on the i386 version but not the 64 bit version which irks me[/QUOTE]
How did you run it on i386, Seveas's packages ? If so, I can build that on amd64 for you, just let me know. I obviously can't provide support for it though.

---

### Post by countryboy on 2006-04-23
[QUOTE=Yagisan]How did you run it on i386, Seveas's packages ? If so, I can build that on amd64 for you, just let me know. I obviously can't provide support for it though.[/QUOTE]

Hi Yagisan, that's correct, it was using Sevea's packages. If you could build it on amd64 I would be most grateful.

---

### Post by Yagisan on 2006-04-27
[QUOTE=countryboy]Hi Yagisan, that's correct, it was using Sevea's packages. If you could build it on amd64 I would be most grateful.[/QUOTE]
No worries. I'll check them out and build them.

---

### Post by countryboy on 2006-04-27
[QUOTE=Yagisan]No worries. I'll check them out and build them.[/QUOTE]

Cheers for that. No rush, but thanks for your help.

---

### Post by Yagisan on 2006-04-28
ok. Breezy or Dapper packages ? Dapper can get built tonight/tommorow, but breezy will take a bit longer.

---

### Post by countryboy on 2006-04-28
[QUOTE=Yagisan]ok. Breezy or Dapper packages ? Dapper can get built tonight/tommorow, but breezy will take a bit longer.[/QUOTE]

Breezy please :) sorry!

---

### Post by Yagisan on 2006-04-28
[QUOTE=countryboy]Breezy please :) sorry![/QUOTE]
OK. Packages have been built. Please click the link on my sig, go to the doomsday page, and add the faster mirror. Let me know how it goes for you, as I might have a use for freenx in future. (I don't have a test box to play with at the moment)

---

### Post by countryboy on 2006-04-30
[QUOTE=Yagisan]OK. Packages have been built. Please click the link on my sig, go to the doomsday page, and add the faster mirror. Let me know how it goes for you, as I might have a use for freenx in future. (I don't have a test box to play with at the moment)[/QUOTE]
Thanks Yagisan. I hope to install the amd64 version on a Dell Precision 380 sometime this week, so I'll let you know how it goes.

Cheers

---

### Post by C,Kinnane on 2006-05-02
I say to my colleague - "I think ubuntu for amd 64 might be the way to go to get a decent 64 bit debian based distro and now looks like the time to do it."

First thing I want do is install freenx - so I'm here and it seems now is the time!

I gave it a shot by setting up e-yagi's repository and installing everything "nx"

I already have my client configured here on my debian sarge box with a 32-bit breezy freenx server box working well.

apt suggested xdm and expectk which it couldn't find yet - I just installed this today and havn't checked out other allavailble repositories yet. Everything else suggested and required was installed.

I tried to connect and it manages to initialise the X-server before failing.

Here is what I see in /var/log/messages on the server:

May  3 03:09:25 localhost kernel: [35620.505987] nxagent[9335]: segfault at ffff
ffffffffffe4 rip 00002aaaab3e8c56 rsp 00007fffffa24d40 error 6

So, anyone else tried this yet ? does it need more work or am I maybe missing something ?

---

### Post by countryboy on 2006-05-02
Hi Yagisan (and C,Kinnane)

I have also just installed FreeNX on a brand new Dell, running latest version of Breezy, and I also get the same error message as above (bar one or two minor differences in the 00002aaaaab....... section). It seems to connect without a problem and only when it attempts to create the X session it seems to bomb out.

Below is the log from my client side:

Info: Proxy running in client mode with pid '3512'.
Info: Connecting to remote host '130.155.72.156:5001'.
Info: Connection to remote proxy '130.155.72.156:5001' established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Not using NX delta compression.
Info: Using lan link parameters 16384/8/0/0.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Not using ZLIB stream compression.
Info: Not using remote ZLIB stream compression.
Info: Not using persistent cache.
Info: Using remote server '130.155.72.156:5001'.
Info: Forwarding multimedia connections to port '16000'.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Error: Lost connection to peer proxy on FD#10.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.

About to do a reboot and see if it is any different, but I don't expect so.

---

### Post by Yagisan on 2006-05-04
This probally isn't going to be good news, but reading both error messages here (and looking at what gentoo does), leads me to believe freenx, still is incapable of correctly running as a 64bit application. :( (gentoo advise installing a 32bit freenx if possible on their wiki)

That rather sucks, as I've been moving my infrastructre to all amd64 boxes, and I was hoping to hear good news from you guys.

---

### Post by geigerkr on 2006-05-09
I get the same as countryboy on my AMD64 box.  Has anyone been able to get past this?

May  9 02:48:07 localhost kernel: [1479940.279496] nxagent[7240]: segfault at ffffffffffffffe4 rip 00002aaaab3f1c96 rsp 00007fffffa750c0 error 6

Below is what lead me to your post on the segmentation fault after changing the COMMAND_XAUTH, COMMAND_XSET, COMMAND_XMODMAP, and COMMAND_XKBCOMP directives in /etc/nxserver/node.conf:

Info: Established X server connection.
Info: Using shared memory support in X server.
Error: Lost connection to peer proxy on FD#11.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.

It appears to create the session successfully, then the connection dies due to the segmetation fault:

sudo nxserver --list

Display Username        Remote IP       Session ID
------- --------------- --------------- --------------------------------
1033    karlg   127.0.0.1       627EA0D1BB99BC0956B514A473784AD3
1036    karlg   127.0.0.1       8FE9A3E5760541743E55B8C13BD2ADF1
1035    karlg   127.0.0.1       9F9D396003D900439C2B2356E960F1E3
1034    karlg   192.168.0.100   A84A6F9D6AC21D53D4A7C2E2C104A2CD

---

