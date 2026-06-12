---
title: "NetworkManager PPTP problem"
date: 2007-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by koverg on 2007-07-27
Hi,

I use x64 version of 7.04. 

First I run into a bug in the stable network-manager-pptp_0.6.4

crashed with:

Jul 28 00:06:17 kover-desktop kernel: [  155.697466] nm-ppp-auth-dia[8470]: segfault at 0000000000000088 rip 00002ba736bc421b rsp 00007fff79a7c350 error 4

Fortunately I found a newer version here: [http://craig.dubculture.co.nz/blog/2007/05/13/new-networkmanager-pptp-package-fixes-amd64-crashes/]("http://craig.dubculture.co.nz/blog/2007/05/13/new-networkmanager-pptp-package-fixes-amd64-crashes/")

But I still have a problem:

```
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IWill activate VPN connection 'S2', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'kover', vpn_data '', route ''. 
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IVPN Activation (S2) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IVPN Activation (S2) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IVPN Activation (S2) Stage 2 of 4 (Connection Prepare Wait) complete. 
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IVPN Activation (S2) Stage 3 of 4 (Connect) scheduled... 
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IVPN Activation (S2) Stage 3 of 4 (Connect) sending connect request. 
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IVPN Activation (S2) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Jul 28 00:41:12 kover-desktop NetworkManager: <WARNING>^I nm_vpn_service_process_signal (): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'VPNConfigBad', with message 'Validating options failed'. 
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 6. 
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IVPN Activation (S2) Stage 3 of 4 (Connect) reply received. 
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IVPN Activation (S2) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Jul 28 00:41:12 kover-desktop NetworkManager: <information>^IVPN Activation (S2) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Jul 28 00:41:12 kover-desktop NetworkManager: <WARNING>^I nm_vpn_service_stop_connection (): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'S2' because service was 6. 


```

Other problem, that I cannot edit previously created PPTP connections, becuse the config dialog is empty.

Thanks in advance,

koverg

---

### Post by koverg on 2007-07-30
Finally I solved the problem.

In the new PPTP connection dialog I had to fill some extra fields (which seems to be required but not checked) and viola: the PPTP connection is saved, can be edited, and WORKS!

koverg

---

### Post by justDIY on 2007-08-02
what fields did you have to fill in?  I've run into the same trouble on a fresh install of Fiesty on Core2 Duo (amd-x64)

Thanks!

---

