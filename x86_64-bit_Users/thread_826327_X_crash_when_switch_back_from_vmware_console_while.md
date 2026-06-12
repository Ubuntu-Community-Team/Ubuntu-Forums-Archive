---
title: "X crash when switch back from vmware console while playing music"
date: 2008-06-11
forum: x86 64-bit Users
---

### Post by astranberg on 2008-06-11
I'm not quite sure where to post this odd problem.  I have 8.04 64bit, and the latest vmware server installed.  It seems that when I switch from the x desktop to the vmware console while playing music (audacious) x crashes.  I checked dmesg and found messages similar to:
"[21811.833618] vmmon: Had to deallocate locked 1337 pages from vm driver ffff81002a09a000
[21811.842469] vmmon: Had to deallocate AWE 2557 pages from vm driver ffff81002a09a000"

the frequency of these messages seems to correlate with my x crashes.  Any suggestions on how to trouble shoot this.  I am currently following the "if it hurts then stop moving you arm" philosophy of no music while working in vmware, which makes life alot more boring.

Additional details
Ideapad y510
nvidia video card
4gb mem
t5550 processor



Thanks
-Aaron

---

### Post by pietro2580 on 2009-06-17
I have exactly the same message, and it occurs *very* frequently last days. Did you find a solution for your problem?

[ 8245.085262] vmmon: Had to deallocate locked 208560 pages from vm driver f6279a00
[ 8245.087502] vmmon: Had to deallocate AWE 6627 pages from vm driver f6279a00

Thanks

---

### Post by pietro2580 on 2009-06-17
In my case it is not when playing music, but just running vmware console.

---

### Post by rocketship on 2009-06-17
This just started happening to me today - running Vmware Workstation version 6.5.1 on Ubuntu 64 (Jaunty).  Amarok was also running...though I've worked in this same setup for a few weeks with no problem.  Could this be related to the kernel update that just happened? (linux-generic (2.6.28.12.16) to 2.6.28.13.17)

I'm also using a tethered Blackberry through pppd.  Here's the log lines around the event:
```
Jun 17 16:49:03 asterix pppd[23408]: Hangup (SIGHUP)
Jun 17 16:49:03 asterix pppd[23408]: Connect time 32.2 minutes.
Jun 17 16:49:03 asterix pppd[23408]: Sent 834906 bytes, received 10465552 bytes.
Jun 17 16:49:03 asterix pppd[23408]: restoring old default route to eth0 [192.168.0.111]
Jun 17 16:49:03 asterix kernel: [23930.497151] vmmon: Had to deallocate locked 294868 pages from vm driver ffff880214c52400
Jun 17 16:49:03 asterix kernel: [23930.498883] vmmon: Had to deallocate AWE 4936 pages from vm driver ffff880214c52400
Jun 17 16:49:03 asterix kernel: [23930.502462] device virbr0 left promiscuous mode
Jun 17 16:49:03 asterix kernel: [23930.502465] bridge-virbr0: disabled promiscuous mode
```

RS

---

### Post by kerrin on 2009-06-21
Same problem...    Only the last couple of days...

Jun 22 14:52:04 IBMT-G500 kernel: [21270.628457] vmmon: Had to deallocate locked 474709 pages from vm driver f0319c00
Jun 22 14:52:04 IBMT-G500 kernel: [21270.636951] vmmon: Had to deallocate AWE 8700 pages from vm driver f0319c00
Jun 22 14:52:05 IBMT-G500 gdm[3454]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

:confused:

---

### Post by kerrin on 2009-06-22
Earlier today I disabled Compiz desktop effects and ran for 4 hours without an X crash...   

Reading between the lines it appeared to me to be something to do with the Video drivers, however I've just remembered upgrading to kernel 2.6.28-13.44 a couple of days ago - which coincides with the issue starting.

For now I've gone back to the previous version 2.6.28-11.42 to be on the safe side until the cause of the issue is confirmed by someone more knowledgeable than myself.

---

### Post by samR on 2009-07-02
hello,

I have the same problem, and same messages in the dmesg 

[ 2468.749403] vmmon: Had to deallocate locked 177706 pages from vm driver f4c51e00
[ 2468.751236] vmmon: Had to deallocate AWE 4952 pages from vm driver f4c51e00

I am not sure when it happens and how to reproduce the issue. It seem to happen when I go back to VM player, after spending "some" time (10, 20 minute?) doing something else (not necessarily playing music, but working with OpenOffice for example, or may be even doing nothing?)
I use ubuntu 9.04 on DELL latitude D830.

