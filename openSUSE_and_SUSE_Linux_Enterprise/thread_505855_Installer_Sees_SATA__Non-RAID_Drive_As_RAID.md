---
title: "Installer Sees SATA / Non-RAID Drive As RAID"
date: 2007-07-20
forum: openSUSE and SUSE Linux Enterprise
---

### Post by SuSUntu on 2007-07-20
When attempting to install OpenSuse 10.2 (in a multiboot system), the partitioner identified one of my non-RAID drives in this way:

USED BY RAID pdc_efeidfef
dev/mapper/pdc_efeidfef

and it identified the volumes on that drive in this way:

dev/mapper/pdc_efeidfef_part1 (my note: represents extended partition)
dev/mapper/pdc_efeidfef_part5 (my note: represents 1st volume on extended partition)
dev/mapper/pdc_efeidfef_part6 (my note: represents 2nd volume on extended partition) 
dev/mapper/pdc_efeidfef_part7 (my note: represents 3rd volume on extended partition)
dev/mapper/pdc_efeidfef_part8 (my note: represents 4th volume on extended partition)
etc.

The drive should have been correctly identified as /dev/sdb,  and the volumes as /dev/sdb5, /dev/sdb6, /dev/sdb7, /dev/sdb8, etc.

The drive in question is a SATA I Samsung 160GB on one of the non-RAID SATA connectors on the MB.Two other drives in the system (a WD Raptor and a Seagate 320GB SATA II) are correctly identified. Oddly enough, the Seagate is the only drive on the SATA / RAID controller (set to SATA only) and it does not confuse the OpenSuse 10.2 partitioner. 

Ubuntu properly identifies the drive / volumes as does CentOS installers. Standalone partitioners also identify the drive / volumes correctly (i.e., gParted works correctly).

I also tried installing PCLinuxOS immediately afterward (I liked its ability to run Beryl so easily from the LiveCD), and much to my dismay, its partitioner (drak?) also thought the drive was in a RAID setup.

I'd like to install the new versions of OpenSuse and / or PCLinuxOS, but I make it a policy to abort any installer whose partitioner misidentifies anything during installation (most people probably do, don't they?). In this case, the distributions themselves were to be installed on /dev/sdc (which was identified correctly), but I do need to mount some volumes on /dev/sdb. In any case, I just don't trust any installer that can't properly identify my drives.

Any thoughts?

---

