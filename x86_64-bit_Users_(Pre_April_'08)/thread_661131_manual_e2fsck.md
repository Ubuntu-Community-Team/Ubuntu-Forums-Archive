---
title: "manual e2fsck"
date: 2008-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by hotbit on 2008-01-07
My system freezes recently for some reasons(?) and I had to do hard restarts. I am trying  to run manually e2fsck (from system started from live CD), but
1)  I am called a BONEHEAD :(
2) E2FSCK says FIXED, but next check is showing the same or different(!!) errors. 
I paste 2 consecutive checks, done one by one:


ubuntu@ubuntu:~$ sudo e2fsck -y -f -v /dev/sda1
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Entry 'mount.smb.8.gz' in /usr/share/man/man8 (7323697) has an incorrect filetype (was 7, should be 1).
Fix? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
WARNING: PROGRAMMING BUG IN E2FSCK!
        OR SOME BONEHEAD (YOU) IS CHECKING A MOUNTED (LIVE) FILESYSTEM.
inode_link_info[1835380] is 1, inode.i_links_count is 2.  They should be the same!
Inode 1835380 ref count is 2, should be 2.  Fix? yes

Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

  201013 inodes used (2.47%)
    3488 non-contiguous inodes (1.7%)
         # of inodes with ind/dind/tind blocks: 10095/137/0
 3152710 blocks used (19.39%)
       0 bad blocks
       3 large files

  157756 regular files
   18382 directories
     329 character device files
      26 block device files
       3 fifos
     473 links
   24496 symbolic links (16853 fast symbolic links)
      12 sockets
--------
  201477 files


ubuntu@ubuntu:~$ sudo e2fsck -C0 -y -f -v /dev/sda1
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Entry 'mount.smb.8.gz' in /usr/share/man/man8 (7323697) has an incorrect filetype (was 1, should be 7).
Fix? yes

Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
WARNING: PROGRAMMING BUG IN E2FSCK!                                            
        OR SOME BONEHEAD (YOU) IS CHECKING A MOUNTED (LIVE) FILESYSTEM.
inode_link_info[1835380] is 1, inode.i_links_count is 2.  They should be the same!
Inode 1835380 ref count is 2, should be 2.  Fix? yes

Inode 7094777 ref count is 4, should be 1.  Fix? yes                           

WARNING: PROGRAMMING BUG IN E2FSCK!
        OR SOME BONEHEAD (YOU) IS CHECKING A MOUNTED (LIVE) FILESYSTEM.
inode_link_info[7668089] is 1, inode.i_links_count is 2.  They should be the same!
Inode 7668089 ref count is 2, should be 2.  Fix? yes

Pass 5: Checking group summary information
                                                                               
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

  201013 inodes used (2.47%)
    3488 non-contiguous inodes (1.7%)
         # of inodes with ind/dind/tind blocks: 10095/137/0
 3152710 blocks used (19.39%)
       0 bad blocks
       3 large files

  157756 regular files
   18382 directories
     329 character device files
      26 block device files
       3 fifos
     473 links
   24496 symbolic links (16853 fast symbolic links)
      12 sockets
--------
  201477 files

I have no idea what am I doing wrong. Help appreciated.
Cheers!

---