output of the uname -a command:
Linux sappcr62 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

This morning kernel's update (#45) didn't solve the problem.

I use VMplayer 2.5.2 build-156735 for running windows XP. 
this problem now occurs *VERY* frequently (since kernel #44 may be?) and I cannot reasonnably keep working like that, and unfortunately I have no solution for abandoning completely Windows...

S.

---

### Post by samR on 2009-07-02
some precision:

I have had this issue since february or januray 2009, with ubuntu 8.10. So before kernel 2.6.28-13 #44... but it happens much more frequently (several times per day!) since this week.
compiz is disable --> problem is still there.

IT IS A VERY SERIOUS PROBLEM FOR ME!!!! what can we do?????

S.

---

### Post by samR on 2009-07-02
ok, now it is happening every 15 minutes or so, I can't work, it's a nightmare. it has nothing to do with going back to the vm player after some time, it just happens, randomly (or so it seems to me, but I can't figure out what I am doing in particular when it happens... may be has to do with the programm I run in windows?)

below is my dmesg output, just after logging in again following the X crash.

> [ 5703.770822] wlan0: disassociating by local choice (reason=3)
[ 5703.771024] wlan0: direct probe to AP 00:17:9a:c2:e9:fa try 1
[ 5703.771466] bridge-wlan0: disabling the bridge
[ 5703.773607] wlan0 direct probe responded
[ 5703.773610] wlan0: authenticate with AP 00:17:9a:c2:e9:fa
[ 5703.775516] wlan0: authenticated
[ 5703.775519] wlan0: associate with AP 00:17:9a:c2:e9:fa
[ 5703.777939] wlan0: RX AssocResp from 00:17:9a:c2:e9:fa (capab=0x21 status=0 aid=6)
[ 5703.777941] wlan0: associated
[ 5703.785830] bridge-wlan0: down
[ 5703.786043] wlan0: disassociating by local choice (reason=3)
[ 5703.804204] bridge-wlan0: enabling the bridge
[ 5703.804208] bridge-wlan0: is a Wireless Adapter
[ 5703.804212] bridge-wlan0: up
[ 5703.804939] bridge-wlan0: disabling the bridge
[ 5703.816050] bridge-wlan0: down
[ 5703.816059] bridge-wlan0: detached
[ 5704.146252] vmmon: Had to deallocate locked 193255 pages from vm driver f4d51800
[ 5704.148344] vmmon: Had to deallocate AWE 5679 pages from vm driver f4d51800
[ 5715.011436] wlan0: deauthenticated
[ 5732.013515] wlan0: authenticate with AP 00:17:9a:c2:e9:fa
[ 5732.014294] wlan0: authenticate with AP 00:17:9a:c2:e9:fa
[ 5732.016000] wlan0: authenticated
[ 5732.016009] wlan0: associate with AP 00:17:9a:c2:e9:fa
[ 5732.019894] wlan0: RX ReassocResp from 00:17:9a:c2:e9:fa (capab=0x21 status=0 aid=6)
[ 5732.019900] wlan0: associated
[ 5732.023930] /dev/vmnet: open called by PID 2603 (vmnet-bridge)
[ 5732.023951] /dev/vmnet: hub 0 does not exist, allocating memory.
[ 5732.023974] /dev/vmnet: port on hub 0 successfully opened
[ 5732.023991] bridge-wlan0: is a Wireless Adapter
[ 5732.023999] bridge-wlan0: up
[ 5732.024011] bridge-wlan0: attached

---

### Post by kerrin on 2009-07-03
Going back to kernel version 2.6.28-11.42 worked.  VMWare hasn't crashed X since.

---

### Post by samR on 2009-07-07
yes that's what I have done, it seems better indeed.

thanks

---

### Post by sk1ds on 2009-07-29
> **kerrin said:**
> Going back to kernel version 2.6.28-11.42 worked.  VMWare hasn't crashed X since.

Hi, 

I am getting the exact same problem, except I am on a different
platform and version (I think).

Hoping someone will be able to help me.

```
$uname -a

Linux ubuntu-laptop 2.6.27-14-generic #1 SMP Tue Jun 30 19:57:39 UTC 2009 i686 GNU/Linux
```This is on a Dell Inspiron 1520 running Ubuntu 8.10.

This seems to be the latest kernel version for me ? 

Any suggestions for me.

Many thanks

Neil

---

