---
title: "SATA Fakeraid problem"
date: 2008-07-21
forum: x86 64-bit Users
---

### Post by ungamed on 2008-07-21
Hello,

I'm having a problem accessing my data drive in ubuntu, it works fine in Windows, here's the specs:

3 x 400 GB Hitachi sata2 disks in nvidia JBoD array, formatted with a single 1.02 TB ntfs partition.

Here's what I've tried:

**dmraid -ay**
```
RAID set "nvidia_fdhibbad" already active
RAID set "nvidia_fdhibbad1" already active

```

**dmraid -s**
```
*** Active Set
name   : nvidia_fdhibbad
size   : 2344268160
stride : 128
type   : linear
status : ok
subsets: 0
devs   : 3
spares : 0

```

**ls -la /dev/mapper**
```
crw-rw----  1 root root  10, 63 2008-07-21 15:47 control
brw-rw----  1 root disk 254,  0 2008-07-21 14:56 nvidia_fdhibbad
brw-rw----  1 root disk 254,  1 2008-07-21 14:56 nvidia_fdhibbad1

```

**mount /dev/mapper/nvidia_fdhibbad1 /media/test**
```
$MFTMirr error: Invalid mft record for '$MFT'.
Failed to mount '/dev/mapper/nvidia_fdhibbad1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```

**ntfsfix /dev/mapper/nvidia_fdhibbad1**
```
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... FAILED
$MFTMirr error: Invalid mft record for $MFT.
```

**fdisk -l /dev/mapper/nvidia_fdhibbad1**
```
Disk /dev/mapper/nvidia_fdhibbad1: 1200.2 Gb, 1200257501184 byte
255 heads, 63 sectors/track, 145922 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74657265

Dette ligner ikke en partitionstabel -> This doesnt look like a partitiontable
Du har nok valgt den forkerte enhed. -> You probably selected the wrong unit. 

                         Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/mapper/nvidia_fdhibbad1p1   ?       68059      139251   571849270   6b  Ukendt -> Unknown
Partition 1 slutter ikke på en cylindergrænse. -> Partition 1 doesn't end on a cylinder boundary.
/dev/mapper/nvidia_fdhibbad1p2   ?      121539      236830   926069648   65  Novell Netware 386
Partition 2 slutter ikke på en cylindergrænse. -> Partition 2 doesn't end on a cylinder boundary.
/dev/mapper/nvidia_fdhibbad1p3   ?       10499       10499           0   74  Ukendt -> Unknown
Partition 3 slutter ikke på en cylindergrænse. -> Partition 3 doesn't end on a cylinder boundary.
/dev/mapper/nvidia_fdhibbad1p4          157185      157188       24275    0  Tom -> Empty
Partition 4 slutter ikke på en cylindergrænse. -> Partition 4 doesn't end on a cylinder boundary.

Partitionstabellens indgange er ikke i disk-rækkefølge -> The partitionstables entries is not in disc-order.
```
(Sorry about the danish output, I didn't want to erase it if I translated something wrong.)

I also ran chkdsk /f under winxp (32 bit), It just said:
```
CHKDSK kontrollerer filer (trin 1 af 3)...

Kontrollen af filer er fuldført.

CHKDSK kontrollerer indeks (trin 2 af 3)...

Kontrollen af indeks er fuldført.

CHKDSK kontrollerer sikkerhedsbeskrivelser (trin 3 af 3)...

Kontrollen af sikkerhedsbeskrivelser er fuldført.

CHKDSK verificerer USN-journalfilen...

Verificeringen af USN-journalfilen er udført.

Windows har kontrolleret filsystemet og fandt ingen problemer.



1172126465 KB samlet diskplads.

1170314628 KB i 118829 filer.

     59132 KB i 8555 indeks.

         0 KB i beskadigede sektorer.

    265173 KB i brug af systemet.

     65536 KB i brug af logfilen.

   1487532 KB diskplads til rådighed.



      4096 byte i hver allokeringsenhed.

 293031616 allokeringsenheder i alt på disken.

    371883 allokeringsenheder til rådighed på disken.
```
Again sorry about the danish output, but it doesn't report any errors whatsoever and 0 KB in bad sectors.

Please help me, I really want this to work, I've searched everywhere but haven't seen any posts after 2006 with this kind of problem.

---

### Post by ungamed on 2008-07-23
Sorry but *BUMP*.

Please, if anyone has any idea whatsoever as to what could be wrong, and/or how to fix.

---

