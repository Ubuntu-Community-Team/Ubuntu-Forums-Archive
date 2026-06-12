---
title: "madwifi problems"
date: 2005-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by dablitz on 2005-10-25
i have done the how-to for madwifi. I am running a amd 64 bit 3000+ with a netgear wg311 v2 wifi card. modprobe find ath_hal, but when I modprobe ath_pci i get errors telling me to look at dmesg. so this is my results:

wlan: Unknown symbol wireless_send_event
ath_rate_sample: Unknown symbol ether_sprintf
ath_rate_sample: Unknown symbol ieee80211_iterate_nodes
ath_pci: Unknown symbol ieee80211_ioctl_siwrate
ath_pci: Unknown symbol ath_rate_tx_complete
ath_pci: Unknown symbol ieee80211_encap
ath_pci: Unknown symbol ieee80211_input
ath_pci: Unknown symbol ieee80211_ioctl_siwap
ath_pci: Unknown symbol ieee80211_ifattach
ath_pci: Unknown symbol if_printf
ath_pci: Unknown symbol ieee80211_sysctl_register
ath_pci: Unknown symbol ieee80211_ioctl_siwencode
ath_pci: Unknown symbol ieee80211_beacon_update
ath_pci: Unknown symbol ieee80211_ioctl_setmlme
ath_pci: Unknown symbol ieee80211_ioctl_setoptie
ath_pci: Unknown symbol ieee80211_ioctl_giwmode
ath_pci: Unknown symbol ieee80211_find_rxnode
ath_pci: Unknown symbol ath_rate_attach
ath_pci: Unknown symbol ether_sprintf
ath_pci: Unknown symbol ieee80211_ifdetach
ath_pci: Unknown symbol ieee80211_free_node
ath_pci: Unknown symbol ieee80211_ioctl_siwsens
ath_pci: Unknown symbol ath_rate_newassoc
ath_pci: Unknown symbol ieee80211_notify_michael_failure
ath_pci: Unknown symbol ieee80211_ioctl_chanlist
ath_pci: Unknown symbol ieee80211_ioctl_getparam
ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register
ath_pci: Unknown symbol ieee80211_dump_pkt
ath_pci: Unknown symbol ieee80211_ioctl_giwrate
ath_pci: Unknown symbol ieee80211_ioctl_siwrts
ath_pci: Unknown symbol ieee80211_ioctl_giwname
ath_pci: Unknown symbol ieee80211_cipher_none
ath_pci: Unknown symbol ieee80211_ioctl_setparam
ath_pci: Unknown symbol ieee80211_ioctl_siwpower
ath_pci: Unknown symbol ieee80211_ioctl_giwsens
ath_pci: Unknown symbol ieee80211_media_change
ath_pci: Unknown symbol ieee80211_ioctl_giwfreq
ath_pci: Unknown symbol ieee80211_beacon_alloc
ath_pci: Unknown symbol ieee80211_ioctl_siwfrag
ath_pci: Unknown symbol ieee80211_ioctl_giwap
ath_pci: Unknown symbol ieee80211_ioctl_siwfreq
ath_pci: Unknown symbol ieee80211_ibss_merge
ath_pci: Unknown symbol ieee80211_ioctl_giwpower
ath_pci: Unknown symbol ieee80211_mhz2ieee
ath_pci: Unknown symbol ieee80211_ioctl_giwrange
ath_pci: Unknown symbol ieee80211_ioctl_giwretry
ath_pci: Unknown symbol ieee80211_ioctl_giwnickn
ath_pci: Unknown symbol ieee80211_ioctl_giwrts
ath_pci: Unknown symbol ieee80211_iw_getstats
ath_pci: Unknown symbol ieee80211_ioctl_addmac
ath_pci: Unknown symbol ath_rate_node_cleanup
ath_pci: Unknown symbol ath_rate_detach
ath_pci: Unknown symbol ieee80211_ioctl_giwfrag
ath_pci: Unknown symbol ieee80211_wme_acnames
ath_pci: Unknown symbol ieee80211_ioctl_giwencode
ath_pci: Unknown symbol ieee80211_next_scan
ath_pci: Unknown symbol ieee80211_media_init
ath_pci: Unknown symbol ieee80211_ioctl_iwsetup
ath_pci: Unknown symbol ieee80211_ioctl
ath_pci: Unknown symbol ieee80211_ioctl_delmac
ath_pci: Unknown symbol ieee80211_classify
ath_pci: Unknown symbol ieee80211_media_status
ath_pci: Unknown symbol ieee80211_announce
ath_pci: Unknown symbol ieee80211_ioctl_setkey
ath_pci: Unknown symbol ieee80211_ioctl_iwaplist
ath_pci: Unknown symbol ieee80211_ioctl_delkey
ath_pci: Unknown symbol ieee80211_ioctl_siwtxpow
ath_pci: Unknown symbol ieee80211_chan2ieee
ath_pci: Unknown symbol ieee80211_ioctl_siwretry
ath_pci: Unknown symbol ieee80211_ioctl_siwnickn
ath_pci: Unknown symbol ieee80211_state_name
ath_pci: Unknown symbol ath_rate_node_init
ath_pci: Unknown symbol ieee80211_ioctl_siwscan
ath_pci: Unknown symbol ieee80211_ioctl_siwmode
ath_pci: Unknown symbol ieee80211_ioctl_getoptie
ath_pci: Unknown symbol ath_rate_findrate
ath_pci: Unknown symbol ieee80211_ioctl_giwessid
ath_pci: Unknown symbol ieee80211_ioctl_giwscan
ath_pci: Unknown symbol ieee80211_crypto_encap
ath_pci: Unknown symbol ieee80211_ioctl_siwessid
ath_pci: Unknown symbol ieee80211_chan2mode
ath_pci: Unknown symbol ieee80211_getrssi
ath_pci: Unknown symbol ieee80211_pwrsave
ath_pci: Unknown symbol ieee80211_find_txnode
ath_pci: Unknown symbol ath_rate_newstate
ath_pci: Unknown symbol ath_rate_setupxtxdesc
ath_pci: Unknown symbol ieee80211_ioctl_giwtxpow

i am wondering what I can do to fix this. any help would be great.

---

