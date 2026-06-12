---
title: "Broadcom chip, AIrPort express hub, wpa encryption - woe ensues ;/"
date: 2007-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by katu on 2007-01-17
Hi,
I have a broadcom chip that works in kubuntu edgy 64 bit (bcm43xx) on an unencrypted network. I need to connect to an apple airport extreme (sorry, the admin told me wrong the first time) hub, that is WPA encrypted (level 2, but has been changed to allow wpa 1 for testing). Right now the essid is broadcasted.  
For the love of me I can't get this to work. 

What I tried: 

[kubuntu howto]("https://wiki.kubuntu.org/WifiDocs/KubuntuWPAHowTo") 
The Knetworkmanager sees the network all right, but when I try to connect it gets to 28% (Configuring up the device) then disappears. 

iwscan list gives this:
```


eth1      Scan completed :
          Cell 01 - Address: 00:0D:88:8C:89:62
                    ESSID:"daqborex"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-61 dBm
                    Extra: Last beacon: 16ms ago
          Cell 02 - Address: 00:0A:95:F5:69:37
                    ESSID:"WAiRPort"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:13
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-39 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 100ms ago

```

I'm interested in the second one. While connecting via knetworkmanager iwconfig gives:


```
eth1      IEEE 802.11b/g  ESSID:"WAiRPort"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Note that it says that the access point is invalid.


Other stuff I tried: [ubuntu howto]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo")
I tried o hardwire the wpa_supplicant to see what happens. 
my wpa_supplicant file looks like this:

```
#
# File: wpa_supplicant.conf
#
ctrl_interface=/var/run/wpa_supplicant
ap_scan=0
#ctrl_interface_group=root
network={
        ssid="WAiRPort"
        scan_ssid=1
        proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
        psk=256db0e3d42e7d5e879d933bcc91cee41c275be013c47dc75aaaacac287f36c3}

```

and running 
**wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd**

doesn't connect, and gives:

```
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=0
Line: 7 - start of a new network block
ssid - hexdump_ascii(len=8):
     57 41 69 52 50 6f 72 74                           WAiRPort
scan_ssid=1 (0x1)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='WAiRPort'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:90:4b:9a:0e:d6
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
Wireless event: cmd=0x8b06 len=12
Wireless event: cmd=0x8b19 len=16
Received 633 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:0a:95:f5:69:37 ssid='WAiRPort' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   selected based on RSN IE
Trying to associate with 00:0a:95:f5:69:37 (SSID='WAiRPort' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
Wireless event: cmd=0x8b06 len=12
Wireless event: cmd=0x8b1a len=25
Wireless event: cmd=0x8c02 len=29
Custom wireless event: 'authenticated'
Wireless event: cmd=0x8b19 len=16
Received 633 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:0a:95:f5:69:37 ssid='WAiRPort' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   selected based on RSN IE
Already associated with the selected AP.
RSN: Ignored PMKID candidate without preauth flag
Wireless event: cmd=0x8c02 len=34
Custom wireless event: 'associating failed'
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:0a:95:f5:69:37 into blacklist
State: ASSOCIATING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Already associated with a configured network - generating associated event
Association info event
State: DISCONNECTED -> ASSOCIATED

```

iwconfig still says that access point is invalid. ;/

different values of ap_scan do nothing. 
At some point I was able to get iwconfig to see the mac of the access point, but I still didn't get an ip. Argh. Worse is I can't remember how ;/.

another thing that mayb useful is what dmesg has to say:
```
[ 1377.556493] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1400.032213] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1416.517826] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1446.493892] eth0: link down
[ 1446.529399] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1480.259456] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1502.191724] warning: many lost ticks.
[ 1502.191731] Your time source seems to be instable or some driver is hogging interupts
[ 1502.191747] rip handle_IRQ_event+0x1a/0x60
[ 1540.668848] SoftMAC: Authentication timed out with 00:0d:88:8c:89:62
[ 1587.551162] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1671.953430] SoftMAC: Authentication timed out with 00:0a:95:f5:69:37
[ 1791.940031] SoftMAC: Authentication timed out with 00:0a:95:f5:69:37
[ 1911.930632] SoftMAC: Authentication timed out with 00:0a:95:f5:69:37
[ 2031.917232] SoftMAC: Authentication timed out with 00:0a:95:f5:69:37
[ 2137.469820] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 2151.915837] SoftMAC: Authentication timed out with 00:0a:95:f5:69:37
[ 2271.902432] SoftMAC: Authentication timed out with 00:0a:95:f5:69:37
[ 2391.889034] SoftMAC: Authentication timed out with 00:0a:95:f5:69:37
[ 2417.556777] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2477.965681] SoftMAC: Authentication timed out with 00:0a:95:f5:69:37
[ 2833.714408] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2893.727531] SoftMAC: Authentication timed out with 00:0d:88:8c:89:62
[ 3296.995487] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3377.345484] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3434.495020] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 3439.367477] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3444.697260] eth0: no IPv6 routers present
[ 3499.775443] SoftMAC: Authentication timed out with 00:0d:88:8c:89:62
[ 3841.772361] SoftMAC: Open Authentication completed with 00:0a:95:f5:69:37
[ 4082.966098] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 4083.353022] SoftMAC: Open Authentication completed with 00:0a:95:f5:69:37
[ 4116.886921] SoftMAC: Open Authentication completed with 00:0a:95:f5:69:37
[ 4127.293185] SoftMAC: Open Authentication completed with 00:0a:95:f5:69:37
[ 4137.695125] SoftMAC: Open Authentication completed with 00:0a:95:f5:69:37
[ 4148.097331] SoftMAC: Open Authentication completed with 00:0a:95:f5:69:37
[ 4158.499990] SoftMAC: Open Authentication completed with 00:0a:95:f5:69:37
[ 4171.218440] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 4171.367303] SoftMAC: Open Authentication completed with 00:0a:95:f5:69:37
[ 4231.782457] SoftMAC: Open Authentication completed with 00:0a:95:f5:69:37
[ 4291.779615] SoftMAC: Open Authentication completed with 00:0a:95:f5:69:37
```

the above is first trying via Knetworkmanager and then wpa_supplicant ... 

Anyone have any ideas what I'm doing wrong here?

---

### Post by wieman01 on 2007-01-17
Want to try the HOWTO in my signature? It's quite straight-forward. Post there if you need support.

---

