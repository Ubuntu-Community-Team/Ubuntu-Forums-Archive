---
title: "[SOLVED] Ubuntu hanging up randomly, difficult reboot"
date: 2008-08-28
forum: x86 64-bit Users
---

### Post by Vashthe3rd on 2008-08-28
I recently moved, and ofcourse, moved my machine with me, after doing this, my Ubuntu has been freezing randomly, it will freeze with music playing, without music playing, with firefox open, without firefox open. It'll freeze if I leave it, it will freeze if I mess with it.
After any one of these, the reboot is difficult, it runs a disk check on 
/dev/sda5, all is fine until it finds a duplicate block, and it will stay there.
Any ideas as to what's wrong, what the solution is?
The disk check will run in regular and recovery mode, in recovery there's no way around it

---

### Post by Crafty Kisses on 2008-08-28
Could be a RAM/resource issue, post the output of > top

---

### Post by Kilz on 2008-08-28
> **Vashthe3rd said:**
> I recently moved, and ofcourse, moved my machine with me, after doing this, my Ubuntu has been freezing randomly, it will freeze with music playing, without music playing, with firefox open, without firefox open. It'll freeze if I leave it, it will freeze if I mess with it.
After any one of these, the reboot is difficult, it runs a disk check on 
/dev/sda5, all is fine until it finds a duplicate block, and it will stay there.
Any ideas as to what's wrong, what the solution is?
The disk check will run in regular and recovery mode, in recovery there's no way around it

The fact that it runs a disk check and finds a bad block on multiple scans may indicatew the drive has some problems. This happened to me about a week before the drive in my small file server died. How old is the drive?

---

### Post by Vashthe3rd on 2008-08-28
This is what I got after a top
The drive itself is around 2-3 years old
[PHP] top - 11:22:35 up 10:39,  2 users,  load average: 0.31, 0.50, 0.51
Tasks: 128 total,   1 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.1%us,  1.9%sy,  0.0%ni, 86.8%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1029056k total,  1017756k used,    11300k free,    30300k buffers
Swap:  3012148k total,       12k used,  3012136k free,   508924k cached
5917 root      20   0  395m  61m  15m S   11  6.1 222:01.85 Xorg                                                                                            
 9533 jordan    20   0  567m  59m  35m S    6  5.9   0:58.37 amarokapp                                                                                       
 9651 jordan    20   0  545m 132m  25m S    3 13.2   0:46.33 firefox                                                                                         
 9132 jordan    20   0  101m  16m 8488 S    3  1.7  16:22.38 npviewer.bin                                                                                    
 9749 jordan    20   0  262m  24m  12m S    2  2.4   0:01.92 gnome-terminal                                                                                  
 6439 jordan    20   0  100m  13m 8548 S    1  1.4   2:23.55 npviewer.bin                                                                                    
 9683 jordan    20   0  101m  16m 8656 S    1  1.7   0:06.30 npviewer.bin                                                                                    
 9773 jordan    20   0 18992 1280  936 R    1  0.1   0:00.18 top                                                                                             
    1 root      20   0  4020  880  592 S    0  0.1   0:00.84 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.80 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:01.60 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.16 events/0                                                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.16 events/1                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   44 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                       
   45 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/1                                                                                       
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   49 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
  159 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                         
  207 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  208 root      20   0     0    0    0 S    0  0.0   0:00.34 pdflush                                                                                         
  209 root      15  -5     0    0    0 S    0  0.0   0:00.26 kswapd0                                                                                         
  252 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
  253 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
 1572 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1573 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
 1584 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                        
 1626 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                                                           
 1627 root      15  -5     0    0    0 S    0  0.0   0:00.16 ata/1                                                                                           
 1628 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
 2353 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                                                                                     
 2362 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                       
 2363 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                       
 2389 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                       
 2390 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                       
 2414 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4                                                                                       
 2418 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                                                       
 2665 root      15  -5     0    0    0 S    0  0.0   0:00.58 kjournald                                                                                       
 2848 root      16  -4 17196 1304  384 S    0  0.1   0:00.70 udevd                                                                                           
 3091 root      15  -5     0    0    0 S    0  0.0   0:00.00 kgameportd                                                                                      
 4568 dhcp      18  -2 15108 1012  484 S    0  0.1   0:00.00 dhclient3                                                                                       
 4945 root      20   0  3864  588  492 S    0  0.1   0:00.00 getty                                                                                           
 4946 root      20   0  3864  588  492 S    0  0.1   0:00.00 getty                                                                                           
 4950 root      20   0  3864  588  492 S    0  0.1   0:00.00 getty                                                                                           
 4951 root      20   0  3864  588  492 S    0  0.1   0:00.00 getty                                                                                           
 4952 root      20   0  3864  584  492 S    0  0.1   0:00.00 getty                                                                                           

[/PHP]

---

### Post by Vashthe3rd on 2008-08-28
had to reboot again, this time i managed to catch something
during the failed disk check the system said something about a fsk needing to be run in read-only mode
if that helps

---

### Post by Vashthe3rd on 2008-08-29
any help for this would be appreciated

---

### Post by Vashthe3rd on 2008-08-29
never mind I found a way to run fsck in root
salvaged and repaired everything, boots like new again

---

### Post by Crafty Kisses on 2008-08-29
Can you please mark the thread as solved. :)

---

