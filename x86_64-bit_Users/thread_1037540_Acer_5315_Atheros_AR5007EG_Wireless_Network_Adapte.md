---
title: "Acer 5315 Atheros AR5007EG Wireless Network Adapter Driver Help"
date: 2009-01-11
forum: x86 64-bit Users
---

### Post by TheAmazingCorey on 2009-01-11
Hi,  first off let me say, I'm Corey and I'm new to Ubuntu \ Forums (less than 24 hrs) and I'm trying to find the right driver for my Atheros AR5007EG Wireless Network Adapter. I did the install using v8.04 LTS DVD and I am dual booting XP Pro SP3.  I am not quite sure which one I need and how to install it.  Any help with this would be greatly appreciated.

---

### Post by stchman on 2009-01-12
> **TheAmazingCorey said:**
> Hi,  first off let me say, I'm Corey and I'm new to Ubuntu \ Forums (less than 24 hrs) and I'm trying to find the right driver for my Atheros AR5007EG Wireless Network Adapter. I did the install using v8.04 LTS DVD and I am dual booting XP Pro SP3.  I am not quite sure which one I need and how to install it.  Any help with this would be greatly appreciated.

You can try this for Hardy.  Taken from the Aspire One community documentation.

```

cd ~
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -vxzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
modprobe ath_pci

```

You may have to append ath_pci to /etc/modules:


```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ath_pci

```

Hope this helps.

Only problem with this is that when a new kernel is pushed you will have to remake the drivers.

---

