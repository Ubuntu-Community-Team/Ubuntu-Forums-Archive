---
title: "Leap 15.5: wifi connection to internet failed."
date: 2024-06-09
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-06-09
(Multi DSL Wireless Router). It works in other distro.

```
# lspci -v
05:00.0 Network controller: Intel Corporation Centrino Wireless-N 135 (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 135 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f7c00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number XXXXX 
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```

```
# systemctl status NetworkManager.service 
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/etc/systemd/system/NetworkManager.service; enabled; vendor preset: disabled)
     Active: active (running) since Sat 2024-06-08 19:00:09 CEST; 4min 8s ago
       Docs: man:NetworkManager(8)
   Main PID: 3995 (NetworkManager)
      Tasks: 4 (limit: 4915)
     CGroup: /system.slice/NetworkManager.service
             &#9500;&#9472; 3995 /usr/sbin/NetworkManager --no-daemon
             &#9492;&#9472; 4070 /sbin/dhclient -d -q -sf /usr/lib/nm-dhcp-helper -pf /var/run/NetworkManager/dhclient-wlan0.pid -lf /var/lib/NetworkMa>

#

```

```
# journalctl -r
Jun 08 19:00:30 maketopsite dbus-daemon[696]: [system] Activating via systemd: service name='org.freedesktop.resolve1' unit='dbus-org.freedesktop.resolve1.service' requested by ':1.69' (uid=0 pid=>
Jun 08 19:00:26 maketopsite dbus-daemon[696]: [system] Activation via systemd failed for unit 'dbus-org.freedesktop.resolve1.service': Unit dbus-org.freedesktop.resolve1.service not found.
Jun 08 19:00:26 maketopsite dbus-daemon[696]: [system] Activating via systemd: service name='org.freedesktop.resolve1' unit='dbus-org.freedesktop.resolve1.service' requested by ':1.69' (uid=0 pid=>
Jun 08 19:00:24 maketopsite dns-dnsmasq.sh[4209]: <debug> NETWORKMANAGER_DNS_FORWARDER is not set to "dnsmasq" in /etc/sysconfig/network/config -> exit
Jun 08 19:00:24 maketopsite dns-dnsmasq.sh[4150]: <debug> NETWORKMANAGER_DNS_FORWARDER is not set to "dnsmasq" in /etc/sysconfig/network/config -> exit
Jun 08 19:00:24 maketopsite dns-dnsmasq.sh[4110]: <debug> NETWORKMANAGER_DNS_FORWARDER is not set to "dnsmasq" in /etc/sysconfig/network/config -> exit
Jun 08 19:00:24 maketopsite dbus-daemon[696]: [system] Activation via systemd failed for unit 'dbus-org.freedesktop.resolve1.service': Unit dbus-org.freedesktop.resolve1.service not found.
Jun 08 19:00:24 maketopsite systemd[1]: Started Network Manager Script Dispatcher Service.
Jun 08 19:00:24 maketopsite dbus-daemon[696]: [system] Activating via systemd: service name='org.freedesktop.resolve1' unit='dbus-org.freedesktop.resolve1.service' requested by ':1.69' (uid=0 pid=>
Jun 08 19:00:24 maketopsite dbus-daemon[696]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 08 19:00:24 maketopsite systemd[1]: Starting Network Manager Script Dispatcher Service...
Jun 08 19:00:24 maketopsite dbus-daemon[696]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.69' (>
Jun 08 19:00:20 maketopsite systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Jun 08 19:00:19 maketopsite lxpanel[2724]: Unhandled action type _OB_WM_ACTION_UNDECORATE
Jun 08 19:00:19 maketopsite kernel: ll header: 00000000: ff ff ff ff ff ff XX XX XX XX XX
Jun 08 19:00:19 maketopsite kernel: IPv4: martian source 255.255.255.255 from 10.0.0.138, on dev wlan0
Jun 08 19:00:18 maketopsite kernel: IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 08 19:00:17 maketopsite kernel: wlan0: associated
Jun 08 19:00:17 maketopsite kernel: wlan0: RX AssocResp from XXXXXX (capab=0x411 status=0 aid=1)
Jun 08 19:00:17 maketopsite kernel: wlan0: associate with XXXXXX (try 1/3)
Jun 08 19:00:17 maketopsite kernel: wlan0: waiting for beacon from XXXXXX
Jun 08 19:00:17 maketopsite kernel: wlan0: authenticated
Jun 08 19:00:17 maketopsite kernel: wlan0: send auth to XXXXXX (try 1/3)
Jun 08 19:00:17 maketopsite kernel: wlan0: authenticate with XXXXXX
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: iwl_trans_wait_tx_queues_empty bad state = 0
Jun 08 19:00:17 maketopsite kernel: ieee80211 phy0: Hardware restart was requested
Jun 08 19:00:17 maketopsite kernel: wlan0: authentication with XXXXXX timed out
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000050305:0x00000000:0125
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000050288:0x11000001:1244
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000050288:0x00000040:1243
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000050145:0x091b004e:0401
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000050038:0x091a0018:0401
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049969:0x09190018:0401
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049966:0x00000037:1592
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049965:0x00000000:0663
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049962:0x00000037:0487
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049957:0x00000015:0472
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049956:0x00000037:0454
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049955:0x00000037:1111
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049891:0x0000c2e3:1110
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049888:0x00000018:0107
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049888:0x00000118:0106
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049887:0x00000016:0104
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049886:0x00000005:0103
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049873:0x00000000:1550
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049873:0x00020000:1552
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: EVT_LOGT:0000049872:0x00000118:0107
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: Start IWL Event Log Dump: display last 20 entries
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00001828 | flow_handler
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x13011700 | timestamp
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000005 | lmpm_pmg_sel
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x000291D2 | wait_event
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00010110 | isr_pref
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | isr4
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x0145FCC0 | isr3
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000602 | isr2
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | isr1
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00022008 | isr0
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x0000001C | hcmd
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00C80300 | board version
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000120 | hw version
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x754312A8 | uCode version
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | time gp3
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x0000C478 | time gp2
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | time gp1
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x000003AB | tsf low
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00018C55 | beacon time
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x000000A2 | line
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | data2
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | data1
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00000000 | interruptlink2
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x0000EB3A | interruptlink1
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00019E0E | branchlink2
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00019E0E | branchlink1
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x00019DA8 | uPc
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: 0x000014E1 | ADVANCED_SYSASSERT          
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: Status: 0x0000004C, count: 6
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: Loaded firmware version: 18.168.6.1 135-6.ucode
Jun 08 19:00:17 maketopsite kernel: iwlwifi 0000:05:00.0: Microcode SW error detected.  Restarting 0x2000000.
Jun 08 19:00:16 maketopsite kernel: iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
Jun 08 19:00:16 maketopsite kernel: iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0

```


Any idea please ?

---

